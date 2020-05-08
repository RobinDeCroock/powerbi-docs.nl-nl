---
title: Externe bibliotheken toevoegen aan Power BI-visuals
description: In dit artikel wordt beschreven hoe u externe bibliotheken gebruikt in Power BI-visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114124"
---
# <a name="adding-external-libraries"></a>Externe bibliotheken toevoegen

In dit artikel wordt beschreven hoe u externe bibliotheken gebruikt in Power BI-visuals. Het bevat informatie over het installeren, importeren en aanroepen van externe bibliotheken vanuit de code van de Power BI-visual.

## <a name="javascript-libraries"></a>JavaScript-bibliotheken

1. Installeer een externe JavaScript-bibliotheek met behulp van een pakketbeheerprogramma, zoals *NPM* of *yarn*.
2. Importeer de vereiste modules in de bronbestanden met behulp van de externe bibliotheek.

>[!NOTE]
>Als u typeringen aan uw JavaScript-bibliotheek wilt toevoegen en IntelliSense en veiligheid tijdens het compileren wilt gebruiken, moet u ervoor zorgen dat u het juiste pakket installeert.

### <a name="installing-the-d3-library"></a>De d3-bibliotheek installeren

Dit is een voorbeeld van het installeren van de [d3-bibliotheek](https://www.npmjs.com/package/d3) en het [@types/d3](https://www.npmjs.com/package/@types/d3)-pakket met behulp van [npm](https://www.npmjs.com/).

Zie voor een volledig voorbeeld de code in [Power BI-visuals](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installeer het *d3*-pakket en het *d3 types*-pakket.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importeer de *d3*-bibliotheek in de bestanden die deze gebruiken, zoals `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS-framework

1. Installeer een extern CSS-framework met behulp van een pakketbeheerprogramma, zoals *npm* of *yarn*.
2. Neem in het bestand `.less` van de visual de instructie `import` op.

### <a name="installing-bootstrap"></a>Bootstrap installeren

Dit is een voorbeeld van het installeren van [bootstrap](https://www.npmjs.com/package/bootstrap) met behulp van [npm](https://www.npmjs.com/).

Zie voor een volledig voorbeeld de code in [Power BI-visuals](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installeer het *bootstrap*-pakket.

    ```powershell
    npm install bootstrap --save
    ```

2. Neem de instructie `import` op in `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
