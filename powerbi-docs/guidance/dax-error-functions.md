---
title: 'DAX: Geschikt gebruik van foutfuncties'
description: Richtlijnen voor het gebruik van de DAX-foutfuncties.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: c0766a989ea3dbfe42620fd53b4c49d6144b4c5f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088460"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Geschikt gebruik van foutfuncties

Wanneer u als gegevensmodeleerder een DAX-expressie schrijft die mogelijk een evaluatiefout veroorzaakt, kunt u overwegen twee handige DAX-functies te gebruiken.

- De functie [ISERROR](/dax/iserror-function-dax), die één expressie aanneemt en TRUE retourneert als de expressie in een fout resulteert.
- De functie [IFERROR](/dax/iferror-function-dax), die twee expressies gebruikt. Als de eerste expressie in een fout resulteert, wordt de waarde voor de tweede expressie geretourneerd. Het is in feite een meer geoptimaliseerde implementatie van het nesten van de functie ISERROR binnen een [IF](/dax/if-function-dax)-functie.

Hoewel deze functies echter nuttig kunnen zijn en kunnen bijdragen aan het schrijven van eenvoudig te begrijpen expressies, kunnen ze ook de prestaties van berekeningen aanzienlijk verslechteren. Dit kan komen doordat deze functies het aantal vereiste scans van de opslagengine verhogen.

De meeste evaluatiefouten worden veroorzaakt door onverwachte lege waarden of nulwaarden, of ongeldige gegevenstypeconversie.

## <a name="recommendations"></a>Aanbevelingen

Het is beter om te voorkomen dat de functies ISERROR en IFERROR worden gebruikt. Pas in plaats daarvan verdedigingsstrategieën toe bij het ontwikkelen van het model en het schrijven van expressies. U kunt bijvoorbeeld de volgende strategieën gebruiken:

- **Garanderen dat kwaliteitsgegevens in het model worden geladen:** gebruik Power Query-transformaties voor het verwijderen of vervangen van ongeldige of ontbrekende waarden en om correcte gegevenstypen in te stellen. Een Power Query-transformatie kan ook worden gebruikt om rijen te filteren wanneer er fouten optreden, zoals ongeldige gegevensconversie.

    De kwaliteit van gegevens kan ook worden bepaald door de eigenschap **Is Nullable** van de modelkolom op Uit in te stellen, waardoor het vernieuwen van gegevens mislukt als er lege waarden worden aangetroffen. Als deze fout optreedt, blijven de gegevens die zijn geladen als gevolg van een geslaagde vernieuwing in de tabellen aanwezig.
- **De functie IF gebruiken:** de logische testexpressie van de functie IF kan worden gebruikt om te bepalen of er een foutresultaat zou optreden. Zoals de functies ISERROR en IFERROR kan deze functie leiden tot extra scans van de opslagengine, maar presteert deze functie waarschijnlijk beter omdat er geen fout hoeft te worden gegenereerd.
- **Fouttolerante functies gebruiken:** met sommige DAX-functies worden foutsituaties getest en gecompenseerd. Met deze functies kunt u een alternatief resultaat invoeren dat in plaats daarvan wordt geretourneerd. De functie [DIVIDE](/dax/divide-function-dax) is daar een voorbeeld van. Lees voor meer informatie over deze functie het artikel [DAX: DIVIDE-functie ten opzichte van deeloperator (/)](dax-divide-function-operator.md).

## <a name="example"></a>Voorbeeld

De volgende meetexpressie test of er een fout zou worden gegenereerd. Er wordt in dit geval een lege waarde geretourneerd (dit is het geval wanneer u de functie IF niet opgeeft met een waarde-if-false-expressie).

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

Deze volgende versie van de meetexpressie is verbeterd door gebruik te maken van de functie IFERROR in plaats van de functies IF en ISERROR.

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

Deze definitieve versie van de meetexpressie levert hetzelfde resultaat op, maar is efficiënter en eleganter.

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)

- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)