---
title: Gegevens en records weergeven in visuele elementen in Power BI Desktop
description: De functies Gegevens weergeven en Records weergeven in Power BI Desktop gebruiken om in te zoomen op details
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 6e425f146228d0139b9eec914a44ed5dc732fe98
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514772"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Gegevens weergeven en Records weergeven gebruiken in Power BI Desktop
In **Power BI Desktop** kunt u inzoomen op de gegevens van een visualisatie en ziet u tekstweergaven van de onderliggende gegevens of de afzonderlijke gegevensrecords voor de geselecteerde visual. Deze functies worden soms aangeduid met *doorklikken*, *drillthrough* of *drillthrough naar details*.

U gebruikt **Gegevens bekijken** om een tekstversie te bekijken van de waarden die worden gebruikt door de geselecteerde visualisatie, of u gebruikt **Records bekijken** om alle gegevens te bekijken voor één geselecteerde record of gegevenspunt. 

![Gegevens bekijken en Records bekijken](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**Gegevens bekijken** en **Records bekijken** ondersteunen alleen de volgende visualisatietypen:
>  - Staafdiagram
>  - Kolomdiagram
>  - Ringdiagram
>  - Choropletenkaart
>  - Trechterdiagram
>  - Kaart
>  - Cirkeldiagram
>  - Treemap

## <a name="use-see-data-in-power-bi-desktop"></a>Gegevens bekijken gebruiken in Power BI Desktop

Met **Gegevens bekijken** ziet u de onderliggende gegevens van een visualisatie. **Gegevens bekijken** bevindt zich op het tabblad **Gegevens/analyseren** in de sectie **Visual Tools** van het lint wanneer een visualisatie is geselecteerd.

![Gegevens bekijken in het lint](media/desktop-see-data-see-records/see-data1.png)

U kunt de gegevens ook bekijken door met de rechtermuisknop op een visualisatie te klikken en vervolgens **Gegevens weergeven** te selecteren vanuit het menu dat verschijnt, of door het beletselteken (...) voor **Meer opties** in de rechterbovenhoek van een visualisatie te selecteren en vervolgens **Gegevens weergeven** te selecteren.

![Met rechtermuisknop klikken op Gegevens weergeven](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![Meer opties van Gegevens weergeven](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> Houd de muisaanwijzer boven een gegevenspunt in de visual, zodat het snelmenu zichtbaar wordt.

Wanneer u **Gegevens bekijken** of **Gegevens weergeven** selecteert, worden op het Power BI Desktop-canvas zowel de visual element als de tekstweergave van de gegevens weergegeven. De visual wordt in de *horizontale weergave* weergegeven op het bovenste gedeelte van het canvas; de gegevens worden weergegeven op de onderste helft. 

![horizontale weergave](media/desktop-see-data-see-records/see-data4a.png)

U kunt schakelen tussen de horizontale weergave en een *verticale weergave* door het pictogram in de rechterbovenhoek van het canvas te selecteren.

![verticale weergave in- of uitschakelen](media/desktop-see-data-see-records/see-data4.png)

Als u terug wilt gaan naar het rapport, selecteert u **< Terug naar rapport** in de linkerbovenhoek van het canvas.

![Terug naar rapport](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Records bekijken gebruiken in Power BI Desktop

U kunt zich ook focussen op één gegevensrecord in een visualisatie en inzoomen op de achterliggende gegevens. Als u **Records bekijken** wilt gebruiken, selecteert u een visualisatie, selecteert u **Records bekijken** op het tabblad **Gegevens/analyseren** in de sectie **Visual Tools** van het lint en selecteert u vervolgens een gegevenspunt of rij van de visualisatie. 

![Records bekijken in het lint](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> Als de knop **Records bekijken** in het lint is uitgeschakeld en niet beschikbaar is, betekent dit dat de geselecteerde visualisatie geen ondersteuning biedt voor **Records bekijken**.

U kunt ook met de rechtermuisknop op een gegevenselement klikken en **Records bekijken** kiezen in het menu dat verschijnt.

![Records bekijken door met de rechtermuisknop te klikken](media/desktop-see-data-see-records/see-record2.png)

Wanneer u **Records bekijken** voor een gegevenselement selecteert, worden op het Power BI Desktop-canvas alle gegevens weergegeven die zijn gekoppeld aan het geselecteerde element. 

![](media/desktop-see-data-see-records/see-record3.png)

Als u terug wilt gaan naar het rapport, selecteert u **< Terug naar rapport** in de linkerbovenhoek van het canvas.

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>**Records bekijken** heeft de volgende beperkingen:
> - U kunt de gegevens in de weergave **Records bekijken** niet wijzigen en in het rapport opslaan.
> - U kunt **Records bekijken** niet gebruiken als voor de visual een berekende meting wordt gebruikt.
> - U kunt **Records bekijken** niet gebruiken als u bent verbonden met een live, multidimensionaal model (MD).

## <a name="next-steps"></a>Volgende stappen
**Power BI Desktop** bevat diverse functies voor gegevensbeheer en het opmaken van rapporten. Bekijk de volgende bronnen voor enkele voorbeelden:

* [Use grouping and binning in Power BI Desktop](desktop-grouping-and-binning.md) (Groeperen en binning in Power BI Desktop gebruiken)
* [Use gridlines, snap-to-grid, z-order, alignment and distribution in Power BI Desktop reports](desktop-gridlines-snap-to-grid.md) (Rasterlijnen, Uitlijnen op raster, Z-volgorde, Uitlijnen en Verdelen gebruiken in Power BI Desktop-rapporten)

