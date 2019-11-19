---
title: Dynamische binding
description: Informatie over insluiten van een rapport met behulp van dynamische binding.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776232"
---
# <a name="dynamic-binding"></a>Dynamische binding

Dynamische bindingen kunnen worden gebruikt voor het dynamisch selecteren van een gegevensset tijdens het insluiten van een rapport. Het rapport en de gegevensset hoeven zich niet in dezelfde werkruimte te bevinden. Eindgebruikers zien verschillende resultaten, afhankelijk van de geselecteerde gegevensset.

Beide werkruimten (één met het rapport en één met de gegevensset) moeten worden toegewezen aan een capaciteit.

Het insluiten van een rapport met behulp van dynamische binding bestaat uit twee fasen:
1. Een token genereren
2. Het configuratieobject aanpassen

## <a name="generating-a-token"></a>Een token genereren
Als u een token wilt genereren, gebruikt u de [API voor het genereren van een insluitingstoken voor meerdere items](embed-sample-for-customers.md#multiEmbedToken).

Dynamische binding wordt ondersteund voor beide insluitingsscenario's, *Inhoud insluiten voor uw organisatie* en *Inhoud insluiten voor uw klanten*.

| Oplossing                   | Token                               | Vereisten                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Inhoud insluiten voor uw organisatie* | Toegangstoken voor Power BI-gebruikers     | De gebruiker van wie het Azure AD-token wordt gebruikt, moet over de juiste machtigingen voor alle artefacten beschikken.                                                                    |
| *Inhoud insluiten voor uw klanten*    | Toegangstoken voor niet-Power BI-gebruikers | Moet machtigingen voor zowel het rapport als de dynamisch gebonden gegevensset bevatten. Gebruik de nieuwe API om een insluitingstoken te genereren die ondersteuning voor meerdere artefacten biedt. |

## <a name="adjusting-the-config-object"></a>Het configuratieobject aanpassen
Voeg `datasetBinding` toe aan het configuratieobject. Gebruik het voorbeeld onderaan de pagina als referentie.

Als u voor het eerst inhoud in Power BI gaat insluiten, leest u eerst deze zelfstudies voor informatie over het insluiten van uw Power BI-inhoud:
* [Power BI-inhoud insluiten in een toepassing voor uw klanten](embed-sample-for-customers.md)
* [Zelfstudie: Power BI-inhoud insluiten in een toepassing voor uw organisatie](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Voorbeeld
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```