---
title: Inleiding tot het gebruik van SVG-hulpmiddelen in een Power BI-visual
description: In dit artikel wordt beschreven hoe u SVG-hulpmiddelen gebruikt om SVG-bewerkingen te vereenvoudigen voor aangepaste Power BI-visuals
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 612c253e53cdaec5819387548354595c8bd94fa0
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819302"
---
# <a name="svg-utils"></a>SVG-hulpmiddelen

SVGUtils is een reeks functies en klassen waarmee u SVG-bewerkingen voor aangepaste Power BI-visuals kunt vereenvoudigen

## <a name="installation"></a>Installatie

U kunt het pakket installeren door de volgende opdracht uit te voeren in de map met uw huidige visual:

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

De module `CssConstants` bevat de speciale functie en interface voor het werken met klasseselectors.

De module `powerbi.extensibility.utils.svg.CssConstants` bevat de volgende functie en interface:

## <a name="classandselector"></a>ClassAndSelector

Deze interface geeft een beschrijving van de algemene eigenschappen van de klasseselector.

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

Met deze functie wordt een instantie van ClassAndSelector met de opgegeven naam van de klasse gemaakt.

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

Voorbeeld:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

De `manipulation` bevat enkele speciale functies voor het genereren van tekenreeksen die kunnen worden gebruikt met de SVG-eigenschap transform.

De module biedt de volgende functies:

### <a name="translate"></a>translate

Met deze functie wordt een translate-tekenreeks gemaakt die kan worden gebruikt met de SVG-eigenschap transform.

```typescript
function translate(x: number, y: number): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

Met deze functie wordt een translateX-tekenreeks gemaakt die kan worden gebruikt met de SVG-eigenschap transform.

```typescript
function translateXWithPixels(x: number): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

Met deze functie wordt een translate-tekenreeks gemaakt die kan worden gebruikt met de SVG-eigenschap transform.

```typescript
function translateWithPixels(x: number, y: number): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

Met deze functie wordt een translate-rotate-tekenreeks gemaakt die kan worden gebruikt met de SVG-eigenschap transform.

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

Met deze functie wordt een scale-tekenreeks gemaakt die kan worden gebruikt in de CSS-eigenschap transform.

```typescript
function scale(scale: number): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

Met deze functie wordt een transform-origin-tekenreeks gemaakt die kan worden gebruikt in de CSS-eigenschap transform-origin.

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

Met deze functie wordt de voltooiing van elke D3-overgang afgedwongen.

```typescript
function flushAllD3Transitions(): void;
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

Met deze functie wordt de transform-tekenreeks geparseerd met de waarde 'translate(x,y)'.

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

Met deze functie wordt een pijl gemaakt.

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

Voorbeeld:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

De module `Rect` bevat enkele speciale functies voor het bewerken van rechthoeken.

De module biedt de volgende functies:

### <a name="getoffset"></a>getOffset

Met deze functie wordt een verschuiving van de rechthoek gemaakt.

```typescript
function getOffset(rect: IRect): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

Met deze functie wordt de grootte van de rechthoek geretourneerd.

```typescript
function getSize(rect: IRect): ISize;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

Met deze functie wordt de grootte van de rechthoek gewijzigd.

```typescript
function setSize(rect: IRect, value: ISize): void;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

Met deze functie wordt de rechterpositie van de rechthoek geretourneerd.

```typescript
function right(rect: IRect): number;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>bottom

Met deze functie wordt de benedenpositie van de rechthoek geretourneerd.

```typescript
function bottom(rect: IRect): number;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

Met deze functie wordt de linksbovenpositie van de rechthoek geretourneerd.

```typescript
function topLeft(rect: IRect): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

Met deze functie wordt de rechtsbovenpositie van de rechthoek geretourneerd.

```typescript
function topRight(rect: IRect): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

Met deze functie wordt de linksonderpositie van de rechthoek geretourneerd.

```typescript
function bottomLeft(rect: IRect): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

Met deze functie wordt de rechtsonderpositie van de rechthoek geretourneerd.

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>Voorbeeld

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

Met deze functie wordt een kopie van de rechthoek gemaakt.

```typescript
function clone(rect: IRect): IRect;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

Met deze functie wordt de rechthoek naar een tekenreeks geconverteerd.

```typescript
function toString(rect: IRect): string;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

Met deze functie wordt de opgegeven verschuiving toegepast op de rechthoek.

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

Met deze functie wordt de eerste rechthoek toegevoegd aan de tweede rechthoek.

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

Met deze functie wordt het dichtstbijzijnde punt op de rechthoek voor het opgegeven punt geretourneerd.

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

Met deze functie worden rechthoeken vergeleken en wordt de waarde True geretourneerd als deze hetzelfde zijn.

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

Met deze functie worden rechthoeken vergeleken op basis van de nauwkeurigheid van de waarden.

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

Met deze functie wordt gecontroleerd of de rechthoek leeg is.

```typescript
function isEmpty(rect: IRect): boolean;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

Met deze functie wordt gecontroleerd of de rechthoek het punt bevat.

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

Met deze functie wordt gecontroleerd of rechthoeken elkaar snijden.

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

Met deze functie wordt een snijpunt van rechthoeken geretourneerd.

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

Met deze functie worden rechthoeken gecombineerd.

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

Met deze functie wordt het middelpunt van de rechthoek geretourneerd.

```typescript
function getCentroid(rect: IRect): IPoint;
```

Voorbeeld:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>pointer

De module `pointer` bevat een speciale functie om de positie van de aanwijzer op te halen.

De module bevat de volgende functie:

### <a name="getcoordinates"></a>getCoordinates

Met deze functie wordt de positie van de aanwijzer geretourneerd.

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

Voorbeeld:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
