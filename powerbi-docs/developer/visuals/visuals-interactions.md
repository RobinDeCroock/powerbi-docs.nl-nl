---
title: Visuele interacties in Power BI-visuals
description: In dit artikel wordt beschreven hoe u kunt controleren of Power BI-visuals visuele interacties moeten toestaan.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: b8b1a1a59ee9fae5a1c248548a14c5f91438edc9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "79378933"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Visuele interacties in Power BI-visuals

Visuals kunnen een query uitvoeren op de waarde van de vlag `allowInteractions`, waarmee wordt aangegeven of de visual visuele interacties moet toestaan. Zo zijn visuals bijvoorbeeld interactief bij het bekijken of bewerken van een rapport, maar niet interactief wanneer deze worden bekeken in een dashboard. Deze interacties zijn onder andere *klikken*, *pannen*, *zoomen*, *selecteren* en meer. 

> [!NOTE]
> Schakel knopinfo in alle scenario's in, ongeacht welke vlag wordt aangegeven.

De vlag `allowInteractions` wordt doorgegeven als een booleaanse waarde tijdens de initialisatie van de visual, als lid van de IVisualHost-interface.

In een Power BI-scenario waarvoor de visuals niet interactief mogen zijn (bijvoorbeeld op Dashboard-tegels), wordt de vlag `allowInteractions` ingesteld op `false`. In andere gevallen (bijvoorbeeld in een rapport) wordt `allowInteractions` ingesteld op `true`.

Zie de [SampleBarChart-opslagplaats voor visuals](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001) voor meer informatie.

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
