---
title: Objecten en eigenschappen van Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: In dit artikel worden de aanpasbare eigenschappen van Power BI-visuals beschreven. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4596465fcd9f59768b18282ec3ad39d2531b7768
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885954"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Objecten en eigenschappen van Power BI-visuals

Met objecten kunt u aanpasbare eigenschappen beschrijven die aan een visual zijn gekoppeld. Een object kan meerdere eigenschappen hebben, en elke eigenschap heeft een bijbehorend type dat aangeeft wat de eigenschap wordt. Dit artikel bevat informatie over objecten en eigenschapstypen.

`myCustomObject` is de interne naam die binnen `dataView` en `enumerateObjectInstances` wordt gebruikt om naar het object te verwijzen.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>Weergavenaam

`displayName` is de naam die wordt weergegeven in het eigenschappenvenster.

## <a name="properties"></a>Eigenschappen

`properties` is een toewijzing van eigenschappen die door de ontwikkelaar zijn gedefinieerd.

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` is een speciale eigenschap waarmee een schakelaar het object kan in-/uitschakelen.

Voorbeeld:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>Eigenschapstypen

Er zijn twee eigenschapstypen: `ValueTypeDescriptor` en `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Waardetypedescriptor

`ValueTypeDescriptor`-typen zijn voornamelijk primitief en worden meestal gebruikt als statisch object.

Hier volgen enkele algemene `ValueTypeDescriptor`-elementen:

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Structuurtypedescriptor

`StructuralTypeDescriptor`-typen worden meestal gebruikt voor gegevensgebonden objecten.
Het meest voorkomende `StructuralTypeDescriptor`-type is *fill*.

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Kleurovergang-eigenschap

De eigenschap kleurovergang is een eigenschap die niet kan worden ingesteld als een standaardeigenschap. In plaats daarvan moet u een regel instellen voor het vervangen van de eigenschap kleurkiezer (type *fill*).

Een voorbeeld wordt weergegeven in de volgende code:

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

Let op de eigenschappen *fill* en *fillRule*. De eerste is de kleurkiezer, de tweede is de vervangingsregel voor de kleurovergang waardoor de *fill-eigenschap*, `visually`, wordt vervangen wanneer aan de voorwaarden van de regel wordt voldaan.

Deze koppeling tussen de eigenschap *fill`"rule"` en de vervangingsregel wordt ingesteld in de sectie* >`"output"` van de eigenschap *fillRule*.

Met de eigenschap `"Rule"`>`"InputRole"` wordt ingesteld welke gegevensrol de regel activeert (voorwaarde). In dit voorbeeld wordt de regel toegepast voor de eigenschap `"fill"` als de gegevensrol `"Gradient"` gegevens bevat.

In de volgende code ziet u een voorbeeld van de gegevensfunctie waarmee de fill-regel (`the last item`) wordt geactiveerd:

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>De methode enumerateObjectInstances

Als u objecten effectief wilt gebruiken, hebt u in uw aangepaste visual een functie nodig met de naam `enumerateObjectInstances`. Deze functie vult het eigenschappenvenster met objecten en bepaalt ook waar uw objecten binnen de dataView moeten worden gebonden.  

Een typische structuur ziet er als volgt uit:

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>Eigenschappen

De eigenschappen in `enumerateObjectInstances` komen overeen met de eigenschappen die u in uw mogelijkheden hebt gedefinieerd. Ga naar het einde van dit artikel voor een voorbeeld.

### <a name="objects-selector"></a>Objectselector

De selector in `enumerateObjectInstances` bepaalt waar elk object in de dataView wordt gebonden. Er zijn vier verschillende opties.

#### <a name="static"></a>statisch

Dit object is gebonden aan metagegevens `dataviews[index].metadata.objects`, zoals hier wordt weergegeven.

```typescript
selector: null
```

#### <a name="columns"></a>kolommen

Dit object is gebonden aan kolommen met de overeenkomende `QueryName`.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Dit object is gebonden aan het element waarvoor we een `selectionID` hebben gemaakt. In dit voorbeeld wordt ervan uitgegaan dat we `selectionID`'s hebben gemaakt voor een aantal gegevenspunten en dat we die in een lus doorlopen.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope-id

Dit object is gebonden aan bepaalde waarden op het snijpunt van groepen. Als u bijvoorbeeld de categorieën `["Jan", "Feb", "March", ...]` en de reeks `["Small", "Medium", "Large"]` hebt, wilt u misschien een object hebben op het snijpunt van waarden dat overeenkomt met `Feb` en `Large`. Om dit te bereiken kunt u de `DataViewScopeIdentity` van beide kolommen ophalen, deze naar de variabele `identities` pushen en deze syntaxis gebruiken met de selector.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Voorbeeld

In het volgende voorbeeld ziet u hoe één objectEnumeration eruit zou zien voor een customColor-object met één eigenschap, *fill*. We willen dit object statisch binden aan `dataViews[index].metadata.objects`, zoals weergegeven:

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
