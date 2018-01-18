---
title: Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
description: Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/20/2017
ms.author: mihart
ms.openlocfilehash: 13da4602306b1218baee81909d37897524f6dfc9
ms.sourcegitcommit: 6ea8291cbfcb7847a8d7bc4e2b6abce7eddcd0ea
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/21/2017
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
In een Power BI-rapport kunt u de meeste visualisaties alfabetisch sorteren op namen of categorieën in het diagram, of op de numerieke waarde van elke categorie. Zo is het onderstaande diagram op winkelnaam gesorteerd.

![](media/power-bi-report-change-sort/pbi_chartsortcategory.png)

U kunt de sortering eenvoudig wijzigen van een categorie (winkelnaam) in een waarde (verkoop per vierkante meter).

1. Selecteer het beletselteken (...) en kies **Sort by Sales Per Sq Ft**.
2. Selecteer desgewenst het pictogram ![](media/power-bi-report-change-sort/sorticon.png) om **aflopend** te sorteren.
   
   ![](media/power-bi-report-change-sort/sortby.gif)
   
   **OPMERKING**: niet alle visuele elementen kunnen worden gesorteerd.  De volgende visuele elementen kunnen niet worden gesorteerd: treemap, kaart, choropletenkaart, spreidingsdiagram, meter, kaart met meerdere rijen, watervalgrafiek.

## <a name="sorting-using-other-criteria"></a>Sorteren op andere criteria
Af en toe wilt u het visuele element sorteren met behulp van een ander veld of andere criteria.  Stel dat u wilt sorteren op maand (en niet in alfabetische volgorde) of op gehele getallen in plaats van op cijfers (bijvoorbeeld op 0, 1, 9, 20 en niet op 0, 1, 20, 9).  

In sommige gevallen kunt u het visuele element sorteren zoals u dat zelf wilt, bijvoorbeeld op maand.  Als dat niet kan, dan moet u de achterliggende gegevensset enigszins aanpassen. Hier volgen enkele oplossingen:

* Gebruik in Power BI Desktop [het tabblad Data Tools Modeling om op een andere kolom te sorteren](desktop-sort-by-column.md) (Engelstalig).
* Als u in Excel eigenaar bent van de gegevensset, voegt u een nieuwe kolom toe waaraan de naam van de maand en het getal worden toegevoegd. Vernieuw vervolgens de gegevensset of importeer deze opnieuw. De nieuwe kolom wordt weergegevens in het gedeelte Velden.
* In Excel: zorg ervoor dat de numerieke kolommen met 'geheel getal' of 'decimaal' zijn aangeduid en niet met 'tekst'.

## <a name="next-steps"></a>Volgende stappen
Meer informatie over [visualisaties in Power BI-rapporten](power-bi-report-visualizations.md) (Engelstalig).

[Power BI - basisconcepten](service-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
