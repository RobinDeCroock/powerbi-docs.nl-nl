---
title: Een responsieve slicer maken waarvan u de grootte kunt wijzigen in Power BI
description: Meer informatie over het maken van een voor uw rapport op maat gemaakte responsieve slicer waarvan u de grootte kunt wijzigen
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: f4e70bdcd877c29063a73cc24111d4dc04aa39b9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280973"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>Een responsieve slicer maken waarvan u de grootte kunt wijzigen in Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Responsieve slicers worden in grootte aangepast zodat ze overal op het rapport passen. U kunt de grootte en vorm van responsieve slicers aanpassen, van horizontaal naar vierkant naar verticaal. De waarden in de slicer worden hierop automatisch gerangschikt. In Power BI Desktop kunt in de Power BI-service horizontale slicers en slicers voor datum/bereik responsief maken. Slicers voor datum/bereik hebben tevens verbeterde aanraakgebieden, zodat u ze eenvoudiger razendsnel kunt wijzigen. U kunt responsieve slicers zo klein of groot maken als u zelf wilt. Het formaat wordt ook automatisch aangepast zodat ze goed op rapporten in de Power BI-service en in de mobiele Power BI-apps passen. 

![Responsieve slicers kunnen verschillende vormen hebben](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>Een slicer maken

De eerste stap bij het maken van een dynamische slicer is het maken van een eenvoudige slicer. 

1. Selecteer het pictogram **Slicer**![Slicerpictogram](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png) in het deelvenster **Visualisaties**.
2. Sleep het veld dat u wilt filteren naar **Veld**.

    ![Een veld aan de slicer toevoegen](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>Naar een horizontale slicer converteren

1. Selecteer de slicer en selecteer vervolgens in het deelvenster **Visualisaties** het tabblad **Indeling**.
2. Vouw de sectie **Algemeen** uit en selecteer vervolgens voor **Afdrukstand** de optie **Horizontaal**.

    ![De slicer instellen op horizontaal](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  Waarschijnlijk wilt u de weergave breder maken om weer waarden weer te geven.

     ![De slicer breder maken](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>De slicer responsief maken en hiermee experimenteren

Deze stap is eenvoudig. 

1. Stel bij **Afdrukstand** in de sectie **Algemeen** van het tabblad **Indeling** de optie **Responsief** in op **Aan**.  

    ![De slicer is nu responsief](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. Nu kunt u ermee experimenteren. Versleep de hoeken om de slicer korter, hoger, breder of smaller te maken. Als u de slicer klein genoeg maakt, wordt alleen nog een filterpictogram weergegeven.

    ![Responsieve slicer die zo klein is dat het een filterpictogram wordt](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>Toevoegen aan de rapportindeling voor telefoons

In Power BI Desktop kunt u voor elke pagina van een rapport een telefoonindeling maken. Als een pagina een telefoonindeling heeft, wordt de pagina op een mobiele telefoon in afdrukstand Staand weergegeven. Anders moet u deze weergeven in de afdrukstand Liggend. 

1. Selecteer in het menu **Beeld** de optie **Telefoonindeling**.

     ![Pictogram Telefoonindeling, menu Beeld](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. Sleep alle visuals die u in het telefoonrapport wilt weergeven in het raster. Wanneer u de responsieve slicer sleept, stelt u dit op de gewenste grootte in; in dit geval slechts een filterpictogram.

    ![De slicer toevoegen aan de indeling van het telefoonrapport](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

Meer informatie over het maken van [rapporten die zijn geoptimaliseerd voor de mobiele Power BI-apps](desktop-create-phone-report.md).

## <a name="make-a-time-or-range-slicer-responsive"></a>Een slicer voor tijd of bereik responsief maken

U kunt dezelfde stappen volgen om een slicer voor tijd of bereik responsief te maken. Nadat u **Responsief** hebt ingesteld op **Aan**, ziet u een aantal dingen:

- In visuals wordt de volgorde van de invoervakken geoptimaliseerd op basis van de grootte die is toegestaan op het canvas. 
- De weergave van gegevenselementen wordt geoptimaliseerd om de slicer zo bruikbaar mogelijk te maken op basis van de grootte die is toegestaan op het canvas. 
- Door de nieuwe ronde handvatten op de schuifregelaars zijn de aanraakinteracties geoptimaliseerd. 
- Wanneer een visual te klein wordt om nog nuttig zijn, wordt het een pictogram weergegeven dat de betreffende visual vertegenwoordigt. Als u hiermee wilt werken, dubbeltikt u hierop om de visual in de focusmodus te openen. Dit bespaart kostbare ruimte op de rapportpagina zonder verlies van de functionaliteit.

## <a name="next-steps"></a>Volgende stappen

- [Slicers in de Power BI-service](../visuals/power-bi-visualization-slicers.md)
- Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).