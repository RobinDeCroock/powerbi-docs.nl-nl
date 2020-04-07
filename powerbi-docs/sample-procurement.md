---
title: 'Voorbeeld van een inkoopanalyse: Rondleiding volgen'
description: 'Voorbeeld van een inkoopanalyse voor Power BI: Rondleiding volgen'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 8ee77485da03cb8e507d30d511c08aa869c3e4ba
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404664"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Voorbeeld van een inkoopanalyse voor Power BI: Rondleiding volgen

Het inhoudspakket Voorbeeld van een inkoopanalyse bevat een dashboard, rapport en gegevensset waarmee de uitgaven van een productiebedrijf aan leveranciers worden geanalyseerd op categorie en locatie. In het voorbeeld verkennen we deze gebieden:

* Wie de belangrijkste leveranciers zijn
* Aan welke categorieën we het meeste besteden
* Welke leveranciers de meeste korting geven en wanneer

![Dashboard voor Procurement Analysis Sample](media/sample-procurement/procurement1.png)

Dit voorbeeld maakt deel uit van een serie die laat zien hoe u Power BI kunt gebruiken met bedrijfsgegevens, rapporten en dashboards. Het voorbeeld is door [obviEnce](http://www.obvience.com/) met echte, geanonimiseerde gegevens gemaakt. De gegevens zijn beschikbaar in verschillende indelingen: inhoudspakket, een PBIX-bestand van Power BI Desktop of een Excel-werkmap. Zie [Voorbeelden voor Power BI](sample-datasets.md). 

In deze zelfstudie gebruiken we het inhoudspakket Voorbeeld van een inkoopanalyse in de Power BI-service. Omdat de rapportervaringen in Power BI Desktop en in de service zo vergelijkbaar zijn, kunt u de zelfstudie ook volgen met het PBIX-voorbeeldbestand in Power BI Desktop. 

U hebt geen licentie voor Power BI nodig om de voorbeelden te bekijken in Power BI Desktop. Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte in de Power BI-service. 

## <a name="get-the-sample"></a>Het voorbeeld ophalen

Voordat u het voorbeeld kunt gebruiken, moet u het eerst downloaden als een [inhoudspakket](#get-the-content-pack-for-this-sample), een [PBIX-bestand](#get-the-pbix-file-for-this-sample) of een [Excel-werkmap](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Het inhoudspakket voor dit voorbeeld ophalen

1. Open de Power BI-service (app.powerbi.com), meld u aan en open de werkruimte waar u het voorbeeld wilt opslaan. 

    Als u geen Power BI Pro-licentie hebt, kunt u het voorbeeld opslaan in uw Mijn werkruimte.

2. Selecteer **Gegevens ophalen** in de linkerbenedenhoek.

    ![Selecteer Gegevens ophalen](media/sample-datasets/power-bi-get-data.png)
3. Selecteer **Voorbeelden** op de pagina **Gegevens ophalen** die wordt weergegeven.

4. Selecteer **Voorbeeld van een inkoopanalyse** en kies **Verbinden**.  
  
   ![Verbinding maken met voorbeeld](media/sample-procurement/procurement1a.png)
   
5. Het inhoudspakket wordt geïmporteerd in Power BI en er wordt een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset toegevoegd aan de huidige werkruimte.
   
   ![De vermelding Procurement Analysis Sample](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Het pbix-bestand voor dit voorbeeld ophalen

U kunt het voorbeeld ook downloaden als een [.pbix-bestand](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix), dat bedoeld is voor gebruik met Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>De Excel-werkmap ophalen voor dit voorbeeld

Als u de gegevensbron voor dit voorbeeld wilt bekijken, is dit ook beschikbaar als [Excel-werkmap](https://go.microsoft.com/fwlink/?LinkId=529784). De werkmap bevat Power View-werkbladen die u kunt bekijken en wijzigen. Als u de onbewerkte gegevens wilt zien, schakelt u de invoegtoepassingen van Gegevensanalyse in en selecteert u vervolgens **Power Pivot > Beheren**. Zie [De Excel-voorbeelden in Excel bekijken](sample-datasets.md#explore-excel-samples-inside-excel) als u de Power View- en Power Pivot-invoegtoepassingen wilt inschakelen.


## <a name="spending-trends"></a>Bestedingstrends
Laten we eerst eens kijken of we bestedingstrends op categorie en locatie kunnen vinden.  

1. Ga naar de werkruimte waarin u het voorbeeld hebt opgeslagen. Open het tabblad **Dashboards**, zoek het dashboard **Procurement Analysis Sample** en selecteer het. 
2. Selecteer de dashboardtegel **Total Invoice by Country/Region** om de pagina **Spend Overview** van het rapport **Procurement Analysis Sample** te openen.

    ![De pagina Spend Overview](media/sample-procurement/procurement2.png)

Let op de volgende details:

* In het lijndiagram **Total Invoice per Month en Category** vertoont de categorie **Direct** consistente uitgaven, terwijl **Logistics** een piek heeft in december en  **Other** een piek in februari.
* Op de kaart **Total Invoice per Country/Region** ziet u dat de Verenigde Staten het grootste deel van de uitgaven voor zijn rekening neemt.
* In het kolomdiagram **Total Invoice per Sub Category** zijn **Hardware** en **Indirect Goods & Services** de grootste bestedingscategorieën.
* In het staafdiagram **Total Invoice per Tier** kunt u zien dat we het meeste zaken doen met onze leveranciers van laag 1 (top 10). Hierdoor kunnen we de leveranciersrelaties beter beheren.

## <a name="spending-in-mexico"></a>Uitgaven in Mexico
Laten we de bestedingsgebieden in Mexico bekijken.

1. Selecteer de bel **Mexico** op de kaart **Total Invoice per Country/Region**. U ziet dat in het kolomdiagram **Total Invoice per Sub Category** het meeste is uitgegeven aan de subcategorie **Indirect Goods & Services**.

   ![Selecteer Mexico op de pagina Spend Overview](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Inzoomen op de kolom **Indirecte goederen en services**:

   * Selecteer in de grafiek **Total Invoice per Sub Category** de pijl voor inzoomen ![Pijl voor inzoomen](media/sample-procurement/pbi_drilldown_icon.png) in de rechterbovenhoek van de grafiek.
   * Selecteer de kolom **Indirecte goederen & Services**.

      Zoals u zien kunt, zijn de uitgaven voor de subcategorie **Sales & Marketing** veruit het hoogst.
   * Selecteer nogmaals **Mexico** op de kaart.

      Voor Mexico worden de grootste uitgaven gevormd door de subcategorie **Maintenance & Repair**.

      ![Inzoomen op Indirect Goods & Services voor Mexico](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Selecteer de pijl omhoog in de linkerbovenhoek van de grafiek om weer uit te zoomen.
4. Selecteer de pijl voor inzoomen opnieuw om inzoomen uit te schakelen.  
5. Selecteer **Voorbeeld van een inkoopanalyse** in de bovenste navigatiebalk om terug te keren naar het dashboard.

## <a name="evaluate-different-cities"></a>Verschillende steden evalueren
U kunt markeren gebruiken om verschillende steden te evalueren.

1. Selecteer de dashboardtegel **Total Invoice, Discount % By Month** om de pagina **Discount Analysis** van het rapport **Procurement Analysis Sample** te openen.
2. Selecteer in de treemap **Total Invoice per City** de verschillende steden om te zien hoe deze zich verhouden. U ziet dat bijna alle facturen van Miami afkomstig zijn van leveranciers van categorie 1.

   ![City vs discount % by tier](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Leverancierskortingen
Laten we ook eens kijken naar de beschikbare kortingen van leveranciers en de perioden waarin de meeste korting wordt gegeven:
* Zijn de kortingen iedere maand verschillend of blijven ze hetzelfde?
* Krijg sommige steden meer kortingen dan andere?

![De pagina Discount Analysis](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Korting per maand
Als we kijken naar de combinatiegrafiek **Total Invoice en Discount % per Month**, zien we dat februari de drukste maand is en september de minst drukke maand. 

Kijk naar het kortingspercentage in deze maanden: in de drukke maanden is de korting lager dan in de minder drukke maanden. Hoe meer we de korting nodig hebben, des te slechter de deal zal zijn.

![De grafiek Total Invoice en Discount % per Month](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Korting per stad
Een ander aspect om te verkennen, is de korting per stad. Selecteer de plaatsen in de treemap en kijk hoe de andere grafieken veranderen:

* St. Louis had een grote piek in het totaal aan facturen in februari en een grote dip in de kortingsbesparingen in april.
* Mexico City heeft het hoogste kortingspercentage (11,05%) en Atlanta het laagste (0,08%).

![Kortingsgrafieken voor Mexico City](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Het rapport bewerken
Selecteer **Rapport bewerken** in de linkerbovenhoek om de bewerkingsweergave te openen:

* Kijk hoe de pagina's zijn samengesteld.
* Voeg pagina's en grafieken toe die zijn gebaseerd op dezelfde gegevens.
* Wijzig het type visualisatie voor een grafiek, wijzig de treemap bijvoorbeeld in een ringdiagram.
* Maak grafieken vast aan uw dashboard.

## <a name="next-steps-connect-to-your-data"></a>Volgende stappen: Verbinding maken met uw gegevens
Dit is een veilige omgeving om in te experimenten, omdat er geen optie is om uw wijzigingen op te slaan. Als u dat toch doet, kunt u altijd **Gegevens ophalen** selecteren voor een nieuw exemplaar van dit voorbeeld.

We hopen dat deze rondleiding heeft laten zien hoe Power BI-dashboards, Q&A en rapporten inzicht kunnen geven in voorbeeldgegevens. Nu is het uw beurt om verbinding met uw eigen gegevens te maken. Met Power BI kunt u verbinding maken met een groot aantal gegevensbronnen. Zie [Aan de slag met de Power BI-service](service-get-started.md) voor meer informatie.

