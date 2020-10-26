---
title: 'Zelfstudie: Aantrekkelijke rapporten van Excel-werkmappen maken in Power BI Desktop'
description: In deze zelfstudie wordt beschreven hoe u snel een aantrekkelijk rapport kunt maken van een Excel-werkmap.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 10/13/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: 40c874e9178ffc3586c2dde83f32260bdb86bfad
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256915"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Zelfstudie: Aantrekkelijke rapporten van Excel-werkmappen maken in Power BI Desktop

In deze zelfstudie bouwt u in slechts 20 minuten een fraai rapport van begin tot eind. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

Uw manager wil een rapport met uw meest recente verkoopcijfers zien. U bent gevraagd een managementsamenvatting te geven van de volgende informatie: 

- In welke maand en welk jaar is de meeste winst behaald? 
- Wat zijn de grootste succesfactoren van het bedrijf (per land)? 
- In welk product en welk segment moet het bedrijf blijven investeren? 

Met behulp van onze werkmap met financiële voorbeelden kunnen we dit rapport in zeer korte tijd opbouwen. Zo ziet het uiteindelijk rapport eruit. Laten we aan de slag gaan! 

In deze zelfstudie leert u het volgende:

> [!div class="checklist"]
> * Voorbeeldgegevens op twee verschillende manieren downloaden
> * Uw gegevens voorbereiden met een aantal transformaties
> * Een rapport bouwen met een titel, drie visuals en een slicer
> * Uw rapport in de Power BI-service publiceren zodat u het met uw collega's kunt delen

## <a name="prerequisites"></a>Vereisten

- Voordat u begint, moet u [Power BI Desktop downloaden](https://powerbi.microsoft.com/desktop/).
- Als u van plan bent om uw rapport te publiceren in de Power BI-service en u zich nog niet hebt aangemeld, kunt u zich [aanmelden voor een gratis proefversie](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="get-data"></a>Gegevens ophalen 

U kunt de gegevens voor deze zelfstudie op twee manieren ophalen.

### <a name="get-data-in-power-bi-desktop"></a>Gegevens ophalen in Power BI Desktop

Nadat u Power BI Desktop hebt geopend, selecteert u **Een voorbeeldgegevensset proberen** rechts in het midden van het canvas.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-desktop-canvas-sample-dataset.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

Als u in deze zelfstudie terecht bent gekomen vanuit Power BI Desktop, kiest u **Gegevens laden**.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-two-ways-load-data.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

### <a name="download-the-sample"></a>Het voorbeeld downloaden

U kunt de voorbeeldwerkmap ook rechtstreeks downloaden. 

1. Download de [Excel-werkmap met financiële voorbeelden](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Open Power BI Desktop.
1. In de sectie **Gegevens** van het lint **Start** selecteert u **Excel**.
1. Ga naar de opslaglocatie van de voorbeeldwerkmap en selecteer **Openen**.

## <a name="prepare-your-data"></a>Uw gegevens voorbereiden 

In **Navigator** hebt u de mogelijkheid om de gegevens te *transformeren* of *laden*. In de Navigator is een preview van uw gegevens beschikbaar, zodat u kunt controleren of u het juiste gegevensbereik hebt. Numerieke gegevenstypen worden cursief weergegeven. Als u wijzigingen moet aanbrengen, transformeert u uw gegevens voordat u deze laadt. We willen de visualisaties later eenvoudiger leesbaar maken, dus nu willen we de gegevens transformeren. Wanneer u elke transformatie uitvoert, ziet u dat deze wordt toegevoegd aan de lijst onder **Query-instellingen** bij **Toegepaste stappen** 

1. Selecteer de tabel **Financiën** en kies **Gegevens transformeren**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

1. Selecteer de kolom **Verkochte eenheden**. Op het tabblad **Start** selecteert u **Gegevenstype** en selecteert u **Geheel getal**. Kies **Huidige vervangen** om het kolomtype te wijzigen. 

    De belangrijkste stap voor het opschonen van gegevens die gebruikers het meest uitvoeren, is het wijzigen van gegevenstypen. In dit geval staan de verkochte eenheden in decimale indeling. Maar het is niet erg logisch om 0,2 of 0,5 verkochte eenheden te gebruiken. We gaan dat dus wijzigen in een geheel getal. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

1. Selecteer de kolom **Segment**. Op het tabblad **Transformeren** selecteert u **Notatie** en vervolgens **HOOFDLETTERS**.

    Ook willen we de segmenten later in het diagram eenvoudiger zichtbaar maken. We gaan de kolom Segment opmaken. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. We korten de kolomnaam in van **Naam van de maand** in alleen **Maand**. Dubbelklik op de kolom **Naam van de maand** en wijzig deze naam in alleen **Maand**.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. In de kolom **Product** selecteert u de vervolgkeuzelijst en schakelt u het selectievakje naast **Montana** uit. 

     We weten dat het Montana-product de afgelopen maand uit de handel is gehaald; we willen deze gegevens dus uit ons rapport filteren om verwarring te voorkomen. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. U ziet dat elke transformatie is toegevoegd aan de lijst onder **Query-instellingen** in **Toegepaste stappen**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Selecteer op het tabblad **Start** de optie **Sluiten en toepassen**. Onze gegevens zijn bijna klaar om er een rapport mee te bouwen. 

    Ziet u het Sigma-symbool in de lijst Velden? Power BI heeft gedetecteerd dat die velden numeriek zijn. Power BI geeft ook het datumveld aan met een kalendersymbool.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Extra punten: Een meting in DAX schrijven

Het schrijven van *metingen* in de *DAX*-formuletaal is erg handig voor gegevensmodellering. Er valt heel wat over DAX te leren in de Power BI-documentatie. Voor nu schrijven we een basismeting en koppelen we twee tabellen. 

1. Selecteer **Gegevensweergave** aan de linkerkant. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Selecteer in het lint **Start** de optie **Nieuwe tabel**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Typ deze meting om de tabel Kalender te genereren met alle datums tussen 1 januari 2013 en 31 december 2014.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. Selecteer het vinkje om te bevestigen.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Selecteer nu **Modelweergave** aan de linkerkant. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Sleep het veld **Datum** van de tabel Financiën naar het veld **Datum** in de tabel Kalender om de tabellen te koppelen en breng een *relatie* tussen deze velden tot stand.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

## <a name="build-your-report"></a>Uw rapport maken 

Nu u uw gegevens hebt getransformeerd en geladen, gaan we uw rapport maken. In het deelvenster Velden aan de rechterkant ziet u de velden in het gegevensmodel dat u hebt gemaakt. 

We gaan het uiteindelijke rapport bouwen, één visual per keer. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

### <a name="visual-1-add-a-title"></a>Visual 1: Een titel toevoegen 

1. Selecteer **Tekstvak** op het lintmenu **Invoegen**. Typ 'Managementsamenvatting – Financieel rapport'. 
1. Selecteer de tekst die u hebt getypt. Stel de lettergrootte in op 20 en vetgedrukt. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Schakel in het deelvenster Visualisaties de **Achtergrond** in op **Uit**. 
1. Pas de grootte van het vak zo aan dat het op één regel past. 

### <a name="visual-2-profit-by-date"></a>Visual 2: Winst per datum 

Maak nu een lijndiagram om te zien in welke maand en welk jaar de hoogste winst werd behaald. 

1. Sleep het veld **Winst** vanuit het deelvenster Velden naar een leeg gebied op het rapportcanvas. Standaard wordt in Power BI een kolomdiagram met één kolom, Winst, weergegeven. 
1. Sleep het veld **Datum** naar dezelfde visual. In Power BI wordt het kolomdiagram bijgewerkt zodat de winst voor die twee jaren wordt weergegeven.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. In de sectie **Velden** van het deelvenster Visualisaties selecteert u de vervolgkeuzelijst in de waarde **As**. Wijzig **Datum** van **Datumhiërarchie** in **Datum**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

    In Power BI wordt het kolomdiagram bijgewerkt zodat de winst per maand wordt weergegeven.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. In het deelvenster Visualisaties wijzigt u het visualisatietype in **Lijndiagram**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

    Nu kunt u goed zien dat in december 2014 de meeste winst is behaald.

### <a name="visual-3-profit-by-country"></a>Visual 3: Winst per land 

Maak een kaart om te zien in welk land de hoogste winst is behaald.

1. Sleep het veld **Land** vanuit het deelvenster Velden naar een leeg gebied op uw rapportcanvas om een kaart te maken.
1. Sleep het veld **Winst** naar de kaart.

    Power BI maakt een kaartvisualisatie met bellen die de relatieve winst per locatie aangeven. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

    Het lijkt erop dat Europa het beter doet dan Noord-Amerika. 

### <a name="visual-4-sales-by-product-and-segment"></a>Visual 4: Omzet per Product en Segment 

Maak een staafdiagram om te bepalen in welke bedrijven en segmenten u moet investeren.

1. Sleep de twee diagrammen die u hebt gemaakt zodat ze naast elkaar staan in de bovenste helft van het canvas. Laat wat ruimte vrij aan de linkerkant van het canvas. 
1. Selecteer een leeg gebied in de onderste helft van uw rapportcanvas. 

1. Selecteer in het deelvenster Velden de velden **Verkoop**, **Product** en **Segment**. 

    Power BI maakt automatisch een geclusterd kolomdiagram. 

1. Versleep het diagram zodat het breed genoeg is om de ruimte onder de twee bovenste diagrammen te vullen.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

    Het lijkt erop dat het bedrijf moet blijven investeren in het Paseo-product en zich het beste kan richten op de segmenten Kleine ondernemingen en Overheid.  

### <a name="visual-5-year-slicer"></a>Visual 5: De slicer Jaar 

Slicers zijn een nuttig hulpmiddel om de visuals op een rapportpagina tot een specifieke selectie te filteren. In dit geval maken we een slicer om in te zoomen op de prestaties per maand en jaar.  

1. In het deelvenster Velden selecteert u het veld **Datum** en sleept u dit naar het lege gebied aan de linkerkant van het canvas. 
2. Kies **Slicer** in het deelvenster Visualisaties. 
3. In de sectie Velden van het deelvenster Visualisaties selecteert u de vervolgkeuzelijst in **Velden**. Verwijder Kwartaal en Dag zodat alleen Jaar en Maand overblijven. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

4. Vouw elk jaar uit en wijzig de grootte van de visual, zodat alle maanden zichtbaar zijn.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

Als uw manager u nu vraagt om alleen de gegevens van 2013 te laten zien, kunt u de slicer gebruiken om tussen jaren, of specifieke maanden van elk jaar, te wisselen. 

### <a name="extra-credit-format-the-report"></a>Extra punten: Het rapport opmaken

Als u enige opmaak op dit rapport wilt toepassen om het net iets mooier te maken, kunt u hier een aantal eenvoudige stappen raadplegen. 

**Thema**

- Wijzig op het lint **Weergave** het thema in **Executive**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

**De visuals verfraaien** 

Maak de volgende wijzigingen op het tabblad **Opmaak** in het deelvenster Visualisaties.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Selecteer Visual 2. In de sectie **Titel** wijzigt u **Titeltekst** in Winst op maand en jaar en stelt u de **Tekstgrootte** in op **16 pt**. Zet **Schaduw** op **Aan**. 

1. Selecteer Visual 3. In de sectie **Kaartstijlen** wijzigt u **Thema** in **Grijswaarden**. In de sectie **Titel** wijzigt u de **Tekstgrootte** van de titel in **16 pt**. Zet **Schaduw** op **Aan**.

1. Selecteer Visual 4. In de sectie **Titel** wijzigt u de **Tekstgrootte** van de titel in **16 pt**. Zet **Schaduw** op **Aan**.

1. Selecteer Visual 5. In de sectie **Selectiebesturingselementen** zet u de optie **Alles selecteren weergeven** op **Aan**. In de sectie **Slicerheader** vergroot u de **Tekstgrootte** naar **16 pt**. 

**Een achtergrondvorm voor de titel toevoegen**

1. Op het lint **Invoegen** selecteert u **Vormen** > **Rechthoek**. Plaats dit bovenaan de pagina en pas de vorm aan de breedte van de pagina en de hoogte van de titel aan. 
1. In het deelvenster **Vorm opmaken** in de sectie **Lijn** wijzigt u **Transparantie** in **100%** . 
1. In de **Fill** sectie wijzigt u **Opvulkleur** in **themakleur 5 #6B91C9** (blauw). 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

1. Op het tabblad **Opmaak** selecteert u **Naar achteren** > **Naar achtergrond**. 
1. Selecteer de tekst in Visual 1, de titel en wijzig de tekstkleur in **Wit**. 

**Een achtergrondvorm voor visuals 2 en 3 toevoegen**

1. Op het lint **Invoegen** selecteert u **Vormen** > **Rechthoek** en rekt u dit uit tot de breedte en hoogte van Visuals 2 en 3. 
1. In het deelvenster **Vorm opmaken** in de sectie **Lijn** wijzigt u **Transparantie** in **100%** . 
1. Op het tabblad **Opmaak** selecteert u **Naar achteren** > **Naar achtergrond**. 

### <a name="finished-report"></a>Voltooid rapport

Uw uiteindelijke rapport met opmaak ziet er als volgt uit:  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

Samengevat: dit rapport beantwoordt de belangrijkste vragen van uw manager: 

- In welke maand en welk jaar is de meeste winst behaald? 

    December 2014 

- In welk land ziet het bedrijf de meeste succesfactoren? 

    In Europa zijn dat met name Frankrijk en Duitsland. 

- In welk product en welk segment moet het bedrijf blijven investeren? 

    Het bedrijf moet blijven investeren in het Paseo-product en kan zich het beste richten op de segmenten Kleine ondernemingen en Overheid. 

## <a name="save-your-report"></a>Uw rapport opslaan

- Selecteer in het menu **Bestand** de optie **Opslaan**.

## <a name="publish-to-the-power-bi-service-to-share"></a>Publiceren naar de Power BI-service om te delen 

Als u uw rapport met uw manager en collega's wilt delen, publiceert u dit in de Power BI-service. Wanneer u uw rapport deelt met collega's die over een Power BI-account beschikken, kunnen ze wel met uw rapport werken maar geen wijzigingen opslaan. 

1. Selecteer in Power BI Desktop **Publiceren** op het lint **Start**. 

    Mogelijk moet u zich aanmelden bij de Power BI-service. Als u nog geen account hebt, kunt u zich [registreren voor een gratis proefversie](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Selecteer een bestemming, zoals **Mijn werkruimte** in de Power BI-service > **Selecteren**.
1. Selecteer **Uw-bestandsnaam openen in Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

    Uw voltooide rapport wordt in de browser geopend.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Schermopname van voltooid Power BI-rapport."::: 

1. Selecteer **Delen** bovenaan het rapport om uw rapport met anderen te delen.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Schermopname van voltooid Power BI-rapport.":::

## <a name="next-steps"></a>Volgende stappen

- [Zelfstudie: Verkoopgegevens uit Excel en een OData-feed analyseren](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).
