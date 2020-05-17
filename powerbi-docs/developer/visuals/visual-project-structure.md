---
title: Projectstructuur van Power BI-visuals
description: In dit artikel wordt de map- en bestandsstructuur beschreven van een Power BI-visualproject
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 18267f06bd43166cb1958d3aff73913a31189953
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "80550766"
---
# <a name="power-bi-visual-project-structure"></a>Projectstructuur van Power BI-visuals

De beste manier om te beginnen met het maken van een nieuwe Power BI-visual is met het hulpprogramma [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools).

Als u een nieuwe visual wilt maken, navigeert u naar de map waarin u de Power BI-visual wilt opslaan, en voert u de volgende opdracht uit:

`pbiviz new <visual project name>`

Als u deze opdracht uitvoert, wordt er een Power BI-visualmap gemaakt die de volgende bestanden bevat:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Beschrijving van de map en het bestand

Deze sectie biedt informatie voor elke map en elk bestand in de map die wordt gemaakt met het hulpprogramma voor Power BI-visuals **pbiviz**.  

### <a name="vscode"></a>.vscode

Deze map bevat de projectinstellingen voor VS Code.

Bewerk het `.vscode/settings.json`-bestand om de werkruimte te configureren.

Zie [Instellingen voor gebruikers en werkruimte](https://code.visualstudio.com/docs/getstarted/settings) voor meer informatie

### <a name="assets"></a>assets

Deze map bevat het `icon.png`-bestand.

Het hulpprogramma voor Power BI-visuals gebruikt dit bestand als het nieuwe pictogram voor Power BI-visuals in het visualisatiedeelvenster van Power BI.

### <a name="src"></a>src

Deze map bevat de broncode van de visual.

In deze map worden met het hulpprogramma voor Power BI-visuals de volgende bestanden gemaakt:
* `visual.ts`: de hoofdbroncode van de visual.
* `settings.ts`: de code van de instellingen voor de visual. De klassen in het bestand bieden een interface voor het definiëren van de [eigenschappen van de visual](./objects-properties.md#properties).

### <a name="style"></a>stijl

Deze map bevat het `visual.less`-bestand, waarin de stijlen van de visual worden bewaard.

### <a name="capabilitiesjson"></a>capabilities.json

Dit bestand bevat de hoofdeigenschappen en instellingen (of [mogelijkheden](./capabilities.md)) voor de visual. Hiermee kunnen ondersteunde functies, objecten, eigenschappen en [toewijzing van gegevens](./dataview-mappings.md) voor de visual worden gedeclareerd.

### <a name="package-lockjson"></a>package-lock.json

Dit bestand wordt automatisch gegenereerd voor bewerkingen waarbij de `node_modules`-structuur of het `package.json`-bestand wordt gewijzigd met *npm*.

Raadpleeg de officiële documentatie voor [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) voor meer informatie over dit bestand.

### <a name="packagejson"></a>package.json

Dit bestand bevat een beschrijving van het projectpakket. Het bevat informatie over het project zoals auteurs, beschrijving, en projectafhankelijkheden.

Raadpleeg de officiële documentatie voor [npm-package.json](https://docs.npmjs.com/files/package.json.html) voor meer informatie over dit bestand.

### <a name="pbivizjson"></a>pbiviz.json

Dit bestand bevat de metagegevens van de visual.

Raadpleeg de sectie [Vermeldingen van metagegevens](#metadata-entries) voor een voorbeeld van een `pbiviz.json`-bestand met opmerkingen die de vermeldingen van metagegevens beschrijven.

### <a name="tsconfigjson"></a>tsconfig.json

Een configuratiebestand voor [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Dit bestand moet het pad bevatten naar het **\*.ts**-bestand, waar zich de hoofdklasse van de visual bevindt, opgegeven in de eigenschap `visualClassName` van het `pbiviz.json`-bestand.

### <a name="tslintjson"></a>tslint.json

Het bestand bevat de [TSLint-configuratie](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Vermeldingen van metagegevens

De opmerkingen in het volgende codebijschrift uit het `pbiviz.json`-bestand beschrijven de vermeldingen van metagegevens.

> [!NOTE]
> * Vanaf versie 3.x.x van het hulpprogramma **pbiviz** wordt `externalJS` niet ondersteund.
> * Voor lokalisatieondersteuning [voegt u de Power BI-landinstelling toe aan de visual](./localization.md).

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Volgende stappen

* Raadpleeg [concept van Power BI-visual](./power-bi-visuals-concept.md) voor meer informatie over de interactie tussen een visual, een gebruiker en Power BI.

* Begin met het ontwikkelen van uw eigen volledig nieuwe Power BI-visuals met behulp van een [ stapsgewijze handleiding](./custom-visual-develop-tutorial.md).
