---
title: Gecertificeerde visuals in Power BI
description: Vereisten en proces voor het indienen van een aangepast visueel element voor certificering. En een lijst met gecertificeerde Power BI-visuals.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: c39b96122016746905ea09c0983adf50356f0c77
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75221960"
---
# <a name="get-a-power-bi-visual-certified"></a>Een Power BI-visual laten certificeren

Gecertificeerde Power BI-visuals zijn visuals in de *Marketplace* die voldoen aan bepaalde vereisten voor *opgegeven code* die zijn getest en goedgekeurd door het *Microsoft Power BI-team*. De testen zijn ontworpen om te controleren of de visual geen toegang heeft tot externe services of resources.

Gecertificeerde Power BI-visuals en [standaardvisuals van Power BI](power-bi-custom-visuals.md) worden gebruikt op dezelfde manier. Ze kunnen worden toegevoegd aan [Power BI Desktop](../desktop-what-is-desktop.md) en de [Power BI-service](../power-bi-service-overview.md) en bekeken met [Power BI - Mobiel](../consumer/mobile/mobile-apps-for-mobile-devices.md) en [Power BI Embedded](embedding.md).

Het certificeringsproces is optioneel. De ontwikkelaars moeten bepalen of ze hun Power BI-visual willen laten certificeren op Marketplace. Zodra een Power BI-visual gecertificeerd is, zijn er meer functies beschikbaar. Zo kunt u de visual [exporteren naar PowerPoint](../consumer/end-user-powerpoint.md) en de visual weergeven in e-mails die worden ontvangen wanneer een gebruiker zich [op rapportpagina's abonneert](../consumer/end-user-subscribe.md).

Niet-gecertificeerde Power BI-visuals zijn niet automatisch onveilige visuals. Sommige visuals zijn niet gecertificeerd omdat ze niet aan een of meer [certificeringsvereisten](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements) voldoen. Bijvoorbeeld als er verbinding wordt gemaakt met een externe service zoals kaartvisuals of visuals waarvoor commerciële bibliotheken worden gebruikt.

Als u een webontwikkelaar bent en uw eigen Power BI-visuals wilt maken en deze wilt toevoegen aan  [Microsoft AppSource](https://appsource.microsoft.com), begint u met de zelfstudie  [Een Power BI-visual ontwikkelen](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft** is *niet* de auteur van Power BI-visuals van derden. Als u de functionaliteit van visuals van derden wilt controleren, kunt u het beste rechtstreeks contact opnemen met de auteur van de visual.

> [!IMPORTANT]
> Microsoft kan naar eigen goeddunken een Power BI-visual uit de lijst met [gecertificeerde Power BI-visuals](#certified-power-bi-visuals) verwijderen.

## <a name="certification-requirements"></a>Vereisten voor certificering

Als uw Power BI-visual moet worden [gecertificeerd](#get-a-power-bi-visual-certified), moet deze voldoen aan de vereisten die in deze sectie worden vermeld. 

> [!TIP]
> U wordt aangeraden EsLint met de standaardbeveiligingsregelset te gebruiken om uw code voorafgaand aan het indienen te valideren.

* Goedgekeurd in Microsoft-verkoperdashboard of Partnercentrum. Uw Power BI-visual moet in onze [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) staan.
* De Power BI-visual is geschreven met *API versie 2.5* of hoger.
* De codeopslagplaats is beschikbaar voor beoordeling door het Power BI-team. Er moet bijvoorbeeld een leesbare indeling van de broncode (JavaScript of TypeScript) beschikbaar voor ons zijn in GitHub.

    >[!NOTE]
    > U hoeft uw code niet openbaar te delen in Github.

* Vereisten voor de codeopslagplaats:
  * Moet deze bestanden bevatten:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Mag niet de map *node_modules* bevatten (voeg *node_modules* toe aan het gitingore*-bestand).
  * De opdracht *npm install* mag geen fouten retourneren.
  * De opdracht *npm audit* mag geen waarschuwingen van het niveau hoog of gemiddeld retourneren.
  * De opdracht *pbiviz package* mag geen fouten retourneren.
  * Moet [TSlint van Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) zonder overschreven configuraties bevatten. Deze opdracht mag geen lint-fouten retourneren.
   * Het gecompileerde pakket van de Power BI-visual moet overeenkomen met het verzonden pakket.
* Vereisten voor de broncode:
   * De Power BI-visual moet ondersteuning bieden voor de [API voor het weergeven van gebeurtenissen](./visuals/event-service.md).
   * Zorg ervoor dat er geen willekeurige/dynamische code wordt uitgevoerd (bad: eval(), onveilig om settimeout(), requestAnimationFrame(), setinterval (functie met gebruikersinvoer) te gebruiken, uitvoeren van gebruikersinvoer/-gegevens).
   * Zorg ervoor dat DOM veilig wordt gemanipuleerd (bad: innerHTML, D3.html(<invoer van gebruiker/gegevens>), gebruik opschoning voor invoer van gebruiker/gegevens voordat deze worden toegevoegd aan de DOM.
   * Zorg ervoor dat er geen javascript-fouten of -uitzonderingen aanwezig zijn in de browserconsole voor invoergegevens. Gebruikers kunnen uw Power BI-visual gebruiken met een ander bereik van gegevenswaarden, dus de visual moet hierop voorbereid zijn. U kunt dit [voorbeeldrapport](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) gebruiken als een testgegevensset.

* Als er eigenschappen in het bestand *capabilities.json* worden gewijzigd, moet u ervoor zorgen deze niet tot gevolg hebben dat rapporten van bestaande gebruikers niet meer werken.

* Zorg ervoor dat de Power BI-visual voldoet aan de [richtlijnen voor Power BI-visuals](./guidelines-powerbi-visuals.md).
    
* Uw code mag alleen openbare OSS-onderdelen bevatten, zoals openbare Javascript- of TypeScript-bibliotheken. De broncode is beschikbaar voor beoordeling en bevat geen bekende beveiligingsproblemen. We kunnen aangepaste visuals met een commercieel onderdeel niet verifiëren.

* Er worden geen externe services of bronnen gebruikt voor de Power BI-visual. U kunt bijvoorbeeld vanuit Power BI geen HTTP/S- of WebSocket-aanvragen naar services verzenden. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Een Power BI-visual indienen voor certificering

Via het Partnercentrum kunt u een aanvraag indienen om uw Power BI-visual door het Power BI-team te laten certificeren.

>[!TIP]
>Het Power BI-certificeringsproces kan enige tijd duren. Als u een nieuwe Power BI-visual maakt, wordt u aangeraden de Power BI-visual te publiceren via het Partnercentrum voordat u de certificeringsaanvraag indient. Dit zorgt ervoor dat de publicatie van de visual niet wordt vertraagd.

Power BI-certificering aanvragen:

1. Meld u aan bij Partnercentrum.
2. Kies uw Power BI-visual op de **pagina Overzicht** en ga naar de instellingspagina **Product**.
3. Schakel het selectievakje **Power BI-certificering aanvragen** in.
4. Geef op de pagina **Controleren en publiceren** in het tekstvak **Opmerkingen voor certificering** een koppeling naar de broncode en de benodigde referenties voor toegang op.

>[!NOTE]
> Als u [Verkoperdashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (het oude beheerprogramma) wilt gebruiken voor het indienen van een Power BI-visual, raadpleegt u de instructies voor het indienen van een [certificeringsaanvraag via Verkoperdashboard](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="certified-power-bi-visuals"></a>Gecertificeerde visuals in Power BI

De gecertificeerde Power BI-visuals worden hieronder vermeld. Klik op de koppeling om de Power BI-visual in AppSource te openen. Als er een video beschikbaar is, kunt u op de videokoppeling klikken om deze te bekijken.

* [3AG Systems - Staafdiagram met absolute afwijking](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems - Staafdiagram met relatieve afwijking](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems - Kolomdiagram met relatieve afwijking](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems - Kolomdiagram met afwijking](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Geavanceerde visual met ringdiagram (volledige functionaliteit)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Geavanceerde visual met ringdiagram (basisfunctionaliteit)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Geavanceerde visual met grafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Geavanceerde netwerkvisualisatie](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Geavanceerde TimeSeries-visual (volledige functionaliteit)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Asterdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft-agenda](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Vlinderdasdiagram door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Box-and-whisker-grafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Box-and-whisker-grafiek door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Bouwsteendiagram door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Belgrafiek door Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Visual met uitgebreid staafdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755), **[videokoppeling](https://youtu.be/AOlsFYkfkcw)**
* [Opsommingstekendiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Visual met uitgebreid staafdiagram door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[videokoppeling](https://youtu.be/mtvUNl9bMjA)**
* [Agenda door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Kalender door Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Candlestick door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[videokoppeling](https://youtu.be/nT_18gyRxPo)**
*  [Kaart met staten door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet-slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Akkoord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[videokoppeling](https://youtu.be/AQvd2FhRyCI)**
*  [Ronde meter door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Cluster-kaart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Aangepaste agenda door Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cilindrische meter door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Meetklok](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[puntdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Puntdiagram door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[videokoppeling](https://youtu.be/By16pX9KT40)**
*  [Inzoom-cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Inzoom-choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Inzoom-kolomdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[videokoppeling](https://youtu.be/lBy2gQQ5YsQ)**
*  [Inzoom-kolomdiagram voor op tijd gebaseerde gegevens](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[videokoppeling](https://youtu.be/T_mRou18vx0)**
*  [Inzoom-ringdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[videokoppeling](https://youtu.be/AUVFrSHmPeo)**
*  [Dual KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamische knopinfo door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Verbeterde spreidingsgrafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[videokoppeling](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten-wafeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filteren op lijstitems door Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[videokoppeling](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed Graph](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[videokoppeling](https://youtu.be/YsTa7uyJ4sg)**
*  [Trechter met bron door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[videokoppeling](https://youtu.be/qJ7s_KrGiUU)**
* [Opgeefdiagram door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globe-gegevensbalken](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Raster door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hiërarchiegrafiek door Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[videokoppeling](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogram met punten door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Horizontaal staafdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Horizontale trechter door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Afbeelding door CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Afbeeldingenraster](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI-grafiek door Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [KPI-kolom door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [KPI-raster door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI-indicator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI-ticker door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Lineaire meter door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot-grafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekkodiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[videokoppeling](https://youtu.be/90FLCKpgicA)**
*  [Multi-KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Overzicht door CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Afspeelas (dynamische slicer)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [videokoppeling](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI-matrix](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[videokoppeling](https://youtu.be/1enze8pcGzY)**
*  [Pulse-grafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[videokoppeling](https://youtu.be/DQWdcQtjDVw)**
*  [Kwadrantdiagram door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Radardiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ringgrafiek door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Draaigrafiek door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankeydiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[videokoppeling](https://youtu.be/WWP9wVUHGaA)**
*  [Spreidingsdiagram door Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Bladerscherm](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Slimme filter door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[videokoppeling](https://youtu.be/gcJsDDRQq28)**
*  [Sparkline door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[videokoppeling](https://youtu.be/0m3Vnvso9tY)**
*  [Stroomgrafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Zonnestraal](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Synoptic Panel door OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Tabelheatmap](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[videokoppeling](https://youtu.be/C3OXdETbS9o)**
*  [Tekstfilter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Tekst-wrapper door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Tijdlijnslicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[videokoppeling](https://youtu.be/ozMtZ4_NZ10)**
*  [Tijdlijn door CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [videokoppeling](https://youtu.be/szNi9YgXFJc)
*  [Tornadodiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[videokoppeling](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Handelsgrafiek door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultieme KPI-kaart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultieme afwijking](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[videokoppeling](https://youtu.be/pDYF8iZxERs)**
*  [Ultieme waterval](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[videokoppeling](https://youtu.be/0BZsVCQdEkc)**
*  [Gebruikerslijst door CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn-diagram door MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Vioolgrafiek](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio-visual](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Wafeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[videokoppeling](https://youtu.be/1vRqYUsm3Vk)**
*  [Woordwolk](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[videokoppeling](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Veelgestelde vragen

Voor meer informatie over visuals gaat u naar [Veelgestelde vragen over gecertificeerde visuals](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Volgende stappen

* [Een aangepaste visual voor Power BI ontwikkelen](../developer/custom-visual-develop-tutorial.md)
* [Microsoft-afspeellijst voor aangepaste visuele elementen op YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualisaties in Power BI](../visuals/power-bi-report-visualizations.md)  
* [Aangepaste visualisaties in Power BI](power-bi-custom-visuals.md)  
* [Power BI-visuals publiceren naar Microsoft AppSource](../developer/office-store.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
