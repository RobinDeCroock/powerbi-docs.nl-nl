---
title: Implementeren en beheren van Power BI Premium-capaciteiten
description: De mogelijkheden van Power BI Premium begrijpen en meer informatie over het ontwerpen, implementeren, bewaken en problemen oplossen schaalbare oplossingen.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: fbae2a8b577c52ae597d44bd6ea9913510c4c65c
ms.sourcegitcommit: dc73e932c9982a4aa0b0ec5297fb9f94c6156bc5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66518571"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Implementeren en beheren van Power BI Premium-capaciteiten

**Samenvatting:** Power BI Premium biedt consistente prestaties, ondersteuning voor grote hoeveelheden gegevens en de flexibiliteit van een uniforme self-service en enterprise BI platform voor iedereen in uw organisatie. In dit technisch document met niveau 300 is specifiek voor Power BI-beheerders en auteurs van inhoud en uitgevers geschreven. Het is erop gericht om te begrijpen van de mogelijkheden van Power BI Premium, en waarin wordt uitgelegd hoe u kunt ontwerpen, implementeren, bewaken en problemen oplossen schaalbare oplossingen.

**Auteur:** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (Data Platform MVP en onafhankelijke BI deskundige met Bitsgewijs oplossingen)

**Technische controleurs:** Active Directory-toepassingsmodus Saxton, Akshai Nitin, Bhavik verkoper, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Olivier Matrat, Swati Gupta

**Van toepassing op:** Power BI-service, Power BI Premium en Azure Power BI Embedded-capaciteiten

> [!NOTE]
> U kunt dit technische document opslaan of afdrukken door in uw browser **Afdrukken** en vervolgens **Opslaan als PDF-bestand** te selecteren.

## <a name="introducing-power-bi"></a>Inleiding tot Power BI

Power BI is een business analytics service is ontworpen voor inzichten waarmee snelle en onderbouwde beslissingen te nemen. Sinds de release in 2015 is deze snel een populaire service die wordt gebruikt voor het leveren van oplossingen voor de kleinste van organisaties naar de grootste geworden van ondernemingen.

Deze wordt beschikbaar gesteld op twee manieren: Als een service in de cloud en een on-premises reporting oplossing met de naam **Power BI Report Server**. \[[1](#endnote-01)\]

Power BI als een cloudservice Software-as-a-Service (SaaS is) \[ [2](#endnote-02)\]. Hiermee geeft u een set services en toepassingen die organisaties kunnen te ontwikkelen, implementeren, beheren en deel oplossingen voor het controleren van hun bedrijf.

Het is niet de bedoeling van deze whitepaper over een uitgebreide beschrijving van de Power BI-service op te geven. In plaats daarvan ligt de nadruk op onderwerpen die relevant zijn voor het onderwerp van Power BI Premium. Raadpleeg voor algemene informatie over Power BI, de doorlopende [Power BI-documentatie](service-admin-premium-multi-geo.md). Voor een meer gedetailleerde uitleg van de Power BI-service met een focus op goed presterende enterprise-implementaties te bereiken, raadpleegt u de uitgebreide [een Power BI Enterprise-implementatie plannen](https://aka.ms/pbienterprisedeploy) technisch document.

Binnen de context van de houder van dit technisch document van deze sectie introduceert en beschrijvingen capaciteiten, Power BI inhoudstypen, model opslag modi en licentieverlening. Een goed begrip van de volgende onderwerpen is essentieel voor succes implementeren en beheren van Power BI Premium.

### <a name="capacities"></a>Capaciteiten

**Capaciteiten** een kernconcept van de Power BI voor een set met resources (opslag, processor en geheugen) gebruikt om te hosten en leveren van Power BI-inhoud zijn. Capaciteiten zijn gedeeld of toegewezen. Een **gedeelde capaciteit** wordt gedeeld met andere Microsoft-klanten, terwijl een **toegewezen capaciteit van** is volledig toegewezen voor één klant. Toegewezen capaciteit zijn geïntroduceerd in de [Premium-capaciteiten](#premium-capacities) onderwerp.

In gedeelde capaciteit workloads worden uitgevoerd op calculatiebronnen die worden gedeeld met andere klanten. Als de capaciteit bronnen delen moet, kunnen beperkingen worden opgelegd om ervoor te zorgen "eerlijke play', zoals de maximale Modelgrootte (1 GB) en de maximale dagelijkse vernieuwingsfrequentie (acht keer per dag).

### <a name="workspaces"></a>Werkruimten

Power BI-werkruimten in capaciteiten staan en staan voor beveiliging, samenwerking en implementatie van containers. Elke Power BI-gebruiker heeft een persoonlijke werkruimte wel **mijn werkruimte**. Extra werkruimten kunnen worden gemaakt om in te schakelen voor samenwerking en implementatie, en dit staat bekend als **App-werkruimten**. -Inclusief persoonlijke werkruimten - werkruimten worden standaard gemaakt in de gedeelde capaciteit.

### <a name="power-bi-content-types"></a>Power BI-inhoud typen

Om te introduceren Power BI Premium-onderwerpen, is het belangrijk om te beginnen met een uitgebreide bespreking van Power BI-architectuur met inbegrip van fundamentele typen inhoud.

Alle Power BI-inhoud is opgeslagen en beheerd in werkruimten die containers voor Power BI-inhoud zijn. Elke Power BI-gebruikers hun eigen persoonlijke werkruimte heeft, maar de algemeen aanbevolen procedure is het maken van app-werkruimten. App-werkruimten inschakelen co-ownership van inhoud en de mogelijkheid om samen te werken op inhoud. Ze bieden ook de mogelijkheid om te zetten en inhoud distribueren naar grote doelgroepen als apps.

De volgende Power BI-inhoud is opgeslagen in werkruimten:

- Gegevensstromen
- Gegevenssets
- Werkmappen
- Rapporten
- Dashboards

#### <a name="dataflows"></a>Gegevensstromen

Power BI-gegevensstromen kunnen organisaties om gegevens uit verschillende bronnen. Deze kunnen worden overwogen als gegevens voorbereid en tijdelijk worden opgeslagen voor gebruik in modellen, maar ze kunnen niet rechtstreeks als een bron worden gebruikt voor rapportage. Kunnen ze gebruikmaken van de uitgebreide verzameling gegevensconnectors van Microsoft, waardoor de opname van gegevens van on-premises en cloud-gebaseerde gegevensbronnen.

Gegevensstromen kunnen alleen worden gemaakt en beheerd in de app-werkruimten, en ze worden opgeslagen als entiteiten in de Common Data Model (CDM) in Azure Data Lake Storage Gen2. Normaal gesproken zijn gepland om te vernieuwen op periodieke basis voor het opslaan van actuele gegevens.

Voor meer informatie raadpleegt u de [dataprep selfservice in Power BI (Preview)](service-dataflows-overview.md) document.

#### <a name="datasets"></a>Gegevenssets

Power BI-gegevenssets vertegenwoordigen een bron van de gegevens die klaar zijn voor rapportage en visualisatie. Er zijn veel soorten gegevenssets, die zijn gemaakt door:

- Verbinding maken met een bestaand gegevensmodel die niet wordt gehost in een Power BI-capaciteit
- Uploaden van een Power BI Desktop-bestand met een model
- Uploaden van een Excel-werkmap (met een of meer Excel-tabellen en/of een werkmap-gegevensmodel) of een Comma-Separated waarde (CSV)-bestand uploaden
- Met de Power BI-service voor het maken van een push, streaming of hybride streaminggegevensset

Met uitzondering van streaminggegevenssets \[ [3](#endnote-03)\], vertegenwoordigt de gegevensset een gegevensmodel maakt gebruik van de technologieën volwassen modellen van Analysis Services.

Houd er rekening mee dat in de documentatie soms de terminologie gegevenssets en -modellen verwisselbaar zijn. Over het algemeen vanuit het oogpunt van Power BI-service wordt ernaar gerefereerd als een **gegevensset** , en uit oogpunt van ontwikkeling wordt ernaar gerefereerd als een **model**. In de context van dit technisch document betekenen die veel hetzelfde.

##### <a name="externally-hosted-models"></a>Extern gehoste modellen

Verbinding maken met een Extern gehost model omvat het installeren van de [On-Premises Data Gateway](service-gateway-onprem.md) verbinding maken met SQL Server Analysis Services, of het on-premises of virtuele machine wordt gehost Infrastructure-as-a-Service (IaaS). Azure Analysis Services is niet vereist voor een gateway. In dit scenario wordt vaak zinvol als er bestaande investeringen in model bestaan, doorgaans die deel uitmaken van de Enterprise Data Warehouse (EDW). Hierdoor kan Power BI om uit te voeren een **Liveverbinding** (LC) met Analysis Services en door het afdwingen van machtigingen voor gegevens met behulp van de identiteit van de gebruiker van Power BI-rapport. Voor SQL Server Analysis Services, worden zowel multidimensionale modellen (kubussen) en modellen in tabelvorm ondersteund. Zoals weergegeven in de volgende afbeelding, worden query's in een Liveverbinding gegevensset doorgegeven aan extern gehoste modellen.

![De gegevensset van een Liveverbinding met doorgegeven query's aan extern gehoste modellen](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Power BI Desktop ontwikkelde modellen

Power BI Desktop - een clienttoepassing die bestemd zijn voor de ontwikkeling van Power BI - kan worden gebruikt voor het ontwikkelen van een model dat is in feite een tabellair model van Analysis Services. Modellen kunnen worden ontwikkeld door het importeren van gegevens uit gegevensstromen, die vervolgens kunnen worden geïntegreerd met andere gegevensbronnen. Tijdens de details over hoe u modellen kunt doen is buiten het bereik van dit technisch document, is het belangrijk om te weten dat er drie verschillende typen - modi - modellen die kunnen worden ontwikkeld zijn met behulp van Power BI Desktop. Deze modi bepalen of gegevens worden geïmporteerd in het model, of of blijft in de gegevensbron. Er zijn drie modi: Import, DirectQuery en samengesteld. Een volledige bespreking van beide modi worden behandeld de [Model opslag modi](#model-storage-modes) onderwerp.

Extern gehoste modellen en modellen die zijn ontwikkeld in Power BI desktop kunnen afdwingen Row-Level Security (RLS) om te beperken van de gegevens die kunnen worden opgehaald voor een bepaalde gebruiker. Gebruikers die zijn toegewezen aan de beveiligingsgroep verkopers kunnen bijvoorbeeld alleen weergeven rapportgegevens voor de verkoop regio('s) waaraan ze zijn toegewezen. RLS-rollen kunnen dynamisch of statisch zijn. **Dynamische functies** filteren op de rapportgebruiker, terwijl **statische functies** voor alle gebruikers die zijn toegewezen aan de rol dezelfde filters toegepast.

##### <a name="excel-workbook-models"></a>Excel-werkmap modellen

Het maken van gegevenssets op basis van Excel-werkmappen of CSV-bestanden, leidt het automatisch maken van een model. Excel-tabellen en CSV-gegevens worden geïmporteerd voor het maken van tabellen voor gegevensmodel, terwijl een gegevensmodel van Excel-werkmap wordt voor het maken van een Power BI-model worden omgezet. In alle gevallen worden gegevens uit een bestand wordt geïmporteerd in een model.

Verschillen, kunnen vervolgens worden gemaakt over Power BI-gegevenssets die staan voor modellen:

- Ze ofwel worden gehost in de Power BI-service, of extern worden gehost door Analysis Services
- Geïmporteerde gegevens kunnen bevatten, of ze kunnen passthrough queryaanvragen geven voor de onderliggende gegevensbronnen, of een combinatie van beide

Hier volgt een samenvatting van belangrijke informatie over Power BI-gegevenssets die staan voor modellen:

- Modellen van SQL Server Analysis Services gehost vereisen wel een gateway LC query's uitvoeren
- Power BI-hosted modellen waarmee gegevens worden geïmporteerd
  - Volledig geladen in het geheugen moet zijn zodat ze kunnen worden opgevraagd
  - Vernieuw om de gegevens actueel houden nodig en moet betrekking hebben op gateways wanneer de brongegevens niet rechtstreeks via Internet toegankelijk is
- Power BI-hosted modellen die gebruikmaken van DirectQuery (DQ)-opslagmodus moeten verbinding met de brongegevens. Wanneer het model wordt gevraagd, geeft Power BI query's met de brongegevens huidige gegevens op te halen. In deze modus moet hebben betrekking op gateways wanneer de brongegevens niet rechtstreeks via Internet toegankelijk is.
- Modellen kunnen RLS-regels, het afdwingen van filters om te beperken van toegang tot gegevens voor bepaalde gebruikers afdwingen

Als u wilt met succes implementeren en beheren van Power BI Premium, is het belangrijk te weten waar de modellen worden gehost, de opslagmodus, eventuele afhankelijkheden van gateways, grootte van geïmporteerde gegevens, en vernieuwen type en de frequentie. Deze kunnen allemaal een aanzienlijke invloed hebben op de Power BI Premium-resources. Bovendien kunt het modelontwerp zelf, met inbegrip van de voorbereiding van query's en berekeningen toevoegen aan de combinatie van overwegingen.

Het is ook belangrijk om te weten dat Power BI-hosted import modellen kunnen vernieuwen op basis van planning of worden geactiveerd door een gebruiker in de Power BI-service.

Het ontwerpen van geoptimaliseerde modellen wordt besproken verderop in dit technische document in de [optimaliseren modellen](#optimizing-models) onderwerp.

#### <a name="workbooks"></a>Werkmappen

Power BI-werkmappen zijn een type van de Power BI-inhoud \[ [4](#endnote-04)\]. Excel-werkmappen die zijn geüpload naar Power BI-service en moeten niet worden verward met geüploade Excel-werkmappen die gegevenssets (modellen) zijn. Het inhoudstype van de werkmap vertegenwoordigt een verbinding met een werkmap, die ofwel kan worden geüpload naar Power BI-service of blijven in opslag in de cloud in OneDrive of SharePoint Online.

Het is belangrijk om te begrijpen dat dit type inhoud niet beschikbaar als een gegevensbron voor Power BI-gegevensvisualisaties is. In plaats daarvan kan worden geopend als een werkmap in Power BI-service met behulp van Excel Online. Het belangrijkste doel van dit type inhoud is waarmee verouderde Excel-werkmaprapporten zijn toegankelijk is vanuit de Power BI-service en om toe te staan de gegevensvisualisaties worden vastgemaakt aan Power BI-dashboards.

Voor meer informatie raadpleegt u de [gegevens ophalen uit Excel-werkmapbestanden](service-excel-workbook-files.md) document.

#### <a name="reports"></a>Rapporten

Er zijn twee typen rapporten: Power BI-rapporten en gepagineerde rapporten.

**Power BI-rapporten** bieden een interactieve gegevensvisualisatie ervaringen die verbindt met slechts één gegevensset. Rapporten zijn vaak bedoeld om aan te moedigen deelname van de gebruiker toe te staan te communiceren met een buitengewone reeks mogelijkheden, zoals filteren, segmenteren, kruislings filteren en markeren, uitzoomen, hoe u kunt inzoomen, uitzoomen, Q & een natuurlijke taal ondervragen, pagina te focussen, navigatie, spotlighting bladwijzers bekijken en meer.

In de context van dit technisch document, is het belangrijk om te begrijpen hoe de architectuur van Power BI, Power BI-rapport ontwerp- en -interacties allemaal gevolgen op de Power BI-service-resources hebben kunnen:

- Als u wilt laden en interactie met rapporten op basis van de import modellen, moet het model worden volledig geladen in het geheugen (die wordt gehost in de Power BI-service of Extern gehost)
- Elk rapport visual problemen met een query voor het ophalen van gegevens door het opvragen van het model
- Over het algemeen filter- en slicerstatus interacties hebben betrekking op het model uitvoeren van query's. Bijvoorbeeld, als u de slicerselectie van een wijzigt - standaard - moet elk visuele element op de pagina opnieuw laden \[ [5](#endnote-05)\]
- Power BI-rapporten niet gegarandeerd dat actuele gegevens weer te geven en is mogelijk de gebruiker het rapport opnieuw te laden van de rapportpagina en de visuals vernieuwen
- Gebruikers kunnen omgaan met de Q & een functie van natuurlijke taal vragen stellen, biedt het ontwerp van de Power BI-rapport wordt dit toegestaan en de gegevensset staat voor een model van Power BI-hosted gegevens importeren of een gegevensset LC is geconfigureerd voor Q & A inschakelen

**Gepagineerde rapporten** zodat de publicatie en rendering van SQL Server Reporting Services (SSRS) rapporten (\*RDL-indeling). Zoals de naam al aangeeft, wordt gepagineerde rapporten worden vaak gebruikt als nodig voor het afdrukken op een vast formaat vereisten, of wanneer er zijn variabele lijsten met gegevens die moet volledig worden uitgevouwen. Bijvoorbeeld, een factuur is ontworpen voor rendering met meerdere pagina's (in plaats binnen een visueel element schuiven) en afdrukken.

De twee ondersteunde rapporttypen biedt keuze voor auteurs van rapporten, zodat ze het type te selecteren op basis van vereisten en de bedoeling gebruiken. Power BI-rapporten zijn algemeen, ideaal voor interactieve ervaringen zodat de gebruiker om te verkennen en het ontdekken van inzichten uit gegevens, terwijl gepagineerde rapporten beter voor de parameter-driven pagina-indeling geschikt zijn.

Ongeacht het rapporttype is van cruciaal belang voor het leveren met een betrouwbare en goed presterende gebruikerservaring responsief rapport laden en gegevens updates bereiken (als filters of parameters worden gewijzigd).

#### <a name="dashboards"></a>Dashboards

Power BI-dashboards zijn bedoeld om te controleren ervaringen bieden en zijn conceptueel gezien heel verschillend van Power BI-rapporten. Dashboards zijn ontworpen voor weergave op een enkel glazen Express waarden en visualisaties in tegels. Dashboards bieden over het algemeen minder interactie ervaringen dan Power BI-rapporten met sommige dashboard ontwerpen zonder tussenkomst van de wordt verwacht. Bijvoorbeeld: een zonder toezicht dashboard weergegeven op een niet-touchscreen in een kamer van de server. Een andere belangrijke verschil is dat dashboards tegels die brongegevens uit meerdere gegevenssets, terwijl een Power BI-rapport kan altijd maar zijn gebaseerd op een enkele gegevensset kunnen opleveren.

Het is belangrijk om te begrijpen dat een dashboard is ontworpen om te snel geladen en de meest recente gegevens (bekend is bij de Power BI-service) op alle snelle tijden. Het bereikt dit door de queryresultaten naast elkaar opslaan in cache en dit gebeurt voor elk dashboard. In feite moet zij dit doen voor elke gebruiker die toegang heeft tot een dashboard dat is gebaseerd op modellen die dynamische beveiliging op Rijniveau afdwingen.

Dashboard query caches updates Power BI-service automatisch direct na het importeren van Power BI-hosted modellen worden vernieuwd. In het geval van LC en DQ modellen is de eigenaar van de gegevensset een zekere mate van controle over hoe vaak de cache, die kan worden geconfigureerd als vaak als elke 15 minuten of weinig één keer per week in Power BI-service worden bijgewerkt. Houd er rekening mee dat LC query cache updates eerst query's modelmetagegevens uitvoeren om te bepalen of het vernieuwen van een model heeft plaatsgevonden sinds de laatste update van de cache en deze wordt niet gaat u verder met de cache bijwerken wanneer sindsdien niet een vernieuwing heeft plaatsgevonden. Deze controle is niet mogelijk voor DQ modellen en dus cache updates of de brongegevens zijn gewijzigd of niet wordt uitgevoerd.

Dashboard querycache bijgewerkt op basis van DQ en LC modellen aanzienlijk op zowel Power BI-service-resources en externe gegevensbronnen kunnen worden beïnvloed. U kunt een dashboard met 20 tegels, alles op basis van een Azure Analysis Services-model dat dynamische beveiliging op Rijniveau wordt afgedwongen en die elk uur wordt vernieuwd en dat dit dashboard is gedeeld met 100 gebruikers. Als de gegevensset is geconfigureerd voor het vernieuwen van elk uur, resulteert dit in ten minste 2000 (20 x 100) LC query's. Dit kan een enorme belasting op de Power BI-service en de externe gegevensbronnen plaatsen en het kan ook overschrijdt de grenzen die zijn opgelegd voor beschikbare resources. Capaciteit en limieten worden beschreven in de [Capaciteitsknooppunten](#capacity-nodes) onderwerp.

Gebruikers kunnen werken met een dashboard op verschillende manieren, waarvoor de bronnen van Power BI-service. Specifiek, kunnen ze:

- Een vernieuwing van dashboardtegels, wat leiden een vernieuwing op aanvraag van alle gerelateerde gegevens Power BI-hosted import modellen tot kan activeren
- Neem contact op met de Q & een functie van natuurlijke taal vragen (inclusief het ontwerpen van dashboards toestaat en de gegevensset is een model van Power BI-hosted gegevens importeren of een gegevensset LC is geconfigureerd voor Q & A inschakelen)
- Gebruik de functie Snelle inzichten in om Power BI ontdekken van inzichten van een onderliggende gegevensset en reageren met visuele elementen die worden weergegeven en beschreven (inclusief dat de tegel is gebaseerd op een gegevensset die wordt gehost Power BI-gegevens importeren model)
- Waarschuwingen configureren op dashboardtegels, dat de Power BI-service om te vergelijken drempelwaarden waarden zijn: mogelijk zo vaak als per uur - tegel en gebruikers waarschuwen wanneer drempels zijn overschreden (dat de tegel toont één numerieke waarde en is gebaseerd op een de gegevensset die wordt gehost Power BI-gegevens importeren model)

### <a name="model-storage-modes"></a>Modi voor opslag

Intrekken dat Power BI Desktop kunt ontwikkelen van een model in een van drie modi. Het is belangrijk om te begrijpen van de logica voor elke opslagmodus voor gegevens-model en de mogelijke gevolgen voor de bronnen van Power BI-service. In deze sectie wordt alle drie de modi. Deze zal worden gedetailleerd besproken verderop in dit technisch document in het onderwerp modellen te optimaliseren.

#### <a name="import-mode"></a>Importmodus

Importmodus is de meest voorkomende modus voor het ontwikkelen van modellen vanwege het zeer snelle prestaties die zijn gekoppeld aan in het geheugen uitvoeren van query's, de flexibiliteit bij het ontwerpen worden modelers, en ondersteuning voor specifieke Power BI-servicemogelijkheden (Q & A, snelle inzichten enz.). Dit is de standaardmodus bij het maken van een nieuwe Power BI Desktop-oplossing.

Het is belangrijk om te begrijpen dat geïmporteerde gegevens altijd worden opgeslagen op schijf en moeten worden volledig geladen in het geheugen worden opgevraagd of vernieuwd. Eenmaal in het geheugen, import modellen enorm snelle queryresultaten bereiken. Het is ook belangrijk om te weten dat er geen concept van een model importeren is gedeeltelijk in het geheugen wordt geladen is.

Vernieuwd, worden gegevens gecomprimeerd en geoptimaliseerd en klik vervolgens op de schijf zijn opgeslagen door de VertiPaq-opslag-engine. Wanneer in het geheugen geladen vanaf schijf, is het mogelijk om te zien van 10 x compressie en het is dus redelijk te verwachten dat 10 GB aan gegevens tot ongeveer 1 GB groot comprimeren kunt. Opslaggrootte op schijf kunt hiervoor een 20% korting op de voorgrond. \[[6](#endnote-06)\]

Flexibiliteit bij het ontwerpen kunt op drie manieren worden bereikt. Gegevensmodellen kunt doen:

- Integreer gegevens met caching van gegevens uit meerdere bronnen -, ongeacht het gegevensbrontype en indeling
- Maak gebruik van de volledige set van functies van Power Query-Formuletaal (informeel M genoemd) bij het maken van query's voorbereiden
- Gebruikmaken van de volledige set van functies voor Data Analysis Expressions (DAX) wanneer het model met zakelijke logica, berekende kolommen, berekende tabellen en-maatregelen verbeteren

Zoals weergegeven in de volgende afbeelding, kan een model importeren gegevens uit een willekeurig aantal ondersteunde typen gegevensbronnen kunt integreren.

![Een model importeren kunt gegevens uit een willekeurig aantal ondersteunde typen gegevensbronnen integreren](media/whitepaper-premium-deployment/import-model.png)

Hoewel er aantrekkelijke voordelen die zijn gekoppeld aan import modellen, zijn er echter nadelen te:

- Het hele model moet worden geladen in het geheugen voordat Power BI een query het model, deze druk plaatsen kunt aan het aantal en de grootte van modellen op beschikbare bronnen
- Modelgegevens is alleen de meest recente vernieuwing zo actueel en dus import modellen moeten worden vernieuwd, bij voorkeur op een gepland schema
- Een volledige vernieuwing worden alle gegevens verwijderen uit alle tabellen en laad deze opnieuw uit de gegevensbron. Dit kan zijn bijzonder veeleisende in termen van tijd en resources voor Power BI-service en de gegevensbron(nen). Power BI beschikt over ondersteuning voor incrementeel vernieuwen die bezig met afbreken en opnieuw te laden hele tabellen kunt voorkomen en dit wordt behandeld de [Optimizing Power BI-Hosted modellen](#optimizing-power-bi-hosted-models) onderwerp.

Uit een perspectief van de resource in de Power BI-service vereisen import modellen:

- Voldoende geheugen laden van het model wanneer deze wordt opgevraagd of vernieuwd
- Resources voor het verwerken en extra geheugenbronnen om gegevens te vernieuwen

#### <a name="directquery-mode"></a>DirectQuery-modus

Modellen die zijn ontwikkeld in de modus DirectQuery (DQ) importeren gegevens niet. In plaats daarvan bestaan alleen uit metagegevens wordt opgevraagd problemen systeemeigen query's naar de onderliggende gegevensbron.

![Problemen met systeemeigen query's naar de onderliggende gegevensbron een DirectQuery-model](media/whitepaper-premium-deployment/direct-query-model.png)

Er zijn twee belangrijke redenen om te overwegen een analysemodel DQ. De eerste reden is wanneer gegevensvolumes te groot is -, zelfs wanneer gegevens vermindering methoden worden toegepast - laden in een gegevensmodel of vrijwel vernieuwen. De tweede reden is wanneer u rapporten en dashboards die zijn vereist voor het leveren van de gegevens 'bijna realtime' is, dan wat binnen de grenzen van de geplande vernieuwing (48 keer per dag voor een toegewezen capaciteit) kan worden bereikt.

Er zijn diverse voordelen die zijn gekoppeld aan DQ modellen:

- Maximale grootte van importeren model niet van toepassing
- Modellen hoeven niet vernieuwen
- Rapportgebruikers zien de meest recente gegevens tijdens interactie met de rapportfilters en slicers, en het hele rapport huidige gegevens op te halen kunt vernieuwen
- Dashboard-tegels, bij op basis van modellen DQ, automatisch kunnen worden bijgewerkt als elke 15 minuten

Er zijn echter talrijke nadelen en beperkingen die zijn gekoppeld aan DQ modellen:

- Het model moet worden gebaseerd op een ondersteunde gegevensbron en daarom een integratie van gegevens moet al zijn bereikt in de gegevensbron. Ondersteunde gegevensbronnen zijn relationele en analytische systemen, met ondersteuning voor veel populaire gegevensarchieven \[ [7](#endnote-07)\].
- Prestaties kan traag zijn, mogelijk een negatieve invloed op de Power BI-service (query's kunnen erg CPU-intensief zijn) en op de gegevensbron (die mogelijk niet zijn geoptimaliseerd voor analytische query's) zijn
- Power Query-query's kunnen niet te ingewikkeld en zijn beperkt tot de M-expressies en functies die kunnen worden omgezet naar systeemeigen query's door de gegevensbron te begrijpen
- DAX-functies zijn beperkt tot die kunnen worden omgezet naar systeemeigen query's begrepen door de gegevensbron en er is geen ondersteuning voor berekende tabellen of ingebouwde voorzieningen voor Time Intelligence
- Standaard mislukt model-query's die nodig voor het ophalen van meer dan één miljoen rijen hebt
- Rapporten en dashboards met meerdere visuele elementen kunnen inconsistente resultaten weergeven met name wanneer de gegevensbron vluchtig zijn
- Q & A en snelle inzichten worden niet ondersteund.

Uit een perspectief van de resource in de Power BI-service vereisen DQ modellen:

- Het minimale geheugen laden van het model (alleen metagegevens) wanneer deze wordt opgevraagd
- Soms aanzienlijke processorbronnen genereren en verwerken van query's verzonden naar de gegevensbron

Voor meer informatie raadpleegt u de [Directquery gebruiken in Power BI Desktop](desktop-use-directquery.md) document.

#### <a name="composite-mode"></a>Samengestelde modus

Modellen die zijn ontwikkeld in de modus voor samengestelde kunnen de modus voor opslag voor afzonderlijke model-tabellen configureren. Daarom ondersteunt een combinatie van invoer- en DQ tabellen. Het ondersteunt ook berekende tabellen (gedefinieerd met DAX) en meerdere DQ-gegevensbronnen.

Opslagmodus van de tabel kan worden geconfigureerd als Import, DirectQuery of Dual. Een tabel die is geconfigureerd als dubbele opslagmodus is zowel importeren als DirectQuery en Hiermee wordt de Power BI-service om te bepalen van de meest efficiënte modus te gebruiken op basis van de query door de query.

![Een samengestelde model is een combinatie van de Import- en DQ opslag modi, geconfigureerd op het tabelniveau van de](media/whitepaper-premium-deployment/composite-model.png)

Samengestelde modellen streven naar het beste van importeren en DirectQuery-modus. Wanneer geconfigureerd op de juiste wijze kunnen ze hoge queryprestaties van modellen in het geheugen combineren met de mogelijkheid om op te halen in de buurt van real-time gegevens van gegevensbronnen.

Gegevensmodellen die samengestelde modellen ontwikkelen waarschijnlijk dimensietype tabellen configureren in Import of Dual-modus en type feit opslagtabellen in de modus DirectQuery. Neem bijvoorbeeld een model met een tabel van de dimensie-type Product in Dual-modus en een verkooptabel feit-type in de modus DirectQuery. De tabel Product kan worden snel en efficiënt opgevraagd uit in het geheugen om een rapportslicer weer te geven. De tabel Sales kan vervolgens worden doorzocht in DirectQuery-modus die lid is van de gerelateerde tabel Product. De laatste query kan de generatie van een enkele efficiënte systeemeigen query om toe te voegen tabellen Product en Sales en filteren door de waarden van de slicer inschakelen.

In het algemeen de voordelen en nadelen, die zijn gekoppeld aan elke modus model kunnen worden beschouwd als toe te passen op de opslagmodus tabel in samengestelde modellen.

Voor meer informatie raadpleegt u de [samengestelde modellen gebruiken in Power BI Desktop](desktop-composite-models.md) document.

### <a name="licensing"></a>Licentieverlening

Power BI heeft drie licenties:

- Gratis versie van Power BI
- Power BI Pro
- Power BI Premium

De **Power BI Free** licentie staat een persoon zich aanmeldt bij Power BI-service en werken binnen hun persoonlijke werkruimte door modellen en rapporten te publiceren. Het is belangrijk om te begrijpen dat het is niet mogelijk voor het delen van Power BI-inhoud met behulp van deze licentie. Deze licentie, is zoals de naam al aangeeft, gratis.

De **Power BI Pro** licentie staat een individu maken en samenwerken binnen de app-werkruimten en delen en distribueren van Power BI-inhoud. Ze kunnen ook vernieuwen voor de gegevenssets automatisch gegevens om up-to-date te houden, met inbegrip van on-premises gegevensbronnen configureren. Bovendien kunnen controleren en bepalen hoe gegevens worden geopend en die wordt gebruikt. Deze licentie is vereist voor het ontvangen van gedeelde inhoud van andere, tenzij de gebruiker gekoppeld aan een capaciteit van Power BI Premium is toegewezen is.

De **Power BI Premium** licentie is een licentie op tenantniveau en deze wordt besproken in de [introductie van Power BI Premium](#introducing-power-bi-premium) sectie.

Raadpleeg voor meer informatie over de licentieverlening voor Power BI de [prijzen van Power BI](https://powerbi.microsoft.com/pricing/) pagina.

## <a name="introducing-power-bi-premium"></a>Introducing Power BI Premium

Power BI Premium biedt een uniforme self-service en enterprise BI platform met schaal, betrouwbare prestaties en voorspelbare kosten. Voornamelijk bereikt dit door op te geven van de toegewezen resources voor het uitvoeren van de Power BI-service voor uw organisatie.

Power BI Premium biedt bovendien veel enterprise-functies:

- Rendabele distributie van inhoud, waardoor het delen van Power BI-inhoud naar een onbeperkt aantal gebruikers voor Power BI Free, met inbegrip van externe gebruikers
- Ondersteuning voor grotere gegevensset \[ [8](#endnote-08)\]
- Hogere vernieuwingsfrequenties van gegevensstromen en gegevenssets (maximaal 48 keren per dag)
- Incrementeel vernieuwen van gegevensstromen en gegevenssets
- Gegevensstroom gekoppelde entiteiten en parallelle uitvoering van transformaties
- Gepagineerde rapporten
- Power BI Report Server, voor on-premises rapportage
- Mogelijkheid om inhoud in apps insluiten namens app-gebruikers (PaaS)

Veel van deze functies kunnen worden gebruikt voor het leveren van efficiënte en schaalbare bedrijfsoplossingen en worden behandeld in de [optimaliseren van Premium-capaciteiten](#optimizing-premium-capacities) sectie.

### <a name="subscriptions-and-licensing"></a>Abonnementen en licentieverlening

Power BI Premium is een op tenantniveau Office 365-abonnement beschikbaar in twee SKU (Stock Keeping Unit)-families:

- **EM** SKU's (EM1-EM3) voor het insluiten van inhoud, vereisen een jaarlijkse toezegging hebben gedaan, maandelijks gefactureerd
- **P** SKU's (P1-P3) voor het insluiten van inhoud en enterprise-functies vereisen een maandelijkse of jaarlijkse toezegging, maandelijks gefactureerd en bevat een licentie voor Power BI Report Server on-premises installeert

Een alternatieve methode is het kopen van een Azure Power BI Embedded-abonnement met een enkele SKU-serie: **Een** SKU's (A1-A6) voor het insluiten van inhoud en -capaciteit alleen testdoeleinden.

Alle SKU's leveren v-cores voor het maken van capaciteit \[ [9](#endnote-09)\], maar de EM-SKU's zijn niet toegestaan voor het insluiten van kleinere schaal. Hoewel de focus van dit technisch document over de P-SKU, is veel van wat wordt besproken ook relevant zijn ook voor de A-SKU's.

In tegenstelling tot de Premium-abonnement SKU's, Azure-SKU's vereisen geen verplichtingen op tijd en worden per uur gefactureerd. Ze bieden volledige elasticiteit inschakelen schaal omhoog, omlaag schalen, onderbreken, hervatten en verwijderen.

Azure Power BI Embedded is grotendeels buiten het bereik van dit technisch document, maar deze wordt besproken in het onderwerp benaderingen testen als een praktische en economische optie voor het testen en meten van workloads.

Raadpleeg voor meer informatie over de Azure SKU's, de [documentatie voor Azure Power BI Embedded](/azure/power-bi-embedded/).

Power BI Premium-abonnementen worden aangeschaft door beheerders in de Microsoft 365-beheercentrum. Specifiek, kunnen alleen globale beheerders van Office 365 of beheerders facturering SKU's aanschaffen.

Nadat u hebt aangeschaft, ontvangt een overeenkomstige aantal v-cores om toe te wijzen aan capaciteit - Dit staat bekend als **v-core groepering**. Een P3-SKU kopen geeft bijvoorbeeld de tenant 32 v-cores.

Voor meer informatie raadpleegt u de [Power BI Premium kopen](service-admin-premium-purchase.md) document.

### <a name="premium-capacities"></a>Premium-capaciteiten

In tegenstelling tot een gedeelde capaciteit waar workloads worden uitgevoerd op calculatiebronnen die worden gedeeld met andere klanten kunnen een **toegewezen capaciteit** is voor exclusief gebruik door een organisatie. Het is geïsoleerd met een toegewezen rekenkracht, waardoor de betrouwbare en consistente prestaties voor gehoste inhoud.

De focus van dit technisch document is **Premium-capaciteit** , wat betekent dat deze is gekoppeld aan een van de EM- of P-SKU's.

#### <a name="capacity-nodes"></a>Capaciteit knooppunten

Zoals is beschreven in de abonnementen en licentieverlening onderwerp, zijn er twee Power BI Premium SKU-families: EM en P. Alle Power BI Premium-SKU's zijn beschikbaar als capaciteitsknooppunten van de, met elk bij een vaste hoeveelheid resources die bestaat uit een processor, geheugen en opslag. Naast de resources, elke SKU heeft operationele limieten voor het aantal verbindingen van DirectQuery (DQ) en Live-verbinding (LC) per seconde en het aantal parallelle model wordt vernieuwd.

Verwerking wordt bereikt door een bepaald aantal v-cores, evenredig verdeeld over back-end en frontend.

**Back-end-v-cores** verantwoordelijk zijn voor de kernfunctionaliteit van het Power BI queryverwerking, Cachebeheer, uitvoeren van R services, modelvernieuwing, verwerking van natuurlijke taal (Q & A) en server-side rendering van rapporten en afbeeldingen. Back-end-v-cores zijn een vaste hoeveelheid geheugen die wordt primair gebruikt voor het host-modellen die ook worden aangeduid als actieve gegevenssets toegewezen.

**Front-end-v-cores** verantwoordelijk zijn voor de web service, dashboard en rapport documentbeheer, beheren van de toegangsrechten, planning, API's, wordt geüpload en gedownload en in het algemeen voor alles met betrekking tot de gebruiker optreedt.

Opslag is ingesteld op 100 TB per capaciteitsknooppunt.

De resources en limieten van elke Premium-SKU (en de grootte oftewel een SKU) in de volgende tabel worden beschreven.

| Capaciteit knooppunten | Totaal aantal v-cores | v-cores voor back-end | RAM (GB) | v-cores voor front-end | DQ/LC (per seconde) | Model vernieuwen parallelle uitvoering |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Capaciteit Workloads

Capaciteit werkbelastingen zijn services beschikbaar gesteld aan gebruikers. Standaard ondersteuning voor Premium en Azure-capaciteiten alleen een gegevensset werkbelasting die is gekoppeld aan het uitvoeren van Power BI-query's die niet kunnen worden uitgeschakeld.

Extra werkbelasting kunnen worden ingeschakeld voor gepagineerde rapporten, gegevensstromen en AI. Elke extra belasting is vereist voor het configureren van de maximale hoeveelheid geheugen (als percentage van totale beschikbare geheugen) door de werkbelasting kan worden gebruikt.

#### <a name="how-capacities-function"></a>Hoe capaciteiten werken

Allen tijde wil de Power BI-service het beste gebruik van capaciteit resources maken terwijl de capaciteit niet meer dan limieten opgelegd.

Capaciteit bewerkingen zijn geclassificeerd als een interactieve of achtergrond. Interactieve bewerkingen zijn onder meer het weergeven van aanvragen van en reageren op interactie van gebruikers (filteren, Q & A uitvoeren van query's, enz.). Over het algemeen is uitvoeren van query's importeren model geheugen resource-intensieve CPU-intensieve LC/DQ modellen uitvoeren van query's is. Bewerkingen op de achtergrond gegevensstroom opnemen en importeer model wordt vernieuwd en dashboard query opslaan in cache.

Het is belangrijk om te begrijpen dat interactieve bewerkingen altijd voorrang boven bewerkingen op de achtergrond krijgen om te controleren of de best mogelijke gebruikerservaring. Als er onvoldoende bronnen, worden de bewerkingen op de achtergrond toegevoegd aan een wachtrij voor verwerking en resources vrij te maken. Bewerkingen op de achtergrond, zoals gegevensset wordt vernieuwd en AI-functies, kunnen worden gestopt halverwege verwerkt door de Power BI-service en toegevoegd aan een wachtrij.

Import modellen moet volledig geladen in het geheugen, zodat ze kunnen worden opgevraagd of vernieuwd. Geheugen gebruik door middel van geavanceerde algoritmen om ervoor te zorgen maximaal gebruik van het beschikbare geheugen en kan maar liefst inplannen van meer de capaciteit wordt beheerd door de Power BI-service: Het is mogelijk voor een capaciteit voor het opslaan van veel import-modellen (maximaal 100 TB per Premium-capaciteit), wanneer de gecombineerde schijfopslag de ondersteunde geheugen overschrijdt (en extra geheugen vereist voor het uitvoeren van query's en vernieuwen is), klikt u vervolgens deze kunnen niet alle worden geladen in het geheugen op tegelijkertijd.

Import modellen zijn daarom geladen in - en verwijderd uit het - geheugen op basis van gebruik. Een model importeren wordt geladen wanneer het opgevraagde (interactieve bewerking) is en is nog niet in het geheugen, of wanneer het is om te worden vernieuwd (bewerking op de achtergrond).

Het verwijderen van een model uit het geheugen wordt ook wel **verwijdering** , en het is een bewerking die Power BI snel, afhankelijk van de grootte van de modellen uitvoeren kunt. Als de capaciteit niet een geheugendruk voordoet is, zijn modellen eenvoudig in het geheugen geladen en er blijft. \[[10](#endnote-10) \] echter wanneer er onvoldoende geheugen beschikbaar om te laden van een model is, Power BI-service moet eerst geheugen vrij te maken. Het geheugen vrijgemaakt door het detecteren van modellen die door de modellen die niet zijn gebruikt in de laatste drie minuten inactief zijn geworden \[ [11](#endnote-11)\], en ze vervolgens te verwijderen. Als er geen niet-actieve modellen onbeschikbaar maken, zoekt Power BI-service onbeschikbaar maken van modellen die worden geladen voor bewerkingen op de achtergrond. Dit kan de verwijdering van achtergrond-workloads, zoals de AI-werkbelasting omvatten. Laatste redmiddel na 30 seconden van mislukte pogingen \[ [11](#endnote-11)\], wordt de interactieve bewerking mislukken. In dit geval de rapportgebruiker wordt zonder problemen op de hoogte gesteld van de fout met een suggestie om te proberen het over enkele ogenblikken opnieuw.

Het is belangrijk om te zorgen dat de verwijdering van de gegevensset een normale en de verwachte gedrag is. Wordt ernaar gestreefd om te maximaliseren van geheugengebruik door laden en modellen waarvan gecombineerde grootte kunnen groter zijn dan beschikbaar geheugen op te lossen. Dit is het ontwerp en volledig transparant voor gebruikers. Hoge verwijdering tarieven betekenen niet noodzakelijkerwijs dat de capaciteit is onvoldoende resources voorzien. Ze kunnen echter een probleem worden als query of vernieuwen reactietijd is lijden vanwege de hoge verwijdering tarieven.

Vernieuwen van import modellen zijn altijd geheugenintensieve modellen moeten worden geladen in het geheugen en meer geheugen is vereist voor de verwerking. Een volledige vernieuwing kunt ongeveer de dubbele hoeveelheid geheugen die nodig is voor het model gebruiken. Dit zorgt ervoor dat het model kan worden opgevraagd, zelfs wanneer die worden verwerkt (query's verzonden naar het bestaande model, totdat het vernieuwen is voltooid en de gegevens van het nieuwe model beschikbaar is). Opmerking: incrementeel vernieuwen minder geheugen is vereist en kan sneller zijn voltooid en dus kan aanzienlijk verminderen druk op de capaciteit van bronnen. Vernieuwen kunnen ook worden de CPU-intensieve voor modellen, met name degenen die complexe Power Query-transformaties of berekende tabellen/kolommen die zijn complexe of zijn gebaseerd op grote tabellen.

Vernieuwingen -, query's, zoals is vereist dat het model in het geheugen worden geladen. Als er onvoldoende geheugen, Power BI-service probeert te verwijderen van inactieve modellen, en als dit niet mogelijk is (als alle modellen actief zijn), de vernieuwingstaak is in de wachtrij geplaatst. Vernieuwingen worden doorgaans erg CPU-intensieve, zelfs meer dus dan query's. Om deze reden zijn er beperkingen van de capaciteit van het aantal gelijktijdige wordt vernieuwd, ingesteld op 1,5 keer het aantal back-end-v-cores, naar boven afgerond. Als er te veel gelijktijdige wordt vernieuwd, een geplande vernieuwing wordt in de wachtrij geplaatst. Wanneer deze situaties zich voordoet, duurt het langer voor het vernieuwen is voltooid. Houd er rekening mee dat drie keer wordt opnieuw geprobeerd op aanvraag wordt vernieuwd (geactiveerd door een aanvraag van de gebruiker of een API-aanroep) \[ [11](#endnote-11)\], en vervolgens mislukken als er nog steeds niet voldoende bronnen zijn.

## <a name="managing-power-bi-premium"></a>Managing Power BI Premium

Power BI Premium beheren omvat het aanschaffen van abonnementen, en maken, beheren en controleren van de Premium-capaciteiten.

### <a name="creating-and-managing-capacities"></a>Het maken en beheren van capaciteit

De **capaciteitsinstellingen** pagina van de **Power BI-beheerder** Portal geeft het aantal v-cores aangeschaft en beschikbaar (dat wil zeggen nog moet worden toegewezen aan een capaciteit) en een lijst met Premium-capaciteiten. Op de pagina kunt beheerders Premium-capaciteiten van beschikbare v-cores maken of wijzigen van bestaande Premium-capaciteiten voor globale beheerders van Office 365 of Power BI-service.

Bij het maken van een Premium-capaciteit, moet de beheerder is vereist om te definiëren:

- Capaciteitsnaam (uniek zijn binnen de tenant)
- Capaciteit admin(s)
- Capaciteitsgrootte
- De regio voor gegevensresidentie \[ [12](#endnote-12)\]

Ten minste één Capaciteitsbeheerder moet worden toegewezen. Gebruikers die zijn toegewezen als Capaciteitsbeheerders kunt doen:

- Werkruimten toewijzen aan de capaciteit
- Gebruikersmachtigingen, voor het toevoegen van extra Capaciteitsbeheerders of gebruikers met toewijzingsmachtigingen (zodat ze werkruimten toewijzen aan de capaciteit) beheren
- Workloads voor het configureren van maximale geheugengebruik voor gepagineerde rapporten en gegevensstromen workloads beheren
- Opnieuw opstarten van de capaciteit, opnieuw instellen van alle bewerkingen in het geval van systeem overbelasting \[ [13](#endnote-13)\]

Capaciteitsbeheerders heeft geen toegang tot inhoud van de werkruimte (tenzij expliciet toegewezen machtigingen voor de werkruimte) en ze ook geen toegang tot alle gebieden van de Power BI-beheerder (tenzij expliciet toegewezen), zoals metrische gegevens over gebruik, auditlogboeken of tenantinstellingen. Bovendien bent Capaciteitsbeheerders niet gemachtigd voor het maken van nieuwe capaciteiten of bestaande capaciteiten te schalen. Bovendien zijn toegewezen op een per-capaciteit-basis, ervoor te zorgen dat ze alleen kunnen weergeven en beheren van de capaciteiten waarvoor ze zijn toegewezen.

Capaciteitsgrootte moet worden geselecteerd uit een lijst met beschikbare SKU-opties die wordt beperkt door het aantal beschikbare v-cores in de groep. Het is mogelijk te maken van meerdere capaciteiten van de pool die kan worden afkomstig is van een of meer SKU's die zijn aangeschaft. Bijvoorbeeld een P3 SKU (32 v-cores) kunnen worden gebruikt voor het maken van drie capaciteiten: één P2 (16 v-cores), en twee P1 (2 x 8 v-cores). Verbeterde prestaties en schaal kunnen worden bereikt door het maken van kleinere grootte capaciteiten en in dit onderwerp wordt beschreven in de [optimaliseren van Premium-capaciteiten](#optimizing-premium-capacities) sectie. De volgende afbeelding toont een voorbeeld van de instellingen voor de fictieve Contoso-organisatie die bestaat uit vijf Premium-capaciteiten (3 x P1 en 2 x P3) met elke met app-werkruimten en verschillende werkruimten in gedeelde capaciteit.

![Een voorbeeld van de instellingen voor de fictieve organisatie Contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Een Premium-capaciteit kan worden toegewezen aan een andere regio dan de basisregio van de Power BI-tenant, beheer via welke datacenters (in afgebakende geografische regio's) Power BI-inhoud zich bevindt. \[[12](#endnote-12)\]

Power BI-servicebeheerders en globale beheerders van Office 365 kunt Premium-capaciteiten wijzigen. Specifiek, kunnen ze:

- Wijzig de grootte van de capaciteit om te vergroten of verkleinen van resources. Het is echter niet mogelijk om te downgraden van een P-SKU in een EM-SKU, of omgekeerd te upgraden.
- Toevoegen of verwijderen van Capaciteitsbeheerders
- Gebruikers die over toewijzingsmachtigingen beschikken toevoegen of verwijderen
- Toevoegen of verwijderen van extra werkbelasting
- Regio's wijzigen

Machtigingen voor capaciteitstoewijzingen zijn vereist voor een werkruimte toewijzen aan een specifieke Premium-capaciteit. De machtigingen kunnen worden verleend aan de hele organisatie, specifieke gebruikers of groepen.

Standaard ondersteuning voor Premium-capaciteiten werkbelastingen die zijn gekoppeld aan het uitvoeren van query's van Power BI. Het biedt ook ondersteuning voor drie extra workloads: **Gepagineerde rapporten**, **gegevensstromen**, en **AI**. Elke workload is vereist voor het configureren van de maximale hoeveelheid geheugen (als percentage van totale beschikbare geheugen) door de werkbelasting kan worden gebruikt. Het is belangrijk om te begrijpen dat maximale geheugentoewijzingen verhogen kan invloed hebben op op het aantal actieve modellen die kan worden gehost, en de doorvoer van wordt vernieuwd.

Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar in het geval van gepagineerde rapporten betreft het een statische toewijzing. De reden voor het toewijzen van statisch de maximale hoeveelheid geheugen is dat gepagineerde rapporten worden uitgevoerd binnen een beveiligde ruimte van de capaciteit die wordt ingesloten. Zorg moet worden uitgevoerd wanneer de instelling gepagineerde rapporten geheugen als beperkt het beschikbare geheugen voor het laden van modellen.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Gepagineerde rapporten | N.v.t. | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% | standaard 20%; minimaal 2,5% |
| Gegevensstromen | standaard 20%; minimaal 8%  | standaard 20%; minimaal 4%  | standaard 20%; minimaal 2% | standaard 20%; minimaal 1%  |
| AI | N.v.t. | standaard 20%. 20% minimale  | standaard 20%; minimaal 10% | standaard 20%; minimaal 5%  |
| | | | | |

Verwijderen van een Premium-capaciteit is mogelijk en leidt niet tot het verwijderen van de werkruimten en de inhoud. In plaats daarvan wordt er geen toegewezen werkruimten verplaatst naar gedeelde capaciteit. Wanneer de Premium-capaciteit is gemaakt in een andere regio, wordt de werkruimte worden verplaatst naar gedeelde capaciteit van de eigen regio.

### <a name="assigning-workspaces-to-capacities"></a>Werkruimten toewijzen aan capaciteit

Werkruimten kunnen worden toegewezen aan een Premium-capaciteit in de **Power BI-beheerder** **Portal** of - voor een app-werkruimte, in de **werkruimte** deelvenster.

Capaciteitsbeheerders, evenals globale beheerders van Office 365 of Power BI-servicebeheerders kunnen bulksgewijs werkruimten toewijzen in de **Power BI-beheerder** **Portal**. Toegewezen bulksgewijs kunt toepassen op:

- **Werkruimten door gebruikers** : Alle werkruimten die eigendom zijn van gebruikers, met inbegrip van persoonlijke werkruimten zijn toegewezen aan de Premium-capaciteit. Hierbij wordt het opnieuw toewijzen van werkruimten wanneer ze al zijn toegewezen aan een ander Premium-capaciteit. Bovendien zijn de gebruikers ook machtigingen voor capaciteitstoewijzingen werkruimte toegewezen.

- **Specifieke werkruimten**
- **Werkruimten van de hele organisatie** : Alle werkruimten, met inbegrip van persoonlijke werkruimten zijn toegewezen aan de Premium-capaciteit. Bovendien is het zo dat alle huidige en toekomstige gebruikers werkruimte toewijzingsmachtigingen zijn toegewezen. \[[14](#endnote-14)\]

Een werkruimte kan worden toegevoegd aan een Premium-capaciteit met behulp van de **werkruimte** deelvenster leveren van de gebruiker is zowel een beheerder van de werkruimte en machtigingen voor capaciteitstoewijzingen heeft.

![Met behulp van het deelvenster met een werkruimte toewijzen aan een Premium-capaciteit](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Werkruimtebeheerders kunnen een werkruimte van een capaciteit (naar gedeelde capaciteit) verwijderen zonder machtiging voor werkruimtetoewijzingen. De werkruimte voor het verwijderen van werkruimten uit toegewezen capaciteit is het effectief worden verplaatst naar gedeelde capaciteit. Houd er rekening mee dat een werkruimte verwijderen uit een Premium-capaciteit mogelijk negatieve gevolgen leidt, bijvoorbeeld gedeelde inhoud niet meer beschikbaar is voor Power BI Free licentiëren gebruikers of opschorting van geplande vernieuwing wanneer ze langer zijn dan de limiet die wordt ondersteund door gedeelde capaciteit.

In de Power BI-service wordt een werkruimte die is toegewezen aan een Premium-capaciteit eenvoudig geïdentificeerd door de ruitvormig pictogram die adorns naam van de werkruimte.

![Identificeren van een werkruimte die is toegewezen aan een Premium-capaciteit](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Bewaking van capaciteit

Premium-capaciteiten bewaking biedt beheerders met een goed begrip van hoe de capaciteiten uitvoert. Capaciteit kunnen worden bewaakt met behulp van de [metrische gegevens over Power BI Premium capaciteit app](service-admin-premium-monitor-capacity.md) of de [Power BI-beheerportal](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>Metrische gegevens interpreteren

Metrische gegevens moeten worden gecontroleerd voor het maken van een basislijn begrip van de activiteit voor het gebruik en de werkbelasting van resources. Als de capaciteit traag wordt, is het belangrijk om te begrijpen welke metrische gegevens voor het bewaken van en de conclusies die u kunt maken.

In het ideale geval zou query's binnen een tweede responsieve ervaringen bieden aan gebruikers en het inschakelen van hogere querydoorvoer voltooid. Het is doorgaans minder problematisch wanneer achtergrondprocessen - inclusief vernieuwingen - langer duurt om te voltooien.

Trage rapporten kunnen in het algemeen een indicatie van een capaciteit te veel verwarming zijn. Wanneer rapporten niet worden geladen, is dit een indicatie van een te veel hete capaciteit. In beide gevallen kan de hoofdoorzaak worden toe te rekenen aan verschillende factoren, met inbegrip van:

- **Mislukte query's** zeker geven geheugendruk en die een model kan niet worden geladen in het geheugen. Power BI-service probeert te laden van een model voor 30 seconden voordat deze is mislukt.

- **Overmatige query wachttijden** kan worden veroorzaakt door verschillende redenen:
  - De noodzaak van Power BI-service naar het eerste onbeschikbaar maken van modellen en laad vervolgens het model naar-worden opgevraagd (intrekken dat alleen verwijdering tarieven hogere gegevensset niet een indicatie van capaciteit stress die gepaard gaat, zijn tenzij vergezeld gaan van lange query wachttijden die wijzen op geheugenthrashing)
  - Model laden tijden (met name de wachttijd voor het laden van een grote model in het geheugen)
  - Langlopende query 's
  - Te veel LC\DQ verbindingen (meer dan de capaciteitslimieten)
  - Belasting van de CPU
  - Complexe rapportontwerpen met een uitzonderlijk groot aantal visualisaties op een pagina (intrekken dat elk visuele element een query is)
- **Lange duur query** kan erop wijzen dat model modellen zijn niet geoptimaliseerd, met name wanneer meerdere gegevenssets actief in een capaciteit zijn, en slechts één gegevensset wordt geproduceerd lange duur van de query. Dit kan erop wijzen dat de capaciteit is voldoende resources voorzien en dat de gegevensset in de vraag suboptimale of alleen traag is. Langlopende query's kan problematisch zijn, aangezien ze toegang tot resources die vereist zijn andere processen kunnen blokkeren.
- **Lange vernieuwen wachttijden of AI-aanroep wachttijden** wijzen onvoldoende geheugen beschikbaar vanwege een groot aantal actieve modellen geheugen, of dat een lastig vernieuwen wordt geblokkeerd door andere wordt vernieuwd (meer dan parallelle vernieuwen limieten).

Een meer gedetailleerde uitleg van het gebruik van de metrische gegevens die vervolgens wordt beschreven in de [optimaliseren van Premium-capaciteiten](#optimizing-premium-capacities) sectie.

## <a name="optimizing-premium-capacities"></a>Premium-capaciteiten optimaliseren

Wanneer prestatieproblemen van Premium-capaciteit zich voordoen, is een algemene first-aanpak te optimaliseren of af te stemmen oplossingen voor het herstellen van acceptabele responstijden al zijn geïmplementeerd. De vervangende logica is om te voorkomen dat het aanschaffen van extra Premium-capaciteit, tenzij kan worden aangetoond.

Als u meer Premium-capaciteit vereist is, zijn er twee opties die later in deze sectie wordt besproken:

- De Premium-capaciteit opschalen
- Toevoegen van een nieuwe Premium-capaciteit

Ten slotte testen benaderingen en Premium-capaciteitsgrootte, wordt in deze sectie sluiten.

### <a name="general-best-practices"></a>Algemene aanbevolen procedures

Wanneer het streven naar bereiken het beste zijn gebruik en prestaties er enkele aanbevolen procedures die kunnen worden uitgevoerd aan boord als algemene aanbevelingen. Deze omvatten:

- App-werkruimten gebruiken in plaats van persoonlijke werkruimten
- Bedrijfskritiek en Self-Service BI (SSBI) te scheiden in verschillende capaciteiten

  ![Bedrijfskritiek en Self-Service BI scheiden in verschillende capaciteiten](media/whitepaper-premium-deployment/separate-capacities.png)

- Als u delen van inhoud alleen met Power BI Pro-gebruikers, is er mogelijk niet nodig voor het opslaan van de inhoud in een toegewezen capaciteit
- Toegewezen capaciteit gebruiken bij het zoeken naar voor het bereiken van een specifieke vernieuwingstijd, of wanneer bepaalde functies zijn vereist, bijvoorbeeld grote gegevenssets of gepagineerde rapporten

### <a name="addressing-common-questions"></a>Veelgestelde vragen-adressering

Power BI Premium-implementaties te optimaliseren, is een complex onderwerp met betrekking tot een goed begrip van de vereisten van workloads, beschikbare resources en het effectieve gebruik.

Dit onderwerp bevat zeven veelgestelde ondersteuningsvragen, met een beschrijving van mogelijke problemen en uitleg en informatie over het identificeren en op te lossen.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Waarom is de capaciteit traag en wat kan ik doen?

Er zijn veel redenen die aan een trage Premium-capaciteit bijdragen kunnen. Deze vraag vereist meer informatie over wat wordt bedoeld met traag. Zijn rapporten langzaam worden geladen? Of worden ze niet worden geladen? Zijn visuele rapportelementen langzaam geladen of wanneer gebruikers werken interactief met het rapport bijwerken? Vernieuwingen langer duurt dan verwacht of eerder is voltooid?

Ervaring van een goed begrip van de reden hiervoor kunt u vervolgens gaan om te onderzoeken. Antwoorden op de volgende zes vragen helpt u om meer specifieke problemen.

#### <a name="what-content-is-using-up-my-capacity"></a>Welke inhoud wordt mijn capaciteit gebruikt?

U kunt de **metrische gegevens over Power BI Premium capaciteit** app om te filteren op capaciteit en bekijk metrische gegevens voor prestaties voor de inhoud van de werkruimte. Het is mogelijk om te controleren van de prestaties van metrische gegevens en resources gebruik per uur voor de afgelopen zeven dagen voor alle inhoud die zijn opgeslagen in een Premium-capaciteit. Dit is vaak de eerste stap bij het nemen bij het oplossen van een algemeen probleem over de prestaties van de Premium-capaciteit.

Belangrijke metrische gegevens voor het bewaken van zijn onder andere:

- Gemiddelde CPU- en hoog gebruik tellen
- Gemiddeld geheugen en hoog gebruik aantal en het geheugengebruik voor bepaalde gegevenssets, gegevensstromen en gepagineerde rapporten
- Actieve gegevenssets in het geheugen geladen
- Query van gemiddelde en maximale duur
- Gemiddelde query wachttijden
- Gemiddelde gegevensset en gegevensstroom vernieuwen keren
- Gemiddelde AI keer aanroepen en wachttijden

Bovendien bevat actieve geheugen in de Power BI Premium-capaciteit metrische gegevens App de totale hoeveelheid geheugen toegewezen aan een rapport dat kan niet worden verwijderd omdat deze gebruikt in de laatste drie minuten wordt. Een grote piek in vernieuwen wachttijd kan worden gecorreleerd met een grote en/of actieve gegevensset.

De grafiek "5 door de gemiddelde duur boven" markeert de gegevenssets van vijf, gepagineerde rapporten, gegevensstromen en AI-aanroepen capaciteit bronnen verbruikt. De inhoud van de top vijf lijsten zijn kandidaten voor onderzoek en mogelijke optimalisatie.

#### <a name="why-are-reports-slow"></a>Waarom zijn rapporten langzaam?

De volgende tabellen ziet u mogelijke problemen en manieren om te identificeren en deze te verwerken.

##### <a name="insufficient-capacity-resources"></a>Er is onvoldoende capaciteit resources

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Maximale totale actieve geheugen (model kan niet worden verwijderd omdat deze gebruikt in de laatste drie minuten wordt)<br><br> Meerdere hoge pieken in de query wachttijden<br><br> Meerdere hoge pieken in de tijdstippen voor vernieuwing wait | Controleer metrische gegevens voor geheugen \[ [18](#endnote-18)\], en verwijdering tellingen \[ [19](#endnote-19)\] | Model verkleinen, of converteren naar de modus DirectQuery - Zie de [optimaliseren modellen](#optimizing-models) onderwerp in deze sectie<br><br> De capaciteit opschalen<br><br> De inhoud toewijzen aan een andere capaciteit |

##### <a name="inefficient-report-designs"></a>Inefficiënt rapportontwerpen

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Rapportpagina's bevatten een groot aantal visuele elementen (interactieve filteren kunt activeren ten minste één query per visualisatie)<br><br> Visuele elementen ophalen van meer gegevens dan nodig is | Bekijk rapportontwerpen<br><br> Rapportgebruikers gesprek om te begrijpen hoe ze communiceren met de rapporten<br><br> Controleer metrische gegevens voor gegevensset query \[ [20](#endnote-20)\] | Deze rapporten met minder visuele elementen per pagina |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>Gegevensset vertragen (met name wanneer rapporten zijn eerder uitgevoerd ook)

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Steeds grotere hoeveelheden gegevens importeren<br><br> Berekening van complexe of inefficiënte logica, met inbegrip van RLS-rollen<br><br> Model niet volledig geoptimaliseerd<br><br> (DQ/LC) Gateway-latentie<br><br> Trage DQ bron query-reactietijden | Bekijk model ontwerpen<br><br> Gateway-prestatiemeteritems bewaken | Zie de [optimaliseren modellen](#optimizing-models) onderwerp in deze sectie |

##### <a name="high-concurrent-report-usage"></a>Hoge gelijktijdige rapport gebruik

| Mogelijke oorzaken | Identificeren | Over het oplossen van |
| --- | --- | --- |
| Hoge query wachttijden<br><br> Belasting van de CPU<br><br> DQ/LC limieten overschreden | CPU-gebruik bewaken \[ [21](#endnote-21)\], wachttijden query en het gebruik van DQ/LC \[ [22](#endnote-22) \] metrische gegevens + duur van de Query-als wisselt kunt problemen met gelijktijdigheid geven | De capaciteit vergroten, of de inhoud toewijzen aan een andere capaciteit<br><br> Deze rapporten met minder visuele elementen per pagina |

#### <a name="why-are-reports-not-loading"></a>Waarom zijn rapporten niet laden?

Wanneer rapporten niet laden is een slechtste scenario en een of teken dat de capaciteit onvoldoende geheugen heeft en te veel hete is. Dit kan gebeuren wanneer alle geladen modellen actief worden opgevraagd en kunnen niet worden verwijderd en alle bewerkingen voor Gegevensvernieuwing is onderbroken of uitgesteld. Power BI-service probeert te laden van de gegevensset gedurende 30 seconden en de gebruiker wordt zonder problemen op de hoogte gesteld van de fout met een suggestie om te proberen het over enkele ogenblikken opnieuw.

Er is momenteel geen metrische gegevens om te controleren voor rapport laden van fouten. U kunt de mogelijkheden voor dit probleem identificeren door bewaking systeemgeheugen, specifiek hoogste gebruik en de tijd van het hoogste gebruik. Hoge gegevensset databasebestandspagina's en lang gegevensset vernieuwen gemiddelde wachttijd kunnen voorstellen dat dit probleem zich voordoet.

Als dit slechts zelden gebeurt, dit kan niet worden beschouwd als een probleem met de prioriteit. Rapportgebruikers zien een bericht dat de service bezet is en dat ze na een korte periode opnieuw moeten proberen. Als dit te vaak gebeurt, kan het probleem worden opgelost door het omhoog schalen van de Premium-capaciteit of door de inhoud toewijzen aan een andere capaciteit.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **mislukte query's** metrische gegevens om te bepalen wanneer dit gebeurt. Ze kunnen ook de capaciteit, opnieuw instellen van alle bewerkingen in het geval van systeem overbelasting opnieuw worden gestart.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Waarom zijn wordt vernieuwd niet volgens planning gestart?

Begintijden van geplande vernieuwing niet worden gegarandeerd. Intrekken dat Power BI-service wordt altijd prioriteit gegeven aan interactieve bewerkingen via bewerkingen op de achtergrond. Vernieuwen is een achtergrondbewerking die optreden kan wanneer twee voorwaarden wordt voldaan:

- Er is onvoldoende geheugen
- Het aantal ondersteunde gelijktijdige wordt vernieuwd voor de Premium-capaciteit is niet overschreden

Als niet aan de voorwaarden wordt voldaan, het vernieuwen is in de wachtrij geplaatst totdat de voorwaarden gunstig zijn.

Voor een volledige vernieuwing intrekken dat ten minste tweemaal de huidige gegevensset geheugengrootte vereist is. Als er niet voldoende geheugen beschikbaar is, kan niet klikt u vervolgens het vernieuwen beginnen pas model verwijdering vrijgemaakt geheugen wordt: dit betekent vertragingen dat totdat een of meer gegevenssets inactief en kan worden verwijderd.

Het intrekken of het aantal ondersteunde maximum aantal gelijktijdige vernieuwingen is ingesteld op 1,5 keer de back-end-v-cores, naar boven afgerond.

Een geplande vernieuwing mislukt wanneer deze kan niet beginnen voordat de volgende geplande vernieuwing is verschuldigd is om te beginnen. Een vernieuwing op aanvraag handmatig wordt geactiveerd vanuit de gebruikersinterface probeert te maximaal drie keer uitvoeren voordat deze is mislukt.

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **gemiddelde vernieuwen wachttijd (minuten)** metrische gegevens om te bepalen van de gemiddelde vertraging tussen het geplande tijdstip en het begin van de bewerking.

Zorg ervoor dat voldoende geheugen beschikbaar is terwijl meestal niet een administratieve prioriteit, om te beïnvloeden op tijd-gegevens wordt vernieuwd. Dit kan betrekking hebben op gegevenssets kunnen capaciteiten met bekende voldoende resources isoleren. Het is ook mogelijk dat beheerders werkt u met eigenaren van gegevenssets samen kan te spreiden of geplande tijdstippen voor vernieuwing te minimaliseren conflicten verminderen. Houd er rekening mee dat het is niet mogelijk voor een beheerder om de wachtrij vernieuwen weer te geven of om op te halen van de gegevensset-schema's.

#### <a name="why-are-refreshes-slow"></a>Waarom zijn traag wordt vernieuwd?

Vernieuwen is traag- of waargenomen langzaam zijn (als de vorige algemene vraag-adressen).

Wanneer het vernieuwen in feite traag is, kan het zijn verschillende oorzaken hebben:

- Onvoldoende CPU (vernieuwen kan erg CPU-intensief zijn)
- Er is onvoldoende geheugen, wat resulteert in vernieuwen onderbreken (hiervoor is het vernieuwen te beginnen als voorwaarden gunstig zijn voor hervat)
- Niet-capaciteit redenen, waaronder data source systeem reactiesnelheid, netwerklatentie, ongeldige machtigingen of gateway-doorvoer
- Gegevensvolume - een goede reden het configureren van incrementeel vernieuwen, zoals hieronder wordt beschreven

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **gemiddelde vernieuwen duur (minuten)** metrische gegevens om te bepalen van een benchmark voor vergelijking na verloop van tijd en de **gemiddelde vernieuwen wachttijd (minuten)** metrische gegevens om te bepalen van de gemiddelde vertraging tussen de gemiddelde vertraging tussen het geplande tijdstip en het begin van de bewerking.

Incrementeel vernieuwen kunt gegevens vernieuwen duur, met name voor grote modellen tabellen aanzienlijk verkorten. Er zijn vier voordelen die zijn gekoppeld aan incrementeel vernieuwen:

- **Vernieuwingen zijn sneller** : Alleen een subset van een tabel moet laden, te reduceren CPU- en geheugengebruik en parallelle uitvoering kan hoger zijn bij het vernieuwen van meerdere partities
- **Gegevens alleen in indien nodig bijgewerkt** : Beleidsregels voor incrementeel vernieuwen kunnen worden geconfigureerd voor het laden van alleen wanneer gegevens zijn gewijzigd
- **Vernieuwingen zijn betrouwbaarder** : Kortere actieve verbindingen met vluchtige gegevensbronsystemen zijn minder vatbaar voor verbreken
- **Modellen blijven Knippen** : Beleidsregels voor incrementeel vernieuwen kunnen worden geconfigureerd voor de geschiedenis van meer dan een sliding window van tijd automatisch verwijderd

Voor meer informatie raadpleegt u de [incrementeel vernieuwen in Power BI Premium](service-premium-incremental-refresh.md) document.

#### <a name="why-are-data-refreshes-not-completing"></a>Waarom zijn gegevens vernieuwen niet voltooien?

Wanneer het vernieuwen van gegevens wordt gemaakt, maar kan niet worden voltooid, kan het zijn verschillende oorzaken hebben:

- Er is onvoldoende geheugen, zelfs als er slechts één model in de Premium-capaciteit, dat wil zeggen het model zeer groot is
- Redenen voor niet-capaciteit, met inbegrip van gegevens van bron systeem verbreken, ongeldige machtigingen of gatewayfout

Capaciteit beheerders (en Power BI-servicebeheerders) kunt bewaken de **vernieuwen, mislukte aanmeldingen vanwege onvoldoende geheugen** metrische gegevens.

#### <a name="why-are-ai-calls-failing"></a>Waarom zijn AI-oproepen mislukt?

AI-aanroepen kunnen om verschillende redenen mislukken. Het minimale geheugen vereist om te beginnen de AI werkbelasting is 5 GB, maar dit mogelijk niet voldoende is voor sommige invoergegevenssets. Bijvoorbeeld, vereist geautomatiseerde machine learning-modeltraining ten minste twee keer, en soms ook meerdere keren de grootte van de invoergegevensset. Een AI-aanroep is ook beëindigd als het duurt langer dan twee uur om te voltooien. Voor geautomatiseerde machine wordt learning-model training aanroepen die niet worden voltooid in twee uur, het beste model gevonden in deze twee uur geretourneerd.  AI-aanroepen kunnen ook worden onderbroken door interactieve aanvragen, welke voorrang.

Beheerders moeten AI wachttijden voor het tekenen van andere aanvragen prioriteit te controleren. Beheerders kunnen er ook voor zorgen dat voldoende geheugen beschikbaar voor de AI-werkbelasting ten opzichte van invoergegevens grootten is. Dit kan betrekking hebben op AI-workloads naar de capaciteiten die bekend is dat voldoende bronnen isoleren. Het is ook mogelijk dat beheerders met eigenaren van de gegevensstroom coördineren kan te spreiden of vernieuwingstijden gegevensstroom te minimaliseren, conflicten te verminderen. Opmerking: het is niet mogelijk voor een beheerder om de wachtrij van de aanroep van AI weer te geven.

### <a name="optimizing-models"></a>Modellen te optimaliseren

Optimale modelontwerp is essentieel om te kunnen leveren van een efficiënte en schaalbare oplossing. Het is echter buiten het bereik van dit technisch document voor een volledige bespreking van. In plaats daarvan biedt deze sectie belangrijke gebieden ter overweging bij het optimaliseren van modellen.

#### <a name="optimizing-power-bi-hosted-models"></a>Power BI-Hosted modellen te optimaliseren

Optimaliseren modellen die worden gehost in een Premium-capaciteit kunnen op de gegevens bron(nen) die en het model voor lagen worden behaald.

Houd rekening met de optimalisatiemogelijkheden voor een model importeren:

![Optimalisatiemogelijkheden voor een model importeren](media/whitepaper-premium-deployment/import-model-optimizations.png)

Op de bronlaag van gegevens:

- Relationele gegevensbronnen worden geoptimaliseerd om te controleren of het vernieuwen van de snelst mogelijke door vooraf geïntegreerde gegevens, het toepassen van de juiste indexen, Tabelpartities die zijn afgestemd voor incrementeel vernieuwen perioden te definiëren en materialiseren berekeningen (in plaats van berekend model voor tabellen en kolommen) of berekening logica toevoegen aan weergaven
- Niet-relationele gegevensbronnen kunnen vooraf worden geïntegreerd met relationele winkels
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbronnen zijn

Op het niveau van het model:

- Power Query-queryontwerpen kunnen minimaliseren of verwijderen van complexe transformaties en met name toepassingen die samenvoegen van verschillende gegevensbronnen (datawarehouses hiervoor tijdens de fase Extract-Transform-Load). Ervoor te zorgen dat de juiste privacyniveaus van gegevensbronnen zijn ingesteld, kan dit ook voorkomen dat Power BI laden van de volledige resultaten te produceren van een gecombineerde resultaat voor query's.
- De modelstructuur bepaalt welke gegevens worden geladen en heeft een directe invloed op de Modelgrootte. Deze kan worden ontworpen om te voorkomen dat het laden van onnodige gegevens door het verwijderen van kolommen, verwijderen van rijen (met name historische gegevens) of door het laden van samengevatte gegevens (ten koste van het laden van gedetailleerde gegevens). Indrukwekkende formaat beperking kan worden bereikt door het verwijderen van hoge kardinaliteit kolommen (met name tekstkolommen) die niet opslaan of zeer efficiënt comprimeren.
- Prestaties van de model-query's kan worden verbeterd door het configureren van relaties één richting, tenzij er is een goede reden om toe te staan van bidirectionele filters. U kunt ook met de functie CROSSFILTER in plaats van bidirectionele filters.
- Aggregatie van tabellen kunnen maar liefst snel query antwoorden van het laden van vooraf samengevatte gegevens, maar dit de grootte van het model en het resultaat in langer tijdstippen voor vernieuwing vergroot. Over het algemeen moeten aggregatie van tabellen voor zeer grote modellen of ontwerpen die samengestelde model worden gereserveerd.
- Berekende tabellen en kolommen Verhoog de Modelgrootte en leiden tot langere vernieuwingstijden. Over het algemeen kunnen een kleinere opslaggrootte en snellere vernieuwingstijd worden behaald als de gegevens zijn gerealiseerde of berekend in de gegevensbron. Als dit niet mogelijk is, met Power Query aangepaste kolommen verbeterde opslag compressie te kunnen bieden.
- Mogelijk zijn er kans om af te stemmen DAX-expressies voor metingen en RLS-regels, misschien herschrijven logica om te voorkomen dat dure formules
- Incrementeel vernieuwen kunt aanzienlijk minder vernieuwingstijd en besparen geheugen en CPU. Incrementeel vernieuwen kan ook worden geconfigureerd om historische gegevens te verkleinen houden van grootte van het gegevensmodel te verwijderen.
- Een model kan worden aangepast als de twee modellen wanneer er andere, conflicterende querypatronen. Bijvoorbeeld: sommige rapporten aanwezig zijn op hoog niveau statistische functies via alle geschiedenis en kunnen tolereren latentie van 24 uur. Andere rapporten betrokken zijn bij de gegevens van vandaag en gedetailleerde toegang nodig tot afzonderlijke transacties. In plaats van ontwerp één model om te voldoen aan alle rapporten, twee modellen die zijn geoptimaliseerd voor elke vereiste te maken.

Houd rekening met de optimalisatiemogelijkheden voor een model in DirectQuery. Als het model problemen met query-aanvragen naar de onderliggende gegevensbron, is bron-optimalisatie van gegevens essentieel om responsieve model query's leveren.

 ![Optimalisatiemogelijkheden voor een DirectQuery-model](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

Op de bronlaag van gegevens:

- De gegevensbron kan worden geoptimaliseerd om te controleren of de snelste mogelijk uitvoeren van query's door vooraf de integratie van gegevens (dit is niet mogelijk op het niveau van het model), het toepassen van de juiste indexen, Tabelpartities, materialiseren definiëren samengevatte gegevens (met geïndexeerde weergaven), en minimaliseren van het bedrag van de berekening. De beste ervaring wordt bereikt wanneer passthrough-query's moeten alleen filteren en inner joins tussen geïndexeerde tabellen of weergaven uit te voeren.
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbron zijn

Op het niveau van het model:

- Power Query-query ontwerpen gelden bij voorkeur geen transformaties - anders probeert te houden transformaties tot een absoluut minimum
- Prestaties van de model-query's kan worden verbeterd door het configureren van relaties één richting, tenzij er is een goede reden om toe te staan van bidirectionele filters. Bovendien relaties in het gegevensmodel moeten worden geconfigureerd voor wordt ervan uitgegaan dat referentiële integriteit aannemen (als dit het geval is) wordt afgedwongen en resulteert in het data source-query's met efficiënter inner joins (in plaats van outer join).
- Vermijd het maken van aangepaste kolommen van Power Query-query of berekende kolom model - realiseren deze in de gegevensbron, indien mogelijk
- Mogelijk zijn er kans om af te stemmen DAX-expressies voor metingen en RLS-regels, misschien herschrijven logica om te voorkomen dat dure formules

Houd rekening met de optimalisatiemogelijkheden voor een samengestelde model. Intrekken dat een samengestelde model wijze een combinatie van importeren en DirectQuery-tabellen.

![Optimalisatiemogelijkheden voor een samengestelde model](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- De onderwerpen optimalisatie voor importeren en DirectQuery-modellen zijn over het algemeen van toepassing op modeltabellen met samengestelde die gebruikmaken van deze modi opslag.
- Normaal gesproken streven ernaar om een evenwichtige ontwerp realiseren door het configureren van de dimensie-type tabellen (die vertegenwoordigt bedrijfsentiteiten) als Dual-modus en type feit opslagtabellen (vaak grote tabellen, operationele gegevens die) als DirectQuery-opslagmodus. Dual-opslagmodus betekent dat beide importeren en DirectQuery-modi voor opslag, en dit kunt Power BI-service om te bepalen van de meest efficiënte opslagmodus gebruiken bij het genereren van een systeemeigen query voor passthrough.
- Zorg ervoor dat gateways onvoldoende bronnen, bij voorkeur op specifieke virtuele machines, met voldoende netwerkbandbreedte en dicht in de gegevensbronnen zijn
- Aggregaties tabellen geconfigureerd als opslagmodus voor importeren query indrukwekkende prestatieverbeteringen wanneer die wordt gebruikt om samen te vatten DirectQuery-modus type feit opslagtabellen kan leveren. In dit geval aggregatie van tabellen wordt Verhoog de grootte van het model en vernieuwingstijd verhogen en vaak is dit geen bezwaar voor snellere query's.

#### <a name="optimizing-externally-hosted-models"></a>Extern gehoste modellen te optimaliseren

Veel optimalisatiemogelijkheden besproken de [Optimizing Power BI-Hosted modellen](#optimizing-power-bi-hosted-models) onderwerp ook van toepassing op modellen die zijn ontwikkeld door Azure Analysis Services en SQL Server Analysis Services. Schakel uitzonderingen zijn bepaalde functies die worden momenteel niet ondersteund, met inbegrip van samengestelde modellen en aggregatie van tabellen.

Een extra aandacht voor extern gehoste gegevenssets is de database die als host fungeert ten opzichte van de Power BI-service. Voor Azure Analysis Services, betekent dit dat het maken van de Azure-resource in dezelfde regio als de Power BI-tenant (basisregio). Dit betekent dat de virtuele machine in dezelfde regio die als host fungeert voor SQL Server Analysis Services, voor IaaS, en voor on-premises, betekent dit dat ervoor te zorgen dat de installatie van een doeltreffende gateway.

Als een aside kan zijn van belang te weten dat Azure Analysis Services-databases en tabellaire databases van SQL Server Analysis Services is vereist dat hun modellen volledig in het geheugen worden geladen en dat ze blijven er helemaal tijden voor het uitvoeren van query's. Net als Power BI-service moet er voldoende geheugen voor het vernieuwen van als het model online tijdens het vernieuwen blijven moet. In tegenstelling tot de Power BI-service is er geen concept dat modellen automatisch zijn verouderde geheugen op basis van gebruik. Power BI Premium biedt daarom een efficiëntere benadering voor het model uitvoeren van query's met lagere geheugengebruik te maximaliseren.

### <a name="capacity-planning"></a>Capaciteitsplanning

De grootte van een Premium-capaciteit bepaalt de beschikbare geheugen en processorbronnen en beperkingen van de capaciteit. Het aantal Premium-capaciteiten is ook een vergoeding, als het maken van meerdere Premium capaciteit kunnen helpen bij de workloads van elkaar isoleren. Houd er rekening mee dat opslagruimte 100 TB per capaciteitsknooppunt is en dit is waarschijnlijk meer dan voldoende zijn voor elke workload.

Bepalen van de grootte en het aantal Premium-capaciteiten kan lastig zijn, met name voor de initiële capaciteit die u maakt. De eerste stap bij het capaciteitsgrootte is om te begrijpen van de gemiddelde werkbelasting weergeven van het verwachte dagelijkse gebruik. Het is belangrijk om te begrijpen dat niet alle workloads gelijk zijn. Een voorbeeld - is 100 gelijktijdige gebruikers toegang tot één rapportpagina waarin één visueel element aan het ene uiteinde van een spectrum - eenvoudig haalbare. Nog - aan het andere uiteinde van het spectrum - 100 gelijktijdige gebruikers toegang hebben tot 100 verschillende rapporten, elk met 100 visuele elementen op de rapportpagina, maak ik zeer verschillende eisen van de capaciteit van bronnen.

Capaciteitsbeheerders moet daarom rekening houden veel factoren die specifiek zijn voor uw omgeving, de inhoud en het verwachte gebruik. Het overschrijven doel is om te maximaliseren capaciteitsverbruik bij het leveren van consistente tijden acceptabele wachttijden en tarieven voor verwijdering. Factoren ter overweging kunnen opnemen:

- **Grootte en gegevens modelleren** : Import modellen moet volledig geladen in geheugen voor het uitvoeren van query's of vernieuwd. LC/DQ gegevenssets kunnen vereisen dat aanzienlijke processortijd en mogelijk aanzienlijke hoeveelheid geheugen aan het evalueren van complexe metingen of RLS-regels. Geheugen en de grootte van de processor en querydoorvoer LC/DQ worden beperkt door de grootte van de capaciteit.
- **Gelijktijdige active modellen** : Gelijktijdige query's naar verschillende import modellen verzorgt aanbevolen reactiesnelheid en prestaties wanneer ze in het geheugen blijven. Er moet voldoende geheugen voor het hosten van alle sterk opgevraagd modellen, met extra geheugen om toe te staan om hun te vernieuwen.
- **Import-modelvernieuwing** : De vernieuwingstype (volledige of incrementele), de duur en de complexiteit van Power Query-query's en logica van de berekende tabel/kolom kunnen van invloed op geheugen en met name processorgebruik. Gelijktijdige wordt vernieuwd, worden beperkt door de grootte van de capaciteit (1,5 x backend v-cores, naar boven afgerond).
- **Gelijktijdige query's** : Veel gelijktijdige query's kunnen resulteren in rapporten die van niet-reagerende wanneer processor- of LC/DQ verbindingen groter is dan de maximale capaciteit. Dit geldt met name voor rapportpagina's die veel visuele elementen bevatten.
- **Gegevensstromen, gepagineerde rapporten en AI-functies** : De capaciteit kan worden geconfigureerd ter ondersteuning van gegevensstromen, gepagineerde rapporten en AI-functies, met elk een configureerbare maximumpercentage van capaciteit geheugen vereisen. Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar het wordt statisch toegewezen aan gepagineerde rapporten en de AI-werkbelasting.

Naast deze factoren kunt Capaciteitsbeheerders Houd rekening met het maken van meerdere capaciteit. Meerdere capaciteiten staan voor de isolatie van workloads en kunnen worden geconfigureerd om ervoor te zorgen prioriteit workloads hebt resources gegarandeerd. Twee capaciteiten kunnen bijvoorbeeld worden gemaakt om bedrijfskritische werkbelastingen scheiden van workloads van selfservice-BI (SSBI). De essentiële capaciteit kan worden gebruikt voor het isoleren van grote zakelijke modellen met gegarandeerde resources, met het ontwerpen van toegang verleend tot de IT-afdeling. De capaciteit SSBI kan worden gebruikt voor het hosten van een groeiend aantal kleinere-modellen, met toegang tot zakelijke analisten verleend. De capaciteit SSBI kan soms query of vernieuwen wacht die toegestane optreden.

Na verloop van tijd Capaciteitsbeheerders kan worden verdeeld werkruimten capaciteiten door het verplaatsen van inhoud tussen werkruimten of werkruimten tussen capaciteiten en capaciteiten schaal omhoog of omlaag. Over het algemeen als host voor grotere modellen u opschalen en voor hogere gelijktijdigheid u de schaal vergroten.

Let erop dat het aanschaffen van een licentie voor de tenant v-cores biedt. De aanschaf van een **P3** abonnement kan worden gebruikt om het maken van een en maximaal vier Premium-capaciteiten, dat wil zeggen 1 x P3, of 2 x P2, of 4 x P1. Ook, voordat u een capaciteit P2 aan een capaciteit P3 converteren, kunnen worden overwogen de v-cores splitsen twee P1-capaciteit maken.

### <a name="testing-approaches"></a>Benaderingen testen

Zodra een grootte van de capaciteit, wordt besloten kan testen worden uitgevoerd door het maken van een gecontroleerde omgeving. Een praktische en betaalbare optie is het maken een capaciteit van Azure (A-SKU's), geldt dat een capaciteit P1 even groot is als een A4-capaciteit, met de P2 en P3 capaciteiten even groot is als de A5 en A6-capaciteit, respectievelijk. Azure-capaciteiten snel kunnen worden gemaakt en worden op uurbasis in rekening gebracht. Ja, zodra het testen is voltooid, ze kunnen worden eenvoudig verwijderd als u wilt stoppen kosten oplopen.

De test-inhoud kan worden toegevoegd aan de werkruimten die zijn gemaakt op de Azure-capaciteit, en vervolgens als één gebruiker rapporten kunt uitvoeren voor het genereren van een realistische en representatieve workload van query's. Als er import modellen, moet u ook een vernieuwing voor elk model uitgevoerd. Controlehulpprogramma's kan vervolgens worden gebruikt om te controleren van alle metrische gegevens voor meer informatie over Resourcegebruik.

Het is belangrijk dat de tests herhaalbare zijn: Tests moeten worden uitgevoerd op meerdere keren en ze ongeveer hetzelfde resultaat telkens moeten leveren. Een gemiddelde is van deze resultaten kan worden gebruikt om te extrapoleren en een schatting maken van een werkbelasting waar productie voorwaarden wordt voldaan.

Voor het genereren van een stresstest, houd rekening met het ontwikkelen van een belastingstest van toepassing voor het simuleren van een realistische werkbelasting. De details van hoe u om dit te bereiken vallen buiten het bereik van dit technisch document. Raadpleeg voor meer informatie, inclusief een voorbeeld van code, de [Load tests Power BI-toepassingen met Visual Studio-belastingstest](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="exploring-real-world-scenarios"></a>Real-World scenario's verkennen

In deze sectie, worden aantal praktijkscenario's geïntroduceerd om te beschrijven van algemene problemen of uitdagingen, hoe om ze te identificeren en hoe u kunt ze op te lossen:

- [Gegevenssets actueel te houden](#keeping-datasets-up-to-date)
- [Gegevenssets langzaam reageert identificeren](#identifying-slow-responding-datasets)
- [Identificeren van oorzaken voor sporadisch langzaam reageert gegevenssets](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Bepalen of er voldoende geheugen](#determining-whether-there-is-enough-memory)
- [Bepalen of er voldoende CPU](#determining-whether-there-is-enough-cpu)

De stappen, samen met de grafiek en tabel voorbeelden zijn van de **Power BI Premium-capaciteit metrische gegevens App** (app) dat een Power BI-beheerder toegang tot heeft.

### <a name="keeping-datasets-up-to-date"></a>Gegevenssets Up houden tot datum

Een onderzoek is in dit scenario wordt geactiveerd wanneer gebruikers klacht betrekking heeft dat rapportgegevens soms leek te zijn van de oude of 'verlopen'.

In de app, de beheerder de interactie met de **wordt vernieuwd** visueel element sorteren gegevenssets door de **maximale wachttijd** statistieken in aflopende volgorde. Hiermee kunnen ze geven de gegevenssets waarvoor de langste wachttijden, gegroepeerd op de naam van de werkruimte.

![Gegevensset wordt vernieuwd gesorteerd op aflopende maximale wachttijd, gegroepeerd op de werkruimte](media/whitepaper-premium-deployment/dataset-refreshes.png)

Bovendien, in de **per uur gemiddelde vernieuwen wacht tijden** visual, ze zoals u ziet dat de wachttijden vernieuwen consistent ongeveer 4 uur per dag pieken.

![Vernieuwen wacht piek periodiek om 4 uur](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Er zijn verschillende mogelijke oorzaken van deze resultaten:

- Te veel vernieuwingspogingen kunnen plaatsvinden op hetzelfde moment, de limieten die zijn opgelegd door het capaciteitsknooppunt (zes gelijktijdige vernieuwen op een P1 met geheugentoewijzing standaard)

- Gegevenssets worden vernieuwd kan worden te groot voor in het beschikbare geheugen (ten minste 2 x de hoeveelheid geheugen die nodig zijn voor volledig vernieuwen vereist)
- Inefficiënt Power Query-logica kan worden leidt tot een piek van geheugen tijdens het vernieuwen van de gegevensset. Op een bezet capaciteit kunt dit af en toe de fysieke limiet, mislukt het vernieuwen en mogelijk die betrekking hebben op andere bewerkingen voor het weergeven van rapport van de capaciteit is bereikt.
- Vaak opgevraagde gegevenssets die u nodig hebt om te blijven in het geheugen kan invloed hebben op de mogelijkheid van andere gegevenssets wilt vernieuwen, vanwege beperkte beschikbare geheugen

Om te onderzoeken dit, kunt de Power BI-beheerder zoeken naar:

- Weinig geheugen beschikbaar op het moment van vernieuwen van gegevens, wanneer het beschikbare geheugen kleiner dan 2 x de grootte van de gegevensset is worden vernieuwd
- Gegevenssets die zijn niet worden vernieuwd en zijn niet in het geheugen voor vernieuwen, maar die aan de slag om interactieve verkeer tijdens zware vernieuwingstijden weer te geven. Om te zien welke gegevenssets zijn geladen in het geheugen op een bepaald moment een Power BI beheerder kunt kijken naar het gebied van gegevenssets van **gegevenssets** tabblad in de app en cross-filter op een bepaald moment door te klikken op een van de balken in de **per uur Telt het aantal gegevensset geladen**. Een lokale piek (weergegeven in de onderstaande afbeelding) geeft aan dat een uur wanneer meerdere gegevenssets in het geheugen, die het begin van de geplande vernieuwingen mogelijk vertraagd zijn geladen
- Verbeterde gegevensset databasebestandspagina's waarbij plaats wanneer gegevens worden vernieuwd zijn gepland om te starten, waarmee wordt aangegeven er is hoge geheugenbelasting veroorzaakt door te fungeren te veel verschillende interactieve rapporten voorafgaand aan het moment van vernieuwen. De **per uur gegevensset databasebestandspagina's en geheugenverbruik** visual kunt duidelijk pieken in databasebestandspagina's.

De volgende afbeelding ziet u een lokale piek in geladen gegevenssets, wat erop duidt interactieve query's uitvoeren begin van het vernieuwen uitgesteld. Selecteren van een bepaalde periode in de **per uur geladen gegevensset telt** visual wordt kruislings filteren de **omvang van gegevenssets** visual.

![Een lokale piek in geladen gegevenssets voorgesteld interactieve query vertraagd starten van vernieuwen](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

De Power BI-beheerder kunt proberen het probleem oplossen door te nemen stappen om ervoor te zorgen dat voldoende geheugen beschikbaar is voor gegevens worden vernieuwd om op te starten:

- Contact opnemen met de gegevensset vernieuwen eigenaren en waarin ze wordt gevraagd om te spreiden en ruimte gegevens schema 's
- Vermindering van de gegevensset querybelasting door het verwijderen van onnodige dashboards of dashboard-tegels, met name degenen die die beveiliging op rijniveau afdwingen
- Versnellen van de gegevens worden vernieuwd door Power Query logica te optimaliseren, model berekende kolommen of tabellen, het verminderen van de omvang van gegevenssets of het configureren van nemen uit grotere gegevenssets om uit te voeren van incrementele gegevens vernieuwen

### <a name="identifying-slow-responding-datasets"></a>Gegevenssets langzaam reageert identificeren

In dit scenario wordt een onderzoek is geactiveerd wanneer gebruikers klacht betrekking heeft dat bepaalde rapporten duurde het lang om te openen, en soms zou vastloopt.

In de app, de Power BI-beheerder kan gebruiken de **Query duur** visual om te bepalen van de slechtste presterende gegevenssets gegevenssets wordt gesorteerd in aflopende **gemiddelde duur**. Dit visuele element wordt ook weergegeven gegevensset aantal query's, zodat u kunt zien hoe vaak de gegevenssets worden opgevraagd.

![Slechtste presterende gegevenssets te onthullen](media/whitepaper-premium-deployment/worst-performing-datasets.png)

De Power BI-beheerder kan verwijzen naar de **Query Duurdistributie** visual, waarin een algehele verdeling van gerangschikte queryprestaties (< = 30ms, 0-100 MS, enz.) voor de gefilterde periode. In het algemeen, query's één seconde voor toets maken of minder zijn responsieve beschouwd door de meeste gebruikers. query's die langer duren meestal te maken van een perceptie van slechte prestaties.

De **per uur Query Duurdistributie** visual kan de Power BI-beheerder om één uur durende perioden wanneer de capaciteit prestaties kan hebben is waargenomen te identificeren als slecht. Hoe groter de balk segmenten die query vertegenwoordigen duur van meer dan één seconde, hoe groter het risico dat gebruikers slechte prestaties wordt waarneemt.

Het visuele element is interactief en wanneer een segment van de balk is ingeschakeld, de bijbehorende **Query duur** tabelvisualisatie op de pagina van het rapport wordt gefilterd om weer te geven van de gegevenssets die staat voor. Deze kruislings filteren, kunt de Power BI-beheerder om eenvoudig te identificeren die gegevenssets langzaam reageert.

De volgende afbeelding ziet u een visueel element gefilterd op **per uur Query duur distributies**, bundeling voor de slechtste presterende gegevenssets in één uur durende buckets. 

![Gefilterde per uur Query duur distributies visual bevat de nog erger gegevenssets uitvoeren](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Zodra de slecht presterende gegevensset in een specifieke periode van 1 uur wordt geïdentificeerd, wordt de Power BI-beheerder kunt onderzoeken of slechte prestaties wordt veroorzaakt door een overbelaste capaciteit of vanwege een slecht gegevensset of rapport ontworpen. Om dit te bereiken, kunnen verwijzen naar de **uitvoertijden van Query wacht** visual en gegevenssets op gemiddelde Querytijd Aflopend sorteren. Als een groot percentage van query's staan, wordt een hoog belasting voor de gegevensset is waarschijnlijk de oorzaak van de vele query-wacht. Als de gemiddelde query wachttijd is aanzienlijk (> 100 ms), kan het zinvol zijn voor het controleren van de gegevensset en het rapport om te zien als optimalisaties kunnen worden gemaakt. Bijvoorbeeld, wellicht minder visuele elementen op gegeven rapportpagina's of de optimalisatie van een DAX-expressie.

![De visual uitvoertijden van Query wacht helpt om weer te geven van slecht presterende gegevenssets](media/whitepaper-premium-deployment/query-wait-times.png)

Er zijn verschillende mogelijke oorzaken voor de query wacht tijd build van in gegevenssets:

- Een modelontwerp suboptimale, metingexpressies of zelfs rapportontwerp - alle omstandigheden die kan bijdragen aan langlopende query's die een hoge mate van CPU in beslag nemen. Dit zorgt ervoor dat nieuwe query's moet worden gewacht tot threads CPU beschikbaar en een bus wordt vervangen effect (Beschouw verkeer is vastgelopen), die vaak gezien tijdens piek tijdens kantooruren maakt. De **Querywachttijden** pagina worden de belangrijkste bron om te bepalen of gegevenssets wachttijden hoge, gemiddelde query.
- Een groot aantal gelijktijdige capaciteit gebruikers (honderden tot duizenden) hetzelfde rapport of gegevensset verbruikt. Zelfs goed ontworpen gegevenssets kunt onjuist buiten een drempel voor gelijktijdigheid van taken uitvoeren. Dit wordt gewoonlijk aangegeven door een enkele gegevensset van een aanzienlijk hogere waarde voor query dan andere gegevenssets worden weergegeven telt (dat wil zeggen 300 kB query's voor één gegevensset in vergelijking met < 30K-query's voor alle andere gegevenssets). Op een bepaald moment de query moet wachten voor deze gegevensset te spreiden, en deze is zichtbaar de **Query duur** visual.
- Veel verschillende gegevenssets gelijktijdig, opgevraagd geheugenthrashing veroorzaakt, zoals gegevenssets cyclus vaak in en uit het geheugen. Dit resulteert in gebruikers met trage prestaties wanneer de gegevensset in het geheugen wordt geladen. U kunt dit controleren de Power BI-beheerder kan verwijzen naar de **per uur gegevensset databasebestandspagina's en geheugenverbruik** visual, die kan duiden dat een groot aantal gegevenssets in het geheugen geladen zijn herhaaldelijk verwijderd.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificeren van oorzaken voor sporadisch langzaam reageert gegevenssets

In dit scenario is een onderzoek wanneer gebruikers beschreven dat rapport visuals soms voelde vertragen om te reageren of kan niet meer reageren, maar op andere momenten ze acceptabel responsieve konden geactiveerd.

In de app de **Query duur** sectie is gebruikt voor het vinden van de gegevensset overmatig in de volgende manier:

- In de **Query duur** visual admin gefilterde gegevensset met de gegevensset (vanaf de bovenste gegevenssets opgevraagd) en onderzoeken het kruislings gefilterd balken in de **per uur Query distributies** visual.
- Als een enkel één uur durende balk gebleken dat met belangrijke wijzigingen in de verhouding tussen de duur van alle querygroepen vergeleken met andere staven één uur voor deze gegevensset (dat wil zeggen de verhouding tussen de kleuren wijzigt drastisch), betekent dit dat deze gegevensset aangetoond sporadisch gewijzigd prestaties.
- Een TimeSpan-waarde waar deze gegevensset is beïnvloed door een effect ruis, veroorzaakt door de andere gegevenssets activiteiten heeft aangegeven dat de één uur durende balken met een onregelmatige gedeelte van slecht presterende query's.

De afbeelding hieronder toont één uur op 30 januari waar een aanzienlijke tegenslag in de prestaties van een gegevensset is opgetreden, aangegeven door de grootte van de '(3,10s] "uitvoering duurbucket. Alle gegevenssets in het geheugen geladen gedurende die tijd is dus zichtbaar te maken van de kandidaat overmatig gegevenssets veroorzaakt door het effect van de ruis te klikken op die één uur voor de balk worden weergegeven.

![Met slechtste prestaties door een groot deel van de balk](media/whitepaper-premium-deployment/worst-performing-queries.png)

Zodra een problematische timespan wordt geïdentificeerd (dat wil zeggen tijdens 30 januari in de bovenstaande afbeelding) kan de Power BI-beheerder verwijdert alle filters uit gegevensset vervolgens filteren alleen op dat timespan om te bepalen welke gegevenssets actief tijdens deze periode zijn opgevraagd. De gegevensset overmatig voor het effect van de ruis is meestal de belangrijkste aangevraagde gegevensset of één met de langste gemiddelde queryduur.

Een oplossing voor dit probleem kan worden voor het distribueren van het overmatig gegevenssets via verschillende werkruimten in verschillende Premium-capaciteiten, of in gedeelde capaciteit als de grootte van de gegevensset, verbruik vereisten en gegevens vernieuwen patronen worden ondersteund.

Omgekeerd kan ook waar zijn. De Power BI-beheerder kan identificeren tijden wanneer de prestaties van een gegevensset-query's aanzienlijk worden verbeterd en kijk wat is verdwenen. Als bepaalde informatie ontbreekt, wordt deze op dat moment mogelijk om te verwijzen naar het probleem waardoor die helpen.

### <a name="determining-whether-there-is-enough-memory"></a>Bepalen of er is onvoldoende geheugen

Om te bepalen of er onvoldoende geheugen om de capaciteit is voor het voltooien van de werkbelasting, de Power BI-beheerder kan verwijzen naar de **verbruikte geheugen Percentages** visual in de **gegevenssets** tabblad van de app. **Alle** (totaal) geheugen vertegenwoordigt de hoeveelheid geheugen die worden gebruikt door de gegevenssets die worden geladen in het geheugen, ongeacht of ze actief wordt opgevraagd of verwerkt. **Actieve** geheugen vertegenwoordigt de hoeveelheid geheugen die worden gebruikt door de gegevenssets die actief worden verwerkt.

In een gezonde capaciteit het visuele element ziet er als u deze, met een kloof tussen alle (totaal) en actieve geheugen:

![Een gezonde capaciteit ziet u een kloof tussen alle (totaal) en actieve geheugen](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

In een capaciteit geheugendruk voordoet, wordt dezelfde visual duidelijk weergegeven actieve geheugen en het totale geheugen geconvergeerd, wat betekent dat het is niet mogelijk extra gegevenssets in het geheugen laden op dat punt in tijd. In dit geval de Power BI-beheerder kunt klikken op **capaciteit opnieuw** (in **geavanceerde opties** van het gebied van de instellingen voor capaciteit van de beheerportal). Opnieuw opstarten van de resultaten van de capaciteit in alle gegevenssets wordt leeggemaakt uit het geheugen en zodat ze opnieuw te laden in het geheugen zoals vereist (door query's of gegevens vernieuwen).

![** Actieve ** geheugen convergeert met ** alle ** geheugen](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Bepalen of er is onvoldoende CPU

In het algemeen is moet de gemiddelde CPU-gebruik van een capaciteit blijven dan 80%. Meer dan deze waarde betekent dat de capaciteit bijna is bereikt voor belasting van de CPU.

Gevolgen van de belasting van de CPU worden door bewerkingen duurt langer dan ze vanwege de capaciteit die veel CPU-context switches uitvoeren zoals het probeert te verwerken van alle bewerkingen moeten uitgedrukt. In een Premium-capaciteit met een groot aantal gelijktijdige query's, die dit wordt aangegeven door de hoge query wachttijden. Een gevolg van wachttijden hoge query is trager reactiesnelheid dan normaal. De beheerder van de Power BI eenvoudig kunt herkennen wanneer de CPU is verzadigd hand de **per uur Query wacht tijd distributies** visual. Periodieke pieken van query wachttijd aantallen duiden op potentiële belasting van de CPU.

![Periodieke pieken van query wachttijd aantallen duiden op potentiële belasting van de CPU](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Een vergelijkbaar patroon kan soms worden gedetecteerd in bewerkingen op de achtergrond als de taalkenmerken aan de belasting van de CPU bijdragen. Een Power BI-beheerder kunt zoeken naar een periodieke piek in de tijdstippen voor vernieuwing voor een specifieke gegevensset, wat op belasting van de CPU op het moment (waarschijnlijk vanwege andere lopende gegevensset wordt vernieuwd en/of interactieve query's duiden kan). In dit geval verwijzen naar de **System** weergeven in de app kan niet per se blijkt dat de CPU 100% is. De **System** weergave worden weergegeven per uur gemiddelden, maar de CPU kan worden verzadigd voor enkele minuten van zware bewerkingen, die wordt weergegeven als pieken in de wachttijd.

Er zijn meer aspecten om te zien van het effect van de belasting van de CPU. Terwijl het aantal query's die wachten belangrijk is, de wachttijd query altijd gebeurt tot op zekere hoogte zonder aanmerkelijke prestatievermindering. Sommige gegevenssets (met een langere gemiddelde querytijd, complexiteit of grootte) zijn meer gevoelig zijn voor de gevolgen van de belasting van de CPU dan andere. Als u wilt deze gegevenssets eenvoudig kunt identificeren, de Power BI-beheerder kunt zoeken naar wijzigingen in de samenstelling van de kleur van de balken in de **per uur wachten verdeling** visual. Na een balk uitschieter ontdekken, kunnen ze zoeken naar de gegevenssets waarvoor query wacht gedurende die tijd en Bekijk ook de gemiddelde query wachttijd vergeleken met het gemiddelde queryduur van de. Wanneer deze twee metrische gegevens van dezelfde grootte zijn en de werkbelasting query voor de gegevensset essentieel is, is het waarschijnlijk dat de gegevensset wordt beïnvloed door onvoldoende CPU.

Dit effect is duidelijk is met name wanneer een gegevensset wordt gebruikt in korte pieken van high-frequency query's door meerdere gebruikers (dat wil zeggen in een trainingssessie), wat resulteert in de belasting van de CPU tijdens elke burst. In dit geval kunnen wachttijden belangrijke query voor deze gegevensset worden ervaren en dat dit gevolgen heeft voor andere gegevenssets in de capaciteit (ruis werkt).

In sommige gevallen kan Power BI-beheerders kunnen aanvragen dat eigenaren van gegevenssets maken met een kleiner vluchtige queryworkload door het maken van een dashboard (query's die u regelmatig met een gegevensset vernieuwen voor tegels in de cache) in plaats van een rapport. Dit kan helpen pieken voorkomen wanneer het dashboard wordt geladen. Deze oplossing niet altijd mogelijk voor bepaalde zakelijke vereisten, maar een effectieve manier om te voorkomen dat de belasting van de CPU, zonder te wijzigen in de gegevensset.

## <a name="conclusion"></a>Conclusie

Power BI Premium biedt consistente prestaties, ondersteuning voor grote hoeveelheden gegevens en de flexibiliteit van een uniforme self-service en enterprise BI platform voor iedereen in uw organisatie. In dit technisch document met niveau 300 is specifiek voor Power BI-beheerders en auteurs van inhoud en uitgevers geschreven. Het is erop gericht om te begrijpen van de mogelijkheden van Power BI Premium, en waarin wordt uitgelegd hoe u kunt ontwerpen, implementeren, bewaken en problemen oplossen schaalbare oplossingen.

Als u wilt implementeren en beheren van Power BI Premium-capaciteiten, beheerders en ontwikkelaars van model moet een zeer goed begrip van hoe u capaciteiten functie, hoe ze kunnen worden beheerd en bewaakt en hoe modellen kunnen worden geoptimaliseerd, om te reageren op de juiste wijze prestatieproblemen en knelpunten moeten deze zich voordoen.

## <a name="end-notes"></a>Opmerkingen bij de einde

<a name="endnote-01"></a>\[1\] dit technische document zich bezighoudt met Power BI Premium die alleen wordt ondersteund door de Power BI-cloudservice en zodat Power BI Report Server niet binnen het bereik, is met uitzondering van status die de licentie vereist voor het installeren van Power BI Report Server is opgenomen in sommige Power BI Premium-SKU's.

<a name="endnote-02"></a>\[2\] power BI als een service in de cloud als gebruikt voor het insluiten van inhoud namens gebruikers van de toepassing is een Platform-as-a-Service (PaaS). Dit type insluiting sluit kan worden bereikt met de andere twee producten, waarbij een van de Power BI Premium is.

<a name="endnote-03"></a>\[3\] pushen, streaming en hybride gegevenssets worden niet opgeslagen in de Premium-capaciteiten, en zijn daarom niet een overweging bij het implementeren, beheren en controleren van Premium-capaciteiten.

<a name="endnote-04"></a>\[4\] Excel-werkmappen als Power BI content-type worden niet opgeslagen in de Premium-capaciteiten en zijn daarom niet overweging bij het implementeren, beheren of Premium-capaciteiten bewaking.

<a name="endnote-05"></a>\[5\] visuele elementen kunnen worden geconfigureerd voor het negeren van slicerinteracties. Voor meer informatie raadpleegt u de [visualisatie-interacties in een Power BI-rapport](service-reports-visual-interactions.md) document.

<a name="endnote-06"></a>\[6\] het verschil in grootte kan worden bepaald door het vergelijken van de grootte van het Power BI Desktop met Taakbeheer geheugen gebruiken voor het bestand.

<a name="endnote-07"></a>\[7\] deel uit van ondersteuning voor gegevensbronnen van Microsoft SQL Server, Azure Data Bricks, Azure HDInsight Spark (bèta), Azure SQL Database en Azure SQL Data Warehouse. Voor informatie over aanvullende bronnen, raadpleegt u de [gegevensbronnen ondersteund door Directquery in Power BI](desktop-directquery-data-sources.md) document.

<a name="endnote-08"></a>\[8\] power BI Premium biedt ondersteuning voor uploaden van een bestand met Power BI Desktop (.pbix) tot een maximum van 10 GB groot. Na het uploaden, kan een gegevensset tot 12 GB groot als gevolg van vernieuwen groeien. Maximale grootte voor uploaden varieert per SKU. Voor meer informatie raadpleegt u de [Power BI Premium-ondersteuning voor grotere gegevenssets](service-premium-large-datasets.md) document.

<a name="endnote-09"></a>\[9\] SKU's met minder dan vier v-cores niet uitgevoerd op toegewezen infrastructuur. Dit omvat de EM1, EM2, A1 en A2-SKU's.

<a name="endnote-10"></a>\[10\] Hoewel zeldzaam, modellen kunnen worden verwijderd uit het geheugen vanwege servicebewerkingen.

<a name="endnote-11"></a>\[11\] deze tijdsinstellingen zijn onderhevig aan wijzigingen op elk gewenst moment.

<a name="endnote-12"></a>\[12\] dit wordt aangeduid als meerdere geografische gebieden, momenteel in preview. De logica voor een implementatie van meerdere geografische gebieden wordt doorgaans gebruikt voor zakelijke of naleving van de overheid, in plaats van prestaties en schaalbaarheid. Rapport en dashboard laden omvat het nog steeds aanvragen voor de basisregio van voor metagegevens. Voor meer informatie raadpleegt u de [ondersteuning voor meerdere geografische gebieden voor Power BI Premium (Preview)](service-admin-premium-multi-geo.md) document.

<a name="endnote-13"></a>\[13\] is het mogelijk dat gebruikers prestatieproblemen veroorzaken kunnen door overbelasting van de Power BI-service met taken, zeer complexe query's schrijven, het maken van kringverwijzingen, enzovoort.

<a name="endnote-14"></a>\[14\] de optie voor het toewijzen van de hele organisatie werkruimten wordt niet aanbevolen, en een meer gerichte aanpak heeft de voorkeur. Het is in het algemeen niet aanbevolen persoonlijke werkruimten gebruiken voor productie-inhoud.

<a name="endnote-15"></a>\[15\] is het mogelijk voor het bewaken van A-SKU's in de app of in Azure portal, maar niet in de Power BI-beheerportal. Voor het controleren van A-SKU's, mislukt het vernieuwen van het rapport als de app is niet toegevoegd aan de rol van lezer van de resource. Voor meer informatie raadpleegt u de [Monitor Power BI Premium en Power BI Embedded-capaciteit](service-admin-premium-monitor-capacity.md) document.

<a name="endnote-16"></a>\[16\] vernieuwingen aanvragen kunnen wachten wanneer er onvoldoende CPU of geheugen te starten.

<a name="endnote-17"></a>\[17\] de grootte van de gegevensset in het geheugen kan niet groter zijn dan de grootte van de schijf met maximaal 20%.

<a name="endnote-18"></a>\[18\] gemiddelde geheugengebruik (GB) en de hoogste geheugengebruik (GB)

<a name="endnote-19"></a>\[19\] gegevensset databasebestandspagina's

<a name="endnote-20"></a>\[20\] gegevensset query's, gegevensset gemiddelde Queryduur (ms), gegevensset wacht aantal en de gegevensset gemiddelde wachttijd (ms)

<a name="endnote-21"></a>\[21\] aantal van hoog CPU-gebruik en CPU-tijd van het hoogste gebruik (afgelopen zeven dagen)

<a name="endnote-22"></a>\[22\] DQ/LC hoog gebruik Count en DQ/LC tijd van het hoogste gebruik (afgelopen zeven dagen)