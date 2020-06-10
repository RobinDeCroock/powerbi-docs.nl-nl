---
title: Vertrouwelijkheidslabels voor gegevens inschakelen in Power BI
description: Informatie over het inschakelen van vertrouwelijkheidslabels voor gegevens in Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315644"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels voor gegevens inschakelen in Power BI

Als u [Microsoft Information Protection-gegevensvertrouwelijkheidslabels](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) wilt gebruiken in Power BI, moeten ze zijn ingeschakeld op de tenant. In dit artikel wordt aan Power BI-tenantbeheerders uitgelegd hoe dit te doen. Zie [Overzicht van gegevensbescherming in Power BI](service-security-data-protection-overview.md) voor een overzicht van gegevensvertrouwelijkheidslabels in Power BI. Zie [Vertrouwelijkheidslabels toepassen](../collaborate-share/service-security-apply-data-sensitivity-labels.md) voor informatie over het toepassen van vertrouwelijkheidslabels in Power BI 

Wanneer vertrouwelijkheidslabels zijn ingeschakeld:

* Bepaalde gebruikers en beveiligingsgroepen in een organisatie kunnen [vertrouwelijkheidslabels classificeren en toepassen](../collaborate-share/service-security-apply-data-sensitivity-labels.md) op hun Power BI-dashboards, -rapporten, -gegevenssets en -gegevensstromen.
* Alle leden van de organisatie kunnen die labels zien.

Voor het inschakelen van vertrouwelijkheidslabels voor gegevens is een Azure Information Protection-licentie vereist. Zie [Licenties](service-security-data-protection-overview.md#licensing) voor meer informatie.

## <a name="enable-data-sensitivity-labels"></a>Vertrouwelijkheidslabels voor gegevens inschakelen

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

* U beschikt niet over een Azure Information Protection-[licentie](service-security-data-protection-overview.md#licensing).
* De vertrouwelijkheidslabels zijn niet gemigreerd naar de Microsoft Information Protection-versie die wordt ondersteund door Power BI. Krijg meer informatie over [het migreren van vertrouwelijkheidslabels](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Er zijn geen Microsoft Information Protection-vertrouwelijkheidslabels gedefinieerd in de organisatie. Let op: een label moet onderdeel zijn van een gepubliceerd beleid om te kunnen worden gebruikt. [Krijg meer informatie over vertrouwelijkheidslabels](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) of ga naar het [Microsoft-beveiligings- en compliancecentrum](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) voor meer informatie over het definiëren van labels en het publiceren van beleidsregels voor uw organisatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

De volgende lijst biedt een aantal beperkingen van vertrouwelijkheidslabels in Power BI:

**Algemeen**
* Vertrouwelijkheidslabels kunnen alleen worden toegepast op dashboards, rapporten, gegevenssets en gegevensstromen. Ze zijn momenteel niet beschikbaar voor [gepagineerde rapporten](../paginated-reports/report-builder-power-bi.md) en werkmappen.
* Vertrouwelijkheidslabels op Power BI-assets zijn zichtbaar in de werkruimtelijst en de weergaven Herkomst, Favorieten, Recente items en Apps; labels zijn momenteel niet zichtbaar in de weergave Gedeeld met mij. Houd er echter rekening mee dat een label dat op een Power BI-asset is toegepast, zelfs als dit niet zichtbaar is, permanent worden toegevoegd aan de gegevens die naar Excel-, PowerPoint- en PDF-bestanden worden geëxporteerd.
* Vertrouwelijkheidslabels worden alleen ondersteund voor tenants in de wereldwijde (openbare) cloud. Vertrouwelijkheidslabels worden niet ondersteund voor tenants in andere clouds.
* Vertrouwelijkheidslabels voor gegevens worden niet ondersteund voor sjabloon-apps. Gevoeligheidslabels die door de maker van de sjabloon-app zijn ingesteld, worden verwijderd wanneer de app wordt uitgepakt en geïnstalleerd, en gevoeligheidslabels die door gebruikers van de app aan artefacten in een geïnstalleerde sjabloon-app zijn toegevoegd, gaan verloren (opnieuw ingesteld op niets) wanneer de app wordt bijgewerkt.
* Power BI biedt geen ondersteuning voor vertrouwelijkheidslabels van de beveiligingstypen [Niet doorsturen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Door de gebruiker gedefinieerd](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) en [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). De beveiligingstypen Niet doorsturen en Door de gebruiker gedefinieerd verwijzen naar labels die zijn gedefinieerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).
* U wordt afgeraden gebruikers toe te staan om bovenliggende labels toe te passen in Power BI. Als een bovenliggend label wordt toegepast op inhoud, mislukt het exporteren van gegevens van die inhoud naar een bestand (Excel, PowerPoint en PDF). Zie [Sublabels (labels groeperen)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Exporteren**
* Besturingselementen voor labels en beveiliging worden alleen afgedwongen wanneer gegevens worden geëxporteerd naar Excel-, PowerPoint-en PDF-bestanden. Labels en beveiliging worden niet afgedwongen wanneer gegevens worden geëxporteerd naar CSV- of PBIX-bestanden, Analyseren in Excel of een ander exportpad.
* Bij het toepassen van een vertrouwelijkheidslabel en beveiliging op een geëxporteerd bestand wordt geen markering van inhoud toegevoegd aan het bestand. Als het label echter is geconfigureerd voor het toepassen van inhoudsmarkeringen, worden ze automatisch toegepast door de Azure Information Protection Unified labeling-client wanneer het bestand wordt geopend in Office-bureaublad-apps. De inhoudsmarkeringen worden niet automatisch toegepast wanneer u ingebouwde labels gebruikt voor desktop-, mobiele of web-apps. Zie [Wanneer Office-apps inhoud markeren en versleutelen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) voor meer details.
* Een gebruiker die een bestand uit Power BI exporteert, beschikt over machtigingen voor toegang tot en het bewerken van dat bestand volgens de instellingen voor het vertrouwelijkheidslabel. De gebruiker die de gegevens exporteert, krijgt geen eigenaarsmachtigingen voor het bestand.
* Het exporteren mislukt als een label niet kan worden toegepast wanneer gegevens naar een bestand worden geëxporteerd. Als u wilt controleren of het exporteren is mislukt omdat het label niet kan worden toegepast, klikt u op de naam van het rapport of het dashboard in het midden van de titelbalk en kijkt u of de tekst Vertrouwelijkheidslabel kan niet worden geladen in de info-vervolgkeuzelijst wordt weergegeven. Dit kan gebeuren als het toegepaste label niet is gepubliceerd of verwijderd door de beveiligingsbeheerder of als gevolg van een tijdelijk systeemprobleem.

## <a name="next-steps"></a>Volgende stappen

In dit artikel is beschreven hoe u vertrouwelijkheidslabels voor gegevens in Power BI kunt inschakelen. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Overzicht van gegevensbeveiliging in Power BI](service-security-data-protection-overview.md)
* [Vertrouwelijkheidslabels voor gegevens toepassen in Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Metrisch rapport gegevensbescherming](service-security-data-protection-metrics-report.md)