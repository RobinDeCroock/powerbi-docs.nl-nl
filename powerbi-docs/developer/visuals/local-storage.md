---
title: Local Storage API in Power BI Visuals
description: In het artikel wordt beschreven hoe u de Power BI Visuals API gebruikt om toegang te krijgen tot de lokale opslag van de browser
author: uve
ms.author: v-grniki
ms.reviewer: KesemSharabi
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 85517fcd7ec773f947135614c94c0c4e4638ea48
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/23/2020
ms.locfileid: "76539320"
---
# <a name="local-storage-api"></a>Local Storage API

De Local Storage API is een API die voor een aangepaste visual kan worden gebruikt om de host te vragen gegevens op te slaan in of te laden uit de opslag van het apparaat. De API is geïsoleerd in de zin dat verschillende visualtypen gescheiden toegang tot de opslag hebben.

## <a name="sample"></a>Voorbeeld

Als een bepaalde teller steeds door de aangepaste visual moet worden verhoogd wanneer de updatemethode wordt aangeroepen, maar de tellerwaarde ook moet worden behouden en niet opnieuw mag worden ingesteld bij elke start van een visual:

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>Bekende beperkingen en problemen

De Local Storage API wordt niet standaard voor aangepaste visuals geactiveerd. Als u deze API voor uw aangepaste visual wilt activeren, stuurt u een aanvraag naar de ondersteuning voor aangepaste visuals voor Power BI `pbicvsupport@microsoft.com`.  
**Houd er rekening mee dat uw visual beschikbaar moet zijn in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) en [gecertificeerd](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/) moet zijn.**
