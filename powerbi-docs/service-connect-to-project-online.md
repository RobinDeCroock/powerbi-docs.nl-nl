---
title: Verbinding maken met Project Online via Power BI
description: Project Online voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a6ada87813593fd0f06d7870fa1727bc35fe7d47
ms.sourcegitcommit: fe8a25a79f7c6fe794d1a30224741e5281e82357
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2019
ms.locfileid: "68324977"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Verbinding maken met Project Web App via Power BI
Microsoft Project Web App is een flexibele onlineoplossing voor Project Portfolio Management (PPM) en dagelijkse werkzaamheden. Met Project Web App kunnen organisaties meteen aan de slag, projectportfolio-investeringen prioriteren en de beoogde bedrijfswaarde leveren. Met het Project Web App-inhoudspakket voor Power BI kunt u inzichten ontlenen aan Power Web App om projecten, portfolio's en resources te beheren.

Maak verbinding met de [Project Web App-sjabloon-app](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken

   ![](media/service-connect-to-project-online/GetApps.png)
1. Selecteer in het linkernavigatievenster **Apps** en selecteer in de rechterbovenhoek vervolgens **Apps downloaden**.
2. Selecteer **Ophalen** in het vak **Services**.
   
   ![](media/service-connect-to-project-online/AppSource.png)
3. Selecteer in AppSource het tabblad **Apps** en zoek/selecteer **Microsoft Project Web App**.
   
4. U krijgt de vraag **Wilt u deze Power BI-app installeren?** Selecteer **Installeren**. 

   ![](media/service-connect-to-project-online/ProjectTile.png)
5. Selecteer in het deelvenster **Apps** de tegel **Microsoft Project Web App**. 
   
   ![](media/service-connect-to-project-online/getstarted.png)
6. Selecteer in **Aan de slag met uw nieuwe app** de optie **Verbinding maken met gegevens**.
   
   ![](media/service-connect-to-project-online/mproject.png)
7. Voer in het tekstvak **Project Web App-URL** de URL in voor de Project Web APP (PWA) waarmee u verbinding wilt maken.  Houd er rekening mee dat deze instructie kan afwijken van het voorbeeld als u een aangepast domein hebt. Typ in het tekstvak **Taal PWA-site** het getal dat overeenkomt met de taal van uw PWA-site. Typ het cijfer '1' voor Engels, '2' voor Frans, '3' voor Duits, '4' voor Portugees (Brazilië), '5' voor Portugees (Portugal) en '6' voor Spaans. 
   
   ![](media/service-connect-to-project-online/params.png)
8. Selecteer voor de verificatiemethode **oAuth2** \> **Aanmelden**. Geef uw Project Web App-referenties op als hierom wordt gevraagd en voer het verificatieproces uit.

    
Houd er rekening mee dat u machtigingen als Portfolioviewer, Portfoliomanager of beheerder moet hebben voor de Project Web App waarmee u verbinding maakt.

9. U ziet een melding dat uw gegevens geladen worden. Dit kan enige tijd duren, afhankelijk van de grootte van uw account. Nadat de gegevens zijn geïmporteerd in Power BI wordt de inhoud van uw nieuwe werkruimte weergegeven. Mogelijk moet u de gegevensset vernieuwen om de nieuwste updates op te halen. 

Nadat de gegevens in Power BI zijn geïmporteerd, ziet u een rapport van dertien pagina's en een gegevensset in het navigatiedeelvenster aan de linkerzijde. 

10. Wanneer uw rapporten klaar zijn, kunt u uw Project Web App-gegevens verkennen. De sjabloon-app wordt geleverd met dertien uitgebreide en gedetailleerde rapporten voor het Portfolio-overzicht (zes rapportpagina's), het Resource-overzicht (vijf rapportpagina's) en de Project-status (twee rapportpagina's). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**Wat nu?**

* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

**De sjabloon-app uitbreiden**

Download het [GitHub PBIT-bestand](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) om het inhoudspakket verder aan te passen en bij te werken

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

