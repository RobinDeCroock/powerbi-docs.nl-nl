---
title: Power BI voor klanten uit de Amerikaanse overheid - Overzicht
description: Amerikaanse overheidsklanten kunnen een Power BI Pro-abonnement toevoegen aan hun Microsoft 365 Government-abonnement. Meer informatie over het registreren, verbinden en controleren van de beschikbaarheid van functies in deze servicebeschrijving.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/30/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: c90d15c20b54a25ccea5865302753e0189359be2
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396099"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI voor klanten uit de Amerikaanse overheid

Dit artikel is voor Amerikaanse overheidsklanten die Power BI implementeren als onderdeel van een Microsoft 365 Government-abonnement. Overheidsplannen zijn ontworpen voor de unieke behoeften van organisaties die moeten voldoen aan Amerikaanse nalevings-en beveiligingsnormen. De Power BI-service die voor Amerikaanse overheidsklanten is ontworpen, verschilt van de commerciële versie van de Power BI-service. Deze functieverschillen en mogelijkheden worden beschreven in de volgende secties.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Power BI toevoegen een Microsoft 365 Government-abonnement toevoegen

Voordat u een abonnement op Power BI voor de Amerikaanse overheid krijgt en licenties aan gebruikers toewijst, moet u zich inschrijven voor een Microsoft 365 Government-abonnement. Als uw organisatie al een Microsoft 365 Government-abonnement heeft, gaat u naar [Een Power BI Pro-abonnement voor overheidsklanten aanschaffen](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Inschrijven voor een Microsoft 365 Government-abonnement

Als u een nieuwe klant bent, moet u de geschiktheid van uw organisatie valideren voordat u zich kunt aanmelden voor een Microsoft 365 Government-abonnement.  Begin door het [geschiktheidsformulier voor Microsoft 365 voor Government](https://www.microsoft.com/microsoft-365/government/eligibility-validation) in te vullen om te kijken of u wel in aanmerking komt. Raadpleeg de [Microsoft 365 US Government Service-beschrijvingen](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) om er zeker van te zijn dat u het juiste abonnement voor uw organisatie selecteert.

> [!NOTE]
> Als u Power BI al hebt geïmplementeerd in een commerciële omgeving en wilt migreren naar de cloud van de Amerikaanse overheid, moet u een nieuw Power BI Pro-abonnement toevoegen aan uw Microsoft 365 Government-abonnement. Repliceer vervolgens de commerciële gegevens naar de Power BI-service voor de Amerikaanse overheid, verwijder commerciële licentietoewijzingen van gebruikersaccounts en wijs vervolgens een Power BI Pro Government-licentie toe aan de gebruikersaccounts.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Een Power BI Pro-abonnement voor overheidsklanten aanschaffen

Nadat u Microsoft 365 hebt geïmplementeerd, kunt u een Power BI Pro-abonnement toevoegen. Volg de stapsgewijze instructies in [Uw Amerikaanse overheidsorganisatie registreren](service-govus-signup.md) om de Power BI Pro Government-service aan te schaffen. Schaf voldoende licenties aan voor alle gebruikers die Power BI nodig hebben, en wijs deze licenties vervolgens toe aan afzonderlijke gebruikersaccounts.

> [!IMPORTANT]
> Power BI voor de Amerikaanse overheid is niet beschikbaar als een *gratis* licentie. Aan elke gebruiker moet een *Pro* -licentie zijn toegewezen om toegang te krijgen tot de Government Community Cloud. Als aan een gebruikersaccount een gratis licentie is toegewezen, heeft de gebruiker alleen toegang tot de commerciële cloud en zal deze verificatie- en toegangsproblemen ondervinden. Als u Power BI Premium hebt aangeschaft, hoeft u geen Pro-licenties toe te wijzen om gebruikerstoegang in te schakelen.  Gebruikers in de organisatie hebben toegang tot rapporten die met hen zijn gedeeld, mits deze rapporten zijn gepubliceerd in een premium-capaciteit. Raadpleeg [Power BI-servicefuncties per licentietype](../fundamentals/service-features-license-type.md) om de verschillen tussen licentietypen te bekijken.
>

## <a name="government-cloud-instances"></a>Cloud van de Amerikaanse overheid

Microsoft 365 biedt verschillende omgevingen voor overheidsinstanties om te voldoen aan verschillende nalevingsvereisten. Raadpleeg voor meer informatie over elke omgeving:

* [Microsoft 365 Government Community Cloud (GCC)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) is ontworpen voor federale, staats- en lokale overheden.

* [Microsoft 365 GCC High (Government Community High)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is ontworpen voor federale agentschappen, de defensie-industrie, luchtvaart en andere organisaties die niet-geclassificeerde informatie hebben. Deze omgeving is geschikt voor nationale beveiligingsorganisaties en bedrijven met internationaal verkeer in ITAR-gegevens (International Traffic in Arms Regulations) of ingrijpende DFARS-vereisten (Defense Federal Acquisition Regulations Supplement).

* De [Microsoft 365 DoD-omgeving](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is uitsluitend ontworpen voor het Amerikaanse ministerie van defensie.


## <a name="sign-in-to-power-bi-for-us-government"></a>Aanmelden bij Power BI voor de Amerikaanse overheid

De URL voor het verbinding maken met Power BI verschilt voor overheidsgebruikers en commerciële gebruikers. Als u zich wilt aanmelden bij Power BI, gebruikt u de volgende URL's:

| Commerciële versie  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Uw account is mogelijk ingesteld in meerdere clouds. Als uw account op deze manier is ingesteld, kunt u kiezen met welke cloud u verbinding wilt maken wanneer u zich aanmeldt bij Power BI Desktop.

## <a name="allow-connections-to-power-bi"></a>Verbindingen met Power BI toestaan

Als u de Power BI-service wilt gebruiken, moet u verbindingen met de vereiste eindpunten op internet toestaan. Deze doelen moeten bereikbaar zijn om communicatie mogelijk te maken tussen uw eigen netwerk, Power BI en andere afhankelijke services.

In de onderstaande tabel worden de vereiste eindpunten weergegeven die u aan de acceptatielijst moet toevoegen om verbinding te kunnen maken met de Power BI-service voor algemeen gebruik van de website. Deze eindpunten zijn uniek voor de cloud van de Amerikaanse overheid. Voor de Power BI-service is alleen vereist dat TCP-poort 443 is geopend voor de vermelde eindpunten. De eindpunten voor het ophalen van gegevens, dashboard- en rapportintegratie, Power BI-visuals en andere optionele services zijn niet uniek voor de cloud van de Amerikaanse overheid. Zie [Power BI-URL's toevoegen aan uw acceptatielijst](power-bi-whitelist-urls.md) om deze URL's ook toe te voegen aan de acceptatielijst.

Verificatie, identiteit en beheer van Power BI is afhankelijk van de verbinding met Microsoft 365-services. U moet ook verbinding maken met Microsoft 365 om auditlogboeken weer te geven. Zie integratie van Microsoft 365 in de onderstaande tabel om de eindpunten voor deze services te identificeren.

### <a name="power-bi-urls-for-general-site-usage"></a>Power BI-URL's voor algemeen gebruik van de website

|  Doel | Doel |
| ---- | ----- |
| Back-end API's | **GCC** : api.powerbigov.us |
| | **GCC-High** : api.high.powerbigov.us |
| | **DoD** : api.mil.powerbi.gov.us |
| Back-end API's | **GCC** : *analysis.usgovcloudapi.net |
| | **GCC High** : *.high.analysis.usgovcloudapi.net |
| | **DoD** : *.mil.analysis.usgovcloudapi.net |
| Back-end API's | **All** : *.pbidedicated.usgovcloudapi.net |
| Content Delivery Network (CDN) | **GCC** : gov.content.powerapps.us |
| | **GCC High** : high.content.powerapps.us |
| | **DoD** : mil.content.powerapps.us |
| Integratie van Microsoft 365 | **GCC** : [Wereldwijde eindpunten](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High** : [Amerikaanse overheid GCC High-eindpunten](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD** : [Amerikaanse Government DOD-eindpunten](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| Portal |**GCC** : *.powerbigov.us |
| | **GCC-High** : *.high.powerbigov.us |
| | **DoD** : *.mil.powerbigov.us |
| Telemetrie naar service | **All** : dc.services.visualstudio.us |
| Informatieve berichten (optioneel) | **All** : dynmsg.modpim.com |
| NPS-enquêtes (optioneel) | **All** : nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>Azure Government en algemene Azure Cloud Services verbinden

Azure wordt gedistribueerd over meerdere clouds. Standaard kunt u firewallregels inschakelen om een verbinding met een Cloud-specifiek exemplaar te openen, maar dit is anders over verschillende cloud-netwerken.  Als u wilt communiceren tussen services in de openbare cloud en services in de Government Community Cloud, moet u specifieke firewallregels configureren. Als u bijvoorbeeld toegang wilt krijgen tot openbare cloudexemplaren van een SQL-database vanuit uw Power BI-implementatie in de cloud, hebt u een firewallregel in de SQL-database nodig. Configureer specifieke firewallregels voor SQL-databases om verbindingen met de Azure Government Cloud toe te staan voor de volgende datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* US DoD East
* US DoD Central

Als u de IP-adresbereiken voor de cloud van de Amerikaanse overheids wilt ophalen, downloadt u het bestand [Azure IP-bereiken en servicetags – Cloud van de Amerikaanse overheid](https://www.microsoft.com/download/details.aspx?id=57063). bereiken worden weergegeven voor zowel Power BI als Power Query.

Zie [Documentatie van Azure Government](/azure/azure-government/) voor meer informatie over Microsoft Azure Government-cloudservices.

Raadpleeg [IP-firewallregels maken en beheren](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules) als u firewalls wilt instellen voor SQL-databases.

## <a name="power-bi-feature-availability"></a>Beschikbaarheid van Power BI-functies

Er zijn een aantal verschillen tussen overheidsplannen en commerciële abonnementen om te voldoen aan de vereisten van klanten in de Cloud. We streven ernaar om alle functies in overheidsclouds binnen 30 dagen na de algemene beschikbaarheid beschikbaar te maken. In sommige gevallen ligt het aan onderliggende afhankelijkheden dat we een functie niet beschikbaar kunnen maken.

De volgende tabel bevat een lijst met functies die niet beschikbaar zijn in een bepaalde overheidsomgeving. We voegen geschatte beschikbaarheid toe als de release is gepland:

|Functie |GCC |GCC High |DoD|
|------|------|------|------|
|[Azure B2B Collaboration tussen overheidscloud en commerciële cloud](service-admin-azure-ad-b2b.md)<sup>1</sup>|![beschikbaar](../media/yes.png)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|
|[Insluiten in SharePoint online met het webonderdeel Power BI](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![beschikbaar](../media/yes.png)|![Beschikbaar](../media/yes.png)|![niet beschikbaar](../media/no.png)|
|[Power Automate-connectiviteit voor gegevensgestuurde waarschuwingen](../connect-data/power-bi-data-sources.md)|![beschikbaar](../media/yes.png)|![beschikbaar](../media/yes.png)|![niet beschikbaar](../media/no.png)|
|[Tabblad Power BI in Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![beschikbaar](../media/yes.png)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|
|[Grote modellen](service-premium-large-models.md) | K4 2020 |K4 2020| ![niet beschikbaar](../media/no.png) |
|[Gegevensstromen - optimalisatie SQL-rekenengine](../transform-model/dataflows/dataflows-premium-features.md) | K4 2020 |K4 2020| ![niet beschikbaar](../media/no.png) |
|[Gegevensstromen - directe query](../transform-model/dataflows/dataflows-configure-consume.md) | K4 2020 |K4 2020|![niet beschikbaar](../media/no.png)|
|[Gegevensbescherming (MIP-labels)](service-security-sensitivity-label-overview.md)|K4 2020|K4 2020 |K4 2020|
|[Sjabloon-apps](../connect-data/service-template-apps-overview.md)<sup>3</sup>|K4 2020 |K4 2020| K4 2020|
|[Aangepaste visuals](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|K4 2020 |K4 2020| K4 2020|
|[Dataconnector voor gesprekskwaliteit](/microsoftteams/cqd-power-bi-connector)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|
|[Bring Your Own Storage (Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|
|[Genereren van QR-code](../create-reports/service-create-qr-code-for-tile.md)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|![niet beschikbaar](../media/no.png)|

<sup>1</sup> Hoewel B2B-samenwerking beschikbaar is voor GCC, moet de externe gebruiker een licentie in die omgeving hebben. Licenties voor de commerciële cloud zijn niet geldig in GCC. [Vergelijk Azure Government en Global Azure](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2) voor meer informatie over bekende beperkingen met B2B Collaboration voor de Amerikaanse overheid

<sup>2</sup> De Power BI-ervaring in Teams voor GCC is beperkt, werkt alleen voor klassieke werkruimten en bevat niet de uitgebreide functionaliteit die wordt beschreven in [Power BI-inhoud insluiten in Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> De functionaliteit voor sjabloon-apps en aangepaste visuals is bij vrijgave beperkt voor overheidsclouds. Meer informatie over specifieke beperkingen wordt gepubliceerd bij vrijgave.

## <a name="next-steps"></a>Volgende stappen

* [Registreren voor Power BI voor de Amerikaanse overheid](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate voor de Amerikaanse overheid](/power-automate/us-govt)
* [Demo van Power BI voor de Amerikaanse overheid](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)