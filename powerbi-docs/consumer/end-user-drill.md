---
title: Inzoomen en uitzoomen in een visual
description: In dit artikel wordt beschreven hoe u kunt inzoomen op een visual in de Microsoft Power BI-service.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/21/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 17fe24957dbcccd7038ea34566a8db8f5684cb18
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721519"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Zoommodus voor een visual in Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


In dit artikel wordt beschreven hoe u kunt inzoomen op een visual in de Microsoft Power BI-service. Door uw gegevenspunten in en uit te zoomen kunt u diepgaande details over uw gegevens verkennen. 

## <a name="drill-requires-a-hierarchy"></a>Voor zoomen is een hiërarchie vereist

Wanneer een visueel element een hiërarchie heeft, kunt u inzoomen om extra details te onthullen. U kunt bijvoorbeeld een visual hebben die kijkt naar het aantal Olympische medailles door een hiërarchie bestaande uit sport, discipline en gebeurtenis. Standaard zou de visual het aantal medailles weergeven per sport: gymnastiek, skiën, watersport, enzovoort. Maar omdat deze een hiërarchie bevat, zou het selecteren van één van de visuele elementen (zoals een balk, lijn of bel) een steeds gedetailleerder beeld weergeven. Het selecteren van het element **watersport** zou u de gegevens voor zwemmen, duiken en waterpolo laten zien.  Het selecteren van het element **duiken** zou u de details voor duikplank, platform en gesynchroniseerde duikgebeurtenissen laten zien.

Datums zijn een uniek type hiërarchie.  *Ontwerpers* van rapporten voegen vaak datumhiërarchieën toe aan visuals. Een algemene datumhiërarchie bevat jaar, kwartaal, maand en dag. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Uitzoeken op welke visuals kan worden ingezoomd
Weet u niet zeker welke Power BI-visuals een hiërarchie bevatten? Beweeg de muisaanwijzer over een visual. Als u bovenaan een combinatie van deze besturingselementen voor een detailanalyse ziet, heeft uw visual een hiërarchie.

![Schermopname van de pictogrammen voor het inzoomen.](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>Meer informatie over in- en uitzoomen

In dit voorbeeld gebruiken we een treemap met een hiërarchie die bestaat uit een gebied, plaats, postcode en archiefnaam. De treemap, voorafgaand aan het inzoomen, zoekt per gebied naar het totale aantal verkochte eenheden van dit jaar. Gebied is het hoogste niveau van de hiërarchie.

![Schermopname van de treemap en de bijbehorende filters.](./media/end-user-drill/power-bi-treemap.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Twee manieren om toegang te krijgen tot de zoomfuncties

U hebt twee manieren om toegang te krijgen tot de functies voor inzoomen, uitzoomen en uitvouwen voor visuals met hiërarchieën. Probeer ze allebei en gebruik de optie die het beste bij u past.

- Eerste manier: beweeg de muisaanwijzer over een visual om de pictogrammen te zien en te gebruiken. Schakel eerst inzoomen in door de pijl-omlaag te selecteren. Aan de grijze achtergrond kunt u zien dat inzoomen actief is.   

    ![Schermopname van het voorbeeld van aanwijzen.](./media/end-user-drill/power-bi-drill-hover.png)

- Tweede manier: klik met de rechtermuisknop op een visual om het menu weer te geven en te gebruiken.

    ![Schermopname van het voorbeeld van klikken met de rechtermuisknop.](./media/end-user-drill/power-bi-drill-action-menu.png)



## <a name="drill-pathways"></a>Paden voor inzoomen

### <a name="drill-down-all-fields-at-once"></a>Inzoomen op alle velden tegelijk
![Het pictogram Inzoomen](./media/end-user-drill/power-bi-drill-icon3.png)

U hebt verschillende manieren om op uw visual in te zoomen. Als u het pictogram met de dubbele pijl ![selecteert om alle niveaus tegelijk in te zoomen](./media/end-user-drill/power-bi-drill-icon3.png), gaat u naar het volgende niveau in de hiërarchie. Als u op zoek bent naar het niveau **Territory** voor Kentucky en Tennessee, kunt u inzoomen op plaatsniveau voor beide staten, vervolgens postcodeniveau voor beide staten en, ten slotte, het archiefnaamniveau voor beide staten. Elke stap in het pad toont u nieuwe informatie.

![Diagram met het pad voor zoomen](./media/end-user-drill/power-bi-drill-path.png)

Het pictogram voor uitzoomen selecteren ![Het pictogram Uitzoomen](./media/end-user-drill/power-bi-drill-icon5.png) totdat u terugkeert naar ‘Totaal aantal eenheden dit jaar per gebied’.

### <a name="expand-all-fields-at-once"></a>Alle velden in één keer uitvouwen
![Het pictogram uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png)

Met **Uitvouwen** voegt u een extra hiërarchieniveau toe aan de huidige weergave. Als u bijvoorbeeld naar het niveau **Gebied** kijkt, kunt u alle huidige bladeren in de structuur in één keer uitvouwen.  Met de eerste zoombewerking voegt u plaatsgegevens toe voor zowel **KY** als **TN**. Met de volgende bewerking worden postcodegegevens toegevoegd voor zowel **KY** als **TN**, en blijven de plaatsgegevens zichtbaar. Elke stap in het pad toont u dezelfde informatie en voegt één niveau aan nieuwe informatie toe.

![Diagram met het pad voor uitvouwen](./media/end-user-drill/power-bi-expand-path.png)


### <a name="drill-down-one-field-at-a-time"></a>Inzoomen op één veld tegelijk


1. Selecteer het inzoompictogram om dit in te schakelen ![Schermopname van het inzoompictogram ingeschakeld.](./media/end-user-drill/power-bi-drill-icon2.png).

    Nu hebt u de optie om op **één veld tegelijk** in te zoomen door een visueel element te selecteren. Voorbeelden van visuele elementen zijn: balk, bel en bladknooppunt.

    ![Schermopname van de visual met een pijl die wijst naar het inzoompictogram dat is ingeschakeld.](media/end-user-drill/power-bi-select-drill-icon.png)

    Als u inzoomen niet inschakelt, kunt u een visueel element (zoals een balk, bel of bladknooppunt) niet inzoomen als u het selecteert. In plaats hiervan worden de andere grafieken op de rapportpagina kruislings gefilterd.

1. Selecteer het bladknooppunt voor **TN**. In de treemap worden nu alle steden en gebieden in Tennessee weergegeven waarin een winkel is gevestigd.

    ![Schermopname van de treemap waarin alleen de gegevens voor TN worden weergegeven.](media/end-user-drill/power-bi-drill-down-first.png)

1. Vanaf dit punt kunt u:

    1. Verder inzoomen in Tennessee.

    1. Inzoomen in een bepaalde stad in Tennessee.

    1. Vouw in plaats daarvan uit.

    We blijven voor dit moment inzoomen op één veld tegelijk.  Selecteer **Knoxville, TN**. In de treemap wordt nu de postcode voor uw winkel in Knoxville weergegeven.

    ![Schermopname van de treemap waarin de postcode 37919 wordt weergegeven.](media/end-user-drill/power-bi-drill-twice.png)

    U ziet dat de titel wordt gewijzigd tijdens het in- en uitzoomen.

    We zoomen nog even in op een ander veld. Selecteer postcode **37919** en zoom in op winkelnaam (Store Name). 

    ![Schermopname van de treemap met de gegevens voor Knoxville Lindseys.](media/end-user-drill/power-bi-drill-last.png)    

    Voor deze specifieke gegevens is het inzoomen van alle niveaus mogelijk niet interessant. Laten we eens kijken of uitbreiden zinvol is.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Alle velden tegelijk en één veld tegelijk uitvouwen

Het gebruik van een treemap die alleen een postcode of winkelnaam laat zien, is niet informatief.  Laten we dus één niveau in de hiërarchie omlaag *uitvouwen*.  

1. Zoom eerst uit naar het niveau van postcodes.     
1. Selecteer met de treemap actief het pictogram *omlaag uitvouwen* ![Schermopname van het pictogram voor omlaag uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png). In de treemap worden nu twee niveaus van de hiërarchie weergegeven: postcode en winkelnaam.

    ![Schermopname van de treemap waarin de postcode en winkelnaam worden weergegeven](./media/end-user-drill/power-bi-expand.png)

1. Als u alle vier de hiërarchieniveaus met gegevens voor Tennessee wilt zien, selecteert u de pijl voor uitzoomen totdat u het tweede niveau bereikt, **Totaal aantal eenheden dit jaar per gebied en plaats**.

    ![Schermopname van de treemap waarin alle gegevens voor TN worden weergegeven.](media/end-user-drill/power-bi-expand-second.png)

1. Zorg ervoor dat inzoomen nog steeds is ingeschakeld ![Schermopname van het inzoompictogram ingeschakeld.](./media/end-user-drill/power-bi-drill-icon2.png) en selecteer het pictogram *omlaag uitvouwen* ![Schermopname van het pictogram voor omlaag uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png). In uw treemap wordt nu hetzelfde aantal bladknooppunten (vakken) weergegeven, maar elk bladknooppunt bevat extra details. In plaats van alleen plaats en staat wordt nu ook de postcode weergegeven.

    ![Schermopname van de visual waarin de plaats, staat en postcode wordt weergegeven.](./media/end-user-drill/power-bi-expand-third.png)

1. Selecteer het pictogram voor *omlaag uitvouwen* nog één keer om alle vier hiërarchieniveaus met details voor Tennessee in de treemap weer te geven. Beweeg de muisaanwijzer over een bladknooppunt voor nog meer informatie.

    ![Schermopname van de treemap waarin knopinfo wordt weergegeven met bladknooppuntgegevens.](./media/end-user-drill/power-bi-expand-final.png)

## <a name="show-the-data-as-you-drill"></a>De gegevens weergeven tijdens het inzoomen
Gebruik **Als tabel weergeven** om een kijkje achter de schermen te nemen. Telkens wanneer u inzoomt of uitvouwt, laat **Als tabel weergeven** zien welke gegevens worden gebruikt om de visual op te bouwen. Dit kan u helpen inzicht te krijgen in de manier waarop hiërarchieën, zoomen en uitvouwen samen werken om visuals op te bouwen. 

Selecteer in de rechterbovenhoek **Meer opties** (...) en selecteer vervolgens **Als tabel weergeven**. 

![Schermopname van het menu met beletseltekens.](./media/end-user-drill/power-bi-more-actions.png)

De treemap wordt geopend in Power BI en vult het hele canvas. De gegevens waaruit de treemap is opgebouwd, worden weergegeven onder de visual. 

![Schermopname van treemap met gegevenstabel die eronder wordt weergegeven.](./media/end-user-drill/power-bi-show-table.png)

Met alleen de visual op het canvas gaat u verder met inzoomen. Kijk naar de gegevens in de tabel en u ziet dat deze overeenkomen met de gegevens die worden gebruikt om de treemap te maken. In de volgende tabel ziet u de resultaten van het inzoomen op alle velden in één keer van gebied naar archiefnaam. De eerste tabel vertegenwoordigt het hoogste niveau van de hiërarchie, de treemap met twee bladeren, één voor **KY** en één voor **TN**. De volgende drie tabellen vertegenwoordigen de gegevens van de treemap wanneer u alle niveaus tegelijk inzoomt; van gebied naar plaats naar postcode en naar winkelnaam.


![Schermopname van het weergeven van gegevens voor alle vier de niveaus van inzoomen.](./media/end-user-drill/power-bi-show-data.png)

Merk op dat de totalen hetzelfde zijn voor **Plaats**, **Postcode** en **Naam**. Dit zal niet altijd het geval zijn.  Maar voor deze gegevens is er slechts één archief in elke postcode en in elke plaats.  



## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
- Standaard wordt met zoomen niet op andere visuals in een rapport gefilterd. De rapportontwerper kan dit standaard gedrag echter wijzigen. Controleer tijdens het inzoomen of de andere visuels op de pagina kruislings worden gefilterd of kruislings worden gemarkeerd.

- Als u een rapport wilt weergeven dat met u is gedeeld, hebt u een Power BI Pro- of een Premium-licentie nodig of moet het rapport zijn opgeslagen in de Power BI Premium-capaciteit. [Welke licentie heb ik?](end-user-license.md)


## <a name="next-steps"></a>Volgende stappen

[Visuals in Power BI-rapporten](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporten](end-user-reports.md)

[Power BI - basisconcepten](end-user-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
