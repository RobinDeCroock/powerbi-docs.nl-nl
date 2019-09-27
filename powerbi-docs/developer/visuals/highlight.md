---
title: Markeren
description: Selecties van gegevenspunten markeren in Power BI Visuals
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4ff2187dc99d4e790b08c11f55a37e31e85693ad
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71193977"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Gegevenspunten markeren in Power BI Visuals

Wanneer een element wordt geselecteerd, wordt de `values`-matrix in het `dataView`-object standaard gefilterd op alleen de geselecteerde waarden. Hierdoor worden in alle andere visuals op de pagina alleen de geselecteerde gegevens weergegeven.

![markeren met standaardgedrag dataView](./media/highlight-dataview.png)

Als u de eigenschap `supportsHighlight` in uw `capabilities.json` instelt op `true`, krijgt u de volledige ongefilterde `values`-matrix, samen met een `highlights`-matrix. De `highlights`-matrix heeft dezelfde lengte als de values-matrix, en alle niet-geselecteerde waarden worden ingesteld op `null`. Als deze eigenschap is ingeschakeld, is het de verantwoordelijkheid van de visual om de juiste gegevens te markeren door de `values`-matrix te vergelijken met de `highlights`-matrix.

![markeren met dataView supportshighlight](./media/highlight-dataview-supports.png)

In het voorbeeld ziet u de ene geselecteerde balk. Dit is de enige waarde in de highlights-matrix. Het is ook belangrijk om te weten dat er meerdere selecties en gedeeltelijke markeringen kunnen zijn. Er is de overeenkomstige numerieke waarde in de values-matrix en de highlights-matrix zal aanwezig maar verschillend zijn.
