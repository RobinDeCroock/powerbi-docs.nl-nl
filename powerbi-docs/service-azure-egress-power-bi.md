---
title: Power BI en uitgaand Azure-verkeer
description: De kosten voor uitgaand Azure-verkeer, Power BI op basis van tenantlocatie en Power BI Premium begrijpen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from databases
ms.openlocfilehash: 17175e1accb5013b960c5e1a71ae036b3dda72f3
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855570"
---
# <a name="power-bi-and-azure-egress"></a>Power BI en uitgaand Azure-verkeer

Wanneer u Power BI gebruikt met Azure-gegevensbronnen, kunt u kosten voor uitgaand Azure-verkeer voorkomen. Zorg er hiertoe voor dat uw Power BI-tenant zich in dezelfde regio bevindt als uw Azure-gegevensbronnen.

Wanneer uw Power BI-tenant is geïmplementeerd in dezelfde Azure-regio als die waarin u uw gegevensbronnen implementeert, worden er geen kosten voor uitgaand verkeer voor geplande vernieuwing en DirectQuery-interacties in rekening gebracht. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Bepalen waar uw Power BI-tenant zich bevindt

Zie het artikel [Waar bevindt mijn Power BI-tenant zich?](service-admin-where-is-my-tenant-located.md) als u wilt weten waar uw Power BI-tenant zich bevindt.

Voor klanten van Power BI Premium Multi-Geo: als uw Power BI-tenant zich niet op de optimale locatie voor sommige van uw Azure-gegevensbronnen bevindt, kunt u Power BI Premium Multi-Geo implementeren in de gewenste Azure-regio en ervan profiteren dat uw Power BI-tenant en Azure-gegevensbronnen zich in dezelfde Azure-regio bevinden.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over Power BI Premium of Multi-Geo:

* [Wat is Microsoft Power BI Premium?](service-premium-what-is.md)
* [Power BI Premium aanschaffen](service-admin-premium-purchase.md)
* [Multi-Geo-ondersteuning voor Power BI Premium (Preview)](service-admin-premium-multi-geo.md)
* [Waar bevindt mijn Power BI-tenant zich?](service-admin-where-is-my-tenant-located.md)
* [Veelgestelde vragen over Power BI Premium](service-premium-faq.md)


