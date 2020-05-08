---
title: 'DAX: Verwijzingen naar kolommen en metingen'
description: Richtlijnen voor het verwijzen naar kolommen in metingen in uw DAX-expressies.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: 3ca49008639f7e3e084c8d045bc911aff57b7b21
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "75498732"
---
# <a name="dax-column-and-measure-references"></a>DAX: Verwijzingen naar kolommen en metingen

Als gegevensmodeleerder gebruikt u DAX-expressies die naar modelkolommen en -metingen verwijzen. Kolommen en metingen zijn altijd gekoppeld aan modeltabellen, maar deze koppelingen verschillen. Daarom doen we verschillende aanbevelingen voor de wijze waarop u naar beide verwijst in uw expressies.

## <a name="columns"></a>Kolommen

Een kolom is een object op tabelniveau en kolomnamen moeten uniek zijn in een tabel. Het is dus mogelijk dat dezelfde kolomnaam meerdere keren wordt gebruikt in uw model, als deze maar tot verschillende tabellen behoort. Er is nog een regel: een kolomnaam mag niet dezelfde naam hebben als een metingnaam of hiërarchienaam die in dezelfde tabel voorkomt.

Over het algemeen wordt het gebruik van een _volledig gekwalificeerde_ verwijzing naar een kolom niet afgedwongen door DAX. Een volledig gekwalificeerde verwijzing houdt in dat de tabelnaam voorafgaat aan de kolomnaam.

Hier volgt een voorbeeld van een definitie van een berekende kolom waarbij alleen kolomnaamverwijzingen worden gebruikt. De kolommen **Verkoop** en **Kosten** behoren beide tot een tabel met de naam **Orders**.

```dax
Profit = [Sales] - [Cost]
```

Dezelfde definitie kan worden herschreven met volledig gekwalificeerde kolomverwijzingen.

```dax
Profit = Orders[Sales] - Orders[Cost]
```

Soms moet u echter volledig gekwalificeerde kolomverwijzingen gebruiken wanneer Power BI ambiguïteit detecteert. Wanneer u een formule invoert, krijgt u een waarschuwing door middel van een rode kronkellijn en een foutbericht. Daarnaast moet u voor sommige DAX-functies, zoals de DAX-functie [LOOKUPVALUE](/dax/lookupvalue-function-dax), volledig gekwalificeerde kolommen gebruiken.

We raden u aan om altijd volledig gekwalificeerde kolomverwijzingen te gebruiken. De redenen hiervoor worden beschreven in de sectie [Aanbevelingen](#recommendations).

## <a name="measures"></a>Metingen

Een meting is een object op modelniveau. Daarom moeten metingnamen uniek zijn binnen het model. In het deelvenster **Velden** zien auteurs van rapporten echter dat elke meting is gekoppeld aan één modeltabel. Deze koppeling is ingesteld vanwege cosmetische redenen en u kunt deze configureren door de eigenschap **Starttabel** in te stellen voor de meting. Zie [Metingen in Power BI Desktop (uw metingen ordenen)](../desktop-measures.md#organizing-your-measures) voor meer informatie.

U kunt een volledig gekwalificeerde meting in uw expressies gebruiken. DAX IntelliSense biedt zelfs de suggestie aan. Het is echter niet nodig en het is geen aanbevolen procedure. Als u de starttabel voor een meting wijzigt, werken de expressies niet meer die een volledig gekwalificeerde metingverwijzing naar de tabel gebruiken. Vervolgens moet u elke ongeldige formule bewerken om de verwijzing naar de meting te verwijderen (of bij te werken).

We raden u aan om nooit volledig gekwalificeerde metingverwijzingen te gebruiken. De redenen hiervoor worden beschreven in de sectie [Aanbevelingen](#recommendations).

## <a name="recommendations"></a>Aanbevelingen

Onze aanbevelingen zijn eenvoudig en gemakkelijk te onthouden:

- Gebruik altijd volledig gekwalificeerde kolomverwijzingen
- Gebruik nooit volledig gekwalificeerde metingverwijzingen

Waarom?

- **Invoer van formules**: Expressies worden geaccepteerd, omdat er geen ambigue verwijzingen hoeven te worden opgelost. Daarnaast voldoet u aan de vereiste voor de DAX-functies waarvoor volledig gekwalificeerde kolomverwijzingen moeten worden gebruikt.
- **Degelijkheid**: Expressies blijven werken, zelfs wanneer u een eigenschap van de starttabel voor de meting wijzigt.
- **Leesbaarheid**: Expressies zijn snel en eenvoudig te begrijpen: u kunt snel bepalen of het om een kolom of meting gaat, op basis van het feit of deze al dan niet volledig gekwalificeerd is.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
