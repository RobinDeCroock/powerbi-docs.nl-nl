---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: b2be085c48b303304d46ea93c272e6a860143c51
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074843"
---
## <a name="limitations"></a>Beperkingen

Hier volgt een lijst van de huidige beperkingen voor beveiliging op rijniveau voor cloudmodellen.

* Als u eerder rollen en regels hebt gedefinieerd in de Power BI-service, moet u deze opnieuw maken in Power BI Desktop.

* U kunt RLS alleen definiëren in gegevenssets die zijn gemaakt met Power BI Desktop. Als u RLS wilt inschakelen voor gegevenssets die zijn gemaakt met Excel, moet u uw bestanden eerst naar PBIX-bestanden (Power BI Desktop) converteren. [Meer informatie](../desktop-import-excel-workbooks.md)

* Alleen ETL- en DirectQuery-verbindingen worden ondersteund. Live verbindingen met Analysis Services worden afgehandeld in het on-premises model.

* Cortana wordt op dit moment niet ondersteund met RLS.

## <a name="known-issues"></a>Bekende problemen

Er is een bekend probleem waarbij er een foutmelding optreedt wanneer u een eerder gepubliceerd rapport probeert te publiceren vanuit Power BI Desktop. Het scenario is als volgt.

1. Anna heeft een gegevensset die is gepubliceerd naar de Power BI-service en heeft RLS geconfigureerd.

1. Anna werkt het rapport bij in Power BI Desktop en publiceert het opnieuw.

1. Anna krijgt een foutmelding.

**Tijdelijke oplossing:** Publiceer het Power BI Desktop-bestand opnieuw vanuit de Power BI-service totdat dit probleem is opgelost. U kunt dat doen door **Gegevensbestanden** > **ophalen** te selecteren.
