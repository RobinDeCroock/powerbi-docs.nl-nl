---
title: Standaard DAX-bewerkingen in Power BI Desktop
description: Standaard DAX-bewerkingen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: fcff0bf1d6c68b9bdb000855f4984b3664b882c1
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "73877915"
---
# <a name="dax-basics-in-power-bi-desktop"></a>Standaard DAX-bewerkingen in Power BI Desktop
Dit artikel is bedoeld voor nieuwe gebruikers van Power BI Desktop. In deze korte en eenvoudige inleiding wordt beschreven hoe u met Data Analysis Expressions (DAX) een aantal problemen met basisberekeningen en gegevensanalyse kunt oplossen. We bekijken conceptuele informatie en een reeks taken die u kunt uitvoeren, en doen een kennistoets om te testen wat u hebt geleerd. Nadat u dit artikel hebt gelezen, zou u een goed begrip van de belangrijkste basisconcepten in DAX moeten hebben.

## <a name="what-is-dax"></a>Wat is DAX?
DAX is een verzameling functies, operators en constanten die in een formule, of expressie, kunnen worden gebruikt om een of meer waarden te berekenen en te retourneren. Eenvoudig gezegd, DAX helpt u nieuwe informatie samen te stellen op basis van gegevens die al in het model staan.

## <a name="why-is-dax-so-important"></a>Waarom is DAX zo belangrijk?
Het is eenvoudig om een nieuw Power BI Desktop-bestand te maken en daar gegevens in te importeren. U kunt zelfs rapporten maken die waardevolle inzichten bieden zonder enig gebruik te maken van DAX-formules. Maar wat als u groeipercentages voor verschillende productcategorieën en verschillende datumbereiken moet analyseren? Of als u de jaarlijkse groei ten opzichte van markttrends moet berekenen? DAX-formules maken dit mogelijk en bieden bovendien tal van andere belangrijke mogelijkheden. Door te leren hoe u effectieve DAX-formules kunt maken, kunt u optimaal gebruikmaken van uw gegevens. Wanneer u over alle benodigde informatie beschikt, kunt u beginnen met het oplossen van bedrijfsproblemen die invloed hebben op de winstgevendheid van uw bedrijf. Dit is de kracht van Power BI en DAX helpt u daarbij.

## <a name="prerequisites"></a>Vereisten
U bent mogelijk al bekend met het samenstellen van formules in Microsoft Excel. Deze kennis komt van pas om DAX beter te begrijpen, maar zelfs als u geen ervaring hebt met Excel-formules, kunt u met de hier beschreven concepten DAX-formules gaan maken en meteen praktische BI-problemen gaan oplossen.

We gaan kijken hoe DAX-formules worden gebruikt in berekeningen, en met name in metingen en berekende kolommen. U dient wel bekend te zijn met Power BI Desktop en te weten hoe u gegevens importeert en velden aan een rapport toevoegt. Daarnaast moet u vertrouwd zijn met de grondbeginselen van [metingen](desktop-measures.md) en [berekende kolommen](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Voorbeeldwerkmap

De beste manier om bekend te raken met DAX, is door enkele eenvoudige formules te maken, deze te gebruiken met feitelijke gegevens en zelf de resultaten daarvan te bekijken. In de hier gegeven voorbeelden en taken wordt gebruikgemaakt van het bestand [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Dit voorbeeldbestand is hetzelfde als het bestand dat wordt gebruikt in het artikel [Zelfstudie: Uw eigen metingen maken in Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>Laten we beginnen.
We gaan ons een beeld vormen van DAX aan de hand van drie fundamentele concepten: *syntaxis*, *functies* en *context*. Er zijn andere belangrijke concepten in DAX, maar deze drie bieden de beste basis om uw vaardigheden in DAX verder uit te bouwen.

### <a name="syntax"></a>Syntaxis
Voordat u uw eigen formules gaat maken, kijken we eerst naar de syntaxis van de DAX-formules. De syntaxis omvat de verschillende elementen van een formule, of eenvoudiger gezegd, hoe de formule wordt geschreven. Bekijk bijvoorbeeld de volgende eenvoudige DAX-formule voor een meting:

![De syntaxis van de DAX-formule](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Deze formule bevat de volgende syntaxiselementen:

**A.** De naam van de meting, **Totale verkoop**.

**B.** Het Is gelijk-teken ( **=** ) dat het begin van de formule aangeeft. Wanneer deze wordt berekend, wordt een resultaat geretourneerd.

**C.** De DAX-functie **SUM** waarmee u alle getallen in de kolom **Sales[SalesAmount]** bij elkaar optelt. Later geven we meer informatie over functies.

**D.** Haakjes **()** die een expressie omgeven die een of meer argumenten bevat. Alle functies hebben minimaal één argument nodig. Een argument geeft een waarde door aan een functie.

**E.** De tabel, **Sales**, waarnaar wordt verwezen.

**F.** De kolom, **[SalesAmount]** , waarnaar wordt verwezen in de tabel Sales. Door dit argument weet de functie SUM voor welke kolom een som moet worden samengesteld.

Voor een beter begrip van een DAX-formule kan het handig zijn om elk van de elementen op te splitsen in een taal waarin u dagelijks denkt en die u dagelijks spreekt. U kunt deze formule bijvoorbeeld lezen als:

> *Bereken (=) voor de meting met de naam Total Sales de som van de waarden uit de kolom [SalesAmount] in de tabel Sales.*
> 
> 

Wanneer deze meting wordt toegevoegd aan een rapport, worden door de meting waarden berekend en geretourneerd door verkoopbedragen op te tellen voor elk van de andere velden die we opnemen, bijvoorbeeld voor Cell Phones in the USA.

Misschien denkt u "Doet deze meting niet hetzelfde als wanneer ik het veld SalesAmount gewoon aan mijn rapport zou toevoegen?" En dan hebt u gelijk. Maar er is een goede reden om onze eigen meting te maken die waarden uit het veld SalesAmount optelt: we kunnen deze gebruiken als argument in andere formules. Dit kan nu wat verwarrend lijken, maar naarmate u meer vaardigheid krijgt in DAX-formules, neemt de efficiëntie van uw formules en uw model alleen maar toe. De meting voor Total Sales wordt overigens weergegeven als een argument in andere formules verderop in dit artikel.

Laten we wat andere aspecten van deze formule bekijken. Meer in het bijzonder hebben we een functie geïntroduceerd, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Functies zijn vooraf geschreven formules die het eenvoudiger maken om complexe berekeningen en bewerkingen uit te voeren met getallen, datums, tijd, tekst en meer. We zullen functies later nader bespreken.

U ziet ook dat de kolomnaam [SalesAmount] wordt voorafgegaan door de tabel Sales waartoe de kolom behoort. Deze naam wordt de volledig gekwalificeerde kolomnaam genoemd, omdat deze de naam van de kolom bevat, voorafgegaan door de naam van de tabel. Voor kolommen waarnaar in dezelfde tabel wordt verwezen, hoeft de tabelnaam niet te worden opgenomen in de formule. Op die manier wordt de lengte beperkt van formules waarin naar veel kolommen wordt verwezen en zijn deze gemakkelijker te lezen. Het is echter raadzaam de tabelnaam in uw metingformules op te nemen, zelfs als de kolommen tot dezelfde tabel behoren.

> [!NOTE]
> Als een tabelnaam spaties, gereserveerde trefwoorden of niet-toegestane tekens bevat, moet u de tabelnaam tussen enkele aanhalingstekens plaatsen. U moet ook tabelnamen tussen aanhalingstekens plaatsen als de naam tekens bevat die buiten de alfanumerieke ANSI-tekenset vallen, ongeacht of uw landinstelling de tekenset wel of niet ondersteunt.
> 
> 

Het is belangrijk dat uw formules de juiste syntaxis hebben. In de meeste gevallen geldt dat, als de syntaxis niet juist is, er een syntaxisfout wordt geretourneerd. In andere gevallen kan de syntaxis juist zijn, maar zijn de geretourneerde waarden misschien niet wat u verwacht. De DAX-editor in Power BI Desktop biedt een suggestiefunctie. Dit is een functie waarmee u syntactisch juiste formules kunt maken door u te helpen de juiste elementen te selecteren.

We gaan een eenvoudige formule maken. Deze taak biedt u meer inzicht in de syntaxis van formules en laat zien hoe de suggestiefunctie in de formulebalk u kan helpen.

### <a name="task-create-a-measure-formula"></a>Taak: Maak een metingformule

1. [Download](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) en open het bestand Contoso Sales Sample Power BI Desktop. 
    
2. Klik in de rapportweergave in de lijst met velden met de rechtermuisknop op de tabel **Sales** en selecteer vervolgens **Nieuwe meting**.
    
3. Vervang in de formulebalk **Meting** door een nieuwe metingnaam *Verkoop vorig kwartaal*.
    
4. Na het gelijkteken typt u de eerste letters *CAL* en dubbelklikt u vervolgens op de functie die u wilt gebruiken. In deze formule wilt u de functie **CALCULATE** gebruiken.

   U gebruikt de functie CALCULATE om de bedragen te filteren die we willen laten optellen door een argument dat we doorgeven aan de functie CALCULATE. Dit wordt ook wel het nesten van functies genoemd. De functie CALCULATE heeft minimaal twee argumenten. De eerste is de te evalueren expressie en de tweede is een filter.
   
5. Na het haakje *(* voor de functie **CALCULATE**, typt u *SUM*, gevolgd door een nog een haakje openen *(* . 

   Vervolgens geven we een argument door aan de functie SUM.

6. Begin met het typen van *Sal* en selecteer vervolgens **Sales [SalesAmount]** , gevolgd door een haakje sluiten *)* . 

   Dit is het eerste argument van de expressie voor de functie CALCULATE.
    
7. Typ een komma ( *,* ) gevolgd door een spatie om het eerste filter op te geven en typ daarna *PREVIOUSQUARTER*. 
    
   U gebruikt de functie PREVIOUSQUARTER voor tijdintelligentie om de SUM-resultaten te filteren op het vorige kwartaal.
    
8. Na de haakjes openen *()* voor de functie PREVIOUSQUARTER typt u *Calendar[DateKey]* .
    
   De functie PREVIOUSQUARTER heeft één argument, te weten een kolom met een aaneengesloten reeks datums. In ons geval is dat de kolom DateKey in de tabel Calendar.
    
9. Sluit de beide argumenten die worden doorgegeven aan de functies PREVIOUSQUARTER en CALCULATE af door twee haakjes sluiten *))* te typen.
    
   De formule moet er nu zo uitzien:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey])) =**
    
10. Schakel het selectievakje ![Pictogram met vinkje](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) in de formulebalk in of druk op Enter om de formule te valideren en aan het model toe te voegen.

Prima! U hebt zojuist een ingewikkelde meting met DAX gemaakt en deze was zeker niet de eenvoudigste. Wat deze formule doet, is de totale verkoop van het vorige kwartaal berekenen, afhankelijk van de filters die in een rapport zijn toegepast. Als we bijvoorbeeld SalesAmount en de nieuwe meting voor Verkoop vorig kwartaal in een diagram plaatsen en vervolgens Year en QuarterOfYear als slicers toevoegen, is dit het resultaat:

![Diagram met Verkoop vorig kwartaal en SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

U hebt nu kennisgemaakt met verschillende belangrijke aspecten van DAX-formules: 

- Deze formule bevat twee functies. [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), een functie voor tijdintelligentie, is genest als een argument dat wordt doorgegeven aan [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), een filterfunctie. 

   DAX-formules kunnen maximaal 64 geneste functies bevatten. Maar het is niet erg waarschijnlijk dat een formule zo veel geneste functies zal bevatten. Een dergelijke formule zou in feite lastig te maken zijn en de fouten hiervoor moeilijk op te sporen. Daarnaast is zo'n formule waarschijnlijk ook niet erg snel.

- In deze formule hebt u ook filters gebruikt. Filters bakenen af wat er wordt berekend. In dit geval hebt u één filter als argument geselecteerd, wat in feite het resultaat van een andere functie is. Later geven we meer informatie over filters.

- U hebt de functie CALCULATE gebruikt. Deze functie is een van de krachtigste functies in DAX. Bij het ontwerpen van modellen en het samenstellen van complexere formules zult u deze functie waarschijnlijk vaak gebruiken. Hoewel verdere bespreking van de functie CALCULATE buiten het bereik van dit artikel valt, moet u aan deze functie extra aandacht besteden wanneer u beter bekend raakt met DAX.

### <a name="syntax-quickquiz"></a>QuickQuiz over syntaxis
1. Waarvoor wordt deze knop op de formulebalk gebruikt?
   
   > ![Selectie van knop](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Waardoor wordt een kolomnaam in een DAX-formule altijd omgeven?

Aan het einde van dit artikel vindt u de antwoorden.

### <a name="functions"></a>Functies
Functies zijn vooraf gedefinieerde formules waarmee berekeningen in een bepaalde volgorde of met een bepaalde structuur worden uitgevoerd met behulp van specifieke waarden, argumenten genaamd. Argumenten kunnen bestaan uit andere functies, een andere formule, een expressie, kolomverwijzingen, getallen, tekst, logische waarden zoals TRUE of FALSE, of constanten.

DAX omvat de volgende functiecategorieën: [Datum en tijd](https://msdn.microsoft.com/library/ee634786.aspx), [Tijdintelligentie](https://msdn.microsoft.com/library/ee634763.aspx), [Informatie](https://msdn.microsoft.com/library/ee634552.aspx), [Logisch](https://msdn.microsoft.com/library/ee634365.aspx), [Wiskundig](https://msdn.microsoft.com/library/ee634241.aspx), [Statistisch](https://msdn.microsoft.com/library/ee634822.aspx), [Tekst](https://msdn.microsoft.com/library/ee634938.aspx), [Bovenliggend/onderliggend](https://msdn.microsoft.com/library/mt150102.aspx) en [Overige functies](https://msdn.microsoft.com/library/mt150101.aspx). Als u vertrouwd bent met functies in Excel-formules, zullen veel van de functies in DAX u bekend voorkomen. DAX-functies zijn echter uniek vanwege het volgende:

* Een DAX-functie heeft altijd betrekking op een volledige kolom of tabel. Als u alleen bepaalde waarden uit een tabel of kolom wilt gebruiken, kunt u filters toevoegen aan de formule.
* Als u berekeningen moet aanpassen op rijbasis, biedt DAX functies waarmee u de huidige rijwaarde of een gerelateerde waarde als een soort argument kunt gebruiken, voor het uitvoeren van berekeningen die per context verschillen. Later wordt de context nader beschreven.
* DAX bevat veel functies die in plaats van een waarde een tabel retourneren. De tabel wordt niet weergegeven, maar hiermee wordt invoer geleverd aan andere functies. U kunt bijvoorbeeld een tabel ophalen en vervolgens de afzonderlijke waarden daarin tellen of dynamische totalen in gefilterde tabellen of kolommen berekenen.
* DAX omvat tal van functies voor tijdintelligentie. Met deze functies kunt u datumbereiken definiëren of selecteren en daarop gebaseerde dynamische berekeningen uitvoeren. U kunt bijvoorbeeld totalen in parallelle perioden vergelijken.
* Excel heeft een populaire functie, VLOOKUP. DAX-functies gebruiken geen cel of celbereik als verwijzing zoals VERT.ZOEKEN in Excel. DAX-functies gebruiken een kolom of tabel als verwijzing. Houd er rekening mee dat u in Power BI Desktop met een relationeel gegevensmodel werkt. Het opzoeken van waarden in een andere tabel is eenvoudig en in de meeste gevallen hoeft u helemaal geen formule te maken.
  
  Zoals u ziet, kunnen functies in DAX u helpen bij het maken van krachtige formules. Maar we hebben eigenlijk alleen nog maar naar de basisprincipes van functies gekeken. Naarmate uw vaardigheden met DAX toenemen, gaat u formules maken met veel verschillende functies. Een van de beste plekken om meer te weten te komen over elk van de DAX-functies is de [Naslag voor DAX-functies](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>QuickQuiz voor functies
1. Waarnaar verwijst een functie altijd?
2. Kan een formule meer dan één functie bevatten?
3. Welke functiecategorie zou u gebruiken om twee tekenreeksen samen te voegen tot één tekenreeks?

Aan het einde van dit artikel vindt u de antwoorden.

### <a name="context"></a>Context
Context is een van de belangrijkste DAX-concepten. Er zijn twee typen context in DAX: rijcontext en filtercontext. We kijken eerst naar rijcontext.

**Rijcontext**

Rijcontext kan het beste worden beschouwd als zijnde de huidige rij. Dit is van toepassing wanneer een formule een functie bevat die filters gebruikt om één specifieke rij in een tabel te identificeren. De functie past een rijcontext toe voor elke rij in de tabel die wordt gefilterd. Dit type rijcontext geldt doorgaans voor metingen.

**Filtercontext**

Filtercontext is wat ingewikkelder dan rijcontext. U kunt filtercontext zien als een of meer filters die worden toegepast in een berekening waarmee een resultaat of waarde wordt bepaald.

Filtercontext komt niet in de plaats van rijcontext, maar wordt toegepast naast rijcontext. U kunt de waarden die in een berekening moeten worden opgenomen bijvoorbeeld nog verder beperken door een filtercontext toe te passen die niet alleen de rijcontext aangeeft, maar ook een bepaalde waarde (filter) in die rijcontext aangeeft.

Filtercontext is gemakkelijk te zien in uw rapporten. Wanneer u bijvoorbeeld TotalCost in een visualisatie opneemt, gevolgd door add Year en Region, definieert u een filtercontext waarmee een subset van gegevens wordt geselecteerd op basis van een bepaald jaar en bepaalde regio.

Waarom is filtercontext zo belangrijk voor DAX? Filtercontext kan het gemakkelijkst worden gebruikt door velden aan een visualisatie toe te voegen, maar kan ook worden toegepast in een DAX-formule door een filter te definiëren met behulp van functies zoals ALL, RELATED, FILTER, CALCULATE, op basis van relaties en andere metingen en kolommen. Laten we eens naar de volgende formule kijken die wordt gebruikt in een meting met de naam Store Sales:

![Meting Verkoop winkel](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Voor een beter begrip van de formule gaan we deze opsplitsen, net zoals we met andere formules kunnen doen.

Deze formule bevat de volgende syntaxiselementen:

**A.** De naam van de meting, **Verkoop winkel**.

**B.** Het Is gelijk-teken ( **=** ) dat het begin van de formule aangeeft.

**C.** De functie **CALCULATE** waarmee een expressie, als argument, wordt bewerkt in een context die wordt gewijzigd door de opgegeven filters.

**D.** Haakjes **()** die een expressie omgeven die een of meer argumenten bevat.

**E.** Een meting **[Total Sales]** in dezelfde tabel als een expressie. De meting Total Sales heeft de formule: =SUM(Sales[SalesAmount]).

**F.** Een komma ( **,** ) die het eerste expressieargument scheidt van het filterargument.

**G.** De volledig gekwalificeerde kolom waarnaar wordt verwezen, **Channel[ChannelName]** . Dit is onze rijcontext. Elke rij in deze kolom geeft een kanaal aan, zoals Winkel of Online.

**H.** De specifieke waarde, **Winkel** als filter. Dit is onze filtercontext.

Deze formule zorgt ervoor dat alleen verkoopwaarden die door de Totale verkoop-meting zijn gedefinieerd alleen worden berekend voor rijen in de kolom Channel[ChannelName] waarbij de waarde *Winkel* wordt gebruikt als filter.

U kunt zich wel voorstellen dat het definiëren van filtercontext binnen een formule bijzonder krachtige mogelijkheden biedt. De mogelijkheid om alleen naar één bepaalde waarde in een gerelateerde tabel te verwijzen, is slechts één voorbeeld. Maakt u zich geen zorgen als u het concept van context nog niet meteen kunt vatten. Wanneer u uw eigen formules gaat samenstellen, krijgt u een beter begrip van context en waarom dit in DAX zo belangrijk is.

### <a name="context-quickquiz"></a>QuickQuiz over context
1. Welke twee typen context zijn er?
2. Wat is filtercontext?
3. Wat is rijcontext?

Aan het einde van dit artikel vindt u de antwoorden.

## <a name="summary"></a>Samenvatting
Nu u de grondbeginselen van de belangrijkste concepten in DAX kent, kunt u zelf DAX-formules voor metingen gaan maken. DAX is misschien niet zo heel eenvoudig in de vingers te krijgen, maar er zijn veel hulpbronnen beschikbaar. Na het lezen van dit artikel en met zelfgemaakte formules te hebben geëxperimenteerd, kunt u meer leren over andere DAX-concepten en -formules die u kunt toepassen op uw eigen situatie. U hebt de beschikking over tal van DAX-hulpbronnen. De belangrijkste daarvan is de [Naslag voor Data Analysis Expressions (DAX)](https://msdn.microsoft.com/library/gg413422.aspx).

Omdat DAX al een aantal jaren deel uit maakt van andere Microsoft BI-programma's, zoals Power Pivot en Analysis Services-modellen in tabelvorm, is er veel nuttige informatie beschikbaar. Er is nog meer informatie te vinden in handboeken, whitepapers en blogs van zowel Microsoft als toonaangevende BI-deskundigen. Ook de [Wiki over DAX Resource Center op TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) (Engelstalig) is een prima plek om te beginnen.

### <a name="quickquiz-answers"></a>QuickQuiz: de antwoorden
Syntaxis:

1. Valideert de meting en voert deze in het model in.
2. Vierkante haken [].

Functies:

1. Een tabel en een kolom.
2. Ja. Een formule kan maximaal 64 geneste functies bevatten.
3. [Tekstfuncties](https://msdn.microsoft.com/library/ee634938.aspx).

Context:

1. Rijcontext en filtercontext.
2. Een of meer filters in een berekening om één specifieke waarde te bepalen.
3. De huidige rij.

