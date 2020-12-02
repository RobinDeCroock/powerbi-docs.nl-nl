---
title: COVID-19-traceringsvoorbeeld voor Amerikaanse staats- en lokale overheden
description: Download en wijzig het voorbeeldrapport met Amerikaanse staats- en lokale gegevens voor de COVID-19-pandemie.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 04/28/2020
LocalizationGroup: Samples
ms.openlocfilehash: e6f8e02efa7dc2e56a945aaffcf22d8497052404
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396010"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>COVID-19-traceringsvoorbeeld voor Amerikaanse staats- en lokale overheden

Het Power BI-team heeft een voorbeeld voor tracering van COVID-19 gemaakt waarmee Amerikaanse staats- en lokale overheden een interactief rapport over COVID-19 kunnen publiceren of aanpassen. Met behulp van Power BI Desktop kunnen ze COVID-19-gegevens analyseren en visualiseren om hun gemeenschappen per plaats, regio, staat of landelijk op de hoogte te houden. Vervolgens kunnen ze het rapport via Power BI publiceren op internet om inwoners te informeren. Het artikel biedt verschillende opties voor het gebruik van interactieve Power BI-visualisaties in uw eigen openbare verhaal, blog of website.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="COVID-19-voorbeeld met Amerikaanse gegevens":::

In dit artikel komen de volgende onderwerpen aan bod:

- Invoegcode kopiëren en deze op uw eigen site plaatsen. 
- Aanpassingen aanbrengen, zoals het opmaken van een specifieke status.
- Publiceren naar de Power BI-service.
- Publiceren op internet. 
- Deze gegevens verfijnen met gegevens uit een andere bron. 

## <a name="prerequisites"></a>Vereisten

Voordat u aan de slag kunt gaan met Power BI om uw verhaal te vertellen, moet u aan de volgende vereisten voldoen:

- Download de gratis [Power BI Desktop](https://powerbi.microsoft.com/desktop/)-app.
- Meld u aan voor de [Power BI-service](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Optie 1: Vooraf gemaakte invoegcode

Microsoft heeft het voorbeeldrapport gepubliceerd en een invoegcode voor publiceren op internet gemaakt. U kunt de invoegcode gebruiken om het volledige voorbeeld in te sluiten, met inbegrip van de landelijke weergave en inzoomen op de weergave per staat of regio in uw eigen website. Voordat u deze gegevens publiceert, kunt u het beste de [disclaimers](#disclaimers) in dit artikel lezen.

Als u de interactieve afbeelding wilt opnemen op uw site, kopieert en plakt u de volgende invoegcode om de afbeelding op uw webpagina weer te geven.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

De invoegcode is een HTML-iFrame-element dat u in een HTML-pagina kunt invoegen. Pas de breedte en hoogte van het iFrame aan voor weergave op uw site. Het voorbeeldrapport is gemaakt in de beeldverhouding 16:9, dus kies een grootte waarbij die verhouding blijft behouden. Bij een juiste implementatie wordt de afbeelding weergegeven zonder extra grijze randen. [Bekijk de tips en trucs voor de grootte van het iFrame](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width) wanneer u deze wijzigingen aanbrengt.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Optie 2: Het Power BI-voorbeeldbestand aanpassen

Het Power BI-bestand met de gegevens en interactieve afbeelding is een PBIX-bestand, zodat u het kunt bewerken in Power BI Desktop.  

Een typische aanpassing is het rapport te filteren op een specifieke staat, om vervolgens uw eigen invoegcode voor publiceren naar internet te maken voor uw aangepaste rapport.

USAFacts-gegevens worden verschaft onder een Creative Commons-licentie waarvoor een naamsvermelding vereist is. Lees de [disclaimers](#disclaimers) voordat u deze gegevens publiceert.

Om aan de slag te gaan, [downloadt u het PBIX-bestand (hier)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Uw rapport bijwerken 

1. Download de nieuwste versie van de gratis app, [Power BI Desktop](https://powerbi.microsoft.com/desktop/), als u dat nog niet hebt gedaan. 

2. Download het [PBIX-bestand](https://go.microsoft.com/fwlink/?linkid=2125058), als u dat nog niet hebt gedaan, en open het in Power BI Desktop.

3. Als u het rapport wilt filteren op een specifieke staat, selecteert u de pijl om het deelvenster Filters uit te vouwen.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Het deelvenster Filters uitvouwen":::

4. Selecteer een staat waarin u bent geïnteresseerd. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Een staat selecteren":::

5. Selecteer **Bestand** > **Opslaan** om uw wijzigingen op te slaan. 

### <a name="refresh-your-report"></a>Uw rapport vernieuwen 

1. Selecteer de knop **Vernieuwen**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Knop Vernieuwen":::

2. Selecteer **Anoniem** > **Verbinding maken**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Anoniem selecteren":::

 
3. Selecteer **Privacyniveaus negeren**, indien weergegeven, en vervolgens **Opslaan**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Privacyniveaus selecteren":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Uw rapport publiceren in de Power BI-service

Wanneer u het rapport naar wens hebt aangepast, [voert u de stappen uit die hier worden beschreven om uw rapport te publiceren](../create-reports/desktop-upload-desktop-files.md) in de Power BI-service.

### <a name="configure-scheduled-refresh"></a>Geplande vernieuwing configureren

Als u de gegevens in het rapport up-to-date wilt houden, kunt u [geplande vernieuwing configureren](../connect-data/refresh-scheduled-refresh.md) nadat u het rapport hebt gepubliceerd.

Wanneer u de stappen uitvoert, kiest u de volgende opties:

1. Verificatiemethode voor gegevensbronreferenties: Anoniem
2. Instelling van privacyniveau voor deze gegevensbron: Openbaar

Als u de instelling voor het vernieuwen wilt testen, selecteert u de optie [Nu vernieuwen](../connect-data/refresh-data.md#data-refresh), die beschikbaar is via het item van de gegevensset.

De vernieuwde gegevens worden telkens geladen wanneer de geplande vernieuwing wordt uitgevoerd. De onderliggende gegevens worden verschaft door USAFacts en worden mogelijk niet zo vaak bijgewerkt als volgens uw geplande vernieuwing. Ga naar de [website van USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) als uw wilt weten wanneer de onderliggende gegevens voor het laatst zijn bijgewerkt. 

Als u het aangepaste rapport op uw website wilt publiceren, kunt u het beste de geplande vernieuwing zo configureren dat deze ten minste zo vaak wordt uitgevoerd als de gegevens van USAFacts worden bijgewerkt. Omdat de gegevens van USAFacts elke dag op verschillende tijden kunnen worden vernieuwd, kunt u waarschijnlijk het beste meerdere vernieuwingen per dag configureren. 

### <a name="create-a-publish-to-web-embed-code"></a>Een invoegcode voor publiceren naar internet maken 

Als u het aangepaste rapport in uw eigen website wilt invoegen, voert u de instructies voor het [maken van uw eigen invoegcode voor publiceren naar internet](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web) uit.

Zodra u de invoegcode hebt gepubliceerd, gebruikt u de iFrame in het bevestigingsvenster om deze in te voegen in uw website.

Als u wijzigingen aanbrengt in het rapport in Power BI Desktop, kunt u het bestaande rapport in de Power BI-service publiceren en vervangen. De invoegcode wordt niet gewijzigd. Het duurt ongeveer een uur voordat wijzigingen in het rapport of vernieuwde gegevens op uw website worden weergegeven. 

## <a name="option-3-mash-up-data-from-another-source"></a>Optie 3: Gegevens verfijnen met gegevens uit een andere bron 

U kunt de gegevens in dit rapport ook verfijnen met gegevens uit een andere bron. Het volgende voorbeeld is gebaseerd op gegevens van [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Voordat u deze gegevens publiceert, kunt u het beste de [disclaimers](#disclaimers) in dit artikel lezen.

1. Selecteer **Gegevens ophalen** > **Internet**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Knop Gegevens ophalen":::

2. Voer de volgende URL in:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Gegevens op internet selecteren":::

3. Selecteer **OK**. 

    > [!NOTE]
    > De koppeling die door Johns Hopkins University is gepubliceerd, kan worden gewijzigd. Ga naar de [GitHub-pagina van Johns Hopkins](https://github.com/CSSEGISandData/COVID-19) voor de meest recente informatie.

4. Selecteer **Laden** om de gegevensset voor het totale aantal bevestigde gevallen ter wereld te laden.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Gegevens van internet laden":::

    Raadpleeg het artikel [Verbinding met webpagina's maken vanuit Power BI Desktop](../connect-data/desktop-connect-to-web.md) voor meer informatie over het laden van gegevens van internet.
    
Vervolgens kunt u de gegevens visualiseren met Power BI Desktop. Gebruik tot slot de stappen in **Optie 2:** [Uw rapport publiceren in de Power BI-service](#publish-your-report-to-the-power-bi-service) om het rapport te publiceren en een aangepaste invoegcode te maken. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Optie 4: De sjabloon-app Traceringsrapport voor COVID-19 in de Verenigde Staten gebruiken

Als extra optie heeft het Power BI-team *sjabloon-app* Traceringsrapport voor COVID-19 in de Verenigde Staten gemaakt zodat u onmiddellijk aan de slag kunt. Sjabloon-apps zijn bundels rapporten, dashboards en gegevenssets voor een specifieke gegevensbron. U kunt deze downloaden van AppSource, ze gebruiken of aanpassen aan uw eigen behoeften en ze distribueren naar uw collega's. 

Deze sjabloon-app Traceringsrapport voor COVID-19 in de Verenigde Staten bevat een vooraf gemaakt rapport met metrische COVID-19-gegevens dat u zo kunt gebruiken, rechtstreeks kunt personaliseren in de Power BI-service of kunt downloaden om desgewenst andere gegevensbronnen toe te voegen. Meer informatie over het installeren van de [sjabloon-app Traceringsrapport voor COVID-19 in de Verenigde Staten](../connect-data/service-connect-to-covid-19-tracking.md) en direct aan de slag gaan.

## <a name="about-the-data-source-for-this-report"></a>Over de gegevensbron voor dit rapport
In dit interactieve rapport worden gegevens verzameld van het Amerikaanse centrum voor ziektepreventie en -bestrijding (CDC) en staats- en lokale gezondheidsinstellingen. Gegevens op districtsniveau worden bevestigd door rechtstreeks naar de staats- en lokale instanties te verwijzen (koppeling).

De gegevens worden geleverd door USAFacts. Vanwege de frequentie van gegevensupdates, komen ze mogelijk niet overeen met de exacte aantallen die worden gerapporteerd door overheidsorganisaties of nieuwsmedia. Ga naar de [website van USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) voor meer informatie of om de gegevens te downloaden. 

## <a name="disclaimers"></a>Disclaimers

Dit rapport en deze gegevens worden geleverd "zoals deze is", "met alle fouten" en zonder enige garantie. Microsoft geeft geen expliciete garanties en wijst uitdrukkelijk alle impliciete garanties af, waaronder garanties van verhandelbaarheid, geschiktheid voor een bepaald doel en niet-schending.

De gegevens van USAFacts zijn beschikbaar onder een Creative Commons-licentie. Als u deze wilt gebruiken, moet u USAFacts als de gegevensprovider vermelden en een koppeling terug naar USAFacts maken. De exacte stappen voor de naamsvermelding vindt u in de sectie **#MadewithUSAFacts** van de pagina van USAFacts, [Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

De gegevens van Johns Hopkins University zijn auteursrechtelijk beschermd door 2020 Johns Hopkins University. Alle rechten voorbehouden. Deze zijn uitsluitend bestemd voor onderwijs- en academische onderzoeksdoeleinden. Hier vindt u de volledige [Gebruiksvoorwaarden](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) voor het verfijnen van de gegevens uit het voorbeeld. Meer informatie vindt u op de [website van Johns Hopkins University](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Volgende stappen

[Voorbeelden voor Power BI downloaden](../create-reports/sample-datasets.md)




