---
title: Browserondersteuning voor Power BI Report Server
description: Meer informatie over welke browserversies worden ondersteund voor het beheren en weergeven van Power BI Report Server en de besturingselementen van de rapportviewer.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 724bd7a9a11c42520c520019f1c4a67415aa5487
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874294"
---
# <a name="browser-support-for-power-bi-report-server"></a>Browserondersteuning voor Power BI Report Server
Meer informatie over welke browserversies worden ondersteund voor het beheren en weergeven van Power BI Report Server en de besturingselementen van de rapportviewer.

## <a name="browser-requirements-for-the-web-portal"></a>Browservereisten voor de webportal
Hier volgt de huidige lijst met browsers die worden ondersteund voor de web-portal.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*iPhone en iPad met iOS 10*

* Apple Safari (+)

**Google Android**  
*Telefoons en tablets met Android 4.4 (KitKat) of hoger*

* Google Chrome (+)
  
  **(+)**  Nieuwste openbaar vrijgegeven versie

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>Browservereisten voor het webbesturingselement voor rapportviewer (2015)
Hier volgt de huidige lijst met browsers die worden ondersteund voor het webbesturingselement voor rapportviewer. De rapportviewer ondersteunt de weergave van rapporten vanuit de webportal.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)**  Nieuwste openbaar vrijgegeven versie

### <a name="authentication-requirements"></a>Verificatievereisten
Browsers ondersteunen specifieke verificatieschema's die moeten worden verwerkt door de rapportserver om ervoor te zorgen dat de aanvraag van de client lukt. De volgende tabel geeft aan welke standaard verificatietypen worden ondersteund door elke browser die wordt uitgevoerd op een Windows-besturingssysteem.

| **Browsertype** | **Ondersteunt** | **De standaardinstellingen van browser** | **Standaardinstellingen van server** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. De standaardinstellingen voor verificatie werken met Edge. |
| **Microsoft Internet Explorer** |Negotiate, Kerberos, NTLM, Basic |Negotiate |Ja. De standaardinstellingen voor verificatie werken met Internet Explorer. |
| **Google Chrome**(+) |Negotiate, NTLM, Basic |Negotiate |Ja. De standaardinstellingen voor verificatie werken met Chrome. |
| **Mozilla Firefox**(+) |NTLM, Basic |NTLM |Ja. De standaardinstellingen voor verificatie werken met Firefox. |
| **Apple Safari**(+) |NTLM, Basic |Basic |Ja. De standaardinstellingen voor verificatie werken met Safari. |

 **(+)**  Nieuwste openbaar vrijgegeven versie

### <a name="script-requirements-for-viewing-reports"></a>Scriptvereisten voor het weergeven van rapporten
Configureer uw browser voor het uitvoeren van scripts wanneer u de rapportviewer wilt gebruiken.

Als het uitvoeren van scripts niet is ingeschakeld, ziet u een foutbericht dat vergelijkbaar is met het hierna volgende bericht wanneer u een rapport opent:

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 Als u ervoor kiest om het rapport zonder scriptondersteuning voor weer te geven, wordt het rapport weergegeven in HTML-code zonder rapportviewerfunctionaliteit zoals de rapportwerkbalk en de documentstructuur.

> [!NOTE]
> De rapportwerkbalk maakt deel uit van de HTML-viewercomponent. Standaard verschijnt de werkbalk boven aan elk rapport dat in een browservenster wordt weergegeven. De rapportviewer biedt functies waaronder de mogelijkheid om het rapport te doorzoeken op informatie, naar een bepaalde pagina te scrollen en de paginagrootte aan te passen voor weergavedoeleinden. Zie [HTML-viewer en de rapportwerkbalk](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar) voor meer informatie over de rapportwerkbalk of HTML-Viewer.
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Browserondersteuning voor webserverbesturingselementen voor rapportviewer in Visual Studio
Het webserverbesturingselement voor rapportviewer wordt gebruikt om de rapportfunctionaliteit in een ASP.NET-webtoepassing te bouwen. Zie [Rapportservices integreren met behulp van het besturingselement van de rapportviewer - Aan de slag](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started) voor meer informatie over het verkrijgen van het besturingselement van de rapportviewer.

Gebruik een browser waarbij scriptondersteuning is ingeschakeld. Als de browser geen scripts kan uitvoeren, kunt u het rapport niet weergeven.

**Microsoft Windows**  
*Windows 7, 8.1, 10; Windows Server 2008 R2, 2012, 2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)**  Nieuwste openbaar vrijgegeven versie

## <a name="next-steps"></a>Volgende stappen
[Administratoroverzicht](admin-handbook-overview.md)  
[Power BI Report Server installeren](install-report-server.md)  
[Report Builder downloaden](https://www.microsoft.com/download/details.aspx?id=53613)  
[SQL Server Data Tools (SSDT) downloaden](https://go.microsoft.com/fwlink/?LinkID=616714)

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

