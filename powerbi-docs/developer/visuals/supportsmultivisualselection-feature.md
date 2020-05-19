---
title: De functie supportsMultiVisualSelection
description: In dit artikel wordt beschreven hoe u de functie supportsMultiVisualSelection gebruikt in Power BI-visuals, alsmede de vereisten voor die functie.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272690"
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

Zie [Een Power BI-visual ontwikkelen](custom-visual-develop-tutorial.md) als u het ontwikkelen van een visual in Power BI wilt uitproberen.
