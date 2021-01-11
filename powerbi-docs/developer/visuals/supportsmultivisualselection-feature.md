---
title: De functie supportsMultiVisualSelection in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u de functie supportsMultiVisualSelection gebruikt in Power BI-visuals, alsmede de vereisten voor die functie. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 9e6b17a4576f2354a5cbecc0c3a965a5611784ee
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887932"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>De functie supportsMultiVisualSelection gebruiken

Met de functie `supportsMultiVisualSelection` kunt u selectie in meerdere visuals in een rapport gebruiken.

## <a name="example"></a>Voorbeeld

Selecteer twee waarden in een rapport met meer dan één visual om deze waarden toe te passen op andere visuals. Selecteer bijvoorbeeld in dit [voorbeeld van een retailanalyse](../../create-reports/sample-retail-analysis.md)**Fashions Direct** in één visual. Houd Ctrl ingedrukt en selecteer **Jan** in een andere visual. In het rapport worden uw selecties toegepast op de andere visuals waarin het gebruik van deze functie wordt ondersteund. Het bereik van andere visuals worden nu gefilterd op **Fashions Direct** en **Jan**.

## <a name="requirements"></a>Vereisten

Voor deze functie is API v3.2.0 of hoger vereist.

U kunt deze functie niet toepassen op afbeeldingsvisuals. U kunt deze niet toepassen op sommige geavanceerde visuals, zoals een sleutelstuurprogramma, een ontledingsstructuur, Q&A-visuals, tekstvakken en meterdiagrammen.

## <a name="usage"></a>Gebruik

Als u de functie `supportsMultiVisualSelection` wilt gebruiken, voegt u de volgende code toe aan het bestand `capabilities.json` van uw visual.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Volgende stappen

Zie [Visuals in Power BI](power-bi-visuals-concept.md) voor meer informatie over Power BI-concepten.

Zie [Een aangepaste visual met cirkelkaart voor Power BI ontwikkelen](develop-circle-card.md) als u het ontwikkelen van een visual in Power BI wilt uitproberen.
