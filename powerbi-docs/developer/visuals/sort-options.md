---
title: Sorteeropties voor Power BI-visuals
description: In dit artikel wordt het standaardsorteergedrag voor Power BI-visuals beschreven.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 3cb8f5af63960667dc46cab1d818ba48943fd582
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378064"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Sorteeropties voor Power BI-visuals

In dit artikel wordt beschreven hoe u met opties voor *sorteren* het sorteergedrag voor Power BI-visuals opgeeft. 

Voor de sorteerfunctie is een van de volgende parameters vereist.

## <a name="default-sorting"></a>Standaardsortering

De `default`-optie is de eenvoudigste vorm. Hiermee kunnen de gegevens die worden gepresenteerd in de sectie 'DataMappings' worden gesorteerd. Met deze optie kan de gebruiker de gegevenstoewijzingen sorteren en de sorteerrichting opgeven.

```json
    "sorting": {
        "default": {   }
    }
```

![Sorteeropties in contextmenu](media/sort-options/sorting.png)

## <a name="implicit-sorting"></a>Impliciete sortering

Impliciet sorteren is sorteren met de matrixparameter `clauses`, waarmee de sortering voor elke gegevensrol wordt beschreven. `implicit` betekent dat de gebruiker van de visual de sorteervolgorde niet kan wijzigen. In Power BI worden geen sorteeropties weergegeven in het menu van de visual. In Power BI worden de gegevens echter wel gesorteerd volgens de opgegeven instellingen.

`clauses`-parameters kunnen verschillende objecten bevatten met twee parameters:

- `role`: bepaalt `DataMapping` voor sorteren
- `direction`: bepaalt de sorteerrichting (1 = oplopend, 2 = aflopend)

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Aangepaste sortering

Met aangepaste sortering wordt de sortering beheerd door de ontwikkelaar, in de code van de visual.
