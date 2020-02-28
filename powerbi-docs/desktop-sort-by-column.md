---
title: Op kolom sorteren in Power BI Desktop
description: U kunt in Power BI de weergave van een visueel element wijzigen door deze op andere gegevensvelden te sorteren.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 0cbba86bd77debda9ab2162b8f9b190e1846b99c
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464646"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Op kolom sorteren in Power BI Desktop
In Power BI Desktop en de Power BI-service kunt u de weergave van een visueel element wijzigen door deze op andere gegevensvelden te sorteren. Als u de sortering van een visual wijzigt, kunt u de informatie markeren die u wilt overbrengen en ervoor zorgen dat de visual de trend (of de nadruk) weergeeft.

Of u nu numerieke gegevens (zoals verkoopcijfers) of tekstgegevens (zoals provincienamen) gebruikt, u kunt uw visualisaties sorteren en ze eruit laten zien zoals u wilt. Power BI biedt veel flexibiliteit voor sorteren en snelle menu's die u kunt gebruiken. Als u visuals wilt selecteren, selecteert u het menu **Meer opties** (...), selecteert u **Sorteren op** en selecteert u vervolgens het veld waarop u wilt sorteren.

![Het menu Meer opties](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>Voorbeeld van sorteren
We gebruiken een voorbeeld met meer diepgang en bekijken hoe dit werkt in Power BI Desktop.

De volgende visualisatie toont kosten, hoeveelheden en bedragen op naam van de fabrikant. De visualisatie ziet er als volgt uit voordat we verder gaan sorteren:

![Initiële visualisatie](media/desktop-sort-by-column/sortbycolumn_1.png)

De visual is momenteel gesorteerd op de kolom **SalesQuantity**. We kunnen de sorteerkolom bepalen door de kleur van de oplopende balken te vergelijken met de legenda, maar er is een betere manier: het menu **Meer opties**, dat u kunt openen door de beletseltekens (...) te selecteren.

![Het menu Meer opties](media/desktop-sort-by-column/sortbycolumn_2.png)

Dit zijn de sorteerselecties:

* Het huidige sorteerveld is **SalesQuantity**, wat wordt aangegeven doordat **SalesQuantity** vetgedrukt is en wordt voorafgegaan door een gele balk. 

* De huidige sorteerrichting is oplopend, zoals wordt aangegeven doordat **Oplopend sorteren** vetgedrukt is en wordt voorafgegaan door een gele balk.

We kijken naar het sorteerveld en de sorteerrichting in de volgende twee gedeelten.

## <a name="select-which-column-to-use-for-sorting"></a>Selecteren welke kolom moet worden gebruikt voor het sorteren
U hebt de gele balk voor **SalesQuantity** in het menu **Meer opties** zien staan; deze geeft aan dat de visual wordt gesorteerd op de kolom **SalesQuantity**. Sorteren op een andere kolom is heel eenvoudig: selecteer de beletseltekens (...) om het menu **Meer opties** weer te geven, selecteer **Sorteren op** en selecteer vervolgens een andere kolom.

In de volgende afbeelding selecteren we **DiscountAmount** als de kolom waarop we willen sorteren. Deze kolom lijkt meer op een van de lijnen op de visual, dan op een van de balken. 

![Sorteren op DiscountAmount](media/desktop-sort-by-column/sortbycolumn_3.png)

U ziet hoe het visuele element is gewijzigd. De waarden worden nu gerangschikt van de hoogste waarde voor **DiscountAmount**, Fabrikam Inc., naar de laagste, Northwind Traders. 

Maar wat moeten we doen als we de staten oplopend willen sorteren, in plaats van aflopend? In de volgende sectie wordt beschreven hoe gemakkelijk u dit kunt doen.

## <a name="select-the-sort-order"></a>De sorteervolgorde selecteren
Wanneer we het menu **Meer opties** in de vorige afbeelding wat nader bekijken, zien we dat **Aflopend sorteren** vet wordt weergegeven en wordt voorafgegaan door een gele balk.

![Van grootste naar kleinste sorteren](media/desktop-sort-by-column/sortbycolumn_4.png)

Wanneer **Aflopend sorteren** is geselecteerd, betekent dit dat de visual die is gesorteerd op de geselecteerde kolom wordt weergegeven van de hoogste naar laagste waarde. Wilt u dit wijzigen? Geen probleem. Selecteer **Oplopend sorteren** en de sorteervolgorde van de geselecteerde kolom wordt gewijzigd van kleinste naar grootste waarde.

Hier ziet u dezelfde visual, nadat u de volgorde van **DiscountAmount** hebt gewijzigd. U ziet dat Northwind Traders nu de eerste fabrikant in de lijst is en dat Fabrikam Inc. de laatste in de lijst, de tegenovergestelde sorteervolgorde als eerst.

![Van kleinste naar grootste sorteren](media/desktop-sort-by-column/sortbycolumn_5.png)

U kunt sorteren op elke kolom die is opgenomen in de visual; we hadden heel eenvoudig **SalesQuantity** kunnen selecteren als de kolom waarop we willen sorteren, om de fabrikanten die het meeste hebben verkocht als eerste weer te geven. Hierbij kunnen we de andere kolommen in de visual behouden, omdat deze van toepassing zijn op die fabrikant. Hier ziet u de visual met deze instellingen:

![Sorteren op SalesQuantity](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>Sorteren met de knop Sorteren op kolom
Er is een andere manier om uw gegevens te sorteren, namelijk met behulp van de knop **Sorteren op kolom** in het lint **Modelleren**.

![De knop Sorteren op kolom](media/desktop-sort-by-column/sortbycolumn_8.png)

Als u deze aanpak voor het sorteren gebruikt, selecteert u eerst de kolom (veld) om te sorteren in het deelvenster **Velden** en vervolgens **Modelleren** > **Sorteren op kolom** om uw visual te sorteren. Als u geen kolom selecteert, is de knop **Op kolom sorteren** niet actief.

Laten we een veelvoorkomend voorbeeld bekijken. U hebt gegevens van elke maand van het jaar en u wilt ze sorteren op chronologische volgorde. U doet dit met de volgende stappen:

1. U ziet dat de knop **Sorteren op kolom** inactief is (lichter gekleurd) wanneer de visual is geselecteerd, maar er is geen kolom geselecteerd in het deelvenster **Velden**.
   
   ![Inactieve knop Sorteren op kolom](media/desktop-sort-by-column/sortbycolumn_9.png)

2. Wanneer we de kolom selecteren waarop we wilt sorteren in het deelvenster **Velden**, wordt de knop **Sorteren op kolom** geactiveerd.
   
   ![Actieve knop Sorteren op kolom](media/desktop-sort-by-column/sortbycolumn_10.png)
3. Nu de visual is geselecteerd, kunnen we **MonthOfYear** selecteren, in plaats van de standaardoptie **MonthName**. De visual wordt gesorteerd in de volgorde die we willen: op de maand van het jaar.
   
   ![Het menu Sorteren op kolom](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Drillthrough voor meerdere rapporten gebruiken in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Slicers in Power BI](visuals/power-bi-visualization-slicers.md)

