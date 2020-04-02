---
title: Whitepaper Power BI-beveiliging
description: Technisch document met een beschrijving van de beveiligingsarchitectuur en implementatie van Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2019
LocalizationGroup: Conceptual
ms.openlocfilehash: a13e48e413f047812d9b00fe67c2ee2b69bbc2dc
ms.sourcegitcommit: 6e56d038280efab86521602cbc089b3989dddbd0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80551094"
---
# <a name="power-bi-security-whitepaper"></a>Whitepaper Power BI-beveiliging

**Samen vatting:** Power BI is een online software service (*SaaS*of software als een service) van micro soft waarmee u eenvoudig en snel Self-Service Business Intelligence-Dash boards, rapporten, gegevens sets en visualisaties kunt maken. Met Power BI kunt u verbinding maken met veel verschillende gegevensbronnen, gegevens via deze verbindingen combineren en vormgeven, en vervolgens rapporten en dashboards maken die met anderen kunnen worden gedeeld.

**Schrijver:** David Iseminger

**Technische revisoren:** Pedram Rezaei, Cristian Petculescu, Siva Harinath, Tod Personeelsing, Haydn Richardson, Adam Wilson, ben Childs, Robert Bruckner, Sergei Gundorov, Kasper de jonge

**Van toepassing op:** Power BI SaaS, Power BI Desktop, Power BI Embedded Power BI Premium

> [!NOTE]
> U kunt dit technische document opslaan of afdrukken door in uw browser **Afdrukken** en vervolgens **Opslaan als PDF-bestand** te selecteren.

## <a name="introduction"></a>Inleiding

**Power BI** is een online softwareservice-aanbod (_SaaS_ of software als een dienst) van Microsoft waarmee u snel en eenvoudig selfservice Business Intelligence-dashboards, -rapporten, -gegevenssets en -visualisaties (BI) kunt maken. Met Power BI kunt u verbinding maken met veel verschillende gegevensbronnen, gegevens via deze verbindingen combineren en vormgeven, en vervolgens rapporten en dashboards maken die met anderen kunnen worden gedeeld.

De Power BI-service is onderworpen aan de [Microsoft Online Services-voorwaarden](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31) en de [Microsoft Enterprise-privacyverklaring](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Raadpleeg de voorwaarden met betrekking tot de gegevensverwerkingslocatie in de Microsoft Online Services-voorwaarden voor informatie over de locatie waar de gegevens worden verwerkt. Het [Microsoft Vertrouwenscentrum](https://www.microsoft.com/trustcenter) is de primaire resource voor nalevingsinformatie met betrekking tot Power BI. Het Power BI-team doet er alles aan om klanten de nieuwste innovaties en productiviteit te bieden. Power BI bevindt zich momenteel in tier D van het [nalevings raamwerk van Office 365](https://www.microsoft.com/trust-center/compliance/compliance-overview).

Dit artikel bevat informatie over Power BI-beveiliging aan de hand van een uitleg over de Power BI-architectuur. Er wordt uitgelegd hoe gebruikers worden geverifieerd bij Power BI en hoe gegevensverbindingen tot stand worden gebracht. Vervolgens wordt beschreven hoe met de Power BI-service gegevens worden opgeslagen en verplaatst. De laatste sectie is gewijd aan vragen met betrekking tot beveiliging, waarop tevens de antwoorden worden gegeven.

## <a name="power-bi-architecture"></a>Architectuur van Power BI

De **Power BI**-service is gebaseerd op **Azure**, het [cloudcomputingplatform](https://azure.microsoft.com/overview/what-is-azure/) van Microsoft. Power BI wordt momenteel geïmplementeerd in veel datacenters over de hele wereld. Er zijn veel actieve implementaties beschikbaar gesteld aan klanten in de regio's die door deze datacenters worden bediend. Daarnaast zijn er even veel passieve implementaties, die als back-up fungeren voor alle actieve implementaties.

Elke Power BI-implementatie bestaat uit twee clusters: een **WFE**-cluster (Web Front End) en een **Back-End**cluster. Deze twee clusters zijn in de volgende afbeelding weergegeven en vormen de achtergrond voor de rest van dit artikel. 

![Het WFE en het Back-End](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

Power BI maakt gebruik van Azure Active Directory (**AAD**) voor accountverificatie en beheer. Power BI gebruikt ook de **Azure Traffic Manager** (ATM) om gebruikersverkeer te leiden naar het dichtstbijzijnde datacentrum, dat wordt bepaald door het DNS-record van de client die probeert verbinding te maken, voor het verificatieproces en om statische inhoud en voor het downloaden van bestanden. Power BI gebruikt de geografische, dichtstbijzijnde WFE om efficiënt de benodigde statische inhoud en bestanden naar gebruikers te distribueren, met uitzonde ring van Power BI visuals die worden geleverd met behulp van de **Azure Content Delivery Network (CDN)** .

### <a name="the-wfe-cluster"></a>Het cluster WFE

Het cluster **WFE** beheert het eerste verbindings- en verificatieproces voor Power BI. Het maakt hierbij gebruik van AAD om clients te verifiëren en tokens te leveren voor volgende clientverbindingen met de Power BI-service.

![Het cluster WEF](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

Wanneer gebruikers verbinding maken met de Power BI-service, kan de DNS-service van de client communiceren met de **Azure Traffic Manager** om het dichtstbijzijnde datacentrum met een Power BI-implementatie te vinden. Zie [Performance traffic routing method for Azure Traffic Manager](https://azure.microsoft.com/documentation/articles/traffic-manager-routing-methods/#performance-traffic-routing-method) (Prestaties verkeersrouteringsmethode voor Azure Traffic Manager) voor meer informatie over dit proces.

Het cluster WFE dat zich het dichtst bij de gebruiker bevindt, beheert de aanmeldings- en verificatievolgorde (die verderop in dit artikel wordt beschreven) en levert een AAD-token aan de gebruiker zodra de verificatie geslaagd is. De ASP.NET-component binnen het cluster WFE parseert de aanvraag om te bepalen tot welke organisatie de gebruiker behoort en raadpleegt vervolgens de Power BI **Global Service**. De Global Service is een individuele Azure-tabel die wordt gedeeld tussen alle WFE- en back-endclusters wereldwijd. Hiermee worden gebruikers en klantorganisaties toegewezen aan het datacenter waar zich hun Power BI-tenant bevindt. Het WFE geeft aan de browser door in welk back-endcluster de tenant van de organisatie zich bevindt. Wanneer een gebruiker is geverifieerd, vinden de hierop volgende clientinteracties rechtstreeks plaats met het back-endcluster. De WFE is geen intermediator meer voor deze aanvragen.

### <a name="the-power-bi-back-end-cluster"></a>Het back-endcluster van Power BI

Via het cluster **Back-End** communiceren geverifieerde clients met de Power BI-service. Het cluster **Back-End** beheert visualisaties, gebruikersdashboards, gegevenssets, rapporten, gegevensopslag, gegevensverbindingen, het vernieuwen van gegevens en andere aspecten van de interactie met de Power BI-service.

![Het back-endcluster](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

De **Gatewayrol** fungeert als een gateway tussen aanvragen van gebruikers en de Power BI-service. Gebruikers werken niet rechtstreeks met rollen, behalve met de Gatewayrol.

**Belang rijk:** Het is belang rijk te weten dat _alleen_ rollen van Azure API Management (**APIM**) en gateway (**gw**) toegankelijk zijn via het open bare Internet. Ze bieden verificatie, autorisatie, DDoS-beveiliging, beperking, taakverdeling, routering en andere mogelijkheden.

De stippellijn in de bovenstaande afbeelding van het **back-endcluster** verduidelijkt de grens tussen de enige twee rollen die toegankelijk zijn voor gebruikers (links van de stippellijn) en de rollen die alleen toegankelijk zijn voor het systeem. Wanneer een geverifieerde gebruiker verbinding maakt met de Power BI-service, wordt de verbinding en elke aanvraag van de client geaccepteerd en beheerd door de **Gatewayrol** en door **Azure API Management**, die vervolgens namens de gebruiker communiceert met de rest van de Power BI-service. Wanneer een client bijvoorbeeld probeert een dashboard weer te geven, accepteert de **Gatewayrol** die aanvraag en stuurt vervolgens afzonderlijk een aanvraag naar de **Presentatierol** om de gegevens op te halen die de browser nodig heeft om het dashboard weer te geven.

![De Gatewayrol](media/whitepaper-powerbi-security/powerbi-security-whitepaper_04.png)

### <a name="power-bi-premium"></a>Power BI Premium

**Power BI Premium** biedt een speciaal ingerichte en gepartitioneerde servicewerkruimte voor abonnees die toegewezen resources voor hun Power BI-activiteiten nodig hebben. Wanneer een klant zich registreert voor een Power BI Premium-abonnement wordt de Premium-capaciteit gemaakt via de **Azure Resource Manager**. Tijdens de implementatie van het abonnement wordt een set virtuele machines toegewezen die overeenkomt met het abonnementsniveau, in het datacenter waar de Power BI-tenant van de abonnee wordt gehost (met uitzondering van meerdere geografische gebieden omgevingen, zoals verderop in dit document wordt beschreven). Dit wordt geïnitieerd als een **Azure Service Fabric**-implementatie.

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

Als de implementatie gereed is, wordt alle communicatie met het Premium-cluster gerouteerd via het back-endcluster van Power BI, waarbij een verbinding met de virtuele machines van het toegewezen **Power BI Premium**-abonnement van de client tot stand wordt gebracht.

### <a name="data-storage-architecture"></a>Gegevensopslagarchitectuur

Power BI maakt gebruik van twee primaire opslagplaatsen om gegevens op te slaan en te beheren. Gegevens van gebruikers die zijn geüpload worden meestal verzonden naar **Azure Blob**-opslag. Alle metagegevens, alsmede artefacten voor het systeem zelf, worden achter een firewall opgeslagen in  **Azure SQL Database**.

![Gegevensopslag](media/whitepaper-powerbi-security/powerbi-security-whitepaper_06.png)

Wanneer een gebruiker bijvoorbeeld een Excel-werkmap importeert in de Power BI-service, wordt een in-memory tabellaire Analysis Services-database gemaakt en worden de gegevens maximaal één uur in het geheugen opgeslagen (of tot geheugenbelasting in het systeem plaatsvindt). De gegevens worden ook verzonden naar **Azure Blob**-opslag.

Metagegevens over het Power BI-abonnement van een gebruiker, zoals dashboards, rapporten, recente gegevensbronnen, werkruimten, organisatiegegevens, tenant-gegevens en andere metagegevens over het systeem worden opgeslagen en bijgewerkt in **Azure SQL Database**. Alle gegevens die zijn opgeslagen in Azure SQL Database zijn volledig versleuteld met behulp van [Azure SQL TDE-technologie](https://msdn.microsoft.com/library/dn948096.aspx) (Transparent Data Encryption). Alle gegevens die zijn opgeslagen in Azure Blob-opslag zijn eveneens versleuteld. In de sectie **Gegevensopslag en -verplaatsing** vindt u meer informatie over het proces van het laden, opslaan en verplaatsen van gegevens.

## <a name="tenant-creation"></a>Een tenant maken

Een tenant is een toegewezen exemplaar van de Azure AD-service die een organisatie ontvangt en waarvan de organisatie eigenaar is wanneer deze zich aanmeldt voor een Microsoft-cloudservice zoals Azure, Microsoft Intune, Power BI of Office 365. Elke Azure AD-tenant is uniek en werkt afzonderlijk van andere Azure AD-tenants.

Een tenant bevat de gebruikers in een bedrijf en de informatie over deze gebruikers: hun wachtwoorden, gebruikersprofielgegevens, machtigingen, enzovoort. Het bevat ook groepen, toepassingen en andere gegevens met betrekking tot een organisatie en de beveiliging. Zie [Wat is een Azure AD-tenant](https://msdn.microsoft.com/library/azure/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) voor meer informatie.

Een Power BI-tenant wordt gemaakt in het datacenter dat zich het dichtst bij het land (of de regio) en de staat bevindt, zoals voor de tenant is opgegeven in Azure Active Directory. Deze informatie is opgegeven toen de Office 365- of Power BI-service werd ingericht. De Power BI-tenant wordt nu niet verplaatst uit die datacenterlocatie.

### <a name="multiple-geographies-multi-geo"></a>Meerdere geografische gebieden (Multi-geo)

Voor sommige organisaties is een Power BI-aanwezigheid in meerdere landen of regio's vereist, op basis van hun bedrijfsbehoeften. Een bedrijf kan bijvoorbeeld zijn Power BI Tenant in de Verenigde Staten, maar kan ook zaken doen in andere geografische gebieden, zoals Australië, en bepaalde Power BI gegevens nodig hebben om te voldoen aan lokale voor Schriften. Vanaf de tweede helft van 2018 kunnen organisaties met hun thuis Tenant in één geografie ook Power BI resources inrichten en gebruiken die zich in een andere geografie bevinden. In dit document wordt deze functie aangeduid als **Meerdere geografische gebieden**.

Het meest actuele en primaire artikel voor multi-geo-informatie is het artikel [multi-geo-ondersteuning configureren voor Power bi Premium](service-admin-premium-multi-geo.md) . 

Er zijn meerdere technische details die in de context van lokale wetten en voor schriften moeten worden geëvalueerd wanneer ze in verschillende geografische grafieken worden uitgevoerd. Deze informatie omvat het volgende:

- Een uitvoerings laag voor externe query's wordt gehost in de externe capaciteits regio, om ervoor te zorgen dat het gegevens model, de caches en de meeste gegevens verwerking in het gebied externe capaciteit blijven. Er zijn enkele uitzonde ringen, zoals beschreven in het artikel over [meerdere geo-Power bi Premium](service-admin-premium-multi-geo.md) .
- Een query tekst in de cache en het overeenkomstige resultaat dat is opgeslagen in een externe regio, blijft in die regio in de rest, maar andere gegevens in de door Voer kunnen echter tussen meerdere geografi worden weer gegeven.
- PBIX-of XLSX-bestanden die zijn gepubliceerd (geüpload) naar een multi-geo-capaciteit van de Power BI-service, kunnen ertoe leiden dat een kopie tijdelijk wordt opgeslagen in Azure Blob Storage in de Tenant regio van Power BI. In dergelijke gevallen worden de gegevens versleuteld met behulp van Azure Storage-service versleuteling (SSE) en wordt de kopie gepland voor garbagecollection zodra de verwerking van de bestands inhoud en de overdracht naar de externe regio is voltooid. 
- Bij het verplaatsen van gegevens tussen regio's in een multi-geografische omgeving, wordt het exemplaar van de gegevens in de bron regio binnen 7-30 dagen verwijderd. 

### <a name="datacenters-and-locales"></a>Datacenters en landinstellingen

Power BI wordt aangeboden in bepaalde regio's, op basis van waar de Power BI-clusters in regionale datacenters worden geïmplementeerd. Microsoft wil de Power BI-infrastructuur uitbreiden naar extra datacenters.

De volgende koppelingen bieden aanvullende informatie over Azure-datacenters.

- [Azure-regio's](https://azure.microsoft.com/regions/): informatie over de wereldwijde aanwezigheid en locaties van Azure
- [Azure-services per regio](https://azure.microsoft.com/regions/#services): een volledig overzicht van Azure-services (infrastructuurservices en platformservices) die door Microsoft in elke regio beschikbaar worden gesteld.

Op dit moment is de Power BI-service beschikbaar in bepaalde regio's, zoals beschreven in het [vertrouwens centrum van micro soft](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Via de volgende koppeling ziet u een overzicht van de Power BI-datacenters. Beweeg de cursor boven een regio om de hier gevestigde datacenters te zien:

* [Power BI-datacenters](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)

Microsoft biedt ook datacenters voor onafhankelijke clouds. Zie [Nationale Power BI-clouds](https://powerbi.microsoft.com/clouds/) voor meer informatie over de beschikbaarheid van de Power BI-service voor nationale clouds.

Zie [Microsoft Trust Center](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where) voor meer informatie over waar uw gegevens worden opgeslagen en hoe deze worden gebruikt. Toezeggingen over de locatie van data-at-rest van klanten zijn te vinden in de **voorwaarden voor gegevensverwerking** van de [voorwaarden voor Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31).

## <a name="user-authentication"></a>Verificatie van de gebruiker

De gebruikersverificatie voor de Power BI-service bestaat uit een reeks aanvragen, antwoorden en omleidingen tussen de browser van de gebruiker en de Power BI-service of de Azure-services die worden gebruikt door Power BI. Met deze reeks wordt het proces van gebruikersverificatie in Power BI beschreven. Zie [Een aanmeldingsmodel kiezen voor Office 365](https://blogs.office.com/2014/05/13/choosing-a-sign-in-model-for-office-365/) voor meer informatie over opties voor gebruikersverificatiemodellen van bedrijven (aanmeldingsmodellen).

### <a name="authentication-sequence"></a>Verificatiereeks

De gebruikersverificatiereeks voor de Power BI-service vindt plaats zoals wordt beschreven in de volgende stappen die in de volgende afbeeldingen worden geïllustreerd.

1. Een gebruiker initieert een verbinding met de Power BI-service vanuit een browser, door het Power BI adres in de adres balk te typen (zoals `https://app.powerbi.com`) of door _Aanmelden_ te selecteren op de Power bi landings pagina (https://powerbi.microsoft.com). De verbinding wordt tot stand gebracht met behulp van TLS 1.2 en HTTPS, en bij alle verdere communicatie tussen de browser en de Power BI-service wordt HTTPS gebruikt. De aanvraag wordt verzonden naar **Azure Traffic Manager**.

2. **Azure Traffic Manager** controleert de DNS-record van de gebruiker om te bepalen wat het dichtstbijzijnde datacenter is waar Power BI is geïmplementeerd, en reageert op de DNS met het IP-adres van het WFE-cluster waar de gebruiker naartoe moet worden gestuurd.

3. De gebruiker wordt vervolgens door WFE omgeleid naar de aanmeldingspagina voor Microsoft Online Services.

    ![Verificatiereeks](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

1. Zodra de gebruiker is geverifieerd, wordt deze met de aanmeldingspagina omgeleid naar het eerder vastgestelde dichtstbijzijnde **WFE-cluster** van de Power BI-service.

2. De browser verzendt een cookie die is verkregen van de geslaagde aanmelding voor Microsoft Online Services die is gecontroleerd door de **ASP.NET-service** binnen het **WFE-cluster**.

3. Het WFE-cluster controleert bij de service **Azure Active Directory** (**AAD**) om het Power BI-service-abonnement van de gebruiker te verifiëren en om een AAD-beveiligingstoken op te halen. Als AAD een geslaagde verificatie van de gebruiker en een AAD-beveiligingstoken retourneert, raadpleegt het WFE-cluster de **Power BI**** Global Service** die een lijst met tenants en hun Power BI-back-endclusterlocaties onderhoudt, en wordt bepaald welk Power BI-servicecluster de tenant van de gebruiker bevat. Vervolgens wordt de gebruiker door het WFE-cluster omgeleid naar het Power BI-cluster waar de tenant zich bevindt en wordt een verzameling items naar de browser van de gebruiker geretourneerd:

      - Het **AAD-beveiligingstoken**
      - **Sessiegegevens**
      - Het webadres van het **back-endcluster** waarmee de gebruiker kan communiceren en werken

1. De browser van de gebruiker neemt vervolgens contact op met de opgegeven Azure CDN (of voor bepaalde bestanden de WFE) voor het downloaden van de verzameling opgegeven algemene bestanden die nodig zijn voor de interactie van de browser met de Power BI-service. De browserpagina bevat dan tijdens de duur van de browsersessie van de Power BI-service het AAD-token, sessiegegevens, de locatie van het gekoppelde back-endcluster en de verzameling bestanden die zijn gedownload uit het Azure CDN- en WFE-cluster.

![Azure CDN-interactie](media/whitepaper-powerbi-security/powerbi-security-whitepaper_09.png)

Zodra deze items zijn voltooid, maakt de browser contact met het opgegeven back-endcluster en wordt de interactie van de gebruiker met de Power BI-service gestart. Vanaf dat moment vinden alle aanroepen naar de Power BI-service plaats met het opgegeven back-endcluster en bevatten alle aanroepen het AAD-token van de gebruiker. Het AAD-token heeft een time-out van één uur; om toegang te houden vernieuwt de WFE het token regelmatig als een gebruikerssessie geopend blijft.

## <a name="data-storage-and-movement"></a>Gegevensopslag en -verplaatsing

In de Power BI-service zijn gegevens _data-at-rest_ (gegevens beschikbaar voor een Power BI-gebruiker waarmee op dat moment niet wordt gewerkt) of gegevens _in verwerking_ (bijvoorbeeld query's die worden uitgevoerd, gegevensverbindingen en modellen waarmee wordt gewerkt, gegevens en/of modellen die worden geüpload naar de Power BI-service, en andere acties die gebruikers of de Power BI-service uitvoeren voor gegevens die actief worden geopend of bijgewerkt). Gegevens die worden verwerkt, worden aangeduid als _gegevens in verwerking_. Data-at-rest in Power BI is versleuteld. Gegevens die onderweg zijn (dit zijn gegevens die worden verzonden of ontvangen door de Power BI-service) zijn eveneens versleuteld.

Ook worden gegevens met de Power BI-service verschillend beheerd, afhankelijk van of de gegevens worden geopend met een **DirectQuery** of worden geïmporteerd. Dus er zijn twee soorten gebruikersgegevens voor Power BI: gegevens die worden gebruikt door DirectQuery en gegevens die niet worden gebruikt door DirectQuery.

Een **DirectQuery** is een query waarvoor een query van een Power BI-gebruiker is omgezet van de DAX-taal (Data Analysis Expressions) van Microsoft (dit is de taal die wordt gebruikt door Power BI en andere Microsoft-producten om query's te maken) in de systeemeigen gegevenstaal van de gegevensbron (zoals T-SQL of andere systeemeigen databasetalen). De gegevens die zijn gekoppeld aan een DirectQuery, worden alleen met een verwijzing opgeslagen, wat betekent dat de brongegevens niet zijn opgeslagen in Power BI wanneer de DirectQuery niet actief is (met uitzondering van visualisatiegegevens die worden gebruikt om dashboards en rapporten weer te geven, zoals wordt beschreven in het onderstaande gedeelte _Gegevens in verwerking (gegevensverplaatsing)_ ). In plaats hiervan worden verwijzingen naar DirectQuery-gegevens opgeslagen zodat deze gegevens kunnen worden gebruikt wanneer de DirectQuery wordt uitgevoerd. Een DirectQuery bevat alle benodigde informatie voor het uitvoeren van de query, met inbegrip van de verbindingsreeks en de referenties die worden gebruikt voor toegang tot de gegevensbronnen, waardoor de DirectQuery verbinding kan maken met de opgenomen gegevensbronnen voor automatische vernieuwingen. Bij een DirectQuery wordt de informatie over onderliggende gegevensmodellen opgenomen in de DirectQuery.

Een query voor een gegevensset voor importeren bestaat uit een verzameling DAX-query's die _niet_ rechtstreeks kunnen worden omgezet naar de systeemeigen taal van onderliggende gegevensbronnen. Importeerquery's bevatten geen referenties voor de onderliggende gegevens en de onderliggende gegevens worden in de Power BI-service geladen, tenzij het om on-premises gegevens gaat die worden gebruikt via een [Power BI Gateway](service-gateway-onprem.md), waarbij de query alleen verwijzingen naar on-premises gegevens opslaat.

In de volgende tabel worden Power BI-gegevens beschreven op basis van het querytype dat wordt gebruikt. Een **X** geeft aan dat er Power BI-gegevens aanwezig zijn wanneer u het bijbehorende querytype gebruikt.


|  |Importeren  |DirectQuery  |Live Connect  |
|---------|---------|---------|---------|
|Schema     |     X    |    X     |         |
|Rijgegevens     |    X     |         |         |
|Plaatsen van visuele gegevens in het cachegeheugen     |    X     |     X    |    X     |

Het verschil tussen een DirectQuery en andere query's bepaalt hoe de Power BI-service data-at-rest verwerkt en of de query zelf is versleuteld. De volgende gedeelten bevatten een beschrijving van data-at-rest en van gegevens die worden verplaatst. Hierin worden de versleuteling, de locatie en het proces voor het verwerken van gegevens uitgelegd.

### <a name="data-at-rest"></a>Data-at-rest

Bij data-at-rest worden gegevenssets, rapporten en dashboardtegels met de Power BI-service opgeslagen zoals wordt beschreven in de volgende subgedeelten. Zoals eerder vermeld, is data-at-rest in Power BI versleuteld. ETL staat voor Extract, Transform en Load (uitpakken, transformeren en laden) in de volgende gedeelten.

#### <a name="encryption-keys"></a>Versleutelingssleutels

- De versleutelingssleutels voor Azure Blob-sleutels worden versleuteld opgeslagen in Azure Key Vault.
- De versleutelingssleutels voor Azure SQL Database TDE-technologie worden door Azure SQL zelf beheerd.
- De versleutelingssleutel voor de service Gegevensverplaatsing en on-premises gegevensgateway worden opgeslagen:
  - In de on-premises gegevensgateway in de infrastructuur van de klant voor on-premises gegevensbronnen
  - In de gegevensverplaatsingsrol voor gegevensbronnen in de cloud

De versleutelings sleutel voor inhoud (CEK) die wordt gebruikt voor het versleutelen van de Microsoft Azure Blob Storage is een wille keurig gegenereerd 256-bits sleutel. Het algoritme dat door de CEK wordt gebruikt voor het versleutelen van de inhoud is AES\_CBC\_256.

De KEK (Key Encryption Key, sleutel van versleutelingssleutel) die wordt gebruikt om vervolgens de CEK te versleutelen, is een vooraf gedefinieerde 256-bits sleutel. Het algoritme van KEK om de CEK te versleutelen is A256KW.

Gatewayversleutelingssleutels op basis van de herstelsleutel verlaten nooit een on-premises infrastructuur. Power BI heeft geen toegang tot de versleutelde on-premises referentiewaarden en kan deze referenties niet onderscheppen; webclients versleutelen de referentie met een openbare sleutel die is gekoppeld aan de specifieke gateway waarmee wordt gecommuniceerd.

Voor gegevensbronnen in de cloud versleutelt de gegevensverplaatsingsrol versleutelingssleutels met [Always Encrypted](https://msdn.microsoft.com/library/mt163865.aspx)-methoden. Zie de [Always Encrypted-databasefunctie](https://msdn.microsoft.com/library/mt163865.aspx) voor meer informatie.

#### <a name="datasets"></a>Gegevenssets

1. Metagegevens (tabellen, kolommen, metingen, berekeningen, verbindingsreeksen enzovoort)

    a. Voor on-premises Analysis Services wordt niets in de service opgeslagen, met uitzondering van een verwijzing naar deze database die versleuteld is opgeslagen in Azure SQL.

    b. Alle andere metagegevens voor ETL, DirectQuery en pushgegevens worden versleuteld en opgeslagen in Azure Blob Storage.

1. Referenties voor de oorspronkelijke gegevensbronnen
  
      a. On-premises Analysis Services: er zijn geen referenties nodig en daarom worden er geen referenties opgeslagen.

      b. DirectQuery - Dit verschilt. Als het model rechtstreeks in de service is gemaakt, wordt het in de verbindingsreeks opgeslagen en versleuteld in Azure Blob. Als het model uit Power BI Desktop is geïmporteerd, worden de referenties versleuteld opgeslagen in Azure SQL Database van de gegevensverplaatsing. De versleutelingssleutel wordt op de machine opgeslagen waarop de gateway op de infrastructuur van de klant wordt uitgevoerd.

      c. Gepushte gegevens - niet van toepassing

      d. ETL

      - Voor **Salesforce** of **OneDrive**: de vernieuwingstokens worden versleuteld opgeslagen in de Azure SQL Database van de Power BI-service.
      - Anders:
        - Als de gegevensset is ingesteld voor vernieuwing, worden de referenties versleuteld opgeslagen in de Azure SQL Database voor gegevensverplaatsing. De versleutelingssleutel wordt op de machine opgeslagen waarop de gateway op de infrastructuur van de klant wordt uitgevoerd.
        - Als de gegevensset is niet ingesteld voor vernieuwing, worden er geen referenties opgeslagen voor de gegevensbronnen

1. Gegevens

    a. Analysis Services on-premises en DirectQuery - Niets wordt opgeslagen in de Power BI-service.

    b. ETL - Versleuteld in Azure Blob-opslag, maar voor alle gegevens die momenteel in de Azure Blob-opslag van de Power BI-service staan, wordt gebruikgemaakt van [Azure Storage Service Encryption (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), ook wel 'versleuteling aan de serverzijde' genoemd. SSE wordt ook gebruikt bij gebruik van meerdere geografische gebieden.

    c. Push data v1 - Versleuteld opgeslagen in Azure Blob-opslag, maar voor alle gegevens die momenteel in de Azure Blob-opslag van de Power BI-service staan, wordt gebruikgemaakt van [Azure Storage Service Encryption (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), ook wel 'versleuteling aan de serverzijde' genoemd. SSE wordt ook gebruikt bij gebruik van meerdere geografische gebieden. Push data v1 zijn stopgezet vanaf 2016. 

    d. Push data v2 - Versleuteld opgeslagen in Azure SQL.

Bij Power BI wordt gebruikgemaakt van versleuteling aan de clientzijde en Cipher Block Chaining (CBC) met een geavanceerde versleutelingsnorm (AES) om de Azure Blob-opslag te versleutelen. U kunt [hier](https://azure.microsoft.com/documentation/articles/storage-client-side-encryption/) meer lezen over versleuteling aan de clientzijde.

Power BI biedt op de volgende manieren bewaking van de gegevensintegriteit:

* Bij data-at-rest in Azure SQL maakt Power BI gebruik van dbcc, TDE en constante controlesommen voor pagina's. Dit is onderdeel van het systeemeigen SQL-aanbod.

* Bij data-at-rest in Azure Blob-opslag maakt Power BI gebruik van versleuteling aan de clientzijde en HTTPS voor het overdragen van gegevens naar de opslag. Er wordt ook gebruikgemaakt van integriteitscontroles bij het ophalen van gegevens. U leest [hier](https://azure.microsoft.com/documentation/articles/storage-security-guide/) meer over de Azure Blob-opslagbeveiliging.

#### <a name="reports"></a>Rapporten

1. Metagegevens (rapportdefinitie)

   a. Rapporten kunnen Excel voor Office 365-rapporten of Power BI-rapporten zijn. Het volgende is van toepassing voor metagegevens, afhankelijk van het type rapport:
        
    &ensp; &ensp; een. Meta gegevens van Excel-rapporten worden als versleuteld opgeslagen in SQL Azure. Meta gegevens worden ook opgeslagen in Office 365.

    &ensp; &ensp; b. Power BI-rapporten worden versleuteld opgeslagen in Azure SQL database.

2. Statische gegevens

   Statische gegevens zijn onder andere artefacten zoals achtergrond afbeeldingen en visuele elementen van Power BI.

    &ensp; &ensp; een. Bij rapporten die zijn gemaakt met Excel voor Office 365 wordt er niets opgeslagen.

    &ensp; &ensp; b. Bij Power BI-rapporten worden de statische gegevens opgeslagen en versleuteld in Azure Blob-opslag.

3. Caches

    &ensp; &ensp; een. Bij rapporten die zijn gemaakt met Excel voor Office 365 wordt er niets in de cache opgeslagen.

    &ensp; &ensp; b. Bij Power BI-rapporten worden de gegevens van weergegeven visuals versleuteld in de cache van Azure SQL Database opgeslagen.
 

4. Originele Power BI Desktop- (.pbix) of Excel-bestanden (.xlsx) die zijn gepubliceerd naar Power BI

    Soms wordt er een kopie of een schaduwkopie van de xlsx- of pbix-bestanden opgeslagen in de Azure Blob-opslag van Power BI. Als dit gebeurt, worden de gegevens versleuteld. Bij al deze rapporten die zijn opgeslagen in de Power BI-service in Azure Blob-opslag wordt gebruikgemaakt van [Azure Storage Service Encryption (SSE)](https://docs.microsoft.com/azure/storage/common/storage-service-encryption), ook wel 'versleuteling aan de serverzijde' genoemd. SSE wordt ook gebruikt bij gebruik van meerdere geografische gebieden.

#### <a name="dashboards-and-dashboard-tiles"></a>Dashboards en dashboardtegels

1. Caches - De gegevens die nodig zijn voor de visuals op het dashboard worden meestal in de cache opgeslagen en versleuteld in Azure SQL Database. Andere tegels, zoals vastgemaakte visuals uit Excel of de SQL Server Reporting Services (SSRS) worden als afbeeldingen opgeslagen in Azure Blob; deze worden ook versleuteld.

2. Statische gegevens: Dit omvat artefacten zoals achtergrond afbeeldingen en Power BI visuele elementen die zijn opgeslagen, versleuteld in Azure Blob-opslag.

Microsoft beheert, ongeacht de versleutelingsmethode die wordt gebruikt, de sleutelversleuteling namens klanten. Dit gebeurt in een geheim archief of in Azure Key Vault.

### <a name="data-transiently-stored-on-non-volatile-devices"></a>Gegevens die tijdelijk worden opgeslagen op niet-vluchtige apparaten

Niet-vluchtige apparaten zijn apparaten die geheugen hebben dat zonder constante kracht blijft. Hierna worden gegevens beschreven die tijdelijk worden opgeslagen op niet-vluchtige apparaten. 

#### <a name="datasets"></a>Gegevenssets

1. Metagegevens (tabellen, kolommen, metingen, berekeningen, verbindingsreeksen enzovoort)

2. Sommige schemagerelateerde artefacten kunnen gedurende een beperkte periode worden opgeslagen op de schijf van de rekenknooppunten. Sommige artefacten kunnen ook gedurende een beperkte periode niet-versleuteld worden opgeslagen in Azure Redis Cache.

3. Referenties voor de oorspronkelijke gegevensbronnen

    a. Analysis Services on-premises - Niets wordt opgeslagen

    b. DirectQuery - Dit verschilt. Als het model rechtstreeks in de service is gemaakt, wordt het versleuteld in de verbindingsreeks opgeslagen en wordt de versleutelingssleutel niet-versleuteld opgeslagen op dezelfde locatie (naast de versleutelde informatie). Als het model uit Power BI Desktop is geïmporteerd, worden de referenties niet opgeslagen op niet-vluchtige apparaten.

    > [!NOTE]
    > De functie voor het maken van het model voor de service is niet meer vanaf 2017.

    c. Gepushte gegevens - Geen (niet van toepassing)

    d. ETL - geen (niets wordt opgeslagen op het rekenknooppunt, of anders dan wordt uitgelegd in het gedeelte **Data-at-rest** hierboven)
4. Gegevens

    Sommige gegevensartefacten kunnen gedurende een beperkte periode worden opgeslagen op de schijf van de rekenknooppunten.

### <a name="data-in-process"></a>Gegevens in verwerking

Gegevens zijn 'in verwerking' wanneer ze actief worden gebruikt door een gebruiker of toegankelijk zijn. Gegevens zijn bijvoorbeeld in verwerking wanneer een gebruiker een gegevensset opent of een dashboard of rapport reviseert of bewerkt, wanneer er wordt vernieuwd of wanneer gegevens op andere manieren worden gebruikt. Als een van deze gebeurtenissen zich voordoet en er sprake is van gegevens in verwerking, wordt met de **gegevensrol** in de Power BI-service een Analysis Services-database (AS) gemaakt in het geheugen en wordt de gegevensset naar die Analysis Services-database in het geheugen geladen. Of de gegevensset nu is gebaseerd op een DirectQuery of niet, gegevens die naar de AS-database worden geladen, zijn niet versleuteld zodat er met de **gegevensrol** toegang toe kan worden verkregen. Ze worden voor verder gebruik ondergebracht in het geheugen tot de Power BI-service de gegevensset niet meer nodig heeft. Bij klanten met een Power BI Premium-abonnement maakt Power BI een Analysis Services-database (AS) in het geheugen van de afzonderlijk ingerichte virtuele Power BI-machines van de klant.

Zodra er iets met de gegevens wordt gedaan (dit omvat ook het laden van de gegevens naar Power BI), kan het zijn dat de Power BI-service de visualisatiegegevens in de cache van een versleutelde **Azure SQL-database** opslaat, ongeacht of de gegevensset is gebaseerd op een DirectQuery.

Voor het bewaken van de integriteit van gegevens in verwerking maakt Power BI gebruikt van HTTPS, TCP/IP en TLS; zo bent u er zeker van dat gegevens worden versleuteld en de integriteit tijdens het transport wordt behouden.

## <a name="user-authentication-to-data-sources"></a>Gebruikersverificatie voor gegevensbronnen

Met elke gegevens bron brengt een gebruiker een verbinding tot stand op basis van hun aanmelding en opent deze de gegevens met deze referenties. Gebruikers kunnen vervolgens query's, dashboards en rapporten maken op basis van de onderliggende gegevens.

Als een gebruiker query's, dashboards, rapporten of een visualisatie deelt, moet worden bekeken of de onderliggende gegevensbronnen ondersteuning bieden voor beveiliging op rolniveau (RLS) om te bepalen of toegang kan worden verkregen tot die gegevens en visualisaties.

Als een onderliggende gegevensbron geschikt is voor **de beveiliging op rolniveau (RLS) van Power BI**, past de Power BI-service die beveiliging op rolniveau toe. Gebruikers met onvoldoende referenties voor toegang tot de onderliggende gegevens (voor bijvoorbeeld via een query in een dashboard, rapport of ander gegevensartefact) krijgen alleen de gegevens te zien waarvoor ze wel voldoende machtigingen hebben. Als een bepaalde gebruiker andere toegang tot de onderliggende gegevens heeft dan de gebruiker die het dashboard of rapport heeft gemaakt, worden in de visualisaties en andere artefacten alleen gegevens weergegeven op basis van het toegangsniveau van de gebruiker die ze bekijkt.

Als bij een gegevensbron RLS **niet** wordt toegepast, worden er Power BI-aanmeldingsreferenties toegepast op de onderliggende gegevensbron. Als er andere referenties zijn opgegeven bij het verbinden, worden die referenties toegepast. Als een gebruiker vanaf niet-RLS-gegevensbronnen gegevens naar de Power BI-service laadt, worden gegevens in Power BI opgeslagen zoals wordt beschreven in het gedeelte **Gegevens opslaan en verplaatsen** in dit document. Als er bij gegevensbronnen zonder RLS gegevens met andere gebruikers worden gedeeld (bijvoorbeeld via een dashboard of rapport) of als de gegevens worden vernieuwd, worden de oorspronkelijke referenties gebruikt voor het openen of weergeven van de gegevens.

![Beveiliging op rolniveau (RLS)](media/whitepaper-powerbi-security/powerbi-security-whitepaper_10.png)

We zullen het verschil tussen gegevensbronnen met en zonder RLS duidelijk proberen te maken: stel Sam maakt een rapport en een dashboard en deelt deze vervolgens met Abby en Ralph. Als de gegevensbronnen in het rapport en dashboard afkomstig zijn van bronnen die **geen** ondersteuning bieden voor RLS, kunnen Abby en Ralph de gegevens die Sam in het dashboard heeft opgegeven, zien (deze zijn geüpload naar de Power BI-service). Zij kunnen allebei aan de slag met de gegevens. Als Sam daarentegen een rapport en een dashboard maakt op basis van gegevensbronnen die wel ondersteuning bieden voor RLS en deze vervolgens met Abby en Ralph deelt, gebeurt het volgende wanneer Abby het dashboard wilt bekijken:

1. Omdat het dashboard afkomstig is van een RLS-gegevensbron, wordt bij dashboardvisualisaties kort het bericht &quot;Laden...&quot; weergegeven terwijl de Power BI-service een query naar de gegevensbron stuurt om de gegevensset op te halen die in de verbindingsreeks is opgegeven die is gekoppeld aan de onderliggende query van het dashboard.

2. De gegevens worden geopend en opgehaald op basis van de referenties en rol van Abby. Alleen de gegevens waarvoor Abby onvoldoende autorisatie heeft, worden in het dashboard en rapport weergegeven.

3. De visualisaties op het dashboard en uit het rapport worden weergegeven op basis van het rolniveau van Abby.

Als Ralph het gedeelde dashboard of rapport opent, worden op basis van zijn rolniveau dezelfde handelingen uitgevoerd.

## <a name="power-bi-mobile"></a>Power BI - Mobiel

Power BI-Mobiel is een verzameling apps die zijn ontworpen voor de drie primaire mobiele platforms: Android, iOS en Windows Mobile. De beveiligingsoverwegingen voor Power BI Mobile-apps worden onderverdeeld in twee categorieën:

* Apparaatcommunicatie
* De toepassing en gegevens op het apparaat

Voor **apparaatcommunicatie** communiceren alle toepassingen van Power BI - Mobiel met de Power BI-service en gebruiken dezelfde verbinding en verificatiereeksen als browsers, die eerder in dit technisch document uitgebreid zijn beschreven. In de Power BI Mobile-apps voor iOS en Android wordt een browsersessie in de app zelf geopend en in de mobiele app voor Windows wordt een broker geopend om het communicatiekanaal met Power BI tot stand te brengen.

De volgende tabel geeft een overzicht van de ondersteuning voor op certificaten gebaseerde verificatie (CBA) voor Power BI Mobile op basis van een platform voor mobiele apparaten:

| **CBA-ondersteuning** | **iOS** | **Android** | **Windows** |
| --- | --- | --- | --- |
| **Power BI** (aanmelden bij de service) | Ondersteund | Ondersteund | Niet ondersteund |
| **SSRS ADFS** (verbinding maken met SSRS-server) | Niet ondersteund | Ondersteund | Niet ondersteund |

Power BI Mobile-apps communiceren actief met de Power BI-service. Telemetrie wordt gebruikt voor het verzamelen van gebruiksstatistieken van de mobiele app en vergelijkbare gegevens, die worden verzonden naar services die worden gebruikt voor het controleren van gebruik en activiteit. Er worden geen gegevens verzonden met telemetriegegevens.

De Power BI-**app op het apparaat** slaat gegevens op het apparaat op voor het gebruik van de app:

* Azure Active Directory en vernieuwingstokens worden opgeslagen in een beveiligd mechanisme op het apparaat, waarvoor gebruik wordt gemaakt van beveiligingsmaatregelen die voldoen aan de industriestandaard.

* De gegevens worden opgeslagen in de cache op het apparaat, die niet direct door de app wordt versleuteld

* De instellingen worden ook niet-versleuteld opgeslagen op het apparaat, maar er worden geen gebruikersgegevens opgeslagen.

De gegevenscache van Power BI Mobile blijft twee weken op het apparaat staan of totdat de app wordt verwijderd, de gebruiker zich afmeldt bij Power BI Mobile of wanneer de gebruiker zich niet kan aanmelden (bijvoorbeeld doordat het token is verlopen of het wachtwoord is gewijzigd). De gegevenscache bevat dashboards en rapporten die eerder zijn geopend vanuit de Power BI Mobile-app.

Power BI Mobile-apps controleren geen mappen op het apparaat. 

Alle drie de platformen waarvoor Power BI Mobile beschikbaar is, bieden ondersteuning voor Microsoft Intune, een softwareservice voor het beheer van mobiele apparaten en toepassingen. Als Intune is ingeschakeld en geconfigureerd, worden gegevens op het mobiele apparaat versleuteld en kan de Power BI-app niet op een SD-kaart worden geïnstalleerd. [Meer informatie over Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="power-bi-security-questions-and-answers"></a>Beveiligingsvragen en -antwoorden voor Power BI

De volgende vragen zijn algemene beveiligingsvragen en -antwoorden voor Power BI. Deze zijn ingedeeld op basis van de datum waarop ze zijn toegevoegd aan dit technisch document, zodat u snel nieuwe vragen en antwoorden kunt bekijken wanneer dit document is bijgewerkt. De nieuwste vragen worden toegevoegd aan het einde van deze lijst.

**Hoe maken gebruikers verbinding met gegevensbronnen en hoe worden deze geopend tijdens het gebruik van Power BI?**

* **Power bi referenties en domein referenties:** Gebruikers melden zich aan bij Power BI met behulp van een e-mail adres. Wanneer een gebruiker probeert verbinding te maken met een gegevens bron, Power BI het e-mail adres van Power BI aanmelding als referenties door gegeven. Voor domeinverbonden resources (on-premises of in de cloud), wordt het e-mailadres voor aanmelding door de adreslijstservice vergeleken met een _user principal name_ ([UPN](https://msdn.microsoft.com/library/windows/desktop/aa380525(v=vs.85).aspx)) om te bepalen of er voldoende referenties zijn om toegang te verlenen. Voor organisaties die gebruikmaken van zakelijke e-mailadressen voor aanmelding bij Power BI (het e-mailadres dat ook wordt gebruikt voor aanmelding bij werkresources, zoals _david@contoso.com_ ), verloopt de toewijzing vlekkeloos. Voor organisatie die geen gebruikmaken van zakelijke e-mailadressen (zoals _david@contoso.onmicrosoft.com_ ), moet maptoewijzing worden uitgevoerd voor toegang tot on-premises resources met Power BI-aanmeldingsreferenties.

* **SQL Server Analysis Services en Power BI:** Voor organisaties die gebruikmaken van on-premises SQL Server Analysis Services, biedt Power BI de Power BI on-premises gegevens gateway (een **Gateway**, waarnaar wordt verwezen in vorige gedeelten).  De Power BI on-premises gegevensgateway kan beveiliging op rolniveau op gegevensbronnen (RLS) afdwingen. Zie **Gebruikersverificatie voor gegevensbronnen** eerder in dit document voor meer informatie over RLS. Zie [on-premises gegevens gateway](service-gateway-onprem.md)voor meer informatie over gateways.

  Bovendien kunnen organisaties Kerberos gebruiken voor de **eenmalige aanmelding** (SSO) en naadloos vanuit Power BI verbinding maken met on-premises gegevensbronnen, zoals SQL Server, SAP HANA en Teradata. Zie [**Kerberos gebruiken voor eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI**](https://docs.microsoft.com/power-bi/service-gateway-kerberos-for-sso-pbi-to-on-premises-data) voor meer informatie en de specifieke configuratievereisten.

* **Niet-domein verbindingen**: voor gegevens verbindingen die geen lid zijn van een domein en niet geschikt zijn voor beveiliging op rollen niveau, moet de gebruiker referenties opgeven tijdens de verbindings reeks, die Power bi vervolgens door gegeven aan de gegevens bron om de verbinding tot stand te brengen. Als er voldoende machtigingen zijn, worden de gegevens vanuit de gegevensbron in de Power BI-service geladen.

**Hoe worden gegevens overgedragen naar Power BI?**

* Alle gegevens die zijn aangevraagd en worden verzonden door Power BI, worden tijdens de overdracht versleuteld via HTTPS om verbinding te maken tussen de gegevensbron en de Power BI-service. Er wordt een beveiligde verbinding met de gegevensprovider gemaakt en de gegevens stromen pas in het netwerk nadat de verbinding tot stand is gebracht.

**Hoe worden rapporten, dashboards of modelgegevens in Power BI opgeslagen en zijn deze veilig?**

* Wanneer een gegevensbron wordt geopend, volgt de Power BI-service het proces dat eerder in dit document wordt beschreven in de sectie **Gegevensopslag en -verplaatsing**.

**Worden gegevens van webpagina's lokaal opgeslagen door clients?**

* Wanneer browserclients Power BI openen, stellen de webservers van Power BI de instructie _Cache-Control_ in op _no-store_. De instructie _no-store_ geeft browsers de opdracht om de webpagina die door de gebruiker wordt bekeken niet op te slaan in de cache of in de cachemap van de client.

**Hoe zit het met beveiliging op basis van rollen, het delen van rapporten of Dash boards en gegevens verbindingen? Hoe werkt dat in termen van toegang tot gegevens, het weer geven van Dash boards, toegang tot rapporten of vernieuwen?**

* Voor **niet-RLS** ingeschakelde gegevensbronnen geldt dat wanneer een dashboard, rapport of gegevensmodel wordt gedeeld met andere gebruikers via Power BI, de gegevens beschikbaar zijn voor gebruikers waarmee deze worden gedeeld voor weergave en gebruik. Power BI verifieert gebruikers *niet* opnieuw aan de hand van de oorspronkelijke bron van de gegevens; zodra de gegevens zijn geüpload naar Power BI, is de gebruiker die is geverifieerd aan de hand van de brongegevens verantwoordelijk voor de toegang tot de gegevens door gebruikers en groepen.

  Wanneer gegevensverbindingen worden gemaakt met een **RLS**-compatibele gegevensbron, zoals een Analysis Services-gegevensbron, worden alleen dashboardgegevens in de cache van Power BI opgeslagen. Telkens wanneer een rapport of gegevensset wordt weergegeven of geopend in Power BI die gebruikmaakt van gegevens uit de RLS-compatibele gegevensbron, opent de Power BI-service de gegevensbron om gegevens op te halen op basis van de referenties van de gebruiker. Als de gebruiker voldoende machtigingen heeft, worden de gegevens geladen in het rapport of gegevensmodel voor de gebruiker. Als de verificatie mislukt, wordt een fout weergegeven.

  Zie de sectie **Gebruikersverificatie voor gegevensbronnen** eerder in dit document voor meer informatie.

**Onze gebruikers maken steeds verbinding met dezelfde gegevens bronnen, waarvan sommige referenties zijn vereist die afwijken van de referenties van hun domein. Hoe kan het voor komen dat deze referenties worden ingevoerd telkens wanneer ze een gegevens verbinding maken?**

* Power BI ondersteunt de [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846). Hiermee kunnen gebruikers referenties voor meerdere verschillende gegevensbronnen maken en deze referenties vervolgens automatisch gebruiken voor toegang tot een van deze gegevensbronnen. Zie [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846) voor meer informatie.

**Hoe werken Power BI-groepen?**

* Met Power BI-groepen kunnen gebruikers in een team snel en eenvoudig samenwerken aan dashboards, rapporten en gegevensmodellen. Als u bijvoorbeeld een Power BI-groep hebt met iedereen in uw directe team, kunt u eenvoudig samenwerken met uw team door de groep in Power BI te selecteren. Power BI-groepen werken hetzelfde als Office 365 universele groepen (die u kunt [maken](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1) en [beheren](https://support.office.com/Article/View-create-and-delete-Groups-in-the-Office-365-admin-center-a6360120-2fc4-46af-b105-6a04dc5461c7) en waar u [meer informatie](https://support.office.com/Article/Manage-Group-membership-in-the-Office-365-admin-center-e186d224-a324-4afa-8300-0e4fc0c3000a) over kunt vinden), en maken gebruik van dezelfde verificatiemechanismen die worden gebruikt in Azure Active Directory om gegevens te beveiligen. U kunt [groepen maken in Power BI](https://support.powerbi.com/knowledgebase/articles/654250) of een universele groep in het Microsoft 365-beheercentrum maken. Dit heeft hetzelfde resultaat.

  Voor gegevens die worden gedeeld met Power BI-groepen gelden dezelfde veiligheidsoverwegingen als voor andere gedeelde gegevens in Power BI. Voor **niet-RLS** gegevensbronnen verifieert Power BI gebruikers **niet** opnieuw aan de hand van de oorspronkelijke gegevensbron; zodra de gegevens zijn geüpload naar Power BI, is de gebruiker die is geverifieerd aan de hand van de brongegevens verantwoordelijk voor de toegang tot de gegevens door gebruikers en groepen. Zie de sectie **Gebruikersverificatie voor gegevensbronnen** eerder in dit document voor meer informatie.

  Lees meer informatie over [Groepen in Power BI](https://support.powerbi.com/knowledgebase/articles/654247).

**Welke poorten worden gebruikt door de on-premises gegevens gateway en de persoonlijke gateway? Zijn er domein namen die moeten worden toegestaan voor connectiviteits doeleinden?**

* Het gedetailleerde antwoord op deze vraag is beschikbaar via de volgende koppeling: [Gateway poorten](/data-integration/gateway/service-gateway-communication#ports)

**Hoe worden er herstel sleutels gebruikt en waar worden deze opgeslagen bij het opslaan van de on-premises gegevens gateway? Hoe zit het met beveiligd referentie beheer?**

* Tijdens de installatie en configuratie van de gateway geeft de beheerder een **herstelsleutel** voor de gateway op. Deze **herstel sleutel** wordt gebruikt voor het genereren van een sterke **AES** symmetrische sleutel. Er wordt ook een asymmetrische **RSA** -sleutel gemaakt.

    De gegenereerde sleutels (**RSA** en **AES**) worden opgeslagen in een bestand op de lokale computer. Dit bestand is eveneens versleuteld. De inhoud van het bestand kan alleen worden ontsleuteld door de specifieke Windows-computer en uitsluitend door dat specifieke gatewayserviceaccount.

    Wanneer een gebruiker referenties van de gegevensbron invoert in de gebruikersinterface van de Power BI-service, worden de referenties versleuteld met de openbare sleutel in de browser. De gateway ontsleutelt de referenties met behulp van de persoonlijke RSA-sleutel en versleutelt deze opnieuw met een AES symmetrische sleutel voordat de gegevens worden opgeslagen in de Power BI-service. Door dit proces heeft de Power BI-service nooit toegang tot de niet-versleutelde gegevens.

**Welke communicatieprotocollen worden gebruikt door de on-premises gegevensgateway en hoe zijn deze beveiligd?**

* De gateway ondersteunt de volgende twee communicatieprotocollen:

  - **AMQP 1,0 – TCP + TLS**: voor dit protocol zijn de poorten 443, 5671-5672 en 9350-9354 vereist om te worden geopend voor uitgaande communicatie. Dit protocol heeft de voorkeur vanwege de lagere overhead aan communicatie.

  - **Https: Websockets via https + TLS**: voor dit protocol wordt alleen poort 443 gebruikt. De WebSocket wordt geïnitieerd door één HTTP CONNECT-bericht. Nadat het kanaal is ingesteld, is de communicatie in feite TCP + TLS. U kunt afdwingen dat de gateway dit protocol gebruikt door een instelling te wijzigen die wordt beschreven in het [artikel on-premises gateway](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

**Wat is de rol van Azure CDN in Power BI?**

* Zoals eerder vermeld, gebruikt Power BI het **Azure Content Delivery Network (CDN)** om de benodigde statische inhoud en bestanden op een efficiënte manier te distribueren naar gebruikers op basis van geografische landinstelling. Specifieker gezegd, de Power BI-service maakt gebruik van meerdere **CDN's** om de benodigde statische inhoud en bestanden op een efficiënte manier te distribueren naar gebruikers via het openbare internet. Deze statische bestanden bevatten productdownloads (zoals **Power BI Desktop**, de **on-premises gegevensgateway** of Power BI-apps van verschillende onafhankelijke serviceproviders), browserconfiguratiebestanden die worden gebruikt om volgende verbindingen met de Power BI-service te initiëren en tot stand te brengen, en de eerste, beveiligde Power BI-aanmeldingspagina.

  Op basis van informatie die tijdens een eerste verbinding met de Power BI-service wordt opgegeven, neemt de browser van een gebruiker contact op met de opgegeven Azure **CDN** (of voor bepaalde bestanden de **WFE**) voor het downloaden van de verzameling opgegeven algemene bestanden die nodig zijn voor de interactie van de browser met de Power BI-service. De browserpagina bevat dan tijdens de duur van de browsersessie van de Power BI-service het AAD-token, sessiegegevens, de locatie van het gekoppelde **back-endcluster** en de verzameling bestanden die zijn gedownload uit het Azure **CDN**- en **WFE**-cluster.

**Voor Power BI visuals voert micro soft een beveiligings-of privacy-evaluatie uit van de aangepaste Visual code voordat items naar de galerie worden gepubliceerd?**

* Aantal Het is de verantwoordelijkheid van de klant om te controleren en te bepalen of aangepaste visualcode betrouwbaar is. Alle aangepaste visualcode wordt in een sandbox-omgeving uitgevoerd zodat eventuele onjuiste code in een aangepaste visual geen nadelige invloed heeft op de rest van de Power BI-service.

**Zijn er andere Power BI-visuals waarmee gegevens buiten het klantnetwerk worden verzenden?**

* Ja. Met Bing Maps- en ESRI-visuals worden gegevens buiten de Power BI-service verzonden voor visuals die gebruikmaken van deze services.

**Voor sjabloon-apps voert micro soft een beveiligings-of privacy-evaluatie uit van de sjabloon-app voordat items naar de galerie worden gepubliceerd?**
* Aantal De uitgever van de app is verantwoordelijk voor de inhoud terwijl de verantwoordelijkheid van de klant kan controleren en bepalen of de uitgever van de sjabloon app moet worden vertrouwd. 

**Zijn er sjabloon-apps die informatie kunnen verzenden buiten het netwerk van de klant?**
* Ja. Het is de verantwoordelijkheid van de klant om het privacybeleid van de uitgever te controleren en te bepalen of de sjabloon-app moet worden geïnstalleerd op de Tenant. Bovendien is de uitgever verantwoordelijk voor een melding van het gedrag en de mogelijkheden van de app.

**Hoe zit het met data soevereiniteit? Kunnen we tenants inrichten in data centers die zich in specifieke geografies bevinden, om ervoor te zorgen dat gegevens de land grenzen niet behouden?**

* Sommige klanten in bepaalde geografische gebieden hebben de mogelijkheid om een tenant te maken in een nationale cloud waar de opslag en verwerking van gegevens gescheiden blijft van alle andere datacenters. De beveiliging van nationale clouds is iets anders omdat een afzonderlijke gegevensbeheerder namens Microsoft de nationale cloud met de Power BI-service uitvoert.

  Daarnaast kunnen klanten een tenant in een specifieke regio instellen, maar dergelijke tenants hebben geen afzonderlijke gegevensbeheerder van Microsoft. Prijzen voor nationale clouds verschillen van die voor de algemeen beschikbare commerciële Power BI-service. Zie [Nationale Power BI-clouds](https://powerbi.microsoft.com/clouds/) voor meer informatie over de beschikbaarheid van de Power BI-service voor nationale clouds.

**Hoe behandelen micro soft verbindingen voor klanten die Power BI Premium-abonnementen hebben? Zijn deze verbindingen anders dan die welke zijn ingesteld voor de niet-Premium Power BI-service?**

* Met de verbindingen voor klanten met Power BI Premium-abonnementen wordt een autorisatieproces van [Azure Business-to-Business (B2B)](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) geïmplementeerd waarbij Azure Active Directory (AD) wordt gebruikt voor toegangsbeheer en autorisatie. Verbindingen met Power BI Premium-resources van Power BI Premium-abonnees worden met Power BI net zo afgehandeld als voor elke andere Azure AD-gebruiker.

## <a name="conclusion"></a>Conclusie

De Power BI-service-architectuur is gebaseerd op twee clusters: het cluster Web Front End (WFE) en het back-endcluster. Het cluster WFE verantwoordelijk is voor de eerste verbinding en verificatie met de Power BI-service. Eenmaal geverifieerd, verwerkt de Back-End alle daaropvolgende gebruikersinteracties. Power BI maakt gebruik van Azure Active Directory (AAD) om gebruikers-id's op te slaan en beheren en beheert de opslag van gegevens en metagegevens met respectievelijk Azure Blob en Azure SQL Database.

Gegevensopslag en gegevensverwerking in Power BI verschillen al naar gelang de gegevens worden geopend met behulp van een DirectQuery en zijn ook afhankelijk van of de gegevensbronnen zich in de cloud of on-premises bevinden. Power BI is tevens geschikt voor het afdwingen van beveiliging op rolniveau (RLS) en communiceert met gateways die toegang bieden tot on-premises gegevens.

## <a name="feedback-and-suggestions"></a>Feedback en suggesties

We stellen uw feedback op prijs. We horen graag of u suggesties hebt voor verbeteringen, aanvullingen of verduidelijkingen van dit technische document of van andere inhoud met betrekking tot Power BI. Stuur uw suggesties naar [pbidocfeedback@microsoft.com](mailto:pbidocfeedback@microsoft.com).

## <a name="additional-resources"></a>Aanvullende resources

Raadpleeg de volgende resources voor meer informatie over Power BI.

- [Groepen in Power BI](https://support.powerbi.com/knowledgebase/articles/654247)
- [Getting Started with Power BI Desktop](https://support.powerbi.com/knowledgebase/articles/471664) (Aan de slag met Power BI Desktop)
- [Overzicht van de REST API voor Power BI](https://msdn.microsoft.com/library/dn877544.aspx)
- [Naslag voor API van Power BI](https://msdn.microsoft.com/library/mt147898.aspx)
- [On-premises gegevensgateway](service-gateway-onprem.md)
- [Power BI National Clouds](https://powerbi.microsoft.com/clouds/)
- [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
- [Kerberos gebruiken voor eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI](service-gateway-sso-overview.md)
