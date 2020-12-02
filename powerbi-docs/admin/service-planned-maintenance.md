---
title: Gepland onderhoud van Power BI
description: Informatie voor beheerders over hoe gepland onderhoud voor Power BI van invloed is op de organisatie en de volgende stappen die ze moeten uitvoeren.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/30/2020
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: d62b06e23f7e97141f6d10451e9d75f8fb9e417e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412317"
---
# <a name="power-bi-planned-maintenance"></a>Gepland onderhoud van Power BI

Gepland onderhoud voor de Power BI-service is een vereist onderdeel van onze toezegging voor het leveren van een betrouwbaar product aan onze klanten. Wanneer gepland onderhoud plaatsvindt, zal de Power BI-service enige tijd niet beschikbaar zijn voor uw organisatie. Gebruikers kunnen mogelijk geen toegang krijgen tot de Power BI-service en de achtergrondbewerkingen zijn mogelijk niet geslaagd. Na het onderhoudsvenster verwachten we dat de service normaal werkt en interactieve en achtergrondbewerkingen worden uitgevoerd.  

Het onderhoud is gepland om te worden uitgevoerd buiten de normale kantooruren om de gevolgen voor uw organisatie tot een minimum te beperken. Voor organisaties die gebruikers over de hele wereld hebben, herkennen we dat "buiten de normale kantooruren" niet voor iedereen hetzelfde is. Wij bieden onze excuses aan voor eventuele overlast voor uw gebruikers. We werken hard om Power BI te verbeteren en om deze onderhoudsvensters te minimaliseren.

Als uw organisatie wordt beïnvloed, wordt u hiervan op de hoogte gesteld. Microsoft 365-beheerders zien een waarschuwend bericht in het Microsoft 365 Message Center en ontvangen een e-mail. Daarnaast worden klanten met Premier Support-contracten hiervan op de hoogte gebracht via hun Microsoft-accountteam.

## <a name="actions-to-take-now"></a>Acties die nu moeten worden uitgevoerd

* Microsoft 365-beheerders moeten [Message Center controleren](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) op berichten over gepland onderhoud voor Power BI. Deel het bericht met personen die op de hoogte moeten zijn, maar mogelijk geen toegang hebben tot Message Center.
* Als u geen Microsoft 365-beheerder bent, neemt u contact op met uw IT-afdeling of uw interne ondersteuningsteams om u te informeren over onderhoudswerkzaamheden.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Te ondernemen acties wanneer onderhoud is voltooid

* Gebruikers moeten geopende browservensters vernieuwen.
* Power BI-Mobiel-appgebruikers moeten controleren of ze de meest recente versie gebruiken en zich vervolgens weer aanmelden bij de app. Controleer de App Store van uw telefoon of controleer onze pagina [Power BI-Mobiel](https://powerbi.microsoft.com/mobile/).
* Klanten die actief rapporten bijwerken of publiceren die organisatorische visuals gebruiken, lokaal of van OneDrive en SharePoint-locaties, moeten de visual opnieuw importeren via de visual store van de organisatie of een bijgewerkte PBIX downloaden voordat ze opnieuw worden gepubliceerd. Zie [Organisatievisuals](organizational-visuals.md) voor meer informatie over aangepaste visuals voor organisaties.
* Als Excel-werkmappen die gebruikmaken van de functie Analyseren in Excel niet worden vernieuwd, moet u mogelijk de verbindingsreeks bijwerken of de ODC-verbinding voor die gegevensset opnieuw downloaden. Zie [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data) voor meer informatie.
* Koppelingen naar Power BI Embedded in de inhoud kunnen mogelijk niet worden verbonden wanneer het onderhoud is voltooid. Een ingesloten koppeling in SharePoint of Teams kan bijvoorbeeld een gebruikersfout veroorzaken. Om dit probleem op te lossen, moet u de ingesloten koppeling opnieuw genereren in Power BI en vervolgens de locaties bijwerken waar ze worden gebruikt. Zie voor meer informatie over ingesloten koppelingen [Een rapportwebonderdeel insluiten in SharePoint Online](../collaborate-share/service-embed-report-spo.md) en [Samenwerken in Microsoft Teams met Power BI](../collaborate-share/service-collaborate-microsoft-teams.md).
* Een aantal gebruiksgegevens die voor de onderhoudswerkzaamheden zijn verzameld, zijn niet beschikbaar nadat die werkzaamheden zijn uitgevoerd. Deze gebruiksgegevens bestaan onder andere uit:

  * [Power BI-activiteitenlogboek](service-admin-auditing.md#use-the-activity-log). Gebruikers moet activiteitenlogboeken downloaden voordat het onderhoud wordt uitgevoerd. U kunt ook de [Office 365-controlelogboekgegevens](service-admin-auditing.md#access-your-audit-logs) gebruiken om vergelijkbare activiteitsgegevens te krijgen.
  * Aantal weergaven in [lineaire weergave](../collaborate-share/service-data-lineage.md#explore-lineage-view)
  * [Metrisch rapport gegevensbescherming](service-security-data-protection-metrics-report.md)
  * [Metrische gegevens over het gebruik (preview-versie)](../collaborate-share/service-modern-usage-metrics.md)

## <a name="next-steps"></a>Volgende stappen

* [Meldingen over onderbrekingen van de service inschakelen](service-interruption-notifications.md)
* [Toekomstige wijzigingen bijhouden in Message Center](/microsoft-365/admin/manage/message-center)