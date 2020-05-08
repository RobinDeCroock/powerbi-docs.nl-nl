---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464360"
---
## <a name="limitations"></a>Beperkingen

Hierna volgen de huidige beperkingen voor de beveiliging op rijniveau in cloudmodellen:

* Als u eerder rollen en regels hebt gedefinieerd in de Power BI-service, moet u deze opnieuw maken in Power BI Desktop.

* U kunt RLS alleen definiëren in gegevenssets die zijn gemaakt met Power BI Desktop. Als u RLS wilt inschakelen voor gegevenssets die zijn gemaakt met Excel, moet u uw bestanden eerst naar PBIX-bestanden (Power BI Desktop) converteren. [Meer informatie](../desktop-import-excel-workbooks.md).

* Alleen Import- en DirectQuery-verbindingen worden ondersteund. Live verbindingen met Analysis Services worden afgehandeld in het on-premises model.

## <a name="known-issues"></a>Bekende problemen

Er is een bekend probleem waarbij er een foutmelding optreedt wanneer u een eerder gepubliceerd rapport probeert te publiceren vanuit Power BI Desktop. Het scenario is als volgt:

1. Anna heeft een gegevensset die is gepubliceerd naar de Power BI-service en heeft RLS geconfigureerd.

1. Anna werkt het rapport bij in Power BI Desktop en publiceert het opnieuw.

1. Anna krijgt een foutmelding.

**Tijdelijke oplossing:** publiceer het Power BI Desktop-bestand opnieuw vanuit de Power BI-service totdat dit probleem is opgelost. U kunt dat doen door **Gegevensbestanden** > **ophalen** te selecteren.
