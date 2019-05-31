---
title: 'Zelfstudie: Gegevens uit Excel en een OData-feed combineren in Power BI Desktop'
description: 'Zelfstudie: Gegevens uit Excel en een OData-feed combineren'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/21/2018
ms.author: v-thepet
LocalizationGroup: Learn more
ms.openlocfilehash: 94e40681d065591db008f8a9062d851e0bd83f61
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61368339"
---
# <a name="tutorial-combine-sales-data-from-excel-and-an-odata-feed"></a>Zelfstudie: Verkoopgegevens uit Excel en een OData-feed combineren

Het komt vaak voor dat gegevens over meerdere gegevensbronnen zijn verdeeld, bijvoorbeeld de productgegevens in de ene database en de verkoopgegevens in de andere. Met **Power BI Desktop** kunt u gegevens uit verschillende bronnen combineren om interessante en aantrekkelijke gegevensanalyses en -visualisaties te maken. 

In deze zelfstudie leert u hoe gegevens uit twee gegevensbronnen kunt combineren: een Excel-werkmap met de productgegevens en een OData-feed met de ordergegevens. Nadat u alle gegevenssets hebt geïmporteerd en de transformatie- en aggregatiestappen hebt uitgevoerd, gebruikt u de gegevens uit beide bronnen om een verkoopanalyserapport met interactieve visualisaties te genereren. Deze technieken kunnen ook worden toegepast op de SQL Server-query's, CSV-bestanden en andere gegevensbronnen in Power BI Desktop.

>[!NOTE]
>In Power BI Desktop zijn er vaak een aantal manieren om een taak uit te voeren. Veel lintselecties zijn bijvoorbeeld ook beschikbaar door met de rechtermuisknop te klikken, of via het menu **Meer opties** in een kolom of cel. In de onderstaande stappen worden verschillende alternatieve methoden beschreven. 

## <a name="import-the-product-data-from-excel"></a>De productgegevens importeren uit Excel

Importeert eerst de productgegevens uit de Excel-werkmap Products.xlsx in Power BI Desktop.

1. [Download de Excel-werkmap Products.xlsx](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Products.xlsx) en sla de werkmap op als **Products.xlsx**.
   
2. Selecteer de pijl naast **Gegevens ophalen** op het tabblad **Start** op het Power BI Desktop-lint. Selecteer **Excel** in de vervolgkeuzelijst **Meest voorkomend**. 
   
   ![Gegevens ophalen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_1.png)
   
   >[!NOTE]
   >U kunt ook het item **Gegevens ophalen** zelf selecteren of **Gegevens ophalen** in het dialoogvenster **Aan de slag** in Power BI selecteren en vervolgens **Excel** of **Bestand** > **Excel** selecteren in het dialoogvenster **Gegevens ophalen**. Selecteer vervolgens **Verbinding maken**.
   
3. Navigeer in het dialoogvenster **Openen** naar het bestand **Products.xlsx**, selecteer het bestand en kies **Openen**.
   
4. In het deelvenster **Navigator** selecteert u de tabel **Products** en selecteert u vervolgens **Bewerken**.
   
   ![Navigator-deelvenster voor Excel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_2.png)
   
In **Power Query-editor** wordt een voorbeeld van de tabel geopend, waarin u transformaties kunt toepassen om de gegevens op te schonen. 
   
![Power Query-editor](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_3.png)
   
>[!NOTE]
>U kunt **Power Query-editor** ook openen door **Query's bewerken** > **Query's bewerken** te selecteren in **Start** op het lint in Power BI Desktop, of door met de rechtermuisknop te klikken op **Meer opties** of deze optie te kiezen naast een query in de **rapportweergave**. Selecteer vervolgens **Query bewerken**.

## <a name="clean-up-the-products-columns"></a>De productkolommen opschonen

In het gecombineerde rapport worden alleen de kolommen **ProductID**, **ProductName**, **QuantityPerUnit** en **UnitsInStock** uit de Excel-werkmap gebruikt. De overige kolommen kunnen dus worden verwijderd. 

1. Selecteer in **Power Query-editor** de kolommen **ProductID**, **ProductName**, **QuantityPerUnit** en **UnitsInStock** (gebruik **Ctrl**+**klikken** om meer dan één kolom te selecteren of **Shift**+**klikken** om kolommen naast elkaar te selecteren).
   
2. Klik met de rechtermuisknop op een van de geselecteerde koppen en selecteer **Overige kolommen verwijderen** in de vervolgkeuzelijst om alle kolommen met uitzondering van de geselecteerde kolommen uit de tabel te verwijderen. 
   U kunt ook **Kolommen verwijderen** > **Overige kolommen verwijderen** selecteren in de groep **Kolommen beheren** op het tabblad **Start** op het lint. 
   
   ![Overige kolommen verwijderen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_removeothercolumns.png)

## <a name="import-the-order-data-from-an-odata-feed"></a>De ordergegevens importeren uit een OData-feed

Vervolgens importeert u de ordergegevens uit de OData-feed van het Northwind-voorbeeldverkoopsysteem. 

1. Selecteer **Nieuwe bron** in **Power Query-editor** en selecteer **OData-feed** in de vervolgkeuzelijst **Meest voorkomend**. 
   
   ![OData ophalen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata.png)
   
2. Plak de URL voor de OData-feed Northwind in het dialoogvenster **OData-feed**, `http://services.odata.org/V3/Northwind/Northwind.svc/`, en selecteer **OK**.
   
   ![Dialoogvenster OData-feed](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/get_odata2.png)
   
3. Selecteer in het **Navigator**-deelvenster de tabel **Orders** en selecteer **OK** om de gegevens in **Power Query-editor** te laden.
   
   ![Navigator-deelvenster voor OData](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/analyzingsalesdata_odatafeed.png)
   
   >[!NOTE]
   >In **Navigator** kunt u een tabelnaam selecteren (zonder het selectievakje te selecteren) om een voorbeeld te bekijken.

## <a name="expand-the-order-data"></a>De ordergegevens uitvouwen

Als u verbinding maakt met gegevensbronnen die meerdere tabellen bevatten, zoals relationele databases of de OData-feed Northwind, kunt u verwijzingen tussen de tabellen gebruiken om uw query's op te bouwen. De tabel **Orders** bevat verwijzingen naar verschillende verwante tabellen. U kunt de kolommen **ProductID**, **UnitPrice** en **Quantity** uit de verwante tabel **Order_Details** toevoegen aan de onderwerptabel (**Orders**). Hiervoor gebruikt u de bewerking **Uitvouwen**. 

1. Schuif naar rechts in de tabel **Orders** totdat u de kolom **Order_Details** ziet. In de tabel worden geen gegevens, maar verwijzingen naar de andere tabel weergegeven.
   
   ![Kolom Order_Details](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/7.png)
   
2. Selecteer het pictogram **Uitvouwen** (![Pictogram Uitvouwen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/expand.png)) in de kolomkop **Order_Details**. 
   
3. In de vervolgkeuzelijst **Uitbreiden**:
   
   1. Selecteer **(Alle kolommen selecteren)** om alle kolommen te wissen.
      
   2. Selecteer **ProductID**, **UnitPrice** en **Quantity**, en selecteer vervolgens **OK**.
      
      ![Dialoogvenster Uitvouwen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/8.png)

Nadat u de tabel **Order_Details** hebt uitgevouwen, wordt de kolom **Order_Details** vervangen door de drie nieuwe kolommen uit de geneste tabel. Daarnaast zijn er in de tabel nieuwe rijen voor de toegevoegde gegevens uit elke order. 

![Uitgevouwen kolommen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/9.png)

## <a name="create-a-custom-calculated-column"></a>Een aangepaste berekende kolom maken

In Power Query-editor kunt u aangepaste berekeningen en aangepaste velden maken om uw gegevens te verrijken. U maakt een aangepaste kolom waarmee de totaalprijs voor elk regelartikel in een order wordt berekend door de prijs per eenheid te vermenigvuldigen met de artikelhoeveelheid.

1. Selecteer **Aangepaste kolom** op het tabblad **Kolom toevoegen** op het lint van Power Query-editor.
   
   ![](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/10.png)
   
2. Typ **LineTotal** in het veld **Nieuwe kolomnaam** van het dialoogvenster **Aangepaste kolom**.

3. Voer **[Order_Details.UnitPrice]** \* **[Order_Details.Quantity]** in het veld **Aangepaste kolomformule** in, achter het teken **=** . (U kunt ook de veldnamen selecteren in het schuifblok **Beschikbare kolommen** en **<< Invoegen** selecteren in plaats van de namen te typen.) 
3. Selecteer **OK**.
   
   ![Dialoogvenster Aangepaste kolom](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/11.png)

Het nieuwe veld **LineTotal** wordt als laatste kolom in de tabel **Orders** weergegeven.

## <a name="set-the-data-type-for-the-new-field"></a>Het gegevenstype voor het nieuwe veld instellen

Tijdens het maken van verbinding met gegevens in Power Query-editor wordt automatisch bepaald wat het beste gegevenstype voor elk veld is, waarna de gegevens dienovereenkomstig worden weergegeven. De pictogrammen in de koppen geven aan welke gegevenstypen aan de velden zijn toegewezen. De gegevenstypen kunt u ook bekijken onder **Gegevenstype** in de groep **Transformeren** van het tabblad **Start** op het lint. 

De gegevenstype van de nieuwe kolom **LineTotal** is **Willekeurig**, maar de waarden zijn valuta's. Als u een gegevenstype wilt toewijzen, klikt u met de rechtermuisknop op de kolomkop **LineTotal**, selecteert u **Gegevenstype wijzigen** in de vervolgkeuzelijst en selecteert u vervolgens **Vast decimaal getal**. 

![Gegevenstype wijzigen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/12.png)

>[!NOTE]
>U kunt ook de kolom **LineTotal** selecteren, de pijl naast **Gegevenstype** in het gebied **Transformeren** van het tabblad **Start** op het lint selecteren en vervolgens **Vast decimaal getal** selecteren.

## <a name="clean-up-the-orders-columns"></a>De orderkolommen opschonen

U kunt in rapporten gemakkelijker met uw model werken door bepaalde kolommen te verwijderen, te rangschikken en de namen van de kolommen te wijzigen.

In uw rapport worden alleen de kolommen **OrderDate**, **ShipCity**, **ShipCountry**, **Order_Details.ProductID**, **Order_Details.UnitPrice** en **Order_Details.Quantity** gebruikt. U kunt deze kolommen selecteren en **Overige kolommen verwijderen** gebruiken (zoals u ook hebt gedaan met de Excel-gegevens), of u kunt alle kolommen behalve de weergegeven kolommen selecteren, met de rechtermuisknop op een van de geselecteerde kolommen klikken en **Kolommen verwijderen** selecteren om alle kolommen te verwijderen. 

U kunt ervoor zorgen dat de kolommen **Order_Details.ProductID**, **Order_Details.UnitPrice** en **Order_Details.Quantity** makkelijker te vinden zijn door de voorvoegsels *Order_Details.* uit de kolomnamen te verwijderen. Ga als volgt te werk om de namen van de kolommen te wijzigen in respectievelijk **ProductID**, **UnitPrice** en **Quantity**:

1. Dubbelklik of tik op elke kolomkop en houd deze ingedrukt, of klik met de rechtermuisknop op de kolomkop en selecteer **Naam wijzigen** in de vervolgkeuzelijst. 
2. Verwijder het voorvoegsel *Order_Details.* uit elke naam en druk vervolgens op **Enter**.

Als u de kolom **LineTotal** toegankelijker wilt maken, sleept u de kolom naar links en zet u deze rechts van de kolom **ShipCountry** neer.

![Opgeschoonde tabel](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/14.png)

## <a name="review-the-query-steps"></a>De querystappen bekijken

Tijdens het vormgeven en transformeren van gegevens in Power Query-editor wordt elke stap vastgelegd in het gebied **Toegepaste stappen** van het deelvenster **Queryinstellingen** aan de rechterkant van het venster van Power Query-editor. U kunt stap voor stap terug door de toegepaste stappen lopen om te zien welke wijzigingen u hebt aangebracht en deze indien nodig bewerken, verwijderen of opnieuw rangschikken (hoewel dit riskant kan zijn, omdat het wijzigen van de voorgaande stappen later fouten kan veroorzaken in stappen). 

Selecteer uw query's in de lijst **Query's** aan de linkerkant van Power Query-editor en bekijk de **toegepast stappen** in **Query-instellingen**. Nadat de vorige gegevenstransformaties zijn toegepast, moeten de toegepaste stappen voor uw twee query's er als volgt uitzien:

![Toegepaste stappen voor query voor producten](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/15.png) &nbsp;&nbsp; ![Toegepaste stappen voor query voor orders](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/17.png)

>[!TIP]
>Onder de Toegepaste stappen liggen formules die geschreven zijn in de **Power Query-taal**, ook wel bekend als de **M**-taal. Als u de formules wilt bekijken en bewerken, selecteert u **Geavanceerde editor** in de groep **Query** van het tabblad Start van het lint. 

## <a name="import-the-transformed-queries"></a>De getransformeerde query's importeren

Wanneer u tevreden bent met de gegevens, selecteert u **Sluiten en toepassen** > **Sluiten en toepassen** in de groep **Sluiten** van het tabblad **Start** op het lint om de gegevens te importeren in de rapportweergave in Power BI Desktop. 

![Sluiten en toepassen](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_4.png)

Wanneer de gegevens zijn geladen, worden de query's weergegeven in de lijst **Velden** in de rapportweergave in Power BI Desktop.

![Query's in lijst Velden](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/18.png)

## <a name="manage-the-relationship-between-the-datasets"></a>De relatie tussen de gegevenssets beheren

In Power BI Desktop hoeft u niet query's te combineren om erover te rapporteren. U kunt echter de relaties tussen gegevenssets gebruiken (op basis van velden die ze gemeen hebben) om uw rapporten uit te breiden en te verrijken. In Power BI Desktop kunnen relaties automatisch worden gedetecteerd, maar u kunt ze ook maken in het dialoogvenster **Relaties beheren**. Zie [Relaties maken en beheren in Power BI Desktop](desktop-create-and-manage-relationships.md) voor meer informatie over relaties in Power BI Desktop.

De gegevenssets voor orders en producten in deze zelfstudie delen een gemeenschappelijk veld, *ProductID*, dus op basis van deze kolom is er een relatie tussen deze gegevenssets. 

1. Selecteer in de rapportweergave in Power BI Desktop de optie **Relaties beheren** in het gebied **Relaties** op het tabblad **Start** van het lint.
   
   ![Relaties beheren op het lint](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_5.png)
   
2. In het dialoogvenster **Relaties beheren** ziet u dat in Power BI Desktop al een actieve relatie tussen de tabellen met producten en orders is gedetecteerd die wordt weergegeven. Selecteer **Bewerken** om de relatie weer te geven. 
   
   ![Dialoogvenster Relaties beheren](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_6.png)
   
   Het dialoogvenster **Relatie bewerken** wordt geopend, met de details over de relatie.  
   
   ![Dialoogvenster Relatie bewerken](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_7.png)
   
3. De relatie is op de juiste manier automatisch gedetecteerd in Power BI Desktop. U kunt dus **Annuleren** en vervolgens **Sluiten** selecteren om de dialoogvensters voor de relatie af te sluiten.

U kunt ook de relaties tussen uw query's weergeven en beheren door de weergave **Relatie** aan de linkerkant van het Power BI Desktop-venster te selecteren. Dubbelklik op de pijl op de lijn die de twee query's verbindt om het dialoogvenster **Relatie bewerken** te openen en de relatie weer te geven of te wijzigen. 

![Relatieweergave](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_8.png)

Als u vanuit de relatieweergave terug wilt gaan naar de rapportweergave, selecteert u het pictogram **Rapportweergave**. 

![Het pictogram Rapportweergave](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/t_excelodata_9.png)

## <a name="create-visualizations-using-your-data"></a>Visualisaties maken met behulp van uw gegevens

In de rapportweergave van Power BI Desktop kunt u een aantal visualisaties maken om inzicht in uw gegevens te krijgen. U kunt rapporten met meerdere pagina's maken en elke pagina kan meerdere visuals bevatten. U en andere gebruikers kunnen interactief werken met uw visualisaties om uw gegevens te analyseren en er meer inzicht in te krijgen. Zie het Engelstalige artikel [Edit a Report](service-interact-with-a-report-in-editing-view.md) (Een rapport bewerken) voor meer informatie over het weergeven en bewerken van rapport in de Power BI-service (uw site).

Voor het visualiseren en analyseren van uw verkoopgegevens kunt u beide gegevenssets (en de relatie tussen deze sets) gebruiken. 

Maak eerst een gestapeld kolomdiagram waarin gebruik wordt gemaakt van velden uit beide query's om de hoeveelheid van elk besteld product weer te geven. 

1. Selecteer het veld **Quantity** in **Orders** in het deelvenster **Velden** aan de rechterkant of sleep het veld naar een lege plek op het canvas. Hiermee wordt een gestapeld kolomdiagram gemaakt met de totale hoeveelheid bestelde producten. 
   
2. Selecteer **ProductName** in **Products** in het deelvenster **Velden** of sleep het veld naar de grafiek om de hoeveelheid van elk besteld product weer te geven. 
   
3. Als u de producten wilt sorteren op de minst bestelde hoeveelheden, selecteert u het weglatingsteken ( **...** ) bij **Meer opties** en selecteert u rechts boven in de visualisatie **Op hoeveelheid sorteren**.
   
4. Gebruik de handgrepen in de hoeken van het diagram om het diagram groter te maken zodat meer productnamen zichtbaar zijn. 
   
   ![Staafdiagram met hoeveelheid op ProductName](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/19.png)

Maak vervolgens een diagram met de orderbedragen (**LineTotal**) gedurende een bepaalde periode (**OrderDate**). 

1. Zorg dat er niets is geselecteerd op het canvas, selecteer **LineTotal** in **Orders** in het deelvenster **Velden** of sleep het item naar een lege ruimte op het canvas. Het gestapelde kolomdiagram bevat het totaalbedrag voor alle orders. 
   
2. Selecteer het diagram, selecteer **OrderDate** in **Orders** of sleep het item naar het diagram. Het diagram bevat nu voor elke orderdatum de regeltotalen. 
   
3. U kunt de grootte van de visualisatie aanpassen door de hoeken te verslepen; u kunt dan meer gegevens bekijken. 
   
   ![Lijndiagram LineTotals op OrderDate](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/20.png)
   
   >[!TIP]
   >Als u alleen de jaren in het diagram (slechts drie gegevenspunten) ziet, klikt u op de pijl naast **OrderDate** in het veld **As** van het deelvenster **Visualisaties**. Selecteer vervolgens **OrderDate** in plaats van **Datumhiërarchie**. 

Maak ten slotte een kaartvisualisatie waarin de orderbedragen van elk land worden weergegeven. 

1. Zorg dat er niets is geselecteerd op het canvas, selecteer **ShipCountry** in **Orders** in het deelvenster **Velden** of sleep het item naar een lege ruimte op het canvas. In Power BI Desktop wordt gedetecteerd dat de gegevens uit landnamen bestaan, waarna automatisch een kaartvisualisatie wordt gemaakt met een gegevenspunt voor elk land waarvoor orders bestaan. 
   
2. Als u de orderbedragen voor elk land wilt weergeven aan de hand van de grootte van de gegevenspunten, sleept u het veld **LineTotal** naar de kaart (of sleept u het veld naar **Sleep hier gegevensvelden** onder **Grootte** in de onderste helft van het deelvenster **Visualisaties**). De grootte van de cirkels op de kaart geven nu de bedragen van de orders vanuit elk land weer. 
   
   ![Kaartvisualisatie van LineTotals op ShipCountry](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/21.png)

## <a name="interact-with-your-report-visuals-to-analyze-further"></a>Interactief werken met de visuals in uw rapport voor verdere analyse

Met Power BI Desktop kunt u verdere trends ontdekken door interactief te werken met de visuals, zoals kruislings markeren en filteren. Zie het Engelstalige artikel [Filtering and Highlighting in Reports](power-bi-reports-filters-and-highlighting.md) (Filteren en markeren in rapporten) voor meer informatie. 

Vanwege de relatie tussen uw query's heeft het interactief werken met één visualisatie gevolgen voor alle andere visualisaties op de pagina. 

Selecteer de cirkel in het midden van **Canada** in de kaartvisualisatie. Houd er rekening mee dat met de andere twee visualisaties gegevens alleen worden gefilterd om de regeltotalen en orderhoeveelheden voor Canada te markeren.

![Verkoopgegevens gefilterd voor Canada](media/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed/22.png)

Als u een van de producten in het diagram **Hoeveelheid op ProductName** selecteert, worden het kaart- en datumdiagram gefilterd om de gegevens voor het desbetreffende product weer te geven. Als u een van de datums in het diagram **LineTotal op OrderDate** selecteert, worden het kaart- en het productdiagram gefilterd om de gegevens voor die datum weer te geven. 
>[!TIP]
>Als u een selectie wilt opheffen, selecteert u de visualisatie opnieuw of selecteert u een van de andere visualisaties. 

## <a name="complete-the-sales-analysis-report"></a>Het verkoopanalyserapport voltooien

In het voltooide rapport worden gegevens van het Excel-bestand Products.xlsx samengevoegd met gegevens van de OData-feed Northwind. Deze gegevens worden gecombineerd tot visuals waarmee u ordergegevens voor verschillende landen, perioden en producten kunt analyseren. Wanneer uw rapport klaar is, kunt u [het uploaden naar de Power BI-service](desktop-upload-desktop-files.md) en delen met andere Power BI-gebruikers.

## <a name="next-steps"></a>Volgende stappen
* [Andere zelfstudies voor Power BI Desktop lezen](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Power BI Desktop-video's bekijken](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Een bezoek brengen aan het Power BI-forum](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Het Power BI-blog lezen](http://go.microsoft.com/fwlink/?LinkID=519327)