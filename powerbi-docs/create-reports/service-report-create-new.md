---
title: 'Een rapport maken op basis van een Excel-bestand in de Power BI-service '
description: Een Power BI-rapport maken op basis van een Excel-bestand in de Power BI-service.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: a971e0d0b35b0a3988a1c10ea2b7b801830229d6
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721542"
---
# <a name="create-a-report-from-an-excel-file-in-the-power-bi-service"></a>Een rapport maken op basis van een Excel-bestand in de Power BI-service
U hebt [Rapporten in Power BI](../consumer/end-user-reports.md) gelezen en u wilt nu uw eigen rapport maken. Er zijn verschillende manieren om een rapport te maken. In dit artikel gaan we eerst in de Power BI-service een basisrapport maken op basis van een Excel-bestand. Als u de basisbeginselen van het maken van een rapport onder de knie hebt, kunt u met [Volgende stappen](#next-steps) aan het einde naar meer geavanceerde onderwerpen over rapporten gaan.  

## <a name="prerequisites"></a>Vereisten
- [Meld u aan voor de Power BI-service](../fundamentals/service-self-service-signup-for-power-bi.md). 
- [Download het Excel-bestand Voorbeeld van een retailanalyse](https://go.microsoft.com/fwlink/?LinkId=529778) en sla het bestand op de computer op of in OneDrive voor Bedrijven.

## <a name="import-the-excel-file"></a>Het Excel-bestand importeren
Bij deze methode om een rapport te maken begint u met een bestand en een leeg rapportcanvas. U kunt meedoen aan de hand van het Excel-bestand Voorbeeld van een retailanalyse.

1. Selecteer **Mijn werkruimte** in het navigatievenster.
   
   :::image type="content" source="media/service-report-create-new/power-bi-select-my-workspace.png" alt-text="Schermopname van het selecteren van Mijn werkruimte.":::
2. Selecteer **Gegevens ophalen** onderaan het navigatievenster.
   
   ![Gegevens ophalen](media/service-report-create-new/power-bi-get-data3.png)
3. Selecteer **Bestanden** en navigeer naar de locatie waar u het voorbeeld van een retailanalyse hebt opgeslagen.
   
    ![Bestanden selecteren](media/service-report-create-new/power-bi-select-files.png)
4. Selecteer voor deze oefening **Importeren**.
   
   ![Importeren selecteren](media/service-report-create-new/power-bi-import.png)
5. Selecteer **Openen**.

   Zodra het Excel-bestand is geïmporteerd, wordt het als een *gegevensset* vermeld in de lijst met werkruimten.

1. Selecteer **Meer opties (...)** naast de gegevensset en selecteer **Rapport maken**.
   
   :::image type="content" source="media/service-report-create-new/power-bi-dataset-create-report.png" alt-text="Schermopname van het selecteren van Rapport maken.":::
6. De rapporteditor wordt geopend. 
   
   ![Schermopname van de rapporteditor.](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Selecteer het menupictogram om het navigatiedeelvenster te verbergen, zodat u meer ruimte krijgt.
> 
> :::image type="content" source="../media/power-bi-hide-navigation-pane.png" alt-text="Schermopname van Selecteer het menupictogram om het navigatiedeelvenster te verbergen.":::


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

* [Visualisaties aan een dashboard vastmaken](service-dashboard-pin-tile-from-report.md)
* [Rapportinstellingen in de Power BI-service wijzigen](power-bi-report-settings.md)
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
