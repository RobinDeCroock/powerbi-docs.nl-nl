---
title: Analyseer populaire aandelen met Power BI
description: Analyseer populaire aandelen met Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 02/09/2021
LocalizationGroup: Connect to services
ms.openlocfilehash: 934451c06927237fd252d60102e2e5db73e31bc1
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/10/2021
ms.locfileid: "100082782"
---
# <a name="analyze-popular-stocks-with-power-bi"></a>Analyseer populaire aandelen met Power BI

De aandelen markt-app laat u meerdere Kpi's zien om uw analyse traject in Power BI te starten. U kunt het gebruiken voor het bijhouden van de uiteinden van offertes en wekelijkse, maandelijkse of jaarlijkse trends voor populaire aandelen en ETFs. De app toont u Power BI in actie, met het bijhouden van aandelen hoogten en laagste dagkoers, zwevende gemiddelden, sector gerichte distributie, Bollinger-stroken en zelfs prestatie vergelijkingen voor populaire aandelen gedurende een periode.

De app is voorzien van vier Dash boards:
* **ETF-dash board**: laat u trends sluiten voor vier grote indexen. 
* Voor **raden en ETFs-Vergelijking**: biedt genormaliseerde grafieken waarmee u eenvoudig aandelen en EFTs kunt vergelijken.
* **Analyse van voorraad prestaties**: Hiermee wordt een gedetailleerde analyse van de geselecteerde aandelen met visuele elementen voor het sluiten van trends, volume, OHLC en Bollinger banden ingeschakeld.
* **Sector-gerichte distributie**: Hiermee kunt u de aandelen prestaties op sector opdelen.

U kunt navigeren tussen de Dash boards met behulp van het navigatie deel venster of de pijlen vooruit en terug in de rechter bovenhoek van de pagina.

![Scherm opname van de app stocks.](media/service-connect-to-analyze-stocks/stocks-app.png)

## <a name="etf-dashboard"></a>ETF-dash board

Het ETF-dash board heeft visuele elementen waarin de sluitings trends voor vier primaire indices worden weer gegeven. 
* **NASDAQ**: de NASDAQ-samengestelde index meet de wijziging in meer dan 3.000 voor raden die worden verhandeld op de NASDAQ-uitwisseling.
* **S&p 500**: s&P 500 wordt beschouwd als de beste één meter van grote aandelen in de Verenigde Staten.
* **Dow Jones**: de Dow Jones toont u de markt groei van de leiders van de IT-branche, zoals micro soft. De sluitings trend van Dow Jones geeft aan op welke trend de voor raden van deze index zijn gesloten.
* **Russells 2000**: Russel 2000 is het meest voorkomende referentie punt voor beleggings fondsen. Het Visual Russells 2000-sluitende trend kan worden gebruikt om investerings richtlijnen te bieden over meer dan 2000 aandelen van een groot bereik.

Aan de bovenkant van het dash board ziet u de afsluiting van de huidige dag en de prijs wijziging ten opzichte van de vorige dagen voor de vier indexen die op de pagina worden weer gegeven.

De standaard weergave voor grafieken: helpt u te begrijpen hoe drastisch de trend in de loop van de tijd is gewijzigd. U kunt de knoppen tijd schaal linksboven in het dash board gebruiken om de trend voor een week, maand of jaar weer te geven. Beweeg de muis aanwijzer over de grafiek om het exacte gegevens punt van een bepaalde dag te verkrijgen.

![Scherm afbeelding van ETF-dashboard diagram weergave.](media/service-connect-to-analyze-stocks/etf-dashboard-graph.png)  

Op de x-as ziet u de tijds periode en op de y-as waarvan u de afsluit waarde ziet.

U kunt ook overschakelen naar een Candlestick-grafiek door te klikken op de wissel knop rechtsboven in het dash board. In de weer gave Candlestick ziet u de openstaande, hoog, laag en slot prijs voor elk gegevens punt. Beweeg de muis aanwijzer over de grafiek om het exacte gegevens punt van een bepaalde dag te verkrijgen.

![Scherm opname van ETF dash board Candlestick-weer gave.](media/service-connect-to-analyze-stocks/etf-dashboard-candlestick.png)

## <a name="stocks-and-etfs-comparison"></a>Vergelijking van voor raden en ETFs

In het dash board voor raden en ETFs vergelijkingen ziet u twee genormaliseerde grafieken waarmee de geselecteerde aandelen en ETFs eenvoudig kunnen worden vergeleken.

![Scherm afbeelding van het dash board voor aandelen vergelijking selecteren knop.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard.png)

Als u deze pagina wilt gebruiken, selecteert u eerst de aandelen die u wilt vergelijken. 
1. Klik op  de ![ scherm opname van het aandelen vergelijkings dashboard selecteren selecties opheffen.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select.png)
1. Op de pagina **aandelen selecteren** die wordt weer gegeven, klikt u op **wissen** om eventuele eerdere selecties te verwijderen en selecteert u vervolgens de aandelen die u wilt vergelijken  ![ scherm opname van het dash board voor aandelen vergelijking selecteren.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-clear.png)
1. Klik op **Toepassen**.

Nadat u de gewenste aandelen hebt geselecteerd, gebruikt u de pijl-omlaag om de betreffende aandelen te selecteren die u wilt vergelijken.

![Scherm afbeelding van het dash board voor aandelen vergelijking selectie vervolg keuzelijst selecteren.](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-dropdown.png)

## <a name="stock-performance-analysis"></a>Analyse van voorraad prestaties

 Dash board analyse van aandelen prestaties toont u belang rijke KPI'S over geselecteerde aandelen, zoals Close, close, open, hoog en laag van de vorige dag. Selecteer de vervolg keuzelijst om het aandeel te kiezen dat u wilt zien uit de aandelen die u hebt geselecteerd voor analyse. U ziet dat de waarde wordt gewijzigd nadat u op de gewenste voor Raad hebt geklikt.

![Scherm opname van analyse van voorraad prestaties selecteren.](media/service-connect-to-analyze-stocks/stocks-performance-select.png)
 
### <a name="closing-trend"></a>Trend sluiten

U kunt de sluitings trend voor het geselecteerde aandeel zien en u kunt overschakelen naar de weer gave maand of jaar door te klikken op de knoppen linksboven op de pagina. Als u een jaar weergave hebt, kunt u zien in welk deel van het jaar de waarde voor de winst of het verlies van de aandelen is opgetreden.

![Scherm opname van het sluiten van trends van geselecteerde aandelen](media/service-connect-to-analyze-stocks/stocks-performance-closing-trend.png)  

### <a name="volume"></a>Volume

U kunt het volume van de geselecteerde voor Raad bekijken door naar de volgende Visual te scrollen. U kunt op een tijds interval aanwijzen om de hoeveelheid voor Raad op dat deel van het jaar te bekijken.

![Scherm opname van het volume van de geselecteerde aandelen](media/service-connect-to-analyze-stocks/stocks-performance-volume.png)
 
### <a name="ohlc-chart"></a>OHLC grafiek

OHLC grafieken zijn zeer nuttig, omdat ze op hetzelfde moment vier grote data Points voor een bepaald aandeel weer geven. In het volgende visuele element op de pagina ziet u dus OHLC Visual, waarin u kunt zien dat u de geselecteerde aandelen opent, sluit, hoog en laag hebt geselecteerd. U kunt ook dieper in de gegevens zoeken door het zwevende gemiddelde te wijzigen. 

![Scherm opname van OHLC](media/service-connect-to-analyze-stocks/stocks-performance-ohlc.png)

### <a name="bollinger-band"></a>Bollinger-band

Bollinger-banden gebruiken complexe wiskunde om de trends weer te geven. U kunt een aantal van de KPI'S zien die zich in OHLC bevonden, samen met dat u een andere drie regels kunt zien. In de middelste lijn wordt het zwevende gemiddelde weer gegeven. De bovenste regel wordt met een bepaald aantal standaard afwijkingen omhoog geschoven en de onderste regel wordt met een standaard afwijking omlaag geschoven.

![Scherm opname van Bollinger-band.](media/service-connect-to-analyze-stocks/stocks-performance-bollinger.png) 

## <a name="sectorwise-distribution"></a>Sectorwise-distributie

Op de pagina sector-weerdistributie ziet u de verschillende aandelen en de markt waarvan deze deel uitmaken. Als u op een van de sectoren klikt, worden de bestanden uitgefilterd en worden de voor raden die horen bij de geselecteerde sector weer gegeven. 

![Scherm opname van de verdeling van de sector.](media/service-connect-to-analyze-stocks/sector-wise-distribution.png)
 
U kunt de muis aanwijzer over het aandeel bewegen om de belang rijke KPI te zien, zoals vorige sluiten, sluiten en het verschil. Het verschil helpt u inzicht te krijgen in het aandeel dat sinds gisteren is verworven of verloren is gegaan.

![Scherm opname van Details over de sector gerichte distributie.](media/service-connect-to-analyze-stocks/sector-wise-distribution-detail.png)

U kunt omlaag schuiven om alle voor raden in die categorie weer te geven.
 
Voor een overzicht van de distributie van de markt voor verschillende sectoren hebben we het visuele element ' sector gerichte distributie ' die van boven naar beneden de sectoren met het hoogste verschil in de eind prijs van de afgelopen dag wordt weer gegeven.

![Scherm afbeelding van de distributie van de markt voor verschillende sectoren](media/service-connect-to-analyze-stocks/stocks-comparison-based-on-sector.png)


## <a name="next-steps"></a>Volgende stappen

* [Wat zijn Power BI-sjabloon apps?](service-template-apps-overview.md)
* [Een sjabloon-app maken in Power BI](service-template-apps-create.md)
* [Sjabloon-apps in uw organisatie installeren en distribueren](service-template-apps-install-distribute.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
