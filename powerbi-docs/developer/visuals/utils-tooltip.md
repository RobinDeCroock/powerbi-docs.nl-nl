---
title: Inleiding tot het gebruik van hulpmiddelen voor knopinfo in een Power BI-visual in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u de hulpmiddelen voor knopinfo kunt gebruiken om het aanpassen van knopinfo voor Power BI-visuals te vereenvoudigen. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: b2ddc85d9ba2530dc394b4106d72b4af702bd9b4
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888645"
---
# <a name="tooltip-utils"></a>Hulpmiddelen voor knopinfo
Dit artikel helpt u bij het installeren, importeren en gebruiken van hulpmiddelen voor knopinfo. Dit hulpmiddel is handig voor het aanpassen van de knopinfo in Power BI-visuals.

## <a name="requirements"></a>Vereisten
Als u het pakket wilt gebruiken, moet u beschikken over het volgende:
* [node.js](https://nodejs.org) (de meest recente LTS-versie wordt aanbevolen)
* [npm](https://www.npmjs.com/) (de minimaal ondersteunde versie is 3.0.0)
* De aangepaste visual die is gemaakt met [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools)

## <a name="installation"></a>Installatie

U kunt het pakket installeren door de volgende opdracht uit te voeren in de map met uw huidige visual:

```bash
npm install powerbi-visuals-utils-tooltiputils --save
```
Met deze opdracht wordt het pakket geïnstalleerd en wordt een pakket als een afhankelijkheid toegevoegd aan uw ```package.json```

## <a name="usage"></a>Gebruik

> In de gebruikshandleiding wordt een openbare API van het pakket beschreven. U vindt een beschrijving en enkele voorbeelden voor elke openbare interface van het pakket.

De inhoud van dit pakket biedt u een manier om `TooltipServiceWrapper` en methoden te maken voor het afhandelen van acties voor knopinfo. Er wordt gebruikgemaakt van interfaces voor knopinfo: `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

Het pakket heeft ook specifieke methoden (handlers voor aanraakgebeurtenissen) met betrekking tot mobiele ontwikkeling: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` biedt de eenvoudigste manier om knopinfo te bewerken.

Deze module biedt de volgende interface en functie:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfaces](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Aanraakgebeurtenissen](#touch-events)

### `createTooltipServiceWrapper`
Met deze functie wordt een instantie van ITooltipServiceWrapper gemaakt.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

De ```ITooltipService``` is beschikbaar in [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Voorbeeld**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

U kunt [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391) de voorbeeldcode bekijken van de aangepaste visual.

### `ITooltipServiceWrapper`
In deze interface worden de openbare methoden van TooltipService beschreven.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Met deze methode wordt knopinfo toegevoegd aan de huidige selectie.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Voorbeeld**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

U kunt [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931) de voorbeeldcode bekijken van de aangepaste visual.

Bekijk [hier](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648) ook nauwkeurig het volgende voorbeeld van een aanpassing van knopinfo in een aangepaste Gantt-visual

### `ITooltipServiceWrapper.hide`

Met deze methode wordt de knopinfo verborgen.

```typescript
hide(): void;
```

**Voorbeeld**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Deze interfaces worden gebruikt tijdens het maken van TooltipServiceWrapper en het gebruik ervan. Ze worden [hier](#itooltipservicewrapperaddtooltip) ook vermeld, in voorbeelden uit het vorige onderwerp.

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Met hulpmiddelen voor knopinfo kunnen nu verschillende aanraakgebeurtenissen worden verwerkt die handig zijn voor mobiele ontwikkeling.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Met deze methode wordt de naam van de touchStart-gebeurtenis geretourneerd.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Met deze methode wordt de naam van de touchStart-gebeurtenis geretourneerd.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Met deze methode wordt de huidige touchStart-gebeurtenis geretourneerd die wel/niet betrekking heeft op de aanwijzer.
