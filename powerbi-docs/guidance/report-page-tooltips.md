---
title: Visuals uitbreiden met Knopinfo rapportpagina
description: Richtlijnen voor het werken met knopinfo voor rapportpagina's.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 5a6b7bda8bf5e8d80ae8b22a71035f8bc362fb89
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377737"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>Visuals uitbreiden met Knopinfo rapportpagina

Dit artikel is bedoeld voor u wanneer u als auteur Power BI-rapporten gaat ontwerpen. U vindt hier suggesties en aanbevelingen voor het maken van [knopinfo voor rapportpagina's](../desktop-tooltips.md).

## <a name="suggestions"></a>Suggesties

Met behulp van knopinfo voor rapportpagina's kunt u uw rapportgebruikers een betere ervaring bieden. Uw rapportgebruikers kunnen knopinfo voor pagina's gebruiken om snel en efficiënt meer inzicht te krijgen op basis van een visual. Ze kunnen aan verschillende rapportobjecten worden gekoppeld:

- **Visuals:** Per visual kunt u configureren bij welke visuals de knopinfo voor de pagina moet worden weergegeven. Ook is het per visual mogelijk om geen knopinfo weer te geven, standaard knopinfo voor visuals weer te geven (dit wordt geconfigureerd in het deelvenster met velden voor visuals) of specifieke knopinfo voor de pagina weer te geven.
- **Visualheaders:** U kunt configureren dat bij specifieke visuals knopinfo voor de pagina moet worden weergegeven. Uw rapportgebruikers kunnen de knopinfo voor de pagina zien wanneer ze met de cursor boven het pictogram van de visualheader bewegen. Informeer uw gebruikers over dit pictogram.

> [!NOTE]
> In een rapportvisual kan knopinfo voor de pagina alleen worden weergegeven wanneer filters voor knopinfo compatibel zijn met het ontwerp van de visual. Een visual waarbij items op _product_ worden gegroepeerd is bijvoorbeeld compatibel met knopinfo voor een pagina waarop wordt gefilterd op _product_.
>
> Interactiviteit wordt niet door knopinfo voor een pagina ondersteund. Als u ervoor wilt zorgen dat uw rapportgebruikers interactief met het rapport kunnen werken, maakt u in plaats daarvan een [drillthrough-pagina](../desktop-drillthrough.md).
>
> Knopinfo voor een pagina wordt niet door Power BI-visuals ondersteund.

Hier ziet u een aantal aanbevolen ontwerpscenario's:

- [Een ander perspectief](#different-perspective)
- [Details toevoegen](#add-detail)
- [Hulp toevoegen](#add-help)

### <a name="different-perspective"></a>Een ander perspectief

Met knopinfo voor een pagina kunt u dezelfde gegevens als van de bronvisual weergeven. Hiervoor gebruikt u dezelfde visual en draaigroepen, of verschillende visualtypen. Voor knopinfo voor een pagina kunnen ook andere filters worden toegepast dan de filters die op de bronvisual zijn toegepast.

In het volgende voorbeeld ziet u wat er gebeurt wanneer de rapportgebruiker de cursor boven de waarde **EnabledUsers** beweegt. De filtercontext voor de waarde is Yammer in november 2018.

![In een matrixvisual wordt een raster weergegeven met waarden die op jaar en maand in de rijen zijn gegroepeerd. De rapportgebruiker heeft de cursor over één waarde bewogen. Er wordt knopinfo voor de pagina weergegeven.](media/report-page-tooltips/suggestion-different-perspective.png)

Er wordt knopinfo voor de pagina weergegeven. Hierin ziet u een andere gegevensvisual (lijndiagram en gegroepeerd kolomdiagram) en wordt een contrasterend tijdfilter toegepast. U ziet dat de filtercontext voor het gegevenspunt november 2018 is. Toch wordt bij de knopinfo voor de pagina de trend over _een heel jaar aan maanden_ weergegeven.

### <a name="add-detail"></a>Details toevoegen

In knopinfo voor een pagina kunnen extra details worden weergegeven en kan meer context worden toegevoegd.

In het volgende voorbeeld ziet u wat er gebeurt wanneer de rapportgebruiker de cursor boven de waarde **Gemiddeld aantal schendingspunten** beweegt, voor de postcode 98022.

![In een tabelvisual wordt een raster met waarden weergegeven. De tabel bevat drie kolommen. Er wordt knopinfo voor de pagina weergegeven.](media/report-page-tooltips/suggestion-add-details.png)

Er wordt knopinfo voor de pagina weergegeven. Voor de postcode 98022 worden specifieke kenmerken en statistieken weergegeven.

### <a name="add-help"></a>Hulp toevoegen

Visualheaders kunnen zo worden geconfigureerd dat er knopinfo voor de pagina wordt weergegeven in visualheaders. U kunt Help-documentatie aan knopinfo voor de pagina toevoegen met behulp van tekstvakken met opmaak. Ook is het mogelijk om afbeeldingen en vormen toe te voegen.

Wist u dat op knoppen, afbeeldingen, tekstvakken en vormen ook knopinfo voor de pagina in een visualheaders kan worden weergegeven?

In het volgende voorbeeld ziet u wat er gebeurt wanneer de rapportgebruiker de cursor boven het [pictogram van de visualheader](../desktop-visual-elements-for-reports.md) beweegt.

![Een rapportgebruiker heeft de cursor boven het pictogram van de visualheader (het vraagtekenpictogram) bewogen. Er wordt knopinfo met opmaak weergegeven.](media/report-page-tooltips/suggestion-add-help.png)

Er wordt knopinfo voor de pagina weergegeven. Er wordt opgemaakte tekst weergegeven in vier tekstvakken, en een vorm (lijn). De knopinfo voor de pagina biedt ondersteuning door een beschrijving te geven van elk acroniem dat in de visual wordt weergegeven.

## <a name="recommendations"></a>Aanbevelingen

Tijdens het ontwerpen van een rapport worden de volgende werkwijzen aangeraden:

- **Paginagrootte:** Configureer de knopinfo voor de pagina zodanig dat deze klein is. U kunt de opgebouwde optie **Knopinfo** gebruiken (320 pixels breed, 240 pixels hoog). Of u kunt aangepaste afmetingen instellen. Zorg ervoor dat u geen paginaformaat gebruikt dat te groot is: hierdoor zijn de visuals op de bronpagina mogelijk niet meer zichtbaar.
- **Paginaweergave:** In het rapportontwerpprogramma stelt u de paginaweergave in op **Ware grootte** (de paginaweergave wordt standaard ingesteld op **Aan pagina aanpassen**). Op deze manier ziet u tijdens het ontwerpen de ware grootte van de knopinfo voor de pagina.
- **Stijl:** Ontwerp uw knopinfo voor de pagina zodanig dat hiervoor hetzelfde thema en dezelfde stijl als voor het rapport worden gebruikt. Op deze manier hebben gebruikers het idee dat ze hetzelfde rapport voor zich hebben. Of ontwerp een aanvullende stijl voor uw knopinfo en zorg ervoor dat u deze stijl op alle knopinfo voor de pagina toepast.
- **Knopinfo-filters:** Wijs filters aan de knopinfo voor de pagina toe zodat u tijdens het ontwerpen een voorbeeld van een realistisch resultaat kunt bekijken. Vergeet deze filters niet te verwijderen voordat u uw rapport publiceert.
- **Zichtbaarheid pagina:** Verberg altijd pagina's met knopinfo: gebruikers hoeven hier niet rechtstreeks naar te navigeren.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Knopinfo maken op basis van rapportpagina's in Power BI Desktop](../desktop-tooltips.md)
- [Knopinfo in Power BI Desktop aanpassen](../desktop-custom-tooltips.md)
- [Power BI-rapporten verbeteren met visuele elementen](../desktop-visual-elements-for-reports.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
