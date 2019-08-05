---
title: Markeren
description: Selecties van gegevenspunten markeren in Power BI Visuals
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1ee45781ddc29eee9eeab23a5d748fb7752fe907
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424810"
---
# <a name="highlight-data-points-in-power-bi-visuals"></a>Gegevenspunten markeren in Power BI Visuals

Wanneer een element wordt geselecteerd, wordt de `values`-matrix in het `dataView`-object standaard gefilterd op alleen de geselecteerde waarden. Hierdoor worden in alle andere visuals op de pagina alleen de geselecteerde gegevens weergegeven.

![markeren met standaardgedrag dataView](./media/highlight-dataview.png)

Als u de eigenschap `supportsHighlight` in uw `capabilities.json` instelt op `true`, krijgt u de volledige ongefilterde `values`-matrix, samen met een `highlights`-matrix. De `highlights`-matrix heeft dezelfde lengte als de values-matrix, en alle niet-geselecteerde waarden worden ingesteld op `null`. Als deze eigenschap is ingeschakeld, is het de verantwoordelijkheid van de visual om de juiste gegevens te markeren door de `values`-matrix te vergelijken met de `highlights`-matrix.

![markeren met dataView supportshighlight](./media/highlight-dataview-supports.png)

In het voorbeeld ziet u de ene geselecteerde balk. Dit is de enige waarde in de highlights-matrix. Het is ook belangrijk om te weten dat er meerdere selecties en gedeeltelijke markeringen kunnen zijn. Er is de overeenkomstige numerieke waarde in de values-matrix en de highlights-matrix zal aanwezig maar verschillend zijn.
