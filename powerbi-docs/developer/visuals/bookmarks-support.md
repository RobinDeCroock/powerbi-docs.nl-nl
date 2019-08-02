---
title: Bladwijzers
description: In Power BI-visual is het overschakelen van bladwijzers mogelijk
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425500"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Ondersteuning voor bladwijzers toevoegen voor Power BI-visuals

Met bladwijzers in Power BI rapporten kan de geconfigureerde weergave van een rapportpagina, selectiestatus, filterstatus van de visual worden vastgelegd. Hiervoor is wel een extra actie vereist wat aangepaste visuals betreft, om ondersteuning te bieden voor bladwijzers en op de juiste manier op wijzigingen te reageren.

Lees meer over bladwijzers in de [documentatie](https://docs.microsoft.com/power-bi/desktop-bookmarks)

## <a name="report-bookmarks-support-in-your-visual"></a>Ondersteuning voor bladwijzers in rapporten in uw visual

Als uw visual interactief wordt gebruikt met andere visuals, hiermee gegevenspunten worden geselecteerd of andere visuals worden gefilterd, moet u de status vanuit de eigenschappen herstellen.

## <a name="how-to-add-report-bookmarks-support"></a>Ondersteuning voor rapportbladwijzers toevoegen

1. Installeer het vereiste hulpprogramma (of werk dit bij): `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) versie 3.0.0 of hoger. Dit bevat extra klassen om de statusselectie of het filter te manipuleren. Het is vereist voor filtervisuals en alle visuals die de `InteractivityService` gebruiken.

2. Werk de API van de visual bij naar 1.11.0 om `registerOnSelectCallback` te gebruiken in het exemplaar van `SelectionManager`. Dit is vereist voor visuals zonder filters die de gewone `SelectionManager` gebruiken in plaats van de `InteractivityService`.

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>Hoe aangepaste visuals interactief werken met Power BI in het scenario met rapportbladwijzers

Kijk eens naar het volgende voorbeeld: Een gebruiker maakt verschillende bladwijzers op de rapportpagina, met een andere status in elke bladwijzer.

De gebruiker selecteert eerst een gegevenspunt in uw visual. De visual werkt interactief met Power BI en andere visuals door selecties aan de host door te geven. Vervolgens selecteert de gebruiker Toevoegen in `Bookmark panel`. In Power BI worden de huidige selecties voor de nieuwe bladwijzer opgeslagen.

Dit gebeurt regelmatig als de gebruiker de selectie wijzigt en nieuwe bladwijzers toevoegt.
Zodra de gebruiker de bladwijzers heeft gemaakt, kan hij of zij tussen de bladwijzers schakelen.

Wanneer gebruikers een bladwijzer selecteren, herstelt Power BI het opgeslagen filter of de selectiestatus en wordt deze aan de visuals doorgegeven. Andere visuals worden gemarkeerd of gefilterd volgens de status die in de bladwijzer is opgeslagen. De Power BI-host is verantwoordelijk voor acties. Uw visual is verantwoordelijk voor de juiste weergave van de nieuwe selectiestatus (bijvoorbeeld de gewijzigde kleur van weergegeven gegevenspunten).

De nieuwe selectiestatus wordt naar de visual gecommuniceerd via de `update`-methode. Het `options`-argument bevat een speciale eigenschap: `options.jsonFilters`. Dit is JSONFilter en deze eigenschap kan `Advanced Filter` en `Tuple Filter` bevatten.

De visual moet filterwaarden herstellen om de bijbehorende status van de visual voor de geselecteerde bladwijzer weer te geven.

Of gebruik de speciale callback-functie van voor aanroepen geregistreerde `registerOnSelectCallback`-methode ISelectionManager, als voor de visual alleen selecties worden gebruikt.

### <a name="visuals-with-selections"></a>Visuals met selecties

Als uw visuals interactief andere visuals gebruiken met behulp van [selecties](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md). U kunt op twee manieren bladwijzers toevoegen.

* U kunt de `FilterManager.restoreSelectionIds`-methode gebruiken als u **nog niet eerder gebruik hebt gemaakt van [`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** in uw visual.

* Als **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** al in uw visual wordt gebruikt om selecties te beheren. U moet de `applySelectionFromFilter`-methode gebruiken in een exemplaar van `InteractivityService`.

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>`ISelectionManager.registerOnSelectCallback` gebruiken

Wanneer een gebruiker op bladwijzers klikt, wordt in Power BI de `callback`-methode aangeroepen van de visual met overeenkomstige selecties. 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

Stel dat u een gegevenspunt in uw visual hebt gemaakt in de [`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74)-methode.

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

U hebt dus `visualDataPoints` als uw gegevenspunten en de `ids`-matrix is doorgestuurd naar de `callback`-functie.

Op dit punt moet de visual de matrix van `ISelectionId[]` vergelijken met de selecties in uw `visualDataPoints`-matrix en overeenkomstige gegevenspunten als Geselecteerd markeren.

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

Nadat de gegevenspunten zijn bijgewerkt, tonen ze de huidige selectiestatus die is opgeslagen in het `filter`-object. Vervolgens zal, nadat de gegevenspunten zijn weergegeven, de selectiestatus van de aangepaste visual overeenkomen met de status van de bladwijzer.

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>`InteractivityService` gebruiken om selecties in de visual te controleren

Als voor uw visual `InteractivityService` wordt gebruikt, hoeft u geen extra acties te ondernemen voor ondersteuning van bladwijzers in uw visual.

Het hulpprogramma verwerkt de selectiestatus van de visual zodra de gebruiker bladwijzers selecteert.

### <a name="visuals-with-filter"></a>Visuals met filter

Stel dat de visual een filter van gegevens maakt op basis van datumbereik. We hebben dus `startDate` en `endDate` als begin- en eindpunt van het bereik.
De visual maakt een geavanceerd filter en roept de hostmethode `applyJsonFilter` aan om gegevens te filteren op de relevante voorwaarden.
De `target` is de tabel voor filtering.

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

Steeds wanneer een gebruiker op een bladwijzer klikt, wordt een `update`-aanroep naar de aangepaste visual verzonden.

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

Daarna moet de interne status van de visual worden gewijzigd (gegevenspunten en visualisatie-objecten zoals lijnen en rechthoeken) zodat de huidige voorwaarden worden weergegeven.

> [!IMPORTANT]
> In het scenario met rapportbladwijzers moet `applyJsonFilter` niet door de visual worden aangeroepen om andere visuals te filteren: deze worden al gefilterd door Power BI.

De visual Tijdlijn-slicer wijzigt de bereikkiezer in de overeenkomstige gegevensbereiken.

Zie de [opslagplaats voor tijdlijn-slicers](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df) voor meer informatie.

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>Filterstatus om visuele eigenschappen in bladwijzers op te slaan

Door de `filterState`-eigenschap wordt een eigenschap een onderdeel van het filterproces. In de visual kunnen verschillende waarden in bladwijzers worden opgeslagen.

Als u de eigenschapswaarde als filterstatus wilt opslaan, moet de objecteigenschap worden gemarkeerd als `"filterState": true` in `capabilities.json`.

Voorbeeld: met `Timeline Slicer` worden de eigenschapswaarden van `Granularity` opgeslagen in een filter. Het biedt ook de mogelijkheid om de huidige granulariteit voor het wijzigen van bladwijzers per gebruiker te wijzigen.

Zie de [opslagplaats voor tijdlijn-slicers](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334) voor meer informatie;
