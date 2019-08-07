---
title: Object en eigenschappen
description: Aanpasbare eigenschappen van Power BI Visual
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424603"
---
# <a name="object-and-properties"></a>Object en eigenschappen

Met objecten kunt u de aanpasbare eigenschappen beschrijven die aan de visual zijn gekoppeld.
Elk object kan meerdere eigenschappen hebben, en aan elke eigenschap is een type gekoppeld.
Typen verwijzen naar de uiteindelijke functie van de eigenschap. Hieronder vindt u meer informatie over typen.

`myCustomObject` is de interne naam die binnen `dataView` en `enumerateObjectInstances` wordt gebruikt om naar het object te verwijzen

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

`properties` is een toewijzing van door de ontwikkelaar gedefinieerde eigenschappen.

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

Er zijn twee soorten eigenschapstypen: `ValueTypeDescriptor` en `StructuralTypeDescriptor`.

#### <a name="value-type-descriptor"></a>Waardetypedescriptor

`ValueTypeDescriptor` zijn voornamelijk primitieve typen, en worden meestal gebruikt als statisch object.
Hier volgen enkele algemene `ValueTypeDescriptor`

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>Structuurtypedescriptor

`StructuralTypeDescriptor` worden meestal gebruikt voor gegevensgebonden objecten.
Fill is de meestvoorkomende `StructuralTypeDescriptor`

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>Kleurovergang-eigenschap

De kleurovergang-eigenschap is een eigenschap die niet kan worden ingesteld als een standaardeigenschap. In plaats daarvan moet u een regel instellen voor het vervangen van de kleurkiezer-eigenschap (type opvulling).
Zie het voorbeeld hieronder:

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

Let op de eigenschappen `"fill"` en `"fillRule"`. De eerste is de kleurkiezer, de tweede is de vervangingsregel voor de kleurovergang waardoor de eigenschap 'fill' `visually` wordt vervangen wanneer aan de voorwaarden van de regel wordt voldaan.

Deze koppeling tussen de eigenschap 'fill' en de vervangingsregel wordt ingesteld in de sectie `"rule"`->`"output"` van de eigenschap `"fillRule"`.

Met `"Rule"`->`"InputRole"` wordt ingesteld welke gegevensrol de regel activeert (voorwaarde). In dit voorbeeld wordt de regel toegepast voor de eigenschap `"fill"` als de gegevensrol `"Gradient"` gegevens bevat.

Hieronder ziet u een voorbeeld van de gegevensfunctie waarmee de fill-regel (`the last item`) wordt geactiveerd.

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

## <a name="enumerateobjectinstances-method"></a>`enumerateObjectInstances`-methode

Als u objecten effectief wilt gebruiken, hebt u in uw aangepaste visual een functie nodig met de naam `enumerateObjectInstances`. Deze functie vult het eigenschappenvenster met objecten, en bepaalt ook waar uw objecten binnen de dataView moeten worden gebonden.  

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

De eigenschappen in `enumerateObjectInstances` komen overeen met de eigenschappen die u in uw mogelijkheden hebt gedefinieerd. Zie het voorbeeld onderaan de pagina.

### <a name="objects-selector"></a>Objectselector

De selector in `enumerateObjectInstances` bepaalt waar elk object in de data View wordt gebonden. Er zijn vier verschillende opties.

#### <a name="static"></a>statisch

Dit object wordt gebonden aan metagegevens `dataviews[index].metadata.objects`

```typescript
selector: null
```

#### <a name="columns"></a>kolommen

Dit object wordt gebonden aan kolommen met de overeenkomende `QueryName`.

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>selector

Dit object wordt gebonden aan het element waarvoor we een `selectionID` hebben gemaakt. In dit voorbeeld wordt ervan uitgegaan dat we voor een aantal dataPoints `selectionID`'s hebben gemaakt en dat we die in een lus doorlopen.

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>Scope-id

Dit object wordt gebonden aan bepaalde waarden op het snijpunt van groepen. Als ik bijvoorbeeld de categorieën `["Jan", "Feb", "March", ...]` en de reeks `["Small", "Medium", "Large"]` heb, wil ik misschien een object hebben op het snijpunt van waarden dat overeenkomt met `Feb` en `Large`. Om dit te bereiken kan ik de `DataViewScopeIdentity` van beide kolommen ophalen, deze naar de variabele `identities` pushen, en deze syntaxis gebruiken met de selector.

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>Voorbeeld

In dit voorbeeld laten we zien hoe één objectEnumeration eruit zou zien voor een customColor-object met één `fill`-eigenschap. We willen dit object statisch binden aan `dataViews[index].metadata.objects`

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
