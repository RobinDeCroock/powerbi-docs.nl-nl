---
title: Proces van implementatiepijplijnen
description: Uitleg over het proces van Power BI-implementatiepijplijnen
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: contperfq1
ms.date: 10/21/2020
ms.openlocfilehash: 6c1e4212cb991ff7eb3d0f8a5e336010499bcd1c
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668598"
---
# <a name="understand-the-deployment-process"></a>Uitleg over het implementatieproces

Met het implementatieproces kunt u inhoud van de ene pijplijnfase klonen naar een andere. Meestal is dit van ontwikkeling naar test, of van test naar productie.

Tijdens de implementatie wordt in Power BI de inhoud van de huidige fase gekopieerd naar de doelfase. De verbindingen tussen de gekopieerde items blijven behouden tijdens het kopieerproces. In Power BI worden ook de geconfigureerde gegevenssetregels toegepast op de bijgewerkte inhoud in de doelfase. Het implementeren van inhoud kan enige tijd duren, afhankelijk van het aantal items dat wordt geïmplementeerd. Gedurende deze tijd kunt u navigeren naar andere pagina's in de Power BI-portal, maar u kunt de inhoud in de doelfase niet gebruiken.

## <a name="deploying-content-to-an-empty-stage"></a>Inhoud implementeren in een lege fase

Wanneer u inhoud implementeert in een lege fase, worden de metagegevens van de rapporten, dashboards en gegevenssets in de werkruimte vanwaaruit u implementeert, gekopieerd naar de fase waarin u implementeert. Er wordt in een premium-capaciteit een nieuwe werkruimte gemaakt voor de fase waarin u implementeert.

Er zijn twee manieren om inhoud te implementeren van de ene fase naar de volgende. U kunt alle inhoud implementeren of u kunt [selecteren welke inhoudsitems u wilt implementeren](deployment-pipelines-get-started.md#selective-deployment).

U kunt inhoud ook achterwaarts implementeren, vanuit een latere fase in de implementatiepijplijn, naar een eerdere.

Als de implementatie is voltooid, vernieuwt u de gegevenssets zodat u de zojuist gekopieerde inhoud kunt gebruiken. Vernieuwen van de gegevensset is vereist omdat de gegevens niet van de ene fase naar de andere worden gekopieerd. Raadpleeg de sectie [Gekopieerde eigenschappen van items tijdens de implementatie](#item-properties-copied-during-deployment) als u wilt weten welke eigenschappen van items tijdens het implementatieproces wel worden gekopieerd en welke niet.

### <a name="creating-a-premium-capacity-workspace"></a>Een werkruimte maken in een premium-capaciteit

Tijdens de eerste implementatie wordt met de implementatiepijplijnen gecontroleerd of u beschikt over machtigingen voor premium-capaciteit.  

Als u capaciteitsmachtigingen hebt, wordt de inhoud van de werkruimte gekopieerd naar de fase waarin u implementeert. Er wordt ook een nieuwe werkruimte voor deze fase gemaakt in de premium-capaciteit.

Als u geen capaciteitsmachtigingen hebt, wordt de werkruimte wel gemaakt, maar wordt de inhoud niet gekopieerd. U kunt een capaciteitsbeheerder vragen om uw werkruimte toe te voegen aan een capaciteit of u kunt vragen om toewijzingsmachtigingen voor de capaciteit. Later, wanneer de werkruimte is toegewezen aan een capaciteit, kunt u inhoud implementeren in deze werkruimte.

Als u [Premium per gebruiker (PPU)](../admin/service-premium-per-user-faq.md) gebruikt, wordt uw werkruimte automatisch gemaakt in de capaciteit die is gekoppeld aan uw PPU. In dergelijke gevallen zijn capaciteitsmachtigingen niet vereist. Werkruimten die zijn gemaakt door een PPU-gebruiker, kunnen echter alleen worden geopend door andere PPU-gebruikers. Daarnaast kan inhoud die is gemaakt in dergelijke werkruimten alleen worden gebruikt door PPU-gebruikers.

### <a name="workspace-and-content-ownership"></a>Eigendom van werkruimte en inhoud

De gebruiker die implementeert wordt automatisch de gegevensseteigenaar van de gekloonde gegevenssets en de enige beheerder van de nieuwe werkruimte.

## <a name="deploy-content-to-an-existing-workspace"></a>Inhoud implementeren in een bestaande werkruimte

Voorbeelden van implementeren van inhoud in een werkende productiepijplijn, in een fase die een bestaande werkruimte bevat:

* Nieuwe inhoud als aanvulling implementeren in een fase die al inhoud bevat.

* Nieuwe inhoud die wordt geïmplementeerd ter vervanging van oude inhoud, in een huidige werkende fase.

### <a name="deployment-process"></a>Implementatieproces

Inhoud van de huidige fase wordt gekopieerd naar de doelfase. In Power BI wordt bestaande inhoud in de doelfase geïdentificeerd en overschreven. Implementatiepijplijnen gebruiken de verbinding tussen het bovenliggende item en de bijbehorende klonen om te identificeren welk inhoudsitem moet worden overschreven. Deze verbinding blijft behouden wanneer nieuwe inhoud wordt gemaakt. Bij het overschrijven wordt alleen de inhoud van het item overschreven. De id, URL en machtigingen van het item blijven ongewijzigd.

In de doelfase blijven [eigenschappen van items die niet zijn gekopieerd](deployment-pipelines-process.md#item-properties-that-are-not-copied), behouden zoals ze waren vóór de implementatie. Nieuwe inhoud en nieuwe items worden uit de huidige fase gekopieerd naar de doelfase.

### <a name="refreshing-the-dataset"></a>De gegevensset vernieuwen​​

Gegevens in de doelgegevensset blijven waar mogelijk behouden. Als er geen wijzigingen zijn aangebracht in een gegevensset, blijven de gegevens behouden zoals ze waren vóór de implementatie.

Bij kleine wijzigingen, zoals het toevoegen van een tabel of metingen, blijven in Power BI de oorspronkelijke gegevens behouden en wordt de vernieuwing geoptimaliseerd om alleen te vernieuwen wat nodig is. Bij wijzigingen in het schema die fouten veroorzaken, of wijzigingen in de verbinding met de gegevensbron, is een volledige vernieuwing vereist.

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>Vereisten voor implementatie in een fase met een bestaande werkruimte

Zolang de geïmplementeerde inhoud zich in een [premium-capaciteit](../admin/service-premium-what-is.md) bevindt, kan een gebruiker die aan de volgende voorwaarden voldoet, de inhoud implementeren in een fase met een bestaande werkruimte:

* Een gebruiker met een [Pro-licentie](../admin/service-admin-purchasing-power-bi-pro.md) of een [PPU-gebruiker](../admin/service-premium-per-user-faq.md) die lid is van beide werkruimten in de bron- en doelimplementatiefasen.

* Een eigenaar van alle gegevenssets in de doelwerkruimte die op het punt staan te worden geïmplementeerd.

Raadpleeg de sectie [Machtigingen](#permissions) voor meer informatie.

## <a name="deployed-items"></a>Geïmplementeerde items

Wanneer u inhoud vanuit de ene pijplijnfase implementeert in een andere, bevat de gekopieerde inhoud de volgende Power BI-items:

* Gegevenssets

* Rapporten

* Dashboards

### <a name="unsupported-items"></a>Niet-ondersteunde items

Implementatiepijplijnen bieden geen ondersteuning voor de volgende items:

* Gegevenssets die niet afkomstig zijn uit een PBIX-bestand

* Rapporten die zijn gebaseerd op niet-ondersteunde gegevenssets

* [Werkruimtes voor sjabloon-app](../connect-data/service-template-apps-create.md#create-the-template-workspace)

* Gepagineerde rapporten

* Gegevensstromen

* PUSH-gegevenssets

* Werkmappen

## <a name="item-properties-copied-during-deployment"></a>Eigenschappen van items die worden gekopieerd tijdens de implementatie

Tijdens de implementatie worden de volgende eigenschappen van items gekopieerd, en worden de eigenschappen van items in de doelfase hiermee overschreven:

* Gegevensbronnen ([gegevenssetregels](deployment-pipelines-get-started.md#step-4---create-dataset-rules) worden ondersteund)

* Parameters ([gegevenssetregels](deployment-pipelines-get-started.md#step-4---create-dataset-rules) worden ondersteund)

* Rapportvisuals

* Rapportpagina's

* Update van dashboardtegels

* Modelmetagegevens

* Itemrelaties

### <a name="item-properties-that-are-not-copied"></a>Eigenschappen van items die niet worden gekopieerd

De volgende eigenschappen van items worden niet gekopieerd tijdens de implementatie:

* Gegevens - Er worden geen gegevens gekopieerd, alleen metagegevens worden gekopieerd

* URL

* Id

* Machtigingen: voor een werkruimte of een specifiek item

* Werkruimte-instellingen: elke fase heeft een eigen werkruimte

* App-inhoud en -instellingen: raadpleeg [Power BI-apps implementeren](#deploying-power-bi-apps) om uw apps te implementeren

De volgende eigenschappen van gegevenssets worden niet gekopieerd tijdens de implementatie:

* Roltoewijzing

* Vernieuwingsschema

* Gegevensbronreferenties

* Cache-instellingen voor query's (kunnen worden overgenomen van de capaciteit)

* Goedkeuringsinstellingen

## <a name="incremental-refresh"></a>Incrementeel vernieuwen

Implementatiepijplijnen ondersteunen [incrementeel vernieuwen](../admin/service-premium-incremental-refresh.md), een functie waarmee grote gegevenssets sneller en betrouwbaarder kunnen worden vernieuwd, en met een lager verbruik.

Met implementatiepijplijnen kunt u gegevensset met incrementeel vernieuwen bijwerken en zowel gegevens als partities behouden. Wanneer u de gegevensset implementeert, wordt het beleid ook gekopieerd.

### <a name="activating-incremental-refresh-in-a-pipeline"></a>Incrementeel vernieuwen in een pijplijn activeren

Als u incrementeel vernieuwen wilt inschakelen, [schakelt u het in Power BI Desktop in](../admin/service-premium-incremental-refresh.md#configure-incremental-refresh) en publiceert u vervolgens uw gegevensset. Nadat de publicatie is het beleid voor incrementeel vernieuwen in de hele de pijplijn vergelijkbaar en kan het alleen worden geschreven in Power BI Desktop.

Als de pijplijn is geconfigureerd met incrementeel vernieuwen, wordt u aangeraden de volgende stroom te gebruiken:

1. Wijzigingen aanbrengen in uw PBIX-bestand in Power BI Desktop. Als u lange wachttijden wilt voorkomen, kunt u wijzigingen aanbrengen met behulp van een sample van uw gegevens.

2. Uw PBIX-bestand uploaden naar de *ontwikkelingsfase*.

3. Uw inhoud implementeren in de *testfase*. Na de implementatie worden de aangebrachte wijzigingen toegepast op de volledige gegevensset die u gebruikt.

4. Controleer de wijzigingen die u in de *testfase* hebt aangebracht en implementeer ze na de controle in de *productiefase*.

### <a name="usage-examples"></a>Gebruiksvoorbeelden

Hieronder ziet u enkele voorbeelden van hoe u incrementeel vernieuwen kunt integreren met implementatiepijplijnen.

* [Maak een nieuwe pijplijn](deployment-pipelines-get-started.md#step-1---create-a-deployment-pipeline) en verbindt deze met een werkruimte met een gegevensset waarvoor incrementeel vernieuwen is ingeschakeld.

* Schakel incrementeel vernieuwen in een gegevensset in die zich al in een *ontwikkelingswerkruimte* bevindt.  

* Maak een pijplijn vanuit een productiewerkruimte die een gegevensset bevat waarvoor incrementeel vernieuwen wordt gebruikt. Dit wordt gedaan door de werkruimte toe te wijzen aan de *productiefase* van een nieuwe pijplijn en met behulp van [achterwaartse implementatie](deployment-pipelines-get-started.md#backwards-deployment) te implementeren in de *testfase*. Vervolgens implementeert u de werkruimte in de *ontwikkelingsfase*.

* Publiceer een gegevensset die incrementeel vernieuwen gebruikt voor een werkruimte die deel uitmaakt van een bestaande pijplijn.

### <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Voor incrementeel vernieuwen bieden implementatiepijplijnen alleen ondersteuning voor gegevenssets die gebruikmaken van [verbeterde metagegevens](../connect-data/desktop-enhanced-dataset-metadata.md). Vanaf de release van Power BI Desktop van september 2020 implementeren alle gegevenssets die zijn gemaakt of gewijzigd met Power BI Desktop, automatisch verbeterde metagegevens van de gegevensset.

Wanneer een gegevensset opnieuw wordt gepubliceerd naar een actieve pijplijn waarvoor incrementeel vernieuwen is ingeschakeld, zullen de volgende wijzigingen tot een mislukte implementatie leiden vanwege een mogelijk verlies aan gegevens:

* Opnieuw publiceren van een gegevensset waarvoor geen incrementeel vernieuwen is gebruikt, om een gegevensset te vervangen waarvoor incrementeel vernieuwen is ingeschakeld.

* Het wijzigen van de naam van een tabel waarvoor incrementeel vernieuwen is ingeschakeld.

* Het wijzigen van de naam van niet-berekende kolommen in een tabel waarvoor incrementeel vernieuwen is ingeschakeld.

Andere wijzigingen, zoals het toevoegen van een kolom, het verwijderen van een kolom en het wijzigen van de naam van een berekende kolom, zijn toegestaan. Als de wijzigingen echter van invloed zijn op de weergave, moet u vernieuwen voordat de wijziging zichtbaar is.

## <a name="deploying-power-bi-apps"></a>Power BI-apps implementeren

[Power BI-apps](../consumer/end-user-apps.md) zijn de aanbevolen manier om inhoud te distribueren naar gebruikers van de gratis versie van Power BI. Met behulp van implementatiepijplijnen kunt u Power BI-apps beheren in een implementatiepijplijn, zodat u meer controle en flexibiliteit hebt wanneer het gaat om de levenscyclus van uw app.

Maak een app voor elke implementatiepijplijnfase, zodat u elke app-update kunt testen vanuit het perspectief van de eindgebruiker. Met een implementatiepijplijn kunt u dit proces eenvoudig beheren. Gebruik de knop Publiceren of Weergeven in de werkruimtekaart om de app te publiceren of weer te geven in een specifieke pijplijnfase.

[![Een schermopname die de knop ‘app publiceren’ toont, rechtsonder in de productiefase.](media/deployment-pipelines-process/publish.png)](media/deployment-pipelines-process/publish.png#lightbox)

In de productiefase wordt met de hoofdactieknop (in de rechterbenedenhoek) de pagina App bijwerken in Power BI geopend, zodat eventuele inhoudsupdates beschikbaar worden voor gebruikers van de app.

[![Een schermopname die de knop app bijwerken toont, rechtsonder in de productiefase.](media/deployment-pipelines-process/update-app.png)](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>Het implementatieproces omvat niet het bijwerken van de inhoud of instellingen van de app. Als u wijzigingen wilt aanbrengen in de inhoud of instellingen, moet u de app handmatig bijwerken in de vereiste pijplijnfase.

## <a name="permissions"></a>Machtigingen

Pijplijnmachtigingen en werkruimtemachtigingen worden afzonderlijk verleend en beheerd. Bijvoorbeeld, een gebruiker met pijplijntoegang die niet beschikt over werkruimtemachtigingen, kan de pijplijn weergeven en delen met anderen. Deze gebruiker kan echter de inhoud van de werkruimte niet weergeven in de pijplijn, of op de werkruimtepagina, en kan geen implementaties uitvoeren.

### <a name="user-with-pipeline-access"></a>Gebruiker met pijplijntoegang

Gebruikers met pijplijntoegang beschikken over de volgende machtigingen:

* De pijplijn weergeven

* De pijplijn delen met anderen

* De pijplijn bewerken en verwijderen

>[!NOTE]
>Pijplijntoegang verleent geen machtigingen om de inhoud van de werkruimte weer te geven of er acties op uit te voeren.

### <a name="workspace-viewer"></a>Werkruimteviewer

Werkruimteviewers die *pijplijntoegang* hebben, kunnen ook het volgende doen:

* Inhoud gebruiken

>[!NOTE]
>Werkruimteviewers hebben geen toegang tot de gegevensset en kunnen de inhoud van de werkruimte niet bewerken.

### <a name="workspace-contributor"></a>Werkruimtebijdrager

Werkruimtebijdragers die *pijplijntoegang* hebben, kunnen ook het volgende doen:

* Inhoud gebruiken

* Fasen vergelijken

* Gegevenssets weergeven

### <a name="workspace-member"></a>Werkruimtelid

Werkruimteleden die *pijplijntoegang* hebben, kunnen ook het volgende doen:

* Inhoud van de werkruimte weergegeven

* Fasen vergelijken

* Rapporten en dashboards implementeren

* Werkruimten verwijderen

### <a name="workspace-admin"></a>Werkruimtebeheerder

Werkruimtebeheerders met *pijplijntoegang* kunnen acties voor *werkruimteleden* uitvoeren, en kunnen ook het volgende doen:

* Werkruimten toewijzen

* Werkruimten verwijderen

### <a name="dataset-owner"></a>Eigenaar van gegevensset

Eigenaars van gegevenssets die lid of beheerder van de werkruimte zijn, kunnen ook het volgende doen:

* Gegevenssets bijwerken

* Regels configureren

>[!NOTE]
>In deze sectie worden gebruikersmachtigingen in implementatiepijplijnen beschreven. De machtigingen die in deze sectie worden vermeld, kunnen een andere toepassing hebben in andere Power BI-functies.

## <a name="limitations"></a>Beperkingen

In deze sectie worden de meeste beperkingen in implementatiepijplijnen vermeld.

* De werkruimte moet zich bevinden in een  [premium-capaciteit](../admin/service-premium-what-is.md).

* Power BI-items, zoals rapporten en dashboards, met Power BI-[vertrouwelijkheidslabels](../admin/service-security-sensitivity-label-overview.md), kunnen niet worden geïmplementeerd.

* Het maximum aantal Power BI-items dat in één implementatie kan worden geïmplementeerd, is 300.

* Zie [Beperkingen voor werkruimtetoewijzing](deployment-pipelines-get-started.md#workspace-assignment-limitations) voor een lijst met beperkingen voor werkruimten.

* Zie [Niet-ondersteunde items](#unsupported-items) voor een lijst met niet-ondersteunde items.

### <a name="dataset-limitations"></a>Beperkingen van gegevensset

* Er kunnen geen gegevenssets worden geïmplementeerd die gebruikmaken van realtime verbinding.

* Als de doel-dataset tijdens de implementatie gebruikmaakt van een [live-verbinding](../connect-data/desktop-report-lifecycle-datasets.md), moet de bron-gegevensset ook deze verbindingsmodus gebruiken.

* Na de implementatie wordt het downloaden van een gegevensset (vanuit de fase waarnaar deze is geïmplementeerd) niet meer ondersteund.

* Zie [Beperkingen voor gegevenssetregels](deployment-pipelines-get-started.md#dataset-rule-limitations) voor een lijst met beperkingen voor gegevenssetregels.

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Inleiding tot implementatiepijplijnen](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[Best practices voor implementatiepijplijnen](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[Aan de slag gaan met implementatiepijplijnen](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Problemen met implementatiepijplijnen oplossen](deployment-pipelines-troubleshooting.md)
