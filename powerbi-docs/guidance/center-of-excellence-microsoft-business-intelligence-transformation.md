---
title: BI-transformatie van Microsoft
description: Meer informatie over hoe Microsoft een gegevenscultuur voor de besluitvorming van bedrijven heeft gestimuleerd. Hierin worden de strategie voor en de visie op BI beschreven.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 8e1e590f871e1840209e72eb611bde7b21610c6e
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86162362"
---
# <a name="microsofts-bi-transformation"></a>BI-transformatie van Microsoft

Dit artikel is gericht op IT-professionals en IT-beheerders. Hier vindt u informatie over onze strategie voor en visie op BI, waardoor we onze gegevens voortdurend kunnen gebruiken als assets. U leert ook hoe we een gegevenscultuur van zakelijke besluitvorming stimuleren met Power BI.

Eerst enige achtergrondinformatie: Vandaag de dag is de explosieve groei van gegevens van invloed op consumenten en bedrijven door de duizelingwekkende snelheid ervan. Om te kunnen slagen in deze gegevensintensieve omgeving zijn analisten en leidinggevenden nodig die uit een enorme hoeveelheid gegevens een beknopt inzicht kunnen afleiden. De revolutie in de BI-hulpprogramma's van Microsoft hebben de manier veranderd waarop Microsoft zelf de eigen gegevens verkent en tot de juiste inzichten komt die nodig zijn om de invloed in het bedrijf te vergroten.

Hoe kan uw organisatie ook de manier radicaal veranderen waarop deze met gegevens omgaat? We gaan het verhaal van onze BI-transformatietraject met u delen om u meer inzicht te geven.

## <a name="microsoft-journey"></a>Microsoft-traject

Enkele jaren geleden moedigde onze organisatiecultuur bij Microsoft mensen aan om naar volledige eigendom van gegevens en inzichten te streven. Ook werd een sterke culturele weerstand ervaren om dingen op een gestandaardiseerde manier te doen. Daarom heeft de organisatiecultuur geleid tot rapportage- en analyseproblemen. Met name leidde dit tot:

- Inconsistente gegevensdefinities, hiërarchieën, metrische gegevens en KPI's (Key Performance Indicators). Elk land had bijvoorbeeld een eigen manier om te rapporteren over nieuwe inkomsten. Er was geen consistentie, maar wel veel verwarring.
- Analisten besteedden 75% van de tijd aan het verzamelen en compileren van gegevens.
- 78% van de rapporten werden gemaakt in een offline omgeving.
- Meer dan 350 gecentraliseerde financiële hulpmiddelen en systemen.
- Ongeveer 30 miljoen dollar werd jaarlijks besteed aan schaduwtoepassingen.

Deze uitdagingen dwongen ons om na te denken over hoe we de zaken beter konden aanpakken. Het Financiën-team en andere interne teams kregen ondersteuning van de leiding om bedrijfsevaluatieproces te transformeren. Dit heeft geleid tot het ontwikkelen van een uniform BI-platform als onze enige bron van waarheid. (Verderop in dit artikel gaan we het meer hebben over ons BI-platform.) Uiteindelijk leidden deze innovaties ertoe dat bedrijfsevaluaties van opeengepakte weergaven met tabellen werden getransformeerd in eenvoudigere, meer inzichtelijke visuals die gericht waren op belangrijke bedrijfsthema's.

Hoe hebben we dit succesvolle resultaat gerealiseerd? Het werd een succes doordat we hebben gezorgd voor een gecentraliseerde, door IT beheerde BI die werd uitgebreid met selfservice BI (SSBI). We beschrijven het op twee creatieve manieren: _discipline van binnen_ en _flexibiliteit aan de rand_.

### <a name="discipline-at-the-core"></a>Discipline van binnen

Discipline van binnen houdt in dat de IT de controle houdt door één hoofdgegevensbron te beheren. Het leveren van gestandaardiseerde bedrijfs-BI en het definiëren van consistente taxonomieën en hiërarchieën van KPI's maken deel uit van die discipline. Belangrijk is dat machtigingen voor gegevens centraal worden afgedwongen, zodat onze gebruikers alleen de gegevens kunnen lezen die ze nodig hebben.

We hebben eerst ingezien dat onze BI-transformatie geen technologieprobleem was. We ontdekten dat we, als we succes wilden bereiken, eerst succes moesten definiëren en vervolgens vertalen in belangrijke metrische gegevens. Het kan niet genoeg worden benadrukt hoe belangrijk het voor ons was om consistentie in de definitie van onze gegevens te bereiken.

Onze gehele transformatie vond niet in een keer plaats. We hebben een prioriteit gegeven aan de levering van de scorecard voor vestigingen die bestaat uit ongeveer 30 KPI's. Daarna hebben we gedurende enkele jaren geleidelijk het aantal en de diepte van de onderwerpgebieden uitgebreid en complexere KPI-hiërarchieën ontwikkeld. Vandaag de dag kunnen we hierdoor KPI's op een (lager) klantniveau samenvoegen met de hogere op bedrijfsniveau. Het totale aantal KPI's is nu hoger dan 2000 en elke KPI is een belangrijke maatstaf van succes en is afgestemd op bedrijfsdoelstellingen. In het hele bedrijf geven nu bedrijfsrapporten en SSBI-oplossingen blijk van KPI's die goed zijn gedefinieerd, consistent en veilig zijn.

### <a name="flexibility-at-the-edge"></a>Flexibiliteit aan de rand

Aan de rand van de binnenste kern zijn onze analisten in de financiën-, verkoop- en marketingteams steeds flexibeler geworden. Ze profiteren nu van de mogelijkheid om gegevens sneller te analyseren. Formeel is dit scenario beschreven als _beheerde selfservice BI (SSBI)_ . We begrijpen nu dat beheerde SSBI voor IT en analisten _wederzijdse voordelig_ is. Belangrijk is dat we optimalisaties hebben ervaren door onze drang naar standaardisatie, kennis en het hergebruik van onze gegevens en BI-oplossingen. En als bedrijf hebben we synergetisch gezien meer waarde hieruit gehaald, omdat we de juiste balans hebben gevonden tussen gecentraliseerde BI en beheerde SSBI.

### <a name="our-solution"></a>Onze oplossing

**Starlight** is de naam die we geven aan ons unificatie- en analyseplatform voor interne gegevens, dat ondersteuning biedt aan financiën, verkoop, marketing en techniek. Het is bedoeld om een robuust, gedeeld en schaalbaar gegevensplatform te bieden. Het platform is volledig ontwikkeld door het Financiën-team en blijft momenteel functioneren met behulp van de nieuwste Microsoft-producten.

De **KPI Lake** is geen Azure Data Lake. Het is in plaats daarvan een door Starlight mogelijk gemaakt model in tabelvorm dat wordt gehost in Azure IaaS met behulp van SQL Server Analysis Services van Microsoft. Het model in tabelvorm biedt gegevens afkomstig van meer dan 100 interne bronnen en definieert talrijke hiërarchieën en KPI's. Het is bedoeld om rapportage en analyses van bedrijfsprestaties mogelijk te maken voor Financiën-, Marketing- en Verkoop-teams. Zo kunt u actuele, nauwkeurige en goed presterende inzichten verkrijgen via uniforme modellen vanuit relevante bronnen.

Toen het voor het eerst werd geïmplementeerd, was het een opwindende tijd omdat het model in tabelvorm heeft geleid tot onmiddellijke en meetbare voordelen. De eerste versie gecentraliseerde BI-platforms voor C + E-financiën en marketing. De afgelopen zes jaar is het vervolgens uitgebreid met de consolidatie van aanvullende oplossingen voor bedrijfsinzichten. Vandaag de dag blijft de ontwikkeling doorgaan, waardoor onze wereldwijde en commerciële bedrijfsevaluaties en de standaardrapportage en SSBI mogelijk worden gemaakt. De invoering ervan is met de factor 5 gestegen sinds de release, ruim hoger dan onze aanvankelijke verwachtingen.

Hier volgt een samenvatting van de belangrijkste voordelen:

- Dit maakt onze scorecard van vestigingen, wereldwijde bedrijfsevaluaties en rapporten en analyses op het gebied van financiën, marketing en verkopen mogelijk.
- Het biedt ondersteuning voor selfservice analyses, waardoor analisten in gegevens verborgen inzichten kunnen ontdekken.
- Het stimuleert rapportage en analyses voor vergoeding van incentives, marketing- en bedrijfsanalyses, metrische gegevens voor verkoopprestaties, beoordeling van senior leidinggevenden en het jaarlijkse planningsproces.
- Het biedt geautomatiseerde en dynamische rapportages en analyses vanuit _één enkele bron van waarheid_.

De **KPI Lake** is een uitstekend succesverhaal. Het wordt vaak aan onze klanten gepresenteerd om een voorbeeld te tonen van hoe onze nieuwste technologieën effectief gebruikt kunnen worden. Het mag geen verrassing heten dat de KPI Lake veel overeenkomsten heeft met veel ervan.

#### <a name="how-it-works"></a>Uitleg

Het Starlight-platform beheert de gegevensstroom van verwerving tot verwerking en vervolgens helemaal tot aan de publicatie:

1. De robuuste en flexibele gegevensintegratie vindt plaats op basis van een planning, waarbij gegevens van meer dan 100 verschillende onbewerkte bronnen worden geconsolideerd. Systemen voor brongegevens zijn onder meer relationele databases, Azure Data Lake Storage en Azure Synapse-databases. De onderwerpsgebieden zijn onder meer financiën, marketing, verkoop en techniek.
2. Zodra de gegevens zijn klaargezet, worden ze in overeenstemming gebracht en verrijkt met hoofdgegevens en bedrijfslogica. De gegevens worden vervolgens geladen in datawarehousetabellen. Het model in tabelvorm wordt vervolgens vernieuwd.
3. Analisten in het bedrijf gebruiken Excel en Power BI voor het leveren van inzichten en analyses vanuit het model in tabelvorm. Bovendien biedt het bedrijfseigenaren de mogelijkheid om voor metrische definities voor hun eigen bedrijf op te komen. Indien nodig, kan de schaal worden aangepast met behulp van Azure IaaS met taakverdeling.

## <a name="deliver-success"></a>Zorgen voor succes

Grappig genoeg wil iedereen één versie van de waarheid... zolang het zijn/haar versie is. Maar voor sommige organisaties is het realiteit. Ze hebben meerdere versies van de waarheid als gevolg van personen die volledige eigendom van gegevens en inzichten nastreven. Voor deze organisaties is deze onbeheerde benadering waarschijnlijk geen traject naar een succesvol bedrijf.

Daarom zijn we van mening dat u een COE (_Center of Excellence) nodig hebt_. Een COE is een centraal team dat verantwoordelijk is voor het definiëren van metrische gegevens en definities voor het hele bedrijf, en nog veel meer. Het is ook een bedrijfsfunctie waarmee mensen, processen en technologie-onderdelen in een uitgebreide reeks bedrijfscompetenties en -mogelijkheden worden georganiseerd.

Er is veel bewijsmateriaal ter ondersteuning ervan dat een uitgebreide en robuuste COE cruciaal is voor het leveren van waarde en maximaal succes van uw bedrijf. Het kan onder andere gaan om initiatieven tot wijzigingen, standaardprocessen, rollen, richtlijnen, best practices, ondersteuning, training en nog veel meer.

We nodigen u uit om de artikelen in deze COE-serie te lezen voor meer informatie. We gaan u laten zien hoe uw organisatie veranderingen kan aangrijpen om voor succes te zorgen.

## <a name="next-steps"></a>Volgende stappen

In de [volgende artikel in deze reeks](center-of-excellence-establish.md) leert u hoe bij Microsoft een COE ons heeft geholpen om een gestandaardiseerd analyse- en gegevensplatform te maken, waardoor we inzichten hebben verkregen uit onze gegevens.

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Een Center of Excellence instellen](center-of-excellence-establish.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
