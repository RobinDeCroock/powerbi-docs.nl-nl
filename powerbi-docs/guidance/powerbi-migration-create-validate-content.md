---
title: Inhoud maken om te migreren naar Power BI
description: Richtlijnen voor het maken en valideren van inhoud bij het migreren naar Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 03a55f2f414ca8af7ca86f51dcafb0258efc88b7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418596"
---
# <a name="create-content-to-migrate-to-power-bi"></a>Inhoud maken om te migreren naar Power BI

In dit artikel wordt **fase 4** beschreven, die betrekking heeft op het maken en valideren van inhoud wanneer u naar Power BI migreert.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. Fase 4 wordt in dit artikel uitgelicht.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De focus van fase 4 is het uitvoeren van het daadwerkelijke werk om het POC (werkbare concept) te converteren naar een oplossing die gereed is voor productie.

De uitvoer van deze fase is een Power BI-oplossing die gevalideerd is in een ontwikkelingswerkruimte en gereed is voor implementatie tot productie.

> [!TIP]
> De meeste onderwerpen die in dit artikel worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject.

## <a name="create-the-production-solution"></a>De productieoplossing maken

Op dit moment kan dezelfde persoon die het POC heeft uitgevoerd, verdergaan met het produceren van de productieklare Power BI-oplossing. Ook kan iemand anders meedoen. Mits tijdlijnen niet in gevaar komen, kan het goed zijn om mensen mee te laten doen die in de toekomst verantwoordelijk zullen zijn voor de ontwikkeling van Power BI. Op deze manier kunnen ze actief bijleren.

> [!IMPORTANT]
> Hergebruik zoveel mogelijk het werk van het POC.

### <a name="develop-new-import-dataset"></a>Ontwikkel een nieuwe gegevensset voor importeren

U kunt ervoor kiezen om een nieuwe gegevensset voor importeren te maken als er nog geen Power BI-gegevensset bestaat die (dusdanig kan worden verbeterd dat hij) aan uw behoeften voldoet.

Idealiter overweegt u vanaf het begin het ontwikkelingswerk voor gegevens en rapporten te ontkoppelen. [Het ontkoppelen van gegevens en rapporten](report-separate-from-model.md) maakt het mogelijk om werk te scheiden en faciliteert machtigingen, waarbij verschillende mensen verantwoordelijk zijn voor gegevensmodellering en rapporten. Hierdoor wordt de aanpak schaalbaarder en wordt het hergebruik van gegevens gestimuleerd.

De essentiële activiteiten die met de ontwikkeling van een gegevensset voor importeren samenhangen, zijn:

- [Gegevens verkrijgen](../connect-data/desktop-quickstart-connect-to-data.md) van een of meer gegevensbronnen (dit kan een Power BI-gegevensstroom zijn).
- Gegevens [vormgeven, combineren en voorbereiden](../connect-data/desktop-shape-and-combine-data.md).
- Het [gegevensmodel](../transform-model/desktop-modeling-view.md) maken, inclusief [gegevenstabellen](../transform-model/desktop-date-tables.md).
- [Modelrelaties](../transform-model/desktop-create-and-manage-relationships.md) maken en verifiëren.
- [Metingen](../transform-model/desktop-measures.md) definiëren.
- Indien nodig [beveiliging op rijniveau](../admin/service-admin-rls.md) instellen.
- Synoniemen configureren en [de Q&A optimaliseren](../natural-language/q-and-a-best-practices.md).
- Rekening houden met schaalbaarheid, prestaties en gelijktijdigheid, wat uw beslissingen over gegevensopslagmodellen kan beïnvloeden, waaronder het gebruik van een [samengesteld model](../transform-model/desktop-composite-models.md) of [aggregaties](../transform-model/desktop-aggregations.md).

> [!TIP]
> Als u verschillende ontwikkelings-/test-/productieomgevingen hebt, overweeg dan om [gegevensbronnen](/power-query/power-query-query-parameters) te parametriseren. Hierdoor wordt de in [fase 5](powerbi-migration-deploy-support-monitor.md) beschreven implementatie een stuk eenvoudiger.

### <a name="develop-new-reports-and-dashboards"></a>Nieuwe rapporten en dashboards ontwikkelen

De essentiële, aan de ontwikkeling van een Power BI-rapport of -dashboard gerelateerde activiteiten zijn:

- Beslissen over het gebruik van een liveverbinding met een bestaand gegevensmodel of een nieuw gegevensmodel maken
- Bij het maken van een nieuw gegevensmodel, beslissen over de [gegevensopslagmodus](../transform-model/desktop-storage-mode.md) voor modeltabellen (Importeren, DirectQuery of Samengesteld).
- Beslissen welke gegevensvisualiseringstool het beste aan de vereisten voldoet: Power BI Desktop, Paginated Report Builder of Excel.
- Beslissen wat de [beste visuals](../consumer/end-user-visual-type.md) zijn om het verhaal te vertellen dat het rapport moet overbrengen of om de vragen te behandelen die het rapport moet beantwoorden.
- Zorgen dat alle visuals duidelijke, beknopte en bedrijfsvriendelijke terminologie hanteren.
- Interactiviteitsvereisten aanpakken.
- [Metingen op rapportniveau](../transform-model/desktop-tutorial-create-measures.md) toevoegen bij het gebruik van een liveverbinding.
- Een [dashboard](../create-reports/service-dashboards.md) in de Power BI-service maken, vooral als gebruikers belangrijke metrische gegevens eenvoudig willen kunnen bewaken.

> [!NOTE]
> Veel van deze beslissingen zullen zijn gemaakt tijdens het vroege planningsstadium of tijdens het technische POC.

## <a name="validate-the-solution"></a>De oplossing valideren

Bij de validatie van een Power BI-oplossing spelen vier belangrijke aspecten een rol:

1. Gegevensnauwkeurigheid
2. Beveiliging
3. Functionaliteit
4. Prestaties

### <a name="validate-data-accuracy"></a>Nauwkeurigheid van gegevens valideren

Tijdens de migratie moet u eenmalig controleren of de gegevens in het nieuwe rapport overeenkomen met wat er in het verouderde rapport staat. Als er een verschil bestaat tussen de twee rapporten, moet u dit verschil kunnen verklaren. Het komt vaker voor dan u denkt dat er een fout in de verouderde oplossing wordt gevonden die in de nieuwe oplossing wordt opgelost.

Omdat gegevens constant worden gevalideerd, moet het nieuwe rapport doorgaans worden vergeleken met het originele bronsysteem. Idealiter vindt deze validatie telkens plaats wanneer u een rapportwijziging publiceert.

### <a name="validate-security"></a>Beveiliging valideren

Bij het valideren van de beveiliging zijn twee aspecten van belang:

- Gegevensmachtigingen
- Toegang tot gegevenssets, rapporten en dashboards

Bij een gegevensset voor importeren worden gegevensmachtigingen toegepast door [beveiliging op rijniveau](../admin/service-admin-rls.md) (RLS) te definiëren. Daarnaast is het mogelijk dat gegevensmachtigingen door het bronsysteem worden afgedwongen wanneer de DirectQuery-opslagmodus wordt gebruikt (eventueel met [eenmalige aanmelding](../connect-data/service-gateway-sso-overview.md)).

De voornaamste manieren om toegang tot Power BI-inhoud te verlenen, zijn:

- [Werkruimterollen](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (voor inhoudseditors- en viewers).
- [Appmachtigingen](../collaborate-share/service-create-distribute-apps.md#publish-your-app) toegepast op een verpakte set werkruimte-inhoud (voor viewers).
- Het [delen](../collaborate-share/service-share-dashboards.md) van een individueel rapport of dashboard (voor viewers).

> [!TIP]
> We raden aan inhoudsauteurs te trainen in het effectief beheren van beveiliging. Daarnaast is het van belang dat er een robuust test-, controle- en bewakingssysteem van kracht is.

### <a name="validate-functionality"></a>Functionaliteit valideren

Nu is het tijd om gegevenssetdetails zoals veldnamen, indelingen, sorteringen en standaard samenvattingsgedrag te controleren. Interactieve rapportkenmerken, zoals [slicers](../visuals/power-bi-visualization-slicers.md), [inzoomen](../consumer/end-user-drill.md), [drillthrough](../create-reports/desktop-drillthrough.md), [expressies](../create-reports/desktop-conditional-format-visual-titles.md), [knoppen](../create-reports/desktop-buttons.md) of [bladwijzers](../create-reports/desktop-bookmarks.md), moeten ook allemaal worden geverifieerd.

Tijdens het ontwikkelingsproces moet de Power BI-oplossing regelmatig op een ontwikkelingswerkruimte in de Power BI-service worden gepubliceerd. Controleer of in de service alle functionaliteit, zoals de rendering van aangepaste visuals, naar behoren werkt. Dit is tevens een goed moment om meer te testen. Test [geplande vernieuwing](../connect-data/refresh-scheduled-refresh.md), [Q&A](../consumer/end-user-q-and-a.md) en hoe rapporten en dashboards er uitzien op een [mobiel apparaat](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Prestaties valideren

De prestaties van de Power BI-oplossing zijn van belang voor de gebruikerservaring. De meeste rapporten moeten visuals in minder dan 10 seconden kunnen laden. Als u rapporten hebt die langer nodig hebben om te laden, bedenk dan wat de oorzaken van die vertragingen zouden kunnen zijn. De prestaties van rapporten moeten niet alleen in Power BI Desktop, maar ook regelmatig in de Power BI-service worden beoordeeld.

Veel prestatieproblemen vloeien voort uit ondermaatse [DAX (Data Analysis eXpressions)](../transform-model/desktop-quickstart-learn-dax-basics.md), slecht gegevenssetontwerp of suboptimaal rapportontwerp (bijvoorbeeld te veel visuals op één pagina willen weergeven). Problemen met de technische omgeving, zoals het netwerk, een overbelaste gegevensgateway of de configuratie van een Premium-capaciteit, kunnen ook tot prestatieproblemen leiden. Zie voor meer informatie de [Optimalisatiegids voor Power BI](power-bi-optimization.md) en [Problemen met rapportprestaties in Power BI oplossen](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>De oplossing documenteren

Er zijn twee soorten documentatie die nuttig zijn voor een Power BI-oplossing:

- Gegevenssetdocumentatie
- Rapportdocumentatie

Documentatie kan worden opgeslagen waar deze het toegankelijkst is voor de doelgroep. Veelvoorkomende opties zijn:

- **Binnen een SharePoint-site:** Er kan een SharePoint-site bestaan voor uw Center of Excellence of een interne Power BI-communitysite.
- **Binnen een app:** URL's kunnen worden geconfigureerd wanneer een Power BI-app wordt gepubliceerd om de gebruiker door te verwijzen naar meer informatie.
- **Binnen individuele Power BI Desktop-bestanden:** Modelelementen, zoals tabellen en kolommen, kunnen een beschrijving definiëren. Deze beschrijvingen verschijnen als knopinfo in het deelvenster **Velden** wanneer rapporten worden geschreven.

> [!TIP]
> Als u een site maakt als hub voor Power BI-gerelateerde documentatie, overweeg dan [het menu Hulp vragen aan te passen](../admin/service-admin-portal.md#publish-get-help-information) binnen de URL-locatie.

### <a name="create-dataset-documentation"></a>Gegevenssetdocumentatie maken

Gegevenssetdocumentatie is gericht op gebruikers die de gegevensset in de toekomst gaan beheren. Het is nuttig om de volgende zaken in deze documentatie op te nemen:

- Ontwerpbeslissingen en waarom ze genomen zijn.
- Wie de gegevenssets bezit, beheert en certificeert.
- Vereisten voor gegevensvernieuwing.
- Aangepaste bedrijfsregels gedefinieerd in gegevenssets.
- Specifieke gegevenssetbeveiliging of vereisten voor gegevensprivacy.
- Toekomstige onderhoudsbehoeften.
- Bekende openstaande problemen of uitgestelde achterstandsitems.

U kunt er ook voor kiezen om een wijzigingenlogboek te maken waarin de belangrijkste wijzigingen van de gegevensset na verloop van tijd worden samengevat.

### <a name="create-report-documentation"></a>Rapportdocumentatie maken

Rapportdocumentatie, die doorgaans wordt gestructureerd als een instructie voor rapportgebruikers, kan gebruikers helpen meer waarde uit uw rapporten en dashboards te halen. Een korte zelfstudievideo werkt meestal goed.

U kunt er ook voor kiezen om aanvullende rapportdocumentatie toe te voegen op een verborgen pagina van uw rapport. Deze documentatie zou kunnen bestaan uit ontwerpbeslissingen en een wijzigingenlogboek.

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel van deze reeks over Power BI-migratie](powerbi-migration-deploy-support-monitor.md) komt u meer te weten over fase 5, die zich bezighoudt met het implementeren, ondersteunen en bewaken van inhoud tijdens de migratie naar Power BI.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).
