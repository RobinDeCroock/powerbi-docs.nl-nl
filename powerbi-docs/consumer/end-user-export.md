---
title: Gegevens uit een Power BI-visualisatie exporteren
description: Exporteer gegevens uit een rapportvisual en dashboardvisual en bekijk ze in Excel.
author: mihart
manager: kvivek
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/11/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 80033cafbe66303a1d6f55bba61f7d19449dc45b
ms.sourcegitcommit: f34acbf9fb1ab568fd89773aaf412a847f88dd34
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589526"
---
# <a name="export-data-from-a-visual"></a>Gegevens uit een visualisatie exporteren

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Als u de gegevens wilt zien die worden gebruikt om een visual te maken, [kunt u die gegevens weergeven in Power BI](end-user-show-data.md) of exporteren naar Excel. De optie om gegevens te exporteren vereist een bepaald type of licentie en bewerkingsmachtigingen voor de inhoud. Als u niets kunt exporteren, neemt u contact op met uw Power BI-beheerder. 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Vanuit een visual in een Power BI-dashboard

1. Begin in een Power BI-dashboard. Hier gebruiken we het dashboard uit de voorbeeldapp ***Verkoop en marketing***. U [downloadt deze app van AppSource.com](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282).

    ![App-dashboard](media/end-user-export/power-bi-dashboards.png)

2. Beweeg met de muis over een visual om het beletselteken (...) weer te geven en klik erop om het actiemenu weer te geven.

    ![Menu dat wordt weergegeven wanneer u het beletselteken selecteert](media/end-user-export/power-bi-action-menu.png)

3. Selecteer **Exporteren naar Excel**.

4. Wat er nu gebeurt, hangt af van de browser die u gebruikt. U wordt mogelijk gevraagd om het bestand op te slaan, of u ziet mogelijk onderaan de browser een link naar het geëxporteerde bestand. 

    ![Chrome-browser die link naar geëxporteerd bestand weergeeft](media/end-user-export/power-bi-dashboard-exports.png)

5. Open het bestand in Excel.  

    ![Totaalaantal eenheden jaar tot nu in Excel](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>Vanuit een visual in een rapport
U kunt gegevens exporteren uit een visual in een rapport als .csv of .xlsx (Excel). 

1. Selecteer een tegel in een dashboard om het onderliggende rapport te openen.  In dit voorbeeld selecteren we dezelfde visual als hierboven, *Totaalaantal eenheden jaar tot nu, variabel percentage*. 

    ![Dashboardtegel markeren](media/end-user-export/power-bi-export-reports.png)

    Aangezien deze tegel is gemaakt vanuit het voorbeeldrapport *Verkoop en marketing*, wordt dat rapport geopend. De pagina die de visual van de geselecteerde tegel bevat, wordt ook geopend. 

2. Selecteer de tegel in het rapport. Bekijk het venster **Filters** aan de rechterzijde. Er zijn filters toegepast op de visual. Voor meer informatie over filters raadpleegt u [Filters gebruiken in een rapport](end-user-report-filter.md).

    ![Filtervenster geselecteerd](media/end-user-export/power-bi-export-filter.png)


3. Selecteer het beletselteken in de rechterbovenhoek van de visualisatie. Kies **Gegevens exporteren**.

    ![In vervolgkeuzelijst geselecteerde gegevens exporteren](media/end-user-export/power-bi-export-report.png)

4. U ziet opties om Samengevatte gegevens of Onderliggende gegevens te exporteren. Als u gebruikmaakt van de voorbeeldapp *Verkoop en marketing*, wordt **Onderliggende gegevens** uitgeschakeld. U kunt echter wel rapporten tegenkomen waarbij beide opties zijn ingeschakeld. Dit is een voorbeeld van het verschil.

    **Samengevatte gegevens**: selecteer deze optie als u gegevens wilt exporteren voor wat u ziet in de visual.  Dit type export geeft alleen de gegevens weer die werden gebruikt om de visual te maken. Als er filters zijn toegepast op de visual, worden de gegevens die u exporteert ook gefilterd. Voor deze visual bevat uw export bijvoorbeeld alleen gegevens voor 2014 en de centrale regio en alleen gegevens voor vier van de fabrikanten: VanArsdel, Natura, Aliqui en Pirum.
  

    **Onderliggende gegevens**: selecteer deze optie als u gegevens wilt exporteren voor wat u in de visual ziet **en** aanvullende gegevens uit de onderliggende gegevensset.  Dit zijn mogelijk gegevens die zijn opgenomen in de gegevensset, maar die niet worden gebruikt in de visual. 

    ![Menu waar u onderliggend of samengevat kiest](media/end-user-export/power-bi-export-option.png)

5. Wat er nu gebeurt, hangt af van de browser die u gebruikt. U wordt mogelijk gevraagd om het bestand op te slaan, of u ziet mogelijk onderaan de browser een link naar het geëxporteerde bestand. 

    ![Geëxporteerd bestand wordt weergegeven in de Microsoft Edge-browser](media/end-user-export/power-bi-export-edge-browser.png)


6. Open het bestand in Excel. Vergelijk de hoeveelheid geëxporteerde gegevens met de gegevens die u hebt geëxporteerd uit dezelfde visual op het dashboard. Het verschil is dat deze export ook **Onderliggende gegevens** omvat. 

    ![Excel-voorbeeld](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>Volgende stappen

[De gegevens weergeven die worden gebruikt om een visual te maken](end-user-show-data.md)