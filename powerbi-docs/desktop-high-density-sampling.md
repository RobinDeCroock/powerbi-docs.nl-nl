---
title: High-Densitysampling in Power BI
description: High-Densitysampling in Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 357611d36fd59be1b674f06ce72c5aba8d020822
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454339"
---
# <a name="high-density-line-sampling-in-power-bi"></a>High-densitysampling in Power BI
Sinds de release in juni 2017 van **Power BI Desktop** en updates voor de **Power BI-service** is er een nieuw samplingalgoritme beschikbaar waarmee visuals worden verbeterd die high-densitygegevens verzamelen. U kunt bijvoorbeeld een lijndiagram maken op basis van de verkoopresultaten van uw winkels, waarbij elke winkel jaarlijks meer dan tienduizend verkoopontvangsten genereert. Een lijndiagram van dergelijke verkoopcijfers zou sample van gegevens (Selecteer een zinvolle representatie van alle gegevens, te laten zien hoe de verkoop gedurende een periode variëren) van de gegevens voor elke winkel en maakt u een lijndiagram met meerdere reeksen dat op die manier de onderliggende gegevens. Dit is gebruikelijk bij het visualiseren van high-densitygegevens. In Power BI Desktop is de sampling van high-densitygegevens verbeterd, zoals nader beschreven in dit artikel.

![](media/desktop-high-density-sampling/high-density-sampling_01.png)

> [!NOTE]
> Het **high-densitysampling**-algoritme dat in dit artikel wordt beschreven, is beschikbaar in zowel **Power BI Desktop** als de **Power BI-service**.

## <a name="how-high-density-line-sampling-works"></a>Hoe High regel werkt steekproeven
Voorheen selecteerde **Power BI** op deterministische wijze een sample van gegevenspunten in het volledige bereik van onderliggende gegevens. Voor high-densitygegevens in een visual die één jaar bestrijkt, kunnen er in de visual bijvoorbeeld 350 sample-gegevenspunten worden weergegeven, die allemaal zijn geselecteerd om te controleren of het volledige gegevensbereik (de totale reeks onderliggende gegevens) in de visual is weergegeven. Om te begrijpen hoe dit gebeurt, stel een aandelenkoers uitzet gedurende een periode van één jaar en 365 gegevenspunten te maken van een lijndiagram visual (met één gegevenspunt voor elke dag) te selecteren.

In dat geval zijn er elke dag veel waarden voor een aandelenkoers. Er is natuurlijk een dagelijkse hoogste en laagste koers, maar die kunnen zich op elk moment van de dag voordoen wanneer de beurs geopend is. Als bij high-densitysampling van lijnen de onderliggende gegevenssample elke dag is genomen om 10.30 uur en 24.00 uur, ontstaat er een representatieve momentopname van de onderliggende gegevens (de koers op 10.30 uur en 24.00 uur), maar daarmee worden mogelijk niet de werkelijke hoogste en laagste koers voor dat representatieve gegevenspunt (voor die dag) vastgelegd. In situaties als deze vertegenwoordigt de sample de onderliggende gegevens, maar daarin zijn niet altijd de belangrijke punten opgenomen, in dit geval de hoogste en laagste dagkoers.

High-densitygegevens worden per definitie verzameld om redelijk snel visualisaties te maken die responsief zijn voor op interactiviteit. Door te veel gegevenspunten op een visual kan de snelheid omlaag gaan. Bovendien kan dit afbreuk doen aan de zichtbaarheid van de trends. De manier waarop dergelijke gegevens worden verzameld, is bepalend voor het samenstellen van het samplingalgoritme om de best mogelijke visualisatie te bieden. In Power BI Desktop is het algoritme nu verbeterd om de best mogelijke combinatie van reactievermogen, weergave en behoud van belangrijke punten in elke periode te bieden.

## <a name="how-the-new-line-sampling-algorithm-works"></a>De werking van het nieuwe samplingalgoritme voor lijnen
Het nieuwe algoritme voor high-densitysampling van lijnen is beschikbaar voor visuals met lijn- en vlakdiagrammen met een doorlopende x-as.

Voor een High, **Power BI** densityvisual uw gegevens in segmenten van hoge resolutie en kiest belangrijke punten om elk segment vertegenwoordigt. Dat proces van het splitsen van gegevens met hoge resolutie is specifiek is afgestemd op om ervoor te zorgen dat het resulterende diagram is visueel niet te onderscheiden van de weergave van alle van de onderliggende gegevenspunten, maar veel sneller en interactiever.

### <a name="minimum-and-maximum-values-for-high-density-line-visuals"></a>Minimale en maximale waarden voor visuals met lijn met hoge dichtheid
Voor een bepaalde visualisatie gelden de volgende beperkingen:

* Ongeacht het aantal onderliggende gegevenspunten of -reeksen is **3500** het maximumaantal gegevenspunten dat in de visual wordt *weergegeven* (zie de *uitzonderingen* in de volgende lijsten met opsommingstekens). Als er 10 reeksen met 350 gegevenspunten elk zijn, heeft de visual het maximumaantal gegevenspunten bereikt. Als u één reeks hebt, kan deze maximaal 3500 gegevenspunten bevatten als het nieuwe algoritme dit als de beste sampling voor de onderliggende gegevens beoordeelt.

* Er geldt een maximum van **60 reeksen** voor een visual. Als er meer dan 60 reeksen zijn, splitst u de gegevens op en maakt u meerdere visuals met elk 60 of minder reeksen. Het is raadzaam om een **slicer** te gebruiken om alleen de segmenten van de gegevens weer te geven (alleen bepaalde reeksen). Als u bijvoorbeeld alle subcategorieën in de legenda weergeeft, kunt u met een slicer filteren op de algehele categorie op dezelfde rapportpagina.

Het maximumaantal gegevenslimieten is hoger voor de volgende typen visuele elementen, die *uitzonderingen* vormen op de gegevenslimiet van 3500 gegevenspunten:

* maximaal **150.000** gegevenspunten voor R-visuals;
* **30.000** gegevenspunten voor aangepaste visuele elementen;
* **10.000** gegevenspunten voor spreidingsdiagrammen (voor spreidingsdiagrammen is de standaard 3500);
* **3500** voor alle andere visuele elementen.

Deze parameters zorgen ervoor dat visuals in Power BI Desktop zeer snel worden weergegeven, reageren op interactie door gebruikers en niet leiden tot onnodige verwerkingsoverhead op de computer die de visual genereert.

### <a name="evaluating-representative-data-points-for-high-density-line-visuals"></a>Representatieve gegevenspunten voor visuals met lijn met hoge dichtheid beoordelen
Wanneer het aantal onderliggende gegevenspunten het maximum aantal gegevenspunten overschrijdt dat in de visual kan worden weergegeven, begint een zogeheten *binning*-proces, dat de onderliggende gegevens opsplitst in groepen die *bins* worden genoemd, waarna deze bins regelmatig worden verfijnd.

Het algoritme maakt zo veel mogelijk bins om de grootst mogelijke granulariteit voor de visual te realiseren. Het algoritme zoekt binnen elke bin naar de minimale en maximale gegevenswaarde om ervoor te zorgen dat belangrijke en significante waarden (zoals uitschieters) worden vastgelegd en weergegeven in de visual. Op basis van de resultaten van de binning en de daaropvolgende evaluatie van de gegevens door Power BI, wordt de minimale resolutie voor de x-as van de visual bepaald, om voor een maximale granulariteit voor de visual te zorgen.

Zoals eerder is vermeld, is de minimale granulariteit voor elke reeks 350 punten, het maximum is 3500 voor de meeste visuele elementen, waarbij de *uitzonderingen* worden vermeld in de vorige alinea's.

Elke bin wordt weergegeven door twee gegevenspunten, die de representatieve gegevenspunten van de bin in de visual worden. De gegevenspunten zijn simpelweg de hoogste en laagste waarde voor die bin, en door die hoogste en laagste waarde te selecteren zorgt het binning-proces ervoor dat elke belangrijke hoogste waarde, of significante laagste waarde, wordt vastgelegd en weergegeven in de visual.

Als u denkt dat dit een hoop analysewerk betekent om er zeker van te zijn dat een incidentele uitschieter wordt vastgelegd en correct wordt weergegeven in de visual, dan klopt dat inderdaad. Dit is echter ook de reden voor het nieuwe algoritme en binning-proces.

## <a name="tooltips-and-high-density-line-sampling"></a>ToolTips en High-densitysampling
Het is belangrijk te weten dat dit binning-proces, dat de minimum- en maximumwaarde oplevert in een vastgelegde en weergegeven bin, van invloed kan zijn op de manier waarop gegevens worden weergegeven in de tooltips wanneer u de muisaanwijzer boven de gegevenspunten houdt. Voor een uitleg over hoe en waarom dat gebeurt, gaan we terug naar ons voorbeeld over aandelenkoersen.

Stel dat u maakt een visual op basis van aandelenkoersen en u vergelijkt twee verschillende aandelen, die beide gebruikmaken **High-Density steekproeven**. De onderliggende gegevens voor elke reeks bevatten veel gegevenspunten (mogelijk omdat u aandelenkoersen elke seconde van de dag hebt vastgelegd). Het algoritme voor high-densitysampling van lijnen voert voor elke afzonderlijke reeks binning uit.

Stel nu dat de koers van het eerste aandeel om 12:02 uur omhoog gaat en tien seconden later meteen weer omlaag duikt. Dat is een belangrijk gegevenspunt. Wanneer er voor dat aandeel binning wordt uitgevoerd, wordt de hoge waarde om 12:02 uur een representatief gegevenspunt voor die bin.

Voor het tweede aandeel was er echter noch een hoge, noch een lage waarde die de tijd bevatte voor de bin die plaatsvond om 12:02. Mogelijk vond de hoge en lage waarde voor de bin die plaatsvond om 12:02 drie minuten later plaats. Wanneer in dat geval het lijndiagram wordt gemaakt en u de muisaanwijzer boven 12:02 houdt, ziet u een waarde in de tooltip voor het eerste aandeel (omdat dit aandeel om 12:02 omhoog ging en die waarde werd geselecteerd als hoogste gegevenspunt voor die bin), maar ziet u *geen* enkele waarde in de tooltip van 12:02 voor het tweede aandeel. Dat komt doordat het tweede aandeel noch een hoge, noch een lage waarde voor de bin had die plaatsvond om 12:02. Er zijn om 12:02 dus geen gegevens om weer te geven voor het tweede aandeel en daarom worden er geen tooltipgegevens weergegeven.

Dat gebeurt vaker met tooltips. De hoge en lage waarden voor een bepaalde bin komen wellicht niet volledig overeen met de waardepunten op de gelijkmatig geschaalde x-as, waardoor de tooltip de waarde niet laat zien.  

## <a name="how-to-turn-on-high-density-line-sampling"></a>Het inschakelen van high-densitysampling
Het nieuwe algoritme is standaard **ingeschakeld**. Als u wilt deze instelling wijzigen, gaat u naar de **opmaak** deelvenster in de **algemene** kaart, en langs de onderkant, ziet u de schuifregelaar **High-Density steekproeven**. U schakelt de schuifregelaar uit door deze op **Uit** te zetten.

![](media/desktop-high-density-sampling/high-density-sampling_02.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
Het nieuwe algoritme voor high-densitysampling van lijnen is een belangrijke verbetering in Power BI, maar er zijn wel enkele zaken waarmee u rekening moet houden wanneer u werkt met high-densitywaarden en -gegevens.

* Vanwege toegenomen granulariteit en het binning-proces geven **tooltips** mogelijk alleen een waarde weer als de representatieve gegevens worden uitgelijnd met uw muisaanwijzer. Zie de *Tooltips en High-densitysampling* sectie in dit artikel voor meer informatie.
* Wanneer een algemene gegevensbron te groot is, elimineert het nieuwe algoritme reeksen (legenda-elementen) op basis van het maximum voor het importeren van gegevens.
  
  * In dit geval rangschikt het nieuwe algoritme legendareeksen op alfabet, begint het de lijst met legenda-elementen in alfabetische volgorde af te werken totdat het maximum voor gegevensimport is bereikt en er geen verdere reeksen meer worden geïmporteerd.
* Wanneer een onderliggende gegevensset meer dan 60 reeksen heeft (het maximumaantal reeksen, zoals eerder beschreven), rangschikt het nieuwe algoritme de reeksen op alfabet en worden alle reeksen boven de 60e reeks die alfabetisch is gerangschikt, verwijderd.
* Als de waarden in de gegevens niet van het type *numeriek* of *datum/tijd* zijn, maakt Power BI geen gebruik van het nieuwe algoritme en wordt het vorige (niet-high-densitysampling)-algoritme gebruikt.
* De instelling **Items zonder gegevens weergeven** wordt niet ondersteund door het nieuwe algoritme.
* Het nieuwe algoritme wordt niet ondersteund bij gebruik van een live-verbinding met een model dat wordt gehost in SQL Server Analysis Services (versie 2016 of lager). Het wordt wel ondersteund in modellen die worden gehost in **Power BI** of Azure Analysis Services.

## <a name="next-steps"></a>Volgende stappen
Zie het volgende artikel voor informatie over high-densitysampling in spreidingsdiagrammen.

* [High-densitysampling in Power BI-spreidingsdiagrammen](desktop-high-density-scatter-charts.md)

