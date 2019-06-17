---
title: 'Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen'
description: 'Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen'
author: maggiesMSFT
manager: kfile
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2018
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 04676ee789b90eb09cbed3bafb623e8e9b89e4e4
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66720873"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Voorbeeld van een retailanalyse voor Power BI: Rondleiding volgen

In dit voorbeelddashboard en het onderliggende rapport met bedrijfsgegevens worden de verkoopgegevens uit de detailhandel geanalyseerd van artikelen die in verschillende winkels en gebieden zijn verkocht. Met de metrische gegevens vergelijkt u de prestaties van dit jaar met die van vorig jaar voor de volgende gebieden: omzet, eenheden, brutomarge, afwijkingen en analyses van nieuwe winkels. Dit zijn echte gegevens die afkomstig zijn van obviEnce ([www.obvience.com)](http://www.obvience.com) die zijn geanonimiseerd.

![](media/sample-retail-analysis/retail1.png)

## <a name="prerequisites"></a>Vereisten

 Voordat u het voorbeeld kunt gebruiken, moet u het eerst downloaden als een [inhoudspakket](https://docs.microsoft.com/power-bi/sample-datasets#get-and-open-a-sample-content-pack-in-power-bi-service), een [PBIX-bestand](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) of een [Excel-werkmap](http://go.microsoft.com/fwlink/?LinkId=529778).


### <a name="get-the-content-pack-for-this-sample"></a>Het inhoudspakket voor dit voorbeeld ophalen

1. Open Power BI-service (app.powerbi.com) en meld u aan.
2. Selecteer in de linkerbendehoek **Gegevens ophalen**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. Selecteer op de pagina Gegevens ophalen het pictogram **Voorbeelden**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Selecteer **Voorbeeld van een retailanalyse** en kies **Verbinding maken**.  
  
   ![Voorbeeld van een retailanalyse](media/sample-retail-analysis/retail16.png)
   
5. Het inhoudspakket wordt geïmporteerd in Power BI en er wordt een nieuw dashboard, nieuw rapport en een nieuwe gegevensset toegevoegd aan de huidige werkruimte. De nieuwe inhoud is gemarkeerd met een geel sterretje. 
   
   ![Voorbeeld van een retailanalyse](media/sample-retail-analysis/retail17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Het pbix-bestand voor dit voorbeeld ophalen

U kunt ook het voorbeeld downloaden als pbix-bestand, dat bedoeld is voor gebruik met Power BI Desktop. 

 * [Voorbeeld van een retailanalyse](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>De Excel-werkmap ophalen voor dit voorbeeld
U kunt ook [alleen de gegevensset (Excel-werkmap)](http://go.microsoft.com/fwlink/?LinkId=529778) voor dit voorbeeld downloaden. De werkmap bevat Power View-werkbladen die u kunt bekijken en wijzigen. Als u de onbewerkte gegevens wilt bekijken, selecteert u **Power Pivot > Beheren**.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Rapport openen op dashboard
1. Selecteer de tegel 'Total Stores' op het dashboard:

   ![](media/sample-retail-analysis/retail-analysis-7.png)  

   Hiermee gaat u naar de pagina 'Store Sales Overview' in het rapport. U ziet dat we in totaal 104 winkels hebben, waarvan er tien nieuw zijn. We hebben ketens: Fashions Direct en Lindseys. Fashions Direct-winkels zijn gemiddeld groter.
2. Selecteer in het cirkeldiagram **Fashions Direct**.

   ![](media/sample-retail-analysis/retail3.png)  

   Kijk wat er in het bellendiagram gebeurt:

   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   Het district FD-01 heeft de hoogste gemiddelde omzet per vierkante meter, FD-02 heeft de laagste variantie in omzet vergeleken met vorig jaar, FD-03 en FD 04 presteren algemeen gezien het slechtst.
3. Selecteer afzonderlijke bellen of andere grafieken om overal andere gegevens te markeren, zodat u de impact van uw selecties kunt zien.
4. Als u terug wilt naar het dashboard, selecteert u de naam van het dashboard in de bovenste navigatiebalk (breadcrumbs).

   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. Selecteer op het dashboard de tegel 'This Year’s Sales'.

   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Dit heeft hetzelfde effect als het typen van 'This Year’s Sales in het vragenvak.

   U ziet dit scherm:

   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Een tegel die is gemaakt met Q&A van Power BI
Laten we eens wat specifieke gegevens bekijken.

1. Stel de vraag 'this year sales **by district**'. Bekijk het resultaat: Het antwoord wordt automatisch uitgezet in een staafdiagram en u krijgt ook andere suggesties:

   ![](media/sample-retail-analysis/retail8.png)
2. Verander de vraag in 'this year sales **by zip and chain**'.

   U ziet het antwoord verschijnen in de juiste grafieken terwijl u de vraag typt.
3. Experimenteer met andere vragen en kijk wat voor soort resultaten u krijgt.
4. Als u klaar bent, gaat u terug naar het dashboard.

## <a name="dive-deeper-into-the-data"></a>Dieper in de gegevens duiken
Nu gaan we gaan meer op detailniveau kijken, met name naar de prestaties van de districten.

1. Selecteer op het dashboard de tegel waarop de omzet van vorig jaar en dit jaar wordt vergeleken.

   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Let vooral op het grote verschil in het variantiepercentage. Vooral in de maanden januari, april en juli is vorig jaar veel meer omzet gehaald dan dit jaar.

   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Laten we eens kijken of we kunnen zien waar de problemen zitten.
2. Selecteer **020-Mens** in het bellendiagram.

   ![](media/sample-retail-analysis/retail11.png)  

   U ziet dat de mannenkleding in april beter heeft verkocht dan het bedrijf als geheel, maar januari en juli zijn nog steeds probleemmaanden.
3. Selecteer nu de bel **010-Womens**.

   ![](media/sample-retail-analysis/retail12.png)

   U ziet dat de dameskleding gedurende alle maanden veel slechter heeft gepresteerd dan de overige categorieën, en veel slechter in bijna elke maand vergeleken met afgelopen jaar.
4. Selecteer de bel opnieuw om het filter te wissen.

## <a name="try-out-the-slicer"></a>De slicer uitproberen
Laten we eens kijken hoe specifieke districten het doen.

1. Selecteer Allan Guinot in de slicer linksboven.

   ![](media/sample-retail-analysis/retail13.png)

   U ziet dat zijn district vorig jaar een beter dan gemiddeld omzet haalde in maart en juni.
2. Selecteer nu de bel voor dameskleding.

   ![](media/sample-retail-analysis/power-bi-allan.png)

   Het valt meteen op dat zijn district voor de categorie dameskleding nooit de omzetcijfers van vorig jaar heeft gehaald.
3. Verken de andere districtmanagers en categorieën. Welke inzichten kunt u nog meer vinden?
4. Als u klaar bent, gaat u terug naar het dashboard.

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>Wat vertellen onze gegevens ons over omzetgroei dit jaar?
Het laatste onderdeel dat we willen verkennen is onze groei, aangezien er dit jaar weer nieuwe winkels zijn geopend.

1. Selecteer de tegel 'Stores Opened This Year’.

   ![](media/sample-retail-analysis/retail15.png)

   Zoals u kunt zien op de tegel, zijn er dit jaar meer Fashions Direct-winkels geopend dan vestigingen van Lindseys.
2. Kijk eens naar de grafiek 'Sales Per Sq Ft per Name':

   ![](media/sample-retail-analysis/retail14.png)

    Er is nogal wat verschil in de gemiddelde omzet per vierkante meter in de nieuwe winkels.
3. Klik op Fashions Direct in de legenda van de grafiek rechtsboven. U ziet dat, zelfs voor dezelfde keten, de beste winkel (Winchester Fashions Direct) aanzienlijk beter presteert dan de slechtste winkel (Cincinnati 2 Fashions Direct), met $ 21,22 tegenover $ 12,86 respectievelijk.

   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. Klik op Winchester Fashions Direct in de slicer en bekijk het lijndiagram. De eerste omzetcijfers zijn voor februari.
5. Klik op Cincinnati 2 Fashions Direct in de slicer en u ziet in het lijndiagram dat deze winkel is geopend in juni en de slechtste presterende winkel lijkt te zijn.
6. Net als in eerdere weergaven, kunt u de gegevens verkennen door op andere staven, lijnen en bellen in de grafieken te klikken en te kijken welke inzichten u kunt vaststellen.

Dit is een veilige omgeving om in te experimenteren. U kunt er namelijk altijd voor kiezen de wijzigingen niet op te slaan. Als u deze wel opslaat, kunt u altijd naar Gegevens ophalen gaan voor een nieuwe kopie van dit voorbeeld.

## <a name="connect-to-your-data"></a>Verbinding maken met uw gegevens
We hopen dat deze rondleiding heeft laten zien hoe Power BI-dashboards, Q&A en rapporten inzicht kunnen geven in retailgegevens. Nu is het uw beurt om verbinding met uw eigen gegevens te maken. Met Power BI kunt u verbinding maken met een groot aantal gegevensbronnen. Zie [Aan de slag met Power BI](service-get-started.md) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen
* [Het inhoudspakket Retail Analysis Sample downloaden](sample-tutorial-connect-to-the-samples.md)
* [Een ZIP-bestand van alle voorbeeldbestanden downloaden](http://go.microsoft.com/fwlink/?LinkId=535020)    
* [De Excel-werkmap voor dit Power BI-voorbeeld downloaden](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [Gegevens ophalen (voor Power BI)](service-get-data.md)    
* [Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md)    
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
