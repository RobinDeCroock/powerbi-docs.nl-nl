---
title: Inleiding tot het gebruik van typehulpmiddelen in een Power BI-visual
description: In dit artikel wordt beschreven hoe u SVG-hulpmiddelen gebruikt om de basistypen voor Power BI-visuals uit te breiden
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206fda4e64dd13782753bfd067c962b3079bb4ff
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818727"
---
# <a name="type-utils"></a>Typehulpmiddelen

TypeUtils is een set functies en klassen om de basistypen voor Power BI-visuals uit te breiden.

## <a name="installation"></a>Installatie

Als u het pakket wilt installeren, voert u de volgende opdracht uit in de map met uw huidige aangepaste visual:

npm install powerbi-visuals-utils-typeutils --save Met deze opdracht wordt het pakket geïnstalleerd en wordt een pakket toegevoegd als afhankelijkheid van uw package.json

## <a name="double"></a>Double

`Double` biedt mogelijkheden voor het bewerken van de precisie van de getallen.

De module biedt de volgende functies:

### <a name="pow10"></a>pow10

Met deze functie wordt tot de macht 10 geretourneerd.

```typescript
function pow10(exp: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

Met deze functie wordt de logaritme met grondtal 10 van het getal geretourneerd.

```typescript
function log10(val: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

Met deze functie wordt tot de macht 10 geretourneerd, waarmee de precisie van het getal wordt aangegeven.

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

Met deze functie wordt gecontroleerd of een verschil tussen twee getallen kleiner is dan de opgegeven precisie.

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

Met deze functie wordt gecontroleerd of de eerste waarde kleiner is dan de tweede waarde.

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

Met deze functie wordt gecontroleerd of de eerste waarde kleiner dan of gelijk is aan de tweede waarde.

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

Met deze functie wordt gecontroleerd of de eerste waarde groter is dan de tweede waarde.

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

Met deze functie wordt gecontroleerd of de eerste waarde groter dan of gelijk is aan de tweede waarde.

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

Met deze functie wordt het getal naar beneden afgerond met de opgegeven precisie.

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

Deze functie `ceils` het getal met de opgegeven precisie.

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

Met deze functie wordt het getal naar beneden afgerond naar de opgegeven precisie.

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

Deze functie `ceils` het getal naar de opgegeven precisie.

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

Met deze functie wordt het getal afgerond naar de opgegeven precisie.

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

Met deze functie wordt een getal dat tussen min en max ligt geretourneerd.

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

Met deze functie wordt het getal afgerond.

```typescript
function round(x: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

Met deze functie wordt de decimale ruis verwijderd.

```typescript
function removeDecimalNoise(value: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

Met deze functie wordt gecontroleerd of het getal een geheel getal is.

```typescript
function isInteger(value: number): boolean;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

Met deze functie wordt het getal verhoogd met het opgegeven getal en het afgeronde getal geretourneerd.

```typescript
function toIncrement(value: number, increment: number): number;
```

Voorbeeld:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>Prototype

`Prototype` biedt mogelijkheden om objecten over te nemen.

De module biedt de volgende functies:

## <a name="inherit"></a>inherit

Met deze functie wordt een nieuw object geretourneerd met het opgegeven object als het prototype ervan.

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

Voorbeeld:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

Met deze functie wordt een nieuw object geretourneerd met het opgegeven object als het prototype ervan, maar uitsluitend als het prototype niet is ingesteld.

```typescript
function inheritSingle<T>(obj: T): T;
```

Voorbeeld:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` biedt de mogelijkheid om pixels te converteren naar punten en punten naar pixels.

De module biedt de volgende functies:

## <a name="tostring"></a>toString

Met deze functie wordt de pixelwaarde geconverteerd naar een tekenreeks.

```typescript
function toString(px: number): string;
```

Voorbeeld:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

Met deze functie wordt de opgegeven puntwaarde geconverteerd naar de pixelwaarde en wordt de tekenreeksinterpretatie geretourneerd.

```typescript
function fromPoint(pt: number): string;
```

Voorbeeld:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

Met deze functie wordt de opgegeven puntwaarde geconverteerd naar de pixelwaarde.

```typescript
function fromPointToPixel(pt: number): number;
```

Voorbeeld:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

Met deze functie wordt de pixelwaarde geconverteerd naar de puntwaarde.

```typescript
function toPoint(px: number): number;
```

Voorbeeld:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
