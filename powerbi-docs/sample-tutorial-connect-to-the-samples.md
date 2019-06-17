---
title: Verbinding maken met de voorbeelden in de Power BI-service
description: Informatie over het installeren en verkennen van de voorbeelden in de Power BI-service.
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: dfa8ff694a1f4a4ba4e5078fe93300e4bf26cc73
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721408"
---
#  <a name="connect-to-the-samples-in-the-power-bi-service"></a>Verbinding maken met de voorbeelden in de Power BI-service

In deze zelfstudie leert u het volgende: 
- Een voorbeeldinhoudspakket importeren, het toevoegen aan de Power BI-service en de inhoud ervan openen. Een *inhoudspakket* is een type voorbeeld waarbij de gegevensset wordt geleverd met een dashboard en een rapport. 
- Een .pbix-voorbeeldbestand openen in Power BI Desktop.

Als u eerst meer achtergrondinformatie wilt, raden we u aan te beginnen met het artikel [Voorbeeldgegevenssets voor Power BI](sample-datasets.md). In dat artikel leest u alles over de voorbeelden: hoe u ze downloadt, waar u ze kunt opslaan, hoe u ze gebruikt en enkele verhalen die elk voorbeeld kan vertellen. Wanneer u de basisbeginselen begrijpt, keert u terug naar deze zelfstudie.   

## <a name="prerequisites"></a>Vereisten
De voorbeelden zijn beschikbaar voor de Power BI-service en Power BI Desktop. Gebruik het voorbeeld van de retailanalyse als u mee wilt doen.

Het voorbeeldinhoudspakket *Retail Analysis* dat in deze zelfstudie wordt gebruikt, bestaat uit een dashboard, een rapport en een gegevensset.
Om vertrouwd te raken met dit type inhoudspakket en het bijbehorende scenario, kunt u [een rondleiding door het voorbeeld Retail Analysis bekijken](sample-retail-analysis.md) voordat u begint.

## <a name="samples-and-power-bi-service"></a>Voorbeelden en de Power BI-service

1. Open de Power BI-service (app.powerbi.com) en meld u aan.
2. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster. Als u **Gegevens ophalen** niet ziet, vouwt u het navigatievenster uit door het ![hamburgerpictogram](media/sample-tutorial-connect-to-the-samples/expand-nav.png) te selecteren.
   
   ![pictogram voor gegevens ophalen](media/sample-tutorial-connect-to-the-samples/pbi_getdata.png)
5. Selecteer **Voorbeelden**.  
   
   ![Voorbeelden-knop](media/sample-tutorial-connect-to-the-samples/pbi_samplesdownload.png)
6. Selecteer *Retail Analysis Sample* en kies **Verbinding maken**.   
   
   ![gele knop voor verbinding maken](media/sample-tutorial-connect-to-the-samples/pbi_retailanalysissampleconnect.png)

## <a name="what-exactly-was-imported"></a>Wat is er precies geïmporteerd?
Wanneer u bij de voorbeeldinhoudspakketten **Verbinding maken** selecteert, haalt Power BI in werkelijkheid een kopie van dat inhoudspakket op en slaat dit voor u op in de cloud. Omdat de persoon die het inhoudspakket heeft gemaakt, een gegevensset, een rapport en een dashboard heeft opgenomen, krijgt u die wanneer u klikt op **Verbinding maken**. 

1. Power BI maakt het nieuwe dashboard en geeft dit weer op het tabblad **Dashboards**. Het gele sterretje geeft aan dat het nieuw is.
   
   ![Het bericht Geslaagd](media/sample-tutorial-connect-to-the-samples/power-bi-new-dashboard.png)
2. Open het tabblad **Rapporten**.  Hier ziet u een nieuw rapport met de naam *Retail Analysis Sample*.
   
   ![rood kader rond Retail Analysis Sample en een gele ster](media/sample-tutorial-connect-to-the-samples/power-bi-new-report.png)
   
   Bekijk ook het tabblad **Gegevenssets**.  Er is ook een nieuwe gegevensset.
   
   ![rood kader rond Retail Analysis Sample](media/sample-tutorial-connect-to-the-samples/power-bi-new-dataset.png)

## <a name="explore-your-new-content"></a>De nieuwe inhoud verkennen
Verken nu zelf het dashboard, de gegevensset en het rapport. Er zijn veel verschillende manieren om te navigeren naar uw dashboards, rapporten en gegevenssets en slechts een van die manieren wordt hieronder beschreven.  

> [!TIP]
> Wilt u eerst wat meer uitleg?  Bekijk dan de [rondleiding door het voorbeeld Retail Analysis](sample-retail-analysis.md) voor een stapsgewijze uitleg van dit voorbeeld.
> 
> 

1. Ga terug naar het tabblad **Dashboards** en selecteer het dashboard *Voorbeeld van retailanalyse* om dit te openen.    
   
   ![tabblad Dashboard geselecteerd](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards.png)
2. Het dashboard wordt geopend.  Dit bevat diverse visualisatietegels.
   
   ![dashboard met visual gemarkeerd](media/sample-tutorial-connect-to-the-samples/power-bi-dashboards2new.png)
3. Selecteer een van de tegels om het onderliggende rapport te openen.  In dit voorbeeld selecteren we het vlakdiagram (dat een roze kader heeft in de vorige afbeelding). Het rapport wordt geopend op de pagina die dat vlakdiagram bevat.
   
    ![pagina van het rapport met de bijbehorende visual gemarkeerd](media/sample-tutorial-connect-to-the-samples/power-bi-report.png)
   
   > [!NOTE]
   > Als de tegel was gemaakt met [Power BI Q&A](power-bi-tutorial-q-and-a.md), zou in plaats daarvan de Q&A-pagina zijn geopend. Als de tegel [vanuit Excel was vastgemaakt](service-dashboard-pin-tile-from-excel.md) zou Excel Online het in Power BI hebben geopend.
   > 
   > 
1. Terug op het tabblad **Gegevenssets** hebt u verschillende mogelijkheden om de gegevensset te verkennen.  U kunt de set niet openen en alle rijen en kolommen bekijken (zoals wel kan in Power BI Desktop of Excel).  Als iemand een inhoudspakket deelt met collega's, wil hij of zij doorgaans alleen de inzichten delen en de collega's niet direct toegang geven tot de gegevens. Maar dat betekent niet dat u de gegevensset niet kunt verkennen.  
   
   ![Tabblad Gegevenssets](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon2.png)
   
   * Eén manier om de gegevensset te verkennen, is door zelf uw eigen visualisaties en rapporten te maken.  Selecteer het diagrampictogram ![rapportpictogram](media/sample-tutorial-connect-to-the-samples/power-bi-chart-icon4.png) om de gegevensset te openen in de rapportbewerkingsmodus.
     
       ![compleet nieuw rapport](media/sample-tutorial-connect-to-the-samples/power-bi-report-editing.png)
   * Een andere manier om de gegevensset te verkennen, is door [Snelle inzichten](consumer/end-user-insights.md) uit te voeren. Selecteer de drie puntjes (...) en kies **Inzichten verkrijgen**. Wanneer de inzichten gereed zijn, selecteert u **Inzichten weergeven**.
     
       ![Insights-rapport](media/sample-tutorial-connect-to-the-samples/power-bi-insights.png)

## <a name="samples-and-power-bi-desktop"></a>Voorbeelden en Power BI Desktop 
Wanneer u het PBIX-voorbeeldbestand voor het eerst opent, wordt het in de Rapportgave weergegeven en kunt u een oneindig aantal rapportpagina's met visualisaties verkennen, maken en bewerken. De rapportweergave kent vrijwel hetzelfde ontwerp als de bewerkingsweergave van een rapport in de Power BI-service. U kunt er visuele elementen verplaatsen, kopiëren en plakken, samenvoegen, enzovoort.

Het verschil is dat u in Power BI Desktop met uw query's kunt werken en gegevens kunt modelleren om ervoor te zorgen dat uw rapporten de beste inzichten geven in uw gegevens. U kunt uw Power BI Desktop-bestand vervolgens opslaan waar u wilt, bijvoorbeeld op de lokale harde schijf of in de cloud.

1. Open het [PBIX-voorbeeldbestand](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) van de retailanalyse in Power BI Desktop. 

    ![Voorbeeld geopend in de rapportweergave van Power BI](media/sample-tutorial-connect-to-the-samples/power-bi-samples-desktop.png)

1. Het bestand wordt geopend in de rapportweergave. Ziet u de 4 tabbladen onder in de rapporteditor? Dat betekent dat er 4 pagina's in dit rapport zijn en momenteel is de pagina 'New Stores' (nieuwe winkels) geselecteerd. 

    ![close-up van tabbladen onderin en New Stores gemarkeerd](media/sample-tutorial-connect-to-the-samples/power-bi-sample-tabs.png).

3. Zie voor een diepgaande uitleg van de rapporteditor [De rapporteditor... Een rondleiding](service-the-report-editor-take-a-tour.md)

## <a name="what-exactly-was-imported"></a>Wat is er precies geïmporteerd?
Wanneer u het PBIX-voorbeeldbestand in Desktop opent, haalt Power BI in werkelijkheid een kopie van die gegevens op en slaat deze voor u op in de cloud. Vanaf Desktop hebt u toegang tot het rapport ***en de onderliggende gegevensset***. Wanneer de gegevens geladen zijn, probeert Power BI Desktop voor u relaties te zoeken en te maken.  

1. Schakel over naar [gegevensweergave](desktop-data-view.md) door het tabelpictogram ![tabelpictogram](media/sample-tutorial-connect-to-the-samples/power-bi-data-icon.png) te selecteren.
 
    ![Gegevensweergave in Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-sample-data.png)

    De gegevensweergave helpt u bij het controleren, onderzoeken en begrijpen van gegevens in uw Power BI Desktop-model. Het verschilt van de manier waarop u tabellen, kolommen en gegevens in Query-editor bekijkt. In de gegevensweergave bekijkt u gegevens nadat deze in het model zijn geladen.

    Wanneer u een gegevensmodel maakt, wilt u soms zien wat een tabel of kolom nu echt bevat zonder een visueel element te maken op het rapportcanvas, vaak tot rijniveau aan toe. Dit is vooral van toepassing wanneer u metingen en berekende kolommen maakt of als u een gegevenstype of gegevenscategorie moet identificeren.

1. Schakel over naar [Relatieweergave](desktop-relationship-view.md) door het pictogram ![ pictogram dat lijkt op 3 verbonden vakken](media/sample-tutorial-connect-to-the-samples/power-bi-desktop-relationship-icon.png) te selecteren.
 
    ![relatieweergave in Power BI Desktop](media/sample-tutorial-connect-to-the-samples/power-bi-relationships.png)

    In de relatieweergave worden alle tabellen, kolommen en relaties in uw model weergegeven. Hier kunt u relaties bekijken, wijzigen en maken.

## <a name="explore-your-new-content"></a>De nieuwe inhoud verkennen
Verken nu zelf de gegevensset, de relaties en het rapport. Voor een introductie gaat u naar [Aan de slag met Power BI Desktop](desktop-getting-started.md).    


## <a name="next-steps"></a>Volgende stappen

- [Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md)
- [Voorbeelden voor de Power BI-service](sample-datasets.md)
- [Gegevensbronnen voor Power BI](service-get-data.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
