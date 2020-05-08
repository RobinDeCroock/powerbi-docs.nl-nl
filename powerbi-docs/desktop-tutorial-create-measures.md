---
title: 'Zelfstudie: Uw eigen metingen maken in Power BI Desktop'
description: Metingen in Power BI Desktop helpen u bij het uitvoeren van berekeningen op gegevens tijdens het werken met rapporten.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 0d2b316b53b4107c86a036cc8a436440dd8bd674
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "74311529"
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Zelfstudie: Uw eigen metingen maken in Power BI Desktop
Met behulp van metingen kunt u in Power BI Desktop zeer krachtige gegevensanalyseoplossingen maken. Metingen helpen u bij het uitvoeren van berekeningen op gegevens tijdens het werken met rapporten. Deze zelfstudie bevat uitleg over metingen en een stapsgewijze procedure voor het maken van een aantal basismetingen in Power BI Desktop.

## <a name="prerequisites"></a>Vereisten

- Deze zelfstudie is bedoeld voor Power BI-gebruikers die al bekend zijn met het gebruik van Power BI Desktop en eraan toe zijn om geavanceerdere modellen te maken. U dient al te weten hoe u Gegevens ophalen en Query-editor gebruikt om gegevens te importeren, hoe u werkt met meerdere verwante tabellen en hoe u velden toevoegt aan het rapportcanvas. Raadpleeg [Aan de slag met Power BI Desktop](desktop-getting-started.md) als u nog geen ervaring hebt met het gebruik van Power BI Desktop.
  
- In deze zelfstudie wordt het bestand [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip) gebruikt, waarin online verkoopgegevens van het fictieve bedrijf Contoso zijn opgenomen. Deze gegevens zijn geïmporteerd uit een database, dus kunt u geen verbinding maken met de gegevensbron of deze bekijken in Query Editor. Download het bestand en pak het uit op uw computer.

## <a name="automatic-measures"></a>Automatische metingen

Wanneer in Power BI Desktop een meting wordt gemaakt, wordt dit meestal automatisch gedaan. Volg deze stappen om te zien hoe een meting wordt gemaakt in Power BI Desktop:

1. Selecteer in Power BI Desktop **Bestand** > **Openen**, blader naar het bestand *Contoso Sales Sample for Power BI Desktop.pbix* en selecteer **Openen**.

2. Breid de tabel **Sales** in het deelvenster **Velden** uit. Schakel vervolgens het selectievakje naast het veld **SalesAmount** in of sleep **SalesAmount** naar het rapportcanvas.

    Er wordt een nieuwe visualisatie van een kolomdiagram weergegeven die de som van alle waarden in de kolom **SalesAmount** van de tabel **Sales** toont.

    ![Kolomdiagram SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Elk veld (kolom) in het deelvenster **Velden** met een ![Sigma-pictogram](media/desktop-tutorial-create-measures/meastut_sigma.png) is een numeriek veld waarvan de waarden kunnen worden geaggregeerd. In plaats van een tabel met veel waarden weer te geven (twee miljoen rijen voor **SalesAmount**), wordt in Power BI Desktop automatisch een meting gemaakt en berekend om de gegevens te aggregeren wanneer een numeriek gegevenstype wordt gedetecteerd. Som is de standaardaggregatie voor een numeriek gegevenstype, maar u kunt eenvoudig andere aggregaties toepassen zoals gemiddelde of aantal. Het begrijpen van aggregaties is van cruciaal belang voor het begrijpen van metingen, omdat bij elke meting wel een bepaald type aggregatie wordt uitgevoerd. 

Volg deze stappen om de aggregatie van de grafiek te wijzigen:

1. Selecteer de visualisatie **SalesAmount** in het rapportcanvas.  

1. Selecteer de pijl-omlaag aan de rechterkant van **SalesAmount** in het gebied **Waarde** van het deelvenster **Visualisaties**. 

1. Selecteer **Gemiddelde** in het menu dat wordt weergegeven. 

    De visualisatie wordt gewijzigd in het gemiddelde van alle omzetwaarden in het veld **SalesAmount**.

    ![Diagram gemiddelde SalesAmount](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Afhankelijk van het gewenste resultaat kunt u het type aggregatie wijzigen. Niet alle typen aggregatie kunnen echter worden toegepast op elk numeriek gegevenstype. Voor het veld **SalesAmount** zijn Som en Gemiddelde bijvoorbeeld nuttig, terwijl ook Minimum en Maximum handig kunnen zijn. Aantal heeft echter niet zo veel zin voor het veld **SalesAmount**. De waarden zijn weliswaar numeriek, maar betreffen in feite valuta (bedragen).

De waarden die worden berekend op basis van metingen, veranderen bij elke wijziging van het rapport. Als u bijvoorbeeld het veld **RegionCountryName** vanuit de tabel **Geography** naar de bestaande grafiek **SalesAmount** sleept, wordt dit gewijzigd en wordt het gemiddelde van de omzetbedragen per land weergegeven.

![SalesAmount per land](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

Wanneer het resultaat van een meting verandert doordat u een wijziging in het rapport aanbrengt, wijzigt u in feite de *context* van de meting. Bij elke interactie met de rapportvisualisaties, wijzigt u de context waarin een meting wordt berekend en worden de resultaten daarvan weergegeven.

## <a name="create-and-use-your-own-measures"></a>Uw eigen metingen maken en gebruiken

In de meeste gevallen worden de waarden in Power BI Desktop automatisch berekend en geretourneerd in overeenstemming met de door u gekozen typen velden en aggregatie. In sommige gevallen wilt u echter uw eigen metingen maken om ingewikkeldere, unieke berekeningen uit te voeren. Met Power BI Desktop kunt u uw eigen metingen maken met de formuletaal DAX (Data Analysis Expressions). 

In DAX-formules worden veel dezelfde functies en operatoren gebruikt als in Excel-formules, en ook de syntaxis is vrijwel identiek. DAX-functies zijn echter ontworpen voor het werken met relationele gegevens en het uitvoeren van meer dynamische berekeningen tijdens het werken met rapporten. Er zijn meer dan 200 DAX-functies, variërend van eenvoudige aggregaties zoals som en gemiddelde tot complexe statistische functies en filters. Er zijn veel bronnen waarmee u meer over DAX te weten kunt komen. Raadpleeg [Standaard DAX-bewerkingen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md) nadat u deze zelfstudie hebt afgerond.

Wanneer u uw eigen meting maakt, wordt deze een *modelmeting* genoemd en wordt deze toegevoegd aan de lijst **Velden** voor de tabel die u selecteert. Enkele voordelen van modelmetingen zijn: u kunt ze welke naam u maar wilt geven, waardoor ze gemakkelijker te herkennen zijn; u kunt ze als argumenten in andere DAX-expressies gebruiken; en u kunt er snel complexe berekeningen mee uitvoeren.

### <a name="quick-measures"></a>Snelle metingen

Vanaf de release van februari 2018 van Power BI Desktop zijn een groot aantal veelgebruikte berekeningen beschikbaar als *snelle metingen*, die de DAX-formules schrijven op basis van de gegevens die u in een venster invoert. Deze snelle, krachtige berekeningen zijn ook ideaal voor het leren kennen van DAX of het seeden van uw eigen aangepaste metingen. 

Een snelle meting maken met behulp van een van deze methoden: 
 - Klik vanuit een tabel in het deelvenster **Velden** met de rechtermuisknop op **Meer opties** ( **...** ) of selecteer dit en selecteer vervolgens **Nieuwe snelle meting** in de lijst.

 - Selecteer **Nieuwe snelle meting** onder **Berekeningen** op het tabblad **Start** van het lint van Power BI Desktop.

Zie [Snelle metingen gebruiken](desktop-quick-measures.md) voor meer informatie over het maken en gebruiken van snelle metingen.

### <a name="create-a-measure"></a>Een meting maken

Stel, u wilt uw netto-omzet analyseren door kortingen en terugbetalingen af te trekken van de totale omzetbedragen. Voor de context in uw visualisatie hebt u een meting nodig die de som van DiscountAmount en ReturnAmount aftrekt van de som van SalesAmount. Er is geen veld voor netto-omzet in de lijst **Velden**, maar u hebt zo de basis voor het maken van uw eigen meting om de netto-omzet te berekenen. 

Volg deze stappen om een meting te maken:

1. Klik in het deelvenster **Velden** met de rechtermuisknop op de tabel **Sales** of beweeg met de muisaanwijzer over de tabel en selecteer **Meer opties** ( **...** ). 

1. Selecteer **Nieuwe meting** in het menu dat wordt weergegeven. 

    Hiermee wordt de nieuwe meting opgeslagen in de tabel **Sales**, waar u deze eenvoudig terug kunt vinden.
    
    ![Nieuwe meting vanuit lijst](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    U kunt ook een nieuwe meting maken door op het tabblad **Start** van het Power BI Desktop-lint in de groep **Berekeningen** de optie **Nieuwe meting** te selecteren.
    
    ![Nieuwe meting vanuit lint](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    
    >[!TIP]
    >Wanneer u een meting vanuit het lint maakt, kunt u deze in elke tabel maken, maar de meting is eenvoudiger te vinden als u deze maakt waar u van plan bent om deze te gebruiken. In dit geval selecteert u eerst de tabel **Sales** om deze te activeren en selecteert u vervolgens **Nieuwe meting**. 
    
    De formulebalk wordt weergegeven bovenaan het rapportcanvas. Hier kunt u de naam van uw meting wijzigen en een DAX-formule invoeren.
    
    ![Formulebalk](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
1. De standaardnaam voor een nieuwe meting is *Meting*. Als u de naam niet wijzigt, worden extra nieuwe metingen *Meting 2*, *Meting 3* enzovoort genoemd. U wilt deze meting makkelijker kunnen herkennen, dus markeer *Meting* in de formulebalk en wijzig dit vervolgens in *Net Sales*.
    
1. Voer de formule in. Typ na het gelijkteken *Sum*. Terwijl u typt, verschijnt er een vervolgkeuzelijst met alle DAX-functies die beginnen met de letters die u typt. Scrol zo nodig omlaag, selecteer **SUM** in de lijst en druk op **Enter**.
    
    ![SUM in de lijst kiezen](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    Nu wordt er een haakje-openen weergegeven en een vervolgkeuzelijst met suggesties, ditmaal voor de beschikbare kolommen die kunnen worden doorgegeven in de functie SUM.
    
    ![Kolom kiezen](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
1. Expressies worden altijd weergegeven tussen een haakje-openen en een haakje-sluiten. In dit voorbeeld bevat de expressie één argument voor doorgeven aan de functie SUM: de kolom **SalesAmount**. Begin met het typen van *SalesAmount* totdat **Sales(SalesAmount)** de enige overgebleven waarde in de lijst is. 

    De naam van de kolom die wordt voorafgegaan door de naam van de tabel wordt de volledig gekwalificeerde naam van de kolom genoemd. Volledig gekwalificeerde kolomnamen zorgen ervoor dat uw formules gemakkelijker te lezen zijn.
    
    ![SalesAmount selecteren](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
1. Selecteer **Sales[SalesAmount]** in de lijst en typ vervolgens een haakje sluiten.
    
    > [!TIP]
    > Syntaxisfouten zijn meestal te wijten aan een ontbrekend of verkeerd geplaatst haakje sluiten.
    
    
    
1. De andere twee kolommen in de formule aftrekken:

    a. Typ na het haakje-sluiten van de eerste expressie een spatie, een minteken (-) en vervolgens nog een spatie. 

    b. Voer nog een SUM-functie in en begin met het typen van *DiscountAmount* tot u de kolom **Sales[DiscountAmount]** als argument kunt kiezen. Voeg een haakje-sluiten toe. 

    c. Typ een spatie, een minteken, een spatie, nog een SUM-functie met **Sales[ReturnAmount]** als argument, en vervolgens een haakje-sluiten.
    
    ![Formule voltooien](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
1. Druk op **Enter** of selecteer **Doorvoeren** (het vinkje) in de formulebalk om de formule te voltooien en te valideren. 

    De gevalideerde meting **Net Sales** kan nu worden gebruikt in de tabel **Sales** in het deelvenster **Velden**.
    
    ![De meting Net Sales in de lijst met tabelvelden Sales](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
1. Als u te weinig ruimte hebt voor het invoeren van een formule of de formule op twee regels wilt hebben, selecteert u aan de rechterkant van de formulebalk de pijl-omlaag om meer ruimte te creëren. 

    De pijl-omlaag verandert in een pijl-omhoog en er wordt een groot vak weergegeven.

    ![Formule pijl-omhoog](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)

1. Scheid delen van uw formule door op **Alt** + **Enter** te drukken voor afzonderlijke regels of door op **Tab** te drukken om tabruimte toe te voegen.

   ![Uitgebreide formule](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)

### <a name="use-your-measure-in-the-report"></a>De meting in het rapport gebruiken
Voeg de nieuwe meting **Net Sales** toe aan het rapportcanvas en bereken de netto-omzet voor alle andere velden die u aan het rapport toevoegt. 

De netto-omzet per land bekijken:

1. Selecteer de meting **Net Sales** in de tabel **Sales** of sleep deze naar het rapportcanvas.
    
1. Selecteer het veld **RegionCountryName** in de tabel **Geography** of sleep deze naar de grafiek **Net Sales**.
    
    ![Netto-omzet per land](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
1. Selecteer het veld **SalesAmount** of sleep het naar de grafiek om het verschil tussen de netto-omzet en de totale omzet per land te bekijken. 

    ![Totale omzet en netto-omzet per land](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)

    De grafiek gebruikt nu twee metingen: De meting **SalesAmount**, die automatisch werd berekend in Power BI, en de meting **Net Sales**, die u zelf hebt gemaakt. Elke meting is berekend in de context van een ander veld: **RegionCountryName**.
    
### <a name="use-your-measure-with-a-slicer"></a>De meting met een slicer gebruiken

Voeg een slicer toe om de netto-omzet en omzetbedragen verder te filteren op kalenderjaar:
    
1. Selecteer een leeg gebied naast de grafiek. Selecteer de visualisatie **Tabel** in het deelvenster **Visualisaties**. 

    Hiermee maakt u een lege tabelvisualisatie op het rapportcanvas.
    
    ![Nieuwe, lege tabelvisualisatie](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
1. Sleep het veld **Year** van de tabel **Calendar** naar de nieuwe, lege tabelvisualisatie. 
    
    Omdat **Year** een numeriek veld is, worden de waarden ervan in Power BI Desktop opgesomd. Deze opsomming werkt niet zo goed als aggregatie. Dit bespreken we in de volgende stap.

    ![Aggregatie van jaartallen](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
3. Selecteer de pijl-omlaag naast **Year** in het vak **Waarden** in het deelvenster **Visualisaties** en selecteer vervolgens **Niet samenvatten** in de lijst. De tabel geeft nu afzonderlijke jaartallen weer.
    
    ![Niet samenvatten selecteren](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
4.  Selecteer het pictogram **Slicer** in het deelvenster **Visualisaties** om de tabel naar een slicer te converteren. Als via de visualisatie een schuifregelaar wordt weergegeven in plaats van een lijst, selecteert u **Lijst** via de pijl-omlaag in de schuifregelaar.

    ![Tabel converteren naar slicer](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
5.  Selecteer een waarde in de slicer **Year** om de grafiek voor **Net Sales en Sales Amount per RegionCountryName** te filteren. De metingen **Net Sales** en **SalesAmount** herberekenen de resultaten en geven ze weer in de context van het geselecteerde veld **Year**. 
    
    ![Grafiek gefilterd op jaar](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

### <a name="use-your-measure-in-another-measure"></a>Uw meting in een andere meting gebruiken

Stel, uw wilt weten welke producten het hoogste netto verkoopbedrag per verkochte eenheid hebben. U hebt een meting nodig die de netto-omzet deelt door het aantal verkochte eenheden. Maak een nieuwe meting die het resultaat van de meting **Net Sales** deelt door de som van **Sales[SalesQuantity]** .

1.  Maak in het deelvenster **Velden** een nieuwe meting met de naam **Net Sales per Unit** in de tabel **Sales**.
    
1. Begint met het typen van *Net Sales* in de formulebalk. In de lijst met suggesties wordt weergegeven wat u kunt toevoegen. Selecteer **[Netto-omzet]** .
    
    ![Formule met Net Sales](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
1. U kunt ook verwijzen naar metingen door alleen een haakje-openen te typen ( **[** ). De lijst met suggesties toont alleen metingen die u aan uw formule kunt toevoegen.
    
    ![Haakje toont alleen metingen](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
1. Voer een spatie, een deelteken (/), nog een spatie, en een SUM-functie in en typ vervolgens *Quantity*. In de lijst met suggesties worden alle kolommen met *Quantity* in de naam weergegeven. Selecteer **Sales[SalesQuantity]** , typ een haakje-sluiten, en druk op **Enter** of selecteer **Doorvoeren** (het vinkje) om de formule te valideren. 

    De formule zou er vervolgens zo uit moeten zien:
    
    `Net Sales per Unit = [Net Sales] / SUM(Sales[SalesQuantity])`
    
1. Selecteer de meting **Net Sales per Unit** in de tabel **Sales** of sleep deze naar een leeg vlak in het rapportcanvas. 

    De grafiek toont de netto-omzet per eenheid voor alle verkochte producten. Deze grafiek is niet heel nuttig. Dit bespreken we in de volgende stap.
    
    ![Netto-omzet per eenheid](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
1. Wijzig het visualisatietype van de grafiek in **Structuurkaart** voor een andere weergave.
    
    ![Wijzigen in structuurkaart](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
1. Selecteer het veld **Product Category** of sleep het naar de treemap of naar het veld **Groep** van het deelvenster **Visualisaties**. U hebt nu handige informatie tot uw beschikking.
    
    ![Structuurkaart per productcategorie](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
7. Verwijder het veld **ProductCategory** en sleep in plaats daarvan het veld **ProductName** naar de grafiek. 
    
    ![Structuurkaart per productnaam](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
   Dit is vooral ter illustratie, maar u zult moeten toegeven dat deze functionaliteit geweldig is. Experimenteer met andere manieren om de visualisatie te filteren en in te delen.

## <a name="what-youve-learned"></a>Wat u hebt geleerd
Metingen bieden u de mogelijkheid om nuttige inzichten uit uw gegevens te halen. U hebt geleerd hoe u metingen maakt met behulp van de formulebalk, hoe u ze een handige naam geeft, en hoe u de juiste formule-elementen vindt en selecteert met behulp van de DAX-suggestielijsten. U hebt ook kennisgemaakt met context, waarbij het resultaat van berekeningen in metingen varieert, afhankelijk van andere velden of andere expressies in uw formule.

## <a name="next-steps"></a>Volgende stappen
- Zie [Gebruik Snelle metingen om eenvoudig algemene en krachtige berekeningen uit te voeren](desktop-quick-measures.md) voor meer informatie over snelle metingen in Power BI Desktop, die u volop veelgebruikte en krachtige berekeningen bieden.
  
- Zie [Standaard DAX-bewerkingen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md) voor meer informatie over DAX-formules en geavanceerde metingen. Dit artikel is voornamelijk gericht op de grondbeginselen van DAX, zoals de syntaxis en functies. Daarnaast gaan we iets dieper in op het begrip context.
  
- Voeg [Naslaginformatie over Data Analysis Expressions (DAX)](https://docs.microsoft.com/dax/index) toe aan uw favorieten. In deze referentie vindt u gedetailleerde informatie over de syntaxis, operators en meer dan 200 functies van DAX.

