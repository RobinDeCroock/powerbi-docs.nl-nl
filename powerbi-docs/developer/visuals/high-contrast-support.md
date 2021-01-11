---
title: Ondersteuning voor de modus voor hoog contrast in Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel wordt beschreven hoe u ondersteuning voor de modus met hoog contrast aan Power BI-visuals kunt toevoegen. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: f55427511a76fc65b3ae6b3933dca68ef742039c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889197"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>Ondersteuning voor de modus met hoog contrast in Power BI-visuals

De instelling *Hoog contrast* van Windows maakt tekst en apps gemakkelijker zichtbaar door meer contrasterende kleuren te gebruiken. In dit artikel wordt behandeld hoe u ondersteuning voor de modus met hoog contrast aan Power BI-visuals kunt toevoegen. Zie [ondersteuning voor hoog contrast in Power BI](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast) voor meer informatie.

Ga naar de [opslagplaats voor de visual PowerBI-visuals-sampleBarChart](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6) voor een implementatie van ondersteuning voor hoog contrast.

## <a name="on-initialization"></a>Bij initialisatie

Het lid colorPalette van `options.host` heeft verschillende eigenschappen voor de hoog-contrastmodus. Gebruik deze eigenschappen om te bepalen of de modus met hoog contrast actief is en zo ja, welke kleuren moeten worden gebruikt.

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Detecteren dat Power BI zich in de modus met hoog contrast bevindt

Als `host.colorPalette.isHighContrast` de waarde `true` heeft, is de hoog-contrastmodus actief en moet de visual dienovereenkomstig worden getekend.

### <a name="get-high-contrast-colors"></a>Kleuren met hoog contrast ophalen

In de modus met hoog contrast moet uw visual worden beperkt tot de volgende instellingen:

* De **voorgrondkleur** wordt gebruikt om lijnen, pictogrammen, tekst en contouren of opvullingen van vormen te tekenen.
* De **achtergrondkleur** wordt gebruikt voor de achtergrond, en als opvulkleur van vormen met contouren.
* **Voorgrond - geselecteerd** wordt gebruikt om een geselecteerd of actief element aan te geven.
* De **hyperlink**-kleur wordt alleen gebruikt voor hyperlinktekst.

> [!NOTE]
> Als er een secundaire kleur nodig is, kan de voorgrondkleur worden gebruikt met een bepaalde matheid (native visuals van Power BI gebruiken een matheid van 40%). Gebruik dit spaarzaam om de visuele details gemakkelijk zichtbaar te houden.

Tijdens de initialisatie kunt u de volgende waarden opslaan:

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

Of u kunt het `host`-object opslaan tijdens de initialisatie en de relevante `colorPalette`-eigenschappen gebruiken tijdens updates.

## <a name="on-update"></a>Bij updates

De specifieke implementaties van ondersteuning voor hoog contrast variëren van visual tot visual, en zijn afhankelijk van de details van het grafische ontwerp. Voor de modus voor hoog contrast is meestal een enigszins ander ontwerp dan de standaardmodus vereist, om de belangrijke gegevens gemakkelijk te onderscheiden met de beperkte kleuren.

Dit zijn de richtlijnen voor systeemeigen visuals van Power BI:

* Alle gegevenspunten hebben dezelfde kleur (voorgrond).
* Alle tekst, assen, pijlen, lijnen, enzovoort hebben de voorgrondkleur.
* Dikke vormen worden getekend als contouren, met dikke lijnen (ten minste twee pixels) en opgevuld met de achtergrondkleur.
* Indien relevant, worden gegevenspunten onderscheiden door markeringen met verschillende vormen, en gegevenslijnen door verschillende streepjes.
* Wanneer een gegevens element wordt gemarkeerd, wordt de matheid van alle andere elementen gewijzigd in 40%.
* Voor slicers gebruiken actieve filterelementen de kleur voorgrond-geselecteerd.

Zo worden in het volgende voorbeeldstaafdiagram alle balken getekend met een twee pixels dikke omtrek in de voorgrondkleur en een opvulling met de achtergrondkleur. Vergelijk de weergave met standaardkleuren en met een paar thema's met hoog contrast:

![Voorbeeld van een staafdiagram met standaardkleuren](media/high-contrast-support/hc-samplebarchart-standard.png)
![Voorbeeld van een staafdiagram met het thema *Hoog contrast nr. 2*](media/high-contrast-support/hc-samplebarchart-dark2.png)
![Voorbeeld van een staafdiagram met het thema *Wit - hoog contrast*](media/high-contrast-support/hc-samplebarchart-white.png)

In de volgende sectie wordt één plek weergegeven in de `visualTransform`-functie die is gewijzigd om hoog contrast te ondersteunen. Deze functie wordt aangeroepen als onderdeel van de rendering tijdens de update.

### <a name="before"></a>Voor

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>Na

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
