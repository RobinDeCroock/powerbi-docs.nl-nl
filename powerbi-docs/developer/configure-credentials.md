---
title: Referenties via een programma configureren voor Power BI
description: Referenties via een programma configureren voor Power BI voor automatisering
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836601"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Referenties via een programma configureren voor Power BI

Volg deze stappen voor het configureren van referenties via een programma voor Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Een referentiestroom configureren voor gegevensbronnen

1. Roep [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Gegevensbronnen ophalen ) aan om de gegevensbronnen van de gegevensset te detecteren. De antwoordtekst voor elke gegevensbron bevat het type, verbindingsgegevens, gateway en gegevens-id.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Bouw een referentietekenreeks volgens de [voorbeelden voor datasource bijwerken](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource), afhankelijk van het type referenties.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Bouw de referentiedetails.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Roep [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Gegevensbron bijwerken) aan om referenties in te stellen met de gateway en bron-id uit stap 1 en met de referentiegegevens uit stap 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Verlopen referentiestroom voor on-premises gegevensbron

1. [Voer stap 1 en 2 uit het vorige scenario uit](#configure-a-credential-flow-for-data-sources).

2. Roep [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Gateway ophalen) aan om de openbare sleutel van de gateway op te halen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Versleutel de referentietekenreeks met de openbare sleutel van de gateway. Voor verschillende gatewayversies zijn wellicht verschillende openbare sleutelgrootten beschikbaar.
    
    Raadpleeg het voorbeeld in de SDK-code, die beschikbaar is via de Power BI-CSharp GitHub-opslagplaats, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. Bouw referentiegegevens met versleutelde referenties.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Roep [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Gegevensbron bijwerken) aan om referenties in te stellen.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Een nieuwe gegevensbron configureren voor een gegevensgateway

1. Installeer de [on-premises gegevensgateway](https://powerbi.microsoft.com/gateway/) op uw computer.

2. Roep [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Gateways ophalen) aan om de id en openbare sleutel van de gateway op te halen.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Bouw referentiegegevens zoals in het voorgaande scenario met de openbare sleutel van de gateway die u in de stap [verlopen referentiestroom voor on-premises gegevensbron](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway) hebt opgehaald.

4. de aanvraagtekst bouwen

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

## <a name="troubleshooting"></a>Problemen oplossen

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Er zijn geen gateway en gegevensbron-id gevonden bij het aanroepen van gegevensbronnen ophalen

Dit probleem betekent dat de gegevensset niet is gebonden aan een gateway. Bij het maken van een nieuwe gegevensset, wordt automatisch voor elke cloudverbinding een gegevensbron zonder referenties gemaakt op de cloudgateway van de gebruiker. Deze gateway wordt gebruikt voor het opslaan van de referenties voor cloudverbindingen.

Nadat u de gegevensset hebt gemaakt, wordt een automatische binding uitgevoerd tussen de gegevensset en een geschikte gateway, die overeenkomende gegevensbronnen voor alle verbindingen bevat. Als er geen dergelijke gateway is of meerdere geschikt gateways zijn, mislukt de automatische binding.

Maak ontbrekende on-premises gegevensbronnen indien van toepassing en koppel de gegevensset handmatig aan een gateway met [Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) (Aan gateway verbinden).

Als u gateways wilt detecteren die geschikt zijn voor binding, gebruikt u [Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) (Gateway detecteren).