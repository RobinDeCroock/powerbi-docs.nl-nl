---
title: Inleiding tot eenheidstest
description: Eenheidstests schrijven voor Power BI Visuals-project
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 4b16eaad9b541bf6e5d8df49ffda99d9bbd5bbf2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424534"
---
# <a name="tutorial-add-unit-tests-for-power-bi-visual-projects"></a>Zelfstudie: eenheidstests voor Power BI Visual-projecten toevoegen

In deze zelfstudie worden de basisbeginselen van het schrijven van tests voor uw Power BI-visuals beschreven.

In deze zelfstudie wordt behandeld

* testrunner karma.js gebruiken, test-framework - jasmine.js
* pakket powerbi-visuals-utils-testutils gebruiken
* hoe een set prototypen en nabootsingen helpen eenheidstests voor Power BI-visuals te vereenvoudigen.

## <a name="prerequisites"></a>Vereisten

* U hebt een Power BI-visuals-project
* Geconfigureerde Node.JS-omgeving

## <a name="install-and-configure-karmajs-and-jasmine"></a>karma.js en jasmine installeren en configureren

Vereiste bibliotheken toevoegen aan package.json in sectie `devDependencies`:

```json
"@babel/polyfill": "^7.2.5",
"@types/d3": "5.5.0",
"@types/jasmine": "2.5.37",
"@types/jasmine-jquery": "1.5.28",
"@types/jquery": "2.0.41",
"@types/karma": "3.0.0",
"@types/lodash-es": "4.17.1",
"coveralls": "3.0.2",
"istanbul-instrumenter-loader": "^3.0.1",
"jasmine": "2.5.2",
"jasmine-core": "2.5.2",
"jasmine-jquery": "2.1.1",
"jquery": "3.1.1",
"karma": "3.1.1",
"karma-chrome-launcher": "2.2.0",
"karma-coverage": "1.1.2",
"karma-coverage-istanbul-reporter": "^2.0.4",
"karma-jasmine": "2.0.1",
"karma-junit-reporter": "^1.2.0",
"karma-sourcemap-loader": "^0.3.7",
"karma-typescript": "^3.0.13",
"karma-typescript-preprocessor": "0.4.0",
"karma-webpack": "3.0.5",
"puppeteer": "1.17.0",
"style-loader": "0.23.1",
"ts-loader": "5.3.0",
"ts-node": "7.0.1",
"tslint": "^5.12.0",
"webpack": "4.26.0"
```

Zie de beschrijving hieronder voor meer informatie over het pakket.

Sla `package.json` op en voer het uit op de opdrachtregel op de locatie van `package.json`:

```cmd
npm install
```

De pakketmanager installeert alle nieuwe pakketten die zijn toegevoegd aan `package.json`

Voor het uitvoeren van eenheidstests moet u de testrunner en `webpack`-configuratie configureren. Het voorbeeld van de configuratie kunt u hier vinden

Voorbeeld van `test.webpack.config.js`:

```typescript
const path = require('path');
const webpack = require("webpack");

module.exports = {
    devtool: 'source-map',
    mode: 'development',
    optimization : {
        concatenateModules: false,
        minimize: false
    },
    module: {
        rules: [
            {
                test: /\.tsx?$/,
                use: 'ts-loader',
                exclude: /node_modules/
            },
            {
                test: /\.json$/,
                loader: 'json-loader'
            },
            {
                test: /\.tsx?$/i,
                enforce: 'post',
                include: /(src)/,
                exclude: /(node_modules|resources\/js\/vendor)/,
                loader: 'istanbul-instrumenter-loader',
                options: { esModules: true }
            },
            {
                test: /\.less$/,
                use: [
                    {
                        loader: 'style-loader'
                    },
                    {
                        loader: 'css-loader'
                    },
                    {
                        loader: 'less-loader',
                        options: {
                            paths: [path.resolve(__dirname, 'node_modules')]
                        }
                    }
                ]
            }
        ]
    },
    externals: {
        "powerbi-visuals-api": '{}'
    },
    resolve: {
        extensions: ['.tsx', '.ts', '.js', '.css']
    },
    output: {
        path: path.resolve(__dirname, ".tmp/test")
    },
    plugins: [
        new webpack.ProvidePlugin({
            'powerbi-visuals-api': null
        })
    ]
};
```

Voorbeeld van `karma.conf.ts`

```typescript
"use strict";

const webpackConfig = require("./test.webpack.config.js");
const tsconfig = require("./test.tsconfig.json");
const path = require("path");

const testRecursivePath = "test/visualTest.ts";
const srcOriginalRecursivePath = "src/**/*.ts";
const coverageFolder = "coverage";

process.env.CHROME_BIN = require("puppeteer").executablePath();

import { Config, ConfigOptions } from "karma";

module.exports = (config: Config) => {
    config.set(<ConfigOptions>{
        mode: "development",
        browserNoActivityTimeout: 100000,
        browsers: ["ChromeHeadless"], // or Chrome to use locally installed Chrome browser
        colors: true,
        frameworks: ["jasmine"],
        reporters: [
            "progress",
            "junit",
            "coverage-istanbul"
        ],
        junitReporter: {
            outputDir: path.join(__dirname, coverageFolder),
            outputFile: "TESTS-report.xml",
            useBrowserName: false
        },
        singleRun: true,
        plugins: [
            "karma-coverage",
            "karma-typescript",
            "karma-webpack",
            "karma-jasmine",
            "karma-sourcemap-loader",
            "karma-chrome-launcher",
            "karma-junit-reporter",
            "karma-coverage-istanbul-reporter"
        ],
        files: [
            "node_modules/jquery/dist/jquery.min.js",
            "node_modules/jasmine-jquery/lib/jasmine-jquery.js",
            {
                pattern: './capabilities.json',
                watched: false,
                served: true,
                included: false
            },
            testRecursivePath,
            {
                pattern: srcOriginalRecursivePath,
                included: false,
                served: true
            }
        ],
        preprocessors: {
            [testRecursivePath]: ["webpack", "coverage"]
        },
        typescriptPreprocessor: {
            options: tsconfig.compilerOptions
        },
        coverageIstanbulReporter: {
            reports: ["html", "lcovonly", "text-summary", "cobertura"],
            dir: path.join(__dirname, coverageFolder),
            'report-config': {
                html: {
                    subdir: 'html-report'
                }
            },
            combineBrowserReports: true,
            fixWebpackSourcePaths: true,
            verbose: false
        },
        coverageReporter: {
            dir: path.join(__dirname, coverageFolder),
            reporters: [
                // reporters not supporting the `file` property
                { type: 'html', subdir: 'html-report' },
                { type: 'lcov', subdir: 'lcov' },
                // reporters supporting the `file` property, use `subdir` to directly
                // output them in the `dir` directory
                { type: 'cobertura', subdir: '.', file: 'cobertura-coverage.xml' },
                { type: 'lcovonly', subdir: '.', file: 'report-lcovonly.txt' },
                { type: 'text-summary', subdir: '.', file: 'text-summary.txt' },
            ]
        },
        mime: {
            "text/x-typescript": ["ts", "tsx"]
        },
        webpack: webpackConfig,
        webpackMiddleware: {
            stats: "errors-only"
        }
    });
};
```

U kunt deze configuratie wijzigen als dat nodig is.

Enkele instellingen van `karma.conf.js`:

* De variabele `recursivePathToTests` bepaalt de plaats van de code van tests.

* De variabele `srcRecursivePath` bepaalt de plaats van de uitgevoerde JS-code na compilatie.

* De variabele `srcCssRecursivePath` bepaalt de plaats van de uitgevoerde CSS na het compileren van het LESS-bestand met stijlen.

* De variabele `srcOriginalRecursivePath` bepaalt de plaats van de broncode van uw visual.

* De variabele `coverageFolder` bepaalt een plaats waar het rapport van de dekking wordt gemaakt.

Enkele eigenschappen van de configuratie:

* `singleRun: true` -tests worden uitgevoerd op het CI-systeem. En het is voldoende om één keer uit te voeren.
U kunt dit instellen op `false` voor het opsporen van fouten in uw tests. Karma blijft de browser uitvoeren, en u kunt de console gebruiken voor het opsporen van fouten.

* `files: [...]` - in deze matrix kunt u bestanden zetten om te laden in de browser.
Normaal gesp roken zijn er bronbestanden, testcases, bibliotheken (Jasmine, testprogramma's). U kunt indien nodig andere bestanden toevoegen aan de lijst.

* `preprocessors` -in deze sectie van de configuratie configureert u acties die worden uitgevoerd voor de uitvoering van de eenheidstests. Er is een precompilatie van TypeScript naar JS, het voorbereiden van brontoewijzingsbestanden en het genereren van een codedekkingsrapport. U kunt `coverage` uitschakelen voor het opsporen van fouten in uw tests. Dekking genereert extra code voor het controleren van code voor de testdekking, en het compliceert foutopsporingstests.

**Beschrijving van alle configuraties die u kunt vinden in [de ](https://karma-runner.github.io/1.0/config/configuration-file.html)documentatie van karma.js**

Voor gemakkelijk gebruik kunt u testopdrachten toevoegen in `scripts`:

```json
{
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "typings":"node node_modules/typings/dist/bin.js i",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "pretest": "pbiviz package --resources --no-minify --no-pbiviz --no-plugin",
        "test": "karma start"
    }
    ...
}
```

Nu bent u klaar om te beginnen met het schrijven van uw eenheidstests.

## <a name="simple-unit-test-for-check-dom-element-of-the-visual"></a>Eenvoudige eenheidstest voor controle van het DOM-element van de visual

Voor het testen van de visual moet u een instantie maken van de visual.

### <a name="creating-visual-instance-builder"></a>Instancebuilder voor visuals maken

Voeg het bestand `visualBuilder.ts` toe aan de map `test` met de volgende code:

```typescript
import {
    VisualBuilderBase
} from "powerbi-visuals-utils-testutils";

import {
    BarChart as VisualClass
} from "../src/visual";

import  powerbi from "powerbi-visuals-api";
import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions;

export class BarChartBuilder extends VisualBuilderBase<VisualClass> {
    constructor(width: number, height: number) {
        super(width, height);
    }

    protected build(options: VisualConstructorOptions) {
        return new VisualClass(options);
    }

    public get mainElement() {
        return this.element.children("svg.barChart");
    }
}
```

Er is een `build`-methode voor het maken van een instantie van uw visual. `mainElement` is een get-methode, waarmee een instantie van het DOM-element 'root' in uw visual wordt geretourneerd. De getter is optioneel, maar maakt het schrijven van de eenheidstest eenvoudiger.

Nu hebben we dus de builder van een instantie van de visual. We gaan de testcase schrijven. Het is een testcase voor het controleren van de SVG-elementen die worden gemaakt bij het weergeven van uw visual.

### <a name="creating-typescript-file-to-write-test-cases"></a>TypeScript-bestand maken om testcases te schrijven

Voeg het bestand `visualTest.ts` voor testcases toe met deze code:

```typescript
import powerbi from "powerbi-visuals-api";

import { BarChartBuilder } from "./VisualBuilder";

import {
    BarChart as VisualClass
} from "../src/visual";

import VisualBuilder = powerbi.extensibility.visual.test.BarChartBuilder;

describe("BarChart", () => {
    let visualBuilder: VisualBuilder;
    let dataView: DataView;

    beforeEach(() => {
        visualBuilder = new VisualBuilder(500, 500);
    });

    it("root DOM element is created", () => {
        expect(visualBuilder.mainElement).toBeInDOM();
    });
});
```

Er worden verschillende methoden aangeroepen.

* De methode [`describe`](https://jasmine.github.io/api/2.6/global.html#describe) beschrijft testcases. In de context van Jasmine Framework wordt dit vaak suite of groep met specificaties genoemd.

* De methode `beforeEach` wordt aangeroepen voor elke aanroep van de methode `it`, die wordt gedefinieerd binnen de [`describe`](https://jasmine.github.io/api/2.6/global.html#beforeEach)-methode.

* `it` definieert één specificatie. De [`it`](https://jasmine.github.io/api/2.6/global.html#it) -methode moet een of meer `expectations` bevatten.

* De methode [`expect`](https://jasmine.github.io/api/2.6/global.html#expect)creëert de verwachting voor een specificatie. Een specificatie slaagt als aan alle verwachtingen zonder fouten wordt voldaan.

* `toBeInDOM` is een van de matchers-methoden. Over exists-matchers kunt u lezen in de [documentatie](https://jasmine.github.io/api/2.6/matchers.html) van Jasmine Framework.

**Meer informatie over Jasmine Framework vindt u in de officiële [documentatie](https://jasmine.github.io/).**

Daarna kunt u de eenheidstest uitvoeren door een opdracht in te voeren in het opdrachtregelprogramma.

Deze test controleert of het root-SVG-element van de visuals wordt gemaakt.

### <a name="launch-unit-tests"></a>Eenheidstests starten

U kunt de eenheidstest uitvoeren door deze opdracht te typen in het opdrachtregelprogramma.

```cmd
npm run test
```

`karma.js` voert de Chrome-browser uit en voert de testcase uit.

![KarmaJS gestart in Chrome](./media/karmajs-chrome.png)

> [!NOTE]
> Google Chrome moet lokaal worden geïnstalleerd.

Op de opdrachtregel krijgt u de volgende uitvoer:

```cmd
> karma start

23 05 2017 12:24:26.842:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 12:24:30.836:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 12:24:30.849:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 12:24:30.850:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 12:24:31.059:INFO [launcher]: Starting browser Chrome
23 05 2017 12:24:33.160:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#2meR6hjXFmsE_fjiAAAA with id 5875251
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (0.194 secs / 0.011 secs)

=============================== Coverage summary ===============================
Statements   : 27.43% ( 65/237 )
Branches     : 19.84% ( 25/126 )
Functions    : 43.86% ( 25/57 )
Lines        : 20.85% ( 44/211 )
================================================================================
```

### <a name="how-to-add-static-data-for-unit-tests"></a>Statische gegevens voor eenheidstests toevoegen

Maak het bestand `visualData.ts` in de map `test`. Met deze code:

```typescript
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;

import {
    testDataViewBuilder,
    getRandomNumbers
} from "powerbi-visuals-utils-testutils";

export class SampleBarChartDataBuilder extends TestDataViewBuilder {
    public static CategoryColumn: string = "category";
    public static MeasureColumn: string = "measure";

    public constructor() {
        super();
        ...
    }

    public getDataView(columnNames?: string[]): DataView {
        let dateView: any = this.createCategoricalDataViewBuilder([
            ...
        ],
        [
            ...
        ], columnNames).build();

        // there's client side computed maxValue
        let maxLocal = 0;
        this.valuesMeasure.forEach((item) => {
                if (item > maxLocal) {
                    maxLocal = item;
                }
        });
        (<any>dataView).categorical.values[0].maxLocal = maxLocal;
    }
}
```

De `SampleBarChartDataBuilder`-klasse breidt `TestDataViewBuilder` uit en implementeert de abstracte methode `getDataView`.

Wanneer u gegevens in gegevensveldbuckets plaatst, produceert Power BI een categorisch `dataview`-object op basis van uw gegevens.

![Gevulde buckets](./media/fields-buckets.png)

In eenheidstests hebt u geen Power BI-kernfuncties om deze te reproduceren. Maar u moet uw statische gegevens toewijzen aan categorische `dataview`. En de klasse `TestDataViewBuilder` helpt u hier.

[Meer informatie over DataViewMapping](https://github.com/Microsoft/PowerBI-visuals/blob/master/Capabilities/DataViewMappings.md)

In de methode `getDataView` roept u gewoon de methode `createCategoricalDataViewBuilder` aan met uw gegevens.

In [capabilities.json](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/capabilities.json#L2) van de visual `sampleBarChart`, hebben we dataRoles- en dataViewMapping-objecten:

```json
"dataRoles": [
    {
        "displayName": "Category Data",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measure Data",
        "name": "measure",
        "kind": "Measure"
    }
],
"dataViewMappings": [
    {
        "conditions": [
            {
                "category": {
                    "max": 1
                },
                "measure": {
                    "max": 1
                }
            }
        ],
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "select": [
                    {
                        "bind": {
                            "to": "measure"
                        }
                    }
                ]
            }
        }
    }
],
```

Als u dezelfde toewijzing wilt genereren, moet u de volgende parameters instellen in de `createCategoricalDataViewBuilder`-methode:

```typescript
([
    {
        source: {
            displayName: "Category",
            queryName: SampleBarChartData.ColumnCategory,
            type: ValueType.fromDescriptor({ text: true }),
            roles: {
                Category: true
            },
        },
        values: this.valuesCategory
    }
],
[
    {
        source: {
            displayName: "Measure",
            isMeasure: true,
            queryName: SampleBarChartData.MeasureColumn,
            type: ValueType.fromDescriptor({ numeric: true }),
            roles: {
                Measure: true
            },
        },
        values: this.valuesMeasure
    },
], columnNames)
```

Waarbij `this.valuesCategory` de matrix met categorieën is,

```ts
public valuesCategory: string[] = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"];
```

en `this.valuesMeasure` de metingenmatrix voor elke categorie. Voorbeeld:

```ts
public valuesMeasure: number[] = [742731.43, 162066.43, 283085.78, 300263.49, 376074.57, 814724.34, 570921.34];
```

Nu kunt u de klasse `SampleBarChartDataBuilder` in uw eenheidstest gebruiken.

Klasse `ValueType` gedefinieerd in het pakket `powerbi-visuals-utils-testutils`. En de methode `createCategoricalDataViewBuilder` vereist een `lodash`-bibliotheek.

Voeg deze pakketten toe aan afhankelijkheden.

In `package.json` in de sectie `devDependencies`

```json
"lodash-es": "4.17.1",
"powerbi-visuals-utils-testutils": "2.2.0"
```

Roept u

```cmd
npm install
```

aan om de `lodash-es`-bibliotheek te installeren.

Nu kunt u de eenheidstest opnieuw uitvoeren. U moet deze uitvoer krijgen

```cmd
> karma start

23 05 2017 16:19:54.318:WARN [watcher]: Pattern "E:/WORKSPACE/PowerBI/PowerBI-visuals-sampleBarChart/data/*.csv" does not match any file.
23 05 2017 16:19:58.333:WARN [karma]: No captured browser, open http://localhost:9876/
23 05 2017 16:19:58.346:INFO [karma]: Karma v1.3.0 server started at http://localhost:9876/
23 05 2017 16:19:58.346:INFO [launcher]: Launching browser Chrome with unlimited concurrency
23 05 2017 16:19:58.394:INFO [launcher]: Starting browser Chrome
23 05 2017 16:19:59.873:INFO [Chrome 58.0.3029 (Windows 10 0.0.0)]: Connected on socket /#NcNTAGH9hWfGMCuEAAAA with id 3551106
Chrome 58.0.3029 (Windows 10 0.0.0): Executed 1 of 1 SUCCESS (1.266 secs / 1.052 secs)

=============================== Coverage summary ===============================
Statements   : 56.72% ( 135/238 )
Branches     : 32.54% ( 41/126 )
Functions    : 66.67% ( 38/57 )
Lines        : 52.83% ( 112/212 )
================================================================================
```

En u moet de gestarte Chrome-browser met uw visual zien.

![UT wordt gestart in Chrome](./media/karmajs-chrome-ut-runned.png)

U ziet in de samenvatting dat de dekking is toegenomen. Open `coverage\index.html` voor meer informatie over de huidige codedekking

![UT-dekkingsindex](./media/code-coverage-index.png)

Of in het bereik van de map `src`

![Dekking van src-map](./media/code-coverage-src-folder.png)

In het bereik van het bestand kunt u de broncode bekijken. `Coverage`-hulpprogramma's markeert de achtergrond van regels met rood als er code niet is uitgevoerd tijdens het uitvoeren van eenheidstests.

![Codedekking van het bestand visual.ts](./media/code-coverage-visual-src.png)

> [!IMPORTANT]
> Maar codedekking betekent niet dat u een goede functionaliteitsdekking van de visual hebt. Eén eenvoudige eenheidstest zorgde voor meer dan 96% dekking in `src\visual.ts`.

## <a name="next-steps"></a>Volgende stappen

Wanneer uw visual klaar is, kunt u uw visual verzenden voor publicatie.

[Meer informatie over het publiceren van visuals naar AppSource](../office-store.md)
