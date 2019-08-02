---
title: API voor visuele filters
description: Hoe u met Power BI-visuals andere visuals kunt filteren
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425040"
---
# <a name="power-bi-visual-filters-api"></a>Power BI-API voor visuele filters

Met Visuals filteren kunt u gegevens filteren. Het belangrijkste verschil met selecties is dat andere visuals sowieso worden gefilterd, ondanks de ondersteuning voor markeringen in andere visuals.

Als u filters voor de visual wilt inschakelen, moet de visual het `filter`-object bevatten in het `general`-gedeelte met capabilities.json-inhoud.

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

Filter-API-interfaces zijn beschikbaar in het [`powerbi-models`](https://www.npmjs.com/package/powerbi-models)-pakket. Het pakket bevat tevens klassen om filterexemplaren te maken.

```cmd
npm install powerbi-models --save
```

Als u oude versies van hulpprogramma's gebruikt (ouder dan 3.x.x), moet u `powerbi-models` insluiten in het visualspakket. [Beknopte handleiding over het insluiten van het pakket](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

De `IFilter`-interface wordt in alle filters gebruikt.

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target`: is een tabelkolom in een gegevensbron.

## <a name="basic-filter-api"></a>Basisfilter-API

Basisfilterinterface is

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator`: is een opsomming met de waarden In, NotIn en All

`values`: zijn waarden voor voorwaarden

Voorbeeld van basisfilter:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Het filter betekent: 'geef alle rijen weer waarbij `col1` overeenkomt met een van de waarden 1, 2 of 3'.

SQL-equivalent is

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Als u een filter wilt maken, kunt u de BasicFilter-klasse in `powerbi-models` gebruiken.

Als u de oude versies van hulpprogramma's gebruikt, krijgt u een exemplaar van modellen in het vensterobject van `window['powerbi-models']`:

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

Het filter wordt door de visual aangeroepen met behulp van de methode applyJsonFilter() op de hostinterface IVisualHost die in de constructor voor de visual is opgegeven.

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>Geavanceerd filteren-API

Met de [Geavanceerde filter-API](https://github.com/Microsoft/powerbi-models) zijn complexe query's met gegevenspuntselectie/-filters voor meerdere visuals mogelijk op basis van meerdere criteria (zoals LessThan, Contains, Is, IsBlank, enzovoort).

Het filter werd voor het eerst gebruikt in Visuals-API 1.7.0.

Voor de Geavanceerde filter-API is ook `target` vereist, met de naam `table` en `column`. Maar Geavanceerde filter-API-operators zijn `"And" | "Or"`. 

Daarnaast worden voor het filter voorwaarden gebruikt in plaats van waarden met een interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Voorwaardeoperators voor parameter `operator` zijn `"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"`

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

SQL-equivalent is

```sql
SELECT * FROM table WHERE col1 < 0;
```

U vindt de volledige voorbeeldcode voor het gebruik van de Geavanceerde filter-API in de [`Sampleslicer visual`-opslagplaats](https://github.com/Microsoft/powerbi-visuals-sampleslicer).

## <a name="tuple-filter-api-multi-column-filter"></a>Tuple-filter-API (filter voor meerdere kolommen)

De Tuple-filter-API werd voor het eerst gebruikt in Visuals-API 2.3.0.

De Tuple-filter-API is vergelijkbaar met het basisfilter, maar hiermee kunt u voorwaarden voor verschillende kolommen en tabellen definiëren.

En een filter heeft een interface: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` is een matrix met kolommen met tabelnamen:

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  Met het filter kunnen kolommen uit andere tabellen worden gebruikt.

`$schema` is "http://powerbi.com/product/schema#tuple"

`filterType` is `FilterType.Tuple`

`operator` staat alleen het gebruik van de `"In"`-operator toe

`values` is een matrix met waardetuples, waarbij elke tuple één toegestane combinatie van de doelkolomwaarden vertegenwoordigt 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

Volledig voorbeeld:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**De volgorde van kolomnamen en de waarden van een voorwaarde zijn gevoelig.**

SQL-equivalent is

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>JSON-filters herstellen vanuit DataView

Vanaf API 2.2 kunnen **JSON-filters** worden hersteld via **VisualUpdateOptions**

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

In Power BI wordt de `update`-methode van de visual aangeroepen, wanneer u schakelbladwijzers gebruikt en de visual het bijbehorende `filter`-object krijgt.
[Meer informatie over ondersteuning voor bladwijzers](bookmarks-support.md)

### <a name="sample-json-filter"></a>Voorbeeld van JSON-filter

![Schermopname van JSON-filter](./media/json-filter.png)

### <a name="clear-json-filter"></a>JSON-filter wissen

De Filter-API accepteert de `null`-waarde van het filter als Opnieuw instellen of Wissen.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
