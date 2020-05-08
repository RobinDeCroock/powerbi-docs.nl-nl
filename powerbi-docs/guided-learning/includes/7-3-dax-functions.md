---
ms.openlocfilehash: c3b1b7288d0d277fc866ea47887335d10279c6cc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799798"
---
DAX bevat veel functies voor het vormen en bewerken van uw gegevens en andere manieren om uw gegevens te analyseren. Deze functies kunnen worden gegroepeerd in de volgende categorieën:

* **Aggregatie**functies
* **Tel**functies
* **Logische** functies
* **Informatie**functies
* **Tekst**functies
* **Datum**functies

Wanneer u de formule begint te typen in de **formulebalk** van Power BI Desktop, verschijnt net als in Excel een lijst met beschikbare functies waaruit u de gewenste functie kunt kiezen. Met behulp van de **pijl-omhoog-** en **pijl-omlaag-** toetsen op het toetsenbord kunt u de beschikbare functies markeren en een korte beschrijving van de functie weergeven.

Power BI biedt de functies die overeenkomen met de letters die u hebt getypt. Als u bijvoorbeeld *S* hebt getypt, worden alleen de functies weergegeven die beginnen met een *S*. Als u *Su* typt, worden alleen de functies weergegeven die de letterreeks *Su* *bevatten* in de naam (de functies hoeven niet te beginnen met *Su*).

![](media/7-3-dax-functions/dax-functions_1.png)

U kunt op deze manier eenvoudig experimenteren met DAX en de verschillende DAX-functies bekijken die in Power BI beschikbaar zijn. U hoeft alleen maar te typen, Power BI doet de rest.

Nu we weten hoe we aan de slag kunnen met een DAX-formule, gaan we eens kijken naar de verschillende functiecategorieën.

## <a name="aggregation-functions"></a>Aggregatiefuncties
DAX bevat een aantal **aggregatie**functies, waaronder de volgende veelgebruikte functies:

* SUM
* AVERAGE
* MIN
* MAX
* SUMX (en andere *X*-functies)

Deze functies werken alleen voor numerieke kolommen. Over het algemeen kan slechts één kolom tegelijk worden geaggregeerd.

Aggregatiefuncties die eindigen op **X**, zoals **SUMX**, zijn echter geschikt voor meerdere kolommen. Deze functies worden door de tabel heen herhaald en evalueren de expressie voor elke rij.

## <a name="counting-functions"></a>Telfuncties
De volgende **tel**functies worden vaak in DAX gebruikt:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Deze functies tellen verschillende elementen, zoals afzonderlijke waarden, niet-lege waarden en tabelrijen.

## <a name="logical-functions"></a>Logische functies
DAX bevat de volgende **logische** functies:

* EN
* OF
* NOT
* IF
* IFERROR

Deze speciale functies kunnen ook worden uitgedrukt met *operators*. **AND** kan bijvoorbeeld worden getypt als (of vervangen worden door) **&&** in uw DAX-formule.

U kunt operators gebruiken (zoals **&&** ) als u meer dan twee voorwaarden in de formule wilt gebruiken. Anders kunt u voor de leesbaarheid van de DAX-code het best de functienaam zelf gebruiken (zoals **AND**).

## <a name="information-functions"></a>Informatiefuncties
DAX bevat de volgende **informatie**functies:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Deze functies kunnen soms handig zijn. Het is echter verstandig als u vooraf weet welke gegevenstypen in de kolommen staan, zodat u niet afhankelijk bent van deze functies voor het juiste gegevenstype.

DAX gebruikt de functies **MAX** en **MIN** op beide *aggregatie*waarden en *vergelijkt*  de waarden.

## <a name="text-functions"></a>Tekstfuncties
De volgende **tekst**functies worden vaak in DAX gebruikt:

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Deze **tekst** werkt op dezelfde manier als in de Excel-functies met dezelfde naam. Het scheelt dus als u bekend bent met tekstfuncties in Excel. Zo niet, dan kunt u experimenteren met deze functies in Power BI.

## <a name="date-functions"></a>Datumfuncties
DAX bevat de volgende **datum**functies:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Deze functies zijn weliswaar handig voor het berekenen en extraheren van gegevens in *datum*waarden, maar zijn niet van toepassing op tijdsintelligentie die gebruikmaakt van een datumtabel.

> Met dank aan [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax) voor de video
> 
> 

