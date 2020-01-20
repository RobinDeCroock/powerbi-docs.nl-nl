---
title: Migratie naar powerbi-visuals-tools versie 3.x
description: Aan de slag met de nieuwe versie van powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 1b819aeb0f59df9ee0d48d7c41807abe62efed08
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885130"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migreren naar de nieuwe powerbi-visuals-tools versie 3.*x*

Vanaf versie 3 maakt Power BI Visuals Tools (powerbi-visuals-tools, of `pbiviz`) gebruik van Webpack voor het bouwen van aangepaste visuals.
De nieuwe versie biedt ontwikkelaars een groot aantal verbeteringen voor het maken van visuals:

- Standaard wordt TypeScript-versie 3.*x* gebruikt. Vanaf TypeScript 1.5 is de naamgeving gewijzigd. [Meer informatie over TypeScript-modules](https://www.typescriptlang.org/docs/handbook/modules.html).

- ES6-modules (ECMAScript 6) worden ondersteund. Gebruik nu ES6-importbewerkingen in plaats van [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Nieuwe versies van Data-Driven Documents ([D3v5](https://d3js.org/)) en andere op ES6 modules gebaseerde bibliotheken worden ondersteund.

- Gereduceerde pakketgrootte. Webpack maakt gebruik van [tree shaking](https://webpack.js.org/guides/tree-shaking/) om ongebruikte code te verwijderen. Hiermee wordt de JavaScript-code verminderd en krijgt u betere prestaties bij het laden van visuals.

- Verbeterde API-prestaties.

- De bibliotheek Globalize.js [is geïntegreerd](migrate-to-new-tools.md#remove-the- globalizejs-library) in FormattingUtils.

- Power BI Visual Tools maken gebruik van [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) om de codebasis van de visual weer te geven.

In dit artikel worden alle migratiestappen voor de nieuwe versie van Power BI Visuals Tools beschreven.

## <a name="backward-compatibility"></a>Compatibiliteit met eerdere versies

In de nieuwe hulpprogramma's wordt informatie over compatibiliteit met eerdere versies voor de codebasis van oude visuals opgeslagen, maar er kunnen wel aanvullende wijzigingen vereist zijn voor het laden van externe bibliotheken.

De bibliotheken die modulesystemen ondersteunen, worden geïmporteerd als Webpack-modules. Alle andere bibliotheken en broncode voor de visual worden in één module verpakt.

Globale variabelen zoals JQuery en Lodash, die in de vorige Power BI Visuals Tools werden gebruikt, zijn nu verouderd. Als de oude code voor uw visual afhankelijk is van algemene variabelen, werkt de visual waarschijnlijk niet met de nieuwe hulpprogramma's.

In de vorige versie van Power BI Visuals Tools was het noodzakelijk om een visualklasse te definiëren onder de module `powerbi.extensibility.visual`. Met de nieuwe versie van de hulpprogramma's moet u in plaats daarvan een visualklasse definiëren in het belangrijkste TypeScript-bestand (.ts). Normaal gesproken is dat bestand `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>powerbi-visuals-tools installeren

Voer deze opdracht uit om de nieuwe hulpprogramma's te installeren:

```cmd
npm install -g powerbi-visuals-tools
```

De volgende code is afkomstig uit het bestand `package.json` in de [opslagplaats met sampleBarChart-visuals](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15) nadat het visualproject is bijgewerkt om te werken met de nieuwe hulpprogramma's:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>De Power BI-API voor aangepaste visuals installeren

De nieuwe versie van powerbi-visual-tools bevat niet alle API-versies. In plaats daarvan moet u een specifieke versie van het pakket [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api) installeren. Kies de versie van het pakket die overeenkomt met de API-versie van uw aangepaste Power BI-visuals. Het pakket bevat alle typedefinities voor de API van de aangepaste Power BI-visuals.

Voer de volgende opdracht uit om `powerbi-visuals-api` toe te voegen aan de projectafhankelijkheden van een project:

```cmd
npm install --save-dev powerbi-visuals-api
```

Verwijder ook eventuele koppelingen naar oude API-typedefinities, omdat Webpack automatisch typen uit `powerbi-visuals-api` bevat. De bijbehorende wijzigingen staan in [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) en [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>tsconfig.json bijwerken

Als u externe modules wilt gebruiken, wijzigt u de optie `out` in `outDir`. U kunt bijvoorbeeld `"outDir": "./.tmp/build/",` weergeven in plaats van `"out": "./.tmp/build/visual.js",`.

Deze wijziging is vereist omdat TypeScript-bestanden onafhankelijk van elkaar worden gecompileerd naar JavaScript-bestanden. Daarom hoeft u het bestand visual.js niet meer op te geven als uitvoerbestand.

U kunt ook de optie `target` wijzigen in `ES6` als u een modern JavaScript-uitvoerbestand wilt gebruiken. Deze wijziging is [optioneel](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Hulpprogramma's voor aangepaste visuals bijwerken

Als u gebruikmaakt van een van de [powerbi-visuals-tools](https://www.npmjs.com/search?q=powerbi-visuals-utils)-pakketten, moet u ze ook bijwerken naar de nieuwste versie. Voer hiervoor de volgende opdracht uit:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Voer bijvoorbeeld het volgende uit om de nieuwe versie met externe modules van TypeScript op te halen: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Zie [MekkoChart-opslagplaats](https://github.com/Microsoft/powerbi-visuals-mekkochart) voor een voorbeeld van een visual waarbij gebruik wordt gemaakt van alle `powerbi-visuals-utils`-pakketten.

## <a name="remove-the-globalizejs-library"></a>De bibliotheek Globalize.js verwijderen

In de nieuwe versie van [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) is Globalize.js al opgenomen. U hoeft deze bibliotheek dus niet handmatig aan het project toe te voegen. Alle vereiste lokalisaties worden automatisch toegevoegd aan het uiteindelijke pakket.

## <a name="configure-loading-of-external-libraries"></a>Het laden van externe bibliotheken configureren

Voeg nieuwe JavaScript-bestanden toe na bibliotheken in de `externalJS`-matrix van `pbiviz.json`. Bijvoorbeeld:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importeer de bibliotheken in de broncode. Gebruik bijvoorbeeld voor `lodash-es` de volgende instructie:

```JS
import * as _ from "lodash-es";
```

In het vorige voorbeeld is `_` de algemene variabele voor de `lodash`-bibliotheek.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Wijzigingen aanbrengen in de bronnen van uw visuals

De belangrijkste wijziging die u moet aanbrengen, is het omzetten van interne modules naar externe modules. U kunt geen externe modules in interne modules gebruiken.

Hier volgt een gedetailleerde beschrijving van de wijzigingen die u moet aanbrengen. De wijzigingen worden beschreven in de context van het voorbeeld van aangepaste visuele code in een staafdiagram:

1. Verwijder alle moduledefinities uit elk bestand met [broncode](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importeer definities voor de Power BI-API voor aangepaste visuals](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importeer de benodigde interfaces of klassen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) uit de interne module `powerbi`.

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

4. [Importeer de bibliotheek D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Of importeer alleen de vereiste D3-bibliotheekmodules:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importeerhulpprogramma's, klassen en interfaces die zijn gedefinieerd in het visualproject](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) van het hoofdbronbestand:

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

Met de nieuwe versie van de hulpprogramma's kunt u `CSS`- en `Less`-stijlen rechtstreeks importeren in de TypeScript-code. De [sectie Stijlen](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) die eerder is gebruikt, wordt nu door de compiler genegeerd.

Als u uw opmaakmodel wilt gebruiken, opent u het hoofd-TypeScript-bestand (.ts) en voegt u er de volgende regel aan toe:  

```typescript
import "./../style/visual.less";
```  

Uw `CSS`- en `Less`-stijlen worden automatisch gecompileerd.

### <a name="externaljs-section-in-pbivizjson"></a>sectie externalJS in pbiviz. json

Voor de hulpprogramma's [hoeft geen lijst met `externalJS`-bibliotheken](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) in de bundel met visuals te worden geladen, omdat Webpack alle geïmporteerde bibliotheken bevat.

> [!NOTE]
> Laat in `pbiviz.json` de sectie `externalJS` leeg.

Roep de gebruikelijke opdracht `npm run package` aan om het visualpakket te maken of `npm run start` om de ontwikkelingsserver te starten.

## <a name="update-the-d3js-library-to-version-5"></a>De bibliotheek D3.js bijwerken naar versie 5

Met de nieuwe hulpprogramma's voor visuals kunt u de nieuwe versie van de bibliotheek D3.js gebruiken. Voer deze opdrachten uit om D3 bij te werken in uw visualproject:

- `npm install --save d3@5` om de nieuwe bibliotheek D3.js te installeren.

- `npm install --save-dev @types/d3@5` om de nieuwe typedefinities voor D3.js te installeren.

> [!IMPORTANT]
> In D3-versie 5 worden diverse belangrijke wijzigingen geïntroduceerd.

Wijzig uw code zodat deze werkt met de nieuwe D3.js:

- De interface `d3.Selection<T>` [is gewijzigd](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) in `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- U kunt niet meerdere kenmerken toepassen met één aanroep naar de methode `attr`. In plaats daarvan moet u [elk kenmerk in een afzonderlijke aanroep doorgeven](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) aan `attr`. Maak ook [afzonderlijke aanroepen naar de `style`-methode](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- In D3.js versie 4 is de nieuwe `merge`-methode geïntroduceerd. Deze methode wordt vaak gebruikt voor het samenvoegen van `enter`- en `update`-selecties na een bewerking voor het samenvoegen van gegevens. Als u D3 op de juiste wijze wilt gebruiken, [roept u de `merge`-methode aan](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Lees meer](https://github.com/d3/d3/blob/master/CHANGES.md) over wijzigingen in de bibliotheek D3.js.

## <a name="install-babel-and-core-js"></a>Babel en core-js installeren

Vanaf versie 3.1 maken de hulpprogramma's voor visuals gebruik van Babel om moderne JavaScript-code naar oude ES5-code (ECMAScript 5) te compileren ter ondersteuning van allerlei browsers.

De Babel-optie is standaard ingeschakeld, maar u moet het pakket [`core-js`](https://www.npmjs.com/package/core-js) handmatig importeren. Voer deze opdracht uit om het pakket te installeren:

```cmd
npm install --save core-js
```

Importeer het pakket vervolgens aan het beginpunt van de visualcode. Doorgaans is dit het bestand src/visual.ts.

```JS
import "core-js/stable";
```

Lees meer over Babel [in de documentatie](https://babeljs.io/docs/en/).
