---
title: Aanbevolen tabellen in Power BI Desktop instellen
description: Maak aanbevolen tabellen in Power BI Desktop zodat ze worden weergegeven in de galerie Organisatiegegevenstypen in Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906883"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Aanbevolen tabellen in Power BI Desktop zo instellen dat ze worden weergegeven in de galerie Organisatiegegevenstypen in Excel

In de galerie Gegevenstypen in Excel kunnen uw gebruikers gegevens uit *aanbevolen tabellen* in uw Power BI-gegevenssets vinden. In dit artikel leert u hoe u tabellen als *aanbevolen* tabellen in uw gegevenssets instelt. Met deze tags is het voor uw gebruikers eenvoudiger om zakelijke gegevens aan hun Excel-werkbladen toe te voegen. Dit zijn de basisstappen voor het instellen en delen van aanbevolen tabellen.

1. U identificeert aanbevolen tabellen in uw gegevenssets in Power BI Desktop (dit artikel)
1. U slaat die gegevenssets met aanbevolen tabellen op in één van de nieuwe werkruimten. Auteurs van rapporten kunnen rapporten met die aanbevolen tabellen maken. 
1. De rest van de organisatie kan verbinding maken met die aanbevolen tabellen, ook wel *gegevenstypen* genoemd in Excel, voor relevante en vernieuwbare gegevens. In het artikel [Toegang tot aanbevolen Power BI-tabellen in Excel](service-excel-featured-tables.md) wordt het gebruiken van deze aanbevolen tabellen in Excel besproken.

> [!NOTE]
> U kunt [gegevenssets in Power BI promoveren of certificeren](../collaborate-share/service-endorse-content.md). Dat wordt *goedkeuring* genoemd. In Excel krijgen tabellen in goedgekeurde gegevenssets in de galerie met gegevenstypen een hogere prioriteit. In Excel worden eerst aanbevolen tabellen in gecertificeerde gegevenssets vermeld, vervolgens tabellen in gepromoveerde gegevenssets. In Excel worden daarna aanbevolen tabellen in niet-goedgekeurde gegevenssets vermeld. 

> [!NOTE]
> Vanaf de Power BI Desktop versie van december 2020 is het maken van aanbevolen tabellen standaard beschikbaar. Als u een eerdere versie gebruikt, voert u een upgrade van Power BI Desktop uit of schakelt u de capaciteit **Aanbevolen tabellen** in via **Bestand** > **Opties en instellingen** > **Opties** > **Preview-functies**.

## <a name="select-a-table"></a>Een tabel selecteren

1. Ga in Power BI Desktop naar de modelweergave.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modelweergave":::
 
2. Selecteer een tabel en stel **Is een aanbevolen tabel** in **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Stel Is aanbevolen tabel in op Ja":::

4. Geef in **Deze aanbevolen tabel instellen** de vereiste velden op:

    - **Beschrijving**. 
        > [!TIP]
        > Begin de beschrijving met 'Aanbevolen tabel' zodat makers van Power BI-rapporten deze kunnen identificeren.
    - De waarde van het veld **Rijlabel** wordt gebruikt in Excel, zodat gebruikers de rij eenvoudig kunnen identificeren. De waarde wordt weergegeven als de celwaarde voor een gekoppelde cel, in het deelvenster **Gegevenskiezer** en op de kaart **Gegevens**. 
    - De waarde van het veld **Sleutelkolom** bevat de unieke id voor de rij. Met deze waarde kan Excel een cel koppelen aan een specifieke rij in de tabel.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Deze aanbevolen tabel instellen":::

1. Nadat u de gegevensset hebt gepubliceerd of geïmporteerd naar de Power BI-service, wordt de aanbevolen tabel weergegeven in de galerie Gegevenstypen van Excel. U en andere rapportmakers kunnen ook rapporten maken op basis van deze gegevensset.

1. In Excel: 
    - Excel slaat de lijst met gegevenstypen op in de cache, wat betekent dat u Excel opnieuw moet starten om nieuw gepubliceerde aanbevolen tabellen te zien.
    - Sommige gegevenssets worden niet ondersteund. De aanbevolen tabellen die in deze gegevenssets zijn gedefinieerd, worden niet weergegeven in Excel. Bekijk de volgende sectie, Overwegingen en beperkingen, voor meer informatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Dit zijn de huidige beperkingen:

- De integratie is beschikbaar in Excel in het huidige kanaal.
- Aanbevolen tabellen in Power BI-gegevenssets die gebruikmaken van de volgende mogelijkheden, worden niet weergegeven in Excel: 

    - DirectQuery-gegevenssets
    - Gegevenssets met een liveverbinding

- In Excel worden alleen gegevens in kolommen, berekende kolommen en in de aanbevolen tabel gedefinieerde metingen weergegeven. De volgende opties zijn niet beschikbaar:
   
    - Metingen die zijn gedefinieerd in gerelateerde tabellen.
    - Impliciete metingen berekend op basis van relaties.

- In Excel worden alleen aanbevolen tabellen (*gegevenstypen*) weergegeven die zijn opgeslagen in de nieuwe Power BI-werkruimten. Aanbevolen tabellen die zijn opgeslagen in de klassieke werkruimten, worden niet als gegevenstypen in Excel weergegeven. U kunt [klassieke werkruimten bijwerken naar de nieuwe werkruimten](service-upgrade-workspaces.md) in Power BI.

De ervaring van gegevenstypen in Excel is vergelijkbaar met een opzoekfunctie. Er wordt een celwaarde aangeboden door het Excel-werkblad, waarna er wordt gezocht naar overeenkomende rijen in aanbevolen tabellen van Power BI. De zoekervaring heeft de volgende gedragskenmerken:

- Overeenkomende rijen worden gebaseerd op tekstkolommen in de aanbevolen tabel. De ervaring maakt gebruik van dezelfde indexering als de functie Power BI Q&A, die is geoptimaliseerd voor het zoeken in de Engelse taal. Zoeken in andere talen levert mogelijk geen nauwkeurige overeenkomsten op. 
- De meeste numerieke kolommen worden niet meegenomen bij het zoeken naar overeenkomsten. Als het rijlabel of de sleutelkolom numeriek is, worden deze opgenomen bij het zoeken naar overeenkomsten.
- Vergelijken is gebaseerd op exacte en voorvoegselovereenkomsten voor afzonderlijke zoektermen. De waarde van een cel wordt gesplitst op basis van spaties of andere witruimtetekens, zoals tabs. Vervolgens wordt elk woord beschouwd als zoekterm. De tekstveldwaarden van een rij worden vergeleken met de zoektermen voor exacte en voorvoegselovereenkomsten. Er wordt een voorvoegselovereenkomst geretourneerd als het tekstveld van de rij begint met de zoekterm. Als een cel bijvoorbeeld 'Geldersch Landschap' bevat, zijn 'Geldersch' en 'Landschap' unieke zoektermen. 

    - Rijen met tekstkolommen waarvan de waarden exact overeenkomt met 'Geldersch' of 'Landschap' worden geretourneerd. 
    - Rijen met tekstkolommen waarvan de waarden beginnen met 'Geldersch' of 'Landschap' worden geretourneerd. 
    - Belangrijk: rijen die 'Geldersch' of 'Landschap' bevatten, maar niet beginnen met deze termen worden niet geretourneerd.

- Power BI retourneert maximaal 100 rijsuggesties voor elke cel.
- Sommige symbolen worden niet ondersteund.
- Het instellen of bijwerken van de aanbevolen tabel wordt niet ondersteund in het XMLA-eindpunt
- Excel-bestanden met een gegevensmodel kunnen worden gebruikt voor het publiceren van aanbevolen tabellen. Laad de gegevens in Power BI Desktop en publiceer vervolgens de aanbevolen tabel.
- Als u de tabelnaam, het rijlabel of de sleutelkolom wijzigt in de aanbevolen tabel, kan dit gevolgen hebben voor Excel-gebruikers met cellen die zijn gekoppeld aan rijen in de tabel. 
- Excel geeft aan wanneer de gegevens zijn opgehaald uit de Power BI-gegevensset. Dit hoeft niet de tijd te zijn dat de gegevens zijn vernieuwd in Power BI, of de tijd van het meest recente gegevenspunt in een gegevensset. Stel bijvoorbeeld dat een gegevensset in Power BI een week geleden is vernieuwd, maar dat de onderliggende brongegevens een week oud waren op het moment van vernieuwen. De gegevens zijn dan in werkelijkheid twee weken oud, maar in Excel wordt dan de datum/tijd weergegeven waarop de gegevens zijn opgehaald in Excel.
- Zie [Overwegingen en beperkingen](service-excel-featured-tables.md#considerations-and-limitations) in het artikel Toegang tot aanbevolen Power BI-tabellen in Excel voor andere Excel-overwegingen.

## <a name="next-steps"></a>Volgende stappen

- [Toegang tot aanbevolen Power BI-tabellen in Excel](service-excel-featured-tables.md)
- Lees meer over [het gebruik van Excel-gegevenstypen vanuit Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) in de Excel-documentatie.
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

