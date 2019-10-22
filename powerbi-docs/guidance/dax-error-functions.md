---
title: 'DAX: Geschikt gebruik van foutfuncties'
description: Richtlijnen voor het gebruik van de DAX-foutfuncties.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 0855a9ee4c699c4a3b65e4331b5af2fa68a5610c
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021063"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX: Geschikt gebruik van foutfuncties

Dit artikel gaat in op de gegevens modelers die DAX-expressies definiëren.

## <a name="background"></a>Achtergrond

Bij het schrijven van een DAX-expressie die mogelijk een evaluatiefout veroorzaakt, kunt u overwegen twee handige DAX-functies te gebruiken.

- De functie [ISERROR](/dax/iserror-function-dax), die één expressie aanneemt en TRUE retourneert als de expressie in een fout resulteert.
- De functie [IFERROR](/dax/iferror-function-dax), die twee expressies gebruikt. Als de eerste expressie in een fout resulteert, wordt de waarde voor de tweede expressie geretourneerd. Het is in feite een meer geoptimaliseerde implementatie van het nesten van de functie ISERROR binnen een [IF](/dax/if-function-dax)-functie.

Hoewel deze functies echter nuttig kunnen zijn en kunnen bijdragen aan het schrijven van eenvoudig te begrijpen expressies, kunnen ze ook de prestaties van berekeningen aanzienlijk verslechteren. Dit komt doordat deze functies het aantal vereiste scans van de opslagengine verhogen.

Houd er rekening mee dat de meeste evaluatiefouten worden veroorzaakt door onverwachte lege waarden of nulwaarden, of ongeldige gegevenstypeconversie.

## <a name="recommendations"></a>Aanbevelingen

Het is beter om te voorkomen dat de functies ISERROR en IFERROR worden gebruikt. Pas in plaats daarvan verdedigingsstrategieën toe bij het ontwikkelen van het model en het schrijven van expressies. Bijvoorbeeld:

- **Garanderen dat kwaliteitsgegevens in het model worden geladen:** gebruik Power Query-transformaties voor het verwijderen of vervangen van ongeldige of ontbrekende waarden en om correcte gegevenstypen in te stellen. Een Power Query-transformatie kan ook worden gebruikt om rijen te filteren wanneer er fouten optreden, zoals ongeldige gegevensconversie.

    De kwaliteit van gegevens kan ook worden bepaald door de eigenschap **Is Nullable** van de modelkolom op Uit in te stellen, waardoor het vernieuwen van gegevens mislukt als er lege waarden worden aangetroffen. Als deze fout optreedt, blijven de gegevens die zijn geladen als gevolg van een geslaagde vernieuwing in de tabellen aanwezig.
- **De functie IF gebruiken:** de logische testexpressie van de functie IF kan worden gebruikt om te bepalen of er een foutresultaat zou optreden. Zoals de functies ISERROR en IFERROR kan deze functie leiden tot extra scans van de opslagengine, maar presteert deze functie waarschijnlijk beter omdat er geen fout hoeft te worden gegenereerd.
- **Fouttolerante functies gebruiken:** met sommige DAX-functies worden foutsituaties getest en gecompenseerd. Met deze functies kunt u een alternatief resultaat invoeren dat in plaats daarvan wordt geretourneerd. De functie [DIVIDE](/dax/divide-function-dax) is daar een voorbeeld van. Lees voor meer informatie over deze functie het artikel [DAX: DIVIDE-functie ten opzichte van deeloperator (/)](dax-divide-function-operator.md).

## <a name="example"></a>Voorbeeld

De volgende meetexpressie test of er een fout zou worden gegenereerd. Er wordt in dit geval een lege waarde geretourneerd (dit is het geval wanneer u de functie IF niet opgeeft met een waarde-if-false-expressie).
```dax
= IF(ISERROR([Profit] / [Sales]))
```
Deze volgende versie van de meetexpressie is verbeterd door gebruik te maken van de functie IFERROR in plaats van de functies IF en ISERROR.
```dax
= IFERROR([Profit] / [Sales], BLANK())
```
Deze definitieve versie van de meetexpressie levert hetzelfde resultaat op, maar is efficiënter en eleganter.
```dax
= DIVIDE([Profit], [Sales])
```