---
title: Interacties met visuals
description: Controleren of Power BI Visual visuele interacties moet toestaan
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424488"
---
# <a name="visuals-interactions"></a>Interacties met visuals

Visuals kunnen de waarde van de vlag 'allowInteractions' opvragen, die aangeeft of de visual visuele interacties moet toestaan.
Zo zijn visuals bijvoorbeeld interactief bij het bekijken of bewerken van een rapport, maar niet interactief wanneer ze worden bekeken in een dashboard.
Deze interacties zijn onder andere klikken, pannen, zoomen en selecteren.
Merk op dat knopinfo in alle scenario's actief moet zijn, ongeacht de waarde van deze vlag.

De vlag 'allowInteractions' wordt doorgegeven als een booleaanse waarde tijdens de initialisatie van de visual, als lid van de IVisualHost-interface.

In een Power BI-scenario waarvoor de visuals niet interactief mogen zijn (bijvoorbeeld Dashboard-tegels), wordt de vlag 'allowInteractions' ingesteld op 'false'.
Anders (bijvoorbeeld in een rapport), wordt 'allowInteractions' ingesteld op 'true'.

Zie voor meer informatie de [SampleBarChart visual repository](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
