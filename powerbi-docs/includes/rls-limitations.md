---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: 912b0213c328c623e7881f7f30fe7d67f6d889b3
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274627"
---
## <a name="limitations"></a>Beperkingen

Hierna volgen de huidige beperkingen voor de beveiliging op rijniveau in cloudmodellen:

* Als u eerder rollen en regels hebt gedefinieerd in de Power BI-service, moet u deze opnieuw maken in Power BI Desktop.

* U kunt RLS alleen definiëren in gegevenssets die zijn gemaakt met Power BI Desktop. Als u RLS wilt inschakelen voor gegevenssets die zijn gemaakt met Excel, moet u uw bestanden eerst naar PBIX-bestanden (Power BI Desktop) converteren. [Meer informatie](../connect-data/desktop-import-excel-workbooks.md).

* Alleen Import- en DirectQuery-verbindingen worden ondersteund. Live verbindingen met Analysis Services worden afgehandeld in het on-premises model.

## <a name="known-issues"></a>Bekende problemen

Er is een bekend probleem waarbij er een foutmelding optreedt wanneer u een eerder gepubliceerd rapport probeert te publiceren vanuit Power BI Desktop. Het scenario is als volgt:

1. Anna heeft een gegevensset die is gepubliceerd naar de Power BI-service en heeft RLS geconfigureerd.

1. Anna werkt het rapport bij in Power BI Desktop en publiceert het opnieuw.

1. Anna krijgt een foutmelding.

**Tijdelijke oplossing:** publiceer het Power BI Desktop-bestand opnieuw vanuit de Power BI-service totdat dit probleem is opgelost. U kunt dat doen door **Gegevensbestanden** > **ophalen** te selecteren.

