---
title: Modelrelaties in Power BI Desktop
description: Inleidende theorie over modelrelaties in Power BI Desktop
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/15/2019
ms.author: v-pemyer
ms.openlocfilehash: 0029d275e5180c29e8653f549d8450014362b59b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75304247"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Modelrelaties in Power BI Desktop

Dit artikel is geschreven voor iedereen die Import-gegevensmodellen maakt met Power BI Desktop. Het is een belangrijk onderwerp over het ontwerpen van modellen dat essentieel is voor het leveren van intuïtieve, nauwkeurige en optimale modellen.

Voor een diepgaande bespreking over optimaal modelontwerp, met inbegrip van tabelrollen en -relaties, raadpleegt u het artikel [Het sterschema en het belang ervan voor Power BI begrijpen](guidance/star-schema.md) artikel.

## <a name="relationship-purpose"></a>Doel van relatie

Power BI-relaties worden gebruikt om filters die zijn toegepast op de kolommen van modeltabellen door te geven aan andere modeltabellen. Filters worden doorgegeven zolang er een relatiepad is dat kan worden gevolgd. Hierbij kunnen filters aan meerdere tabellen worden doorgegeven.

Relatiepaden zijn deterministisch, wat betekent dat filters altijd op dezelfde manier worden doorgegeven en zonder willekeurige variatie. Relaties kunnen echter worden uitgeschakeld of gewijzigde filtercontext door modelberekeningen hebben die gebruikmaken van specifieke DAX-functies. Bekijk het onderwerp [Relevante DAX-functies](#relevant-dax-functions) verderop in dit artikel voor meer informatie.

> [!IMPORTANT]
> Het is belangrijk om te begrijpen dat modelrelaties geen gegevensintegriteit afdwingen. Bekijk het onderwerp [Beoordeling van relaties](#relationship-evaluation) verderop in dit artikel voor meer informatie. In deze onderwerpen wordt uitgelegd hoe modelrelaties zich gedragen wanneer er problemen zijn met de gegevensintegriteit van uw gegevens.

Laten we eens kijken hoe relaties filters doorgeven met een geanimeerd voorbeeld.

![Geanimeerd voorbeeld van het doorgeven van filters door relatie](media/desktop-relationships-understand/animation-filter-propagation.gif)

In dit voorbeeld bestaat het model uit vier tabellen: **Categorie**, **Product**, **Jaar** en **Verkoop**. De tabel **Categorie** is gekoppeld aan de tabel **Product** en de tabel **Product** is gekoppeld aan de tabel **Verkoop**. De tabel **Jaar** is ook gekoppeld aan de tabel **Verkoop**. Alle relaties zijn een-op-veel (de details worden verderop in dit artikel beschreven).

Een query (die kan zijn gegenereerd door een Power BI-kaartvisual) vraagt de totale verkopen aan voor verkooporders die zijn geplaatst voor een enkele categorie, **Cat-A**, en voor één jaar, **CY2018**. Daarom kunt u filters zien die zijn toegepast op de tabellen **Categorie** en **Jaar**. Het filter voor de tabel **Categorie** wordt doorgegeven aan de tabel **Product** om twee producten te isoleren die zijn toegewezen aan de categorie **Cat-A**. Vervolgens worden de filters van de tabel **Product** doorgegeven aan de tabel **Verkoop** om slechts twee verkooprijen voor deze producten te isoleren. Deze twee verkooprijen vertegenwoordigen de verkoop van producten die zijn toegewezen aan de categorie **Cat-A**. De gecombineerde hoeveelheid is 14 eenheden. Tegelijkertijd wordt het filter in de tabel **Jaar** doorgegeven om de tabel **Verkoop** verder te filteren, wat resulteert in slechts één verkooprij voor producten die zijn toegewezen aan categorie **Cat-A** en die zijn besteld in jaar **CY2018**. De hoeveelheid die door de query wordt geretourneerd, is 11 eenheden. Houd er rekening mee dat als er meerdere filters worden toegepast op een tabel (zoals de tabel **Verkoop** in dit voorbeeld), het altijd gaat om een AND-bewerking, waarbij alle voorwaarden waar moeten zijn.

### <a name="disconnected-tables"></a>Losgekoppelde tabellen

Het is ongebruikelijk dat een modeltabel niet aan een andere modeltabel is gekoppeld. Een dergelijke tabel in een geldig modelontwerp kan worden beschreven als een _losgekoppelde tabel_. Een losgekoppelde tabel is niet bedoeld om filters door te geven aan andere modeltabellen. In plaats daarvan wordt invoer van de gebruiker geaccepteerd (mogelijk met een slicervisual), zodat modelberekeningen de invoerwaarde op een zinvolle manier kunnen gebruiken. Denk bijvoorbeeld aan een losgekoppelde tabel die wordt geladen met verschillende wisselkoersen. Als u een filter opgeeft voor één valutawaarde, kan deze worden gebruikt door een meetexpressie om verkoopwaarden te converteren.

Met de What if-parameter van Power BI Desktop kan een losgekoppelde tabel worden gemaakt. Bekijk het artikel [Een What if-parameter maken en gebruiken om variabelen in Power BI Desktop te visualiseren](desktop-what-if.md) voor meer informatie.

## <a name="relationship-properties"></a>Eigenschappen van relaties

Een modelrelatie verbindt één kolom in een tabel met één kolom in een andere tabel. (Er is één gespecialiseerd geval waarbij deze vereiste niet waar is, en dit geldt alleen voor relaties met meerdere kolommen in DirectQuery-modellen. Zie het artikel over de DAX-functie [COMBINEVALUES](/dax/combinevalues-function-dax) voor meer informatie.)

> [!NOTE]
> Het is niet mogelijk om een kolom te koppelen aan een andere kolom _in dezelfde tabel_. Dit wordt soms verward met het definiëren van een beperking op de refererende sleutel voor een relationele database, die naar dezelfde tabel verwijst. Dit concept voor relationele databases kan worden gebruikt voor het opslaan van relaties tussen bovenliggende en onderliggende items (bijvoorbeeld elk werknemersrecord is gerelateerd aan de werknemer 'rapporten aan'). Een modelhiërarchie op basis van dit type relatie kan niet worden opgelost door modelrelaties te maken. Bekijk het artikel [Bovenliggende en onderliggende functies](/dax/parent-and-child-functions-dax) om dit te bewerkstelligen.

### <a name="cardinality"></a>Kardinaliteit

Elke modelrelatie moet worden gedefinieerd met een type kardinaliteit. Er zijn vier opties voor het type kardinaliteit, die de gegevenskenmerken van de gerelateerde kolommen 'van' en 'aan' vertegenwoordigen. De 'een'-zijde betekent dat de kolom unieke waarden bevat. De 'twee'-zijde betekent dat de kolom dubbele waarden kan bevatten.

> [!NOTE]
> Als een bewerking voor gegevensvernieuwing probeert dubbele waarden te laden in een kolom met een 'een'-zijde, mislukt de volledige gegevensvernieuwing.

De vier opties en hun verkorte notaties worden beschreven in de volgende lijst:

- Een-op-veel (1:\*)
- Veel-op-een (\*:1)
- Een-op-een (1:1)
- Veel-op-veel (\*:\*)

Wanneer u een relatie maakt in Power BI Desktop wordt het type kardinaliteit automatisch gedetecteerd en ingesteld door de ontwerper. De ontwerper kan dit doen omdat deze het model doorzoekt om te achterhalen welke kolommen unieke waarden bevatten. Bij Import-modellen wordt gebruikgemaakt van interne opslagstatistieken. Bij DirectQuery-modellen verzendt het de profileringsquery's naar de gegevensbron. Soms kan de ontwerper zich echter vergissen. Dit gebeurt omdat er nog gegevens moeten worden geladen in de tabellen of omdat kolommen waarvan u verwacht dat deze dubbele waarden bevatten, momenteel enkele waarden bevatten. In beide gevallen kunt u het type kardinaliteit bijwerken als een kolom met een 'een'-zijde enkele waarden bevat (of als de tabel nog moet worden geladen met rijen gegevens).

De kardinaliteitsopties **Een-op-veel** en **Veel-op-een** zijn in wezen hetzelfde, en ze zijn ook de meest voorkomende typen kardinaliteit.

Bij het configureren van een een-op-veel- of veel-op-een-relatie, kiest u de opties die overeenkomt met de volgorde waarin u de kolommen hebt gekoppeld. Denk na over hoe u de relatie van de tabel **Product** met de tabel **Verkoop** zou configureren met behulp van de kolom **ProductID** die in elke tabel staat. Het type kardinaliteit wordt _Een-op-veel_, omdat de kolom **ProductID** in de tabel **Product** enkele waarden bevat. Als u de tabellen in omgekeerde volgorde hebt gekoppeld, **Verkoop** aan **Product**, wordt de kardinaliteit _Veel-op-een_.

Een **Een-op-een**-relatie betekent dat beide kolommen enkele waarden bevatten. Dit type kardinaliteit is niet gebruikelijk en doet vermoeden dat het modelontwerp niet optimaal is, omdat er redundante gegevens worden opgeslagen.<!-- For guidance on using this cardinality type, see the [One-to-one relationship guidance](guidance/relationships-one-to-one) article.-->

Een **Veel-op-veel**-relatie betekent dat beide kolommen dubbele waarden kunnen bevatten. Dit type kardinaliteit wordt zelden gebruikt. Het is doorgaans handig bij het ontwerpen van complexe modelvereisten. Zie [Richtlijnen voor veel-op-veel-relaties](guidance/relationships-many-to-many.md) voor hulp bij het gebruik van dit type kardinaliteit.

> [!NOTE]
> Het type kardinaliteit Veel-op-veel wordt momenteel niet ondersteund voor modellen die zijn ontwikkeld voor Power BI Report Server.

> [!TIP]
> In de modelweergave van Power BI Desktop kunt u het type kardinaliteit van een relatie bekijken door de indicatoren (1 of \*) aan beide zijden van de relatielijn te bekijken. Als u wilt bepalen welke kolommen gekoppeld zijn, moet u de relatielijn selecteren of de muisaanwijzer op de relatielijn houden om de kolommen te markeren.

### <a name="cross-filter-direction"></a>Kruisfilterrichting

Elke modelrelatie moet worden gedefinieerd met een kruisfilterrichting. Uw selectie bepaalt de richting(en) die door de filters worden doorgegeven. De mogelijke opties voor kruislings filteren zijn afhankelijk van het type kardinaliteit.

| Type kardinaliteit | Kruisfilteropties |
| --- | --- |
| Een-op-veel (of veel-op-een) | Enkel<br>Beide |
| Een-op-een | Beide |
| Veel-op-veel | Enkel (Tabel1 naar tabel2)<br>Enkel (Tabel2 naar tabel1)<br>Beide |

De kruisfilterrichting _Enkel_ betekent 'een richting' en _Beide_ betekent 'beide richtingen'. Een relatie die wordt gefilterd in beide richtingen, wordt doorgaans beschreven als _bidirectioneel_.

Voor een-op-veel-relaties is de kruisfilterrichting altijd vanaf de 'een'-zijde en optioneel vanaf de 'veel'-zijde (bidirectioneel). Voor een-op-een-relaties is de kruisfilterrichting altijd vanuit beide tabellen. Ten slotte kunt u voor de veel-op-veel-relaties een kruisfilterrichting van één van de tabellen of van beide tabellen gebruiken. Houd er rekening mee dat wanneer het type kardinaliteit een 'een'-zijde bevat, deze filters altijd van die zijde worden doorgegeven.

Wanneer de kruisfilterrichting is ingesteld op **Beide**, is er een extra eigenschap beschikbaar om bidirectionele filtering toe te passen wanneer regels voor beveiliging op rijniveau worden afgedwongen. Voor meer informatie over beveiliging op rijniveau raadpleegt u het artikel [Beveiliging op rijniveau met Power BI Desktop](desktop-rls.md).

Het wijzigen van de kruisfilterrichting voor relaties, inclusief het uitschakelen van het doorgeven van filters, kan ook worden uitgevoerd door een modelberekening. Dit wordt bereikt met behulp van de DAX-functie [CROSSFILTER](/dax/crossfilter-function).

Bidirectionele relaties kunnen een negatieve invloed hebben op de prestaties. Als u een bidirectionele relatie wilt configureren, kan dit leiden tot dubbelzinnige paden voor het doorgeven van filters. In dit geval kan Power BI Desktop de relatiewijziging mogelijk niet doorvoeren en wordt er een foutbericht weer gegeven. Soms kan Power BI Desktop echter toestaan dat er ambigue relatiepaden tussen tabellen worden gedefinieerd. Prioriteitsregels die van invloed zijn op de oplossing van dubbelzinnigheid en paden, worden verderop in dit artikel beschreven in het onderwerp [Prioriteitsregels](#precedence-rules).

We raden u aan om bidirectionele filtering alleen naar behoefte te gebruiken.<!-- For guidance on bi-directional filtering, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

> [!TIP]
> In de modelweergave van Power BI Desktop kunt u de kruisfilterrichting van een relatie interpreteren door de pijlpunt(en) op de relatielijn te bekijken. Een enkele pijlpunt vertegenwoordigt een filter met één richting in de richting van de pijlpunt en een dubbele pijlpunt vertegenwoordigt een bidirectionele relatie.

### <a name="make-this-relationship-active"></a>Deze relatie activeren

U kunt slechts één actief pad voor het doorsturen van filters tussen twee modeltabellen gebruiken. Het is echter mogelijk om extra relatiepaden in te voeren, maar deze relaties moeten allemaal worden geconfigureerd als _inactief_. Inactieve relaties kunnen alleen actief worden gemaakt tijdens de evaluatie van een modelberekening. Dit wordt bereikt met behulp van de DAX-functie [USERELATIONSHIP](/dax/userelationship-function-dax).

<!--For guidance on defining inactive relationships, see the [Active vs inactive relationship guidance](guidance/relationships-active-inactive) article.-->

> [!TIP]
> In de modelweergave van Power BI Desktop kunt u de status Actief of Inactief van een relatie bekijken. Een actieve relatie wordt weergegeven met een ononderbroken lijn en een inactieve relatie wordt weergegeven als een stippellijn.

### <a name="assume-referential-integrity"></a>Referentiële integriteit aannemen

De eigenschap _Referentiële integriteit aannemen_ is alleen beschikbaar voor een-op-veel- en een-op-een-relaties tussen twee DirectQuery-opslagmodustabellen die zijn gebaseerd op dezelfde gegevensbron. Wanneer deze eigenschap is ingeschakeld, voegen systeemeigen query's die worden verzonden naar de gegevensbron, de twee tabellen samen met een INNER JOIN in plaats van een OUTER JOIN. Het inschakelen van deze eigenschap is in het algemeen beter voor de queryprestaties, hoewel de specifieke gegevensbron hierbij ook een rol speelt.

Deze eigenschap moet altijd worden ingeschakeld als er een beperking bestaat voor de refererende databasesleutel tussen de twee tabellen. Als er geen beperking is voor de refererende sleutel, kunt u de eigenschap alsnog inschakelen als u zeker weet dat er sprake is van gegevensintegriteit.

> [!IMPORTANT]
> Als de gegevensintegriteit is aangetast, worden de niet-overeenkomende rijen tussen de tabellen door de inner join geëlimineerd. Stel dat een model de tabel **Verkoop** heeft met een kolomwaarde voor **ProductID** die niet bestaat in de gerelateerde tabel **Product**. Bij het doorgeven van filters uit de tabel **Product** naar de tabel **Verkoop** worden verkooprijen voor onbekende producten verwijderd. Dit zou resulteren in een negatief beeld van de verkoopresultaten.
>
> Bekijk het artikel [Instellingen voor Referentiële integriteit aannemen in Power BI Desktop](desktop-assume-referential-integrity.md) voor meer informatie.

## <a name="relevant-dax-functions"></a>Relevante DAX-functies

Er zijn verschillende DAX-functies die relevant zijn voor modelrelaties. In de volgende lijst wordt elke functie kort beschreven:

- [RELATED](/dax/related-function-dax): Hiermee haalt u de waarde op uit de 'een'-zijde.
- [RELATEDTABLE](/dax/relatedtable-function-dax): Hiermee haalt u een tabel met rijen op van de 'veel'-zijde.
- [USERELATIONSHIP](/dax/userelationship-function-dax): Hiermee wordt het gebruik van een specifieke inactieve modelrelatie geforceerd.
- [CROSSFILTER](/dax/crossfilter-function): Hiermee wijzigt u de richting van de relatie tussen filters (van enkel naar beide), of wordt het doorgeven van filters uitgeschakeld (geen).
- [COMBINEVALUES](/dax/combinevalues-function-dax): Hiermee worden twee of meer tekenreeksen samengevoegd tot één tekenreeks. Het doel van deze functie is ondersteuning bieden aan relaties tussen DirectQuery-modellen met meerdere kolommen.
- [TREATAS](/dax/treatas-function): Hiermee wordt het resultaat van een tabelexpressie toegepast als filters voor kolommen uit een losgekoppelde tabel.
- [Bovenliggende en onderliggende functies](/dax/parent-and-child-functions-dax): Een groep verwante functies die kunnen worden gebruikt om berekende kolommen te genereren voor het maken van een hiërarchie met boven- en onderliggende elementen. Deze kolommen kunnen vervolgens worden gebruikt voor het maken van een hiërarchie met een vast niveau.

## <a name="relationship-evaluation"></a>Relaties evalueren

Modelrelaties worden bij een evaluatie geclassificeerd als _sterk_ of _zwak_. Dit is geen configureerbare relatie-eigenschap. Het wordt in feite afgeleid van het type kardinaliteit en de gegevensbron van de twee gerelateerde tabellen. Het is belangrijk om inzicht te krijgen in het evaluatietype omdat de prestaties kunnen worden beïnvloed als de gegevensintegriteit wordt aangetast. Deze implicaties en gevolgen voor de integriteit worden in dit onderwerp beschreven.

Allereerst is het belangrijk dat u enige theoretische kennis over modellen hebt om de evaluatie van relaties volledig te begrijpen.

Een Import- of DirectQuery-model haalt alle gegevens uit de Vertipaq-cache of de brondatabase. In beide gevallen kan Power BI bepalen dat er een 'een'-zijde van een relatie bestaat.

Een samengesteld model kan echter bestaan uit tabellen die gebruikmaken van verschillende opslagmodi (Import, DirectQuery of Dual), of meerdere DirectQuery-bronnen. Elke bron, met inbegrip van de Vertipaq-cache voor Import-gegevens, wordt beschouwd als een _gegevenseiland_. Modelrelaties kunnen vervolgens worden geclassificeerd als _intra-eiland_ of _kruis-eiland_. Met een intra-eilandrelatie worden twee tabellen in een gegevenseiland gekoppeld, terwijl een kruis-eilandrelatie tabellen uit verschillende gegevenseilanden verbindt. Houd er rekening mee dat relaties in Import- of DirectQuery-modellen altijd intra-eiland zijn.

Laten we een voorbeeld van een samengesteld model bekijken.

![Voorbeeld van een samengesteld model dat bestaat uit twee eilanden](media/desktop-relationships-understand/data-island-example.png)

In dit voor beeld bestaat het samengestelde model uit twee eilanden: een Vertipaq-gegevenseiland en een DirectQuery-brongegevenseiland. Het Vertipaq-gegevenseiland bevat drie tabellen en het DirectQuery-brongegevenseiland bevat twee tabellen. Er bestaat één kruis-eilandrelatie om een tabel in het Vertipaq-gegevenseiland te koppelen aan een tabel in het DirectQuery-brongegevenseiland.

### <a name="strong-relationships"></a>Sterke relaties

Een modelrelatie is _sterk_ wanneer de query-engine de 'een'-zijde van de relatie kan bepalen. Er wordt bevestigd dat de 'een'-zijde enkele waarden bevat. Alle een-op-veel-relaties binnen eilanden zijn een sterke relatie.

Het volgende voorbeeld bevat twee sterke relaties, gemarkeerd met een **S**. Deze relaties zijn de een-op-veel-relatie in het Vertipaq-eiland en de een-op-veel-relatie in de DirectQuery-bron.

![Voorbeeld van een samengesteld model dat bestaat uit twee eilanden waarbij de sterke relaties zijn gemarkeerd](media/desktop-relationships-understand/data-island-example-strong.png)

Bij Import-modellen, waarbij alle gegevens worden opgeslagen in de Vertipaq-cache, wordt bij het vernieuwen van gegevens een gegevensstructuur gemaakt voor elke sterke relatie. De gegevensstructuren bestaan uit geïndexeerde toewijzingen van alle kolom-naar-kolom-waarden. Het doel hiervan is het koppelen van tabellen tijdens het uitvoeren van query's te versnellen.

Bij het uitvoeren van query's kunnen _tabeluitbreidingen_ worden uitgevoerd voor sterke tabellen. Tabeluitbreiding resulteert in het maken van een virtuele tabel. Hierin worden de systeemeigen kolommen van de basistabel opgenomen en deze worden vervolgens uitgebreid naar gekoppelde tabellen. Bij Import-tabellen wordt dit gedaan in de query-engine. Bij DirectQuery-tabellen wordt dit gedaan in de systeemeigen query die wordt verzonden naar de brondatabase (waarbij de eigenschap 'Referentiële integriteit aannemen' niet is ingeschakeld). De query-engine past vervolgens de filters toe op de uitgebreide tabel en groepeert de waarden in de kolommen van deze tabel.

> [!NOTE]
> Inactieve relaties worden ook uitgebreid, zelfs wanneer de relatie niet wordt gebruikt door een berekening. Bidirectionele relaties hebben geen invloed op tabeluitbreiding.

Bij een-op-veel-relaties vindt tabeluitbreiding plaats van de 'veel'-zijde naar de 'een'-zijde door gebruik te maken van de semantiek van LEFT OUTER JOIN. Als er geen overeenkomende waarde bestaat tussen de 'veel'-zijde en de 'een'-zijde, wordt er een lege virtuele rij toegevoegd aan de 'een'-zijde van de tabel.

Tabeluitbreidingen vinden ook plaats voor een-op-een-relaties binnen eilanden, maar met behulp van de semantiek FULL OUTER JOIN. Het zorgt ervoor dat lege virtuele rijen aan beide zijden worden toegevoegd als dat nodig is.

De lege virtuele rijen worden _onbekende leden_. Onbekende leden vertegenwoordigen schendingen van referentiële integriteit, waarbij de 'veel'-zijde geen bijbehorende waarde heeft aan de 'een'-zijde. In het ideale geval zijn deze lege items niet aanwezig en ze kunnen worden verwijderd door de brongegevens op te schonen of te herstellen.

Laten we eens kijken hoe tabeluitbreidingen werken aan de hand van een geanimeerd voorbeeld.

![Geanimeerd voorbeeld van tabeluitbreiding](media/desktop-relationships-understand/animation-expanded-table.gif)

In dit voorbeeld bestaat het model uit drie tabellen: **Categorie**, **Product** en **Verkoop**. De tabel **Categorie** is gekoppeld aan de tabel **Product** met een een-op-veel-relatie en de tabel **Product** is gekoppeld aan de tabel **Verkoop** met een een-op-veel-relatie. De tabel **Categorie** bevat twee rijen, de tabel **Product** bevat drie rijen en de tabellen **Verkoop** bevatten vijf rijen. Er zijn overeenkomende waarden aan beide zijden van alle relaties, wat betekent dat er geen schendingen van de referentiële integriteit zijn. Tijdens het uitvoeren van de query wordt er een uitgebreide tabel getoond. De tabel bestaat uit de kolommen van alle drie de tabellen. Het is in feite een gedenormaliseerd perspectief van de gegevens in de drie tabellen. Er wordt een nieuwe rij toegevoegd aan de tabel **Verkoop** en deze heeft een productie-id-waarde (9) die geen overeenkomende waarde bevat in de tabel **Product**. Dit is een schending van de referentiële integriteit. In de uitgebreide tabel bevat de nieuwe rij (lege) waarden in de kolommen van de tabellen **Categorie** en **Product**.

### <a name="weak-relationships"></a>Zwakke relaties

Een model relatie is _zwak_ wanneer er geen gegarandeerde 'een'-zijde is. Dit kan twee oorzaken hebben:

- De relatie maakt gebruik van het type kardinaliteit veel-op-veel (zelfs als een of beide kolommen enkele waarden bevatten)
- Het is een kruis-eilandrelatie (wat alleen het geval kan zijn bij gecombineerde modellen)

Het volgende voorbeeld bevat twee zwakke relaties, gemarkeerd met een **Z**. Deze twee relaties zijn de veel-op-veel-relatie in het Vertipaq-eiland en de een-op-veel-relatie tussen eilanden in de DirectQuery-bron.

![Voorbeeld van een samengesteld model dat bestaat uit twee eilanden waarbij de zwakke relaties zijn gemarkeerd](media/desktop-relationships-understand/data-island-example-weak.png)

Bij Import-modellen worden nooit gegevensstructuren voor zwakke relaties gemaakt. Dit betekent dat tabelsamenvoegingen moeten worden opgelost tijdens het uitvoeren van de query.

Tabeluitbreidingen vindt nooit plaats voor zwakke relaties. Tabellen worden samengevoegd met behulp van de semantiek INNER JOIN en daarom worden er geen lege virtuele rijen toegevoegd om schendingen van de referentiële integriteit te compenseren.

Er gelden extra beperkingen voor zwakke relaties:

- De DAX-functie RELATED kan niet worden gebruikt om de kolomwaarden van de 'een'-zijde op te halen
- Het afdwingen van beveiliging op rijniveau heeft topologische beperkingen

> [!NOTE]
> In de modelweergave van Power BI Desktop is het niet altijd mogelijk om te bepalen of een modelrelatie sterk of zwak is. Een veel-op-veel-relatie is altijd zwak, evenals een een-op-veel-relatie wanneer het een kruis-eilandrelatie is. Als u wilt bepalen of er sprake is van een kruis-eilandrelatie, moet u de opslagmodi en gegevensbronnen van de tabel controleren om de juiste conclusie te kunnen trekken.

### <a name="precedence-rules"></a>Prioriteitsregels

Bidirectionele relaties kunnen leiden tot meerdere, en daardoor dubbelzinnige paden voor het doorgeven van filters tussen modeltabellen. De volgende lijst geeft een overzicht van de prioriteitsregels die Power BI gebruikt voor het detecteren van dubbelzinnigheid en het oplossen van paden:

1. Veel-op-een- en een-op-een-relaties, met inbegrip van zwakke relaties
2. Veel-op-veel-relaties
3. Bidirectionele relaties, in omgekeerde richting (dat wil zeggen vanuit de 'veel'-zijde)

### <a name="performance-preference"></a>Voorkeuren voor prioriteit

De volgende lijst geeft een overzicht van de prestaties bij het doorgeven van filters, van de snelste tot de langzaamste prestaties:

1. Een-op-veel-relaties binnen een eiland
2. Veel-op-veel-kardinaliteitsrelaties
3. Veel-op-veel-modelrelaties die tot stand zijn gebracht met een intermediaire tabel en die ten minste één bidirectionele relatie bevatten
4. Relaties tussen eilanden

<!--For further information and guidance on many-to-many relationships, see the [Cross filter relationship guidance](guidance/relationships-bidirectional-filtering) article.-->

## <a name="next-steps"></a>Volgende stappen

- [Meer informatie over stervormige schema's en het belang daarvan voor Power BI](guidance/star-schema.md)
- [Richtlijnen voor veel-op-veel-relaties](guidance/relationships-many-to-many.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
