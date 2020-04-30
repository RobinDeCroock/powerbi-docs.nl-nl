---
title: Een nieuwe Power-app insluiten in een Power BI-rapport
description: Een app insluiten die gebruikmaakt van dezelfde gegevensbron en waarop kan worden gefilterd, net als bij andere rapportitems
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 03/17/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: bd27973a1cf6a73ba79079911ec175f990925524
ms.sourcegitcommit: 20f15ee7a11162127e506b86d21e2fff821a4aee
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82585457"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Zelfstudie: Een Power Apps-visual insluiten in een Power BI-rapport

In deze zelfstudie gebruikt u de Power Apps-visual om een nieuwe app te maken die wordt ingesloten in een Power BI-voorbeeldrapport. Deze app communiceert met andere visuals in dit rapport.

Als u geen Power Apps-abonnement hebt, [maakt u een gratis account](https://web.powerapps.com/signup?redirect=marketing&email=) voordat u begint.

In deze zelfstudie leert u het volgende:
> [!div class="checklist"]
> * Een Power Apps-visual toevoegen aan een Power BI-rapport
> * Werk in Power Apps om een nieuwe app te maken die gebruikmaakt van gegevens uit het Power BI-rapport
> * De Power Apps-visual in het rapport weergeven en ermee werken

## <a name="prerequisites"></a>Vereisten

* [Google Chrome](https://www.google.com/chrome/browser/)- of [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)-browser
* Een [Power BI-abonnement](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi) waarin het [voorbeeld van een verkoopkansanalyse](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample) is geïnstalleerd
* Begrip van hoe u [apps maakt in Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/data-platform-create-app-scratch) en hoe u [Power BI-rapporten bewerkt](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)



## <a name="create-a-new-app"></a>Een nieuwe app maken
Wanneer u de Power Apps-visual toevoegt aan uw rapport, wordt Power Apps Studio gestart met een livegegevensverbinding tussen Power Apps en Power BI.

1. Open het voorbeeldrapport van een verkoopkansanalyse en selecteer de pagina *Toekomstige verkoopkansen*. 


2. Verplaats en wijzig het formaat van enkele van de rapporttegels om ruimte te maken voor de nieuwe visual.

    ![Rapporttegels verplaatsen en het formaat wijzigen](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. Selecteer in het deelvenster Visualisaties het Power Apps-pictogram, en wijzig de grootte van de visual zodat deze past in de ruimte die u hebt gemaakt.

    ![Deelvenster Visualisatie met het Power Apps-pictogram geselecteerd](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. In het deelvenster **Velden** selecteert u **Naam**, **Productcode** en vervolgens **Verkoopfase**. 

    ![velden selecteren](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. Selecteer in de Power Apps-visual de Power Apps-omgeving waarin u de app wilt maken. Selecteer vervolgens **Nieuwe maken**.

    ![Een nieuwe app maken](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    In Power Apps Studio ziet u dat er een basis-app wordt gemaakt met een *galerie* waarin één van de velden wordt weergegeven die u hebt geselecteerd in Power BI.

    ![Power Apps wordt geopend](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Wijzig de grootte van de galerie zodat deze slechts de helft van het scherm in beslag neemt. 

6. Selecteer in het linkerdeelvenster de optie **Screen1** en stel de eigenschap **Vullen** van het scherm in op LightBlue (voor een betere zichtbaarheid in het rapport).

    ![kleurenpalet](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Maak wat ruimte voor een labelbesturingselement. 

    ![galeriedimensies wijzigen](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. Voeg onder **galerie** een tekstlabelbesturingselement in.

   ![labelbesturingselement](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Sleep het label naar de onderkant van de visual. Stel de eigenschap **Tekst** in op `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Nu wordt het totale aantal verkoopkansen weergegeven in de gegevensset.

    ![App met een galerie waarvan het formaat is gewijzigd](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![App met een bijgewerkt label](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Sla de app op met de naam ‘Verkoopkansen-app’. 

    ![sla de app op](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>De app in het rapport weergeven
De app is nu beschikbaar in het Power BI-rapport. De app communiceert met andere visuals omdat dezelfde gegevensbron wordt gebruikt.

![App in Power BI-rapport](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

In het Power BI-rapport selecteert u **Jan** in de slicer. Hiermee wordt het volledige rapport gefilterd, inclusief de gegevens uit de app.

![gefilterd rapport](media/power-bi-visualization-powerapp/power-bi-last.png)

Het aantal verkoopkansen uit de app komt overeen met het aantal in de linkerbovenhoek van het rapport. U kunt andere items in het rapport en gegevens uit de app-updates selecteren.


## <a name="clean-up-resources"></a>Resources opschonen
Als u het voorbeeld van een verkoopanalyse niet meer wilt gebruiken, kunt u het dashboard, het rapport en de gegevensset verwijderen.


## <a name="next-steps"></a>Volgende stappen
[Q&A-visual](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Zelfstudie: Een Power Apps-visual insluiten in een Power BI-rapport](https://docs.microsoft.com/powerapps/maker/canvas-apps/powerapps-custom-visual)    
