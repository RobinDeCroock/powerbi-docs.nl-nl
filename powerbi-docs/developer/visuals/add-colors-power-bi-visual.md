---
title: Kleuren toevoegen aan uw Power BI-visuals
description: In dit artikel wordt beschreven hoe u kleuren kunt toevoegen aan uw Power BI-visuals en hoe u gegevenspunten voor een visual met kleuren kunt afhandelen.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3a68f3dedbef9e97b6c29d3a0923d43872a5f01a
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048804"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Kleuren toevoegen aan uw Power BI-visuals

In dit artikel wordt beschreven hoe u kleuren kunt toevoegen aan uw visuals en hoe u gegevenspunten voor een visual met kleuren kunt afhandelen.

Een van de services die met `IVisualHost` wordt geboden, zijn kleuren.
Met de voorbeeldcode in dit artikel wordt de [visual SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) gewijzigd.
Zie [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) voor de broncode.

Als u zelf visuals wilt gaan maken, raadpleegt u [Een aangepaste visual met cirkelkaart voor Power BI ontwikkelen](develop-circle-card.md).

## <a name="add-color-to-data-points"></a>Kleuren toevoegen aan gegevenspunten

Elk gegevenspunt heeft een eigen kleur.
Voeg de kleur toe aan de interface `BarChartDataPoint`, zoals in het volgende voorbeeld:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>De kleurenpalet-service gebruiken

Met de service `colorPalette` beheert u de kleuren die in uw visual worden gebruikt.
Er is een exemplaar van de service beschikbaar op `IVisualHost`.

Definieer deze in de methode `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Kleuren toewijzen aan gegevenspunten

Geef vervolgens `dataPoints` op.
In dit voorbeeld bevat elk exemplaar van `dataPoints` een waarde, categorie en kleur.
`dataPoints` kan ook andere eigenschappen bevatten.

In `SampleBarChart` wordt de berekening van `dataPoints` ingekapseld in de methode `visualTransform`.
Deze methode maakt deel uit van het weergavemodel van het staafdiagram.
Omdat de methode wordt herhaald in de berekening van `dataPoints` in `visualTransform`, is het de ideale plaats om kleuren toe te wijzen, zoals in de volgende code:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

Pas vervolgens gegevens van `dataPoints` toe op de [d3](https://d3js.org/)-selectie `barSelection` in de methode `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Volgende stappen

Zie [Mogelijkheden en eigenschappen van Power BI-visuals](capabilities.md) voor meer informatie over Power BI-visuals.

Zie [Fouten in Power BI-visuals opsporen](visuals-how-to-debug.md) en [Problemen met Power BI-visuals oplossen](power-bi-custom-visuals-troubleshoot.md) voor meer informatie over het ontwikkelen van Power BI-visuals.
