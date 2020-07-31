---
title: Aanbevolen tabellen instellen in Power BI Desktop (preview-versie)
description: Maak aanbevolen tabellen in Power BI Desktop zodat ze worden weergegeven in de galerie Gegevenstypen in Excel.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: e39d2fe11a58691b259784c292fec6e5ee6cb322
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253995"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Aanbevolen tabellen instellen in Power BI Desktop (preview-versie)

In de galerie Gegevenstypen in Excel kunnen uw gebruikers gegevens uit *aanbevolen tabellen* in uw Power BI-gegevenssets vinden. In dit artikel leert u hoe u tabellen als *aanbevolen* tabellen in uw gegevenssets instelt. Met deze tags is het voor uw gebruikers eenvoudiger om zakelijke gegevens aan hun Excel-werkbladen toe te voegen. Dit zijn de basisstappen voor het instellen en delen van aanbevolen tabellen.

1. U [promoveert of certificeert gegevenssets in Power BI](../connect-data/service-datasets-promote.md). 
1. U identificeert aanbevolen tabellen in uw gegevenssets in Power BI Desktop (dit artikel)
1. U slaat die gegevenssets met aanbevolen tabellen op in één van de nieuwe werkruimten. Auteurs van rapporten kunnen rapporten met die aanbevolen tabellen maken. 
1. De rest van de organisatie kan verbinding maken met die aanbevolen tabellen, ook wel *gegevenstypen* genoemd in Excel, voor relevante en vernieuwbare gegevens. In het artikel [Toegang tot aanbevolen Power BI-tabellen in Excel (preview-versie)](service-excel-featured-tables.md) wordt het gebruiken van deze aanbevolen tabellen in Excel besproken.

## <a name="turn-on-the-featured-table-preview"></a>De preview-functie Aanbevolen tabellen inschakelen

1. Selecteer in Power BI Desktop **Bestand** > **Opties en instellingen** > **Opties** > **Preview-functies**.
2. Schakel het selectievakje **Aanbevolen tabellen** in.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="De preview-optie Aanbevolen tabellen":::

## <a name="select-a-table"></a>Een tabel selecteren

1. Ga in Power BI Desktop naar de modelweergave.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modelweergave":::
 
2. Selecteer een tabel en stel **Is een aanbevolen tabel** in **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Stel Is aanbevolen tabel in op Ja":::

4. Geef in **Deze aanbevolen tabel instellen**de vereiste velden op:

    - **Beschrijving**. 
        > [!TIP]
        > Begin de beschrijving met 'Aanbevolen tabel' zodat makers van Power BI-rapporten deze kunnen identificeren.
    - De waarde van het veld **Rijlabel** wordt gebruikt in Excel, zodat gebruikers de rij eenvoudig kunnen identificeren. De waarde wordt weergegeven als de celwaarde voor een gekoppelde cel, in het deelvenster **Gegevenskiezer** en op de kaart **Gegevens**. 
    - De waarde van het veld **Sleutelkolom** bevat de unieke id voor de rij. Met deze waarde kan Excel een cel koppelen aan een specifieke rij in de tabel.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Deze aanbevolen tabel instellen":::

1. Nadat u de gegevensset hebt gepubliceerd of geïmporteerd naar de Power BI-service, wordt de aanbevolen tabel weergegeven in de galerie Gegevenstypen van Excel. U en andere rapportmakers kunnen ook rapporten maken op basis van deze gegevensset.

1. In Excel: 
    - Excel slaat de lijst met gegevenstypen op in de cache, wat betekent dat u Excel opnieuw moet starten om nieuw gepubliceerde aanbevolen tabellen te zien.
    - Sommige gegevenssets worden niet ondersteund in de preview-versie. Aanbevolen tabellen die in deze gegevenssets zijn gedefinieerd, worden niet weergegeven in Excel. Bekijk de volgende sectie, Overwegingen en beperkingen, voor meer informatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Dit zijn de beperkingen voor de oorspronkelijke preview-versie.

- Aanbevolen tabellen in Power BI-gegevenssets die gebruikmaken van de volgende mogelijkheden, worden niet weergegeven in Excel: 

    - Gegevenssets met beveiliging op rijniveau
    - Gegevenssets waarvoor Microsoft Information Protection is ingeschakeld
    - DirectQuery-gegevenssets
    - Gegevenssets met een liveverbinding

- In Excel worden alleen gegevens in kolommen en berekende kolommen uit de aanbevolen tabel weergegeven. Het volgende is niet beschikbaar in de oorspronkelijke preview:

    - Metingen die zijn gedefinieerd voor de functietabel.
    - Metingen die zijn gedefinieerd voor gerelateerde tabellen, en impliciete metingen die worden berekend op basis van relaties.

- In Excel worden alleen aanbevolen tabellen weergegeven die zijn opgeslagen in de nieuwe Power BI-werkruimten. Aanbevolen tabellen die zijn opgeslagen in de klassieke werkruimten, of in Mijn werkruimte, worden niet weergegeven als gegevenstypen in Excel. U kunt [klassieke werkruimten bijwerken naar de nieuwe werkruimten](service-upgrade-workspaces.md) in Power BI.
- Zie [Overwegingen en beperkingen](service-excel-featured-tables.md#considerations-and-limitations) in het artikel Toegang tot aanbevolen Power BI-tabellen in Excel voor andere Excel-overwegingen.

## <a name="next-steps"></a>Volgende stappen

- [Toegang tot aanbevolen Power BI-tabellen in Excel](service-excel-featured-tables.md)
- Lees meer over [het gebruik van Excel-gegevenstypen vanuit Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) in de Excel-documentatie.
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

