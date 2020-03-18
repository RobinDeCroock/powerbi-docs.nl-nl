---
title: Ondersteuning voor bladwijzers toevoegen voor Power BI-visuals
description: In Power BI-visuals is het overschakelen van bladwijzers mogelijk
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 5bf1c79aa411788fdb3275b938e7eaad7d6014a1
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380520"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>Ondersteuning voor bladwijzers toevoegen voor Power BI-visuals

Met bladwijzers in Power BI rapporten kan de geconfigureerde weergave van een rapportpagina, selectiestatus en filterstatus van de visual worden vastgelegd. Hiervoor is wel een extra actie vereist wat Power BI-visuals betreft, om ondersteuning te bieden voor bladwijzers en op de juiste manier op wijzigingen te reageren.

Zie [Bladwijzers gebruiken om inzichten te delen en verhalen te vertellen in Power BI](https://docs.microsoft.com/power-bi/desktop-bookmarks) voor meer informatie over bladwijzers.

## <a name="report-bookmarks-support-in-your-visual"></a>Ondersteuning voor bladwijzers in rapporten in uw visual

Als uw visual interactief wordt gebruikt met andere visuals, hiermee gegevenspunten worden geselecteerd of andere visuals worden gefilterd, moet u de status vanuit de eigenschappen herstellen.

## <a name="add-report-bookmarks-support"></a>Ondersteuning voor rapportbladwijzers toevoegen

1. Installeer het vereiste hulpprogramma [powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versie 3.0.0 of hoger, of werk dit bij. Dit bevat extra klassen om de statusselectie of het filter te manipuleren. Het is vereist voor filtervisuals en alle visuals die de `InteractivityService` gebruiken.

2. Werk de Visual API naar versie 1.11.0 bij om `registerOnSelectCallback` te gebruiken in een exemplaar van `SelectionManager`. Dit is vereist voor visuals zonder filters die de gewone `SelectionManager` gebruiken in plaats van de `InteractivityService`.

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Hoe Power BI-visuals interactief werken met Power BI in rapportbladwijzers

Laten we eens kijken naar het volgende scenario: u wilt verschillende bladwijzers maken op de rapportpagina, met steeds een andere selectiestatus in elke bladwijzer.

Eerst selecteert u een gegevenspunt in uw visual. De visual werkt interactief met Power BI en andere visuals door selecties aan de host door te geven. Vervolgens selecteert u **Toevoegen** in het deelvenster **Bladwijzer** en Power BI slaat de huidige selecties voor de nieuwe bladwijzer op.

Dit gebeurt regelmatig als u de selectie wijzigt en nieuwe bladwijzers toevoegt. Nadat u de bladwijzers hebt gemaakt, kunt u hiertussen schakelen.

Wanneer u een bladwijzer selecteert, herstelt Power BI het opgeslagen filter of de selectiestatus en wordt deze aan de visuals doorgegeven. Andere visuals worden gemarkeerd of gefilterd volgens de status die in de bladwijzer is opgeslagen. De Power BI-host is verantwoordelijk voor de acties. Uw visual is verantwoordelijk voor de juiste weergave van de nieuwe selectiestatus (bijvoorbeeld voor de gewijzigde kleur van weergegeven gegevenspunten).

De nieuwe selectiestatus wordt naar de visual gecommuniceerd via de `update`-methode. Het `options`-argument bevat een speciale eigenschap, `options.jsonFilters`. De JSONFilter-eigenschap kan `Advanced Filter` en `Tuple Filter` bevatten.

De visual moet de filterwaarden herstellen om de bijbehorende status van de visual voor de geselecteerde bladwijzer weer te geven. Of gebruik de speciale callback-functie van de voor aanroepen geregistreerde `registerOnSelectCallback`-methode ISelectionManager, als voor de visual alleen selecties worden gebruikt.

### <a name="visuals-with-selection"></a>Visuals met selecties

Als uw visual samenwerkt met andere visuals met behulp van [Selectie](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md), kunt u op twee manieren bladwijzers toevoegen:

* Als de visual [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) nog niet heeft gebruikt, kunt u de methode `FilterManager.restoreSelectionIds` gebruiken.

* Als de visual [InteractivityService](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) al gebruikt om selecties te beheren, moet u de `applySelectionFromFilter`-methode gebruiken in het exemplaar van `InteractivityService`.

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>ISelectionManager.registerOnSelectCallback gebruiken

Wanneer u een bladwijzer selecteert, wordt in Power BI de `callback`-methode aangeroepen van de visual met overeenkomstige selecties. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

We gaan ervan uit dat u een gegevenspunt in uw visual hebt die is gemaakt in de methode [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74).

En `datapoints` ziet eruit als:

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

U hebt nu `visualDataPoints` als uw gegevenspunten en de `ids`-matrix is doorgestuurd naar de `callback`-functie.

Op dit punt moet de visual de matrix van `ISelectionId[]` vergelijken met de selecties in uw `visualDataPoints`-matrix en overeenkomstige gegevenspunten als geselecteerd markeren.

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

Nadat de gegevenspunten zijn bijgewerkt, geven deze de huidige selectiestatus weer die is opgeslagen in het `filter`-object. Nadat de gegevenspunten zijn weergegeven, komt de selectiestatus van de aangepaste visual overeen met de status van de bladwijzer.

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>InteractivityService gebruiken om selecties in de visual te controleren

Als voor uw visual `InteractivityService` wordt gebruikt, zijn er geen extra acties nodig voor ondersteuning van bladwijzers in uw visual.

Wanneer u bladwijzers selecteert, behandelt het hulpprogramma de selectiestatus van de visual.

### <a name="visuals-with-a-filter"></a>Visuals met een filter

Stel dat de visual een filter van gegevens maakt op basis van datumbereik. U hebt `startDate` en `endDate` als de begin- en einddatum van het bereik.

In de visual wordt een geavanceerd filter gemaakt en de hostmethode `applyJsonFilter` aangeroepen om gegevens te filteren op de relevante voorwaarden.

Het doel is de tabel die wordt gebruikt voor het filteren.

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

Steeds wanneer u op een bladwijzer klikt, wordt een `update`-aanroep naar de aangepaste visual verzonden.

Met de aangepaste visual wordt het filter gecontroleerd in het object:

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

Als het `filter`-object niet null is, moeten filtervoorwaarden uit het object door de visual worden hersteld:

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

Daarna moet de interne status van de visual worden gewijzigd, zodat deze overeenkomt met de huidige voorwaarden. De interne status bevat de gegevenspunten en visualisatieobjecten (lijnen, rechthoeken, enzovoort).

> [!IMPORTANT]
> In het scenario met rapportbladwijzers moet `applyJsonFilter` niet door de visual worden aangeroepen om andere visuals te filteren. Deze worden al gefilterd door Power BI.

Met de visual Tijdlijn-slicer wijzigt u de bereikkiezer in de overeenkomstige gegevensbereiken.

Zie de [opslagplaats voor tijdlijn-slicers](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) voor meer informatie.

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>Filter de status om visuele eigenschappen in bladwijzers op te slaan

Door de `filterState`-eigenschap wordt een eigenschap een onderdeel van het filterproces. In de visual kunnen verschillende waarden in bladwijzers worden opgeslagen.

Als u de waarde van de eigenschap wilt opslaan als een filterstatus, markeert u de objecteigenschap als `"filterState": true` in het bestand *capabilities.json*.

De tijdlijnslicer slaat bijvoorbeeld `Granularity` de eigenschapswaarden op in een filter. Hiermee kan de huidige granulariteit veranderen als u de bladwijzers wijzigt.

Zie de [opslagplaats voor tijdlijn-slicers](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334) voor meer informatie.
