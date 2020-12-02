---
title: BI-oplossingsarchitectuur in de COE (Center of Excellence)
description: Meer informatie over wat u moet overwegen bij het ontwerpen en ontwikkelen van een robuust BI-platform.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: 88d1e19435207ca094bd9cb1cba770c1cb54573f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394630"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>BI-oplossingsarchitectuur in de COE (Center of Excellence)

Dit artikel is gericht op IT-professionals en IT-beheerders. Meer informatie over de BI-oplossingsarchitectuur vindt u in de COE en de verschillende gebruikte technologieën. Voorbeelden van technologieën zijn Azure, Power BI en Excel. Samen kunnen ze worden gebruikt voor het leveren van een schaalbaar en gegevensgestuurd BI-platform in de cloud.

Het ontwerpen van een robuust BI-platform is vergelijkbaar met het bouwen van een brug: een brug die getransformeerde en verrijkte brongegevens verbindt met gegevensgebruikers. Voor het ontwerp van een dergelijke complexe structuur is een technische instelling vereist, maar dit kan een van de meest creatieve en belonende IT-architecturen zijn die u zou kunnen ontwerpen. In een grote organisatie kan een BI-oplossingsarchitectuur bestaan uit:

- Gegevensbronnen
- Gegevensopname
- Big data-/gegevensvoorbereiding
- Datawarehouse
- Semantische BI-modellen (BISM)
- Rapporten

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="Een diagram met de BI-platformarchitectuur, van gegevensbronnen tot gegevensopname, big data, opslag, datawarehouse, semantische BI-modellen, rapportage en machine learning.":::

Het platform moet specifieke vereisten ondersteunen. In het bijzonder moet het schaalbaar zijn en voldoen aan de verwachtingen van gebruikers van zakelijke services en gegevens. Tegelijk moet het compleet zijn beveiligd. En het moet voldoende tolerant zijn om zich aan te passen aan veranderingen, omdat het een zekerheid is dat mettertijd nieuwe gegevens en onderwerpen online moeten worden gebracht.

## <a name="frameworks"></a>Frameworks

Bij Microsoft hebben we vanaf het begin een systematische aanpak toegepast door te investeren in de ontwikkeling van frameworks. Frameworks voor technische en zakelijk processen verhogen het hergebruik van ontwerp en logica en bieden een consistent resultaat. Ze bieden ook flexibiliteit in architectuur waarin veel technologieën zijn gebruikt en ze stroomlijnen en verminderen de technische overhead dankzij herhaalbare processen.

We hebben geleerd dat goed ontworpen frameworks meer zicht bieden op de herkomst van gegevens, impactanalyse, onderhoud van bedrijfslogica, beheer van de taxonomie en het stroomlijnen van governance. De ontwikkeling is ook sneller verlopen en de samenwerking tussen grote teams zijn responsiever en effectiever geworden.

In dit artikel worden verschillende frameworks beschreven.

## <a name="data-models"></a>Gegevensmodellen

Gegevensmodellen bieden u controle op de manier waarop gegevens worden gestructureerd en geopend. Voor gebruikers van zakelijke services en gegevens zijn gegevensmodellen hun interface met het BI-platform.

Een BI-platform kan voorzien in drie verschillende typen modellen:

- Bedrijfsmodellen
- Semantische BI-modellen (BISM)
- ML-modellen (Machine Learning)

### <a name="enterprise-models"></a>Bedrijfsmodellen

**Bedrijfsmodellen** worden gebouwd en onderhouden door IT-architecten. Ze worden soms dimensionale modellen of datamarts genoemd. Normaal gesproken worden gegevens opgeslagen in relationele indeling als dimensie- en feitentabellen. Deze tabellen bevatten opgeschoonde en verrijkte gegevens die zijn geconsolideerd uit veel systemen. Deze vormen een gezaghebbende bron voor rapportage en analyse.

Bedrijfsmodellen bieden een consistente en enkelvoudige gegevensbron voor rapportage en BI. Ze zijn eenmalig gebouwd en gedeeld als bedrijfsstandaard. Governancebeleid zorgt ervoor dat de gegevens veilig zijn, zodat toegang tot gevoelige gegevenssets, zoals klantgegevens of financiële gegevens, op basis van de behoeften wordt beperkt. Ze nemen naamconventies aan die consistentie garanderen, waardoor gegevens en kwaliteit aan geloofwaardigheid winnen.

In een BI-platform in de cloud kunnen bedrijfsmodellen worden geïmplementeerd in een [Synapse SQL-pool in Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). De Synapse SQL-pool wordt vervolgens de enige versie van de waarheid waarop de organisatie kan rekenen voor snelle en robuuste inzichten.

### <a name="bi-semantic-models"></a>Semantische BI-modellen (BISM)

**Semantische BI-modellen** vormen een semantische laag over bedrijfsmodellen. Ze zijn gemaakt en onderhouden door BI-ontwikkelaars en zakelijke gebruikers. BI-ontwikkelaars maken semantische BI-basismodellen die gegevens halen uit bedrijfsmodellen. Zakelijke gebruikers kunnen onafhankelijke modellen op kleinere schaal maken of ze kunnen semantische BI-basismodellen uitbreiden met afdelingsbronnen of externe bronnen. Semantische BI-modellen zijn doorgaans gericht op één onderwerpgebied en worden vaak op grote schaal gedeeld.

Zakelijke mogelijkheden worden niet alleen door gegevens mogelijk gemaakt, maar ook door semantische BI-modellen waarin concepten, relaties, regels en standaarden worden beschreven. Op deze manier vertegenwoordigen ze intuïtieve en eenvoudig te begrijpen structuren waarmee gegevensrelaties worden gedefinieerd en bedrijfsregels als berekeningen worden ingebouwd. Ze kunnen ook gedetailleerde machtigingen voor gegevens afdwingen, zodat de juiste mensen toegang hebben tot de juiste gegevens. Belangrijk is dat ze de queryprestaties versnellen, waardoor er uiterst responsieve, interactieve analyses worden geboden, zelfs van meer dan terabytes aan gegevens. Net als bij bedrijfsmodellen gebruiken semantische BI-modellen naamconventies die consistentie garanderen.

In een BI-platform in de cloud kunnen BI-ontwikkelaars semantische BI-modellen implementeren in [Azure Analysis Services](/azure/analysis-services/)- of [Power BI Premium-capaciteiten](../admin/service-premium-what-is.md#reserved-capacities). U wordt aangeraden om deze te implementeren in Power BI wanneer deze wordt gebruikt als uw rapportage- en analyselaag. Deze producten ondersteunen verschillende opslagmodi, waardoor tabellen van gegevensmodellen hun gegevens in de cache kunnen opslaan of [DirectQuery](directquery-model-guidance.md) kunnen gebruiken. Dit is een technologie die query's doorgeeft aan de onderliggende gegevensbron. DirectQuery is een ideale opslagmodus wanneer modeltabellen uit grote hoeveelheden gegevens bestaan of wanneer er bijna realtime resultaten moeten worden geleverd. De twee opslagmodi kunnen worden gecombineerd: [Samengestelde modellen](composite-model-guidance.md) combineren tabellen die gebruikmaken van verschillende opslagmodi in één model.

Voor veelvuldig opgevraagde modellen kan [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) worden gebruikt om de querybelasting gelijkmatig te verdelen over modelreplica's. Daarnaast kunt u de schaal van uw toepassingen aanpassen en maximaal beschikbare semantische BI-modellen maken.

### <a name="machine-learning-models"></a>Machine Learning-modellen

[**Machine Learning (ML)-modellen**](/windows/ai/windows-ml/what-is-a-machine-learning-model) worden gemaakt en onderhouden door gegevenswetenschappers. Ze zijn voornamelijk ontwikkeld op basis van onbewerkte bronnen in de data Lake.

Getrainde ML-modellen kunnen patronen in uw gegevens onthullen. In veel gevallen kunnen deze patronen worden gebruikt voor het maken van voorspellingen die kunnen worden gebruikt om gegevens te verrijken. Aankoopgedrag kan bijvoorbeeld worden gebruikt om klantverloop of segmentklanten te voorspellen. U kunt voorspellingsresultaten toevoegen aan bedrijfsmodellen om analyses per klantsegment mogelijk te maken.

In een BI-platform in de cloud kunt u [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) gebruiken om ML-modellen te trainen, te implementeren, te automatiseren, te beheren en bij te houden.

## <a name="data-warehouse"></a>Datawarehouse

De kern van een BI-platform is de datawarehouse, die als host fungeert voor uw bedrijfsmodellen. Het is een bron van goedgekeurde gegevens, als een systeem van records en als hub, dat dienst doet voor bedrijfsmodellen ten behoeve van rapportage, BI en gegevenswetenschap.

Veel zakelijke services, waaronder LOB-toepassingen (Line-of-Business), kunnen rekenen op het datawarehouse als gezaghebbende en beheerde bron van bedrijfskennis.

Bij Microsoft wordt onze datawarehouse gehost op [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) en Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="Een afbeelding toont Azure Synapse Analytics dat verbinding heeft met Azure Data Lake Storage Gen2.":::

- **ADLS Gen2** maakt van Azure Storage de basis voor het bouwen van zakelijke data lakes op Azure. Het is bedoeld om te voorzien in meerdere petabytes aan informatie, terwijl er honderden gigabits aan doorvoer worden ondersteund. Bovendien biedt het goedkope opslagcapaciteit en -transacties. Daarnaast biedt het ondersteuning voor Hadoop-compatibele toegang waarmee u gegevens op dezelfde manier kunt beheren en openen als met een Hadoop Distributed File System (HDFS). [Azure HDInsight](/azure/hdinsight/), [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) en Azure Synapse Analytics hebben in feite alle toegang tot gegevens die zijn opgeslagen in ADLS Gen2. Het is dus een goede keuze om onbewerkte brongegevens, semi-verwerkte of gefaseerde gegevens en productie-klare gegevens in een BI-platform op te slaan. We gebruiken het om al onze bedrijfsgegevens op te slaan.
- **Azure Synapse Analytics** is een analyseservice die datawarehousing voor ondernemingen en big data-analyses combineert. Deze geeft u de vrijheid om op schaal gegevens op te vragen over uw voorwaarden, met behulp van serverloze on-demand of ingerichte resources. Synapse SQL, een onderdeel van Azure Synapse Analytics, biedt ondersteuning voor volledige op T-SQL gebaseerde analyses. Het is dus ideaal voor het hosten van bedrijfsmodellen die bestaan uit uw dimensie- en feitentabellen. Tabellen kunnen efficiënt worden geladen vanuit ADLS Gen2 met behulp van eenvoudige [Polybase T-SQL-](/sql/relational-databases/polybase/polybase-guide)-query's. U hebt vervolgens het vermogen van [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) voor het uitvoeren van hoogwaardige analyses.

### <a name="business-rules-engine-framework"></a>Framework bedrijfsregelengine

We hebben een BRE-Framework (**Business Rules engine**) ontwikkeld voor het catalogiseren van bedrijfslogica die in de datawarehouselaag kan worden geïmplementeerd. Een BRE kan veel dingen betekenen, maar in de context van een datawarehouse is het handig voor het maken van berekende kolommen in relationele tabellen. Deze berekende kolommen worden meestal weergegeven als wiskundige berekeningen of expressies met behulp van voorwaardelijke instructies.

De bedoeling is om bedrijfslogica te splitsen van de BI-basiscode. Normaal gesproken worden bedrijfsregels vastgelegd in-procedures die zijn opgeslagen in SQL, waardoor het vaak veel moeite kost om ze te onderhouden wanneer de bedrijfsbehoeften veranderen. In een BRE worden bedrijfsregels eenmalig gedefinieerd en meermaals gebruikt wanneer ze worden toegepast op verschillende datawarehouse-entiteiten. Als de berekeningslogica moet worden gewijzigd, hoeft deze alleen op één plek te worden bijgewerkt en niet in talloze opgeslagen procedures. Er is ook een bijkomend voordeel: een BRE-framework biedt meer transparantie en inzicht in geïmplementeerde bedrijfslogica, die kan worden weergegeven via een set rapporten waarmee documentatie voor het automatisch bijwerken wordt gemaakt.

## <a name="data-sources"></a>Gegevensbronnen

Een datawarehouse kan gegevens uit vrijwel elke gegevensbron consolideren. Het is voornamelijk gebaseerd op LOB-gegevensbronnen, die vaak relationele databases zijn waarin onderwerpspecifieke gegevens worden opgeslagen voor verkoop, marketing, financiën, enzovoort. Deze databases kunnen worden gehost in de cloud of kunnen zich on-premises bevinden. Andere gegevensbronnen kunnen op bestanden zijn gebaseerd, met name weblogboeken of IOT-gegevens die afkomstig zijn van apparaten. Er kunnen bovendien gegevens worden geput van SaaS-leveranciers (Software-as-a-Service).

Bij Microsoft worden de operationele gegevens rechtstreeks uit een aantal van onze interne systemen in onbewerkte bestandsindelingen naar ADLS Gen2 overgebracht. Naast onze data lake bestaan andere bronsystemen uit relationele LOB-toepassingen, Excel-werkmappen, andere op bestanden gebaseerde bronnen en opslagplaatsen voor beheer van hoofdgegevens (MDM) en aangepaste gegevens. Met MDM-opslagplaatsen kunnen we onze hoofdgegevens beheren, zodat de gezaghebbende, gestandaardiseerde en gevalideerde versies van gegevens zijn gewaarborgd.

## <a name="data-ingestion"></a>Gegevensopname

Op periodieke basis en volgens de ritmiek van het bedrijf worden gegevens uit de bronsystemen opgenomen en in het datawarehouse geladen. Dit kan één keer per dag of vaker worden uitgevoerd. Gegevensopname vindt plaats bij het extraheren, transformeren en laden van gegevens. Mogelijk kan dit ook in omgekeerde richting: gegevens extraheren, laden en vervolgens transformeren. Het verschil zit in de locatie waar de transformatie plaatsvindt. Transformaties worden toegepast om gegevens op te schonen, te conformeren, te integreren en te standaardiseren. Zie [Extraheren, transformeren en laden (ETL)](/azure/architecture/data-guide/relational-data/etl) voor meer informatie.

Uiteindelijk is het doel om de juiste gegevens zo snel en efficiënt mogelijk in uw bedrijfsmodel te laden.

Bij Microsoft gebruiken we [Azure Data Factory](/azure/data-factory/introduction) (ADF). De services worden gebruikt voor het plannen en organiseren van validaties, transformaties en bulksgewijs laden van gegevens uit externe bronsystemen in onze data lake. Dit wordt beheerd door aangepaste frameworks om gegevens parallel en op schaal te verwerken. Daarnaast wordt een uitgebreide logboekregistratie uitgevoerd ter ondersteuning van probleemoplossing, het controleren van de prestaties en het activeren van waarschuwingsmeldingen wanneer aan bepaalde voorwaarden wordt voldaan.

Ondertussen worden in [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks), een op Apache Spark gebaseerd analyseplatform dat is geoptimaliseerd voor het Azure Cloud Services-platform, transformaties uitgevoerd speciaal voor gegevenswetenschap. Daarnaast worden ML-modellen ontwikkeld en uitgevoerd met behulp van Python-notebooks. Scores uit deze ML-modellen worden in de datawarehouse geladen om voorspellingen te integreren met bedrijfstoepassingen en -rapporten. Omdat Azure Databricks de data lake-bestanden rechtstreeks opent, is er (bijna) geen noodzaak om gegevens te kopiëren of te verkrijgen.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="Een afbeelding toont hoe in Azure Data Factory gegevens worden verkregen en gegevenspijplijnen worden georganiseerd met Azure Databricks via Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Opnameframework

Er is een **opnameframework** ontwikkeld als een reeks configuratietabellen en -procedures. Dit ondersteunt een gegevensgestuurde benadering om op hoge snelheid grote hoeveelheden gegevens te verkrijgen, en met minimale code. Kortom, dit framework vereenvoudigt het proces van gegevensverwerving voor het laden van de datawarehouse.

Het framework is afhankelijk van configuratietabellen waarop informatie over gegevensbrongegevens en bestemmingsgerelateerde gegevens worden opgeslagen, zoals brontype, server, database, schema en tabelgerelateerde informatie. Deze ontwerpbenadering houdt in dat we geen specifieke ADF-pijplijnen of [SSIS-pakketten (SQL Server Integration Services)](/sql/integration-services/sql-server-integration-services) hoeven te ontwikkelen. In plaats daarvan worden procedures geschreven in de taal van onze keuze om ADF-pijplijnen te maken die dynamisch worden gegenereerd en uitgevoerd tijdens de uitvoering. Het ophalen van gegevens wordt dus een configuratie-oefening die eenvoudig operationeel kan worden gemaakt. Normaal gesproken zijn er uitgebreide ontwikkelingsbronnen nodig voor het maken van in code vastgelegde ADF-of SSIS-pakketten.

Het opnameframework is zo ontworpen dat het proces van het verwerken van upstream wijzigingen in het bronschema ook wordt vereenvoudigd. Het is eenvoudig om configuratiegegevens handmatig of automatisch bij te werken wanneer er schemawijzigingen worden gedetecteerd voor het verkrijgen van onlangs toegevoegde kenmerken in het bronsysteem.

### <a name="orchestration-framework"></a>Indelingsframework

We hebben een **indelingsframework** ontwikkeld om onze gegevenspijplijnen operationeel te maken en te organiseren. Hierin wordt gebruikgemaakt van een gegevensgestuurd ontwerp dat afhankelijk is van een reeks configuratietabellen. Deze tabellen slaan metagegevens op die afhankelijkheden van pijplijnen beschrijven en de wijze waarop brongegevens worden toegewezen aan doelgegevensstructuren. De investering in het ontwikkelen van dit adaptieve framework heeft zichzelf sindsdien uitbetaald. Het is niet meer nodig om elke gegevensverplaatsing in code vast te leggen.

## <a name="data-storage"></a>Gegevensopslag

Met een data lake kunt u grote hoeveelheden onbewerkte gegevens opslaan voor later gebruik en transformaties van gegevens faseren.

Bij Microsoft gebruiken we ADLS Gen2 als onze enige bron van waarheid. Er worden naast gefaseerde gegevens en voor productie geschikte gegevens onbewerkte gegevens opgeslagen. Dit biedt een zeer schaalbare en rendabele data lake-oplossing voor de analyse van big data. Door de combinatie met het vermogen van een hoogwaardig, uiterst grootschalig bestandssysteem, is deze oplossing optimaal voor gegevensanalyseworkloads, zodat inzichten sneller voorhanden zijn.

ADLS Gen2 biedt het beste van twee werelden: het biedt BLOB-opslag en naamruimte voor een hoogwaardig bestandssysteem, die we configureren met verfijnde toegangsmachtigingen.

Verfijnde gegevens worden vervolgens opgeslagen in een relationele database om een hoogwaardige, zeer schaalbare gegevensopslag te bieden voor bedrijfsmodellen, voorzien van beveiliging, governance en beheersbaarheid. Onderwerpspecifieke datamarts worden opgeslagen in Azure Synapse Analytics, die worden geladen door Azure Databricks of Polybase T-SQL-query's.

## <a name="data-consumption"></a>Gegevensverbruik

Op de rapportagelaag gebruiken bedrijfsservices bedrijfsgegevens die afkomstig zijn uit de datawarehouse. Ze kunnen ook rechtstreeks toegang krijgen tot gegevens in de data lake voor een ad-hoc analyse of voor taken ten aanzien van de gegevenswetenschap.

Fijnmazige machtigingen zijn op alle lagen doorgevoerd: in de data lake, bedrijfsmodellen en semantische BI-modellen. De machtigingen zorgen ervoor dat gegevensgebruikers alleen de gegevens kunnen zien waartoe ze toegang hebben.

Bij Microsoft maken we gebruik van Power BI-rapporten en -dashboards en [gepagineerde rapporten in Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md). Sommige rapporten en ad-hoc analyses worden uitgevoerd in Excel, met name bij financiële rapportage.

We publiceren gegevenswoordenboeken, die naslaginformatie over onze gegevensmodellen bieden. Ze worden beschikbaar gesteld aan onze gebruikers, zodat ze informatie kunnen krijgen over ons BI-platform. In woordenlijsten worden ontwerpen van modellen gedocumenteerd, met beschrijvingen van entiteiten, indelingen, structuur, gegevensherkomst, relaties en berekeningen. We gebruiken [Azure Data Catalog](/azure/data-catalog/overview) om ervoor te zorgen dat onze gegevensbronnen gemakkelijk kunnen worden gedetecteerd en begrijpelijk zijn.

Patronen van gegevensverbruik variëren doorgaans op basis van de rol:

- **Gegevensanalisten** maken rechtstreeks verbinding met de semantische BI-basismodellen. Wanneer semantische BI-basismodellen alle gegevens en logica bevatten die ze nodig hebben, gebruiken ze live-verbindingen om Power BI-rapporten en -dashboards te maken. Wanneer de modellen moeten worden uitgebreid met afdelingsgegevens, maken ze [samengestelde Power BI-modellen](composite-model-guidance.md). Als er rapporten nodig zijn in werkbladstijl, gebruiken ze Excel om rapporten te produceren op basis van semantische BI-basismodellen of semantische BI-modellen voor afdelingen.
- **BI-ontwikkelaars** en auteurs van operationele rapporten maken rechtstreeks verbinding met bedrijfsmodellen. Ze gebruiken Power BI Desktop voor het maken van analyserapporten met een live-verbinding. Ze kunnen ook BI-rapporten van een operationeel type opstellen als gepagineerde Power BI-rapporten, systeemeigen SQL-query's schrijven om toegang te krijgen tot gegevens uit de Azure Synapse Analytics-bedrijfsmodellen (met behulp van T-SQL) of semantische Power BI-modellen (met behulp van DAX of MDX).
- **Gegevenswetenschappers** maken rechtstreeks verbinding met gegevens in de data lake. Ze maken gebruik van Azure Databricks en Python-notebooks voor het ontwikkelen van ML-modellen, die vaak experimenteel zijn en speciale vaardigheden vereisen voor productiegebruik.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Een afbeelding toont het gebruik van Azure Synapse Analytics met Power BI, Excel en Azure Machine Learning.":::

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Enterprise BI in Azure met Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

### <a name="professional-services"></a>Professionele services

Gecertificeerde Power BI-partners zijn beschikbaar om uw organisatie te helpen slagen met het instellen van een COE. Ze kunnen u een kosteneffectieve training of een audit van uw gegevens bieden. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).

U kunt ook contact opnemen met ervaren adviespartners. Ze kunnen u helpen bij het [beoordelen](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evalueren](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) of [implementeren](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) van Power BI.
