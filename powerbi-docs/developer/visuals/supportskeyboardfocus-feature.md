---
title: De functie supportsKeyboardFocus in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u de functie supportsKeyboardFocus gebruikt in Power BI-visuals, alsmede de vereisten voor die functie. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887955"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>De functie supportsKeyboardFocus gebruiken

In dit artikel wordt beschreven hoe u de functie `supportsKeyboardFocus` gebruikt in Power BI-visuals.
Met de functie `supportsKeyboardFocus` wordt alleen navigatie tussen de gegevenspunten van de visual met behulp van het toetsenbord toegestaan.

Zie [Toetsenbordnavigatie](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation) voor meer informatie over toetsenbordnavigatie voor visuals.

## <a name="example"></a>Voorbeeld

Open een visual waarin de functie `supportsKeyboardFocus` wordt gebruikt. Selecteer een willekeurig gegevenspunt in de visual en druk op de tabtoets. Telkens wanneer u op de tabtoets drukt, wordt de focus verplaatst naar het volgende gegevenspunt. Druk op Enter om het geselecteerde gegevenspunt te selecteren.

![Voorbeeld van SupportsKeyboardFocus](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Vereisten

Voor deze functie is API v2.1.0 of hoger vereist.

Deze functie kan worden toegepast op alle visuals, met uitzondering van afbeeldingen.

## <a name="usage"></a>Gebruik

Als u de functie `supportsKeyboardFocus` wilt gebruiken, voegt u de volgende code toe aan het bestand *capabilities.json* van uw visual.
Met deze functie kan de focus naar de visual worden verplaatst via toetsenbordnavigatie.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Volgende stappen

Zie [Power BI-rapporten ontwerpen met het oog op toegankelijkheid](../../create-reports/desktop-accessibility-creating-reports.md) voor meer informatie over toegankelijkheidsfuncties.

Zie [Een aangepaste visual met cirkelkaart voor Power BI ontwikkelen](develop-circle-card.md) als u het ontwikkelen van een visual in Power BI wilt uitproberen.
