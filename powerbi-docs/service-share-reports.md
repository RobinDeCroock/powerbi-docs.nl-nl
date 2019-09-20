---
title: Twee manieren om een gefilterd Power BI-rapport te delen
description: Informatie over twee manieren om een Power BI-rapport te filteren en dit met collega's binnen uw organisatie te delen.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c5bc8b32ae61870b794875c1d1720cd07dcf97f8
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877707"
---
# <a name="two-ways-to-share-a-filtered-power-bi-report"></a>Twee manieren om een gefilterd Power BI-rapport te delen
*Delen* is een goede manier om enkele personen toegang te geven tot uw dashboards en rapporten. Wat gebeurt er als u een gefilterde versie van een rapport wilt delen? Dit kan bijvoorbeeld een rapport zijn dat alleen gegevens weergeeft voor een specifieke stad of verkoper of jaar. Probeer een rapport te filteren en te delen of een aangepaste URL te maken. Het rapport wordt gefilterd zodra een ontvanger dit voor de eerste keer opent. Ze kunnen het filter verwijderen door de URL aan te passen. 

![Gefilterd rapport](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI ondersteunt ook [andere manieren om samen te werken en rapporten te distribueren](service-how-to-collaborate-distribute-dashboards-reports.md). Als u wilt gaan delen, moeten u en de ontvangers een [Power BI Pro licentie](service-features-license-type.md) hebben, of de inhoud moet zich in een [Premium-capaciteit](service-premium-what-is.md) bevinden. 

## <a name="two-ways-to-filter-a-report"></a>Twee manieren om een rapport te filteren

Voor beide filtertechnieken wordt de voorbeeldsjabloon-app Marketing en Sales gebruikt. Wilt u het proberen? U kunt ook de [voorbeeldsjabloon-app Marketing en Sales](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview) installeren.

### <a name="set-a-filter"></a>Filter instellen

Open een rapport in de [bewerkingsweergave](consumer/end-user-reading-view.md) en pas een filter toe.

In dit voorbeeld filteren we de pagina JTD-categorie van de voorbeeldsjabloon-app Marketing en Sales, zodat alleen waarden worden weergegeven waarbij **Regio** gelijk is aan **Centraal**. 
 
![Deelvenster Rapportfilter](media/service-share-reports/power-bi-share-report-filter.png)

Sla het rapport op.

### <a name="create-a-filter-in-the-url"></a>Een filter in de URL maken

Wanneer u het filter aan het einde van de URL van de rapportpagina toevoegt, is het gedrag iets anders. De gefilterde pagina ziet er hetzelfde uit. Power BI voegt het filter echter toe aan het hele rapport en verwijdert de andere waarden uit het filtervenster.  

Voeg het volgende toe aan het einde van de URL van de rapportpagina:
   
    ?filter=*tablename*/*fieldname* eq *value*
   
Het veld moet van het type getal, datum/tijd of reeks zijn. De waarden *tablename* of *fieldname* mogen geen spaties bevatten.
   
In ons voorbeeld is de naam van de tabel **Geo**, de naam van het veld **Regio** en de waarde waarop we willen filteren is **Centraal**:
   
    ?filter=Geo/Region eq 'Central'

De browser voegt speciale tekens toe om slashes, spaties en apostrofs weer te geven, zodat het uiteindelijke resultaat weergegeven wordt als:
   
    app.powerbi.com/groups/xxxx/reports/xxxx/ReportSection4d00c3887644123e310e?filter=Geo~2FRegion%20eq%20'Central'

![Rapport met URL-filter](media/service-share-reports/power-bi-share-report-filter-url.png)

Sla het rapport op.

Zie het artikel [Een rapport filteren door queryreeksparameters in de URL te gebruiken](service-url-filters.md) voor meer informatie.

## <a name="share-the-filtered-report"></a>Het gefilterde rapport delen

1. Als u [het rapport deelt](service-share-dashboards.md), schakelt u het selectievakje **E-mailmelding verzenden naar ontvanger** uit.

    ![Het dialoogvenster Rapport delen](media/service-share-reports/power-bi-share-report-dialog.png)

4. Verzend de koppeling met het filter dat u eerder hebt gemaakt.

## <a name="next-steps"></a>Volgende stappen
* [Manieren om uw werk te delen in Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Een dashboard delen](service-share-dashboards.md)
* Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/).
* Wilt u feedback geven? Dit kan op de [site van de Power BI-community](https://community.powerbi.com/).

