---
title: 'Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen'
description: 'Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 42e3a95e344e17d1ceba11911fc8aa349ebafd0c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858556"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen

Het inhoudspakket Voorbeeld van een retailanalyse bevat een dashboard, rapport en gegevensset waarmee verkoopgegevens van artikelen worden geanalyseerd die zijn verkocht in verschillende winkels en regio's. De metrische gegevens vergelijken de prestaties van dit jaar met die van vorig jaar voor de volgende gebieden: omzet, eenheden, brutomarge, afwijkingen en analyses van nieuwe winkels. 

![Dashboard voor Retail Analysis Sample](media/sample-retail-analysis/retail1.png)

Dit voorbeeld maakt deel uit van een serie die laat zien hoe u Power BI kunt gebruiken met bedrijfsgegevens, rapporten en dashboards. Het voorbeeld is door [obviEnce](http://www.obvience.com/) met echte, geanonimiseerde gegevens gemaakt. De gegevens zijn beschikbaar in verschillende indelingen: inhoudspakket, een PBIX-bestand van Power BI Desktop of een Excel-werkmap. Zie [Voorbeelden voor Power BI](sample-datasets.md). 

In deze zelfstudie gebruiken we het inhoudspakket Voorbeeld van een retailanalyse in de Power BI-service. Omdat de rapportervaringen in Power BI Desktop en in de service zo vergelijkbaar zijn, kunt u de zelfstudie ook volgen met het PBIX-voorbeeldbestand in Power BI Desktop. 

U hebt geen licentie voor Power BI nodig om de voorbeelden te bekijken in Power BI Desktop. Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte in de Power BI-service. 

## <a name="get-the-sample"></a>Het voorbeeld ophalen

 Voordat u het voorbeeld kunt gebruiken, moet u het eerst downloaden als een [inhoudspakket](#get-the-content-pack-for-this-sample), een [PBIX-bestand](#get-the-pbix-file-for-this-sample) of een [Excel-werkmap](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Het inhoudspakket voor dit voorbeeld ophalen

1. Open de Power BI-service (app.powerbi.com), meld u aan en open de werkruimte waar u het voorbeeld wilt opslaan. 

    Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte.

2. Selecteer **Gegevens ophalen** in de linkerbenedenhoek.

    ![Selecteer Gegevens ophalen](media/sample-datasets/power-bi-get-data.png)
3. Selecteer **Voorbeelden** op de pagina **Gegevens ophalen** die wordt weergegeven.
   
4. Selecteer **Voorbeeld van een retailanalyse** en kies **Verbinden**.  
  
   ![Verbinding maken met voorbeeld](media/sample-retail-analysis/retail16.png)
   
5. Het inhoudspakket wordt geïmporteerd in Power BI en er wordt een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset toegevoegd aan de huidige werkruimte.
   
   ![De vermelding Retail Analysis Sample](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Het pbix-bestand voor dit voorbeeld ophalen

U kunt het voorbeeld ook downloaden als een [.pbix-bestand](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix), dat bedoeld is voor gebruik met Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>De Excel-werkmap ophalen voor dit voorbeeld

Als u de gegevensbron voor dit voorbeeld wilt bekijken, is dit ook beschikbaar als [Excel-werkmap](https://go.microsoft.com/fwlink/?LinkId=529778). De werkmap bevat Power View-werkbladen die u kunt bekijken en wijzigen. Als u de onbewerkte gegevens wilt zien, schakelt u de invoegtoepassingen van Gegevensanalyse in en selecteert u vervolgens **Power Pivot > Beheren**. Als u de Power View- en Power Pivot-invoegtoepassingen wilt inschakelen, raadpleegt u [De Excel-voorbeelden in Excel bekijken](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) voor meer informatie.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Rapport openen op dashboard

1. Ga naar de werkruimte waarin u het voorbeeld hebt opgeslagen. Open het tabblad **Dashboards**, zoek het dashboard **Retail Analysis Sample** en selecteer het. 
2. Selecteer in het dashboard de tegel **Total Stores New & Existing Stores** om de pagina **Store Sales Overview** te openen in het rapport Retail Analysis Sample. 

   ![Tegel Totaal aantal winkels](media/sample-retail-analysis/retail-analysis-7.png)  

   Op deze pagina van het rapport ziet u dat we in totaal 104 winkels hebben, waarvan er 10 nieuw zijn. We hebben ketens: Fashions Direct en Lindseys. Fashions Direct-winkels zijn gemiddeld groter.
3. Selecteer in het cirkeldiagram **This Year Sales per Chain** de keten **Fashions Direct**.

   ![De grafiek This Year Sales per Chain](media/sample-retail-analysis/retail3.png)  

   Bekijk het bellendiagram **Total Sales Variance %** :

   ![De grafiek Total Sales Variance %](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   Het district **FD-01** heeft de hoogste gemiddelde omzet per vierkante meter (**Sales Per Sq Ft**) en FD-02 heeft de laagste variantie in omzet (**Total Sales Variance**) vergeleken met vorig jaar. FD-03 en FD 04 presteren algemeen gezien het slechtst.
4. Selecteer afzonderlijke bellen of andere grafieken om overal andere gegevens te markeren, zodat u de impact van uw selecties kunt zien.
5. Selecteer in de bovenste navigatievenster **Voorbeeld van een retailanalyse** om terug te keren naar het dashboard.

   ![Navigatiebalk](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. Selecteer in het dashboard de tegel **This Year's Sales New & Existing Stores**. U kunt deze tegel ook weergeven door *This year sales* te typen in het invoervak van Q&A.

   ![De tegel This Year's Sales](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   De Q&A-resultaten worden weergegeven:

   ![This year's sales in Q&A](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Een tegel die is gemaakt met Q&A van Power BI
Laten we eens wat specifieke gegevens bekijken.

1. Wijzig de vraag in _this year sales **by district**_ . Bekijk het resultaat: Het antwoord wordt automatisch uitgezet in een staafdiagram en u krijgt ook andere suggesties:

   ![This year's sales by district in Q&A](media/sample-retail-analysis/retail8.png)
2. Wijzig de vraag nu in _this year sales **by zip and chain**_ .

   U ziet het antwoord verschijnen in de juiste grafieken terwijl u de vraag typt.
3. Experimenteer met andere vragen en kijk wat voor soort resultaten u krijgt.
4. Als u klaar bent, gaat u terug naar het dashboard.

## <a name="dive-deeper-into-the-data"></a>Dieper in de gegevens duiken
Nu gaan we gaan meer op detailniveau kijken, met name naar de prestaties van de districten.

1. Selecteer in het dashboard de tegel **This Year's Sales, Last Year's Sales** om de pagina **District Monthly Sales** van het rapport te openen.

   ![De tegel This Year's Sales, Last Year's Sales](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   In de grafiek **Total Sales Variance % per FiscalMonth** ziet u grote verschillen voor wat betreft het totale afwijkingspercentage voor verkopen ten opzichte van vorig jaar, waarbij met name januari, april en juli slechte maanden waren.

   ![De grafiek Total Sales Variance % by Fiscal Month](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Laten we eens kijken of we kunnen zien waar de problemen zitten.
2. Selecteer in het bellendiagram de bel **020-Mens**.

   ![Selecteer 020-Mens](media/sample-retail-analysis/retail11.png)  

   U ziet dat de mannenkleding in april beter heeft verkocht dan het bedrijf als geheel, maar dat januari en juli nog steeds probleemmaanden zijn.
1. Selecteer de bel **010-Womens**.

   ![Selecteer 010-Womens](media/sample-retail-analysis/retail12.png)

   U ziet dat de dameskleding gedurende alle maanden veel slechter heeft gepresteerd dan de overige categorieën, en veel slechter in bijna elke maand vergeleken met afgelopen jaar.
1. Selecteer de bel opnieuw om het filter te wissen.

## <a name="try-out-the-slicer"></a>De slicer uitproberen
Laten we eens kijken hoe specifieke districten het doen.

1. Selecteer **Allan Guinot** in de slicer **District Manager** linksboven.

   ![Selecteer Allan Guinot](media/sample-retail-analysis/retail13.png)

   U ziet dat zijn district een beter dan gemiddelde omzet haalde in maart en juni, vergeleken met vorig jaar.
2. Laat **Allan Guinot** geselecteerd en selecteer de bel **Womens-10** in het bellendiagram.

   ![Allan Guinot en Womens-10 geselecteerd](media/sample-retail-analysis/power-bi-allan.png)

   U ziet dat het district van Allan vorig jaar niet het gewenste volume heeft gehaald voor de categorie Womens-10.
3. Verken de andere districtmanagers en categorieën. Welke inzichten kunt u nog meer vinden?
4. Als u klaar bent, gaat u terug naar het dashboard.

## <a name="what-the-data-says-about-sales-growth-this-year"></a>Wat de gegevens zeggen over de omzetgroei dit jaar
Het laatste onderdeel dat we willen verkennen is onze groei, door te kijken naar de nieuwe winkels die we dit jaar hebben geopend.

1. Selecteer de tegel **Stores Opened This Year by Open Month, Chain** om de pagina **New Stores Analysis** van het rapport te openen.

   ![De pagina New Stores Analysis](media/sample-retail-analysis/retail15.png)

   Zoals u kunt zien op de tegel, zijn er dit jaar meer Fashions Direct-winkels geopend dan vestigingen van Lindseys.
2. Kijk eens naar de grafiek **Sales Per Sq Ft per Name**:

   ![De grafiek Sales Per Sq Ft per Name](media/sample-retail-analysis/retail14.png)

    Let op het verschil in gemiddelde verkoop/vierkant meter voor de nieuwe winkels.
3. Selecteer **Fashions Direct** in de legenda van de grafiek **Open Store Count per Open Month en Chain** rechtsboven. U ziet dat, zelfs voor dezelfde keten, de beste winkel (Winchester Fashions Direct) aanzienlijk beter presteert dan de slechtste winkel (Cincinnati 2 Fashions Direct), met $ 21,22 tegenover $ 12,86 respectievelijk.

   ![Fashions Direct geselecteerd](media/sample-retail-analysis/power-bi-lindseys.png)
4. Selecteer **Winchester Fashions Direct** in de slicer **Name** en kijk naar het lijndiagram. De eerste omzetcijfers zijn voor februari.
5. Selecteer **Cincinnati 2 Fashions Direct** in de slicer en u ziet in het lijndiagram dat deze winkel is geopend in juni en de slechtste presterende winkel lijkt te zijn.
6. Bekijk andere gegevens door op andere staven, lijnen en bellen in de grafieken te klikken en te kijken welke inzichten u kunt vaststellen.

## <a name="next-steps-connect-to-your-data"></a>Volgende stappen: Verbinding maken met uw gegevens
Dit is een veilige omgeving om in te experimenten, omdat er geen optie is om uw wijzigingen op te slaan. Als u dat toch doet, kunt u altijd **Gegevens ophalen** selecteren voor een nieuw exemplaar van dit voorbeeld.

We hopen dat deze rondleiding heeft laten zien hoe Power BI-dashboards, Q&A en rapporten inzicht kunnen geven in voorbeeldgegevens. Nu is het uw beurt om verbinding met uw eigen gegevens te maken. Met Power BI kunt u verbinding maken met een groot aantal gegevensbronnen. Zie [Aan de slag met de Power BI-service](service-get-started.md) voor meer informatie.
