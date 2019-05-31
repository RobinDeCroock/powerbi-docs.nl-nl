---
title: Combinatiegrafieken in Power BI
description: In deze zelfstudie over combinatiegrafieken wordt uitgelegd wanneer u ze kunt gebruiken en hoe u in Power BI-service en Power BI Desktop kunt bouwen.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e461480f53f4a97aeb4282e64a8a03eb8e1418d1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187841"
---
# <a name="combo-chart-in-power-bi"></a>Combinatiegrafieken in Power BI
Een combinatiegrafiek in Power BI is een visualisatie waarin een lijndiagram wordt gecombineerd met een kolomdiagram. Als u deze twee diagrammen combineert, kunt u de gegevens sneller vergelijken.

Combinatiegrafieken kunnen één of twee Y-assen bevatten.

## <a name="when-to-use-a-combo-chart"></a>Wanneer gebruikt u een combinatiegrafiek?
In de volgende gevallen komen combinatiegrafieken goed van pas:

* Als u hebt een lijndiagram en een kolomdiagram met dezelfde X-as hebt.
* Als u meerdere metingen met verschillende waardebereiken wilt vergelijken.
* Als u het verband tussen twee metingen wilt illustreren in één visualisatie.
* Als u wilt controleren of één meting voldoet aan het doel dat is gedefinieerd door een andere meting.
* Als u ruimte op het canvas wilt besparen.

### <a name="prerequisites"></a>Vereisten
Combinatiegrafieken zijn beschikbaar in de Power BI-service en Power BI Desktop. Deze zelfstudie maakt gebruik van Power BI-service om een combinatiegrafiek te maken. Als u deze wilt volgen, opent u Power BI-service en maakt u verbinding met de [onderstaande instructies](#create) voor het voorbeeld van een retailanalyse).


## <a name="create-a-basic-single-axis-combo-chart"></a>Een eenvoudige combinatiegrafiek met één as maken
Kijk hoe Will een combinatiegrafiek maakt op basis van het voorbeeld van verkoop en marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a> Als u uw eigen combinatiegrafiek wilt maken, meldt u zich aan bij Power BI-service en selecteert u **Gegevens ophalen \> Voorbeelden \> Voorbeeld van een retailanalyse > Verbinding maken > Naar dashboard gaan**.

1. Selecteer op het dashboard Voorbeeld van een retailanalyse de tegel **Totaal aantal winkels** om het rapport Voorbeeld van een retailanalyse te openen.
2. Selecteer **Rapport bewerken** om het rapport in de bewerkingsweergave te openen.
3. Voeg een nieuwe rapportpagina toe.
4. Maak een kolomdiagram waarin de omzet voor dit jaar en de brutomarge marge per maand wordt weergegeven.

    a.  Selecteer in het deelvenster Velden achtereenvolgens **Verkoop** \> **Omzet dit jaar** > **Waarde**.

    b.  Sleep **Verkoop** \> **Brutomarge dit jaar** naar de bron **Waarde**.

    c. Selecteer **Tijd** \> **FiscalMonth** om deze waarde toe te voegen aan de bron **As**.

    ![](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Selecteer het beletselteken (...) in de rechterbovenhoek van de visualisatie en selecteer **Sorteren op > FiscalMonth**. Als u de sorteervolgorde wilt wijzigen, selecteert u het beletselteken opnieuw en kiest u **Oplopend sorteren** of **Aflopend sorteren**.

6. Converteer de kolomdiagram naar een combinatiegrafiek. Er zijn twee combinatiegrafieken beschikbaar: **Lijndiagram en gestapelde kolomdiagram** en **Lijndiagram en gegroepeerde kolomdiagram**. Selecteer de kolomdiagram en selecteer vervolgens in het deelvenster **Visualisaties** de optie **Lijndiagram en gegroepeerd kolomdiagram**.

    ![](media/power-bi-visualization-combo-chart/converttocombo_new2.png)
7. Ga naar het deelvenster **Velden** en sleep **Verkoop** \> **Omzet van afgelopen jaar** naar de bucket **Regelwaarden**.

   ![](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   Uw combinatiegrafiek moet er ongeveer als volgt uitzien:

   ![](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Een combinatiegrafiek met twee assen maken
In deze taak vergelijken we de brutomarge en de omzet.

1. Maak een nieuw lijndiagram waarin wordt bijgehouden **% van de brutomarge vorig jaar** door **FiscalMonth**. Selecteer het beletselteken om te sorteren per **Maand** en **Oplopend**.  
In januari was de brutomarge 35%, in april nemen we een piek (45%) waar, in juli daalde het brutomargepercentage en in augustus was er opnieuw een daling. Krijgen we een soortgelijk patroon voor afgelopen jaar en dit jaar te zien?

   ![](media/power-bi-visualization-combo-chart/combo1_new.png)
2. Voeg **Omzet van dit jaar > Waarde** en **Omzet van afgelopen jaar** aan het lijndiagram toe. De schaal van de **procentuele brutomarge vorig jaar** is veel kleiner is dan de schaal van **Verkoop**, waardoor het lastig is om de waarden te vergelijken.      

   ![](media/power-bi-visualization-combo-chart/flatline_new.png)
3. Converteer het lijndiagram naar een Lijndiagram en gestapeld kolomdiagram, zodat de visualisatie eenvoudiger te lezen en te interpreteren is.

   ![](media/power-bi-visualization-combo-chart/converttocombo_new.png)
4. Sleep **Brutomarge% vorig jaar** van **Kolomwaarden** naar **Lijnwaarden**. In Power BI worden twee assen gemaakt, zodat de gegevenssets verschillend kunnen worden geschaald. Aan de linkerkant verkopen in dollars en aan de rechterkant in percentages. En we zien het antwoord op onze vraag: ja, het patroon is vergelijkbaar.

   ![](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Titels toevoegen aan de assen
1. Selecteer het pictogram met de verfroller ![](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) om het opmaakvenster te openen.
2. Selecteer de pijl-omlaag om de **Y-as** uit te breiden.
3. Voor **y-as (kolom)** , stel **positie** naar **links**, stel **titel** naar **op**,  **Stijl** naar **alleen titel weergeven**, en **weergave-eenheden** als **miljoenen**.

   ![](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. Onder **y-as (kolom)** , schuif omlaag totdat u ziet **secundaire weergeven**. Omdat er heel veel opties voor de Y-as, mogelijk hebt u beide schuifbalken. De tweede sectie tonen weergegeven opties voor de opmaak van de regel diagram-gedeelte van de combinatiegrafiek.

   ![](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Voor **Y-as (regel)** laat u **Positie** ingesteld staan op **Rechts**, stelt u **Titel** in op **Aan** en stelt u voor **Stijl** de optie **Alleen titel weergeven** in.

   Uw combinatiegrafiek bevat nu twee assen, beide met titels.

   ![](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

6. Wijzig desgewenst het lettertype, grootte en kleur en stel de overige opmaakopties zo in dat de weergave en leesbaarheid van de grafiek wordt verbeterd.

U kunt nu het volgende doen:

* [De combinatiegrafiek toevoegen als dashboardtegel](../service-dashboard-tiles.md).
* [Sla het rapport op](../service-report-save.md).
* [Het rapport toegankelijker maken voor mensen met beperkingen](../desktop-accessibility.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Kruislings markeren en kruislings filteren

Wanneer u een kolom of regel in een combinatiegrafiek markeert, worden de andere visualisaties op de rapportpagina kruislings gemarkeerd en gefilterd, en omgekeerd. U kunt deze standaardwerking wijzigen met behulp van het besturingselement [Visuele interactie](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Volgende stappen

[Ringdiagrammen in Power BI](power-bi-visualization-doughnut-charts.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
