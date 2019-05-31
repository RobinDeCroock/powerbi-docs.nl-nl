---
title: Veelgestelde vragen over Power BI Embedded
description: Hier vindt u een lijst met veelgestelde vragen en antwoorden over Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222176"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Veelgestelde vragen over Power BI Embedded

* Als u andere vragen hebt, kunt u deze stellen [in de Power BI-community](http://community.powerbi.com/).
* Nog steeds geen antwoord? Ga naar de [ondersteuningspagina van Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Algemeen

### <a name="what-is-power-bi-embedded"></a>Wat is Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) kunnen toepassingsontwikkelaars verbluffende, volledig interactieve rapporten insluiten in hun toepassingen zonder te hoeven maken hun eigen gegevensvisualisaties en besturingselementen helemaal.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Wie is de doelgroep voor Power BI Embedded?

Ontwikkelaars en softwarebedrijven, ook wel bekend als onafhankelijke softwareleveranciers (ISV's), programmeren van toepassingen.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Hoe verschilt Power BI Embedded van de Power BI-service?

Power BI is een SaaS-oplossing (Software as a Service) voor analytische gegevens waarmee organisaties in één weergave alle meest kritieke zakelijke gegevens kunnen bekijken.

Microsoft is ontwikkeld voor ISV's willen visuals insluiten in hun toepassingen om hun analytische beslissingen klanten te helpen Power BI Embedded. Dit reserveonderdelen ISV's niet hoeft te maken van hun eigen analyseoplossing zelf. [Ingesloten analyses](embedding.md) kunnen zakelijke gebruikers toegang tot zakelijke gegevens en het uitvoeren van query's voor het genereren van inzichten in de toepassing.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Wat is het verschil tussen Power BI Premium en Power BI Embedded?

Power BI Premium is qua capaciteit afgestemd op ondernemingen die willen een volledige BI-oplossing die een centraal overzicht van de organisatie, partners, klanten en leveranciers biedt. Power BI Premium helpt uw organisatie bij het nemen van beslissingen. Power BI Premium is een SaaS-product waarmee gebruikers om inhoud via mobiele apps, intern ontwikkelde apps of de Power BI-portal te gebruiken.

Power BI Embedded is bedoeld voor ISV's die visuele elementen willen insluiten in hun toepassingen. Power BI Embedded helpt uw klanten bij de besluitvorming omdat Power BI Embedded is bedoeld voor ontwikkelaars van toepassingen en klanten van die toepassingen toegang hebben tot inhoud die is opgeslagen in capaciteit van Power BI Embedded, met inbegrip van iedereen binnen of buiten de organisatie. U kunt niet delen van Power BI Embedded-capaciteit inhoud via één klik publiceren op Internet of één muisklik publiceren naar SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Wat is de aanbeveling van Microsoft voor de keuze tussen Power BI Premium en Power BI Embedded?

Microsoft raadt aan dat ondernemingen Power BI Premium, een geavanceerde, selfservice-BI-oplossing kopen. Het is raadzaam om dat ISV 's Power BI Embedded kopen voor de cloudondersteuning ingesloten analyse-onderdelen. Een klant heeft echter geen beperkingen voor welk product te kopen.

Mogelijk zijn er enkele gevallen waarin een ISV (meestal groot), naast app wilt insluiten, wil een P-SKU gebruiken om op te halen van de extra voordelen van de vooraf verpakte Power BI-service binnen hun organisatie. Voor sommige ondernemingen is het wellicht verstandig gebruik te maken van A-SKU's in Azure als ze alleen geïnteresseerd zijn in het bouwen van Line-Of-Business-toepassingen met ingesloten analytische gegevens en niet in het gebruik van de vooraf verpakte Power BI-service.

### <a name="how-many-embed-tokens-can-i-create"></a>Hoeveel insluitingstokens kan ik maken?

Sluit tokens met PRO-licentie zijn bedoeld voor ontwikkeling, testen, zodat een Power BI-hoofdaccount of [service-principal](embed-service-principal.md) kan slechts een beperkt aantal tokens genereren. U moet [een capaciteit aanschaffen](#technical) voor het insluiten van items in een productieomgeving. Er is geen limiet voor het aantal insluitingstokens genereren van wanneer u een capaciteit aanschaffen. Ga naar [Beschikbare functies](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) om de waarde voor het gebruik te controleren. Hiermee wordt het huidige gebruik van insluittokens in procenten aangegeven.

## <a name="technical"></a>Technisch

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Wat is het verschil tussen de A-SKU's in Azure en de EM-SKU's in Office 365?

PowerBI.com is een enterprise Software als een Service (SaaS)-oplossing met veel mogelijkheden, zoals sociale samenwerking, e-mailabonnement en andere functies. PowerBI.com kunnen ISV's hun inhoud van de oplossing voor ingesloten analyse beheren en tenant-instellingen.

Power BI Embedded is dat een Platform als een Service (PaaS) van ontwikkelaars API's kunt gebruiken om een ingesloten analyse-oplossing te maken.

Hier volgt een gedeeltelijke lijst van de Functieverschillen.

| Functie | Power BI Embedded | Power BI Premium-capaciteit | Power BI Premium-capaciteit |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A-SKU's) | (EM-SKU's) | (P-SKU's) |
| Artefacten uit Power BI-app-werkruimten insluiten | Azure capaciteit | Office 365-capaciteit | Office 365-capaciteit |
| Power BI-rapporten gebruiken in een ingesloten toepassing | Ja | Ja | Ja |
| Power BI-rapporten gebruiken in SharePoint | Nee | Ja | Ja |
| Power BI-rapporten gebruiken in Dynamics | Nee | Ja | Ja |
| Power BI-rapporten gebruiken in Teams (uitgezonderd de mobiele app) | Nee | Ja | Ja |
| Inhoud op Powerbi.com en in de mobiele Power BI-app openen met een GRATIS Power BI-licentie | Nee | Nee | Ja |
| Inhoud die is ingesloten in MS Office-apps openen met een GRATIS Power BI-licentie | Nee | Ja | Ja |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI biedt nu drie SKU’s voor insluiten: A-SKU's, EM-SKU's en P-SKU's. Welke moet ik kopen voor mijn scenario?

|  |A-SKU (Power BI Embedded)  |EM-SKU (Power BI Premium)  |P-SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|Kopen  |Azure-portal |Office |Office |
|Gebruiksvoorbeelden | Inhoud insluiten in uw eigen toepassing | <li> Inhoud insluiten in uw eigen toepassing <br><br><br> <li> Inhoud insluiten in Microsoft Office-toepassingen: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (uitgezonderd de mobiele app)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Inhoud insluiten in uw eigen toepassing <br><br><br> <li> Inhoud insluiten in Microsoft Office-toepassingen: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (uitgezonderd de mobiele app)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Inhoud delen met gebruikers van Power BI via [Power BI-service](https://powerbi.microsoft.com/)  |
|Facturering |Per uur |Per maand |Per maand |
|Min. periode  |Geen minimumperiode |Jaar  |Maand/jaar |
|Differentiatie |Volledige elasticiteit: omhoog/omlaag schalen, resources onderbreken/hervatten in Azure-portal of via API  |U kunt gebruiken voor het insluiten van inhoud in SharePoint Online en Microsoft Teams (met uitzondering van mobiele app) |Insluiten in toepassingen combineren met het gebruik van de Power BI-service in dezelfde capaciteit |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Wat zijn de vereisten voor het maken van een PBIE-capaciteit in Azure?

* Meld u aan bij uw bedrijfsdirectory (Microsoft-accounts worden niet ondersteund).
* U moet beschikken over een Power BI-tenant, dat wil zeggen, ten minste één gebruiker in uw directory heeft aangemeld voor Power BI. 
* U moet een Azure-abonnement hebben in uw bedrijfsdirectory.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Hoe kan ik het verbruik van de Power BI Embedded-capaciteit bewaken?

* De [Power BI-beheerportal](../service-admin-portal.md#power-bi-embedded) gebruiken.

* De [metrische app](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) in Power BI downloaden.

* [Logboekregistratie van diagnostische gegevens in Azure](azure-pbie-diag-logs.md) gebruiken.

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Kan mijn capaciteit automatisch geschaald op mijn app-verbruik?

Hoewel er geen automatisch schalen, zijn alle API's beschikbaar om op elk gewenst moment te schalen.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Waarom wordt een capaciteit bij het maken/schalen/hervatten in de status onderbroken geplaatst?

Capaciteit inrichten (schaal/hervatten/maken) mislukken. U kunt de Details ophalen API gebruiken om te controleren van een capaciteit ProvisioningState: [Capaciteiten - Details ophalen](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Kan ik Power BI Embedded-capaciteiten alleen maken in een specifieke regio?

Met de functie [Meerdere geografische gebieden (preview)](embedded-multi-geo.md) kunt u een [Power BI Embedded-capaciteit](azure-pbie-create-capacity.md) aanschaffen in een andere regio dan uw Power BI-tenantlocatie

### <a name="how-can-i-find-my-pbi-tenant-region"></a>Hoe kan ik mijn tenant PBI regio vinden?

De portal voor aan PBI kunt u de regio van uw Tenant voor aan PBI vinden.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Over Power BI

![Over Power BI](media/embedded-faq/about-01.png)
![Tenantregio](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Wat biedt het Cloud Solution Provider (CSP)-kanaal ondersteuning?

* U kunt PBIE maken voor uw tenant met het abonnementstype CSP
* Het partneraccount kan zich aanmelden bij de klanttenant en PBIE kopen voor de klanttenant. Geef de gebruiker van de klanttenant op als Power BI-capaciteitsbeheerder.

### <a name="why-do-i-get-an-unsupported-account-message"></a>Waarom krijg ik een bericht over een niet-ondersteund account?

Voor Power BI moet u zich aanmelden met een organisatieaccount. Het registreren voor Power BI met behulp van een Microsoft-account wordt niet ondersteund.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Kan ik API's gebruiken voor het maken en beheren van Azure-capaciteiten

Ja, er zijn Powershell-cmdlets en Azure Resource Manager REST API's kunt u maken en beheren van PBIE-resources.

* [Rest-API 's](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [PowerShell-cmdlets](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Wat is de rol van de toegewezen PBI Embedded-capaciteit in een PBI Embedded-oplossing?

Naar [uw oplossing naar productie promoten](embed-sample-for-customers.md#move-to-production), moet u de Power BI-inhoud (app-werkruimte) maakt gebruik van uw toepassing toewijzen aan een capaciteit van Power BI Embedded (A-SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>In welke Azure-regio's is PBI Embedded beschikbaar?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) - Zie Product availability manager

Beschikbare regio's (16 - dezelfde regio's als Power BI)

* US (6) - US - oost, US - oost 2, US - noord-centraal, US - zuid-centraal, US - west, US - west 2
* Europa (2) - Europa - noord, Europa - west
* Azië en Stille Oceaan (2) - Azië - zuidoost, Azië - oost
* Brazilië (1) - Brazilië - zuid
* Japan (1) Japan - oost
* Australië (1) - Australië - zuidoost
* India (1) - India - west
* Canada (1) Canada Centraal
* Verenigd Koninkrijk (1) - UK - zuid

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Wat is Power BI Embedded van verificatie-model?

Power BI Embedded blijft Azure AD gebruiken voor verificatie van de hoofdgebruiker (een aangewezen Power BI Pro-licentie gebruiker) of met [service-principal](embed-service-principal.md) voor het verifiëren van de toepassing binnen Power BI.  

 Een ISV kunt implementeren hun eigen verificatie en autorisatie voor hun toepassingen.

U kunt uw bestaande directory gebruiken als u al een Azure AD-tenant. U kunt ook maken een nieuwe Azure AD-tenant voor uw veiligheid van de content ingesloten toepassing.

Als u een AAD-token wilt ophalen, kunt u één van de [Azure Active Directory-verificatiebibliotheken](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) gebruiken. Er zijn clientbibliotheken beschikbaar voor meerdere platformen.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mijn toepassing gebruikt al AAD voor verificatie van de gebruiker. Hoe kunnen we deze identiteit gebruiken bij de verificatie bij Power BI in een scenario waarin de gebruiker eigenaar is van de gegevens?

Het is standaard OAuth op namens-stroom (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). U moet uw toepassing configureren voor Power BI-service (met de vereiste bereiken) machtigingen zijn vereist. Zodra u een token aan uw app hebt, belt u gewoon aan ADAL API AcquireTokenAsync met behulp van de gebruiker toegang tot het token en geeft u de bron-URL van Power BI als de resource-ID:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Wat object-ID is de service-principal-object-ID?

De *Object-ID* van het hoofdvenster van een geregistreerde app is de object-ID voor de app.

De object-ID gevonden in de *beheerde toepassing in lokale directory > eigenschappen* sectie is de service-principal-object-ID die u wilt gebruiken. Dit object-ID is om te verwijzen naar een service-principal voor bewerkingen of om wijzigingen in het service-principal-object-id. Zoals het toepassen van een service-principal als beheerder aan een werkruimte.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Hoe verschilt Power BI Embedded van andere Azure-services?

U moet een Power BI-account hebben voordat het aanschaffen van Power BI Embedded in Azure. Uw Power BI Embedded geïmplementeerd regio bepaalt uw Power BI-account. U kunt uw Power BI Embedded-resource beheren in Azure om het volgende in te stellen:

* Omhoog/omlaag schalen
* Capaciteitsbeheerders toevoegen
* Service onderbreken/hervatten

Gebruik PowerBI.com om werkruimten toe te wijzen aan uw Power BI Embedded-capaciteit of om hun toewijzing ongedaan te maken.

### <a name="what-are-the-supported-deploy-regions"></a>Wat zijn de ondersteunde regio's implementeren?

Australië - zuidoost, Brazilië - zuid, Canada Centraal, US - oost 2, India - west, Japan - oost, US - noord-centraal, Europa - noord, US - zuid-centraal, Azië - zuidoost, VK Zuid, Europa - west, US - west en US - west 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>Welke gegevenstypen-inhoudspakket kunt u insluiten?

U *kan geen* insluiten **Dashboards** en **tegels** gebouwd op basis van het inhoudspakket gegevenssets. Echter, u *kunt* insluiten **rapporten** gebouwd op basis van de gegevensset van een inhoudspakket.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Wat is het verschil tussen het gebruik van beveiliging op rijniveau (RLS) vs. JavaScript-filters?

Er is vaak verwarring rondom wanneer beveiliging op Rijniveau ten opzichte van JavaScript-filters gebruiken, omdat een methode is over het beheren van wat een specifieke gebruiker kan zien en de andere informatie over het optimaliseren van de weergave van de gebruiker is.

Voor RLS beheert de ISV-ontwikkelaar het filteren van gegevens als onderdeel van het maken van modellen en het genereren van insluittokens. De eindgebruiker ziet alleen wat de ISV heeft ingesteld. In dit geval kan de gebruiker ervoor kiezen om minder te bekijken dan wat er met het filter wordt weergegeven, maar de gebruiker kan de RLS-configuratie niet omzeilen en meer bekijken dan is toegestaan.

De ISV besluiten wat de gebruiker ziet op de eerste weergave voor clientzijde filteren (JavaScript), maar ze geen invloed hebben op wijzigingen die de eindgebruiker van toepassing op de weergave zelf zijn mogelijk. Omdat de gebruiker de clientcode Javascript kunt activeren gegevens filteren op de back-end, deze kan niet worden als veilig beschouwd.

Raadpleeg [RLS vs JavaScript-filters](embedded-row-level-security.md#using-rls-vs-javascript-filters) voor meer informatie.

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Hoe beheer ik machtigingen voor service-principals met Power BI?

Als u inschakelt [service-principal](embed-service-principal.md) voor gebruik met Power BI, AD-machtigingen van de toepassing niet van kracht meer. De machtigingen van de toepassing worden dan beheerd via de Power BI-beheerportal.

Service-principals nemen de machtigingen voor alle instellingen van de Power BI-tenant over van hun beveiligingsgroep. Om machtigingen te beperken, een specifieke beveiligingsgroep voor service-principals maken en toe te voegen aan de **behalve specifieke beveiligingsgroepen** lijst voor de relevante, ingeschakelde instellingen van Power BI.

Deze situatie is belangrijk wanneer u de service-principal als **beheerder** aan de nieuwe werkruimte toevoegt. U kunt deze taak beheren via de [API's](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) of met de Power BI-service.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>Wanneer moet ik een toepassings-id gebruiken en wanneer de object-id van een service-principal?

De **[toepassings-id](embed-sample-for-customers.md#application-id)** wordt gebruikt om het toegangstoken te maken wanneer u de toepassings-id voor verificatie doorgeeft.

Als u naar een service-principal wilt verwijzen voor bewerkingen of om wijzigingen aan te brengen, gebruikt u de **[id van het service-principal-object](embed-service-principal.md#how-to-get-the-service-principal-object-id)** (bijvoorbeeld een service-principal als administrator op een werkruimte toepassen).

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kan een on-premises gegevensgateway worden beheerd met een service-principal?

U kunt een on-premises gegevensgateway (gegevensgateway) niet beheren met een [service-principal](embed-service-principal.md) zoals met een hoofdaccount.

Met een hoofdaccount kunt u een gegevensgateway installeren, gebruikers aan de gateway toevoegen, verbinding maken met gegevensbronnen en andere beheerderstaken uitvoeren.

Met een service-principal kunt u [beveiliging op rijniveau (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) configureren met een on-premises SSAS-gegevensbron (SQL Server Analysis Services) met een live-verbinding. Op deze manier kunt u gebruikers en hun toegang tot gegevens in SSAS beheren wanneer u deze met behulp van een service-principal integreert met **Power BI Embedded**.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Kan ik me met een service-principal aanmelden bij de Power BI-service?

Nee, met een service-principal kunt u zich niet aanmelden bij Power BI.

U kunt ook geen inhoud gebruiken als gebruiker van externe toepassingen (ingesloten SaaS), behalve wanneer u een insluittoken genereert.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Wat zijn de aanbevolen procedures om prestaties te verbeteren?

[Prestaties van Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licentieverlening

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hoe kan ik Power BI Embedded kopen?

Power BI Embedded is beschikbaar via Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Wat gebeurt er als ik al Power BI Premium aangeschaft en ik wil nu een Power BI Embedded in Azure-voordelen?

Klanten blijven betalen voor een bestaande Power BI Premium-aankopen tot het einde van hun huidige abonnementsperiode en klik vervolgens op dat moment kunnen switch hun Power BI Premium-aankopen indien nodig.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Moet ik toch nog Power BI Premium kopen om toegang te krijgen tot Power BI Embedded?

Nee, Power BI Embedded omvat de op Azure gebaseerde capaciteit die u nodig hebt om uw oplossing te implementeren en te distribueren naar klanten.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Wat is de aankoopverplichting voor Power BI Embedded?

Klanten kunnen hun gebruik op uurbasis aanpassen. Er is geen maandelijkse of jaarlijkse verplichting voor de Power BI Embedded-service.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hoe wordt het gebruik van Power BI Embedded weergegeven op mijn factuur?

De facturering voor Power BI Embedded vindt plaats volgens een voorspelbaar uurtarief op basis van het geïmplementeerde type knooppunt (of typen knooppunten). U wordt gefactureerd, zolang uw bron actief is, zelfs als er geen gebruik. U moet uw resource om te stoppen facturering onderbreken.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Wie moet een Power BI Pro-licentie voor Power BI Embedded hebben en waarom?

U hebt een Power BI Pro-licentie nodig of [service-principal](embed-service-principal.md) u REST API's. Rapporten toevoegen aan een Power BI-werkruimte, moet een analist een Power BI Pro-licentie of een service principal. Voor het beheren van Power BI-tenant en -capaciteit, een beheerder is vereist een Power BI Pro-licentie hebt.

Omdat Power BI Embedded kunt Power BI portal gebruiken voor het beheren en valideren van ingesloten inhoud, wordt de Power BI Pro-licentie is vereist voor het verifiëren van de app in PowerBI.com voor toegang tot de rapporten in de juiste opslagplaatsen.

Voor het [maken of bewerken van ingesloten rapporten](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) binnen uw eigen toepassing heeft de eindgebruiker echter geen Pro-licentie nodig, omdat deze helemaal geen Power BI-gebruiker hoeft te zijn.

### <a name="can-i-get-started-for-free"></a>Kan ik gratis aan de slag?

Ja, u kunt uw [Azure-tegoed](https://azure.microsoft.com/free/) gebruiken voor Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Is er een evaluatieversie voor Power BI Embedded in Azure?

Omdat Power BI Embedded een onderdeel van Azure is, is het mogelijk om te gebruiken van de service met de [$200 aan tegoed ontvangen bij het aanmelden voor Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Is Power BI Embedded beschikbaar voor nationale clouds (US Government, Duitsland, China)?

Power BI Embedded is ook beschikbaar voor [nationale clouds](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Is Power BI Embedded beschikbaar voor non-profitorganisaties en het onderwijs?

Er is geen speciale prijzen van Azure voor non-profitorganisaties en onderwijsinstellingen.

## <a name="power-bi-workspace-collection"></a>Power BI-werkruimteverzameling

### <a name="what-is-power-bi-workspace-collection"></a>Wat is de Power BI-werkruimteverzameling?

**Power BI-Werkruimteverzameling** (**Power BI Embedded** versie 1) is een oplossing op basis van de **Power BI-Werkruimteverzameling** Azure-resource. Met deze oplossing kunt u **Power BI Embedded**-toepassingen voor uw klanten maken met behulp van Power BI-inhoud in de **Power BI-werkruimteverzameling**, toegewezen API's en werkruimteverzamelingsleutels waarmee de toepassing kan worden geverifieerd in Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Kan ik inhoud van de Power BI-werkruimteverzameling migreren naar Power BI Embedded?

1. U kunt het hulpprogramma voor migratie gebruiken om inhoud van de **Power BI-werkruimteverzameling** te migreren naar Power BI - https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. U begint met de POC van de **Power BI Embedded**-toepassing waarin gebruik wordt gemaakt van de Power BI-inhoud.

3. Wanneer u klaar bent voor productie, koopt u toegewezen capaciteit van **Power BI Embedded** en wijst u uw Power BI-inhoud (werkruimte) aan die capaciteit toe.

    > [!Note]
    > U kunt de **Power BI-werkruimteverzameling** blijven gebruiken terwijl u daarnaast een **Power BI Embedded**-oplossing bouwt. Zodra u klaar bent, kunt u uw klant naar de nieuwe **Power BI Embedded**-oplossing verplaatsen en de **Power BI-werkruimteverzameling** buiten gebruik stellen.

Zie [Inhoud van de Power BI-werkruimteverzameling migreren naar Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded) voor meer informatie.

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Power BI-Werkruimteverzameling is op een pad afschaffing?

Ja, maar klanten die al gebruikmaken van de **Power BI-Werkruimteverzameling** oplossing kunt blijven gebruiken totdat afschaffing. Daarnaast kunnen klanten nieuwe werkruimteverzamelingen en **Power BI Embedded**-toepassingen maken die nog steeds gebruikmaken van de oplossing **Power BI-werkruimteverzameling**.

Dit betekent echter ook dat dat de nieuwe functies zijn niet toegevoegd aan een **Power BI-Werkruimteverzameling** oplossingen. We raden u aan het plannen van de migratie naar de nieuwe **Power BI Embedded** oplossing.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Wanneer wordt ondersteuning voor de Power BI-werkruimteverzameling stopgezet?

Klanten die al gebruikmaken van de oplossing voor de **Power BI-werkruimteverzamelingen** kunnen deze blijven gebruiken tot eind juni 2018 of tot het einde van de ondersteuningsovereenkomst.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>In welke regio's kan ik een Werkruimteverzameling PBI maken?

Beschikbare regio's zijn Australië - zuidoost, Brazilië - zuid, Canada Centraal, US - oost 2, Japan - oost, US - noord-centraal, Europa - noord, US - zuid-centraal, Azië - zuidoost, VK Zuid, Europa - west, India - west en US - west.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Waarom moet ik inhoud van PBI-werkruimteverzameling migreren naar Power BI Embedded?

Er zijn enkele nieuwe **Power BI Embedded** oplossing functies en mogelijkheden die u niet kunt met doen **Power BI-Werkruimteverzameling**.

Hieronder vindt u enkele voorbeelden van deze functies:
* Alle PBI-gegevensbronnen worden ondersteund. Slechts twee **Power BI-Werkruimteverzameling** gegevensbronnen worden ondersteund. 
* Nieuwe functies, zoals functies voor Q&A, vernieuwen, bladwijzers, het insluiten van dashboards en tegels, aangepaste menu's, enzovoort, worden alleen ondersteund in de **Power BI Embedded**-oplossing.
* Model voor facturering van capaciteit.

## <a name="embedding-setup-tool"></a>Het installatieprogramma voor insluiten

### <a name="what-is-the-embedding-setup-tool"></a>Wat is het installatieprogramma voor insluiten?

Met het [installatieprogramma voor insluiten](https://aka.ms/embedsetup) kunt u snel aan de slag en een voorbeeldtoepassing downloaden om met het insluiten van inhoud met behulp van Power BI te beginnen.

### <a name="which-solution-should-i-choose"></a>Welke oplossing moet ik kiezen?

* [Door inhoud voor uw klanten in te sluiten](embedding.md#embedding-for-your-customers) kunt u dashboards en rapporten insluiten voor gebruikers die geen account voor Power BI hebben. Voer de oplossing [Insluiten voor uw klanten](https://aka.ms/embedsetup/AppOwnsData) uit.
* [Met het insluiten van inhoud voor uw organisatie](embedding.md#embedding-for-your-organization) kunt u Power BI-service uitbreiden. Voer de oplossing [Insluiten voor uw organisatie](https://aka.ms/embedsetup/UserOwnsData) uit.

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Ik heb de voorbeeld-app gedownload. Welke oplossing moet ik kiezen?

Als u met de ervaring **Insluiten voor uw klanten** werkt, moet u het bestand *PowerBI-Developer-Samples.zip* opslaan en uitpakken. Open vervolgens de map *PowerBI-Developer-Samples-master\App Owns Data* en voer het bestand *PowerBIEmbedded_AppOwnsData.sln* uit.

Als u met de ervaring **Insluiten voor uw organisatie** werkt, moet u het bestand *PowerBI-Developer-Samples.zip* opslaan en uitpakken. Open vervolgens de map *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* en voer het bestand *pbi-saas-embed-report.sln* uit.

### <a name="how-can-i-edit-my-registered-application"></a>Hoe kan ik mijn geregistreerde toepassing bewerken?

Voor meer informatie over hoe u geregistreerde Azure AD-toepassingen kunt bewerken, raadpleegt u [Quickstart: Update an application in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app) (Quickstart: Een toepassing in Azure Active Directory bijwerken).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>How kan ik mijn Power BI-gebruikersprofiel of -gegevens bewerken?

U kunt [hier](https://docs.microsoft.com/power-bi/service-basic-concepts) leren hoe u uw Power BI-gegevens bewerkt.

Zie [Problemen oplossen met uw ingesloten toepassing](embedded-troubleshoot.md) voor meer informatie.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
