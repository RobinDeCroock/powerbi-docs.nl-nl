---
title: Visualtypen in Power BI voor consumenten
description: Visualtypen in Power BI-service
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 6fd970064bbe686a433fba0c0675948576edd8c1
ms.sourcegitcommit: 0ae9328e7b35799d5d9613a6d79d2f86f53d9ab0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76039083"
---
# <a name="visual-types-in-power-bi"></a>Visualtypen in Power BI
U vindt visuals in rapporten, dashboards en Q&A. Sommige van deze visualtypen zijn verpakt met Power BI en sommige zijn *aangepaste visuals*. Aangepaste visuals worden gemaakt buiten Power BI en op een manier die het voor *rapportontwerpers* mogelijk maakt om deze aan Power BI-rapporten en dashboards toe te voegen. 

Dit artikel vormt een overzicht van de visuals die zijn verpakt met de Power BI-service.  Dit zijn de visuals die u het vaakst tegenkomt. Raadpleeg de documentatie van de [Power BI-rapport*ontwerper* over visualtypen](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) voor uitgebreide informatie over alle visuals

> [!NOTE]
> Zoek voor meer informatie over aangepaste visualisaties in de sectie **Visuele Power BI-elementen** van [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Van elk visuele element vindt u een beschrijving, auteursgegevens, en schermafdrukken of een video. 

## <a name="list-of-visuals-available-in-power-bi"></a>Lijst van visuals die beschikbaar zijn in Power BI
Al deze visuals kunnen worden gevonden in Power BI-dashboards en -rapporten en zijn [opgegeven in Q&A](end-user-q-and-a.md). Zie [Interactie met visuals in rapporten, dashboards en apps](end-user-visualizations.md) voor meer informatie over de interactie met visuals

### <a name="area-charts-basic-layered-and-stacked"></a>Vlakdiagrammen: eenvoudig (lagen) en gestapeld
![vlakdiagram](media/end-user-visual-type/basic-area-map-small.png)

Het eenvoudige vlakdiagram is gebaseerd op het lijndiagram waarbij het gebied tussen de as en de lijn wordt gevuld. Vlakdiagrammen benadrukken de mate van wijzigingen in de loop van de tijd en kunnen worden gebruikt om de aandacht te vestigen op de totale waarde voor een trend. Gegevens die bijvoorbeeld de winst in de loop van de tijd voorstellen, kunnen worden afgezet in een vlakdiagram om de totale winst te benadrukken.

### <a name="bar-and-column-charts"></a>Staaf- en kolomdiagrammen
![kolomdiagram](media/end-user-visual-type/pbi-nancy-viz-bar.png)

 ![staafdiagram](media/end-user-visual-type/pbi-nancy-viz-col.png)

Staafdiagrammen zijn de standaard als u een specifieke waarde over verschillende categorieën wilt weergeven.

### <a name="cards-single-number"></a>Kaarten: één getal
![kaart met één getal](media/end-user-visual-type/pbi-nancy-viz-card.png)

Kaarten met één getal geven één feit weer, één gegevenspunt. Soms is één getal het belangrijkste dat u wilt bijhouden op uw Power BI-dashboard of -rapport, zoals de totale omzet, het marktaandeel jaar na jaar of het totale aantal verkoopkansen.  

### <a name="cards-multi-row"></a>Kaarten: met meerdere rijen
![kaart met meerdere rijen](media/end-user-visual-type/multi-row-card.png)

Kaarten met meerdere rijen geven een of meer gegevenspunten weer, één per rij.


### <a name="combo-charts"></a>Combinatiegrafieken
![combinatiegrafiek](media/end-user-visual-type/combo-small.png)

Een combinatiegrafiek combineert een kolomdiagram en een lijndiagram. Als u deze twee diagrammen combineert, kunt u de gegevens sneller vergelijken. Combinatiegrafieken kunnen over één of twee Y-assen beschikken, dus zorg ervoor dat u hier goed op let. 

In de volgende gevallen komen combinatiegrafieken goed van pas:
- Als u hebt een lijndiagram en een kolomdiagram met dezelfde X-as hebt.
- Als u meerdere metingen met verschillende waardebereiken wilt vergelijken.
- Als u het verband tussen twee metingen wilt illustreren in één visual
- Als u wilt controleren of één meting voldoet aan het doel dat is gedefinieerd via een andere meting
- Als u ruimte op het canvas wilt besparen.

### <a name="doughnut-charts"></a>Ringdiagrammen
![ringdiagram](media/end-user-visual-type/donut-small.png)

Ringdiagrammen lijken op cirkeldiagrammen.  Ze geven het verband weer tussen delen en het geheel. Het enige verschil is dat het midden leeg is, waardoor er ruimte is voor een label of pictogram.

### <a name="funnel-charts"></a>Trechterdiagrammen
![trechterdiagram](media/end-user-visual-type/pbi-nancy-viz-funnel.png)

Trechters helpen bij het visualiseren van een proces dat bestaat uit fasen en waarbij items achter elkaar van de ene naar de volgende fase stromen.  Een voorbeeld hiervan is een verkoopproces dat begint met potentiële klanten en eindigt met de afhandeling van de aankoop.

Bijvoorbeeld verkoopactiviteiten waarbij de klanten in bepaalde fasen worden bijgehouden: Lead > Gekwalificeerde Lead > Potentiële klant > Contract > Sluiten. De vorm van de trechter brengt de status van het proces dat u bijhoudt in één oogopslag over.
Elke fase van de trechter vertegenwoordigt een percentage van het totaal. In de meeste gevallen heeft een trechterdiagram dus de vorm een trechter. De eerste fase is het grootst en elke latere fase is kleiner dan de vorige. Een trechter in de vorm van een peer is ook nuttig. Hiermee kunt u een probleem in het proces identificeren. Maar normaal gesproken is de eerste fase (de startfase) het grootst.


### <a name="gauge-charts"></a>Meterdiagrammen
![meterdiagram](media/end-user-visual-type/gauge-m.png)

Een radiale-meterdiagram heeft een cirkelvormige boog en toont één waarde die de voortgang naar een doel/KPI meet. Het doel of de doelwaarde wordt weergegeven door de lijn (naald). De voortgang naar het doel wordt weergegeven door de arcering. En de waarde die de voortgang vertegenwoordigt, wordt vetgedrukt weergegeven in de boog. Alle mogelijke waarden zijn gelijkmatig verdeeld langs de boog, van minimum (meest linkse waarde) tot maximum (meest rechtse waarde).

In het bovenstaande voorbeeld zijn we een autohandelaar die de gemiddelde verkoop van het verkoopteam per maand bijhoudt. Ons doel is 140 en dat wordt weergegeven door de zwarte naald. De minimale mogelijke gemiddelde verkoop is ingesteld op 0 en we hebben het maximum ingesteld op 200. De blauwe arcering geeft aan dat we deze maand momenteel ongeveer 120 verkopen gemiddeld hebben. Gelukkig hebben we nog een week de tijd om ons doel te bereiken.

Radiale meters zijn een uitstekende keuze om:
- de voortgang naar een doel weer te geven
- een percentielmeting weer te geven, zoals een KPI
- de status van één meting weer te geven
- informatie weer te geven die snel kan worden gelezen en begrepen

 ### <a name="key-influencers-chart"></a>Grafiek met belangrijkste beïnvloeders
![belangrijkste beïnvloeder](media/end-user-visual-type/power-bi-influencer.png)

Een grafiek met belangrijkste beïnvloeders toont de grote bijdragers aan een geselecteerd resultaat of geselecteerde waarde.

Belangrijkste beïnvloeders zijn een goede keuze om inzicht te krijgen in de factoren die van invloed zijn op een belangrijke metrische waarde. Bijvoorbeeld *wat zijn de invloeden waardoor klanten een tweede order hebben geplaatst*of*waarom was afgelopen juni de verkoop zo hoog*. 

### <a name="kpis"></a>KPI's
![kpi](media/end-user-visual-type/power-bi-kpi.png)

Een Key Performance Indicator (KPI) is een visuele aanwijzing waarmee de voortgang naar een meetbaar doel wordt aangegeven. 

KPI's zijn een prima keuze:
- voor het meten van voortgang (waarmee loop ik voor of achter?)
- voor het meten van de afstand tot een doel (hoe ver loop ik voor of achter?)

### <a name="line-charts"></a>Lijndiagrammen
![lijndiagram](media/end-user-visual-type/pbi-nancy-viz-line.png)

Lijndiagrammen benadrukken de algehele vorm van een volledige reeks waarden, meestal in de loop van de tijd.

### <a name="maps-basic-maps"></a>Kaarten: basiskaarten
![basiskaart](media/end-user-visual-type/pbi-nancy-viz-map.png)

Gebruik een basiskaart om categorische en kwantitatieve gegevens te koppelen aan ruimtelijke locaties.

### <a name="maps-arcgis-maps"></a>Kaarten: ArcGIS-kaarten
![ArcGis-kaart](media/end-user-visual-type/power-bi-esri-map-theme2.png)

De combinatie van ArcGIS-kaarten en Power BI tilt kaarten naar een volledig nieuw niveau, verder dan de presentatie van punten op een kaart. Met de beschikbare opties voor basiskaarten, locatietypen, thema's, symboolstijlen en referentielagen worden prachtige informatieve visuals van de kaart gemaakt. De combinatie van bindende gegevenslagen (zoals censusgegevens) op een kaart met ruimtelijke analyse geeft meer inzicht in de gegevens van uw visual.

### <a name="maps-filled-maps-choropleth"></a>Kaarten: Choropletenkaarten
![choropletenkaart](media/end-user-visual-type/pbi-nancy-viz-filledmap.png)

In een choropletenkaart worden arcering, tinten of patronen gebruikt om aan te geven hoe een waarde in verhouding verschilt voor een geografisch gebied of regio. U kunt zo snel deze relatieve verschillen laten zien met behulp van arcering die varieert van licht (minder frequent/lager) tot donker (meer-frequent/hoger).

### <a name="maps-shape-maps"></a>Kaarten: Shape-kaarten
![shape-kaart](media/end-user-visual-type/power-bi-shape-map2.png)

Met shape-kaarten kunt u op een kaart regio's met elkaar vergelijken met behulp van een kleur. Een shape-kaart kan geen nauwkeurige geografische locaties van gegevenspunten op een kaart weergeven. Het belangrijkste doel ervan is om relatieve vergelijkingen van regio's aan te geven op een kaart door verschillende kleuren te gebruiken.

### <a name="matrix"></a>Matrix
![matrix](media/end-user-visual-type/matrix.png)

De matrixvisualisatie is een type tabelvisualisatie (Zie 'Tabel' hieronder) die ondersteuning biedt voor een indeling met interval. Rapportontwerpers nemen vaak matrices op in rapporten en dashboards waarmee gebruikers een of meer element (rijen, kolommen, cellen) in de matrix kunnen selecteren voor het kruislings markeren van andere visuele elementen op een rapportpagina.  

### <a name="pie-charts"></a>Cirkeldiagrammen
![cirkeldiagram](media/end-user-visual-type/pbi-nancy-viz-pie.png)

Cirkeldiagrammen geven het verband weer tussen delen en het geheel. 

### <a name="power-apps-visual"></a>Power Apps-visual
![Power Apps-visual](media/end-user-visual-type/power-bi-powerapps-visual.png)

Rapportontwerpers kunnen een Power-app maken en deze insluiten in een Power BI-rapport. Gebruikers kunnen met deze visual werken in het Power BI-rapport. 

### <a name="qa-visual"></a>Q&A - visual
![Q&A-visuals](media/end-user-visual-type/power-bi-q-and-a.png)

>[!TIP]
>De Q&A-visual is vergelijkbaar met de [Q&A-ervaring op dashboards](../power-bi-tutorial-q-and-a.md) en biedt u de mogelijkheid om in natuurlijke taal vragen te stellen over uw gegevens. 

Zie [Q&A-visual in Power BI](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md) voor meer informatie.

### <a name="ribbon-chart"></a>Lintgrafiek
![lintgrafiek](media/end-user-visual-type/power-bi-ribbon.png)

Lintgrafieken geven aan welke gegevenscategorie de hoogste rang (hoogste waarde) heeft. In lintgrafieken kunnen wijzigingen in de rang goed worden weergegeven, waarbij voor elke periode de hoogste rang (waarde) altijd bovenaan wordt weergegeven.

### <a name="scatter-bubble-and-dot-plot-charts"></a>Spreidings-, bellen- en eendimensionale puntdiagrammen


Een spreidingsdiagram heeft altijd twee waardeassen, waarbij een reeks numerieke gegevens op een horizontale as en een andere reeks numerieke waarden op de verticale as wordt weergegeven. In het diagram worden punten weergegeven op het snijpunt van een numerieke x- en y-waarde, waarbij deze waarden in één gegevenspunt worden gecombineerd. Deze gegevenspunten kunnen, afhankelijk van de gegevens, gelijkmatig of ongelijkmatig over de horizontale as zijn verdeeld.

![bellendiagram](media/end-user-visual-type/pbi-nancy-viz-bubble.png)

Bij een bellendiagram worden de gegevenspunten vervangen door bellen. De grootte van de bellen geeft de gegevens een extra dimensie.



Een eendimensionaal puntdiagram lijkt erg op een bellendiagram en een spreidingsdiagram, behalve dat er numerieke of categorische gegevens langs de X-as geplaatst kunnen worden. In dit voorbeeld wordt gebruikgemaakt van vierkanten in plaats van cirkels en wordt de verkoop op de X-as getekend.

![eendimensionaal puntdiagram](media/end-user-visual-type/power-bi-dot-plot-squares.png)

### <a name="scatter-high-density"></a>High-densityspreiding
![High-densityspreiding](media/end-user-visual-type/density-scatter.png)

High-densitygegevens worden per definitie verzameld om redelijk snel visuals te maken die responsief zijn op interactiviteit. High-densitysampling maakt gebruik van een algoritme dat overlappende punten elimineert en zorgt ervoor dat alle punten in de gegevensset worden weergegeven in de visualisatie. Er wordt niet alleen een representatieve steekproef van de gegevens geplot.  

Dit zorgt voor de best mogelijke combinatie van reactievermogen, weergave en behoud van belangrijke punten in de algehele gegevensset te bieden.

### <a name="slicers"></a>Slicers
![slicer](media/end-user-visual-type/pbi-slicer.png)

Een slicer is een zelfstandig diagram dat kan worden gebruikt voor het filteren van de andere visualisaties op de pagina. Slicers zijn verkrijgbaar in veel verschillende indelingen (categorie, bereik, datum, enzovoort) en kunnen zo worden geformatteerd dat selectie van slechts één, veel of alle van de beschikbare waarden mogelijk is. 

In de volgende gevallen komen slicers goed van pas:
- als u veelgebruikte of belangrijke filters op het rapportcanvas wilt weergeven voor een eenvoudigere toegang;
- als u de huidige gefilterde status gemakkelijker wilt bekijken zonder dat u een vervolgkeuzelijst hoeft te openen;
- als u wilt filteren op kolommen die niet nodig zijn en verborgen zitten in de gegevenstabellen;
- als u meer gerichte rapporten wilt maken door slicers naast belangrijke visuele elementen te zetten.

### <a name="standalone-images"></a>Zelfstandige afbeeldingen
![zelfstandige afbeelding](media/end-user-visual-type/pbi-nancy-viz-image.png)

Een zelfstandige afbeelding is een afbeelding die is toegevoegd aan een rapport of dashboard. 


### <a name="tables"></a>Tabellen
![tabeldiagram](media/end-user-visual-type/table-type.png)

Een tabel is een raster met gerelateerde gegevens in een logische reeks rijen en kolommen. Het kan ook koppen en een rij voor totalen bevatten. Tabellen werken goed met kwantitatieve vergelijkingen waarbij u veel waarden voor één categorie bekijkt. Deze tabel geeft bijvoorbeeld vijf verschillende eenheden voor Categorie weer.

Tabellen zijn een prima keuze:
- om gedetailleerde gegevens en exacte waarden (in plaats van visuele weergaven) te bekijken en vergelijken;
- om gegevens weer te gegeven in tabelvorm;
- om numerieke gegevens per categorie weer te geven.

### <a name="treemaps"></a>Treemaps
![treemap-diagram](media/end-user-visual-type/pbi-nancy-viz-tree.png)

Treemaps zijn diagrammen van gekleurde rechthoeken waarbij de grootte de waarde aangeeft.  Ze kunnen hiërarchisch zijn waarbij kleinere rechthoeken zijn genest binnen de grootste rechthoeken. De ruimte in elke rechthoek wordt toegewezen op basis van de waarde die wordt gemeten. En de rechthoeken zijn gerangschikt op grootte van linksboven (grootste) naar rechtsonder (kleinste).

In de volgende gevallen komen treemaps goed van pas:
- wanneer u grote hoeveelheden hiërarchische gegevens moet weergeven;
- wanneer een staafdiagram het grote aantal waarden niet effectief kan verwerken;
- wanneer u de verhoudingen tussen de verschillende en het geheel wilt weergeven;
- wanneer u het patroon van de distributie van de meting tussen de verschillende niveaus van categorieën in de hiërarchie wilt weergeven;
- wanneer u kenmerken wilt weergeven met grootte- en kleurcoderingen;
- wanneer u patronen, uitbijters, de belangrijkste bijdragers en uitzonderingen wilt identificeren.

### <a name="waterfall-charts"></a>Watervalgrafieken
![watervalgrafiek](media/end-user-visual-type/waterfall-small.png)

Een watervalgrafiek toont een voorlopig totaal terwijl waarden worden toegevoegd of afgetrokken. Dit is handig om te begrijpen hoe een beginwaarde (bijvoorbeeld netto inkomsten) wordt beïnvloed door een reeks positieve en negatieve wijzigingen.

De kolommen worden met een kleur gecodeerd, zodat u snel toenames en afnames kunt zien. De kolommen met de eerste en de uiteindelijke waarde beginnen vaak op de horizontale as, terwijl de tussenliggende waarden zwevende kolommen zijn. Vanwege dit 'uiterlijk' worden watervalgrafieken ook wel bruggrafieken genoemd.

In de volgende gevallen komen watervalgrafieken goed van pas:
- wanneer er wijzigingen voor de meting zijn over tijd of over verschillende categorieën
- om de belangrijkste wijzigingen te controleren die bijdragen aan de totaalwaarde
- om de jaarlijkse winst van uw bedrijf uit te zetten door verschillende bronnen van omzet weer te geven en uiteindelijk bij de totale winst (of verlies) uit te komen.
- om het aantal personeelsleden aan het begin en het einde van een jaar in beeld te brengen
- om te visualiseren hoeveel geld u elke maand verdient en uitgeeft, en het huidige saldo voor uw rekening

## <a name="qna"></a>Aangeven welke visual Q&A moet gebruiken
Wanneer u query's in natuurlijke taal typt met Power BI Q&A, kunt u het type visual in uw query opgeven.  Bijvoorbeeld:


'***verkoop per staat als treemap***'

![Q&A-sessie](media/end-user-visual-type/qa-treemap.png)

## <a name="next-steps"></a>Volgende stappen
[Werken met visuals in rapporten, dashboards en apps](end-user-visualizations.md)    
[The right visual reference van sqlbi.com](https://www.sqlbi.com/wp-content/uploads/videotrainings/dashboarddesign/visuals-reference-may2017-A3.pdf)
