---
title: Wijzigen hoe een diagram in een rapport wordt gesorteerd
description: Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: Conceptual
ms.date: 05/12/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 67246168b5387f49e7bda22e470f5a908a4bff9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608239"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
In een Power BI-rapport kunt u de meeste visualisaties alfabetisch sorteren op namen of categorieën in het diagram, of op de numerieke waarde van elke categorie. Dit diagram is op de categorie **winkelnaam** gesorteerd.

![Staafdiagram waar x-as alfabetisch is gesorteerd](media/end-user-change-sort/pbi_chartsortcategory.png)

U kunt de sortering eenvoudig wijzigen van een categorie (winkelnaam) in een waarde (verkoop per vierkante meter).

1. Selecteer het beletselteken (...) en kies **Sorteren op > Sales Per Sq Ft**.
2. Selecteer zo nodig opnieuw het beletselteken en kies **Aflopend sorteren**.

   ![Video waarin Sorteren op wordt weergegeven en vervolgens oplopend en aflopend](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Niet alle visuele elementen kunnen worden gesorteerd. De volgende visuals kunnen niet worden gesorteerd: Treemap, overzicht, choropletenkaart, spreiding, meter, kaart, kaart met meerdere rijen, waterval.

## <a name="saving-changes-you-make-to-sort-order"></a>Wijzigingen opslaan die u aan de sorteervolgorde hebt aangebracht
Power BI-rapporten behouden de gemaakte wijzigingen in de filters, slicers, sorteervolgorde en gegevensweergave. Als u dus weg navigeert van een rapport en later terugkeert, worden uw wijzigingen opgeslagen.  Als u uw wijzigingen wilt terugzetten naar de instellingen van de maker van het rapport, selecteert u **Standaardinstelling herstellen** in de bovenste menubalk. 

![Sorteervolgorde behouden](media/end-user-change-sort/power-bi-reset-to-default.png)

Als de knop **Standaardinstelling herstellen** echter in het grijs wordt weergegeven, heeft de maker van het rapport de mogelijkheid om uw wijzigingen op te slaan (te behouden) uitgeschakeld.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sorteren op andere criteria
Af en toe wilt u het visuele element sorteren met behulp van een ander veld of andere criteria.  Stel dat u wilt sorteren op maand (en niet in alfabetische volgorde) of op gehele getallen in plaats van op cijfers (bijvoorbeeld op 0, 1, 9, 20 en niet op 0, 1, 20, 9).  

In sommige gevallen kunt u het visuele element sorteren zoals u dat zelf wilt, bijvoorbeeld op maand.  Als dat niet kan, dan moet u de achterliggende gegevensset enigszins aanpassen. Vraag de maker van het rapport de gegevensset bij te werken.

## <a name="next-steps"></a>Volgende stappen
Meer informatie over [visualisaties in Power BI-rapporten](end-user-visualizations.md) (Engelstalig).

[Power BI - basisconcepten](end-user-basic-concepts.md)
