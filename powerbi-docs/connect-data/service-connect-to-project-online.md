---
title: Verbinding maken met Project Online via Power BI
description: Project Online voor Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 07/25/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: e5d97da4d643512396a17e95fb7cae2e841d7521
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403278"
---
# <a name="connect-to-project-web-app-with-power-bi"></a>Verbinding maken met Project Web App via Power BI
Microsoft Project Web App is een flexibele onlineoplossing voor Project Portfolio Management (PPM) en dagelijkse werkzaamheden. Met Project Web App kunnen organisaties meteen aan de slag, projectportfolio-investeringen prioriteren en de beoogde bedrijfswaarde leveren. Met het Project Web App-inhoudspakket voor Power BI kunt u inzichten ontlenen aan Power Web App om projecten, portfolio's en resources te beheren.

Maak verbinding met de [Project Web App-sjabloon-app](https://appsource.microsoft.com/product/power-bi/pbi_msprojectonline.pbi-microsoftprojectwebapp) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken

1. Selecteer in het navigatievenster **Apps** en selecteer in de rechterbovenhoek vervolgens **Apps downloaden**.

    ![Apps ophalen](media/service-connect-to-project-online/GetApps.png)

2. Selecteer **Ophalen** in het vak **Services**.
   
   ![Schermopname van het venster AppSource met vijf beschikbare apps.](media/service-connect-to-project-online/AppSource.png)
3. Selecteer in AppSource het tabblad **Apps** en zoek/selecteer **Microsoft Project Web App**.
   
4. U krijgt de vraag **Wilt u deze Power BI-app installeren?** Selecteer **Installeren**. 

   ![Project Web installeren](media/service-connect-to-project-online/ProjectTile.png)
5. Selecteer in het deelvenster **Apps** de tegel **Microsoft Project Web App**. 
   
   ![Web-app van Microsoft-project](media/service-connect-to-project-online/getstarted.png)
6. Selecteer in **Aan de slag met uw nieuwe app** de optie **Verbinding maken met gegevens**.
   
   ![Verbinding maken met gegevens](media/service-connect-to-project-online/mproject.png)
7. Voer in het tekstvak **Project Web App-URL** de URL in voor de Project Web App (PWA) waarmee u verbinding wilt maken.  Houd er rekening mee dat deze instructie kan afwijken van het voorbeeld als u een aangepast domein hebt. Typ in het tekstvak **Taal PWA-site** het getal dat overeenkomt met de taal van uw PWA-site. Typ het cijfer '1' voor Engels, '2' voor Frans, '3' voor Duits, '4' voor Portugees (Brazilië), '5' voor Portugees (Portugal) en '6' voor Spaans. 
   
   ![Verbinding maken met Microsoft Project Online](media/service-connect-to-project-online/params.png)
8. Selecteer voor de verificatiemethode de optie **oAuth2** \>  **Aanmelden**. Geef uw Project Web App-referenties op als hierom wordt gevraagd en voer het verificatieproces uit.

    > [!NOTE]
    > U moet machtigingen als Portfolioviewer, Portfoliomanager of Beheerder hebben voor de Project Web App waarmee u verbinding maakt.

9. U ziet een melding dat uw gegevens geladen worden. Dit kan enige tijd duren, afhankelijk van de grootte van uw account. Nadat de gegevens zijn geïmporteerd in Power BI wordt de inhoud van uw nieuwe werkruimte weergegeven. Mogelijk moet u de gegevensset vernieuwen om de nieuwste updates op te halen. 

    Nadat de gegevens in Power BI zijn geïmporteerd, ziet u een rapport van dertien pagina's en een gegevensset in het navigatievenster. 

10. Wanneer uw rapporten klaar zijn, kunt u uw Project Web App-gegevens verkennen. De sjabloon-app wordt geleverd met dertien uitgebreide en gedetailleerde rapporten voor het Portfolio-overzicht (zes rapportpagina's), het Resource-overzicht (vijf rapportpagina's) en de Project-status (twee rapportpagina's). 

    ![Portfoliodashboard](media/service-connect-to-project-online/report1.png)
   
    ![Beschikbaarheid](media/service-connect-to-project-online/report3.png)
   
    ![Projectstatus](media/service-connect-to-project-online/report2.png)

**Wat nu?**

* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**.

**De sjabloon-app uitbreiden**

Download het [GitHub PBIT-bestand](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) om het inhoudspakket verder aan te passen en bij te werken.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](../fundamentals/service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)
