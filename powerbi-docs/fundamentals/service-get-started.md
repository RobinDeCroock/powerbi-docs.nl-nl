---
title: 'Zelfstudie: Aan de slag met de Power BI-service'
description: Aan de slag met Power BI-onlineservice (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: eeda30e5a075166af3718084c2c9f7737f876cbe
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861102"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Zelfstudie: Aan de slag met de Power BI-service
Deze zelfstudie is een inleiding tot een aantal functies van de *Power BI-service*. U kunt daarmee verbinding maken met gegevens, een rapport en een dashboard maken en vragen stellen over uw gegevens. U kunt veel meer doen in de Power BI-service. Deze zelfstudie is alleen maar bedoeld om de smaak naar meer op te wekken. Als u wilt weten hoe de Power BI-service aansluit bij de andere Power BI-aanbiedingen, is het een goed idee om [Wat is Power BI?](power-bi-overview.md) te lezen.

Bent u een *lezer* in plaats van maker van rapporten? Dan is [Navigeren in de Power BI-service](../consumer/end-user-experience.md) een goed startpunt voor u.

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Schermopname van het voorbeelddashboard Financieel.":::

In deze zelfstudie voert u de volgende stappen uit:

> [!div class="checklist"]
> * Meld u aan bij uw Power BI Online-account of registreert u zich als u nog geen account hebt.
> * De Power BI-service openen.
> * Enkele gegevens ophalen en deze openen in de rapportweergave.
> * Deze gegevens gebruiken om visualisaties te maken en deze op te slaan als een rapport.
> * Een dashboard maken door tegels van het rapport vast te maken.
> * Andere visualisaties toevoegen aan uw dashboard met behulp van Q&A (query's uitvoeren in natuurlijke taal).
> * Wijzig het formaat, schik de tegels opnieuw en bewerk de details voor de tegels op het dashboard.
> * Resources opschonen door het verwijderen van de gegevensset, het rapport en het dashboard.

## <a name="sign-up-for-the-power-bi-service"></a>Aanmelden voor de Power BI-service
U hebt een Power BI Pro-licentie nodig om een werkruimte te maken. Als u geen Power BI-account hebt, kunt u zich [aanmelden voor een gratis Power BI Pro-proefversie](https://app.powerbi.com/signupredirect?pbi_source=web) voordat u begint.

## <a name="step-1-get-data"></a>Stap 1: Gegevens ophalen

Wanneer u een Power BI-rapport wilt maken, kunt u vaak het beste beginnen in Power BI Desktop. Power BI Desktop is krachtiger. U kunt gegevens transformeren, vormgeven en modelleren voordat u begint met het ontwerpen van het rapport. Dit keer maken we echter een geheel nieuw rapport in de Power BI-service.

In deze zelfstudie worden de gegevens opgehaald uit een eenvoudig Microsoft Excel-bestand. Doet u mee? [Download het bestand met financiële voorbeelden](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Open om te beginnen de Power BI-service (app.powerbi.com) in uw browser. 

    Hebt u geen account? Geen probleem, u kunt zich [aanmelden voor een gratis proefversie van Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web)

1. Selecteer **Mijn werkruimte** in het navigatievenster.

1. Selecteer in **Mijn werkruimte** de opties **Nieuw** > **Een bestand uploaden**.

    De pagina **Gegevens ophalen** wordt geopend.   

3. Zorg ervoor dat in de sectie **Nieuwe inhoud maken** de optie **Bestanden** is geselecteerd en selecteer vervolgens de locatie waar u het Excel-bestand hebt opgeslagen.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Schermopname van Nieuw inhoud maken > Bestanden.":::

5. Blader naar het bestand op uw computer en kies **Openen**.

5. Voor deze zelfstudie selecteren we **Importeren** om het Excel-bestand toe te voegen als een gegevensset die we vervolgens kunnen gebruiken om rapporten en dashboards te maken. Als u **Uploaden** selecteert, wordt de hele Excel-werkmap geüpload naar Power BI, waar u deze kunt openen en bewerken in Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Schermopname van het kiezen van Importeren.":::
6. Wanneer uw gegevensset gereed is, selecteert u **Meer opties (...)** naast uw gegevensset voor Financieel voorbeeld en selecteert u vervolgens **Rapport maken**.
1. Open de rapporteditor. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Schermopname van Alle inhoud > Rapport maken.":::

    Het rapportcanvas is leeg. Aan de rechterkant zien we de deelvensters **Filters**, **Visualisaties** en **Velden**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Schermopname van een leeg rapportcanvas.":::

    > [!TIP]
    > Selecteer in de linkerbovenhoek de knop voor globale navigatie om het navigatiedeelvenster samen te vouwen. Op die manier is er meer ruimte voor uw canvas.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Knop voor globale navigatie.":::
    >

7. U bevindt zich momenteel in de bewerkingsweergave. Zoals u kunt zien, is in de menubalk de optie **Leesweergave** beschikbaar. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Schermopname van de optie Leesweergave.":::

    In de weergave Bewerken kunt u uw rapporten maken en aanpassen omdat u de *eigenaar* en *maker* van het rapport bent. Wanneer u uw rapport met collega’s deelt, kunnen zij het rapport vaak alleen in de leesweergave gebruiken. Ze zijn *gebruikers* van rapporten in uw **Mijn werkruimte**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Stap 2: Een grafiek in een rapport maken
Nu u verbinding met de gegevens hebt gemaakt, kunt u gaan verkennen. Wanneer u iets interessants hebt gevonden, kunt u dit opslaan op het rapportcanvas. Vervolgens kunt u het vastmaken aan een dashboard om het te bewaken en te zien hoe het in de loop van de tijd verandert. Maar zover is het nog niet.
    
1. Eerst gaat u in de rapporteditor naar het deelvenster **Velden** aan de rechterkant van de pagina om een visualisatie te bouwen. Selecteer het veld **Brutoverkoop** en vervolgens het veld **Datum**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Schermopname van de lijst Velden.":::

    Power BI analyseert de gegevens en maakt vervolgens een kolomdiagram. 

    > [!NOTE]
    > Als u het veld **Datum** eerst hebt geselecteerd in plaats van **Brutoverkopen**, wordt een tabel weer geven. Maakt u zich geen zorgen. In de volgende stap wijzigt u de visualisatie.

    Naast sommige velden staat het sigmasymbool, omdat Power BI heeft gedetecteerd dat ze numerieke waarden bevatten.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Velden met het sigmasymbool.":::

2. Probeer de gegevens eens op een andere manier weer te geven. Lijndiagrammen zijn goede visuals om waarden gedurende een bepaalde periode weer te geven. Selecteer het pictogram **Lijndiagram** in het deelvenster **Visualisaties**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Schermopname van de rapporteditor waarvoor een lijndiagram is geselecteerd.":::

3. Dit diagram lijkt interessant, dus laten we deze *vastmaken* aan een dashboard. Beweeg de muisaanwijzer over de visualisatie en selecteer het pictogram voor vastmaken.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Schermopname van het pictogram Vastmaken.":::

4. Omdat dit een nieuw rapport is, wordt u gevraagd dit rapport op te slaan voordat u een visualisatie aan een dashboard kunt vastmaken. Geef uw rapport een naam (bijvoorbeeld *Financieel voorbeeldrapport*) en selecteer vervolgens **Opslaan**. 

    U bekijkt het rapport nu in de leesweergave. 

6. Selecteer het pictogram **Vastmaken** opnieuw.
 
5. Selecteer **Nieuw dashboard** en geef het de naam *Financieel voorbeelddashboard*. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Schermopname van Dashboardnaam opgeven.":::
  
    U ontvangt het bericht (in de rechterbovenhoek) dat de visualisatie als tegel aan uw dashboard is toegevoegd.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Schermopname van het dialoogvenster Aan dashboard vastgemaakt.":::

    Nu u deze visualisatie hebt vastgemaakt, wordt deze opgeslagen op uw dashboard. De gegevens blijven up-to-date zodat u in één oogopslag de meest recente waarde kunt volgen. Als u in het rapport het type visualisatie wijzigt nadat u deze hebt vastgemaakt, blijft de visualisatie op het dashboard ongewijzigd.

7. Selecteer **Naar het dashboard gaan** om uw nieuwe dashboard met het lijndiagram te bekijken dat u er als tegel aan hebt vastgemaakt. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Schermopname van een dashboard met vastgemaakte visualisatie.":::
   
8. Selecteer de nieuwe tegel op uw dashboard. Met Power BI keert u terug naar het rapport in de leesweergave.

1. Als u wilt terugkeren naar de bewerkingsweergave, selecteert u **Meer opties** (...) in de menubalk > **Bewerken**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Schermopname van het selecteren van Bewerken om het rapport te bewerken.":::

    Terug in de Bewerkingsweergave, kunt u tegels blijven verkennen en vastmaken.

## <a name="step-3-explore-with-qa"></a>Stap 3: Verkennen met Q&A

Als u uw gegevens snel wilt verkennen, kunt u een vraag stellen in het Q&A-vak. Met Q&A kunt u query's in natuurlijke taal over uw gegevens vragen. In een dashboard bevindt het vak Q&A zich bovenaan (**Stel een vraag over uw gegevens**) onder de menubalk. In een rapport bevindt het zich in de bovenste menubalk (**Een vraag stellen**).

1. Selecteer **Mijn werkruimte** in de zwarte koptekstbalk in **Power BI** om terug te gaan naar het dashboard.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Schermopname van Terug naar Mijn werkruimte.":::

1. Selecteer uw dashboard in **Mijn werkruimte**.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Schermopname van het selecteren van uw dashboard.":::

1. Selecteer **Een vraag stellen over uw gegevens**. Q&A toont automatisch een aantal suggesties. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Schermopname van het Q&A-canvas.":::

    > [!NOTE]
    > Als u de suggesties niet ziet, schakelt u **Nieuwe Q&A-ervaring** in.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Schermopname van het inschakelen van een nieuwe Q&A-ervaring.":::

1. Sommige suggesties retourneren één waarde. Selecteer bijvoorbeeld **wat zijn de gemiddelde kosten van goederen**.

    Via Q&A wordt een antwoord gezocht dat vervolgens als *kaart*-visualisatie wordt weergegeven.

3. Selecteer **Visueel element vastmaken** en maak deze visualisatie vast aan het dashboard Financieel voorbeeld.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Schermopname van het vastmaken van het visuele element.":::

1. Ga terug naar Q&A en selecteer **Alle suggesties weergeven**.
1. Selecteer **totale winst per land**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Schermopname van de totale winst per land.":::

1. Maak de kaart ook vast het dashboard Financieel voorbeeld.

1. Selecteer op het dashboard de kaart die u zojuist hebt vastgemaakt. Zoals u ziet wordt Q&A opnieuw geopend? 
1. Plaats de cursor na *per land* in het vak Q&A en typ *als balk*. Power BI maakt direct een staafdiagram met de resultaten.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Schermopname van een visualisatie van een staafdiagram.":::

1. Maak ook het staafdiagram vast aan het dashboard Financieel voorbeeld.

4. Selecteer **Q&A afsluiten** om terug te gaan naar uw dashboard, waar u de nieuwe tegels ziet die u gemaakt hebt. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Schermopname van een dashboard met vastgemaakte Q&A-visuals.":::

   Hoewel u de kaart in Q&A hebt gewijzigd in een staafdiagram, blijft de tegel een kaart omdat de tegel een kaart was toen u deze vastmaakte. 

## <a name="step-4-reposition-tiles"></a>Stap 4: Tegels verplaatsen

We kunnen de tegels opnieuw rangschikken om beter gebruik te maken van de dashboardruimte.

1. Sleep de rechterbenedenhoek van de lijndiagramtegel *Brutoverkoop* omhoog, totdat deze op dezelfde hoogte wordt uitgelijnd als de tegel Verkoop en laat deze vervolgens los.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Schermopname van het wijzigen van het formaat van de tegel.":::

    De twee tegels hebben nu dezelfde hoogte.

1. Selecteer **Meer opties (...)** voor de tegel Gemiddelde KPV-kosten > **Details bewerken**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Schermopname van het menu Meer opties voor een tegel.":::

1. Typ in het vak **Titel** de tekst *Gemiddelde kosten van verkochte goederen* > **Toepassen**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Schermopname van het dialoogvenster Details bewerken.":::

1. Schik de andere visuals opnieuw om ze passend te maken.

    Dat ziet er beter uit.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Schermopname van het opnieuw geschikte dashboard.":::


## <a name="clean-up-resources"></a>Resources opschonen
Nu u de zelfstudie hebt voltooid, kunt u de gegevensset, het rapport en het dashboard verwijderen. 

1. Selecteer **Mijn werkruimte** in de zwarte koptekstbalk in **Power BI**.
2. Selecteer **Meer opties (...)** naast de gegevensset Financieel voorbeeld > **Verwijderen**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Schermopname van het verwijderen van de gegevensset.":::

    U ziet de waarschuwing **Alle rapporten en dashboardtegels met gegevens van deze gegevensset worden ook verwijderd**.

4. Selecteer **Verwijderen**.

## <a name="next-steps"></a>Volgende stappen

Verken deze verzamelingen met Microsoft Learn-inhoud voor Power BI:

- [Leer Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [Word een Power BI-gegevensanalist](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)