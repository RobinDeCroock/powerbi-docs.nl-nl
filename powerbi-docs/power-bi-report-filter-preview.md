---
title: De nieuwe filterervaring in Power BI-rapporten (preview)
description: Filters in Power BI krijgen nieuwe functionaliteit en een nieuw ontwerp.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0a9e4986ae2f686eb8a8fd2d9fa07b169661ce60
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65853480"
---
# <a name="the-new-filter-experience-in-power-bi-reports-preview"></a>De nieuwe filterervaring in Power BI-rapporten (preview)

Filters in Power BI hebben de nieuwe functionaliteit en een nieuw ontwerp. Wanneer u zich aan voor het nieuwe filter-ervaring meldt, kunt u het deelvenster Filters zodat het eruitziet als de rest van het rapport opmaken. U kunt vergrendelen en zelfs filters verbergen. Bij het ontwerpen van uw rapport, ziet u niet meer het oude deelvenster Filters in het deelvenster visualisaties. U kunt alle uw filter bewerken en de opmaak in één deelvenster Filters doen. 

![Nieuwe filterfunctionaliteit](media/power-bi-report-filter-preview/power-bi-filter-reading.png)

> [!NOTE]
> De nieuwe filterervaring is in preview. Nieuwe builds kunnen opmaak overschrijven die u al hebt ingesteld.

Als de rapportontwerper van een, moet u dit is wat u kunt doen in het nieuwe deelvenster voor één Filters:

- Velden toevoegen en verwijderen om te filteren op. 
- Wijzig de filterstatus.
- Indeling en het deelvenster Filters aanpassen zodat het onderdeel van uw rapport werkt.
- Definiëren of het venster Filters standaard open of samengevouwen is wanneer een gebruiker het rapport opent.
- De volledige het deelvenster Filters of specifieke filters die u niet wilt dat gebruikers om te zien verbergen.
- Controle en zelfs bladwijzer de zichtbaarheid, open en status van het nieuwe deelvenster Filters samengevouwen.
- Filters vergrendelen waarvan u niet wilt dat gebruikers deze bewerken.

Met de nieuwe ervaring voor het filter kunnen gebruikers ook de muisaanwijzer over een visueel element voor een alleen-lezen-overzicht van alle filters en slicers die betrekking hebben op deze visual.

![Lijst met filters voor een visueel element](media/power-bi-report-filter-preview/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>De nieuwe filterfunctionaliteit aanzetten 

U schakelt de nieuwe ervaring in Power BI Desktop in. Vervolgens kunt u daar of in de Power BI-service filters bewerken (https://app.powerbi.com). Omdat deze nieuwe filterervaring in preview is, moet u deze eerst inschakelen in Power BI Desktop. Als u een rapport begint te maken in de Power BI-service, kan het geen nieuwe filters hebben.

### <a name="turn-on-new-filters-for-all-new-reports"></a>Nieuw filter inschakelen voor alle nieuwe rapporten

1. Selecteer in Power BI Desktop **Bestand** > **Opties en instellingen** > **Opties** > **Preview-functies** en selecteer vervolgens het selectievakje **Nieuwe filterervaring**. 
2. Start Power BI Desktop opnieuw op om de nieuwe filterervaring in alle nieuwe rapporten te kunnen zien.

Nadat u Power BI Desktop opnieuw hebt opgestart, is het standaard ingeschakeld voor alle nieuwe rapporten die u maakt.  

### <a name="turn-on-new-filters-for-an-existing-report"></a>Nieuwe filters inschakelen voor een bestaand rapport

U kunt de nieuwe filters ook voor bestaande rapporten inschakelen.

1. Selecteer in een bestaand rapport in Power BI Desktop **Bestand** > **Opties en instellingen** > **Opties**
2. In de linkernavigatiebalk onder **huidige bestand**, selecteer **rapporteren instellingen**.
3. Onder **filteren ervaring**, selecteer **inschakelen van de bijgewerkte filterdeelvenster en filters weergeven in de visuele kopteksten voor dit rapport**.

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Filters voor een visual bekijken in Leesmodus

In de Leesmodus kunt u uw muisaanwijzer over het filterpictogram een visual bewegen en een pop-upvenster bekijken met alle filters, slicers, enz. die invloed hebben op die visual. De opmaak van het pop-upvenster is hetzelfde als de Filters deelvenster opmaak. 

![Filters die invloed hebben op een visual](media/power-bi-report-filter-preview/power-bi-filter-per-visual.png)

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

## <a name="build-the-new-filters-pane"></a>Het nieuwe deelvenster Filters maken

Nadat u het nieuwe deelvenster Filters inschakelt, wordt het aan de rechterkant van de rapportpagina, opgemaakt standaard op basis van de huidige rapportinstellingen voor het. Het nieuwe deelvenster Filters kunt u configureren welke filters om op te nemen en om bij te werken van de bestaande filters in het nieuwe deelvenster. Het nieuwe deelvenster Filters ziet u wat uw gebruikers zien wanneer u uw rapport publiceert. 

1. Standaard ziet uw gebruikers het deelvenster Filters. Als u niet laten zien wilt, selecteert u het oogpictogram naast **Filters**.

    ![Oogpictogram voor Power BI-filter](media/power-bi-report-filter-preview/power-bi-filter-eye.png)

2. Voor het starten van het bouwen van uw nieuwe deelvenster Filters, sleept u velden van belang als visual, pagina naar het nieuwe deelvenster Filters of filters op rapportniveau.

Wanneer u een visueel element aan een rapportcanvas toevoegt, Power BI automatisch een filter toegevoegd aan het deelvenster FIlters voor elk veld in het visuele element. 

## <a name="lock-or-hide-filters"></a>Filters vergrendelen of verbergen

U kunt afzonderlijke filterkaarten vergrendelen of verbergen. Wanneer u een filter vergrendelt, kunnen de gebruikers van uw rapport het filter zien, maar niet wijzigen. Als u het filter verbergt, kunnen de gebruikers het ook niet zien. Het is handig om filterkaarten te verbergen als u opruimfilters wilt verbergen die onverwachte of null-waarden uitsluiten. 

- In het nieuwe deelvenster Filters, selecteert of wist u de **Zamknout filtr** of **verbergen filter** pictogrammen in een filterkaart.

   ![Filters verbergen of vergrendelen](media/power-bi-report-filter-preview/power-bi-filter-lock-hide.png)

Als u deze instellingen in- en uitschakelen in het nieuwe deelvenster Filters inschakelt, ziet u de wijzigingen zijn doorgevoerd in het rapport. Verborgen filters worden niet weergegeven in pop-upfilters voor een visual.

U kunt ook de nieuwe status van de deelvenster Filters om de stroom met uw rapport bladwijzers configureren. De zichtbaarheidsstatus en de status open of gesloten zijn allemaal vast te leggen.
 
## <a name="format-the-new-filters-pane"></a>Het nieuwe venster Filters indelen

Een groot deel van deze nieuwe ervaring is dat u het deelvenster Filters zodat deze overeenkomt met het uiterlijk van uw rapport kunt opmaken. U kunt het deelvenster Filters anders voor elke pagina in het rapport opmaken. Dit zijn de elementen die u kunt opmaken: 

- Achtergrondkleur
- Doorzichtigheid van achtergrond
- Rand in- of uitschakelen
- Randkleur
- Titel en koptekst lettertype, kleur en grootte

U kunt deze elementen ook opmaken voor filterkaarten, afhankelijk van of deze zijn toegepast (ingesteld op iets) of beschikbaar zijn (uitgeschakeld): 

- Achtergrondkleur
- Doorzichtigheid van achtergrond
- Rand: in- of uitschakelen
- Randkleur
- Lettertype, kleur en tekstgrootte
- Kleur van het invoervak

### <a name="format-the-filters-pane-and-cards"></a>Het deelvenster Filters en de kaarten opmaken

1. In het rapport klikt u op het rapport zelf, of op de *achtergrond*, en vervolgens selecteert u **Indeling** in het venster **Visualisaties**. 
    Ziet u opties voor het opmaken van de rapportpagina, de achtergrond, en ook het deelvenster Filters en Filter kaarten.

    ![Het pictogram Indeling selecteren](media/power-bi-report-filter-preview/power-bi-filter-format.png)    

1. Vouw het **Filtervenster** uit om de kleur van de achtergrond, het pictogram en de linkerrand te kiezen om de rapportpagina op te maken.

    ![Het venster Filters uitvouwen](media/power-bi-report-filter-preview/power-bi-filter-format-pane-font.png)

1. Vouw **Filterkaarten** uit om de kleuren en randen voor **Beschikbaar** en **Toegepast** in te stellen. Als u beschikbare en toegepaste kaarten verschillende kleuren geeft, is het duidelijk welke filters er zijn toegepast. 
  
    ![De Filterkaart uitvouwen](media/power-bi-report-filter-preview/power-bi-filter-format-card-font.png)

## <a name="theming-for-filter-pane"></a>Thema's voor het filterdeelvenster
U kunt nu de standaardinstellingen van het filterdeelvenster wijzigen met het themabestand. Hier volgt een voorbeeld-thema-codefragment aan de slag te gaan:

 
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

## <a name="sort-the-filter-pane"></a>Het filterdeelvenster sorteren

Aangepaste sorteren functionaliteit maakt deel uit van de nieuwe filter deelvenster ervaring. Makers van rapporten kunnen slepen en neerzetten filters te rangschikken in de volgorde waarin die ze willen.

![Sorteervolgorde filter opnieuw rangschikken](media/power-bi-report-filter-preview/power-bi-filter-sort.gif)

De standaardsorteervolgorde wordt op alfabetische volgorde voor filters. Voor het starten van aangepaste sorteren modus, sleept u een filter naar de nieuwe positie. U kunt alleen filters op niveau van de die ze van toepassing op, bijvoorbeeld een filter op niveau, op paginaniveau en rapportniveau sorteren.

## <a name="filters-pane-scaling"></a>Schalen van het deelvenster filters

Het nieuwe deelvenster Filters kan worden geschaald met de rapportpagina en visuele elementen, zodat de rapportpagina en gefilterd deelvenster verblijf in verhouding met elkaar.

## <a name="improved-filters-pane-accessibility"></a>Verbeterde Filters deelvenster Toegankelijkheid

We hebben de navigatie voor het nieuwe deelvenster Filters met het toetsenbord verbeterd. U kunt elk onderdeel van het deelvenster Filters met de tab en gebruik van de Contextsleutel op het toetsenbord of Shift + F10 om te open het contextmenu.

![Filters deelvenster Toegankelijkheid](media/power-bi-report-filter-preview/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Wijzig de naam van filters
Als u het deelvenster Filters bewerkt, kunt u dubbelklikken op de titel om deze te bewerken. Wijzigen van de naam is handig als u wilt bijwerken van de filterkaart als u wilt meer zinvol zijn voor uw eindgebruikers. Houd er rekening mee dat naam van de filterkaart heeft *niet* Wijzig de naam van de weergavenaam van het veld in de lijst met velden. Wordt alleen de weergavenaam die wordt gebruikt in de filterkaart gewijzigd.

![Wijzig de naam van een filter](media/power-bi-report-filter-preview/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Wijzigingen om te filteren type beperken

Onder de Filtering optreden sectie van de rapportinstellingen die u een optie om te bepalen hebt of gebruikers van het filtertype wijzigen kunnen.

![Wisselende filtertype beperken](media/power-bi-report-filter-preview/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Volgende stappen

Probeer de nieuwe filterervaring eens uit. Geef ons uw feedback voor deze functie en hoe we verder kunnen blijven verbeteren, op de [Power BI ideeën site](https://ideas.powerbi.com/forums/265200-power-bi). 

- [How to use report filters](consumer/end-user-report-filter.md) (Rapportfilters gebruiken)
- [Filters en markeren in rapporten](power-bi-reports-filters-and-highlighting.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

