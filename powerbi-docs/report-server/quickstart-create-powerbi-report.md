---
title: Een Power BI-rapport maken voor Power BI Report Server
description: Leer hoe u in een paar eenvoudige stappen een Power BI-rapport voor Power BI Report Server maakt.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/03/2020
ms.author: maggies
ms.openlocfilehash: 69ebfa9b1d2ef500b388a1bbb57926dc53ff2607
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76975005"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Een Power BI-rapport maken voor Power BI Report Server
U kunt Power BI-rapporten on-premises opslaan en beheren in de webportal van Power BI Report Server, net zoals u Power BI-rapporten kunt opslaan in de cloud in de Power BI-service (https://powerbi.com) ). U maakt rapporten in Power BI Desktop en publiceert deze naar de webportal. Gebruikers in uw organisatie kunnen de rapporten weergeven in een browser of in een mobiele Power BI-app op een mobiele apparaat.

![Power BI-rapport in de webportal](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Nu volgen vier snelle stappen om u op weg te helpen.

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>Stap 1: Voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop installeren

Als u al Power BI-rapporten hebt gemaakt in Power BI Desktop, bent u bijna klaar om Power BI-rapporten te maken voor Power BI Report Server. Het is raadzaam om de versie van Power BI Desktop te installeren die is geoptimaliseerd voor Power BI Report Server, zodat u zeker weet dat de server en app altijd zijn gesynchroniseerd. U kunt beide versies van Power BI Desktop op dezelfde computer installeren.

1. Selecteer in de webportal voor rapportserver de pijl **Downloaden** > **Power BI Desktop**.

    ![Power BI Desktop downloaden van de webportal](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    Of ga naar de startpagina van [Power BI Report Server](https://powerbi.microsoft.com/report-server/) en selecteer **Geavanceerde downloadopties**.

2. Selecteer **Downloaden** in het downloadcentrum.

3. Selecteer het volgende, afhankelijk van uw computer:

    - **PBIDesktopRS.msi** (de 32-bits versie) of

    - **PBIDesktopRS_x64.msi** (de 64-bits versie).

4. Nadat u het installatieprogramma hebt gedownload, voert u de installatiewizard van Power BI Desktop (september 2019) uit.

2. Selecteer aan het einde van de installatie de optie **Power BI Desktop nu starten**.
   
    Het programma wordt automatisch gestart en u kunt aan de slag. U beschikt over de juiste versie als **Power BI Desktop (september 2019)** wordt vermeld in de titelbalk.

    ![Power BI Desktop september 2019](media/quickstart-create-powerbi-report/power-bi-report-server-desktop-sept-2019.png)

3. Als u niet bekend bent met Power BI Desktop, is het misschien een goed idee om de video's op het welkomstscherm te bekijken.
   
    ![Welkomstscherm van Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Stap 2: Een gegevensbron selecteren
U kunt verbinding maken met allerlei gegevensbronnen. Lees hier meer informatie over [het maken van verbinding met gegevensbronnen](connect-data-sources.md) (Engelstalig).

1. Selecteer **Gegevens ophalen** op het welkomstscherm.
   
    U kunt de optie **Gegevens ophalen** ook selecteren op het tabblad **Start**.
2. Selecteer uw gegevensbron, in dit voorbeeld **Analysis Services**.
   
    ![Gegevensbron selecteren](media/quickstart-create-powerbi-report/power-bi-report-server-get-data-ssas.png)
3. Voer een waarde in voor **Server** en eventueel voor **Database**. Zorg ervoor dat **Live verbinding maken** is geselecteerd > **OK**.
   
    ![Servernaam](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Kies de rapportserver waarop u de rapporten wilt opslaan.
   
    ![Rapportserver selecteren](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Stap 3: Het rapport ontwerpen
Nu wordt het pas echt leuk: U gaat de visualisaties of visuele elementen maken die uw gegevens het best illustreren.

U kunt bijvoorbeeld een trechterdiagram maken van klanten en waarden groeperen op jaarlijkse omzet.

![Een rapport ontwerpen](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. Selecteer **Trechterdiagram** bij **Visualisaties**.
2. Sleep het veld dat moet worden geteld naar het vak **Waarden**. Als het niet een numeriek veld is, wordt het type waarde automatisch gewijzigd in *Aantal van*.
3. Sleep het veld waarop u wilt groeperen naar het vak **Groep**.

Hier kunt u nog veel meer lezen over [het ontwerpen van een Power BI-rapport](../desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Stap 4: Het rapport opslaan op de rapportserver
Wanneer uw rapport klaar is, kunt u het opslaan op de Power BI-rapportserver die u hebt gekozen in stap 2.

1. Selecteer in het menu **Bestand** de optie **Opslaan als** > **Power BI Report Server**.
   
    ![Opslaan op de rapportserver](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Nu kunt u het rapport bekijken in de webportal.
   
    ![Het rapport bekijken in de webportal](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)
    
> [!NOTE]
> Als u ervoor kiest het rapport in de toekomst te bewerken, zijn de rapportgegevens die u in het bureaublad ziet, altijd gegevens die in het cachegeheugen zijn geplaatst toen het rapport voor het eerst werd gemaakt.  Als u bij het bewerken van het rapport de nieuwste gegevens wilt zien, moet u de gegevens in de Power BI Desktop-toepassing vernieuwen.

## <a name="next-steps"></a>Volgende stappen
### <a name="power-bi-desktop"></a>Power BI Desktop
Er zijn heel interessante informatiebronnen voor het maken van rapporten in Power BI Desktop. Deze koppeling is een goed startpunt.

* [Aan de slag met Power BI Desktop](../desktop-getting-started.md)
* Begeleid leren: [Power BI Desktop verkennen](/learn/modules/get-data-power-bi/2-getting-started-power-bi-desktop)

### <a name="power-bi-report-server"></a>Power BI Report Server
* [Voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop installeren](install-powerbi-desktop.md)  
* [Wat is Power BI Report Server?](get-started.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
