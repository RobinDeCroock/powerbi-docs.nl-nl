---
ms.openlocfilehash: 6ed1690ec77880467007200c30038d185c98d6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273230"
---
Met DAX kunt u twee primaire berekeningen maken:

* **Berekende kolommen**
* **Berekende metingen**

Voordat u gaat kijken welke berekening u gaat maken, is het handig dat u de DAX-syntaxis voor tabellen en kolommen begrijpt die u nodig hebt voor een **berekende kolom** of **berekende meting**.

## <a name="dax-table-and-column-name-syntax"></a>De DAX-naamsyntaxis voor tabellen en kolommen
Of u nu een nieuwe kolom of meting maakt, het is belangrijk dat u de algemene indeling voor tabelnamen in DAX kent:

    'Table Name'[ColumnName]

Als er spaties in de naam van de tabel staan (zoals hierboven), zijn enkele aanhalingstekens rond de tabelnaam verplicht. Als de tabelnaam geen spaties bevat, kunnen enkele aanhalingstekens worden weggelaten, zodat de syntaxis er als volgt uitziet:

    TableName[ColumnName]

De volgende afbeelding toont een DAX-formule die is gemaakt in Power BI:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

U kunt de tabelnaam ook volledig weglaten en alleen de naam van de kolom gebruiken, maar dit is niet de juiste manier om heldere functies (en dus een heldere DAX-code) te schrijven. Kolomnamen moeten altijd de vierkante haken bevatten.

U kunt het best *altijd* als volgt te werk gaan:

* Gebruik geen spaties in tabelnamen
* Neem de tabelnaam altijd op in formules (ook al kunt u de tabelnaam in DAX weglaten)

## <a name="creating-calculated-columns"></a>Berekende kolommen maken
**Berekende kolommen** zijn handig als u op basis van de waarde een segment wilt maken of wilt filteren, of als u een berekening voor elke rij in de tabel wilt maken.

U kunt berekende kolommen in Power BI Desktop maken door **Nieuwe kolom** op het tabblad **Modelleren** te selecteren. U kunt dit het best doen in de weergave **Gegevens** (in plaats van in de weergave **Rapport** of **Relaties**), doordat u hier de nieuwe kolom en de **formulebalk** kunt zien die wordt ingevuld en gereed is voor uw DAX-formule.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Als u de knop **Nieuwe kolom** selecteert, wordt de **formulebalk** gevuld met een basisnaam voor de kolom (die u uiteraard kunt wijzigen) en de **=** operator. De nieuwe kolom wordt weergegeven in het gegevensraster, zoals in de volgende afbeelding.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Voor een berekende kolom zijn de volgende elementen vereist:

* een nieuwe kolomnaam
* ten minste één functie of expressie

Als u verwijst naar een tabel of kolom in de berekende kolomformule, hoeft u geen rij in de tabel op te geven. Power BI berekent de kolom voor de huidige rij namelijk voor elke berekening.

## <a name="creating-calculated-measures"></a>Berekende metingen maken
U gebruikt een **berekende meting** als u percentages of ratio's berekent of als u complexe aggregaties nodig hebt. Als u een meting met behulp van een DAX-formule wilt maken, selecteert u de knop **Nieuwe meting** op het tabblad **Modelleren**. Nogmaals, u kunt dit het best doen in de weergave **Gegevens** van Power BI Desktop omdat in deze weergave de **formulebalk** wordt weergegeven, zodat u eenvoudig uw DAX-formule kunt schrijven.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Als u een **meting** maakt, wordt een nieuw pictogram weergegeven in het deelvenster **Velden** met de naam van de meting. De **formulebalk** wordt gevuld met de naam van uw DAX-formule (in dit geval is dit uw meting).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

De vereiste elementen voor een berekende meting zijn dezelfde als voor een berekende kolom:

* een nieuwe naam van de meting
* ten minste één functie of expressie

> Met dank aan [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax) voor de video
> 
> 

