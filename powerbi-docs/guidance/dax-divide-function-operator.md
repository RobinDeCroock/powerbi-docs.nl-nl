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
ms.openlocfilehash: 7266861304692a1c70f80e3cf9ed3f1fea60f750
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965488"
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

Overweeg zorgvuldig of de functie DIVIDE een alternatieve waarde moet retourneren. Het is voor maateenheden meestal een beter ontwerp wanneer ze leeg worden geretourneerd. Dit komt doordat rapportvisualisaties standaard groeperingen elimineren wanneer samenvattingen leeg zijn. Hierdoor kan de visualisatie worden geconcentreerd op groepen die gegevens bevatten. U kunt de visual zo nodig zo configureren dat alle groepen (die waarden of lege waarden retourneren) in de filtercontext worden weergegeven. Schakel hiervoor de optie [Items zonder gegevens weergeven](../create-reports/desktop-show-items-no-data.md) in.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)