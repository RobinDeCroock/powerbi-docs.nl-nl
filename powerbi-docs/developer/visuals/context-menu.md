---
title: Mogelijkheden en eigenschappen van Power BI-visuals
description: In dit artikel worden de mogelijkheden en eigenschappen van Power BI-visuals beschreven.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1e2fbe3288e5dbb759a56ad1c299db2e277408b2
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380750"
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
