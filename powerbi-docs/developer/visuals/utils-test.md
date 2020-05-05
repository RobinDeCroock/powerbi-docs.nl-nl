---
title: Inleiding tot het gebruik van testhulpmiddelen in een Power BI-visual
description: In dit artikel wordt beschreven hoe u met testhulpmiddelen dummy's en het gebruik van specifieke methoden in eenheidstests voor Power BI-visuals kunt vereenvoudigen
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196601"
---
# <a name="power-bi-visuals-test-utils"></a>Testhulpmiddelen Power BI-visuals

Dit artikel helpt u bij het installeren, importeren en gebruiken van testhulpmiddelen voor Power BI-visuals. Deze testhulpprogramma's kunnen worden gebruikt voor eenheidstests en bevatten dummy's en methoden voor elementen, zoals gegevensweergaven, selecties en kleurenschema's.

## <a name="requirements"></a>Vereisten

Als u dit pakket wilt gebruiken, moet u het volgende installeren:

* [node.js](https://nodejs.org) (het is raadzaam om de LTS-versie te gebruiken)
* [npm](https://www.npmjs.com/), versie 3.0.0 of hoger
* Het [PowerBi-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools)-pakket

## <a name="installation"></a>Installatie

Voer de volgende opdracht uit in de map van uw Power BI-visuals om testhulpmiddelen te installeren en de afhankelijkheid ervan toe te voegen aan uw *package.json*:

```bash
npm install powerbi-visuals-utils-testutils --save
```

Hieronder vindt u beschrijvingen en voorbeelden van de openbare API voor testhulpmiddelen.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Wordt gebruikt door **VisualBuilder** in eenheidstests met de meestgebruikte methoden `build`, `update` en `updateRenderTimeout`. 

Met de methode `build` wordt een gemaakt exemplaar van de visual geretourneerd.

De methoden `enumerateObjectInstances` en `updateEnumerateObjectInstancesRenderTimeout` zijn vereist om te controleren op wijzigingen in de bucket en opmaakopties.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Zie [VisualBuilderBase-eenheidstests schrijven](./unit-tests-introduction.md#create-a-visual-instance-builder) en een [scenario voor werkelijk gebruik van VisualBuilderBase](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts) voor meer voorbeelden.

## <a name="dataviewbuilder"></a>DataViewBuilder

Deze module wordt gebruikt door **TestDataViewBuilder** en biedt een **CategoricalDataViewBuilder**-klasse die wordt gebruikt in de methode `createCategoricalDataViewBuilder`. Er worden ook interfaces en methoden opgegeven die vereist zijn voor het werken met nagebootste **DataView** in eenheidstests.

* Met `withValues` worden kolommen met statische reeksen toegevoegd en met `withGroupedValues` worden kolommen met dynamische reeksen toegevoegd

  Pas geen dynamische reeksen en statische reeksen tegelijk toe in een **DataViewCategorical**-visual. U kunt deze alleen tegelijk gebruiken in de **DataViewCategorical**-query, waarbij **DataViewTransform** deze zal opsplitsen in afzonderlijke visuele **DataViewCategorical**-objecten.

* Met `build` wordt de DataView met metagegevens en DataViewCategorical geretourneerd

  Met `build` wordt **Ongedefinieerd** geretourneerd als de combinatie van parameters ongeldig is, zoals wanneer u zowel dynamische als statische reeksen opneemt bij het bouwen van de **DataView** van de visual.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Wordt gebruikt voor het maken van **VisualData** in eenheidstesten. Wanneer gegevens in gegevensveldbuckets worden geplaatst, produceert Power BI een categorisch **DataView**-object op basis van uw gegevens. Met **TestDataViewBuilder** kunt u het categorisch maken van **DataView** simuleren.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  Hieronder vindt u de meest gebruikte interfaces voor het maken van een `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Zie [TestDataViewBuilder-eenheidstests schrijven](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) en een [scenario voor werkelijk gebruik van TestDataViewBuilder](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts) voor meer voorbeelden.

## <a name="mocks"></a>Dummy's

### <a name="mockivisualhost"></a>MockIVisualHost

Hiermee wordt **IVisualHost** geïmplementeerd, zodat u Power BI-visuals kunt testen zonder externe afhankelijkheden, zoals het Power BI-framework.

Handige methoden zijn onder andere de eigenschappen `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` en getter.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- Met `createVisualHost` wordt een exemplaar van **IVisualHost** gemaakt en geretourneerd, in werkelijkheid **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Voorbeeld
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** is een nepimplementatie van **IVisualHost** en mag alleen worden gebruikt bij eenheidstesten.

### <a name="mockicolorpalette"></a>MockIColorPalette

Hiermee wordt **IColorPalette** geïmplementeerd, zodat u Power BI-visuals kunt testen zonder externe afhankelijkheden, zoals het Power BI-framework.

**MockIColorPalette** biedt nuttige eigenschappen voor het controleren van het kleurenschema of de modus Hoog contrast in eenheidstesten.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - Met `createColorPalette` wordt een exemplaar van **IColorPalette** gemaakt en geretourneerd, in werkelijkheid **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Voorbeeld
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** is een nepimplementatie van **IColorPalette** en mag alleen worden gebruikt bij eenheidstesten.

### <a name="mockiselectionid"></a>MockISelectionId

Hiermee wordt **ISelectionId** geïmplementeerd, zodat u Power BI-visuals kunt testen zonder externe afhankelijkheden, zoals het Power BI-framework.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - Met `createSelectionId` wordt een exemplaar van **ISelectionId** gemaakt en geretourneerd, in werkelijkheid **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Voorbeeld
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** is een nepimplementatie van **ISelectionId** en mag alleen worden gebruikt bij eenheidstesten.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Hiermee wordt **ISelectionIdBuilder** geïmplementeerd, zodat u Power BI-visuals kunt testen zonder externe afhankelijkheden, zoals het Power BI-framework. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - Met `createSelectionIdBuilder` wordt een exemplaar van **ISelectionIdBuilder** gemaakt en geretourneerd, in werkelijkheid **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Voorbeeld
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** is een nepimplementatie van **ISelectionIdBuilder** en mag alleen worden gebruikt bij eenheidstesten.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Hiermee wordt **ISelectionManager** geïmplementeerd, zodat u Power BI-visuals kunt testen zonder externe afhankelijkheden, zoals het Power BI-framework. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - Met `createSelectionManager` wordt een exemplaar van **ISelectionManager** gemaakt en geretourneerd, in werkelijkheid **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Voorbeeld
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** is een nepimplementatie van **ISelectionManager** en mag alleen worden gebruikt bij eenheidstesten.

### <a name="mockilocale"></a>MockILocale

  Hiermee stelt u de landinstelling in en wijzigt u deze naar wens tijdens het eenheidstestproces.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - Met `createLocale` wordt een exemplaar van **MockILocale** gemaakt en geretourneerd
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Hiermee wordt `TooltipService` gesimuleerd en naar wens aangeroepen tijdens het eenheidstestproces.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - Met `createTooltipService` wordt een exemplaar van **MockITooltipService** gemaakt en geretourneerd
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - Met `createAllowInteractions` wordt een exemplaar van **MockIAllowInteractions** gemaakt en geretourneerd
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Hiermee worden basismogelijkheden geboden van **LocalizationManager** die nodig zijn voor eenheidstests.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - Met `createLocalizationManager` wordt een exemplaar van **ILocalizationManager** gemaakt en geretourneerd, in werkelijkheid **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Voorbeeld
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Hiermee wordt het gebruik van **TelemetryService** gesimuleerd.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Maken van `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Hiermee wordt het werk van **AuthenticationService** gesimuleerd, door een nagebootst AAD-token op te geven.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - Met `createAuthenticationService` wordt een exemplaar van **IAuthenticationService** gemaakt en geretourneerd, in werkelijkheid **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Hiermee kunt u **ILocalVisualStorageService** gebruiken met hetzelfde gedrag als **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - Met `createStorageService` wordt een exemplaar van **ILocalVisualStorageService** gemaakt en geretourneerd, in werkelijkheid **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - Met `createEventService` wordt een exemplaar van **IVisualEventService** gemaakt en geretourneerd, in werkelijkheid **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utils

Utils bevat hulpmethoden voor eenheidstests van Power BI-visuals, met inbegrip van hulpmiddelen die betrekking hebben op kleuren, getallen en gebeurtenissen.

- Met `renderTimeout` wordt een time-out geretourneerd
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- Met `testDom` kunt u aansluitingen instellen in eenheidstests
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Voorbeeld
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Hulpmethoden die betrekking hebben op kleur

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Hiermee wordt de volgende structuur geretourneerd:

  ```json
  { solid: { color: color } }
  ```

- Met `assertColorsMatch` worden **RgbColor**-objecten vergeleken die zijn geparseerd uit invoerreeksen
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- Met `parseColorString` wordt de kleur van de invoerreeks geparseerd en geretourneerd in de opgegeven **RgbColor** van de interface
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Hulpmethoden met betrekking tot getallen

- Met `getRandomNumbers` wordt een willekeurig getal gegenereerd met de minimum- en maximumwaarden. U kunt `exceptionList` opgeven en een functie bieden voor een wijziging van de resultaten.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- Met `getRandomNumbers` wordt een matrix geboden met willekeurige getallen die zijn gegenereerd door de `getRandomNumber`-methode met de opgegeven minimum- en maximumwaarden
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Hulpmethoden die betrekking hebben op gebeurtenissen
De volgende methoden zijn geschreven voor het simuleren van webpaginagebeurtenissen in eenheidstests.

- Met `clickElement` wordt een klik op het opgegeven element gesimuleerd
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- Met `createTouch` wordt een **aanraak**object geretourneerd om een aanraakgebeurtenis te simuleren
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- Met `createTouchesList` wordt een lijst met gesimuleerde **aanraak**gebeurtenissen geretourneerd
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- Met `createContextMenuEvent` wordt **MouseEvent** geretourneerd
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- Met `createMouseEvent` wordt **MouseEvent** gemaakt en geretourneerd
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Hulpmethoden met betrekking tot D3-gebeurtenissen

De volgende methoden worden gebruikt voor het simuleren van D3-gebeurtenissen in eenheidstests.

- Met `flushAllD3Transitions` worden alle D3-overgangen geforceerd voltooid

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normaal gesproken worden overgangen met nul vertraging uitgevoerd na een onmiddellijke vertraging (< 10 ms), maar dit kan een korte flikkering veroorzaken als de pagina tweemaal wordt weergegeven in de browser. Eenmaal aan het einde van de eerste gebeurtenislus, daarna onmiddellijk opnieuw bij de eerste callback van de timer.
  >
  > Deze flikkeringen zijn duidelijker waarneembaar in Internet Explorer en bij een groot aantal webweergaven en worden niet aanbevolen voor iOS.
  > 
  > Door de wachtrij voor de timer aan het einde van de eerste gebeurtenislus leeg te maken, kunt u de overgangen met nul vertraging onmiddellijk uitvoeren waarmee de flikkering wordt voorkomen.

De volgende methoden zijn ook opgenomen:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Help-interfaces
De volgende interface en opsommingen worden gebruikt in de Help-functie.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Volgende stappen

Als u eenheidstests voor op webpakketten gebaseerde Power BI-visuals en eenheidstests met `karma` en `jasmine` wilt schrijven, raadpleegt u het voorbeeld [Zelfstudie: Eenheidstests voor Power BI-visualprojecten toevoegen](./unit-tests-introduction.md).
