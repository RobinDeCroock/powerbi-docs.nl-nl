---
title: Choropletenkaarten in Power BI
description: Documentatie over het maken van choropletenkaarten in Power BI
author: mihart
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/19/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 9c35e97fba55230277f9f144a5155071656b6add
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870970"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Choropletenkaarten in Power BI

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

In een choropletenkaart worden arcering, tinten of patronen gebruikt om aan te geven hoe een waarde in verhouding verschilt voor een geografisch gebied of regio.  U kunt zo snel deze relatieve verschillen laten zien met behulp van arcering die varieert van licht (minder frequent/lager) tot donker (meer-frequent/hoger).    

![Kaart van VS](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>Welke gegevens worden naar Bing verzonden?
Power BI is geïntegreerd met Bing om standaardkaartcoördinaten te bieden (een proces dat geocodering wordt genoemd). Wanneer u een visualisatie van een kaart maakt in de Power BI-service of Power BI Desktop, worden de gegevens in de buckets **Locatie**, **Breedtegraad** en **Lengtegraad** naar Bing verzonden. Deze buckets worden trouwens gebruikt om de visualisatie te maken.

U of uw beheerder moet mogelijk uw firewall bijwerken om toegang te krijgen tot de URL’s die Bing gebruikt voor geocodering.  Deze URL's zijn:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Meer informatie over de gegevens die naar Bing worden verzonden en tips voor het verbeteren van de geocodering leest u in [Tips and tricks for map visualizations](power-bi-map-tips-and-tricks.md) (Tips en trucs voor kaartvisualisaties).

## <a name="when-to-use-a-filled-map"></a>Wanneer gebruikt u een choropletenkaart
In de volgende gevallen zijn choropletenkaarten een goede keuze:

* om kwantitatieve gegevens op een kaart weer te geven.
* om ruimtelijke patronen en relaties weer te geven.
* wanneer uw gegevens zijn gestandaardiseerd.
* als u werkt met sociaaleconomische gegevens.
* als gedefinieerde regio's belangrijk zijn.
* om een overzicht te krijgen van de verdeling over verschillende geografische locaties.

### <a name="prerequisites"></a>Vereisten
In deze zelfstudie wordt gebruikgemaakt van het [PBIX-bestand met het voorbeeld van een retailanalyse](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).
1. Selecteer linksboven in de menubalk **Bestand** > **Openen**.
   
2. Ga naar uw kopie van het **PBIX-bestand met het voorbeeld van een retailanalyse**

1. Open het **PBIX-bestand met het voorbeeld van een retailanalyse** in de rapportweergave ![Schermopname van het pictogram voor de rapportweergave.](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. Selecteren ![Schermopname van het gele tabblad.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) om een nieuwe pagina toe te voegen.


## <a name="create-a-basic-filled-map"></a>Een eenvoudige choropletenkaart maken
In deze video maakt Kim een eenvoudige kaart en zet deze om in een choropletenkaart.
   > [!NOTE]
   > In deze video wordt gebruikgemaakt van een eerdere versie van Power BI Desktop.
   > 
   > 

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="create-a-filled-map"></a>Een gevulde kaart maken
1. Selecteer in het deelvenster Velden het veld **Geo** \> **State**.    

   ![geel vinkje naast de status](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Converteer de kaart](power-bi-report-change-visualization-type.md) naar een choropletenkaart. U ziet dat **State** nu ook wordt vermeld onder **Locatie**. Bing Kaarten gebruikt het veld onder **Locatie** om de kaart te maken.  Het deelvenster Locatie kan een aantal geldige locaties bevatten: landen, staten, provincies, steden, postcodes, enzovoort. Bing Kaarten kan choropletenkaarten maken voor locaties over de hele wereld. Hiervoor is wel een geldige vermelding in het deelvenster Locatie vereist.  

   ![sjablonen met het pictogram voor choropletenkaart gemarkeerd](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filter de kaart om alleen het vasteland van de Verenigde Staten weer te geven.

   a.  Zoek links van het deelvenster Visualisaties naar het deelvenster **Filters**. Vouw het uit als het is geminimaliseerd.

   b.  Beweeg de muisaanwijzer over **State** en selecteer de dubbele punthaak om uit te vouwen.  
   ![Filters voor visueel niveau die State(All) weergeven](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Zet een vinkje naast **Alles selecteren** en verwijder het vinkje bij **AK**.

   ![Status van de vervolgkeuzelijst waarbij Alles en AK niet zijn geselecteerd](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Selecteer het pictogram met de verfroller om het opmaakvenster te openen en kies **Gegevenskleuren**.

    ![Opmaakvenster met de optie Gegevenskleuren](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-color.png)

5. Selecteer de drie verticale puntjes en kies **Voorwaardelijke opmaak**.

    ![De knop Voorwaardelijke opmaak van gegevenskleuren](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional-formatting.png)

6. Gebruik het venster **Standaardkleur - Gegevenskleuren** om te bepalen op welke manier uw choropletenkaart wordt gearceerd. U hebt onder andere de optie om te bepalen op welk veld de arcering moet worden gebaseerd en hoe de arcering moet worden toegepast. In dit voorbeeld wordt het veld **SalesFact** > **Sentiment** gebruikt en wordt de laagste waarde voor gevoel ingesteld in het rood en de hoogste waarde in het groen. Waarden die tussen het maximum en het minimum vallen, zijn tinten rood en groen. In de afbeelding onderaan het venster ziet u het kleurenbereik dat wordt gebruikt. 

    ![Deelvenster met standaardkleuren, Gevoel is geselecteerd](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment.png)

7. De choropletenkaart is groen en rood gearceerd, met rood voor lagere gevoelscijfers en groen voor een hoger, positiever gevoel.  Als u meer details wilt weergeven, sleept u een veld naar de knopinfobron.  In dit voorbeeld is **Gevoelshiaat** toegevoegd en is de staat Idaho (ID) gemarkeerd. U ziet dat de gevoelshiaat laag is, namelijk 6.
   ![choropletenkaart met knopinfo over Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map-idaho.png)

10. [Sla het rapport op](../service-report-save.md).

In Power BI hebt u meer dan voldoende controle over de weergave van uw choropletenkaart. Experimenteer gerust met deze besturingselementen voor gegevenskleuren totdat u de gewenste opmaak hebt gevonden. 

## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren
Zie [Een filter aan een rapport toevoegen](../power-bi-report-add-filter.md) voor meer informatie over het gebruik van het deelvenster Filters.

Als u een locatie op een choropletenkaart markeert, worden de andere visualisaties op de rapportpagina ook gefilterd en omgekeerd.

1. Als u wilt meelezen, slaat u dit rapport eerst op door **Bestand > Opslaan** te selecteren. 

2. Kopieer de choropletenkaart met behulp van Ctrl-C.

3. Selecteer onderaan het rapportcanvas het tabblad **Gevoel** om de rapportpagina Gevoel te openen.

    ![Tabblad Gevoel geselecteerd](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Verplaats en wijzig de grootte van de visualisaties op de pagina om ruimte maken, en druk op Ctrl+V om de choropletenkaart uit het vorige rapport te plakken. (Zie de volgende afbeeldingen.)

   ![Choropletenkaart toegevoegd aan pagina Gevoel](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Selecteer een staat op de choropletenkaart.  Hiermee worden de andere visualisaties op de pagina kruislings gemarkeerd en kruislings gefilterd. Als u bijvoorbeeld **Texas** selecteert, ziet u dat de gevoelswaarde 75 is en dat Texas zich in het Central District #23 bevindt.   
   ![Texas geselecteerd](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Selecteer een gegevenspunt in het lijndiagram VanArsdel - Gevoel per maand. Hierdoor wordt de choropletenkaart gefilterd op gevoel voor VanArsdel en niet hun concurrentie.  
   ![nieuwe arcering](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
Kaartgegevens kunnen dubbelzinnig zijn.  Er is bijvoorbeeld een Parijs in Frankrijk, maar ook in Texas. Uw geografische gegevens worden waarschijnlijk opgeslagen in afzonderlijke kolommen (een kolom voor plaatsnamen, een kolom voor namen van staten of provincies, enzovoort), zodat Bing onmogelijk kan vaststellen of het om de Franse versie of Texaanse versie van Parijs gaat. Als uw gegevensset al de breedtegraad- en lengtegraadgegevens bevat, zijn er in Power BI speciale velden beschikbaar om de kaartgegevens uniek te maken. Sleep hiervoor het veld met de breedtegraadgegevens naar het gebied Visualisaties \> Breedtegraad.  Doe hetzelfde voor de lengtegraadgegevens.    

![Deelvensters Visualisaties en Velden](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Als u gemachtigd bent om de gegevensset te bewerken in Power BI Desktop, bekijkt u deze video voor het oplossen van problemen met dubbelzinnigheid in kaarten.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Als u geen toegang hebt tot gegevens voor breedtegraad en lengtegraad maar wel bewerkingstoegang tot de gegevensset hebt, [volgt u deze instructies voor het bijwerken van uw gegevensset](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Zie [Tips and tricks for map visualizations](../power-bi-map-tips-and-tricks.md) (Tips en trucs voor kaartvisualisaties) voor meer hulp bij kaartvisualisaties.

## <a name="next-steps"></a>Volgende stappen

[Shape-kaart](desktop-shape-map.md)

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)