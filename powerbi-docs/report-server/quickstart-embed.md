---
title: Een Power BI Report Server-rapport insluiten met behulp van een iFrame in SharePoint Server
description: In dit artikel wordt aangegeven hoe u een Power BI Report Server-rapport insluit met behulp van een iFrame in SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 07/28/2020
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: 9e639c4a22cc4e01c04374289026a7006f33143b
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861861"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Een Power BI Report Server-rapport insluiten met behulp van een iFrame in SharePoint Server

In dit artikel leert u hoe u een Power BI Report Server-rapport insluit met behulp van een iFrame op een SharePoint-pagina. Als u met SharePoint Online werkt, moet Power BI Report Server openbaar toegankelijk zijn. In SharePoint Online werkt het Power BI-webonderdeel dat geschikt is voor de Power BI-service niet met Power BI Report Server.  

![Voorbeeld van iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Vereisten
* [Power BI Report Server](https://powerbi.microsoft.com/report-server/) moet zijn geïnstalleerd en geconfigureerd.
* [De voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop](install-powerbi-desktop.md) moet zijn geïnstalleerd.
* Er moet een [SharePoint 2013-, 2016- of 2019-omgeving](/sharepoint/install/install) zijn geïnstalleerd en geconfigureerd.
* Internet Explorer 11 wordt alleen ondersteund als de documentmodus is ingesteld op de modus IE11 (Edge) of bij het gebruik van SharePoint Online. U kunt andere ondersteunde browsers gebruiken met SharePoint on-premises en SharePoint Online.

## <a name="create-the-power-bi-report-url"></a>De Power BI-rapport-URL maken

1. Download het voorbeeld vanuit GitHub: [Blogdemo](https://github.com/Microsoft/powerbi-desktop-samples). Selecteer **Klonen of downloaden** en selecteer vervolgens **ZIP-bestand downloaden**.

    ![PBIX-voorbeeldbestand downloaden](media/quickstart-embed/quickstart_embed_14.png)

2. Pak het bestand uit en open het PBIX-voorbeeldbestand in de voor Power BI Report Server geoptimaliseerde versie van Power BI Desktop.

    ![PBI RS Desktop-tool](media/quickstart-embed/quickstart_embed_02.png)

3. Sla het rapport op naar **Power BI Report Server**. 

    ![PBI RS opslaan](media/quickstart-embed/quickstart_embed_03.png)

4. Bekijk het rapport in de webportal van Power BI Report Server.

    ![Webportal](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>De URL-parameter vastleggen

Zodra u de URL hebt, kunt u een iFrame binnen een SharePoint-pagina maken om het rapport te hosten. Voeg voor elke Power BI Report Server-rapport-URL de volgende queryreeksparameter toe om uw rapport in te sluiten in een iFrame in SharePoint: `?rs:embed=true`.

   Bijvoorbeeld:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Het rapport insluiten in een iFrame van SharePoint

1. Navigeer naar een SharePoint **Site-inhoud**-pagina.

    ![De pagina Site-inhoud](media/quickstart-embed/quickstart_embed_05.png)

2. Kies de pagina waaraan u uw rapport wilt toevoegen.

    ![App met de pagina Site-inhoud](media/quickstart-embed/quickstart_embed_06.png)

3. Selecteer het tandwielpictogram in de rechterbovenhoek en selecteer vervolgens **Pagina bewerken**.

    ![De optie Pagina bewerken](media/quickstart-embed/quickstart_embed_07.png)

4. Selecteer **Een webonderdeel toevoegen**.

5. Selecteer onder **Categorieën** de optie **Media en inhoud**. Selecteer onder **Onderdelen** de optie **Inhoudseditor** en selecteer vervolgens **Toevoegen**.

    ![Het webonderdeel Inhoudseditor selecteren](media/quickstart-embed/quickstart_embed_09.png)

6. Selecteer **Klik hier om nieuwe inhoud toe te voegen**.

7. Selecteer in het bovenste menu **Tekst opmaken** en selecteer vervolgens **Bron bewerken**.

     ![Bron bewerken](media/quickstart-embed/quickstart_embed_11.png)

8. Plak in het venster **Bron bewerken** uw iFrame-code in **HTML-bron** en selecteer vervolgens **OK**.

    ![iFrame-code](media/quickstart-embed/quickstart_embed_12.png)

     Bijvoorbeeld:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Selecteer **Pagina** in het bovenste menu en selecteer vervolgens **Stoppen met bewerken**.

    ![Stoppen met bewerken](media/quickstart-embed/quickstart_embed_13.png)

    Het rapport wordt op de pagina weergegeven.

    ![Voorbeeld van iFrame](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Volgende stappen

- [Maak een Power BI-rapport voor Power BI Report Server](quickstart-create-powerbi-report.md).  
- [Maak een gepagineerd rapport voor Power BI Report Server](quickstart-create-paginated-report.md).  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).