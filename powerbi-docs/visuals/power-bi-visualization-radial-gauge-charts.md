---
title: Radiale-meterdiagrammen in Power BI
description: Radiale-meterdiagrammen in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 24f69255ae12400c23cd9ca506e5b103e14e7ffb
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354887"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Radiale-meterdiagrammen in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Een radiale-meterdiagram heeft een cirkelvormige boog en toont één waarde die de voortgang naar een doel of KPI (Key Performance Indicator) meet. De regel (of *naald*) vertegenwoordigt het doel of de doelwaarde. De arcering vertegenwoordigt de voortgang naar dit doel. De waarde in de boog vertegenwoordigt de voortgangswaarde. In Power BI worden alle mogelijke waarden gelijkmatig verdeeld langs de boog, van minimum (meest linkse waarde) tot maximum (meest rechtse waarde).

![Schermopname van radiale meter.](media/power-bi-visualization-radial-gauge-charts/gauge-m.png)

In dit voorbeeld bent u een autohandelaar die de gemiddelde verkoop van het verkoopteam per maand bijhoudt. De naald vertegenwoordigt een verkoopdoel van 140 auto’s. De minimale mogelijke gemiddelde verkoop is ingesteld op 0 en het maximum is 200.  De blauwe arcering geeft aan dat het team deze maand gemiddeld ongeveer 120 verkopen heeft. Gelukkig is er nog één week om het doel te bereiken.

> [!NOTE]
> Voor het delen van uw rapport met een Power BI-collega moeten u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in Premium-capaciteit.

## <a name="when-to-use-a-radial-gauge"></a>Wanneer gebruikt u een radiale meter

Radiale meters zijn een uitstekende keuze om:

* De voortgang van een doel weer te geven.

* Een percentielmeting weer te geven, zoals een KPI.

* De status van één meting weer te geven.

* Informatie weer te geven die u snel kunt scannen en begrijpen.

## <a name="prerequisites"></a>Vereisten

In deze zelfstudie wordt gebruikgemaakt van het [Excel-bestand met het financiële voorbeeld](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Selecteer linksboven in de menubalk **Gegevens ophalen** > **Excel**
   
2. Zoek uw kopie van het **Excel-bestand met het financiële voorbeeld**

1. Open het **Excel-bestand met het financiële voorbeeld** in de rapportweergave ![Schermopname van het pictogram voor de rapportweergave.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecteer **financiën** en **Blad1**

1. Klik op **Laden**

1. Selecteren ![Schermopname van het gele tabblad.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) om een nieuwe pagina toe te voegen.



## <a name="create-a-basic-radial-gauge"></a>Een eenvoudige radiale meter maken

### <a name="step-1-create-a-gauge-to-track-gross-sales"></a>Stap 1: Een meter maken om de brutoverkoop bij te houden

1. Begin op een nieuwe, lege rapportpagina

1. Selecteer in het deelvenster **Velden** de optie **Brutoverkoop**.

   ![financials-tabel uitgevouwen en bruto verkoop geselecteerd](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue-new.png)

1. Wijzig de aggregatie in **Gemiddelde**.

   ![Schermopname van het deelvenster Velden met Brutoverkoop en Gemiddeld totaal uitgelicht.](media/power-bi-visualization-radial-gauge-charts/changetoaverage-new.png)

1. Selecteer het meterpictogram ![Schermopname van het meterpictogram.](media/power-bi-visualization-radial-gauge-charts/gaugeicon-new.png) om de kolomdiagram te converteren naar een meterdiagram.

    ![Schermopname van de meterdiagram.](media/power-bi-visualization-radial-gauge-charts/gauge-no-target.png)

    Afhankelijk van wanneer u het bestand **Financial Sample** downloadt, ziet u mogelijk getallen die niet overeenkomen met deze getallen.

    > [!TIP]
    > Standaard wordt in Power BI een meterdiagram gemaakt, waarbij wordt aangenomen dat de huidige waarde (in dit geval **Gemiddelde van brutoverkoop**) op het middenpunt van de meter staat. Aangezien de waarde van **Gemiddelde brutoverkoop** $182.760 is, is de beginwaarde (Minimum) ingesteld op 0 en de eindwaarde (Maximum) op het dubbele van de huidige waarde.

### <a name="step-3-set-a-target-value"></a>Stap 3: Een doelwaarde instellen

1. Sleep **KVG** uit het deelvenster **Velden** naar de bron **Doelwaarde**.

1. Wijzig de aggregatie in **Gemiddelde**.

   Power BI voegt een naald toe die de doelwaarde van **$ 145.480** vertegenwoordigt.

   ![Schermopname van de meterdiagram met de Gemiddelde KVG toegevoegd.](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress-new.png)

    Zoals u ziet, hebben we ons doel overschreden.

   > [!NOTE]
   > U kunt ook handmatig een doelwaarde invoeren. Zie de sectie [Handmatige opmaakopties gebruiken om de waarden Minimum, Maximum en Doel in te stellen](#use-manual-format-options-to-set-minimum-maximum-and-target-values).

### <a name="step-4-set-a-maximum-value"></a>Stap 4: Een maximumwaarde instellen

In stap 2 werd in Power BI het veld **Waarde** gebruikt om automatisch een minimum- en maximumwaarde in te stellen. Wat als u uw eigen maximumwaarde wilt instellen? Stel dat u, in plaats van de huidige waarde te verdubbelen als de maximaal mogelijke waarde, het maximum wilt instellen op de hoogste waarde voor Brutoverkoop in uw gegevensset.

1. Sleep **Brutoverkoop** uit het deelvenster **Velden** naar de bron **Maximumwaarde**.

1. Wijzig de aggregatie in **Maximum**.

   ![Schermopname van het deelvenster Velden met Brutoverkoop en Maximale totaal uitgelicht.](media/power-bi-visualization-radial-gauge-charts/setmaximum-new.png)

   De meter wordt opnieuw getekend met een nieuwe eindwaarde, 1,21 miljoen, voor brutoverkoop.

   ![Schermopname van de voltooide meterdiagram.](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Stap 5: Uw rapport opslaan

1. [Sla het rapport op](../create-reports/service-report-save.md).

## <a name="use-manual-format-options-to-set-minimum-maximum-and-target-values"></a>Handmatige opmaakopties gebruiken om de waarden Minimum, Maximum en Doel in te stellen

1. Verwijder **Gross Sales** uit het vak **Maximumwaarde**.

1. Selecteer het pictogram met de verfroller om het deelvenster **Opmaak** te openen.

   ![Schermopname van het meterdiagram en het deelvenster Opmaken met het pictogram verfroller uitgelicht.](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)

1. Vouw de **Meter-as** uit en voer waarden in voor **Min** en **Max**.

    ![Schermopname van de opties voor Meter-as.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)

1. Wis de optie **KVG** in het deelvenster **Velden** om de doelwaarde te verwijderen.

    ![Schermopname van de gewiste optie KVG.](media/power-bi-visualization-radial-gauge-charts/pbi-remove-target.png)

1. Wanneer het veld **Doel** wordt weergegeven onder **Meter-as**, voert u een waarde in.

     ![Schermopname van de opties Meter-as met Doel uitgelicht.](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)

1. Pas de opmaak van het meterdiagram desgewenst verder aan.

Als u deze stappen hebt uitgevoerd, beschikt u over een meterdiagram die er ongeveer als volgt uitziet:

![Schermopname van de definitieve meterdiagram.](media/power-bi-visualization-radial-gauge-charts/power-bi-final.png)

## <a name="next-step"></a>Volgende stap

* [KPI-visualisaties (Key Performance Indicator)](power-bi-visualization-kpi.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

