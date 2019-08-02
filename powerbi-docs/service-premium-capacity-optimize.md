---
title: Microsoft Power BI Premium-capaciteiten optimaliseren
description: Hiermee worden de optimalisatiestrategieën voor Power BI Premium-capaciteiten beschreven.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9f5357056c27d6461ad7f7d7fba1daa27a508868
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391146"
---
# <a name="optimizing-premium-capacities"></a>Premium-capaciteiten optimaliseren

Wanneer er zich problemen met de prestaties van de Premium-capaciteit voordoen, moet u eerst proberen uw oplossingen te optimaliseren of af te stemmen om aanvaardbare reactietijden te herstellen. Dit is bedoeld om te voorkomen dat u aanvullende Premium-capaciteit moet aanschaffen, tenzij hier een goede reden voor is.

Wanneer extra Premium-capaciteit nodig is, zijn er twee opties die in dit artikel worden beschreven:

- Een bestaande Premium-capaciteit opschalen
- Nieuwe Premium-capaciteit toevoegen

Als laatste worden in dit artikel testmethoden en het aanpassen van het formaat van Premium-capaciteit beschreven.

## <a name="best-practices"></a>Aanbevolen procedures

Wanneer u optimaal gebruik en optimale prestaties probeert te verkrijgen, zijn er een aantal best practices, zoals:

- App-werkruimten gebruiken in plaats van persoonlijke werkruimten.
- Bedrijfskritieke BI en zelfservice-BI (SSBI) in verschillende capaciteiten scheiden.

  ![Bedrijfskritieke BI en zelfservice-BI in verschillende capaciteiten scheiden](media/service-premium-capacity-optimize/separate-capacities.png)

- Als u alleen inhoud deelt met Power BI Pro-gebruikers, hoeft u mogelijk geen inhoud in een toegewezen capaciteit op te slaan.
- Gebruik toegewezen capaciteiten wanneer u een specifieke vernieuwingstijd probeert te verkrijgen of wanneer u specifieke functies nodig hebt. Bijvoorbeeld met grote gegevenssets of gepagineerde rapporten.

### <a name="addressing-common-questions"></a>Algemene vragen beantwoorden

Het optimaliseren van Power BI Premium-implementaties is een ingewikkeld proces waarbij u moet weten wat voor workload nodig is, welke resources beschikbaar zijn en hoe u effectief gebruik kunt maken van deze implementaties.

In dit artikel worden zeven algemene ondersteuningsvragen beantwoord en mogelijke problemen en oorzaken en informatie over het identificeren en oplossen hiervan beschreven.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Waarom is de capaciteit traag en wat kan ik doen?

Er zijn vele redenen waardoor Premium-capaciteit traag kan worden. Voor deze vraag is meer informatie nodig om te begrijpen wat met 'traag' wordt bedoeld. Duurt het lang voordat rapporten zijn geladen? Of kunt u deze helemaal niet laden? Duurt het lang voordat visuals in rapporten zijn geladen of bijgewerkt wanneer gebruikers het rapport gebruiken? Duurt het vernieuwen langer dan verwacht of langer dan eerst?

Wanneer u de oorzaak weet, kunt u het probleem gaan onderzoeken. Op basis van de antwoorden op de volgende zes vragen kunt u specifiekere problemen oplossen.

### <a name="what-content-is-using-up-my-capacity"></a>Door welke inhoud wordt mijn capaciteit verbruikt?

U kunt de app **Power BI Premium-app voor metrische gegevens van capaciteit** gebruiken om de inhoud op capaciteit te filteren en de metrische gegevens over de prestaties voor inhoud uit de werkruimte controleren. U kunt de metrische gegevens over prestaties en het resourcegebruik per uur controleren voor de afgelopen zeven dagen voor alle inhoud die in Premium-capaciteit is opgeslagen. Controle is vaak de eerste stap om algemene problemen met de prestaties van Premium-capaciteit op te lossen.

Dit zijn de belangrijkste metrische gegevens om te controleren:

- Gemiddeld CPU-verbruik en hoog verbruik.
- Gemiddeld geheugengebruik en hoog verbruik en geheugengebruik voor specifieke gegevenssets, gegevensstromen en gepagineerde rapporten.
- Actieve gegevenssets die in het geheugen zijn geladen.
- Gemiddelde en maximale queryduur.
- Gemiddelde querywachttijden.
- Gemiddelde vernieuwingstijden voor gegevenssets en gegevensstromen.

In de Power BI Premium-app voor metrische gegevens van capaciteit ziet u bij Actief geheugen de totale hoeveelheid geheugen die aan een rapport is gegeven en die niet kan worden verwijderd, omdat dit in de afgelopen drie minuten is gebruikt. Een hoge piek in de wachttijd voor vernieuwen kan wijzen op een grote en/of actieve gegevensset.

In de grafiek **Top 5 op gemiddelde duur** worden de vijf belangrijkste gegevenssets, gepagineerde rapporten en gegevensstromen gemarkeerd die capaciteitsresources verbruiken. Bij de inhoud in de top 5-lijsten staan mogelijke items die kunnen worden onderzocht en geoptimaliseerd.

### <a name="why-are-reports-slow"></a>Waarom duurt het lang voordat rapporten zijn geladen?

In de volgende tabellen staan mogelijke problemen en manieren om ze te identificeren en op te lossen.

#### <a name="insufficient-capacity-resources"></a>Onvoldoende capaciteitsresources

| Mogelijke verklaringen | Instructies voor identificeren | Instructies voor oplossen |
| --- | --- | --- |
| Hoog totaal actief geheugen (model kan niet worden verwijderd omdat het in de afgelopen drie minuten is gebruikt).<br><br> Meerdere hoge pieken in querywachttijden.<br><br> Meerdere hoge pieken in wachttijden voor vernieuwen. | Controleer metrische gegevens over het geheugen \[[1](#endnote-1)\] en het aantal verwijderingen \[[2](#endnote-2)\]. | Verklein het model of stap over op de DirectQuery-modus. Zie het hoofdstuk [Modellen optimaliseren](#optimizing-models) in dit artikel.<br><br> Schaal de capaciteit omhoog.<br><br> Wijs de inhoud toe aan een andere capaciteit. |

#### <a name="inefficient-report-designs"></a>Onvoldoende rapportontwerpen

| Mogelijke verklaringen | Instructies voor identificeren | Instructies voor oplossen |
| --- | --- | --- |
| Rapportpagina's bevatten te veel visuals (door interactieve filters kan ten minste één query per visual worden geactiveerd).<br><br> Visuals ontvangen meer gegevens dan nodig is. | Controleer rapportontwerpen.<br><br> Ondervraag rapportgebruikers om te weten te komen hoe ze de rapporten gebruiken.<br><br> Controleer de metrische gegevens voor de query op de gegevensset \[[3](#endnote-3)\]. | Geef rapporten een nieuw ontwerp met minder visuals per pagina. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>De gegevensset is traag, met name wanneer rapporten eerder wel goed presteerden

| Mogelijke verklaringen | Instructies voor identificeren | Instructies voor oplossen |
| --- | --- | --- |
| Steeds grotere volumes met geïmporteerde gegevens.<br><br> Ingewikkelde of inefficiënte berekeningslogica, waaronder RLS-rollen.<br><br> Het model is niet volledig geoptimaliseerd.<br><br> (DQ/LC) Gatewaylatentie.<br><br> Trage reactietijden op DQ-bronquery. | Controleer modelontwerpen.<br><br> Bewaak de tellers voor de gateway-prestaties. | Zie het hoofdstuk [Modellen optimaliseren](#optimizing-models) in dit artikel. |

#### <a name="high-concurrent-report-usage"></a>Hoog gebruik van gelijktijdige rapporten

| Mogelijke verklaringen | Instructies voor identificeren | Instructies voor oplossen |
| --- | --- | --- |
| Hoge querywachttijden.<br><br> CPU-verzadiging.<br><br> De limiet voor de DQ/LC-verbindingen is overschreden. | Controleer metrische gegevens over het CPU-gebruik\[[4](#endnote-4)\], de querywachttijden en het DQ/LC-gebruik \[[5](#endnote-5)\] en de queryduur. Schommelingen kunnen duiden op problemen met gelijktijdigheid. | Schaal de capaciteit omhoog of wijs de inhoud toe aan een andere capaciteit.<br><br> Geef rapporten een nieuw ontwerp met minder visuals per pagina. |

**Opmerkingen:**    
<a name="endnote-1"></a>\[1\] Gemiddeld geheugengebruik (GB) en Hoogste geheugenverbruik (GB).   
<a name="endnote-2"></a>\[2\] Gegevenssetverwijderingen.   
<a name="endnote-3"></a>\[3\] Gegevenssetquery's, Gemiddelde queryduur voor gegevensset (ms), Wachttijd voor gegevensset en Gemiddelde wachttijd voor gegevensset (ms).   
<a name="endnote-4"></a>\[4\] Hoog CPU-verbruik en CPU-tijd van Hoogste verbruik (afgelopen zeven dagen).   
<a name="endnote-5"></a>\[5\] Hoog DQ/LC-verbruik en DQ/LC-tijd van Hoogste verbruik (afgelopen zeven dagen).   

### <a name="why-are-reports-not-loading"></a>Waarom worden rapporten niet geladen?

Wanneer rapporten niet kunnen worden geladen, betekent dit dat er onvoldoende geheugen beschikbaar is in de capaciteit en dat de capaciteit oververhit is. Dit kan optreden wanneer actieve query's worden uitgevoerd op alle geladen modellen (die dan dus niet kunnen worden verwijderd) en alle vernieuwingsbewerkingen zijn onderbroken of vertraagd. De Power BI-service probeert de gegevensset 30 seconden lang te laden en de gebruiker krijgt een melding over de fout, met het verzoek het later opnieuw te proberen.

Momenteel zijn er geen metrische gegevens om te controleren op fouten tijdens het laden van rapporten. U kunt controleren of er een kans bestaat dat dit probleem zich voordoet door het systeemgeheugen in de gaten te houden, met name het hoogste gebruik en de tijd waarop het hoogste gebruik plaatsvindt. Een groot aantal gegevenssetverwijderingen en een lange gemiddelde wachttijd voor vernieuwing van gegevenssets kan erop duiden dat dit probleem zich voordoet.

Als dit maar zelden gebeurt, wordt dit niet als een probleem met hoge prioriteit beschouwd. Rapportgebruikers worden geïnformeerd dat de service in gebruik is en dat ze het later opnieuw moeten proberen. Als dit regelmatig gebeurt, kunt u het probleem oplossen door de Premium-capaciteit omhoog te schalen of door de inhoud aan een andere capaciteit toe te wijzen.

Capaciteitsbeheerders (en Power BI-servicebeheerders) kunnen de metrische gegevens over de **Queryfouten** controleren om te bepalen wanneer dit probleem zich voordoet. Ook kunnen ze de capaciteit opnieuw opstarten, zodat alle bewerkingen opnieuw worden ingesteld als het systeem is overbelast.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Waarom worden vernieuwingen niet volgens het schema gestart?

Geplande begintijden voor vernieuwen kunnen niet worden gegarandeerd. Onthoud dat de Power BI-service interactieve bewerkingen altijd een hogere prioriteit geeft dan bewerkingen op de achtergrond. Vernieuwen is een achtergrondbewerking die optreedt wanneer er aan twee voorwaarden is voldaan:

- Er is voldoende geheugen
- Het aantal ondersteunde gelijktijdige vernieuwingen voor de Premium-capaciteit wordt niet overschreden

Wanneer er niet aan deze voorwaarden wordt voldaan, wordt de vernieuwing in de wachtrij geplaatst totdat er wel aan de voorwaarden is voldaan.

Let op: voor een volledige vernieuwing is ten minste het dubbele van de huidige geheugengrootte van de gegevensset vereist. Als er niet voldoende geheugen beschikbaar is, kan de vernieuwing pas worden gestart zodra er geheugen vrijkomt doordat er modellen zijn verwijderd. Dit betekent vertraging totdat een of meer gegevenssets inactief zijn geworden en kunnen worden verwijderd.

Let op: het ondersteunde maximumaantal gelijktijdige vernieuwingen wordt ingesteld op 1,5 keer het aantal back-end v-cores (afgerond).

Geplande vernieuwingen kunnen niet worden uitgevoerd als deze niet kunnen worden gestart vóór de volgende geplande vernieuwing wordt gestart. Een on-demand vernieuwing die handmatig is geactiveerd vanuit de gebruikersinterface wordt drie keer geprobeerd voordat dit mislukt.

Capaciteitsbeheerders (en Power BI-servicebeheerders) kunnen de metrische gegevens over de **Gemiddelde wachttijd voor vernieuwen (minuten)** controleren om de gemiddelde vertraging tussen de geplande tijd en de start van de bewerking te bepalen.

Hoewel dit doorgaans geen administratieve prioriteit heeft, moet u ervoor zorgen dat er voldoende geheugen beschikbaar is om ervoor te zorgen dat gegevens op tijd worden vernieuwd. Mogelijk moet u hiervoor gegevenssets isoleren naar capaciteiten waarvan u weet dat hier voldoende resources beschikbaar zijn. Ook is het mogelijk voor beheerders om in overleg met de eigenaars van gegevenssets de geplande vernieuwing van gegevenssets te spreiden of te beperken om conflicten te minimaliseren. Let op: beheerders kunnen de vernieuwingswachtrij niet weergeven of planningen voor gegevenssets ophalen.

### <a name="why-are-refreshes-slow"></a>Waarom duurt het lang voordat mijn gegevens zijn vernieuwd?

Het vernieuwen van gegevens kan lang duren of lang lijken te duren (zoals in de vorige algemene vraag wordt behandeld).

Wanneer het daadwerkelijk lang duurt voordat gegevens zijn vernieuwd, kan dit diverse oorzaken hebben:

- Onvoldoende CPU (voor vernieuwen kan erg veel CPU worden verbruikt).
- Onvoldoende geheugen, waardoor het vernieuwen steeds wordt onderbroken (als er aan bepaalde voorwaarden voor opnieuw starten wordt voldaan, zal het vernieuwen hierdoor telkens opnieuw beginnen).
- Andere oorzaken die niets met capaciteit te maken hebben, zoals het reactievermogen van het gegevensbronsysteem, de netwerklatentie, ongeldige machtigingen of gatewaydoorvoer.
- Gegevensvolume. Dit is altijd een goede reden om incrementeel vernieuwen te configureren (zie hieronder).

Capaciteitsbeheerders (en Power BI-servicebeheerders) kunnen de metrische gegevens over de **Gemiddelde vernieuwingsduur (minuten)** controleren om een benchmark voor vergelijking na bepaalde tijd te bepalen en ze kunnen de metrische gegevens over de **Gemiddelde wachttijd voor vernieuwen (minuten)** gebruiken om de gemiddelde vertraging tussen de geplande tijd en de start van de bewerking te bepalen.

Met Incrementeel vernieuwen kunnen gegevens aanzienlijk sneller worden vernieuwd, met name voor grote modeltabellen. Incrementeel vernieuwen kent vier voordelen:

- **Gegevens worden sneller vernieuwd**: er hoeft alleen maar een subset van een tabel te worden geladen. Hierdoor wordt minder CPU en minder geheugen gebruikt en kunnen meerdere partities gemakkelijker tegelijkertijd worden vernieuwd.
- **Gegevens worden alleen vernieuwd wanneer dat nodig is**: beleid voor Incrementeel vernieuwen kan zodanig worden geconfigureerd dat deze functie alleen wordt geladen wanneer er gegevens zijn gewijzigd.
- **Vernieuwingen zijn betrouwbaarder**: de kortere uitvoeringsverbindingen met vluchtige gegevensbronsystemen zijn minder gevoelig voor het verbreken van verbindingen.
- **Modellen blijven klein**: u kunt beleid voor Incrementeel vernieuwen zodanig configureren dat de geschiedenis na een bepaalde periode automatisch wordt verwijderd.

Raadpleeg [Incremental refresh in Power BI Premium](service-premium-incremental-refresh.md) (Incrementeel vernieuwen in Power BI Premium) voor meer informatie.

### <a name="why-are-data-refreshes-not-completing"></a>Waarom kan het vernieuwen van gegevens niet worden voltooid?

Wanneer het vernieuwen van gegevens wel wordt gestart maar niet kan worden voltooid, kan dit diverse oorzaken hebben:

- Onvoldoende geheugen, zelfs als de Premium-capaciteit maar over één model beschikt, bijvoorbeeld omdat het model erg groot is.
- Andere oorzaken die niets met capaciteit te maken hebben, zoals een verbroken verbinding met het gegevensbronsysteem, ongeldige machtigingen of een gatewayfout.

Capaciteitsbeheerders (en Power BI-servicebeheerders) kunnen de metrische gegevens over de **Vernieuwingsfouten vanwege onvoldoende geheugen** controleren.

## <a name="optimizing-models"></a>Modellen optimaliseren

Voor een efficiënte en schaalbare oplossing is een optimaal modelontwerp essentieel. Dit artikel is echter niet bedoeld om hier verder op in te gaan. In plaats daarvan vindt u in dit hoofdstuk belangrijke overwegingen voor het optimaliseren van modellen.

### <a name="optimizing-power-bi-hosted-models"></a>In Power BI gehoste modellen optimaliseren

U kunt modellen die in een Premium-capaciteit worden gehost zowel in de gegevensbronlaag als in de modellaag optimaliseren.

Bekijk de optimalisatiemogelijkheden voor een importeermodel:

![Optimalisatiemogelijkheden voor een importeermodel](media/service-premium-capacity-optimize/import-model-optimizations.png)

In de gegevensbronlaag:

- Relationele gegevensbronnen kunnen worden geoptimaliseerd voor de snelst mogelijke vernieuwing door gegevens vooraf te integreren, de juiste indexen toe te passen, tabelpartities te definiëren die aansluiten op incrementele vernieuwingsperioden en berekeningen te materialiseren (in plaats van berekende modeltabellen en kolommen) of door berekeningslogica aan weergaven toe te voegen.
- Niet-relationele gegevensbronnen kunnen vooraf worden geïntegreerd met relationele opslagplaatsen.
- Zorg ervoor dat er voldoende resources voor gateways beschikbaar zijn, bij voorkeur op toegewezen computers, met voldoende netwerkbandbreedte en dicht bij de gegevensbronnen.

In de modellaag:

- Door een Power Query op queryontwerpen uit te voeren, kunt u complexe transformaties minimaliseren of verwijderen, met name transformaties waarbij verschillende gegevensbronnen worden samengevoegd (voor datawarehouses wordt dit tijdens de ETL-fase (extraheren, transformeren, laden) bereikt). Bovendien kunt u, door de juiste privacyniveaus voor gegevensbronnen in te stellen, voorkomen dat Power BI volledige resultaten moet laden om een gecombineerd resultaat van meerdere query's te produceren.
- Welke gegevens worden geladen, wordt door de modelstructuur bepaald. Dit heeft direct invloed op de grootte van het model. Deze structuur kan worden ontworpen om het laden van onnodige gegevens te voorkomen door kolommen te verwijderen, rijen te verwijderen (met name historische gegevens) of samengevatte gegevens te laden (ten koste van het laden van gedetailleerde gegevens). U kunt de grootte aanzienlijk verminderen door kolommen met een hoge kardinaliteit (zoals tekstkolommen) te verwijderen die niet erg efficiënt kunnen worden opgeslagen of gecomprimeerd.
- De prestaties van modelquery's kunnen worden verbeterd door eendirectionele relaties te configureren, tenzij er een dwingende reden is om bidirectionele filters toe te staan. U kunt in plaats van bidirectionele filters ook de functie [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) gebruiken.
- Met aggregatietabellen kunt u snel reacties van query's krijgen door vooraf samengevatte gegevens te laden. Hierdoor neemt echter wel de modelgrootte toe en duurt het langer om gegevens te vernieuwen. Over het algemeen moeten aggregatietabellen voor heel grote modellen of voor samengestelde modelontwerpen worden gereserveerd.
- Door berekende tabellen en kolommen neemt de modelgrootte toe en duurt het langer om gegevens te vernieuwen. Over het algemeen zijn een kleinere opslaggrootte en snellere vernieuwingen mogelijk door gegevens te materialiseren of te berekenen in de gegevensbron. Als dit niet mogelijk is, kunt u Power Query gebruiken voor aangepaste kolommen voor betere compressie van de opslag.
- Mogelijk bestaat er een kans om DAX-expressies af te stemmen voor metingen en RLS-regels, mogelijk door logica te herschrijven om dure formules te vermijden
- Door Incrementeel vernieuwen kunt u de vernieuwingstijd aanzienlijk verminderen en geheugen en CPU besparen. Incrementeel vernieuwen kan ook worden geconfigureerd om historische gegevens te verwijderen, zodat het model niet te groot wordt.
- Een model kan opnieuw worden ontworpen als twee modellen als er verschillende en conflicterende querypatronen bestaan. Sommige rapporten bevatten bijvoorbeeld aggregaties op hoog niveau met alle geschiedenis en kunnen een latentie van 24 uur weerstaan. In andere rapporten draait het om de gegevens van vandaag; hiervoor is nauwkeurige toegang tot afzonderlijke transacties vereist. In plaats van één model te ontwerpen voor alle rapporten, maakt u twee modellen die voor elke vereiste zijn geoptimaliseerd.

Bekijk de optimalisatiemogelijkheden voor een DirectQuery-model. Omdat er queryaanvragen worden gedaan bij de onderliggende gegevensbron, is optimalisatie van de gegevensbron essentieel om responsieve modelquery's uit te voeren.

 ![Optimalisatiemogelijkheden voor een DirectQuery-model](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

In de gegevensbronlaag:

- De gegevensbron kan worden geoptimaliseerd voor zo snel mogelijke query's door gegevens vooraf te integreren (dit is niet mogelijk in de modellaag), de juiste indexen toe te passen, tabelpartities te definiëren, samengevatte gegevens (met geïndexeerde weergaven) te materialiseren en het aantal berekeningen te minimaliseren. U krijgt de beste ervaring als Pass Through-query's alleen inner joins tussen geïndexeerde tabellen of weergaven hoeven te filteren en uit te voeren.
- Zorg ervoor dat er voldoende resources voor gateways beschikbaar zijn, bij voorkeur op toegewezen computers, met voldoende netwerkbandbreedte en dicht bij de gegevensbronnen.

In de modellaag:

- Bij voorkeur worden door Power Query-queryontwerpen geen transformaties toegepast; probeer transformaties anders tot een absoluut minimum te beperken.
- De prestaties van modelquery's kunnen worden verbeterd door eendirectionele relaties te configureren, tenzij er een dwingende reden is om bidirectionele filters toe te staan. Daarnaast moeten modelrelaties worden geconfigureerd zodat referentiële integriteit wordt afgedwongen (als dit het geval is); hierdoor worden voor query's op gegevensbronnen efficiëntere inner joins gebruikt (in plaats van outer joins).
- Maak geen aangepaste kolommen of door modellen berekende kolommen in een Power Query-query, maar materialiseer deze zoveel mogelijk in de gegevensbron.
- Mogelijk bestaat er een kans om DAX-expressies af te stemmen voor metingen en RLS-regels, mogelijk door logica te herschrijven om dure formules te vermijden.

Bekijk de optimalisatiemogelijkheden voor een samengesteld model. U weet dat met een samengesteld model een combinatie van geïmporteerde tabellen en DirectQuery-tabellen mogelijk is.

![Optimalisatiemogelijkheden voor een samengesteld model](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Over het algemeen is de optimalisatie voor importeer- en DirectQuery-modellen van toepassing op samengestelde modeltabellen waarvoor deze opslagmodi worden gebruikt.
- Maak een uitgebalanceerd ontwerp door tabellen van het type Dimensie (die bedrijfsentiteiten vertegenwoordigen) als dubbele opslagmodus te configureren en tabellen van het type Feit (vaak grote tabellen, die operationele feiten vertegenwoordigen) als de DirectQuery-opslagmodus te configureren. De dubbele opslagmodus betreft zowel de importeer- als DirectQuery-opslagmodus. Hierdoor kan de Power BI-service de efficiëntste opslagmodus bepalen die moet worden gebruikt bij het genereren van een systeemeigen query voor pass-through.
- Zorg ervoor dat er voldoende resources voor gateways beschikbaar zijn, bij voorkeur op toegewezen computers, met voldoende netwerkbandbreedte en dicht bij de gegevensbronnen
- Met aggregatietabellen die als de importeeropslagmodus zijn geconfigureerd, kunnen de prestaties van query's aanzienlijk worden verbeterd wanneer ze worden gebruikt om tabellen van het type Feit voor de DirectQuery-opslagmodus samen te vatten. In dit geval wordt het model groter en duurt vernieuwen langer door de aggregatietabellen; dit is vaak een acceptabele balans voor snellere query's.

### <a name="optimizing-externally-hosted-models"></a>Extern gehoste modellen optimaliseren

Veel van de optimalisatiemogelijkheden die we in het gedeelte [In Power BI gehoste modellen optimaliseren](#optimizing-power-bi-hosted-models) hebben besproken, zijn ook van toepassing op modellen die met Azure Analysis Services en SQL Server Analysis Services zijn ontwikkeld. De uitzondering geldt voor bepaalde functies die momenteel niet worden ondersteund, zoals samengestelde modellen en aggregatietabellen.

Wat extern gehoste gegevenssets betreft, moet ook rekening worden gehouden met de databasehosting met betrekking tot de Power BI-service. Voor Azure Analysis Services betekent dit dat u de Azure-resource in dezelfde regio moet maken als de Power BI-tenant (thuisregio). Voor SQL Server Analysis Services, voor IaaS, betekent dit dat u de virtuele machine in dezelfde regio moet hosten. Voor on-premises betekent dit dat u voor een efficiënte gatewayinstallatie moet zorgen.

Het is wellicht ook interessant om te weten dat modellen voor Azure Analysis Services-databases en SQL Server Analysis Services-databases met tabbladen volledig in het geheugen moeten worden geladen en dat ze daar te allen tijde blijven om het uitvoeren van query's te ondersteunen. Net zoals bij de Power BI-service moet er voldoende geheugen beschikbaar zijn om gegevens te kunnen vernieuwen indien het model online moet blijven tijdens het vernieuwen. In tegenstelling tot de Power BI-service is er geen concept waarbij modellen automatisch op basis van gebruik vanwege veroudering uit het geheugen worden gehaald of daarin worden geplaatst. Power BI Premium biedt dus een efficiëntere methode om modelquery's te maximaliseren met minder geheugengebruik.

## <a name="capacity-planning"></a>Capaciteitsplanning

De grootte van een Premium-capaciteit bepaalt hoeveel geheugen en processorresources hiervoor beschikbaar zijn en welke beperkingen voor de capaciteit gelden. Ook is het handig om over het aantal Premium-capaciteiten na te denken, omdat u workloads van elkaar kunt isoleren door meerdere Premium-capaciteiten te maken. Houd er rekening mee dat voor elk capaciteitsknooppunt 100 TB opslagruimte beschikbaar is; dit is waarschijnlijk meer dan genoeg voor elke workload.

Het kan een enorme uitdaging zijn om de grootte van en het aantal Premium-capaciteiten te bepalen, met name voor de initiële capaciteiten die u maakt. Wanneer u de grootte van een capaciteit gaat bepalen, moet u eerst weten wat de gemiddelde workload is die bij dagelijks gebruik kan worden verwacht. Het is belangrijk dat u begrijpt dat niet alle workloads gelijk zijn. Een voorbeeld: stel dat aan het ene uiteinde van een spectrum 100 gelijktijdige gebruikers zich toegang verschaffen tot één rapportpagina met één eenvoudig te maken visual. Tegelijkertijd proberen 100 gelijktijdige gebruikers aan het andere uiteinde van het spectrum toegang te krijgen tot 100 verschillende rapporten, elk met 100 visuals op de rapportpagina. Dit vergt een totaal andere vraag naar capaciteitsresources.

Capaciteitsbeheerders moeten daarom rekening houden met vele specifieke factoren voor uw omgeving, inhoud en verwachte gebruik. Het uiteindelijke doel is het gebruik van de capaciteit te maximaliseren en tegelijkertijd consistente querytijden, acceptabele wachttijden en verwijderingsnelheden te realiseren. Factoren die u kunt overwegen zijn bijvoorbeeld:

- **Modelgrootte en gegevenskenmerken**: importeermodellen moeten volledig in het geheugen worden geladen om query's te kunnen uitvoeren of gegevens te vernieuwen. Voor LC/DQ-gegevenssets kan veel processortijd en mogelijk veel geheugen zijn vereist om complexe metingen of RLS-regels te evalueren. Voor het geheugen, de processorgrootte en de LC/DQ-querydoorvoer geldt een beperking volgens de capaciteitsgrootte.
- **Gelijktijdige actieve modellen**: u krijgt de beste reacties en prestaties wanneer u gelijktijdig query's op verschillende importeermodellen uitvoert door ze in het geheugen te houden. Er moet voldoende geheugen beschikbaar zijn om alle modellen waarop vaak query's worden uitgevoerd te hosten, met extra geheugen om gegevens te kunnen vernieuwen.
- **Importeermodellen vernieuwen**: het vernieuwingstype (volledig of incrementeel), de duur en complexiteit van Power Query-query's en berekende tabel-/modellogica kunnen invloed hebben op het geheugen en met name op het processorgebruik. Gelijktijdige vernieuwingen worden beperkt door de capaciteitsgrootte (1,5 x de back-end v-cores, afgerond).
- **Gelijktijdige query's**: het gelijktijdig uitvoeren van veel query's kan ertoe leiden dat rapporten niet reageren wanneer processor- of LC/DQ-verbindingen de capaciteitslimiet overschrijden. Dit geldt vooral voor rapportpagina's met veel visuals.
- **Gegevensstromen en gepagineerde rapporten**: de capaciteit kan worden geconfigureerd om gegevensstromen en gepagineerde rapporten te ondersteunen, waarbij voor elk type een configureerbaar maximumpercentage van capaciteitsgeheugen is vereist. Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar in het geval van gepagineerde rapporten betreft het een statische toewijzing.

Naast deze factoren kunnen capaciteitsbeheerders ook meerdere capaciteiten maken. Met meerdere capaciteiten kunnen workloads worden geïsoleerd, en de capaciteiten kunnen zodanig worden geconfigureerd dat workloads met een hoge prioriteit gegarandeerd over resources kunnen beschikken. Er kunnen bijvoorbeeld twee capaciteiten worden gemaakt om bedrijfskritische workloads en SSBI-workloads (selfservice-BI) van elkaar te scheiden. De bedrijfskritische capaciteit kan worden gebruikt om grote bedrijfsmodellen te isoleren zodat hier gegarandeerd resources voor beschikbaar zijn, waarbij alleen aan de IT-afdeling schrijftoegang wordt verleend. De SSBI-capaciteit kan worden gebruikt om een toenemend aantal kleinere modellen te hosten, waarbij toegang wordt verleend aan bedrijfsanalisten. Voor de SSBI-capaciteit kunnen soms wachttijden voor query's of vernieuwingen worden ervaren die acceptabel zijn.

Na verloop van tijd kunnen capaciteitsbeheerders werkruimten over meerdere capaciteiten verdelen door inhoud tussen werkruimten of werkruimten tussen capaciteiten te verplaatsen en door de capaciteiten omhoog of omlaag te schalen. Over het algemeen geldt dat u voor het hosten van grotere modellen omhoog schaalt en dat u voor een hogere mate van gelijktijdigheid omlaag schaalt.

U weet dat de tenant van v-cores wordt voorzien wanneer u een licentie aanschaft. De aankoop van een **P3**-abonnement kan worden gebruikt voor het maken van één of maximaal vier Premium-capaciteiten, zoals 1x P3, 2x P2 of 4x P1. Voordat u van een P2-capaciteit overstapt naar de grotere P3-capaciteit, kunt u overwegen om de v-cores op te splitsen en zo twee P1-capaciteiten te maken.

## <a name="testing-approaches"></a>Testmethoden

Zodra u de grootte van een capaciteit hebt bepaald, kunt u testen uitvoeren door een gecontroleerde omgeving te maken. Het is een praktische en rendabele optie om een Azure-capaciteit (A SKU's) te maken, waarbij u er rekening mee moet houden dat een P1-capaciteit dezelfde grootte heeft als een A4-capaciteit, waarbij de P2- en P3-capaciteiten dezelfde grootte hebben als respectievelijk de A5- en A6-capaciteiten. Azure-capaciteiten kunnen snel worden gemaakt en worden op uurbasis gefactureerd. Ze kunnen dus eenvoudig worden verwijderd zodra de testen zijn voltooid. Hiermee voorkomt u dat de kosten doorlopen.

De inhoud van de test kan worden toegevoegd aan de werkruimte die u op de Azure-capaciteit hebt gemaakt. Vervolgens kan één gebruiker rapporten uitvoeren om een realistische en representatieve workload met query's te genereren. Als er importeermodellen zijn, moet u ook elk model vernieuwen. Vervolgens kunt u gebruikmaken van controlehulpprogramma's om alle metrische gegevens te controleren, zodat u begrijpt hoe de resources worden gebruikt.

Het is belangrijk dat de testen kunnen worden herhaald. Voer testen een aantal keer uit en kijk of ze steeds ongeveer dezelfde resultaten opleveren. Het gemiddelde van deze resultaten kan worden gebruikt om een workload te extrapoleren en in te schatten op basis van echte productievoorwaarden.

Als u al beschikt over een capaciteit en de rapporten waarop u een laadtest wilt uitvoeren, gebruikt u het [PowerShell-hulpprogramma voor het genereren van een laadtest](https://aka.ms/PowerBILoadTestingTool) om snel een laadtest te genereren. Met dit hulpprogramma kunt u inschatten hoeveel exemplaren van elk rapport binnen een uur door uw capaciteit kunnen worden uitgevoerd. Gebruik het hulpprogramma om te evalueren in hoeverre u afzonderlijke rapporten kunt weergeven met uw capaciteit of verschillende rapporten tegelijkertijd kunt weergeven. Voor meer informatie bekijkt u de video [Microsoft Power BI: Premium-capaciteit](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw).

Als u een complexere test wilt genereren, kunt u een toepassing voor laadtesten ontwikkelen waarbij een realistische workload wordt gesimuleerd. Zie de webinar [Load Testing Power BI Applications with Visual Studio Load Test](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) (Laadtesten uitvoeren op Power BI-toepassingen met de Visual Studio-laadtest) voor meer informatie.

## <a name="acknowledgements"></a>Erkenningen

Dit artikel is geschreven door Peter Myers, Data Platform MVP en onafhankelijk BI-expert bij [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Scenario's voor Premium-capaciteit](service-premium-capacity-scenarios.md)   
  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

||||||