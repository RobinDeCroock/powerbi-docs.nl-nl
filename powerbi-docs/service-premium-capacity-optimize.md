---
title: Microsoft Power BI Premium-capaciteiten optimaliseren
description: Beschrijft strategieën voor kostenoptimalisatie voor Power BI Premium-capaciteiten.
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
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565345"
---
# <a name="optimizing-premium-capacities"></a>Premium-capaciteiten optimaliseren

Wanneer prestatieproblemen van Premium-capaciteit zich voordoen, is een algemene first-aanpak te optimaliseren of af te stemmen uw oplossingen voor het herstellen van acceptabele responstijden. De logica worden om te voorkomen dat het aanschaffen van extra Premium-capaciteit, tenzij gerechtvaardigd.

Als extra Premium-capaciteit vereist is, zijn er twee opties die in dit artikel wordt beschreven:

- Scale-up van een bestaande Premium-capaciteit
- Toevoegen van een nieuwe Premium-capaciteit

Ten slotte testen benaderingen en Premium-capaciteitsgrootte sluiten in dit artikel.

## <a name="best-practices"></a>Aanbevolen procedures

Bij het ophalen van de beste gebruik en prestaties, zijn er enkele aanbevolen procedures, met inbegrip van:

- Met behulp van app-werkruimten in plaats van persoonlijke werkruimten.
- Bedrijfskritiek en Self-Service BI (SSBI) te scheiden in verschillende capaciteiten.

  ![Bedrijfskritiek en Self-Service BI scheiden in verschillende capaciteiten](media/service-premium-capacity-optimize/separate-capacities.png)

- Als u delen van inhoud alleen met Power BI Pro-gebruikers, is er mogelijk niet nodig voor het opslaan van de inhoud in een toegewezen capaciteit.
- Toegewezen capaciteit gebruiken bij het zoeken naar voor het bereiken van een specifieke vernieuwingstijd, of wanneer bepaalde functies zijn vereist. Bijvoorbeeld, met grote gegevenssets of gepagineerde rapporten.

### <a name="addressing-common-questions"></a>Veelgestelde vragen-adressering

Power BI Premium-implementaties te optimaliseren, is een complex onderwerp met betrekking tot een goed begrip van de werkbelasting vereisten, beschikbare resources en het daadwerkelijke gebruik.

In dit artikel komen zeven veelgestelde ondersteuningsvragen, met een beschrijving van mogelijke problemen en uitleg en informatie over het identificeren en op te lossen.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Waarom is de capaciteit traag en wat kan ik doen?

Er zijn veel redenen die aan een trage Premium-capaciteit bijdragen kunnen. Deze vraag vereist meer informatie over wat wordt bedoeld met traag. Zijn rapporten langzaam worden geladen? Of worden ze niet worden geladen? Zijn visuele rapportelementen langzaam geladen of wanneer gebruikers werken interactief met het rapport bijwerken? Worden vernieuwd duurt langer dan verwacht, of als u eerder ervaring?

Ervaring van een goed begrip van de reden hiervoor kunt u vervolgens gaan om te onderzoeken. Antwoorden op de volgende zes vragen helpt u om meer specifieke problemen.

### <a name="what-content-is-using-up-my-capacity"></a>Welke inhoud wordt mijn capaciteit gebruikt?

U kunt de **metrische gegevens over Power BI Premium capaciteit** app om te filteren op capaciteit en bekijk metrische gegevens voor prestaties voor de inhoud van de werkruimte. Het is mogelijk om te controleren van de prestaties van metrische gegevens en resources gebruik per uur voor de afgelopen zeven dagen voor alle inhoud die zijn opgeslagen in een Premium-capaciteit. Bewaking is vaak de eerste stap bij het nemen bij het oplossen van een algemeen probleem over de prestaties van de Premium-capaciteit.

Belangrijke metrische gegevens voor het bewaken van zijn onder andere:

- Gemiddelde CPU- en hoog gebruik count.
- Gemiddelde geheugen en hoog gebruik aantal en het geheugengebruik voor bepaalde gegevenssets, gegevensstromen en gepagineerde rapporten.
- Actieve gegevenssets in het geheugen geladen.
- Query van gemiddelde en maximale duur.
- Gemiddelde query wachttijden.
- Gemiddelde gegevensset en gegevensstroom vernieuwen tijden.

In de app Power BI Premium-capaciteit metrische gegevens over ziet actieve geheugen u de totale hoeveelheid geheugen die aan een rapport dat kan niet worden verwijderd omdat deze gebruikt in de laatste drie minuten is. Een grote piek in vernieuwen wachttijd kan worden gecorreleerd met een grote en/of actieve gegevensset.

De **Top 5 van de gemiddelde duur** diagram illustreert de gegevenssets van vijf, gepagineerde rapporten, en gegevensstromen capaciteit bronnen verbruikt. Inhoud in de bovenste vijf een lijst met kandidaten voor onderzoek en mogelijke optimalisatie is.

### <a name="why-are-reports-slow"></a>Waarom zijn rapporten langzaam?

De volgende tabellen ziet u mogelijke problemen en manieren om te identificeren en deze te verwerken.

#### <a name="insufficient-capacity-resources"></a>Er is onvoldoende capaciteit resources

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Maximale totale actieve geheugen (model kan niet worden verwijderd omdat deze gebruikt in de laatste drie minuten wordt).<br><br> Meerdere hoge pieken in de query wachttijden.<br><br> Meerdere hoge pieken in het vernieuwen van wachttijden. | Controleer metrische gegevens voor geheugen \[ [1](#endnote-1)\], en verwijdering tellingen \[ [2](#endnote-2)\]. | Het model te verkleinen of converteren naar de modus DirectQuery. Zie de [optimaliseren modellen](#optimizing-models) sectie in dit artikel.<br><br> De capaciteit voor scale-up.<br><br> De inhoud toewijzen aan een andere capaciteit. |

#### <a name="inefficient-report-designs"></a>Inefficiënt rapportontwerpen

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Rapportpagina's bevatten te veel visuele elementen (interactieve filteren kunt activeren ten minste één query per visualisatie).<br><br> Visuele elementen ophalen van meer gegevens dan nodig is. | Bekijk rapportontwerpen.<br><br> Interview rapportgebruikers als u wilt weten hoe ze communiceren met de rapporten.<br><br> Controleer metrische gegevens voor gegevensset query \[ [3](#endnote-3)\]. | Deze rapporten met minder visuele elementen per pagina. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Gegevensset is traag, met name wanneer rapporten eerder goed hebt uitgevoerd

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Steeds grotere hoeveelheden gegevens importeren.<br><br> Berekening van complexe of inefficiënte logica, met inbegrip van RLS-rollen.<br><br> Het model is niet volledig geoptimaliseerd.<br><br> (DQ/LC) Latentie van de gateway.<br><br> Trage DQ bron query reactietijden. | Bekijk model ontwerpen.<br><br> Gateway-prestatiemeteritems bewaken. | Zie de [optimaliseren modellen](#optimizing-models) sectie in dit artikel. |

#### <a name="high-concurrent-report-usage"></a>Hoge gelijktijdige rapport gebruik

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Hoge query wachttijden.<br><br> Belasting van de CPU.<br><br> DQ/LC limieten overschreden. | CPU-gebruik bewaken \[ [4](#endnote-4)\], wachttijden query en het gebruik van DQ/LC \[ [5](#endnote-5) \] metrische gegevens + duur van de Query. Als wisselt, kan duiden op problemen met gelijktijdigheid. | De capaciteit vergroten, of de inhoud toewijzen aan een andere capaciteit.<br><br> Deze rapporten met minder visuele elementen per pagina. |

**Opmerkingen:**    
<a name="endnote-1"></a>\[1\] gemiddelde geheugengebruik (GB) en de hoogste geheugengebruik (GB).   
<a name="endnote-2"></a>\[2\] gegevensset databasebestandspagina's.   
<a name="endnote-3"></a>\[3\] gegevensset query's, gegevensset gemiddelde Queryduur (ms), gegevensset wacht aantal en de gegevensset gemiddelde wachttijd (ms).   
<a name="endnote-4"></a>\[4\] aantal van hoog CPU-gebruik en CPU-tijd van het hoogste gebruik (afgelopen zeven dagen).   
<a name="endnote-5"></a>\[5\] DQ/LC hoog gebruik Count en DQ/LC tijd van het hoogste gebruik (afgelopen zeven dagen).   

### <a name="why-are-reports-not-loading"></a>Waarom zijn rapporten niet laden?

Wanneer rapporten niet worden geladen, is ervoor dat de capaciteit heeft onvoldoende geheugen en is te veel hete teken. Dit kan gebeuren wanneer alle geladen modellen actief worden opgevraagd en kunnen niet worden verwijderd en alle bewerkingen voor Gegevensvernieuwing is onderbroken of uitgesteld. Power BI-service probeert te laden van de gegevensset gedurende 30 seconden en de gebruiker wordt zonder problemen op de hoogte gesteld van de fout met een suggestie om te proberen het over enkele ogenblikken opnieuw.

Er is momenteel geen metrische gegevens om te controleren voor rapport laden van fouten. U kunt de mogelijkheden voor dit probleem identificeren door bewaking systeemgeheugen, specifiek hoogste gebruik en de tijd van het hoogste gebruik. Hoge gegevensset databasebestandspagina's en lang gegevensset vernieuwen gemiddelde wachttijd kunnen voorstellen dat dit probleem zich voordoet.

Als dit slechts zelden gebeurt, dit kan niet worden beschouwd als een probleem met de prioriteit. Rapportgebruikers zien een bericht dat de service bezet is en dat ze na een korte periode opnieuw moeten proberen. Als dit te vaak gebeurt, kan het probleem worden opgelost door het omhoog schalen van de Premium-capaciteit of door de inhoud toewijzen aan een andere capaciteit.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **mislukte query's** metrische gegevens om te bepalen wanneer dit gebeurt. Ze kunnen ook de capaciteit, opnieuw instellen van alle bewerkingen in het geval van systeem overbelasting opnieuw worden gestart.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Waarom zijn wordt vernieuwd niet volgens planning gestart?

Begintijden van geplande vernieuwing niet worden gegarandeerd. Intrekken dat Power BI-service wordt altijd prioriteit gegeven aan interactieve bewerkingen via bewerkingen op de achtergrond. Vernieuwen is een achtergrondbewerking die optreden kan wanneer twee voorwaarden wordt voldaan:

- Er is onvoldoende geheugen
- Het aantal ondersteunde gelijktijdige wordt vernieuwd voor de Premium-capaciteit is niet overschreden

Als niet aan de voorwaarden wordt voldaan, het vernieuwen is in de wachtrij geplaatst totdat de voorwaarden gunstig zijn.

Voor een volledige vernieuwing intrekken dat ten minste tweemaal de huidige gegevensset geheugengrootte vereist is. Als er niet voldoende geheugen beschikbaar is, kan niet klikt u vervolgens het vernieuwen beginnen pas model verwijdering vrijgemaakt geheugen wordt: dit betekent vertragingen dat totdat een of meer gegevenssets inactief en kan worden verwijderd.

Het intrekken of het aantal ondersteunde maximum aantal gelijktijdige vernieuwingen is ingesteld op 1,5 keer de back-end-v-cores, naar boven afgerond.

Een geplande vernieuwing mislukt wanneer deze kan niet beginnen voordat de volgende geplande vernieuwing is verschuldigd is om te beginnen. Een vernieuwing op aanvraag handmatig wordt geactiveerd vanuit de gebruikersinterface probeert te maximaal drie keer uitvoeren voordat deze is mislukt.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **gemiddelde vernieuwen wachttijd (minuten)** metrische gegevens om te bepalen van de gemiddelde vertraging tussen het geplande tijdstip en het begin van de bewerking.

Zorg ervoor dat voldoende geheugen beschikbaar is terwijl meestal niet een administratieve prioriteit, om te beïnvloeden op tijd-gegevens wordt vernieuwd. Dit kan betrekking hebben op gegevenssets kunnen capaciteiten met bekende voldoende resources isoleren. Het is ook mogelijk dat beheerders werkt u met eigenaren van gegevenssets samen kan te spreiden of geplande tijdstippen voor vernieuwing te minimaliseren conflicten verminderen. Houd er rekening mee dat het is niet mogelijk voor een beheerder om de wachtrij vernieuwen weer te geven of om op te halen van de gegevensset-schema's.

### <a name="why-are-refreshes-slow"></a>Waarom zijn traag wordt vernieuwd?

Vernieuwen is traag- of waargenomen langzaam zijn (als de vorige algemene vraag-adressen).

Wanneer het vernieuwen in feite traag is, kan het zijn verschillende oorzaken hebben:

- Onvoldoende CPU (vernieuwen kan erg CPU-intensief zijn).
- Er is onvoldoende geheugen, wat resulteert in vernieuwen onderbreken (hiervoor is het vernieuwen te beginnen als voorwaarden gunstig zijn voor hervat).
- Niet-capaciteit redenen, met inbegrip van de reactiesnelheid van het systeem datasource, netwerklatentie, ongeldige machtigingen of gateway-doorvoer.
- Gegevensvolume - een goede reden het configureren van incrementeel vernieuwen, zoals hieronder wordt beschreven.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **gemiddelde vernieuwen duur (minuten)** metrische gegevens om te bepalen van een benchmark voor vergelijking na verloop van tijd en de **gemiddelde vernieuwen wachttijd (minuten)** metrische gegevens om te bepalen van de gemiddelde vertraging tussen de gemiddelde vertraging tussen het geplande tijdstip en het begin van de bewerking.

Incrementeel vernieuwen kunt gegevens vernieuwen duur, met name voor grote modellen tabellen aanzienlijk verkorten. Er zijn vier voordelen die zijn gekoppeld aan incrementeel vernieuwen:

- **Vernieuwingen zijn sneller** : alleen een subset van een tabel moet laden, te reduceren CPU- en geheugengebruik en parallelle uitvoering kan hoger zijn bij het vernieuwen van meerdere partities.
- **Gegevens alleen in indien nodig bijgewerkt** -beleidsregels voor incrementeel vernieuwen kunnen worden geconfigureerd voor het laden van alleen wanneer gegevens zijn gewijzigd.
- **Vernieuwingen zijn betrouwbaarder** -kortere actieve verbindingen met vluchtige datasource-systemen zijn minder vatbaar voor verbreken.
- **Modellen blijven Knippen** -beleidsregels voor incrementeel vernieuwen kunnen worden geconfigureerd voor de geschiedenis van meer dan een sliding window van tijd automatisch worden verwijderd.

Zie voor meer informatie, [incrementeel vernieuwen in Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Waarom zijn gegevens vernieuwen niet voltooien?

Wanneer het vernieuwen van gegevens wordt gemaakt, maar kan niet worden voltooid, kan het zijn verschillende oorzaken hebben:

- Onvoldoende geheugen, zelfs als er slechts één model in de Premium-capaciteit, dat wil zeggen het model erg groot is.
- Niet-capaciteit redenen, met inbegrip van datasource-systeem verbreken, ongeldige machtigingen of gatewayfout.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **vernieuwen, mislukte aanmeldingen vanwege onvoldoende geheugen** metrische gegevens.

## <a name="optimizing-models"></a>Modellen te optimaliseren

Optimale modelontwerp is essentieel om te kunnen leveren van een efficiënte en schaalbare oplossing. Het is echter buiten het bereik van dit artikel voor een volledige bespreking van. In plaats daarvan biedt deze sectie belangrijke gebieden ter overweging bij het optimaliseren van modellen.

### <a name="optimizing-power-bi-hosted-models"></a>Optimaliseren Power BI modellen die worden gehost

Optimaliseren van modellen die worden gehost in een Premium-capaciteit kan worden bereikt op de lagen gegevensbronnen kunnen en het model.

Houd rekening met de optimalisatiemogelijkheden voor een model importeren:

![Optimalisatiemogelijkheden voor een model importeren](media/service-premium-capacity-optimize/import-model-optimizations.png)

Op het niveau van de gegevensbron:

- Relationele gegevensbronnen worden geoptimaliseerd om te controleren of het vernieuwen van de snelst mogelijke door vooraf geïntegreerde gegevens, het toepassen van de juiste indexen, Tabelpartities die zijn afgestemd voor incrementeel vernieuwen perioden te definiëren en materialiseren berekeningen (in plaats van berekend model voor tabellen en kolommen) of berekening logica toevoegen aan weergaven.
- Niet-relationele gegevensbronnen kunnen vooraf worden geïntegreerd met relationele winkels.
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbronnen zijn.

Op het niveau van het model:

- Power Query-queryontwerpen kunnen minimaliseren of verwijderen van complexe transformaties en met name toepassingen die samenvoegen van verschillende gegevensbronnen (datawarehouses hiervoor tijdens de fase Extract-Transform-Load). Ook ervoor te zorgen dat de juiste gegevensbron privacyniveaus worden ingesteld, dit kan voorkomen dat van Power BI laden van de volledige resultaten te produceren van een gecombineerde resultaat voor query's.
- De modelstructuur bepaalt welke gegevens worden geladen en heeft een directe invloed op de Modelgrootte. Deze kan worden ontworpen om te voorkomen dat het laden van onnodige gegevens door het verwijderen van kolommen, verwijderen van rijen (met name historische gegevens) of door het laden van samengevatte gegevens (ten koste van het laden van gedetailleerde gegevens). Indrukwekkende formaat beperking kan worden bereikt door het verwijderen van hoge kardinaliteit kolommen (met name tekstkolommen) die niet opslaan of zeer efficiënt comprimeren.
- Prestaties van de model-query's kan worden verbeterd door het configureren van relaties één richting, tenzij er is een goede reden om toe te staan van bidirectionele filters. Overweeg het gebruik van ook de [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) functie in plaats van bidirectionele filters.
- Aggregatie van tabellen kunnen maar liefst snel query antwoorden van het laden van vooraf samengevatte gegevens, maar dit de grootte van het model en het resultaat in langer tijdstippen voor vernieuwing vergroot. Over het algemeen moeten aggregatie van tabellen voor zeer grote modellen of ontwerpen die samengestelde model worden gereserveerd.
- Berekende tabellen en kolommen Verhoog de Modelgrootte en leiden tot langere vernieuwingstijden. Over het algemeen kunnen een kleinere opslaggrootte en snellere vernieuwingstijd worden behaald als de gegevens zijn gerealiseerde of berekend in de gegevensbron. Als dit niet mogelijk is, met Power Query aangepaste kolommen verbeterde opslag compressie te kunnen bieden.
- Mogelijk zijn er kans om af te stemmen DAX-expressies voor metingen en RLS-regels, misschien herschrijven logica om te voorkomen dat dure formules
- Incrementeel vernieuwen kunt aanzienlijk minder vernieuwingstijd en besparen geheugen en CPU. Incrementeel vernieuwen kan ook worden geconfigureerd om historische gegevens te verkleinen houden van grootte van het gegevensmodel te verwijderen.
- Een model kan worden aangepast als de twee modellen wanneer er andere, conflicterende querypatronen. Bijvoorbeeld: sommige rapporten aanwezig zijn op hoog niveau statistische functies via alle geschiedenis en kunnen tolereren latentie van 24 uur. Andere rapporten betrokken zijn bij de gegevens van vandaag en gedetailleerde toegang nodig tot afzonderlijke transacties. In plaats van ontwerp één model om te voldoen aan alle rapporten, twee modellen die zijn geoptimaliseerd voor elke vereiste te maken.

Houd rekening met de optimalisatiemogelijkheden voor een model in DirectQuery. Als het model problemen met query-aanvragen met de onderliggende gegevensbron, is optimalisatie van de gegevensbron essentieel om responsieve model query's leveren.

 ![Optimalisatiemogelijkheden voor een DirectQuery-model](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Op het niveau van de gegevensbron:

- De gegevensbron kan worden geoptimaliseerd om te controleren of de snelste mogelijk uitvoeren van query's door vooraf de integratie van gegevens (dit is niet mogelijk op het niveau van het model), het toepassen van de juiste indexen, Tabelpartities, materialiseren definiëren samengevatte gegevens (met geïndexeerde weergaven), en minimaliseren van het bedrag van de berekening. De beste ervaring wordt bereikt wanneer Pass Through-query's moeten alleen filteren en inner joins tussen geïndexeerde tabellen of weergaven uit te voeren.
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbron zijn.

Op het niveau van het model:

- Power Query-query ontwerpen gelden bij voorkeur geen transformaties - anders probeert transformaties tot een absoluut minimum te houden.
- Prestaties van de model-query's kan worden verbeterd door het configureren van relaties één richting, tenzij er is een goede reden om toe te staan van bidirectionele filters. Bovendien relaties in het gegevensmodel moeten worden geconfigureerd voor wordt ervan uitgegaan dat referentiële integriteit aannemen (als dit het geval is) wordt afgedwongen en resulteert in datasource-query's met efficiënter inner joins (in plaats van outer join).
- Vermijd het maken van aangepaste kolommen van Power Query-query of berekende kolom model - realiseren in de gegevensbron, indien mogelijk.
- Mogelijk zijn er kans om af te stemmen DAX-expressies voor metingen en RLS-regels, misschien herschrijven logica om te voorkomen dat dure formules.

Houd rekening met de optimalisatiemogelijkheden voor een samengestelde model. Intrekken dat een samengestelde model wijze een combinatie van importeren en DirectQuery-tabellen.

![Optimalisatiemogelijkheden voor een samengestelde model](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Over het algemeen gelden de optimalisatie voor importeren en DirectQuery-modellen voor samengestelde modeltabellen die gebruikmaken van deze modi opslag.
- Normaal gesproken streven ernaar om een evenwichtige ontwerp realiseren door het configureren van de dimensie-type tabellen (die vertegenwoordigt bedrijfsentiteiten) als Dual-modus en type feit opslagtabellen (vaak grote tabellen, operationele gegevens die) als DirectQuery-opslagmodus. Dual-opslagmodus betekent dat beide importeren en DirectQuery-modi voor opslag, en dit kunt Power BI-service om te bepalen van de meest efficiënte opslagmodus gebruiken bij het genereren van een systeemeigen Pass Through-query.
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbronnen zijn
- Aggregaties tabellen geconfigureerd als opslagmodus voor importeren query indrukwekkende prestatieverbeteringen wanneer die wordt gebruikt om samen te vatten DirectQuery-modus type feit opslagtabellen kan leveren. In dit geval aggregatie van tabellen wordt Verhoog de grootte van het model en vernieuwingstijd verhogen en vaak is dit geen bezwaar voor snellere query's.

### <a name="optimizing-externally-hosted-models"></a>Modellen optimaliseren Extern gehost

Veel optimalisatiemogelijkheden besproken de [optimaliseren van Power BI gehost modellen](#optimizing-power-bi-hosted-models) sectie ook van toepassing op modellen die zijn ontwikkeld door Azure Analysis Services en SQL Server Analysis Services. Schakel uitzonderingen zijn bepaalde functies die worden momenteel niet ondersteund, met inbegrip van samengestelde modellen en aggregatie van tabellen.

Een extra aandacht voor extern gehoste gegevenssets is de database die als host fungeert ten opzichte van de Power BI-service. Voor Azure Analysis Services, betekent dit dat het maken van de Azure-resource in dezelfde regio als de Power BI-tenant (basisregio). Dit betekent dat de virtuele machine in dezelfde regio die als host fungeert voor SQL Server Analysis Services, voor IaaS, en voor on-premises, betekent dit dat ervoor te zorgen dat de installatie van een doeltreffende gateway.

Als een aside kan zijn van belang te weten dat Azure Analysis Services-databases en tabellaire databases van SQL Server Analysis Services is vereist dat hun modellen volledig in het geheugen worden geladen en dat ze blijven er helemaal tijden voor het uitvoeren van query's. Net als Power BI-service moet er voldoende geheugen voor het vernieuwen van als het model online tijdens het vernieuwen blijven moet. In tegenstelling tot de Power BI-service is er geen concept dat modellen automatisch zijn verouderde geheugen op basis van gebruik. Power BI Premium biedt daarom een efficiëntere benadering voor het model uitvoeren van query's met lagere geheugengebruik te maximaliseren.

## <a name="capacity-planning"></a>Capaciteitsplanning

De grootte van een Premium-capaciteit bepaalt de beschikbare geheugen en processorbronnen en beperkingen van de capaciteit. Het aantal Premium-capaciteiten is ook een vergoeding, als het maken van meerdere Premium capaciteit kunnen helpen bij de workloads van elkaar isoleren. Houd er rekening mee dat opslagruimte 100 TB per capaciteitsknooppunt is en dit is waarschijnlijk meer dan voldoende zijn voor elke workload.

Bepalen van de grootte en het aantal Premium-capaciteiten kan lastig zijn, met name voor de initiële capaciteit die u maakt. De eerste stap bij het capaciteitsgrootte is om te begrijpen van de gemiddelde werkbelasting weergeven van het verwachte dagelijkse gebruik. Het is belangrijk om te begrijpen dat niet alle workloads gelijk zijn. Een voorbeeld - is 100 gelijktijdige gebruikers toegang tot één rapportpagina waarin één visueel element aan het ene uiteinde van een spectrum - eenvoudig haalbare. Nog - aan het andere uiteinde van het spectrum - 100 gelijktijdige gebruikers toegang hebben tot 100 verschillende rapporten, elk met 100 visuele elementen op de rapportpagina, maak ik zeer verschillende eisen van de capaciteit van bronnen.

Capaciteitsbeheerders moet daarom rekening houden veel factoren die specifiek zijn voor uw omgeving, de inhoud en het verwachte gebruik. Het overschrijven doel is om te maximaliseren capaciteitsverbruik bij het leveren van consistente tijden acceptabele wachttijden en tarieven voor verwijdering. Factoren ter overweging kunnen opnemen:

- **Grootte en gegevens modelleren** -Import modellen moeten worden volledig geladen in het geheugen om toe te staan bij het controleren of vernieuwen. LC/DQ gegevenssets kunnen vereisen dat aanzienlijke processortijd en mogelijk aanzienlijke hoeveelheid geheugen aan het evalueren van complexe metingen of RLS-regels. Geheugen en de grootte van de processor en querydoorvoer LC/DQ worden beperkt door de grootte van de capaciteit.
- **Gelijktijdige active modellen** -gelijktijdige query's naar verschillende import modellen verzorgt aanbevolen reactiesnelheid en prestaties wanneer ze in het geheugen blijven. Er moet voldoende geheugen voor het hosten van alle sterk opgevraagd modellen, met extra geheugen om toe te staan om hun te vernieuwen.
- **Import-modelvernieuwing** -de vernieuwingstype (volledige of incrementele), de duur en de complexiteit van Power Query-query's en berekende tabelkolom logica kunnen gevolgen hebben voor geheugen en met name processorgebruik. Gelijktijdige wordt vernieuwd, worden beperkt door de grootte van de capaciteit (1,5 x backend v-cores, naar boven afgerond).
- **Gelijktijdige query's** -groot aantal gelijktijdige query's kunnen resulteren in rapporten die van niet-reagerende wanneer processor- of LC/DQ verbindingen groter is dan de maximale capaciteit. Dit geldt met name voor rapportpagina's die veel visuele elementen bevatten.
- **Gegevensstromen en gepagineerde rapporten** -de capaciteit kan worden geconfigureerd ter ondersteuning van gegevensstromen en gepagineerde rapporten, met elk een configureerbare maximumpercentage van capaciteit geheugen vereisen. Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar wordt statisch toegewezen aan gepagineerde rapporten.

Naast deze factoren kunt Capaciteitsbeheerders Houd rekening met het maken van meerdere capaciteit. Meerdere capaciteiten staan voor de isolatie van workloads en kunnen worden geconfigureerd om ervoor te zorgen prioriteit workloads hebt resources gegarandeerd. Twee capaciteiten kunnen bijvoorbeeld worden gemaakt om bedrijfskritische werkbelastingen scheiden van workloads van selfservice-BI (SSBI). De essentiële capaciteit kan worden gebruikt voor het isoleren van grote zakelijke modellen met gegarandeerde resources, met het ontwerpen van toegang verleend tot de IT-afdeling. De capaciteit SSBI kan worden gebruikt voor het hosten van een groeiend aantal kleinere-modellen, met toegang tot zakelijke analisten verleend. De capaciteit SSBI kan soms query of vernieuwen wacht die toegestane optreden.

Na verloop van tijd Capaciteitsbeheerders kan worden verdeeld werkruimten capaciteiten door het verplaatsen van inhoud tussen werkruimten of werkruimten tussen capaciteiten en capaciteiten schaal omhoog of omlaag. Over het algemeen schalen voor host grotere modellen scale-up en hogere gelijktijdigheid u opwaarts.

Let erop dat het aanschaffen van een licentie voor de tenant v-cores biedt. De aanschaf van een **P3** abonnement kan worden gebruikt om het maken van een en maximaal vier Premium-capaciteiten, dat wil zeggen 1 x P3, of 2 x P2, of 4 x P1. Ook, voordat u een capaciteit P2 aan een capaciteit P3 converteren, kunnen worden overwogen de v-cores splitsen twee P1-capaciteit maken.

## <a name="testing-approaches"></a>Benaderingen testen

Zodra een grootte van de capaciteit, wordt besloten kan testen worden uitgevoerd door het maken van een gecontroleerde omgeving. Een praktische en betaalbare optie is het maken een capaciteit van Azure (A-SKU's), geldt dat een capaciteit P1 even groot is als een A4-capaciteit, met de P2 en P3 capaciteiten even groot is als de A5 en A6-capaciteit, respectievelijk. Azure-capaciteiten snel kunnen worden gemaakt en worden op uurbasis in rekening gebracht. Ja, zodra het testen is voltooid, ze kunnen worden eenvoudig verwijderd als u wilt stoppen kosten oplopen.

De test-inhoud kan worden toegevoegd aan de werkruimten die zijn gemaakt op de Azure-capaciteit, en vervolgens als één gebruiker rapporten kunt uitvoeren voor het genereren van een realistische en representatieve workload van query's. Als er import modellen, moet u ook een vernieuwing voor elk model uitgevoerd. Controlehulpprogramma's kan vervolgens worden gebruikt om te controleren van alle metrische gegevens voor meer informatie over Resourcegebruik.

Het is belangrijk dat de tests herhaalbaar zijn. Tests moeten worden uitgevoerd op meerdere keren en ze ongeveer hetzelfde resultaat telkens moeten leveren. Een gemiddelde is van deze resultaten kan worden gebruikt om te extrapoleren en een schatting maken van een werkbelasting waar productie voorwaarden wordt voldaan.

Voor het genereren van een stresstest, houd rekening met het ontwikkelen van een belastingstest van toepassing voor het simuleren van een realistische werkbelasting. De details van hoe u om dit te bereiken vallen buiten het bereik van dit artikel. Raadpleeg voor meer informatie, inclusief een voorbeeld van code, de [laden van toepassingen voor Power BI met belastingstest van Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="acknowledgements"></a>Bevestigingen

In dit artikel is geschreven door Peter Myers, Data Platform MVP en onafhankelijke BI deskundige met [Bitsgewijs oplossingen](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Scenario's voor Premium-capaciteit](service-premium-capacity-scenarios.md)   
  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

||||||