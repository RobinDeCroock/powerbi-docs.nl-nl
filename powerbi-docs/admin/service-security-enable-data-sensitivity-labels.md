---
title: Vertrouwelijkheidslabels inschakelen in Power BI
description: Meer informatie over het inschakelen van vertrouwelijkheidslabels in Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/10/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: afe81469bc3ce67979602eedbf49b00cf7a3f1e6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90854305"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels inschakelen in Power BI

Als u [vertrouwelijkheidslabels voor Microsoft Information Protection](/microsoft-365/compliance/sensitivity-labels) wilt gebruiken in Power BI, moeten ze zijn ingeschakeld op de tenant. In dit artikel wordt aan Power BI-tenantbeheerders uitgelegd hoe dit te doen. Zie [Vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md) voor een overzicht van vertrouwelijkheidslabels in Power BI. Zie [Vertrouwelijkheidslabels toepassen](./service-security-apply-data-sensitivity-labels.md) voor informatie over het toepassen van vertrouwelijkheidslabels in Power BI 

Wanneer vertrouwelijkheidslabels zijn ingeschakeld:

* Bepaalde gebruikers en beveiligingsgroepen in een organisatie kunnen [vertrouwelijkheidslabels classificeren en toepassen](./service-security-apply-data-sensitivity-labels.md) op hun Power BI-dashboards, -rapporten, -gegevenssets en -gegevensstromen.
* Alle leden van de organisatie kunnen die labels zien.

Voor het inschakelen van vertrouwelijkheidslabels is een Azure Information Protection-licentie vereist. Zie [Licenties en vereisten](#licensing-and-requirements) voor meer details.

## <a name="licensing-and-requirements"></a>Licenties en vereisten

* Voor het toepassen en weergeven van Microsoft Information Protection-vertrouwelijkheidslabels in Power BI is een Azure Information Protection Premium P1- of Premium P2-licentie vereist. Azure Information Protection kan hetzij als zelfstandig product of via een van de Microsoft-licentiesuites worden aangeschaft. Zie [Prijzen voor Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) voor meer informatie.

* Als gebruikers labels willen toepassen op Power BI-inhoud, moeten ze naast een van de bovenstaande Azure Information Protection-licenties ook over een Power BI Pro-licentie beschikken.

* Office-apps hebben hun eigen [licentievereisten voor het weergeven en toepassen van vertrouwelijkheidslabels]( https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels ).

* Voordat u vertrouwelijkheidslabels toepast op de tenant, moet u controleren of vertrouwelijkheidslabels zijn gedefinieerd en gepubliceerd voor relevante gebruikers en groepen. Zie [Vertrouwelijkheidslabels en bijbehorend beleid maken en configureren](/microsoft-365/compliance/create-sensitivity-labels?view=o365-worldwide) voor meer details.

>[!NOTE]
> Als uw organisatie gebruikmaakt van vertrouwelijkheidslabels van Azure Information Protection, moeten deze worden gemigreerd naar het Microsoft Information Protection Unified Labeling-platform om te kunnen worden gebruikt in Power BI. [Meer informatie over het migreren van vertrouwelijkheidslabels](/azure/information-protection/configure-policy-migrate-labels).

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

* U beschikt niet over een Azure Information Protection-[licentie](#licensing-and-requirements).
* De vertrouwelijkheidslabels zijn niet [gemigreerd](#enable-sensitivity-labels) naar de Microsoft Information Protection-versie die wordt ondersteund in Power BI.
* Er zijn geen Microsoft Information Protection-vertrouwelijkheidslabels [gedefinieerd in de organisatie](#enable-sensitivity-labels).

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Zie [Vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md#limitations) voor de lijst met beperkingen voor vertrouwelijkheidslabels in Power BI.

## <a name="next-steps"></a>Volgende stappen

In dit artikel wordt beschreven hoe u vertrouwelijkheidslabels in Power BI kunt inschakelen. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Overzicht van vertrouwelijkheidslabels in Power BI](service-security-sensitivity-label-overview.md)
* [Vertrouwelijkheidslabels toepassen in Power BI](./service-security-apply-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Rapport met metrische gegevens voor beveiliging](service-security-data-protection-metrics-report.md)