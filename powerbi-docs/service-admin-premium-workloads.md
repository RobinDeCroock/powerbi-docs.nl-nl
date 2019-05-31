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
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564865"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Workloads configureren in een Premium-capaciteit

In dit artikel wordt het inschakelen en configureren van workloads voor Power BI Premium-capaciteiten beschreven. Standaard bieden capaciteiten alleen ondersteuning voor de workload die aan het uitvoeren van Power BI-query's is gekoppeld. U kunt ook extra workloads inschakelen en configureren voor **[AI (Cognitive Services)](service-cognitive-services.md)** , **[gegevensstromen](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** en **[gepagineerde rapporten](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Standaardinstellingen voor geheugen

Queryworkloads zijn geoptimaliseerd voor en beperkt door de resources die voor uw Premium-capaciteit-SKU zijn vastgesteld. Premium-capaciteiten bieden bovendien ondersteuning voor extra workloads die de resources van uw capaciteit kunnen gebruiken. De standaardgeheugenwaarden voor deze workloads zijn gebaseerd op de capaciteitsknooppunten die voor uw SKU beschikbaar zijn. De maximale geheugeninstellingen zijn niet cumulatief. Het geheugen tot de opgegeven maximumwaarde wordt dynamisch toegewezen voor AI en gegevensstromen, maar statisch voor gepagineerde rapporten. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office-SKU's voor SaaS-scenario's (Software as a Service)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N.v.t. | N.v.t. | standaard 20%. 20% minimale | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% |
| Gegevensstromen | N.v.t. |Standaard 20%, minimaal 12%  | standaard 20%; minimaal 5%  | Standaard 20%, minimaal 3% | standaard 20%; minimaal 2%  |
| Gepagineerde rapporten | N.v.t. |N.v.t. | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% | standaard 20%; minimaal 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Azure-SKU's voor PaaS-scenario's (Platform as a Service)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N.v.t.                      | standaard 20%. 100% minimale                     | standaard 20%. 50% minimale                     | standaard 20%. 20% minimale | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% |
| Gegevensstromen         | Standaard 40%, minimaal 40% | Standaard 24%, minimaal 24% | Standaard 20%, minimaal 12% | standaard 20%; minimaal 5%  | Standaard 20%, minimaal 3% | standaard 20%; minimaal 2%   |
| Gepagineerde rapporten | N.v.t.                      | N.v.t.                      | N.v.t.                     | standaard 20%; minimaal 10% | standaard 20%; minimaal 5% | standaard 20%; minimaal 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Instellingen van de werkbelasting

### <a name="ai-preview"></a>AI (Preview)

Naast de **Max Memory** instellen, de AI-werkbelasting heeft een extra instelling **gebruik toestaan vanuit Power BI Desktop**. De standaardwaarde is **uit**. Deze instelling is gereserveerd voor toekomstig gebruik en kan niet worden weergegeven in alle tenants.

### <a name="datasets-preview"></a>Gegevenssets (Preview)

Standaard is de werkbelasting gegevenssets is ingeschakeld en kan niet worden uitgeschakeld. Deze workload bevat een aanvullende instelling **XMLA-eindpunt**. De standaardwaarde is **1**, betekenis ingeschakeld. Deze instelling bepaalt u verbindingen van clienttoepassingen voldoen aan de beveiligingsgroep die is ingesteld op het niveau van de werkruimte en de app. Zie voor meer informatie, [verbinding maken met gegevenssets met client-toepassingen en hulpprogramma's](service-premium-connect-tools.md).

### <a name="dataflows"></a>Gegevensstromen

Naast de **Max Memory** instellen, de gegevensstromen werkbelasting heeft een extra instelling **containergrootte**. Deze instelling kunt u het optimaliseren van prestaties van de gegevensstroom werkbelastingen voor de verwerking van complexe, compute-zware gegevensstromen.

Bij het vernieuwen van een gegevensstroom, worden in de gegevensstroom werkbelasting een container voor elke entiteit in de gegevensstroom gestart. Elke container kan duren voordat het geheugen tot het volume in opgegeven in de instelling voor de Container. De standaardwaarde voor alle SKU's **700 MB**. Het is raadzaam deze instelling te wijzigen als:

- Gegevensstromen duurt te lang om te vernieuwen of vernieuwen van de gegevensstroom mislukt op een time-out.
- Gegevensstroom entiteiten bevatten berekening stappen, bijvoorbeeld een join.  

Het aanbevolen dat u gebruikt de [metrische gegevens over Power BI Premium capaciteit](service-admin-premium-monitor-capacity.md) app voor het analyseren van prestaties van de gegevensstroom werkbelastingen. 

In sommige gevallen vergroten van de container kan niet de prestaties verbeteren. Bijvoorbeeld, wordt niet containergrootte waarschijnlijk wijzigen als de gegevensstroom is ophalen van gegevens alleen uit een bron zonder aanzienlijke berekeningen uitvoert, helpen. Vergroten van de container kan helpen als deze service voorziet in de gegevensstroom werkbelasting meer geheugen toewijzen voor entiteit bewerkingen voor gegevensvernieuwing. Door meer geheugen toegewezen, kan deze minder tijd nodig is om u te veel berekende entiteiten vernieuwen. 

De waarde voor de Container kan niet groter zijn dan de maximale hoeveelheid geheugen voor de workload voor gegevensstromen. Een capaciteit P1 heeft bijvoorbeeld 25GB geheugen. Als de werkbelasting gegevensstroom Max Memory (%) is ingesteld op 20%, Container-grootte (MB) mag niet meer dan 5000. In alle gevallen moet de grootte van de Container kan niet groter zijn dan de Max Memory, zelfs als u een hogere waarde instelt. 

### <a name="paginated-reports-preview"></a>Gepagineerde rapporten (Preview)

Gepagineerde rapporten kunnen aangepaste code moet worden uitgevoerd wanneer een rapport wordt gerenderd. Bijvoorbeeld, dynamisch wijzigen op basis van inhoud de kleur van tekst, die kan duren voordat extra geheugen. In Power BI Premium worden gepagineerde rapporten in een ingesloten ruimte in de capaciteit uitgevoerd. De Max Memory opgegeven gebruikt *of* de werkbelasting actief is. Als de instelling maximale geheugen wijzigen van de standaardwaarde, controleert u of u instellen dat deze laag niet genoeg dat deze negatieve invloed hebben op andere werkbelastingen.

In sommige gevallen kan zijn de werkbelasting gepagineerde rapporten niet beschikbaar. In dit geval de werkbelasting toont de foutstatus van een in de beheerportal en gebruikers zien time-outs voor het weergeven van rapporten. Dit probleem beperken, uitschakelen van de werkbelasting en vervolgens weer inschakelen.

## <a name="configure-workloads"></a>Workloads configureren

Maximaliseer de beschikbare resources van uw capaciteit door workloads alleen in te schakelen als ze worden gebruikt. Wijzig de geheugeninstellingen alleen wanneer u hebt vastgesteld dat de standaardinstellingen niet voldoen aan de resourcevereisten van uw capaciteit.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Workloads configureren in de Power BI-beheerportal

1. Selecteer een capaciteit bij **Capaciteitsinstellingen** > **PREMIUM-CAPACITEITEN**.

1. Vouw **Workloads** uit onder **MEER OPTIES**.

1. Schakel een of meer workloads in en stel een waarde in voor **Maximaal geheugen**.   

    
    ![Workloads inschakelen](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Klik op **Toepassen**.

### <a name="rest-api"></a>REST API

Workloads kunnen worden ingeschakeld en aan een capaciteit worden toegewezen met behulp van de REST API's voor [capaciteiten](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Workloads bewaken

De app [Power BI Premium Capacity Metrics](service-admin-premium-monitor-capacity.md) biedt metrische gegevens over gegevenssets, gegevensstromen en gepagineerde rapporten om workloads te bewaken die zijn ingeschakeld voor uw capaciteiten. 

## <a name="next-steps"></a>Volgende stappen

[Power BI Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)     
[Selfservice voor gegevensvoorbereiding in Power BI met gegevensstromen](service-dataflows-overview.md)   
[Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Hebt u nog vragen? [Stel een vraag aan de Power BI-community](http://community.powerbi.com/)