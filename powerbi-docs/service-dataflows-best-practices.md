---
title: Aanbevolen procedures voor Power BI-gegevensstromen
description: Aanbevolen procedures voor Power BI-gegevensstromen
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c499a83b87eb15031d75974084468f418a17804a
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142315"
---
# <a name="dataflows-best-practice"></a>Aanbevolen procedure voor gegevensstromen

In dit artikel worden de aanbevolen procedures voor het ontwerpen van gegevensstromen in Power BI beschreven. U kunt deze richtlijnen gebruiken voor meer informatie over het maken van gegevensstromen. Pas deze procedures toe op uw eigen gegevensstromen.

> [!NOTE]
> De aanbevelingen die in dit artikel worden gedaan, zijn richtlijnen. Bij elke aanbevolen procedure in dit artikel kunnen er gegronde redenen zijn om van deze richtlijnen af te wijken. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Opname en transformatie splitsen om de verbeterde rekenengine te gebruiken

Bij het maken van gegevensstromen bent u mogelijk geneigd om een enkele gegevensstroom te maken met alle entiteiten, transformaties, samenvoegingen en verbeteringen op één plek. Voor kleinere gegevenssets kan één gegevensstroom effectief zijn. Maar bij het verwerken van grotere gegevensvolumes kunnen er vertragingen of geheugenfouten optreden tijdens het uitvoeren van samenvoegingen of bepaalde transformaties. Om deze problemen op te lossen, is er nu een verbeterde engine voor Power BI Premium-gebruikers. Deze engine is geschikt voor veel grotere gegevensvolumes. De verbeterde rekenengine werkt alleen met gekoppelde of berekende entiteiten, dus u kunt hier baat bij hebben als u een afzonderlijke gegevensstroom maakt voor opname en een gekoppelde gegevensstroom voor het uitvoeren van alle complexe samenvoegingen en transformaties.

Het splitsen van gegevensstromen is ook gunstig voor het opsporen en oplossen van problemen bij het vernieuwen, met name als u werkt met bronnen waarvoor beperkingen gelden.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Voer acties uit waarbij de verbeterde rekenengine kan worden gebruikt

Maak gebruik van de verbeterde rekenengine door eerst samenvoegingen en filtertransformaties uit te voeren in een berekende entiteit voordat u andere typen transformaties uitvoert.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Splits gegevensstromen bij het maken van verbinding met SharePoint

Wanneer u met SharePoint werkt en verbinding maakt met meerdere bestanden, kunnen er sporadisch fouten optreden. In SharePoint gelden aanvraagbeperkingen om ervoor te zorgen dat SharePoint betrouwbaar en responsief blijft. Als gevolg hiervan bent u bij het maken van verbinding met Excel-bestanden vanuit SharePoint mogelijk geneigd om alle bestanden in één gegevensstroom te downloaden. Als u veel bestanden (meer dan 20) wilt downloaden, kunt u beter twee of meer gegevensstromen maken om de werkbelasting voor het vernieuwen te splitsen en deze SharePoint-beperkingen te overwinnen.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Plan geen vernieuwingen voor gekoppelde entiteiten binnen dezelfde werkruimte

Als u regelmatig geen toegang meer krijgt tot gegevensstromen met gekoppelde entiteiten, kan het zijn dat bijbehorende, afhankelijke gegevensstromen binnen dezelfde werkruimte worden vergrendeld bij het vernieuwen van de gegevensstromen. Deze vergrendelingen zorgen er weliswaar voor dat transacties nauwkeurig worden uitgevoerd en dat beide gegevensstromen correct worden vernieuwd, maar verhinderen dat u ze kunt bewerken. 

Als u een afzonderlijk schema voor de gekoppelde gegevensstroom instelt, kunnen gegevensstromen onnodig worden vernieuwd waardoor u deze niet kunt bewerken. U kunt dit op twee manieren voorkomen: 

* Stel geen vernieuwingsschema in voor een gekoppelde gegevensstroom in dezelfde werkruimte als de brongegevensstroom
* Als u een afzonderlijk vernieuwingsschema wilt configureren en het vergrendelingsgedrag wilt vermijden, moet u de gegevensstroom onderbrengen in een afzonderlijke werkruimte.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Maak een afzonderlijke werkruimte voor opname/transformatie

Als u veel gebruikers toegang wilt bieden tot onderliggende gegevensstroomgegevens, zonder hen toegang te verlenen tot de onbewerkte gegevens van het onderliggende bronsysteem, maakt u een afzonderlijke werkruimte met alle gegevens die u wilt delen en wijst u de gebruikers daarvoor machtigingen toe. Afzonderlijke gegevensstroommachtigingen worden momenteel niet ondersteund.

### <a name="ensure-capacity-is-in-the-same-region"></a>Zorg ervoor dat de capaciteit zich in dezelfde regio bevindt

Gegevensstromen bieden momenteel geen ondersteuning voor meerdere geografische regio's. De Premium-capaciteit moet zich bevinden in dezelfde regio als uw Power BI-tenant.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Scheid on-premises bronnen van cloudbronnen

Naast de eerder beschreven aanbevolen procedures kunt u een afzonderlijke gegevensstroom voor elk type bron maken, zoals on-premises, cloud, SQL Server, Spark, Dynamics, enzovoort. Het wordt ten zeerste aanbevolen om uw gegevensstroom te splitsen op gegevensbrontype. Hierdoor kunt u sneller problemen oplossen en voorkomen dat interne limieten worden overschreden bij het vernieuwen van uw gegevensstromen.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Scheid gegevensstromen in afzonderlijke capaciteiten

Als u tegen beperkingslimieten aanloopt of als er regelmatig problemen met uw gegevensstromen optreden vanwege geheugenlimieten voor uw capaciteit, kunt u overwegen uw gegevensstromen te scheiden of uw Premium-capaciteit op te schalen voor meer geheugen.

## <a name="next-steps"></a>Volgende stappen

Dit artikel biedt informatie over aanbevolen procedures voor gegevensstromen. De volgende artikelen bieden mogelijk meer informatie over gegevensstromen:

* [Self-service data prep with dataflows](service-dataflows-overview.md) (Selfservice voor gegevensvoorbereiding met gegevensstromen)
* [Gegevensstromen maken en gebruiken in Power BI](service-dataflows-create-use.md)
* [Berekende entiteiten gebruiken in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Gegevensstromen gebruiken met on-premises gegevensbronnen](service-dataflows-on-premises-gateways.md)

Voor informatie over CDM-ontwikkeling en zelfstudiebronnen, raadpleegt u:
* [Overzicht van Common Data Model](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [CDM-mappen](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Bestandsdefinitie van CDM-model](https://go.microsoft.com/fwlink/?linkid=2045521)


U kunt de volgende artikelen lezen voor meer informatie over Power Query en geplande vernieuwing:
* [Queryoverzicht in Power BI Desktop](desktop-query-overview.md)
* [Geplande vernieuwing configureren](refresh-scheduled-refresh.md)
