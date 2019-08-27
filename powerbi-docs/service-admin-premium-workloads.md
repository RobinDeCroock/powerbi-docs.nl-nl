---
title: Workloads configureren in Power BI Premium
description: Ontdek hoe u workloads kunt configureren in een Power BI Premium-capaciteit.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985687"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Workloads configureren in een Premium-capaciteit

In dit artikel wordt het inschakelen en configureren van workloads voor Power BI Premium-capaciteiten beschreven. Standaard bieden capaciteiten alleen ondersteuning voor de workload die aan het uitvoeren van Power BI-query's is gekoppeld. U kunt ook extra workloads inschakelen en configureren voor **[AI (Cognitive Services)](service-cognitive-services.md)** , **[gegevensstromen](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** en **[gepagineerde rapporten](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Standaardinstellingen voor geheugen

Queryworkloads zijn geoptimaliseerd voor en beperkt door de resources die voor uw Premium-capaciteit-SKU zijn vastgesteld. Premium-capaciteiten bieden bovendien ondersteuning voor extra workloads die de resources van uw capaciteit kunnen gebruiken. De standaardgeheugenwaarden voor deze workloads zijn gebaseerd op de capaciteitsknooppunten die voor uw SKU beschikbaar zijn. De maximale geheugeninstellingen zijn niet cumulatief. Het geheugen tot de opgegeven maximumwaarde wordt dynamisch toegewezen voor AI en gegevensstromen, maar statisch voor gepagineerde rapporten.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office-SKU's voor SaaS-scenario's (Software as a Service)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N.v.t. | N.v.t. | Standaard 20%; minimaal 20% | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% |
| Gegevensstromen | N.v.t. |Standaard 20%, minimaal 12%  | standaard 20%; minimaal 5%  | Standaard 20%, minimaal 3% | standaard 20%; minimaal 2%  |
| Gepagineerde rapporten | N.v.t. |N.v.t. | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% | standaard 20%; minimaal 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Azure-SKU's voor PaaS-scenario's (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N.v.t.                      | Standaard 20%; minimaal 100%                     | Standaard 20%; minimaal 50%                     | Standaard 20%; minimaal 20% | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% |
| Gegevensstromen         | Standaard 40%, minimaal 40% | Standaard 24%, minimaal 24% | Standaard 20%, minimaal 12% | standaard 20%; minimaal 5%  | Standaard 20%, minimaal 3% | standaard 20%; minimaal 2%   |
| Gepagineerde rapporten | N.v.t.                      | N.v.t.                      | N.v.t.                     | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% | standaard 20%; minimaal 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Workloadinstellingen

### <a name="ai-preview"></a>AI (preview)

Met de AI-workload kunt u cognitive services en automatische Machine Learning in Power BI gebruiken. Gebruik de volgende instellingen om het gedrag van workloads te beheren.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door AI-processen in een capaciteit kan worden gebruikt. |
| **Gebruik via Power BI Desktop toestaan** | Deze instelling is gereserveerd voor toekomstig gebruik en wordt niet in alle tenants weergegeven. |
| **Het bouwen van Machine Learning-modellen toestaan** | Hiermee geeft u aan of bedrijfsanalisten rechtstreeks in Power BI Machine Learning-modellen mogen trainen, valideren en aanroepen. Zie [Geautomatiseerde Machine Learning in Power BI (preview-versie)](service-machine-learning-automated.md) voor meer informatie. |
| **Parallelle uitvoering voor AI-aanvragen inschakelen** | Hiermee geeft u op of AI-aanvragen parallel kunnen worden uitgevoerd. |
|  |  |

### <a name="datasets"></a>Gegevenssets

De workload Gegevenssets is standaard ingeschakeld en kan niet worden uitgeschakeld. Gebruik de volgende instellingen om het gedrag van workloads te beheren.

| Instellingsnaam | Beschrijving |
|---------------------------------|----------------------------------------|
| **Maximaal geheugen (%)** | Het maximale percentage beschikbaar geheugen dat door gegevenssets in een capaciteit kan worden gebruikt. |
| **XMLA-eindpunt** | Hiermee geeft u op dat verbindingen vanuit clienttoepassingen aan het in de werkruimte en app-niveaus ingestelde lidmaatschap van de beveiligingsgroep moeten voldoen. Zie [Verbinding maken met gegevenssets met clienttoepassingen en hulpprogramma's](service-premium-connect-tools.md) voor meer informatie. |
| **Maximum aantal in te stellen tussenliggende rijen** | Het maximumaantal tussenliggende rijen dat door DirectQuery wordt geretourneerd. De standaardwaarde is ingesteld op 1.000.000 en het toegestane bereik ligt tussen 100.000 en 2.147.483.647. Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. |
| **Maximale grootte van offline gegevensset (GB)** | De maximale grootte van de offline gegevensset in het geheugen. Dit is de gecomprimeerde grootte op een schijf. De standaardwaarde wordt ingesteld per SKU en het toegestane bereik ligt tussen 0,1 en 10 GB. Gebruik deze instelling om te voorkomen dat rapportmakers een grote gegevensset publiceren die de capaciteit negatief kan beïnvloeden. |
| **Maximum aantal in te stellen rijen met resultaten** | Het maximumaantal rijen dat in een DAX-query wordt geretourneerd. De standaardwaarde is ingesteld op -1 (onbeperkt) en het toegestane bereik ligt tussen 100.000 en 2.147.483.647. Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. |
| **Geheugenlimiet voor query's (%)** | Het maximale percentage beschikbaar geheugen dat kan worden gebruikt voor tijdelijke resultaten in een query of een DAX-meting. Gebruik deze instelling om de impact van resource-intensieve of slecht ontworpen rapporten te beheren. |
| **Time-out van query (seconden)** | De maximale hoeveelheid tijd voordat een time-out optreedt voor de query. De standaardwaarde is 3600 seconden (1 uur). Met de waarde 0 wordt aangegeven dat er geen time-out zal optreden voor query's. Gebruik deze instelling om een betere controle over langlopende query's te houden. |
|  |  |  |

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

Bij het vernieuwen van een gegevensstroom wordt met de gegevensstroomworkload een container voor elke entiteit in de gegevensstroom gegenereerd. Elke container kan geheugen in beslag nemen tot het volume dat is opgegeven in de instelling **Containergrootte. De standaardwaarde voor alle SKU's is 700 MB. Mogelijk wilt u deze instelling wijzigen, indien:

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

Met gepagineerde rapporten kan aangepaste code worden uitgevoerd bij rapportrendering. Een voorbeeld is het dynamisch wijzigen van de tekstkleur op basis van de inhoud, wat extra geheugen kan kosten. In Power BI Premium worden gepagineerde rapporten in een ingesloten ruimte in de capaciteit uitgevoerd. Er wordt van de maximale geheugengrootte gebruikgemaakt, ongeacht of de workload *wel of niet* actief is. Als u de standaardinstelling voor maximale geheugengrootte wijzigt, moet u ervoor zorgen dat u deze zo laag instelt dat er geen nadelig effect optreedt voor andere workloads.

In enkele gevallen kan het gebeuren dat de workload Gepagineerde rapporten niet beschikbaar is. U ziet dan een foutstatus voor de workload in de beheerportal. Gebruikers zien time-outs als ze rapporten willen weergeven. U kunt dit probleem oplossen door de workload uit te schakelen en vervolgens weer in te schakelen.

## <a name="configure-workloads"></a>Workloads configureren

Maximaliseer de beschikbare resources van uw capaciteit door workloads alleen in te schakelen als ze worden gebruikt. Wijzig de geheugeninstellingen en overige instellingen alleen wanneer u hebt vastgesteld dat de standaardinstellingen niet voldoen aan de resourcevereisten van uw capaciteit.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Workloads configureren in de Power BI-beheerportal

1. Selecteer een capaciteit bij **Capaciteitsinstellingen** > **PREMIUM-CAPACITEITEN**.

1. Vouw **Workloads** uit onder **MEER OPTIES**.

1. Schakel een of meer workloads in en stel een waarde in voor **Maximaal geheugengrootte** en overige instellingen.

1. Selecteer **Toepassen**.

### <a name="rest-api"></a>REST API

Workloads kunnen worden ingeschakeld en aan een capaciteit worden toegewezen met behulp van de REST API's voor [capaciteiten](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Workloads bewaken

De app [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) biedt metrische gegevens over gegevenssets, gegevensstromen en gepagineerde rapporten om workloads te bewaken die zijn ingeschakeld voor uw capaciteiten. 

## <a name="next-steps"></a>Volgende stappen

[Power BI Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)     
[Selfservice voor gegevensvoorbereiding in Power BI met gegevensstromen](service-dataflows-overview.md)   
[Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Hebt u nog vragen? [Stel een vraag aan de Power BI-community](http://community.powerbi.com/)