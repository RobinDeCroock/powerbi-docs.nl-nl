---
title: Vertrouwelijkheidslabels inschakelen in Power BI
description: Meer informatie over het inschakelen van vertrouwelijkheidslabels in Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/06/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 0fe1b7b1b8175511838005b7b63ca7543bbf939a
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034331"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels inschakelen in Power BI

Als u [vertrouwelijkheidslabels voor Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) wilt gebruiken in Power BI, moeten ze zijn ingeschakeld op de tenant. In dit artikel wordt aan Power BI-tenantbeheerders uitgelegd hoe dit te doen. Zie [Vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md) voor een overzicht van vertrouwelijkheidslabels in Power BI. Zie [Vertrouwelijkheidslabels toepassen](./service-security-apply-data-sensitivity-labels.md) voor informatie over het toepassen van vertrouwelijkheidslabels in Power BI 

Wanneer vertrouwelijkheidslabels zijn ingeschakeld:

* Bepaalde gebruikers en beveiligingsgroepen in een organisatie kunnen [vertrouwelijkheidslabels classificeren en toepassen](./service-security-apply-data-sensitivity-labels.md) op hun Power BI-dashboards, -rapporten, -gegevenssets en -gegevensstromen.
* Alle leden van de organisatie kunnen die labels zien.

Voor het inschakelen van vertrouwelijkheidslabels is een Azure Information Protection-licentie vereist. Zie [Licenties](service-security-sensitivity-label-overview.md#licensing) voor meer informatie.

## <a name="enable-sensitivity-labels"></a>Vertrouwelijkheidslabels inschakelen

Ga naar de Power BI-**beheerportal**, open het deelvenster **Tenant** en zoek de sectie **Informatiebeveiliging**.

![De sectie Information Protection zoeken](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Voer in de sectie **Information Protection** de volgende stappen uit:
1. Open **Gebruikers toestaan om vertrouwelijkheidslabels toe te passen op Power BI-inhoud**.
1. Schakel de wisselknop in.
1. Definieer wie vertrouwelijkheidslabels in Power BI-assets kan toepassen en wijzigen. Standaard kan iedereen in uw organisatie vertrouwelijkheidslabels toepassen. U kunt er echter voor kiezen om vertrouwelijkheidslabels alleen voor specifieke gebruikers of beveiligingsgroepen in te stellen. Zodra u ofwel de gehele organisatie of specifieke beveiligingsgroepen hebt geselecteerd, kunt u specifieke subsets van gebruikers of beveiligingsgroepen uitsluiten.
   
   * Wanneer vertrouwelijkheidslabels zijn ingeschakeld voor de gehele organisatie, worden uitzonderingen doorgaans gevormd door beveiligingsgroepen.
   * Wanneer vertrouwelijkheidslabels alleen zijn ingeschakeld voor specifieke gebruikers of beveiligingsgroepen, vormen specifieke gebruikers doorgaans de uitzondering.  
    Dankzij deze methode is het mogelijk om te voorkomen dat bepaalde gebruikers vertrouwelijkheidslabels kunnen toepassen in Power BI, zelfs als ze deel uitmaken van een groep die wel machtigingen heeft om dit te doen.

1. Druk op **Toepassen**.

![Vertrouwelijkheidslabels inschakelen](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Alleen Power BI Pro-gebruikers die over machtigingen beschikken voor het *maken*  en *bewerken* van de asset en die deel uitmaken van de relevante beveiligingsgroep die in deze sectie is ingesteld, kunnen de vertrouwelijkheidslabels instellen en bewerken. Gebruikers die geen deel uitmaken van deze groep kunnen het label niet instellen of bewerken.  

## <a name="troubleshooting"></a>Problemen oplossen

Power BI maakt gebruik van vertrouwelijkheidslabels voor Microsoft Information Protection. Als u dus een foutbericht krijgt wanneer u vertrouwelijkheidslabels inschakelt, kan dit een van de volgende redenen hebben:

* U beschikt niet over een Azure Information Protection-[licentie](service-security-sensitivity-label-overview.md#licensing).
* De vertrouwelijkheidslabels zijn niet gemigreerd naar de Microsoft Information Protection-versie die wordt ondersteund door Power BI. Krijg meer informatie over [het migreren van vertrouwelijkheidslabels](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Er zijn geen Microsoft Information Protection-vertrouwelijkheidslabels gedefinieerd in de organisatie. Let op: een label moet onderdeel zijn van een gepubliceerd beleid om te kunnen worden gebruikt. [Krijg meer informatie over vertrouwelijkheidslabels](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) of ga naar het [Microsoft-beveiligings- en compliancecentrum](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) voor meer informatie over het definiëren van labels en het publiceren van beleidsregels voor uw organisatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Zie [Vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md#limitations) voor de lijst met beperkingen voor vertrouwelijkheidslabels in Power BI.

## <a name="next-steps"></a>Volgende stappen

In dit artikel wordt beschreven hoe u vertrouwelijkheidslabels in Power BI kunt inschakelen. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Overzicht van vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md)
* [Vertrouwelijkheidslabels toepassen in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport met metrische gegevens voor beveiliging](service-security-data-protection-metrics-report.md)