---
title: Wijzigingenlogboek voor de API voor Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel worden de belangrijkste wijzigingen in verschillende versies van de API voor Power BI-visuals beschreven. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: 4ed42f8c9c3acf740b68bf6c28aaa201efb0d5ba
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2021
ms.locfileid: "97927130"
---
# <a name="power-bi-visuals-api-changelog"></a>wijzigingenlogboek voor API voor Power BI-visuals
Deze pagina bevat een beknopt overzicht van de verschillende API-versies. De hier vermelde versies worden als stabiel beschouwd en worden niet meer gewijzigd.


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData` : nieuwe `aggregateSegments`-parameter (standaard true), ter ondersteuning van fetchMoreData zonder aggregatie

## <a name="api-v320"></a>API v3.2.0
  * Ondersteunt **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Hiermee wordt **isInFocus** toegevoegd aan de optie update, en de methode **switchFocusModeState** aan visual host
  * Ondersteunt aanpassing van **subtotalen**

## <a name="api-v250"></a>API v2.5.0
  * Ondersteunt het **[deelvenster Analyse](./analytics-pane.md)**
  * Ondersteunt de methoden `SelectionIdBuilder` **withMatrixNode** en **withTable**
  * Ondersteunt niet langer de interface `DataRepetitionSelector`, vervangen door de interface `data.CustomVisualOpaqueIdentity`

## <a name="api-v230"></a>API v2.3.0
  * **[API voor landingspagina](./landing-page.md)**
  * **[Lokale opslag-API](./local-storage.md)**
  * **[Tuple-filter-API (filter voor meerdere kolommen)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[Gebeurtenisweergave-API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Ondersteunt **[JSON-filters herstellen vanuit DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[Contextmenu-API](./context-menu.md)**
  * Biedt ondersteuning voor de functie **[Analyseren](../../create-reports/desktop-drillthrough.md)**

## <a name="api-v210"></a>API v2.1.0
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

## <a name="api-v1130"></a>API v1.13.0
* Ondersteunt **[Slicers synchroniseren](./enable-sync-slicers.md)** . Dit werkt alleen voor slicers met één veld vanwege de huidige status van code in PBI. [Meer informatie](../../visuals/power-bi-visualization-slicers.md).
* Toegankelijkheid: [Ondersteuning voor hoog contrast](./high-contrast-support.md) 
* Toegankelijkheid: Vlag Toetsenbordfocus toestaan

## <a name="api-v1120"></a>API v1.12.0
* Ondersteunt thema's
* Ondersteunt **[fetchMoreData](./fetch-more-data.md)** . Merk op dat de **fetchMoreData-API** niet gebonden is aan de vaste limiet van 30.000 gegevenspunten
* **[Canvasknopinfo-API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[FilterManager-API](./filter-api.md)**
* Ondersteunt **[bladwijzers](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* Voegt `ILocalizationManager` toe
* **Verificatie-API**

## <a name="api-v190"></a>API v1.9.0
* **[launchUrl-API](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Ondersteunt het nieuwe type **fillRule** (kleurovergang) in het mogelijkhedenschema
* Ondersteunt de eigenschap **rule** (regel) in het mogelijkhedenschema voor objecteigenschappen

## <a name="api-v170"></a>API v1.7.0
* Ondersteunt **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Ondersteunt de **[bewerkingsmodus](./advanced-edit-mode.md)** om te kunnen overschakelen naar de bewerkingsmodus in een visual
* Ondersteunt **[Interactieve (HTML) R Power BI-visuals](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** , op basis van HTML

## <a name="api-v150"></a>API v1.5.0
* Ondersteunt **[Interacties toestaan](./visuals-interactions.md)** voor interactie tussen visuals

## <a name="api-v140"></a>API v1.4.0
* Ondersteunt **[lokalisatie](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Ondersteunt **[knopinfo](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Voegt **colorPalette** toe voor het beheren van de kleuren die in uw visual worden gebruikt.
* Ondersteunt **meervoudige selectie**: in selectionManager kan een matrix van `SelectionId` worden geaccepteerd.
* Ondersteunt **[R-visuals](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** met R-scripts

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
* Voegt een matrix met standaard **kleuren** toe voor gebruik in visuals

## <a name="api-v100"></a>API v1.0.0
* Eerste release van de API
