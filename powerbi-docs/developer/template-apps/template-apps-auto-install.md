---
title: De configuratie van de installatie van sjabloon-apps automatiseren voor uw klanten
description: Meer informatie over het automatiseren van de configuratie van de installatie van sjabloon-apps.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 33de464a1bb1389fadfbc7a85ded9365321e0a62
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926292"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Automatische configuratie van de-installatie van een sjabloon-app

Sjabloon-apps bieden klanten een uitstekende manier om inzichten te verkrijgen op basis van hun gegevens. Met sjabloon-apps kunnen ze snel aan de slag doordat ze hiermee worden verbonden met hun gegevens. De sjabloon-apps bieden vooraf ontwikkelde rapporten die ze desgewenst kunnen aanpassen.

Klanten weten niet altijd precies hoe ze verbinding kunnen maken met hun gegevens. Het kan een knelpunt voor ze zijn om deze gegevens te moeten opgeven bij het installeren van een sjabloon-app.

Als u een gegevensserviceprovider bent en een sjabloon-app hebt gemaakt om uw klanten te helpen aan de slag te gaan met hun gegevens in uw service, kunt u de installatie van uw sjabloon-app voor hen vereenvoudigen. U kunt de configuratie van de parameters van uw sjabloon-app automatiseren. Wanneer de klant zich aanmeldt bij uw portal, selecteert deze een speciale koppeling die u hebt voorbereid. Met deze koppeling gebeurt het volgende:

- De automatisering wordt gestart, waarmee de benodigde informatie wordt verzameld.
- De parameters voor de sjabloon-app worden vooraf geconfigureerd.
- Klanten worden naar hun Power BI-account geleid waar ze de app kunnen installeren.

Ze hoeven daar alleen maar **Installeren** te selecteren en zich te verifiëren bij hun gegevensbron om aan de slag te kunnen.

De klantervaring wordt hier geïllustreerd.

![Illustratie van de gebruikerservaring waarbij de toepassing automatisch wordt geïnstalleerd.](media/template-apps-auto-install/high-level-flow.png)

In dit artikel worden de basisstroom, de vereisten en de belangrijkste stappen en API's beschreven die u nodig hebt voor het automatiseren van de configuratie van de installatie van de sjabloon-app. Als u meteen aan de slag wilt gaan, kunt u doorgaan naar de [zelfstudie](template-apps-auto-install-tutorial.md), waar u de configuratie van de installatie van de sjabloon-app automatiseert met behulp van een eenvoudige, al voorbereide sampletoepassing waarin een Azure-functie wordt gebruikt.

## <a name="basic-flow"></a>Basisstroom

De basisstroom voor het automatiseren van de configuratie van de installatie van een sjabloon-app is als volgt:

1. De gebruiker meldt zich aan bij de portal van de onafhankelijke softwareleverancier en selecteert de opgegeven koppeling. Door deze actie wordt de automatische stroom gestart. In deze fase wordt de gebruikersspecifieke configuratie voorbereid in de portal van de onafhankelijke softwareleverancier.

1. De onafhankelijke softwareleverancier verkrijgt een token *voor uitsluitend de app* die is gebaseerd op een [service-principal (token voor uitsluitend de app)](../embedded/embed-service-principal.md), die is geregistreerd in de tenant van de onafhankelijke softwareleverancier.

1. Met behulp van [Power BI REST API's](https://docs.microsoft.com/rest/api/power-bi/) maakt de onafhankelijke softwareleverancier een *installatieticket* dat de configuratie van gebruikersspecifieke parameters bevat die is voorbereid door de onafhankelijke softwareleverancier.

1. De onafhankelijke softwareleverancier stuurt de gebruiker door naar Power BI met behulp van een ```POST```-omleidingsmethode die het installatieticket bevat.

1. De gebruiker wordt omgeleid naar het Power BI-account met het installatieticket en wordt gevraagd om de sjabloon-app te installeren. Wanneer de gebruiker **Installeren** selecteert, wordt de sjabloon-app geïnstalleerd.

>[!Note]
>Terwijl parameterwaarden worden geconfigureerd door de onafhankelijke softwareleverancier tijdens het proces voor het maken van het installatieticket, worden referenties voor de gegevensbron alleen in de laatste fasen van de installatie door de gebruiker verstrekt. Door deze methode wordt voorkomen dat deze worden blootgesteld aan derden en wordt er gezorgd voor een beveiligde verbinding tussen de gebruiker en de gegevensbronnen van de sjabloon-app.

## <a name="prerequisites"></a>Vereisten

De volgende vereisten zijn vereist om een vooraf geconfigureerde installatie-ervaring voor uw sjabloon-app te leveren:

* Een Power BI Pro-licentie. Als u zich niet hebt geregistreerd voor Power BI Pro, [kunt u zich hier aanmelden voor een gratis proefversie](https://powerbi.microsoft.com/pricing/) voordat u begint.
* Uw eigen Azure Active Directory-tenantinstelling (Azure AD). Zie [Een Azure AD-tenant maken](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant) voor instructies voor het instellen hiervan.
* Een **service-principal (token voor uitsluitend de app)** die is geregistreerd in de voorgaande tenant. Zie [Power BI-inhoud insluiten met service-principal en een toepassingsgeheim](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal) voor meer informatie. Zorg ervoor dat u de app registreert als een **web-app aan serverzijde**. U registreert een webtoepassing aan de serverzijde om een toepassingsgeheim te maken. Sla de *toepassings-id* (ClientID) en het *toepassingsgeheim* (ClientSecret) van dit proces op voor latere stappen.
* Een **geparametriseerde sjabloon-app** die gereed is voor installatie. De sjabloon-app moet worden gemaakt in dezelfde tenant als waarin u uw app registreert in Azure AD. Zie [Tips voor sjabloon-apps](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips) of [Een sjabloon-app maken in Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create) voor meer informatie. Noteer de volgende informatie uit de sjabloon-app voor de volgende stappen:
     * *App-id*, *Pakketsleutel* en *Eigenaar-id* zoals deze worden weergegeven in de installatie-URL aan het einde van het proces voor het [definiëren van de eigenschappen van de sjabloon-app](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) toen de app werd gemaakt. U kunt dezelfde koppeling ook verkrijgen door **Koppeling ophalen** te selecteren in het deelvenster [Releasebeheer](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) van de sjabloon-app.
    * *Parameternamen* zoals deze in de gegevensset van de sjabloon-app zijn gedefinieerd. Parameternamen zijn hoofdlettergevoelige tekenreeksen en kunnen ook worden opgehaald van het tabblad **Parameterinstellingen** wanneer u [de eigenschappen van de sjabloon-app definieert](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) of uit de instellingen van de gegevensset in Power BI.

    >[!NOTE]
    >U kunt uw vooraf geconfigureerde installatietoepassing voor uw sjabloon-app testen als de sjabloon-app gereed is voor installatie, ook als deze nog niet openbaar beschikbaar is in AppSource. Als u wilt dat gebruikers buiten uw tenant de toepassing voor geautomatiseerde installatie kunnen gebruiken om uw sjabloon-app te installeren, moet de sjabloon-app openbaar beschikbaar zijn in de [Marketplace voor Power BI-apps](https://app.powerbi.com/getdata/services). Voordat u uw sjabloon-app distribueert met behulp van de toepassing voor geautomatiseerde installatie die u maakt, moet u ervoor zorgen dat deze wordt gepubliceerd in [Partnercentrum](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Belangrijkste stappen en API's

In de volgende secties worden de belangrijkste stappen beschreven waarmee u de configuratie van de installatie van een sjabloon-app en de benodigde API's kunt configureren. Hoewel de meeste stappen met [Power BI REST API's](https://docs.microsoft.com/rest/api/power-bi/) worden uitgevoerd, zijn de hier beschreven codevoorbeelden gemaakt met de .NET SDK.

## <a name="step-1-create-a-power-bi-client-object"></a>Stap 1: een Power BI-clientobject maken

Voor het gebruik van Power BI REST API's is het vereist dat u een *toegangstoken* voor uw [service-principal](../embedded/embed-service-principal.md) uit Azure AD ophaalt. U moet een [Azure Active Directory-toegangstoken ophalen](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) voor uw Power BI-toepassing voordat u de [Power BI REST API's](https://docs.microsoft.com/rest/api/power-bi/) kunt aanroepen.
Als u de Power BI-client met uw toegangstoken wilt maken, moet u uw Power BI-clientobject maken zodat u interacties met de [Power BI REST-API's](https://docs.microsoft.com/rest/api/power-bi/) kunt uitvoeren. U maakt het **Power BI-clientobject** door het AccessToken te verpakken met het object **Microsoft.Rest.TokenCredentials**.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Stap 2: een installatieticket maken

Maak een installatieticket, dat wordt gebruikt wanneer u uw gebruikers omleidt naar Power BI. De API die voor deze bewerking wordt gebruikt, is de API **CreateInstallTicket**.
* [Template Apps CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Een voorbeeld voor het maken van een installatieticket voor de installatie en configuratie van sjabloon-apps is beschikbaar via het bestand [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) in de [voorbeeldtoepassing](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


Het volgende codevoorbeeld geeft aan hoe de REST API **CreateInstallTicket** van de sjabloon app moet worden gebruikt.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Stap 3: gebruikers omleiden naar Power BI met het ticket

Nadat u een installatieticket hebt gemaakt, gebruikt u dit om uw gebruikers om te leiden naar Power BI om door te gaan met de installatie en configuratie van de sjabloon-app. U gebruik een methode ```POST``` voor omleiding naar de installatie-URL van de sjabloon-app, waarbij het installatieticket is opgenomen in de bijbehorende aanvraagbody.

Er zijn verschillende gedocumenteerde methoden voor het verlenen van een omleiding met behulp van ```POST```-aanvragen. Welke u moet kiezen, is afhankelijk van het scenario en hoe uw gebruikers interactie met uw portal of service uitvoeren.

Een eenvoudig voorbeeld, dat meestal wordt gebruikt voor testdoeleinden, maakt gebruik van een formulier met een verborgen veld, dat automatisch wordt verzonden tijdens het laden.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

Het volgende voorbeeld van het antwoord van de [voorbeeldtoepassing](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample) bevat het installatieticket en zorgt ervoor dat gebruikers automatisch worden omgeleid naar Power BI. Het antwoord voor deze Azure-functie is gelijk aan het automatisch verzenden van het formulier in het voorgaande HTML-voorbeeld.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>Er zijn verschillende methoden voor het gebruik van ```POST```-browseromleidingen. Gebruik altijd de veiligste methode, die afhankelijk is van de vereisten en beperkingen van uw service. Houd er rekening mee dat sommige vormen van onveilige omleiding ertoe kunnen leiden dat uw gebruikers of service worden blootgesteld aan beveiligingsproblemen.

## <a name="step-4-move-your-automation-to-production"></a>Stap 4: uw automatisering naar productie verplaatsen

Wanneer de automatisering die u hebt ontworpen klaar is, moet u deze naar productie verplaatsen.

## <a name="next-steps"></a>Volgende stappen

* Probeer onze [zelfstudie](template-apps-auto-install-tutorial.md) waarin een eenvoudige Azure-functie wordt gebruikt voor het automatiseren van de configuratie van de installatie van een sjabloon-app.
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).
