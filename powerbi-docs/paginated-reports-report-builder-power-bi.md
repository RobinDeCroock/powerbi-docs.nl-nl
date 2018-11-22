---
title: Wat zijn gepagineerde rapporten in Power BI Premium? (Voorbeeld)
description: Gepagineerde rapporten zijn rapporten die kunnen worden afgedrukt of gedeeld. U kunt de rapportindeling exact bepalen. Dit type rapport bevat alle gegevens uit een tabel, zelfs als de tabel bijvoorbeeld meerdere pagina's omvat.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/08/2018
ms.author: maggies
ms.openlocfilehash: 15ec21a0b86977173c16071980d7527f27db74ef
ms.sourcegitcommit: 5eb0f37f59b5fec15c0caecbbd1f8d688c7f0013
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297039"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>Wat zijn gepagineerde rapporten in Power BI Premium? (Voorbeeld)
Gepagineerde rapporten waren lang de standaardrapportindeling in SQL Server Reporting Services en zijn nu beschikbaar in de Power BI-service. Gepagineerde rapporten zijn rapporten die zijn ontworpen om te worden afgedrukt of gedeeld. Ze worden 'gepagineerd' genoemd omdat ze door hun opmaak goed op een pagina passen en toch alle gegevens uit een tabel bevatten, zelfs als de tabel bijvoorbeeld meerdere pagina's omvat. Ze worden soms 'pixelperfect' genoemd omdat de pagina-indeling van dit type rapport exact kan worden ingesteld. Gepagineerde rapporten zijn gebaseerd op de RDL-rapporttechnologie in SQL Server Reporting Services. Report Builder is het zelfstandige hulpprogramma voor het maken van gepagineerde rapporten. 

Gepagineerde rapporten kunnen heel veel pagina's hebben. Het rapport in het volgende voorbeeld heeft 563 pagina's, die allemaal zorgvuldig zijn opgemaakt, met één pagina per factuur en herhalende kopteksten en voetteksten.

![Gepagineerd rapport in de Power BI-service](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

U kunt een voorbeeld van uw rapport bekijken in Report Builder en het rapport vervolgens publiceren naar de Power BI-service, http://app.powerbi.com. U hebt een Power BI Pro-licentie nodig om een rapport te publiceren in de service. U kunt gepagineerde rapporten publiceren en delen in Mijn werkruimte of in de app-werkruimten, zolang de werkruimte zich in een Power BI Premium-capaciteit bevindt. Bovendien moet een beheerder van Power BI gepagineerde rapporten inschakelen in de Power BI-beheerportal. Lees meer over het [configureren van werkbelastingen](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Rapporten maken in Report Builder

Gepagineerde rapporten hebben hun eigen ontwerpprogramma, Report Builder genaamd. Als u gepagineerde rapporten hebt gemaakt voor Power BI Report Server of SQL Server Reporting Services (SSRS), kunt u hetzelfde hulpprogramma en dezelfde versie gebruiken. In feite zijn gepagineerde rapporten die u maakt voor SSRS 2016 en 2017 of voor Power BI Report Server on-premises compatibel met de Power BI-service. De Power BI-service ondersteunt achterwaartse compatibiliteit, zodat u uw rapporten kunt upgraden en u gepagineerde rapporten van een eerdere versie kunt bijwerken. Niet alle rapportfuncties zijn beschikbaar bij de release. Zie [Beperkingen en overwegingen](#limitations-and-considerations) in dit artikel voor meer informatie.
     
## <a name="report-from-a-variety-of-data-sources"></a>Rapporteren uit verschillende gegevensbronnen

Een gepagineerd rapport kan een aantal verschillende gegevensbronnen hebben. Dit type rapport heeft geen onderliggende gegevensmodel, zoals Power BI-rapporten. Bij de eerste release van gepagineerde rapporten in de Power BI-service maakt u ingesloten gegevensbronnen en gegevenssets in het rapport zelf, in plaats van verbinding te maken met gedeelde gegevensbronnen of gegevenssets op een server. U maakt rapporten in Report Builder op uw lokale computer. Als een rapport verbinding maakt met on-premises gegevens, moet u na het uploaden van het rapport naar de Power BI-service een gateway maken en de gegevensverbinding omleiden. Dit zijn de gegevensbronnen waarmee u in de eerste release verbinding kunt maken:

- Azure SQL Database en Data Warehouse
- SQL Server via een gateway
- SQL Server Analysis Services via een gateway
 
Tijdens de preview-periode komen er meer gegevensbronnen beschikbaar.

## <a name="design-your-report"></a>Het rapport ontwerpen  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Gepagineerde rapporten maken met matrix-, grafiek- en vrije vorm-indelingen

Maak tabelrapporten voor gegevens in kolommen, matrixrapporten (zoals kruistabel- of draaitabelrapporten) voor samengevatte gegevens, grafiekrapporten voor grafische gegevens en vrije vorm *lijst*-rapporten voor al het overige, zoals facturen. 
  
U kunt beginnen met een van de wizards van Report Builder. De wizards Tabel, Matrix en Grafiek begeleiden u stapsgewijs bij het maken van de ingesloten verbinding met de gegevensbron en de ingesloten gegevensset. Vervolgens sleept u velden om een gegevensset-query te maken, selecteert u een indeling en stijl, en past u het rapport aan.  
  
Met de wizard Kaart maakt u rapporten waarin geaggregeerde gegevens worden uitgezet tegen een geografische of geometrische achtergrond. Kaartgegevens kunnen ruimtelijke gegevens zijn uit een Transact-SQL-query of een ESRI-vormbestand (Environmental Systems Research Institute, Inc). U kunt ook een achtergrond bestaande uit een tegel met een kaart van Microsoft Bing toevoegen.  

### <a name="add-more-to-your-report"></a>Meer toevoegen aan uw rapport

Pas uw gegevens aan door deze te filteren, te groeperen en te sorteren, of door formules of expressies toe te voegen. Voeg grafieken, meters, sparklines en indicatoren toe om gegevens in een visuele indeling samen te vatten.  Gebruik parameters en filters om gegevens te filteren voor aangepaste weergaven. U kunt ook afbeeldingen en andere bronnen insluiten of hiernaar verwijzen, met inbegrip van externe inhoud.  

Alles in een gepagineerd rapport, van het rapport zelf tot de tekstvakken, afbeeldingen, tabellen en grafieken, is gekoppeld aan een matrix van eigenschappen die u kunt instellen om het rapport op exact de gewenste manier weer te geven.

## <a name="creating-a-report-definition"></a>Een rapportdefinitie maken

Wanneer u een gepagineerd rapport ontwerpt, maakt u in feite een *rapportdefinitie*. Het rapport bevat geen gegevens. Er wordt aangegeven waar de gegevens moeten worden opgehaald, welke gegevens u wilt ophalen en hoe u de gegevens wilt weergeven. Wanneer u het rapport uitvoert, worden er gegevens opgehaald aan de hand van de definitie van het rapport die u hebt opgegeven, waarna deze worden gecombineerd met de rapportindeling om het rapport te genereren. U uploadt de rapportdefinitie naar de Power BI-service, http://app.powerbi.com, naar uw Mijn werkruimte of naar een werkruimte die u deelt met uw collega's. Als de gegevensbron van het rapport on-premises is, moet u na het uploaden van het rapport de verbinding met de gegevensbron omleiden via een gateway. 

## <a name="view-your-paginated-report"></a>Een gepagineerd rapport weergeven
U kunt een gepagineerd rapport weergeven in de Power BI-service in een browser en ook in de mobiele Power BI-apps. In de Power BI-service kunt u het rapport exporteren naar verschillende indelingen voor webgeoriënteerde, paginageoriënteerde en bureaubladtoepassingen, zoals HTML, MHTML, PDF, XML, CSV, TIFF, Word en Excel. U kunt het rapport ook delen met anderen.  
  
## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Hier volgen enkele andere functies die niet worden ondersteund in de eerste release:

- Rapportpagina's of visualisaties vastmaken aan Power BI-dashboards.
- Interactieve functies zoals documenttoewijzingen en knoppen Weergeven/Verbergen.
- Subrapporten en drillthrough-rapporten.
- Abonnementen.
- Gedeelde gegevensbronnen en gedeelde gegevenssets.
- Power BI-gegevenssets.
- Visualisaties uit Power BI-rapporten.
- Gepagineerde rapporten in apps. U kunt een gepagineerd rapport delen vanuit een app-werkruimte, maar u kunt het rapport niet toevoegen wanneer u de app vanuit die werkruimte publiceert.
 
## <a name="next-steps"></a>Volgende stappen

- [Report Builder installeren vanuit het Microsoft Downloadcentrum](http://go.microsoft.com/fwlink/?LinkID=734968)

- [Tutorial: Create a paginated report](paginated-reports-quickstart-aw.md) (Zelfstudie: een gepagineerd rapport maken)
  
