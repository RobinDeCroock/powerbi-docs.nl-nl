---
title: Hulpprogramma's voor interactiviteit met Power BI-visuals
description: In dit artikel wordt beschreven hoe u selecties toevoegt aan Power BI-visuals met behulp van hulpprogramma's voor interactiviteit.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379255"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Hulpprogramma's voor interactiviteit met Power BI-visuals

Hulpprogramma's voor interactiviteit (`InteractivityUtils`) is een set functies en klassen waarmee u de implementatie van kruislings selecteren en kruislings filteren kunt vereenvoudigen.

> [!NOTE]
> De nieuwe updates van de hulpprogramma's voor interactiviteit bieden alleen ondersteuning voor de nieuwste versie van de hulpprogramma's (3.x.x en hoger).

## <a name="installation"></a>Installatie

1. U kunt het pakket installeren door de volgende opdracht uit te voeren in de directory die uw huidige Power BI-visualproject bevat:

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Als u versie 3.0 of hoger of het hulpprogramma gebruikt, installeert u `powerbi-models` om afhankelijkheden op te lossen.

    ```bash
    npm install powerbi-models --save
    ```

3. Om de hulpprogramma's voor interactiviteit te gebruiken, moet u het vereiste onderdeel importeren in de broncode van de Power BI-visual.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Inclusief de CSS-bestanden

Als u het pakket met uw Power BI-visuals wilt gebruiken, moet u het volgende CSS-bestand importeren in het `.less`-bestand.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importeer het CSS-bestand als een `.less`-bestand omdat met het hulpprogramma voor Power BI-visuals externe CSS-regels worden meegenomen.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint-eigenschappen

Gegevenspunten bevatten meestal selecties en waarden. De interface breidt de `SelectableDataPoint`-interface uit.

`SelectableDataPoint` bevat al eigenschappen, zoals hieronder wordt beschreven.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Een interface voor gegevenspunten definiëren

1. Maak een exemplaar van de hulpprogramma's voor interactiviteit en sla het object op als een eigenschap van de visual

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

2. Breid de basisgedragsklasse uit.

    > [!NOTE]
    > `BaseBehavior` is geïntroduceerd in versie [5.6.x van de hulpprogramma's voor interactiviteit](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Als u een oudere versie gebruikt, maak dan een gedragsklasse op basis van onderstaand voorbeeld.

3. Definieer de interface voor de opties van de gedragsklasse.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Definieer een klasse voor `visual behavior`. Of breid de klasse `BaseBehavior` uit.

    **Een klasse definiëren voor `visual behavior`**

    De klasse is verantwoordelijk voor het afhandelen van de muisgebeurtenissen `click`, `contextmenu`.

    Wanneer een gebruiker op gegevenselementen klikt, roept de visual de selectiehandler aan om gegevenspunten te selecteren. Als de gebruiker op het achtergrondelement van de visual klikt, wordt de handler voor het wissen van de selectie aangeroepen.

    De klasse heeft de volgende bijbehorende methoden:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
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

    **De `BaseBehavior`-klasse uitbreiden**

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

5. Als u het klikken op elementen wilt afhandelen, roept u methode `on` voor het *d3*-selectieobject aan. Dit geldt ook voor `elementsSelection` en `clearCatcherSelection`.

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

6. Voeg een soortgelijke handler toe voor de gebeurtenis `contextmenu` om methode `showContextMenu` van de selectiemanager aan te roepen.

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

7. Voor het toewijzen van functies aan handlers roepen de hulpprogramma's voor interactiviteit de methode `bindEvents` aan. Voeg de volgende aanroepen toe aan de methode `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

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

8. De methode `renderSelection` is verantwoordelijk voor het bijwerken van de status van elementen van visuals in de grafiek. Voorbeeld van implementatie van `renderSelection`.

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

9. De laatste stap is het maken van een exemplaar van `visual behavior` en het aanroepen van de methode `bind` van het exemplaar van de hulpprogramma's voor interactiviteit.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` is het *d3*-selectieobject, dat alle selecteerbare elementen van de visual vertegenwoordigt.
    * `select(this.target)` is het *d3*-selectieobject, dat de hoofd-DOM-elementen van de visual vertegenwoordigt.
    * `this.categories` zijn gegevenspunten met elementen, waarbij de interface `VisualDataPoint` of `categories: VisualDataPoint[];` is.
    * `this.behavior` is een nieuw exemplaar van `visual behavior`, gemaakt in de constructor van de visual, zoals hieronder wordt weergegeven.

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
## <a name="next-steps"></a>Volgende stappen

* [Lees hoe u selecties voor het wijzigen van bladwijzers kunt afhandelen](bookmarks-support.md#visuals-with-selection)

* [Lees hoe u een contextmenu voor gegevenspunten van visuals kunt toevoegen](context-menu.md)

* [Lees hoe u SelectionManager kunt gebruiken om selecties aan Power BI-visuals toe te voegen](selection-api.md)
