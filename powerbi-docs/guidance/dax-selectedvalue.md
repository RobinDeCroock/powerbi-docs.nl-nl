---
title: 'DAX: SELECTEDVALUE gebruiken in plaats van VALUES'
description: Richtlijnen voor het gebruik van de functies SELECTEDVALUE.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 3f80a4bf4d7b220192c81e9c567d676e60f5baf0
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965052"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX: SELECTEDVALUE gebruiken in plaats van VALUES

Als gegevensmodelbouwer moet u soms een DAX-expressie schrijven waarmee u kunt testen of een kolom op een specifieke waarde wordt gefilterd.

In eerdere DAX-versies werd veilig aan deze vereiste voldaan door het gebruik van een patroon met drie DAX-functies. De functies zijn [IF](/dax/if-function-dax), [HASONEVALUE](/dax/hasonevalue-function-dax) en [VALUES](/dax/values-function-dax). Voor de volgende definitie van een meting wordt een voorbeeld weergegeven. Hiermee wordt het btw-bedrag berekend, maar alleen voor de verkoop aan klanten in Australië.

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

In ons voorbeeld wordt met de functie HASONEVALUE alleen TRUE geretourneerd wanneer de kolom **Country-Region** door één waarde wordt gefilterd. Als het resultaat TRUE is, wordt de functie VALUES vergeleken met de letterlijke tekst 'Australië'. Wanneer de functie VALUES de waarde TRUE retourneert, wordt de meting **Verkoop** met 0,10 vermenigvuldigd (dit staat voor 10%). Als de functie HASONEVALUE de waarde FALSE retourneert (omdat de kolom op meer dan één waarde wordt gefilterd), wordt met de eerste functie IF het resultaat BLANK geretourneerd.

Het gebruik van de functie HASONEVALUE is een defensieve techniek. Dit is vereist omdat het mogelijk is dat de kolom **Country-Region** door meerdere waarden wordt gefilterd. In dit geval wordt met de functie VALUES een tabel met meerdere rijen geretourneerd. Wanneer u een tabel met meerdere rijen met een scalaire waarde vergelijkt, wordt een fout gegenereerd.

## <a name="recommendation"></a>Aanbeveling

Het wordt aanbevolen de waarde [SELECTEDVALUE](/dax/selectedvalue-function) te gebruiken. Hiermee krijgt u hetzelfde resultaat als het patroon dat in dit artikel wordt beschreven, maar wel efficiënter en eleganter.

Met behulp van de functie SELECTEDVALUE wordt het voorbeeld van de metingdefinitie nu herschreven.

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> Het is nu mogelijk om een waarde voor een _alternatief resultaat_ in te voegen in de functie SELECTEDVALUE. De waarde voor het alternatieve resultaat wordt geretourneerd wanneer er geen filters (of meerdere filters) op de kolom worden toegepast.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)