---
title: Meerdere velden aan een hiërarchieslicer toevoegen
description: Meer informatie over het maken van een hiërarchieslicer met meerdere velden in een hiërarchie.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238182"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Meerdere velden aan een hiërarchieslicer toevoegen

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Als u meerdere gerelateerde velden wilt filteren binnen één slicer, doet u dit door een zogeheten *hiërarchie*slicer te maken. U kunt deze slicers maken in een Power BI Desktop of in de Power BI-service.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Hiërarchieslicer in Power BI":::

Wanneer u meerdere velden aan de slicer toevoegt, wordt er standaard een pijl of een *dubbele punthaak* weergegeven naast de items die kunnen worden uitgevouwen, zodat de items op het volgende niveau te zien zijn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Hiërarchieslicer als vervolgkeuzelijst in Power BI":::
 
 
Wanneer u een of meer onderliggende items voor een item selecteert, ziet u een semi-geselecteerde cirkel voor het item op het hoogste niveau.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Hiërarchieslicer voor enkelvoudige selectie in Power BI":::

## <a name="format-the-slicer"></a>De slicer opmaken

Het gedrag van de slicer is niet gewijzigd. U kunt ook uw slicer opmaken zoals u wilt. U kunt deze bijvoorbeeld instellen op de modus voor enkelvoudige selectie. U kunt ook wisselen tussen een lijst en vervolgkeuzelijst. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Hiërarchieslicer opgemaakt als vervolgkeuzeslicer":::

### <a name="change-the-expandcollapse-icon"></a>Het pictogram uitvouwen/samenvouwen veranderen

Hiërarchieslicers hebben een aantal andere opmaakopties. U kunt het pictogram uitvouwen/samenvouwen wijzigen van de standaard pijl naar een plus/min-teken of een caret-teken.

1. Selecteer de slicer en selecteer vervolgens **Indeling**.
1. Vouw **Items** uit en selecteer **Pictogram uitvouwen/samenvouwen**.
1. Kies uit **Dubbele punthaak**, **Plus/min** of **Caret**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Selecteer een pictogram voor uitvouwen/samenvouwen voor uw hiërarchieslicer":::
 
### <a name="change-the-indentation"></a>De inspringing wijzigen

Als er weinig ruimte op uw rapport is, is het raadzaam om de hoeveelheid die u voor de onderliggende items laat inspringen te verminderen. Standaard is de inspringing 15 pixels, maar u kunt deze verhogen of verlagen. 

1. Selecteer de slicer en selecteer vervolgens **Indeling**.
1. Vouw **Items** uit en sleep **Lay-outindeling met interval** naar kleiner of groter. U kunt ook gewoon een getal in het vak typen.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="De inspringing van de hiërarchieslicer instellen":::

## <a name="next-steps"></a>Volgende stappen

- [Slicers in Power BI](../visuals/power-bi-visualization-slicers.md)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)