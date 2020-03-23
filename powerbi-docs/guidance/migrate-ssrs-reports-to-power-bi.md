---
title: SQL Server Reporting Services-rapporten migreren naar Power BI
description: Hulp bij het migreren van uw SSRR-rapporten (SQL Server Reporting Services) naar Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: b87848953722d33235a11729a3643c627cca7234
ms.sourcegitcommit: 646d2de454a2897dc52cbc02b7743aaa021bac04
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79525609"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>SQL Server Reporting Services-rapporten migreren naar Power BI

Dit artikel is bedoeld voor auteurs van SSRS-rapporten (SQL Server Reporting Services) en Power BI-beheerders. Het biedt u richtlijnen om u te helpen bij het migreren van uw [RDL-rapporten (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) naar Power BI.

> [!NOTE]
> Het is alleen mogelijk om RDL-rapporten te migreren. In Power BI worden RDL-rapporten _gepagineerde rapporten_ genoemd.

De richtlijnen zijn onderverdeeld in vier fasen. We raden u aan eerst het hele artikel te lezen voordat u uw rapporten migreert.

1. [Voordat u begint](#before-you-start)
1. [Pre-migratiefase](#pre-migration-stage)
1. [Migratiefase](#migration-stage)
1. [Post-migratiefase](#post-migration-stage)

U kunt een migratie realiseren zonder downtime naar uw SSRS-servers of verstoring voor uw rapportgebruikers. Het is belangrijk om te begrijpen dat er geen gegevens of rapporten hoeven te worden verwijderd. Dus dit betekent dat u uw huidige omgeving kunt behouden totdat u klaar bent om deze buiten gebruik te stellen.

## <a name="before-you-start"></a>Voordat u begint

Voordat u met de migratie begint, moet u controleren of uw omgeving voldoet aan bepaalde vereisten. Deze vereisten worden beschreven en u kunt ook kennismaken met een handig migratieprogramma.

### <a name="preparing-for-migration"></a>De migratie voorbereiden

Als u zich voorbereidt op het migreren van uw rapporten naar Power BI, controleert u eerst of uw organisatie een [Power BI Premium](../service-premium-what-is.md)-abonnement heeft. Dit abonnement is vereist voor het hosten en uitvoeren van uw gepagineerde Power BI-rapporten.

### <a name="supported-versions"></a>Ondersteunde versies

U kunt SSRS-exemplaren migreren die ter plaatse worden uitgevoerd of op virtuele machines die worden gehost door cloudproviders, zoals Azure.

In de volgende lijst worden de SQL Server-versies beschreven die worden ondersteund voor migratie naar Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Migratie van Power BI Report Server is ook mogelijk.

### <a name="migration-tool"></a>Hulpprogramma voor migratie

Het wordt aanbevolen het [hulpprogramma voor RDL-migratie](https://github.com/microsoft/RdlMigration) te gebruiken om uw rapporten voor te bereiden en te migreren. Dit hulpprogramma is ontwikkeld door Microsoft om klanten te helpen bij het migreren van RDL-rapporten van hun SSRS-servers naar Power BI. Het is beschikbaar op GitHub en bevat een end-to-end overzicht van het migratiescenario.

Het hulpprogramma automatiseert de volgende taken:

* Hiermee wordt gecontroleerd op [niet-ondersteunde gegevensbronnen](../paginated-reports/paginated-reports-data-sources.md) en [niet-ondersteunde rapportfuncties](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* Hiermee worden _gedeelde_ resources geconverteerd naar _ingesloten_ resources:
  * Gedeelde **gegevensbronnen** worden ingesloten gegevensbronnen
  * Gedeelde **gegevenssets** worden ingesloten gegevenssets
* Hiermee worden rapporten gepubliceerd (die door controles komen) als gepagineerde rapporten, naar een bepaalde Power BI-werkruimte (op een Premium-capaciteit)

De bestaande rapporten worden niet gewijzigd of verwijderd. Bij voltooiing voert het hulpprogramma een overzicht uit van alle voltooide acties: geslaagd of mislukt.

Na verloop van tijd kan het hulpprogramma worden verbeterd door Microsoft. De gemeenschap wordt aangemoedigd om bij te dragen en te helpen bij het verbeteren ervan.

## <a name="pre-migration-stage"></a>Pre-migratiefase

Nadat u hebt gecontroleerd of uw organisatie aan de voorwaarden voldoet, bent u klaar om de _pre-migratiefase_ te starten. Deze fase bestaat uit drie fasen:

1. Ontdekken
1. Evalueren
1. Voorbereiden

### <a name="discover"></a>Ontdekken

Het doel van de fase _Ontdekken_ is het identificeren van uw bestaande SSRS-instanties. Dit proces omvat het scannen van het netwerk om alle SQL Server-exemplaren in uw organisatie te identificeren.

U kunt de [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826) gebruiken. Dit is ook bekend als de MAP Toolkit. Hiermee worden uw SQL Server-exemplaren, versies en geïnstalleerde functies gedetecteerd en wordt hierover gerapporteerd. Het is een krachtig hulpmiddel voor inventarisatie, evaluatie en rapportage dat uw migratieplanningsproces kan vereenvoudigen.

### <a name="assess"></a>Evalueren

Nadat u uw SSRS-exemplaren hebt ontdekt, is het doel van de fase _Evalueren_ inzicht te krijgen in SSRS-rapporten (of serveritems) die niet kunnen worden gemigreerd.

Alleen RDL-rapporten kunnen worden gemigreerd van uw SSRS-servers naar Power BI. Elk gemigreerd RDL-rapport wordt een gepagineerd Power BI-rapport.

De volgende SSRS-itemtypen kunnen echter niet worden gemigreerd naar Power BI:

- Gedeelde gegevensbronnen <sup>1</sup>
- Gedeelde gegevenssets <sup>1</sup>
- Resources, zoals afbeeldingsbestanden
- KPI's (SSRS 2016 of hoger — alleen Enterprise Edition)
- Mobiele rapporten (SSRS 2016 of hoger — alleen Enterprise Edition)
- Rapportmodellen (afgeschaft)
- Rapportonderdelen (afgeschaft)

<sup>1</sup> Het [RDL-migratieprogramma](https://github.com/microsoft/RdlMigration) converteert automatisch gedeelde gegevensbronnen en gedeelde gegevenssets, op voorwaarde dat ze ondersteunde gegevensbronnen gebruiken.

Als uw RDL-rapporten afhankelijk zijn van functies [die nog niet worden ondersteund door gepagineerde Power BI-rapporten](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi), kunt u plannen ze opnieuw te ontwikkelen als [Power BI-rapporten](../consumer/end-user-reports.md). Zelfs als u uw RDL-rapporten kunt migreren, wordt aanbevolen ze te moderniseren als Power BI-rapporten, wanneer dit zinvol is.

Als uw RDL-rapporten gegevens moeten ophalen uit _on-premises gegevensbronnen_, kunnen ze geen gebruikmaken van eenmalige aanmelding (SSO). Op dit moment wordt voor het ophalen van gegevens uit deze bronnen de beveiligingscontext van het _gebruikersaccount van de gegevensbron van de gateway_ gebruikt. Het is niet mogelijk voor SQL Server Analysis Services (SSAS) om beveiliging op rijniveau per gebruiker af te dwingen.

In het algemeen zijn gepagineerde rapporten van Power BI geoptimaliseerd voor **afdrukken** of **voor het genereren van PDF's**. Power BI-rapporten zijn geoptimaliseerd voor **verkenning en interactiviteit**. Zie [Wanneer u gepagineerde rapporten gebruikt in Power BI](report-paginated-or-power-bi.md) voor meer informatie.

### <a name="prepare"></a>Voorbereiden

Het doel van de fase _Voorbereiden_ is om alles gereed te maken. Het omvat het instellen van de Power BI-omgeving, het plannen van hoe u uw rapporten beveiligt en publiceert en ideeën voor het opnieuw ontwikkelen van SSRS-items die niet worden gemigreerd.

1. Zorg ervoor dat de [workload van gepagineerde rapporten](../service-admin-premium-workloads.md#paginated-reports) is ingeschakeld voor uw Power BI Premium-capaciteit en dat deze voldoende geheugen heeft.
1. Controleer de ondersteuning voor de [gegevensbronnen](../paginated-reports/paginated-reports-data-sources.md) van uw rapport en stel een [Power BI Gateway](../service-gateway-onprem.md) in om connectiviteit met alle on-premises gegevensbronnen toe te staan.
1. Raak vertrouwd met Power BI-beveiliging en plan [hoe u uw SSRS-mappen en -rechten](/sql/reporting-services/security/secure-folders) gaat reproduceren met [Power BI-werkruimten en -rollen](../service-new-workspaces.md).
1. Raak vertrouwd met delen in Power BI en plan hoe u inhoud distribueert door [Power BI-apps](../service-create-distribute-apps.md) te publiceren.
1. U kunt ook [gedeelde Power BI-gegevenssets](../service-datasets-build-permissions.md) gebruiken in plaats van de gedeelde databronnen van SSRS.
1. Gebruik [Power BI Desktop](../desktop-what-is-desktop.md) om voor mobiele apparaten geoptimaliseerde rapporten te ontwikkelen, eventueel met behulp van de aangepaste [Power KPI-Visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) in plaats van uw SSRS mobiele rapporten en KPI's.
1. Evalueer opnieuw het gebruik van het ingebouwde veld **UserID** in uw rapporten. Als u vertrouwt op de **UserID** om rapportgegevens te beveiligen, moet u weten dat voor gepagineerde rapporten (als deze worden gehost in de Power BI-service) de UPN (User Principal Name) wordt geretourneerd. Dus in plaats van de naam van het NT-account te retourneren, zoals _AW\mblythe_, retourneert het ingebouwde veld iets als _m.blythe&commat;adventureworks.com_. U moet de definities van uw gegevensset wijzigen en mogelijk ook van de brongegevens. Als dat is gebeurd en de gegevens opnieuw zijn gepubliceerd, raden we u aan om uw rapporten grondig te testen om er zeker van te zijn dat de gegevensmachtigingen naar verwachting werken.
1. Evalueer opnieuw het gebruik van het ingebouwde veld **ExecutionTime** in uw rapporten. Voor gepagineerde rapporten (als deze worden gehost in de Power BI-service), retourneert het ingebouwde veld de datum/tijd _in Coordinated Universal Time (of UTC)_ . Dit kan invloed hebben op de standaardwaarden voor rapportparameters en op tijdlabels voor de rapportuitvoering (meestal toegevoegd aan rapportvoetteksten).
1. Als uw gegevensbron SQL Server (on-premises) is, controleert u of rapporten geen kaartvisualisaties gebruiken. Kaartvisualisaties zijn afhankelijk van ruimtelijke gegevenstypen van SQL Server, en deze worden niet ondersteund door de gateway. Zie [Richtlijnen voor het ophalen van gegevens voor gepagineerde rapporten (complexe gegevenstypen van SQL Server)](report-paginated-data-retrieval.md#sql-server-complex-data-types) voor meer informatie.
1. Zorg ervoor dat de rapportauteurs [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) hebben geïnstalleerd en dat latere releases eenvoudig in uw organisatie kunnen worden gedistribueerd.

## <a name="migration-stage"></a>Migratiefase

Nadat u uw Power BI-omgeving en rapporten hebt voorbereid, bent u klaar voor de _migratiefase_.

Er zijn twee migratieopties: _handmatig_ en _geautomatiseerd_. Handmatige migratie is geschikt voor een klein aantal rapporten of rapporten die vóór migratie moeten worden gewijzigd. Geautomatiseerde migratie is geschikt voor de migratie van een groot aantal rapporten.

### <a name="manual-migration"></a>Handmatige migratie

Iedereen met toestemming voor toegang tot het SSRS-exemplaar en de Power BI-werkruimte kan rapporten handmatig migreren naar Power BI. Dit zijn de stappen:

1. Open de SSRS-portal die de rapporten bevat die u wilt migreren.
1. Download elke rapportdefinitie en sla de .rdl-bestanden lokaal op.
1. Open _de nieuwste versie_ van Power BI Report Builder en maak verbinding met de Power BI-service met uw Azure AD-inloggegevens.
1. Open elk rapport in Power BI Report Builder en:
   1. Controleer of alle gegevensbronnen en gegevenssets zijn ingebed in de rapportdefinitie en of ze [ondersteunde gegevensbronnen](../paginated-reports/paginated-reports-data-sources.md) zijn.
   1. Bekijk een voorbeeld van het rapport om te controleren of het correct wordt weergegeven.
   1. Kies de optie _Opslaan als_ en selecteer vervolgens _Power BI-service_.
   1. Selecteer de werkruimte die het rapport zal bevatten.
   1. Controleer of het rapport wordt opgeslagen. Als bepaalde functies in uw rapportontwerp nog niet worden ondersteund, kan het niet worden opgeslagen. U wordt op de hoogte gebracht van de redenen. Vervolgens moet u het ontwerp van het rapport herzien en opnieuw proberen op te slaan.

### <a name="automated-migration"></a>Geautomatiseerde migratie

Er zijn twee opties voor automatische migratie. U kunt gebruikmaken van:

- Het RDL-migratieprogramma
- De openbaar beschikbare API's voor SSRS en Power BI

Het [RDL-migratieprogramma](#migration-tool) is al beschreven in dit artikel.

U kunt ook gebruik maken van de openbaar beschikbare SSRS en Power BI API's om de migratie van uw inhoud te automatiseren. Hoewel deze API's al worden gebruikt door het RDL-migratieprogramma, kunt u een aangepast hulpprogramma ontwikkelen dat geschikt is voor uw exacte vereisten.

Voor meer informatie over de API's, zie:

- [Naslag voor REST-API voor Power BI](../developer/automation/rest-api-reference.md)
- [SQL Server Reporting Services REST API’s](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Post-migratiefase

Nadat u de migratie hebt voltooid, bent u klaar voor de _post-migratiefase_. In deze fase wordt een aantal taken na de migratie uitgevoerd om ervoor te zorgen dat alles correct en efficiënt functioneert.

### <a name="configure-data-sources"></a>Gegevensbronnen configureren

Zodra de rapporten zijn gemigreerd naar Power BI, moet u ervoor zorgen dat hun gegevensbronnen correct zijn ingesteld. Het kan gaan om toewijzing aan gateway-gegevensbronnen en [veilige opslag van gegevensbronreferenties](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). Deze acties worden niet uitgevoerd door het RDL-migratieprogramma.

### <a name="review-report-performance"></a>Rapportprestaties bekijken

Het wordt ten zeerste aanbevolen de volgende acties uit te voeren om de best mogelijke gebruikerservaring met rapporten te garanderen:

1. Test de rapporten in elke [browser die wordt ondersteund door Power BI](../power-bi-browsers.md) om te bevestigen dat het rapport correct wordt weergegeven.
1. Voer tests uit om de tijden voor het genereren van rapporten in SSRS en Power BI te vergelijken. Controleer of Power BI-rapporten binnen een acceptabele tijd worden weergegeven.
1. Als Power BI-rapporten niet kunnen worden gerenderd vanwege onvoldoende geheugen, wijst u [extra resources toe aan de Power BI Premium-capaciteit](../service-admin-premium-workloads.md#paginated-reports).
1. Voor rapporten met een lange rendering kunt u Power BI deze aan uw rapportgebruikers laten leveren als [e-mailabonnementen met rapportbijlagen](../consumer/paginated-reports-subscriptions.md).
1. Bekijk voor Power BI-rapporten op basis van Power BI-gegevenssets de modelontwerpen om ervoor te zorgen dat deze volledig zijn geoptimaliseerd.

### <a name="reconcile-issues"></a>Problemen oplossen

De fase na de migratie is cruciaal voor het oplossen van eventuele problemen en het aanpakken van eventuele prestatieproblemen. Het toevoegen van de workload van gepagineerde rapporten aan een capaciteit kan leiden tot trage prestaties voor gepagineerde rapporten _en andere inhoud_ die is opgeslagen in de capaciteit.

Zie de volgende artikelen voor meer informatie over deze problemen, met inbegrip van specifieke stappen om deze te begrijpen en te verhelpen:

- [Premium-capaciteiten optimaliseren](../service-premium-capacity-optimize.md)
- [Premium-capaciteiten bewaken met de app](../service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Wat zijn gepagineerde rapporten in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Richtlijnen voor het ophalen van gegevens voor gepagineerde rapporten](report-paginated-data-retrieval.md)
- [Wanneer gebruikt u gepagineerde rapporten in Power BI](report-paginated-or-power-bi.md)
- [Gepagineerde rapporten in Power BI: veelgestelde vragen](../paginated-reports/paginated-reports-faq.md)
- [Onlinecursus: Gepagineerde rapporten in een dag](../paginated-reports/paginated-reports-online-course.md)
- [Veelgestelde vragen over Power BI Premium](../service-premium-faq.md)
- [Het hulpprogramma voor RDL-migratie](https://github.com/microsoft/RdlMigration)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)

Power BI-partners zijn beschikbaar om uw organisatie te helpen slagen met het migratieproces. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).
