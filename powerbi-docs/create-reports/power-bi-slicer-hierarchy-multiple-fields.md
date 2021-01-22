---
title: Meerdere velden aan een hiërarchieslicer toevoegen
description: Meer informatie over het maken van een hiërarchieslicer met meerdere velden in een hiërarchie.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Create reports
ms.openlocfilehash: abed7e9f6da352d5461868e6371ffefb814eb3ff
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597637"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Meerdere velden aan een hiërarchieslicer toevoegen

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Als u meerdere gerelateerde velden wilt filteren binnen één slicer, doet u dit door een zogeheten *hiërarchie* slicer te maken. U kunt deze slicers maken in een Power BI Desktop of in de Power BI-service.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Schermopname van hiërarchieslicer in Power BI.":::

Wanneer u meerdere velden aan de slicer toevoegt, wordt er standaard een pijl of een *dubbele punthaak* weergegeven naast de items die kunnen worden uitgevouwen, zodat de items op het volgende niveau te zien zijn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Schermopname van hiërarchieslicer als vervolgkeuzelijst in Power BI.":::
 
 
Wanneer u een of meer onderliggende items voor een item selecteert, ziet u een semi-geselecteerde cirkel voor het item op het hoogste niveau.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Schermopname van hiërarchieslicer voor enkelvoudige selectie in Power BI.":::

## <a name="format-the-slicer"></a>De slicer opmaken

Het gedrag van de slicer is niet gewijzigd. U kunt ook uw slicer opmaken zoals u wilt. U kunt deze bijvoorbeeld instellen op de modus voor enkelvoudige selectie. U kunt ook wisselen tussen een lijst en vervolgkeuzelijst. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Schermopname van hiërarchieslicer opgemaakt als vervolgkeuzeslicer.":::

U kunt ook de volgende opmaakwijzigingen aanbrengen.

### <a name="change-the-title"></a>De titel wijzigen

U kunt de titel voor elke slicer ook bewerken, maar dit is vooral handig voor hiërarchieslicers. De naam van een hiërarchieslicer is standaard een lijst met de veldnamen in de hiërarchie.

In dit voorbeeld bevat de titel van de slicer de drie velden in de hiërarchie: Type, Platform en Naam.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Schermopname van hiërarchieslicer met type-, platform-en naamvelden.":::

Als u de naam wilt wijzigen, selecteert u de slicer en selecteert u vervolgens het deelvenster **Opmaak**. Onder **Koptekstslicer** ziet u de huidige naam van de slicer in het vak **Titeltekst**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Schermopname van het deelvenster Indeling met de in huidige titel.":::

Selecteer de tekst en voeg een nieuwe naam toe.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Schermopname van de nieuwe titel voor de hiërarchieslicer.":::


### <a name="change-the-expandcollapse-icon"></a>Het pictogram uitvouwen/samenvouwen veranderen

Hiërarchieslicers hebben een aantal andere opmaakopties. U kunt het pictogram uitvouwen/samenvouwen wijzigen van de standaard pijl naar een plus/min-teken of een caret-teken.

1. Selecteer de slicer en selecteer vervolgens **Indeling**.
1. Vouw **Items** uit en selecteer **Pictogram uitvouwen/samenvouwen**.
1. Kies uit **Dubbele punthaak**, **Plus/min** of **Caret**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Schermopname van Selecteer een pictogram voor uitvouwen/samenvouwen voor uw hiërarchieslicer.":::
 
### <a name="change-the-indentation"></a>De inspringing wijzigen

Als er weinig ruimte op uw rapport is, is het raadzaam om de hoeveelheid die u voor de onderliggende items laat inspringen te verminderen. Standaard is de inspringing 15 pixels, maar u kunt deze verhogen of verlagen. 

1. Selecteer de slicer en selecteer vervolgens **Indeling**.
1. Vouw **Items** uit en sleep **Lay-outindeling met interval** naar kleiner of groter. U kunt ook gewoon een getal in het vak typen.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Schermopname van De inspringing van de hiërarchieslicer instellen.":::
    
## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

- Voor modellen met tabbladen is voor deze functie SQL Server Analysis Services 2017 of nieuwer vereist.
- Voor multidimensionale modellen is voor deze functie SQL Server Analysis Services 2019 CU5 of nieuwer vereist, waarbij SuperDAXMD moet zijn ingeschakeld. Lees meer over [SuperDAXMD](/analysis-services/multidimensional-models/dax-for-multidimensional-models#superdaxmd).

## <a name="next-steps"></a>Volgende stappen

- [Slicers in Power BI](../visuals/power-bi-visualization-slicers.md)
- Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
