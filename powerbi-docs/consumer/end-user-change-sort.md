---
title: Wijzigen hoe een diagram in een rapport wordt gesorteerd
description: Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852367"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

U kunt in de Power BI-service de weergave van een visueel element wijzigen door deze op andere gegevensvelden te sorteren. Als u de sortering van een visual wijzigt, kunt u de informatie markeren die u wilt overbrengen en ervoor zorgen dat de visual de trend (of de nadruk) weergeeft.

Of u nu numerieke gegevens (zoals verkoopcijfers) of tekstgegevens (zoals provincienamen) gebruikt, u kunt uw visualisaties sorteren zoals u wilt en ze eruit laten zien zoals u wilt. Power BI biedt veel flexibiliteit voor sorteren en snelle menu's die u kunt gebruiken. Selecteer in een visual **Meer acties** (...) en selecteer vervolgens het veld waarop u wilt sorteren.

![Staafdiagram waar x-as alfabetisch is gesorteerd](media/end-user-change-sort/power-bi-more-actions.png)

Visuals op een dashboard kunnen niet worden gesorteerd, maar in een Power BI-rapport kunt u de meeste visualisaties alfabetisch sorteren op namen of categorieën in het diagram, of op de numerieke waarde van elke categorie. Zo is dit diagram alfabetisch gesorteerd op de categorie **winkelnaam**.

![Staafdiagram waar x-as alfabetisch is gesorteerd](media/end-user-change-sort/pbi-chartsortcategory.png)

U kunt de sortering eenvoudig wijzigen van een categorie (winkelnaam) in een waarde (verkoop per vierkante meter).

1. Selecteer **Meer acties** (...) en kies **Sorteren op > Sales Per Sq Ft**.
2. Selecteer zo nodig opnieuw **Meer acties** (...) en kies **Aflopend sorteren**. Het veld dat wordt gebruikt om te sorteren is vetgedrukt en bevat een gele balk.

   ![Video waarin Sorteren op wordt weergegeven en vervolgens oplopend en aflopend](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Niet alle visuele elementen kunnen worden gesorteerd. De volgende visuals kunnen bijvoorbeeld niet worden gesorteerd: treemap, kaart, choropletenkaart, spreiding, meter, kaart, waterval.

## <a name="saving-changes-you-make-to-sort-order"></a>Wijzigingen opslaan die u aan de sorteervolgorde hebt aangebracht
Power BI-rapporten behouden de gemaakte wijzigingen in de filters, slicers, sorteervolgorde en gegevensweergave. Als u dus weg navigeert van een rapport en later terugkeert, worden uw wijzigingen opgeslagen.  Als u uw wijzigingen wilt terugzetten naar de instellingen van de maker van het rapport, selecteert u **Standaardinstelling herstellen** in de bovenste menubalk. 

![Sorteervolgorde behouden](media/end-user-change-sort/power-bi-reset.png)

Als de knop **Standaardinstelling herstellen** echter in het grijs wordt weergegeven, heeft de maker van het rapport de mogelijkheid om uw wijzigingen op te slaan (te behouden) uitgeschakeld.

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>Sorteren op andere criteria
Af en toe wilt u de visual sorteren met behulp van een ander veld (Dat niet in de visual is opgenomen) of andere criteria.  Stel dat u wilt sorteren op maand (en niet in alfabetische volgorde) of op gehele getallen in plaats van op cijfers (bijvoorbeeld op 0, 1, 9, 20 en niet op 0, 1, 20, 9).  De rapportontwerper kan de gegevensset bijwerken om dit type sortering in te schakelen. Contactinformatie voor de ontwerper vindt u door de naam van het rapport te selecteren in de balk met de koptekst.

![Vervolgkeuzelijst met contactgegevens](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Volgende stappen
Meer informatie over [visualisaties in Power BI-rapporten](end-user-visualizations.md) (Engelstalig).

[Power BI - basisconcepten](end-user-basic-concepts.md)
