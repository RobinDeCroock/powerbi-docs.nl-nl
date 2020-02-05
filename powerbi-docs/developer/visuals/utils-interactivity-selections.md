---
title: Hulpprogramma's voor interactiviteit met Power BI-visuals
description: In dit artikel wordt beschreven hoe u selecties toevoegt aan Power BI-visuals met behulp van hulpprogramma's voor interactiviteit.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: be7a708dfcc6ebc40c62a1a9075e2cbf134363b1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818681"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Hulpprogramma's voor interactiviteit met Microsoft Power BI-visuals

InteractivityUtils is een set functies en klassen waarmee u de implementatie kunt vereenvoudigen van kruislingse selectie en kruislings filteren voor aangepaste visuals van Power BI.

## <a name="installation"></a>Installatie

> [!NOTE]
> Als u nog de oude versie van powerbi-visuals-tools gebruikt (versienummer eerder dan 3.x.x), installeert u de nieuwe versie van de hulpprogramma's (3.x.x).

> [!IMPORTANT]
> De nieuwe updates van de hulpprogramma's voor interactiviteit bieden alleen ondersteuning voor de nieuwste versie van de hulpprogramma's. [Lees hier meer over het bijwerken van de code voor uw visual om deze te gebruiken met de nieuwste hulpprogramma's](migrate-to-new-tools.md)

Als u het pakket wilt installeren, voert u de volgende opdracht uit in de map met uw huidige aangepaste visual:

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

Vanaf versie 3.0 of hoger moet u ook ```powerbi-models``` installeren om afhankelijkheden op te lossen.

```bash
npm install powerbi-models --save
```

Om de hulpprogramma's voor interactiviteit te gebruiken, moet u het vereiste onderdeel importeren in de broncode van de visual.

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>CSS-artefacten toevoegen aan de aangepaste visual

Als u het pakket wilt gebruiken met uw aangepaste visuals, moet u het volgende CSS-bestand importeren in het `your.less`-bestand:

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

U beschikt daarna over de volgende bestandsstructuur:

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Importeer het .css-bestand als een .less-bestand, omdat Power BI Visual Tools de externe CSS-regels inpakt.

## <a name="usage"></a>Gebruik

### <a name="define-interface-for-data-points"></a>Interface voor gegevenspunten definiëren

Gegevenspunten bevatten meestal selecties en waarden. De interface breidt de `SelectableDataPoint`-interface uit. `SelectableDataPoint` bevat al eigenschappen:

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

De eerste stap voor het gebruiken van de hulpprogramma's voor interactiviteit is het maken van een exemplaar van de hulpprogramma's en het opslaan van het object als een eigenschap van de visual

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

De tweede stap is het uitbreiden van de klasse BaseBehavior:

> [!NOTE]
> BaseBehavior is geïntroduceerd in [versie 5.6.x van de hulpprogramma's voor interactiviteit](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Als u de oudere versie gebruikt, maakt u een gedragsklasse op basis van het voorbeeld hieronder (`BaseBehavior`-klasse is hetzelfde):

Definieer de interface voor opties van gedragsklasse:

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

Definieer een klasse voor `visual behavior`. De klasse is verantwoordelijk voor het afhandelen van de muisgebeurtenissen `click`, `contextmenu`.
Als een gebruiker klikt op gegevenselementen van de visual, wordt de selectie-handler aangeroepen om gegevenspunten te selecteren. Als de gebruiker op het achtergrondelement van de visual klikt, wordt de handler voor het wissen van de selectie aangeroepen. De klasse heeft bijbehorende methoden: `bindClick`, `bindClearCatcher`, `bindContextMenu`.

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

U kunt de klasse `BaseBehavior` ook uitbreiden:

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

Als u het klikken op elementen wilt afhandelen, roept u de methode `on` van het D3-Selection-object aan (ook voor elementsSelection en clearCatcherSelection):

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

Voeg een soortgelijke handler toe voor de gebeurtenis `contextmenu` om de methode `showContextMenu` van de SelectionManager aan te roepen:

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

De hulpprogramma's voor interactiviteit roepen `bindEvents`-methoden aan om functies toe te wijzen aan handlers, en om aanroepen van `bindClick`, `bindClearCatcher` en `bindContextMenu` toe te voegen aan de methode `bindEvents`:

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

De methode `renderSelection` is verantwoordelijk voor het bijwerken van de status van elementen van visuals in de grafiek.

Voorbeeld van implementatie van de methode `renderSelection`:

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

De laatste stap is het maken van een exemplaar van `visual behavior` en het aanroepen van de methode `bind` van het exemplaar van de hulpprogramma's voor interactiviteit:

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` is het D3-selectieobject dat alle selecteerbare elementen in de visual vertegenwoordigt.

* `select(this.target)` is het D3-selectieobject dat DOM-hoofdelementen van de visual vertegenwoordigt.

* `this.categories` zijn gegevenspunten met elementen, waarbij de interface `VisualDataPoint` is (of `categories: VisualDataPoint[];`)

* `this.behavior` is een nieuw exemplaar van `visual behavior`

  gemaakt in de constructor van de visual:

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

Uw visual is nu gereed om de selectie af te handelen.

## <a name="next-steps"></a>Volgende stappen

* [Lees hoe u selecties voor het wijzigen van bladwijzers kunt afhandelen](bookmarks-support.md#visuals-with-selection)

* [Lees hoe u een contextmenu voor gegevenspunten van visuals kunt toevoegen](context-menu.md)

* [Lees hoe u SelectionManager kunt gebruiken om selecties aan Power BI-visuals toe te voegen](selection-api.md)
