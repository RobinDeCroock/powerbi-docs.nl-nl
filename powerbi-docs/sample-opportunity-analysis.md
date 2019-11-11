---
title: 'Voorbeeld van een verkoopkansanalyse voor Power BI: Rondleiding volgen'
description: 'Voorbeeld van een verkoopkansanalyse voor Power BI: Rondleiding volgen'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: d871fa15c999e5b6c83b0334d6c978b2ba3c9870
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858708"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Voorbeeld van een verkoopkansanalyse voor Power BI: Rondleiding volgen

Het inhoudspakket Voorbeeld van een verkoopanalyse bevat een dashboard, rapport en gegevensset voor een softwarebedrijf met twee verkoopkanalen: *direct* en *partner*. De salesmanager heeft dit dashboard gemaakt om verkoopkansen en omzet bij te houden per regio, dealgrootte en kanaal.

In dit voorbeeld worden twee soorten omzet gebruikt:

* Revenue (omzet): een schatting door een verkoopmedewerker van de omzet.
* Factored revenue (gewogen omzet): dit wordt berekend als omzet x waarschijnlijkheidspercentage en wordt algemeen gezien als een nauwkeurigere manier om de werkelijke omzet te voorspellen. Waarschijnlijkheid wordt bepaald door de huidige *verkoopfase* van de deal:
  * Lead (potentiële klant): 10%  
  * Qualify (in aanmerking komend): 20%  
  * Oplossing: 40%  
  * Proposal (voorstel): 60%  
  * Finalize (afronden): 80%

![Dashboard voor het voorbeeld van een verkoopkansanalyse](media/sample-opportunity-analysis/opportunity1.png)

Dit voorbeeld maakt deel uit van een serie die laat zien hoe u Power BI kunt gebruiken met bedrijfsgegevens, rapporten en dashboards. Het voorbeeld is door [obviEnce](http://www.obvience.com/) met echte, geanonimiseerde gegevens gemaakt. De gegevens zijn beschikbaar in verschillende indelingen: inhoudspakket, een PBIX-bestand van Power BI Desktop of een Excel-werkmap. Zie [Voorbeelden voor Power BI](sample-datasets.md). 

In deze zelfstudie gebruiken we het inhoudspakket Voorbeeld van een verkoopanalyse in de Power BI-service. Omdat de rapportervaringen in Power BI Desktop en in de service zo vergelijkbaar zijn, kunt u de zelfstudie ook volgen met het PBIX-voorbeeldbestand in Power BI Desktop. 

U hebt geen licentie voor Power BI nodig om de voorbeelden te bekijken in Power BI Desktop. Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte in de Power BI-service. 

## <a name="get-the-sample"></a>Het voorbeeld ophalen

Voordat u het voorbeeld kunt gebruiken, moet u het eerst downloaden als een [inhoudspakket](#get-the-content-pack-for-this-sample), een [PBIX-bestand](#get-the-pbix-file-for-this-sample) of een [Excel-werkmap](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Het inhoudspakket voor dit voorbeeld ophalen

1. Open de Power BI-service (app.powerbi.com), meld u aan en open de werkruimte waar u het voorbeeld wilt opslaan. 

    Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte.

2. Selecteer **Gegevens ophalen** in de linkerbenedenhoek.

    ![Selecteer Gegevens ophalen](media/sample-datasets/power-bi-get-data.png)
3. Selecteer **Voorbeelden** op de pagina **Gegevens ophalen** die wordt weergegeven.

4. Selecteer **Voorbeeld van een verkoopkansanalyse** en kies **Verbinden**.  

   ![Verbinding maken met voorbeeld](media/sample-opportunity-analysis/opportunity-connect.png)
5. Het inhoudspakket wordt geïmporteerd in Power BI en er wordt een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset toegevoegd aan de huidige werkruimte.

   ![De vermelding Opportunity Analysis Sample](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Het pbix-bestand voor dit voorbeeld ophalen

U kunt het voorbeeld ook downloaden als een [.pbix-bestand](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix), dat bedoeld is voor gebruik met Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>De Excel-werkmap ophalen voor dit voorbeeld

Als u de gegevensbron voor dit voorbeeld wilt bekijken, is dit ook beschikbaar als [Excel-werkmap](https://go.microsoft.com/fwlink/?LinkId=529782). De werkmap bevat Power View-werkbladen die u kunt bekijken en wijzigen. Als u de onbewerkte gegevens wilt zien, schakelt u de invoegtoepassingen van Gegevensanalyse in en selecteert u vervolgens **Power Pivot > Beheren**. Als u de Power View- en Power Pivot-invoegtoepassingen wilt inschakelen, raadpleegt u [De Excel-voorbeelden in Excel bekijken](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself) voor meer informatie.

## <a name="what-is-our-dashboard-telling-us"></a>Wat vertelt het dashboard ons?
Onze salesmanager heeft een dashboard gemaakt om de metrische gegevens bij te houden die voor hen het belangrijkst zijn. Wanneer ze iets interessants zien, kunnen ze een tegel selecteren om op de gegevens in te zoomen:

- De bedrijfsomzet is $ 2 miljard en de gewogen omzet is $ 461 miljoen.
- Het aantal verkoopkansen en de omzet volgen een vertrouwd trechterpatroon, met totalen die afnemen in elke volgende fase.
- In de regio Oost liggen onze meeste kansen.
- Grote verkoopkansen genereren meer omzet dan gemiddelde of kleine verkoopkansen.
- Grote partnerdeals genereren meer omzet: $8 miljoen gemiddeld tegenover $6 miljoen voor directe verkopen.

Aangezien de inspanningen om een deal binnen te halen dezelfde zijn of de deal nu is geclassificeerd als groot, gemiddeld of klein, moet ons bedrijf de gegevens analyseren om meer te leren over grote verkoopkansen.

1. Ga naar de werkruimte waarin u het voorbeeld hebt opgeslagen. Open het tabblad **Dashboards**, zoek het dashboard **Opportunity Analysis Sample** en selecteer het.

2. Selecteer de tegel **Opportunity Count by Partner Driven, Sales Stage** om de eerste pagina van het rapport Opportunity Analysis Sample te openen. 

    ![De tegel Opportunity Count by Partner Driven, Sales Stage](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>De pagina's in het rapport verkennen

U kunt de afzonderlijke pagina's in het rapport weergeven door de tabbladen aan de onderkant te selecteren.

### <a name="opportunity-count-overview-page"></a>De pagina Opportunity Count Overview
![De pagina Opportunity Count](media/sample-opportunity-analysis/opportunity3.png)

Let op de volgende details:
* Oost is onze belangrijkste regio wat betreft het aantal verkoopkansen.  
* Selecteer in het cirkeldiagram **Opportunity Count by Region** achtereenvolgens de verschillende regio's om de pagina op regio te filteren. U ziet dat partners voor elke regio aanzienlijk grotere verkoopkansen nastreven.   
* Het kolomdiagram **Opportunity Count by Partner Driven and Opportunity Size** geeft aan dat de meeste grote verkoopkansen door partners worden gestuurd, terwijl dat niet het geval is bij het merendeel van de kleine en middelgrote verkoopkansen.
* Selecteer in het staafdiagram **Opportunity Count by Sales Stage** de verschillende verkoopfases bij **Sales Stage** om het verschil in regionale aantallen te zien. Hoewel de regio East het grootste aantal verkoopkansen heeft, hebben de drie regio's in de verkoopfasen Solution, Proposal en Finalize vergelijkbare aantallen. Dit resultaat betekent dat we een hoger percentage deals afsluiten in de regio's Central en West.

### <a name="revenue-analysis-page"></a>De pagina Revenue Analysis
Deze pagina kijkt op een vergelijkbare manier naar de gegevens, maar gebruikt het perspectief van omzet in plaats van aantal.  

![De pagina Revenue Overview](media/sample-opportunity-analysis/opportunity4.png)

Let op de volgende details:
* East is niet alleen onze grootste regio wat betreft het aantal verkoopkansen, maar ook wat betreft omzet.  
* Als u het diagram **Revenue by Sales Stage and Partner Driven** filtert door **Yes** te selecteren voor **Partner Driven**, ziet u een omzet van $1,5 miljard en een gewogen omzet van $ 294 miljoen. Vergelijk deze bedragen met $ 644 miljoen en $ 166 miljoen voor niet-partnergestuurde omzet. 
* De gemiddelde omzet voor grote accounts is met 8 miljoen hoger als de verkoopkans partnergestuurd is, vergeleken met 6 miljoen voor niet-partnergestuurde transacties.  
* Voor partnergestuurde transacties is de gemiddelde omzet voor grote verkoopkansen bijna het dubbele van die van gemiddelde verkoopkansen.  
* De gemiddelde omzet voor het midden- en kleinbedrijf is vergelijkbaar voor zowel partnergestuurde als niet-partnergestuurde zakelijke activiteiten.   

Het is duidelijk dat onze partners het beter doen als het gaat om verkopen aan klanten dan niet-partners. Het is misschien verstandig om meer deals via onze partners te laten lopen.

### <a name="opportunity-count-by-region-and-stage"></a>Opportunity Count by Region and Stage
Op deze pagina van het rapport ziet u een analyse van gegevens die vergelijkbaar zijn met de gegevens op de vorige pagina, maar dan uitgesplitst naar regio en fase. 

![De pagina Opportunity Count by Region and Stage](media/sample-opportunity-analysis/opportunity5.png)

Let op de volgende details:
* Als u **East** selecteert in het cirkeldiagram **Opportunity Count per Region** om te filteren op de regio Oost, ziet u dat de verkoopkansen in deze regio bijna evenredig zijn verdeeld tussen partnergestuurd en niet-partnergestuurd.
* Grote verkoopkansen komen het meeste voor in de regio Central, kleine verkoopkansen komen het meest voor in de regio East en middelgrote verkoopkansen komen het meest voor in de regio West.

### <a name="upcoming-opportunities-by-month-page"></a>De pagina Upcoming Opportunities by Month
Op deze pagina kijken we naar vergelijkbare factoren, maar nu vanuit het perspectief van datum en tijd. 
 
![De pagina Upcoming Opportunities](media/sample-opportunity-analysis/opportunity6.png)

Onze CFO gebruikt deze pagina om de werkbelasting te beheren. Door te kijken naar de omzetmogelijkheden per verkoopfase en maand, kunnen ze op de juiste manier plannen.

Let op de volgende details:
* De gemiddelde omzet is voor de fase Finalize het hoogst. Het sluiten van deze deals is een topprioriteit.
* Door te filteren op maand (door de naam van de maand te selecteren in de slicer **Month**) ziet u dat er in januari zich een groot percentage deals in de fase Finalize bevindt met een gewogen omzet van $ 75 miljoen. Februari heeft daarentegen voornamelijk middelgrote deals in de fasen Solution en Proposal.
* In het algemeen fluctueren de cijfers van gewogen omzet op basis van verkoopfase, aantal verkoopkansen en dealgrootte. Voeg filters toe voor deze factoren met behulp van het deelvenster **Filters** aan de rechterkant om meer inzichten te ontdekken.

## <a name="next-steps-connect-to-your-data"></a>Volgende stappen: Verbinding maken met uw gegevens
Dit is een veilige omgeving om in te experimenten, omdat er geen optie is om uw wijzigingen op te slaan. Als u dat toch doet, kunt u altijd **Gegevens ophalen** selecteren voor een nieuw exemplaar van dit voorbeeld.

We hopen dat deze rondleiding heeft laten zien hoe Power BI-dashboards, Q&A en rapporten inzicht kunnen geven in voorbeeldgegevens. Nu is het uw beurt om verbinding met uw eigen gegevens te maken. Met Power BI kunt u verbinding maken met een groot aantal gegevensbronnen. Zie [Aan de slag met de Power BI-service](service-get-started.md) voor meer informatie.

