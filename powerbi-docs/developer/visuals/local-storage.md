---
title: De API voor lokale opslag in Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In het artikel wordt beschreven hoe u de API voor Power BI-visuals gebruikt om toegang te krijgen tot de lokale opslag van de browser. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: abec68c5622d3dcd96746148ed7a6da4f06c8ec0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888185"
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

De Local Storage API wordt niet standaard voor Power BI-visuals geactiveerd. Als u deze API voor uw Power BI-visual wilt activeren, stuurt u een aanvraag naar de ondersteuning voor Power BI-visuals`pbicvsupport@microsoft.com`.  
**Houd er rekening mee dat uw visual beschikbaar moet zijn in [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) en [gecertificeerd](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/) moet zijn.**
