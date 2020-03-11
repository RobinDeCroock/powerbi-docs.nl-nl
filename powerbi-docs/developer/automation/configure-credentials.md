---
title: Referenties via een programma configureren voor Power BI
description: Referenties via een programma configureren bij het automatiseren van Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079503"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Referenties via een programma configureren voor Power BI

Volg deze stappen voor het configureren van referenties via een programma voor Power BI.

## <a name="update-credentials-flow-for-data-sources"></a>Referentiestroom bijwerken voor gegevensbronnen

1. Roep [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Gegevensbronnen ophalen ) aan om de gegevensbronnen van de gegevensset te detecteren. De antwoordtekst voor elke gegevensbron bevat type, verbindingsgegevens, gateway en gegevensbron-id.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Bouw een referentietekenreeks volgens de [voorbeelden voor datasource bijwerken](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource), afhankelijk van het type referenties.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Roep [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Gateway ophalen) aan om de openbare sleutel van de gateway op te halen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Versleutel de referenties.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    Versleutel de referentietekenreeks met de openbare sleutel van de gateway uit stap 2. Voor verschillende gatewayversies zijn wellicht verschillende openbare sleutelgrootten beschikbaar. Raadpleeg de volgende voorbeelden in de SDK-code, die beschikbaar zijn in de [PowerBI-CSharp GitHub-opslagplaats](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Bouw referentiegegevens met versleutelde referenties.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Gebruik de klasse AssymetricKeyEncriptor met de openbare sleutel die u hebt opgehaald in **Stap 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Roep [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Gegevensbron bijwerken) aan om referenties in te stellen.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Een nieuwe gegevensbron configureren voor een gegevensgateway

1. Installeer de [on-premises gegevensgateway](https://powerbi.microsoft.com/gateway/) op uw computer.

2. Roep [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Gateways ophalen) aan om de id en openbare sleutel van de gateway op te halen.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Bouw referentiegegevens, zoals beschreven in [referentiestroom voor gegevensbronnen bijwerken](#update-credentials-flow-for-data-sources), met behulp van de openbare sleutel die u hebt opgehaald in **stap 2**.

4. Stel de aanvraagtekst op.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Roep de API [Create Datasource ](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Gegevensbron maken) aan.

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Referentietypen

Als u [Gegevensbron maken](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) of [Gegevensbron bijwerken](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) aanroept onder een **on-premises bedrijfsgateway** met de [REST API van Power BI](https://docs.microsoft.com/rest/api/power-bi/), moet de waarde voor de referenties worden versleuteld met de openbare sleutel van de gateway.

>[!NOTE]
>In .NET SDK v3 kunnen ook de voorbeelden voor .NET SDK v2 worden uitgevoerd die u hieronder ziet.

### <a name="windows-and-basic-credentials"></a>Windows- en basisreferenties

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Sleutelreferenties

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2-referenties**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Anonieme referenties**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Problemen oplossen

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Er zijn geen gateway en gegevensbron-id gevonden bij het aanroepen van gegevensbronnen ophalen

Dit probleem betekent dat de gegevensset niet is gebonden aan een gateway. Bij het maken van een nieuwe gegevensset wordt automatisch voor elke cloudverbinding een gegevensbron zonder referenties gemaakt voor de cloudgateway van de gebruiker. Deze gateway wordt gebruikt voor het opslaan van de referenties voor cloudverbindingen.

Nadat u de gegevensset hebt gemaakt, wordt een automatische binding gemaakt tussen de gegevensset en een geschikte gateway, die overeenkomende gegevensbronnen voor alle verbindingen bevat. Als er geen dergelijke gateway is of meerdere geschikt gateways zijn, mislukt de automatische binding.

Als u gebruikmaakt van on-premises gegevenssets, maakt u de ontbrekende on-premises gegevensbronnen en verbindt u de gegevensset handmatig aan een gateway met [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (Aan gateway verbinden).

Als u gateways wilt detecteren die geschikt zijn voor binding, gebruikt u [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Gateway detecteren).