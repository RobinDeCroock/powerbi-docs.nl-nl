---
title: Referenties versleutelen
description: 'Rondleiding: Referenties versleutelen voor on-premises gatewaygegevensbronnen'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836604"
---
# <a name="encrypt-credentials"></a>Referenties versleutelen

Als u [Gegevensbron maken](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) of [Gegevensbron bijwerken](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) aanroept onder een **on-premises bedrijfsgateway** met de [REST API van Power BI](https://docs.microsoft.com/rest/api/power-bi/), moet de waarde voor de referenties worden versleuteld met de openbare sleutel van de gateway.

In het codevoorbeeld hieronder ziet u hoe u de referenties in .NET versleutelt.

Referenties die worden opgegeven voor de onderstaande EncodeCredentials-methode, moeten een van de volgende indelingen hebben, afhankelijk van het type referenties:

**Basis-/Windows-referenties**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Sleutelreferenties**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2-referenties**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Anonieme referenties**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Referenties versleutelen**

Versleutel de referentiewaarde met behulp van de openbare sleutel van de gateway. Voor verschillende gatewayversies zijn wellicht verschillende openbare sleutelgrootten beschikbaar.

Raadpleeg het voorbeeld in de SDK-code, die beschikbaar is via de Power BI-CSharp GitHub-opslagplaats, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)