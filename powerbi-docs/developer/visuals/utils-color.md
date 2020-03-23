---
title: Inleiding tot het gebruik van hulpprogramma's voor kleur in een Power BI-visual
description: In dit artikel wordt beschreven hoe u met hulpprogramma's voor kleur het toepassen van thema's en paletten op gegevenspunten van visuals in Power BI-visuals vereenvoudigt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 8de530871739a18c1afc72cee3e0da5fc70ebb16
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379347"
---
# <a name="color-utils"></a>Kleurhulpmiddelen
Dit artikel helpt u bij het installeren, importeren en gebruiken van hulpprogramma's voor kleur. In dit artikel wordt beschreven hoe u met hulpprogramma's voor kleur het toepassen van thema's en paletten op gegevenspunten van visuals in Power BI-visuals vereenvoudigt.

## <a name="requirements"></a>Vereisten
Als u het pakket wilt gebruiken, moet u beschikken over het volgende:
* [node.js](https://nodejs.org) (de meest recente LTS-versie wordt aanbevolen)
* [npm](https://www.npmjs.com/) (de minimaal ondersteunde versie is 3.0.0)
* De aangepaste visual die is gemaakt met [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installatie

U kunt het pakket installeren door de volgende opdracht uit te voeren in de map met uw huidige visual:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Met deze opdracht wordt het pakket geïnstalleerd en wordt een pakket als een afhankelijkheid toegevoegd aan uw ```package.json```

## <a name="usage"></a>Gebruik

Om de hulpprogramma's voor interactiviteit te gebruiken, moet u het vereiste onderdeel importeren in de broncode van de visual.
```typescript
import { ColorHelper } from "powerbi-visuals-utils-colorutils";
```

Meer informatie over de installatie en het gebruik van de ColorUtils in uw Power BI-visuals:

* [Gebruikshandleiding] In de gebruikshandleiding wordt een openbare API van het pakket beschreven. U vindt een beschrijving en enkele voorbeelden voor elke openbare interface van het pakket.

Dit pakket bevat de volgende klassen en modules:
* [ColorHelper](#colorhelper): helpt bij het genereren van verschillende kleuren voor de grafiekwaarden
* [colorUtils](#colorutils): helpt bij het converteren van kleurindelingen

## `ColorHelper`
De klasse `ColorHelper` biedt de volgende functies en methoden:

### `getColorForSeriesValue` 
Met deze methode wordt de kleur voor de opgegeven reekswaarde opgehaald. Als er geen expliciete kleur of standaardkleur is ingesteld, wordt de kleur van de kleurenschaal voor deze reeks toegewezen.
```typescript
getColorForSeriesValue(objects: IDataViewObjects, value: PrimitiveValue, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Voorbeeld
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;

import DataViewValueColumns = powerbi.DataViewValueColumns;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;

import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const valueColumns: DataViewValueColumns = visualUpdateOptions.dataViews[0].categorical.values,
            grouped: DataViewValueColumnGroup[] = valueColumns.grouped(),
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        for (let i = 0; i < grouped.length; i++) {
            let grouping: DataViewValueColumnGroup = grouped[i];

            let color = colorHelper.getColorForSeriesValue(grouping.objects, grouping.name); // returns a color of the series
        }
    }
}
```

### `getColorForMeasure`
Met deze methode wordt de kleur voor de opgegeven meetwaarde opgehaald.
```typescript
 getColorForMeasure(objects: IDataViewObjects, measureKey: any, themeColorName?: ThemeColorName): string;
```
#### <a name="example"></a>Voorbeeld
```typescript
import powerbi from "powerbi-visuals-api";
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

import DataViewObjects = powerbi.DataViewObjects;
import IVisual = powerbi.extensibility.visual.IVisual;
import IColorPalette = powerbi.extensibility.IColorPalette;
import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions;
import DataViewObjectPropertyIdentifier = powerbi.DataViewObjectPropertyIdentifier;
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class YourVisual implements IVisual {
    // Implementation of IVisual

    private colorPalette: IColorPalette;

    constructor(options: VisualConstructorOptions) {
        this.colorPalette = options.host.colorPalette;
    }

    public update(visualUpdateOptions: VisualUpdateOptions): void {
        const objects: DataViewObjects = visualUpdateOptions.dataViews[0].categorical.categories[0].objects[0],
            defaultDataPointColor: string = "green",
            fillProp: DataViewObjectPropertyIdentifier = {
                objectName: "objectName",
                propertyName: "propertyName"
            };

        let colorHelper: ColorHelper = new ColorHelper(
            this.colorPalette,
            fillProp,
            defaultDataPointColor);

        let color = colorHelper.getColorForMeasure(objects, ""); // returns a color
    }
}
```

### <a name="static-normalizeselector"></a>statisch `normalizeSelector`
Deze methode retourneert de genormaliseerde selector
```typescript
static normalizeSelector(selector: Selector, isSingleSeries?: boolean): Selector;
```
#### <a name="example"></a>Voorbeeld
```typescript
import ISelectionId = powerbi.visuals.ISelectionId;
import { ColorHelper } from "powerbi-visuals-utils-colorutils";

let selectionId: ISelectionId = ...;
let selector = ColorHelper.normalizeSelector(selectionId.getSelector(), false);
```

Methoden `getThemeColor` en `getHighContrastColor` zijn beide gerelateerd aan kleuren van kleurenthema's.
`ColorHelper` heeft ook eigenschap `isHighContrast` die nuttig moet zijn voor controle.

### `getThemeColor`
Deze methode retourneert een themakleur
```typescript
 getThemeColor(themeColorName?: ThemeColorName): string;
```
### `getHighContrastColor`
 Deze methode retourneert een kleur voor de modus Hoog contrast
```typescript
getHighContrastColor(themeColorName?: ThemeColorName, defaultColor?: string): string;
```
#### <a name="example-related-to-high-contrast-mode-usage"></a>Voorbeeld met betrekking tot het gebruik van de modus Hoog contrast:
```typescript

import { ColorHelper } from "powerbi-visuals-utils-colorutils";

export class MyVisual implements IVisual {
        private colorHelper: ColorHelper;

        private init(options: VisualConstructorOptions): void {
            this.colors = options.host.colorPalette;
            this.colorHelper = new ColorHelper(this.colors);
        } 

            private createViewport(element: HTMLElement): void {
                const fontColor: string = "#131aea";
                const axisBackgroundColor: string = this.colorHelper.getThemeColor();
                
                // some d3 code before
                d3ElementName.attr("fill", colorHelper.getHighContrastColor("foreground", fontColor);
            }
                
            public static parseSettings(dataView: DataView, colorHelper: ColorHelper): VisualSettings {
                // some code that should be applied on formatting settings
                if (colorHelper.isHighContrast) {
                        this.settings.fontColor = colorHelper.getHighContrastColor("foreground", this.settings.fontColor);
                    }
            }
}
```


## `ColorUtils`
 De module biedt de volgende functies:

* [hexToRGBString](#hextorgbstring)
* [rotate](#rotate)
* [parseColorString](#parsecolorstring)
* [calculateHighlightColor](#calculatehighlightcolor)
* [createLinearColorScale](#createlinearcolorscale)
* [shadeColor](#shadecolor)
* [rgbBlend](#rgbblend)
* [channelBlend](#channelblend)
* [hexBlend](#hexblend)

### <a name="hextorgbstring"></a>hexToRGBString
De hex-kleur wordt geconverteerd naar een RGB-tekenreeks.

```typescript
function hexToRGBString(hex: string, transparency?: number): string
```

#### <a name="example"></a>Voorbeeld

```typescript
import  { hexToRGBString } from "powerbi-visuals-utils-colorutils";

hexToRGBString('#112233');

// returns: "rgb(17,34,51)"
```

### <a name="rotate"></a>rotate
RGB-kleur wordt gedraaid.

```typescript
function rotate(rgbString: string, rotateFactor: number): string
```

#### <a name="example"></a>Voorbeeld

```typescript
import { rotate } from "powerbi-visuals-utils-colorutils";

rotate("#CC0000", 0.25); // returns: #66CC00
```

### <a name="parsecolorstring"></a>parseColorString
Alle kleurenreeksen worden geparseerd naar een RGB-indeling.

```typescript
function parseColorString(color: string): RgbColor
```

#### <a name="example"></a>Voorbeeld

```typescript
import { parseColorString } from "powerbi-visuals-utils-colorutils";

parseColorString('#09f');
// returns: {R: 0, G: 153, B: 255 }

parseColorString('rgba(1, 2, 3, 1.0)');
// returns: {R: 1, G: 2, B: 3, A: 1.0 }
```

### <a name="calculatehighlightcolor"></a>calculateHighlightColor
De markeerkleur wordt berekend vanuit de rgbColor op basis van de lumianceThreshold en delta.

```typescript
function calculateHighlightColor(rgbColor: RgbColor, lumianceThreshold: number, delta: number): string
```

#### <a name="example"></a>Voorbeeld

```typescript
import { calculateHighlightColor } from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    yellowRGB = parseColorString(yellow);

calculateHighlightColor(yellowRGB, 0.8, 0.2);

// returns: '#CCCC00'
```

### <a name="createlinearcolorscale"></a>createLinearColorScale
Retourneert een lineaire kleurschaal voor het opgegeven domein met getallen.

```typescript
function createLinearColorScale(domain: number[], range: string[], clamp: boolean): LinearColorScale
```

#### <a name="example"></a>Voorbeeld

```typescript
import { createLinearColorScale } from "powerbi-visuals-utils-colorutils";

let scale = ColorUtility.createLinearColorScale(
    [0, 1, 2, 3, 4],
    ["red", "green", "blue", "black", "yellow"],
    true);

scale(1); // returns: green
scale(10); // returns: yellow
```

### <a name="shadecolor"></a>shadeColor
Converteert een hexadecimale tekenreeksexpressie naar een getal, berekent het percentage en de R-, G- en B-kanalen.
Past het percentage voor elk kanaal toe en retourneert een hexadecimale waarde als tekenreeks met een hekje (#).

```typescript
function shadeColor(color: string, percent: number): string
```

#### <a name="example"></a>Voorbeeld

```typescript
import { shadeColor } from "powerbi-visuals-utils-colorutils";

shadeColor('#000000', 0.1); // returns '#1a1a1a'
shadeColor('#FFFFFF', -0.5); // returns '#808080'
shadeColor('#00B8AA', -0.25); // returns '#008a80'
shadeColor('#00B8AA', 0); // returns '#00b8aa'
```

### <a name="rgbblend"></a>rgbBlend
Bedekt een kleur met dekking over een achtergrondkleur. Elk alfakanaal wordt genegeerd.

```typescript
function rgbBlend(foreColor: RgbColor, opacity: number, backColor: RgbColor): RgbColor
```

#### <a name="example"></a>Voorbeeld

```typescript
import { rgbBlend} from "powerbi-visuals-utils-colorutils";

rgbBlend({R: 100, G: 100, B: 100}, 0.5, {R: 200, G: 200, B: 200});

// returns: {R: 150, G: 150, B: 150}
```

### <a name="channelblend"></a>channelBlend
Mengt één kanaal voor twee kleuren.

```typescript
function channelBlend(foreChannel: number, opacity: number, backChannel: number): number
```

#### <a name="example"></a>Voorbeeld

```typescript
import { channelBlend} from "powerbi-visuals-utils-colorutils";

channelBlend(0, 1, 255); // returns: 0
channelBlend(128, 1, 255); // returns: 128
channelBlend(255, 0, 0); // returns: 0
channelBlend(88, 0, 88); // returns: 88
```

### <a name="hexblend"></a>hexBlend
Bedekt een kleur met dekking over een achtergrondkleur.

```typescript
function hexBlend(foreColor: string, opacity: number, backColor: string): string
```

#### <a name="example"></a>Voorbeeld

```typescript
import { hexBlend} from "powerbi-visuals-utils-colorutils";

let yellow = "#FFFF00",
    black = "#000000",
    white = "#FFFFFF";

hexBlend(yellow, 0.5, white); // returns: "#FFFF80"
hexBlend(white, 0.5, yellow); // returns: "#FFFF80"

hexBlend(yellow, 0.5, black); // returns: "#808000"
hexBlend(black, 0.5, yellow); // returns: "#808000"
```