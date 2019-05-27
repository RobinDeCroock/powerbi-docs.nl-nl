---
title: Standaard DAX-bewerkingen in Power BI Desktop
description: Standaard DAX-bewerkingen in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 64957fa71249c551b4f69b619a12baf03fae6b06
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513734"
---
# <a name="dax-basics-in-power-bi-desktop"></a>Standaard DAX-bewerkingen in Power BI Desktop
Dit artikel is bedoeld voor nieuwe gebruikers van Power BI Desktop. Het bevat een snelle en eenvoudige inleiding over hoe u met Data Analysis Expressions (DAX) een aantal problemen met basisberekeningen en gegevensanalyse kunt oplossen. We bekijken conceptuele informatie, een reeks taken die u kunt uitvoeren en enkele kwisjes om te testen wat u hebt geleerd. Nadat u dit artikel hebt gelezen, zou u een goed begrip van de belangrijkste basisconcepten in DAX moeten hebben.

## <a name="what-is-dax"></a>Wat is DAX?
DAX is een verzameling functies, operators en constanten die in een formule, of expressie, kunnen worden gebruikt om een of meer waarden te berekenen en te retourneren. Eenvoudig gezegd, DAX helpt u nieuwe informatie samen te stellen op basis van gegevens die al in het model staan.

## <a name="why-is-dax-so-important"></a>Waarom is DAX zo belangrijk?
Het is heel eenvoudig een nieuw Power BI Desktop-bestand te maken en daar wat gegevens naartoe te importeren. U kunt zelfs rapporten maken die waardevolle inzichten bieden zonder enig gebruik te maken van DAX-formules. Maar wat als u groeipercentages voor verschillende productcategorieën en verschillende datumbereiken moet analyseren? Of als u de jaarlijkse groei ten opzichte van markttrends moet berekenen? DAX-formules maken dit mogelijk en bieden bovendien tal van andere belangrijke mogelijkheden. Door te leren hoe u effectieve DAX-formules kunt maken, kunt u optimaal gebruikmaken van uw gegevens. Wanneer u over alle benodigde informatie beschikt, kunt u beginnen met het oplossen van bedrijfsproblemen die invloed hebben op de winstgevendheid van uw bedrijf. Dit is de kracht van Power BI en DAX helpt u daarbij.

## <a name="prerequisites"></a>Vereisten
U bent mogelijk al bekend met het samenstellen van formules in Microsoft Excel. Deze kennis komt van pas om DAX beter te begrijpen, maar zelfs als u geen ervaring hebt met Excel-formules, kunt u met de hier beschreven concepten DAX-formules gaan maken en meteen praktische BI-problemen gaan oplossen.

We gaan kijken hoe DAX-formules worden gebruikt in berekeningen, en meer in het bijzonder, in metingen en berekende kolommen. U dient wel bekend te zijn met Power BI Desktop, importeren van gegevens, toevoegen van velden aan een rapport en u moet tevens vertrouwd zijn met de grondbeginselen van [metingen](desktop-measures.md) en [berekende kolommen](desktop-calculated-columns.md).

**Voorbeeldwerkmap**

De beste manier om DAX te leren kennen, is enkele eenvoudige formules maken, die gaan gebruiken met feitelijke gegevens en zelf de resultaten daarvan zien. De hier gegeven voorbeelden en taken maken gebruik van het bestand Contoso Sales Sample for Power BI Desktop Preview. Dit is hetzelfde voorbeeldbestand dat wordt gebruikt in het artikel [Zelfstudie: Uw eigen metingen maken in Power BI Desktop](desktop-tutorial-create-measures.md). Hier volgt het te downloaden [voorbeeldbestand](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip).

## <a name="lets-begin"></a>Laten we beginnen.
We gaan ons een beeld vormen van DAX aan de hand van drie fundamentele concepten: *syntaxis*, *functies* en *context*. Natuurlijk, er zijn andere belangrijke concepten in DAX, maar deze drie bieden de beste basis om uw vaardigheden in DAX verder uit te bouwen.

### <a name="syntax"></a>Syntaxis
Voordat u uw eigen formules gaat maken, kijken we eerst naar de syntaxis van de DAX-formules. De syntaxis omvat de verschillende elementen van een formule, of eenvoudiger gezegd, hoe de formule wordt geschreven. Laten we eens kijken naar een eenvoudige DAX-formule voor een meting.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Deze formule bevat de volgende syntaxiselementen:

**A.** De naam van de meting, **Total Sales**.

**B.** De gelijkteken-operator (**=**) geeft het begin van de formule aan. Wanneer deze wordt berekend, wordt een resultaat geretourneerd.

**C.** De DAX-functie **SUM** is de som van alle getallen in de kolom **Sales[SalesAmount]**. Later geven we meer informatie over functies.

**D.** Haakjes **()** omgeven een expressie die een of meer argumenten bevat. Alle functies hebben minimaal één argument nodig. Een argument geeft een waarde door aan een functie.

**E.** De tabel waarnaar wordt verwezen, **Sales**.

**F.** De kolom waarnaar wordt verwezen, **[SalesAmount]**, in de tabel Sales. Door dit argument weet de functie SUM voor welke kolom een som moet worden samengesteld.

Voor een beter begrip van een DAX-formule kan het handig zijn om elk van de elementen op te splitsen in een taal waarin u dagelijks denkt en die u dagelijks spreekt. U kunt deze formule bijvoorbeeld lezen als:

> *Bereken (=) voor de meting met de naam Total Sales de som van de waarden uit de kolom [SalesAmount] in de tabel Sales.*
> 
> 

Wanneer deze meting wordt toegevoegd aan een rapport, worden door de meting waarden berekend en geretourneerd door verkoopbedragen op te tellen voor elk van de andere velden die we opnemen, bijvoorbeeld voor Cell Phones in the USA.

Misschien denkt u 'Doet deze meting niet hetzelfde als ik alleen het veld SalesAmount aan mijn rapport zou toevoegen?' En dan hebt u gelijk. Maar er is een goede reden om onze eigen meting te maken die waarden uit het veld SalesAmount optelt: we kunnen deze gebruiken als argument in andere formules. Dit kan nu wat verwarrend lijken, maar naarmate uw vaardigheden met DAX-formules beter worden, worden uw formules en uw model alleen maar efficiënter. De meting voor Total Sales wordt overigens weergegeven als een argument in andere formules verderop in dit artikel.

Laten we wat andere aspecten van deze formule bekijken. Meer in het bijzonder hebben we een functie geïntroduceerd, [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Functies zijn vooraf geschreven formules die het eenvoudiger maken om complexe berekeningen en bewerkingen uit te voeren met getallen, datums, tijd, tekst en meer. Later geven we meer informatie over functies.

U ziet ook dat de kolom [SalesAmount] wordt voorafgegaan door de tabel Sales waar de kolom deel van uitmaakt. Dit staat bekend als een volledig gekwalificeerde kolomnaam omdat het de naam van de kolom bevat, voorafgegaan door de naam van de tabel. Voor kolommen waarnaar in dezelfde tabel wordt verwezen, hoeft de tabelnaam niet in de formule worden opgenomen. Hierdoor worden lange formules die verwijzen naar veel kolommen korter en zijn ze gemakkelijker te lezen. Het is echter raadzaam de tabelnaam in uw metingformules op te nemen, zelfs als ze in dezelfde tabel staan.

> [!NOTE]
> Als een tabelnaam spaties, gereserveerde trefwoorden of niet-toegestane tekens bevat, moet u de tabelnaam tussen enkele aanhalingstekens plaatsen. U moet ook tabelnamen tussen aanhalingstekens plaatsen als de naam tekens bevat die buiten de alfanumerieke ANSI-tekenset vallen, ongeacht of uw landinstelling de tekenset wel of niet ondersteunt.
> 
> 

Het is belangrijk dat uw formules de juiste syntaxis hebben. In de meeste gevallen geldt dat als de syntaxis niet juist is, er een syntaxisfout wordt geretourneerd. In andere gevallen kan de syntaxis juist zijn, maar zijn de geretourneerde waarden niet wat u verwacht. De DAX-editor in Power BI Desktop biedt een suggestiefunctie. Dit is een functie waarmee u syntactisch juiste formules kunt maken door u te helpen de juiste elementen te selecteren.

We gaan een eenvoudige formule maken. Deze taak biedt u meer inzicht in de syntaxis van formules en laat zien hoe de suggestiefunctie in de formulebalk u kan helpen.

### <a name="task-create-a-measure-formula"></a>Taak: Maak een metingformule
Voor het uitvoeren van deze taak moet u het bestand Contoso Sales Sample for Power BI Desktop Preview openen.
    
1. Klik vanuit de Rapportweergave met de rechtermuisknop op de tabel **Sales** in de lijst met velden en klik op **New Measure**.
    
2. Vervang **Measure** in de formulebalk door een nieuwe metingnaam te typen, **Previous Quarter Sales**.
    
3. Na het gelijkteken typt u de eerste letters **CAL** en dubbelklikt u vervolgens op de functie die u wilt gebruiken. In deze formule wilt u de functie **CALCULATE** gebruiken.

   U gebruikt de functie CALCULATE om de bedragen te filteren die we willen laten optellen door een argument dat we doorgeven aan de functie CALCULATE. Dit is wat wordt aangeduid als functies nesten. De functie CALCULATE heeft minimaal twee argumenten. De eerste is de te evalueren expressie en de tweede is een filter.
   
4. Na het haakje **(** voor de functie **CALCULATE**, typt u **SUM**, gevolgd door een nog een haakje openen **(**. Nu moeten we een argument doorgeven aan de functie SUM.

5. Begin met het typen van **Sal** en selecteer vervolgens **Sales [SalesAmount]**, gevolgd door een haakje sluiten **)**. Dit is het eerste argument van de expressie voor de functie CALCULATE.
    
6. Typ een komma (**,**) gevolgd door een spatie om het eerste filter op te geven en typ daarna **PREVIOUSQUARTER**. Dit wordt ons filter.
    
   U gebruikt de functie PREVIOUSQUARTER voor tijdintelligentie om de SUM-resultaten te filteren op het vorige kwartaal.
    
7. Na de haakjes openen **()** voor de functie PREVIOUSQUARTER typt u **Calendar[DateKey]**.
    
   De functie PREVIOUSQUARTER heeft één argument, te weten een kolom met een aaneengesloten reeks datums. In ons geval is dat de kolom DateKey in de tabel Calendar.
    
8. Controleer of de beide argumenten die worden doorgegeven aan de functies PREVIOUSQUARTER en CALCULATE worden afgesloten door twee haakjes sluiten **))** te typen.
    
   De formule moet er nu zo uitzien:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey])) =**
    
9. Klik op het vinkje ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) in de formulebalk of druk op Enter om de formule te valideren en toe te voegen aan het model.

Prima! U hebt zojuist een meting met DAX gemaakt, en dat was zeker niet de eenvoudigste. Wat deze formule doet, is de totale verkoop van het vorige kwartaal berekenen, afhankelijk van de filters die in een rapport zijn toegepast. Als we bijvoorbeeld SalesAmount en de nieuwe meting voor Previous Quarter Sales in een diagram plaatsen en vervolgens Year en QuarterOfYear als slicers toevoegen, is dit het resultaat:

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

U hebt nu kennisgemaakt met verschillende belangrijke aspecten van DAX-formules. Om te beginnen, deze formule bevat twee functies. [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx), een functie voor tijdintelligentie, is genest als een argument dat wordt doorgegeven aan [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx), een filterfunctie. DAX-formules kunnen maximaal 64 geneste functies bevatten. Maar het is niet erg waarschijnlijk dat een formule zo veel geneste functies zal bevatten. Een dergelijke formule zou in feite zeer moeilijk te maken en te debuggen zijn, en snel is zo’n formule waarschijnlijk ook niet.

In deze formule hebt u ook filters gebruikt. Filters bakenen af wat er wordt berekend. In dit geval hebt u één filter als argument geselecteerd, wat in feite het resultaat van een andere functie is. Later geven we meer informatie over filters.

Ten slotte hebt u de functie CALCULATE gebruikt. Dit is een van de krachtigste functies in DAX. Bij het ontwerpen van modellen en het samenstellen van complexere formules zult u deze functie waarschijnlijk vaak gebruiken. Bespreking van de functie CALCULATE valt buiten het bereik van dit artikel, maar naarmate uw kennis van DAX toeneemt, is het belangrijk deze functie extra aandacht te geven.

### <a name="syntax-quickquiz"></a>QuickQuiz over syntaxis
1. Waarvoor wordt deze knop op de formulebalk gebruikt?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Waardoor wordt een kolomnaam in een DAX-formule altijd omgeven?

Aan het einde van dit artikel vindt u de antwoorden.

### <a name="functions"></a>Functies
Functies zijn vooraf gedefinieerde formules waarmee berekeningen in een bepaalde volgorde of met een bepaalde structuur worden uitgevoerd met behulp van specifieke waarden, argumenten genaamd. Argumenten kunnen bestaan uit andere functies, een andere formule, een expressie, kolomverwijzingen, getallen, tekst, logische waarden zoals TRUE of FALSE, of constanten.

DAX omvat de volgende functiecategorieën: [Datum en tijd](https://msdn.microsoft.com/library/ee634786.aspx), [Tijdintelligentie](https://msdn.microsoft.com/library/ee634763.aspx), [Informatie](https://msdn.microsoft.com/library/ee634552.aspx), [Logisch](https://msdn.microsoft.com/library/ee634365.aspx), [Wiskundig](https://msdn.microsoft.com/library/ee634241.aspx), [Statistisch](https://msdn.microsoft.com/library/ee634822.aspx), [Tekst](https://msdn.microsoft.com/library/ee634938.aspx), [Bovenliggend/onderliggend](https://msdn.microsoft.com/library/mt150102.aspx) en [Overige functies](https://msdn.microsoft.com/library/mt150101.aspx). Als u vertrouwd bent met functies in Excel-formules, zullen veel van de functies in DAX u bekend voorkomen. DAX-functies zijn echter uniek vanwege het volgende:

* Een DAX-functie heeft altijd betrekking op een volledige kolom of tabel. Als u alleen bepaalde waarden uit een tabel of kolom wilt gebruiken, kunt u filters toevoegen aan de formule.
* Als u berekeningen moet aanpassen op rijbasis, biedt DAX functies waarmee u de huidige rijwaarde of een gerelateerde waarde als een soort argument kunt gebruiken, voor het uitvoeren van berekeningen die per context verschillen. Later geven we meer informatie over context.
* DAX bevat veel functies die in plaats van een waarde een tabel retourneren. De tabel niet wordt weergegeven, maar wordt gebruikt voor invoer naar andere functies. U kunt bijvoorbeeld een tabel ophalen en vervolgens de afzonderlijke waarden daarin tellen of dynamische totalen in gefilterde tabellen of kolommen berekenen.
* DAX omvat tal van functies voor tijdintelligentie. Met deze functies kunt u datumbereiken definiëren of selecteren en daarop gebaseerde dynamische berekeningen uitvoeren. U kunt bijvoorbeeld totalen in parallelle perioden vergelijken.
* Excel heeft een heel populair functie, VERT.ZOEKEN. DAX-functies gebruiken geen cel of celbereik als verwijzing zoals VERT.ZOEKEN in Excel. DAX-functies gebruiken een kolom of tabel als verwijzing. Denk eraan dat u in Power BI Desktop werkt met een relationeel gegevensmodel. Het opzoeken van waarden in een andere tabel is heel eenvoudig en in de meeste gevallen hoeft u helemaal geen formule te maken.
  
  Zoals u ziet, kunnen functies in DAX u helpen bij het maken van zeer krachtige formules. Maar we hebben eigenlijk alleen nog maar naar de basisprincipes van functies gekeken. Naarmate uw vaardigheden met DAX toenemen, gaat u steeds meer formules maken die veel verschillende functies gebruiken. Een van de beste plekken om meer te weten te komen over elk van de DAX-functies is de [Naslag voor DAX-functies](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>QuickQuiz voor functies
1. Waarnaar verwijst een functie altijd?
2. Kan een formule meer dan één functie bevatten?
3. Welke functiecategorie zou u gebruiken om twee tekenreeksen samen te voegen tot één tekenreeks?

Aan het einde van dit artikel vindt u de antwoorden.

### <a name="context"></a>Context
Context is een van de belangrijkste DAX-concepten. Er zijn twee typen context in DAX, te weten rijcontext en filtercontext. We kijken eerst naar rijcontext.

**Rijcontext**

Rijcontext kan het beste worden beschouwd als zijnde de huidige rij. Dit is van toepassing wanneer een formule een functie bevat die filters gebruikt om één specifieke rij in een tabel te identificeren. De functie past een rijcontext toe voor elke rij in de tabel die wordt gefilterd. Dit type rijcontext geldt doorgaans voor metingen.

**Filtercontext**

Filtercontext is wat ingewikkelder dan rijcontext. U kunt filtercontext zien als een of meer filters die worden toegepast in een berekening waarmee een resultaat of waarde wordt bepaald.

Filtercontext komt niet in de plaats van rijcontext, maar wordt toegepast naast rijcontext. U kunt de in een berekening op te nemen waarden nog verder uitfilteren met een filtercontext die niet alleen de rijcontext aangeeft, maar ook alleen een bepaalde waarde (filter) in die rijcontext aangeeft.

Filtercontext is gemakkelijk te zien in uw rapporten. Wanneer u bijvoorbeeld TotalCost in een visualisatie opneemt, gevolgd door add Year en Region, definieert u een filtercontext waarmee een subset van gegevens wordt geselecteerd op basis van een bepaald jaar en bepaalde regio.

Waarom is filtercontext zo belangrijk voor DAX? Filtercontext kan het gemakkelijkst worden gebruikt door velden aan een visualisatie toe te voegen, maar kan ook worden toegepast in een DAX-formule door een filter te definiëren met behulp van functies zoals ALL, RELATED, FILTER, CALCULATE, op basis van relaties en andere metingen en kolommen. Laten we eens naar de volgende formule kijken die wordt gebruikt in een meting met de naam Store Sales:

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Voor een beter begrip van de formule gaan we deze opsplitsen, net zoals we met andere formules kunnen doen.

Deze formule bevat de volgende syntaxiselementen:

**A.** De naam van de meting, **Store Sales**.

**B.** De gelijkteken-operator (**=**) geeft het begin van de formule aan.

**C.** De functie **CALCULATE** berekent een expressie, als argument, in een context die wordt gewijzigd door de opgegeven filters.

**D.** Haakjes **()** omgeven een expressie die een of meer argumenten bevat.

**E.** Een meting **[Total Sales]** in dezelfde tabel als een expressie. De meting Total Sales heeft de formule: =SUM(Sales[SalesAmount]).

**F.** Een komma (**,**) scheidt het eerste expressie-argument van het filterargument.

**G.** De volledig gekwalificeerde kolom waarnaar wordt verwezen, **Channel[ChannelName]**. Dit is onze rijcontext. Elke rij in deze kolom geeft een kanaal aan: Store, Online, enzovoort.

**H.** De specifieke waarde, **Store**als filter. Dit is onze filtercontext.

Deze formule zorgt ervoor dat alleen verkoopwaarden die door de Total Sales-meting zijn gedefinieerd alleen worden berekend voor rijen in de kolom Channel[ChannelName] met de waarde “Store” als filter.

U kunt zich wel voorstellen dat het definiëren van filtercontext binnen een formule bijzonder krachtige mogelijkheden biedt. Om alleen al naar één bepaalde waarde in een gerelateerde tabel te kunnen verwijzen, is een van de vele voorbeelden daarvan. Maakt u zich geen zorgen als u het concept van context nog niet meteen kunt vatten. Wanneer u uw eigen formules gaat samenstellen, krijgt u een beter begrip van context en waarom dit in DAX zo belangrijk is.

### <a name="context-quickquiz"></a>QuickQuiz over context
1. Welke twee typen context zijn er?
2. Wat is filtercontext?
3. Wat is rijcontext?

Aan het einde van dit artikel vindt u de antwoorden.

## <a name="summary"></a>Samenvatting
Nu u de grondbeginselen van de belangrijkste concepten in DAX kent, kunt u zelf DAX-formules voor metingen gaan maken. DAX is misschien niet zo heel eenvoudig in de vingers te krijgen, maar er zijn veel hulpbronnen beschikbaar. Na het lezen van dit artikel en met zelfgemaakte formules te hebben geëxperimenteerd, kunt u meer leren over andere DAX-concepten en -formules die u kunt toepassen op uw eigen situatie. U hebt de beschikking over tal van DAX-hulpbronnen. De belangrijkste daarvan is de [Naslag voor Data Analysis Expressions (DAX)](https://msdn.microsoft.com/library/gg413422.aspx).

DAX maakt al een aantal jaren deel uit van andere Microsoft BI-programma’s zoals Power Pivot en tabellaire modellen van Analysis Services. Er is dus heel veel informatie beschikbaar. Er is nog meer informatie te vinden in handboeken, whitepapers en blogs van zowel Microsoft als toonaangevende BI-deskundigen. Ook de [Wiki over DAX Resource Center op TechNet](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) (Engelstalig) is een prima plek om te beginnen.

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

