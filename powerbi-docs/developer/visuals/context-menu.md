---
title: Contextmenu toevoegen aan Power BI-visual
description: Meer informatie over het toevoegen van een contextmenu aan een visueel Power BI-element.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 9e63a1196ddc7557fcf8b2fceb424415a63d4df9
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748075"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Contextmenu toevoegen aan Power BI-visual

U kunt `selectionManager.showContextMenu()` gebruiken met `selectionId`-parameters en een positie (als een `{x:, y:}`-object) om in Power BI een contextmenu weer te geven voor uw visual.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` is geïntroduceerd in de Visuals-API 2.2.0.

Normaal gesproken wordt dit toegevoegd als een contextmenu dat wordt weergegeven door met de rechtermuisknop te klikken (of lang indrukken voor aanraakapparaten). Ter referentie toegevoegd aan het voorbeeld van het staafdiagram:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
