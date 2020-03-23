---
title: De nieuwe filterervaring in Power BI-rapporten
description: Filters in Power BI hebben nieuwe functionaliteit en een nieuw ontwerp.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/26/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: f4dbbdd30b403c8ac14db069b826f26af0bce24a
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79201816"
---
# <a name="work-with-filters-in-power-bi-reports"></a>Werken met filters in Power BI-rapporten

Filters in Power BI hebben nieuwe functionaliteit en een nieuw ontwerp. Wanneer u kiest voor de nieuwe filterervaring, kunt u het deelvenster Filters opmaken zodat het eruitziet als de rest van het rapport. U kunt filters vergrendelen en zelfs verbergen. Bij het ontwerpen van uw rapport ziet u het oude deelvenster Filters helemaal niet meer in het deelvenster Visualisaties. Alle bewerkingen en opmaakaanpassingen van filters kunnen nu vanuit één deelvenster Filters worden gedaan. 

![Nieuwe filterfunctionaliteit](media/power-bi-report-filter/power-bi-filter-new-look.png)

Hieronder staan enkele taken die u als rapportontwerper kunt uitvoeren met het nieuwe deelvenster Filters:

- Velden toevoegen en verwijderen om op te filteren. 
- De filterstatus wijzigen.
- Het deelvenster Filters zo indelen en aanpassen dat het een onderdeel van uw rapport lijkt.
- Definiëren of het venster Filters standaard open of samengevouwen is wanneer een gebruiker het rapport opent.
- Het deelvenster Filters helemaal verbergen of alleen bepaalde filters die rapportgebruikers niet mogen zien.
- De zichtbaarheid, en de uitgevouwen of samengevouwen status van het nieuwe deelvenster Filters beheren en er zelfs bladwijzers voor maken.
- Filters vergrendelen waarvan u niet wilt dat gebruikers deze bewerken.

Met de nieuwe filterervaring kunnen rapportgebruikers ook een visualisatie aanwijzen om een lijst van alle filters of slicers te zien die invloed hebben op deze visualisatie. Deze lijst kan overigens niet worden gewijzigd.

![Lijst met filters voor een visualisatie](media/power-bi-report-filter/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>De nieuwe filterfunctionaliteit aanzetten 

De nieuwe filterervaring is standaard ingeschakeld voor nieuwe rapporten. U kunt de nieuwe ervaring inschakelen voor bestaande rapporten in Power BI Desktop of de Power BI-service.

### <a name="turn-on-new-filters-for-an-existing-report-in-power-bi-desktop"></a>Nieuwe filters inschakelen voor een bestaand rapport in Power BI Desktop

1. Selecteer in een bestaand rapport in Power BI Desktop **Bestand** > **Opties en instellingen** > **Opties**
2. Selecteer in het navigatievenster onder **Huidig bestand** de optie **Rapportinstellingen**.
3. Selecteer onder **Rapportinstellingen** de optie **Het bijgewerkte deelvenster Filters inschakelen en filters weergeven in de visuele koptekst voor dit rapport**.

### <a name="turn-on-new-filters-for-an-existing-report-in-the-service"></a>Nieuwe filters inschakelen voor een bestaand rapport in de service

Als u het **nieuwe uiterlijk** in de Power BI-service hebt ingeschakeld ![Nieuw uiterlijk ingeschakeld](media/power-bi-report-filter/power-bi-new-look-on.png), wordt de nieuwe filterfunctionaliteit automatisch ingeschakeld. Lees meer over het [nieuwe uiterlijk in de Power BI-service](service-new-look.md).

Als u het nieuwe uiterlijk niet hebt ingeschakeld, kunt u nog steeds de nieuwe filterfunctionaliteit zien door de volgende stappen uit te voeren.

1. Open in de Power BI-service de inhoudslijst voor een werkruimte.
2. Zoek het rapport dat u wilt inschakelen, selecteer **Meer opties (...)** en selecteer vervolgens **Instellingen** voor dat rapport.

    ![Rapportinstellingen](media/power-bi-report-filter/power-bi-filter-options.png)

3. Selecteer onder **Rapportinstellingen** de optie **Het bijgewerkte deelvenster Filters inschakelen en filters weergeven in de visuele koptekst voor dit rapport**.

    ![Het deelvenster Bijgewerkte filters inschakelen](media/power-bi-report-filter/power-bi-service-filter-enable.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Filters voor een visual bekijken in Leesmodus

Wijs in de Leesmodus het filterpictogram voor een visual aan om een pop-upfilterlijst weer te geven met alle filters, slicers, enzovoort voor die visual. De indeling van de pop-upfilterlijst is gelijk aan de indeling van het deelvenster Filters. 

![Filters die invloed hebben op een visual](media/power-bi-report-filter/power-bi-filter-per-visual.png)

Dit zijn de typen filters die in deze weergave worden weergegeven: 
- Standaardfilters
- Slicers
- Kruislings markeren 
- Kruislings filteren
- Geavanceerde filters
- Top N-filters
- Relatieve datumfilters
- Synchroonslicers
- Opname-/uitsluitingsfilters
- Filters die via een URL zijn doorgegeven

## <a name="build-the-new-filters-pane"></a>Het nieuwe deelvenster Filters indelen

Nadat u het nieuwe deelvenster Filters hebt ingeschakeld, ziet u het rechts van de rapportpagina, standaard ingedeeld op basis van uw huidige rapportinstellingen. U gebruikt het nieuwe deelvenster Filters om in te stellen welke filters u wilt gebruiken en om bestaande filters in het nieuwe deelvenster bij te werken. In het nieuwe deelvenster Filters kunt u zien wat de gebruikers van uw rapport zien wanneer u het rapport publiceert. 

1. De standaardinstelling is dat rapportgebruikers het deelvenster Filters kunnen zien. Als u wilt dat gebruikers het venster niet zien, selecteert u het pictogram van een oog naast **Filters**.

    ![Pictogram van oog naast Filters](media/power-bi-report-filter/power-bi-filter-eye-icon.png)

2. Als u het nieuwe deelvenster Filters wilt gaan indelen, sleept u de gewenste velden als filters op het niveau van de visualisatie, de pagina of het rapport naar het nieuwe deelvenster Filters.

Wanneer u een visual toevoegt aan een rapportcanvas, wordt er automatisch voor elk veld in de visual een filter toegevoegd aan het deelvenster Filters. 

## <a name="hide-the-filters-pane-while-editing"></a>Het deelvenster Filters verbergen tijdens het bewerken

Power BI Desktop heeft een nieuw lint in de preview-versie. Met de wisselknop **Filters** op het tabblad **Weergave** kunt u het deelvenster Filters weergeven of verbergen. Deze functie is handig als u het deelvenster Filters niet gebruikt en u extra ruimte op het scherm nodig hebt. Hiermee wordt het deelvenster Filters uitgelijnd met de andere deelvensters die u kunt openen en sluiten, zoals de deelvensters Bladwijzers en Selectie. 

![Het deelvenster Filters verbergen of weergeven tijdens het bewerken](media/power-bi-report-filter/power-bi-filter-hide.png)

Met deze instelling wordt alleen het deelvenster Filters in Power BI Desktop verborgen. Als u het deelvenster Filters voor uw eindgebruikers wilt verbergen, selecteert u in plaats daarvan het pictogram van het **oog** naast **Filters**.

![Oogpictogram](media/power-bi-report-filter/power-bi-filter-eye.png) 

## <a name="lock-or-hide-filters"></a>Filters vergrendelen of verbergen

U kunt afzonderlijke filterkaarten vergrendelen of verbergen. Wanneer u een filter vergrendelt, kunnen de gebruikers van uw rapport het filter zien, maar niet wijzigen. Als u het filter verbergt, kunnen de gebruikers het ook niet zien. Het is handig om filterkaarten te verbergen als u opruimfilters wilt verbergen die onverwachte of null-waarden uitsluiten. 

- Schakel in het nieuwe deelvenster Filters de pictogrammen **Filter vergrendelen** of **Filter verbergen** in of uit op een filterkaart.

   ![Filters verbergen of vergrendelen](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

Als u deze instellingen in- of uitschakelt in het nieuwe deelvenster Filters, worden de wijzigingen direct doorgevoerd in het rapport. Verborgen filters worden niet weergegeven in de pop-upfilterlijst voor een visual.

U kunt de status van het nieuwe deelvenster Filters ook zo configureren dat het venster zich aanpast aan de bladwijzers in uw rapport. De zichtbaarheidsstatus en de status open of gesloten zijn allemaal vast te leggen.
 
## <a name="format-the-new-filters-pane"></a>Het nieuwe venster Filters indelen

Een belangrijk onderdeel van deze nieuwe ervaring is dat u de opmaak van het deelvenster Filters in overeenstemming kunt brengen met het uiterlijk van uw rapport. U kunt het deelvenster Filters verschillend indelen voor elke pagina in het rapport. Dit zijn de elementen die u kunt opmaken: 

- Achtergrondkleur
- Doorzichtigheid van achtergrond
- Rand wel of niet weergeven
- Randkleur
- Lettertype, kleur en tekstgrootte van titel en koptekst

U kunt deze elementen ook opmaken voor filterkaarten, afhankelijk van of deze zijn toegepast (ingesteld op iets) of beschikbaar zijn (uitgeschakeld): 

- Achtergrondkleur
- Doorzichtigheid van achtergrond
- Rand: in- of uitschakelen
- Randkleur
- Lettertype, kleur en tekstgrootte
- Kleur van het invoervak

### <a name="format-the-filters-pane-and-cards"></a>De indeling voor het deelvenster Filters en de filterkaarten instellen

1. In het rapport klikt u op het rapport zelf, of op de *achtergrond*, en vervolgens selecteert u **Indeling** in het venster **Visualisaties**. 
    U ziet opties voor het opmaken van de rapportpagina en de achtergrond, evenals het deelvenster Filters en de filterkaarten.

1. Vouw het **deelvenster Filters** uit om de kleur van de achtergrond, het pictogram en de linkerrand te kiezen om de rapportpagina op te maken.

    ![Deelvenster Filters uitvouwen](media/power-bi-report-filter/power-bi-format-filter-pane.png)

1. Vouw **Filterkaarten** uit om de kleuren en randen voor **Beschikbaar** en **Toegepast** in te stellen. Als u beschikbare en toegepaste kaarten verschillende kleuren geeft, is het duidelijk welke filters er zijn toegepast. 
  
    ![De Filterkaart uitvouwen](media/power-bi-report-filter/power-bi-format-filter-cards.png)

## <a name="theming-for-filters-pane"></a>Thema's voor het deelvenster Filters
U kunt nu de standaardinstellingen van het deelvenster Filters wijzigen met het themabestand. Hier volgt een voorbeeld van een codefragment voor een thema om u een beetje op weg te helpen:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filters-pane"></a>Het deelvenster Filters sorteren

De mogelijkheid om aangepast te sorteren maakt deel uit van de ervaring met het nieuwe deelvenster Filters. Makers van rapporten kunnen filters slepen en neerzetten om ze in elke gewenste volgorde te rangschikken.

![Sorteervolgorde van filters aanpassen](media/power-bi-report-filter/power-bi-filter-sort.gif)

Filters worden standaard op alfabetische volgorde gesorteerd. U start de modus voor aangepast sorteren door een filter naar een andere positie te slepen. U kunt filters alleen sorteren op het niveau waarop ze van toepassing zijn, dus op niveau van de visualisatie, de pagina of het rapport.

## <a name="improved-filters-pane-accessibility"></a>Verbeterde toegankelijkheid van deelvenster Filters

We hebben de toetsenbordnavigatie voor het nieuwe deelvenster Filters verbeterd. U kunt met de Tab-toets door de onderdelen van het deelvenster Filters lopen en de contexttoets op het toetsenbord of Shift + F10 gebruiken om het contextmenu te openen.

![Toegankelijkheid van deelvenster Filters](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Namen van filters wijzigen
Als u het deelvenster Filters bewerkt, kunt u dubbelklikken op de titel om deze te bewerken. Dit is handig als u de filterkaart wilt bijwerken om deze meer zinvol te maken voor uw eindgebruikers. Als u de naam van de filterkaart wijzigt, heeft dit *geen* gevolgen voor de weergavenaam van het veld in de lijst met velden. U verandert alleen de weergavenaam die wordt gebruikt op de filterkaart.

![De naam van een filter wijzigen](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="filters-pane-search"></a>Zoeken in het deelvenster Filters

Met de functie voor zoeken in het deelvenster Filters kunt u op titel zoeken in uw filterkaarten. Deze functie is handig als u verschillende filterkaarten in het deelvenster Filters hebt en u hulp nodig hebt bij het vinden van belangrijke items.

![Een filter zoeken](media/power-bi-report-filter/power-bi-filter-search.png)

U kunt ook het zoekvak opmaken, net zoals u de andere elementen van het deelvenster Filters kunt opmaken.

![Het zoekvak opmaken](media/power-bi-report-filter/power-bi-filter-format-search.png)

Hoewel deze functie van het deelvenster Filters standaard is ingeschakeld, kunt u er ook voor kiezen om deze in of uit te schakelen via **Zoeken in het deelvenster Filters inschakelen** in de rapportinstellingen van het dialoogvenster Opties.

![Zoekfunctie in- of uitschakelen](media/power-bi-report-filter/power-bi-enable-search-filter.png)

## <a name="restrict-changes-to-filter-type"></a>Wijzigingen van filtertype beperken

In het gedeelte Filterervaring van de rapportinstellingen kunt u een optie kiezen om te bepalen of gebruikers het filtertype kunnen wijzigen.

![Wijzigen van filtertype beperken](media/power-bi-report-filter/power-bi-enable-change-filter-type.png)

## <a name="next-steps"></a>Volgende stappen

Probeer de nieuwe filterervaring eens uit. Geef ons feedback over deze functie en vertel ons hoe we deze kunnen blijven verbeteren. Ga hiervoor naar de [site Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi). 

- [How to use report filters](consumer/end-user-report-filter.md) (Rapportfilters gebruiken)
- [Filters en markeren in rapporten](power-bi-reports-filters-and-highlighting.md)
- [Verschillende soorten filters in Power BI](power-bi-report-filter-types.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

