---
title: Een Center of Excellence instellen
description: Ontdek hoe een Center of Excellence Microsoft heeft geholpen om een gestandaardiseerd analyse- en gegevensplatform te maken voor het ontsluiten van inzichten met het juiste operationele model, de betrokkenheid van de belanghebbende en gedeelde en gerichte investeringen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: v-pemyer
ms.openlocfilehash: 477b6a1e29fc05da3004a2dcf8466ef969df4531
ms.sourcegitcommit: f73ea4b9116ad186817ec5cc5d5f487d49cc0cb0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/20/2020
ms.locfileid: "88638607"
---
# <a name="establish-a-center-of-excellence"></a>Een Center of Excellence instellen

Dit artikel is gericht op IT-professionals en IT-beheerders. U leert hoe u een Center of Excellence (COE) voor BI en analyses kunt instellen in uw organisatie en hoe Microsoft het eigen COE heeft ingesteld.

Het is echter een misvatting om te denken dat een COE gewoon een helpdesk is.

Een COE voor BI en analyse bestaat doorgaans uit een team professionals dat verantwoordelijk is voor het opzetten en onderhouden van een BI-platform. Het team is ook verantwoordelijk voor de realisatie van een enkele bron van waarheid en het definiëren van een reeks consistente, bedrijfsbrede metrische gegevens om inzichten te ontsluiten en te versnellen. Alsnog blijft de term COE een ruim begrip. Een COE kan op verschillende manieren worden geïmplementeerd en beheerd, en kan de structuur en het bereik per organisatie variëren. In de kern gaat het altijd om een robuust platform waarmee de juiste gegevens en inzichten op het juiste moment aan de juiste mensen worden geleverd. In het ideale geval draagt het ook bij aan de promotie, training en ondersteuning. Bij Microsoft wordt het beschreven als _[discipline in de kern](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ , en het wordt geleverd als ons BI-platform en een enkele bron van waarheid.

Grotere organisaties hebben mogelijk meerdere COE's waarbij het hoofd-COE wordt _uitgebreid_ met satelliet-COE's, vaak op afdelingsniveau. Een satelliet-COE bestaat vaak uit een groep experts die bekend is met bepaalde taxonomieën en definities en die weet hoe belangrijke gegevens kunnen worden getransformeerd in zinvolle informatie _voor hun afdeling_. Afdelingsanalisten krijgen machtigingen toegekend voor kerngegevens die ze gebruiken in hun eigen rapporten. Ze bouwen oplossingen die zijn gebaseerd op nauwkeurig voorbereide kerndimensies, feiten en bedrijfslogica. In bepaalde gevallen kunnen ze de gegevens uitbreiden met afdelingsspecifieke gegevenssets en bedrijfslogica. Belangrijk is dat satelliet-COE's nooit worden losgekoppeld en nooit geïsoleerd opereren. Bij Microsoft staan satelliet-COE's voor _[flexibiliteit aan de rand](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Om dit uitgebreide scenario te laten slagen, geldt voor elke afdeling het principe van _pay to play_. Met andere woorden, afdelingen moeten financieel investeren in het hoofd-COE. Zodoende wordt voorkomen dat niet iedereen krijgt waar het recht op heeft of dat hun minder prioriteit krijgen.

Ter ondersteuning van dit scenario moet het hoofd-COE worden geschaald om te voldoen aan de gefinancierde behoeften van de afdeling. Zodra er meerdere gegevenssets beschikbaar zijn, komen de schaalvoordelen tot uiting. Bij Microsoft werd het snel duidelijk dat het rendabeler is om centraal te werken en dat er op die manier ook sneller resultaten worden geboekt. Bij elk nieuw onderwerpgebied bleken de schaalvoordelen nog groter en konden we nog beter gebruikmaken van en bijdragen aan het hele platform, waardoor we onze onderliggende gegevenscultuur verder konden versterken.

Een voorbeeld: Ons BI-platform biedt kerndimensies, feiten en bedrijfslogica voor Financiën, Sales en Marketing. Ook worden er honderden Key Performance Indicators (KPI's) gedefinieerd. Nu moet een analist van Microsoft Power Platform een leadershipdashboard voorbereiden. Sommige van de KPI's, zoals inkomsten en pijplijnen, komen rechtstreeks van het BI-platform. Andere zijn echter gebaseerd op gedetailleerdere behoeften van het bedrijf. Er is onder andere behoefte aan een KPI met betrekking tot het gebruik van de specifieke Power BI-functie voor gegevensstromen. De analist produceert daarom een [samengesteld Power BI-model](composite-model-guidance.md) om kerngegevens van het BI-platform te integreren met afdelingsgegevens. Vervolgens wordt er bedrijfslogica toegevoegd om de KPI's van hun afdeling te definiëren. Tot slot ontwerpen ze hun leadershipdashboard op basis van het nieuwe model, dat gebruikmaakt van de bedrijfsbrede COE-bronnen versterkt met lokale kennis en gegevens.

Belangrijk is dat afdelingsanalisten zich door de verdeling van de verantwoordelijkheid tussen de hoofd- en satelliet-COE's kunnen richten op nieuwe gebieden in plaats van het beheer van een gegevensplatform. Het is zelfs mogelijk dat er op bepaalde momenten een wederzijdse voordelig relatie tussen de satelliet-COE's en het hoofd-COE ontstaat. Het is bijvoorbeeld mogelijk dat een satelliet-COE nieuwe metrische gegevens definieert, die gunstig bleken voor de eigen afdeling, die uiteindelijk als metrische kerngegevens door het hele bedrijf worden gebruikt en beschikbaar zijn en worden ondersteund via het hoofd-COE.

## <a name="bi-platform"></a>BI-platform

In uw organisatie wordt het COE mogelijk aangeduid als het BI-team of de BI-groep. De naam is minder belangrijk dan wat er daadwerkelijk gebeurt. Als u geen formeel team hebt, raden we u aan een team samen te stellen met daarin uw belangrijkste BI-experts om uw BI-platform te realiseren.

Bij Microsoft wordt het COE ook wel het BI-platform genoemd. Het platform heeft verschillende groepen belanghebbenden die verschillende afdelingen vertegenwoordigen, zoals Financiën, Sales en Marketing. Het is georganiseerd om [gedeelde capaciteiten](#shared-capabilities) en [speciale leveringen](#dedicated-deliveries) uit te voeren.

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="Diagram met gedeelde capaciteiten en speciale leveringen, die worden beschreven in de volgende sectie.":::

### <a name="shared-capabilities"></a>Gedeelde functionaliteit

Gedeelde capaciteiten zijn vereist om het BI-platform te maken en uit te voeren. Ze ondersteunen alle groepen van belanghebbenden die het platform financieren. Ze omvatten de volgende teams:

- **Platformengineering:** We hebben het BI-platform ontworpen met een technisch uitgangspunt. In wezen bestaat het platform uit een reeks frameworks die ondersteuning biedt voor gegevensopname, de aanvulling van gegevens en de levering van de desbetreffende gegevens in semantische BI-modellen die kunnen worden gebruikt door analisten. De engineers zijn verantwoordelijk voor het technische ontwerp en de implementatie van de kerncapaciteiten van het BI-platform. Ze ontwerpen en implementeren bijvoorbeeld de gegevenspijplijnen.
- **Infrastructuur en hosting:** IT-engineers zijn verantwoordelijk voor het inrichten en beheren van alle Azure-services.
- **Ondersteuning en operations:** Dit team houdt het platform draaiende. De ondersteuning houdt zich bezig met de behoeften van gebruikers, zoals gegevensmachtigingen. Operations houdt het platform draaiende, zodat aan de Service Level Agreements (SLA's) wordt voldaan en vertragingen of fouten worden gecommuniceerd.
- **Releasebeheer:** Technische programmamanagers (PM's) geven wijzigingen vrij. Wijzigingen kunnen variëren van updates voor het platformframework tot wijzigingsaanvragen voor semantische BI-modellen. Zij vormden de laatste verdedigingslinie om ervoor te zorgen dat wijzigingen geen schade aanbrengen.

### <a name="dedicated-deliveries"></a>Speciale leveringen

Voor elke groep belanghebbenden is er een speciaal leveringsteam. Het team bestaat meestal uit een data engineer, een analyse-engineer en een technisch PM, die allemaal worden gefinancierd door hun belanghebbende groep.

## <a name="bi-team-roles"></a>BI-teamrollen

Bij Microsoft wordt het BI-platform geëxploiteerd door schaalbare teams van professionals. Teams worden gevormd door speciale en gedeelde resources. Momenteel hebben we de volgende rollen:

- **Programmabeheerders:** PM's zijn speciale resources. Een PM fungeert als primaire contactpersoon tussen het BI-team en de belanghebbenden. Het is hun taak om zakelijke vereisten voor belanghebbenden om te zetten naar een technische specificatie. En ze beheren de prioriteit van de producten en diensten die de belanghebbenden moeten leveren.
- **Databaseleads:** Een databaselead is een speciale resource die verantwoordelijk is voor de onboarding van nieuwe gegevenssets in het datawarehouse. De onboarding van een gegevensset kan betrekking hebben op het instellen van de overeengekomen dimensies, het toevoegen van bedrijfslogica en aangepaste kenmerken, en standaardnamen en -indelingen.
- **Analyseleads:** Een analyselead is een speciale resource die verantwoordelijk is voor het ontwerpen en ontwikkelen van semantische BI-modellen. Ze streven ernaar een consistente architectuur toe te passen met behulp van een standaardnaamgeving en -indeling. Een belangrijk onderdeel van hun rol vormt het optimaliseren van de prestatie.
- **Operations en infrastructuur:** Een gedeelde resource die verantwoordelijk is voor het beheer van taken en gegevenspijplijnen. Ze zijn ook verantwoordelijk voor het beheren van Azure-abonnementen, Power BI-capaciteiten, virtuele machines en gegevensgateways.
- **Ondersteuning:** Een gedeelde resource die verantwoordelijk is voor het schrijven van documentatie, het organiseren van training, het communiceren van wijzigingen in semantische BI-modellen en het beantwoorden van vragen van gebruikers.

## <a name="governance-and-compliance"></a>Governance en naleving

Voor elke groep van belanghebbenden is er een PM-lead die toezicht op het programma houdt en zich bezighoudt met het bestuur. Het belangrijkste doel is om ervoor te zorgen dat de IT-investeringen bedrijfswaarde genereren en tot minder risico's leiden. Het stuurcomité komt regelmatig bijeen om de voortgang te beoordelen en de belangrijkste initiatieven goed te keuren.

## <a name="grow-your-own-community"></a>Uw eigen community uitbreiden

Zet een community binnen uw organisatie op en breid deze uit met behulp van de volgende activiteiten:

- Regelmatig evenementen voor een 'spreekuur' met het BI-team houden, waarbij tijd met wordt vrijgemaakt zodat mensen vragen kunnen stellen, suggesties kunnen doorgeven, ideeën kunnen delen en zelfs klachten kunnen indienen.
- Een Teams-kanaal opzetten voor ondersteuning en om iedereen aan te moedigen om vragen te stellen en te reageren op geplaatste vragen.
- Informele gebruikersgroepen instellen en promoten en medewerkers aanmoedigen om presentaties te houden of deel te nemen.
- Meer formele trainingsevenementen verzorgen voor specifieke producten en het BI-platform zelf. Overwegen om [Power BI Dashboard in a Day](https://powerbi.microsoft.com/diad/) beschikbaar te stellen, een gratis cursuspakket dat een uitstekende manier biedt om werknemers te laten kennismaken met Power BI.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [BI-oplossingsarchitectuur in het COE](center-of-excellence-business-intelligence-solution-architecture.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

In het [volgende artikel in deze reeks](center-of-excellence-business-intelligence-solution-architecture.md) krijgt u meer informatie over de BI-oplossingsarchitectuur in de COE en de verschillende gebruikte technologieën.

### <a name="professional-services"></a>Professionele services

Gecertificeerde Power BI-partners zijn beschikbaar om uw organisatie te helpen slagen met het instellen van een COE. Ze kunnen u een kosteneffectieve training of een audit van uw gegevens bieden. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).

U kunt ook contact opnemen met ervaren adviespartners. Ze kunnen u helpen bij het [beoordelen](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evalueren](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) of [implementeren](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) van Power BI.
