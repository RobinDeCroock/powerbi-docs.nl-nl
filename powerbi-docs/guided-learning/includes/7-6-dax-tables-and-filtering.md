---
ms.openlocfilehash: 5bc0d3bbfb2c2b67b56e6406646f6131a360b97d
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799799"
---
Een belangrijk verschil tussen **DAX** en de formuletaal in Excel is dat u met DAX *gehele tabellen* in expressies kunt opnemen, zodat u niet bent beperkt tot één enkele waarde. Met DAX kunt u tabellen in expressies filteren en vervolgens werken met de gefilterde reeks waarden.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

U kunt volledige opnieuw berekende tabellen maken en deze vervolgens als elke andere tabel gebruiken. Ook kunt u relaties tussen tabellen en andere tabellen in uw gegevenstabel maken.

## <a name="dax-table-functions"></a>Tabelfuncties in DAX
DAX beschikt over een uitgebreide reeks **tabel**functies, waaronder:

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Deze functies retourneren een volledige tabel in plaats van een afzonderlijke waarde. Doorgaans gebruikt u de resultaten van een **tabel**functie in verdere analyse als onderdeel van een grotere expressie, in plaats van de geretourneerde tabel als uiteindelijke waarde te gebruiken. Wanneer u een tabelfunctie gebruikt, nemen de resultaten de relaties tussen de kolommen over.

U kunt tabelfuncties in uw expressie combineren, zolang elke functie gebruikmaakt van een tabel en een tabel retourneert. Bekijk het volgende voorbeeld van een DAX-expressie:

    FILTER (ALL (Table), Condition)

Deze expressie plaatst een filter op de *tabel* als geheel en negeert eventuele filterinhoud.

De functie DISTINCT retourneert de afzonderlijke waarden van een kolom die ook zichtbaar zijn in de huidige context. Als u het voorbeeld hierboven met de DAX-expressie wilt gebruiken, worden met **ALL** in deze expressie filters genegeerd. Als u **ALL** echter vervangt door **DISTINCT**, worden de filters niet genegeerd.

## <a name="counting-values-with-dax"></a>Waarden met DAX tellen
Een algemene vraag die rapportmakers met DAX willen beantwoorden is:

* Hoeveel waarden heb ik voor deze kolom?

Dit lijkt misschien een eenvoudige vraag voor een tabel die u bekijkt, maar DAX benadert deze vraag op een andere manier, met name als er een relatie bestaat tussen tabellen.

Power BI en DAX bevatten bijvoorbeeld waarden die niet goed zijn gekruisindexeerd. Als de binnenkomende relatie verbroken is, voegt DAX een nieuwe rij aan de betreffende tabel toe met lege waarden in elk veld. Deze nieuwe rij wordt vervolgens gekoppeld aan de niet-geïndexeerde rij om de referentiële integriteit te waarborgen. Als uw functie lege rijen bevat, zoals vaak het geval is als u **ALL** gebruikt, worden de lege rijen opgenomen in het aantal waarden dat wordt geretourneerd voor die kolom.

U kunt ook volledig berekende tabellen maken met DAX-functies. Berekende tabellen die zijn gemaakt met behulp van DAX moeten een **naam** en een **tabel**functie hebben. Berekende tabellen kunnen worden gebruikt als elke andere tabel, zoals voor het opstellen van relaties.

> Met dank aan [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax) voor de video
> 
> 

