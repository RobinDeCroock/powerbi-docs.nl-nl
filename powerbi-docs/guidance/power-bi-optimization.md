---
title: Optimalisatiegids voor Power BI
description: Optimalisatiegids voor Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: f189ea2944f86a3caabfbc51ae5b2887bc7c89bb
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83278602"
---
# <a name="optimization-guide-for-power-bi"></a>Optimalisatiegids voor Power BI

Dit artikel bevat richtlijnen waarmee ontwikkelaars en beheerders geoptimaliseerde Power BI-oplossingen kunnen maken en onderhouden. U kunt uw oplossing optimaliseren in verschillende architectuurlagen. Voorbeelden van deze lagen zijn:

- De gegevensbron(nen)
- Het gegevensmodel
- Visualisaties, inclusief dashboards, Power BI-rapporten en gepagineerde rapporten in Power BI
- De omgeving, inclusief capaciteiten, gegevensgateways en het netwerk

## <a name="optimizing-the-data-model"></a>Het gegevensmodel optimaliseren

Het gegevensmodel biedt ondersteuning voor de hele visualisatie-ervaring. Gegevensmodellen worden extern gehost of intern gehost. In Power BI worden ze _gegevenssets_ genoemd. Het is belangrijk om uw opties te begrijpen en om het juiste type gegevensset voor uw oplossing te kiezen. Er zijn drie gegevenssetmodi: Import, DirectQuery en Samengesteld. Zie [Gegevenssets in de Power BI-service](../connect-data/service-datasets-understand.md) en [Gegevenssetmodi in de Power BI-service](../connect-data/service-dataset-modes-understand.md) voor meer informatie.

Zie voor specifieke richtlijnen voor de gegevenssetmodus:

- [Gegevensreductietechnieken voor het importeren van modellen](import-modeling-data-reduction.md)
- [Richtlijnen voor het DirectQuery-model in Power BI Desktop](directquery-model-guidance.md)
- [Richtlijnen voor samengestelde modellen in Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Visualisaties optimaliseren

Power BI-visualisaties kunnen dashboards, Power BI-rapporten en gepagineerde rapporten in Power BI zijn. Elk van deze opties heeft een andere architectuur, en daarom ook eigen richtlijnen. 

### <a name="dashboards"></a>Dashboards

Het is belang rijk om te begrijpen dat in Power BI een cache wordt bijgehouden voor uw dashboardtegels, met uitzondering van tegels voor liverapporten en voor streams. Zie [Gegevens vernieuwen in Power BI (tegels vernieuwen)](../connect-data/refresh-data.md#tile-refresh) voor meer informatie. Als voor uw gegevensset dynamische [RLS (beveiliging op rijniveau)](../admin/service-admin-rls.md) wordt afgedwongen, moet u de gevolgen voor de prestaties goed kennen, omdat tegels op gebruikersbasis in de cache worden geplaatst.

Wanneer u liverapporttegels vastmaakt aan een dashboard, worden deze niet bediend vanuit de querycache. In plaats hiervan gedragen ze zich als rapporten en voeren ze tussendoor query's uit naar back-endkernen.

Zoals de naam al aangeeft, zorgt het ophalen van de gegevens uit de cache voor betere en consistentere prestaties dan wanneer u vertrouwt op de gegevensbron. Een manier om te profiteren van deze functionaliteit is door dashboards in te stellen als startpagina voor uw gebruikers. Maak veelgebruikte en vaak opgevraagde visuals vast aan de dashboards. Op deze manier worden dashboards een waardevolle 'eerste verdedigingslinie' die consistente prestaties bieden met minder belasting van de capaciteit. Gebruikers kunnen nog steeds doorklikken naar een rapport om de details te analyseren.

Voor DirectQuery en liveverbindingen met gegevenssets wordt de cache periodiek bijgewerkt door een query uit te voeren op de gegevensbron. Dit vindt standaard elk uur plaats, maar u kunt een andere frequentie configureren in de instellingen voor de gegevensset. Via elke update van de cache worden query's naar de onderliggende gegevensbron verzonden om de cache bij te werken. Het aantal query's dat wordt gegenereerd, is afhankelijk van het aantal visuals dat is vastgemaakt aan dashboards die afhankelijk zijn van de gegevensbron. U ziet dat als beveiliging op rijniveau is ingeschakeld, er query's worden gegenereerd voor elke andere beveiligingscontext. Bedenk, bijvoorbeeld, dat er twee verschillende rollen zijn die uw gebruikers categoriseren, en dat deze twee verschillende weergaven van de gegevens opleveren. Tijdens het vernieuwen van de querycache, worden in Power BI twee sets query’s gegenereerd.

### <a name="power-bi-reports"></a>Power BI-rapporten

Er zijn verschillende aanbevelingen voor het optimaliseren van ontwerpen voor Power BI-rapporten.

> [!NOTE]
> Zie [Richtlijnen voor DirectQuery-modellen in Power BI Desktop (ontwerpen voor rapporten optimaliseren)](directquery-model-guidance.md#optimize-report-designs) als rapporten zijn gebaseerd op een DirectQuery-gegevensset, voor extra optimalisaties van ontwerpen voor rapporten.

#### <a name="apply-the-most-restrictive-filters"></a>Pas de meest beperkende filters toe

Hoe meer gegevens via een visual moeten worden weergegeven, des te langzamer de visual wordt geladen. Hoewel dit principe duidelijk lijkt, kan het gemakkelijk worden vergeten. Voorbeeld: stel u eens voor dat u een grote gegevensset hebt. Op basis van deze gegevensset stelt u een rapport samen met een tabel. Eindgebruikers gebruiken slicers op de pagina om de gewenste rijen weer te geven. Doorgaans zijn ze slechts in enkele tientallen rijen geïnteresseerd.

Vaak wordt de fout gemaakt dat de standaardweergave van de tabel niet wordt gefilterd, waardoor alle meer dan 100 miljoen rijen worden weergegeven. De gegevens voor deze rijen worden in het geheugen geladen en bij elke vernieuwing gedecomprimeerd. Deze verwerking eist heel veel van het geheugen. De oplossing: gebruik het filter Top N om het maximum aantal items te beperken dat in de tabel wordt weergegeven. U kunt voor het maximum aantal items een hoger aantal instellen dan wat gebruikers nodig hebben, bijvoorbeeld 10.000. Hierdoor verandert de ervaring van eindgebruikers niet, maar neemt het geheugengebruik aanzienlijk af. En het belangrijkste is dat de prestaties verbeteren.

Een soortgelijke ontwerpbenadering zoals hierboven beschreven, wordt aangeraden voor alle visuals in uw rapport. Stel uzelf de vraag of alle gegevens in deze visual nodig zijn. Zijn er manieren om de hoeveelheid gegevens die worden weergegeven in de visual te filteren met minimale gevolgen voor de eindgebruiker? Onthoud dat tabellen kostbaar kunnen zijn.

#### <a name="limit-visuals-on-report-pages"></a>Visuals op rapportpagina's beperken

Het bovenstaande principe is evenzeer van toepassing op het aantal visuals dat wordt toegevoegd aan een rapportpagina. Het wordt ten zeerste aangeraden het aantal visuals op een bepaalde rapportpagina te beperken tot het noodzakelijke aantal. [Drillthrough-pagina's](report-drillthrough.md) en [knopinfo voor rapportpagina’s](report-page-tooltips.md) vormen een uitstekende manier om meer informatie te bieden zonder nog meer visuals op de rapportpagina te laden.

#### <a name="evaluate-custom-visual-performance"></a>Prestaties van aangepaste visuals evalueren

Zorg ervoor dat u voor elke aangepaste visual de juiste stappen uitvoert om hoge prestaties te garanderen. Onvoldoende geoptimaliseerde Power BI-visuals kunnen de prestaties van het volledige rapport negatief beïnvloeden.

### <a name="power-bi-paginated-reports"></a>Gepagineerde rapporten in Power BI

Ontwerpen voor gepagineerde rapport in Power BI kunnen worden geoptimaliseerd door aanbevolen procedures voor ontwerpen toe te passen op het ophalen van gegevens voor het rapport. Zie [Richtlijnen voor het ophalen van gegevens voor gepagineerde rapporten](report-paginated-data-retrieval.md) voor meer informatie.

Zorg er ook voor dat uw capaciteit voldoende geheugen heeft toegewezen aan de [workload voor gepagineerde rapporten](../admin/service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>De omgeving optimaliseren

U kunt de Power BI-omgeving optimaliseren door capaciteitsinstellingen te configureren, de grootte van gegevensgateways aan te passen, en de netwerklatentie te verlagen.

### <a name="capacity-settings"></a>Capaciteitsinstellingen

Als u gebruikmaakt van toegewezen capaciteiten (beschikbaar in Power BI Premium (P SKU’s), of Power BI Embedded (A SKU’s, A4-A6)) kunt u de capaciteitsinstellingen beheren. Zie [Premium-capaciteiten beheren](../admin/service-premium-capacity-manage.md) voor meer informatie. Zie [Premium-capaciteiten optimaliseren](../admin/service-premium-capacity-optimize.md) voor hulp bij het optimaliseren van uw capaciteit.

### <a name="gateway-sizing"></a>Grootte van gateways aanpassen

Een gateway is vereist, wanneer Power BI toegang nodig heeft tot gegevens die niet rechtstreeks toegankelijk zijn via internet. U kunt de [on-premises gegevensgateway](../connect-data/service-gateway-onprem.md) installeren op een on-premises server of in een IaaS (Infrastructure-as-a-Service) die wordt gehost op een VM.

Zie [Grootte van on-premises gegevensgateways aanpassen](gateway-onprem-sizing.md) voor begrip over workloads voor gateways en aanbevelingen voor het aanpassen van de grootte.

### <a name="network-latency"></a>Netwerklatentie

Netwerklatentie kan invloed hebben op rapportprestaties doordat de tijd toeneemt die nodig is voor aanvragen de Power BI-service bereiken en voor antwoorden worden geleverd. Tenants in Power BI worden toegewezen aan een specifieke regio.

> [!TIP]
> Zie [Waar bevindt mijn Power BI-tenant zich?](../admin/service-admin-where-is-my-tenant-located.md) om de locatie van uw Power BI-tenant te bepalen.

Wanneer gebruikers van een tenant de Power BI-service openen, worden hun aanvragen altijd doorgestuurd naar deze regio. Wanneer aanvragen de Power BI-service bereiken, kan de service aanvullende aanvragen verzenden, bijvoorbeeld naar de onderliggende gegevensbron of een gegevensgateway. Ook hierop is netwerklatentie van toepassing.

Hulpprogramma's zoals [Azure-snelheidstest](https://azurespeedtest.azurewebsites.net/) bieden een indicatie van de netwerklatentie tussen de client en de Azure-regio. Probeer in het algemeen om gegevensbronnen, gateways en uw Power BI-cluster zo dicht mogelijk bij te houden om de impact van de netwerklatentie te beperken. Plaats ze bij voorkeur in dezelfde regio. Als netwerklatentie een probleem vormt, kunt u gateways en gegevensbronnen dichter bij uw Power BI-cluster brengen door ze op virtuele machines te plaatsen die worden gehost in de cloud.

## <a name="monitoring-performance"></a>Prestaties bewaken

U kunt de prestaties bewaken om knelpunten te identificeren. Trage query’s (of trage rapportvisuals) moet u in de gaten houden voor doorlopende optimalisatie. Bewaking kan worden uitgevoerd tijdens de ontwerpfase in Power BI Desktop, of in productieworkloads in Power BI Premium-capaciteiten. Zie [Rapportprestaties bewaken in Power BI](monitor-report-performance.md) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Power BI-richtlijnen](index.yml)
- [Rapportprestaties bewaken](monitor-report-performance.md)
- Technisch document: [Een Power BI Enterprise-implementatie plannen](https://go.microsoft.com/fwlink/?linkid=2057861)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)




