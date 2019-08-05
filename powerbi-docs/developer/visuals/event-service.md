---
title: Gebeurtenissen weergeven
description: Power BI-visuals kunnen Power BI melden dat ze gereed zijn om te exporteren naar Power Point/PDF
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425086"
---
# <a name="event-service"></a>Gebeurtenisservice

De nieuwe API bestaat uit drie methoden (gestart, voltooid of mislukt) die tijdens de rendering moeten worden aangeroepen.

Wanneer de rendering wordt gestart, roept de code van de aangepaste visual de methode renderingStarted aan om aan te geven dat het renderingproces is gestart.

Als de rendering met succes voltooid is, roept de code van de aangepaste visual onmiddellijk de `renderingFinished`-methode aan en stelt de listeners (**primair 'exporteren naar PDF' en 'exporteren naar PowerPoint'** ) ervan op de hoogte dat de afbeelding van de visual gereed is.

Als er een probleem is opgetreden tijdens het renderingproces waardoor de aangepaste visual niet worden voltooid, moet de code van de aangepaste visual de `renderingFailed`-methode aanroepen om de listener te laten weten dat het renderingproces niet is voltooid. Deze methode biedt ook een optionele tekenreeks voor de oorzaak van het mislukken.

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
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>Eenvoudig voorbeeld. De visual heeft geen animaties bij rendering

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

### <a name="sample-the-visual-with-animation"></a>Voorbeeld. De visual met animatie

Als de visual animaties of asynchrone functies voor rendering heeft, moet de `renderingFinished`-methode worden aangeroepen na de animatie of binnen de asynchrone functie.

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>Renderinggebeurtenissen voor certificering van visuals

Het ondersteunen van renderinggebeurtenissen door de visual is een van de vereisten voor de certificering van visuals. Lees meer over [vereisten voor certificering](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)
