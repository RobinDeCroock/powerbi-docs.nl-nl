---
title: Een landingspagina toevoegen aan uw Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u een landingspagina toevoegt aan Power BI-visuals. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4381ecf63c0864c4d68e48959efc14baa9d4553b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886345"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Een landingspagina toevoegen aan Power BI-visuals

Met API 2.3.0 kunt u een landingspagina toevoegen aan uw Power BI-visuals. U kunt dit doen door `supportsLandingPage` toe te voegen aan de mogelijkheden en deze in te stellen op waar. Met deze actie wordt uw visual geïnitialiseerd en bijgewerkt voordat u er gegevens aan toevoegt. Omdat de visual geen watermerk meer bevat, kunt u een eigen landingspagina ontwerpen voor weergave in de visual, zolang deze geen gegevens bevat.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Een voorbeeld van een landingspagina wordt in de volgende afbeelding weergegeven:

![schermopname van landingspagina](media/landing-page/app-landing-page.png)
