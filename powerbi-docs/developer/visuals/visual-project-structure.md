---
title: Projectstructuur van Power BI-visuals
description: In het artikel wordt een structuur van visualprojecten beschreven
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542088"
---
# <a name="power-bi-visual-project-structure"></a>Projectstructuur van Power BI-visuals

Na het uitvoeren van de nieuwe `<visual project name>` van de pbiviz wordt door het hulpprogramma de basisstructuur van bestanden en mappen gemaakt in de map `<visual project name>`.

## <a name="visual-project-structure"></a>Visualprojectstructuur

![Visualprojectstructuur](./media/visual-project-structure.png)

* `.vscode`: bevat instellingen van het project voor VS-code. Bewerk het bestand `.vscode/settings.json` om uw werkruimte te configureren. Meer informatie [over VS-code-instellingen in de documentatie](https://code.visualstudio.com/docs/getstarted/settings)

* De map `assets` bevat alleen het bestand `icon.png`. Dit bestand wordt door het hulpprogramma gebruikt als een pictogram van de visual in het deelvenster Visualisatie van Power BI.

    ![Het deelvenster Visualisatie](./media/visualization-pane-analytics-tab.png)

* De map `node_modules` bevat alle pakketten die [zijn geïnstalleerd door Node Package Manager](https://docs.npmjs.com/files/folders.html).

* De map `src` bevat de broncode van de visual. Via het hulpprogramma worden standaard twee bestanden gemaakt:

  * `visual.ts`: de hoofdbroncode van de visual.

  * `settings.ts`: de code van de instellingen voor de visual. Met de klassen in het bestand wordt [werken met de visuele eigenschappen](./objects-properties.md#properties) eenvoudiger.

* De map `style` bevat het bestand `visual.less` met stijlen voor de visual.

* Het bestand `capabilities.json` bevat de hoofdeigenschappen en -instellingen voor de visual. Hiermee kunnen ondersteunde functies, objecten, eigenschappen en toewijzing van gegevens voor de visual worden gedeclareerd.

    Lees meer [over de mogelijkheden in de documentatie](./capabilities.md).

* `package-lock.json` wordt automatisch gegenereerd voor bewerkingen waarbij de `node_modules`-structuur of `package.json` door NPM wordt gewijzigd.

    Lees meer [over `package-lock.json` in de officiële NPM-documentatie](https://docs.npmjs.com/files/package-lock.json).

* `package.json` bevat een beschrijving van het projectpakket. Gewoonlijk bevat het informatie over het project, de auteurs, de beschrijving en de afhankelijkheden van het project.

    Lees meer [over `package.json` in de officiële NPM-documentatie](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` bevat de metagegevens van de visual. Geef de metagegevens van de visual op in dit bestand.

    Typische inhoud van het bestand:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    waarbij het volgende geldt

  * `name`: de interne naam van de visual.

  * `displayName`: de naam van de visual in de gebruikersinterface van Power BI.

  * `guid`: de unieke id van de visual.

  * `visualClassName`: de naam van de hoofdklasse voor de visual. In Power BI wordt het exemplaar van deze klasse gemaakt om de visual te gaan gebruiken in Power BI-rapporten.

  * `version`: het versienummer van de visual.

  * `author`: bevat de naam van de auteur en het e-mailadres van de contactpersoon.

  * `icon` in `assets`: het pad naar het pictogrambestand voor de visual.

  * `externalJS` bevat paden naar JS-bibliotheken die in de visual worden gebruikt.

    > [!IMPORTANT]
    > In de nieuwste versie van hulpprogramma 3.x.x wordt `externalJS` niet meer gebruikt.

  * `style` is het pad naar de stijlbestanden.

  * `capabilities` is het pad naar het bestand `capabilities.json`.

  * `dependencies` is het pad naar het bestand `dependencies.json`. `dependencies.json` bevat informatie over R-pakketten die worden gebruikt in op R gebaseerde visuals.

  * `stringResources` is een matrix met paden naar bestanden met lokalisaties.

  Lees meer [over lokalisatie in visuals in de documentatie](./localization.md)

* `tsconfig.json` is een configuratiebestand voor TypeScript.

    Lees meer [over de TypeScript-configuratie in de officiële documentatie](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    `tsconfig.json` in de sectie `files` moet het pad bevatten naar het bestand *.ts, waar zich de hoofdklasse van de visual bevindt, opgegeven in de eigenschap `visualClassName` van bestand `pbiviz.json`.

* Het bestand `tslint.json` bevat een TSLint-configuratie.

    Lees meer [over de TSLint-configuratie in de officiële documentatie](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Volgende stappen

* Lees meer [over concepten van visuals](./power-bi-visuals-concept.md) voor meer inzicht in hoe visual, gebruiker en Power BI met elkaar communiceren.

* Begin met het ontwikkelen van uw eigen volledig nieuwe Power BI-visuals [met een stapsgewijze handleiding](./custom-visual-develop-tutorial.md).
