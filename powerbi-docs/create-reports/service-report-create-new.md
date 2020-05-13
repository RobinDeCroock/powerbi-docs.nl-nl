---
title: Een rapport maken van een gegevensset
description: Maak een Power BI-rapport van een gegevensset.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 66a690f9ee786747e59a55d498dfd206ecbcb992
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349742"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Een rapport in de Power BI-service maken door een gegevensset te importeren
U hebt [Rapporten in Power BI](../consumer/end-user-reports.md) gelezen en u wilt nu uw eigen rapport maken. Er zijn verschillende manieren om een rapport te maken. In dit artikel gaan we eerst in de Power BI-service een basisrapport op basis van een Excel-gegevensset maken. Als u de basisbeginselen van het maken van een rapport onder de knie hebt, kunt u met [Volgende stappen](#next-steps) aan het einde naar meer geavanceerde onderwerpen over rapporten gaan.  

## <a name="prerequisites"></a>Vereisten
- [Meld u aan voor de Power BI-service](../fundamentals/service-self-service-signup-for-power-bi.md). Zie [Rapportweergave in Desktop](desktop-report-view.md) voor het maken van rapporten met Power BI Desktop. 
- [Download de Excel-gegevensset Voorbeeld van een retailanalyse](https://go.microsoft.com/fwlink/?LinkId=529778) en sla deze op in OneDrive voor bedrijven of lokaal.

## <a name="import-the-dataset"></a>De gegevensset importeren
Bij deze methode om een rapport te maken begint u met een gegevensset en een leeg rapportcanvas. U kunt mee doen met de Excel-gegevensset Voorbeeld van een retailanalyse.

1. We maken het rapport in een Power BI-servicewerkruimte. Selecteer daarom een bestaande werkruimte of maak een nieuwe.
   
   ![Lijst met werkruimten](media/service-report-create-new/power-bi-workspaces2.png)
2. Selecteer **Gegevens ophalen** onderaan het navigatievenster.
   
   ![Gegevens ophalen](media/service-report-create-new/power-bi-get-data3.png)
3. Selecteer **Bestanden** en navigeer naar de locatie waar u het voorbeeld van een retailanalyse hebt opgeslagen.
   
    ![Bestanden selecteren](media/service-report-create-new/power-bi-select-files.png)
4. Selecteer voor deze oefening **Importeren**.
   
   ![Importeren selecteren](media/service-report-create-new/power-bi-import.png)
5. Als de gegevensset is geïmporteerd, selecteert u **Gegevensset weergeven**.
   
   ![Gegevensset weergeven selecteren](media/service-report-create-new/power-bi-view-dataset.png)
6. Als u een gegevensset bekijkt, wordt de rapporteditor geopend.  U ziet een leeg canvas en de bewerkingshulpmiddelen voor het rapport.
   
   ![Rapporteditor](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Als u niet weet hoe u een rapportcanvas moet bewerken of als u uw kennis wilt opfrissen, kunt u [een rondleiding van de rapporteditor volgen](service-the-report-editor-take-a-tour.md) voordat u doorgaat.> 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Een radiale meter toevoegen aan het rapport
Nu onze gegevensset is geïmporteerd, kunnen we vragen beantwoorden.  Onze Chief Marketing Officer (CMO) wil weten hoe dicht we de verkoopdoelstellingen voor dit jaar zijn genaderd. Een meter is een [goede visualisatiekeuze](../visuals/power-bi-report-visualizations.md) om dit soort informatie weer te geven.

1. Selecteer **Verkoop** > **Omzet van dit jaar** > **Waarde** in het deelvenster Velden.
   
    ![Staafdiagram in rapporteditor](media/service-report-create-new/power-bi-report-step1.png)
2. Converteer de visual naar een meter door de metersjabloon te selecteren ![Meterpictogram](media/service-report-create-new/powerbi-gauge-icon.png) in het deelvenster **Visualisaties**.
   
    ![Metervisual in rapporteditor](media/service-report-create-new/power-bi-report-step2.png)
3. Sleep **Verkoop** > **Omzet van dit jaar** > **Doel** naar de bron **Doelwaarde**. Het lijkt erop dat we heel dicht bij ons doel zijn.
   
    ![Metervisual met Doel als doelwaarde](media/service-report-create-new/power-bi-report-step3.png)
4. Dit is een goed moment om uw rapport op te slaan.
   
   ![Menu Bestand](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Een vlakdiagram en slicer toevoegen aan het rapport
Onze CMO heeft nog een paar vragen voor ons. Ze willen graag weten hoe de omzet dit jaar zich verhoudt tot de omzet van vorig jaar. En ze willen graag de resultaten per district zien.

1. Laten we eerst wat ruimte maken op ons canvas. Selecteer de meter en verplaats deze naar de rechterbovenhoek. Pak en sleep een van de hoeken om het vlak kleiner te maken.
2. Hef de selectie van de meter op. Selecteer **Verkoop** > **Omzet van dit jaar** > **Waarde** in het deelvenster Velden en selecteer **Verkoop** > **Omzet van vorig jaar**.
   
    ![Rapporteditor met meter en staafdiagram](media/service-report-create-new/power-bi-report-step4.png)
3. Converteer de visual naar een vlakdiagram door de vlakdiagramsjabloon ![Diagrampictogram](media/service-report-create-new/power-bi-areachart-icon.png) te selecteren in het deelvenster **Visualisaties**.
4. Selecteer **Tijd** > **Periode** om deze toe te voegen aan de bron **As**.
   
    ![Rapporteditor met geactiveerd vlakdiagram](media/service-report-create-new/power-bi-report-step5.png)
5. Als u de visualisatie wilt sorteren op tijdsperiode, selecteert u de weglatingstekens en kiest u **Sorteren op periode**.
6. Nu gaan we de slicer toevoegen. Selecteer een leeg gebied in het canvas en kies de sjabloon ![Slicerpictogram](media/service-report-create-new/power-bi-slicer-icon.png) Slicer. We hebben nu een lege slicer op ons canvas.
   
    ![rapportcanvas](media/service-report-create-new/power-bi-report-step6.png)    
7. Selecteer **District** > **District** in het deelvenster Velden. Verplaats de slicer en verander het formaat ervan.
   
    ![Rapporteditor, District toevoegen](media/service-report-create-new/power-bi-report-step7.png)  
8. Ga met de slicer zoeken naar patronen en inzichten per district.
   
   ![Video van het gebruik van slicer](media/service-report-create-new/power-bi-slicer-video2.gif)  

Blijf uw gegevens verkennen en visualisaties toevoegen. Wanneer u interessante inzichten tegenkomt, kunt u deze [vastmaken aan een dashboard](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Volgende stappen

* Meer informatie over [visualisaties aan een dashboard vastmaken](service-dashboard-pin-tile-from-report.md)   
* Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
