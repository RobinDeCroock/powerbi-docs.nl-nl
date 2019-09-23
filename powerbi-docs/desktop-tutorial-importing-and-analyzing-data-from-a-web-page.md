---
title: 'Zelfstudie: Gegevens van een webpagina importeren en analyseren'
description: 'Zelfstudie: Gegevens van een webpagina importeren en analyseren met Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: d6cdcf47b42be4a9b541aa355efb3dd5e9667204
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514635"
---
# <a name="tutorial-analyze-web-page-data-using-power-bi-desktop"></a>Zelfstudie: Gegevens van een webpagina analyseren met Power BI Desktop

Als een fanatieke voetbalfan wilt u rapporteren over de winnaars van het UEFA Europees kampioenschap (Euro Cup) in de afgelopen jaren. Met Power BI Desktop kunt u deze gegevens vanuit een webpagina in een rapport importeren en visualisaties maken die de gegevens weergeven. In deze zelfstudie leert u hoe Power BI Desktop kunt gebruiken voor het volgende:

- Verbinding maken met een webgegevensbron en door alle beschikbare tabellen navigeren,
- Gegevens vormgeven en transformeren in de **Power Query-editor**,
- Een query een naam geven en importeren in een Power BI Desktop-rapport, en 
- Een kaart- en een cirkeldiagramvisualisatie maken en aanpassen.

## <a name="connect-to-a-web-data-source"></a>Verbinding maken met een webgegevensbron

U kunt de gegevens over de UEFA-winnaars verkrijgen uit de tabel met resultaten op de Wikipedia-pagina over het UEFA Europees kampioenschap (Engelstalig) op http://en.wikipedia.org/wiki/UEFA_European_Football_Championship. 

![Resultatentabel op Wikipedia (Engelstalig)](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Er kunnen alleen webverbindingen worden gemaakt bij gebruik van basisverificatie. Websites waarvoor verificatie is vereist, werken mogelijk niet goed met de webconnector.

Ga als volgt te werk om de gegevens te importeren:

1. Klik op het linttabblad **Start** van Power BI Desktop op de pijl van de vervolgkeuzelijst **Gegevens ophalen** en selecteer **Web**.
   
   ![Gegevens ophalen via lint](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 
   
   >[!NOTE]
   >U kunt ook het item **Gegevens ophalen** zelf selecteren of **Gegevens ophalen** in het dialoogvenster **Aan de slag** in Power BI selecteren en vervolgens **Web** selecteren in de sectie **Alles** of **Overige** van het dialoogvenster **Gegevens ophalen**. Selecteer vervolgens **Verbinding maken**.
   
2. Plak in het dialoogvenster **Van web**de URL `http://en.wikipedia.org/wiki/UEFA_European_Football_Championship` in het tekstvak **URL** en selecteer vervolgens **OK**.
   
    ![Gegevens ophalen via dialoogvenster](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)
   
   Nadat u verbinding hebt gemaakt met de Wikipedia-pagina (Engelstalig), wordt in het dialoogvenster **Navigator** van Power BI een lijst met beschikbare tabellen op de pagina weergegeven. U kunt een van de tabelnamen selecteren om een voorbeeld van de gegevens weer te geven. De tabel **Resultaten [bewerken]** bevat de gegevens die u wilt, hoewel deze niet precies in de gewenste vorm zijn. Voordat u de gegevens in uw rapport laadt, geeft u ze vorm en schoont u ze op. 
   
   ![Dialoogvenster Navigator](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)
   
   >[!NOTE]
   >In het deelvenster **Voorbeeld** wordt de meest recent geselecteerde tabel weergegeven, maar alle geselecteerde tabellen worden geladen in de **Power Query-editor** wanneer u **Bewerken** of **Laden**  selecteert. 
   
3. Selecteer de tabel **Resultaten [bewerken]** in de lijst **Navigator**, en selecteer vervolgens **Bewerken**. 
   
   In **Power Query-editor** wordt een voorbeeld van de tabel geopend, waarin u transformaties kunt toepassen om de gegevens op te schonen. 
   
   ![Power Query-editor](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)
   
## <a name="shape-data-in-power-query-editor"></a>Gegevens vormgeven in Power Query-Editor

U wilt de gegevens gemakkelijker te scannen maken door alleen het jaar en de landen die gewonnen hebben weer te geven. U kunt de **Power Query-editor** gebruiken om deze stappen voor het vormgeven en opschonen van gegevens uit te voeren.

Verwijder eerst alle kolommen behalve **Year** en **Final Winners** uit de tabel.

1. Selecteer in het raster **Power Query-editor** de kolommen**Year** en **Final Winners** (houd de **Ctrl**-toets ingedrukt om meerdere items te selecteren).
   
2. Klik met de rechtermuisknop en selecteer **Andere kolommen verwijderen** in de vervolgkeuzelijst of selecteer **Kolommen verwijderen** > **Andere kolommen verwijderen** in de groep  **Kolommen beheren** op het linttabblad **Start** en verwijder alle andere kolommen uit de tabel. 
   
   ![Vervolgkeuzelijst Andere kolommen verwijderen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png) of ![Lint Andere kolommen verwijderen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

Verwijder vervolgens het extra woord **Details** uit de kolomcellen **Year**.

1. Selecteer de kolom **Year**.
   
2. Klik met de rechtermuisknop en selecteer **Waarden vervangen** in de vervolgkeuzelijst, of selecteer **Waarden vervangen** in de groep **Transformeren** op het tabblad **Start** van het lint (ook te vinden in de groep **Elke kolom** op het tabblad **Transformeren**). 
   
   ![Vervolgkeuzelijst Waarden vervangen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) of ![Lint Waarden vervangen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)
   
3. Typ in het dialoogvenster **Waarden vervangen** **Details** in het tekstvak **Te zoeken waarde** en laat het tekstvak **Vervangen door** leeg. Selecteer **OK** om het woord 'Details' uit de **Year**-vermeldingen te verwijderen.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

Sommige **Year**-cellen bevatten alleen het woord 'Year' in plaats van jaarwaarden. U kunt de kolom **Year** filteren om alleen rijen weer te geven die het woord 'Year' niet bevatten. 

1. Selecteer de pijl omlaag voor het filter voor de kolom **Year**.
   
2. Blader omlaag in de vervolgkeuzelijst en schakel het selectievakje naast de optie **Year** uit en selecteer vervolgens **OK** om de rijen te verwijderen die alleen het woord 'Year' in de kolom **Year** bevatten. 

   ![Gegevens filteren](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

Nu u de gegevens in de kolom **Year** hebt opgeschoond, kunt u gaan werken aan de kolom **Final Winner**. Omdat u nu alleen de lijst met winnaars bekijkt, kunt u de naam van deze kolom wijzigen in **Country**. Ga als volgt te werk om de naam van de kolom te wijzigen:

1. Dubbelklik op de kolomkop **Final Winner** of tik op de kolomkop en houd deze vast, of 
   - Klik met de rechtermuisknop op de kolomkop **Final Winners** en selecteer **Naam wijzigen** in de vervolgkeuzelijst, of 
   - Selecteer de kolom **Final Winners** en selecteer **Naam wijzigen** in de groep **Elke kolom** op het tabblad **Transformeren** van het lint. 
   
   ![Vervolgkeuzelijst Naam wijzigen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) of ![Lint Naam wijzigen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)
   
2. Typ **Country** in de koptekst en druk op **Enter** om de naam van de kolom te wijzigen.

Ook wilt u rijen zoals '2020' wegfilteren die null-waarden in de kolom **Country** bevatten. U kunt het filtermenu gebruiken zoals u hebt gedaan met de **Year**-waarden, of u kunt:

1. Met de rechtermuisknop op de cel **Country** in de rij **2020** klikken, die de waarde *null* heeft. 
2. **Tekstfilters** > **Is niet gelijk aan** in het contextmenu selecteren om rijen die de waarde van deze cel bevatten te verwijderen.
   
   ![Tekstfilter](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)
   
## <a name="import-the-query-into-report-view"></a>De query importeren in de rapportweergave

Nu u de gegevens de gewenste vorm hebt gegeven, kunt u de query de naam 'Euro Cup Winners' geven en importeren in uw rapport.

1. Voer in het deelvenster **Queryinstellingen** in het tekstvak **Naam** **Euro Cup Winners** in en druk op **Enter**.
   
   ![De query een naam geven](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

2. Selecteer **Sluiten en toepassen** > **Sluiten en toepassen** op het tabblad **Start** van het lint.
   
   ![Sluiten en toepassen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)
   
De query wordt geladen in de **rapportweergave** van Power BI Desktop, waar u deze kunt zien in het deelvenster **Velden**. 
   
   ![Deelvenster Velden](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)
>[!TIP]
>U kunt altijd teruggaan naar de **Power Query-editor** om uw query te bewerken en te verfijnen door:
>- Het beletselteken ( **...** ) **Meer opties** naast **Euro Cup Winners** in het deelvenster **Velden** te selecteren en **Query bewerken** te selecteren in de vervolgkeuzelijst, of
>- **Query's bewerken** > **Query's bewerken** te selecteren in de groep **Externe gegevens** van het linttabblad **Start** in de rapportweergave. 

## <a name="create-a-visualization"></a>Een visualisatie maken

Ga als volgt te werk om een visualisatie te maken op basis van uw gegevens: 

1. Selecteer het veld **Country** in het deelvenster **Velden** of sleep het naar het rapportcanvas. Power BI Desktop herkent de gegevens als landnamen en maakt automatisch een **kaart**visualisatie. 
   
   ![Kaartvisualisatie](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)
   
2. Vergroot de kaart door te slepen met de grepen in de hoeken, zodat de namen van alle winnende landen zichtbaar zijn.  

   ![Kaart vergroten](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
   
3. De kaart toont identieke gegevenspunten voor elk land dat een toernooi Euro Cup-toernooi heeft gewonnen. Als u wilt dat de grootte van elk gegevenspunt weergeeft hoe vaak het land heeft gewonnen, sleept u het veld **Year** naar **Sleep gegevensvelden hierheen** onder **Grootte** in het onderste gedeelte van het deelvenster **Visualisaties**. Het veld wordt automatisch gewijzigd in de meetwaarde**Count of Year** en de kaartvisualisatie toont nu grotere gegevenspunten voor landen die meer toernooien hebben gewonnen. 
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)
   

## <a name="customize-the-visualization"></a>De visualisatie aanpassen

Zoals u ziet, is het zeer eenvoudig om visualisaties te maken op basis van uw gegevens. U kunt uw visualisaties ook eenvoudig aanpassen om de gegevens beter te presenteren op manieren die u wilt. 

### <a name="format-the-map"></a>De kaart opmaken
U kunt de weergave van een visualisatie wijzigen door deze te selecteren en vervolgens te klikken op het pictogram **Opmaak** (verfroller) in het deelvenster **Visualisaties**. De gegevenspunten 'Duitsland' in uw visualisatie kunnen bijvoorbeeld misleidend zijn, omdat West-Duitsland twee toernooien heeft gewonnen en Duitsland er een heeft gewonnen en de kaart de twee punten over elkaar heen plaatst in plaats van deze van elkaar te scheiden of bij elkaar op te tellen. U kunt deze twee punten een andere kleur geven om dit te markeren. U kunt de kaart ook een aantrekkelijkere en meer beschrijvende titel geven. 

1. Selecteer met de visualisatie geselecteerd het pictogram **Opmaak** en selecteer vervolgens **Gegevenskleuren** om de opties voor gegevenskleuren uit te vouwen. 
   
   ![Gegevens opmaken met kleuren](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)
   
2. Schakel **Alles weergeven** in op **Aan** en selecteer vervolgens de vervolgkeuzelijst naast **West-Duitsland** en kies de kleur geel. 
   
   ![Kleur wijzigen](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)
   
3. Selecteer **Titel** om de opties voor titels uit te vouwen en typ in het veld **Titeltekst** de tekst **Euro Cup Winners** in plaats van de huidige titel. 
4. Wijzig de **Tekenkleur**in rood, de **Tekengrootte** in **12** en de **Lettertypefamilie** in **Segoe (Bold)** . 
   
   ![Gegevens opmaken met kleuren](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)
   

De visualisatie van uw kaart ziet er nu als volgt uit:

![Opgemaakte kaartvisualisatie](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)
   
### <a name="change-the-visualization-type"></a>Het type visualisatie wijzigen
U kunt het type visualisatie wijzigen door dit te selecteren en vervolgens boven aan het deelvenster **Visualisatie** op een ander pictogram te klikken. Op uw kaartvisualisatie ontbreken bijvoorbeeld de gegevens voor de Sovjetunie en Tsjechoslowakije, omdat deze landen niet meer op de wereldkaart bestaan. Een ander type visualisatie zoals een treemap of cirkeldiagram zijn mogelijk nauwkeuriger, omdat alle waarden worden weergegeven. 

Als u de kaart wilt wijzigen in een cirkeldiagram, selecteert u de kaart en selecteert u vervolgens het pictogram **Cirkeldiagram** in het deelvenster **Visualisatie**. 
   
![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- U kunt de opmaakopties voor **Gegevenskleuren** gebruiken om 'Duitsland' en 'West Duitsland' dezelfde kleur te geven. 
>- Als u de landen met de meeste overwinningen samen in het cirkeldiagram wilt groeperen, selecteert u het beletselteken ( **...** ) rechts boven in de visualisatie en selecteert u vervolgens **Sorteren op aantal jaar** in de vervolgkeuzelijst. 

Power BI Desktop biedt een naadloze complete ervaring voor het ophalen van gegevens uit een breed scala aan gegevensbronnen en het vormgeven van deze gegevens om te voldoen aan uw analysebehoeften. Zo kunt u deze gegevens op uitgebreide en interactieve manieren visualiseren. Wanneer uw rapport klaar is, kunt u [het uploaden naar Power BI](desktop-upload-desktop-files.md) en op basis van dit rapport dashboards maken die u kunt delen met andere Power BI-gebruikers.

## <a name="see-also"></a>Zie ook
* [Andere zelfstudies voor Power BI Desktop lezen](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Power BI Desktop-video's bekijken](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Een bezoek brengen aan het Power BI-forum](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Het Power BI-blog lezen](http://go.microsoft.com/fwlink/?LinkID=519327)

