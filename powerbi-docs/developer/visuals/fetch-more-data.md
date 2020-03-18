---
title: Meer gegevens ophalen uit Power BI
description: In dit artikel wordt beschreven hoe u grote gegevenssets voor Power BI-visuals gesegmenteerd kunt ophalen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 6d51a27bc5c0f18b7f784395dedd58813bfffbc0
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380681"
---
# <a name="fetch-more-data-from-power-bi"></a>Meer gegevens ophalen uit Power BI

In dit artikel wordt beschreven hoe u meer gegevens kunt laden om de harde limiet van een gegevenspunt van 30 kB over te slaan. Met deze benadering worden gegevens opgehaald in segmenten. Als u de prestaties wilt verbeteren, kunt u de segmentgrootte afstemmen op uw use-case.  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Gesegmenteerd ophalen van grote gegevenssets mogelijk maken

Voor de `dataview`-segmentmodus definieert u een venstergrootte voor dataReductionAlgorithm in het bestand *capabilities.json* van de visual voor de vereiste dataViewMapping. Het aantal, `count`, bepaalt de grootte van het venster dat het aantal nieuwe gegevensrijen beperkt dat bij elke update aan de `dataview` kan worden toegevoegd.

Voeg de volgende code toe aan het bestand *capabilities.json*:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Nieuwe segmenten worden toegevoegd aan de bestaande `dataview` en aan de visual doorgegeven als een `update`-aanroep.

## <a name="usage-in-the-power-bi-visual"></a>Gebruik in de Power BI-visual

U kunt bepalen of er gegevens bestaan door het bestaan van `dataView.metadata.segment` te controleren:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

U kunt ook controleren of het de eerste update is of een volgende update door `options.operationKind` te controleren. In de volgende code verwijst `VisualDataChangeOperationKind.Create` naar het eerste segment en verwijst `VisualDataChangeOperationKind.Append` naar volgende segmenten.

Zie het volgende codefragment voor een voorbeeldimplementatie:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

U kunt de methode `fetchMoreData` ook aanroepen vanuit een UI-gebeurtenishandler, zoals hier wordt weergegeven:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Als reactie op het aanroepen van de methode `this.host.fetchMoreData` roept Power BI de `update`-methode van de visual aan met een nieuw gegevenssegment.

> [!NOTE]
> Power BI beperkt de totaal opgehaalde gegevens momenteel tot 100 MB om beperkingen van het clientgeheugen te vermijden. U kunt zien dat de limiet is bereikt als fetchMoreData() `false` retourneert.
