---
title: De API voor visuele filters in Power BI-visuals
description: In dit artikel wordt beschreven hoe u met Power BI-visuals andere visuals kunt filteren.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 98ebc87cf5a6b7bf8f0b8b88d4ff498edfd5bf9a
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194019"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>De API voor visuele filters in Power BI-visuals

Met de API voor visuele filters kunt u gegevens filteren in Power BI-visuals. Het belangrijkste verschil met andere selecties is dat andere visuals sowieso worden gefilterd, ondanks de ondersteuning voor markeringen in andere visuals.

Als u filters voor de visual wilt inschakelen, moet de visual een `filter`-object bevatten in het `general`-gedeelte met *capabilities.json*-code.

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

API-interfaces voor visuele filters zijn beschikbaar in het [Power BI-modellen](https://www.npmjs.com/package/powerbi-models)-pakket. Het pakket bevat tevens klassen om filterexemplaren te maken.

```cmd
npm install powerbi-models --save
```

Als u een oudere versie van de hulpprogramma's (ouder dan 3.x.x) gebruikt, moet u `powerbi-models` aan het visuals-pakket toevoegen. Zie de korte handleiding [Add the Advanced Filter API to the custom visual](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md) voor meer informatie.

Met alle filters wordt de `IFilter`-interface uitgebreid, zoals wordt weergegeven in de volgende code:

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
Waarbij:
* `target` de kolomtabel op de gegevensbron is.

## <a name="the-basic-filter-api"></a>De Basisfilter-API

De Basisfilter-interface wordt weergegeven in de volgende code:

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

Waarbij:
* `operator` is een opsomming met de waarden *In*, *NotIn* en *All*.
* `values` zijn waarden voor de voorwaarde.

Voorbeeld van een basisfilter:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

Het filter betekent: 'Geef alle rijen weer waarbij `col1` overeenkomt met 1, 2 of 3'.

Het SQL-equivalent is:

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

Als u een filter wilt maken, kunt u de BasicFilter-klasse in `powerbi-models` gebruiken.

Als u een oudere versie van het hulpprogramma gebruikt, krijgt u een exemplaar van modellen in het vensterobject door `window['powerbi-models']` te gebruiken, zoals wordt weergegeven in de volgende code:

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

## <a name="the-advanced-filter-api"></a>De Geavanceerde filter-API

Met de [Geavanceerde filter-API](https://github.com/Microsoft/powerbi-models) zijn complexe query's met gegevenspuntselectie en filters voor meerdere visuals mogelijk op basis van meerdere criteria, zoals *LessThan*, *Contains*, *Is*, *IsBlank*, enzovoort.

Het filter werd voor het eerst gebruikt in Visuals-API 1.7.0.

Voor de Geavanceerde filter-API is ook `target` vereist, met een naam voor `table` en `column`. De Geavanceerde filter-API-operators zijn echter *And* en *Or*. 

Daarnaast worden voor het filter voorwaarden gebruikt in plaats van waarden met de interface:

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

Voorwaardeoperators voor de `operator`-parameter zijn *None*, *LessThan*, *LessThanOrEqual*, *GreaterThan*, *GreaterThanOrEqual*, *Contains*, *DoesNotContain*, *StartsWith*, *DoesNotStartWith*, *Is*, *IsNot*, *IsBlank* en IsNotBlank

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

Het SQL-equivalent is:

```sql
SELECT * FROM table WHERE col1 < 0;
```

Ga naar de [Sampleslicer-opslagplaats voor visuals](https://github.com/Microsoft/powerbi-visuals-sampleslicer) voor de volledige voorbeeldcode voor de Geavanceerde filter-API.

## <a name="the-tuple-filter-api-multi-column-filter"></a>De Tuple-filter-API (filter voor meerdere kolommen)

De Tuple-filter-API werd voor het eerst gebruikt in Visuals-API 2.3.0. De Tuple-filter-API is vergelijkbaar met de Basisfilter-API, maar hiermee kunt u voorwaarden voor verschillende kolommen en tabellen definiëren.

De filterinterface wordt weergegeven in de volgende code: 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

Waarbij:
* `target` is een matrix met kolommen met tabelnamen:

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  Met het filter kunnen kolommen uit verschillende tabellen worden gebruikt.

* `$schema` is http://powerbi.com/product/schema#tuple.

* `filterType` is *FilterType.Tuple*.

* `operator` kan alleen worden gebruikt in de *In*-operator.

* `values` is een matrix met waardetuples en elke tuple vertegenwoordigt één toegestane combinatie van de doelkolomwaarden. 

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
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
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

> [!IMPORTANT]
> De volgorde van de kolomnamen en waarde van voorwaarden is gevoelig.

Het SQL-equivalent is:

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>Het JSON-filter herstellen vanuit de gegevensweergave

Vanaf API-versie 2.2 kunt u het JSON-filter herstellen vanuit *VisualUpdateOptions*, zoals wordt weergegeven in de volgende code:

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

In Power BI wordt de `update`-methode van de visual aangeroepen, wanneer u schakelbladwijzers gebruikt en de visual het bijbehorende `filter`-object krijgt. Zie [Ondersteuning voor bladwijzers toevoegen voor Power BI-visuals](bookmarks-support.md) voor meer informatie.

### <a name="sample-json-filter"></a>Voorbeeld van JSON-filter

In de volgende afbeelding wordt een voorbeeld van JSON-filtercode weergegeven:

![JSON-filtercode](./media/json-filter.png)

### <a name="clear-the-json-filter"></a>Het JSON-filter wissen

De Filter-API accepteert de `null`-waarde van het filter als *Opnieuw instellen* of *Wissen*.

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
