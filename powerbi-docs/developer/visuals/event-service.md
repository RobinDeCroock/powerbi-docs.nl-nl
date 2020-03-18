---
title: Gebeurtenissen weergeven in Power BI-visuals
description: Power BI-visuals kunnen Power BI melden dat ze gereed zijn om te worden geëxporteerd naar Power Point of PDF.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: c54aaa92f3463ce1102866c8d3b69532c8b25cf7
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380244"
---
# <a name="render-events-in-power-bi-visuals"></a>Gebeurtenissen weergeven in Power BI-visuals

De nieuwe API bestaat uit drie methoden (`started`, `finished` of `failed`) die tijdens de weergave moeten worden aangeroepen.

Wanneer de weergave wordt gestart, roept de code van de Power BI-visual de methode `renderingStarted` aan om aan te geven dat het weergaveproces is gestart.

Als het weergaveproces is voltooid, roept de code van de Power BI-visual onmiddellijk de methode `renderingFinished` aan en stelt de listeners (primair *exporteren naar PDF* en *exporteren naar PowerPoint*) ervan op de hoogte dat de afbeelding van de visual gereed is om te worden geëxporteerd.

Als er een probleem optreedt tijdens het proces, wordt de Power BI-visual niet weergegeven. De code van de Power BI-visual moet de methode `renderingFailed` aanroepen om de listener te laten weten dat het weergaveproces niet is voltooid. Deze methode biedt ook een optionele tekenreeks om de reden voor het mislukken aan te geven.

## <a name="usage"></a>Gebruik

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>Voorbeeld: In de visual worden geen animaties weergegeven

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>Voorbeeld: In de visual worden animaties weergegeven

Als de visual animaties of asynchrone functies voor weergave heeft, moet de methode `renderingFinished` worden aangeroepen na de animatie of binnen de asynchrone functie.

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Renderinggebeurtenissen voor certificering van visuals

Het ondersteunen van weergavegebeurtenissen door de visual is een van de vereisten voor de certificering van visuals. Voor meer informatie raadpleegt u de [vereisten voor certificering](power-bi-custom-visuals-certified.md#certification-requirements).