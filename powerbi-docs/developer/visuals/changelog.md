---
title: wijzigingenlogboek voor API voor Power BI-visuals
description: In dit artikel worden de belangrijkste wijzigingen in verschillende versies van de API voor Power BI-visuals beschreven
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141061"
---
# <a name="power-bi-visuals-api-changelog"></a>wijzigingenlogboek voor API voor Power BI-visuals
Deze pagina bevat een beknopt overzicht van de verschillende API-versies. De hier vermelde versies worden als stabiel beschouwd en worden niet meer gewijzigd.

## <a name="api-v26"></a>API v2.6
  * Hiermee wordt **isInFocus** toegevoegd aan de optie update, en de methode **switchFocusModeState** aan visual host
  * Ondersteunt aanpassing van **subtotalen**

## <a name="api-v25"></a>API v2.5
  * Ondersteunt het **[deelvenster Analyse](./analytics-pane.md)**
  * Ondersteunt de methoden `SelectionIdBuilder` **withMatrixNode** en **withTable**
  * Ondersteunt niet langer de interface `DataRepetitionSelector`, vervangen door de interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v23"></a>API v2.3
  * **[API voor landingspagina](./landing-page.md)**
  * **[Lokale opslag-API](./local-storage.md)**
  * **[Tuple-filter-API (filter voor meerdere kolommen)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[Gebeurtenisweergave-API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API v2.2
  * Ondersteunt **[JSON-filters herstellen vanuit DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[Contextmenu-API](./context-menu.md)**

## <a name="api-v21"></a>API v2.1
  * Prestatieverbeteringen:
    * Snellere laadtijden
    * Kleinere geheugen-footprint
    * Geoptimaliseerde gegevens en gebeurtenistransacties  

**Releaseopmerkingen**
* Geherstructureerde filter-API's zijn beschikbaar in API 2.2 en worden niet ondersteund in API 2.1.
* Visuals ontvangen alleen het dataView-type dat in de mogelijkheden van de visual is gedeclareerd. Visuals waarin meerdere dataView-typen worden gebruikt, werken niet meer als gevolg van deze update.
* Ondersteunt niet langer de interface `DataViewScopeIdentity`, vervangen door de interface `data.DataRepetitionSelector`. Als u de sleuteleigenschap van de interface `DataViewScopeIdentity` hebt gebruikt, kunt u deze vervangen door `JSON.stringify(identity)`
* `undefined` wordt vervangen door `null` in de dataView. Bij herhaling via een matrix met `var item in myArray` wordt deze overslagen bij `undefined`, maar niet bij `null`. Visuals die gebruikmaken van dit patroon, werken mogelijk niet meer door deze update. Controleer of `null` voorkomt in matrices:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* De eigenschap `proto` slaat geen verborgen metagegevens\gegevens meer op in de dataView. Visuals met toegang tot eigenschappen via `proto` werken mogelijk niet meer door deze update.

## <a name="api-v113"></a>API v1.13
* Ondersteunt **[Slicers synchroniseren](./enable-sync-slicers.md)** . Dit werkt alleen voor slicers met één veld vanwege de huidige status van code in PBI. [Meer informatie](/power-bi/desktop-slicers).
* Toegankelijkheid: [Ondersteuning voor hoog contrast](./high-contrast-support.md) 
* Toegankelijkheid: Vlag Toetsenbordfocus toestaan

## <a name="api-v112"></a>API v1.12
* Ondersteunt thema's
* Ondersteunt **[fetchMoreData](./fetch-more-data.md)** . Merk op dat de **fetchMoreData-API** niet gebonden is aan de vaste limiet van 30.000 gegevenspunten
* **[Canvasknopinfo-API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API v1.11
* **[FilterManager-API](./filter-api.md)**
* Ondersteunt **[bladwijzers](./bookmarks-support.md)** 

## <a name="api-v110"></a>API v1.10
* Voegt `ILocalizationManager` toe
* **Verificatie-API**

## <a name="api-v19"></a>API v1.9
* **[launchUrl-API](./launch-url.md)**

## <a name="api-v18"></a>API v1.8
* Ondersteunt het nieuwe type **fillRule** (kleurovergang) in het mogelijkhedenschema
* Ondersteunt de eigenschap **rule** (regel) in het mogelijkhedenschema voor objecteigenschappen

## <a name="api-v17"></a>API v1.7
* Ondersteunt **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Ondersteunt de **[bewerkingsmodus](./advanced-edit-mode.md)** om te kunnen overschakelen naar de bewerkingsmodus in een visual
* Ondersteunt **[Interactieve (HTML) R Power BI-visuals](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , op basis van HTML

## <a name="api-v150"></a>API v1.5.0
* Ondersteunt **[Interacties toestaan](./visuals-interactions.md)** voor interactie tussen visuals

## <a name="api-v140"></a>API v1.4.0
* Ondersteunt **[lokalisatie](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Ondersteunt **[knopinfo](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Voegt **colorPalette** toe voor het beheren van de kleuren die in uw visual worden gebruikt.
* Ondersteunt **meervoudige selectie**: in selectionManager kan een matrix van `SelectionId` worden geaccepteerd.
* Ondersteunt **[R-visuals](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** met R-scripts

## <a name="api-v110"></a>API v1.1.0
* Ondersteunt foutopsporing voor visuals in iFrame
* Voegt een lichtgewicht sandbox met snellere initialisatie van het iFrame toe
* Lost het probleem [Capabilities.objects does not support "text" type](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12) (Capabilities.objects ondersteunt het type "text" niet) op
* Ondersteunt `pbiviz update` voor het bijwerken van de definities en het schema van API-typen voor visuals
* Ondersteunt de vlag `--api-version` in `pbiviz new` voor het maken van visuals met een specifieke API-versie
* Ondersteunt de alpha-release van API v1.2.0

**Visual-host**
* Voegt **createSelectionIdBuilder** toe voor het maken van unieke id's die worden gebruikt voor gegevensselectie
* Voegt **createSelectionManager** toe om de selectiestatus van de visual te beheren en geeft wijzigingen door aan de visual-host
* Voegt een matrix met standaard**kleuren** toe voor gebruik in visuals

## <a name="api-v100"></a>API v1.0.0
* Eerste release van de API