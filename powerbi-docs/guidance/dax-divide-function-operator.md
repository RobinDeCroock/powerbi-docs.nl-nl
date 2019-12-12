---
title: 'DAX: DIVIDE-functie t.o.v. deeloperator (/)'
description: Richtlijnen voor het gebruik van de DAX DIVIDE-functie.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695192"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: DIVIDE-functie t.o.v. deeloperator (/)

Wanneer u als gegevensmodeleerder een DAX-expressie schrijft om een teller door een noemer te delen, kunt u kiezen of u de functie [DIVIDE](/dax/divide-function-dax) of de operator voor delen (/ - slash) wilt gebruiken.

Wanneer u de functie DIVIDE gebruikt, moet u de expressies opgeven in de teller en noemer. U kunt desgewenst een waarde opgeven die een _alternatief resultaat_ vertegenwoordigt.

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

De functie DIVIDE is zo ontworpen dat deze delen door nul automatisch verwerkt. Als er geen alternatief resultaat wordt doorgegeven en de noemer nul of leeg is, retourneert de functie een leeg resultaat. Wanneer een alternatief resultaat is opgegeven, wordt dit geretourneerd in plaats van BLANK.

De functie voor delen is handig omdat deze voorkomt dat uw expressie eerst de waarde van de noemer moet testen. De functie is ook beter geoptimaliseerd voor het testen van de waarde van de noemer dan de functie [IF](/dax/if-function-dax). De prestaties zijn aanzienlijk verbeterd omdat de controle op delen door nul kostbaar kan zijn. Het verdere gebruik van DIVIDE levert een beknoptere en elegantere expressie op.

## <a name="example"></a>Voorbeeld

De volgende meetexpressie levert een veilige deling op, maar hiervoor worden vier DAX-functies gebruikt.

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

Deze meetexpressie levert hetzelfde resultaat op, maar is efficiënter en eleganter.

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>Aanbevelingen

U wordt aangeraden de functie DIVIDE te gebruiken wanneer de noemer een expressie is die nul of leeg _zou kunnen_ retourneren.

Als de noemer een constante waarde is, raden we u aan de operator voor delen te gebruiken. In dit geval is de deling gegarandeerd goed en wordt de expressie beter, omdat onnodige tests worden voorkomen.

Overweeg zorgvuldig of de functie DIVIDE een alternatieve waarde moet retourneren. Bij metingen is het qua ontwerp normaal gesproken beter als er BLANK wordt geretourneerd wanneer er geen zinvol resultaat kan worden geëvalueerd. Zie [Avoid converting BLANKs to values](dax-avoid-converting-blank.md) (Converteren van BLANK naar waarden voorkomen) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
