---
title: Een gegevensset maken
description: 'Stappen: Gegevens naar een gegevensset pushen: een gegevensset maken in Power BI'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: 149b4f8663838c0a87609a1ec24358fb9ee9727e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "80403644"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>Stap 3: Een gegevensset maken in Power BI
Dit artikel maakt deel uit van een stapsgewijze uitleg van hoe u [gegevens naar een gegevensset pusht](walkthrough-push-data.md).

In **stap 2** van Gegevens naar een gegevensset pushen, [Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md), hebt u een token opgehaald voor verificatie bij **Azure AD**. In deze stap gebruikt u de token om de bewerking [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) aan te roepen.

Als u een REST-resource aanroept, gebruikt u een URL die de resource zoekt en verzendt u een JSON-tekenreeks (JavaScript Object Notation), waarin de gegevensset wordt beschreven, naar de resource van de Power BI-service. Een REST-resource geeft het deel van de Power BI-service aan waarmee u wilt werken. Als u gegevens naar de gegevensset wilt pushen, is de doelresource een **gegevensset**. De URL waarmee een gegevensset wordt geïdentificeerd is `https://api.PowerBI.com/v1.0/myorg/datasets`. Als u de gegevens binnen een groep pusht, is de URL `https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets`.

Als u een REST-bewerking voor Power BI wilt verifiëren, voegt u de token die u hebt gekregen in [Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md) toe aan een aanvraagheader:

Wanneer u de bewerking [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) aanroept, wordt een nieuwe gegevensset gemaakt. 

![](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

U maakt als volgt een gegevensset in Power BI.

## <a name="create-a-dataset-in-power-bi"></a>Een gegevensset maken in Power BI
> [!NOTE]
> Voordat u begint, zorgt u dat u de vorige stappen in [Gegevens naar een gegevensset pushen](walkthrough-push-data.md) hebt gevolgd.
> 
> 

1. In het consoletoepassingsproject dat u hebt gemaakt in [Stap 2: Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md) voegt u **using System.Net;** en **using System.IO;** toe aan Program.cs.
2. Voeg de onderstaande code toe in Program.cs.
3. Voer de console-app uit en meld u aan bij uw Power BI-account. U ziet **Gegevensset gemaakt** in het consolevenster. U kunt zich ook aanmelden bij Power BI om de nieuwe gegevensset te zien.

**Voorbeeldgegevens naar een gegevensset pushen**

Voeg deze code toe in Program.cs.

* In static void Main(string[] args):
  
    ```csharp
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* Voeg de methode CreateDataset() toe:
  
    ```csharp
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

In de volgende stap ziet u hoe u [een gegevensset ophaalt om rijen toe te voegen aan een Power BI-tabel](walkthrough-push-data-get-datasets.md).

Hieronder ziet u de [volledige code](#code).

<a name="code"/>

## <a name="complete-code-listing"></a>Volledige vermelding van de code

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

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


        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion
    }
}
```

[Volgende stap >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>Volgende stappen
* [Een gegevensset ophalen om rijen toe te voegen aan een Power BI-tabel](walkthrough-push-data-get-datasets.md)  
* [Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md)  
* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
* [Gegevens pushen naar een Power BI-dashboard](walkthrough-push-data.md)  
* [Overview of Power BI REST API](overview-of-power-bi-rest-api.md) (Overzicht van de REST-API voor Power BI)  
* [Power BI REST API reference](https://docs.microsoft.com/rest/api/power-bi/) (Naslag voor REST-API voor Power BI)  

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

