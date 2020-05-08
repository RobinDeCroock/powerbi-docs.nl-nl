---
title: Een verificatietoegangstoken ophalen
description: Stapsgewijze uitleg van het pushen van gegevens - Een verificatietoegangstoken ophalen
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 7e74b01a6b12302393a3e4bc40b2e9cccfc13d63
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "79488264"
---
# <a name="step-2-get-an-authentication-access-token"></a>Stap 2: Een toegangstoken voor verificatie ophalen

Dit artikel is de tweede stap in de reeks [Gegevens naar een Power BI-gegevensset pushen](walkthrough-push-data.md).

In stap 1 [hebt u een client-app geregistreerd bij Azure AD](../embedded/register-app.md). In deze stap krijgt u een verificatietoegangstoken. Power BI-apps worden geïntegreerd met Azure Active Directory om beveiligde aanmelding en autorisatie voor uw app te verzorgen. Uw app gebruikt een token om te verifiëren bij Azure AD en toegang te krijgen tot Power BI-resources.

## <a name="get-an-authentication-access-token"></a>Een verificatietoegangstoken ophalen

Zorg er voordat u begint voor dat u de [vorige stap](../embedded/register-app.md) in de reeks [Gegevens naar een Power BI-gegevensset pushen](walkthrough-push-data.md) hebt voltooid. 

Voor deze procedure is Visual Studio 2015 of hoger vereist.

1. Maak in Visual Studio een nieuw C# **Consoletoepassing**-project.

2. Installeer het [Azure AD Authentication Library-pakket voor .NET-NuGet](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727). Uw .Net-app heeft dit pakket nodig om een verificatietoegangstoken op te halen. 

     a. Selecteer **Extra** > **NuGet-pakketbeheer** > **Package Manager Console**.

     b. Voer **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612** in

     c. Voeg in Program.cs `using Microsoft.IdentityModel.Clients.ActiveDirectory;` toe.

3. Voeg de voorbeeldcode die wordt weergegeven na deze stappen, toe aan Program.cs.

4. Vervang {ClientID} door de **client-id** die u hebt gekregen in het [vorige artikel van de reeks](../embedded/register-app.md) toen u uw app registreerde.

5. Voer uw console-app uit en meld u aan bij uw Power BI-account. 

   U ziet nu een tokentekenreeks in het consolevenster.

**Voorbeeldcode voor het ophalen van een verificatietoegangstoken**

Voeg deze code toe aan Program {...}.

* Een tokenvariabele voor het aanroepen van bewerkingen: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* In static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Een methode GetToken() toevoegen:

```csharp
       #region Get an authentication access token
       private static string GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Nadat u een verificatietoken hebt opgehaald, kunt u elke Power BI-bewerking aanroepen.

In het volgende artikel in deze reeks ziet u hoe u [een gegevensset maakt in Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Volledige vermelding van de code

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Volgende stappen

* Het volgende artikel in deze reeks is [Een gegevensset maken in Power BI](walkthrough-push-data-create-dataset.md)
* [Overview of Power BI REST API](overview-of-power-bi-rest-api.md) (Overzicht van de REST-API voor Power BI)  
* [Power BI REST API's](https://docs.microsoft.com/rest/api/power-bi/)  

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)