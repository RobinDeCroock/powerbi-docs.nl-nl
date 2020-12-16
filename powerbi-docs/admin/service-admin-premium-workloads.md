---
title: Workloads configureren in Power BI Premium
description: Ontdek hoe u workloads kunt configureren in een Power BI Premium-capaciteit.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 04340be9c7e3700630657306093e3d96e3e9e693
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491409"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Workloads configureren in een Premium-capaciteit

In dit artikel wordt het inschakelen en configureren van workloads voor Power BI Premium-capaciteiten beschreven. Standaard bieden capaciteiten alleen ondersteuning voor de workload die aan het uitvoeren van Power BI-query's is gekoppeld. U kunt ook extra workloads inschakelen en configureren voor **[AI (Cognitive Services)](../transform-model/dataflows/dataflows-machine-learning-integration.md)** , **[gegevensstromen](../transform-model/dataflows/dataflows-introduction-self-service.md)** en **[gepagineerde rapporten](../paginated-reports/paginated-reports-save-to-power-bi-service.md)** .

> [!NOTE]
> Power BI Premium heeft onlangs een nieuwe versie van Premium uitgebracht, genaamd **Premium Gen2**, die momenteel beschikbaar is als preview. Premium Gen2 vereenvoudigt het beheer van Premium-capaciteiten en vermindert de overhead voor beheer. Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie.

## <a name="default-memory-settings"></a>Standaardinstellingen voor geheugen

Queryworkloads zijn geoptimaliseerd voor en beperkt door de resources die voor uw Premium-capaciteit-SKU zijn vastgesteld. Premium-capaciteiten bieden bovendien ondersteuning voor extra workloads die de resources van uw capaciteit kunnen gebruiken. De standaardgeheugenwaarden voor deze workloads zijn gebaseerd op de capaciteitsknooppunten die voor uw SKU beschikbaar zijn. De maximale geheugeninstellingen zijn niet cumulatief. 


|                       | EM1 / A1                  | EM2 / A2                  | EM3 / A3                  | P1 / A4                  | P2 / A5                  | P3 / A6                   |
|-----------------------|---------------------------|---------------------------|---------------------------|--------------------------|--------------------------|---------------------------|
| **AI**                | Niet ondersteund               | Standaard 40%, minimaal 40%  | Standaard 20%; minimaal 20%  | standaard 20%; minimaal 8%  | standaard 20%; minimaal 4%  | standaard 20%; minimaal 2%   |
| **Gegevenssets**          | Standaard 100%; minimaal 67% | Standaard 100%; minimaal 40% | Standaard 100%; minimaal 20% | Standaard 100%; minimaal 8% | Standaard 100%; minimaal 4% | Standaard 100%; minimaal 2%  |
| **Gegevensstromen**         | Standaard 40%, minimaal 40%  | Standaard 24%, minimaal 24%  | Standaard 20%, minimaal 12%  | standaard 20%; minimaal 5%  | Standaard 20%, minimaal 3%  | standaard 20%; minimaal 2%   |
| **Gepagineerde rapporten** | Niet ondersteund               | Niet ondersteund               | Niet ondersteund               | standaard 20%; minimaal 10% | standaard 20%; minimaal 5%  | standaard 20%; minimaal 2,5% |

> [!NOTE]
> Voor **Premium Gen2**, die momenteel als preview-versie beschikbaar is, hoeven geen geheugeninstellingen te worden gewijzigd. Het geheugen in Premium Gen2 wordt automatisch beheerd door het onderliggende systeem. 


## <a name="workload-settings"></a>Workloadinstellingen

In de volgende secties vindt u informatie over de instellingen voor de werkbelasting die in de vorige tabel zijn beschreven. 

### <a name="ai-preview"></a>AI (preview)

Met de AI-workload kunt u cognitive services en automatische Machine Learning in Power BI gebruiken. Gebruik de volgende instellingen om het gedrag van workloads te beheren.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door AI-processen in een capaciteit kan worden gebruikt. |
| **Gebruik via Power BI Desktop toestaan** | Deze instelling is gereserveerd voor toekomstig gebruik en wordt niet in alle tenants weergegeven. |
| **Het bouwen van Machine Learning-modellen toestaan** | Hiermee geeft u aan of bedrijfsanalisten rechtstreeks in Power BI Machine Learning-modellen mogen trainen, valideren en aanroepen. Zie [Geautomatiseerde Machine Learning in Power BI (preview-versie)](../transform-model/dataflows/dataflows-machine-learning-integration.md) voor meer informatie. |
| **Parallelle uitvoering voor AI-aanvragen inschakelen** | Hiermee geeft u op of AI-aanvragen parallel kunnen worden uitgevoerd. |
|  |  |

### <a name="datasets"></a>Gegevenssets

De workload Gegevenssets is standaard ingeschakeld en kan niet worden uitgeschakeld. Gebruik de volgende instellingen om het gedrag van workloads te beheren. Voor sommige instellingen is er meer informatie over het gebruik van de tabel.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door gegevenssets in een capaciteit kan worden gebruikt. |
| **XMLA-eindpunt** | Hiermee geeft u op dat verbindingen vanuit clienttoepassingen aan het in de werkruimte en app-niveaus ingestelde lidmaatschap van de beveiligingsgroep moeten voldoen. Zie [Verbinding maken met gegevenssets met clienttoepassingen en hulpprogramma's](service-premium-connect-tools.md) voor meer informatie. |
| **Maximum aantal in te stellen tussenliggende rijen** | Het maximumaantal tussenliggende rijen dat door DirectQuery wordt geretourneerd. De standaardwaarde is ingesteld op 1.000.000 en het toegestane bereik ligt tussen 100.000 en 2.147.483.647. |
| **Maximale grootte van offline gegevensset (GB)** | De maximale grootte van de offline gegevensset in het geheugen. Dit is de gecomprimeerde grootte op een schijf. De standaardwaarde is 0. Dat is de hoogste limiet die door SKU is gedefinieerd. Het toegestane bereik ligt tussen 0 en de capaciteitsgroottelimiet. |
| **Maximum aantal in te stellen rijen met resultaten** | Het maximumaantal rijen dat in een DAX-query wordt geretourneerd. De standaardwaarde is ingesteld op -1 (onbeperkt) en het toegestane bereik ligt tussen 100.000 en 2.147.483.647. |
| **Geheugenlimiet voor query's (%)** | Het maximale percentage van het beschikbare geheugen in de workload dat kan worden gebruikt voor het uitvoeren van een MDX- of DAX-query. De standaardwaarde is 0, wat betekent dat er automatisch een SKU-specifieke geheugenlimiet voor query's wordt toegepast. |
| **Time-out van query (seconden)** | De maximale hoeveelheid tijd voordat een time-out optreedt voor de query. De standaardwaarde is 3600 seconden (1 uur). Met de waarde 0 wordt aangegeven dat er geen time-out zal optreden voor query's. |
| **Pagina automatisch vernieuwen** | In-/uitschakelen om toe te staan dat Premium-werkruimten rapporten kunnen bevatten waarvoor pagina's automatisch kunnen worden vernieuwd op vaste intervallen. |
| **Minimaal vernieuwingsinterval** | Als Pagina automatisch vernieuwen is ingeschakeld, is dit het minimale interval dat als interval voor het vernieuwen van pagina's is toegestaan. De standaardwaarde is vijf minuten en het toegestane minimum is één seconde. |
| **Detectiemeting wijzigen** | In-/uitschakelen om toe te staan dat Premium-werkruimten rapporten kunnen bevatten waarvoor pagina's automatisch kunnen worden vernieuwd op basis van wijzigingsdetectie. |
| **Minimaal uitvoeringsinterval** | Als de meting voor de wijzigingsdetectie is ingeschakeld, is er een minimaal uitvoeringsinterval dat is toegestaan voor het controleren van gegevenswijzigingen. De standaardwaarde is vijf minuten en het toegestane minimum is één seconde. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Maximum aantal in te stellen tussenliggende rijen

Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. Wanneer een query naar een DirectQuery-gegevensset resulteert in een zeer groot resultaat van de brondatabase, kan dit leiden tot een piek in het geheugengebruik en de verwerkingsoverhead. Deze situatie kan ertoe leiden dat andere gebruikers en rapporten op weinig resources uitgevoerd worden. Met deze instelling kan de capaciteitsbeheerder aanpassen hoeveel rijen een afzonderlijke query uit de gegevensbron kan ophalen.

Als de capaciteit aan de andere kant meer dan de standaardwaarde van een miljoen kan ondersteunen en u een grote gegevensset hebt, vergroot u deze instelling om meer rijen op te halen.

Houd er rekening mee dat deze instelling alleen van invloed is op DirectQuery-query's, terwijl [Maximum aantal in te stellen rijen met resultaten](#max-result-row-set-count) DAX-query's beïnvloedt.

#### <a name="max-offline-dataset-size"></a>Maximale grootte van offline gegevensset

Gebruik deze instelling om te voorkomen dat rapportmakers een grote gegevensset publiceren die de capaciteit negatief kan beïnvloeden. Houd er rekening mee dat Power BI de werkelijke geheugengrootte niet kan bepalen totdat de gegevensset in het geheugen wordt geladen. Het is mogelijk dat een gegevensset met een kleinere offline grootte een grotere geheugen-footprint kan hebben dan een gegevensset met een grotere offline grootte.

Als u een bestaande gegevensset hebt die groter is dan de grootte die u voor deze instelling opgeeft, dan kan de gegevensset niet worden geladen wanneer een gebruiker deze probeert te openen. De gegevensset kan ook niet worden geladen als deze groter is dan het maximale geheugen dat is geconfigureerd voor de workload van de gegevenssets.

Ter bescherming van de prestaties van het systeem, wordt er een extra SKU-specifiek hard plafond toegepast als maximale grootte voor offline gegevenssets, ongeacht de geconfigureerde waarde. Dit harde plafond is niet van toepassing op Power BI-gegevenssets die zijn geoptimaliseerd voor een grote gegevensomvang. Zie [Grote modellen in Power BI Premium](service-premium-large-models.md) voor meer informatie.

|                                               | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |
|-----------------------------------------------|----------|----------|----------|---------|---------|---------|
| **Hard plafond voor maximale grootte van offline gegevenssets** | 3 GB     | 5 GB     | 6 GB     | 10 GB   | 10 GB   | 10 GB   |

#### <a name="max-result-row-set-count"></a>Maximum aantal in te stellen rijen met resultaten

Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. Als deze limiet wordt bereikt in een DAX-query, ziet een rapportgebruiker de volgende foutmelding. Hij of zij moet de foutgegevens kopiëren en contact opnemen met een beheerder.

![Kan gegevens voor deze visual niet laden](media/service-admin-premium-workloads/could-not-load-data.png)

Houd er rekening mee dat deze instelling alleen van invloed is op DAX-query's, terwijl [Maximum aantal in te stellen tussenliggende rijen](#max-intermediate-row-set-count) DirectQuery-query's beïnvloedt.

#### <a name="query-memory-limit"></a>Geheugenlimiet voor query's

Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. Sommige query's en berekeningen kunnen leiden tot tussenliggende resultaten die veel geheugen van de capaciteit gebruiken. Deze situatie kan ertoe leiden dat andere query's zeer traag worden uitgevoerd en andere gegevenssets van de capaciteit worden verwijderd. Dat kan leiden tot onvoldoende geheugen voor andere gebruikers van de capaciteit.

Deze instelling geldt voor alle DAX- en MDX-query's die worden uitgevoerd door Power BI-rapporten, rapporten op basis van Analyseren in Excel en andere hulpprogramma's die mogelijk verbinding maken via het XMLA-eindpunt.

Houd er rekening mee dat bewerkingen voor het vernieuwen van gegevens ook DAX-query's kunnen uitvoeren als onderdeel van het vernieuwen van de dashboardtegels en caches met visuals nadat de gegevens in de gegevensset zijn vernieuwd. Dergelijke query's kunnen mogelijk ook mislukken als gevolg van deze instelling, en dit kan ertoe leiden dat de bewerking voor het vernieuwen van de gegevens de status Mislukt krijgt, zelfs als de gegevens in de gegevensset wel zijn bijgewerkt.

De standaardinstelling is 0, wat betekent dat de volgende SKU-specifieke geheugenlimiet voor query's automatisch wordt toegepast.

|                                  | EM1 / A1 | EM2 / A2 | EM3 / A3 | P1 / A4 | P2 / A5 | P3 / A6 |
|----------------------------------|----------|----------|----------|---------|---------|---------|
| **Automatische geheugenlimiet voor query's** | 1 GB     | 2 GB     | 2 GB     | 6 GB    | 6 GB    | 10 GB   |

Als waarborging van de prestaties van het systeem wordt een hard plafond van 10 GB afgedwongen voor alle query's die worden uitgevoerd door Power BI-rapporten, ongeacht de geheugenlimiet voor query's die door de gebruiker is geconfigureerd. Dit harde plafond geldt niet voor query's die worden uitgevoerd door hulpprogramma's die gebruikmaken van het Analysis Services-protocol (ook wel XMLA genoemd). Gebruikers moeten overwegen om de query of de berekeningen ervan te vereenvoudigen als de query te geheugenintensief is.

#### <a name="query-timeout"></a>Time-out van query

Gebruik deze instelling om langlopende query's beter te kunnen blijven beheersen, waardoor rapporten langzaam kunnen worden geladen voor gebruikers.

Deze instelling geldt voor alle DAX- en MDX-query's die worden uitgevoerd door Power BI-rapporten, rapporten op basis van Analyseren in Excel en andere hulpprogramma's die mogelijk verbinding maken via het XMLA-eindpunt.

Houd er rekening mee dat bewerkingen voor het vernieuwen van gegevens ook DAX-query's kunnen uitvoeren als onderdeel van het vernieuwen van de dashboardtegels en caches met visuals nadat de gegevens in de gegevensset zijn vernieuwd. Dergelijke query's kunnen mogelijk ook mislukken als gevolg van deze instelling, en dit kan ertoe leiden dat de bewerking voor het vernieuwen van de gegevens de status Mislukt krijgt, zelfs als de gegevens in de gegevensset wel zijn bijgewerkt.

Deze instelling geldt voor één query en niet de tijdsduur die nodig is voor het uitvoeren van alle query's die zijn gekoppeld aan het bijwerken van een gegevensset of rapport. Kijk eens naar het volgende voorbeeld:

- De instelling voor de **Time-out van query** is 1200 (20 minuten).
- Er zijn vijf query's die moeten worden uitgevoerd en elke query duurt 15 minuten.

De gecombineerde tijd voor alle query's is 75 minuten, maar de limiet voor de instelling is niet bereikt omdat alle afzonderlijke query's in minder dan 20 minuten worden uitgevoerd.

Houd er rekening mee dat Power BI-rapporten deze standaardinstelling overschrijven met een veel kleinere time-out voor elke query op de capaciteit. De time-out voor elke query is doorgaans ongeveer drie minuten.

#### <a name="automatic-page-refresh-preview"></a>Pagina automatisch vernieuwen (preview-versie)

Indien ingeschakeld, kunnen gebruikers in uw Premium-capaciteit met behulp van de functie Pagina automatisch vernieuwen, ervoor zorgen dat voor DirectQuery-bronnen pagina's in hun rapport op een gedefinieerd interval worden vernieuwd. Als capaciteitsbeheerder kunt u het volgende doen:

- Pagina automatisch vernieuwen in- en uitschakelen
- Een minimaal vernieuwingsinterval definiëren

In de volgende afbeelding wordt de locatie van de instelling voor het automatische vernieuwingsinterval weergegeven:

![beheerinstelling voor automatisch vernieuwingsinterval](media/service-admin-premium-workloads/automatic-refresh-interval.png)

Query's die door het automatisch vernieuwen van pagina's worden gemaakt, gaan direct naar de gegevensbron, en het is dus van belang om na te denken over de betrouwbaarheid ervan en welke belasting ze vormen voor die bronnen als u toestaat dat het automatisch vernieuwen van pagina's in uw organisatie kan worden gebruikt. 

### <a name="dataflows"></a>Gegevensstromen

Met de workload Gegevensstromen kunt u de zelfservice voor gegevensvoorbereiding voor gegevensstromen gebruiken om gegevens op te nemen, te transformeren, te integreren en te verrijken. Gebruik de volgende instellingen om het gedrag van workloads te beheren.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door gegevensstromen in een capaciteit kan worden gebruikt. |
| **Verbeterde rekenengine voor gegevensstromen (preview-versie)** | Schakel deze optie in voor tot 20x snellere berekening van berekende entiteiten als u grootschalige gegevensvolumes gebruikt. **U moet de capaciteit opnieuw opstarten om de nieuwe engine te activeren.** Zie [Verbeterde rekenengine voor gegevensstromen](#enhanced-dataflows-compute-engine) voor meer informatie. |
| **Containergrootte** | De maximumgrootte van de container die door gegevensstromen wordt gebruikt voor elke entiteit in de gegevensstroom. De standaardwaarde is 700 MB. Zie [Containergrootte](#container-size) voor meer informatie. |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Verbeterde rekenengine voor gegevensstromen

Als u wilt profiteren van de nieuwe rekenengine, splitst u de opname van gegevens in afzonderlijke gegevensstromen en plaatst u de transformatielogica in berekende entiteiten in verschillende gegevensstromen. Dit is de aanbevolen methode omdat de rekenengine werkt op gegevensstromen waarin naar een bestaande gegevensstroom wordt verwezen. Dit werkt niet op gegevensstromen voor opname. Als u deze richtlijnen volgt, zorgt u ervoor dat de nieuwe rekenengine transformatiestappen, zoals koppelen en samenvoegen, verwerkt voor optimale prestaties.

#### <a name="container-size"></a>Containergrootte

Bij het vernieuwen van een gegevensstroom wordt met de gegevensstroomworkload een container voor elke entiteit in de gegevensstroom gegenereerd. Elke container kan geheugen in beslag nemen tot het volume dat is opgegeven in de instelling Containergrootte. De standaardwaarde voor alle SKU's is 700 MB. Mogelijk wilt u deze instelling wijzigen, indien:

- Het vernieuwen van de gegevensstromen te lang duurt of het vernieuwen van de gegevensstroom mislukt door een time-out.
- Gegevensstroomentiteiten rekenstappen omvatten, bijvoorbeeld een samenvoeging.  

Het is raadzaam om de app [Metrische Power BI Premium-capaciteitsgegevens](service-admin-premium-monitor-capacity.md) te gebruiken voor het analyseren van de prestaties van de gegevensstroomworkloads.

In sommige gevallen worden de prestaties mogelijk niet verbeterd wanneer de containergrootte toeneemt. Als de gegevensstroom bijvoorbeeld alleen gegevens ophaalt uit een bron zonder dat er aanzienlijke berekeningen worden uitgevoerd, zal het wijzigen van de containergrootte waarschijnlijk niet helpen. Een toename van de containergrootte kan helpen indien hiermee in de gegevensstroomworkload meer geheugen wordt toegewezen aan het vernieuwen van entiteiten. Door de toewijzing van extra geheugen kan de tijd worden verkort die benodigd is voor het vernieuwen van entiteiten waarvoor veel rekenkracht is vereist.

De waarde voor containergrootte kan niet groter zijn dan de maximale geheugengrootte voor de gegevensstroomworkload. Een P1-capaciteit heeft bijvoorbeeld 25 GB geheugen. Als de maximale geheugengrootte voor de gegevensstroomworkload (%) is ingesteld op 20%, mag Containergrootte (MB) niet groter zijn dan 5000. In elk geval mag de containergrootte niet groter zijn dan de maximale geheugengrootte, zelfs niet als u een hogere waarde instelt.

### <a name="paginated-reports"></a>Gepagineerde rapporten

Met de workload Gepagineerde rapporten kunt u gepagineerde rapporten uitvoeren, op basis van de standaardindeling voor SQL Server Reporting Services, in de Power BI-service. Gebruik de volgende instelling om het gedrag van workloads te beheren.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door gepagineerde rapporten in een capaciteit kan worden gebruikt. |
|  |  |

Gepagineerde rapporten bieden dezelfde mogelijkheden als SSRS-rapporten (SQL Server Reporting Services) momenteel bieden, waaronder de mogelijkheid voor rapportauteurs om aangepaste code toe te voegen.  Hierdoor kunnen auteurs dynamisch rapporten wijzigen, bijvoorbeeld tekstkleuren wijzigen op basis van code-expressies.  Gepagineerde rapporten worden uitgevoerd binnen een beveiligde sandbox per capaciteit om goede isolatie te garanderen. Rapporten die in dezelfde capaciteit worden uitgevoerd, kunnen onder elkaar neveneffecten veroorzaken. Net zoals u beperkt welke auteurs inhoud kunnen publiceren in een SSRS-exemplaar, is het aan te raden dit te doen voor gepagineerde rapporten. Zorg ervoor dat auteurs die inhoud publiceren in een capaciteit worden vertrouwd door de organisatie. U kunt uw omgeving verder beveiligen door meerdere capaciteiten in te richten en aan elk ervan verschillende auteurs toe te wijzen. 

In enkele gevallen kan het gebeuren dat de workload Gepagineerde rapporten niet beschikbaar is. U ziet dan een foutstatus voor de workload in de beheerportal. Gebruikers zien time-outs als ze rapporten willen weergeven. U kunt dit probleem oplossen door de workload uit te schakelen en vervolgens weer in te schakelen.

## <a name="configure-workloads"></a>Workloads configureren

Maximaliseer de beschikbare resources van uw capaciteit door workloads alleen in te schakelen als ze worden gebruikt. Wijzig de geheugeninstellingen en overige instellingen alleen wanneer u hebt vastgesteld dat de standaardinstellingen niet voldoen aan de resourcevereisten van uw capaciteit.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Workloads configureren in de Power BI-beheerportal

1. Selecteer een capaciteit bij **Capaciteitsinstellingen** > **PREMIUM-CAPACITEITEN**.

1. Vouw **Workloads** uit onder **MEER OPTIES**.

1. Schakel een of meer workloads in en stel een waarde in voor **Maximaal geheugengrootte** en overige instellingen.

1. Selecteer **Toepassen**.

### <a name="rest-api"></a>REST API

Workloads kunnen worden ingeschakeld en aan een capaciteit worden toegewezen met behulp van de REST API's voor [capaciteiten](/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Workloads bewaken

De app [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) biedt metrische gegevens over gegevenssets, gegevensstromen en gepagineerde rapporten om workloads te bewaken die zijn ingeschakeld voor uw capaciteiten. 


> [!IMPORTANT]
> Als er een hoog resourcegebruik is in uw Power BI Premium-capaciteit, wat leidt tot problemen met prestaties of betrouwbaarheid, kunt u e-mailmeldingen ontvangen om het probleem te identificeren en op te lossen. Dit kan een gestroomlijnde manier zijn om problemen met overbelaste capaciteiten op te lossen. Zie [Meldingen over capaciteit en betrouwbaarheid](service-interruption-notifications.md#capacity-and-reliability-notifications) voor meer informatie.


## <a name="next-steps"></a>Volgende stappen

[Power BI Premium-capaciteit optimaliseren](service-premium-capacity-optimize.md)
[Selfservice-gegevensvoorbereiding in Power BI met Gegevensstromen](../transform-model/dataflows/dataflows-introduction-self-service.md)
[Wat zijn gepagineerde rapporten in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
[Automatische paginavernieuwing in Power BI Desktop (preview-versie)](../create-reports/desktop-automatic-page-refresh.md)

Hebt u nog vragen? [Stel een vraag aan de Power BI-community](https://community.powerbi.com/)

Power BI heeft Power BI Premium Gen2 geïntroduceerd als preview-aanbieding, waardoor de Power BI Premium-ervaring als volgt wordt aangepast met verbeteringen:
* Prestaties
* Licenties per gebruiker
* Grotere schaal
* Verbeterde metrische gegevens
* Automatisch schalen
* Minder beheeroverhead

Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie over Power BI Premium Gen2.