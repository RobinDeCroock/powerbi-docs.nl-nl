---
title: Overzicht van het ontwikkelaarshandboek voor Power BI Report Server
description: Welkom bij het ontwikkelaarshandboek voor Power BI Report Server, een on-premises locatie om uw Power BI-rapporten, mobiele rapporten en gepagineerde rapporten op te slaan en te beheren.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.openlocfilehash: 8fbe19beddbb95b27828ee1fae73860fe92e6b4f
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044149"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>Overzicht van het ontwikkelaarshandboek voor Power BI Report Server

Welkom bij het ontwikkelaarshandboek voor Power BI Report Server, een on-premises locatie om uw Power BI-rapporten, mobiele rapporten en gepagineerde rapporten op te slaan en te beheren.

![Overzicht van Power BI Report Server.](media/admin-handbook-overview/admin-handbook.png)

In dit handboek worden de opties besproken waarover u als ontwikkelaar beschikt om te werken met Power BI Report Server.

## <a name="embedding"></a>Insluiten

U kunt elk rapport in Power BI Report Server insluiten in een iFrame door de parameter `?rs:Embed=true` voor de querytekenreeks toe te voegen aan de URL. Deze techniek werkt voor Power BI-rapporten en voor andere rapporttypen.

### <a name="report-viewer-control"></a>Besturingselement van de rapportviewer

Voor gepagineerde rapporten kunt u profiteren van het besturingselement van de rapportviewer. Hiermee kunt u het besturingselement binnen een .NET Windows- of webtoepassing plaatsen. Zie [Get started with the Report Viewer Control](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started) (Aan de slag met het besturingselement van de rapportviewer) voor meer informatie.

## <a name="apis"></a>API's

U hebt verschillende API-opties voor interactie met Power BI Report Server. Deze techniek omvat het volgende.

* [REST-API's](rest-api.md)
* [URL-toegang](/sql/reporting-services/url-access-ssrs)
* [WMI-provider](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

U kunt ook de [open source-hulpprogramma’s van PowerShell](https://github.com/Microsoft/ReportingServicesTools) gebruiken om de rapportserver te beheren.

> [!NOTE]
> De hulpprogramma's van PowerShell bieden ondersteuning voor Power BI Desktop-bestanden (.pbix) via de -RsRest*-opdrachten.

Voer de volgende opdracht uit om te ontdekken welke opdrachten in de PowerShell-module ReportingServicesTools ondersteuning bieden voor Power BI Desktop-bestanden (.pbix).

```powershell
Get-Command -Module ReportingServicesTools -Noun RsRest*
```

## <a name="custom-extensions"></a>Aangepaste extensies

De extensiebibliotheek is een set klassen, interfaces en waardetypen die zijn opgenomen in Power BI Report Server. Deze bibliotheek biedt toegang tot systeemfuncties en is ontworpen als basis voor het gebruik van Microsoft .NET Framework-toepassingen voor het uitbreiden van Power BI Report Server-onderdelen.

U kunt verschillende typen extensies bouwen.

* Extensies voor gegevensverwerking
* Extensies voor bezorging
* Extensies voor het weergeven van gepagineerde rapporten
* Extensies voor beveiliging

Zie [Extension library](/sql/reporting-services/extensions/reporting-services-extension-library) (Extensiebibliotheek) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Get started with the Report Viewer Control](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started) (Aan de slag met het besturingselement van de rapportviewer)  
[Building Applications Using the Web Service and the .NET Framework](/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework) (Toepassingen bouwen met behulp van de webservice en .NET Framework)  
[URL-toegang](/sql/reporting-services/url-access-ssrs)  
[Extensiebibliotheek](/sql/reporting-services/extensions/reporting-services-extension-library)  
[WMI-provider](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
