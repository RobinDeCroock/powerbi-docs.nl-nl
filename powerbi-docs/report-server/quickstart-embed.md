---
title: Een rapport insluiten met een iFrame
description: Power BI Report Server-rapport insluiten in een iFrame in SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: ca26770c652c12573bf28e24b218b214bf1196fa
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769865"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Quickstart: Een Power BI Report Server-rapport insluiten met behulp van een iFrame in SharePoint Server

In deze snelstart leert u hoe u een Power BI Report Server-rapport insluit met behulp van een iFrame op een SharePoint-pagina. Als u met SharePoint Online werkt, moet Power BI Report Server openbaar toegankelijk zijn. In SharePoint Online werkt het Power BI-webonderdeel dat geschikt is voor de Power BI-service niet met Power BI Report Server. 

![Voorbeeld van iFrame](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Vereisten
* U moet [Power BI Report Server](https://powerbi.microsoft.com/report-server/) hebben geïnstalleerd en geconfigureerd.
* U moet een voor [Power BI Report Server geoptimaliseerde versie van Power BI Desktop](install-powerbi-desktop.md) hebben geïnstalleerd.
* U moet een [SharePoint](https://docs.microsoft.com/sharepoint/install/install)-omgeving hebben geïnstalleerd en geconfigureerd.

## <a name="creating-the-power-bi-report-server-report-url"></a>De Power BI Report Server-rapport-URL maken

1. Download het voorbeeld vanuit GitHub [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples).

    ![PBIX-voorbeeldbestand downloaden](media/quickstart-embed/quickstart_embed_14.png)

2. Open het PBIX-voorbeeldbestand vanuit GitHub in de voor **Power BI Report Server geoptimaliseerde versie van Power BI Desktop**.

    ![PBI RS Desktop-tool](media/quickstart-embed/quickstart_embed_02.png)

3. Sla het rapport op naar **Power BI Report Server**. 

    ![PBI RS opslaan](media/quickstart-embed/quickstart_embed_03.png)

4. Bekijk het rapport in de **webportal**.

    ![Webportal](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>De URL-parameter vastleggen

Zodra u de URL hebt, kunt u een iFrame binnen een SharePoint-pagina maken om het rapport te hosten. Voor elke Power BI Report Server-rapport-URL kunt u een queryreeksparameter van `?rs:embed=true` toevoegen om uw rapport in te sluiten in een iFrame. 

   Bijvoorbeeld:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Power BI Report Server-rapport insluiten in een SharePoint iFrame

1. Navigeer naar een SharePoint **Site-inhoud**-pagina.

    ![Pagina Site-inhoud](media/quickstart-embed/quickstart_embed_05.png)

2. Kies de pagina waaraan u uw rapport wilt toevoegen.

    ![App Site-inhoud-pagina](media/quickstart-embed/quickstart_embed_06.png)

3. Selecteer het tandwielpictogram rechts bovenin en selecteer **Pagina bewerken**.

    ![Optie Pagina bewerken](media/quickstart-embed/quickstart_embed_07.png)

4. Selecteer **Webonderdeel toevoegen**.

    ![Webonderdeel toevoegen](media/quickstart-embed/quickstart_embed_08.png)

5. Selecteer onder **Categorieën** de optie **Media en inhoud**, selecteer onder **Delen** de optie **Inhoudseditor** en selecteer vervolgens **Toevoegen** .

    ![Selecteer Webonderdeel Inhoudseditor](media/quickstart-embed/quickstart_embed_09.png) ![Selecteer toevoegen](media/quickstart-embed/quickstart_embed_091.png)

6. Selecteer **Klik hier om nieuwe inhoud toe te voegen**.

    ![Nieuwe inhoud toevoegen](media/quickstart-embed/quickstart_embed_10.png)

7. Selecteer in het lint het tabblad **Tekstopmaak** en selecteer **Bron bewerken**.

     ![Bron bewerken](media/quickstart-embed/quickstart_embed_11.png)

8. Plak uw iFrame-code in het venster Bron bewerken en selecteer OK.

    ![iFrame-code](media/quickstart-embed/quickstart_embed_12.png)

     Bijvoorbeeld:
     ```html
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Selecteer in het lint het tabblad **Pagina** en selecteer **Stoppen met bewerken**.

    ![Stoppen met bewerken](media/quickstart-embed/quickstart_embed_13.png)

10. U ziet nu het rapport op de pagina.

    ![Voorbeeld van iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Volgende stappen

[Quickstart: Een Power BI-rapport maken voor Power BI Report Server](quickstart-create-powerbi-report.md)  
[Quickstart: Een gepagineerd rapport maken voor Power BI Report Server](quickstart-create-paginated-report.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/) 