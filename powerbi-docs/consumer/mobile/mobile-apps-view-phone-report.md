---
title: Voor uw telefoon geoptimaliseerde Power BI-rapporten weergeven
description: Lees over de interactie met rapportpagina's die zijn geoptimaliseerd voor weergave in de Power BI-apps voor uw telefoon.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: mshenhav
ms.openlocfilehash: 79ca47f83bb39ab9d6df141b5a26dcb54e00c72c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101024"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Voor uw telefoon geoptimaliseerde Power BI-rapporten weergeven

Van toepassing op:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android-telefoon](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhones |Android-telefoons |

Wanneer u een Power BI-rapport op uw telefoon weergeeft, controleert Power BI als het rapport is geoptimaliseerd voor telefoons. Als dat zo is, wordt het geoptimaliseerde rapport door Power BI automatisch in staande weergave geopend.

![Rapport in de staande modus](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Als er geen voor de telefoon geoptimaliseerd rapport bestaat, wordt het rapport geopend in de niet-geoptimaliseerde liggende weergave. Een voor de telefoon geoptimaliseerd rapport wordt ook in de niet-geoptimaliseerde weergave met de indeling van het oorspronkelijke rapport weergegeven als u uw telefoon kantelt. Als slechts enkele pagina’s zijn geoptimaliseerd, ziet u een bericht in de portretweergave met de mededeling dat het rapport in de liggende modus beschikbaar is.

![Niet-geoptimaliseerde rapportpagina](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Alle andere functies van Power BI-rapporten werken nog steeds in voor de telefoon geoptimaliseerde rapporten. Meer informatie over wat u kunt doen in:

* [Rapporten op iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Rapporten op Android-telefoons](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>De rapportpagina filteren op een telefoon
Als u een voor de telefoon geoptimaliseerd rapport hebt waarvoor filters zijn gedefinieerd, kunt u deze filters gebruiken wanneer u het rapport op een telefoon bekijkt. Het rapport wordt geopend op uw telefoon, gefilterd op de waarden worden gefilterd in het rapport op het web. U ziet een bericht waarin staat dat er op de pagina filters actief zijn. U kunt de filters op uw telefoon wijzigen.

1. Tik op het filterpictogram ![Filterpictogram op telefoon](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) onder aan de pagina. 
2. Gebruik basis- of geavanceerde filters om de resultaten waarin u geïnteresseerd bent te bekijken.
   
    ![Geavanceerde filter voor Power BI-rapporten op de telefoon](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Visuele elementen kruislings markeren
Kruislings markeren van visuele elementen in de staande werkt weergave u de manier waarop die dit gebeurt in Power BI-service en op telefoons in de liggende weergave: Wanneer u gegevens in een visual selecteert, worden de gerelateerde gegevens in de andere visuals op die pagina's uitgelicht.

Meer informatie over [filteren en markeren in Power BI](../../power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Visuele elementen selecteren
Wanneer u een visueel element selecteert in een rapport op de telefoon, wordt dit visuele element gemarkeerd en wordt erop gefocust. Canvasgebaren werken niet meer.

Als het visuele element is geselecteerd, kunt u verschillende dingen doen, zoals schuiven binnen het visuele element. Om de selectie van een visueel element ongedaan te maken, tikt u op een willekeurige plek buiten het visuele element.

## <a name="open-visuals-in-focus-mode"></a>Visuele elementen openen in de focusmodus
Telefoonrapporten bieden ook een focusmodus: U krijgt een grotere weergave van één visual en eenvoudig kunt verkennen.

* Tik in een rapport op de telefoon op het beletselteken ( **...** ) in de rechterbovenhoek van een visueel element > **Uitvouwen voor focusmodus**.
  
    ![Uitvouwen voor focusmodus](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

Wat u doet in de focusmodus wordt doorgevoerd in naar het rapportcanvas en omgekeerd. Bijvoorbeeld, als u een waarde in een visueel element markeert en vervolgens naar het hele rapport terugkeren, wordt het rapport gefilterd op de waarde die u in het visuele element hebt gemarkeerd.

Sommige handelingen zijn alleen mogelijk in de focusmodus vanwege beperkingen door het scherm:

* **Inzoomen** op de weergegeven gegevens in een visueel element. Lees hieronder meer over het [in- en uitzoomen](mobile-apps-view-phone-report.md#drill-down-in-a-visual) in een rapport op de telefoon.
* De waarden in het visuele element **sorteren**.
* **Herstellen**: Hiermee wist u stappen die u hebt gemaakt op een visueel element en keert u terug naar de definitie die is ingesteld bij het maken van het rapport.
  
    Als u alle stappen op een visueel element ongedaan wilt maken, tikt u op het beletselteken ( **...** ) > **Herstellen**.
  
    ![Ongedaan maken](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Herstellen is beschikbaar op het niveau van het rapport verkennen op alle visuele elementen, uit te schakelen of op het niveau van de visual, stappen op het geselecteerde visuele element te wissen.   

## <a name="drill-down-in-a-visual"></a>Inzoomen op een visueel element
Als hiërarchieniveaus zijn gedefinieerd in een visueel element, u kunt inzoomen op de gedetailleerde informatie die wordt weergegeven in een visueel element. Vervolgens kunt u weer uitzoomen. U kunt [inzoomen op een visueel element toevoegen](../end-user-drill.md) in de Power BI-service of in Power BI Desktop.

Er zijn enkele typen van inzoomen:

### <a name="drill-down-on-a-value"></a>Inzoomen op een waarde
1. Tik lang (tikken en vasthouden) op een gegevenspunt in een visueel element.
2. Knopinfo wordt weergegeven, en als hiërarchie is gedefinieerd, klikt u vervolgens de voettekst van de knopinfo wordt weergegeven in inzoomen naar beneden en pijl-omhoog.
3. Tik op de pijl-omlaag voor inzoomen

    ![Tik op inzoomen](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Tik op de pijl-omhoog voor uitzoomen.

### <a name="drill-to-next-level"></a>Zoomen naar het volgende niveau
1. Tik in een rapport op de telefoon op het beletselteken ( **...** ) in de rechterbovenhoek > **Uitvouwen voor focusmodus**.
   
    ![Uitvouwen voor focusmodus](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    In dit voorbeeld geven de balken de waarden voor de staten weer.
2. Tik op het verkenpictogram ![Verkenpictogram](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) in de linkerbenedenhoek van het scherm.
   
    ![Verkenmodus](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Tik op **Volgende niveau weergeven** of **Uitbreiden naar het volgende niveau**.
   
    ![Uitbreiden naar het volgende niveau](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Nu geven de balken de waarden voor steden weer.
   
    ![Uitgevouwen niveaus](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Als u op de pijl in de linkerbovenhoek tikt, gaat u terug naar het rapport op de telefoon en blijven de waarden naar het lagere niveau uitgevouwen.
   
    ![Nog steeds uitgevouwen naar het lagere niveau](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Om terug te gaan naar het oorspronkelijke niveau, tikt u weer op het beletselteken ( **...** ) > **Herstellen**.
   
    ![Ongedaan maken](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>In detail analyseren van een waarde
Waarden in één rapportpagina drill-through verbindt met andere rapportpagina's. Wanneer u door middel van een gegevenspunt naar een andere rapportpagina, de waarden van de punt worden gebruikt voor het filteren van de drilled via de pagina of het is in de context van de geselecteerde gegevens.
Auteurs van rapporten kunnen [definiëren drill-through](https://docs.microsoft.com/power-bi/desktop-drillthrough) wanneer ze het rapport maken.

1. Tik lang (tikken en vasthouden) op een gegevenspunt in een visueel element.
2. Knopinfo wordt weergegeven, en als drill-through is gedefinieerd, klikt u vervolgens de voettekst van de knopinfo wordt weergegeven in drill-through pijl.
3. Tik op de pijl voor analyse

    ![Tik op drill-through](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Kies welke op de rapportpagina om een Drillthrough

    ![Rapportpagina kiezen](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Gebruik de knop terug op de kop van de app om terug te gaan naar de pagina die u vanuit gestart.


## <a name="next-steps"></a>Volgende stappen
* [Rapporten maken die zijn geoptimaliseerd voor de mobiele Power BI-apps](../../desktop-create-phone-report.md)
* [Een telefoonweergave van een dashboard maken in Power BI](../../service-create-dashboard-mobile-phone-view.md)
* [Responsieve visuele elementen maken die zijn geoptimaliseerd voor elke grootte](../../visuals/desktop-create-responsive-visuals.md)
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

