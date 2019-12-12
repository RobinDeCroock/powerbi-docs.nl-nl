---
title: Migratie naar powerbi-visuals-tools 3.x
description: Aan de slag met de nieuwe versie van powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 245475feeb43ee544117aaa54969f2de1e207cd5
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74696277"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migratie naar het nieuwe powerbi-visuals-tools 3.x.x

Vanaf versie 3 maakt Power BI Visuals Tools gebruik van Webpack voor het bouwen van aangepaste visuals.
De nieuwe versie biedt veel nieuwe mogelijkheden voor ontwikkelaars om visuele elementen te maken:

* TypeScript v3. x. x standaard. Vanaf TypeScript 1.5 is de naamgeving gewijzigd. [Meer informatie over TypeScript-modules](https://www.typescriptlang.org/docs/handbook/modules.html).

* ES6-modules worden ondersteund. U hoeft [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries) niet meer te gebruiken. In plaats daarvan gebruikt u ES6-importbewerkingen.

* Nieuwe versies van [D3v5](https://d3js.org/) en andere op ES6 modules gebaseerde bibliotheken worden ondersteund.

* Gereduceerde pakketgrootte. Webpack maakt gebruik van [tree shaking](https://webpack.js.org/guides/tree-shaking/) om ongebruikte code te verwijderen. Het vermindert de code van JS en daardoor krijgt u betere prestaties bij het laden van visuals.

* Verbeterde API-prestaties.

* De bibliotheek Globalize.js [is geïntegreerd](migrate-to-new-tools.md#remove-globalizejs-library) in formatting-utils.

* Hulpprogramma's maken gebruik van [webpack-bundel-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) om de codebasis van de visual weer te geven.

Alle migratiestappen voor de nieuwe versie van Power BI Visuals Tools worden hieronder beschreven.

## <a name="backward-compatibility"></a>Compatibiliteit met eerdere versies

In de nieuwe hulpprogramma's wordt compatibiliteit met eerdere versies voor de codebasis van oude visuals opgeslagen, maar er kunnen wel aanvullende wijzigingen vereist zijn voor het laden van externe bibliotheken.

De bibliotheken, die modulesystemen ondersteunen, worden geïmporteerd als Webpack-modules. Alle andere bibliotheken en broncode van de visual worden verpakt in één module.

Globale variabelen, zoals JQuery en Lodash die in de vorige pbiviz-hulpprogramma's werden gebruikt, zijn nu verouderd. Dit betekent dat de visual wordt verbroken als de oude code van de visual afhankelijk was van globale variabelen.

In de vorige versie van Power BI Visuals Tools was het noodzakelijk om een visualklasse te definiëren onder de module `powerbi.extensibility.visual`.

## <a name="how-to-install-powerbi-visuals-tools"></a>powerbi-visuals-tools installeren

De nieuwe toolset kan worden geïnstalleerd met de opdracht

```cmd
npm install -g powerbi-visuals-tools
```

Het voorbeeld van de visual sampleBarChart en de bijbehorende [wijzigingen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) in `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Power BI-API voor aangepaste visuals installeren

De nieuwe versie van powerbi-visual-tools bevat niet alle API-versies. In plaats daarvan moet de ontwikkelaar een specifieke versie van het pakket [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api) installeren. De versie van het pakket komt overeen met de API-versie van Power BI Custom Visuals en bevat alle typedefinities voor de Power BI-API voor aangepaste visuals.

Voeg `powerbi-visuals-api` toe aan de afhankelijkheden van een project door de opdracht `npm install --save-dev powerbi-visuals-api` uit te voeren.
Verwijder ook de koppeling naar de typedefinities van de oude API. Typen van `powerbi-visuals-api` worden immers automatisch toegevoegd via Webpack. De bijbehorende wijzigingen bevinden zich in [deze](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) regel van `package.json`.

## <a name="update-tsconfigjson"></a>`tsconfig.json` bijwerken

Als u externe modules wilt gebruiken, moet u de optie `out` wijzigen in `outDir`.
Gebruik `"outDir": "./.tmp/build/",` in plaats van `"out": "./.tmp/build/visual.js",`.

Dit is vereist omdat TypeScript-bestanden onafhankelijk van elkaar worden gecompileerd naar JavaScript-bestanden. Daarom hoeft u visual.js niet meer op te geven als uitvoerbestand.

U kunt ook de optie `target` wijzigen in `ES6` als u een modern JavaScript-uitvoerbestand wilt gebruiken. [Dit is niet verplicht](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Hulpprogramma's voor aangepaste visuals bijwerken

Als u gebruikmaakt van een van deze hulpprogramma's voor Power BI-visuals(https://www.npmjs.com/search?q=powerbi-visuals-utils), moet u ze ook bijwerken naar de nieuwste versie.

Voer de opdracht `npm install powerbi-visuals-utils-<UTILNAME> --save` uit. (Bijvoorbeeld: `npm install powerbi-visuals-utils-dataviewutils --save` om de nieuwe versie met externe modules van TypeScript op te halen.)

U vindt een voorbeeld in het Mekko-diagram in deze [opslagplaats](https://github.com/Microsoft/powerbi-visuals-mekkochart).
Deze visual maakt gebruik van alle hulpprogramma's.

## <a name="remove-globalizejs-library"></a>De bibliotheek Globalize.js verwijderen

In de nieuwe versie van [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) is globalize.js al kant-en-klaar opgenomen.
U hoeft deze bibliotheek niet handmatig aan het project toe te voegen.
Alle vereiste lokalisaties worden automatisch toegevoegd aan het uiteindelijke pakket.

## <a name="fix-loading-external-libraries"></a>Laden van externe bibliotheken wijzigen

Voeg in plaats daarvan een nieuw JS-bestand toe na bibliotheken in de `externalJS`-matrix van `pbiviz.json`. Voorbeeld:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importeer de bibliotheken in de bron. Voorbeeld voor `lodash-es`:

```JS
import * as _ from "lodash-es";
```

hierbij is `_` de globale variabele voor de bibliotheek `lodash`.

## <a name="changes-in-the-visuals-sources"></a>Wijzigingen in de visuals-bronnen

De belangrijkste wijziging is het omzetten van interne modules naar externe modules, omdat u geen externe modules kunt gebruiken binnen interne modules.

In deze wijzigingen worden de wijzigingen beschreven die zijn toegepast op het voorbeeldstaafdiagram

Gedetailleerde beschrijvingen van de wijzigingen vindt u hieronder:

1. Alle moduledefinities verwijderen uit elk bestand met [broncode](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importeer definities voor Power BI-API voor aangepaste visuals](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importeer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) benodigde interfaces of klassen uit de interne module `powerbi`.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importeer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) de bibliotheek D3.js

    ```typescript
    import * as d3 from "d3";
    ```

    Of importeer alleen vereiste d3-bibliotheekmodules

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importeer](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) hulpprogramma's, klassen, interfaces die zijn gedefinieerd in het visualproject naar het hoofdbronbestand

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>CSS-stijlen importeren

Met de nieuwe versie kunnen ontwikkelaars CSS- en LESS-stijlen rechtstreeks importeren in de TypeScript-code.

De eerder gebruikte [sectie met stijlen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) wordt door een compiler genegeerd.

Als u uw opmaakmodel wilt gebruiken, opent u het hoofd-ts-bestand en voegt u er de volgende regel aan toe:  

```typescript
import "./../style/visual.less";
```  

Uw CSS- en LESS-stijlen worden automatisch gecompileerd.  

### <a name="externaljs-section-in-pbivizjson"></a>sectie externalJS in pbiviz. json

Voor de hulpprogramma's hoeft er [geen](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) lijst met `externalJS` te worden geladen in de visualbundel. Omdat Webpack alle geïmporteerde bibliotheken bevat.

**De sectie externalJS in pbivi.json moet leeg zijn.**

Roep de gebruikelijke opdracht `npm run package` aan om het visualpakket te maken of `npm run start` om de Dev-server te starten.

## <a name="updating-d3js-library-to-version-5"></a>De bibliotheek D3.js bijwerken naar versie 5

Met nieuwe hulpprogramma's kunt u de nieuwe versie van de bibliotheek D3.js gebruiken.

Opdrachten aanroepen om D3 bij te werken in uw visualproject

`npm install --save d3@5` om de nieuwe bibliotheek D3.js te installeren.

`npm install --save-dev @types/d3@5` om de nieuwe typedefinities voor D3.js te installeren.

Er zijn verschillende wijzigingen die fouten veroorzaken en u moet uw code zo aanpassen dat de nieuwe D3.js wordt gebruikt.

1. De interface `d3.Selection<T>` [is gewijzigd](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. U kunt niet meerdere kenmerken toepassen met één aanroep van de methode `attr`. U [moet elk kenmerk doorgeven](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) in een afzonderlijke aanroep van de methode `attr`. Iets [vergelijkbaars](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) geldt voor de methode `style`.

3. In D3.js v4 is de nieuwe samenvoegingsmethode geïntroduceerd. Deze methode wordt vaak gebruikt voor het samenvoegen, invoeren en bijwerken van selecties na een data-join. [Roep de samenvoegmethode aan](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) om d3 correct te gebruiken.

[Lees meer](https://github.com/d3/d3/blob/master/CHANGES.md) over wijzigingen in de bibliotheek D3.js.

## <a name="babel"></a>Babel

Vanaf versie 3.1 maken de hulpprogramma's gebruik van Babel om nieuwe moderne JS-code naar oude ES5-code te compileren ter ondersteuning van allerlei browsers.

Deze optie is standaard ingeschakeld, maar u moet het pakket [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) handmatig importeren.

Voer de installatieopdracht voor het pakket uit

`npm install --save @babel/polyfill`

en importeer het pakket op het startpunt van de visualcode (meestal is dit het bestand src/visual.ts):

`import "@babel/polyfill";`

Lees meer over Babel [in de documentatie](https://babeljs.io/docs/en/).

Voer tenslotte [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) uit om de codebasis van de visual weer te geven.  

![Statistieken van de code van de visual](./media/webpack-stats.png)
