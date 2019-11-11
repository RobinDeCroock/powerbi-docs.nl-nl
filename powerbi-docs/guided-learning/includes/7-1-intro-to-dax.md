---
ms.openlocfilehash: 3966521d158c244487638be4117f98ea570e1f28
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799797"
---
Welkom bij de sectie **Begeleide training** van Power BI als introductie op **DAX**.

**DAX** staat voor **Data Analysis Expressions** en is de formuletaal die in Power BI (en achter de schermen) wordt gebruikt. DAX wordt ook in andere producten van Microsoft gebruikt, zoals Power Pivot en SSAS Tabular. In deze onderwerpen van Begeleide training wordt alleen besproken hoe DAX in Power BI wordt gebruikt en hoe u het kunt gebruiken.

## <a name="dax-and-this-guided-learning-video-series"></a>DAX en de videoserie 'Begeleide training'
Het doel van deze sectie **Begeleide training** is om u de basisprincipes en grondbeginselen van DAX te leren, zodat u weet wat DAX is en hoe het werkt. Ook worden de handigste functies besproken door DAX-deskundige [Alberto Ferrari](https://www.sqlbi.com/learning-dax).

![Portret van Alberto Ferrari](media/7-1-intro-to-dax/intro_dax_6_alberto_ferrari.png)

In de video's in deze sectie **Begeleide training** over **DAX** leert u alles over de basisprincipes van DAX op basis van de manier waarop de DAX-formuletaal werkt. Dit is handig als u zelf nieuwe DAX-formules maakt, maar ook om te begrijpen hoe in Power BI DAX-formules worden gemaakt als u query's maakt in de **Query-Editor**.

## <a name="in-this-video---introduction-to-dax"></a>In deze video - Inleiding op DAX
Alhoewel de concepten eenvoudig en simpel zijn, is DAX uiterst krachtig. DAX maakt gebruik van enkele unieke programmeerconcepten en -patronen die soms moeilijk te begrijpen zijn. De traditionele manier om een taal te leren is niet de beste manier om DAX te leren begrijpen. Daarom leert u in deze video een aantal concepten en de theorie die u later zelf in uw werk met DAX kunt gebruiken.

DAX is een *functionele taal*. De volledige uitgevoerde code is opgenomen in een functie.

In DAX kunnen functies andere geneste functies, voorwaardelijke instructies en waardereferenties bevatten. Uitvoering in DAX wordt gestart vanuit de binnenste functie of parameter en van daaruit verder toegepast. DAX-formules worden in Power BI geschreven op één regel, waardoor een juiste indeling van functies belangrijk is voor de leesbaarheid.

DAX is ontworpen voor gebruik met tabellen, zodat er slechts twee primaire gegevenstypen zijn: **Numeriek** en **Overig**. **Numerieke** gegevenstypen kunnen *gehele getallen*, *decimalen*, en *valuta* bevatten. **Andere** gegevenstypen kunnen *tekenreeksen* en *binaire objecten* bevatten. Als u uw DAX-functie afstemt op een type getallen, kunt u deze functies ook gebruiken voor andere numerieke gegevens.

DAX maakt gebruik van operatoroverbelasting. Dit betekent dat u gegevenstypen in uw berekeningen kunt combineren. De resultaten worden gewijzigd op basis van het type gegevens dat in de invoer is gebruikt. Conversie wordt automatisch uitgevoerd. Dit betekent dat u de gegevenstypen van de kolommen waarmee u werkt in Power BI niet hoeft te weten. Het betekent echter ook dat conversie soms onverwacht wordt uitgevoerd. Het is verstandig dat u de gebruikte gegevens begrijpt, zodat uw operators naar verwachting werken.

Er is één gegevenstype dat u waarschijnlijk veel zult gebruiken in Power BI: **Datum/tijd**. **Datum/tijd** wordt opgeslagen als een drijvende-kommawaarde met zowel gehele getallen als decimale delen. Datum/tijd kan nauwkeurig worden gebruikt voor berekeningen van elke periode na 1 maart 1900.

> Met dank aan [Alberto Ferrari, SQLBI](https://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit) voor de video
> 
> 

