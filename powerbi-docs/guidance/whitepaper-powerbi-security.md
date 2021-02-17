---
title: Technisch document Power BI beveiliging
description: Een technisch document waarin de beveiligings architectuur en-implementatie voor Power BI worden beschreven en beschreven.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/11/2021
LocalizationGroup: Conceptual
ms.openlocfilehash: 9752eddb82fa8f612b9d740cf010c0649ba5b3f8
ms.sourcegitcommit: 803653e8aa79ed38ec555c27c13b3b6835f98a5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/17/2021
ms.locfileid: "100569734"
---
# <a name="power-bi-security-white-paper"></a>Technisch document Power BI beveiliging

**Samen vatting:** Power BI is een online software service (*SaaS* of software als een service) van micro soft waarmee u eenvoudig en snel Self-Service Business Intelligence-Dash boards, rapporten, gegevens sets en visualisaties kunt maken. Met Power BI kunt u verbinding maken met veel verschillende gegevensbronnen, gegevens via deze verbindingen combineren en vormgeven, en vervolgens rapporten en dashboards maken die met anderen kunnen worden gedeeld.

**Schrijvers:** Yitzhak Kesselman, padie Osborne, Matt Neely, Tony Bencic, Srinivasan Turuvekere, Cristian Petculescu, Adi Regev, Naveen Sivaraj, ben Glastein, Evgeny Tshiorny, Arthi Ramasubramanian Iyer, sid Jayadevan, Ronald Chang, ori Eduar, Anton Fritz, Idan Sheinberg, Loek Gilad, Sagiv Hadaya, Paul Inbar, Igor Uzhviev, Michael Roth, Janny Tarquino, Gennady PATS, Orion Lee, Yury Berezansky, Maya Shenhav, romit Chattopadhyay, Yariv Maimon, Bogdan Crivat

**Technische revisoren:** Cristian Petculescu, Amir Netz, Sergei Gundorov

**Van toepassing op:** Power BI SaaS, Power BI Desktop, Power BI Premium, Power BI Embedded Analytics Power BI-Mobiel

> [!NOTE]
> U kunt dit technisch document opslaan of afdrukken door **afdrukken** te selecteren in uw browser en vervolgens **Opslaan als PDF** te selecteren.

## <a name="introduction"></a>Introductie

Power BI is een online softwareservice-aanbod (*SaaS* of software als een dienst) van Microsoft waarmee u snel en eenvoudig selfservice Business Intelligence-dashboards, -rapporten, -gegevenssets en -visualisaties (BI) kunt maken. Met Power BI kunt u verbinding maken met veel verschillende gegevensbronnen, gegevens via deze verbindingen combineren en vormgeven, en vervolgens rapporten en dashboards maken die met anderen kunnen worden gedeeld.

De wereld is snel te wijzigen. organisaties gaan door met een versnelde digitale trans formatie en we zien een grote toename in de externe werk belasting, een verhoogde vraag van de klant voor onlineservices en uitgebreid gebruik van geavanceerde technologieën in de activiteiten en de besluit vorming van uw bedrijf. En dit alles wordt mogelijk gemaakt door de Cloud.

Omdat de overgang naar de Cloud is gewijzigd van een trickle naar een stroom, en met de nieuwe, beschik bare surface area die erin wordt geleverd, vragen meer en meer bedrijven *Hoe veilig mijn gegevens in de Cloud is?* en *welke end-to-end-beveiliging beschikbaar is om te voor komen dat mijn gevoelige gegevens worden gelekt?* En voor de BI-platforms die vaak een deel van de meest strategische informatie in de onderneming afhandelen, zijn deze vragen twee belang rijk.

De tien oude basis principes van de beveiliging op object niveau en op rijniveau van het BI-beveiligings model: en nog steeds belang rijker niet langer voldoende voor het leveren van de beveiliging die nodig is in het Cloud-tijd perk. In plaats daarvan moeten organisaties zoeken naar een in de Cloud ingebouwde, op meerdere lagen gebaseerde, uitgebreide beveiligings oplossing voor hun business intelligence gegevens.

Power BI is ontwikkeld om de toonaangevende volledige en hermetisch beveiligde beveiliging voor gegevens te bieden. Het product heeft de hoogste beveiligings classificaties behaald die beschikbaar zijn in de branche, en veel nationale veiligheids instanties, financiële instellingen en gezondheids zorgdiensten belasten zich met hun meest gevoelige informatie.

Alles begint met de basis. Na een ruwe periode in de vroege 2000s heeft micro soft grote investeringen gemaakt om de beveiligings problemen op te lossen, en in de volgende decennia is een zeer krachtige beveiligings stack gemaakt die zo diep als de machine op de computer in de chip-BIOS-kernel wordt uitgebreid en alle mogelijkheden tot eind gebruikers uitbreidt. Deze diepe investeringen blijven bestaan en vandaag meer dan 3.500 micro soft-technici zijn bezig met het bouwen en verbeteren van de beveiligings stack van micro soft en het proactief verpakken van de steeds verschuivende bedreigings mogelijkheden. Met miljarden computers, biljoenen aan aanmeldingen en talloze Zettabytes gegevens die aan de bescherming van micro soft zijn toevertrouwd, beschikt het bedrijf nu over de meest geavanceerde beveiligings stack in de technische branche en wordt deze wereld wijd gezien als algemene leider bij het bestrijden van kwaad aardige actors.

Power BI bouwt voort op deze zeer krachtige basis. Er wordt gebruikgemaakt van dezelfde beveiligings stack die Azure het beste heeft behaald om de meest gevoelige gegevens van de wereld te bedienen en te beschermen, en deze wordt geïntegreerd met de meest geavanceerde hulp middelen voor gegevens bescherming en-naleving van Microsoft 365. Op deze manier wordt er beveiliging geboden via beveiligings maatregelen met meerdere lagen, wat leidt tot end-to-end-beveiliging, die is ontworpen voor de unieke uitdagingen van het Cloud-tijd perk.

Om een end-to-end oplossing te bieden voor het beveiligen van gevoelige assets, is het product team nodig om lastige klanten problemen te verhelpen op meerdere gelijktijdige voor raden:
* *Hoe kunnen we bepalen wie verbinding kan maken, waar ze verbinding mee maken en hoe ze verbinding maken?* *Hoe kunnen we de verbindingen beheren?*
* *Hoe worden de gegevens opgeslagen?* *Hoe wordt het versleuteld?* *Welke besturings elementen heb ik op mijn gegevens?*
* *Hoe kan ik besturings element en beveiligen van mijn gevoelige gegevens?* *Hoe kan ik ervoor te zorgen dat deze gegevens niet kunnen lekken buiten de organisatie?*
* *Hoe kan ik controleren wie welke bewerkingen uitvoeren?* *Hoe kan ik snel reageren als er verdachte activiteiten zijn op de service?*

In dit artikel vindt u een uitgebreide oplossing voor al deze vragen. Het begint met een overzicht van de service architectuur en legt uit hoe de belangrijkste stromen in het systeem werken. Vervolgens wordt er geklikt om te beschrijven hoe gebruikers zich verifiëren bij Power BI, hoe gegevens verbindingen tot stand worden gebracht en hoe Power BI gegevens opslaat en verplaatst via de service. In de laatste sectie vindt u informatie over de beveiligings functies waarmee u, als service beheerder, uw meest waardevolle assets kunt beveiligen.

De Power BI-service is onderworpen aan de [Microsoft Online Services-voorwaarden](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31) en de [Microsoft Enterprise-privacyverklaring](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Voor de locatie van de gegevens verwerking raadpleegt u de locatie van de voor waarden voor gegevens verwerking in de [voor waarden van micro soft Online Services](http://www.microsoftvolumelicensing.com/Downloader.aspx?DocumentId=9555) en het [addendum op gegevens bescherming](https://www.microsoft.com/download/details.aspx?id=101581). Het [Microsoft Vertrouwenscentrum](https://www.microsoft.com/trustcenter) is de primaire resource voor nalevingsinformatie met betrekking tot Power BI. Het Power BI-team doet er alles aan om klanten de nieuwste innovaties en productiviteit te bieden. Meer informatie over naleving in de [nalevings aanbiedingen van micro soft](/compliance/regulatory/offering-home).

De Power BI-service volgt de beveiligings ontwikkeling lifecycle (SDL), strikte beveiligings procedures die de vereisten voor beveiliging en naleving ondersteunen. SDL helpt ontwikkel aars bij het bouwen van veiligere software door het aantal en de ernst van beveiligings problemen in software te verminderen, terwijl de ontwikkelings kosten worden verminderd. Meer informatie over [micro soft Security Development Lifecycle-procedures](https://www.microsoft.com/securityengineering/sdl/practices).

## <a name="power-bi-architecture"></a>Power BI architectuur

Het Power BI-service is gebaseerd op Azure, het [Cloud computing platform](https://azure.microsoft.com/overview/what-is-azure/)van micro soft. Power BI wordt momenteel geïmplementeerd in veel datacenters over de hele wereld. Er zijn veel actieve implementaties beschikbaar gesteld aan klanten in de regio's die door deze datacenters worden bediend. Daarnaast zijn er even veel passieve implementaties, die als back-up fungeren voor alle actieve implementaties.

![Het WFE en het Back-End](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

### <a name="web-front-end-cluster-wfe"></a>Web-front-end-cluster (WFE)

Het WFE-cluster biedt de browser van de gebruiker de oorspronkelijke HTML-pagina-inhoud op de site belasting en beheert het eerste verbindings-en verificatie proces voor Power BI, met behulp van Azure Active Directory (Azure AD) voor het verifiëren van clients en het leveren van tokens voor volgende client verbindingen met de Power BI back-end-service.

![Het cluster WEF](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

Een WFE-cluster bestaat uit een ASP.NET-website die wordt uitgevoerd in de [Azure app service Environment](/azure/app-service/environment/intro). Wanneer gebruikers verbinding proberen te maken met de Power BI-service, kan de DNS-service van de client communiceren met de Azure-Traffic Manager om het meest geschikte (meestal dichtstbijzijnde) Data Center te vinden met een Power BI-implementatie. Zie [prestaties verkeer-routerings methode voor Azure Traffic Manager](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method)voor meer informatie over dit proces.

Het cluster WFE dat aan de gebruiker is toegewezen, beheert de aanmeldings-en verificatie volgorde (verderop in dit artikel beschreven) en verkrijgt een Azure AD-toegangs token zodra de verificatie is geslaagd. Het ASP.NET-onderdeel binnen het WFE-cluster parseert het token om te bepalen tot welke organisatie de gebruiker behoort en raadpleegt vervolgens de Power BI globale service. De WFE geeft aan de browser door welk back-end-cluster de Tenant van de organisatie is. Als een gebruiker eenmaal is geverifieerd, worden de volgende client interacties voor klant gegevens direct uitgevoerd met het back-end-of Premium-cluster, zonder dat de WFE een eigen interactie voor die aanvragen is.

Statische resources zoals **. js*, **. CSS* en afbeeldings bestanden worden meestal opgeslagen in azure Content Delivery Network (CDN) en worden rechtstreeks opgehaald door de browser. Houd er rekening mee dat implementaties van soevereine Government-clusters een uitzonde ring vormen op deze regel en dat om redenen van naleving de CDN weglaat en dat er in plaats daarvan een WFE-cluster wordt gebruikt vanuit een compatibel gebied voor het hosten van statische inhoud.

### <a name="power-bi-back-end-cluster-be"></a>Power BI back-end-cluster (is)

Het back-end-cluster is de backbone van alle functies die beschikbaar zijn in Power BI. Het bestaat uit verschillende service-eind punten die worden gebruikt door web front-end-en API-clients, evenals achtergrond werk Services, data bases, caches en verschillende andere onderdelen.

De back-end is beschikbaar in de meeste Azure-regio's en wordt geïmplementeerd in nieuwe regio's zodra deze beschikbaar komen. Eén Azure-regio fungeert als host voor een of meer back-endservers die onbeperkte horizontale schaling van de Power BI-service mogelijk maken zodra de verticale en horizontale schaal limiet van één cluster worden uitgeput.

Elk back-end-cluster is stateful en host alle gegevens van alle tenants die aan het cluster zijn toegewezen. Een cluster dat de gegevens van een specifieke Tenant bevat, wordt het thuis cluster van de Tenant genoemd. De gegevens van het thuis cluster van een geverifieerde gebruiker worden verstrekt door de wereld wijde service en worden gebruikt door de web-front-end om aanvragen te routeren naar het thuis cluster van de Tenant.

Elk back-end-cluster bestaat uit meerdere virtuele machines die zijn gecombineerd in meerdere verstel bare schaal sets die zijn afgestemd op het uitvoeren van specifieke taken, stateful resources zoals SQL-data bases, opslag accounts, service bussen, caches en andere nood zakelijke cloud onderdelen.

Tenant-meta gegevens en-gegevens worden opgeslagen in cluster limieten, behalve voor gegevens replicatie naar een secundair back-end-cluster in een gekoppelde Azure-regio in dezelfde Azure-geografie. Het secundaire back-end-cluster fungeert als een failovercluster in het geval van regionale storingen en is op een wille keurig moment passief.

De back-end-functionaliteit wordt geleverd door micro services die worden uitgevoerd op verschillende computers in het virtuele netwerk van het cluster die niet toegankelijk zijn vanaf buiten, met uitzonde ring van twee onderdelen die toegankelijk zijn via het open bare Internet:
* Gateway Service
* Azure API Management

![Het back-end-cluster](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

### <a name="power-bi-premium-infrastructure"></a>Power BI Premium-infra structuur

Power BI Premium biedt een service voor abonnees die Premium-Power BI functies nodig hebben, zoals gegevens stromen, gepagineerde rapporten, AI, enzovoort. Wanneer een klant zich aanmeldt voor een Power BI Premium abonnement, wordt de Premium-capaciteit gemaakt via de Azure Resource Manager.

Power BI Premium capaciteit worden gehost in back-end-clusters die onafhankelijk zijn van de normale Power BI back-end-zie hierboven). Dit biedt betere isolatie, toewijzing van resources, ondersteunings-, beveiligings isolatie en schaal baarheid van de Premium-aanbieding.

In het volgende diagram ziet u de architectuur van de Power BI Premium-infra structuur:

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

De verbinding met de Power BI Premium-infra structuur kan op verschillende manieren worden uitgevoerd, afhankelijk van het gebruikers scenario. Power BI Premium-clients kunnen de browser van een gebruiker zijn, een gewone Power BI back-end, rechtstreekse verbindingen via een XMLA-client, ARM-Api's, enzovoort.

De Power BI Premium-infra structuur in een Azure-regio bestaat uit meerdere Power BI Premium clusters (de minimum waarde is één). De meeste Premium-bronnen worden ingekapseld in een cluster (bijvoorbeeld Compute) en er zijn enkele algemene regionale bronnen (bijvoorbeeld meta gegevens opslag). Premium-infra structuur biedt twee manieren om horizontale schaal baarheid in een regio te bereiken: het nemen van resources binnen clusters en/of het toevoegen van meer clusters op aanvraag indien nodig (als de limiet van de cluster bronnen wordt bereikt).

De backbone van elk cluster is reken resources die worden beheerd door [Virtual Machine Scale sets (VMSS)](/azure/virtual-machine-scale-sets/overview) en [Azure service Fabric](/azure/service-fabric/service-fabric-overview). VMSS en Service Fabric staan snelle en eenvoudige methode verhoging van reken knooppunten toe, omdat gebruik groeit en de implementatie, het beheer en de controle van Power BI Premium Services en toepassingen worden beheerd.

Er zijn veel bronnen die een veilige en betrouw bare infra structuur garanderen: load balancers, Virtual Networks, Network Security Groups, service bus, Storage, enzovoort. Alle geheimen, sleutels en certificaten die vereist zijn voor Power BI Premium worden alleen door [Azure Key Vault](/azure/key-vault/general/basic-concepts) beheerd. Verificatie wordt uitgevoerd via de integratie met Azure AD.

Elke aanvraag die wordt geleverd bij Power BI Premium-infra structuur gaat eerst naar front-end-knoop punten. Dit zijn de enige knoop punten die beschikbaar zijn voor externe verbindingen. De rest van de resources worden verborgen achter virtuele netwerken. De front-end-knoop punten verifiëren de aanvraag, verwerken deze of stuurt deze door naar de juiste bronnen (bijvoorbeeld back-end-knoop punten).

Back-end-knoop punten bieden de meeste Power BI Premium mogelijkheden en functies.

### <a name="power-bi-mobile"></a>Power BI Mobile

Power BI-Mobiel is een verzameling apps die zijn ontworpen voor de drie primaire mobiele platforms: Android, iOS en Windows (UWP). Beveiligings overwegingen voor de Power BI-Mobiel-apps zijn onderverdeeld in twee categorieën:
* Apparaatcommunicatie
* De toepassing en gegevens op het apparaat

Voor communicatie met apparaten communiceren alle Power BI-Mobiel-toepassingen met de Power BI-service en gebruiken ze dezelfde verbindings-en verificatie volgordes die worden gebruikt door browsers, die eerder in dit technisch document worden beschreven. Met de mobiele toepassingen van Power BI voor iOS en Android wordt een browser sessie in de toepassing zelf weer geven. de Windows Mobile-App brengt een Broker tot stand om het communicatie kanaal met Power BI (voor het aanmeldings proces) te bepalen.

De volgende tabel toont op certificaten gebaseerde verificatie (dit) voor Power BI-Mobiel, op basis van het platform voor mobiele apparaten:


|Dit-ondersteuning  |iOS  |Android  |Windows  |
|---------|---------|---------|---------|
|Power BI (aanmelden bij de service)    |Ondersteund         |Ondersteund         |Niet ondersteund         |
|SSRS AD FS on-premises (verbinding maken met SSRS-server)     |Niet ondersteund         |Ondersteund         |Niet ondersteund         |
|Proxy voor de SSRS-app     |Ondersteund         |Ondersteund         |Niet ondersteund         |

Power BI Mobile-apps communiceren actief met de Power BI-service. Telemetrie wordt gebruikt voor het verzamelen van gebruiks statistieken voor mobiele apps en soort gelijke gegevens, die worden verzonden naar services die worden gebruikt voor het bewaken van het gebruik en de activiteit. Er worden geen klant gegevens verzonden met telemetrie.

De Power BI-toepassing slaat gegevens op het apparaat op die het gebruik van de app vergemakkelijken:
* Azure AD en vernieuwings tokens worden opgeslagen in een beveiligd mechanisme op het apparaat, met behulp van de industrie standaard beveiligings maatregelen.
* Gegevens en instellingen (sleutel-waardeparen voor gebruikers configuratie) worden in de cache opgeslagen op het apparaat en kunnen worden versleuteld door het besturings systeem. In iOS wordt dit automatisch gedaan wanneer de gebruiker een wachtwoord code instelt. In Android kan dit worden geconfigureerd in de instellingen. In Windows wordt dit bereikt met behulp van BitLocker.
* Voor de Android-en iOS-apps worden de gegevens en instellingen (sleutel-waardeparen voor gebruikers configuratie) opgeslagen in de opslag op het apparaat in een sandbox en interne opslag die alleen toegankelijk is voor de app. De gegevens voor de Windows-app zijn alleen toegankelijk voor de gebruiker (en de systeem beheerder).
* Geolocatie wordt expliciet door de gebruiker ingeschakeld of uitgeschakeld. Als deze functie is ingeschakeld, worden geolocatie gegevens niet opgeslagen op het apparaat en worden ze niet gedeeld met micro soft.
* Meldingen worden expliciet door de gebruiker ingeschakeld of uitgeschakeld. Als deze functie is ingeschakeld, ondersteunen Android en iOS geen geografische gegevens locatie vereisten voor meldingen.

Gegevens versleuteling kan worden uitgebreid door versleuteling op bestands niveau toe te passen via Microsoft Intune, een software service die mobiele apparaten en toepassings beheer biedt. Alle drie de platforms waarvoor Power BI-Mobiel ondersteuning biedt voor intune. Als Intune is ingeschakeld en geconfigureerd, worden gegevens op het mobiele apparaat versleuteld en kan de Power BI-app niet op een SD-kaart worden geïnstalleerd. Meer [informatie over Microsoft intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

De Windows-app biedt ook ondersteuning voor [windows Information Protection (WIP)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).

Voor de implementatie van SSO zijn enkele beveiligde opslag waarden met betrekking tot de op tokens gebaseerde verificatie beschikbaar voor andere micro soft-apps voor de eerste partij (zoals Microsoft Authenticator) en worden beheerd door de Azure Active Directory Authentication Library (ADAL) SDK.  

Power BI-Mobiel gegevens in de cache worden verwijderd wanneer de app wordt verwijderd, wanneer de gebruiker zich afmeldt bij Power BI-Mobiel of wanneer de gebruiker zich niet kan aanmelden (bijvoorbeeld na een verloop gebeurtenis voor het token of het wijzigen van het wacht woord). De gegevenscache bevat dashboards en rapporten die eerder zijn geopend vanuit de Power BI Mobile-app.

Power BI-Mobiel heeft geen toegang tot andere toepassings mappen of-bestanden op het apparaat.

Met de Power BI-apps voor iOS en Android kunt u uw gegevens beveiligen door extra identificatie te configureren, zoals het opgeven van Face ID, touch ID of een wachtwoord code voor iOS en biometrische gegevens (vinger afdruk-ID) voor Android. Meer [informatie over aanvullende identificatie](../consumer/mobile/mobile-native-secure-access.md).

## <a name="authentication-to-the-power-bi-service"></a>Verificatie voor de Power BI-service

De gebruikersverificatie voor de Power BI-service bestaat uit een reeks aanvragen, antwoorden en omleidingen tussen de browser van de gebruiker en de Power BI-service of de Azure-services die worden gebruikt door Power BI. In deze reeks wordt het proces van verificatie van de gebruiker in Power BI beschreven, die de toewijzings stroom voor de [verificatie code van de Azure Active Directory](/azure/active-directory/develop/v2-oauth2-auth-code-flow)volgt. Zie [een aanmeldings model kiezen voor Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/blog/2014/05/13/choosing-a-sign-in-model-for-office-365/)voor meer informatie over de opties voor de gebruikers authenticatie modellen van een organisatie (aanmeld modellen).

### <a name="authentication-sequence"></a>Verificatiereeks

De gebruikers verificatie reeks voor de Power BI-service vindt plaats zoals beschreven in de volgende stappen, die in de onderstaande afbeelding worden weer gegeven.

1. Een gebruiker initieert een verbinding met de Power BI-service vanuit een browser, door te typen in het Power BI adres in de adres balk of door *Aanmelden* te selecteren op de Power bi landings pagina ( https://powerbi.microsoft.com) . De verbinding wordt tot stand gebracht met behulp van TLS 1.2 en HTTPS, en bij alle verdere communicatie tussen de browser en de Power BI-service wordt HTTPS gebruikt.

1. De Azure Traffic Manager controleert de DNS-record van de gebruiker om het meest geschikte Data Center te bepalen waar Power BI wordt geïmplementeerd, en reageert op de DNS met het IP-adres van het WFE-cluster waarnaar de gebruiker moet worden verzonden.

1. WFE leidt de gebruiker vervolgens naar de aanmeldings pagina van micro soft Online Services.

1. Nadat de gebruiker is geverifieerd, wordt de gebruiker door de aanmeldings pagina omgeleid naar het eerder vastgestelde dichtstbijzijnde Power BI-service WFE-cluster met een verificatie code.

1. De WFE-cluster controleert met de Azure AD-service voor het verkrijgen van een Azure AD-beveiligings token met behulp van de verificatie code. Wanneer Azure AD de geslaagde verificatie van de gebruiker retourneert en een Azure AD-beveiligings token retourneert, raadpleegt het WFE-cluster de Power BI Global-Service, die een lijst met tenants en hun Power BI back-end-cluster locaties onderhoudt en bepaalt welke Power BI back-end-service cluster de Tenant van de gebruiker bevat. Het WFE-cluster keert vervolgens een toepassings pagina terug naar de browser van de gebruiker met de sessie-, toegangs-en routerings gegevens die nodig zijn voor de werking ervan.

1. Wanneer de browser van de client klant gegevens vereist, worden er nu aanvragen verzonden naar het back-end-cluster adres met het Azure AD-toegangs token in de autorisatie-header. Het Power BI back-end-cluster leest het Azure AD-toegangs token en valideert de hand tekening om ervoor te zorgen dat de identiteit van de aanvraag geldig is. Het [Azure AD-toegangs token heeft een standaard levensduur van 1 uur](/azure/active-directory/develop/active-directory-configurable-token-lifetimes#configurable-token-lifetime-properties-after-the-retirement)en om de huidige sessie te onderhouden, zullen de browser van de gebruiker periodieke aanvragen indienen om het toegangs token te vernieuwen voordat het verloopt.

![Verificatiereeks](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

## <a name="data-residency"></a>Gegevenslocatie

Tenzij anders vermeld in de documentatie, Power BI klant gegevens op te slaan in een Azure-geografie die wordt toegewezen wanneer een [Azure AD-Tenant](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings) zich voor de eerste keer aanmeldt voor Power BI Services. Een Azure AD-Tenant is de gebruikers-en toepassings identiteiten, groepen en andere relevante informatie die betrekking hebben op een organisatie en de beveiliging ervan. 

De toewijzing van een Azure-Geografie voor Tenant gegevens opslag geschiedt door het land of de regio die is geselecteerd als onderdeel van de Azure AD-Tenant installatie, toe te wijzen aan het meest geschikte Azure-geografie waar een Power BI-implementatie bestaat. Zodra deze bepaling is uitgevoerd, worden alle Power BI klant gegevens opgeslagen in deze geselecteerde Azure-Geografie (ook wel bekend als de *geografische* locatie), behalve in gevallen waarin organisaties multi-geo-implementaties gebruiken.

### <a name="multiple-geographies-multi-geo"></a>Meerdere geographs (meerdere geografische locaties)

Sommige organisaties hebben een wereld wijde aanwezigheid en vereisen mogelijk Power BI Services in meerdere Azure-geografi. Een bedrijf kan bijvoorbeeld hun hoofd kantoor hebben in de Verenigde Staten, maar kan ook zaken doen in andere geografische gebieden, zoals Australië. In dergelijke gevallen kan het bedrijf eisen dat bepaalde Power BI gegevens in rust zijn opgeslagen in de externe regio om te voldoen aan lokale voor Schriften. Deze functie van de Power BI-service wordt aangeduid als *multi-geo*.

De query execution-laag, query-caches en artefact gegevens die aan een multi-geo-werk ruimte zijn toegewezen, worden gehost en blijven in de Azure-Geografie van externe capaciteit. Sommige meta gegevens van artefacten, zoals een rapport structuur, kunnen echter opgeslagen worden in de rest van de geo-huis van de Tenant. Daarnaast kunnen er nog steeds gegevens doorvoer en-verwerking plaatsvinden in de geografische locatie van de Tenant, zelfs voor werk ruimten die worden gehost in een multi-geo Premium-capaciteit.

Zie [Configure multi-geo-ondersteuning voor Power bi Premium](../admin/service-admin-premium-multi-geo.md) voor meer informatie over het maken en beheren van Power bi-implementaties die meerdere Azure-grafieken omvatten.

### <a name="regions-and-datacenters"></a>Regio's en data centers

Power BI Services zijn beschikbaar in specifieke Azure-geografies, zoals beschreven in het [micro soft vertrouwens centrum](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location). Raadpleeg het [vertrouwens centrum van micro soft](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where)voor meer informatie over waar uw gegevens worden opgeslagen en hoe deze worden gebruikt. Verplichtingen met betrekking tot de locatie van de klant gegevens in rust zijn gespecificeerd in de voor waarden voor gegevens verwerking van de [micro soft Online Services-voor waarden](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31).

Micro soft biedt ook data centers voor soevereine entiteiten. Zie [Nationale Power BI-clouds](https://powerbi.microsoft.com/clouds/) voor meer informatie over de beschikbaarheid van de Power BI-service voor nationale clouds. 

## <a name="data-handling"></a>Gegevensverwerking

In deze sectie worden Power BI procedures voor het verwerken van gegevens beschreven, wanneer het gaat om klant gegevens op te slaan, te verwerken en te verplaatsen.

### <a name="data-at-rest"></a>Inactieve gegevens

Power BI gebruikt twee bron typen voor primaire gegevens opslag:
* Azure Storage
* Azure SQL Databases

In het meren deel van scenario's wordt Azure Storage gebruikt om de gegevens van Power BI artefacten persistent te maken, terwijl Azure SQL-data bases voor het behouden van meta gegevens van artefacten. 

Alle gegevens die door Power BI worden bewaard, worden standaard versleuteld met door micro soft beheerde sleutels. Klant gegevens die zijn opgeslagen in Azure SQL-data bases zijn volledig versleuteld met [de transparent Data Encryption-technologie (TDE) van Azure SQL](/azure/sql-database/transparent-data-encryption-azure-sql) . Klant gegevens die zijn opgeslagen in Azure Blob Storage, worden versleuteld met [Azure Storage versleuteling](/azure/storage/common/storage-service-encryption).

Organisaties kunnen eventueel gebruikmaken van Power BI Premium om hun eigen sleutels te gebruiken voor het versleutelen van gegevens in rest die in een gegevensset worden geïmporteerd. Deze methode wordt vaak beschreven als Bring Your Own Key (BYOK). Het gebruik van BYOK zorgt ervoor dat de klant gegevens, zelfs in het geval van een service operator fout, niet kunnen worden weer gegeven, iets wat u niet eenvoudig kunt bereiken met behulp van transparante service-side versleuteling. Raadpleeg [uw eigen versleutelings sleutels voor Power bi](../admin/service-encryption-byok.md) voor meer informatie.

Met Power BI gegevens sets kunnen verschillende modi voor gegevens bron verbindingen worden gemaakt waarmee wordt bepaald of de gegevens bron gegevens worden bewaard in de service of niet.

|Modus gegevensset (soort)   |De gegevens zijn opgeslagen in Power BI |
|----------------------|---------------------------|
|Importeren                |Yes |
|Direct Query          |No |
|Live Connect          |No |
|Composite             |Als bevat een gegevens bron voor importeren |
|Streaming             |Indien geconfigureerd om persistent te maken |

Power BI mag de opgehaalde gegevens tijdelijk in de cache opslaan om de query-en rapport belasting prestaties te optimaliseren, ongeacht de gebruikte gegevensset.

### <a name="data-in-processing"></a>Gegevens in verwerking

Gegevens worden verwerkt wanneer het actief wordt gebruikt door een of meer gebruikers als onderdeel van een interactief scenario, of wanneer een achtergrond proces, zoals vernieuwen, deze gegevens raakt. Power BI laadt gegevens die actief zijn verwerkt in de geheugen ruimte van een of meer service werkbelastingen. De verwerkte gegevens in het geheugen worden niet versleuteld om de functionaliteit te vergemakkelijken die vereist is voor de werk belasting.

### <a name="data-in-transit"></a>Actieve gegevens
Voor Power BI moet al het binnenkomende HTTP-verkeer worden versleuteld met behulp van TLS 1,2 of hoger. Aanvragen die proberen de service met TLS 1,1 of lager te gebruiken, worden geweigerd.

## <a name="authentication-to-data-sources"></a>Verificatie voor gegevens bronnen

Wanneer u verbinding maakt met een gegevens bron, kan een gebruiker ervoor kiezen om een kopie van de gegevens te importeren in Power BI of om rechtstreeks verbinding te maken met de gegevens bron. 

In het geval van import brengt een gebruiker een verbinding tot stand op basis van de aanmelding van de gebruiker en opent de gegevens met de referentie. Nadat de gegevensset is gepubliceerd naar de Power BI-service, gebruikt Power BI altijd de referentie van deze gebruiker om gegevens te importeren. Zodra de gegevens zijn geïmporteerd, kunnen de gegevens in rapporten en dash boards niet worden geopend met de onderliggende gegevens bron. Power BI ondersteunt verificatie met eenmalige aanmelding voor geselecteerde gegevens bronnen. Als de verbinding is geconfigureerd voor het gebruik van eenmalige aanmelding, worden de referenties van de eigenaar van de gegevensset gebruikt om verbinding te maken met de gegevens bron.

Als een gegevens bron direct is verbonden met behulp van vooraf geconfigureerde referenties, worden de vooraf geconfigureerde referenties gebruikt om verbinding te maken met de gegevens bron wanneer een gebruiker de gegevens bekijkt. Als een gegevens bron direct is verbonden via eenmalige aanmelding, worden de referenties van de huidige gebruiker gebruikt om verbinding te maken met de gegevens bron wanneer een gebruiker de gegevens bekijkt. Bij gebruik met eenmalige aanmelding kan beveiliging op rijniveau worden geïmplementeerd op de gegevens bron. Hiermee kunnen gebruikers alleen de gegevens weer geven waartoe ze toegang hebben. Als de verbinding is met gegevens bronnen in de Cloud, wordt Azure AD-verificatie gebruikt voor eenmalige aanmelding; voor on-premises gegevens bronnen worden Kerberos, Security Assertion Markup Language (SAML) en Azure AD ondersteund.

Als de gegevens bron Azure Analysis Services of on-premises Analysis Services is en er beveiliging op RIJNIVEAU is geconfigureerd, wordt de Power BI-service de beveiliging op rijniveau toegepast en kunnen gebruikers die niet voldoende referenties hebben voor toegang tot de onderliggende gegevens (dit kan een query zijn die wordt gebruikt in een dash board, rapport of ander gegevens artefact) geen gegevens zien waarvoor ze niet voldoende bevoegdheden hebben.

## <a name="premium-features"></a>Premium-functies

### <a name="dataflows-architecture"></a>Gegevens stromen-architectuur

Gegevens stromen bieden gebruikers de mogelijkheid om back-upbewerkingen voor gegevens verwerking te configureren waarmee gegevens worden opgehaald uit polymorfismee gegevens bronnen, transformatie logica kunnen worden uitgevoerd op basis van de gegevens en vervolgens in een doel model kan worden gebruikt voor verschillende rapportage presentatie technologieën. Gebruikers met een rol lid, Inzender of beheerder in een werk ruimte kunnen een gegevensstroom maken. Gebruikers met de rol van de gebruiker kunnen gegevens weer geven die zijn verwerkt door de gegevensstroom, maar kunnen geen wijzigingen aanbrengen in de samen stelling. Zodra een gegevensstroom is gemaakt, kan een lid, Inzender of beheerder van de werk ruimte vernieuwingen plannen, en de gegevensstroom weer geven en bewerken door eigenaar te worden van het gegevens bestand.

Elke geconfigureerde gegevens bron is gebonden aan een client technologie voor toegang tot die gegevens bron. De structuur van de referenties die nodig zijn om toegang te krijgen, wordt gevormd door de vereiste implementatie details van de gegevens bron te vergelijken. Trans formatie logica wordt toegepast door Power Query Services terwijl de gegevens zich in de vlucht bevindt. Voor Premium-gegevens stromen worden Power Query Services in de back-end-knoop punten uitgevoerd. Gegevens kunnen rechtstreeks worden opgehaald uit de Cloud bronnen of via een gateway die on-premises is geïnstalleerd. Wanneer rechtstreeks vanuit een Cloud bron naar de service of naar de gateway wordt getrokken, gebruikt het Trans Port een beveiligings methodologie die specifiek is voor de client technologie, indien van toepassing. Wanneer gegevens worden overgedragen van de gateway naar de Cloud service, wordt deze versleuteld. Zie de sectie [gegevens in verwerking](#data-in-processing) .

Wanneer de door de klant opgegeven gegevens bronnen referenties vereisen voor toegang, levert de eigenaar/maker van de gegevensstroom deze tijdens het ontwerpen. Deze worden opgeslagen met behulp van de standaard referentie opslag voor het hele product. Zie de sectie [verificatie voor gegevens bronnen](#authentication-to-data-sources) hierboven. Er zijn verschillende benaderingen die gebruikers kunnen configureren om gegevens persistentie en toegang te optimaliseren. Standaard worden de gegevens in een Power BI eigendom en beveiligd opslag account geplaatst. Opslag versleuteling wordt ingeschakeld op de Blob Storage-containers om de gegevens te beveiligen terwijl deze in rust zijn. Zie de sectie [gegevens in rest](#data-at-rest) hieronder. Gebruikers kunnen echter hun eigen opslag account configureren dat is gekoppeld aan hun eigen Azure-abonnement. Als u dit doet, wordt aan een Power BI-service-principal toegang verleend tot dat opslag account, zodat de gegevens daar tijdens het vernieuwen kunnen worden geschreven. In dit geval is de eigenaar van de opslag resource verantwoordelijk voor het configureren van versleuteling voor het geconfigureerde ADLS-opslag account. Gegevens worden altijd verzonden naar Blob-opslag met behulp van versleuteling.

Omdat de prestaties bij het openen van opslag accounts voor sommige gegevens mogelijk zijn, hebben gebruikers ook de mogelijkheid om een Power BI gehoste Compute-engine te gebruiken om de prestaties te verbeteren. In dit geval zijn gegevens redundant opgeslagen in een SQL database die beschikbaar is voor DirectQuery via toegang door het back-end-Power BI systeem. Gegevens worden altijd versleuteld op het bestands systeem. Als de gebruiker een sleutel bevat voor het versleutelen van de gegevens die zijn opgeslagen in de SQL database, wordt die sleutel gebruikt om deze te versleutelen.

Wanneer u een query uitvoert met behulp van DirectQuery, wordt het versleutelde Trans Port protocol HTTPS gebruikt voor toegang tot de API. Alle secundaire of indirecte gebruik van DirectQuery wordt bepaald door de eerder beschreven toegangs beheer functies. Omdat gegevens stromen altijd zijn gebonden aan een werk ruimte, wordt de toegang tot de gegevens altijd gegatedeerd door de rol van de gebruiker in die werk ruimte. Een gebruiker moet ten minste lees toegang hebben om de gegevens op een wille keurige manier te kunnen opvragen.

Als Power BI Desktop wordt gebruikt voor toegang tot gegevens in een gegevensstroom, moet deze de gebruiker eerst verifiëren met behulp van Azure AD om te bepalen of de gebruiker voldoende rechten heeft om de gegevens weer te geven. Als dat het geval is, wordt er een SaS-sleutel aangeschaft en gebruikt om rechtstreeks toegang te krijgen tot de opslag met het versleutelde Trans Port protocol HTTPS.

Door de verwerking van gegevens in de pijp lijn worden de gebeurtenissen van Office 365 gecontroleerd. Bij sommige van deze gebeurtenissen worden beveiligings-en privacy-gerelateerde bewerkingen vastgelegd.

### <a name="paginated-reports"></a>Gepagineerde rapporten

Gepagineerde rapporten zijn ontworpen om te worden afgedrukt of gedeeld. Ze worden gepagineerd genoemd, omdat ze zo zijn opgemaakt dat ze op een pagina passen. Alle gegevens worden in een tabel weergegeven, zelfs als de tabel meerdere pagina's omvat. Ze worden soms pixelperfect genoemd, omdat de pagina-indeling van dit type rapport exact kan worden ingesteld.

Gepagineerde rapporten ondersteunen uitgebreide en krachtige expressies die in micro soft Visual Basic .NET zijn geschreven. Expressies worden op grote schaal in gepagineerde rapporten van Power BI Report Builder gebruikt voor het ophalen, berekenen, weergeven, groeperen, sorteren en filteren van gegevens, om parameters aan gegevens toe te wijzen en om gegevens op te maken.

Expressies worden gemaakt door de auteur van het rapport met toegang tot een breed scala aan functies van .NET Framework. De verwerking en uitvoering van gepagineerde rapporten wordt uitgevoerd in een sandbox.

Gepagineerde rapport definities (. RDL) worden opgeslagen in Power BI en om een gepagineerd rapport te publiceren en/of weer te geven, moet een gebruiker zich op dezelfde manier verifiëren en autoriseren als wordt beschreven in de sectie [verificatie naar het Power bi service](#authentication-to-the-power-bi-service) -gedeelte hierboven.

Het Azure AD-token dat is verkregen tijdens de verificatie wordt gebruikt om rechtstreeks vanuit de browser te communiceren naar het Power BI Premium-cluster.

Voor Premium-gen1 bestaat één sandbox per de capaciteit van de Tenant en wordt gedeeld door de werk ruimten die zijn toegewezen aan de capaciteit.

![Gepagineerde rapporten gen 1](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen1.png)

Voor Premium-Gen2 (in Preview) wordt een afzonderlijke en exclusieve tijdelijke sandbox gemaakt voor elk van de weer gaven van een rapport, waardoor er een hoger isolatie niveau is tussen gebruikers.

![Gepagineerde rapporten gen 2](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen2.png)

Een gepagineerd rapport heeft toegang tot een grote set gegevens bronnen als onderdeel van de rendering van het rapport. De sandbox communiceert niet rechtstreeks met een van de gegevens bronnen, maar communiceert met het vertrouwde proces om gegevens aan te vragen. vervolgens voegt het vertrouwde proces de vereiste referenties toe aan de verbinding. Op deze manier heeft de sandbox nooit toegang tot referenties of een geheim. 

Voor de ondersteuning van functies zoals Bing Maps of aanroepen naar Azure Functions, heeft de sandbox toegang tot internet.

### <a name="power-bi-embedded-analytics"></a>Power BI embedded Analytics

Independent Software Vendors (Isv's) en solution providers hebben twee hoofd modi voor het insluiten van Power BI artefacten in hun webtoepassingen en portals: [sluit u in voor uw organisatie](../developer/embedded/embed-sample-for-your-organization.md) en [sluit u in voor uw klanten](../developer/embedded/embed-sample-for-customers.md). Het artefact is inge sloten in een IFRAME in de toepassing of portal. Een IFRAME mag geen gegevens lezen of schrijven van de externe webtoepassing of portal en de communicatie met het iframe geschiedt met behulp van de Power BI client-SDK met behulp van POST-berichten.

In een [Inge sloten scenario voor uw organisatie](../developer/embedded/embed-sample-for-your-organization.md) hebben Azure AD-gebruikers toegang tot hun eigen Power bi inhoud via portals die zijn aangepast aan hun ondernemingen en haar. Alle Power BI-beleid en-mogelijkheden die in dit document worden beschreven, zoals beveiliging op rijniveau, worden automatisch toegepast op alle gebruikers, onafhankelijk van of ze toegang hebben tot Power BI via de [Power BI portal](https://app.powerbi.com/) of via aangepaste Port alen.

In het scenario [insluiten voor uw klanten](../developer/embedded/embed-sample-for-customers.md) zijn isv's meestal eigenaar van Power bi tenants en Power bi artefacten (Dash boards, rapporten, gegevens sets, enzovoort). Het is de verantwoordelijkheid van een ISV-back-end-service om de eind gebruikers te verifiëren en te bepalen welke artefacten en welk toegangs niveau geschikt is voor die eind gebruiker. Het ISV-beleid wordt versleuteld in een [insluit token](/rest/api/power-bi/embedtoken) dat wordt gegenereerd door Power bi en is door gegeven aan de back-end van de ISV voor verdere distributie naar de eind gebruikers volgens de bedrijfs logica van de ISV. Eind gebruikers die een browser of andere client toepassingen gebruiken, kunnen geen insluitings tokens ontsleutelen of wijzigen. Sdk's aan de client zijde, zoals [Power bi client-api's](/javascript/api/overview/powerbi/) , voegen het versleutelde insluit token automatisch toe aan Power bi aanvragen als *autorisatie: insluit token* -header. Op basis van deze header dwingt Power BI alle beleids regels (zoals Access of beveiliging op rijniveau) precies zoals opgegeven door de ISV tijdens het genereren af te dwingen.

Als u insluiten en automatisering wilt inschakelen en de hierboven beschreven insluit tokens wilt genereren, wordt door Power BI een uitgebreide set [rest-api's](/rest/api/power-bi/embedtoken)weer gegeven. Deze Power BI REST-Api's bieden ondersteuning voor zowel door gebruikers [gedelegeerde](/azure/active-directory/develop/v2-permissions-and-consent) als [service-principals](../admin/service-premium-service-principal.md) voor de verificatie en autorisatie van Azure AD-methoden.

Power BI embedded Analytics en de REST Api's ondersteunen alle Power BI mogelijkheden voor netwerk isolatie die in dit artikel worden beschreven: bijvoorbeeld [service Tags](#service-tags) en [persoonlijke koppelingen](#private-link-integration).

### <a name="ai-features"></a>AI-functies

Power BI ondersteunt momenteel twee uitgebreide categorieën van AI-functies in het product: AI-visuals en AI-verrijkingen. De AI-functies op het niveau van het visuele element bevatten mogelijkheden zoals belang rijke kenmerken, ontleding structuur, slimme afname, anomalie detectie, R-Visual, python-Visual, Clustering, prognose, Q&A, Quick-Insights enzovoort. De AI-verrijkings mogelijkheden omvatten mogelijkheden zoals AutoML, AzureML, CognitiveServices, R/python transformaties, enzovoort. 

De meeste functies die hierboven worden genoemd, worden momenteel ondersteund in zowel gedeelde als Premium-werk ruimten. AutoML en CognitiveServices worden echter alleen ondersteund in Premium-werk ruimten, vanwege IP-beperkingen. Vandaag de dag, met de AutoML-integratie in Power BI, kan een gebruiker een aangepast ML-model bouwen en trainen (bijvoorbeeld voor spelling, classificatie, regressie enz.) en dit Toep assen om voor spellingen te krijgen tijdens het laden van gegevens in een gegevensstroom die is gedefinieerd in een Premium-werk ruimte. Daarnaast kunnen Power BI gebruikers verschillende CognitiveServices-Api's Toep assen, zoals TextAnalytics en ImageTagging, om gegevens te transformeren voordat ze worden geladen in een gegevensstroom/gegevensset die is gedefinieerd in een Premium-werk ruimte. 

De Premium AI-verrijkings functies kunnen het beste worden weer gegeven als een verzameling staatloze AI-functies/-trans formaties die kunnen worden gebruikt door Power BI gebruikers in hun gegevens integratie pijplijnen die worden gebruikt door een Power BI dataset of gegevensstroom. Houd er rekening mee dat deze functies ook kunnen worden geopend vanuit huidige gegevensstroom-en gegevensset-ontwerp omgevingen in de Power BI-service en Power BI Desktop. Deze AI-functies/-trans formaties worden altijd uitgevoerd in een Premium-werk ruimte/capaciteit. Deze functies worden in Power BI weer gegeven als een gegevens bron waarvoor een Azure AD-token is vereist voor de Power BI gebruiker die de AI-functie gebruikt. Deze AI-gegevens bronnen zijn speciaal, omdat ze geen eigen gegevens hebben. ze bieden alleen deze functies/trans formaties. Tijdens de uitvoering maken deze functies geen uitgaande oproepen naar andere services voor het verzenden van de gegevens van de klant. Laat ons de Premium-scenario's individueel bekijken om inzicht te krijgen in de communicatie patronen en relevante informatie over de beveiliging. 

Voor training en het Toep assen van een AutoML-model, maakt Power BI gebruik van de Azure AutoML SDK en voert alle trainingen uit in de Power BI capaciteit van de klant. Tijdens de trainings herhalingen roept Power BI een service voor het uitvoeren van experimenten aan om een geschikt model en Hyper-para meters voor de huidige iteratie te selecteren. In deze uitgaande oproep worden alleen de relevante experimentele meta gegevens (zoals nauw keurigheid, ml-algoritme, algoritme parameters enzovoort) van de vorige iteratie verzonden. De AutoML-training produceert een ONNX-model en opleidings rapport gegevens die vervolgens worden opgeslagen in de gegevensstroom. Later kunnen gebruikers Power BI het getrainde ML model als een trans formatie Toep assen om het ML-model op een geplande basis te operationeel maken. Voor TextAnalytics-en ImageTagging-Api's roept Power BI de CognitiveServices-service-Api's niet rechtstreeks aan, maar wordt in plaats daarvan een interne SDK gebruikt om de Api's uit te voeren in de Power BI Premium capaciteit. Deze Api's worden vandaag ondersteund in zowel Power BI gegevens stromen als gegevens sets. Bij het ontwerpen van een gegevensset in Power BI Desktop, hebben gebruikers alleen toegang tot deze functionaliteit als ze toegang hebben tot een Premium Power BI-werk ruimte. Daarom wordt klanten gevraagd hun Azure AD-referenties op te geven. 

## <a name="network-isolation"></a>Netwerkisolatie

In deze sectie vindt u een overzicht van geavanceerde beveiligings functies in Power BI. Sommige functies hebben specifieke licentie vereisten. Zie de secties hieronder voor meer informatie.

### <a name="service-tags"></a>Servicetags

Een servicetag vertegenwoordigt een groep IP-adres voorvoegsels van een bepaalde Azure-service. Het helpt de complexiteit van regel matige updates voor netwerk beveiligings regels te minimaliseren. Klanten kunnen service tags gebruiken om netwerk toegangs beheer te definiëren voor [netwerk beveiligings groepen](/azure/virtual-network/security-overview#security-rules) of [Azure firewall](/azure/firewall/service-tags). Klanten kunnen service tags gebruiken in plaats van specifieke IP-adressen bij het maken van beveiligings regels. Door de naam van de servicetag (bijvoorbeeld PowerBI) op te geven in het juiste bron-of doel veld (voor Api's) van een regel, kunnen klanten het verkeer voor de bijbehorende service toestaan of weigeren. Micro soft beheert de adres voorvoegsels die zijn opgenomen in het servicetag van de service en werkt de servicetag automatisch bij met gewijzigde adressen.

### <a name="private-link-integration"></a>Integratie van persoonlijke koppelingen

Azure Networking biedt de functie voor persoonlijke Azure-koppelingen waarmee Power BI veilige toegang kunt bieden via Azure-netwerken persoonlijke eind punten. Met persoonlijke Azure-koppelingen en privé-eind punten wordt gegevens verkeer privé verzonden met de backbone-netwerk infrastructuur van micro soft, zodat de gegevens niet via internet worden doorgestuurd.

Een persoonlijke koppeling zorgt ervoor dat Power BI gebruikers de backbone van het particuliere netwerk van micro soft gebruiken wanneer ze naar resources in het Power BI-service gaan.

Het gebruik van een persoonlijke koppeling met Power BI biedt de volgende voor delen:
* Met een persoonlijke koppeling zorgt u ervoor dat verkeer via de Azure-backbone over een persoonlijk eind punt voor Azure-Cloud bronnen loopt.
* Voor netwerk verkeer isolatie van niet-Azure-infra structuur, zoals on-premises toegang, moeten klanten ExpressRoute of een virtueel particulier netwerk (VPN) hebben geconfigureerd.

Zie [persoonlijke koppelingen voor toegang tot Power bi](../admin/service-security-private-links.md) voor meer informatie.

### <a name="vnet-connectivity-preview---coming-soon"></a>VNet-connectiviteit (preview-binnenkort beschikbaar)

Hoewel de functie voor integratie van persoonlijke koppelingen beveiligde binnenkomende verbindingen met Power BI biedt, schakelt de VNet-connectiviteits functie beveiligde uitgaande connectiviteit van Power BI naar gegevens bronnen binnen een VNet. 

VNet-gateways (door micro soft beheerd) elimineren de overhead van het installeren en bewaken van on-premises gegevens gateways om verbinding te maken met gegevens bronnen die zijn gekoppeld aan een VNet. Ze zullen echter nog steeds het vertrouwde proces voor het beheren van de beveiliging en gegevens bronnen volgen, net als bij een on-premises gegevens gateway.

Hier volgt een overzicht van wat er gebeurt wanneer u communiceert met een Power BI-rapport dat is verbonden met een gegevens bron in een VNet met behulp van VNet-gateways:

1. De Power BI-Cloud service (of een van de andere ondersteunde Cloud Services) start een query en verzendt de query, gegevens bron Details en referenties naar de Power platform VNet-service (PP VNet).

1. De PP VNet-service voert vervolgens veilig een container met een VNet-gateway in het subnet in. Deze container kan nu verbinding maken met gegevens services die vanuit dit subnet toegankelijk zijn.

1. De PP VNet-service verzendt vervolgens de query, gegevens bron Details en referenties naar de VNet-gateway. 

1. De VNet-gateway haalt de query op en maakt verbinding met de gegevens bronnen met deze referenties.

1. De query wordt vervolgens naar de gegevens bron verzonden om te worden uitgevoerd.

1. Na de uitvoering worden de resultaten verzonden naar de VNet-gateway en de PP-service zorgt ervoor dat de gegevens van de container veilig worden gepusht naar de Power BI-Cloud service.

Deze functie is binnenkort beschikbaar als open bare preview.

### <a name="service-principals"></a>Service-principals

Power BI ondersteunt het gebruik van service-principals. Sla de referenties van de Service-Principal op die worden gebruikt voor het versleutelen of openen van Power BI in een Key Vault, wijs het juiste toegangs beleid toe aan de kluis en controleer regel matig de toegangs machtigingen.

Zie [Premium-werk ruimte en gegevensset-taken automatiseren met Service-principals](../admin/service-premium-service-principal.md) voor meer informatie.

## <a name="data-loss-prevention-dlp"></a>Preventie van gegevens verlies (DLP)

### <a name="microsoft-365-sensitivity-labels"></a>Microsoft 365 gevoeligheids labels

Power BI heeft een diep gaande integratie met micro Information Protection Soft MIP-labels voor de gevoeligheid, waarmee organisaties één geïntegreerde oplossing kunnen hebben voor het DLP-beleids beheer, de controle en de naleving van het hele Office-pakket.

Wanneer gevoeligheids labels zijn ingeschakeld in Power BI:
* Gevoelige gegevens, zowel in de Power BI-service (GA) als in Power BI Desktop (preview), kunnen worden geclassificeerd en gelabeld met dezelfde vertrouwde micro soft Information Protection-codelabels labels die worden gebruikt in Office en in azure controle sfeer liggen. 
* Beheer beleid kan worden afgedwongen, zelfs wanneer Power BI inhoud wordt geëxporteerd naar Excel-, Power Point-, PDF-of *pbix* -bestanden, om ervoor te zorgen dat gegevens beveiligd blijven, zelfs wanneer deze Power bi.
* *pbix* -bestanden kunnen worden versleuteld volgens een MIP-label beleid wanneer een MIP-label wordt toegepast op het *. pbix* -bestand op het bureau blad, zodat alleen geautoriseerde gebruikers dit bestand kunnen bewerken.
* Het is eenvoudig om *pbix* -bestanden te classificeren en te beveiligen, net als bij Excel-, Word-en Power Point-bestanden. Met slechts twee klikken kan een bestand worden gelabeld op basis van het niveau van de gevoeligheid en, zelfs nog verder, worden versleuteld als het zakelijke vertrouwelijke gegevens bevat.
* Excel-werkmappen nemen automatisch de gevoeligheids labels over wanneer ze verbinding maken met Power BI (preview), waardoor het mogelijk is om end-to-end-classificatie te onderhouden en beveiliging toe te passen wanneer de Power BI-gegevensset in Excel wordt geanalyseerd.
* Gevoeligheids labels die op Power BI rapporten en dash boards worden toegepast, worden weer gegeven in de Power BI mobiele iOS-en Android-apps.
* Gevoeligheids labels blijven behouden wanneer een Power BI rapport wordt Inge sloten in teams, share point of een beveiligde website (preview). Dit helpt organisaties bij het insluiten van Power BI inhoud classificatie en beveiliging te hand haven.
* Label overname bij het maken van nieuwe inhoud in de Power BI-service zorgt ervoor dat het label dat wordt toegepast op een gegevensset in de Power BI-service wordt toegepast op nieuwe inhoud die boven op de gegevensset wordt gemaakt. 
* Met [Power bi scan-api's](/rest/api/power-bi/admin/workspaceinfo_getscanresult) van de beheerder kunt u het gevoeligheids label van een Power bi artefact extra heren, waardoor Power bi en INFOSEC beheerders in staat zijn om de labels in de Power bi-service te controleren en rapporten te maken. 
* Power BI zorgt ervoor dat alleen geautoriseerde gebruikers labels kunnen wijzigen of verwijderen met beveiligings instellingen in de Power BI-service. 
* Binnenkort beschikbaar
    * Power BI-beheer-Api's voor het Toep assen van MIP-labels zodat centrale teams op programmatische wijze inhoud in de Power BI-service kunnen labelen.  
    * Beheerders kunnen labels Toep assen op nieuwe of bewerkte inhoud met een verplicht label beleid in de Power BI-service (preview).
    * Automatische stroomafwaartse artefacten in de Power BI-service. Wanneer een label in een gegevensset wordt toegepast of gewijzigd, wordt het label automatisch toegepast op alle downstream-inhoud die is verbonden met dit artefact.

Raadpleeg de [documentatie voor micro soft Information Protection-gevoeligheids label in Power bi](../admin/service-security-sensitivity-label-overview.md) voor meer informatie.

### <a name="microsoft-cloud-app-security-mcas-for-power-bi"></a>Microsoft Cloud App Security (MCAS) voor Power BI

Microsoft Cloud App Security is een van de belangrijkste toonaangevende cloud Access Security-makelaars, met de naam leider in de Magic kwadrant van Gartner voor de Cloud Access Security Broker-markt (CASB). Cloud app Security wordt gebruikt om het gebruik van Cloud-apps te beveiligen. Hiermee kunnen organisaties in real-time Risk ante Power BI sessies bewaken en beheren, zoals gebruikers toegang van niet-beheerde apparaten. Beveiligings beheerders kunnen beleids regels definiëren voor het beheren van gebruikers acties, zoals het downloaden van rapporten met gevoelige informatie.

Met Cloud App Security kunnen organisaties de volgende DLP-mogelijkheden verkrijgen: 
* Stel realtime-besturings elementen in om Risk ante gebruikers sessies in Power BI af te dwingen. Als een gebruiker bijvoorbeeld verbinding maakt met Power BI van buiten hun land, kan de sessie worden bewaakt door de real-time besturings elementen van Cloud App Security en Risk ante acties, zoals het downloaden van gegevens die zijn gelabeld met een ' zeer vertrouwelijke ' gevoeligheids label, direct kunnen worden geblokkeerd.
* Onderzoek Power BI gebruikers activiteit met het activiteiten logboek van Cloud App Security. Het Cloud App Security activiteiten logboek bevat Power BI-activiteit zoals vastgelegd in het Office 365-audit logboek, dat informatie bevat over alle gebruikers-en beheer activiteiten, evenals informatie over de gevoeligheids label voor relevante activiteiten zoals Toep assen, wijzigen en verwijderen. Beheerders kunnen gebruikmaken van geavanceerde filters en snelle acties van Cloud App Security voor effectief probleem onderzoek. 
* Aangepaste beleids regels maken om een waarschuwing te ontvangen over verdachte gebruikers activiteit in Power BI. De functie van het activiteiten beleid van Cloud App Security kan worden gebruikt om uw eigen aangepaste regels te definiëren, zodat u het gebruikers gedrag kunt detecteren dat afwijkt van de norm en zelfs mogelijk automatisch moet handelen als het te gevaarlijk lijkt.
* Werken met de ingebouwde anomalie detectie van Cloud App Security. Het beleid voor anomalie detectie van Cloud App Security biedt kant-en-klare gedrags analyse van gebruikers en machine learning, zodat u vanaf het begin de geavanceerde detectie van bedreigingen in uw cloud omgeving kunt uitvoeren. Wanneer een beleid voor anomalie detectie een verdacht gedrag identificeert, wordt er een beveiligings waarschuwing geactiveerd. 
* Power BI beheerdersrol in de Cloud App Security Portal. Cloud App Security biedt een toepassingsspecifieke beheerdersrol die kan worden gebruikt om Power BI beheerders alleen de machtigingen te verlenen die ze nodig hebben om toegang te krijgen tot Power BI relevante gegevens in de portal, zoals waarschuwingen, gebruikers die risico lopen, activiteiten logboeken en andere informatie die Power BI.

Zie [Microsoft Cloud app Security-besturings elementen gebruiken in Power bi](../admin/service-security-using-microsoft-cloud-app-security-controls.md) voor meer informatie.

## <a name="preview-security-features"></a>Preview-beveiligings functies

Dit onderwerp bevat een lijst met functies die zijn gepland om te worden uitgebracht tot en met 2021 maart. Omdat in dit onderwerp functies worden vermeld die nog niet zijn vrijgegeven, **kunnen bezorgings tijdlijn wijzigingen worden toegestaan en geprojecteerde functionaliteit later dan maart 2021 worden vrijgegeven of helemaal niet worden vrijgegeven**. Raadpleeg de [voor waarden voor Online Services](https://www.microsoft.com/licensing/product-licensing/products)voor meer informatie.

### <a name="bring-your-own-log-analytics-byola"></a>Uw eigen Log Analytics meenemen (BYOLA)

Gebruik uw eigen Log Analytics om de integratie tussen Power BI en Azure Log Analytics mogelijk te maken. Deze integratie omvat Azure Log Analytics geavanceerde analyse-engine, interactieve query taal en ingebouwde machine learning constructies.

## <a name="power-bi-security-questions-and-answers"></a>Beveiligings vragen en-antwoorden Power BI

De volgende vragen zijn algemene beveiligingsvragen en -antwoorden voor Power BI. Deze zijn ingedeeld op basis van het feit wanneer ze aan dit technisch document zijn toegevoegd, zodat u snel nieuwe vragen en antwoorden kunt vinden wanneer dit artikel wordt bijgewerkt. De nieuwste vragen worden toegevoegd aan het einde van deze lijst.

**Hoe maken gebruikers verbinding met gegevensbronnen en hoe worden deze geopend tijdens het gebruik van Power BI?**

* Power BI beheert referenties voor gegevens bronnen voor elke gebruiker voor Cloud referenties of voor connectiviteit via een persoonlijke gateway. Gegevens bronnen die worden beheerd door een on-premises gegevens gateway kunnen worden gedeeld door de hele onderneming en machtigingen voor deze gegevens bronnen kunnen worden beheerd door de Gateway beheerder. Bij het configureren van een gegevensset mag de gebruiker een referentie selecteren in hun persoonlijke archief of een on-premises gegevens gateway gebruiken om een gedeelde referentie te gebruiken.

    In het geval van importeren brengt een gebruiker een verbinding tot stand op basis van de aanmelding van de gebruiker en opent de gegevens met de referentie. Nadat de gegevensset is gepubliceerd naar Power BI-service, gebruikt Power BI altijd de referentie van deze gebruiker om gegevens te importeren. Zodra de gegevens zijn geïmporteerd, heeft het weer geven van de gegevens in rapporten en dash board geen toegang tot de onderliggende gegevens bron. Power BI ondersteunt verificatie met eenmalige aanmelding voor geselecteerde gegevens bronnen. Als de verbinding is geconfigureerd voor het gebruik van eenmalige aanmelding, wordt de referentie van de eigenaar van de gegevensset gebruikt om verbinding te maken met de gegevens bron.

    Voor rapporten die zijn verbonden met DirectQuery is de gegevens bron rechtstreeks verbonden met een vooraf geconfigureerde referentie. de vooraf geconfigureerde referentie wordt gebruikt om verbinding te maken met de gegevens bron wanneer een gebruiker de gegevens bekijkt. Als een gegevens bron direct is verbonden via eenmalige aanmelding, wordt de referenties van de huidige gebruiker gebruikt om verbinding te maken met de gegevens bron wanneer de gebruiker de gegevens bekijkt. Wanneer u gebruikmaakt van eenmalige aanmelding, kan beveiliging op rijniveau worden geïmplementeerd op de gegevens bron, waardoor gebruikers gegevens kunnen bekijken waartoe ze toegang hebben. Als de verbinding is met gegevens bronnen in de Cloud, wordt Azure AD-verificatie gebruikt voor eenmalige aanmelding. voor on-premises gegevens bronnen worden Kerberos, SAML en Azure AD ondersteund.  

    Wanneer u verbinding maakt met Kerberos, wordt de UPN van de gebruiker door gegeven aan de gateway en met behulp van beperkte Kerberos-delegering, wordt de gebruiker geïmiteerd en verbonden met de betreffende gegevens bronnen. SAML wordt ook ondersteund op de gateway voor SAP HANA gegevens bron. Meer informatie is beschikbaar in [overzicht van eenmalige aanmelding voor gateways](../connect-data/service-gateway-sso-overview.md).

    Als de gegevens bron is Azure Analysis Services of op een on-premises Analysis Services en beveiliging op RIJNIVEAU is geconfigureerd, wordt in de Power BI-service die beveiliging op rijniveau toegepast en kunnen gebruikers die niet voldoende referenties hebben voor toegang tot de onderliggende gegevens (dit kan een query zijn die wordt gebruikt in een dash board, rapport of een ander gegevens artefact) geen gegevens zien waarvoor de gebruiker onvoldoende machtigingen heeft.

    [Beveiliging op rijniveau met Power bi](../admin/service-admin-rls.md) kan worden gebruikt om de toegang tot gegevens voor bepaalde gebruikers te beperken. Filters beperken gegevens toegang op rijniveau en u kunt filters binnen een rol definiëren.  

**Hoe worden gegevens overgedragen naar Power BI?**

* Alle gegevens die worden aangevraagd en verzonden door Power BI, worden tijdens de verzen ding versleuteld met behulp van HTTPS (behalve wanneer de door de klant gekozen gegevens bron geen ondersteuning biedt voor HTTPS) om verbinding te maken tussen de gegevens bron en de Power BI-service. Er wordt een beveiligde verbinding met de gegevensprovider gemaakt en de gegevens stromen pas in het netwerk nadat de verbinding tot stand is gebracht.

**Hoe worden rapporten, dashboards of modelgegevens in Power BI opgeslagen en zijn deze veilig?**

* Wanneer een gegevens bron wordt geopend, volgt de Power BI-service het proces dat wordt beschreven in de sectie [verificatie naar gegevens bronnen](#authentication-to-data-sources) eerder in dit document.

**Worden gegevens van webpagina's lokaal opgeslagen door clients?**

* Wanneer browserclients Power BI openen, stellen de webservers van Power BI de instructie *Cache-Control* in op *no-store*. De instructie *no-store* geeft browsers de opdracht om de webpagina die door de gebruiker wordt bekeken niet op te slaan in de cache of in de cachemap van de client.

**Hoe zit het met beveiliging op basis van rollen, het delen van rapporten of Dash boards en gegevens verbindingen? Hoe werkt dat in termen van toegang tot gegevens, het weer geven van Dash boards, toegang tot rapporten of vernieuwen?**

* Voor **niet-RLS** ingeschakelde gegevensbronnen geldt dat wanneer een dashboard, rapport of gegevensmodel wordt gedeeld met andere gebruikers via Power BI, de gegevens beschikbaar zijn voor gebruikers waarmee deze worden gedeeld voor weergave en gebruik. Power BI verifieert gebruikers *niet* opnieuw aan de hand van de oorspronkelijke bron van de gegevens; zodra de gegevens zijn geüpload naar Power BI, is de gebruiker die is geverifieerd aan de hand van de brongegevens verantwoordelijk voor de toegang tot de gegevens door gebruikers en groepen.

  Wanneer gegevens verbindingen worden gemaakt met een gegevens bron die geschikt is voor **beveiliging op rijniveau**, zoals een Analysis Services gegevens bron, worden alleen dashboard gegevens in de cache opgeslagen in Power bi. Telkens wanneer een rapport of gegevensset wordt weergegeven of geopend in Power BI die gebruikmaakt van gegevens uit de RLS-compatibele gegevensbron, opent de Power BI-service de gegevensbron om gegevens op te halen op basis van de referenties van de gebruiker. Als de gebruiker voldoende machtigingen heeft, worden de gegevens geladen in het rapport of gegevensmodel voor de gebruiker. Als de verificatie mislukt, wordt een fout weergegeven.

  Zie de sectie [verificatie voor gegevens bronnen](#authentication-to-data-sources) eerder in dit document voor meer informatie.

**Onze gebruikers maken steeds verbinding met dezelfde gegevens bronnen, waarvan sommige referenties zijn vereist die afwijken van de referenties van hun domein. Hoe kan het voor komen dat deze referenties worden ingevoerd telkens wanneer ze een gegevens verbinding maken?**

* Power BI ondersteunt de [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md). Hiermee kunnen gebruikers referenties voor meerdere verschillende gegevensbronnen maken en deze referenties vervolgens automatisch gebruiken voor toegang tot een van deze gegevensbronnen. Zie [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md) voor meer informatie.

**Welke poorten worden gebruikt door de on-premises gegevens gateway en de persoonlijke gateway? Zijn er domein namen die moeten worden toegestaan voor connectiviteits doeleinden?**

* Het gedetailleerde antwoord op deze vraag is beschikbaar via de volgende koppeling: [Gateway poorten](/data-integration/gateway/service-gateway-communication#ports)

**Hoe worden er herstel sleutels gebruikt en waar worden deze opgeslagen bij het opslaan van de on-premises gegevens gateway? Hoe zit het met beveiligd referentie beheer?**

* Tijdens de installatie en configuratie van de gateway geeft de beheerder een **herstelsleutel** voor de gateway op. Deze **herstel sleutel** wordt gebruikt voor het genereren van een sterke AES symmetrische sleutel. Er wordt ook een asymmetrische RSA-sleutel gemaakt.

    Deze gegenereerde sleutels (RSA en AES) worden opgeslagen in een bestand op de lokale computer. Dit bestand is eveneens versleuteld. De inhoud van het bestand kan alleen worden ontsleuteld door de specifieke Windows-computer en uitsluitend door dat specifieke gatewayserviceaccount.

    Wanneer een gebruiker referenties van de gegevensbron invoert in de gebruikersinterface van de Power BI-service, worden de referenties versleuteld met de openbare sleutel in de browser. De gateway ontsleutelt de referenties met behulp van de persoonlijke RSA-sleutel en versleutelt deze opnieuw met een AES symmetrische sleutel voordat de gegevens worden opgeslagen in de Power BI-service. Door dit proces heeft de Power BI-service nooit toegang tot de niet-versleutelde gegevens.

**Welke communicatieprotocollen worden gebruikt door de on-premises gegevensgateway en hoe zijn deze beveiligd?**

* De gateway ondersteunt de volgende twee communicatieprotocollen:

  - AMQP 1,0 – TCP + TLS: voor dit protocol zijn de poorten 443, 5671-5672 en 9350-9354 vereist om te worden geopend voor uitgaande communicatie. Dit protocol heeft de voorkeur vanwege de lagere overhead aan communicatie.

  - HTTPS: websockets via HTTPS + TLS: voor dit protocol wordt alleen poort 443 gebruikt. De WebSocket wordt geïnitieerd door één HTTP CONNECT-bericht. Nadat het kanaal is ingesteld, is de communicatie in feite TCP + TLS. U kunt afdwingen dat de gateway dit protocol gebruikt door een instelling te wijzigen die wordt beschreven in het [artikel on-premises gateway](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

**Wat is de rol van Azure CDN in Power BI?**

* Zoals eerder vermeld, gebruikt Power BI het Azure Content Delivery Network (CDN) om de benodigde statische inhoud en bestanden op een efficiënte manier te distribueren naar gebruikers op basis van geografische landinstelling. Specifieker gezegd, de Power BI-service maakt gebruik van meerdere CDN's om de benodigde statische inhoud en bestanden op een efficiënte manier te distribueren naar gebruikers via het openbare internet. Deze statische bestanden bevatten productdownloads (zoals Power BI Desktop, de on-premises gegevensgateway of Power BI-apps van verschillende onafhankelijke serviceproviders), browserconfiguratiebestanden die worden gebruikt om volgende verbindingen met de Power BI-service te initiëren en tot stand te brengen, en de eerste, beveiligde Power BI-aanmeldingspagina.

  Op basis van informatie die tijdens een eerste verbinding met de Power BI-service wordt opgegeven, neemt de browser van een gebruiker contact op met de opgegeven Azure CDN (of voor bepaalde bestanden de WFE) voor het downloaden van de verzameling opgegeven algemene bestanden die nodig zijn voor de interactie van de browser met de Power BI-service. De browser pagina bevat vervolgens de Azure AD-token, sessie gegevens, de locatie van het gekoppelde back-end-cluster en de verzameling van bestanden die zijn gedownload van het Azure CDN-en WFE-cluster, voor de duur van de Power BI-service-browser sessie.

**Voor Power BI visuals voert micro soft een beveiligings-of privacy-evaluatie uit van de aangepaste Visual code voordat items naar de galerie worden gepubliceerd?**

* Nee. Het is de verantwoordelijkheid van de klant om te controleren en te bepalen of aangepaste visualcode betrouwbaar is. Alle aangepaste visualcode wordt in een sandbox-omgeving uitgevoerd zodat eventuele onjuiste code in een aangepaste visual geen nadelige invloed heeft op de rest van de Power BI-service.

**Zijn er andere Power BI-visuals waarmee gegevens buiten het klantnetwerk worden verzenden?**

* Ja. Met Bing Maps- en ESRI-visuals worden gegevens buiten de Power BI-service verzonden voor visuals die gebruikmaken van deze services.

**Voor sjabloon-apps voert micro soft een beveiligings-of privacy-evaluatie uit van de sjabloon-app voordat items naar de galerie worden gepubliceerd?**
* Nee. De uitgever van de app is verantwoordelijk voor de inhoud en het is de verantwoordelijkheid van de klant om te controleren en te bepalen of de uitgever van de sjabloon app moet worden vertrouwd. 

**Zijn er sjabloon-apps die informatie kunnen verzenden buiten het netwerk van de klant?**
* Ja. Het is de verantwoordelijkheid van de klant om het privacybeleid van de uitgever te controleren en te bepalen of de sjabloon-app moet worden geïnstalleerd op de Tenant. De uitgever is verantwoordelijk voor het informeren van de klant over het gedrag en de mogelijkheden van de app.

**Hoe zit het met data soevereiniteit? Kunnen we tenants inrichten in data centers die zich in specifieke geografies bevinden, om ervoor te zorgen dat gegevens de land grenzen niet behouden?**

* Sommige klanten in bepaalde geografische gebieden hebben de mogelijkheid om een tenant te maken in een nationale cloud waar de opslag en verwerking van gegevens gescheiden blijft van alle andere datacenters. De beveiliging van nationale clouds is iets anders omdat een afzonderlijke gegevensbeheerder namens Microsoft de nationale cloud met de Power BI-service uitvoert.

  Klanten kunnen ook een Tenant instellen in een specifieke regio. Dergelijke tenants hebben echter geen afzonderlijke gegevens beheerder van micro soft. Prijzen voor nationale clouds verschillen van die voor de algemeen beschikbare commerciële Power BI-service. Zie [Nationale Power BI-clouds](https://powerbi.microsoft.com/clouds/) voor meer informatie over de beschikbaarheid van de Power BI-service voor nationale clouds.

**Hoe behandelen micro soft verbindingen voor klanten die Power BI Premium-abonnementen hebben? Zijn deze verbindingen anders dan die welke zijn ingesteld voor de niet-Premium Power BI-service?**

* De verbindingen die tot stand zijn gebracht voor klanten met Power BI Premium-abonnementen, implementeren een B2B-autorisatie proces [(Business-to-Business) van Azure](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) met behulp van Azure AD om toegangs beheer en autorisatie in te scha kelen. Verbindingen met Power BI Premium-resources van Power BI Premium-abonnees worden met Power BI net zo afgehandeld als voor elke andere Azure AD-gebruiker.

## <a name="feedback-and-suggestions"></a>Feedback en suggesties

We stellen uw feedback op prijs. We horen graag suggesties die u hebt voor verbetering, toevoegingen of uitleg van dit technisch document of andere inhoud met betrekking tot Power BI. Uw suggesties verzenden naar [pbiss@microsoft.com](mailto:pbiss@microsoft.com) .

## <a name="additional-resources"></a>Aanvullende bronnen

Raadpleeg de volgende resources voor meer informatie over Power BI.

* [Getting Started with Power BI Desktop](../fundamentals/desktop-getting-started.md) (Aan de slag met Power BI Desktop)
* [Overzicht van de REST API voor Power BI](/rest/api/power-bi/)
* [Naslag voor API van Power BI](/rest/api/power-bi/)
* [On-premises data gateway](../connect-data/service-gateway-onprem.md) (On-premises gegevensgateway)
* [Power BI National Clouds](https://powerbi.microsoft.com/clouds/)
* [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Overzicht van eenmalige aanmelding (SSO) voor gateways in Power BI](../connect-data/service-gateway-sso-overview.md)