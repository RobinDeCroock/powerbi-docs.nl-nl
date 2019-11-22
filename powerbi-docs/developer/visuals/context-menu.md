---
title: Mogelijkheden en eigenschappen van Power BI-visuals
description: In dit artikel worden de mogelijkheden en eigenschappen van Power BI-visuals beschreven.
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061771"
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
