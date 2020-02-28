---
title: Inzoomen en uitzoomen in een visual
description: In dit artikel wordt beschreven hoe u kunt inzoomen op een visual in de Microsoft Power BI-service.
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7c0c08e8056232fa7c60b20faf48b0137a19bc5f
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496426"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Zoommodus voor een visual in Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

In dit artikel wordt beschreven hoe u kunt inzoomen op een visual in de Microsoft Power BI-service. Door uw gegevenspunten in en uit te zoomen kunt u diepgaande details over uw gegevens verkennen. 

## <a name="drill-requires-a-hierarchy"></a>Voor zoomen is een hiërarchie vereist

Wanneer een visueel element een hiërarchie heeft, kunt u inzoomen om extra details te onthullen. U kunt bijvoorbeeld een visual hebben die kijkt naar het aantal Olympische medailles door een hiërarchie bestaande uit sport, discipline en gebeurtenis. Standaard zou de visual het aantal medailles weergeven per sport: gymnastiek, skiën, watersport, enzovoort. Maar omdat deze een hiërarchie bevat, zou het selecteren van één van de visuele elementen (zoals een balk, lijn of bel) een steeds gedetailleerder beeld weergeven. Het selecteren van het element **watersport** zou u de gegevens voor zwemmen, duiken en waterpolo laten zien.  Het selecteren van het element **duiken** zou u de details voor duikplank, platform en gesynchroniseerde duikgebeurtenissen laten zien.

Datums zijn een uniek type hiërarchie.  Rapportontwerpers voegen vaak datumhiërarchieën toe aan visuals. Een algemene datumhiërarchie bevat jaar, kwartaal, maand en dag. 

## <a name="figure-out-which-visuals-can-be-drilled"></a>Uitzoeken op welke visuals kan worden ingezoomd
Weet u niet zeker welke Power BI-visuals een hiërarchie bevatten? Beweeg de muisaanwijzer over een visual. Als u bovenaan een combinatie van deze besturingselementen voor een detailanalyse ziet, heeft uw visual een hiërarchie.

![Schermopname van de pictogrammen voor het inzoomen.](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>Meer informatie over in- en uitzoomen

In dit voorbeeld gebruiken we een treemap met een hiërarchie die bestaat uit een gebied, plaats, postcode en archiefnaam. De treemap, voorafgaand aan het inzoomen, zoekt per gebied naar het totale aantal verkochte eenheden van dit jaar. 

![Schermopname van de treemap en de bijbehorende filters.](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>Twee manieren om toegang te krijgen tot de zoomfuncties

U hebt twee manieren om toegang te krijgen tot de functies voor inzoomen, uitzoomen en uitvouwen voor visuals met hiërarchieën. Probeer ze allebei en gebruik de optie die het beste bij u past.

- Eerste manier: beweeg de muisaanwijzer over een visual om de pictogrammen te zien en te gebruiken.  

    ![Schermopname van het voorbeeld van aanwijzen.](./media/end-user-drill/power-bi-hover.png)

- Tweede manier: klik met de rechtermuisknop op een visual om het menu weer te geven en te gebruiken.

    ![Schermopname van het voorbeeld van klikken met de rechtermuisknop.](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>Paden voor inzoomen

### <a name="drill-down-all-fields-at-once"></a>Inzoomen op alle velden tegelijk
![Het pictogram inzoomen](./media/end-user-drill/power-bi-drill-icon3.png)

U hebt verschillende manieren om op uw visual in te zoomen. Door het pictogram inzoomen te selecteren, gaat u naar het volgende niveau in de hiërarchie. Als u op zoek bent naar het niveau **Territory** voor Kentucky en Tennessee, kunt u inzoomen op plaatsniveau voor beide staten, vervolgens postcodeniveau voor beide staten en, ten slotte, het archiefnaamniveau voor beide staten. Elke stap in het pad toont u nieuwe informatie.

![Diagram met het pad voor zoomen](./media/end-user-drill/power-bi-drill-path.png)

Het pictogram voor uitzoomen selecteren ![Pictogram uitzoomen](./media/end-user-drill/power-bi-drill-icon5.png) totdat u terugkeert naar ‘Totaal aantal eenheden dit jaar per gebied’.

### <a name="expand-all-fields-at-once"></a>Alle velden in één keer uitvouwen
![Het pictogram uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png)

Met **Uitvouwen** voegt u een extra hiërarchieniveau toe aan de huidige weergave. Dus als u naar het niveau **Gebied** kijkt, kunt u dit uitvouwen en informatie over plaats, postcode en naam toevoegen de treemap. Elke stap in het pad toont u dezelfde informatie en voegt één niveau aan nieuwe informatie toe.

![Diagram met het pad voor uitvouwen](./media/end-user-drill/power-bi-expand-path.png)

U kunt er ook voor kiezen om op één veld per keer in te zoomen of uit te vouwen.


### <a name="drill-down-one-field-at-a-time"></a>Inzoomen op één veld tegelijk


1. Selecteer het inzoompictogram om dit in te schakelen ![Schermopname van het inzoompictogram ingeschakeld.](./media/end-user-drill/power-bi-drill-icon2.png).

    Nu hebt u de optie om op **één veld tegelijk** in te zoomen door een visueel element te selecteren. Voorbeelden van visuele elementen zijn: balk, bel en bladknooppunt.

    ![Schermopname van de visual met een pijl die wijst naar het inzoompictogram dat is ingeschakeld.](media/end-user-drill/power-bi-drill-icon-selected.png)

    Als u inzoomen niet inschakelt, kunt u een visueel element (zoals een balk, bel of bladknooppunt) niet inzoomen als u het selecteert. In plaats hiervan worden de andere grafieken op de rapportpagina kruislings gefilterd.

1. Selecteer het bladknooppunt voor **TN**. In de treemap worden nu alle steden en gebieden in Tennessee weergegeven waarin een winkel is gevestigd.

    ![Schermopname van de treemap waarin alleen de gegevens voor TN worden weergegeven.](media/end-user-drill/power-bi-drill-down-one.png)

1. Vanaf dit punt kunt u:

    1. Verder inzoomen in Tennessee.

    1. Inzoomen in een bepaalde stad in Tennessee.

    1. Vouw in plaats daarvan uit.

    We blijven voor dit moment inzoomen op één veld tegelijk.  Selecteer **Knoxville, TN**. In de treemap wordt nu de postcode voor uw winkel in Knoxville weergegeven.

    ![Schermopname van de treemap waarin de postcode 37919 wordt weergegeven.](media/end-user-drill/power-bi-drill-two.png)

    U ziet dat de titel wordt gewijzigd tijdens het in- en uitzoomen.

### <a name="expand-all-and-expand-one-field-at-a-time"></a>Alle velden tegelijk en één veld tegelijk uitvouwen

Het gebruik van een treemap die alleen een postcode laat zien, is niet informatief.  Laten we dus één niveau in de hiërarchie omlaag *uitvouwen*.  

1. Selecteer met de treemap actief het pictogram *omlaag uitvouwen*![Schermopname van het pictogram voor omlaag uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png). In de treemap worden nu twee niveaus van de hiërarchie weergegeven: postcode en winkelnaam.

    ![Schermopname van de treemap waarin de postcode en winkelnaam worden weergegeven](./media/end-user-drill/power-bi-expand-one.png)

1. Als u alle vier hiërarchieniveaus met gegevens voor Tennessee wilt zien, selecteert u de pijl voor uitzoomen totdat u het tweede niveau van de treemap bereikt, **Totaal aantal eenheden dit jaar per gebied en plaats**.

    ![Schermopname van de treemap waarin alle gegevens voor TN worden weergegeven.](media/end-user-drill/power-bi-expand-two.png)

1. Zorg ervoor dat inzoomen nog steeds is ingeschakeld ![Schermopname van het inzoompictogram ingeschakeld.](./media/end-user-drill/power-bi-drill-icon2.png) en selecteer het pictogram *omlaag uitvouwen*![Schermopname van het pictogram voor omlaag uitvouwen](./media/end-user-drill/power-bi-drill-icon6.png). In uw treemap wordt nu hetzelfde aantal bladknooppunten (vakken) weergegeven, maar elk bladknooppunt bevat extra details. In plaats van alleen plaats en staat wordt nu ook de postcode weergegeven.

    ![Schermopname van de visual waarin de plaats, staat en postcode wordt weergegeven.](./media/end-user-drill/power-bi-expand-three.png)

1. Selecteer het pictogram voor *omlaag uitvouwen* nog één keer om alle vier hiërarchieniveaus met details voor Tennessee in de treemap weer te geven. Beweeg de muisaanwijzer over een bladknooppunt voor nog meer informatie.

    ![Schermopname van de treemap waarin knopinfo wordt weergegeven met bladknooppuntgegevens.](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>De gegevens weergeven tijdens het inzoomen
Gebruik **Gegevens weergeven** om een kijkje achter de schermen te krijgen. Telkens wanneer u inzoomt of uitvouwt, laat **Gegevens weergeven** zien welke gegevens worden gebruikt om de visual op te bouwen. Dit kan u helpen inzicht te krijgen in de manier waarop hiërarchieën, zoomen en uitvouwen samen werken om visuals op te bouwen. 

Selecteer in de rechterbovenhoek **Meer opties** (...) en selecteer vervolgens **Gegevens weergeven**. 

![Schermopname van het menu met beletseltekens.](./media/end-user-drill/power-bi-ellipses.png)

In de volgende tabel ziet u de resultaten van het inzoomen op alle velden in één keer van gebied naar archiefnaam.  


![Schermopname van het weergeven van gegevens voor alle vier de niveaus van inzoomen.](./media/end-user-drill/power-bi-show-data.png)

Merk op dat de totalen hetzelfde zijn voor **Plaats**, **Postcode** en **Naam**. Dit zal niet altijd het geval zijn.  Maar voor deze gegevens is er slechts één archief in elke postcode en in elke plaats.  



## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
- Standaard wordt met zoomen niet op andere visuals in een rapport gefilterd. De rapportontwerper kan dit standaard gedrag echter wijzigen. Controleer tijdens het inzoomen of de andere visuels op de pagina kruislings worden gefilterd of kruislings worden gemarkeerd.

- Als u een rapport wilt weergeven dat met u is gedeeld, hebt u een Power BI Pro- of Power BI Premium-licentie nodig. [Welke licentie heb ik?](end-user-license.md)


## <a name="next-steps"></a>Volgende stappen

[Visuals in Power BI-rapporten](../visuals/power-bi-report-visualizations.md)

[Power BI-rapporten](end-user-reports.md)

[Power BI - basisconcepten](end-user-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
