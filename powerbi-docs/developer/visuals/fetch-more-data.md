---
title: Meer gegevens ophalen
description: Gesegmenteerd ophalen van grote gegevenssets voor Power BI-visuals mogelijk maken
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425063"
---
# <a name="fetch-more-data-from-power-bi"></a>Meer gegevens ophalen uit Power BI

Met de API voor het laden van meer gegevens kunt u de harde limiet van 30.000 gegevenspunten te boven komen. Hiermee worden gegevens opgehaald in chunks. De chunkgrootte is configureerbaar, om de prestaties te verbeteren afhankelijk van de use-case.  

## <a name="enable-segmented-fetch-of-large-datasets"></a>Gesegmenteerd ophalen van grote gegevenssets mogelijk maken

Voor de `dataview`-segmentmodus definieert u een dataReductionAlgorithm 'window' (venster) in de `capabilities.json` van de visual voor de vereiste dataViewMapping.
Het aantal, `count`, bepaalt de grootte van het venster dat het aantal nieuwe gegevensrijen beperkt dat bij elke update aan de `dataview` wordt toegevoegd.

Toe te voegen in capabilities.json

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

## <a name="usage-in-the-custom-visual"></a>Gebruik in de aangepaste visual

Of er gegevens bestaan of niet, kan worden bepaald door het bestaan van `dataView.metadata.segment` te controleren:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

Het is ook mogelijk om te controleren of dit de eerste of een latere update is door `options.operationKind`te controleren.

`VisualDataChangeOperationKind.Create` betekent het eerste segment, en `VisualDataChangeOperationKind.Append` betekent latere segmenten.

Zie het onderstaande codefragment voor een voorbeeldimplementatie:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

De `fetchMoreData`-methode kan ook worden aangeroepen vanuit een UI-gebeurtenis-handler

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI roept de `update`-methode van de visual aan met een nieuw gegevenssegment als antwoord op de aanroep van de methode `this.host.fetchMoreData`.

> [!NOTE]
> Power BI beperkt de totaal opgehaalde gegevens momenteel tot **100 MB** om beperkingen van het clientgeheugen te vermijden. U kunt detecteren dat deze limiet is bereikt wanneer fetchMoreData() 'false' retourneert.*
