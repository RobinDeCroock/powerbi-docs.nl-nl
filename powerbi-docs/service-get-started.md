---
title: Aan de slag met de Power BI-service
description: Aan de slag met Power BI-onlineservice (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/25/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 06b60e5d493532efbdb49932ace48897e17961c1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61238352"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>Zelfstudie: Aan de slag met de Power BI-service (app.powerbi.com)
In deze zelfstudie leest u hoe u aan de slag kunt met de ***Power BI-service***. Als u wilt weten hoe de Power BI-service aansluit bij de andere Power BI-aanbiedingen, is het een goed idee om eerst [Wat is Power BI?](power-bi-overview.md) te lezen.

![illustratie van de relatie tussen Power BI Desktop, service en mobiel](media/service-get-started/power-bi-components.png)

In deze zelfstudie voert u de volgende stappen uit:

> [!div class="checklist"]
> * Andere inhoud zoeken om aan de slag te gaan met de Power BI-service
> * Inloggen op uw Power BI Online-account of u aanmelden voor een account als u er nog geen hebt
> * De Power BI-service openen
> * Enkele gegevens ophalen en openen in de rapportweergave
> * Deze gegevens gebruiken om visualisaties te maken en op te slaan als een rapport
> * Een dashboard maken door tegels van het rapport vast te maken
> * Een andere visualisatie toevoegen aan uw dashboard met behulp van Q&A (query's uitvoeren in natuurlijke taal)
> * Resources opschonen door het verwijderen van de gegevensset, het rapport en het dashboard

## <a name="sign-up-for-the-power-bi-service"></a>Aanmelden voor de Power BI-service
Als u zich niet hebt aangemeld voor Power BI, kunt u zich [aanmelden voor een gratis Power BI Pro-proefversie](https://app.powerbi.com/signupredirect?pbi_source=web) voordat u begint.

Als u al een account hebt, opent u een browser en typt u app.powerbi.com om de Power BI-service te openen. 

![Gratis aanmelden of registreren](media/service-get-started/power-bi-sign-up.png)

Als u hulp nodig hebt bij Power BI Desktop, leest u [Aan de slag met Power BI Desktop](desktop-getting-started.md). Als u hulp zoekt voor een mobiele Power BI-app, leest u [Power BI-apps voor mobiele apparaten](consumer/mobile/mobile-apps-for-mobile-devices.md).

> [!TIP]
> Volgt u liever een gratis training in uw eigen tempo? [Schrijf u in voor de cursus Analyzing and Visualizing Data with Power BI op EdX](http://aka.ms/edxpbi).

Bezoek onze [afspeellijst op YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP). Dit is een goede video om een algemeen beeld te krijgen van de Power BI-service:
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>Wat is de Power BI-service?
De Microsoft Power BI-service wordt ook wel Power BI Online of app.powerbi.com genoemd. Power BI helpt u om up-to-date te blijven met de informatie die belangrijk voor u is.  Met behulp van de ***dashboards*** van de Power BI-service weet u altijd precies wat er speelt in uw bedrijf.  De dashboards bevatten ***tegels*** waarop u kunt klikken om ***rapporten*** te openen voor nog meer inzicht in de gegevens.  U kunt verbinding maken met verschillende ***gegevenssets*** om alle relevante gegevens op één plek samen te brengen. Wilt u weten wat de bouwstenen zijn van Power BI?  Zie [Power BI - Basisconcepten](consumer/end-user-basic-concepts.md).

Als u belangrijke gegevens hebt verzameld in Excel- of CSV-bestanden, kunt u een Power BI-dashboard maken om overal en altijd op de hoogte te blijven en inzichten te delen met anderen.  Hebt u een abonnement op een SaaS-toepassing zoals Salesforce?  U kunt een goede start maken door verbinding te maken met Salesforce en automatisch een dashboard te maken van die gegevens. [Bekijk ook alle andere SaaS-apps](service-get-data.md) waarmee u verbinding kunt maken. Als u deel uitmaakt van een organisatie, controleert u of er misschien [apps](service-create-distribute-apps.md) voor u zijn gepubliceerd.

Lees hier meer over de andere manieren om [gegevens op te halen voor Power BI](service-get-data.md).

## <a name="step-1-get-data"></a>Stap 1: Gegevens ophalen
Hier volgt een voorbeeld van het ophalen van gegevens uit een CSV-bestand. Wilt u deze zelfstudie zelf uitvoeren? [Download dan dit CSV-voorbeeldbestand](http://go.microsoft.com/fwlink/?LinkID=521962).

1. [Meld u aan bij Power BI](http://www.powerbi.com/). Hebt u geen account? Geen probleem, u kunt zich aanmelden voor een gratis proefversie.
2. Power BI wordt geopend in uw browser. Selecteer **Gegevens ophalen** onderin de linkernavigatiebalk.
   
   ![Gegevens ophalen](media/service-get-started/getdata3.png)
3. Selecteer **Bestanden**. 
   
   ![Bestanden ophalen](media/service-get-started/gs1.png)
4. Blader naar het bestand op uw computer en kies **Openen**. Als u het bestand hebt opgeslagen in OneDrive voor Bedrijven, selecteert u die optie. Als u het bestand lokaal hebt opgeslagen, selecteert u **Lokaal bestand**. 
   
   ![Gegevens ophalen > scherm Bestanden](media/service-get-started/gs2.png)
5. Voor deze zelfstudie selecteren we **Importeren** om het Excel-bestand toe te voegen als een gegevensset die we vervolgens kunnen gebruiken om rapporten en dashboards te maken. Als u **Uploaden** selecteert, wordt de hele Excel-werkmap geüpload naar Power BI, waar u deze kunt openen en bewerken in Excel Online.
   
   ![Importeren kiezen](media/service-get-started/power-bi-import.png)
6. Als de gegevensset klaar is, selecteert u **Gegevensset weergeven** om deze te openen in de rapporteditor. 

    ![Dialoogvenster Uw gegevensset is gereed](media/service-get-started/power-bi-gs.png)

    Omdat we nog geen visualisaties hebben gemaakt, is het rapportcanvas nog leeg.

    ![Leeg rapportcanvas](media/service-get-started/power-bi-report-editor.png)

6. Bekijk de bovenste menubalk en kijk of u de optie **Leesweergave** ziet staan. Als u de optie voor de leesweergave kunt zien, betekent dit dat u zich in de **bewerkweergave** bevindt. 

    ![Optie Leesweergave](media/service-get-started/power-bi-editing-view.png)

    In de bewerkweergave kunt u uw rapporten maken en aanpassen omdat u de *eigenaar* van het rapport bent; u bent een *maker*. Wanneer u uw rapport met collega’s deelt, kunnen zij alleen interactief met het rapport werken in de leesweergave; zij worden *consumenten* genoemd. Lees meer over de [leesweergave en de bewerkweergave](consumer/end-user-reading-view.md).
    
    Een uitstekende manier om vertrouwd te raken met de rapporteditor is door [een rondleiding te volgen](service-the-report-editor-take-a-tour.md).
   > 
 

## <a name="step-2-start-exploring-your-dataset"></a>Stap 2: De gegevensset verkennen
Nu u verbinding met de gegevens hebt gemaakt, kunt u gaan verkennen.  Wanneer u iets interessants hebt gevonden, kunt u een dashboard maken om dit te controleren en te zien hoe dit na verloop van tijd verandert. Laten we zien hoe het werkt.
    
1. In de rapporteditor gebruiken we het deelvenster **Velden** aan de rechterkant van de pagina voor het bouwen van een visualisatie.  Schakel het selectievakje in van **Gross Sales** en **Date**.
   
   ![Lijst met velden](media/service-get-started/fields.png)

2. Power BI analyseert de gegevens en maakt vervolgens een visualisatie.  Als u eerst **Date** hebt geselecteerd, ziet u een tabel.  Als u eerst **Gross Sales** hebt geselecteerd, ziet u een grafiek. Probeer de gegevens eens op een andere manier weer te geven. Laten we deze gegevens eens bekijken als lijndiagram. Selecteer het pictogram Lijndiagram (ook wel sjabloon genoemd) in het **deelvenster Visualisaties**.
   
   ![Rapporteditor waarin pictogram is geselecteerd](media/service-get-started/gettingstart5new.png)

3. Dit diagram lijkt interessant, dus laten we deze *vastmaken* aan een dashboard. Beweeg de muisaanwijzer over de visualisatie en selecteer het pictogram **Vastmaken**.  Wanneer u deze visualisatie vastmaakt, wordt deze opgeslagen op uw dashboard en kunt u in één oogopslag zien wat de meest recente waarde is.
   
   ![Speldpictogram](media/service-get-started/pinnew.png)

4. Omdat dit een nieuw rapport is, wordt u gevraagd dit rapport op te slaan voordat u een visualisatie aan een dashboard kan vastmaken. Geef uw rapport een naam (bijv. *Verkoop over periode*) en selecteer **Opslaan en doorgaan**. 
   
   ![Dialoogvenster Rapport opslaan](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. Laten we het lijndiagram aan het nieuwe dashboard vastmaken aan en deze de naam 'Financieel voorbeeld voor de zelfstudie' geven. 
   
   ![Het rapport een naam geven](media/service-get-started/power-bi-pin.png)
   
1. Selecteer **Vastmaken**.
   
    U ontvangt het bericht (in de rechterbovenhoek) dat de visualisatie als tegel aan uw dashboard is toegevoegd.
   
    ![Dialoogvenster Aan dashboard vastgemaakt](media/service-get-started/power-bi-pin-success.png)

6. Selecteer **Naar het dashboard gaan** om de lijndiagram, die als tegel aan uw nieuwe dashboard is vastgemaakt, te bekijken. Maak het dashboard nog beter door meer visualisatietegels toe te voegen en [tegels een andere naam te geven, groter of kleiner te maken, te koppelen en te verplaatsen](service-dashboard-edit-tile.md).
   
   ![Dashboard waarin visualisatie is vastgemaakt](media/service-get-started/power-bi-new-dashboard.png)
   
   Selecteer de nieuwe tegel in het dashboard als u wilt terugkeren naar het rapport. U keert terug naar de rapporteditor in de leesweergave. Als u terug wilt naar de bewerkweergave, selecteert u **Rapport bewerken** in de bovenste menubalk. Eenmaal in de bewerkweergave, kunt u meer tegels verkennen en vastmaken. 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>Stap 3:  Ga verder met verkennen met behulp van Q&A (query's uitvoeren in natuurlijke taal)
1. Als u gegevens snel wilt verkennen, kunt u een vraag typen in het vak Een vraag stellen. Het vak Q&A bevindt zich boven aan uw dashboard (**Q&A over uw gegevens**) en in de bovenste menubalk in uw rapport (**Q&A**). Typ bijvoorbeeld eens ‘what segment had the most revenue’.
   
   ![Q&A-canvas](media/service-get-started/powerbi-qna.png)

2. Via Q&A wordt een antwoord gezocht dat vervolgens als visualisatie wordt weergegeven. Selecteer het speldpictogram ![Speldpictogram](media/service-get-started/pbi_pinicon.png) om deze visualisatie ook in uw dashboard weer te geven.
3. Maak de visualisatie vast aan het dashboard ‘Financieel voorbeeld voor zelfstudie’.
   
    ![Dialoogvenster Aan dashboard vastmaken](media/service-get-started/power-bi-pin2.png)

4. Ga terug naar uw dashboard. Hier ziet u de nieuwe tegel.

   ![Dashboard waarin grafiek is vastgemaakt](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>Resources opschonen
Nu u de zelfstudie hebt voltooid, kunt u de gegevensset, het rapport en het dashboard verwijderen. 

1. Selecteer **Mijn werkruimte** in de linkernavigatiebalk.
2. Selecteer het tabblad **Gegevenssets** en zoek de gegevensset die u voor deze zelfstudie hebt geïmporteerd.  
3. Selecteer het beletselteken (...) > **Verwijderen**.

    ![De gegevensset verwijderen](media/service-get-started/power-bi-delete.jpg)

    Als u de gegevensset verwijdert, worden ook het rapport en het dashboard verwijderd. 


## <a name="next-steps"></a>Volgende stappen
Klaar om meer uit te proberen?  Hier volgen enkele goede manieren om nader kennis te maken met Power BI.

> [!div class="nextstepaction"]
> [Verbinding maken met de onlineservices die u gebruikt](service-connect-to-services.md)

