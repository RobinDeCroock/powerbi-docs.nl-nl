---
title: Eigenschappen van X-as en Y-as aanpassen
description: Eigenschappen van X-as en Y-as aanpassen
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bfe84acdf73fcb5ace791c9a84943262d0f73ab
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390239"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>Eigenschappen van X-as en Y-as aanpassen

In deze zelfstudie leert u veel verschillende manieren om de X-as en Y-as van uw visualisaties aan te passen. Niet alle visualisaties hebben assen. Cirkeldiagrammen hebben bijvoorbeeld geen assen. Daarnaast verschillen de aanpassingsopties per visualisatie. Aangezien de mogelijkheden te groot zijn om in één artikel te behandelen, bekijken we een aantal van de meestgebruikte as-aanpassingen en maken we u vertrouwd met het tabblad **Indeling** voor de opmaak van visualisaties in het rapportcanvas van Power BI.  

> [!NOTE]
> Deze pagina is van toepassing op zowel de Power BI-service als Power BI Desktop. Deze aanpassingen komen beschikbaar wanneer u het pictogram **Indeling** (de verfroller ![ Schermopname van verfrollerpictogram.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) selecteert en zijn ook beschikbaar in Power BI Desktop.

Kijk hoe Amanda de X- en Y-assen aanpast. Ze laat zien hoe u op verschillende manieren de samenvoeging kunt regelen wanneer u gaat inzoomen of uitzoomen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>Vereisten

- De Power BI service

- Het rapport Voorbeeld van een retailanalyse

## <a name="customize-visualization-x--and-y-axes-in-reports"></a>X- en Y-assen van visualisaties aanpassen in rapporten

Als u mee wilt doen, meld u zich aan bij de [Power BI-service](https://app.powerbi.com) en opent u het rapport [Voorbeeld van een retailanalyse](../sample-datasets.md) in de weergave [Rapport bewerken](../service-interact-with-a-report-in-editing-view.md).

### <a name="create-a-stacked-column-chart-visualization"></a>Een visualisatie met een gestapeld kolomdiagram maken

Voordat u een visualisatie kunt aanpassen, zult u deze moeten bouwen.

1. Vouw in de Power BI-service **Mijn werkruimte** uit.

1. Scrol omlaag en selecteer **Retail Analysis Sample** in de lijst **Gegevenssets**.

1. Selecteer in het deelvenster **Visualisaties** het pictogram Gestapeld kolomdiagram.

    ![Schermopname van het deelvenster Visualisaties en een leeg gestapeld kolomdiagram](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stacked-column-chart.png)

1. Als u de waarden voor de X-as wilt instellen, selecteert u **Time** > **FiscalMonth** in het deelvenster **Velden**.

1. Als u de waarden voor de Y-as wilt instellen, selecteert u **Sales** > **Last Year Sales** en **Sales** > **This Year Sales** > **Value** in het deelvenster **Fields**.

    ![Schermopname van een ingevuld gestapeld kolomdiagram](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

### <a name="customize-the-x-axis"></a>De X-as aanpassen

Nu kunt u de X-as gaan aanpassen.

1. Selecteer in het deelvenster **Visualisaties** het pictogram **Indeling** (het pictogram van een verfroller ![Schermopname van het verfrollerpictogram.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) om de aanpassingsopties weer te geven.

1. Vouw de X-as-opties uit.

   ![Schermopname van de opties voor de X-as.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)

1. Verplaats de schuifregelaar **X-as** naar **Aan**.

    ![Schermopname van de schuifregelaar bij Aan.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Een reden waarom u mogelijk de X-as zou willen uitschakelen, is om ruimte te maken voor meer gegevens.

1. Maak de kleur, de grootte en het lettertype van de tekst op:

    - **Kleur**: selecteer zwart

    - **Tekengrootte**: voer *14* in

    - **Lettertypefamilie**: selecteer **Arial Black**

1. Zet de schuifregelaar **Titel** op **Aan** om de naam van de X-as weer te geven. In dit geval is dat **FiscalMonth**.

1. Maak de kleur, de grootte en het lettertype van de titeltekst op:

    - **Titelkleur**: selecteer oranje

    - **Astitel**: voer *Fiscal Month* in

    - **Tekengrootte titel**: voer *21* in

Als u klaar bent met de aanpassingen, ziet het gestapelde kolomdiagram er ongeveer zo uit:

![Schermopname van het aangepaste gestapelde kolomdiagram](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **X-as**.

### <a name="customize-the-y-axis"></a>De Y-as aanpassen

Vervolgens gaat u de Y-as aanpassen.

1. Vouw de Y-as-opties uit.

   ![Schermopname van de opties voor de Y-as.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

1. Zet de schuifregelaar **Y-as** op **Aan**.  

    ![Schermopname van de schuifregelaar bij Aan.](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Een reden waarom u mogelijk de Y-as zou willen uitschakelen, is om ruimte te maken voor meer gegevens.

1. Selecteer voor **Positie** de optie **Rechts**.

1. Maak de kleur, de grootte en het lettertype van de tekst op:

    - **Kleur**: selecteer zwart

    - **Tekengrootte**: voer *14* in

    - **Lettertypefamilie**: selecteer **Arial Black**

1. Stel **Weergave-eenheden** in op **Miljoenen** en **Decimaalposities voor de waarden** op *0*.

1. Deze visualisatie wordt er niet beter op als we een titel gebruiken voor de Y-as, dus laten we **Titel** op **Uit** staan.  

1. We laten de rasterlijnen opvallen door de kleur te wijzigen en de streek dikker te maken:

    - **Kleur**: selecteer donkergrijs

    - **Streekdikte**: voer *2* in

Na al deze aanpassingen zou uw kolomdiagram er ongeveer als volgt moeten uitzien:

![Schermopname van het diagram met de aangepaste Y-as.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>Visualisaties met twee Y-assen aanpassen

Eerst maakt u een combinatiegrafiek waarmee u de impact kunt bekijken die het aantal winkels heeft op de verkoop. Dit is dezelfde grafiek die we hebben gemaakt in de [zelfstudie over combinatiegrafieken](power-bi-visualization-combo-chart.md). Vervolgens gaat u de twee Y-assen opmaken.

### <a name="create-a-chart-with-two-y-axes"></a>Een grafiek met twee Y-assen maken

1. Maak een nieuw lijndiagram waarin de **Sales (Verkoop) > Gross Margin last year % (Brutomarge% vorig jaar)** per **Time (Tijd) > FiscalMonth (Boekmaand)** wordt bijgehouden.

    ![Schermopname van het nieuwe lijndiagram.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [!NOTE]
    > Zie [Sorteren op andere criteria](../consumer/end-user-change-sort.md#other) voor hulp bij het sorteren op maand.

    In januari bedroeg de brutomarge 35%, met daarna een piek van 45% in april, een lichte terugval in juli en opnieuw een piek in augustus. Krijgen we een soortgelijk patroon voor afgelopen jaar en dit jaar te zien?

1. Voeg **Omzet van dit jaar > Waarde** en **Omzet van afgelopen jaar** aan het lijndiagram toe.

    ![Schermopname van het lijndiagram met de nieuwe gegevens toegevoegd.](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

    De schaal van **Gross Margin Last Year %** (de blauwe lijn die langs de rasterlijn **0M%** loopt) is veel kleiner dan de schaal van **Sales**, waardoor het lastig is om een vergelijking te maken. Een de percentages in de labels op de Y-as zijn absurd.

1. U kunt de visualisatie makkelijker te lezen en te interpreteren maken door het lijndiagram te converteren naar een lijndiagram met een gestapeld kolomdiagram.

   ![Schermopname van het deelvenster Visualisaties met het pictogram Lijndiagram en gestapeld kolomdiagram omkaderd.](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

1. Sleep **Brutomarge% vorig jaar** van **Kolomwaarden** naar **Lijnwaarden**.

    ![Schermopname van het lijndiagram met een gestapeld kolomdiagram met alle drie de waarden duidelijk voorgesteld.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

    U hebt nu het gestapelde kolomdiagram dat u in de eerste sectie hebt gemaakt, met een lijndiagram dat eroverheen is gelegd. Gebruik eventueel wat u hierboven hebt geleerd om de kleur en tekengrootte van de assen op te maken.

   ![Schermopname van het aangepaste lijndiagram met gestapeld kolomdiagram](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

   Power BI maakt twee assen, waardoor de schaal van de gegevenssets afzonderlijk van elkaar kan worden ingesteld. Op de linkeras wordt de verkoop aangegeven in dollars en op de rechteras in percentages.

### <a name="format-the-secondary-y-axis"></a>De secundaire Y-as opmaken

1. Selecteer het verfrollerpictogram in het deelvenster **Visualisaties** om de opmaakopties weer te geven.

1. Vouw de Y-as-opties uit.

1. Scrol omlaag totdat u de optie **Secundaire weergeven** ziet. Controleer of deze op **Aan** staat.

   ![Schermopname van de optie Secundaire weergeven.](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

1. (Optioneel) Pas de twee assen aan. Als u de **Positie** voor de kolomas of de lijnas verwisselt, wisselen de twee assen van kant.

### <a name="add-titles-to-both-axes"></a>Voeg titels toe aan beide assen

In het geval van een visualisatie die zo ingewikkeld is, kan het zinvol zijn om astitels toe te voegen.  Titels helpen uw collega's om het verhaal te begrijpen dat u met uw visualisatie wilt vertellen.

1. Zet de **Titel** op **Aan** voor **Y-as (kolom)** en de **Y-as (rij)** .

1. Stel **Stijl** in op **Alleen titel weergeven** voor beide assen.

   ![Schermopname van de opties voor titel en stijl.](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)

1. In uw combinatiegrafiek worden nu twee assen weergegeven, beide met titels.

   ![Schermopname van de aangepaste grafiek met dubbele Y-assen.](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

Zie [Tips en trucs voor het gebruik van kleuren in Power BI](service-tips-and-tricks-for-color-formatting.md) voor meer informatie.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

Als de X-as door de eigenaar van het rapport wordt gecategoriseerd als een gegevenstype, wordt de optie **Type** weergegeven en kunt u kiezen tussen doorlopend of categorisch.

## <a name="next-steps"></a>Volgende stappen

- [Visualisaties in Power BI-rapporten](power-bi-report-visualizations.md)

- [Titels, legenda's en achtergronden van visualisaties aanpassen](power-bi-visualization-customize-title-background-and-legend.md)

- [Aan de slag met de kleuropmaak en de eigenschappen van assen](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Basisconcepten voor gebruikers van de Power BI-service](../consumer/end-user-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
