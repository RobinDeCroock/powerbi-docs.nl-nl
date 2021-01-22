---
title: Power BI en uitgaand Azure-verkeer
description: De kosten voor uitgaand Azure-verkeer, Power BI op basis van tenantlocatie en Power BI Premium begrijpen
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Data from databases
ms.openlocfilehash: ec47968294e0fd905d1733bdb30ae1840069aed7
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597472"
---
# <a name="power-bi-and-azure-egress"></a>Power BI en uitgaand Azure-verkeer

Voor gegevens die uit Azure-datacentrums worden verplaatst (uitgaand), kunnen bandbreedtekosten in rekening worden gebracht. Wanneer u Power BI gebruikt met Azure-gegevensbronnen, kunt u kosten voor uitgaand Azure-verkeer voorkomen. Zorg er hiertoe voor dat uw Power BI-tenant zich in dezelfde regio bevindt als uw Azure-gegevensbronnen.

Wanneer uw Power BI-tenant is geïmplementeerd in dezelfde Azure-regio als die waarin u uw gegevensbronnen implementeert, worden er geen kosten voor uitgaand verkeer voor geplande vernieuwing en DirectQuery-interacties in rekening gebracht. 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Bepalen waar uw Power BI-tenant zich bevindt

Zie het artikel [Waar bevindt mijn Power BI-tenant zich?](../admin/service-admin-where-is-my-tenant-located.md) als u wilt weten waar uw Power BI-tenant zich bevindt.

Voor klanten van Power BI Premium Multi-Geo: als uw Power BI-tenant zich niet op de optimale locatie voor sommige van uw Azure-gegevensbronnen bevindt, kunt u Power BI Premium Multi-Geo implementeren in de gewenste Azure-regio en ervan profiteren dat uw Power BI-tenant en Azure-gegevensbronnen zich in dezelfde Azure-regio bevinden.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over Power BI Premium of Multi-Geo:

* [Details over Azure-prijzen voor bandbreedte](https://azure.microsoft.com/pricing/details/bandwidth/)
* [Wat is Microsoft Power BI Premium?](../admin/service-premium-what-is.md)
* [Power BI Premium aanschaffen](../admin/service-admin-premium-purchase.md)
* [Ondersteuning voor Multi-Geo voor Power BI Premium (preview-versie)](../admin/service-admin-premium-multi-geo.md)
* [Waar bevindt mijn Power BI-tenant zich?](../admin/service-admin-where-is-my-tenant-located.md)
* [Veelgestelde vragen over Power BI Premium](../admin/service-premium-faq.md)
