---
title: Drillthrough voor rapportpagina gebruiken
description: Richtlijnen voor het werken met drillthrough voor rapportpagina's.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/28/2019
ms.openlocfilehash: 4aa7c3992183dad6fad30e31e31e935fbaa29c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418481"
---
# <a name="use-report-page-drillthrough"></a>Drillthrough voor rapportpagina gebruiken

Dit artikel is bedoeld voor u wanneer u als auteur Power BI-rapporten gaat ontwerpen. U vindt hier suggesties en aanbevelingen voor het maken van een [drillthrough voor rapportpagina's](../create-reports/desktop-drillthrough.md).

U kunt het rapport het beste zo ontwerpen dat rapportgebruikers de volgende stroom bereiken:

1. Een rapport weergeven.
2. Een visueel element identificeren voor een uitgebreidere analyse.
3. Op de rechtermuisknop op het visuele element klikken om de drillthrough uit te voeren.
4. Aanvullende analyse uitvoeren.
5. Terugkeren naar de bronrapportpagina.

## <a name="suggestions"></a>Suggesties

Er zijn twee drillthrough-scenario's die u kunt bekijken:

- [Aanvullende uitgebreidere informatie](#additional-depth)
- [Breder perspectief](#broader-perspective)

### <a name="additional-depth"></a>Aanvullende uitgebreidere informatie

Wanneer een overzicht van de resultaten op uw rapportpagina wordt weergegeven, kunnen gebruikers van het rapport via een drillthrough-pagina meer informatie op transactieniveau bekijken. Dankzij deze ontwerpmethode kunnen ze, uitsluitend wanneer ze dat willen, ondersteunende transacties bekijken.

In het volgende voorbeeld ziet u wat er gebeurt wanneer een rapportgebruiker een drillthrough uitvoert op basis van een overzicht van de maandelijkse verkoop. Op de drillthrough-pagina staat een gedetailleerde lijst met orders voor een specifieke maand.

![In de matrixvisual 'Verkoopoverzicht' wordt de verkoop in de rijen per jaar en maand gegroepeerd, en in de kolommen per land. Ook wordt een drillthrough-pagina weergegeven.](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>Breder perspectief

Met een drillthrough-pagina kunt u het tegenovergestelde bereiken als met aanvullende uitgebreidere informatie. Dit scenario is nuttig om dieper op de informatie in te gaan om een holistische weergave te krijgen.

In het volgende voorbeeld ziet u wat er gebeurt wanneer een rapportgebruiker een drillthrough uitvoert op basis van een postcode. Op de drillthrough-pagina wordt algemene informatie over die postcode weergegeven.

![Een tabelvisual heeft drie kolommen: Postcode, Gemiddeld aantal schendingspunten en Gemiddelde waardering. Ook wordt de drillthrough-pagina weergegeven.](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>Aanbevelingen

Tijdens het ontwerpen van een rapport worden de volgende werkwijzen aangeraden:

- **Stijl:** Ontwerp uw drillthrough-pagina zodanig dat hiervoor hetzelfde thema en dezelfde stijl als voor het rapport worden gebruikt. Op deze manier hebben gebruikers het idee dat ze hetzelfde rapport voor zich hebben.
- **Drillthrough-filters:** Stel drillthrough-filters in zodat u een voorbeeld van een realistisch resultaat kunt bekijken tijdens het ontwerpen van de drillthrough-pagina. Vergeet deze filters niet te verwijderen voordat u het rapport publiceert.
- **Aanvullende mogelijkheden:** Een drillthrough-pagina is vergelijkbaar met een rapportpagina. U kunt deze zelfs uitbreiden met aanvullende interactieve mogelijkheden, zoals slicers of filters.
- **Lege waarden:** Voeg geen visuals toe waardoor BLANK kan worden weergegeven of die fouten genereren wanneer drillthrough-filters worden toegepast.
- **Zichtbaarheid pagina:** U kunt drillthrough-pagina's verbergen. Als u besluit een drillthrough-pagina zichtbaar te houden, moet u ook een knop toevoegen waarmee gebruikers eventueel eerder ingestelde drillthrough-filters kunnen wissen. Wijs een [bladwijzer](../create-reports/desktop-bookmarks.md) aan de knop toe. De bladwijzer moet zo worden geconfigureerd dat u hiermee alle filters kunt verwijderen.
- **Knop Terug:** De [knop](../create-reports/desktop-buttons.md) Terug wordt automatisch toegevoegd wanneer u een drillthrough-filter toewijst. Het is handig om deze knop te behouden. Op deze manier kunnen uw rapportgebruikers eenvoudig naar de bronpagina terugkeren.
- **Detectie:** Maak gebruikers bewust van een drillthrough-pagina door tekst voor het pictogram van de visualheader in te stellen of door instructies aan een tekstvak toe te voegen. Ook kunt u een overlay ontwerpen. Dit wordt in [deze blogpost](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/) beschreven.

> [!TIP]
> Het is ook mogelijk om drillthrough naar uw gepagineerde Power BI-rapporten te configureren. U doet dit door koppelingen aan Power BI-rapporten toe te voegen. Met koppelingen kunnen [URL-parameters](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/) worden gedefinieerd.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Drillthrough gebruiken in Power BI Desktop](../create-reports/desktop-drillthrough.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
