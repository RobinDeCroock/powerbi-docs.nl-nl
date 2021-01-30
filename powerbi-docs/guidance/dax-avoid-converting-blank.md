---
title: 'DAX: Converteren van BLANK naar waarden voorkomen'
description: Richtlijnen voor het converteren van BLANK naar waarden.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/24/2019
ms.openlocfilehash: c7090b690f4b941068db91c4b47dad30373d0f16
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088552"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Converteren van BLANK naar waarden voorkomen

Als u als gegevensmodelbouwer expressies voor metingen schrijft, kunt u situaties tegenkomen waarin geen nuttige waarde kan worden geretourneerd. In deze gevallen bent u misschien geneigd om in plaats daarvan een waarde, zoals nul, te retourneren. We raden u aan zorgvuldig te bepalen of dit ontwerp efficiënt en praktisch is.

Bekijk de volgende metingsdefinitie, waarmee BLANK-resultaten expliciet naar nul worden geconverteerd.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Bekijk een andere metingsdefinitie, waarmee ook BLANK-resultaten naar nul worden geconverteerd.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

Met de functie [DIVIDE](/dax/divide-function-dax) wordt de meting **Winst** gedeeld door de meting **Verkoop**. Als het resultaat nul of BLANK is, wordt het derde argument, het alternatieve resultaat (dat optioneel is), geretourneerd. In dit voorbeeld wordt voor de meting gegarandeerd altijd een waarde geretourneerd, omdat nul als het alternatieve resultaat is doorgegeven.

Deze ontwerpen voor metingen zijn inefficiënt en leiden tot slechte rapportontwerpen.

Wanneer deze aan een rapportvisual worden toegevoegd, probeert Power BI alle groeperingen binnen de filtercontext op te halen. Het evalueren en ophalen van grote queryresultaten leidt vaak tot trage rapportrendering. Door elke voorbeeldmeting wordt een eenvoudige berekening in feite omgezet in een ingewikkelde berekening, waardoor Power BI noodgedwongen meer geheugen moet gebruiken dan noodzakelijk is.

Ook kunnen uw rapportgebruikers overweldigd raken als er te veel groeperingen zijn.

Laten we eens kijken wat er gebeurt wanneer de meting **Winstmarge** aan een tabelvisual wordt toegevoegd, en op klanten wordt gegroepeerd.

![Schermopname van Power BI Desktop met tabelweergave van gegevens met één rij per klant. De verkoopwaarden zijn LEEG en de winstmarges zijn nul procent. ](media/dax-avoid-converting-blank/table-visual-poor.png)

In de tabelvisual wordt een overweldigend aantal rijen weergegeven. (Het model bevat 18.484 klanten, dus de tabel probeert deze allemaal weer te geven.) U ziet dat de klanten die worden weergegeven, geen verkopen hebben bereikt. Maar omdat voor de meting **Winstmarge** altijd een waarde wordt weergegeven, worden ze wel weergegeven.

> [!NOTE]
> Wanneer er te veel gegevenspunten zijn om in een visual weer te geven, kunnen in Power BI strategieën voor gegevensreductie worden gebruikt om grote hoeveelheden queryresultaten te verwijderen of samen te vatten. Zie [Gegevenspuntlimieten en strategieën op visualtype](../visuals/power-bi-data-points.md) voor meer informatie.

Laten we eens kijken wat er gebeurd wanneer we de definitie voor de meting **Winstmarge** verbeteren. Nu wordt alleen nog een waarde geretourneerd wanneer de meting **Verkoop** niet BLANK is (of nul).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

In de tabelvisual worden nu alleen klanten weergegeven die binnen de huidige filtercontext een verkoop hebben gemaakt. De verbeterde meting biedt uw rapportgebruikers een efficiëntere en praktische ervaring.

![Schermopname van Power BI Desktop met een tabelweergave van gegevens die gefilterde inhoud bevatten.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> U kunt een visual zo nodig zo configureren dat alle groeperingen (die waarden of BLANK retourneren) in de filtercontext worden weergegeven. Schakel hiervoor de optie [Items zonder gegevens weergeven](../create-reports/desktop-show-items-no-data.md) in.

## <a name="recommendation"></a>Aanbeveling

Het is handig als uw metingen BLANK retourneren wanneer er geen nuttige waarde kan worden geretourneerd.

Deze ontwerpmethode is efficiënt en biedt Power BI de mogelijkheid om rapporten sneller weer te geven. Het retourneren van BLANK is tevens beter omdat rapportvisualisaties standaard groeperingen elimineren wanneer samenvattingen BLANK bevatten.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)