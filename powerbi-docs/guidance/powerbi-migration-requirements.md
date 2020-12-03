---
title: Vereisten voor migratie naar Power BI verzamelen
description: Richtlijnen voor het verzamelen en prioriteren van vereisten bij migratie naar Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 2aee1be1d5e221f8feaeae05f8284f0388b4b8af
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418550"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Vereisten voor migratie naar Power BI verzamelen

In dit artikel wordt **fase 1** beschreven; deze fase heeft betrekking op het verzamelen en prioriteren van vereisten bij migratie naar Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. In dit artikel wordt fase 1 uitgelicht.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De nadruk van fase 1 ligt op het verzamelen van gegevens en het plannen van een afzonderlijke oplossing die wordt gemigreerd naar Power BI.

De uitvoer van fase 1 bevat gedetailleerde vereisten waaraan prioriteit is gegeven. In fase 2 en 3 moeten echter aanvullende activiteiten worden uitgevoerd om het inspanningsniveau volledig te kunnen inschatten.

> [!IMPORTANT]
> Fasen 1-5 vertegenwoordigen activiteiten die betrekking hebben op één specifieke oplossing. Er zijn beslissingen en activiteiten op het niveau van de organisatie/tenant die van invloed zijn op het proces op het niveau van de oplossing. Enkele van deze planningsactiviteiten op een hoger niveau worden besproken in het artikel [Overzicht van Power BI-migratie](powerbi-migration-overview.md). Raadpleeg indien van toepassing de beslissingen op organisatieniveau voor efficiëntie en consistentie.

> [!TIP]
> De meeste onderwerpen die in dit artikel worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject.

## <a name="compile-requirements"></a>Vereisten compileren

De inventarisatie van bestaande BI-artefacten die in de [Stappen voorafgaand aan de migratie](powerbi-migration-pre-migration-steps.md) zijn gecompileerd, vormt de input voor de vereisten van de nieuwe oplossing die in Power BI moet worden gemaakt. Het verzamelen van vereisten is nodig om inzicht te krijgen in de huidige status en in welke items gebruikers anders willen hebben wanneer rapporten opnieuw worden ontworpen in Power BI. Gedetailleerde vereisten zijn handig voor de planning van de implementatie van oplossingen in [fase 2](powerbi-migration-planning.md), tijdens het maken van een werkbaar concept in [fase 3](powerbi-migration-proof-of-concept.md) en bij het maken van de oplossing die gereed is voor productie in [fase 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Rapportvereisten verzamelen

Stel uitgebreide, gemakkelijk te raadplegen informatie samen over rapporten, zoals:

- **Doel, doelgroep en verwachte actie:** Identificeer het doel en bedrijfsproces die van toepassing zijn op elk rapport, evenals de doelgroep, analytische werkstroom en verwachte actie die moet worden uitgevoerd door de gebruikers van het rapport.
- **Hoe consumenten het rapport gebruiken:** U zou met gebruikers van rapporten kunnen meekijken om precies te begrijpen wat ze met die rapporten doen. U leert dan misschien dat bepaalde elementen van het rapport in de nieuwe Power BI-versie kunnen worden geëlimineerd of verbeterd. Dit proces omvat extra tijdinvestering, maar is nuttig voor kritieke rapporten of rapporten die vaak worden gebruikt.
- **Eigenaar en onderwerpexpert:** Identificeer de rapporteigenaar en de deskundige(n) die zijn gekoppeld aan het rapport of gegevensdomein. Ze kunnen de eigenaren van het nieuwe Power BI-rapport worden. Neem eventuele specifieke vereisten voor wijzigingsbeheer op (die doorgaans verschillen tussen IT-beheerde en bedrijfsbeheerde oplossingen), evenals welke goedkeuringen vereist zijn wanneer wijzigingen in de toekomst worden aangebracht.
- **Methode voor contentlevering:** Verhelder de verwachtingen van de gebruikers van een rapport voor levering van content. Een rapport kan on-demand zijn, interactief worden uitgevoerd, ingesloten in een aangepaste toepassing of worden geleverd op basis van een e-mailabonnement. Er zijn mogelijk ook vereisten om waarschuwingen te activeren.
- **Interactiviteitsbehoeften:** Bepaal _noodzakelijke_ en _wenselijke_  interactiviteitsbehoeften, zoals filters, inzoomen of uitzoomen.
- **Gegevensbronnen:** Zorg ervoor dat alle gegevensbronnen die door het rapport nodig heeft, zijn gedetecteerd en dat de gegevenslatentiebehoeften (gegevensversheid) zijn begrepen. Bepaal de vereisten voor historische gegevens, trending en gegevensmomentopnamen voor elk rapport, zodat ze kunnen worden afgestemd op de gegevensvereisten. Documentatie over gegevensbronnen kan ook later handig zijn bij het uitvoeren van gegevensvalidatie van een nieuw rapport met de brongegevens.
- **Beveiligingsvereisten:** Verhelder beveiligingsvereisten (zoals toegestane lezers, toegestane editors en eventuele beveiliging op rijniveau), inclusief eventuele uitzonderingen op de normale organisatiebeveiliging. Documenteer alle behoeften op het gebied van gegevensgevoeligheid, gegevensprivacy of juridische en/of nalevingsbehoeften.
- **Berekeningen, KPI's en bedrijfsregels:** Identificeer en documenteer alle berekeningen, KPI's en bedrijfsregels die momenteel in het bestaande rapport zijn gedefinieerd, zodat ze kunnen worden afgestemd op de gegevensvereisten.
- **Bruikbaarheids-, indelings- en cosmetische vereisten:** Bepaal welke specifieke bruikbaarheids-, indelings- en cosmetische behoeften zijn gerelateerd aan gegevensvisualisaties, groepeer- en sorteervereisten en voorwaardelijke zichtbaarheid. Neem alle specifieke overwegingen op die betrekking hebben op de levering op mobiele apparaten.
- **Afdruk- en export vereisten:** Bepaal of er specifieke vereisten zijn voor het afdrukken, exporteren of een pixelperfecte indeling. Deze behoeften zijn van invloed op de keuze van het meest geschikte type rapport (zoals een Power BI-, Excel- of gepagineerd rapport). Houd er rekening mee dat consumenten van rapporten vaak erg zijn gehecht aan de manier waarop ze altijd hebben gewerkt. Wees dus niet bang om hun manier van denken enigszins op de proef te stellen. Praat in termen van _verbeteringen_ in plaats van _wijzigingen_.
- **Risico's of bezorgdheid:** Bepaal of er andere technische of functionele vereisten zijn voor rapporten, of risico's of zaken met betrekking tot de informatie die hierin wordt gepresenteerd.
- **Niet-opgeloste problemen en achterstallige items:** Identificeer toekomstige onderhoud, bekende problemen of uitgestelde vragen om op dit moment toe te voegen aan de takenlijst.

> [!TIP]
> Overweeg het prioriteren van activiteiten door ze te classificeren als _noodzakelijk_ of _wenselijk_. Gebruikers vragen op voorhand vaak om alles wat ze mogelijk nodig denken te hebben, omdat ze denken dat dit hun enige kans is om wensen kenbaar te maken. Zorg er bij het prioriteren in meerdere rondes ook voor dat de takenlijst beschikbaar is voor belanghebbenden. Het helpt bij de communicatie, besluitvorming en het bijhouden van niet afgehandelde verplichtingen.

### <a name="gather-data-requirements"></a>Gegevensvereisten verzamelen

Verzamel gedetailleerde informatie met betrekking tot gegevens, zoals:

- **Bestaande query's:** Bepaal of er bestaande rapportquery's of opgeslagen procedures zijn die kunnen worden gebruikt door een [DirectQuery-model](../connect-data/desktop-use-directquery.md) of een [samengestelde model](../transform-model/desktop-composite-models.md), of die kunnen worden geconverteerd naar een importmodel.
- **Soorten gegevensbronnen:** Maak een overzicht van de benodigde typen gegevensbronnen, inclusief gecentraliseerde gegevensbronnen (zoals een datawarehouse van een onderneming) en niet-standaard gegevensbronnen (zoals platte bestanden of Excel-bestanden die gegevensbronnen van een onderneming uitbreiden voor rapportagedoeleinden). Voor connectiviteit met de [gegevensgateway](../connect-data/service-gateway-onprem.md) is het ook belangrijk te achterhalen waar gegevensbronnen zich bevinden.
- **Gegevensstructuur en opschoningsbehoeften:** Bepaal de gegevensstructuur voor elke vereiste gegevensbron en in welke mate [gegevensopschoningsactiviteiten](../transform-model/desktop-query-overview.md) nodig zijn.
- **Gegevensintegratie:** Beoordeel hoe gegevensintegratie wordt verwerkt wanneer er meerdere gegevensbronnen zijn en hoe [relaties](../transform-model/desktop-create-and-manage-relationships.md) tussen elke modeltabel kunnen worden gedefinieerd. Identificeer specifieke gegevenselementen die nodig zijn om het model te vereenvoudigen en [de grootte te verkleinen](import-modeling-data-reduction.md).
- **Aanvaardbare gegevenslatentie:** Bepaal de gegevenslatentiebehoeften voor elke gegevensbron. Dit is van invloed op beslissingen over welke [gegevensopslagmodus](../transform-model/desktop-storage-mode.md) er moet worden gebruikt. De gegevensvernieuwingsfrequentie voor importmodeltabellen is eveneens belangrijk om te weten.
- **Gegevensvolume en schaalbaarheid:** Evalueer verwachtingen omtrent gegevensvolume, welke meespelen in beslissingen over [ondersteuning voor grote modellen](../admin/service-premium-large-models.md) en het ontwerpen van DirectQuery- of [samengestelde modellen](../transform-model/desktop-composite-models.md). Overwegingen met betrekking tot historische gegevensbehoeften zijn ook essentieel om te weten. Voor grotere gegevenssets is het noodzakelijk om de regels voor [incrementele gegevensvernieuwing](../admin/service-premium-incremental-refresh.md) te bepalen.
- **Berekeningen, KPI's en bedrijfsregels:** Beoordeel de behoeften voor metingen, KPI's en bedrijfsregels. Ze zijn mede bepalend voor waar de logica moet worden toegepast: in de gegevensset of het gegevensintegratieproces.
- **Hoofdgegevens en gegevenscatalogus:** Bepaal of er zaken zijn met betrekking tot de hoofdgegevens die aandacht vereisen. Bepaal of integratie met een bedrijfsgegevenscatalogus in aanmerking komt voor het verbeteren van detecteerbaarheid, de toegang tot definities of het produceren van consistente terminologie die door de organisatie wordt geaccepteerd.
- **Beveiliging en gegevensprivacy:** Bepaal of er specifieke aandachtspunten zijn op het gebied van beveiliging of gegevensprivacy, met inbegrip van [beveiliging op rijniveau](../admin/service-admin-rls.md).
- **Niet-opgeloste problemen en achterstallige items:** Identificeer eventuele bekende problemen, bekende defecten op het gebied van gegevenskwaliteit, toekomstig onderhoud of uitgestelde vragen om op dit moment toe te voegen aan de takenlijst.

> [!IMPORTANT]
> Herbruikbaarheid van gegevens kan worden bereikt met [gedeelde gegevenssets](../connect-data/service-datasets-share.md), die optioneel kunnen worden [gecertificeerd](../collaborate-share/service-endorse-content.md) om betrouwbaarheid aan te geven en detecteerbaarheid te verbeteren. Herbruikbaarheid van gegevensvoorbereiding kan worden bereikt met [gegevensstromen](../transform-model/dataflows/dataflows-introduction-self-service.md), om herhaaldelijke logica in meerdere gegevenssets te reduceren. Gegevensstromen kunnen ook de belasting van bronsystemen aanzienlijk verminderen, omdat de gegevens minder vaak worden opgehaald. Meerdere gegevenssets kunnen vervolgens gegevens importeren uit de gegevensstroom.

## <a name="identify-improvement-opportunities"></a>Mogelijkheden om verbeterpunten te identificeren

In de meeste gevallen vinden er enkele wijzigingen en verbeteringen plaats. Het komt maar zelden voor dat een een-op-een-migratie wordt uitgevoerd zonder enige refactoring of verbetering. Er zijn drie soorten verbeteringen die u kunt overwegen:

- **Consolidatie van rapporten:** Vergelijkbare rapporten kunnen worden samengevoegd met technieken als filters, bladwijzers of persoonlijke instellingen. Het gebruik van minder rapporten, die elk flexibeler zijn, kan de ervaring voor van gebruikers van rapporten aanzienlijk verbeteren. Overweeg het optimaliseren van gegevenssets voor [Q&A (query's in natuurlijke taal)](../natural-language/q-and-a-best-practices.md) om consumenten van rapporten nóg meer flexibiliteit te bieden, zodat ze hun eigen visualisaties kunnen maken.
- **Efficiëntieverbeteringen:** Tijdens het verzamelen van vereisten kunnen vaak verbeteringen worden geïdentificeerd. Bijvoorbeeld wanneer analisten getallen handmatig compileren of een werkstroom kan worden gestroomlijnd. [Power Query](../transform-model/desktop-query-overview.md) kan een grote rol spelen bij het vervangen van handmatige activiteiten die momenteel worden uitgevoerd. Als bedrijfsanalisten regelmatig dezelfde activiteiten uitvoeren om gegevens op te schonen en voor te bereiden, kunnen herhaalbare Power Query-stappen voor gegevensvoorbereiding aanzienlijk veel tijd besparen en fouten verminderen.
- **Centralisatie van gegevensmodel:** Een gezaghebbende en gecertificeerde gegevensset fungeert als de backbone voor beheerde selfservice BI. In dit geval worden de gegevens eenmaal beheerd en hebben analisten de flexibiliteit om deze gegevens te gebruiken en uit te breiden om te voldoen aan de behoeften aan rapportage en analyse.

> [!NOTE]
> Meer informatie over centralisatie van gegevensmodellen vindt u in [Discipline van binnen](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) en [Flexibiliteit aan de rand](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>De complexiteit prioriteren en aanpakken

Op dit moment is er een eerste inventarisatie beschikbaar en deze kan specifieke vereisten bevatten. Tijdens het prioriteren van de eerste set met BI-artefacten die gereed is voor migratie, moet rekening worden gehouden met rapporten en gegevens als geheel en onafhankelijk van elkaar.

Identificeer rapporten met hoge prioriteit; dit kunnen rapporten zijn die:

- Zeer waardevol zijn voor het bedrijf;
- Regelmatig worden uitgevoerd;
- Het management of leidinggevenden nodig hebben;
- Niet bovenmatig complex zijn (om de kans op succes tijdens de eerste migratieherhalingen te vergroten);

Gegevens met hoge prioriteit identificeren; dit kunnen gegevens bevatten die:

- Belangrijke gegevenselementen bevatten;
- Algemene organisatiegegevens zijn die veelvuldig worden gebruikt;
- Kunnen worden gebruikt om een gedeelde gegevensset te maken voor hergebruik door rapporten en veel rapportontwerpers;
- Niet bovenmatig complex zijn (om de kans op succes tijdens de eerste migratieherhalingen te vergroten).

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel in deze reeks over Power BI-migratie](powerbi-migration-planning.md) leest u meer over fase 2; deze heeft betrekking op de planning van de migratie van één Power BI-oplossing.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).