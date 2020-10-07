---
title: Inhoud insluiten in uw toepassing voor nationale en overheidsclouds
description: Informatie over het integreren of insluiten van een rapport, dashboard of tegel in een toepassing voor uw klanten met behulp van de Power BI-API's voor ingesloten analyse. Informatie over het integreren van Power BI in uw toepassing met behulp van software voor ingesloten analyse, hulpprogramma's voor ingesloten analyse of hulpprogramma's voor ingesloten business intelligence voor nationale en overheidsclouds.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: c5a902a8de8449290d52974063b25f51ff92dd9d
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747569"
---
# <a name="tutorial-embed-a-power-bi-content-into-your-application-for-national-clouds"></a>Zelfstudie: Power BI-inhoud insluiten in uw toepassing voor nationale clouds

Informatie over het insluiten van analytische inhoud binnen uw bedrijfsprocestoepassingen voor de nationale cloud. U kunt de Power BI .NET SDK met de Power BI JavaScript-API gebruiken om rapporten, dashboards of tegels in uw webtoepassingen in te sluiten.

Power BI ondersteunt ook [nationale clouds](/azure/active-directory/develop/authentication-national-cloud).

De verschillende nationale clouds zijn:

* U.S. Government Community Cloud (GCC)

* U. S. Government Community Cloud High (GCC High)

* U. S. Military Contractors (DoDCON)

* U. S. Military (DoD)

* Power BI-cloud voor Duitsland

* Power BI-cloud voor China

![Ingesloten dashboard](media/embed-sample-for-customers/powerbi-embed-dashboard.png)

Als u wilt beginnen met dit scenario, hebt u een **Power BI**-account nodig. Als u geen account hebt ingesteld, dan kunt u de voor u juiste nationale cloud kiezen op basis van het type overheid of land. U kunt zich aanmelden voor een [Power BI-account voor de Amerikaanse overheid](../../admin/service-govus-signup.md), een [Power BI-cloudaccount voor Duitsland](https://powerbi.microsoft.com/power-bi-germany/?ru=https%3A%2F%2Fapp.powerbi.de%2F%3FnoSignUpCheck%3D1) of een [Power BI-cloudaccount voor China](https://www.21vbluecloud.com/powerbi/).

> [!NOTE]
> Wilt u liever een dashboard insluiten voor uw organisatie? Bekijk dan [Een dashboard integreren in een app voor uw organisatie](embed-sample-for-your-organization.md).

Als u een dashboard wilt integreren in een web-app, gebruikt u de **Power BI** API en een **AD-toegangstoken** (Azure Active Directory) voor verificatie bij het ophalen van een dashboard. Vervolgens kunt u het dashboard laden met een insluittoken. De **Power BI**-API biedt programmatische toegang tot specifieke **Power BI**-resources. Zie [Power BI REST-API](/rest/api/power-bi/), [Power BI .NET-SDK] en [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) voor meer informatie.

## <a name="download-the-sample"></a>Het voorbeeld downloaden

Dit artikel bevat code die wordt gebruikt in het [App Owns Data-voorbeeld](https://github.com/Microsoft/PowerBI-Developer-Samples) in GitHub. Als u dit scenario wilt volgen, kunt u het voorbeeld downloaden. 

![App Owns Data-voorbeeld](media/embed-sample-for-customers-national-clouds/embed-sample-for-customers-026.png)

* Government Community Cloud (GCC):

    > [!NOTE]
    > Het insluiten van Power BI-inhoud van Government Community Cloud (GCC) kan alleen worden uitgevoerd met een Microsoft 365-SKU. Andere klanten van een nationale cloud kunnen [Microsoft 365- of Azure-SKU's](embedded-faq.md) gebruiken.

1. Overschrijf het bestand Cloud.config door GCCCloud.config.

2. Werk applicationId (applicationId van systeemeigen app), workspaceId, de gebruiker (hoofdgebruiker) en het wachtwoord bij in het bestand Web.config.

3. Voeg de GCC-parameters als volgt toe aan het bestand web.config.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.com/common/" />
<add key="resourceUrl" value="https://analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.powerbigov.us" />
```

* Military Contractors (DoDCON):

1. Overschrijf het bestand Cloud.config door TBCloud.config.

2. Werk applicationId (applicationId van systeemeigen app), workspaceId, de gebruiker (hoofdgebruiker) en het wachtwoord bij in het bestand Web.config.

3. Voeg de DoDCON-parameters als volgt toe aan het bestand web.config.

```xml
<add key="authorityUrl" value="https://login.microsoftonlineS.us/common/" />
<add key="resourceUrl" value="https://high.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.high.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.high.powerbigov.us" />
```

* Military (DoD):

1. Overschrijf het bestand Cloud.config door PFCloud.config.

2. Werk applicationId (applicationId van systeemeigen app), workspaceId, de gebruiker (hoofdgebruiker) en het wachtwoord bij in het bestand Web.config.

3. Voeg de DoDCON-parameters als volgt toe aan het bestand web.config.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.us/common/" />
<add key="resourceUrl" value="https://mil.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.mil.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.mil.powerbigov.us" />
```

* Parameters voor Power BI-cloud voor Duitsland

1. Overschrijf het bestand Cloud.config met inhoud van Power BI-cloud voor Duitsland.

2. Werk applicationId (applicationId van systeemeigen app), workspaceId, de gebruiker (hoofdgebruiker) en het wachtwoord bij in het bestand Web.config.

3. Voeg de parameters voor Power BI-cloud voor Duitsland als volgt toe aan het bestand web.config.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.de/common/" />
<add key="resourceUrl" value="https://analysis.cloudapi.de/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.de/" />
<add key="embedUrlBase" value="https://app.powerbi.de" />
```

* Parameters van de Power BI-cloud voor China

1. Overschrijf het bestand Cloud.config met inhoud van de [Power BI-cloud voor China](https://github.com/microsoft/PowerBI-Developer-Samples/blob/master/.NET%20Framework/Embed%20for%20your%20organization/CloudConfigs/Power%20BI%20operated%20by%2021Vianet%20in%20China/Cloud.config).

2. Werk applicationId (applicationId van systeemeigen app), workspaceId, de gebruiker (hoofdgebruiker) en het wachtwoord bij in het bestand Web.config.

3. Voeg de parameters voor de Power BI-cloud voor China als volgt toe aan het bestand web.config.

```xml
<add key="authorityUrl" value="https://login.chinacloudapi.cn/common/" />
<add key="resourceUrl" value="https://analysis.chinacloudapi.cn/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.cn/" />
<add key="embedUrlBase" value="https://app.powerbi.cn" />
```

## <a name="step-1---register-an-app-in-azure-ad"></a>Stap 1: een app bij Azure AD registreren

Registreer uw toepassing met Azure AD om REST API-aanroepen te maken. Zie [Een Azure AD-app voor het insluiten van Power BI-inhoud registreren](register-app.md) voor meer informatie. Omdat er verschillende lidmaatschappen voor nationale clouds zijn, zijn er afzonderlijke URL's om uw toepassing te registreren.

* Government Community Cloud (GCC): ```https://app.powerbigov.us/apps```

* Military Contractors (DoDCON): ```https://app.high.powerbigov.us/apps```

* Military (DoD): ```https://app.mil.powerbigov.us/apps```

* Power BI-cloud voor Duitsland: ```https://app.powerbi.de/apps```

* Power BI-cloud voor China - ```https://app.powerbi.cn/apps```

Als u het [voorbeeld voor het insluiten van inhoud voor uw klanten](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData) hebt gedownload, gebruikt u de **applicationId** die u verkrijgt, zodat het voorbeeld kan worden geverifieerd voor Azure AD. Voor het configureren van het voorbeeld wijzigt u de **applicationId** in het bestand *web.config*.

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Stap 2: een toegangstoken ophalen uit Azure AD

In uw toepassing moet u een **toegangstoken** van Azure AD ophalen voordat u de Power BI REST API kunt aanroepen. Zie [Gebruikers verifiëren en een Azure AD-toegangstoken verkrijgen voor uw Power BI-app](get-azuread-access-token.md) voor meer informatie. Omdat er verschillende lidmaatschappen voor nationale clouds zijn, zijn er afzonderlijke URL's om een toegangstoken voor uw toepassing op te halen.

* Government Community Cloud (GCC): ```https://login.microsoftonline.com```

* Military Contractors (DoDCON): ```https://login.microsoftonline.us```

* Military (DoD): ```https://login.microsoftonline.us```

* Power BI-cloud voor Duitsland: ```https://login.microsoftonline.de```

* Power BI-cloud voor China - ```https://login.chinacloudapi.cn```

U kunt voorbeelden bekijken van dit toegangstoken binnen elke inhoudsitemtaak in het bestand **Controllers\HomeController.cs**.

## <a name="step-3---get-a-content-item"></a>Stap 3: een inhoudsitem ophalen

Als u uw Power BI-inhoud wilt insluiten, moet u een aantal zaken doen om ervoor te zorgen dat dit op de juiste manier gebeurt. Al deze stappen kunt u rechtstreeks uitvoeren met de REST API, maar voor de voorbeeldtoepassing en deze voorbeelden wordt gebruikgemaakt van de .NET-SDK.

### <a name="create-the-power-bi-client-with-your-access-token"></a>De Power BI-client maken met uw toegangstoken

U maakt uw Power BI-clientobject met uw toegangstoken, zodat het kan communiceren met de Power BI-API's. U maakt uw eigen Power BI-clientobject door het AccessToken te verpakken met het object *Microsoft.Rest.TokenCredentials*.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. This is used to call the Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Het inhoudsitem dat u wilt insluiten ophalen

Gebruik het Power BI-clientobject voor het ophalen van een verwijzing naar het item dat u wilt insluiten. U kunt dashboards, tegels of rapporten insluiten. Hier volgt een voorbeeld van hoe u een eerste dashboard, tegel of rapport ophaalt uit een bepaalde werkruimte.

Een voorbeeld is beschikbaar in **Controllers\HomeController.cs** van het [App Owns Data-voorbeeld](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

#### <a name="reports"></a>Rapporten

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

#### <a name="dashboards"></a>Dashboards

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();
```

#### <a name="tiles"></a>Tegels

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// To retrieve the tile, you first need to retrieve the dashboard.

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();

// Get a list of tiles from a specific dashboard
ODataResponseListTile tiles = client.Dashboards.GetTilesInGroup(workspaceId, dashboard.Id);

// Get the first tile in the group.
Tile tile = tiles.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Het insluittoken maken

U kunt een insluittoken genereren met de JavaScript-API. Het insluittoken heeft alleen betrekking op het item dat u insluit. Dit betekent dat u een nieuw insluittoken moet maken voor elk stukje Power BI-inhoud dat u wilt insluiten. Zie [Insluittoken](/rest/api/power-bi/embedtoken) voor meer informatie, onder andere over welk **accessLevel** u moet gebruiken.

> [!IMPORTANT]
> Omdat insluittokens alleen voor ontwikkelingstesten zijn bedoeld, kan een Power BI-masteraccount een onbeperkt aantal insluittokens genereren. Er moet een [capaciteit moet worden aangeschaft](./embedded-faq.md#technical) voor insluitingsscenario's voor de productie. Het aantal te genereren insluitingstokens is onbeperkt wanneer een capaciteit is aangeschaft.

Een voorbeeld is beschikbaar in **Controllers\HomeController.cs** van het [Embedding for your organization-voorbeeld](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

Er wordt een klasse wordt gemaakt voor **EmbedConfig** en **TileEmbedConfig**. Er is een voorbeeld beschikbaar in **Models\EmbedConfig.cs** en **Models\TileEmbedConfig.cs**.

#### <a name="reports"></a>Rapporten

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

#### <a name="dashboards"></a>Dashboards

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Dashboards.GenerateTokenInGroup(workspaceId, dashboard.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = dashboard.EmbedUrl,
    Id = dashboard.Id
};
```

#### <a name="tiles"></a>Tegels

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token for a tile.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Tiles.GenerateTokenInGroup(workspaceId, dashboard.Id, tile.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new TileEmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = tile.EmbedUrl,
    Id = tile.Id,
    dashboardId = dashboard.Id
};
```

## <a name="step-4---load-an-item-using-javascript"></a>Stap 4: een item laden met JavaScript

U kunt JavaScript gebruiken om een dashboard te laden in een div-element op uw webpagina. Het voorbeeld maakt gebruik van een EmbedConfig/TileEmbedConfig-model en weergaven van een dashboard, de tegel of het rapport. Voor een volledig voorbeeld van het gebruik van de JavaScript API kunt u het [Voorbeeld van Microsoft Power BI Embedded](https://microsoft.github.io/PowerBI-JavaScript/demo) gebruiken.

Een toepassingsvoorbeeld is beschikbaar in [Voorbeeld voor insluiten voor uw organisatie](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

### <a name="viewshomeembeddashboardcshtml"></a>Views\Home\EmbedDashboard.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="dashboardContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedDashboardId
    };

    // Get a reference to the embedded dashboard HTML element
    var dashboardContainer = $('#dashboardContainer')[0];

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);
</script>
```

### <a name="viewshomeembedtilecshtml"></a>Views\Home\EmbedTile.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="tileContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read tile Id from Model
    var embedTileId = "@Model.Id";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.dashboardId";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedTileId,
        dashboardId: embedDashboardId
    };

    // Get a reference to the embedded tile HTML element
    var tileContainer = $('#tileContainer')[0];

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);
</script>
```

### <a name="viewshomeembedreportcshtml"></a>Views\Home\EmbedReport.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="next-steps"></a>Volgende stappen

* Er is een voorbeeldtoepassing beschikbaar op GitHub die u kunt bekijken. De bovenstaande voorbeelden zijn gebaseerd op dat voorbeeld. Voor meer informatie raadpleegt u [Voorbeeld voor insluiten voor uw organisatie](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

* Raadpleeg [Power BI JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript) voor meer informatie over de JavaScript-API.

* Raadpleeg [Veelgestelde vragen over de Power BI-cloud voor Duitsland](../../admin/service-govde-faq.md) voor meer informatie over de Power BI-cloud voor Duitsland

* [Inhoud van Power BI-werkruimteverzameling migreren naar Power BI](migrate-from-powerbi-embedded.md)

Overwegingen en beperkingen

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)