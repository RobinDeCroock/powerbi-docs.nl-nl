---
title: Gebruikers verifiëren en een Azure AD-toegangstoken ophalen voor uw toepassing
description: Informatie over het registreren van een toepassing in Azure Active Directory voor gebruik met ingesloten Power BI-inhoud.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/04/2019
ms.openlocfilehash: 8b20ee4fbac3c4b22bd420e49df0bc1fbfd6e300
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746603"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Een Azure AD-toegangstoken ophalen voor uw Power BI-toepassing

In dit artikel wordt uitgelegd hoe u gebruikers kunt verifiëren in uw Power BI-toepassing en een toegangstoken kunt ophalen voor gebruik met de [Power BI REST API](/rest/api/power-bi/).

Voordat uw app de REST API kan aanroepen, moet u een **verificatietoegangstoken** ophalen voor Azure Active Directory (Azure AD). Uw app gebruikt een token om toegang te krijgen tot Power BI-dashboards, -tegels en -rapporten. Zie [Authorize access to Azure Active Directory web applications using the OAuth 2.0 code grant flow](/azure/active-directory/develop/v1-protocols-oauth-code) (Toegang tot Azure Active Directory-webtoepassingen autoriseren met de OAuth 2.0-stroom voor codetoewijzing) voor meer informatie.

Afhankelijk van hoe u inhoud insluit, wordt het toegangstoken op een andere manier opgehaald. In dit artikel komen twee verschillende benaderingen aan bod.

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Toegangstoken voor Power BI-gebruikers (gebruikers is eigenaar van gegevens)

Dit voorbeeld is bestemd voor gevallen waarin uw gebruikers zich handmatig bij Azure AD aanmelden met hun organisatieaanmeldingsgegevens. Deze taak wordt gebruikt bij het insluiten van inhoud voor gebruikers met toegang tot de Power BI-service.

### <a name="get-an-azure-ad-authorization-code"></a>Een Azure AD-autorisatiecode ophalen

De eerste stap voor het ophalen van een **toegangstoken** bestaat uit het ophalen van een autorisatiecode van **Azure AD**. Maak een querytekenreeks met de volgende eigenschappen en stuur deze terug naar **Azure AD**.

#### <a name="authorization-code-query-string"></a>Querytekenreeks met autorisatiecode

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

Nadat u de querytekenreeks hebt gemaakt, stuurt u deze naar **Azure AD** om een **autorisatiecode** te verkrijgen.  Hieronder staat een volledige C#-methode voor het maken van een querytekenreeks met een **autorisatiecode** en het sturen hiervan naar **Azure AD**. Vervolgens gebruikt u de **autorisatiecode** om een **toegangstoken** op te halen.

Binnen redirect.aspx.cs wordt vervolgens [AuthenticationContext.AcquireTokenByAuthorizationCode](/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync?view=azure-dotnet#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) aangeroepen om het token te genereren.

#### <a name="get-authorization-code"></a>Autorisatiecode verkrijgen

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>Een toegangstoken verkrijgen op basis van een autorisatiecode

Zodra **Azure AD** een **autorisatiecode** terugstuurt naar uw webapp, kunt u deze gebruiken om een toegangstoken op te halen. Hieronder ziet u een C#-voorbeeld dat u kunt gebruiken op uw omleidingspagina, en de `Page_Load`-gebeurtenis voor de default.aspx.

U kunt de naamruimte **Microsoft.IdentityModel.Clients.ActiveDirectory** ophalen uit het [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet-pakket.

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Toegangstoken voor niet-Power BI-gebruikers (app is eigenaar van gegevens)

Deze benadering wordt meestal gebruikt voor ISV-toepassingen waarbij de app eigenaar is van toegang tot de gegevens. Gebruikers zijn niet noodzakelijkerwijs Power BI-gebruikers en de toepassing bepaalt de gebruikersverificatie en -toegang.

### <a name="access-token-with-a-master-account"></a>Toegangstoken met een hoofdaccount

Voor deze benadering gebruikt u een enkel *hoofd*account dat een Power BI Pro-gebruiker is. De accountreferenties worden in de toepassing opgeslagen. Deze opgeslagen referenties worden door de toepassing gebruikt om te verifiëren bij Azure AD. De onderstaande voorbeeldcode is afkomstig uit het [voorbeeld waarbij de app eigenaar is van de gegevens](https://github.com/guyinacube/PowerBI-Developer-Samples)

### <a name="access-token-with-service-principal"></a>Toegangstoken met service-principal

Voor deze benadering gebruikt u een [service-principal](embed-service-principal.md). Dit is een token **alleen voor apps**. Deze service-principal wordt door de toepassing gebruikt om te verifiëren bij Azure AD. De onderstaande voorbeeldcode is afkomstig uit het [voorbeeld waarbij de app eigenaar is van de gegevens](https://github.com/guyinacube/PowerBI-Developer-Samples)

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var AuthorityURL  = "https://login.microsoftonline.com/common/"
var ResourceURL  = "https://analysis.windows.net/powerbi/api"
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>Problemen oplossen

Foutbericht: 'AuthenticationContext' doesn't contain a definition for 'AcquireToken' and no accessible 'AcquireToken' accepting a first argument of type 'AuthenticationContext' could be found (are you missing a using directive or an assembly reference?) (AuthenticationContext bevat geen definitie voor AcquireToken en er is geen toegankelijk AcquireToken gevonden dat een eerste argument van het type AuthenticationContext accepteert (ontbreekt er een USING-instructie of een assemblyverwijzing?)).

   Download [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) als deze fout wordt weergegeven.

## <a name="next-steps"></a>Volgende stappen

Nu u het toegangstoken hebt, kunt u de Power BI REST API aanroepen om inhoud in te sluiten. Zie [How to embed your Power BI content](embed-sample-for-customers.md#embed-content-within-your-application) (Uw Power BI-inhoud insluiten) voor informatie.

Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).