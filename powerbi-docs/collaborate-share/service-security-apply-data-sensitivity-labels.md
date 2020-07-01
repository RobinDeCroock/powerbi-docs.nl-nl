---
title: Vertrouwelijkheidslabels toepassen in Power BI
description: Meer informatie over het toepassen van vertrouwelijkheidslabels op gegevens in Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: c193c6b3397d8e47bed40cb65e5fc60e4fec9323
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85225299"
---
# <a name="apply-data-sensitivity-labels-in-power-bi"></a>Vertrouwelijkheidslabels voor gegevens toepassen in Power BI

Vertrouwelijkheidslabels voor Microsoft Information Protection voor uw rapporten, dashboards, gegevenssets en gegevensstromen kunnen uw gevoelige inhoud beschermen tegen ongeautoriseerde toegang tot gegevens en lekkage. Door uw gegevens op de juiste manier te labelen met vertrouwelijkheidslabels voor gegevens, zorgt u ervoor dat alleen bevoegde personen toegang tot uw gegevens hebben. In dit artikel ziet u hoe u vertrouwelijkheidslabels op uw inhoud kunt toepassen.

Vertrouwelijkheidslabels toepassen in Power BI:
* U moet over een Power BI Pro-licentie en machtigingen voor bewerken beschikken voor de inhoud die u van een label wilt voorzien.
* U moet bij een beveiligingsgroep horen die machtigingen heeft om vertrouwelijkheidslabels voor gegevens toe te passen, zoals beschreven in het artikel [Vertrouwelijkheidslabels voor gegevens inschakelen in Power BI](../admin/service-security-enable-data-sensitivity-labels.md#enable-data-sensitivity-labels).
* Aan alle [vereisten](../admin/service-security-data-protection-overview.md#requirements-for-using-sensitivity-labels-in-power-bi) en [licentievereisten](../admin/service-security-data-protection-overview.md#licensing) moet zijn voldaan.

Zie [Overzicht van gegevensbescherming in Power BI](../admin/service-security-data-protection-overview.md) voor meer informatie over gegevensvertrouwelijkheidslabels in Power BI.

## <a name="applying-sensitivity-labels"></a>Vertrouwelijkheidslabels toepassen

Wanneer gegevensbeveiliging is ingeschakeld op uw tenant, worden vertrouwelijkheidslabels weergegeven in de kolom Vertrouwelijkheid in de lijstweergave van dashboards, rapporten, gegevenssets en gegevensstromen.

![Vertrouwelijkheidslabels voor gegevens inschakelen](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Een vertrouwelijkheidslabel toepassen of wijzigen op een rapport of dashboard**
1. Klik op **Meer opties (...)** .
1. Selecteer **Instellingen**.
1. Kies in het deelvenster van de instellingen het juiste vertrouwelijkheidslabel.
1. Sla de instellingen op.

In de volgende afbeelding ziet u deze stappen in een rapport

![Vertrouwelijkheidslabels voor gegevens instellen](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Een vertrouwelijkheidslabel op een gegevensset of gegevensstroom toepassen of wijzigen**

1. Klik op **Meer opties (...)** .
1. Selecteer **Instellingen**.
1. Kies in het deelvenster van de instellingen het juiste vertrouwelijkheidslabel.
1. Pas de instellingen toe.

De volgende twee afbeeldingen illustreren deze stappen voor een gegevensset.

Kies **Meer opties (...)** en klik vervolgens op **Instellingen**.

![Gegevenssetinstellingen openen](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

Op de pagina Instellingen opent u de sectie Vertrouwelijkheidslabels, kiest u het gewenste vertrouwelijkheidslabel en klikt u op **Toepassen**.

![Vertrouwelijkheidslabel kiezen](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="removing-sensitivity-labels"></a>Vertrouwelijkheidslabels verwijderen
Als u een vertrouwelijkheidslabel wilt verwijderen uit een rapport, dashboard, gegevensset of gegevensstroom, volgt u de [dezelfde procedure als wordt gebruikt voor het toepassen van labels](#applying-sensitivity-labels), maar kiest u **(Geen)** wanneer u wordt gevraagd de vertrouwelijkheid van de gegevens te classificeren. 

## <a name="data-protection-in-exported-files"></a>Gegevensbeveiliging in geëxporteerde bestanden

De gegevensbescherming die is gekoppeld aan vertrouwelijkheidslabels wordt alleen toegepast op gegevens wanneer Excel-, PowerPoint- en PDF-bestanden worden geëxporteerd. Het wordt niet ondersteund voor analyseren in Excel, exporteren naar .csv, dataset downloads (.pbix), Power BI Service Live Connect of een andere exportindeling. Opties voor gegevensexport worden beheerd door Power BI tenantbeheerder [instellingen exporteren](../service-admin-portal.md#export-and-sharing-settings).

Wanneer u [gegevens exporteert uit een rapport](https://docs.microsoft.com/power-bi/consumer/end-user-export) dat van een vertrouwelijkheidslabel voor een Excel-, PowerPoint- of PDF-bestand is voorzien, wordt het vertrouwelijkheidslabel overgenomen door het gegenereerde bestand. Het vertrouwelijkheidslabel wordt zichtbaar in het bestand en toegang tot het bestand wordt beperkt tot alleen gebruikers die over de juiste machtigingen beschikken.

![Vertrouwelijkheidslabels voor gegevens in gebruik](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-04b.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

De volgende lijst biedt een aantal beperkingen van vertrouwelijkheidslabels in Power BI:

**Algemeen**
* Vertrouwelijkheidslabels kunnen alleen worden toegepast op dashboards, rapporten, gegevenssets en gegevensstromen. Ze zijn momenteel niet beschikbaar voor [gepagineerde rapporten](../paginated-reports/report-builder-power-bi.md) en werkmappen.
* Vertrouwelijkheidslabels op Power BI-assets zijn zichtbaar in de werkruimtelijst en de weergaven Herkomst, Favorieten, Recente items en Apps; labels zijn momenteel niet zichtbaar in de weergave Gedeeld met mij. Houd er echter rekening mee dat een label dat op een Power BI-asset is toegepast, zelfs als dit niet zichtbaar is, permanent worden toegevoegd aan de gegevens die naar Excel-, PowerPoint- en PDF-bestanden worden geëxporteerd.
* Vertrouwelijkheidslabels worden alleen ondersteund voor tenants in de wereldwijde (openbare) cloud. Vertrouwelijkheidslabels worden niet ondersteund voor tenants in andere clouds.
* Vertrouwelijkheidslabels voor gegevens worden niet ondersteund voor sjabloon-apps. Gevoeligheidslabels die door de maker van de sjabloon-app zijn ingesteld, worden verwijderd wanneer de app wordt uitgepakt en geïnstalleerd, en gevoeligheidslabels die door gebruikers van de app aan artefacten in een geïnstalleerde sjabloon-app zijn toegevoegd, gaan verloren (opnieuw ingesteld op niets) wanneer de app wordt bijgewerkt.
* Power BI biedt geen ondersteuning voor vertrouwelijkheidslabels van de beveiligingstypen [Niet doorsturen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Door de gebruiker gedefinieerd](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) en [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). De beveiligingstypen Niet doorsturen en Door de gebruiker gedefinieerd verwijzen naar labels die zijn gedefinieerd in het [Microsoft 365-beveiligingscentrum](https://security.microsoft.com/) of het [Microsoft 365-compliancecentrum](https://compliance.microsoft.com/).

**Exporteren**
* Besturingselementen voor labels en beveiliging worden alleen afgedwongen wanneer gegevens worden geëxporteerd naar Excel-, PowerPoint-en PDF-bestanden. Labels en beveiliging worden niet afgedwongen wanneer gegevens worden geëxporteerd naar CSV- of PBIX-bestanden, Analyseren in Excel of een ander exportpad.
* Bij het toepassen van een vertrouwelijkheidslabel en beveiliging op een geëxporteerd bestand wordt geen markering van inhoud toegevoegd aan het bestand. Als het label echter is geconfigureerd voor het toepassen van inhoudsmarkeringen, worden ze automatisch toegepast door de Azure Information Protection Unified labeling-client wanneer het bestand wordt geopend in Office-bureaublad-apps. De inhoudsmarkeringen worden niet automatisch toegepast wanneer u ingebouwde labels gebruikt voor desktop-, mobiele of web-apps. Zie [Wanneer Office-apps inhoud markeren en versleutelen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) voor meer details.
* Een gebruiker die een bestand uit Power BI exporteert, beschikt over machtigingen voor toegang tot en het bewerken van dat bestand volgens de instellingen voor het vertrouwelijkheidslabel. De gebruiker die de gegevens exporteert, krijgt geen eigenaarsmachtigingen voor het bestand.
* Het exporteren mislukt als een label niet kan worden toegepast wanneer gegevens naar een bestand worden geëxporteerd. Als u wilt controleren of het exporteren is mislukt omdat het label niet kan worden toegepast, klikt u op de naam van het rapport of het dashboard in het midden van de titelbalk en kijkt u of de tekst Vertrouwelijkheidslabel kan niet worden geladen in de info-vervolgkeuzelijst wordt weergegeven. Dit kan gebeuren als het toegepaste label niet is gepubliceerd of verwijderd door de beveiligingsbeheerder of als gevolg van een tijdelijk systeemprobleem.

## <a name="next-steps"></a>Volgende stappen

In dit artikel is beschreven hoe u vertrouwelijkheidslabels voor gegevens in Power BI kunt toepassen. De volgende artikelen bieden meer informatie over gegevensbeveiliging in Power BI. 

* [Overzicht van gegevensbeveiliging in Power BI](../admin/service-security-data-protection-overview.md)
* [Vertrouwelijkheidslabels voor gegevens inschakelen in Power BI](../admin/service-security-enable-data-sensitivity-labels.md)
* [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md)