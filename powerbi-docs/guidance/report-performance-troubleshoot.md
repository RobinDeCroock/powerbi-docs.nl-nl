---
title: Problemen met rapportprestaties in Power BI oplossen
description: Probleemoplossingsgids voor het diagnosticeren van slechte rapportprestaties in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: a5230a39706ce5d6941c00386160fe10114442e1
ms.sourcegitcommit: 5ece366fceee9832724dae40eacf8755e1d85b04
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81527986"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Problemen met rapportprestaties in Power BI oplossen

Dit artikel bevat richtlijnen waarmee ontwikkelaars en beheerders problemen met rapportprestaties kunnen oplossen. Het artikel is van toepassing op Power BI-rapporten en gepagineerde Power BI-rapporten.

Trage rapporten kunnen worden geïdentificeerd door rapportgebruikers die te maken krijgen met rapporten die langzaam worden geladen of die langzaam worden bijgewerkt bij interactie met slicers of andere functies. Wanneer rapporten worden gehost op basis van Premium-capaciteit, kunnen langzame rapporten ook worden geïdentificeerd met de [Power BI Premium Metrics-app](../service-admin-premium-monitor-capacity.md). Met deze app kunt u de status en capaciteit van uw Power BI Premium-abonnement bewaken.

## <a name="follow-flowchart-steps"></a>De stappen in het stroomdiagram volgen

Gebruik het volgende stroomdiagram om inzicht te krijgen in de oorzaak van trage prestaties en om te bepalen welke actie moet worden ondernomen.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Afbeelding met het stroomdiagram dat uitgebreid in het artikel wordt beschreven." border="true":::

Er zijn zes stroomdiagramafsluiters die elk beschrijven welke actie moet worden uitgevoerd:

|Afsluiter|Actie(s)|
|---------|---------|
|![Stroomdiagramafsluiter 1.](media/common/icon-01-red-30x30.png)|Capaciteit beheren<br />Schaal van capaciteit aanpassen |
|![Stroomdiagramafsluiter 2.](media/common/icon-02-red-30x30.png)|Capaciteitsactiviteiten onderzoeken tijdens normaal rapportgebruik|
|![Stroomdiagramafsluiter 3.](media/common/icon-03-red-30x30.png)|Architectuurwijziging<br />Azure Analysis Services overwegen<br />On-premises gateway controleren|
|![Stroomdiagramafsluiter 4.](media/common/icon-04-red-30x30.png)|Azure Analysis Services overwegen<br />Power BI Premium overwegen|
|![Stroomdiagramafsluiter 5.](media/common/icon-05-red-30x30.png)|Power BI Desktop Performance Analyzer gebruiken<br />Rapport, model of DAX optimaliseren|
|![Stroomdiagramafsluiter 6.](media/common/icon-06-red-30x30.png)|Ondersteuningsticket indienen|

## <a name="take-action"></a>Actie ondernemen

Eerst moet worden beoordeeld of het trage rapport wordt gehost op een Premium-capaciteit.

### <a name="premium-capacity"></a>Premium-capaciteit

Wanneer het rapport wordt gehost op een Premium-capaciteit, gebruikt u de **Power BI Premium Metrics-app** om te bepalen of de rapporthostingcapaciteit regelmatig groter is dan de capaciteitsresources. Dit is het geval voor de CPU wanneer deze regelmatig hoger is dan 80%. Voor het geheugen is dit het geval wanneer het [cijfer voor het actieve geheugen](../service-premium-metrics-app.md#the-active-memory-metric) groter is dan 50. Wanneer resources onder druk staan, kan het tijd zijn [de capaciteit te beheren of te schalen](../service-admin-premium-manage.md) (stroomdiagramafsluiter 1). Als er voldoende resources zijn, onderzoekt u de capaciteitsactiviteiten tijdens normaal rapportgebruik (stroomdiagramafsluiter 2).

### <a name="shared-capacity"></a>Gedeelde capaciteit

Wanneer het rapport wordt gehost op gedeelde capaciteit, is het niet mogelijk de status van de capaciteit te bewaken. U moet dan gebruikmaken van een andere onderzoeksmethode.

Bepaal eerst of er sprake is van trage prestaties op specifieke tijdstippen van de dag of maand. Als dit het geval is en het rapport op deze tijdstippen door veel gebruikers wordt geopend, hebt u twee mogelijkheden:

- Verhoog de querydoorvoer door de gegevensset te migreren naar [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) of een Premium-capaciteit (stroomdiagramafsluiter 4).
- Gebruik Power BI Desktop [Performance Analyzer](../desktop-performance-analyzer.md) om te zien hoe het gaat met elk van de rapportelementen, zoals visuals en DAX-formules. Het is vooral handig om te bepalen of het de query of de visualweergave is die bijdraagt aan prestatieproblemen (stroomdiagramafsluiter 5).

Als u vaststelt dat er geen tijdspatroon is, gaat u na of de trage prestaties zijn beperkt tot een specifiek gebied of een bepaalde regio. Als dat het geval is, is het waarschijnlijk dat er sprake is van een gegevensbron op afstand en een langzame netwerkcommunicatie. In dit geval kunt u het volgende doen:

- Architectuur wijzigen met behulp van [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (stroomdiagramafsluiter 3).
- [On-premises gegevensgateway](/data-integration/gateway/service-gateway-performance) optimaliseren (stroomdiagramafsluiter 3).

Als u vaststelt dat er geen tijdspatroon is _en_ dat er in alle regio's sprake is van trage prestaties, onderzoekt u of de trage prestaties zich voordoen bij specifieke apparaten, clients of webbrowsers. Als dat niet zo is, gebruikt u Power BI Desktop [Performance Analyzer](../desktop-performance-analyzer.md), zoals eerder is beschreven, om het rapport of model te optimaliseren (stroomdiagramafsluiter 5).

Wanneer u bepaalt dat specifieke apparaten, clients of webbrowsers bijdragen aan trage prestaties, wordt u aangeraden een ondersteuningsticket te maken via de [pagina Power BI-ondersteuning](https://powerbi.microsoft.com/support/) (stroomdiagramafsluiter 6).

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Power BI-richtlijnen](index.yml)
- [Rapportprestaties bewaken](monitor-report-performance.md)
- [Performance Analyzer](../desktop-performance-analyzer.md)
- Technisch document: [Een Power BI Enterprise-implementatie plannen](https://go.microsoft.com/fwlink/?linkid=2057861)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
