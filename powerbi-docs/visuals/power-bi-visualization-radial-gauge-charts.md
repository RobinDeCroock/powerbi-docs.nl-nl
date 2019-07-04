---
title: Radiale-meterdiagrammen in Power BI
description: Radiale-meterdiagrammen in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6Epqa
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8b0db9aebe72d54aa464ec012e614ae0ec5bc723
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390645"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Radiale-meterdiagrammen in Power BI

Een radiale-meterdiagram heeft een cirkelvormige boog en toont één waarde die de voortgang naar een doel of KPI (Key Performance Indicator) meet. De regel (of *naald*) vertegenwoordigt het doel of de doelwaarde. De arcering vertegenwoordigt de voortgang naar dit doel. De waarde in de boog vertegenwoordigt de voortgangswaarde. In Power BI worden alle mogelijke waarden gelijkmatig verdeeld langs de boog, van minimum (meest linkse waarde) tot maximum (meest rechtse waarde).

![Schermopname van radiale meter.](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

In dit voorbeeld bent u een autohandelaar die de gemiddelde verkoop van het verkoopteam per maand bijhoudt. De naald vertegenwoordigt een verkoopdoel van 140 auto’s. De minimale mogelijke gemiddelde verkoop is ingesteld op 0 en het maximum is 200.  De blauwe arcering geeft aan dat het team deze maand gemiddeld ongeveer 120 verkopen heeft. Gelukkig is er nog één week om het doel te bereiken.

Kijk hoe Will op zichzelf staande metrische visualisaties maakt: meters, kaarten en KPI's.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-radial-gauge"></a>Wanneer gebruikt u een radiale meter

Radiale meters zijn een uitstekende keuze om:

* De voortgang van een doel weer te geven.

* Een percentielmeting weer te geven, zoals een KPI.

* De status van één meting weer te geven.

* Informatie weer te geven die u snel kunt scannen en begrijpen.

## <a name="prerequisites"></a>Vereisten

* De Power BI-service of Power BI Desktop

* Excel-werkmap met financiële voorbeelden: [het voorbeeld rechtstreeks downloaden](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Een eenvoudige radiale meter maken

Deze instructies maken gebruik van de Power BI-service. Als u deze wilt volgen, meld u zich aan bij Power BI en opent u het Excel-bestand Financial Sample.

### <a name="step-1-open-the-financial-sample-excel-file"></a>Stap 1: Het Excel-bestand Financial Sample openen

1. Download het [Excel-bestand Financial Sample](../sample-financial-download.md) als u dit nog niet hebt gedaan. Vergeet niet waar u dit opslaat.

1. Selecteer in de Power BI-service **Gegevens ophalen** > **Bestanden**.

1. Selecteer **Lokaal bestand** en blader naar de locatie van het voorbeeldbestand.

1. Selecteer **Importeren**. Financial Sample wordt in Power BI als gegevensset toegevoegd aan uw werkruimte.

1. Selecteer in de inhoudslijst **Gegevensset** het pictogram **Rapport maken** voor **Financial Sample**.

    ![Schermopname van de lijst Gegevensset met een pijl die wijst naar het pictogram Rapport maken voor Financial Sample.](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Stap 2: Een meter maken om de brutoverkoop bij te houden

In de laatste sectie, toen u het pictogram **Rapport maken** hebt geselecteerd, is in Power BI een leeg rapport gemaakt in de bewerkingsweergave.

1. Selecteer in het deelvenster **Velden** de optie **Brutoverkoop**.

   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)

1. Wijzig de aggregatie in **Gemiddelde**.

   ![Schermopname van het deelvenster Velden met Brutoverkoop en Gemiddeld totaal uitgelicht.](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)

1. Selecteer het meterpictogram ![Schermopname van het meterpictogram.](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) om de kolomdiagram te converteren naar een meterdiagram.

    ![Schermopname van de meterdiagram.](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

    Afhankelijk van wanneer u het bestand **Financial Sample** downloadt, ziet u mogelijk getallen die niet overeenkomen met deze getallen.

    > [!TIP]
    > Standaard wordt in Power BI een meterdiagram gemaakt, waarbij wordt aangenomen dat de huidige waarde (in dit geval **Gemiddelde van brutoverkoop**) op het middenpunt van de meter staat. Aangezien de waarde van **Gemiddelde brutoverkoop** $182.760 is, is de beginwaarde (Minimum) ingesteld op 0 en de eindwaarde (Maximum) op het dubbele van de huidige waarde.

### <a name="step-3-set-a-target-value"></a>Stap 3: Een doelwaarde instellen

1. Sleep **KVG** uit het deelvenster **Velden** naar de bron **Doelwaarde**.

1. Wijzig de aggregatie in **Gemiddelde**.

   Power BI voegt een naald toe die de doelwaarde van **$ 145.480** vertegenwoordigt.

   ![Schermopname van de meterdiagram met de Gemiddelde KVG toegevoegd.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)

    Zoals u ziet, hebben we ons doel overschreden.

   > [!NOTE]
   > U kunt ook handmatig een doelwaarde invoeren. Zie de sectie [Handmatige opmaakopties gebruiken om de waarden Minimum, Maximum en Doel in te stellen](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Stap 4: Een maximumwaarde instellen

In stap 2 werd in Power BI het veld **Waarde** gebruikt om automatisch een minimum- en maximumwaarde in te stellen. Wat als u uw eigen maximumwaarde wilt instellen? Stel dat u, in plaats van de huidige waarde te verdubbelen als de maximaal mogelijke waarde, het maximum wilt instellen op de hoogste waarde voor Brutoverkoop in uw gegevensset.

1. Sleep **Brutoverkoop** uit het deelvenster **Velden** naar de bron **Maximumwaarde**.

1. Wijzig de aggregatie in **Maximum**.

   ![Schermopname van het deelvenster Velden met Brutoverkoop en Maximale totaal uitgelicht.](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)

   De meter wordt opnieuw getekend met een nieuwe eindwaarde, 1,21 miljoen, voor brutoverkoop.

   ![Schermopname van de voltooide meterdiagram.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Stap 5: Uw rapport opslaan

1. [Sla het rapport op](../service-report-save.md).

1. [Voeg het meterdiagram toe aan een dashboardtegel](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Handmatige opmaakopties gebruiken om de waarden Minimum, Maximum en Doel in te stellen

1. Verwijder **Gross Sales** uit het vak **Maximumwaarde**.

1. Selecteer het pictogram met de verfroller om het deelvenster **Opmaak** te openen.

   ![Schermopname van het meterdiagram en het deelvenster Opmaken met het pictogram verfroller uitgelicht.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Vouw de **Meter-as** uit en voer waarden in voor **Min** en **Max**.

    ![Schermopname van de opties voor Meter-as.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Wis de optie **KVG** in het deelvenster **Velden** om de doelwaarde te verwijderen.

    ![Schermopname van de gewiste optie KVG.](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)

1. Wanneer het veld **Doel** wordt weergegeven onder **Meter-as**, voert u een waarde in.

     ![Schermopname van de opties Meter-as met Doel uitgelicht.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Pas de opmaak van het meterdiagram desgewenst verder aan.

Als u deze stappen hebt uitgevoerd, beschikt u over een meterdiagram die er ongeveer als volgt uitziet:

![Schermopname van de definitieve meterdiagram.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Volgende stap

* [KPI-visualisaties (Key Performance Indicator)](power-bi-visualization-kpi.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)