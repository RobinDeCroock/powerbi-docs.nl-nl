---
title: Gebruik de functie Analyseren om schommelingen in rapportvisuals te verklaren
description: Eenvoudig inzichten verkrijgen in toenames of afnames in Power BI-service
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/12/2020
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: fe44b183b77cb1e58c89cfd229f3f76d3b06ce39
ms.sourcegitcommit: 3268a9b630cf599c50592d83c70a87eeecf7838f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "88168458"
---
# <a name="use-the-analyze-feature-to-explain-fluctuations-in-report-visuals"></a>Gebruik de functie Analyseren om schommelingen in rapportvisuals te verklaren

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

In rapportvisuals ziet u vaak een grote toename, gevolgd door flink afgenomen waarden. Vraagt u zich ook wel eens af waardoor deze schommelingen worden veroorzaakt? Met **Analyseren** in **de Power BI-service** kunt u met slechts enkele klikken de oorzaak van het probleem achterhalen.

Kijk eens naar de volgende visual. Hierin wordt *Totaal eenheden* per *Maand* en *Fabrikant* weergegeven. VanArsdel doet het beter dan de concurrenten, maar geeft in juni 2014 een forse dip te zien. In dergelijke gevallen kunt u de gegevens verkennen om te achterhalen wat er is veranderd. 

![Visual met toenamen en afnamen](media/end-user-analyze-visuals/power-bi-line-chart.png)

U kunt in Power BI-service vragen om toenames, afnames of ongewone distributies in visuals te verklaren en een snelle, geautomatiseerde, inzichtelijke analyse over uw gegevens te krijgen. Klik met de rechtermuisknop op een gegevenspunt en selecteer **Analyseren > Leg de afname uit** (toename, als de vorige staaf lager is) of **Analyseren > Zoeken waar de distributie verschilt**. U krijgt het inzicht te zien in een gebruiksvriendelijk venster.

![Inzichten in een visual](media/end-user-analyze-visuals/power-bi-decrease.png)

De functie Analyseren is contextueel en gebaseerd op het gegevenspunt dat er onmiddellijk aan vooraf gaat, zoals de vorige staaf of kolom.

> [!NOTE]
> De functie is een preview-versie en kan nog worden gewijzigd. De inzichtfunctie is standaard ingeschakeld (u hoeft geen preview-vak aan te vinken om de functie in te schakelen).

### <a name="which-factors-and-categories-are-chosen"></a>Welke factoren en categorieën worden gekozen?

Na onderzoek van verschillende kolommen selecteert en toont Power BI de factoren die de grootste verandering in de relatieve bijdrage laten zien. Bij elke kolom worden de waarden met de grootste verandering in de bijdrage benoemd in de beschrijving. Daarnaast worden de waarden benoemd met de grootste daadwerkelijke toename en afname.

Gebruik de schuifbalk om alle inzichten weer te geven die door Power BI zijn gegenereerd. De volgorde wordt zodanig gerangschikt dat de belangrijkste bijdrager als eerste wordt weergegeven. 

## <a name="using-insights"></a>Inzichten gebruiken
Klik met de rechtermuisknop op een gegevenspunt in een staaf- of lijndiagram en selecteer **Analyseren** om inzicht te krijgen in trends die in visuals zichtbaar zijn. Kies vervolgens de optie die wordt weergegeven: **Leg de toename uit**, **Leg de afname uit** of **Leg het verschil uit**.

Vervolgens worden de gegevens met machine-learningalgoritmen geanalyseerd en wordt in een venster een visual en een beschrijving weergegeven. Hieraan ziet u welke categorieën de meeste invloed hebben gehad op de toename, afname of het verschil.  In dit voorbeeld is het eerste inzicht een watervalgrafiek.

![pop-upvenster met inzichten](media/end-user-analyze-visuals/power-bi-insight.png)

Als u de kleine pictogrammen onder aan de waterval selecteert, kunt u ervoor kiezen of in de inzichten een spreidingsdiagram, een gestapeld kolomdiagram of lintdiagram wordt weergegeven.

![drie visuals met inzichten](media/end-user-analyze-visuals/power-bi-options.png)

Gebruik de pictogrammen met *duim omhoog* of *duim omlaag* boven aan de pagina om feedback te geven over de visual en de functie.  

![pictogrammen duim omhoog en duim omlaag](media/end-user-analyze-visuals/power-bi-thumbs.png)


U kunt inzichten gebruiken als uw rapport in lees- of bewerkweergave is. U kunt er dan gegevens mee analyseren en visuals mee maken die u makkelijk aan uw rapporten kunt toevoegen. Als u het rapport in de bewerkweergave hebt geopend, ziet u een pictogram met plusteken naast de duimpictogrammen. Selecteer het pluspictogram om het inzicht aan uw rapport toe te voegen als een nieuwe visual. 

![drie visuals met inzichten](media/end-user-analyze-visuals/power-bi-add-visual.png)

## <a name="details-of-the-results-returned"></a>Details van de geretourneerde resultaten

De informatie die wordt geretourneerd door de inzichten is bedoeld om aan te geven wat het verschil was tussen twee perioden.  

Het algoritme bekijkt als het ware alle kolommen in het model en berekent het verschil in de kolommen *vóór* en *na* een bepaald punt. Op die manier wordt bepaald hoeveel verandering er is geweest; de kolommen met de grootste verandering worden geretourneerd. Zo is bijvoorbeeld *Staat* geselecteerd in de watervalgrafiek, omdat de bijdrage van Louisiana, Texas en Colorado in juni en juli met 13% is afgenomen tot 19%. Dit was de grootste bijdrage tot de afname in *Totaal eenheden*.  

Voor elk geretourneerd inzicht kunnen er vier visuals worden weergegeven. Drie van die visuals zijn bedoeld om de verandering in de bijdrage tussen de twee perioden aan te tonen. Hiermee kunt u bijvoorbeeld zien wat de oorzaak was van de stijging tussen *kwartaal 2* en *kwartaal 3*. In het lintdiagram wordt de verandering zowel voor als na het geselecteerde gegevenspunt weergegeven.

### <a name="the-scatter-plot"></a>Het spreidingsplot

![Kleine schermopname met het geselecteerde spreidingsplotpictogram](media/end-user-analyze-visuals/power-bi-scatter-icon.png)

In de visual met het spreidingsplot ziet u de waarde van de meting in de eerste periode (op de x-as) in combinatie met de waarde van de meting in de tweede periode (op de y-as) voor alle waarden in de kolom (*Staat* in dit geval). Gegevenspunten bevinden zich in de groene regio als ze zijn toegenomen en in de rode regio als ze zijn afgenomen. 

De stippellijn is de best passende lijn door de punten. De gegevenspunten boven deze lijn zijn toenames boven de trend en de punten eronder afnames.  

![Spreidingsplot met stippellijn](media/end-user-analyze-visuals/power-bi-scatter.png)

De gegevensitems zonder waarde voor beide perioden worden niet weergegeven in het spreidingsplot.

### <a name="the-100-stacked-column-chart"></a>De 100% gestapelde kolomdiagram

![Kleine schermopname met het geselecteerde kolomdiagrampictogram](media/end-user-analyze-visuals/power-bi-column-icon.png)

Het 100% gestapelde kolomdiagram toont de waarde van de bijdrage aan het totaal (100%) voor het geselecteerde gegevenspunt en het vorige punt. Hierdoor kunnen de bijdragen van alle gegevenspunten met elkaar worden vergeleken. In dit voorbeeld wordt de feitelijke bijdrage voor de geselecteerde waarde voor Texas weergegeven in de knopinfo. Aangezien de lijst met staten lang is, kan door middel van knopinfo de details worden bekeken. In de knopinfo ziet u dat Texas met ongeveer hetzelfde percentage heeft bijgedragen tot Totaal eenheden (31% en 32%), maar dat het werkelijk aantal Totaal eenheden is gedaald van 89 tot 71. Langs de y-as wordt een percentage afgezet, geen totaal, en elke kolom geeft een percentage weer, geen waarde. 

![100% gestapelde kolomdiagram](media/end-user-analyze-visuals/power-bi-stacked.png)

### <a name="the-ribbon-chart"></a>De lintgrafiek

![Kleine schermopname met het geselecteerde lintgrafiekpictogram](media/end-user-analyze-visuals/power-bi-ribbon-icon.png)

In de visual met de lintgrafiek ziet u de waarde van de meting vóór en na een specifiek punt. Het is vooral handig bij het weergeven van de veranderingen in bijdragen wanneer de *volgorde* van de inzenders verandert (bijvoorbeeld *LA* is gezakt van plaats twee naar elf).  En hoewel *TX* wordt voorgesteld door een breed lint aan de bovenkant, waarmee wordt aangegeven dat het vóór en na de belangrijkste bijdrager is, laat de afname zien dat de waarde van de bijdrage tijdens de geselecteerde periode en daarna is afgenomen.

![lintgrafiek](media/end-user-analyze-visuals/power-bi-ribbon-tooltip.png)

### <a name="the-waterfall-chart"></a>De watervalgrafiek

![Kleine schermopname met het geselecteerde watervalgrafiekpictogram](media/end-user-analyze-visuals/power-bi-waterfall-icon.png)

De vierde visual is een watervalgrafiek, met daarin de daadwerkelijke toename of afname in een bepaalde periode. Deze visual laat één belangrijke bijdrager zien tot de afname voor juni 2014 - in dit geval **Staat**. En het bijzondere van de invloed van **Staat** op het totale aantal eenheden is dat afnames in Louisiana, Texas en Colorado de belangrijkste rol hebben gespeeld.      

![watervalgrafiek](media/end-user-analyze-visuals/power-bi-insight.png)


 



## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
Deze inzichten zijn gebaseerd op de wijziging vanaf het voorgaande gegevenspunt. Ze zijn dus niet beschikbaar als u het eerste gegevenspunt in een visual selecteert. 

**Analyseren** is niet beschikbaar voor alle typen visuals. 

In de volgende lijst vindt u een aantal scenario's die momenteel niet worden ondersteund voor **Analyseren: toename/afname/verschil verklaren**:

* TopN-filters
* Opname-/uitsluitingsfilters
* Maateenheidfilters
* Niet-numerieke metingen
* Het gebruik van Waarde weergeven als
* Gefilterde metingen: met gefilterde metingen voert u berekeningen op visueel niveau uit, waarbij een specifiek filter wordt toegepast (bijvoorbeeld *Total Sales for France*). Deze metingen worden gebruikt voor enkele van de visuals die met de inzichtenfunctie zijn gemaakt
* Categorische kolommen op de X-as, tenzij er een scalaire kolomsortering wordt gedefinieerd. Als er een hiërarchie wordt gebruikt, moet elke kolom in de actieve hiërarchie aan deze voorwaarde voldoen


## <a name="next-steps"></a>Volgende stappen
[Watervalgrafieken](../visuals/power-bi-visualization-waterfall-charts.md)    
[Spreidingsdiagrammen](../visuals/power-bi-visualization-scatter.md)    
[Kolomdiagrammen](../visuals/power-bi-report-visualizations.md)    
[Lintgrafieken](../visuals/desktop-ribbon-charts.md)
