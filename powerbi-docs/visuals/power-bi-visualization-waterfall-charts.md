---
title: Watervalgrafieken in Power BI
description: Watervalgrafieken in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67409055"
---
# <a name="waterfall-charts-in-power-bi"></a>Watervalgrafieken in Power BI

Watervalgrafieken tonen een voorlopig totaal terwijl Power BI nog bezig is met het optellen en aftrekken van waarden. Ze zijn handig om te begrijpen hoe een beginwaarde (bijvoorbeeld netto inkomsten) wordt beïnvloed door een reeks positieve en negatieve wijzigingen.

De kolommen worden met een kleur gecodeerd, zodat u toenames en afnames snel kunt overzien. De kolommen met de eerste en de uiteindelijke waarde beginnen vaak [op de horizontale as](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "op de horizontale as"), terwijl de tussenliggende waarden zwevende kolommen zijn. Vanwege deze speciale opmaak worden watervalgrafieken ook wel bruggrafieken genoemd.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Toepassingen voor een watervalgrafiek

In de volgende gevallen komen watervalgrafieken goed van pas:

* Wanneer er wijzigingen in de metingen zijn binnen een periode, reeks of verschillende categorieën.

* Om de belangrijkste wijzigingen te controleren die bijdragen aan de totaalwaarde.

* Om de jaarlijkse winst van uw bedrijf weer te geven door verschillende omzetbronnen te tonen en uiteindelijk bij de totale winst (of verlies) uit te komen.

* Om het aantal personeelsleden aan het begin en het einde van een jaar in beeld te brengen.

* Om te visualiseren hoeveel geld u elke maand verdient en uitgeeft, en het huidige saldo voor uw rekening.

## <a name="prerequisites"></a>Vereisten

* De Power BI-service of Power BI Desktop

* Het rapport Voorbeeld van een retailanalyse

## <a name="get-the-retail-analysis-sample-report"></a>Het rapport Voorbeeld van een retailanalyse downloaden

In deze instructies wordt het voorbeeld van een retailanalyse gebruikt. Voor het maken van een visualisatie hebt u bewerkmachtigingen voor de gegevensset en het rapport nodig. De voorbeelden van Power Bi zijn allemaal bewerkbaar. Als iemand een rapport met u deelt, kunt u geen visualisaties maken in het rapport. Als u mee wilt doen, downloadt u het rapport [Voorbeeld van een retailanalyse](../sample-datasets.md).

Nadat u de gegevensset **Voorbeeld van een retailanalyse** hebt opgehaald, kunt u aan de slag.

## <a name="create-a-waterfall-chart"></a>Een watervalgrafiek maken

U gaat een watervalgrafiek maken waarin de verkoopvariantie (geschatte omzet ten opzichte van werkelijke omzet) per maand wordt aangegeven.

1. Ga naar **Mijn werkruimte** en selecteer **Gegevenssets** > **Een rapport maken**.

    ![Schermopname van Gegevenssets > Een rapport maken.](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. In het deelvenster **Velden** selecteert u **Verkoop** > **Totale verkoopvariantie**.

   ![Screenshot met selectie van Verkoop > Totale verkoopvariantie en het visuele element dat hieruit voortvloeit.](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. Selecteer het watervalpictogram ![Schermafbeelding van het watervalpictogram](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) om de grafiek te converteren naar een treemap.

    Als **Totale verkoopvariantie** zich niet in het gebied van de **Y-as** bevindt, sleept u het daarnaartoe.

    ![Visualisatiesjablonen](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. Selecteer **Tijd** > **Boekmaand** om het ook toe te voegen aan de groep **Categorie**.

    ![waterval](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Zorg ervoor dat Power BI de watervalgrafiek chronologisch heeft gesorteerd. Selecteer het beletselteken (...) in de rechterbovenhoek van de grafiek.

    Controleer of er een gele indicator links naast de opties  **Oplopend sorteren** en **Boekmaand** staat.

    ![Selecteer sorteren op > Boekmaand](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    U kunt ook de X-aswaarden bekijken en zien dat ze in de volgorde van **Jan** tot en met **Aug** staan.

    Breid de grafiek iets uit om te zien welke staten per maand het meeste bijdragen aan de omzet.

1. Sleep **Store** > **Territory** naar de groep **Uitsplitsing**.

    ![Toont Store in groep Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Standaard voegt Power BI de vijf inzenders toe die het meest bijdragen aan de toename of afname per maand.

    ![Toont Store in groep Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    Nu bent u echter alleen geïnteresseerd in de twee belangrijkste inzenders.

1. Selecteer daarom **Uitsplitsing** in het deelvenster **Indeling** en zet **Maximumaantal uitsplitsingen** op **2**.

    ![Indeling > Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    We zien meteen dat de staten Ohio en Pennsylvania op dit moment de grootste bijdrage leveren aan de verkoopvariantie (zowel negatief als positief) in uw watervalgrafiek.

    ![watervalgrafiek](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    Dat is een interessant gegeven. Hebben Ohio en Pennsylvania zo'n grote invloed omdat de verkopen in deze twee staten veel hoger zijn dan in de andere staten? Dat kunt u uiteraard controleren.

1. Maak een kaart waarop de verkoop per territorium voor dit jaar en vorig jaar worden weergegeven.

    ![close-up kaart op PA en Ohio](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    De kaart bevestigt onze theorie. Duidelijk wordt dat deze twee staten zowel vorig jaar (belgrootte) als dit jaar (belarcering) het hoogste omzetcijfer hadden.

## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren

Zie **Filter aan een rapport toevoegen** voor meer informatie over het gebruik van het deelvenster [Filters](../power-bi-report-add-filter.md).

Wanneer u een kolom in een watervalgrafiek markeert, worden de andere visualisaties op de rapportpagina kruislings gefilterd en vice versa. De kolom **Totaal** kan hiervoor overigens niet worden gebruikt.

## <a name="next-steps"></a>Volgende stappen

* [De interactie tussen visuele elementen in een Power BI-rapport wijzigen](../service-reports-visual-interactions.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
