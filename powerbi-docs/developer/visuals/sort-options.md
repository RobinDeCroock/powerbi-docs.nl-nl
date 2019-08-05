---
title: Sorteren
description: Standaardsorteergedrag voor de Power BI-visual.
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f3d913e2bce34850dfae4c9486b2e43c78521a58
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424511"
---
# <a name="sorting-options"></a>Sorteeropties

`Sorting` geeft het standaardsorteergedrag voor de visual op.
Deze mogelijkheid vereist een van de hieronder beschreven parameters:

## <a name="default-sorting"></a>Standaardsortering

De `default`-optie is de eenvoudigste vorm. Hiermee kunnen de gegevens die worden gepresenteerd in de sectie 'DataMappings' worden gesorteerd.
Met deze optie kan de gebruiker de 'DataMappings' sorteren en de sorteerrichting opgeven.

```json
    "sorting": {
        "default": {   }
    }
```

![Sorteeropties in contextmenu](./media/sorting.png)

## <a name="implicit-sorting"></a>Impliciete sortering

`implicit` is sorteren met de matrixparameter `clauses`, waarmee de sortering voor elke gegevensrol wordt beschreven.
`implicit` betekent dat de gebruiker van de visual de sorteervolgorde niet kan wijzigen.
Power BI geeft geen sorteeropties weer in het menu van de visual. Maar Power BI sorteert de gegevens wel volgens de opgegeven instellingen.

`clauses`-parameters kunnen verschillende objecten bevatten met twee parameters:

- `role`: bepaalt `DataMapping` voor sorteren.

- `direction`: bepaalt de sorteerrichting (1 = oplopend, 2 = aflopend).

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

`custom` betekent dat de sortering wordt beheerd door de ontwikkelaar in de code van de visual.
