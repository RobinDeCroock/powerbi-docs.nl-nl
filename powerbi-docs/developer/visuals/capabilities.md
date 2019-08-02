---
title: Mogelijkheden
description: Mogelijkheden en eigenschappen van Power BI-visuals
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425454"
---
# <a name="power-bi-visual-capabilities"></a>Mogelijkheden van Power BI-visuals

Bij de mogelijkheden krijgt de host informatie over uw visual. Alle eigenschappen van het mogelijkhedenmodel zijn `optional`

Hoofdobjecten van de mogelijkheden van een visual zijn `dataRoles`, `dataViewMappings`, enzovoort.

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>De gegevensvelden definiëren die voor uw visual worden verwacht - `dataRoles`

Als u velden wilt definiëren die aan gegevens kunnen worden gekoppeld, gebruikt u `dataRoles`. Hiervoor wordt een array van `DataViewRole`-objecten gebruikt waarmee alle benodigde eigenschappen worden gedefinieerd.

### <a name="properties"></a>Eigenschappen

* **name**: de interne naam van dit gegevensveld (moet uniek zijn)
* **kind**: het soort veld:
    * `Grouping`: discrete waarden die worden gebruikt voor het groeperen van velden met metingen
    * `Measure`: numerieke gegevenswaarden
    * `GroupingOrMeasure`: kan worden gebruikt als groepering of als meting
* **displayName**: de naam die voor gebruikers wordt weergegeven in het deelvenster Eigenschappen
* **description**: een korte beschrijving van het veld (optioneel)
* **requiredTypes**: het vereiste gegevenstype voor deze gegevensrol. Alle waarden die niet overeenkomen, worden ingesteld op null (optioneel)
* **preferredTypes**: het gewenste gegevenstype voor deze gegevensrol (optioneel)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>Geldige gegevenstypen in requiredTypes en preferredTypes

* **bool**: een booleaanse waarde
* **integer**: een waarde die uit een geheel getal bestaat
* **numeric**: een numerieke waarde
* **text**: een tekstwaarde
* **geography**: geografische gegevens

### <a name="example"></a>Voorbeeld

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

Door de bovenstaande gegevensrollen worden de volgende velden gemaakt

![Gegevensrol met weergave van](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>Definiëren hoe u de gegevens wilt toewijzen - `dataViewMappings`

Met een DataViewMapping wordt de relatie tussen de verschillende gegevensrollen beschreven. Ook kunt u hiermee voorwaardelijke vereisten voor deze rollen opgeven.

Voor de meeste visuals is één toewijzing beschikbaar, maar u kunt meerdere dataViewMappings opgeven. Door elke geldige toewijzing wordt een DataView geproduceerd. 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[Meer informatie over DataViewMappings](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>Opties in het deelvenster Eigenschap definiëren - `objects`

Met objecten kunt u de aanpasbare eigenschappen beschrijven die aan de visual zijn gekoppeld.
Elk object kan meerdere eigenschappen hebben en aan elke eigenschap is een type gekoppeld.
Typen verwijzen naar de uiteindelijke functie van de eigenschap. Hieronder vindt u meer informatie over typen.

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[Meer informatie over objecten](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>Gedeeltelijke markeringen verwerken - `supportsHighlight`

Deze waarde is standaard ingesteld op False. Dit houdt in dat uw 'Waarden' automatisch worden gefilterd zodra er iets op de pagina wordt geselecteerd, waardoor uw visual wordt bijgewerkt en alleen de geselecteerde waarde wordt weergegeven. Als u de volledige gegevens wilt weergeven maar alleen de geselecteerde items wilt markeren, moet u `supportsHighlight` instellen op True in uw capabilities.json.

[Meer informatie over markeren](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>Geavanceerde bewerkingsmodus verwerken - `advancedEditModeSupport`

U kunt declareren dat de geavanceerde bewerkingsmodus door de visual wordt ondersteund.
Standaard bieden visuals geen ondersteuning voor de geavanceerde bewerkingsmodus, tenzij dit anders wordt aangegeven in de capabilities.json.

[Meer informatie over advancedEditModeSupport](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>Opties voor het sorteren van gegevens voor visuals - `sorting`

Via de mogelijkheden van een visual kunt u het sorteergedrag van de visual definiëren.
Standaard bieden visuals geen ondersteuning voor aanpassing van de bijbehorende sorteervolgorde, tenzij dit anders wordt aangegeven in de capabilities.json.

[Meer informatie over sorteren](sort-options.md)
