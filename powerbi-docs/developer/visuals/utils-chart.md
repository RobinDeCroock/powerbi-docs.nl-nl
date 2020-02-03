---
title: Inleiding tot het gebruik van grafiekhulpmiddelen in een Power BI-visual
description: In dit artikel wordt beschreven hoe u grafiekhulpmiddelen kunt gebruiken om assen en legenda's te tekenen in een Power BI-visual
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: e87235232860897765ef95bf0ec865410adf8fd1
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819486"
---
# <a name="chart-utils"></a>Grafiekhulpmiddelen

ChartUtils is een set interfaces en methoden voor het maken van assen, gegevenslabels en legenda's in Power BI-visuals.

## <a name="installation"></a>Installatie

U kunt het pakket installeren door de volgende opdracht uit te voeren in de map met uw huidige visual:

```bash
npm install powerbi-visuals-utils-chartutils --save
```

## <a name="axis-helper"></a>As-helper

De as-helper (het object `axis` in de hulpmiddelen) biedt functies om bewerkingen met assen te vereenvoudigen.

De module biedt de volgende functies:

### <a name="getrecommendednumberofticksforxaxis"></a>getRecommendedNumberOfTicksForXAxis

Met deze functie wordt het aanbevolen aantal maatstreepjes geretourneerd op basis van de breedte van de grafiek.

```typescript
function getRecommendedNumberOfTicksForXAxis(availableWidth: number): number;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForXAxis(1024);

// returns: 8
```

### <a name="getrecommendednumberofticksforyaxis"></a>getRecommendedNumberOfTicksForYAxis

Met deze functie wordt het aanbevolen aantal maatstreepjes geretourneerd op basis van de hoogte van de grafiek.

```typescript
function getRecommendedNumberOfTicksForYAxis(availableWidth: number);
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
axis.getRecommendedNumberOfTicksForYAxis(100);

// returns: 3
```

### <a name="getbestnumberofticks"></a>getBestNumberOfTicks

Hiermee wordt het optimale aantal maatstreepjes opgehaald op basis van minimumwaarde, maximumwaarde, metagegevens van de meting en maximumaantal maatstreepjes;

```typescript
function getBestNumberOfTicks(
  min: number,
  max: number,
  valuesMetadata: DataViewMetadataColumn[],
  maxTickCount: number,
  isDateTime?: boolean
): number;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
var dataViewMetadataColumnWithIntegersOnly: powerbi.DataViewMetadataColumn[] = [
  {
    displayName: "col1",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  },
  {
    displayName: "col2",
    isMeasure: true,
    type: ValueType.fromDescriptor({ integer: true })
  }
];
var actual = axis.getBestNumberOfTicks(
  0,
  3,
  dataViewMetadataColumnWithIntegersOnly,
  6
);

// returns: 4
```

### <a name="getticklabelmargins"></a>getTickLabelMargins

Met deze functie worden de marges voor maatstreeplabels geretourneerd.

```typescript
function getTickLabelMargins(
  viewport: IViewport,
  yMarginLimit: number,
  textWidthMeasurer: ITextAsSVGMeasurer,
  textHeightMeasurer: ITextAsSVGMeasurer,
  axes: CartesianAxisProperties,
  bottomMarginLimit: number,
  properties: TextProperties,
  scrollbarVisible?: boolean,
  showOnRight?: boolean,
  renderXAxis?: boolean,
  renderY1Axis?: boolean,
  renderY2Axis?: boolean
): TickLabelMargins;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.getTickLabelMargins(
  plotArea,
  marginLimits.left,
  TextMeasurementService.measureSvgTextWidth,
  TextMeasurementService.estimateSvgTextHeight,
  axes,
  marginLimits.bottom,
  textProperties,
  /*scrolling*/ false,
  showY1OnRight,
  renderXAxis,
  renderY1Axis,
  renderY2Axis
);

// returns:  xMax, yLeft, yRight, stackHeigh;
```

### <a name="isordinal"></a>isOrdinal

Hiermee wordt gecontroleerd of een tekenreeks null, niet gedefinieerd of leeg is.

```typescript
function isOrdinal(type: ValueTypeDescriptor): boolean;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...
let type = ValueType.fromDescriptor({ misc: { barcode: true } });
axis.isOrdinal(type);

// returns: true
```

### <a name="isdatetime"></a>isDateTime

Controleert of een waarde van het type datum/tijd is.

```typescript
function isDateTime(type: ValueTypeDescriptor): boolean;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.isDateTime(ValueType.fromDescriptor({ dateTime: true }));

// returns: true
```

### <a name="getcategorythickness"></a>getCategoryThickness

Maakt gebruik van de D3-schaal om de huidige categoriedikte te verkrijgen.

```typescript
function getCategoryThickness(scale: any): number;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let range = [0, 100];
let domain = [0, 10];
let scale = d3.scale
  .linear()
  .domain(domain)
  .range(range);
let actualThickness = axis.getCategoryThickness(scale);
```

### <a name="invertordinalscale"></a>invertOrdinalScale

Met deze functie wordt de rangtelwoordschaal omgekeerd. Als x < scale.range()[0] wordt scale.domain()[0] geretourneerd.
Anders wordt het grootste item in scale.domain() dat <= x geretourneerd.

```typescript
function invertOrdinalScale(scale: d3.scale.Ordinal<any, any>, x: number);
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let domain: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
  pixelSpan: number = 100,
  ordinalScale: d3.scale.ordinal = axis.createOrdinalScale(
    pixelSpan,
    domain,
    0.4
  );

axis.invertOrdinalScale(ordinalScale, 49);

// returns: 4
```

### <a name="findclosestxaxisindex"></a>findClosestXAxisIndex

Met deze functie wordt de dichtstbijzijnde x-asindex gezocht en geretourneerd.

```typescript
function findClosestXAxisIndex(
  categoryValue: number,
  categoryAxisValues: AxisHelperCategoryDataPoint[]
): number;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

/**
 * Finds the index of the category of the given x coordinate given.
 * pointX is in non-scaled screen-space, and offsetX is in render-space.
 * offsetX does not need any scaling adjustment.
 * @param {number} pointX The mouse coordinate in screen-space, without scaling applied
 * @param {number} offsetX Any left offset in d3.scale render-space
 * @return {number}
 */
private findIndex(pointX: number, offsetX?: number): number {
    // we are using mouse coordinates that do not know about any potential CSS transform scale
    let xScale = this.scaleDetector.getScale().x;
    if (!Double.equalWithPrecision(xScale, 1.0, 0.00001)) {
        pointX = pointX / xScale;
    }
    if (offsetX) {
        pointX += offsetX;
    }

    let index = axis.invertScale(this.xAxisProperties.scale, pointX);
    if (this.data.isScalar) {
        // When we have scalar data the inverted scale produces a category value, so we need to search for the closest index.
        index = axis.findClosestXAxisIndex(index, this.data.categoryData);
    }

    return index;
}
```

### <a name="diffscaled"></a>diffScaled

Met deze functie wordt een verschil van waarden in de schaal berekend en geretourneerd.

```typescript
function diffScaled(
  scale: d3.scale.Linear<any, any>,
  value1: any,
  value2: any
): number;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var scale: d3.scale.Linear<number, number>,
    range = [0, 999],
    domain = [0, 1, 2, 3, 4, 5, 6, 7, 8, 999];

scale = d3.scale.linear()
    .range(range)
    .domain(domain);

return axis.diffScaled(scale, 0, 0));

// returns: 0
```

### <a name="createdomain"></a>createDomain

Met deze functie wordt een domein met aswaarden gemaakt.

```typescript
function createDomain(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

var domain = axis.createDomain(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="getcategoryvaluetype"></a>getCategoryValueType

Met deze functie wordt het `ValueType` van een categoriekolom opgehaald. De standaard is `Text` als het type niet aanwezig is.

```typescript
function getCategoryValueType(
  data: any[],
  axisType: ValueTypeDescriptor,
  isScalar: boolean,
  forcedScalarDomain: any[],
  ensureDomain?: NumberRange
): number[];
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

var cartesianSeries = [
  {
    data: [
      { categoryValue: 7, value: 11, categoryIndex: 0, seriesIndex: 0 },
      {
        categoryValue: 9,
        value: 9,
        categoryIndex: 1,
        seriesIndex: 0
      },
      {
        categoryValue: 15,
        value: 6,
        categoryIndex: 2,
        seriesIndex: 0
      },
      { categoryValue: 22, value: 7, categoryIndex: 3, seriesIndex: 0 }
    ]
  }
];

axis.getCategoryValueType(
  cartesianSeries,
  ValueType.fromDescriptor({ text: true }),
  false,
  []
);

// returns: [0, 1, 2, 3]
```

### <a name="createaxis"></a>createAxis

Met deze functie wordt een D3-as met schaal gemaakt. Deze kan verticaal of horizontaal zijn en datum/tijd, numeriek of tekst zijn.

```typescript
function createAxis(options: CreateAxisOptions): IAxisProperties;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
import { valueFormatter } from "powerbi-visuals-utils-formattingutils";
// ...

var dataPercent = [0.0, 0.33, 0.49];

var formatStringProp: powerbi.DataViewObjectPropertyIdentifier = {
  objectName: "general",
  propertyName: "formatString"
};
let metaDataColumnPercent: powerbi.DataViewMetadataColumn = {
  displayName: "Column",
  type: ValueType.fromDescriptor({ numeric: true }),
  objects: {
    general: {
      formatString: "0 %"
    }
  }
};

var os = axis.createAxis({
  pixelSpan: 100,
  dataDomain: [dataPercent[0], dataPercent[2]],
  metaDataColumn: metaDataColumnPercent,
  formatString: valueFormatter.getFormatString(
    metaDataColumnPercent,
    formatStringProp
  ),
  outerPadding: 0.5,
  isScalar: true,
  isVertical: true
});
```

### <a name="applycustomizeddomain"></a>applyCustomizedDomain

Met deze functie wordt een aangepast domein ingesteld, maar wordt niets gewijzigd wanneer er niets is ingesteld.

```typescript
function applyCustomizedDomain(customizedDomain, forcedDomain: any[]): any[];
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let customizedDomain = [undefined, 20],
  existingDomain = [0, 10];

axis.applyCustomizedDomain(customizedDomain, existingDomain);

// returns: {0:0, 1:20}
```

### <a name="combinedomain"></a>combineDomain

Met deze functie wordt het geforceerde domein gecombineerd met het huidige domein als een van de waarden is ingesteld.
Het forcedDomain heeft de hoogste prioriteit. Het domein wordt uitgebreid als dat vereist is voor een referentiepunt.

```typescript
function combineDomain(
  forcedDomain: any[],
  domain: any[],
  ensureDomain?: NumberRange
): any[];
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

let forcedYDomain = this.valueAxisProperties
  ? [this.valueAxisProperties["secStart"], this.valueAxisProperties["secEnd"]]
  : null;

let xDomain = [minX, maxX];

axis.combineDomain(forcedYDomain, xDomain, ensureXDomain);
```

### <a name="poweroften"></a>powerOfTen

Deze functie geeft aan of het getal tot de macht 10 is.

```typescript
function powerOfTen(d: any): boolean;
```

Voorbeeld:

```typescript
import { axis } from "powerbi-visuals-utils-chartutils";
// ...

axis.powerOfTen(10);

// returns: true
```

## <a name="datalabelmanager"></a>DataLabelManager

`DataLabelManager` helpt bij het maken en onderhouden van labels. Labelelementen worden geschikt met behulp van het ankerpunt of de rechthoek. Conflicten kunnen automatisch worden gedetecteerd om elementen te verplaatsen of te verbergen.

De klasse `DataLabelManager` biedt de volgende methoden:

## <a name="hidecollidedlabels"></a>hideCollidedLabels

Met deze methode worden de positie en zichtbaarheid van labels op het canvas geschikt op basis van labelgrootte en overlapping.

```typescript
function hideCollidedLabels(
  viewport: IViewport,
  data: any[],
  layout: any,
  addTransform: boolean = false
): LabelEnabledDataPoint[];
```

Voorbeeld:

```typescript
let dataLabelManager = new DataLabelManager();
let filteredData = dataLabelManager.hideCollidedLabels(
  this.viewport,
  values,
  labelLayout,
  true
);
```

## <a name="isvalid"></a>IsValid

Met deze statische methode wordt gecontroleerd of een opgegeven rechthoek geldig is (een positieve breedte en hoogte heeft).

```typescript
function isValid(rect: IRect): boolean;
```

Voorbeeld:

```typescript
let rectangle = {
  left: 150,
  top: 130,
  width: 120,
  height: 110
};

DataLabelManager.isValid(rectangle);

// returns: true
```

## <a name="datalabelutils"></a>DataLabelUtils

`DataLabelUtils` biedt hulpprogramma's om gegevenslabels te bewerken.

De module biedt de volgende functies, interfaces en klassen:

### <a name="getlabelprecision"></a>getLabelPrecision

Met deze functie wordt de precisie berekend op basis van de opgegeven opmaak.

```typescript
function getLabelPrecision(precision: number, format: string): number;
```

### <a name="getlabelformattedtext"></a>getLabelFormattedText

Met deze functie wordt de opmaakprecisie geretourneerd op basis van de opgegeven opmaak.

```typescript
function getLabelFormattedText(options: LabelFormattedTextOptions): string;
```

Voorbeeld:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let options: LabelFormattedTextOptions = {
  text: "some text",
  fontFamily: "sans",
  fontSize: "15",
  fontWeight: "normal"
};

dataLabelUtils.getLabelFormattedText(options);
```

### <a name="enumeratedatalabels"></a>enumerateDataLabels

Met deze functie wordt VisualObjectInstance voor gegevenslabels geretourneerd.

```typescript
function enumerateDataLabels(
  options: VisualDataLabelsSettingsOptions
): VisualObjectInstance;
```

### <a name="enumeratecategorylabels"></a>enumerateCategoryLabels

Met deze functie wordt VisualObjectInstance voor categoriegegevenslabels toegevoegd aan een opsommingsobject.

```typescript
function enumerateCategoryLabels(
  enumeration: VisualObjectInstanceEnumerationObject,
  dataLabelsSettings: VisualDataLabelsSettings,
  withFill: boolean,
  isShowCategory: boolean = false,
  fontSize?: number
): void;
```

### <a name="createcolumnformattercachemanager"></a>createColumnFormatterCacheManager

Met deze functie wordt Cachebeheer geretourneerd voor snelle toegang tot opgemaakte labels

```typescript
function createColumnFormatterCacheManager(): IColumnFormatterCacheManager;
```

Voorbeeld:

```typescript
import { dataLabelUtils } from "powerbi-visuals-utils-chartutils";
// ...

let value: number = 200000;

labelSettings.displayUnits = 1000000;
labelSettings.precision = 1;

let formattersCache = DataLabelUtils.createColumnFormatterCacheManager();
let formatter = formattersCache.getOrCreate(null, labelSettings);
let formattedValue = formatter.format(value);

// formattedValue == "0.2M"
```

## <a name="legend-service"></a>Legendaservice

De service `Legend` biedt helper-interfaces voor het maken en beheren van PBI-legenda's voor aangepaste visuals

De module biedt de volgende functies en interfaces:

### <a name="createlegend"></a>createLegend

Met deze helper-functie wordt het maken van legenda's voor aangepaste Power BI-visuals vereenvoudigd.

```typescript
function createLegend(
  legendParentElement: HTMLElement, // top visual element, container in which legend will be created
  interactive: boolean, // indicates that legend should be interactive
  interactivityService: IInteractivityService, // reference to IInteractivityService interface which need to create legend click events
  isScrollable: boolean = false, // indicates that legend could be scrollable or not
  legendPosition: LegendPosition = LegendPosition.Top // Position of the legend inside of legendParentElement container
): ILegend;
```

Voorbeeld:

```typescript
public constructor(options: VisualConstructorOptions) {
    this.visualInitOptions = options;
    this.layers = [];

    var element = this.element = options.element;
    var viewport = this.currentViewport = options.viewport;
    var hostServices = options.host;

    //... some other init calls

    if (this.behavior) {
        this.interactivityService = createInteractivityService(hostServices);
    }
    this.legend = createLegend(
        element,
        options.interactivity && options.interactivity.isInteractiveLegend,
        this.interactivityService,
        true);
}
```

### <a name="ilegend"></a>ILegend

Met deze interface worden alle methoden geïmplementeerd die nodig zijn om een legenda te maken

```typescript
export interface ILegend {
  getMargins(): IViewport;
  isVisible(): boolean;
  changeOrientation(orientation: LegendPosition): void; // processing legend orientation
  getOrientation(): LegendPosition; // get information about current legend orientation
  drawLegend(data: LegendData, viewport: IViewport); // all legend rendering code is placing here
  /**
   * Reset the legend by clearing it
   */
  reset(): void;
}
```

### <a name="drawlegend"></a>drawLegend

Met deze functie wordt de hoogte van de tekst met de opgegeven SVG-teksteigenschappen gemeten.

```typescript
function drawLegend(data: LegendData, viewport: IViewport): void;
```

Voorbeeld:

```typescript
private renderLegend(): void {
    if (!this.isInteractive) {
        let legendObjectProperties = this.data.legendObjectProperties;
        if (legendObjectProperties) {
            let legendData = this.data.legendData;
            LegendData.update(legendData, legendObjectProperties);
            let position = <string>legendObjectProperties[legendProps.position];
            if (position)
                this.legend.changeOrientation(LegendPosition[position]);

            this.legend.drawLegend(legendData, this.parentViewport);
        } else {
            this.legend.changeOrientation(LegendPosition.Top);
            this.legend.drawLegend({ dataPoints: [] }, this.parentViewport);
        }
    }
}
```

## <a name="next-steps"></a>Volgende stappen

- [Lees hoe u InteractivityUtils kunt gebruiken om selecties aan Power BI-visuals toe te voegen](utils-interactivity-selections.md)
