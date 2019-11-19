---
title: Gegevens vernieuwen in Power BI
description: In dit artikel worden de functies beschreven voor het vernieuwen van gegevens van Power BI en de bijbehorende afhankelijkheden op conceptueel niveau.
author: mgblythe
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/14/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 422d742748fc6880b0636bd3a0c5de7011a3ff0a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860798"
---
# <a name="data-refresh-in-power-bi"></a>Gegevens vernieuwen in Power BI

Met Power BI kunt u snel van gegevens tot inzicht en vervolgens tot actie overgaan, maar moet u ervoor zorgen dat de gegevens in uw Power BI-rapporten en dashboards recent is. Het is vaak essentieel om te weten hoe u de gegevens kunt vernieuwen voor het leveren van nauwkeurige resultaten.

In dit artikel worden de functies beschreven voor het vernieuwen van gegevens van Power BI en de bijbehorende afhankelijkheden op conceptueel niveau. Het bevat ook aanbevolen procedures en tips om algemene problemen met vernieuwen te voorkomen. De inhoud legt het fundament om meer inzicht te krijgen over de werking van het vernieuwen van gegevens. Raadpleeg de zelfstudies en instructiegidsen die zijn vermeld in het gedeelte Volgende stappen aan het einde van dit artikel voor gerichte stapsgewijze instructies voor het configureren van gegevensvernieuwing.

## <a name="understanding-data-refresh"></a>Achtergrondinformatie over gegevensvernieuwing

Wanneer u gegevens vernieuwt, moet u in Power BI een query uitvoeren op de onderliggende gegevensbronnen, mogelijkerwijs de brongegevens in een gegevensset laden en vervolgens visualisaties in uw rapporten of dashboards bijwerken die afhankelijk zijn van de bijgewerkte gegevensset. Het hele proces bestaat uit meerdere fasen, afhankelijk van de opslagmodi van uw gegevenssets, zoals wordt uitgelegd in de volgende secties.

Als u wilt begrijpen hoe uw gegevenssets, rapporten en dashboards worden vernieuwd in Power BI, moet u rekening houden met de volgende concepten:

- **Opslagmodi en gegevenssettypen**: De opslagmodi en gegevenssettypen waarvoor Power BI ondersteuning biedt, beschikken over verschillende vernieuwingsvereisten. U kunt kiezen tussen het opnieuw importeren van gegevens in Power BI om te zien welke wijzigingen zijn opgetreden of het rechtstreeks opvragen van de gegevens bij de bron.
- **Vernieuwingstypen in Power BI**: Wanneer u de diverse vernieuwingstypen kent, kunt u beter begrijpen welke processen in Power BI plaatsvinden tijdens een vernieuwingsbewerking. En wanneer deze gegevens worden gecombineerd met specifieke informatie over opslagmodi, geeft dit meer inzicht in welke processen er precies in Power BI plaatsvinden wanneer u **Nu vernieuwen** selecteert voor een gegevensset.

### <a name="storage-modes-and-dataset-types"></a>Opslagmodi en gegevenssettypen

Een Power BI-gegevensset kan in een van de volgende modi werken om gegevens te openen vanuit een verscheidenheid aan gegevensbronnen. Zie [Opslagmodus in Power BI Desktop](desktop-storage-mode.md) voor meer informatie.

- Importmodus
- DirectQuery-modus
- LiveConnect-modus
- Push-modus

In het volgende diagram worden de verschillende gegevensstromen weergegeven op basis van de opslagmodus. Het belangrijkste punt is dat alleen voor gegevenssets in de importmodus een vernieuwing van brongegevens is vereist. Vernieuwen is vereist omdat dit type gegevensset gegevens importeert uit de gegevensbronnen, en de geïmporteerde gegevens kunnen periodiek of ad hoc worden bijgewerkt. DirectQuery-gegevenssets en gegevenssets in de LiveConnect-modus met Analysis Services importeren geen gegevens; deze vragen de onderliggende gegevensbron op met elke gebruikersinteractie. Gegevenssets in push-modus hebben niet rechtstreeks toegang tot gegevensbronnen; hiervoor is vereist dat u de gegevens naar Power BI pusht. De vereisten voor het vernieuwen van gegevenssets verschillen, afhankelijk van de opslagmodus / het gegevenssettype.

![Opslagmodi en gegevenssettypen](media/refresh-data/storage-modes-dataset-types-diagram.png)

#### <a name="datasets-in-import-mode"></a>Gegevenssets in de importmodus

Power BI importeert de gegevens van de oorspronkelijke gegevensbronnen in de gegevensset. Voor query's van Power BI-rapporten en -dashboards die naar de gegevensset zijn verzonden, worden resultaten geretourneerd uit de geïmporteerde tabellen en kolommen. U kunt een dergelijke gegevensset als een kopie op een bepaald tijdstip beschouwen. Omdat in Power BI de gegevens worden gekopieerd, moet u de gegevensset vernieuwen om wijzigingen op te halen uit de onderliggende gegevensbronnen.

Omdat de gegevens in de Power BI-cache worden opgeslagen, kan de grootte van gegevenssets in de importmodus aanzienlijk zijn. Raadpleeg de volgende tabel voor de maximale grootte van de gegevenssets per capaciteit. Zorg ervoor dat u ruim onder de maximale omvang voor gegevenssets blijft ter voorkoming van problemen met vernieuwen die zich kunnen voordoen als tijdens een vernieuwingsbewerking meer dan de maximale beschikbare resources voor uw gegevenssets vereist zijn.

| Capaciteitstype | Maximale grootte van gegevenssets |
| --- | --- |
| Gedeeld, A1, A2 of A3 | 1 GB |
| A4 of P1 | 3 GB |
| A5 of P2 | 6 GB |
| A6 of P3 | 10 GB |
| | |

#### <a name="datasets-in-directqueryliveconnect-mode"></a>Gegevenssets in de modus DirectQuery/LiveConnect

Er worden in Power BI geen gegevens geïmporteerd via verbindingen die worden uitgevoerd in de modus DirectQuery/LiveConnect. In plaats daarvan retourneert de gegevensset steeds resultaten van de onderliggende gegevensbron wanneer een rapport of dashboard de gegevensset opvraagt. De query's worden door Power BI getransformeerd en doorgestuurd naar de gegevensbron.

Hoewel de DirectQuery-modus en de LiveConnect-modus vergelijkbaar zijn in het opzicht dat in Power BI de query's naar de bron worden opgestuurd, is het belangrijk te weten dat query's in de LiveConnect-modus niet door Power BI hoeven te worden getransformeerd. De query's gaan rechtstreeks naar het Analysis Services-exemplaar dat de database host, zonder gebruik te maken van resources op een gedeelde capaciteit of een Premium-capaciteit.

Omdat de gegevens niet worden geïmporteerd in Power BI, hoeft u geen gegevensvernieuwing uit te voeren. In Power BI worden nog wel tegels en mogelijkerwijs rapporten vernieuwd, zoals in de volgende sectie over vernieuwingstypen wordt uitgelegd. Een tegel is een rapportvisual die aan een dashboard is vastgemaakt. Dashboardtegels worden ongeveer elk uur vernieuwd, zodat de tegels recente resultaten weergeven. U kunt het schema in de instellingen voor gegevenssets wijzigen, zoals in de schermopname hieronder, of een dashboard-update handmatig afdwingen met behulp van de optie **Nu vernieuwen**.

![Vernieuwingsschema](media/refresh-data/refresh-schedule.png)

> [!NOTE]
> De sectie **Geplande vernieuwing van cache** van het tabblad **Gegevenssets** is niet beschikbaar voor gegevenssets in de importmodus. Voor deze gegevenssets hoeven de tegels niet afzonderlijk te worden vernieuwd, omdat in Power BI de tegels automatisch worden vernieuwd tijdens elke geplande of on-demand gegevensvernieuwing.

#### <a name="push-datasets"></a>Push-gegevenssets

Push-gegevenssets bevatten geen officiële definitie van een gegevensbron, zodat u geen gegevensvernieuwing hoeft uit te voeren in Power BI. U vernieuwt deze door uw gegevens in de gegevensset via een externe service of procedure te pushen, zoals Azure Stream Analytics. Dit is een gebruikelijke aanpak voor realtime analyses in Power BI. In Power BI wordt nog steeds cachegeheugen vernieuwd voor alle tegels die naast een push-gegevensset zijn gebruikt. Zie voor een gedetailleerd overzicht [Zelfstudie: Stream Analytics en Power BI: Een realtime analysedashboard voor het streamen van gegevens](/azure/stream-analytics/stream-analytics-power-bi-dashboard).

> [!NOTE]
> De Push-modus heeft ook enkele beperkingen zoals beschreven in [Beperkingen van REST API's van Power BI](developer/api-rest-api-limitations.md).

### <a name="power-bi-refresh-types"></a>Vernieuwingstypen in Power BI

Een vernieuwingsbewerking in Power BI kan bestaan uit meerdere vernieuwingstypen, zoals gegevensvernieuwing, OneDrive-vernieuwing, en vernieuwen van query-caches, tegels en rapportvisuals. Terwijl in Power BI de vereiste vernieuwingsstappen voor een bepaalde gegevensset automatisch worden bepaald, moet u weten hoe deze bijdragen aan de complexiteit en de duur van een vernieuwingsbewerking. Raadpleeg de volgende tabel voor een snelle verwijzing.

| Opslagmodus | Gegevens vernieuwen | OneDrive-vernieuwing | Caches van query's | Tegels vernieuwen | Rapportvisuals |
| --- | --- | --- | --- | --- | --- |
| Importeren | Gepland en on-demand | Ja, voor verbonden gegevenssets | Als Premium-capaciteit is geactiveerd | Automatisch en on-demand | Nee |
| DirectQuery | Niet van toepassing | Ja, voor verbonden gegevenssets | Als Premium-capaciteit is geactiveerd | Automatisch en on-demand | Nee |
| LiveConnect | Niet van toepassing | Ja, voor verbonden gegevenssets | Als Premium-capaciteit is geactiveerd | Automatisch en on-demand | Ja |
| Push | Niet van toepassing | Niet van toepassing | Niet praktisch | Automatisch en on-demand | Nee |
| | | | | | |

#### <a name="data-refresh"></a>Gegevens vernieuwen

Voor Power BI-gebruikers betekent vernieuwen van gegevens meestal dat gegevens uit de oorspronkelijke gegevensbronnen in een gegevensset worden geïmporteerd op basis van een vernieuwingsschema of on-demand. U kunt gegevenssets dagelijks meerdere keren vernieuwen, wat noodzakelijk kan zijn als de onderliggende brongegevens regelmatig worden gewijzigd. In Power BI worden gegevenssets op gedeelde capaciteit dagelijks niet vaker dan acht keer vernieuwd. Als de gegevensset zich op een Premium-capaciteit bevindt, kunt u maximaal 48 vernieuwingen per dag plannen in de instellingen van de gegevensset. Zie Geplande vernieuwing configureren verderop in dit artikel voor meer informatie.

Het is ook belangrijk om te benadrukken dat de dagelijkse beperking voor vernieuwen voor gedeelde capaciteit zowel geldt voor geplande vernieuwingen als API-vernieuwingen. U kunt ook een on-demand vernieuwing activeren door **Nu vernieuwen** te selecteren in het gegevenssetmenu, zoals in de volgende schermopname is afgebeeld. Vernieuwingen op aanvraag zijn niet opgenomen in de vernieuwingsbeperking. Houd er ook rekening mee dat gegevenssets voor een Premium-capaciteit geen beperkingen opleggen ten aanzien van API-vernieuwingen. Zie [Gegevenssets - Gegevensset vernieuwen](/rest/api/power-bi/datasets/refreshdataset) als u geïnteresseerd bent in het opstellen van uw eigen vernieuwingsoplossing met behulp van de Power BI REST API.

![Nu vernieuwen](media/refresh-data/refresh-now.png)

> [!NOTE]
> Gegevens op gedeelde capaciteit moeten binnen 2 uur zijn vernieuwd. Als voor uw gegevenssets langere bewerkingen voor Gegevensvernieuwing zijn vereist, kunt u de gegevensset naar een Premium-capaciteit overplaatsen. Voor Premium is de maximale duur voor vernieuwen vijf uur.

#### <a name="onedrive-refresh"></a>OneDrive-vernieuwing

Als u uw gegevenssets en rapporten hebt gemaakt op basis van een Power BI Desktop-bestand, een Excel-werkmap of een CSV-bestand (bestand met door komma's gescheiden waarden) in OneDrive of SharePoint Online, wordt een ander type vernieuwen uitgevoerd in Power BI, bekend als OneDrive-vernieuwing. Zie [Gegevens uit bestanden ophalen voor Power BI](service-get-data-from-files.md) voor meer informatie.

In tegenstelling tot een gegevenssetvernieuwing, waarin door Power BI gegevens uit een gegevensbron in een gegevensset worden geïmporteerd, worden bij een OneDrive-vernieuwing gegevenssets en rapporten met de betreffende bronbestanden gesynchroniseerd. Standaard vindt in Power BI ongeveer om het uur een controle plaats of een met een bestand in OneDrive of SharePoint Online verbonden gegevensset moet worden gesynchroniseerd. Als u eerdere synchronisatiecycli wilt controleren, kunt u de vernieuwingsgeschiedenis nog eens nalopen op het OneDrive-tabblad. In de volgende schermopname ziet u een voltooide synchronisatiecyclus voor een voorbeeldgegevensset.

![Geschiedenis vernieuwen](media/refresh-data/refresh-history.png)

Zoals in bovenstaande schermopname te zien is, is in Power BI deze OneDrive-vernieuwing geïdentificeerd als een **geplande** vernieuwing, maar het is niet mogelijk het interval voor vernieuwen te configureren. U kunt de OneDrive-vernieuwing alleen deactiveren in de instellingen van de gegevensset. Vernieuwen deactiveren is handig als u niet wilt dat uw gegevenssets en rapporten in Power BI automatisch eventuele wijzigingen van de bronbestanden overnemen.

Houd er rekening mee dat op de instellingspagina voor de gegevensset alleen de secties **OneDrive-referenties** en **OneDrive-vernieuwing** worden weergegeven als de gegevensset is verbonden met een bestand in OneDrive of SharePoint Online, zoals in de volgende schermopname. In gegevenssets die niet zijn verbonden met bronbestanden in OneDrive of SharePoint Online worden deze secties niet weergegeven.

![OneDrive-referenties en OneDrive-vernieuwing](media/refresh-data/onedrive-credentials-refresh.png)

Als u OneDrive-vernieuwing voor een gegevensset uitschakelt, kunt u uw gegevensset nog steeds on-demand synchroniseren door **Nu vernieuwen** te selecteren in het gegevenssetmenu. In het kader van de on-demand vernieuwing wordt in Power BI gecontroleerd of het bronbestand op OneDrive of SharePoint Online nieuwer is dan de gegevensset in Power BI is en wordt de gegevensset gesynchroniseerd als dit het geval is. In de **Vernieuwingsgeschiedenis** vindt u deze activiteiten als on-demand vernieuwingen op het tabblad **OneDrive**.

Houd er rekening mee dat bij een OneDrive-vernieuwing geen gegevens worden opgehaald uit de oorspronkelijke gegevensbronnen. Bij OneDrive-vernieuwing worden gewoon de resources in Power BI bijgewerkt met de metagegevens en gegevens uit het pbix-, .xlsx- of CSV-bestand, zoals het volgende diagram illustreert. Om ervoor te zorgen dat de gegevensset de meest recente gegevens uit de gegevensbronnen bevat, activeert Power BI ook gegevens vernieuwen als onderdeel van een on-demand vernieuwing. U kunt dit controleren in de **Vernieuwingsgeschiedenis** als u naar het tabblad **Gepland** overschakelt.

![Het diagram voor OneDrive-vernieuwing](media/refresh-data/onedrive-refresh-diagram.png)

Als u OneDrive-vernieuwing ingeschakeld laat voor een met OneDrive of SharePoint Online verbonden gegevensset en u wilt gegevens volgens een schema vernieuwen, zorg er dan voor dat u het schema zo configureert dat in Power BI gegevens vernieuwen pas na OneDrive-vernieuwing wordt uitgevoerd. Als u bijvoorbeeld uw eigen service of proces hebt gemaakt om het bronbestand in OneDrive of SharePoint Online elke nacht om 1 uur bij te werken, kunt u de geplande vernieuwing voor 2:30 uur configureren, zodat Power BI genoeg tijd heeft om OneDrive-vernieuwing te voltooien voordat u begint met gegevens vernieuwen.

#### <a name="refresh-of-query-caches"></a>Het vernieuwen van querycaches

Als uw gegevensset zich op een Premium-capaciteit bevindt, kunt u mogelijk de prestaties van gekoppelde rapporten en dashboards verbeteren door query's in het cachegeheugen opslaan in te schakelen, zoals in de volgende schermopname. Hierbij kan de Premium-capaciteit gebruikmaken van de lokale cacheservice om de queryresultaten op te slaan, zodat de onderliggende gegevensbron deze resultaten niet meer hoeft te berekenen. Zie [Query caching in Power BI Premium](power-bi-query-caching.md) (Query's in cache opslaan in Power BI Premium) voor meer informatie.

![Query's in cache opslaan](media/refresh-data/query-caching.png)

Na het vernieuwen van gegevens zijn eerder in de cache opgeslagen queryresultaten echter niet meer geldig. In Power BI worden deze resultaten in de cache genegeerd en moeten deze opnieuw worden samengesteld. Om deze reden is het in de cache opslaan van query's mogelijk niet zo voordelig voor rapporten en dashboards die zijn gekoppeld aan gegevenssets die u heel vaak vernieuwt, zoals 48 keer per dag.

#### <a name="tile-refresh"></a>Tegels vernieuwen

In Power BI wordt een cache bijgehouden voor elke tegelvisual op uw dashboards en worden de tegelcaches proactief bijgewerkt wanneer gegevens worden gewijzigd. Met andere woorden, tegels vernieuwen gebeurt automatisch na gegevens vernieuwen. Dit geldt voor zowel, geplande als on-demand vernieuwingsbewerkingen. U kunt het vernieuwen van tegels ook afdwingen door **Meer opties** (...) in de rechterbovenhoek van een dashboard te selecteren en vervolgens **Dashboardtegels vernieuwen** te selecteren.

![Dashboardtegels vernieuwen](media/refresh-data/refresh-dashboard-tiles.png)

Omdat dit automatisch gebeurt, kunt u tegels vernieuwen als een intrinsiek gedeelte beschouwen van gegevens vernieuwen. U zult onder andere misschien merken dat vernieuwen langer duurt naarmate het aantal tegels hoger is. De overhead voor tegels vernieuwen kan aanzienlijk zijn.

Standaard wordt in Power BI één cache voor elke tegel bijgehouden, maar als u dynamische beveiliging gebruikt voor het beperken van de toegang tot gegevens op basis van gebruikersrollen, zoals beschreven in het artikel over [beveiliging op rijniveau (RLS) met Power BI](service-admin-rls.md), en vervolgens moet in Power BI een cache worden bijgehouden voor elke rol en elke tegel. Het aantal tegelcaches wordt vermenigvuldigd met het aantal rollen.

De situatie kan zelfs veelomvattender worden als uw gegevensset gebruikmaakt van een liveverbinding met een Analysis Services-gegevensmodel met beveiliging op rijniveau, zoals in de zelfstudie [Dynamic row level security with Analysis services tabular model](desktop-tutorial-row-level-security-onprem-ssas-tabular.md) (Dynamische beveiliging op rijniveau met het Analysis services-model in tabelvorm). In dit geval moet in Power BI een cache worden bijgehouden en vernieuwd voor elke tegel en elke gebruiker die het dashboard heeft bekeken. Het is niet ongebruikelijk dat het gedeelte voor tegels vernieuwen van dergelijke gegevensvernieuwing langer duurt dan de tijd die nodig is voor het ophalen van de gegevens uit de bron. Zie [Troubleshooting tile errors](refresh-troubleshooting-tile-errors.md) (Problemen met tegelfouten oplossen) voor meer informatie over tegels vernieuwen.

#### <a name="refresh-of-report-visuals"></a>Het vernieuwen van rapportvisuals

Dit vernieuwingsproces is minder belangrijk, omdat het alleen relevant is voor liveverbindingen met Analysis Services. De laatste status van rapportvisuals worden in Power BI opgeslagen voor deze verbindingen, zodat het tabellaire Analysis Services-model niet hoeft te worden opgevraagd in Power BI wanneer u het rapport opnieuw bekijkt. Als u interacties uitvoert met het rapport, zoals door het veranderen van een rapportfilter, doorzoekt Power BI het tabellaire model en worden rapportvisuals automatisch bijgewerkt. Als u vermoedt dat in een rapport verouderde gegevens worden weergegeven, kunt u ook de knop Vernieuwen selecteren van het rapport voor het activeren van een vernieuwing van alle rapportvisuals, zoals in de volgende schermopname is te zien.

![Het vernieuwen van rapportvisuals](media/refresh-data/refresh-report-visuals.png)

## <a name="review-data-infrastructure-dependencies"></a>Afhankelijkheden gegevensinfrastructuur controleren

Ongeacht de opslagmodi kunnen geen gegevens worden vernieuwd, tenzij de onderliggende gegevensbronnen toegankelijk zijn. Er zijn drie belangrijke scenario's voor gegevenstoegang:

- Een gegevensset maakt gebruik van gegevensbronnen die zich on-premises bevinden
- Een gegevensset maakt gebruik van gegevensbronnen in de cloud
- Een gegevensset maakt gebruik van zowel on-premises gegevensbronnen als bronnen in de cloud

### <a name="connecting-to-on-premises-data-sources"></a>Verbinding maken met on-premises gegevensbronnen

Als uw gegevensset een gegevensbron gebruikt waartoe Power BI geen toegang kan krijgen via een rechtstreekse netwerkverbinding, moet u een gateway-verbinding voor deze gegevensset configureren voordat u een schema voor gegevensvernieuwing kunt inschakelen of een on-demand gegevensvernieuwing kunt uitvoeren. Zie [Wat zijn on-premises gegevensgateways?](service-gateway-onprem.md) voor meer informatie over gegevensgateways en hoe deze werken

U hebt de volgende opties:

- Een gegevensgateway voor bedrijven kiezen met de vereiste gegevensbrondefinitie
- Een persoonlijke gegevensgateway implementeren

> [!NOTE]
> U vindt een lijst met typen gegevensbronnen waarvoor een gegevensgateway nodig is in het artikel [Uw gegevensbron beheren - importeren/geplande vernieuwing](service-gateway-enterprise-manage-scheduled-refresh.md).

#### <a name="using-an-enterprise-data-gateway"></a>Met behulp van een gegevensgateway voor bedrijven

Microsoft raadt u aan een gegevensgateway voor bedrijven te gebruiken in plaats van een persoonlijke gateway om een gegevensset verbinding te laten maken met een on-premises gegevensbron. Zorg ervoor dat de gateway correct is geconfigureerd, wat betekent dat de gateway over de meest recente updates en alle vereiste gegevensbrondefinities moet beschikken. Een gegevensbrondefinitie voorziet Power BI van de verbindingsgegevens voor een bepaalde bron, zoals verbindingseindpunten, verificatiemodus en referenties. Zie [Uw gegevensbron beheren - importeren/geplande vernieuwing](service-gateway-enterprise-manage-scheduled-refresh.md) voor meer informatie over het beheren van gegevensbronnen op een gateway.

Een gegevensset verbinding te laten maken met een bedrijfsgateway is relatief eenvoudig als u gatewaybeheerder bent. Met beheerdersmachtigingen kunt u de gateway direct bijwerken en ontbrekende gegevensbronnen, indien nodig, toevoegen. U kunt in feite rechtstreeks vanuit de instellingenpagina van de gegevensset een ontbrekende gegevensbron toevoegen aan uw gateway. Vouw de wisselknop uit voor het weergeven van de gegevensbronnen en selecteer de koppeling **Toevoegen aan gateway**, zoals in de volgende schermopname. Als u daarentegen geen gatewaybeheerder bent, moet u contact opnemen met een gatewaybeheerder om de vereiste gegevensbrondefinitie toe te voegen.

> [!NOTE]
> Alleen gatewaybeheerders kunnen gegevensbronnen toevoegen aan een gateway. Zorg er ook voor dat uw gatewaybeheerder uw gebruikersaccount toevoegt aan de lijst met gebruikers met machtigingen voor het gebruik van de gegevensbron. Op de pagina Gegevenssetinstellingen kunt u alleen een bedrijfsgateway selecteren met een overeenkomende gegevensbron waarvoor u toestemming hebt om deze te gebruiken.

![Toevoegen aan gateway](media/refresh-data/add-to-gateway.png)

Zorg ervoor dat u de juiste gegevensbrondefinitie toewijst aan uw gegevensbron. Zoals in de bovenstaande schermafbeelding is te zien, kunnen gatewaybeheerders meerdere definities maken op één gateway die verbinding maken met dezelfde gegevensbron, elk met andere referenties. In het weergegeven voorbeeld kiest de eigenaar van een gegevensset op de verkoopafdeling de gegevensbrondefinitie AdventureWorksProducts-Sales terwijl de eigenaar van een gegevensset van de ondersteuningsafdeling de gegevensset zou toewijzen aan de gegevensbrondefinitie AdventureWorksProducts-Support. Als de namen van de gegevensbrondefinitie niet intuïtief zijn, neemt u contact op met de gatewaybeheerder voor meer informatie over welke definitie u moet kiezen.

> [!NOTE]
> Voor een gegevensset kan alleen een enkele gatewayverbinding wordt gebruikt. Met andere woorden: het is niet mogelijk om toegang tot on-premises gegevensbronnen te krijgen via meerdere gatewayverbindingen. Daarom moet u alle vereiste gegevensbrondefinities aan dezelfde gateway toevoegen.

#### <a name="deploying-a-personal-data-gateway"></a>Een persoonlijke gegevensgateway implementeren

Als u geen toegang tot een gegevensgateway voor bedrijven hebt en u de enige bent die gegevenssets beheert, zodat u geen gegevensbronnen hoeft te delen met anderen, kunt u een gegevensgateway in de persoonlijke modus implementeren. In de sectie **Gatewayverbinding** onder **U hebt geen persoonlijke gateways geïnstalleerd** selecteert u **Nu installeren**. De persoonlijke gegevensgateway heeft ook enkele beperkingen, zoals is beschreven in [On-premises gegevensgateway (persoonlijke modus)](service-gateway-personal-mode.md).

Anders dan bij een gegevensgateway voor bedrijven hoeft u aan een persoonlijke gateway geen gegevensbrondefinities toe te voegen. In plaats daarvan beheert u de configuratie van de gegevensbron met behulp van de sectie **Gegevensbronreferenties** in de instellingen van de gegevensset, zoals in de volgende schermopname is te zien.

![Gegevensbronreferenties configureren voor gateway](media/refresh-data/configure-data-source-credentials-gateway.png)

> [!NOTE]
> De persoonlijke gegevensgateway biedt geen ondersteuning voor gegevenssets in de modus DirectQuery/LiveConnect. U wordt op de instellingspagina van de gegevensset mogelijk gevraagd of u deze wilt installeren, maar als u alleen een persoonlijke gateway hebt, kunt u geen gatewayverbinding configureren. Zorg ervoor dat u hebt een gegevensgateway voor bedrijven hebt ter ondersteuning van deze typen gegevenssets.

### <a name="accessing-cloud-data-sources"></a>Toegang tot gegevensbronnen in de cloud

Gegevenssets die gebruikmaken van gegevensbronnen in de cloud, zoals Azure SQL DB, hebben geen gegevensgateway nodig als Power BI een rechtstreekse netwerkverbinding met de gegevensbron kan maken. Daarom kunt u de configuratie van deze gegevensbronnen beheren met behulp van de sectie **Gegevensbronreferenties** in de instellingen van de gegevensset. Zoals in de volgende schermopname wordt weergegeven, hoeft u geen gateway-verbinding te configureren.

![Gegevensbronreferenties configureren zonder een gateway](media/refresh-data/configure-data-source-credentials.png)

### <a name="accessing-on-premises-and-cloud-sources-in-the-same-source-query"></a>Toegang tot on-premises en cloudbronnen in dezelfde bronquery

Een dataset kan gegevens ophalen uit meerdere bronnen, en deze bronnen kunnen zich on-premises bevinden of in de cloud. Zoals echter eerder vermeld, kan voor een gegevensset alleen een enkele gatewayverbinding worden gebruikt. Terwijl voor gegevensbronnen in de cloud niet per se een gateway is vereist, is wel een gateway vereist als een gegevensset verbinding maakt met zowel on-premises als cloudbronnen in een enkele mashup-query. In dit scenario moet Power BI gebruikmaken van een gateway voor de gegevensbronnen in de cloud. Het volgende diagram illustreert hoe een dergelijke gegevensset toegang krijgt tot de gegevensbronnen.

![Gegevensbronnen in de cloud en on-premises gegevensbronnen](media/refresh-data/cloud-on-premises-data-sources-diagram.png)

> [!NOTE]
> Als een gegevensset gebruikmaakt van afzonderlijke mashup-query's om verbinding te maken met on-premises bronnen en cloudbronnen, maakt Power BI gebruik van een gatewayverbinding om de on-premises bronnen en een rechtstreekse netwerkverbinding met de cloudbronnen te bereiken. Als een mashup-query wordt samengevoegd of gegevens van on-premises en cloudbronnen eraan worden toegevoegd, schakelt Power BI ook voor de cloudbronnen over op de gatewayverbinding.

Power BI-gegevenssets zijn afhankelijk van Power Query om toegang te krijgen tot brongegevens en deze op te halen. In de volgende mashup-vermelding ziet u een eenvoudige voorbeeld van een query waarmee gegevens uit een on-premises bron en een cloudbron worden samengevoegd.

```
Let

    OnPremSource = Sql.Database("on-premises-db", "AdventureWorks"),

    CloudSource = Sql.Databases("cloudsql.database.windows.net", "AdventureWorks"),

    TableData1 = OnPremSource{[Schema="Sales",Item="Customer"]}[Data],

    TableData2 = CloudSource {[Schema="Sales",Item="Customer"]}[Data],

    MergedData = Table.NestedJoin(TableData1, {"BusinessEntityID"}, TableData2, {"BusinessEntityID"}, "MergedData", JoinKind.Inner)

in

    MergedData
```

Er zijn twee opties voor het configureren van een gegevensgateway voor de ondersteuning voor het samenvoegen of toevoegen van gegevens van on-premises bronnen en cloudbronnen:

- Voeg een gegevensbrondefinitie voor de cloudbron toe aan de gegevensgateway naast de on-premises gegevensbronnen.
- Schakel het selectievakje **Toestaan dat de cloudgegevensbronnen van de gebruiker worden vernieuwd via dit gatewaycluster** in.

![Vernieuwen via een gatewaycluster](media/refresh-data/refresh-gateway-cluster.png)

Als u het selectievakje **Toestaan dat de cloudgegevensbronnen van de gebruiker worden vernieuwd via dit gatewaycluster** in de configuratie van de gateway inschakelt, zoals in de bovenstaande schermopname, kan Power BI van de configuratie gebruikmaken die de gebruiker heeft gedefinieerd voor de cloudbron onder **Gegevensbronreferenties** in de instellingen voor de gegevensset. Dit kan helpen om de overhead van de gatewayconfiguratie te verminderen. Als u anderzijds meer controle wilt over de verbindingen die de gateway tot stand brengt, moet u dit selectievakje niet inschakelen. In dit geval moet u een expliciete gegevensbrondefinitie aan uw gateway toevoegen voor elke cloudbron die u wilt ondersteunen. Het is ook mogelijk om het selectievakje in te schakelen en expliciete gegevensbrondefinities voor uw cloudbronnen aan een gateway toe te voegen. In dit geval worden de gegevensbronnendefinities door de gateway gebruikt voor alle overeenkomende bronnen.

### <a name="configuring-query-parameters"></a>Queryparameters configureren

De mashup- of M-query's die u maakt met behulp van Power Query kunnen variëren in complexiteit, van eenvoudige stappen tot geparameteriseerde constructies. In de volgende lijst ziet u een voorbeeld van een kleine mashup-query die gebruikmaakt van twee parameters met de naam _SchemaName_ en _TableName_ om toegang te krijgen tot een bepaalde tabel in een AdventureWorks-database.

```
let

    Source = Sql.Database("SqlServer01", "AdventureWorks"),

    TableData = Source{[Schema=SchemaName,Item=TableName]}[Data]

in

    TableData
```

> [!NOTE]
> Queryparameters worden alleen ondersteund voor gegevenssets in invoermodus. De DirectQuery-/LiveConnect-modus biedt geen ondersteuning voor definities van queryparameters.

Om ervoor te zorgen dat een geparameteriseerde gegevensset toegang heeft tot de juiste gegevens, moet u de parameters van de mashup-query in de instellingen configureren. U kunt ook de parameters bijwerken via een programma met behulp van de [Power BI REST API](/rest/api/power-bi/datasets/updateparametersingroup). In de volgende schermopname ziet u de gebruikersinterface voor het configureren van de queryparameters voor een gegevensset die gebruikmaakt van de bovenstaande mashup-query.

![Queryparameters configureren](media/refresh-data/configure-query-parameters.png)

> [!NOTE]
> Power BI biedt momenteel geen ondersteuning voor geparameteriseerde gegevensbrondefinities, ook wel bekend als dynamische gegevensbronnen. U kunt bijvoorbeeld geen parameters instellen voor de functie voor gegevenstoegang, Sql.Database("SqlServer01", "AdventureWorks"). Als uw gegevensset afhankelijk is van dynamische gegevensbronnen, krijgt u een bericht van Power BI dat onbekende of niet-ondersteunde gegevensbronnen zijn gedetecteerd. U moet de parameters in de gegevenstoegangsfuncties vervangen door statische waarden als u wilt dat Power BI gegevensbronnen kan identificeren en ermee verbinding kan maken. Zie [Troubleshooting unsupported data source for refresh](service-admin-troubleshoot-unsupported-data-source-for-refresh.md) (Probleem met niet-ondersteunde gegevensbron oplossen) voor meer informatie.

## <a name="configure-scheduled-refresh"></a>Geplande vernieuwing configureren

Het tot stand brengen van verbinding tussen Power BI en uw gegevensbronnen is verreweg de meest uitdagende taak bij het configureren van een gegevensvernieuwing. De resterende stappen zijn relatief eenvoudig en omvatten het instellen van het vernieuwingsschema en het inschakelen van meldingen over mislukte vernieuwingen. Zie de instructiegids [Geplande vernieuwing configureren](refresh-scheduled-refresh.md) voor stapsgewijze instructies.

### <a name="setting-a-refresh-schedule"></a>Een schema voor vernieuwing instellen

In de sectie **Geplande vernieuwingen** definieert u de frequentie en de tijdvakken voor het vernieuwen van een gegevensset. Zoals eerder vermeld, kunt u maximaal acht dagelijkse tijdvakken configureren als uw gegevensset zich op gedeelde capaciteit bevindt, of 48 tijdvakken op Power BI Premium. In de volgende schermopname ziet u een vernieuwingsschema op een interval van twaalf uur.

![Geplande vernieuwing configureren](media/refresh-data/configure-scheduled-refresh.png)

Wanneer een vernieuwingsschema is geconfigureerd, verschijnt een bericht op de instellingspagina van de gegevensset over de volgende vernieuwingstijd, zoals in de bovenstaande schermopname te zien is. Als u de gegevens eerder wilt vernieuwen om bijvoorbeeld uw gateway en de configuratie van de gegevensbron te testen, voert u een on-demand vernieuwing uit met behulp van de optie **Nu vernieuwen** in het gegevenssetmenu in het navigatievenster. On-demand vernieuwingen hebben geen invloed op de volgende keer dat een geplande vernieuwing plaatsvindt, maar tellen mee voor de dagelijkse vernieuwingslimiet, zoals eerder in dit artikel is uitgelegd.

Houd er ook rekening mee dat de geconfigureerde vernieuwingstijd mogelijk niet de precieze tijd is wanneer het volgende geplande proces in Power BI wordt gestart. Geplande vernieuwingen worden in Power BI gestart op basis van 'best effort'. Het doel is om de vernieuwing binnen vijftien minuten te starten na het geplande tijdvak, maar er kan zich een vertraging van maximaal één uur voordoen als de service de vereiste resources niet sneller kan toewijzen.

> [!NOTE]
> Uw vernieuwingsschema wordt door Power BI gedeactiveerd na vier achtereenvolgende mislukte pogingen of wanneer een onherstelbare fout in de service wordt gedetecteerd, waarvoor een configuratie-update nodig is, zoals ongeldige of verlopen referenties. Het is niet mogelijk om de drempelwaarde voor opeenvolgende fouten te wijzigen.

### <a name="getting-refresh-failure-notifications"></a>Meldingen over mislukte vernieuwingen krijgen

Standaard krijgt de eigenaar van de gegevensset in Power BI via e-mail meldingen over mislukte vernieuwingen, zodat deze tijdig kan ingrijpen als er problemen met vernieuwen optreden. U krijgt in Power BI ook een melding wanneer uw schema wordt uitgeschakeld door de service vanwege achtereenvolgende mislukte pogingen. Microsoft raadt aan dat u het selectievakje **Meldingsberichten van mislukte vernieuwingen aan mij verzenden** ingeschakeld laat.

Het is ook verstandig om aanvullende geadresseerden op te geven met behulp van het tekstvak **Deze gebruikers e-mailen wanneer het vernieuwen mislukt**. Naast de eigenaar van de gegevensset ontvangen de opgegeven geadresseerden meldingen over fouten met vernieuwen. Dit kan een collega zijn die voor uw gegevenssets zorgt als u op vakantie bent. Het kan ook de e-mailalias van uw ondersteuningsteam zijn, dat problemen met vernieuwen afhandelt voor uw afdeling of organisatie. Het is nuttig om meldingen over fouten met vernieuwen niet alleen naar de eigenaar van de gegevensset maar ook naar anderen te sturen om ervoor te zorgen dat problemen tijdig worden opgemerkt en opgelost.

Houd er rekening mee dat in Power BI niet alleen meldingen worden verzonden van mislukte vernieuwingen, maar ook als een geplande vernieuwing vanwege inactiviteit in de service wordt onderbroken. Als de dasboards en rapporten die op basis van de gegevensset zijn samengesteld gedurende twee maanden niet door gebruikers zijn bezocht, wordt de gegevensset beschouwd als inactief. In dit geval wordt in Power BI een e-mailbericht verzonden naar de eigenaar van de gegevensset waarin wordt aangegeven dat het vernieuwingsschema voor de gegevensset door de service is onderbroken. Zie de volgende schermopname voor een voorbeeld van een dergelijke melding.

![E-mailbericht voor onderbroken vernieuwing](media/refresh-data/email-paused-refresh.png)

Voor het hervatten van een geplande vernieuwing gaat u naar een rapport of dashboard dat met behulp van deze gegevensset is gemaakt of vernieuwt u de gegevensset handmatig met behulp van de optie **Nu vernieuwen**.

### <a name="checking-refresh-status-and-history"></a>Vernieuwingsstatus en -geschiedenis controleren

Naast meldingen over mislukte vernieuwingen is het een goed idee om uw gegevenssets regelmatig te controleren op fouten bij het vernieuwen. Een snelle manier is het bekijken van de lijst met gegevenssets in een werkruimte. Bij gegevenssets met fouten is een klein waarschuwingspictogram te zien. U kunt het waarschuwingspictogram selecteren voor aanvullende informatie, zoals in de volgende schermopname te zien is. Zie [Problemen met vernieuwingsscenario's oplossen](refresh-troubleshooting-refresh-scenarios.md) voor meer informatie over het oplossen van specifieke fouten bij vernieuwingen.

![Waarschuwing bij vernieuwingsstatus](media/refresh-data/refresh-status-warning.png)

Met het waarschuwingspictogram worden de huidige problemen van de gegevensset aangegeven, maar het is ook een goed idee om af en toe de vernieuwingsgeschiedenis te controleren. Zoals de naam al aangeeft, kunt u met de vernieuwingsgeschiedenis de slagings- of mislukkingsstatus van de laatste synchronisatiecycli controleren. Het kan bijvoorbeeld zijn dat de gatewaybeheerder een verlopen set databasereferenties heeft bijgewerkt. Zoals u in de volgende schermopname ziet, geeft de vernieuwingsgeschiedenis weer wanneer een betrokken vernieuwing weer zijn gaan werken.

![Berichten vernieuwingsgeschiedenis](media/refresh-data/refresh-history-messages.png)

> [!NOTE]
> Hier vindt u een koppeling om de vernieuwingsgeschiedenis in de gegevenssetinstellingen weer te geven. U kunt ook de vernieuwingsgeschiedenis ophalen via een programma met behulp van de [Power BI REST API](/rest/api/power-bi/datasets/getrefreshhistoryingroup). U kunt de vernieuwingsgeschiedenis van meerdere gegevenssets centraal controleren met behulp van een aangepaste oplossing.

## <a name="automatic-page-refresh"></a>Pagina automatisch vernieuwen

Het automatisch vernieuwen van pagina's werkt op het niveau van rapportpagina's en stelt ontwerpers in staat om een vernieuwingsinterval voor visuele elementen in te stellen op een pagina die alleen actief is wanneer de pagina wordt gebruikt. Het automatisch vernieuwen van pagina's is alleen beschikbaar voor gegevensbronnen van DirectQuery. Het minimale vernieuwingsinterval is afhankelijk van het type werkruimte waarin het rapport is gepubliceerd en de instellingen van capaciteitsbeheerders voor Premium-werkruimten.

Meer informatie over het automatisch vernieuwen van pagina's vindt u in het artikel over [automatisch pagina's vernieuwen ](desktop-automatic-page-refresh.md).


## <a name="best-practices"></a>Aanbevolen procedures

Een regelmatige controle van de vernieuwingsgeschiedenis van uw gegevenssets is een van de belangrijkste aanbevolen procedures die u kunt u instellen om ervoor te zorgen dat uw rapporten en dashboards van de actuele gegevens gebruikmaken. Als u problemen detecteren, lost u deze direct op en neemt u vervolgmaatregelen met eigenaars van gegevensbronnen en gatewaybeheerders, indien nodig.

Bovendien kunt u de volgende aanbevelingen overwegen voor het maken en onderhouden van betrouwbare processen voor het vernieuwen van gegevens voor uw gegevenssets:

- Plan uw vernieuwingen voor minder drukke tijden, met name als uw gegevenssets zich in Power BI Premium bevinden. Als u de vernieuwingscycli voor uw gegevenssets over een bredere tijdvenster verdeelt, kunt u helpen om pieken te voorkomen waardoor anders beschikbare resources kunnen worden overbelast. Vertragingen bij het starten van een vernieuwingscyclus zijn een indicatie van overbelasting van resources. Als een Premium capaciteit volledig is uitgeput, kan Power BI een vernieuwingscyclus zelfs overslaan.
- Houd rekening met de vernieuwingslimieten. Als de brongegevens regelmatig worden gewijzigd of het gegevensvolume aanzienlijk is, kunt u de modus DirectQuery/LiveConnect gebruiken in plaats van de importmodus, als de toegenomen belasting op de bron en de impact op de prestaties van query's aanvaardbaar zijn. Voorkom dat gegevenssets in de importmodus voortdurend worden vernieuwd. De modus DirectQuery/LiveConnect heeft echter enkele beperkingen, zoals een limiet van één miljoen rijen voor het retourneren van gegevens en een tijdslimiet van 225 seconden om te antwoorden voor het uitvoeren van query's, zoals is beschreven in [DirectQuery gebruiken in Power BI Desktop](desktop-use-directquery.md). Vanwege deze beperkingen moet u mogelijk toch de importmodus gebruiken. Voor zeer grote gegevensvolumes kunt u overwegen om [aggregaties te gebruiken in Power BI](desktop-aggregations.md).
- Controleer of de vernieuwingstijd van uw gegevensset niet de maximale vernieuwingsduur overschrijdt. Gebruik Power BI Desktop om de duur van de vernieuwing te controleren. Als het meer dan 2 uur duurt, kunt u uw gegevensset naar Power BI Premium overplaatsen. Uw gegevensset kan mogelijk niet worden vernieuwd in gedeelde capaciteit. Ook kunt u overwegen om gegevenssets die groter zijn dan 1 GB [incrementeel te vernieuwen in Power BI Premium](service-premium-incremental-refresh.md), anders duurt het meerdere uren om deze te vernieuwen.
- Optimaliseer uw gegevenssets door alleen de tabellen en kolommen op te nemen waarvan uw rapporten en dashboards gebruikmaken. Optimaliseer uw mashup-query's en vermijd, indien mogelijk, dynamische gegevensbrondefinities en dure DAX-berekeningen. Vermijd vooral DAX-functies die elke rij in een tabel testen vanwege het hoge geheugenverbruik en de overhead van de verwerking.
- Pas dezelfde privacyinstellingen toe als in Power BI Desktop om ervoor te zorgen dat u met Power BI efficiënte bronquery's kunt genereren. Houd er rekening mee dat de privacy-instellingen niet worden gepubliceerd in Power BI Desktop. U moet na het publiceren van uw gegevensset handmatig de instellingen in de gegevensbrondefinities opnieuw toepassen.
- Beperk het aantal visuals op uw dashboards, met name als u [beveiliging op rijniveau (RLS)](service-admin-rls.md) gebruikt. Zoals eerder in dit artikel wordt uitgelegd, kan bij een uitzonderlijk groot aantal dashboardtegels de duur van de vernieuwing aanzienlijk langer worden.
- Gebruik een betrouwbare implementatie van de gegevensgateway voor bedrijven om uw gegevenssets met on-premises gegevensbronnen verbinden. Als u merkt vernieuwingsfouten die te maken hebben met de gateway, bijvoorbeeld dat de gateway niet beschikbaar of overbelast is, moet u contact opnemen met gatewaybeheerders om extra gateways aan een bestaand cluster toe te voegen of om een nieuw cluster te implementeren (omhoog schalen versus uitbreiden).
- Gebruik afzonderlijke gateways voor gegevenssets in importmodus en gegevenssets in de modusDirectQuery/LiveConnect, zodat het importeren van gegevens tijdens de geplande vernieuwing niet van invloed is op de uitvoering van rapporten en dashboards naast de gegevenssets in de modus DirectQuery/LiveConnect, die de gegevensbronnen opvragen met elke gebruikersinteractie.
- Zorg ervoor dat meldingen van Power BI over mislukte vernieuwingen naar uw postvak kunnen worden verzonden. Spamfilters kunnen de e-mailberichten blokkeren of deze naar een afzonderlijke map verplaatsen waar u ze mogelijk niet onmiddellijk opmerkt.


## <a name="next-steps"></a>Volgende stappen

[Geplande vernieuwing configureren](refresh-scheduled-refresh.md)  
[Problemen oplossen met on-premises gateway](service-gateway-onprem-tshoot.md)  
[Problemen met vernieuwingsscenario's oplossen](refresh-troubleshooting-refresh-scenarios.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
