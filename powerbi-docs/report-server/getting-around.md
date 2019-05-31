---
title: Inhoud beheren in de webportal van Power BI Report Server
description: Lees meer over het beheren van inhoud in de webportal van Power BI Report Server.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/24/2018
ms.author: maggies
ms.openlocfilehash: e7a9b4da760f02672f51aa7ace0f3bb19c501834
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770129"
---
# <a name="manage-content-in-the-web-portal"></a>Inhoud beheren in de webportal 
De webportal van Power BI Report Server is een on-premises locatie om uw Power BI-rapporten, mobiele rapporten en gepagineerde rapporten weer te geven, op te slaan en te beheren.

![Webportal van Report Server](media/getting-around/report-server-web-portal.png)

U kunt de webportal weergeven in elke moderne browser. Rapporten en KPI's worden in de webportal geordend in mappen. Deze kunt u markeren als favorieten. U kunt hier ook Excel-werkmappen opslaan. Vanuit de webportal kunt u de hulpprogramma's starten die u nodig hebt om rapporten te maken:

* **Power BI-rapporten** die zijn gemaakt met Power BI Desktop: Bekijk deze in het webportaal en de mobiele Power BI-apps.
* **Gepagineerde rapporten** die in Report Builder zijn gemaakt: Modern ogende documenten met vaste indeling die zijn geoptimaliseerd om af te drukken.
* **KPI's** die rechtstreeks in de webportal zijn gemaakt.

U kunt in de webportal door de mappen van de rapportserver bladeren of naar specifieke rapporten zoeken. U kunt een rapport, de algemene eigenschappen van het rapport en eerdere exemplaren van het rapport, zoals vastgelegd in de rapportgeschiedenis, weergeven. Afhankelijk van uw machtigingen kunt u zich mogelijk ook abonneren op rapporten die worden geleverd aan uw Postvak IN of een gedeelde map in het bestandssysteem.

## <a name="web-portal-roles-and-permissions"></a>Rollen en machtigingen voor de webportal
De webportaltoepassing wordt uitgevoerd in een browser. Wanneer u de webportal start, kunnen er verschillende pagina's, koppelingen en opties worden weergegeven, afhankelijk van de machtigingen die u voor de rapportserver hebt. Als u bent toegewezen aan een rol met volledige machtigingen, hebt u toegang tot alle toepassingsmenu's en pagina's voor het beheren van een rapportserver. Als u aan een rol bent toegewezen met machtigingen voor het weergeven en uitvoeren van rapporten, worden alleen de menu's en pagina's weergegeven die u nodig hebt voor deze activiteiten. Het is mogelijk dat er verschillende rollen aan u zijn toegewezen voor verschillende rapportservers of zelfs voor verschillende rapporten en mappen op één rapportserver.

## <a name="start-the-web-portal"></a>De webportal starten
1. Open uw webbrowser.
   
    Zie de lijst met [ondersteunde webbrowsers en versies](browser-support.md).
2. Typ de URL van de webportal in de adresbalk.
   
    De standaard-URL is <em>http://[computernaam]/reports</em>.
   
    De rapportserver is mogelijk zo geconfigureerd dat een specifieke poort moet worden gebruikt. Bijvoorbeeld <em>http://[computernaam]:80/reports</em> of <em>http://[computernaam]:8080/reports</em>
   
    Zoals u ziet, worden de webportalitems gegroepeerd in de volgende categorieën:
   
   * KPI's
   * Mobiele rapporten
   * Gepagineerde rapporten
   * Power BI Desktop-rapporten
   * Excel-werkmappen
   * Gegevenssets
   * Gegevensbronnen
   * Resources

## <a name="manage-items-in-the-web-portal"></a>Items beheren in de webportal
Met Power BI Report Server hebt u gedetailleerde controle over de items die u op de webportal opslaat. U kunt bijvoorbeeld abonnementen, caching, momentopnamen en de beveiliging voor afzonderlijke gepagineerde rapporten instellen.

1. Selecteer in de rechterbovenhoek van een item het weglatingsteken (...) en selecteer vervolgens **Beheren**.
   
    ![Beheren selecteren](media/getting-around/report-server-web-portal-manage-ellipsis.png)
2. Kies de eigenschap of andere functie die u wilt instellen.
   
    ![Een eigenschap selecteren](media/getting-around/report-server-web-portal-manage-properties.png)
3. Selecteer **Toepassen**.

Meer informatie over het [werken met abonnementen in de webportal](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal).

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI Report Server?](get-started.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

