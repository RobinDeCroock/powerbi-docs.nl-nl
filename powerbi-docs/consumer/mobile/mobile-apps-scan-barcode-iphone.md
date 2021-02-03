---
title: Streepjes code scannen vanuit de mobiele app Power BI
description: Scan streepjescodes in de echte wereld om rechtstreeks naar gefilterde BI-informatie in de mobiele Power BI-app te gaan.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 3d35df1c38a0a62325f88fa19ee7267a3b209647
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494496"
---
# <a name="scan-barcodes-from-the-mobile-app-to-get-filtered-data"></a>Streepjes codes scannen vanuit de mobiele app om gefilterde gegevens op te halen 
Scan streepjes codes in de hele wereld om direct naar gefilterde BI-informatie te gaan in de mobiele app van Power BI.

Van toepassing op:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPads](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android-telefoon](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android-tablet](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhones |iPads |Android-telefoons |Android-tablets |

Stel dat uw organisatie rapporten bevat met gegevens die zijn [gelabeld als streepjescode gegevens in Power bi Desktop](../../transform-model/desktop-mobile-barcodes.md). Wanneer u een product streepjescode scant met de scanner in de Power BI-app op uw apparaat, krijgt u een lijst met de rapporten met streepjescode gegevens. U kunt het gewenste rapport openen en automatisch gefilterd op de informatie die u nodig hebt.

![Schermopname van de scan van een productstreepjescode met de scanner boven de streepjescode van een gekleurd drankje.](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Hier volgen enkele voor beelden van twee scenario's waarin het scannen van streepjes codes nuttig is:
* Stel dat u de inventarisatie op een grote super markt controleert en u in de gangen die u nodig hebt om informatie over bepaalde producten te verkrijgen, zoals het aantal winkels in voor Raad, de afdelingen waarop de artikelen zijn opgeslagen, enzovoort. U kunt de Power BI scanner gewoon openen op uw mobiele apparaat en de streepjes code van een item scannen. U krijgt een lijst met rapporten met streepjescode gegevens. U kiest het relevante rapport en het rapport wordt geopend, gefilterd op de relevante gegevens.
* Stel dat de machines in een fabriek worden aangeduid met streepjes codes en dat de telemetrie van die machines wordt verwerkt en verzonden naar Power BI. Wanneer technici uitvallen op de status van de vloercontrole machine, kunnen ze eenvoudig de streepjes code van een machine scannen en een KPI-rapport ontvangen over de prestaties en status.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Een streepjescode scannen met de Power BI-scanner
1. Tik op de navigatiebalk op **Meer opties** (...) en tik vervolgens op **Scanner**.

    ![Schermopname van de optie Meer op het navigatiepaneel met de scannerselectie.](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

1. Als uw camera niet is ingeschakeld, moet u de Power BI-app toestemming geven voor het gebruik van de camera. U hoeft hier slechts eenmalig toestemming voor te geven. 
1. Wijs de scanner aan op een streepjes code van het item waarin u bent geïnteresseerd. U ziet een lijst met rapporten die streepjescode velden bevatten.
1. Zoek het rapport dat u zoekt en tik erop om het te openen op het apparaat, dat automatisch wordt gefilterd op basis van de streepjes code die u hebt gescand. Als het rapport de streepjes code niet bevat, krijgt u het bericht "kan rapport niet filteren". In dat geval kunt u terugkeren naar de lijst en een ander rapport proberen.
    
>[!NOTE]
>Als er slechts één rapport met een streepjescode veld is, krijgt u geen lijst met rapporten, maar wordt het rapport rechtstreeks geopend, gefilterd op basis van de streepjes code die u hebt gescand. Als het rapport de gescande streepjes code niet bevat, ontvangt u ook het bericht ' kan het rapport niet filteren '.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Op andere streepjescodes filteren in een rapport
Als u op uw apparaat een rapport bekijkt dat op een streepjescode is gefilterd, wilt u hetzelfde rapport mogelijk filteren op een andere streepjescode.

Tik op de actie balk van het rapport op **meer opties (...)** en zoek het streepjescode pictogram.

* Als het streepjescode pictogram is gevuld, ![Pictogram Gefilterd](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png)heeft, is het filter actief en wordt het rapport al gefilterd op streepjescode. 
* Als het pictogram duidelijk is ![Pictogram Niet gefilterd](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png)heeft, is het filter niet actief en wordt het rapport niet gefilterd op streepjescode. 

In beide gevallen kunt u op het pictogram tikken om een klein menu met een zwevende scanner te openen.

* Richt de scanner op het nieuwe item om het filter van het rapport te wijzigen in een andere streepjescodewaarde. 
* Selecteer **Streepjescodefilter wissen** om het ongefilterde rapport weer te geven.
* Selecteer **Filteren op recente streepjescodes** om het rapportfilter te wijzigen in een van de streepjescodes die u tijdens de huidige sessie hebt gescand.

## <a name="clear-a-barcode-filter"></a>Een streepjescode filter wissen
Filteren van streepjes code wissen in een gefilterd rapport:
1. Tik op de actie balk van het rapport op **meer opties (...)** en zoek het opgevulde ![ pictogram voor de gefilterde streepjescode scanner op ](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) dat aangeeft dat een filter actief is en tik erop om de scanner te openen.
1. Selecteer **Streepjescodefilter wissen** om het ongefilterde rapport weer te geven.

## <a name="limitations"></a>Beperkingen

* Het deel venster filters biedt geen indicatie van het filteren van streepjes codes. Als u wilt weten of een rapport momenteel wordt gefilterd op een streepjes code, kijkt u naar het pictogram in de menu opdracht van de streepjescode scanner:

    ![Pictogram Gefilterd](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) geeft aan dat het rapport momenteel wordt gefilterd op een streepjes code.
    
    ![Pictogram Niet gefilterd](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png) geeft aan dat het rapport momenteel niet wordt gefilterd op een streepjes code. 
* De mobiele apps ondersteunen het filteren van streepjes codes alleen voor rapporten die slechts één streepjescode kolom hebben in alle rapport gegevens tabellen. Als u een streepjes code scant voor een rapport met meer dan één streepjescode kolom, vindt er geen filters plaats.

## <a name="issues-with-scanning-a-barcode"></a>Problemen met het scannen van een streepjescode
Hier volgen enkele Issus die u kunt tegen komen wanneer u een streepjes code op een item scant.

* U krijgt een bericht dat het **rapport niet kan worden gefilterd, omdat deze streepjes code niet bestaat in de rapport gegevens**: Dit betekent dat de waarde van de streepjes code die u hebt gescand niet wordt weer gegeven in de datamodel van het rapport dat u wilt filteren. Dit kan bijvoorbeeld het geval zijn als het product waarvan u de streepjes code hebt gescand, niet in het rapport is opgenomen. U kunt een ander product scannen, een ander rapport kiezen (als er meerdere rapporten beschikbaar zijn) of het rapport ongefilterd weergeven.

* Er wordt een bericht weer gegeven met de melding **dat u geen rapporten hebt die kunnen worden gefilterd op streepjes codes**: Dit betekent dat u geen rapporten hebt waarvoor een streepjes code is ingeschakeld. U kunt alleen rapporten met de streepjescodescanner filteren die de kolom **Streepjescode** bevatten. Zorg ervoor dat u of de eigenaar van het rapport een kolom in Power BI Desktop voorziet van het label **Streepjescode**. Meer informatie over [het taggen van een streepjescodeveld in Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md).

* Filteren retourneert een lege status. Dit kan betekenen dat de waarde van de streepjes code die u hebt gescand, aanwezig is in uw model, maar dat alle of enkele visuele elementen in uw rapport deze waarde niet bevatten. In dit geval kunt u andere rapport pagina's bekijken of uw rapporten bewerken in Power BI Desktop die deze waarde bevatten 

## <a name="next-steps"></a>Volgende stappen
* [Een streepjescodeveld in Power BI Desktop taggen](../../transform-model/desktop-mobile-barcodes.md)
* [Dashboardtegels in Power BI](../end-user-tiles.md)
* [Dashboards in Power BI](../end-user-dashboards.md)