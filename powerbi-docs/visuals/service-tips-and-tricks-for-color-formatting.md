---
title: Tips en trucs voor het gebruik van kleuren in Power BI
description: Tips en trucs voor het gebruik van kleuren in Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: d3fba99c5b6b639d851b62d5624331b0bef1567d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61390684"
---
# <a name="tips-and-tricks-for-color-formatting-in-power-bi"></a>Tips en trucs voor het gebruik van kleuren in Power BI
Power BI biedt veel verschillende manieren voor het aanpassen van uw dashboards en rapporten. In dit artikel vindt u een verzameling tips die ervoor kunnen zorgen dat uw Power BI-visualisaties boeiend, interessant en afgestemd op uw behoeften zijn.

De volgende tips worden gegeven. Hebt u nog een goede tip? Mooi! Stuur de tip naar ons en we zullen kijken of deze aan de lijst kan worden toegevoegd.

* De kleur van één gegevenspunt wijzigen
* De kleuren van een grafiek baseren op een numerieke waarde
* De kleur van gegevenspunten baseren op een veldwaarde
* Kleuren in de kleurenschaal aanpassen
* Uiteenlopende kleurenschalen gebruiken
* Hoe kunt u iets ongedaan maken in Power BI?

Als u eventuele wijzigingen wilt aanbrengen, moet u een rapport bewerken. Open het rapport en selecteer **Rapport bewerken** in het bovenste menu, zoals wordt weergegeven in de volgende afbeelding.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-edit.png)

Wanneer het deelvenster **Visualisaties** wordt weergegeven aan de rechterkant van het **rapportcanvas**, kunt u beginnen met aanpassen. Als het deelvenster niet wordt weergegeven, selecteert u de pijl in de rechterbovenhoek om het te openen.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-formatting-pane.png)

## <a name="change-the-color-of-a-single-data-point"></a>De kleur van één gegevenspunt wijzigen
Soms wilt u een bepaald gegevenspunt markeren. Misschien zijn het verkoopcijfers voor de lancering van een nieuw product, of hogere kwaliteitsscores na de lancering van een nieuw programma. Met Power BI kunt u een gegevenspunt markeren door de kleur ervan te wijzigen.

In de volgende visualisatie worden per productsegment verkochte eenheden gerangschikt. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-grey.png)

Stel u voor dat u het segment **Gemak** wilt aanroepen om op basis van kleur te zien hoe goed dit splinternieuw segment presteert. Dit zijn de stappen:

Vouw de sectie **Gegevenskleuren** uit en schakel de schuifregelaar Aan in op **Alles weergeven**. Hiermee worden de kleuren voor elk gegevenselement in de visualisatie weergegeven. Wanneer u met de muisaanwijzer over de gegevenspunten beweegt, is schuiven ingeschakeld zodat u alle gegevenspunten kunt wijzigen.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Stel **Gemak** in op oranje. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-orange.png)

Wanneer dit is geselecteerd, heeft het gegevenspunt **Gemak** een mooie oranje kleur die zeker opvalt.

Zelf als u visualisatietypen wijzigt en vervolgens terugkeert, onthoudt Power BI uw selectie en blijft **Gemak** oranje.

U kunt de kleur van een gegevenspunt voor één, meerdere of alle gegevenselementen in de visualisatie wijzigen. Wellicht wilt u dat uw visual uw bedrijfskleuren bevat. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Er zijn veel verschillende dingen die u met kleuren kunt doen. In de volgende sectie gaan we in op kleurovergangen.

## <a name="base-the-colors-of-a-chart-on-a-numeric-value"></a>De kleuren van een grafiek baseren op een numerieke waarde
Grafieken profiteren vaak van dynamisch ingestelde kleuren op basis van de numerieke waarde van een veld. Hiermee kunt u een andere waarde laten zien dan wat u gewend bent voor de grootte van een balk en twee waarden in één grafiek weergeven. Of u kunt dit gebruiken om gegevenspunten boven (of onder) een bepaalde waarde te markeren - misschien om gebieden met een lage winstgevendheid te accentueren.

In de volgende secties worden verschillende manieren beschreven om kleur te baseren op een numerieke waarde.

## <a name="base-the-color-of-data-points-on-a-value"></a>De kleur van gegevenspunten baseren op een waarde
Als u de kleur wilt wijzigen op basis van een waarde, sleept u het veld waarop u de kleur wilt baseren, naar het gebied **Kleurverzadiging** in het deelvenster **Velden**. In de volgende afbeelding is **Marktaandeelpercentage SPLY YTD** naar **Kleurverzadiging** gesleept. 

![](media/service-tips-and-tricks-for-color-formatting/power-bi-color-saturation.png)

En in het opmaakvenster onder **Gegevenskleuren** bepaalt u hoe de waarde van **Marktaandeelpercentage SPLY YTD** de kleur en arcering in uw kolomdiagram verandert. In dit voorbeeld is een lager marktaandeelpercentage lichtblauw en hogere waarden donkerblauw.


![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


U ziet dat, hoewel er meer eenheden van zowel **Productiviteit** als **Extreem** zijn verkocht (die kolommen zijn hoger), **Toezicht** een groter **Marktaandeelpercentage SPLY YTD** heeft (die kolom heeft meer kleurverzadiging).

![](media/service-tips-and-tricks-for-color-formatting/power-bi-saturation.png)

## <a name="customize-the-colors-used-in-the-color-scale"></a>De kleuren in de kleurenschaal aanpassen
U kunt de kleuren in de kleurenschaal ook aanpassen. Standaard wordt de laagste waarde in uw gegevens toegewezen aan de minst verzadigde kleur en de hoogste waarde aan de meest verzadigde kleur. In de afbeelding hierboven hebben we een blauw kleurovergang gebruikt. 

Vouw **Gegevenskleuren** uit en u ziet een kleurovergang van de kleuren die worden gebruikt voor het visualiseren van uw gegevens. Het kleurbereik wordt weergegeven in een kleurenbalk met het spectrum tussen de kleurwaarden **Minimum** en **Maximum** met **Minimum** aan de linkerzijde en  **Maximum**helemaal rechts.

![](media/service-tips-and-tricks-for-color-formatting/power-bi-data-colors2.png)


Als u de schaal wilt wijzigen om een ander kleurbereik te gebruiken, selecteert u de keuzelijst met kleuren naast **Minimum** of **Maximum**en selecteert u een kleur. In de volgende afbeelding is de kleur **Maximum** gewijzigd in zwart en de kleurenbalk geeft het nieuwe kleurenspectrum aan tussen **Minimum** en **Maximum**.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_11.png)

U kunt ook de manier wijzigen waarop de waarden aan deze kleuren worden toegewezen. In de volgende afbeelding zijn de kleuren voor **Minimum** en **Maximum** ingesteld op respectievelijk oranje en groen.

In deze eerste afbeelding ziet u hoe de balken in de grafiek het kleurverloop in de balk weergeven; de hoogste waarde is groen, de laagste is oranje en elke balk ertussen is gekleurd met een tint uit het spectrum tussen groen en oranje.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_12.png)

Nu gaan we kijken wat er gebeurt als wij numerieke waarden opgeven in de vakken **Minimum** en **Maximum** onder de kleurenkiezers **Minimum** en **Maximum** (zie volgende afbeelding). Stel **Minimum** in op 20.000.000 en **Maximum** in op 20.000.001.

Door het instellen van deze waarden wordt het verloop niet langer toegepast op de waarden in de grafiek die onder **Minimum** of boven **Maximum** liggen; een balk met een waarde boven **Maximum** is groen en een balk met een waarde onder **Minimum** is rood.

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_13.png)

## <a name="use-diverging-color-scales"></a>Uiteenlopende kleurenschalen gebruiken
Soms kunnen uw gegevens van nature verschillen. Een temperatuurbereik heeft bijvoorbeeld een natuurlijk midden op het vriespunt en een rentabiliteitsscore heeft een natuurlijk middelpunt (nul).

Voor het gebruik van uiteenlopende kleurenschalen schuift u de schuifregelaar **Afwijken** naar **Aan**. Wanneer **Afwijken** is ingeschakeld, verschijnen een extra kleurenkiezer en waardevak, beiden **Midden** genoemd (zie de volgende afbeelding).

![](media/service-tips-and-tricks-for-color-formatting/tipstrickscolor_14.png)

Wanneer de schuifregelaar **Afwijken** is ingeschakeld, kunt u de kleuren afzonderlijk instellen voor **Minimum**, **Maximum** en **Midden**. In de volgende afbeelding is **Midden** ingesteld op één, dus balken met waarden boven één zijn een kleurtint van groen en balken onder één zijn tinten van rood.

## <a name="how-to-undo-in-power-bi"></a>Hoe kunt u iets ongedaan maken in Power BI?
Net als in veel andere services en software van Microsoft, biedt Power BI een eenvoudige manier om de laatst uitgevoerde opdracht ongedaan te maken. Laten we bijvoorbeeld zeggen dat u de kleur van een gegevenspunt of een reeks gegevenspunten wijzigt en dat de weergegeven kleur in de visualisatie u niet bevalt. U weet niet precies welke kleur het eerder was, maar u weet wel dat u die kleur terug wilt!

Als u uw laatste actie of acties **ongedaan wilt maken** , doet u het volgende:

- Typ CTRL+Z

## <a name="feedback"></a>Feedback
Hebt u een tip die u wilt delen? Stuur de tip naar ons en we zullen kijken of we deze kunnen toevoegen.

>[!NOTE]
>Deze aanpassingen van kleur, assen en overige aanpassingen die beschikbaar zijn wanneer het pictogram **Opmaak** is geselecteerd, zijn ook beschikbaar in Power BI Desktop.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag met de kleuropmaak en de eigenschappen van assen](service-getting-started-with-color-formatting-and-axis-properties.md)

