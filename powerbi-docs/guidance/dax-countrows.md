---
title: 'DAX: COUNTROWS gebruiken in plaats van COUNT'
description: Richtlijnen voor het gebruik van de COUNTROWS-functies.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 8d3baba388900a9d57d6490db13c25cb363667ba
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088506"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX: COUNTROWS gebruiken in plaats van COUNT

Als gegevensmodelbouwer moet u in sommige gevallen een DAX-expressie schrijven waarmee tabelrijen worden geteld. De tabel kan een modeltabel zijn of een expressie waarmee een tabel wordt geretourneerd.

U kunt uw vereiste op twee manieren bereiken. U kunt de functie [COUNT](/dax/count-function-dax) gebruiken om kolomwaarden te tellen of u kunt de functie [COUNTROWS](/dax/countrows-function-dax) gebruiken om tabelrijen te tellen. Met beide functies bereikt u hetzelfde resultaat, mits de getelde kolom geen lege waarde bevat.

Voor de volgende definitie van een meting wordt een voorbeeld weergegeven. Hiermee wordt het aantal waarden in de kolom **OrderDate** berekend.

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

De meting retourneert een correct resultaat wanneer de granulariteit van de tabel **Sales** één rij per verkooporder is en de kolom **OrderDate** geen lege waarden bevat.

De volgende metingsdefinitie is echter een betere oplossing.

```dax
Sales Orders =
COUNTROWS(Sales)
```

Er zijn drie redenen waarom de tweede metingsdefinitie beter is:

- Deze definitie is efficiënter en zal dus betere prestaties leveren.
- Lege waarden in eender welke kolom van de tabel worden genegeerd.
- De intentie van de formule is duidelijker en bijna zelf-beschrijvend.

## <a name="recommendation"></a>Aanbeveling

Wanneer het uw intentie is om tabelrijen te tellen, wordt altijd aanbevolen de functie COUNTROWS te gebruiken.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)