---
title: Hoge beschikbaarheid, failover in Power BI en veelgestelde vragen over herstel na noodgevallen
description: Begrijpen hoe Power BI-service zijn gebruikers een hoge beschikbaarheid, bedrijfscontinuïteit en herstel na noodgevallen biedt.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 24867d231cca0135c09119f4b885b393cb2b8dd8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699056"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Hoge beschikbaarheid, failover in Power BI en veelgestelde vragen over herstel na noodgevallen

In dit artikel wordt uitgelegd hoe Power BI-service zijn gebruikers een hoge beschikbaarheid, bedrijfscontinuïteit en herstel na noodgevallen biedt. Na het lezen van dit artikel hebt u een beter beeld van hoe hoge beschikbaarheid wordt bereikt, onder welke omstandigheden Power BI een failover uitvoert en wat u kunt verwachten van de service wanneer een failover-overschakeling wordt uitgevoerd.

## <a name="what-does-high-availability-mean-for-power-bi"></a>Wat betekent 'hoge beschikbaarheid' voor Power BI?

Power BI is volledig beheerde Software as a Service (SaaS).  Het ontwerp en de werking zijn zodanig uitgevoerd door Microsoft dat deze tolerant zijn voor infrastructuurstoringen, zodat gebruikers altijd toegang tot hun rapporten hebben.  De service wordt ondersteund door een [SLA van 99,9%](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37).

## <a name="what-is-a-power-bi-failover"></a>Wat is een Power BI-failover?

Power BI houdt meerdere exemplaren van elk onderdeel aan in Azure-datacenters (ook wel bekend als regio's) om bedrijfscontinuïteit te garanderen. Als er een storing of een probleem is die/dat ervoor zorgt dat Power BI niet toegankelijk of onbruikbaar wordt in een regio, wordt in Power BI een failover-overschakeling uitgevoerd van alle bijbehorende onderdelen in die regio naar een back-upexemplaar. De failover herstelt de beschikbaarheid en operabiliteit van het Power BI-service-exemplaar in een nieuwe regio (meestal binnen dezelfde geografische locatie, zoals is aangegeven in de [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)).

Een Power BI-service-exemplaar waarvoor een failover-overschakeling is uitgevoerd, ondersteunt alleen _leesbewerkingen_, wat betekent dat de volgende bewerkingen niet worden ondersteund tijdens de failover: vernieuwingen, rapportpublicaties, wijzigingen aan dashboards of rapporten en andere bewerkingen waarvoor wijzigingen in Power BI-metagegevens nodig zijn (bijvoorbeeld een opmerking invoegen in een rapport).  Leesbewerkingen, zoals het weergeven van dashboards en van rapporten (die niet zijn gebaseerd op DirectQuery of een liveverbinding met on-premises gegevensbronnen gebruiken), blijven correct werken.

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>Hoe blijven back-upexemplaren gesynchroniseerd met mijn gegevens?

Alle onderdelen van Power BI-service worden regelmatig gesynchroniseerd met hun back-upexemplaren. We richten op een synchronisatie van 15 minuten op een bepaald tijdstip voor alle inhoud die is geüpload naar of is gewijzigd in Power BI. In het geval van een failover maakt Power BI gebruik van [geografisch redundante replicatie in Azure Storage](/azure/storage/common/storage-redundancy-grs) en [geografisch redundante replicatie in Azure SQL](/azure/sql-database/sql-database-active-geo-replication) om te waarborgen dat er back-exemplaren aanwezig zijn in andere regio's en dat deze kunnen worden gebruikt in het geval van een failover.

## <a name="where-are-the-failover-clusters-located"></a>Waar bevinden de failover-clusters zich?

Back-upexemplaren bevinden zich binnen dezelfde geografische locatie (geografisch) als die u hebt geselecteerd toen uw organisatie zich registreerde voor Power BI, tenzij anders is aangegeven de [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Een geografisch gebied kan meerdere regio's bevatten en Microsoft kan gegevens repliceren naar een van de regio's binnen een bepaald geografisch gebied voor gegevenstolerantie. Microsoft zal geen klantgegevens repliceren of verplaatsen buiten het geografische gebied. Zie het [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) voor een afbeelding van de geografische gebieden die worden aangeboden door Power BI en de regio's erbinnen.

## <a name="how-does-microsoft-decide-to-failover"></a>Hoe bepaalt Microsoft dat een failover moet worden uitgevoerd?

Er zijn twee verschillende systemen die aangeven wanneer een failover mogelijk is vereist:

- Onze externe en interne bewakingstests duiden op een gebrek aan beschikbaarheid of een onvermogen om correct te functioneren. Dergelijke aanduidingen kunnen zijn gebaseerd op uitval die is gedetecteerd in Power BI-onderdelen of een of meer services waarvan Power BI afhankelijk is in een regio.
- Het centrale operationele team van Microsoft Azure informeert ons over een kritieke storing in een regio.

In beide gevallen nemen leidinggevende Power BI-teamleden de beslissing om een failover uit te voeren; de beslissing zelf is niet automatisch. Zodra de beslissing is genomen,vindt de failover-overschakeling automatisch plaats.

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Hoe kan ik weten dat Power BI zich nu in de failovermodus bevindt?

Er wordt een melding geplaatst op de Power BI-ondersteuningspagina ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)). De melding omvat de primaire bewerkingen die niet beschikbaar zijn tijdens de failover, zoals publiceren, vernieuwen, dashboards maken, dashboards dupliceren en wijzigingen in de machtigingen.

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Hoe lang duurt een door Power BI uitgevoerde failover?

Zodra is besloten om een failover uit te voeren, kan het tot 60 minuten duren voor een failover-exemplaar beschikbaar komt.

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>Wanneer keert mijn Power BI-exemplaar terug naar de oorspronkelijke regio?

Power BI-service-exemplaren keren terug naar hun oorspronkelijke regio wanneer het probleem dat de failover heeft veroorzaakt, is opgelost. Raadpleeg de ondersteuningspagina van Power BI: Als het probleem is opgelost, verwijdert het Power BI-team de melding dat de failover beschrijft. Op dat moment dient de werking weer normaal te zijn geworden.

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>Ben ik verantwoordelijk voor de beschikbaarheid van mijn Power BI-oplossing?

Als de Power BI-oplossing die in uw organisatie wordt gebruikt op een van de volgende elementen betrekking heeft, moet u enkele maatregelen nemen om te waarborgen dat de oplossing een hoge beschikbaarheid behoudt:

- Als uw organisatie gebruikmaakt van Power BI Premium, moet u ervoor zorgen dat de Premium-capaciteit zodanig is dat aan de belastingsvereisten van uw implementatie is voldaan.  De [Power BI Premium-whitepaper voor planning en implementatie](https://aka.ms/Premium-Capacity-Planning-Deployment) en de [Power BI Premium Capacity Metrics-app](service-admin-premium-monitor-capacity.md) kunnen u helpen een planning voor dit vereiste te maken en eraan te voldoen. Er worden ter ondersteuning regelmatig nieuwe functies toegevoegd aan de app voor metrische gegevens en de beheerportal in Power BI.
- Als uw organisatie on-premises gegevensbronnen opent met behulp van de on-premises gateway van Power BI, moet u de gateway instellen [zoals is beschreven in dit artikel](/data-integration/gateway/service-gateway-high-availability-clusters) om hoge beschikbaarheid te ondersteunen. Volg deze richtlijn, of u nu rapporten aan het vernieuwen bent in de importmodus of gegevens of gegevensmodellen opent met behulp van DirectQuery of Live Connect.

## <a name="will-gateways-function-when-in-failover-mode"></a>Werken gateways in de failover-modus?

Nee. Gegevens die nodig zijn vanuit on-premises gegevensbronnen (alle rapporten en dashboards op basis van DirectQuery en liveverbindingen) werken niet tijdens een failover. De configuratie van de gateway wordt echter niet gewijzigd: Wanneer het exemplaar van Power BI in de oorspronkelijke staat terugkeert, herkrijgen de gateways weer hun normale functies.
