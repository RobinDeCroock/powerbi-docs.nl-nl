---
title: Watervalgrafieken in Power BI
description: Watervalgrafieken in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/5/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6abca661a1553bfabc3da35fe714ff9bced5555a
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "74907622"
---
# <a name="waterfall-charts-in-power-bi"></a>Watervalgrafieken in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Watervalgrafieken tonen een voorlopig totaal terwijl Power BI nog bezig is met het optellen en aftrekken van waarden. Ze zijn handig om te begrijpen hoe een beginwaarde (bijvoorbeeld netto inkomsten) wordt beïnvloed door een reeks positieve en negatieve wijzigingen.

De kolommen worden met een kleur gecodeerd, zodat u toenames en afnames snel kunt overzien. De kolommen met de eerste en de uiteindelijke waarde [beginnen vaak op de horizontale as](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "beginnen op de horizontale as"), terwijl de tussenliggende waarden zwevende kolommen zijn. Vanwege deze speciale opmaak worden watervalgrafieken ook wel bruggrafieken genoemd.

   > [!NOTE]
   > Deze video maakt gebruik van een oudere versie van Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>Toepassingen voor een watervalgrafiek

In de volgende gevallen komen watervalgrafieken goed van pas:

* Wanneer er wijzigingen in de metingen zijn binnen een periode, reeks of verschillende categorieën.

* Om de belangrijkste wijzigingen te controleren die bijdragen aan de totaalwaarde.

* Om de jaarlijkse winst van uw bedrijf weer te geven door verschillende omzetbronnen te tonen en uiteindelijk bij de totale winst (of verlies) uit te komen.

* Om het aantal personeelsleden aan het begin en het einde van een jaar in beeld te brengen.

* Om te visualiseren hoeveel geld u elke maand verdient en uitgeeft, en het huidige saldo voor uw rekening.

## <a name="prerequisite"></a>Vereiste

In deze zelfstudie wordt gebruikgemaakt van het [PBIX-bestand met het voorbeeld van een retailanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Selecteer linksboven in de menubalk **Bestand** > **Openen**
   
2. Ga naar uw kopie van het **PBIX-bestand met het voorbeeld van een retailanalyse**

1. Open het **PBIX-bestand met het voorbeeld van een retailanalyse** in de rapportweergave ![Schermopname van het pictogram voor de rapportweergave.](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. Selecteren ![Schermopname van het gele tabblad.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) om een nieuwe pagina toe te voegen.


## <a name="create-a-waterfall-chart"></a>Een watervalgrafiek maken

U gaat een watervalgrafiek maken waarin de verkoopvariantie (geschatte omzet ten opzichte van werkelijke omzet) per maand wordt aangegeven.

### <a name="build-the-waterfall-chart"></a>De watervalgrafiek maken

1. In het deelvenster **Velden** selecteert u **Verkoop** > **Totale verkoopvariantie**.

   ![Schermopname met selectie van Verkoop > Totale verkoopvariantie en de visual die hieruit voortvloeit.](media/power-bi-visualization-waterfall-charts/power-bi-bar.png)

1. Selecteer het watervalpictogram ![Schermafbeelding van het watervalpictogram](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png)

    ![Visualisatiesjablonen](media/power-bi-visualization-waterfall-charts/convert-waterfall.png)

1. Selecteer **Tijd** > **Boekmaand** om het ook toe te voegen aan de groep **Categorie**.

    ![waterval](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-month.png)

### <a name="sort-the-waterfall-chart"></a>De watervalgrafiek sorteren

1. Zorg ervoor dat Power BI de watervalgrafiek chronologisch op maand sorteert. Selecteer **Meer opties** (...) in de rechterbovenhoek van de grafiek.

    Voor dit voorbeeld selecteert u **Sorteren op** en kiest u **Boekmaand**. Een gele indicator naast uw selectie geeft aan wanneer de selectieoptie wordt toegepast.

    ![Selecteer sorteren op > Boekmaand](media/power-bi-visualization-waterfall-charts/power-bi-sort-by-fiscalmonth.png)
    
    Als u de maanden in chronologische volgorde wilt weergeven, selecteert u **Oplopend sorteren**. Controleer net als bij de vorige stap of er links naast **Oplopend sorteren** een gele indicator wordt weergegeven. Dit geeft aan dat de geselecteerde optie wordt toegepast.

    ![Selecteer Sorteren op > Oplopende volgorde](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-ascending.png)

    

    U ziet dat uw grafiek van januari tot augustus is gesorteerd op Boekmaand.  

### <a name="explore-the-waterfall-chart"></a>De watervalgrafiek verkennen

Breid de grafiek iets uit om te zien welke staten per maand het meeste bijdragen aan de omzet.

1.  Selecteer **Winkel** > **Gebied**. Hierdoor wordt **Gebied** toegevoegd aan de bucket **Uitsplitsing**.

    ![Toont Store in groep Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI gebruikt de waarde in **Uitsplitsing** om extra gegevens aan de visualisatie toe te voegen. Hiermee worden de vijf inzenders toegevoegd die het meest bijdragen aan de toename of afname per boekmaand. Dit betekent bijvoorbeeld dat februari nu zes gegevenspunten bevat in plaats van slechts één.  

    ![Toont Store in groep Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-default.png)

    Stel dat u alleen geïnteresseerd bent in de twee belangrijkste inzenders.

1. Selecteer daarom **Uitsplitsing** in het deelvenster **Indeling** en zet **Maximumaantal uitsplitsingen** op **2**.

    ![Indeling > Uitsplitsing](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-two.png)

    We zien meteen dat de staten Ohio en Pennsylvania op dit moment de grootste bijdrage leveren aan de verkoopvariantie (zowel negatief als positief) in uw watervalgrafiek.

    ![watervalgrafiek](media/power-bi-visualization-waterfall-charts/power-bi-axis-waterfall.png)

## <a name="next-steps"></a>Volgende stappen

* [De interactie tussen visuele elementen in een Power BI-rapport wijzigen](../service-reports-visual-interactions.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
