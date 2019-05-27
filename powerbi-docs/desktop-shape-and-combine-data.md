---
title: Gegevens van meerdere gegevensbronnen vormgeven en combineren
description: In deze zelfstudie leert u hoe gegevens in Power BI Desktop kunt vormgeven en combineren
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 2835dd34ce5ba2d7bc6be8659b87eb1f550fdc28
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65514597"
---
# <a name="tutorial-shape-and-combine-data-in-power-bi-desktop"></a>Zelfstudie: Gegevens vormgeven en combineren in Power BI Desktop

Met **Power BI Desktop** kunt u verbinding maken met veel verschillende typen gegevensbronnen en de gegevens vervolgens vormgeven om aan uw behoeften te voldoen, zodat u visuele rapporten kunt maken die u met anderen kunt delen. Het *vormgeven* van gegevens betekent het omzetten van de gegevens, zoals de naam wijzigen van kolommen of tabellen, het wijzigen van tekst in getallen, het verwijderen van rijen, het instellen van de eerste rij als koptekst, enzovoort. Het *combineren* van gegevens betekent verbinding maken met twee of meer gegevensbronnen, deze naar wens vormgeven en ze samenvoegen tot één handige query.

In deze zelfstudie komen de volgende onderwerpen aan bod:

* Gegevens vormgeven met **Query-editor**
* Verbinding maken met een gegevensbron
* Verbinding maken met een andere gegevensbron
* Deze gegevensbronnen combineren en een gegevensmodel maken voor gebruik in rapporten

Deze zelfstudie laat zien hoe u een query kunt vormgeven met Power BI Desktop, waarbij enkele van de meest algemene taken nader worden toegelicht. De hier gebruikte query wordt uitvoeriger beschreven, waaronder het maken van een volledig nieuwe query, in [Aan de slag met Power BI Desktop](desktop-getting-started.md).

Het is handig om te weten dat de **Query-editor** in Power BI Desktop op ruime schaal gebruikmaakt van contextmenu's, samen met het lint. Het meeste van wat u kunt selecteren in het lint **Transformeren** is ook beschikbaar door met de rechtermuisknop op een item (zoals een kolom) te klikken en een keuze te maken in het menu dat verschijnt.

## <a name="shape-data"></a>Gegevens vormgeven
Wanneer u gegevens in de Query-editor vormgeeft, geeft u stapsgewijze instructies (die de Query-editor voor u uitvoert) om de gegevens aan te passen terwijl Query-editor de gegevens laadt en presenteert. De oorspronkelijke gegevensbron wordt daardoor niet beïnvloed; alleen deze specifieke weergave van de gegevens wordt aangepast, ofwel *vormgegeven*.

De stappen die u opgeeft (zoals de naam van een tabel wijzigen, een gegevenstype transformeren of kolommen verwijderen), worden vastgelegd door de Query-editor en elke keer dat deze query verbinding maakt met de gegevensbron, worden die stappen uitgevoerd zodat de gegevens altijd op de door u bepaalde manier worden vormgegeven. Dit proces vindt plaats wanneer u de Query-editor van Power BI Desktop gebruikt, maar vindt ook plaats voor iedereen die gebruikmaakt van de door u gedeelde query, zoals in de **Power BI**-service. Deze stappen worden in volgorde vastgelegd in het deelvenster **Query-instellingen** onder **Toegepaste stappen**.

De volgende afbeelding toont het deelvenster **Query-instellingen** voor een query die is vormgegeven. In de volgende alinea’s bekijken we elk van deze stappen.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished2.png)

Met behulp van de pensioneringsgegevens uit [Aan de slag met Power BI Desktop](desktop-getting-started.md), die we hebben gevonden door verbinding te maken met een gegevensbron op internet, gaan we die gegevens vormgeven op basis van onze behoeften.

Om te beginnen, gaan we een aangepaste kolom toevoegen voor het berekenen van de positie, met als basis dat alle gegevens gelijke factoren zijn, en deze vergelijken met de bestaande kolom _Positie_.  Hier volgt het lint **Kolom toevoegen**, met een pijl naar de knop **Aangepaste kolom** waarmee u een aangepaste kolom kunt toevoegen.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumn.png)

Voer in het dialoogvenster **Aangepaste kolom** bij **Nieuwe kolomnaam**, _Nieuwe positie_ in, en bij **Aangepaste kolomformule**, het volgende:

    ([Cost of living] + [Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 8

Zorg ervoor dat het statusbericht _'Er zijn geen syntaxisfouten gedetecteerd.'_ is en klik op **OK**.

![](media/desktop-shape-and-combine-data/shapecombine_customcolumndialog.png)

Om kolomgegevens consistent te houden, kunnen we de nieuwe kolomwaarden naar gehele getallen transformeren. U hoeft alleen met de rechtermuisknop op de kolomkop te klikken en **Type wijzigen \> Geheel getal** te selecteren om ze om te zetten. 

Als u meer dan één kolom wilt selecteren, selecteert u eerst een kolom en houdt u **SHIFT** ingedrukt, selecteert u extra aangrenzende kolommen en klikt u vervolgens met de rechtermuisknop op een kolomkop om alle geselecteerde kolommen te wijzigen. U kunt ook de **CTRL**-toets gebruiken om niet-aaneengesloten kolommen te selecteren.

![](media/desktop-shape-and-combine-data/shapecombine_changetype2.png)

U kunt ook kolom-gegevenstypen *transformeren* uit het lint **Transformeren**. Hier ziet u het lint **Transformeren**, met een pijl die wijst naar de knop **Gegevenstype**, waarmee u het huidige gegevenstype in een ander gegevenstype kunt omzetten.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

De optie **Toegepaste stappen** in **Query-instellingen** laat alle vormgevingsstappen zien die op de gegevens worden toegepast. Als ik een stap uit het vormgevingsproces wil verwijderen, selecteer ik gewoon de **X** links van de stap. In de volgende afbeelding geeft **Toegepaste stappen** de tot nu toe uitgevoerde stappen aan: verbinding maken met de website (**Bron**); de tabel selecteren (**Navigatie**); en tijdens het laden van de tabel heeft Query-editor kolommen op tekstbasis automatisch gewijzigd van *Tekst* in *Geheel getal* (**Type gewijzigd**). De laatste twee stappen laten onze vorige acties zien met **Aanpassing toegevoegd** en **Gewijzigd type 1**. 

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly2.png)

Voordat we met deze query kunnen werken, moeten we enkele wijzigingen aanbrengen om de bijbehorende gegevens te krijgen zoals we willen:

* *De classificaties aanpassen door het verwijderen van een kolom* - wij hebben besloten dat **Kosten van levensonderhoud** geen factor in onze resultaten is. Na het verwijderen van deze kolom zien we het probleem dat de gegevens ongewijzigd blijven, al is het eenvoudig op te lossen met behulp van Power BI Desktop. In dat geval ziet u een handige functie van **Toegepaste stappen** in de Query.
* *Enkele fouten corrigeren* – omdat we een kolom hebben verwijderd, moeten we onze berekeningen in de kolom **Nieuwe positie** aanpassen. Dit omvat het wijzigen van een formule.
* *Sorteer de gegevens* - op basis van de kolommen **Nieuwe positie** en **Positie**. 
* *Gegevens vervangen* - we laten zien hoe we een bepaalde waarde vervangen en wat de noodzaak is van het invoegen van een **Toegepaste stap**.
* *Wijzig de naam van de tabel*- **Table 0** is geen handige beschrijving, maar dat kan eenvoudig worden gewijzigd.

Voor het verwijderen van de kolom **Kosten van levensonderhoud** selecteert u de kolom en selecteert u het tabblad **Start** op het lint, gevolgd door **Kolommen verwijderen**, zoals weergegeven in de volgende afbeelding.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnscostofliving.png)

Zoals u ziet zijn de waarden voor _Nieuwe positie_ niet gewijzigd; dit wordt veroorzaakt door de volgorde van de stappen. Omdat de Query-editor de stappen sequentieel registreert, weliswaar onafhankelijk van elkaar, kunt u elke **Toegepaste stap** hoger of lager in de reeks zetten. U hoeft alleen maar met de rechtermuisknop te klikken op een stap en in Query Editor wordt een menu weergegeven waarmee u het volgende doen: **Naam wijzigen**, **Verwijderen**, **Verwijderen** **Tot einde** (verwijdert de huidige stap en alle volgende stappen), **Omhoog verplaatsen** of **Omlaag verplaatsen**. Ga verder naar de laatste stap _Verwijderde kolommen_, net boven de stap _Aanpassing toegevoegd_.

![](media/desktop-shape-and-combine-data/shapecombine_movestep.png)

Selecteer vervolgens de stap _Aanpassing toegevoegd_. U ziet in de gegevens nu een _Foutmelding_ die we moeten behandelen. 

![](media/desktop-shape-and-combine-data/shapecombine_error2.png)

Er zijn enkele manieren om meer informatie over elke fout te krijgen. U kunt de cel selecteren (zonder te klikken op het woord **Fout**) of rechtstreeks klikken op het woord **Fout**. Als u de cel selecteert *zonder* rechtstreeks op het woord **Fout** te klikken, geeft Query-editor de foutinformatie weer aan de onderkant van het venster.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo2.png)

Als u rechtstreeks op het woord *Fout* klikt, maakt Query een **Toegepaste stap** in het deelvenster **Query-instellingen** en wordt er informatie over de fout weergegeven. We willen deze route niet nemen, selecteer daarom **Annuleren**.

Om fouten te herstellen, selecteert u de kolom _Nieuwe positie_. Geef vervolgens de formule van de gegevens van de kolom weer door het **Weergave**-lint te openen en het selectievakje **Formulebalk** te selecteren. 

![](media/desktop-shape-and-combine-data/shapecombine_formulabar.png)

Nu kunt u de parameter _Kosten van levensonderhoud_ verwijderen en de deler verlagen, door het wijzigen van de formule in het volgende: 

    Table.AddColumn(#"Removed Columns", "New Rank", each ([Weather] + [Health care quality] + [Crime] + [Tax] + [Culture] + [Senior] + [#"Well-being"]) / 7)

Selecteer het groene vinkje aan de linkerkant van het formulevak of druk op **Enter**. De gegevens moeten worden vervangen door gewijzigde waarden en de stap **Aanpassing toegevoegd** moet nu *zonder fouten* worden voltooid.

> [!NOTE]
> U kunt ook **Fouten verwijderen** (met het lint of het snelmenu), waardoor alle rijen met fouten worden verwijderd. In dit geval zouden alle rijen uit onze gegevens worden verwijderd, maar dat is niet wat we wilden. We vinden al onze gegevens prima en willen die in de tabel houden.

Nu sorteren we de gegevens op basis van de kolom **Nieuwe positie**. Selecteer eerst de laatste toegepaste stap, **Gewijzigd type 1** om de meest recente gegevens te krijgen. Selecteer vervolgens de vervolgkeuzelijst naast de kolomkop **Nieuwe positie** en selecteer **Oplopend sorteren**.

![](media/desktop-shape-and-combine-data/shapecombine_sort.png)

U ziet dat de gegevens nu worden gesorteerd volgens **Nieuwe positie**.  Als u echter in de kolom **Positie** zoekt, ziet u dat de gegevens niet goed zijn gesorteerd in gevallen waar de waarde **Nieuwe positie** gelijk is. Om dit op te lossen, selecteert u de kolom **Nieuwe positie** en wijzigt u de formule in de **Formulebalk** naar het volgende:

    = Table.Sort(#"Changed Type1",{{"New Rank", Order.Ascending},{"Rank", Order.Ascending}})

Selecteer het groene vinkje aan de linkerkant van het formulevak of druk op **Enter**. De rijen moeten nu worden gerangschikt overeenkomstig zowel _Nieuwe positie_ als _Positie_.

Bovendien kunt u een **Toegepaste stap** overal in de lijst selecteren en doorgaan met het vormgeven van de gegevens op dat punt in de reeks. De Query-editor voegt automatisch een nieuwe stap in, onmiddellijk na de geselecteerde **Toegepaste stap**. Laten we dat eens proberen.

Selecteer eerst de **Toegepaste stap** vóór het toevoegen van de aangepaste kolom. Dit moet de stap _Verwijderde kolommen_ zijn. Hier zullen we de waarde van de positie _Weer_ in Arizona vervangen. Klik met de rechtermuisknop op de juiste cel die de ranking _Weer_ van Arizona bevat en selecteer *Waarden vervangen...*  vanuit het menu dat verschijnt. Onthoud welke **Toegepaste stap** momenteel is geselecteerd (de stap voorafgaand aan de stap _Aanpassing toegevoegd_).

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues2.png)

Omdat we een stap invoegen, geeft de Query-editor daarvoor een waarschuwing: de daaropvolgende stappen zouden de query kunnen verbreken. Daarom moeten we zorgvuldig en doordacht te werk gaan. Aangezien dit een zelfstudie is en we een heel handige functie van de Query-editor bespreken om te laten zien hoe u stappen kunt maken, verwijderen, invoegen en anders kunt rangschikken, gaan we verder en selecteren we **Invoegen**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Wijzig de waarde in _51_ en de gegevens voor Arizona worden vervangen. Wanneer u een nieuwe toegepaste stap maakt, geeft de Query-editor deze een naam op basis van de actie, in dit geval **Waarde vervangen**. Wanneer de query meer dan één stap met dezelfde naam bevat, voegt de Query-editor aan elke volgende **Toegepaste stap** een getal toe (in oplopende volgorde) om ze van elkaar te onderscheiden.

Selecteer nu de laatste **Toegepaste stap**, _Gesorteerde rijen_, en zie hoe de gegevens met betrekking tot de nieuwe ranking van Arizona zijn gewijzigd.  Dit is omdat we de stap _Vervangen waarde_ op de juiste plaats hebben ingevoegd, voor de stap _Aanpassing toegevoegd_.

Hoe het ook zij, dit is een goed voorbeeld van hoe krachtig en veelzijdig Query-editor kan zijn.

Tot slot willen we de naam van de tabel meer beschrijvend maken. Wanneer u rapporten gaat maken, is het bijzonder handig om beschrijvende tabelnamen te hebben, vooral wanneer er verbinding met meerdere gegevensbronnen wordt gemaakt en deze allemaal worden weergegeven in het deelvenster **Velden** van de **Rapport**weergave.

De tabelnaam kan eenvoudig worden gewijzigd: typ in het deelvenster **Query-instellingen**, onder **Eigenschappen**, de nieuwe naam van de tabel, zoals weergegeven in de volgende afbeelding, en druk op **Enter**. Laten we deze tabel *RetirementStats* noemen.

![](media/desktop-shape-and-combine-data/shapecombine_renametable2.png)

Goed, we hebben die gegevens vormgegeven voor zover dat nodig was. Laten we nu verbinding maken met een andere gegevensbron en gegevens gaan combineren.

## <a name="combine-data"></a>Gegevens combineren
De informatie over de verschillende staten is best interessant en handig voor extra analyses en query's. Maar er is wel één probleem: de meeste van die gegevens gebruiken de tweeletterige afkorting als code voor staten, niet de volledige naam van de staat. We hebben een manier nodig om namen van staten te koppelen aan hun afkortingen.

Maar gelukkig is er een andere openbare gegevensbron die precies dat doet, maar er moet dan wel eerst aardig wat worden aangepast voordat die bron aan de pensioneringstabel kan worden gekoppeld. Hier is de webbron voor staatafkortingen:

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Op het **Start**-lint van de Query-editor selecteren we **Nieuwe bron \> Web** en typen we het adres. We selecteren **Verbinden** en de Navigator laat zien wat er op die webpagina werd gevonden.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator2.png)

We selecteren **Codes en afkortingen...** omdat hierin de gewenste gegevens zijn opgenomen, maar het kost wel wat werk om de gegevens uit die tabel op de juiste manier aan te passen.

> [!TIP]
> Is er een snellere of gemakkelijkere manier om de onderstaande stappen uit te voeren? Jazeker, we zouden een *relatie* tussen de twee tabellen kunnen maken en de gegevens vormgeven op basis van die relatie. De volgende stappen zijn nog steeds prima geschikt voor het werken met tabellen, maar denk er wel aan dat u met relaties snel gegevens uit meerdere tabellen kunt gebruiken.
> 
> 

We voeren de volgende stappen uit om deze gegevens vorm te geven:

* Verwijder de eerste rij - deze is een resultaat van de manier waarop de tabel van die webpagina werd gemaakt en is niet nodig. Op het **Start**lint selecteren we **Minder rijen \> Minder rijen \> Bovenste rijen verwijderen**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

Het venster **Bovenste rijen verwijderen** wordt weergegeven, waarin u kunt opgeven hoeveel rijen u wilt verwijderen.

>[!NOTE]
>Als Power BI per ongeluk de headers-tabel importeert als een rij in de gegevenstabel, kunt u **Gebruik eerste rij als headers** selecteren uit het tabblad **Start** of vanuit het tabblad **Transformeren** in het lint, om uw tabel te herstellen.

* Verwijder de onderste 26 rijen; dat zijn alle territoriale gebieden en die hebben we nu niet nodig. Op het **Start**lint selecteren we **Minder rijen \> Minder rijen \> Onderste rijen verwijderen**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* Omdat de tabel RetirementStats geen informatie voor Washington DC bevat, moeten we dat uit onze lijst filteren. Klik op de vervolgkeuzepijl naast de kolom Region Status en schakel het selectievakje naast **Federal district** uit.

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Verwijder enkele overbodige kolommen: we hebben alleen de koppeling van een staat met de officiële afkorting van twee letters nodig, dus kunnen we de volgende kolommen verwijderen: **Kolom1**, **Kolom3**, **Kolom4** en vervolgens **Kolom6** tot en met **Kolom11**. Selecteer eerst **Kolom1**, houd de **CTRL**-toets ingedrukt en selecteer de andere kolommen die moeten worden verwijderd (op deze manier kunt u meerdere niet-aaneengesloten kolommen selecteren). Selecteer op het tabblad Start van het lint de optie **Kolommen verwijderen \> Kolommen verwijderen**.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

>[!NOTE]
>Dit is een goed moment om te vermelden dat de *reeks* toegepaste stappen in de Query-editor belangrijk is en van invloed kan zijn op hoe de gegevens worden vormgegeven. Het is ook belangrijk om na te gaan hoe de ene stap van invloed kan zijn op een volgende stap. Als u een stap uit de Toegepaste stappen verwijdert, werken daarop volgende stappen mogelijk niet meer zoals oorspronkelijk beoogd vanwege de impact van de reeks stappen van de query.

>[!NOTE]
>Wanneer u het venster van Query-editor smaller maakt, worden enkele items op het lint verkleind om de zichtbare ruimte zo goed mogelijk te benutten. Wanneer u het venster van Query-editor breder maakt, worden de items op het lint vergroot om de extra ruimte voor het lint zo goed mogelijk te benutten.

* Wijzig de naam van de kolommen en van de tabel zelf. Zoals gewoonlijk zijn er een aantal manieren om de naam van een kolom te wijzigen; selecteer eerst de kolom en selecteer vervolgens **Naam wijzigen** op het tabblad **Transformeren** op het lint, of klik met de rechtermuisknop en selecteer **Naam wijzigen...** in het snelmenu. De volgende afbeelding laat pijlen zien die beide opties aanwijzen; u hoeft er maar één te kiezen.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Laten we de naam wijzigen in *State Name* en *State Code*. U wijzigt de naam van de tabel door de naam te typen in het vak **Naam** van het deelvenster **Query-instellingen**. Laten we deze tabel *StateCodes* noemen.

Nu we de tabel StateCodes de gewenste vorm hebben gegeven, gaan we deze twee tabellen, of query's, samenvoegen in één tabel. Omdat de tabellen die we nu hebben, het resultaat zijn van de query's die we op de gegevens hebben toegepast, worden ze vaak aangeduid als *query's*.

Er zijn twee manieren om query's te combineren: *samenvoegen* en *toevoegen*.

Wanneer u een of meer kolommen hebt die u wilt toevoegen aan een andere query gaat u de query’s **samenvoegen**. Wanneer u extra rijen met gegevens hebt die u aan een bestaande query wilt toevoegen, gaat u de query **toevoegen**.

In dit geval gaan we query's samenvoegen. Als eerste selecteren we in het linkerdeelvenster van de Query-editor de query *waarin* we de andere query willen samenvoegen, in dit geval is dat *RetirementStats*. Selecteer vervolgens **Combineren \> Query's samenvoegen** op het tabblad **Start** van het lint.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

U wordt mogelijk gevraagd de privacyniveaus in te stellen om te controleren of de gegevens worden gecombineerd zonder dat er gegevens worden opgenomen of overgedragen waarvan u niet wilt dat ze worden overgedragen.

Het venster **Samenvoegen** wordt weergegeven, waarin wordt gevraagd welke tabel er in de geselecteerde tabel moet worden samengevoegd, gevolgd door de overeenkomende kolommen die worden gebruikt voor het samenvoegen. Selecteer State in de *RetirementStats*-tabel (query) en selecteer de query *StateCodes* (eenvoudig in dit geval, omdat er maar één andere query is – wanneer u verbinding met veel gegevensbronnen maakt, zijn er veel query's waaruit u kunt kiezen). Wanneer we de juiste overeenkomende kolommen selecteren – **State** uit *RetirementStats* en **State Name** uit *StateCodes* – ziet het venster **Samenvoegen** er als volgt uit en is de knop **OK** ingeschakeld.

![](media/desktop-shape-and-combine-data/shapecombine_merge2.png)

Er wordt een **NewColumn** aan het einde van de query gemaakt, met daarin de inhoud van de tabel (query) die met de bestaande query is samengevoegd. Alle kolommen uit de samengevoegde query zijn samengevoegd in de **NewColumn**, maar u kunt ervoor kiezen de tabel **uit te breiden** om elke gewenste kolom op te nemen.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Als u de samengevoegde tabel wilt uitvouwen en wilt aangeven welke kolommen u wilt opnemen, selecteert u het uitvouwpictogram (![Uitvouwen](media/desktop-shape-and-combine-data/icon.png)). Het venster **Uitvouwen** wordt weergegeven.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

In dit geval hebben we alleen de kolom **State Code** nodig. Daarom selecteren we alleen die kolom en vervolgens **OK**. We schakelen het selectievakje ‘Oorspronkelijke kolomnaam gebruiken als voorvoegsel’ uit omdat we die niet nodig hebben en ook niet willen. Als we het selectievakje ingeschakeld zouden laten, krijgt de samengevoegde kolom de naam **NewColumn.State Code** (de naam van de oorspronkelijke kolom, ofwel **NewColumn**, gevolgd door een punt, gevolgd door de naam van de kolom die in de query wordt opgenomen).

>[!NOTE]
>Wilt u uitproberen hoe u die **NewColumn**-tabel kunt opzetten? U kunt wat experimenteren en als de resultaten u niet bevallen, kunt u die stap gewoon verwijderen uit de lijst **Toegepaste stappen** in het deelvenster **Query-instellingen**. De query krijgt dan weer de status die gold voordat de stap **Uitbreiden** werd toegepast. U kunt de stap zo vaak uitvoeren als u wilt, totdat u met het uitbreidproces het gewenste resultaat hebt bereikt.

We hebben nu één query (tabel) waarin twee gegevensbronnen zijn samengevoegd, die elk volgens onze behoeften zijn vormgegeven. Deze query kan fungeren als basis voor een groot aantal extra, interessante gegevensverbindingen, zoals statistieken voor huisvestingskosten, demografische gegevens of werkgelegenheid in een staat.

Als u wijzigingen wilt toepassen en de Query-editor wilt sluiten, selecteert u **Sluiten & toepassen** in het tabblad **Start** op het lint. De getransformeerde gegevensset wordt weergegeven in Power BI Desktop en is klaar voor het maken van rapporten.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Volgende stappen
U kunt allerlei handelingen uitvoeren met Power BI Desktop. Bekijk de volgende bronnen voor meer informatie over de vele mogelijkheden:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Query Overview with Power BI Desktop](desktop-query-overview.md) (Queryoverzicht met Power BI Desktop)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Verbinding maken met gegevens in Power BI Desktop](desktop-connect-to-data.md)
* [Algemene querytaken in Power BI Desktop](desktop-common-query-tasks.md)   

