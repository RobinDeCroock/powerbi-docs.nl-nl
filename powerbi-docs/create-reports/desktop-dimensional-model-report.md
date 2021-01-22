---
title: 'Zelfstudie: Aantrekkelijke rapporten van dimensionale modellen maken in Power BI Desktop'
description: In deze zelfstudie bouwt u in slechts 20 minuten met behulp van een dimensionaal model een fraai rapport van begin tot eind.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/19/2021
LocalizationGroup: Reports
ms.openlocfilehash: 03eac7aefdebb31eac353c969db2bf8810173395
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687351"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>Zelfstudie: Aantrekkelijke rapporten van dimensionale modellen maken in Power BI Desktop 

In deze zelfstudie bouwt u in slechts 45 minuten met behulp van een dimensionaal model een fraai rapport van begin tot eind.

U werkt bij AdventureWorks en uw manager wil een rapport met uw meest recente verkoopcijfers zien. U bent gevraagd een managementsamenvatting te geven van de volgende informatie: 

- Op welke dag is het meeste verkocht in februari 2019? 
- In welk land ziet het bedrijf de meeste succesfactoren? 
- In welke productcategorie en resellerbedrijfstypen moet het bedrijf blijven investeren? 

Met behulp van de [Excel-voorbeeldwerkmap voor verkoop van AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) kunt u dit rapport in een mum van tijd bouwen. Zo ziet het uiteindelijk rapport eruit. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Voltooid AdventureWorks-rapport.":::

Wilt u het voltooide product zien? U kunt ook het [voltooide Power BI .pbix-bestand](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix) downloaden.

Laten we aan de slag gaan! 

In deze zelfstudie komen de volgende onderwerpen aan bod:

> [!div class="checklist"]
> * Uw gegevens voorbereiden met een aantal transformaties
> * Een rapport bouwen met een titel, drie visuals en een slicer
> * Uw rapport in de Power BI-service publiceren zodat u het met uw collega's kunt delen

## <a name="prerequisites"></a>Vereisten

- Voordat u begint, moet u [Power BI Desktop downloaden](../fundamentals/desktop-get-the-desktop.md). 
- Als u van plan bent om uw rapport te publiceren in de Power BI-service en u zich nog niet hebt aangemeld, kunt u zich [aanmelden voor een gratis proefversie](../fundamentals/service-self-service-signup-for-power-bi.md). 

## <a name="get-data-download-the-sample"></a>Gegevens ophalen: Het voorbeeld downloaden 

1. Download de [Excel-voorbeeldwerkmap voor verkoop van AdventureWorks](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx). 

1. Open Power BI Desktop. 

1. In de sectie **Gegevens** van het lint **Start** selecteert u **Excel**. 

1. Ga naar de opslaglocatie van de voorbeeldwerkmap en selecteer **Openen**. 

## <a name="prepare-your-data"></a>Uw gegevens voorbereiden 

In het deelvenster Navigator hebt u de mogelijkheid om de gegevens te  *transformeren* of te  *laden* . In de Navigator is een preview van uw gegevens beschikbaar, zodat u kunt controleren of u het juiste gegevensbereik hebt. Numerieke gegevenstypen worden cursief weergegeven. In deze zelfstudie gaat u de gegevens transformeren voordat ze worden geladen.

Selecteer alle tabellen en kies  **Gegevens transformeren**. Zorg ervoor dat u niet de bladen selecteert (met het label *_data*). 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="Laad tabellen in Navigator.":::

Controleer of de gegevenstypen van de kolommen overeenkomen met de gegevenstypen in de volgende tabel. Als Power BI gegevens typen voor u wilt laten detecteren, selecteert u een query en selecteert u vervolgens een of meer kolommen. Op het tabblad **Transformeren** selecteert u **gegevens type detecteren**. Als u wijzigingen wilt aanbrengen in het gedetecteerde gegevens type, selecteert u op het tabblad **Start** de optie **gegevens type** en selecteert u vervolgens het juiste gegevens type in de tabel.

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="Controleer de gegevenstypen van de kolommen.":::


|Query’s uitvoeren  |Kolom  |Gegevenstype  |
|---------|---------|---------|
|Klant  |  CustomerKey | Geheel getal |
|Date | DateKey |    Geheel getal     |
|     | Date | Date      |
|     | MonthKey  | Geheel getal |
|Product  | ProductKey | Geheel getal  | 
|     | Standaardkosten | Decimaal getal  | 
|     | Prijs vermelden | Decimaal getal  | 
|Reseller  | ResellerKey | Geheel getal  | 
|Sales   | SalesOrderLineKey | Geheel getal  | 
|     | ResellerKey  | Geheel getal  | 
|     | CustomerKey | Geheel getal  | 
|     | ProductKey  | Geheel getal  | 
|     | OrderDateKey | Geheel getal  | 
|     | DueDateKey  | Geheel getal  | 
|     | ShipDateKey | Geheel getal  | 
|     | SalesTerritoryKey | Geheel getal  | 
|     | Orderhoeveelheid   | Geheel getal  | 
|     | Prijs per eenheid  | Decimaal getal  | 
|     | Uitgebreid bedrag  | Decimaal getal  | 
|     | Percentage korting op prijs per eenheid | Percentage  | 
|     | Standaardkosten voor product | Decimaal getal  | 
|     | Totale productkosten | Decimaal getal  | 
|     | Verkoophoeveelheid | Decimaal getal  | 
| SalesTerritory  | SalesTerritoryKey | Geheel getal  | 
|  SalesOrder   |  SalesOrderLineKey | Geheel getal  | 

Selecteer op het tabblad **Start** de optie  **Sluiten en toepassen**. 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="De Power Query-knop Sluiten en toepassen.":::

## <a name="model-your-data"></a>Uw gegevens modelleren 

De gegevens die u hebt geladen, zijn bijna klaar voor rapportage. We gaan het gegevensmodel controleren en een aantal wijzigingen aanbrengen. 

Selecteer **Modelweergave** aan de linkerkant. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Selecteer Modelweergave in Power BI Desktop.":::

Het gegevensmodel moet eruitzien zoals in de volgende afbeelding, waarbij elke tabel in een vak wordt weergegeven. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="Het gegevensmodel waarmee u moet beginnen.":::

### <a name="create-relationships"></a>Relaties maken

Dit model is een typisch *sterschema* dat kan worden weergegeven vanuit datawarehouses: Het lijkt op een ster. Het midden van de ster is een feitentabel. De omringende tabellen worden dimensietabellen genoemd, die middels relaties aan de feitentabel zijn gekoppeld. De feitentabel bevat numerieke gegevens over verkooptransacties, zoals Verkoopbedrag en Standaardkosten voor product. De dimensies bieden een context zodat u onder andere de volgende zaken kunt analyseren: 

- Welk product is verkocht... 
- aan welke klant... 
- door welke reseller... 
- in welk verkoopgebied.  

Als u goed kijkt, ziet u dat alle dimensietabellen betrekking hebben op de tabel Feit met relatie, met uitzondering van de datum. Voeg nu aan Datum een aantal relaties toe. Versleep de DateKey van de tabel Datum naar OrderDateKey in de tabel Verkoop. U hebt een zogeheten veel-op-een-relatie gemaakt van Datum naar Verkoop, zoals wordt aangegeven door de **1** en het sterretje * (veel) aan de twee uiteinden van de regel.  

De relatie wordt een-op-veel genoemd omdat we voor een bepaalde datum een of meer verkooporders hebben. Als elke datum maar één verkooporder zou hebben, noemen we dit een een-op-een-relatie. Het pijltje in het midden van de regel geeft de richting voor kruislings filteren aan. Hiermee wordt aangegeven dat u waarden uit de tabel Datum kunt gebruiken om de tabel Verkoop te filteren, zodat u met behulp van de relatie kunt analyseren wanneer een verkooporder is geplaatst.  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Relatie tussen de tabellen Verkoop en Datum.":::

In de tabel Verkoop staat meer informatie over datums met betrekking tot verkooporders, zoals Vervaldatum en Verzenddatum. Voeg twee nieuwe relaties toe aan de tabel Datum door het verslepen van: 

- DateKey naar DueDateKey 
- DateKey naar ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Drie relaties tussen de tabellen Verkoop en Datum.":::

U ziet aan de doorlopende lijn dat de eerste relatie, met OrderDateKey, actief is. De andere twee relaties zijn inactief, wat u aan de stippellijnen kunt zien. In Power BI wordt standaard de actieve relatie gebruikt om de relatie tussen Verkoop en Datum aan te duiden. Daarom wordt een som van SalesAmount berekend op basis van Besteldatum, niet Vervaldatum of Verzenddatum. U kunt dit gedrag bewerken. Zie [Extra punten: een meting in DAX schrijven](#extra-credit-write-a-measure-in-dax) verderop in deze zelfstudie.

### <a name="hide-key-columns"></a>Sleutelkolommen verbergen

Een normaal sterschema bevat verschillende sleutels waarmee de relaties tussen Feiten en Dimensies worden bewaard. Normaal worden sleutelkolommen niet gebruikt in de rapporten. Verberg de sleutelkolommen zodat bij de lijst met velden minder velden worden weergegeven en het gegevensmodel eenvoudiger kan worden gebruikt. 

Bekijk alle tabellen en verberg alle kolommen waarvan de naam eindigt op *Key*: 

Selecteer het **oogpictogram** naast de kolom en kies **Verbergen in rapportweergave**.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="Zichtbare kolom met oogpictogram.":::

U kunt ook het **oogpictogram** naast de kolom in het deelvenster Eigenschappen selecteren.

Verborgen velden zijn voorzien van dit pictogram, een oog met een streep erdoorheen. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="Veld met het verborgen oogpictogram.":::
 
Verberg deze velden.

|Tabel  |Kolom  |
|---------|---------|
|Klant  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|Product     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

Als het goed is, ziet uw gegevensmodel er nu uit als dit gegevensmodel, met relaties tussen Verkoop en alle andere tabellen, en zijn alle sleutelvelden verborgen: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="Gegevensmodel met verborgen sleutelkolommen.":::

### <a name="create-hierarchies"></a>Hiërarchieën maken

Nu het gegevensmodel vanwege de verborgen kolommen eenvoudiger kan worden gebruikt, voegt u een aantal *hiërarchieën* toe om het model nog gemakkelijker te kunnen gebruiken. Dankzij hiërarchieën kunt u eenvoudiger door groeperingen navigeren. Steden vallen bijvoorbeeld onder een Staat of Provincie, en die vallen weer onder een Land of Regio. 

Maak de volgende hiërarchieën. 

1. Klik met de rechtermuisknop op het veld van het hoogste niveau, of met de minste granulariteit, in de hiërarchie en kies **Hiërarchie maken**. 

1. Stel in het deelvenster **Eigenschappen** de **Naam** van de hiërarchie in en stel de niveaus in. 

1. **Pas vervolgens niveauwijzigingen toe**. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="Het deelvenster Eigenschappen van hiërarchie.":::

U kunt in het deelvenster Eigenschappen ook de namen van niveaus in een hiërarchie wijzigen zodra u die hebt toegevoegd. Wijzig de naam van de niveaus Jaar en Kwartaal van de fiscale hiërarchie in de tabel Datum. 

Hier ziet u de hiërarchieën die u moet maken.

| Tabel |Hiërarchienaam |Niveaus  |
|---------|---------|---------|
|Klant     | Geografie   | Land-regio  |
|     | | Staat-Provincie  |
|     |         | Plaats |
|Rij4     |         | Postcode |
|Rij5     |         | Klant   |
|Date     | Fiscaal  | Jaar (fiscaal jaar)  |
|     |         | Kwartaal (fiscaal kwartaal) |
|     |         | Maand |
|     |         | Datum |
| Product  | Producten | Categorie |
|     |         | Subcategorie |
|     |         | Model |
|     |         | Product |
| Reseller   | Geografie | Land-regio |
|     |         | Staat-Provincie |
|     |         | Plaats  |
|     |         | Postcode  |
|     |         | Reseller |
| SalesOrder  | Verkooporders | Verkooporder |
|     |         | Verkooporderregel |
| SalesTerritory    | Verkoopgebieden | Groep |
|     |         | Land |
|     |         | Regio |
 
Als het goed is, ziet uw gegevensmodel er nu uit zoals het volgende gegevensmodel. Het model bevat dezelfde tabellen, maar elke dimensietabel bevat een hiërarchie: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="Gegevensmodel met dimensietabellen met hiërarchieën.":::

### <a name="rename-tables"></a>Tabelnamen wijzigen

Ter afsluiting van de modellering wijzigt u de naam van de volgende tabellen in het deelvenster Eigenschappen: 

|Oude tabelnaam  |Nieuwe tabelnaam  |
|---------|---------|
|SalesTerritory    |  Verkoopterritorium   |
|SalesOrder  |  Verkooporder   |

Deze stap is noodzakelijk omdat Excel-tabelnamen geen spaties mogen bevatten.

Nu is uw uiteindelijke gegevensmodel gereed.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="Voltooid gegevensmodel met gewijzigde tabelnamen.":::

## <a name="extra-credit-write-a-measure-in-dax"></a>Extra punten: Een meting in DAX schrijven 

Het schrijven van *metingen* in de DAX-formuletaal is erg handig voor gegevensmodellering. U kunt heel veel [leren over DAX in de Power BI-documentatie](/dax/). Schrijf voor dit moment alleen een basismeting waarmee de totale verkoophoeveelheid wordt berekend op basis van de vervaldatum op de verkooporder in plaats van de standaardbesteldatum. Voor deze meting wordt de [functie USERELATIONSHIP](/dax/userelationship-function-dax) gebruikt om de relatie tussen Verkoop en Datum te activeren op basis van DueDate voor de context van de meting. Vervolgens wordt [CALCULATE](/dax/calculate-function-dax) gebruikt om de som van de verkoophoeveelheid in die context te berekenen.

1. Selecteer Gegevensweergave aan de linkerkant. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="Selecteer Gegevensweergave aan de linkerkant.":::

1. Selecteer de tabel Verkoop in de lijst Velden.

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="Selecteer de tabel Verkoop in de lijst Velden.":::

1. Selecteer op het lint **Start** de optie  **Nieuwe meting**. 

1. Selecteer of typ deze meting om de totale verkoophoeveelheid te berekenen op basis van de vervaldatum op de verkooporder in plaats van de standaardbesteldatum:

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. Selecteer het vinkje om te bevestigen. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="Selecteer het vinkje om de DAX-meting te bevestigen.":::

## <a name="build-your-report"></a>Uw rapport maken 

Nu u uw gegevens hebt gemodelleerd, gaan we uw rapport maken. Ga naar de Rapportweergave. In het deelvenster Velden aan de rechterkant ziet u de velden in het gegevensmodel dat u hebt gemaakt.

We gaan het uiteindelijke rapport bouwen, één visual per keer. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="Voltooid rapport, met nummers die elke visual markeren":::

### <a name="visual-1-add-a-title"></a>Visual 1: Een titel toevoegen 

1. Selecteer **Tekstvak** op het lintmenu **Invoegen**. Typ 'Managementsamenvatting – Verkooprapport'. 

1. Selecteer de tekst die u hebt getypt. Stel de lettergrootte in op **20** en **Vetgedrukt**. 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="Maak de tekst voor de Managementsamenvatting op.":::

1. Schakel in het deelvenster Visualisaties de **Achtergrond** in op **Uit**. 

1. Pas de grootte van het vak zo aan dat het op één regel past. 

### <a name="visual-2-sales-amount-by-date"></a>Visual 2: Verkoophoeveelheid per datum 

Maak vervolgens een lijndiagram om te zien in welke maand en welk jaar de hoogste verkoopcijfers werden behaald.

1. Sleep het veld **Verkoophoeveelheid** vanuit het deelvenster Velden van de tabel **Verkoop** naar een leeg gebied op het rapportcanvas. Standaard wordt in Power BI een kolomdiagram met één kolom, Verkoophoeveelheid, weergegeven. 

1. Versleep het veld **Maand** van de **fiscale** hiërarchie in de tabel **Datum** naar het kolomdiagram. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="Maak een kolomdiagram met voor elk jaar een kolom.":::

1. Verwijder de velden **Jaar** en **Kwartaal** uit de sectie **Velden** van het deelvenster Visualisaties: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="Verwijder de velden Jaar en Kwartaal uit de sectie Velden van het deelvenster Visualisaties.":::

1. In het deelvenster Visualisaties wijzigt u het visualisatietype in **Vlakdiagram**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="Wijzig het kolomdiagram in een vlakdiagram.":::

1. Als u de DAX-meting in het extra krediet hierboven hebt toegevoegd, voegt u deze ook toe aan **Waarden**. 
1. Open het deelvenster Opmaak, open Gegevenskleuren en wijzig de kleur van **Verkoophoeveelheid per vervaldatum** in een kleur die meer contrast biedt, zoals rood.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Verkoophoeveelheid per vervaldatum, als vlakdiagram.":::

    Zoals u kunt zien, valt Verkoophoeveelheid per vervaldatum iets achter Verkoophoeveelheid. Dit geeft aan dat de relatie wordt gebruikt tussen de tabellen Verkoop en Datum, die DueDateKey gebruikt. 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>Visual 3: Orderhoeveelheid per Land reseller 

Maak nu een kaart om te zien in welk land de resellers het hoogste aantal orders hebben.

1. Sleep het veld **Land-regio** in het deelvenster Velden van de tabel **Reseller** naar een leeg gebied op uw rapportcanvas. In Power BI wordt een kaart gemaakt. 

1. Versleep het veld **Orderhoeveelheid** van de tabel **Verkoop** naar de kaart. Zorg ervoor dat **Land-regio** zich in de bron **Locatie** bevindt en dat **Orderhoeveelheid** zich in de bron **Grootte** bevindt. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="Kaart van de orderhoeveelheid per land/regio.":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>Visual 4: Verkoophoeveelheid per productcategorie en resellerbedrijfstype 

Maak vervolgens een kolomdiagram om te onderzoeken welke producten worden verkocht per resellerbedrijfstype.

1. Sleep de twee diagrammen die u hebt gemaakt zodat ze naast elkaar staan in de bovenste helft van het canvas. Laat wat ruimte vrij aan de linkerkant van het canvas. 

1. Selecteer een leeg gebied in de onderste helft van uw rapportcanvas. 

1. Selecteer in het deelvenster Velden de opties **Verkoophoeveelheid** bij **Verkoop**, **Productcategorie** bij **Product** en **Bedrijfstype** bij **Reseller**.
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-field-well.png" alt-text="Controleer of de categorie en het bedrijfs type op rijen en verkoop bedrag zijn geselecteerd als waarden.":::
    
    Power BI maakt automatisch een geclusterd kolomdiagram. Wijzig de visualisatie in een **Matrix**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="Wijzig het geclusterde kolomdiagram in een matrix.":::

1. Houd de matrix geselecteerd en wis vervolgens op het deelvenster Filters, onder **Bedrijfstype** > **Alles selecteren** het vak **[Niet van toepassing]** . 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="Filter het bedrijfstype Niet van toepassing weg.":::

1. Versleep de matrix zodat deze breed genoeg is om de ruimte onder de twee bovenste diagrammen te vullen. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="Maak de matrix breder om het rapport te vullen.":::

1. Open in het deelvenster Opmaak voor de matrix de sectie **Voorwaardelijke opmaak** en schakel **Gegevensbalken** in. Selecteer **Geavanceerde besturingselementen** en stel een lichter kleur in voor de positieve balk. Selecteer **OK**. 

1. Verg root de breedte van de kolom verkoop bedrag zodat het hele gebied wordt bedekt door de matrix te slepen.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Matrix met gegevensbalken voor Verkoophoeveelheid.":::

Zo te zien heeft Fietsen een hogere algemene Verkoophoeveelheid en verkopen de Resellers toegevoegde waarde het meeste, op de voet gevolgd door Magazijnen. Wat Onderdelen betreft verkopen de Magazijnen meer dan de Resellers toegevoegde waarde. 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>Visual 5: Boekkalenderslicer 

Slicers zijn een nuttig hulpmiddel om de visuals op een rapportpagina tot een specifieke selectie te filteren. In dit geval maken we een slicer om in te zoomen op de prestaties per maand, kwartaal en jaar. 

1. Selecteer in het deelvenster Velden de **Fiscale** hiërarchie in de tabel **Datum** en sleep deze naar het lege gebied aan de linkerkant van het canvas. 

1. Kies **Slicer** in het deelvenster Visualisaties. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="Voeg een kalenderslicer voor verkoop voor rapporten toe.":::

1. Verwijder **Kwartaal** en **Datum** uit de sectie Velden van het deelvenster Visualisaties zodat alleen **Year** en **Maand** overblijven. 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="Verwijder Kwartaal en Datum uit de Fiscale slicer.":::

Als uw manager u nu vraagt om alleen de gegevens voor een specifieke maand te laten zien, kunt u de slicer gebruiken om tussen jaren of specifieke maanden van elk jaar te wisselen. 

## <a name="extra-credit-format-the-report"></a>Extra punten: Het rapport opmaken 

Als u enige opmaak op dit rapport wilt toepassen om het net iets mooier te maken, kunt u hier een aantal eenvoudige stappen raadplegen. 

### <a name="theme"></a>Thema 

- Selecteer op het lint  **Weergeven** de optie **Thema's** en wijzig het thema in  **Executive**. 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="Kies het Executive-thema.":::

### <a name="spruce-up-the-visuals"></a>De visuals verfraaien 

Maak de volgende wijzigingen op het tabblad **Opmaak** in het deelvenster Visualisaties. 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="Schermopname van het tabblad Opmaak in het deelvenster Visualisaties.":::

**Visual 2, Verkoophoeveelheid per datum**

1. Selecteer Visual 2, Verkoophoeveelheid per datum. 
1. Als u de DAX-meting niet hebt toegevoegd, wijzigt u in de sectie **Titel** de tekst van de **titel** in 'Verkoophoeveelheid per besteldatum'. 

    Als u de DAX-meting wel hebt toegevoegd, wijzigt u de **titeltekst** in 'Verkoophoeveelheid per besteldatum/vervaldatum'. 

1. Stel de **Tekengrootte** in op  **16 punten**. 
1. Wissel de instelling voor **Schaduw** naar **Aan**. 

**Visual 3, Orderhoeveelheid per Land reseller**

1. Selecteer Visual 3, Orderhoeveelheid per Land reseller. 
1. Wijzig in de sectie **Kaartstijlen** het  **Thema** in **Grijswaarden**. 
1. Wijzig in de sectie  **Titel** de **titeltekst** in 'Orderhoeveelheid per Land reseller'.
1. Stel de **Tekengrootte** in op  **16 punten**. 
1. Wissel de instelling voor **Schaduw** naar **Aan**.  

**Visual 4, Verkoophoeveelheid per productcategorie en resellerbedrijfstype**

1. Selecteer Visual 4, Verkoophoeveelheid per productcategorie en resellerbedrijfstype. 
1. Wijzig in de sectie  **Titel** de **titeltekst** in 'Verkoophoeveelheid per productcategorie en resellerbedrijfstype'.
1. Stel de **Tekengrootte** in op  **16 punten**. 
1. Wissel de instelling voor **Schaduw** naar **Aan**. 

**Visual 5, boekkalenderslicer**

1. Selecteer Visual 5, boekkalenderslicer.
1. Zet in de sectie **Selectiebesturingselementen** de optie  **Alles selecteren weergeven** op **Aan**. 
1. Stel de in de sectie  **Slicerkoptekst** de optie **Tekengrootte** in op  **16 punten**. 

### <a name="add-a-background-shape-for-the-title"></a>Een achtergrondvorm voor de titel toevoegen 

1. Selecteer op het lint  **Invoegen** de optie **Vormen** > **Rechthoek**. 
1. Plaats dit bovenaan de pagina en pas de vorm aan de breedte van de pagina en de hoogte van de titel aan. 
1. Wijzig in het deelvenster **Vorm opmaken** in de sectie **Lijn** , de optie **Transparantie** in **100%** . 
1. Wijzig in de sectie **Opvullen** de **Opvulkleur** in **Themakleur 5 #6B91C9 (blauw)** . 
1. Selecteer op het tabblad **Opmaak** de optie  **Naar achteren** > **Naar achtergrond**. 
1. Selecteer de tekst in Visual 1, de titel en wijzig de **tekstkleur** in  **Wit**. 

## <a name="finished-report"></a>Voltooid rapport 

Selecteer **FY2019** in de slicer.

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Uw uiteindelijke voltooide rapport.":::

Samengevat: dit rapport beantwoordt de belangrijkste vragen van uw manager: 

- Op welke dag is het meeste verkocht in februari 2019? 
    25 februari, met een verkoopbedrag van USD 253.915,47. 

- In welk land ziet het bedrijf de meeste succesfactoren? 
    In de Verenigde Staten, met een orderhoeveelheid van 132.748. 

- In welke productcategorie en resellerbedrijfstypen moet het bedrijf blijven investeren? 
    Het bedrijf kan het beste blijven investeren in de categorie Fietsen en de resellerbedrijven Reseller toegevoegde waarde en Magazijn. 

## <a name="save-your-report"></a>Uw rapport opslaan 

- Selecteer in het menu **Bestand** de optie **Opslaan**. 


## <a name="publish-to-the-power-bi-service-to-share"></a>Publiceren naar de Power BI-service om te delen 

Als u uw rapport met uw manager en collega's wilt delen, publiceert u dit in de Power BI-service. Wanneer u uw rapport deelt met collega's die over een Power BI-account beschikken, kunnen ze wel met uw rapport werken maar geen wijzigingen opslaan.

1. Selecteer op het lint **Start** in Power BI Desktop **Publiceren**. 
1. Mogelijk moet u zich aanmelden bij de Power BI-service. Als u nog geen account hebt, [registreert u zich aan voor een gratis proefversie](https://app.powerbi.com/signupredirect?pbi_source=web). 

1. Selecteer een bestemming, zoals Mijn werkruimte in de Power BI-service >  **Selecteren**. 

1. Selecteer **Uw-bestandsnaam openen in Power BI**. Uw voltooide rapport wordt in de browser geopend. 

1. Selecteer **Delen** bovenaan het rapport om uw rapport met anderen te delen.

## <a name="next-steps"></a>Volgende stappen 

- Download het [voltooide Power BI .pbix-bestand](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- Meer informatie over [DAX en gegevensmodellering in Power BI Desktop](/learn/modules/dax-power-bi-models/)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
