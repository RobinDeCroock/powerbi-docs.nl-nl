---
title: Implementeren in Power BI
description: Richtlijnen voor het implementeren, ondersteunen en bewaken van inhoud bij het migreren naar Power BI.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: bfa3ffad111c7ab819ed1269586a7b32ccf43bba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419263"
---
# <a name="deploy-to-power-bi"></a>Implementeren in Power BI

In dit artikel wordt **fase 5** beschreven. Deze heeft betrekking op het implementeren, ondersteunen en bewaken van inhoud wanneer u naar Power BI migreert.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. Fase 5 wordt in dit artikel uitgelicht.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De primaire focus in fase 5 ligt op de implementatie van de nieuwe Power BI-oplossing in productie.

De uitvoer van deze fase is een productieoplossing die gereed is voor gebruik door het bedrijf. Wanneer u met een agile methode werkt, is het acceptabel om enkele geplande verbeteringen te hebben die in een toekomstige iteratie worden geleverd. Ondersteuning en bewaking zijn in deze fase en op doorlopende basis belangrijk.

> [!TIP]
> De onderwerpen die in dit artikel worden besproken hebben niet alleen betrekking op de parallelle uitvoering met en het uit bedrijf nemen van verouderde rapporten, wat hieronder wordt beschreven, maar ook op een standaard Power BI-implementatieproject.

## <a name="deploy-to-test-environment"></a>Implementeren in testomgeving

Voor IT-beheerde oplossingen of oplossingen die essentieel zijn voor de productiviteit van uw bedrijf, is er meestal een testomgeving. Een testomgeving bevindt zich tussen ontwikkeling en productie en is niet nodig voor alle Power BI-oplossingen. Een testwerkruimte kan worden gebruikt als een stabiele locatie, gescheiden van ontwikkeling, om de gebruikersacceptatietest (UAT) uit te voeren voordat de oplossing wordt vrijgegeven voor productie.

Als uw inhoud is gepubliceerd naar een werkruimte met Premium-capaciteit, kunnen [implementatiepijplijnen](../create-reports/deployment-pipelines-overview.md) het implementatieproces vereenvoudigen voor ontwikkelings-, test- en productiewerkruimten. Publicatie kan echter ook handmatig of met [Power Shell-scripts](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/) worden gedaan.

### <a name="deploy-to-test-workspace"></a>Implementeren naar testwerkruimte

De belangrijkste activiteiten tijdens een implementatie naar de testwerkruimte bevatten doorgaans:

- **Verbindingsreeksen en -parameters:** Wijzig de verbindingsreeksen voor de gegevensset als de gegevensbron verschilt tussen ontwikkelen en testen. [Parameterisering](../connect-data/service-parameters.md) kunnen worden gebruikt om verbindingsreeksen effectief te beheren.
- **Inhoud van werkruimte:** Publiceer gegevenssets en rapporten naar de testwerkruimte en maak dashboards.
- **App.** Publiceer een [app](../consumer/end-user-apps.md) met behulp van de inhoud uit de testwerkruimte als deze deel zal uitmaken van het gebruikersacceptatieproces. Normaal gesproken zijn app-machtigingen beperkt tot een beperkt aantal personen die betrokken zijn bij de gebruikersacceptatietest.
- **Gegevens vernieuwen:** [Plan de vernieuwing van de gegevensset](../connect-data/refresh-scheduled-refresh.md) voor alle importgegevenssets voor de periode waarin de gebruikersacceptatietest actief plaatsvindt.
- **Beveiliging:** Werk [werkruimterollen](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) bij of verifieer ze. Werkruimtetoegang wordt uitgevoerd voor een klein aantal personen die zijn betrokken bij de gebruikersacceptatietest.

> [!NOTE]
> Meer informatie over opties voor de implementatie naar de ontwikkelings, test- en productieomgeving vindt u in sectie 9 van [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Gebruikersacceptatietest uitvoeren

Over het algemeen worden bij gebruikersacceptatietests zakelijke gebruikers betrokken die inhoudelijk deskundig zijn. Na verificatie onderschrijven ze dat de nieuwe inhoud nauwkeurig is, aan de vereisten voldoet en kan worden geïmplementeerd voor een breder gebruik door anderen.

De mate waarin dit UAT-proces formeel is, bijvoorbeeld daadwerkelijk wordt ondertekend, is afhankelijk van uw procedures voor wijzigingsbeheer.

## <a name="deploy-to-production-environment"></a>Implementeren in uw productieomgeving

Er zijn verschillende overwegingen voor implementatie in de productieomgeving.

### <a name="conduct-a-staged-deployment"></a>Een gefaseerde implementatie uitvoeren

Als u risico's en gebruikersonderbrekingen wilt minimaliseren of als er andere overwegingen zijn, kunt u ervoor kiezen een gefaseerde implementatie uit te voeren. Bij de eerste implementatie naar productie is mogelijk een kleinere groep testgebruikers betrokken. Met een pilot kan de testgebruikers actief om feedback worden gevraagd.

Breid de machtigingen in de productiewerkruimte of de app geleidelijk uit totdat alle doelgebruikers zijn gemachtigd om de nieuwe Power BI-oplossing te gebruiken.

> [!TIP]
> Gebruik het [activiteitenlogboek van Power BI](../admin/service-admin-auditing.md) om inzicht te krijgen in hoe gebruikers de nieuwe Power BI-oplossing accepteren en gebruiken.

### <a name="handle-additional-components"></a>Aanvullende onderdelen verstrekken

Tijdens het implementatieproces moet u mogelijk samenwerken met uw Power BI-beheerders om te voldoen aan andere vereisten die nodig zijn om de gehele oplossing te ondersteunen, zoals:

- **Gatewayonderhoud:** Mogelijk moet een [nieuwe gegevensbron](../connect-data/service-gateway-data-sources.md) in de gegevensgateway worden geregistreerd.
- **Gatewaystuurprogramma's en -connectors:** Een nieuwe eigen gegevensbron vereist mogelijk de installatie van een nieuw stuurprogramma of een aangepaste connector op elke server in het gatewaycluster.
- **Nieuwe Premium-capaciteit maken:** U kunt mogelijk een bestaande [Premium-capaciteit](../admin/service-premium-capacity-manage.md) gebruiken. Er kunnen ook situaties zijn waarin een nieuwe Premium-capaciteit is gegarandeerd. Dit kan het geval zijn wanneer u de werkbelasting van een afdeling met opzet wilt scheiden.
- **Een Power BI-gegevensstroom instellen:** Activiteiten voor gegevens voorbereiding kunnen met behulp van Power Query Online eenmaal worden ingesteld in een [Power BI-gegevensstroom](../transform-model/dataflows/dataflows-introduction-self-service.md). Hiermee voorkomt u dat u gegevensvoorbereiding in veel verschillende Power BI Desktop-bestanden moet repliceren.
- **Een nieuwe organisatie-visual registreren:** [Organisatie-visuals](../developer/visuals/power-bi-custom-visuals-organization.md) voor aangepaste visuals die niet afkomstig zijn van AppSource, kunnen in de beheerportal worden geregistreerd.
- **Aanbevolen inhoud instellen:** Er bestaat een tenantinstelling die bepaalt wie [inhoud mag aanbevelen](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) op de startpagina van de Power BI-service.
- **Vertrouwelijkheidslabels instellen:** Alle [vertrouwelijkheidslabels](../admin/service-security-data-protection-overview.md) zijn geïntegreerd in Microsoft Information Protection (aanbevolen).

### <a name="deploy-to-production-workspace"></a>Implementeren in productiewerkruimte

De belangrijkste activiteiten tijdens een implementatie naar de productiewerkruimte bevatten doorgaans:

- **Wijzigingsbeheer:** Verschaf zo nodig goedkeuring voor implementatie en communiceer de implementatie naar de gebruikers via uw standaardprocedures voor wijzigingsbeheer. Er is mogelijk een goedgekeurd venster voor wijzigingsbeheer gedurende welke productie-implementaties zijn toegestaan. Normaal gesproken is dit van toepassing op IT-beheerde inhoud en veel minder vaak op selfservice inhoud.
- **Plan voor terugdraaien:** Bij een migratie wordt uitgegaan van een migratie van een nieuwe oplossing die voor de eerste keer wordt uitgevoerd. Als er al inhoud bestaat, is het verstandig om een plan te maken om terug te gaan naar de vorige versie. Voor dit doel zijn vorige versies van de Power BI Desktop-bestanden (met SharePoint of OneDrive-versiebeheer) prima.
- **Verbindingsreeksen en -parameters:** Wijzig de verbindingsreeksen voor de gegevensset als de gegevensbron verschilt tussen test en productie. [Parameterisering](../connect-data/service-parameters.md) kan voor dit doel effectief worden gebruikt.
- **Gegevens vernieuwen:** [Plan de gegevenssetvernieuwing](../connect-data/refresh-scheduled-refresh.md) voor eventuele geïmporteerde gegevenssets.
- **Inhoud van werkruimte:** Publiceer gegevenssets en rapporten naar de productiewerkruimte en maak dashboards. [De implementatie van pijplijnen](../create-reports/deployment-pipelines-overview.md) kan de implementatie naar ontwikkelings-, test- en productiewerkruimten vereenvoudigen als uw inhoud is gepubliceerd naar een werkruimte met Premium-capaciteit.
- **App:** Als apps deel uitmaken van uw strategie voor inhoudsdistributie, publiceert u een [app](../consumer/end-user-apps.md) met behulp van de inhoud uit de productiewerkruimte.
- **Beveiliging:** De [werkruimterollen](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) moeten worden bijgewerkt en geverifieerd conform uw strategie voor inhoudsdistributie en samenwerking.
- **Gegevenssetinstellingen:** De instellingen voor elke gegevensset moeten worden bijgewerkt en geverifieerd, waaronder:
  - [Aanbeveling](../collaborate-share/service-endorse-content.md) (zoals gecertificeerd of gepromoot)
  - Gatewayverbindings- of gegevensbronreferenties
  - Geplande vernieuwing
  - [Aanbevolen Q&A-vragen](../create-reports/service-q-and-a-create-featured-questions.md)
- **Rapport- en dashboardinstellingen:** De instellingen voor elk rapport en dashboard moeten worden bijgewerkt en geverifieerd. De belangrijkste instellingen zijn onder andere:
  - Beschrijving
  - Contactpersoon of -groep
  - [Vertrouwelijkheidslabel](../admin/service-security-apply-data-sensitivity-labels.md)
  - [Aanbevolen inhoud](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Abonnementen:** Stel zo nodig rapportabonnementen in.

> [!IMPORTANT]
> U hebt op dit moment een grote mijlpaal bereikt. Vier deze prestatie door de migratie te voltooien.

### <a name="communicate-with-users"></a>Communicatie met gebruikers

Kondig de nieuwe oplossing bij consumenten aan. Laat ze weten waar ze de inhoud en de bijbehorende documentatie, veelgestelde vragen en zelfstudies kunnen vinden. Om de nieuwe inhoud te introduceren, zou u bijvoorbeeld een lunch-en-leersessie kunnen hosten of een aantal on-demand video's kunnen voorbereiden.

Zorg ervoor dat u instructies opneemt voor het vragen van hulp en het geven van feedback.

### <a name="conduct-a-retrospective"></a>Evaluatie

U kunt een evaluatie uitvoeren om na te gaan wat er goed ging met de migratie en wat er bij een volgende migratie beter zou kunnen.

## <a name="run-in-parallel"></a>Parallelle uitvoering

In veel gevallen wordt de nieuwe oplossing gedurende een vooraf vastgestelde tijd parallel met de oude oplossing uitgevoerd. Voordelen van parallelle uitvoering zijn onder andere:

- Minder risico's, met name als de rapporten als cruciaal zijn.
- Gebruikers krijgen de tijd om aan de nieuwe Power BI-oplossing te wennen.
- De informatie die in Power BI wordt weergegeven, kan verwijzingen bevatten naar de verouderde rapporten.

## <a name="decommission-the-legacy-report"></a>Het verouderde rapport buiten gebruik stellen

Op een bepaald moment moeten de rapporten die naar Power BI zijn gemigreerd, op het oudere BI-platform buiten gebruik worden gesteld. Verouderde rapporten kunnen buiten gebruik worden gesteld wanneer:

- De vooraf vastgestelde tijd voor parallelle uitvoering - die aan de gebruikers moet zijn gecommuniceerd - is verlopen. Dit is in het algemeen 30-90 dagen.
- Alle gebruikers van het verouderde systeem hebben toegang tot de nieuwe Power BI-oplossing.
- Er worden geen significante activiteiten meer uitgevoerd met het verouderde rapport.
- Er zijn geen problemen opgetreden met de nieuwe Power BI-oplossing die van invloed kunnen zijn op de productiviteit van de gebruiker.

## <a name="monitor-the-solution"></a>De oplossing bewaken

Gebeurtenissen in het [activiteitenlogboek van Power BI](../admin/service-admin-auditing.md) kunnen worden gebruikt om inzicht te krijgen in gebruikspatronen van de nieuwe oplossing (of het [uitvoeringslogboek](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view) voor inhoud die is geïmplementeerd op Power BI Report Server). Door het activiteitenlogboek te analyseren, kunt u achterhalen of het werkelijke gebruik afwijkt van de verwachtingen. Ook kan worden vastgesteld of de oplossing adequaat wordt ondersteund.

Hier volgen enkele vragen die beantwoord kunnen worden door het activiteitenlogboek te bekijken:

- Hoe vaak wordt de inhoud weergegeven?
- Wie bekijkt de inhoud?
- Wordt de inhoud doorgaans bekeken via een app of een werkruimte?
- Gebruiken de meeste gebruikers een browser of een mobiele toepassing?
- Worden er abonnementen gebruikt?
- Worden er nieuwe rapporten gemaakt die op deze oplossing zijn gebaseerd?
- Hoe vaak wordt inhoud weergegeven?
- Hoe is beveiliging gedefinieerd?
- Treden er regelmatig problemen op, zoals problemen met het vernieuwen van gegevens?
- Vinden er activiteiten plaats (bijvoorbeeld aanzienlijke exportactiviteiten of het veelvuldig delen van rapporten), waardoor extra training kan zijn gerechtvaardigd?

> [!IMPORTANT]
> Zorg ervoor dat iemand het activiteitenlogboek regelmatig controleert. Het vastleggen ervan en het opslaan van de geschiedenis heeft alleen waarde voor auditing- -of nalevingsdoeleinden. De werkelijke waarde is echter wanneer proactieve actie kan worden uitgevoerd.

## <a name="support-the-solution"></a>De oplossing ondersteunen

Hoewel de migratie is voltooid, is de periode na de migratie van cruciaal belang voor het oplossen van problemen en het omgaan met eventuele prestatieoverwegingen. Na verloop van tijd zal de gemigreerde oplossing waarschijnlijk wijzigingen ondergaan naarmate de bedrijfsbehoeften zich ontwikkelen.

Ondersteuning is vaak afhankelijk van hoe selfservice BI in de hele organisatie wordt beheerd. Power BI-deskundigen in de bedrijfseenheden fungeren vaak als eerstelijnsondersteuning. Hoewel het een informele rol is, is het wel een essentiële rol die moet worden aangemoedigd.

De implementatie van een formeel ondersteuningsproces, ondersteund door IT met ondersteuningstickets, is eveneens essentieel voor het afhandelen van systeemgebaseerde routineaanvragen en voor escalatiedoeleinden.

U zou ook een [COE (Center of Excellence)](center-of-excellence-establish.md) kunnen hebben, in de vorm van interne consultants die Power BI in de organisatie ondersteunen, trainen en beheren. Een COE kan verantwoordelijk zijn voor het beheer van nuttige Power BI-inhoud in een interne portal.

Tot slot moet het voor inhoudsconsumenten duidelijk zijn met wie ze contact moeten opnemen met vragen over de inhoud, en moet er een mechanisme zijn waarop ze feedback kunnen geven met betrekking tot problemen of verbeteringen.

## <a name="next-steps"></a>Volgende stappen

In het [laatste artikel in deze serie](powerbi-migration-learn-from-customers.md) leert u van klanten tijdens het migreren naar Power BI.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).