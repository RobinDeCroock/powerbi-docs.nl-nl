---
title: Trechterdiagrammen
description: Trechterdiagrammen in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 071b45a4ad9cbd9c753c44de5c55a352767bccbf
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61067734"
---
# <a name="funnel-charts"></a>Trechterdiagrammen
Een trechterdiagram helpt u om een lineaire proces dat bestaat uit opeenvolgende verbonden fasen te visualiseren. Bijvoorbeeld verkoopactiviteiten waarbij de klanten in bepaalde fasen worden bijgehouden: Lead \> Qualified Lead \> Prospect \> Contract \> Close.  De vorm van de trechter brengt de status van het proces dat u bijhoudt in één oogopslag over.

Elke fase van de trechter vertegenwoordigt een percentage van het totaal. In de meeste gevallen heeft een trechterdiagram dus de vorm een trechter. De eerste fase is het grootst en elke latere fase is kleiner dan de vorige.  Een trechter in de vorm van een peer is ook nuttig. Hiermee kunt u een probleem in het proces identificeren.  Maar normaal gesproken is de eerste fase (de startfase) het grootst.

![Voorbeeld van blauwe trechter](media/power-bi-visualization-funnel-charts/funnelplain.png)

## <a name="when-to-use-a-funnel-chart"></a>Wanneer u een trechterdiagram gebruikt
In de volgende gevallen komen trechterdiagrammen goed van pas:

* wanneer de gegevens sequentieel zijn en ten minste 4 fasen doorlopen.
* wanneer het aantal 'items' in de eerste fase naar verwachting groter is dan het aantal in de laatste fase.
* om potentieel (inkomsten/verkoop/deals/enz) te berekenen fasen.
* om conversie- en retentiepercentages te berekenen en bij te houden.
* om knelpunten in een lineair proces te identificeren.
* om de werkstroom van een winkelwagen bij te houden.
* om de voortgang en het succes van reclame-/marketingcampagnes met doorklikken bij te houden.

## <a name="working-with-funnel-charts"></a>Werken met trechterdiagrammen
Trechterdiagrammen:

* Kunnen worden vastgemaakt in rapporten en Q&A.
* Kunnen worden gesorteerd.
* Bieden ondersteuning voor veelvouden.
* Kunnen worden gemarkeerd en gefilterd door andere visualisaties op dezelfde rapportpagina.
* Kunnen worden gebruikt om andere visualisaties op dezelfde rapportpagina te markeren en filteren.

## <a name="create-a-basic-funnel-chart"></a>Een basistrechterdiagram maken
Bekijk deze video om te zien hoe Will een trechterdiagram maakt op basis van het voorbeeld van verkoop en marketing.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Maak nu uw eigen trechterdiagram dat het aantal mogelijkheden weergeeft dat we hebben in elk van onze verkoopfasen.

In deze instructies wordt het voorbeeld van een verkoopkansanalyse gebruikt. Om mee te lezen kunt u het [voorbeeld downloaden](../sample-datasets.md) voor de Power BI-service (app.powerbi.com) of voor Power BI Desktop.   

1. Start op een lege rapportpagina en selecteer het veld **Verkoopfase** \> **Verkoopfase**. Als u de Power BI-service gebruikt, moet u het rapport openen in de [bewerkweergave](../service-interact-with-a-report-in-editing-view.md).
   
    ![selecteer Verkoopfase](media/power-bi-visualization-funnel-charts/funnelselectfield_new.png)
2. [Converteer de grafiek](power-bi-report-change-visualization-type.md) naar een trechter. U ziet dat **Verkoopfase** zich bevindt in het veld **Groep**. 
3. Selecteer vanuit het deelvenster **Velden** de optie **Feit** \> **Aantal kansen**.
   
    ![de trechtergrafiek bouwen](media/power-bi-visualization-funnel-charts/power-bi-funnel.png)
4. Als u de muisaanwijzer boven een balk houdt, wordt een schat aan informatie weergegeven.
   
   * De naam van de fase
   * Aantal verkoopkansen in deze fase
   * Algemene conversieverhouding (% van Lead) 
   * Fase-naar-fase (oftewel Drop Rate) is het percentage van de vorige fase (in dit geval Voorstelfase/Oplossingsfase)
     
     ![Details voor voorstelbalk](media/power-bi-visualization-funnel-charts/funnelhover_new.png)
5. [Voeg de trechter toe als een dashboardtegel](../service-dashboard-tiles.md). 
6. [Sla het rapport op](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren
Zie [Een filter aan een rapport toevoegen](../power-bi-report-add-filter.md) voor meer informatie over het gebruik van het deelvenster Filters.

Als u een balk in een trechter markeert, worden de andere visualisaties op de rapportpagina ook gefilterd en omgekeerd. Als u op de voet wilt volgen, voegt u nog enkele visuele elementen toe op de rapportpagina met de trechtergrafiek.

1. Selecteer op de trechter de balk **Voorstel**. Hiermee worden de andere visualisaties op de pagina kruislings gemarkeerd. Gebruik CTRL voor meervoudige selectie.
   
   ![korte video waarin visuele interacties worden getoond](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Zie [Interacties tussen visuele elementen in Power BI](../service-reports-visual-interactions.md) als u voorkeuren wilt instellen voor hoe visuele elementen elkaar kruislings markeren en filteren

## <a name="create-a-funnel-chart-using-qa"></a>Een trechterdiagram maken met Q&A
Open het dashboard Voorbeeld van een verkoopkansanalyse of een ander dashboard waarop ten minste één visualisatie uit de gegevensset Voorbeeld van een verkoopkansanalyse is vastgezet.  Wanneer u een vraag invoert in Q&A, zoekt Power BI antwoorden in alle gegevenssets die zijn gekoppeld aan het geselecteerde dashboard (waaraan tegels zijn vastgemaakt). Zie [Power BI - basisconcepten](../service-basic-concepts.md) voor meer informatie.

1. Begin op het dashboard Voorbeeld van een verkoopkansanalyse uw vraag te typen in het vak Q&A.
   
   ![vraagvak- en trechterdiagrammen](media/power-bi-visualization-funnel-charts/power-bi-qna.png)
   
2. Zorg ervoor dat u ‘als trechter’ toevoegt zodat Power BI weet welk type visualisatie u wilt gebruiken.

## <a name="next-steps"></a>Volgende stappen

[Meters in Power BI](power-bi-visualization-radial-gauge-charts.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
