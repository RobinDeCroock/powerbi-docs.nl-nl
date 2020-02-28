---
title: 'Zelfstudie: Facebook-gegevens analyseren met Power BI Desktop'
description: Meer informatie over hoe u gegevens uit Facebook importeert en gebruikt in Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 1f5cedba1c32f152cd6e4a9f9f51d0355ac05ce5
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77497309"
---
# <a name="tutorial-analyze-facebook-data-by-using-power-bi-desktop"></a>Zelfstudie: Facebook-gegevens analyseren met Power BI Desktop

In deze zelfstudie leert u hoe u gegevens uit Facebook importeert en gebruikt in Power BI Desktop. U moet verbinding maken met en gegevens importeren van de Power BI Facebook-pagina, transformaties toepassen op de geïmporteerde gegevens en de gegevens in rapportvisualisaties gebruiken.

> [!WARNING]
> Als gevolg van machtigingsbeperkingen voor Facebook-apps, werken de connectorfuncties die in dit artikel worden beschreven, momenteel niet goed. We werken samen met Facebook om deze functionaliteit zo snel mogelijk te herstellen.


## <a name="connect-to-a-facebook-page"></a>Verbinding maken met een Facebook-pagina

In deze zelfstudie gebruiken we gegevens van de [Microsoft Power BI Facebook-pagina](https://www.facebook.com/microsoftbi). Met uitzondering van een persoonlijk Facebook-account hebt u geen speciale referenties nodig om verbinding te maken met en gegevens te importeren van deze pagina.

1. Open Power BI Desktop en selecteer **Gegevens ophalen** in het dialoogvenster **Aan de slag** of selecteer op het linttabblad **Start** de optie **Gegevens ophalen** en vervolgens **Meer**.
   
2. Selecteer in het dialoogvenster **Gegevens ophalen** de optie **Facebook** in de groep **Onlineservices** en selecteer vervolgens **Verbinden**.
   
   ![Gegevens ophalen](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   Er verschijnt een dialoogvenster waarin u wordt gewaarschuwd voor de risico's van het gebruik van een service van derden.
   
   ![Waarschuwing over derden](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. Selecteer **Doorgaan**. 
   
4. Voer in het dialoogvenster **Facebook** de paginanaam **microsoftbi** in als de **gebruikersnaam**, selecteer **Berichten** in de vervolgkeuzelijst **Verbinding** en selecteer **OK**.
   
   ![Verbinden](media/desktop-tutorial-facebook-analytics/2.png)
   
5. Wanneer u wordt gevraagd om referenties in te voeren, meldt u zich aan met uw Facebook-account en geeft u Power Bi toegang tot uw account.
   
   ![Referenties](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   Nadat u verbinding hebt gemaakt met de Power BI Facebook-pagina, ziet u een voorbeeld van de gegevens in de berichten van de pagina. 
   
   ![Voorbeeld van gegevens](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>De geïmporteerde gegevens vormgeven en transformeren

Stel dat u wilt zien en weergeven welke berichten de meeste opmerkingen hebben gedurende een bepaalde periode, maar u ziet dat in het gegevensvoorbeeld Berichten de gegevens over de **created_time** moeilijk te lezen en te begrijpen zijn, en dat er helemaal geen gegevens over opmerkingen zijn. Voer een aantal vormgevings- en opschoningsacties op de gegevens uit om er zoveel mogelijk informatie uit te kunnen halen. Hiervoor kunt u de Power Query-editor van Power BI Desktop gebruiken om de gegevens te bewerken voordat of nadat u deze naar Power BI Desktop importeert. 

### <a name="split-the-datetime-column"></a>De datum/tijd-kolom splitsen

Eerst scheidt u de datum- en tijdwaarden in de kolom **created_time**, zodat deze beter leesbaar zijn. 

1. Selecteer in het Facebook-gegevensvoorbeeld de optie **Bewerken**. 
   
   ![Gegevensvoorbeeld - bewerken](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   De Power Query-editor van Power BI Desktop wordt in een nieuw venster geopend en geeft het voorbeeld van de gegevens van de Power BI Facebook-pagina weer. 
   
   ![Power Query-editor](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. Selecteer de kolom **created_time**. U ziet dat er sprake is van het gegevenstype **Tekst**, dat wordt aangegeven door het pictogram **ABC** in de kolomkop. Klik met de rechtermuisknop op de header en selecteer **Kolom splitsen** > **Op scheidingsteken** in de vervolgkeuzelijst. Of selecteer **Kolom splitsen** > **Op scheidingsteken** in de groep **Transformeren** op het tabblad **Start** op het lint.  
   
   ![Kolom splitsen op scheidingsteken](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. Selecteer in het dialoogvenster **Kolom splitsen op scheidingsteken** de optie **Aangepast** in de vervolgkeuzelijst, voer **T** in (het teken waarmee het tijdgedeelte van de waarden voor **created_time** begint) in het invoerveld en selecteer **OK**. 
   
   ![Het dialoogvenster Kolom splitsen op scheidingsteken](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   De kolom wordt gesplitst in twee kolommen die de tekenreeksen voor en na het *T*-scheidingsteken bevatten. De nieuwe kolommen hebben respectievelijk de naam **created_time.1** en **created_time.2**. Power BI heeft de gegevenstypen automatisch gedetecteerd en gewijzigd in **Datum** voor de eerste kolom en **Tijd** voor de tweede kolom en de datum- en tijdwaarden opgemaakt, zodat deze beter leesbaar zijn.
   
4. Wijzig de naam van de twee kolommen. Selecteer de kolom **created_time.1** en selecteer vervolgens **Naam wijzigen** in de groep **Alle kolommen** van het tabblad **Transformeren**  van het lint. Of dubbelklik op de kolomkop en voer de nieuwe kolomnaam, **created_date**, in. Herhaal dit voor de kolom **created_time.2** en wijzig de naam ervan in **created_time**.
   
   ![Nieuwe datum- en tijdkolommen](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>De geneste kolom uitvouwen

Nu de datum- en tijdgegevens worden weergegeven zoals u wilt, geeft u opmerkingsgegevens weer door een geneste kolom uit te vouwen. 

1. Selecteer het ![uitvouwpictogram](media/desktop-tutorial-facebook-analytics/14.png) boven in de kolom **object_link** om het dialoogvenster **Uitvouwen/aggregatie** te openen. Selecteer **connections** en selecteer vervolgens **OK**. 
   
   ![object_link uitvouwen](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   De kolomkop wordt gewijzigd in **object_link.connections**.
2. Selecteer het ![uitvouwpictogram](media/desktop-tutorial-facebook-analytics/14.png) bovenaan de kolom **object_link.connections**, selecteer **comments** en selecteer vervolgens **OK**. De kolomkop wordt gewijzigd in **object_link.connections.comments**.
   
3. Selecteer het ![uitvouwpictogram](media/desktop-tutorial-facebook-analytics/14.png) bovenaan de kolom **object_link.connections.comments** en selecteer deze keer **Aggregatie** in plaats van **Uitvouwen** in het dialoogvenster. Selecteer **Aantal id’s** en selecteer **OK**. 
   
   ![Opmerkingen samenstellen](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   Het aantal opmerkingen voor elk bericht wordt nu weergegeven in de kolom. 
   
4. Wijzig de naam van de kolom **Aantal object_link.connections.comments.id** in **Aantal opmerkingen**.
   
5. Selecteer de pijl omlaag naast de kolomkop **Aantal opmerkingen** en selecteer **Aflopend sorteren** om de berichten te sorteren van de meeste naar de minste opmerkingen. 
   
   ![Opmerkingen per bericht](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>Querystappen bekijken

Terwijl u gegevens in de **Power Query-editor** vormgeeft en transformeert, wordt elke stap vastgelegd in het gebied **Toegepaste stappen** van het deelvenster **Queryinstellingen** aan de rechterkant van het Power Query-editor-venster. U kunt stap voor stap teruggaan via **Toegepaste stappen** om de doorgevoerde wijzigingen te bekijken en zo nodig te bewerken of verwijderen of om ze opnieuw te rangschikken. Wees voorzichtig wanneer u deze stappen wijzigt, omdat het wijzigen van de voorgaande stappen de volgende stappen kan verstoren. 

Nadat de gegevenstransformaties tot nu toe zijn toegepast, moeten uw **Toegepaste stappen** er als volgt uitzien:
   
   ![Toegepaste stappen](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >**Toegepaste stappen** hebben onderliggende formules die zijn geschreven in de [formuletaal M van Power Query](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language). Als u de formules wilt bekijken en bewerken, selecteert u **Geavanceerde editor** in de groep **Query** van het tabblad **Start** van het lint. 

### <a name="import-the-transformed-data"></a>De getransformeerde gegevens importeren

Wanneer u tevreden bent met de gegevens, selecteert u **Sluiten en toepassen** > **Sluiten en toepassen** op het tabblad **Start** van het lint om deze te importeren in Power BI Desktop. 
   
   ![Sluiten en toepassen](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   In een dialoogvenster wordt de voortgang weergegeven van het laden van de gegevens in het gegevensmodel van Power BI Desktop. 
   
   ![Gegevens laden](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   Zodra de gegevens zijn geladen, worden deze in de weergave **Rapport** weergegeven als een nieuwe query in het deelvenster **Velden**.
   
   ![Nieuwe query](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>De gegevens in rapportvisualisaties gebruiken 

Nu u de gegevens van de Facebook-pagina hebt geïmporteerd, kunt u snel en eenvoudig inzicht krijgen in uw gegevens met behulp van visualisaties. Het maken van een visualisatie is eenvoudig: u hoeft alleen maar een veld te selecteren in het deelvenster **Velden** of het te verslepen naar het rapportcanvas.

### <a name="create-a-bar-chart"></a>Een staafdiagram maken

1. Selecteer in de weergave **Rapport** van Power BI Desktop **bericht** in het deelvenster **Velden** of sleep dit veld naar het rapportcanvas. Er wordt een tabel met alle berichten weergegeven op het canvas. 
   
   ![Nieuwe query](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. Selecteer met deze tabel geselecteerd ook **Aantal opmerkingen** in het deelvenster **Velden** of sleep het veld naar de tabel. 
   
3. Selecteer het pictogram **Gestapeld staafdiagram** in het deelvenster **Visualisaties**. De tabel wordt een staafdiagram waarin het aantal opmerkingen per bericht wordt weergegeven. 
   
   ![Staafdiagram](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. Selecteer **Meer opties** (...) naast de visualisatie en selecteer vervolgens **Sorteren op** > **Aantal opmerkingen** om de tabel te sorteren op aflopend aantal opmerkingen. 

   Merk op dat de meeste opmerkingen zijn gekoppeld aan **(Leeg)** berichten (deze berichten zijn artikelen, koppelingen, video's of andere niet-tekstuele inhoud). 
   
5. Als u lege rijen wilt wegfilteren, selecteert u **bericht is (Alle)** in het deelvenster **Filters** en selecteert u **Alles selecteren** en vervolgens **(Leeg)** om de selectie op te heffen. 

   De vermelding in het deelvenster **Filters** wijzigt in **bericht is niet (Leeg)** en de rij **Leeg** verdwijnt uit de diagramweergave.
   
   ![Lege rij wegfilteren](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>Het diagram opmaken

De visualisatie wordt interessanter, maar u kunt nog niet veel van de berichttekst in het diagram zien. Ga als volgt te werk om meer van de berichttekst weer te geven:

1. Maak het diagram zo groot mogelijk met behulp van de grepen in de diagramweergave. 
   
2. Selecteer met het diagram geselecteerd het pictogram **Opmaak** (verfroller) in het deelvenster **Visualisatie**.
   
3. Selecteer de pijl omlaag naast de **y-as** en sleep de schuifregelaar **Maximumgrootte** helemaal naar rechts (**50%** ). 
4. Verklein de **Tekengrootte** naar **10 punten**, zodat er meer tekst past.
   
   ![Opmaakwijzigingen](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   Het diagram geeft nu meer van de berichtinhoud weer. 
   
   ![Meer berichten weergeven](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
De x-as (het aantal opmerkingen) van het diagram toont geen exacte waarden, en ziet er een beetje verloren uit onderaan het diagram. We gaan in plaats daarvan de gegevenslabels gebruiken: 

1. Selecteer het pictogram **Opmaak** en zet de schuifregelaar voor **x-as** op **Uit**. 
   
2. Selecteer de schuifregelaar **Gegevenslabels** en zet deze op **Aan**. 

   Het diagram toont nu het exacte aantal opmerkingen voor elk bericht.
   
   ![Gegevenslabels toepassen](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>Het gegevenstype bewerken

Dit is beter, maar alle gegevenslabels hebben een decimaal van **.0** die afleidt en misleidend is, omdat het **Aantal berichten** een geheel getal moet zijn. Om ze te herstellen, moet u het gegevenstype van de kolom **Aantal berichten** wijzigen in **Geheel getal**:

1. Klik met de rechtermuisknop op **Query1** in het deelvenster **Velden** of beweeg de muisaanwijzer erover en selecteer **Meer opties** (...). 

2. Selecteer **Query bewerken** in het contextmenu. Of selecteer **Query's bewerken** > **Query's bewerken** in de groep **Externe gegevens** van het tabblad **Start** op het lint. 
   
3. Selecteer in het venster **Power Query Editor** de kolom **Aantal opmerkingen** en wijzig het gegevenstype door een van deze stappen te volgen: 
   - Selecteer het pictogram **1.2** naast de kolomkop **Aantal opmerkingen** en selecteer vervolgens **Geheel getal** in de vervolgkeuzelijst
   - Klik met de rechtermuisknop op de kolomkop en selecteer vervolgens **Type wijzigen** > **Geheel getal**.
   - Selecteer **Gegevenstype: decimaal getal** in de groep **Transformeren** van het tabblad **Start** of in de groep **Elke kolom** van het tabblad **Transformeren** en selecteer **Geheel getal**.
   
   Het pictogram in de kolomkop verandert in **123**, wat het gegevenstype voor een **geheel getal** aangeeft.
   
   ![Gegevenstype wijzigen](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. Selecteer **Bestand** > **Sluiten en toepassen**, of **Bestand** > **Toepassen** om het venster **Power Query-editor** geopend te houden om de wijzigingen toe te passen. 

   Nadat de wijzigingen zijn geladen, worden de gegevenslabels in het diagram gehele getallen.
   
   ![Diagram met gehele getallen](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>Een gegevensslicer maken

Stel dat u het aantal opmerkingen over berichten wilt visualiseren gedurende een bepaalde periode. U kunt een slicervisualisatie maken als u de gegevens in het diagram wilt filteren op andere perioden. 

1. Selecteer op een leeg gebied van het canvas en selecteer vervolgens het pictogram **Slicer** in het deelvenster **Visualisaties**. 

   Er wordt een lege slicervisualisatie weergegeven.
   
   ![Slicerpictogram selecteren](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. Selecteer het veld **created_date** in het deelvenster **Velden** of sleep het naar de nieuwe slicer. 

   De slicer verandert in een schuifregelaar voor het datumbereik, op basis van het gegevenstype **Datum** van het veld.
   
   ![Slicer voor datumbereikschuifregelaar](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. Verplaats de grepen van de schuifregelaar om verschillende datumbereiken te selecteren en merk op hoe de diagramgegevens op basis daarvan worden gefilterd. U kunt ook de datumvelden selecteren in de slicer en specifieke datums typen of deze kiezen in een pop-upkalender.
    
   ![Gegevens slicen](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>De visualisaties opmaken

Geef het diagram een aantrekkelijkere en meer beschrijvende titel: 

1. Als de grafiek is geselecteerd, selecteert u het pictogram **Opmaak** in het deelvenster **Visualisaties** en selecteert u vervolgens de vervolgkeuzepijl naast **Titel** om deze uit te vouwen.

2. Wijzig de **Titeltekst** in **Opmerkingen per bericht**. 

3. Selecteer de pijl van de vervolgkeuzelijst naast **Tekstkleur** en selecteer een groene kleur die overeenkomt met de groene staven van de visualisatie.

4. Vergroot de **Tekengrootte** in **10 punten** en wijzig de **Lettertypefamilie** in **Segoe (Bold)** .

5. Experimenteer met andere opmaakopties en -instellingen om het uiterlijk van uw visualisaties te wijzigen. 

   ![Visualisaties](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>Meer visualisaties maken

Zoals u ziet, is het zeer eenvoudig om visualisaties in uw rapport aan te passen om de gegevens te presenteren op de manieren waarop u wilt. Probeer bijvoorbeeld met behulp van de geïmporteerde Facebook-gegevens dit lijndiagram te maken met het aantal opmerkingen gedurende een bepaalde periode.

![Lijndiagram](media/desktop-tutorial-facebook-analytics/moreviz.png)

Power BI Desktop biedt een naadloze complete ervaring voor het ophalen van gegevens uit een breed scala aan gegevensbronnen en het vormgeven van deze gegevens om te voldoen aan uw analysebehoeften. Zo kunt u deze gegevens op uitgebreide en interactieve manieren visualiseren. Wanneer uw rapport klaar is, kunt u [het uploaden naar de Power BI-service](desktop-upload-desktop-files.md) en op basis van dit rapport dashboards maken die u kunt delen met andere Power BI-gebruikers.

## <a name="next-steps"></a>Volgende stappen
* [Andere zelfstudies voor Power BI Desktop lezen](https://go.microsoft.com/fwlink/?LinkID=521937)
* [Power BI Desktop-video's bekijken](https://go.microsoft.com/fwlink/?LinkID=519322)
* [Een bezoek brengen aan het Power BI-forum](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Het Power BI-blog lezen](https://go.microsoft.com/fwlink/?LinkID=519327)

