---
title: De configuratie van de installatie van sjabloon-apps automatiseren met een Azure-functie
description: Gebruik een voorbeeld-app om te zien hoe u sjabloon-apps voor uw klanten installeert en configureert.
author: paulinbar
ms.author: painbar
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 9a652531b90d65df985c0698d3fade7927a1907b
ms.sourcegitcommit: 24887643bd3e1b3749ce325dc0ae407432d7fee4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2021
ms.locfileid: "100490056"
---
# <a name="tutorial-automate-configuration-of-template-app-installation-using-an-azure-function"></a>Zelfstudie: De configuratie van de installatie van sjabloon-apps automatiseren met een Azure-functie

Sjabloon-apps bieden klanten een uitstekende manier om inzichten te verkrijgen op basis van hun gegevens. Met sjabloon-apps kunnen ze snel aan de slag doordat ze hiermee worden verbonden met hun gegevens. De sjabloon-apps bieden klanten vooraf ontwikkelde rapporten die ze desgewenst kunnen aanpassen.

Klanten weten niet altijd precies hoe ze verbinding kunnen maken met hun gegevens. Het kan een knelpunt voor ze zijn om deze gegevens te moeten opgeven bij het installeren van een sjabloon-app.

Als u een gegevensserviceprovider bent en een sjabloon-app hebt gemaakt om uw klanten te helpen aan de slag te gaan met hun gegevens in uw service, kunt u de installatie van uw sjabloon-app voor hen vereenvoudigen. U kunt de configuratie van de parameters van uw sjabloon-app automatiseren.

Wanneer de klant zich aanmeldt bij uw portal, selecteert deze een speciale koppeling die u hebt voorbereid. Met deze koppeling gebeurt het volgende:

- De automatisering wordt gestart, waarmee de benodigde informatie wordt verzameld.
- De parameters voor de sjabloon-app worden vooraf geconfigureerd.
- Klanten worden naar hun Power BI-account geleid waar ze de app kunnen installeren.

Ze hoeven daar alleen maar **Installeren** te selecteren en zich te verifiëren bij hun gegevensbron om aan de slag te kunnen.

De klantervaring wordt hier geïllustreerd.

![Illustratie van de gebruikerservaring waarbij de toepassing automatisch wordt geïnstalleerd.](media/template-apps-auto-install/high-level-flow.png)

In deze zelfstudie gebruikt u een Azure Functions-sample voor geautomatiseerde installatie die we hebben gemaakt om uw sjabloon-app vooraf te configureren en te installeren. We hebben dit voorbeeld voor demonstratiedoeleinden bewust eenvoudig gehouden. Het omvat het instellen van een Azure-functie zodat gebruik wordt gemaakt van Power BI-API's voor het automatisch installeren en configureren van een sjabloon-app voor uw gebruikers.

Raadpleeg [De configuratie van de installatie van een sjabloon-app automatiseren](template-apps-auto-install.md) voor meer informatie over de algemene automatiseringsstroom en de API's die door de app worden gebruikt.

Onze eenvoudige app maakt gebruik van een Azure-functie. Zie de [documentatie over Azure Functions](/azure/azure-functions/) voor meer informatie over Azure Functions.

## <a name="basic-flow"></a>Basisstroom

In de volgende basisstroom wordt de werking van de app beschreven nadat de klant deze heeft gestart door de koppeling in uw portal te selecteren.

1. De gebruiker meldt zich aan bij de portal van de onafhankelijke softwareleverancier en selecteert de opgegeven koppeling. Door deze actie wordt de stroom gestart. In deze fase wordt de gebruikersspecifieke configuratie voorbereid in de portal van de onafhankelijke softwareleverancier.

1. De onafhankelijke softwareleverancier verkrijgt een token *voor uitsluitend de app* die is gebaseerd op een [service-principal (token voor uitsluitend de app)](../embedded/embed-service-principal.md), die is geregistreerd in de tenant van de onafhankelijke softwareleverancier.

1. Met behulp van [Power BI REST API's](/rest/api/power-bi/) maakt de onafhankelijke softwareleverancier een *installatieticket* dat de configuratie van gebruikersspecifieke parameters bevat die is voorbereid door de onafhankelijke softwareleverancier.

1. De onafhankelijke softwareleverancier stuurt de gebruiker door naar Power BI met behulp van een ```POST```-omleidingsmethode die het installatieticket bevat.

1. De gebruiker wordt omgeleid naar het Power BI-account met het installatieticket en wordt gevraagd om de sjabloon-app te installeren. Wanneer de gebruiker **Installeren** selecteert, wordt de sjabloon-app geïnstalleerd.

>[!Note]
>Terwijl parameterwaarden worden geconfigureerd door de onafhankelijke softwareleverancier tijdens het proces voor het maken van het installatieticket, worden referenties voor de gegevensbron alleen in de laatste fasen van de installatie door de gebruiker verstrekt. Door deze methode wordt voorkomen dat deze worden blootgesteld aan derden en wordt er gezorgd voor een beveiligde verbinding tussen de gebruiker en de gegevensbronnen van de sjabloon-app.

## <a name="prerequisites"></a>Vereisten

* Uw eigen Azure Active Directory-tenantinstelling (Azure AD). Zie [Een Azure AD-tenant maken](../embedded/create-an-azure-active-directory-tenant.md) voor instructies voor het instellen hiervan.
* Een [service-principal (token voor uitsluitend de app)](../embedded/embed-service-principal.md) die is geregistreerd in de voorgaande tenant.
* Een geparametriseerde [sjabloon-app](../../connect-data/service-template-apps-overview.md) die gereed is voor installatie. De sjabloon-app moet worden gemaakt in dezelfde tenant als waarin u uw app registreert in Azure AD. Zie [Tips voor-sjabloon apps](../../connect-data/service-template-apps-tips.md) of [Een sjabloon-app maken in Power BI](../../connect-data/service-template-apps-create.md) voor meer informatie.
* Als u uw automatiserings werk stroom wilt testen, voegt u de Service-Principal toe aan de app-werk ruimte van de sjabloon als beheerder.
* Een Power BI Pro-licentie. Als u zich niet hebt geregistreerd voor Power BI Pro, [kunt u zich hier aanmelden voor een gratis proefversie](https://powerbi.microsoft.com/pricing/) voordat u begint.

## <a name="set-up-your-template-apps-automation-development-environment"></a>Uw ontwikkelomgeving voor de automatisering van sjabloon-apps instellen

Voordat u verdergaat met het instellen van uw app, volgt u de instructies in [Quickstart: Een Azure Functions-app maken met Azure App Configuration](/azure/azure-app-configuration/quickstart-azure-functions-csharp) om een Azure-functie samen met een Azure-appconfiguratie te ontwikkelen. Maak uw appconfiguratie zoals in het artikel wordt beschreven.

### <a name="register-an-application-in-azure-ad"></a>Een toepassing registreren in Azure AD

Maak een service-principal zoals wordt beschreven in [Power BI-inhoud insluiten met een service-principal en een app-geheim](../embedded/embed-service-principal.md).

Zorg ervoor dat u de app registreert als een **web-app aan serverzijde**. U registreert een webtoepassing aan de serverzijde om een toepassingsgeheim te maken.

Sla de *toepassings-id* (ClientID) en het *toepassingsgeheim* (ClientSecret) op voor latere stappen.

U kunt het [Installatieprogramma voor insluiten](https://aka.ms/embedsetup/AppOwnsData) uitvoeren om snel aan de slag te gaan met het maken van een app-registratie. Als u het [hulpprogramma voor app-registratie van Power BI](https://app.powerbi.com/embedsetup) gebruikt, selecteert u de optie **Insluiten voor uw klanten**.

Voeg de Service-Principal toe aan de app-werk ruimte van de sjabloon als beheerder, zodat u uw automatiserings werk stroom kunt testen.

## <a name="template-app-preparation"></a>Voorbereiding sjabloon-app

Wanneer u de sjabloon-app hebt gemaakt en deze gereed is voor installatie, slaat u de volgende informatie op voor de volgende stappen:

* *App-id*, *Pakketsleutel* en *Eigenaar-id* zoals deze worden weergegeven in de installatie-URL aan het einde van het proces [De eigenschappen van de sjabloon-app definiëren](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) toen de app werd gemaakt.

    U kunt dezelfde koppeling ook verkrijgen door **Koppeling ophalen** te selecteren in het [deelvenster Releasebeheer](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) van de sjabloon-app.

* *Parameternamen* zoals deze in de gegevensset van de sjabloon-app zijn gedefinieerd. Parameternamen zijn hoofdlettergevoelige tekenreeksen. Deze kunnen ook worden opgehaald van het tabblad **Parameterinstellingen** wanneer u [de eigenschappen van de sjabloon-app definieert](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), of uit de instellingen van de gegevensset in Power BI.

>[!NOTE]
>U kunt uw vooraf geconfigureerde installatietoepassing voor uw sjabloon-app testen als de sjabloon-app gereed is voor installatie, ook als deze nog niet openbaar beschikbaar is in AppSource. Als u wilt dat gebruikers buiten uw tenant de toepassing voor geautomatiseerde installatie kunnen gebruiken om uw sjabloon-app te installeren, moet de sjabloon-app openbaar beschikbaar zijn in de [Marketplace voor Power BI-apps](https://app.powerbi.com/getdata/services). Voordat u uw sjabloon-app distribueert met behulp van de toepassing voor geautomatiseerde installatie die u maakt, moet u ervoor zorgen dat deze wordt gepubliceerd in [Partnercentrum](/azure/marketplace/partner-center-portal/create-power-bi-app-offer).


## <a name="install-and-configure-your-template-app"></a>Uw sjabloon-app installeren en configureren

In deze sectie gebruikt u een Azure Functions-sample voor geautomatiseerde installatie die we hebben gemaakt om uw sjabloon-app vooraf te configureren en te installeren. We hebben dit voorbeeld voor demonstratiedoeleinden bewust eenvoudig gehouden. U kunt zo gebruikmaken van een [Azure-functie](/azure/azure-functions/functions-overview) en [Azure App Configuration](/azure/azure-app-configuration/overview) om de API voor geautomatiseerde installatie eenvoudig te implementeren en te gebruiken voor uw sjabloon-apps.

### <a name="download-visual-studio-version-2017-or-later"></a>Download [Visual Studio](https://www.visualstudio.com/) (versie 2017 of later)

Download [Visual Studio](https://www.visualstudio.com/) (versie 2017 of later). Download het meest recente [NuGet-pakket](https://www.nuget.org/profiles/powerbi).

### <a name="download-the-automated-installation-azure-functions-sample"></a>De Azure Functions-sample voor geautomatiseerde installatie downloaden

Download de [Azure Functions-sample voor geautomatiseerde installatie](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function) uit GitHub om aan de slag te gaan.

![Schermopname van de Azure Functions-sample voor geautomatiseerde installatie.](media/template-apps-auto-install/azure-function-sample.png)

### <a name="set-up-your-azure-app-configuration"></a>Uw Azure-appconfiguratie instellen

Als u deze sample wilt uitvoeren, moet u uw Azure-appconfiguratie instellen met de waarden en sleutels zoals hier wordt beschreven. De sleutels zijn de **toepassings-id**, het **app-geheim** en de waarden van **AppID** **PackageKey** en **OwnerId** van uw sjabloon-app. Raadpleeg de volgende secties voor informatie over het ophalen van deze waarden.

De sleutels worden ook gedefinieerd in het bestand **Constants.cs**.

| Configuratiesleutel | Betekenis           |
|---------------    |-------------------|
| TemplateAppInstall:Application:AppId | **AppId** uit de [installatie-URL](#get-the-template-app-properties) |
| TemplateAppInstall:Application:PackageKey | **PackageKey** uit de [installatie-URL](#get-the-template-app-properties) |
| TemplateAppInstall:Application:OwnerId | **OwnerId** uit de [installatie-URL](#get-the-template-app-properties) |
| TemplateAppInstall:ServicePrincipal:ClientId | [Toepassings-id](#get-the-application-id) voor de service-principal |
| TemplateAppInstall:ServicePrincipal:ClientSecret | [Toepassingsgeheim](#get-the-application-secret) voor de service-principal |
|||


Het bestand **Constants.cs** wordt hier getoond.

![Schermopname van het bestand Constant.cs.](media/template-apps-auto-install/constants-app-configuration.png)

#### <a name="get-the-template-app-properties"></a>De eigenschappen van de sjabloon-app ophalen

Vul alle relevante eigenschappen van de sjabloon-app in zoals deze zijn gedefinieerd tijdens het maken van de app. Deze eigenschappen zijn de waarden van **AppId**, **PackageKey** en **OwnerId** van de sjabloon-app.

Voer de volgende stappen uit om de voorgaande waarden op te halen:

1. Meld u aan bij [Power BI](https://app.powerbi.com).

1. Ga naar de oorspronkelijke werkruimte van de app.

1. Open het deelvenster **Releasebeheer**.

    ![Schermopname van het deelvenster Releasebeheer.](media/template-apps-auto-install/release-management-001.png)

1. Selecteer de app-versie en haal de bijbehorende installatiekoppeling op.

    ![Schermopname van de knop Releasebeheer.](media/template-apps-auto-install/release-management-002.png)

1. Kopieer de koppeling naar het klembord.

    ![Schermopname van de knop Koppeling ophalen.](media/template-apps-auto-install/release-management-003.png)

1. Deze installatie-URL bevat de drie URL-parameters waarvan u de waarden nodig hebt. Gebruik de waarden van **appID**, **PackageKey** en **ownerId** voor de toepassing. Een voorbeeld-URL ziet er ongeveer uit zoals hier wordt weergegeven.

    ```html
    https://app.powerbi.com/Redirect?action=InstallApp&appId=3c386...16bf71c67&packageKey=b2df4b...dLpHIUnum2pr6k&ownerId=72f9...1db47&buildVersion=5
    ```

#### <a name="get-the-application-id"></a>De toepassings-id ophalen

Vul bij **applicationId** de toepassings-id van Azure in. De waarde van **applicationId** wordt door de toepassing gebruikt om zich te identificeren bij de gebruikers bij wie u machtigingen aanvraagt.

Ga als volgt te werk om de toepassings-id op te halen:

1. Meld u aan bij [Azure Portal](https://portal.azure.com).

1. Selecteer in het linkerdeelvenster **Alle services** > **App-registraties**.

    ![Schermopname van het zoeken naar app-registraties.](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. Selecteer de toepassing waarvoor de **toepassings-id** nodig is.

    ![Schermopname van het kiezen van een app.](media/template-apps-auto-install/embed-sample-for-customers-006.png)

1. Er is een toepassings-id die wordt vermeld als een GUID. Gebruik deze toepassings-id als de **applicationId** voor de toepassing.

    ![Schermopname van de waarde van applicationId.](media/template-apps-auto-install/embed-sample-for-customers-007.png)

#### <a name="get-the-application-secret"></a>Het toepassingsgeheim verkrijgen

Geef de **ApplicationSecret**-gegevens op in de sectie **Sleutels** van de sectie **App-registraties** in Azure. Dit kenmerk werkt wanneer u een [service-principal](../embedded/embed-service-principal.md) gebruikt.

Ga als volgt te werk om het toepassingsgeheim op te halen:

 1. Meld u aan bij [Azure Portal](https://portal.azure.com).

 1. Selecteer in het linkerdeelvenster **Alle services** > **App-registraties**.

    ![Schermopname van het zoeken naar de app-registratie.](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. Selecteer de toepassing die het **toepassingsgeheim** moet gebruiken.

    ![Schermopname van het kiezen van een app.](media/template-apps-auto-install/embed-sample-for-customers-0038.png)

1. Selecteer **Certificaten en geheimen** onder **Beheren**.

1. Selecteer **Nieuwe clientgeheimen**.

1. Voer in het vak **Beschrijving** een naam in en selecteer een duur. Selecteer vervolgens **Opslaan** om de waarde voor uw toepassing op te halen. Wanneer u het deelvenster **Sleutels** sluit nadat u de sleutelwaarde hebt opgeslagen, wordt het veld **Waarde** alleen nog als verborgen weergegeven. Op dat punt kunt u de sleutelwaarde niet meer ophalen. Als u de sleutelwaarde kwijtraakt, kunt u een nieuwe maken in Azure Portal.

    ![Schermopname van de sleutelwaarde.](media/template-apps-auto-install/embed-sample-for-customers-042.png)

## <a name="test-your-function-locally"></a>Uw functie lokaal testen

Voer de stappen uit zoals deze staan beschreven in [De functie lokaal uitvoeren](/azure/azure-functions/functions-create-your-first-function-visual-studio#run-the-function-locally) om uw functie uit te voeren.

Configureer uw portal zo dat een ```POST```-aanvraag wordt verzonden naar de URL van de functie. Een voorbeeld is ```POST http://localhost:7071/api/install```. De aanvraagbody moet een JSON-object zijn waarmee sleutel-waardeparen worden beschreven. Sleutels zijn *parameternamen* zoals gedefinieerd in Power BI Desktop. Waarden zijn de gewenste waarden die moeten worden ingesteld voor elke parameter in de sjabloon-app.

>[!Note]
> In een productieomgeving worden parameterwaarden voor elke gebruiker afgeleid door de beoogde logica van uw portal.

De gewenste stroom moet zijn:

1. De portal bereidt de aanvraag per gebruiker of sessie voor.
1. De ```POST /api/install```-aanvraag wordt naar uw Azure-functie verzonden. De aanvraagbody bestaat uit sleutel-waardeparen. De sleutel is de parameternaam. De waarde is de gewenste waarde die moet worden ingesteld.
1. Als alles juist is geconfigureerd, leidt de browser de gebruiker automatisch om naar het Power BI-account van de klant en wordt de stroom voor de geautomatiseerde installatie weergegeven.
1. Bij de installatie worden parameterwaarden ingesteld zoals geconfigureerd in stap 1 en 2.
 
## <a name="next-steps"></a>Volgende stappen

### <a name="publish-your-project-to-azure"></a>Uw project naar Azure publiceren

U kunt uw project publiceren in Azure door de instructies in de [documentatie over Azure Functions](/azure/azure-functions/functions-create-your-first-function-visual-studio#publish-the-project-to-azure) te volgen. Vervolgens kunt u API‘s voor geautomatiseerde installatie van de sjabloon-app integreren in uw product en deze gaan testen in productieomgevingen.