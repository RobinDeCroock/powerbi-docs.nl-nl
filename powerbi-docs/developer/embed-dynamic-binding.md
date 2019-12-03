---
title: Een rapport verbinden met een gegevensset met behulp van dynamische binding
description: Informatie over het insluiten van een rapport met behulp van dynamische binding.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: f797dd55202ff4cba87cc3a15601d85091e94823
ms.sourcegitcommit: c839ef7437bc8fb8f7eeda23e59d05c7192a7fe8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164056"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Een rapport verbinden met een gegevensset met behulp van dynamische binding 

Wanneer een rapport is verbonden met een gegevensset, kunt u dynamische binding gebruiken. De verbinding tussen het rapport en de gegevensset wordt *binding* genoemd. Wanneer de binding wordt vastgesteld op het moment van insluiten, in plaats van eerder te worden bepaald, wordt de binding ook wel [dynamische binding](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLate_binding&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C5d5b0d2d62cf4818f0c108d7635b151e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637087115150775585&sdata=AbEtdJvgy4ivi4v4ziuui%2Bw2ibTQQXBQNYRKbXn5scA%3D&reserved=0) genoemd.
 
Wanneer u een Power BI-rapport met *dynamische binding* insluit, kunt u hetzelfde rapport verbinden met verschillende gegevenssets, afhankelijk van de referenties van de gebruiker.
 
Dit betekent dat u één rapport kunt gebruiken om verschillende gegevens weer te geven, afhankelijk van de gegevensset waarmee deze is verbonden. Een rapport dat bijvoorbeeld de verkoopwaarden van de detailhandel weergeeft, kan worden verbonden met verschillende gegevenssets van wederverkopers, en kan andere resultaten opleveren, afhankelijk van de gegevensset van de wederverkoper waarmee deze is verbonden.
 
Het rapport en de gegevensset hoeven zich niet in dezelfde werkruimte te bevinden. Beide werkruimten (één met het rapport en één met de gegevensset) moeten worden toegewezen aan een [capaciteit](azure-pbie-create-capacity.md).

Zorg er als onderdeel van het insluitingsproces voor dat u *een token met voldoende machtigingen genereert* en *het configuratie-object aanpast*.


## <a name="generating-a-token-with-sufficient-permissions"></a>Een token met voldoende machtigingen genereren

Dynamische binding wordt ondersteund voor de scenario's *Inhoud insluiten voor uw organisatie* en *Inhoud insluiten voor uw klanten*. In de volgende tabel worden de overwegingen voor elk scenario beschreven.


|Scenario  |Eigendom van gegevens  |Token  |Vereisten  |
|---------|---------|---------|---------|
|*Inhoud insluiten voor uw organisatie*    |Gebruiker is eigenaar van gegevens         |Toegangstoken voor Power BI-gebruikers         |De gebruiker van wie het Azure AD-token wordt gebruikt, moet over de juiste machtigingen voor alle artefacten beschikken.         |
|*Inhoud insluiten voor uw klanten*     |App is eigenaar van gegevens         |Toegangstoken voor niet-Power BI-gebruikers         |Moet machtigingen voor zowel het rapport als de dynamisch gebonden gegevensset bevatten. Gebruik de [-API voor het genereren van een insluittoken voor meerdere items](embed-sample-for-customers.md#multiEmbedToken) om een insluittoken te genereren dat meerdere artefacten ondersteunt.         |

## <a name="adjusting-the-config-object"></a>Het configuratieobject aanpassen
Voeg `datasetBinding` toe aan het configuratieobject. Gebruik het voorbeeld hieronder als referentie.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Volgende stappen

Als u voor het eerst inhoud in Power BI gaat insluiten, leest u eerst deze zelfstudies voor informatie over het insluiten van uw Power BI-inhoud:
* [Zelfstudie: Power BI-inhoud insluiten in een toepassing voor uw klanten](embed-sample-for-customers.md)
* [Zelfstudie: Power BI-inhoud insluiten in een toepassing voor uw organisatie](embed-sample-for-your-organization.md)