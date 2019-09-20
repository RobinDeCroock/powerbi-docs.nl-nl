---
title: 'DAX: DIVIDE-functie t.o.v. deeloperator (/)'
description: Richtlijnen voor het gebruik van de DAX DIVIDE-functie.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 7516aaedb886e7b9e0f57ed76f0a7c5e40efbd6d
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877852"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX: DIVIDE-functie t.o.v. deeloperator (/)

Dit artikel gaat in op de gegevens modelers die DAX-expressies definiëren.

## <a name="background"></a>Achtergrond

Wanneer u een DAX-expressie schrijft om een teller door een noemer te delen, kunt u kiezen of u de functie [DIVIDE](/dax/divide-function-dax) of de operator voor delen (/ - slash) wilt gebruiken.

Wanneer u de functie DIVIDE gebruikt, moet u de expressies opgeven in de teller en noemer. U kunt desgewenst een waarde opgeven die een alternatief resultaat vertegenwoordigt.

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

De functie DIVIDE is zo ontworpen dat deze delen door nul automatisch verwerkt. Als er geen alternatief resultaat wordt doorgegeven en de noemer nul of leeg is, retourneert de functie een leeg resultaat. Als een alternatief resultaat is opgegeven, wordt dit geretourneerd in plaats van een leeg resultaat.

De functie voor delen is handig omdat deze voorkomt dat uw expressie eerst de waarde van de noemer moet testen. De functie is ook beter geoptimaliseerd voor het testen van de waarde van de noemer dan de functie [IF](/dax/if-function-dax). De prestaties zijn aanzienlijk verbeterd omdat de controle op delen door nul kostbaar kan zijn. Het gebruik van DIVIDE levert ook een beknoptere en elegantere expressie op.

## <a name="example"></a>Voorbeeld

De volgende meetexpressie levert een veilige deling op, maar hiervoor worden vier DAX-functies gebruikt.

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

Deze meetexpressie levert hetzelfde resultaat op, maar is efficiënter en eleganter.

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>Aanbevelingen

U wordt aangeraden de functie DIVIDE te gebruiken wanneer de noemer een expressie is die nul of leeg _zou kunnen_ retourneren.

Als de noemer een constante waarde is, raden we u aan de operator voor delen te gebruiken. In dit geval is de deling gegarandeerd goed en wordt de expressie beter, omdat onnodige tests worden voorkomen.

Overweeg zorgvuldig of de functie DIVIDE een alternatieve waarde moet retourneren. Het is voor maateenheden meestal een beter ontwerp dat ze leeg worden geretourneerd. Dit komt doordat rapportvisualisaties standaard groeperingen elimineren wanneer samenvattingen leeg zijn. Hierdoor kan de visualisatie worden geconcentreerd op groepen die gegevens bevatten. U kunt de visualisatie zo nodig zo configureren dat alle groepen (die waarden of lege waarden retourneren) in de filtercontext worden weergegeven. Schakel hiervoor de optie "Items zonder gegevens weergeven" in.
