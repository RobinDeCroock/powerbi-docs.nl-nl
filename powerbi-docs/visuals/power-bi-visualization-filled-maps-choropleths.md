---
title: Choropletenkaarten in Power BI
description: Documentatie over het maken van choropletenkaarten in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 2fa8fa5248ee1e4330804205b2cedb64021b1913
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839755"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Choropletenkaarten in Power BI
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
- Power BI-service of Power BI Desktop
- Voorbeeld van verkoop en marketing

In deze zelfstudie wordt de Power BI-service gebruikt, niet Power BI Desktop.

## <a name="create-a-basic-filled-map"></a>Een eenvoudige choropletenkaart maken
In deze video maakt Kim een eenvoudige kaart en zet deze om in een choropletenkaart.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>Gegevens ophalen en een nieuwe lege pagina toevoegen aan het rapport
1. Als u zelf een choropletenkaart wilt maken, [downloadt u het voorbeeld van verkoop en marketing](../sample-datasets.md) door u aan te melden bij Power BI en **Gegevens ophalen \> Voorbeelden \> Voorbeeld van verkoop en marketing \> Verbinden** te selecteren. Of download de app **Power BI Sales and Marketing** op appsource.com. 

2. Open het rapport Verkoop en marketing.

   ![Het rapport Verkoop en marketing wordt geopend](media/power-bi-visualization-filled-maps-choropleths/power-bi-report-canvas.png)
3. Het rapport wordt geopend in Power BI. Selecteer **Rapport bewerken** om het rapport in de [Bewerkingsweergave](../service-interact-with-a-report-in-editing-view.md) te openen.

4. Voeg een nieuwe pagina toe door onder aan het rapportcanvas het gele plusteken te selecteren.

    ![Tabbladen rapport](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>Een gevulde kaart maken
1. Selecteer in het deelvenster Velden het veld **Geo** \> **State**.    

   ![geel vinkje naast de status](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
5. [Converteer de kaart](power-bi-report-change-visualization-type.md) naar een choropletenkaart. U ziet dat **State** nu ook wordt vermeld onder **Locatie**. Bing Kaarten gebruikt het veld onder **Locatie** om de kaart te maken.  Het deelvenster Locatie kan een aantal geldige locaties bevatten: landen, staten, provincies, steden, postcodes, enzovoort. Bing Kaarten kan choropletenkaarten maken voor locaties over de hele wereld. Hiervoor is wel een geldige vermelding in het deelvenster Locatie vereist.  

   ![sjablonen met het pictogram voor choropletenkaart gemarkeerd](media/power-bi-visualization-filled-maps-choropleths/img003.png)
6. Filter de kaart om alleen het vasteland van de Verenigde Staten weer te geven.

   a.  Onder aan het deelvenster Visualisaties ziet u het gebied **Filters**.

   b.  Beweeg de muisaanwijzer over **State** en klik op de pijl-omlaag.  
   ![Filters voor visueel niveau die State(All) weergeven](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Zet een vinkje naast **Alles selecteren** en verwijder het vinkje bij **AK**.

   ![Status van de vervolgkeuzelijst waarbij Alles en AK niet zijn geselecteerd](media/power-bi-visualization-filled-maps-choropleths/img005.png)
7. Selecteer **SalesFact** \> **Sentiment** om dit veld toe te voegen aan het vak **Kleurverzadiging**. Het veld in het vak **Kleurverzadiging** bepaalt de kaartarcering.  
   ![Sentiment in het vak Kleurverzadiging](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map.png)
8. De choropletenkaart is groen en rood gearceerd, met rood voor lagere gevoelscijfers en groen voor een hoger, positiever gevoel.  Hier heb ik echter de staat Wyoming (WY) geselecteerd en daar valt op dat het gevoel zeer goed is, namelijk 74.  
   ![zwart dialoogvenster met de status en het sentiment](media/power-bi-visualization-filled-maps-choropleths/power-bi-wy.png)
9. [Sla het rapport op](../service-report-save.md).
##    <a name="adjust-the-color-formatting"></a>Kleuropmaak wijzigen
Power BI biedt veel controle over het uiterlijk van uw choropletenkaart.
1. Selecteer het pictogram met de verfroller om het opmaakvenster te openen.

    ![Opmaakvenster](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-colors.png)

2. Selecteer **Gegevenskleuren** om kleuropties weer te geven.
3. Stel de kleuren Minimum en Maximum in op geel en blauw. Voeg waarden toe voor Minimum en Maximum, op basis van uw gegevens. U kunt experimenteren met deze besturingselementen totdat u het gewenste uiterlijk hebt. 

    ![niet-afwijkende kleuren](media/power-bi-visualization-filled-maps-choropleths/power-bi-color.png)

## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren
Zie [Een filter aan een rapport toevoegen](../power-bi-report-add-filter.md) voor meer informatie over het gebruik van het deelvenster Filters.

Als u een locatie op een choropletenkaart markeert, worden de andere visualisaties op de rapportpagina ook gefilterd en omgekeerd.

1. Als u wilt meelezen, slaat u dit rapport eerst op door **Bestand > Opslaan** te selecteren. 

2. Kopieer de choropletenkaart met behulp van Ctrl-C.

3. Selecteer onderaan het rapportcanvas het tabblad **Gevoel** om de rapportpagina Gevoel te openen.

    ![Tabblad Gevoel geselecteerd](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Verplaats en wijzig de grootte van de visualisaties op de pagina om ruimte maken, en druk op Ctrl+V om de choropletenkaart uit het vorige rapport te plakken.

   ![Choropletenkaart toegevoegd aan pagina Gevoel](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. Selecteer een staat op de choropletenkaart.  Hiermee worden de andere visualisaties op de pagina gemarkeerd. Als u bijvoorbeeld **Texas** selecteert, ziet u dat de gevoelswaarde 74 is, dat Texas zich bevindt in het Central District \#23.   
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