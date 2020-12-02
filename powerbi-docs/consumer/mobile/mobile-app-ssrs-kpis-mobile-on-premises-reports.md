---
title: On-premises rapporten en KPI's weergeven in de mobiele Power BI-apps
description: Met de mobiele Power BI-apps hebt u live en mobiel via aanraking toegang tot uw on-premises bedrijfsgegevens in SQL Server 2016 Reporting Services en Power BI Report Server.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/05/2019
ms.openlocfilehash: 18ad1be61202ddf189da064a833fddf6d793a2ba
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413398"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>On-premises rapportserverrapporten en KPI's weergeven in de mobiele Power BI-apps

Met de mobiele Power BI-apps hebt u live en mobiel via aanraking toegang tot uw on-premises bedrijfsgegevens in Power BI Report Server en SQL Server 2016 Reporting Services (SSRS).

Van toepassing op:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Android-tablets |


![Startpagina van Report Server in de mobiele apps](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Om te beginnen
**In de mobiele apps geeft u Power BI-inhoud weer. U maakt de inhoud daar niet.**

* U en andere rapportmakers in uw organisatie [maken Power BI-rapporten met Power BI Desktop. Vervolgens publiceert u deze naar de webportal van Power BI Report Server](../../report-server/quickstart-create-powerbi-report.md). 
* U kunt [rechtstreeks in de webportal KPI's maken](/sql/reporting-services/working-with-kpis-in-reporting-services), deze ordenen in mappen en uw favorieten markeren, zodat u ze eenvoudig kunt terugvinden. 
* U kunt [mobiele Reporting Services-rapporten maken](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) met SQL Server 2016 Enterprise Edition Mobile Report Publisher en deze publiceren naar de [Reporting Services-webportal](/sql/reporting-services/web-portal-ssrs-native-mode).  

Vervolgens kunt u in de mobiele Power BI-apps verbinding maken met maximaal vijf rapportservers om de Power BI-rapporten en -KPI's weer te geven, geordend in mappen of verzameld als favorieten. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>De voorbeelden in de mobiele apps verkennen zonder serververbinding
Ook als u geen toegang hebt tot een Reporting Services-webportal, kunt u de functies van mobiele Reporting Services-rapporten en -KPI's bekijken. 

1. Tik op uw profielafbeelding in de linkerbovenhoek en tik vervolgens op **Instellingen** in het deelvenster Accounts dat wordt weergegeven.

2. Tik op de instellingenpagina die wordt geopend op **Reporting Services-voorbeelden** en blader om de voorbeeld-KPI's en de voorbeelden van mobiele rapporten te gebruiken.
   
   ![Reporting Services-voorbeelden](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Verbinding maken met een on-premises rapportserver
Met de mobiele Power BI-apps kunt u on-premises Power BI-rapporten, mobiele Reporting Services-rapporten en KPI's weergeven in de mobiele Power BI-apps. 

1. Open de Power BI-app op uw mobiele apparaat.
2. Als u zich nog niet hebt aangemeld bij Power BI, tikt u op **Report Server**.
   
   ![Aanmelden bij een rapportserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Als u zich al bij de Power BI-app hebt aangemeld, tikt u op uw profielafbeelding in de linkerbovenhoek en vervolgens op **Instellingen** in het deelvenster Accounts dat wordt weergegeven.
3. Tik op de instellingenpagina die wordt geopend op **Verbinding maken met de server**.
   
    ![Verbinding maken met server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    De mobiele app moet op een bepaalde manier toegang hebben tot de server. Dit kan op een aantal manieren worden verkregen:
     * Het is het gemakkelijkst door hetzelfde netwerk/VPN te gebruiken.
     * Het is mogelijk een Web Application Proxy te gebruiken om verbinding te maken van buiten de organisatie. Zie [OAuth gebruiken om verbinding met Reporting Services te maken](mobile-oauth-ssrs.md) voor meer informatie.
     * Open een verbinding (poort) in de firewall.

4. Vul het serveradres in en geef de server een beschrijvende naam, indien gewenst. Gebruik deze notatie voor het adres van de server:
   
     `https://<servername>/reports`
   
     OF
   
     `https://<servername>/reports`
   
   Voeg **http** of **https** toe aan het begin van de verbindingsreeks.
   
    ![Het dialoogvenster Verbinding maken met server](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. Nadat u het serveradres en de optionele beschrijvende naam hebt ingevoerd, tikt u op **Verbinding maken** en vult u uw gebruikersnaam en wachtwoord in wanneer u hierom wordt gevraagd.
6. De server (in dit voorbeeld 'Werkserver' genoemd) wordt nu weergegeven in het deelvenster Accounts.
   
   ![Rapportserver in het navigatievenster](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>Verbinding maken met een on-premises rapportserver in iOS of Android

Als u Power BI bekijkt in de mobiele iOS- of Android-app, heeft uw IT-beheerder mogelijk een app-configuratiebeleid gedefinieerd. Als dit het geval is, kunt u gestroomlijnd verbinding maken met de rapportserver en hoeft u niet zoveel informatie op te geven wanneer u verbinding maakt met een rapportserver. 

1. U ziet een bericht dat uw mobiele app is geconfigureerd met een rapportserver. Tik op **Aanmelden**.

    ![Aanmelden bij de rapportserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  Op de pagina **Verbinding maken met server** zijn de details over de rapportserver al ingevuld. Tik op **Verbinding maken**.

    ![Ingevulde details rapportserver](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Voer een wachtwoord in om een verificatie uit te voeren en tik vervolgens op **Aanmelden**. 

    ![Schermopname van wachtwoordinvoer met de knop Aanmelden.](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

U kunt nu KPI's en Power BI-rapporten zien en gebruiken die zijn opgeslagen op de rapportserver.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Power BI-rapporten en -KPI's weergeven in de Power BI-app
Power BI-rapporten en mobiele Reporting Services-rapporten worden weergegeven in de mappen waarin ze zijn opgeslagen op de Reporting Services-webportal. 

* Tik op een Power BI-rapport ![Pictogram van een Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Het rapport wordt geopend in de liggende stand. U kunt met het rapport werken in de Power BI-app.

    > [!NOTE]
  > In- en uitzoomen is momenteel niet ingeschakeld in Power BI-rapporten op een Power BI Report Server.
  
    ![Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* In Power BI Desktop kunnen rapporteigenaren [een rapport optimaliseren](../../create-reports/desktop-create-phone-report.md) voor de mobiele Power BI-apps. Geoptimaliseerde rapporten hebben een speciaal pictogram, ![het pictogram Geoptimaliseerd Power BI-rapport](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png), en een speciale indeling.
  
    ![Power BI-rapport dat is geoptimaliseerd voor mobiel](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Tik op een KPI om deze weer te geven in de focusmodus.
  
    ![KPI in focusmodus](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Uw favoriete KPI's en rapporten weergeven
U kunt KPI's en rapporten op het webportal markeren als favorieten en ze vervolgens weergeven in één handige map op uw mobiele apparaat, samen met uw favoriete Power BI-dashboards en -rapporten.

* Tik op **Favorieten** op de navigatiebalk.
  
   ![Favorieten in het navigatievenster](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Uw favoriete KPI's en rapporten van de webportal bevinden zich allemaal op deze pagina, samen met de Power BI-dashboards in de Power BI-service:
  
   ![Power BI-rapporten en -dashboard op de pagina Favorieten](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Een verbinding met een rapportserver verwijderen
1. Open het deelvenster Accounts en tik op **Instellingen**.
2. Tik op de naam van de server waarmee u geen verbinding wilt maken.
3. Tik op **Server verwijderen**.

## <a name="next-steps"></a>Volgende stappen
* [Wat is Power BI?](../../fundamentals/power-bi-overview.md)  
* Vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).