---
title: Migratie naar Power BI voorbereiden
description: Richtlijnen voor de stappen voorafgaand aan de migratie bij migratie naar Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 01d1e48537b2d373be3897259f8ac6e97886f268
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92680968"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Migratie naar Power BI voorbereiden

In dit artikel worden de acties beschreven die u kunt overwegen voordat u naar Power BI migreert.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. In dit artikel ligt de nadruk op de stappen voorafgaand aan de migratie.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De stappen voorafgaand aan de migratie benadrukken de voorafgaande planning, welke een belangrijke voorbereiding is voordat u de vijf migratiefasen gaat doorlopen. De meeste stappen voorafgaand aan de migratie worden één keer uitgevoerd, maar voor grotere organisaties kunnen bepaalde gedeelten voor elke bedrijfseenheid of elke afdeling worden herhaald.

De uitvoer van de stappen voorafgaand aan de migratie omvat een eerste governancemodel, een eerste globale implementatieplanning, naast een inventarisatie van de rapporten en gegevens die moeten worden gemigreerd. Meer informatie over activiteiten in fase 1, 2 en 3 is nodig om het inspanningsniveau voor het migreren van afzonderlijke oplossingen volledig te kunnen inschatten.

> [!TIP]
> De meeste onderwerpen die in dit artikel worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Kosten-/batenanalyse en evaluatie uitvoeren

Enkele belangrijke overwegingen tijdens de eerste evaluatie zijn het verkrijgen van:

- Duidelijkheid over de bedrijfscasus en BI-strategie om een specifieke toekomstige status te bereiken.
- Duidelijkheid over wat succes betekent en hoe u de voortgang en het succes van het migratie-initiatief meet.
- Resultaten van kostenramingen en ROI-berekening (investeringsrendement).
- Succesvolle resultaten voor diverse productieve Power BI-initiatieven die kleiner zijn in bereik en complexiteitsniveau.

## <a name="identify-stakeholders-and-executive-support"></a>Belanghebbenden en executive ondersteuning identificeren

Enkele overwegingen voor het identificeren van belanghebbenden zijn:

- Zorg voor afstemming met belanghebbenden voor de bedrijfscasus en BI-strategie.
- Neem vertegenwoordigers in de bedrijfseenheden op, zelfs als hun inhoud op een later tijdstip pas voor migratie in aanmerking komt, om inzicht te krijgen in hun motivaties en bezorgdheid.
- Betrek Power BI-deskundigen er in een vroeg stadium bij.
- Maak en volg een communicatieplan met belanghebbenden.

> [!TIP]
> Als u bang bent dat er te veel communicatie plaatsvindt, dan is de mate van communicatie waarschijnlijk precies goed.

## <a name="generate-initial-governance-model"></a>Eerste governancemodel genereren

Er zijn verschillende belangrijke items in een Power BI-implementatie die vroegtijdig moeten worden aangepakt:

- Specifieke doelen voor Power BI-adoptie en waar Power BI past in de algemene BI-strategie van de organisatie.
- Hoe de Power BI-beheerdersrol wordt verwerkt, met name in gedecentraliseerde organisaties.
- Beleidsregels met betrekking op het bereiken van vertrouwde gegevens: het gebruik van gezaghebbende gegevensbronnen, het verhelpen van problemen met gegevenskwaliteit en het gebruik van consistente terminologie en algemene definities.
- Beveiligings- en privacystrategie voor gegevensbronnen, gegevensmodellen, rapporten en levering van inhoud aan interne en externe gebruikers.
- Hoe je kunt voldoen aan de vereisten voor interne en externe naleving, regelgeving en audits.

> [!IMPORTANT]
> Het meest effectieve governancemodel streeft naar een goed evenwicht tussen gebruikersmogelijkheden en het noodzakelijke beheerniveau. Meer informatie vindt u in [Discipline van binnen](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) en [Flexibiliteit aan de rand](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>De eerste implementatie plannen

Bij de eerste implementatieplanning moeten standaarden, beleidsregels en voorkeuren worden gedefinieerd voor de Power BI-implementatie van de organisatie.

Houd er rekening mee dat [fase 2](powerbi-migration-planning.md) verwijst naar implementatieplanning op oplossingsniveau. De activiteiten in fase 2 moeten waar mogelijk de beslissingen op het niveau van de organisatie respecteren.

Enkele belangrijke items in een Power BI-implementatie die vroegtijdig moeten worden aangepakt, zijn:

- Beslissingen over [instellingen voor Power BI-tenant](admin-tenant-settings.md); deze moeten worden gedocumenteerd.
- Beslissingen over [werkruimtebeheer](../collaborate-share/service-new-workspaces.md); deze moeten worden gedocumenteerd.
- Overwegingen en voorkeuren met betrekking tot gegevens en [inhoudsdistributiemethoden](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), zoals apps, werkruimten, delen, abonnementen en het insluiten van inhoud.
- Voorkeuren met betrekking tot [gegevenssetmodi](../connect-data/service-dataset-modes-understand.md), zoals het gebruik van de importmodus, de modus DirectQuery of het combineren van de twee modi in een [samengesteld model](composite-model-guidance.md).
- [Gegevens en toegang beveiligen](../admin/service-admin-power-bi-security.md).
- Werken met [gedeelde gegevenssets](../connect-data/service-datasets-share.md) voor herbruikbaarheid.
- [Gegevenscertificering](../collaborate-share/service-endorsement-overview.md) toepassen om het gebruik van gezaghebbende en betrouwbare gegevens te bevorderen.
- Gebruik van verschillende [rapporttypen](../create-reports/index.yml), inclusief Power BI-rapporten, Excel-rapporten of gepagineerde rapporten voor verschillende toepassingen of bedrijfseenheden.
- Wijzigingsbeheerbenaderingen voor het beheren van gecentraliseerde BI-artefacten en door het bedrijf beheerde BI-artefacten.
- Trainingsplannen voor gebruikers, gegevensmodelbouwers, rapportontwerpers en beheerders.
- Ondersteuning voor auteurs van inhoud door gebruik te maken van [Power BI Desktop-sjablonen](../create-reports/desktop-templates.md), [aangepaste visuals](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) en gedocumenteerde ontwerpstandaarden voor rapporten.
- Procedures en processen voor het beheren van gebruikersvereisten, zoals het aanvragen van nieuwe licenties, het toevoegen van nieuwe gatewaygegevensbronnen, het verkrijgen van machtigingen voor gatewaygegevensbronnen, het aanvragen van nieuwe werkruimten, wijzigingen in werkruimtemachtigingen en andere algemene vereisten die regelmatig worden gedetecteerd.

> [!IMPORTANT]
> Implementatieplanning is een iteratief proces. Implementatiebeslissingen zullen vele keren worden verfijnd en uitgebreid naarmate de ervaring van uw organisatie met Power BI groeit en Power BI zich ontwikkelt. De beslissingen die tijdens dit proces worden genomen, worden tijdens de planning van de implementatie op oplossingsniveau gebruikt. Dit wordt besproken in [fase 2](powerbi-migration-planning.md) van het migratieproces.

## <a name="establish-initial-architecture"></a>Initiële architectuur instellen

Uw [BI-oplossingsarchitectuur](center-of-excellence-business-intelligence-solution-architecture.md) zal zich in de loop van de tijd ontwikkelen en vervolmaken. Power BI-instellingstaken die u onmiddellijk wilt afhandelen, zijn onder andere:

- De Power BI-tenant instellen en integratie met Azure Active Directory.
- [Power BI-beheerders](../admin/service-admin-role.md) definiëren.
- Eerste [gebruikerslicenties](../admin/service-admin-licensing-organization.md) aanschaffen en toewijzen.
- [Power BI-instellingen voor tenant](admin-tenant-settings.md) configureren en controleren.
- [Werkruimterollen](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) instellen en toegang tot Azure Active Directory-beveiligingsgroepen en -gebruikers toewijzen.
- Een eerste [Gegevensgateway](../connect-data/service-gateway-deployment-guidance.md)cluster configureren, met een plan om dit regelmatig bij te werken.
- Een [Premium-capaciteitslicentie](../admin/service-admin-premium-purchase.md) aanschaffen (indien van toepassing).
- [Workloads voor Premium-capaciteit](../admin/service-admin-premium-workloads.md) configureren, met een plan om dit op voortdurende basis te beheren.

## <a name="define-success-criteria-for-migration"></a>Criteria voor het slagen van de migratie definiëren

De eerste taak is om te begrijpen hoe een geslaagde migratie van een afzonderlijke oplossing er uitziet. Vragen die u kunt stellen, zijn:

- **Wat zijn de specifieke motivaties en doelstellingen voor deze migratie?** Zie [Overzicht van Power BI migratie (Migratieredenen overwegen)](powerbi-migration-overview.md#consider-migration-reasons) voor meer informatie. In dit artikel worden de meest voorkomende redenen voor een migratie naar Power BI beschreven. Uw doelstellingen moeten op organisatieniveau worden opgegeven. Afgezien daarvan kan de migratie van één oudere BI-oplossing aanzienlijk profiteren van kostenbesparingen, terwijl de migratie van een andere verouderde BI-oplossing kan zijn gericht op het verkrijgen van voordelen van werkstroomoptimalisatie.
- **Wat zijn de verwachte kosten/baten of het investeringsrendement voor deze migratie?** Een duidelijk inzicht in de verwachtingen met betrekking tot kosten, mogelijkheden, gebruiksgemak of flexibiliteit, is nuttig om succes te meten. Het kan richtlijnen bieden om de besluitvorming tijdens het migratieproces te bevorderen.
- **Welke KPI's (Key Performance Indicators) worden gebruikt om het succes te meten?** De volgende lijst bevat enkele voorbeelden van KPI's:
    - Het aantal rapporten dat wordt gegenereerd vanuit het verouderde BI-platform moet maandelijks afnemen.
    - Het aantal rapporten dat vanuit Power BI wordt gegenereerd moet maandelijks toenemen.
    - Het aantal Power BI-rapportgebruikers moet elk kwartaal toenemen.
    - Het percentage rapporten dat wordt gemigreerd naar productie per doeldatum.
    - Kostenreductie van jaarlijkse licentiekosten.

> [!TIP]
> Het [Power BI-activiteitenlogboek](../admin/service-admin-auditing.md) kan worden gebruikt als bron voor het meten van de KPI-voortgang.

## <a name="prepare-inventory-of-existing-reports"></a>Inventarisatie van bestaande rapporten voorbereiden

Het voorbereiden van de inventarisatie van bestaande rapporten in het oudere BI-platform is een belangrijke stap richting inzicht in wat er al bestaat. Het resultaat van deze stap is input voor de beoordeling van het migratieniveau. Activiteiten met betrekking tot het voorbereiden van een inventaris kunnen zijn:

1. **Inventarisatie van rapporten:** Stel een lijst op van rapporten en dashboards die mogelijk gemigreerd kunnen worden.
2. **Inventarisatie van gegevensbronnen:** Stel een lijst op van alle gegevensbronnen die door bestaande rapporten worden gebruikt. Deze moet zowel gegevensbronnen van de onderneming als afdelings- en persoonlijke gegevensbronnen bevatten. Dit proces kan gegevensbronnen aan het licht brengen die eerder niet bekend waren bij de IT-afdeling, vaak aangeduid als _schaduw-IT_ .
3. **Auditlogboek:** Haal gegevens op uit het auditlogboek van het verouderde BI-platform om inzicht te krijgen in gebruikspatronen en om te helpen prioriteiten te stellen. Belangrijke informatie om op te halen uit het auditlogboek omvat:
    - Gemiddeld aantal keer dat elk rapport per week/maand/kwartaal wordt uitgevoerd.
    - Gemiddeld aantal consumenten per rapport per week/maand/kwartaal.
    - De consumenten van elk rapport, met name rapporten die door leidinggevenden worden gebruikt.
    - De meest recente datum waarop elk rapport is uitgevoerd.

> [!NOTE]
> In veel gevallen wordt de inhoud niet exact op dezelfde manier naar Power BI gemigreerd. De migratie is ook een gelegenheid om de gegevensarchitectuur opnieuw te ontwerpen en/of de rapportlevering te verbeteren. Het compileren van een inventarisatie van rapporten is van cruciaal belang om inzicht te krijgen in wat er momenteel bestaat, zodat u kunt bepalen welke refactoring moet worden toegepast. In de overige artikelen in deze reeks worden mogelijke verbeteringen uitvoeriger beschreven.

## <a name="explore-automation-options"></a>Automatiseringsopties verkennen

Het is niet mogelijk een Power BI-conversieproces van het begin tot het einde te automatiseren.

Het compileren van de inventarisatie van bestaande gegevens en rapporten is een mogelijke kandidaat voor automatisering wanneer u een bestaand hulpprogramma hebt dat dit voor u kan doen. De mate waarin automatisering voor sommige delen van het migratieproces kan worden gebruikt, zoals het compileren van de bestaande inventarisatie, is zeer afhankelijk van de hulpprogramma's die u hebt.

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel van deze reeks over Power BI-migratie](powerbi-migration-requirements.md) komt u meer te weten over fase 1, waarin vereisten worden verzameld en geprioriteerd tijdens de migratie naar Power BI.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).
