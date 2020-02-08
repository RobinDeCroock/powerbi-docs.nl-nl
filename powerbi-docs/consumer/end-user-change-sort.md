---
title: Wijzigen hoe een diagram in een rapport wordt gesorteerd
description: Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 76370e2b633e21674ba878e70b5ecfc333453c96
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76889208"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Wijzigen hoe een diagram in een Power BI-rapport wordt gesorteerd



[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]


> [!IMPORTANT]
> **Dit artikel is bedoeld voor Power BI-gebruikers die niet beschikken over bewerkingsmachtigingen voor het rapport of de gegevensset en die alleen werken in de online versie van Power BI (de Power BI-service). Als u een *ontwerper* van rapporten bent, of een *beheerder* of *eigenaar*, bevat dit artikel mogelijk niet alle informatie die u nodig hebt. Lees in dat geval [Op kolom sorteren in Power BI Desktop](../desktop-sort-by-column.md)** .

U kunt in de Power BI-service de weergave van een visueel element wijzigen door deze op andere gegevensvelden te sorteren. Als u de sortering van een visual wijzigt, kunt u de informatie markeren die u wilt overbrengen. Of u nu numerieke gegevens (zoals verkoopcijfers) of tekstgegevens (zoals provincienamen) gebruikt, u kunt uw visualisaties sorteren zoals u wilt. Power BI biedt veel flexibiliteit voor sorteren en snelle menu's die u kunt gebruiken. 

Visuals op een dashboard kunnen niet worden gesorteerd, maar in een Power BI-rapport kunt u de meeste visuals sorteren 

## <a name="get-started"></a>Aan de slag

Als u aan de slag wilt gaan, selecteert u een visual voor een rapport en kiest u **Meer acties** (...).  Er zijn drie opties voor het sorteren: **Aflopend sorteren**, **Oplopend sorteren** en **Sorteren op**. 
    

![Staafdiagram waar x-as alfabetisch is gesorteerd](media/end-user-change-sort/power-bi-more-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Alfabetisch of numeriek sorteren

U kunt u visuals alfabetisch sorteren op de tekstnamen van de categorieën in de visual, of op de numerieke waarden van elke categorie. Zo is dit diagram alfabetisch gesorteerd op de X-ascategorie **Winkelnaam**.

![Staafdiagram waar x-as alfabetisch is gesorteerd](media/end-user-change-sort/powerbi-sort-category.png)

U kunt de sortering eenvoudig wijzigen van een categorie (winkelnaam) in een waarde (verkoop per vierkante meter). Selecteer **Meer acties** (...) en kies **Sorteren op**. Selecteer een numerieke waarde die wordt gebruikt in de visual.  In dit voorbeeld hebben we **Verkoop per vierkante meter** geselecteerd.

![Schermopname van het selecteren van de actie Sorteren op en vervolgens het selecteren van een waarde](media/end-user-change-sort/power-bi-sort-value.png)

Wijzig, indien nodig, de sorteervolgorde van oplopend in aflopend.  Selecteer opnieuw **Meer acties** (...) en kies **Aflopend sorteren** of **Oplopend sorteren**. Het veld dat wordt gebruikt om te sorteren is vetgedrukt en bevat een gele balk.

   ![Video waarin Sorteren op wordt weergegeven en vervolgens oplopend en aflopend](media/end-user-change-sort/sort.gif)

> [!NOTE]
> Niet alle visuele elementen kunnen worden gesorteerd. De volgende visuals kunnen bijvoorbeeld niet worden gesorteerd: treemap, kaart, choropletenkaart, spreiding, meter, kaart, waterval.

## <a name="saving-changes-you-make-to-sort-order"></a>Wijzigingen opslaan die u aan de sorteervolgorde hebt aangebracht
Power BI-rapporten behouden de gemaakte wijzigingen in de filters, slicers, sorteervolgorde en gegevensweergave, ook al werkt u in de [leesweergave](end-user-reading-view.md). Als u dus weg navigeert van een rapport en later terugkeert, zijn uw wijzigingen voor sorteren opgeslagen.  Als u uw wijzigingen wilt terugzetten naar de instellingen van de *ontwerper* van het rapport, selecteert u **Standaardinstelling herstellen** in de bovenste menubalk. 

![Sorteervolgorde behouden](media/end-user-change-sort/power-bi-reset.png)

Als de knop **Standaardinstelling herstellen** echter in het grijs wordt weergegeven, heeft de *ontwerper* van het rapport de mogelijkheid om uw wijzigingen op te slaan (te behouden) uitgeschakeld.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

### <a name="sorting-using-other-criteria"></a>Sorteren op andere criteria
Af en toe wilt u de visual sorteren met behulp van een ander veld (Dat niet in de visual is opgenomen) of andere criteria.  Stel dat u sequentieel wilt sorteren op maand (en niet in alfabetische volgorde) of op gehele getallen in plaats van op cijfers (bijvoorbeeld op 0, 1, 9, 20 en niet op 0, 1, 20, 9).  

Alleen de persoon die het rapport heeft ontworpen, kan deze wijzigingen voor u aanbrengen. Contactinformatie voor de *ontwerper* vindt u door de naam van het rapport te selecteren in de balk met de koptekst.

Als u een *ontwerper* bent en beschikt over bewerkingsmachtigingen voor de inhoud, leest u [Sorteren op kolom in Power BI Desktop](../desktop-sort-by-column.md) voor meer informatie over het bijwerken van de gegevensset en het inschakelen van dit type sortering.

![Vervolgkeuzelijst met contactgegevens](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>Volgende stappen
Meer informatie over [visualisaties in Power BI-rapporten](end-user-visualizations.md) (Engelstalig).

[Power BI - basisconcepten](end-user-basic-concepts.md)
