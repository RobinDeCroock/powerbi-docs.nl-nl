---
title: Aangepaste indelingen met ingesloten Power BI-inhoud
description: Lees meer over aangepaste indelingen wanneer u Power BI-inhoud in uw toepassing insluit.
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.openlocfilehash: cae661641149554a7ecedabda322eb3b181b7f1a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875846"
---
# <a name="custom-layouts"></a>Aangepaste indelingen

Gebruik een aangepaste indeling voor het insluiten van een rapport met een andere indeling dan het oorspronkelijke rapport. Het definiëren van een nieuwe indeling kan betrekking hebben op het definiëren van slechts één paginagrootte, het bepalen van de grootte van visuele elementen, of op positie en zichtbaarheid.

Als u een aangepaste indeling wilt definiëren, moet u een aangepast indelingsobject definiëren en deze doorgeven aan het instellingenobject in de insluitingsconfiguratie. Stel ook LayoutType in op Aangepast. Zie [Configuratiedetails insluiten](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details) voor meer informatie.

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Objectdefinitie

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: Gebruik de paginagrootte om de grootte van het tekengebied te bepalen (bijv. wit vlak in het rapport).
- `displayOptions`: Mogelijke waarden zijn: FitToWidth, FitToPage of ActualSize. Hiermee bepaalt u de schaal waarop het canvas in het iframe past.
- `pagesLayout`: Hiermee bepaalt u de indeling voor elk visuele element. zie PagesLayout voor meer informatie.

## <a name="pages-layout"></a>Indeling van de pagina 's

Wanneer u een indelingsobject voor pagina’s definieert, definieert u als het ware een indeling voor elke pagina, en voor elke pagina definieert u een indeling voor elk visuele element.
PageLayout is optioneel. Als u geen indeling voor een pagina definieert, wordt de standaardindeling (die in het rapport is opgeslagen) toegepast.

pagesLayout is een toewijzing van de paginanaam aan het PageLayout-object. Definitie:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout bevat een visuele indelingstoewijzing, waarbij de naam van elk visuele element wordt toegewezen aan een visueel indelingsobject:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Visuele indeling

Als u een visuele indeling wilt definiëren, voert u een nieuwe positie, grootte en zichtbaarheidsstatus in.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: Hiermee definieert u de nieuwe positie van de visual.
- `width`, hoogte: Hiermee definieert u de nieuwe grootte van de visual.
- `displayState`: Hiermee definieert u de nieuwe zichtbaarheid van de visual.

## <a name="update-layout"></a>Indeling bijwerken

U kunt de UpdateSettings-methode gebruiken om de indeling van het rapport op elk gewenst moment bij te werken terwijl het rapport wordt geladen. Zie [Instellingen bijwerken](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Voorbeeld van code

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;

var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};

// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');

// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);
```

## <a name="see-also"></a>Zie ook

[Dashboards, rapporten en tegels van Power BI insluiten](embedding-content.md)   
[Stel een vraag aan de Power BI-community](https://community.powerbi.com/)