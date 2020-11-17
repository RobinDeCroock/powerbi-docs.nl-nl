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
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483691"
---
# <a name="fetch-more-data-from-power-bi"></a>Meer gegevens ophalen uit Power BI

In dit artikel wordt beschreven hoe u meer gegevens kunt laden om de harde limiet van een gegevenspunt van 30 kB over te slaan met behulp van de methode `fetchMoreData`. Met deze benadering worden gegevens opgehaald in segmenten. Als u de prestaties wilt verbeteren, kunt u de segmentgrootte afstemmen op uw use-case.

## <a name="limitations-of-fetchmoredata"></a>Beperkingen van fetchMoreData

* De venstergrootte is beperkt tot een bereik van 2 tot en met 30.000.
* Totaal aantal rijen in DataView is beperkt tot 1.048.576 rijen.
* In de aggregatiemodus voor segmenten is de geheugengrootte van DataView beperkt tot 100 MB.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Gesegmenteerd ophalen van grote gegevenssets mogelijk maken

Voor de `dataview`-segmentmodus definieert u een venstergrootte voor `dataReductionAlgorithm` in het bestand *capabilities.json* van de visual voor de vereiste `dataViewMapping`. Het aantal, `count`, bepaalt de grootte van het venster dat het aantal nieuwe gegevensrijen beperkt dat bij elke update aan de `dataview` kan worden toegevoegd.

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

In Power BI kunt u `fetchMoreData` gebruiken in de standaardaggregatiemodus voor segmenten of in de modus Incrementele updates. 

### <a name="using-segments-aggregation-mode-default"></a>De aggregatiemodus voor segmenten gebruiken (standaard)

In deze modus bevat de aan de visual opgegeven DataView de gecumuleerde gegevens van alle vorige `fetchMoreData requests`. Daarom wordt de grootte van de DataView naar verwachting met elke update uitgebreid. Als er bijvoorbeeld een totaal van 100.000 rijen wordt verwacht en de venstergrootte op 10.000 is ingesteld, moet DataView van de eerste update 10.000 rijen bevatten, DataView van de tweede over 20.000 rijen beschikken, enzovoort.

Deze modus wordt geselecteerd door `fetchMoreData` met `aggregateSegments = true` aan te roepen.

U kunt bepalen of er gegevens zijn door op de aanwezigheid van `dataView.metadata.segment` te controleren:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

U kunt ook nagaan of het de eerste update is of een volgende update door `options.operationKind` te controleren. In de volgende code verwijst `VisualDataChangeOperationKind.Create` naar het eerste segment en verwijst `VisualDataChangeOperationKind.Append` naar volgende segmenten.

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
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Als reactie op het aanroepen van de methode `this.host.fetchMoreData` roept Power BI de `update`-methode van de visual aan met een nieuw gegevenssegment.

> [!NOTE]
> Power BI beperkt de totaal opgehaalde gegevens momenteel tot 100 MB om beperkingen van het clientgeheugen te vermijden. U kunt zien dat de limiet is bereikt als door `fetchMoreData()` `false` wordt geretourneerd.

### <a name="using-incremental-updates-mode"></a>Incrementele updates gebruiken

In deze modus bevat de aan de visual opgegeven DataView alleen incrementele gegevens. Daarom overtreft de grootte van DataView niet de gedefinieerde venstergrootte. Als er bijvoorbeeld een totaal van 101.000 rijen wordt verwacht en de venstergrootte is ingesteld op 10.000, krijgt de visual 10 updates met een DataView-grootte van 10.000 en één update met een DataView-grootte van 1000.

Deze modus wordt geselecteerd door `fetchMoreData` met `aggregateSegments = false` aan te roepen.

U kunt bepalen of er gegevens zijn door op de aanwezigheid van `dataView.metadata.segment` te controleren:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

U kunt ook nagaan of het de eerste update is of een volgende update door `options.operationKind` te controleren. In de volgende code verwijst `VisualDataChangeOperationKind.Create` naar het eerste segment en verwijst `VisualDataChangeOperationKind.Segment` naar volgende segmenten.

Zie het volgende codefragment voor een voorbeeldimplementatie:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
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
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Als reactie op het aanroepen van de methode `this.host.fetchMoreData` roept Power BI de `update`-methode van de visual aan met een nieuw gegevenssegment.

> [!NOTE]
> Hoewel de gegevens van DataViews tussen de verschillende updates voornamelijk exclusief zijn, is er toch sprake van enige overlapping tussen opeenvolgende DataViews.
> Voor de gegevenstoewijzing van tabellen en categorieën zullen naar verwachting de eerste N DataView-rijen gegevens bevatten die zijn gekopieerd uit de vorige DataView.
> N kan worden bepaald door: `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`