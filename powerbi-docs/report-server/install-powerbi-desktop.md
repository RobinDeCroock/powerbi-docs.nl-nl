---
title: Voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop installeren
description: Meer informatie over het installeren van een voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/16/2020
ms.openlocfilehash: 62add0b1268b06bb227bdc1b8ec2e4ae59358c57
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044758"
---
# <a name="install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop installeren

Als u Power BI-rapporten wilt maken voor Power BI Report Server, moet u de versie van Power BI Desktop downloaden en installeren die is geoptimaliseerd voor Power BI Report Server. Dit is een andere versie van Power BI Desktop dan de versie die wordt gebruikt met de Power BI-service. De versie van Power BI Desktop voor de Power BI-service bevat bijvoorbeeld preview-functies. Deze functies bevinden zich niet in de Power BI Report Server-versie totdat ze algemeen beschikbaar zijn. Als u deze versie gebruikt, moet u ervoor zorgen dat de rapportserver kan werken met een bekende versie van de rapporten en het model. 

Maak u geen zorgen. U kunt Power BI Desktop en de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop naast elkaar op dezelfde computer installeren.

## <a name="download-and-install-power-bi-desktop"></a>Power BI Desktop downloaden en installeren

U kunt het snelste controleren of u over de meest recente versie van de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop beschikt, is door te starten vanuit de webportal van de rapportserver.

1. Selecteer in de webportal van report server de pijl **Downloaden** > **Power BI Desktop**.

    ![Power BI Desktop downloaden van de webportal](media/install-powerbi-desktop/report-server-download-web-portal.png)

    Of ga naar de startpagina van [Power BI Report Server](https://powerbi.microsoft.com/report-server/) en selecteer **Geavanceerde downloadopties**.

2. Selecteer een taal op de pagina van het downloadcentrum en selecteer **Downloaden**.

3. Selecteer het volgende, afhankelijk van uw computer: 

    - **PBIDesktopRS.msi** (de 32-bits versie) of
    - **PBIDesktopRS_x64.msi** (de 64-bits versie).

1. Nadat u het installatieprogramma hebt gedownload, voert u de installatiewizard voor Power BI Desktop uit.

2. Selecteer aan het einde van de installatie de optie **Power BI Desktop starten**.

    Het programma wordt automatisch gestart en u kunt aan de slag.

## <a name="verify-youre-using-the-correct-version"></a>Controleer of u de juiste versie gebruikt
U kunt eenvoudig controleren of u de juiste versie van Power BI Desktop gebruikt: Bekijk het beginscherm of de titelbalk in Power BI Desktop. U hebt de juiste versie als **Power BI Desktop (oktober 2020)** wordt vermeld in de titelbalk. De kleuren in het Power BI-logo zijn ook omgekeerd: geel op zwart in plaats van zwart op geel.

![Power BI Desktop oktober 2020](media/install-powerbi-desktop/power-bi-report-server-desktop-may-2020.png)

Voor de versie van Power BI Desktop voor de Power BI-service worden de maand en het jaar niet in de titelbalk weergegeven.

## <a name="file-extension-association"></a>Bestandsindelingen kopppelen
Stel dat u zowel Power BI Desktop als de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop op dezelfde computer hebt geïnstalleerd. De meest recente installatie van Power BI Desktop heeft de bestandskoppeling met PBIX-bestanden. Wanneer u dubbelklikt op een pbix-bestand, wordt de Power BI Desktop-versie die u het meest recent hebt geïnstalleerd, geopend.

Als u Power BI Desktop hebt en u daarna de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop installeert, worden alle pbix-bestanden standaard geopend in de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop. Als u .pbix-bestanden liever standaard opent met Power BI Desktop, installeert u [Power BI Desktop opnieuw vanuit de Microsoft Store](https://aka.ms/pbidesktopstore).

U kunt ook eerst de versie van Power BI Desktop die u wilt gebruiken openen. En daarna opent u het bestand vanuit Power BI Desktop.

Dit is de veiligste manier om altijd de juiste versie van Power BI Desktop te openen. U kunt beginnen met een Power BI-rapport te bewerken vanuit Power BI Report Server of u kunt een nieuw Power BI-rapport maken vanuit de Power BI-service.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Power BI-rapporten in Power BI Report Server, in de Power BI-service (`https://app.powerbi.com`) en in mobiele Power BI-apps werken bijna exact dezelfde, op een paar functies na.

### <a name="selecting-a-language"></a>Een taal selecteren

Voor Power BI Desktop geoptimaliseerd voor Power BI Report Server selecteert u de taal wanneer u de app installeert. U kunt deze later niet meer wijzigen, maar u kunt een versie in een andere taal installeren.

### <a name="report-visuals-in-a-browser"></a>Rapportvisuals in een browser

Power BI Report Server-rapporten ondersteunen bijna alle visualisaties, met inbegrip van Power BI-visuals. Rapporten voor Power BI Report Server bieden geen ondersteuning voor:

* R-visuals
* ArcGIS-kaarten
* Breadcrumbs
* Preview-functies in Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Rapporten in de Power BI - Mobiel-apps

Rapporten voor Power BI Report Server ondersteunen alle basisfunctionaliteit in de [mobiele Power BI-apps](../consumer/mobile/mobile-apps-for-mobile-devices.md), waaronder:

* [Indeling van telefoonrapport](../create-reports/desktop-create-phone-report.md): u kunt een rapport optimaliseren voor de mobiele Power BI-apps. Op uw mobiele telefoon hebben geoptimaliseerde rapporten een speciaal pictogram, ![het pictogram voor de telefoonrapportindeling](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png), en een speciale indeling.
  
    ![Rapporten geoptimaliseerd voor telefoons](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Rapporten voor Power BI Report Server bieden geen ondersteuning voor deze functies in de mobiele Power BI-apps:

* R-visuals
* ArcGIS-kaarten
* Power BI-visuals
* Breadcrumbs
* Het filteren van geografische gebieden of streepjescodes

### <a name="custom-security"></a>Aangepaste beveiliging

Power BI Desktop geoptimaliseerd voor Power BI Report Server biedt geen ondersteuning voor aangepaste beveiliging. Als uw Power BI Report Server is geconfigureerd met een aangepaste beveiligingsextensie, kunt u een Power BI-rapport niet opslaan vanaf Power BI Desktop (geoptimaliseerd voor Power BI Report Server) naar het Power BI Report Server-exemplaar. U moet het .pbix-rapport bestand opslaan vanuit Power BI Desktop en dit uploaden naar de Power BI Report Server-portal-site.

### <a name="saving-reports-to-a-power-bi-report-server-in-a-different-domain"></a>Rapporten in Power BI Report Server opslaan in een ander domein

Wanneer u een Power BI-rapport opslaat in Power BI Report Server, worden uw Windows-referenties gebruikt. Er is geen ondersteuning voor het rechtstreeks op een rapportserver opslaan in een ander domein met uw Windows-referenties. U kunt in plaats daarvan een webbrowser gebruiken om de rapportserver weer te geven en het bestand handmatig uploaden vanaf uw computer.

## <a name="next-steps"></a>Volgende stappen

Nu u Power BI Desktop hebt geïnstalleerd, kunt u beginnen met het maken van Power BI-rapporten.

[Een Power BI-rapport maken voor Power BI Report Server](quickstart-create-powerbi-report.md)  
[Wat is Power BI Report Server?](get-started.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

