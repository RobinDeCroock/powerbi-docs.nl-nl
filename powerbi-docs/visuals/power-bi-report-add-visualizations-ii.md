---
title: 'Deel 2: Visualisaties toevoegen aan een Power BI-rapport'
description: 'Deel 2: Visualisaties toevoegen aan een Power BI-rapport'
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410086"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>Deel 2: Visualisaties toevoegen aan een Power BI-rapport
In [Deel 1](power-bi-report-add-visualizations-ii.md) hebt u een eenvoudige visualisatie gemaakt door selectievakjes naast de veldnamen te selecteren.  In deel 2 leert u hoe u slepen-en-neerzetten kunt gebruiken, en hoe u gebruik kunt maken van de volledige functionaliteit van de deelvensters **Velden** en **Visualisaties** om visualisaties te maken en te wijzigen.

### <a name="prerequisites"></a>Vereisten
- [Deel 1](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop - visualisaties kunnen worden toegevoegd aan rapporten met gebruik van de Power BI-service of Power BI Desktop. In deze zelfstudie wordt Power BI Desktop gebruikt. 
- [Voorbeeld Retail Analysis](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>Een nieuwe visualisatie maken
In deze zelfstudie verdiepen we ons in de gegevensset voor retailanalyse en maken we een aantal belangrijke visualisaties.

### <a name="open-a-report-and-add-a-new-blank-page"></a>Open een rapport en voeg een nieuwe lege pagina toe.
1. Open het pbix-voorbeeldbestand Retail Analysis in Power BI Desktop. 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. Voeg een nieuwe pagina toe door onderaan het tekenpapier het gele pluspictogram te selecteren.

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>Voeg een visualisatie toe die een beeld geeft van de jaaromzet vergeleken met vorig jaar.
1. Selecteer in de tabel **Sales** (Omzet): **This Year Sales** (Omzet dit jaar)  > **Value** (Waarde) en **Last Year Sales** (Omzet vorig jaar). In Power BI wordt een kolomdiagram gemaakt.  Dit is interessant en u wilt graag meer details weten. Hoe ziet de omzet eruit per maand?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. Sleep **FiscalMonth** uit de tijdstabel naar het **Axis**-gebied.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [Wijzig de visualisatie](power-bi-report-change-visualization-type.md) in een vlakdiagram.  Er zijn veel visualisatietypen waaruit u kunt kiezen. Bekijk [de beschrijvingen van de typen, tips voor aanbevolen procedures en zelfstudies](power-bi-visualization-types-for-reports-and-q-and-a.md) voor hulp bij het bepalen welk type u het beste kunt gebruiken. Selecteer in het venster Visualisaties het pictogram Vlakdiagram ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png).
4. Sorteer de visualisatie door de beletseltekens te selecteren en **Sorteren op FiscalMonth** te kiezen.
5. [Wijzig het formaat van de visualisatie](power-bi-visualization-move-and-resize.md) door de visualisatie te selecteren, en een van de cirkelomtrekken te pakken en te slepen. Maak deze groot genoeg om de schuifbalk te laten verdwijnen en klein genoeg zodat er voldoende ruimte is om nog een visualisatie toe te voegen.
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [Sla het rapport op](../service-report-save.md).

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>Een kaartvisualisatie toevoegen die de omzet per locatie weergeeft
1. Selecteer **Territory** (Territorium) in de tabel **Store** (Winkel). In Power BI wordt herkend dat Territory (Territorium) een locatie is en wordt een kaartvisualisatie gemaakt.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. Sleep **Total Stores** (Total aantal winkels) naar het gebied Size (Grootte).  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. Voeg een legenda toe.  Sleep **Chain** (Keten) naar het gebied Legend (Legenda) om de gegevens te bekijken per winkelnaam.  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>Volgende stappen
* Meer informatie over [Visualisaties in Power BI-rapporten](power-bi-report-visualizations.md).  
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

