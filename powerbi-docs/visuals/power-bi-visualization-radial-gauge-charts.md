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
ms.date: 09/21/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 079494a47452ca0ca043032f78fa35c7d1755d11
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61068089"
---
# <a name="radial-gauge-charts-in-power-bi"></a>Radiale-meterdiagrammen in Power BI
Een radiale-meterdiagram heeft een cirkelvormige boog en toont één waarde die de voortgang naar een doel/KPI meet.  Het doel of de doelwaarde wordt weergegeven door de lijn (naald). De voortgang naar het doel wordt weergegeven door de arcering.  En de waarde die de voortgang vertegenwoordigt, wordt vetgedrukt weergegeven in de boog. Alle mogelijke waarden zijn gelijkmatig verdeeld langs de boog, van minimum (meest linkse waarde) tot maximum (meest rechtse waarde).

In het onderstaande voorbeeld zijn we een autohandelaar die de gemiddelde verkoop van het verkoopteam per maand bijhoudt. Ons doel is 140 en dat wordt weergegeven door de zwarte naald.  De minimale mogelijke gemiddelde verkoop is ingesteld op 0 en we hebben het maximum ingesteld op 200.  De blauwe arcering geeft aan dat we deze maand momenteel ongeveer 120 verkopen gemiddeld hebben. Gelukkig hebben we nog een week de tijd om ons doel te bereiken.

![](media/power-bi-visualization-radial-gauge-charts/gauge_m.png)

## <a name="when-to-use-a-radial-gauge"></a>Wanneer gebruikt u een radiale meter
Radiale meters zijn een uitstekende keuze om:

* de voortgang naar een doel weer te geven.
* een percentielmeting weer te geven, zoals een KPI.
* de status van één meting weer te geven.
* informatie weer te geven die snel kan worden gelezen en begrepen.

### <a name="prerequisites"></a>Vereisten
 - Power BI-service of Power BI Desktop
 - Excel-werkmap met financiële voorbeelden: [het voorbeeld rechtstreeks downloaden](http://go.microsoft.com/fwlink/?LinkID=521962).

## <a name="create-a-basic-radial-gauge"></a>Een eenvoudige radiale meter maken
Deze instructies maken gebruik van Power BI-service. Als u deze wilt volgen, meld u zich aan bij Power BI en opent u het Excel-bestand Financial Sample.  

Of kijk naar Will die laat zien hoe u eenvoudige metrische visuele elementen maakt: meters, kaarten en KPI's.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

### <a name="step-1-open-the-financial-sample-excel-file"></a>Stap 1: Het Excel-bestand Financial Sample openen
1. [Download het Excel-bestand Financial Sample](../sample-financial-download.md) als u dit nog niet hebt gedaan. Vergeet niet de opslaglocatie.

2. Open het bestand in ***Power BI-service***  door **Gegevens ophalen \> Bestanden** te selecteren en naar de locatie te bladeren waar u het bestand hebt opgeslagen. Selecteer **Importeren**. Financial Sample wordt als gegevensset toegevoegd aan uw werkruimte.

3. Selecteer in de inhoudslijst **Gegevensset** **Financial Sample** om dit in de modus Verkennen te openen.

    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-dataset.png)

### <a name="step-2-create-a-gauge-to-track-gross-sales"></a>Stap 2: Een meter maken om de brutoverkoop bij te houden
1. Selecteer **Gross Sales** (brutoverkoop) in het deelvenster **Velden**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/grosssalesvalue_new.png)
2. Wijzig de aggregatie in **Gemiddelde**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/changetoaverage_new.png)
3. Selecteer het meterpictogram ![](media/power-bi-visualization-radial-gauge-charts/gaugeicon_new.png) om het kolomdiagram om te zetten in een meter.
   
   Power BI maakt standaard een meterdiagram waarin ervan wordt uitgegaan dat de huidige waarde (in dit geval het gemiddelde van Gross Sales) ligt op het punt halverwege de meter. Aangezien de gemiddelde brutoverkoop $ 182.760 is, is de beginwaarde (Minimum) ingesteld op 0 en de eindwaarde (Maximum) op het dubbele van de huidige waarde.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gauge_no_target.png)

### <a name="step-3-set-a-target-value"></a>Stap 3: Een doelwaarde instellen
1. Sleep **COGS** naar het veld **Doelwaarde**.
2. Wijzig de aggregatie in **Gemiddelde**.
   Power BI voegt een naald toe die de doelwaarde van **$ 145.480** vertegenwoordigt. Zoals u ziet, hebben we ons doel overschreden.
   
   ![](media/power-bi-visualization-radial-gauge-charts/gaugeinprogress_new.png)
   
   > [!NOTE]
   > U kunt ook handmatig een doelwaarde invoeren.  Zie 'Opmaakopties gebruiken om de minimum-, maximum- en doelwaarde handmatig in te stellen' hieronder.
   > 
   > 

### <a name="step-4-set-a-maximum-value"></a>Stap 4: Een maximumwaarde instellen
In stap 2 gebruikte Power BI het veld Waarde om automatisch een minimum (begin) en maximum (eind) in te stellen.  Stel echter dat u uw eigen maximumwaarde wilt instellen.  Stel dat u, in plaats van de huidige waarde te verdubbelen als de maximaal mogelijke waarde, het maximum wilt instellen op de hoogste waarde voor brutoverkoop in uw gegevensset? 

1. Sleep **Gross Sales** van de lijst **Velden** naar het vak **Maximumwaarde**.
2. Wijzig de aggregatie in **Maximum**.
   
   ![](media/power-bi-visualization-radial-gauge-charts/setmaximum_new.png)
   
   De meter wordt opnieuw getekend met een nieuwe eindwaarde, 1,21 miljoen, voor brutoverkoop.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-final-gauge.png)

### <a name="step-5-save-your-report"></a>Stap 5: Uw rapport opslaan
1. [Sla het rapport op](../service-report-save.md).
2. [Voeg het meterdiagram toe aan een dashboardtegel](../service-dashboard-pin-tile-from-report.md). 

## <a name="use-formatting-options-to-manually-set-minimum-maximum-and-target-values"></a>Opmaakopties gebruiken om de minimum-, maximum- en doelwaarde handmatig in te stellen
1. Verwijder **Gross Sales** uit het vak **Maximumwaarde**.
2. Open het opmaakvenster door het pictogram met de verfroller te selecteren.
   
   ![](media/power-bi-visualization-radial-gauge-charts/power-bi-roller.png)
3. Vouw **Meter-as** uit en voer waarden in voor **Min** en **Max**.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-axis.png)
4. Verwijder de huidige doelwaarde door het vinkje naast **COGS** te verwijderen.
   
    ![](media/power-bi-visualization-radial-gauge-charts/pbi_remove_target.png)
5. Wanneer het veld **Doel** wordt weergegeven onder **Meter-as**, voert u een waarde in.
   
    ![](media/power-bi-visualization-radial-gauge-charts/power-bi-gauge-target.png)
6. Pas de opmaak van het meterdiagram desgewenst verder aan.

## <a name="next-step"></a>Volgende stap

[Meters in Power BI](power-bi-visualization-kpi.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
