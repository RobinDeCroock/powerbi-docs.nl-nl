---
title: Local Storage API in Power BI Visuals
description: In het artikel wordt beschreven hoe u de Power BI Visuals API gebruikt om toegang te krijgen tot de lokale opslag van de browser
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879886"
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

De Local Storage API wordt niet standaard voor aangepaste visuals geactiveerd. Als u deze API voor uw aangepaste visual wilt activeren, stuurt u een aanvraag naar de ondersteuning voor aangepaste visuals voor Power BI `pbicvsupport@microsoft.com`
