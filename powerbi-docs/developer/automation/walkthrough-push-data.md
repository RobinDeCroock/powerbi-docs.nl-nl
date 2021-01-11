---
title: Gegevens in een gegevensset pushen naar ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: Push gegevens naar een Power BI-gegevensset. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 3c5805f4d498e8e2d8a788c5703a09a8109e024b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887426"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Gegevens naar een Power BI-gegevensset pushen

Met de Power BI-API kunt u gegevens pushen naar een Power BI-gegevensset. In dit artikel laten we u zien hoe u een gegevensset voor Verkoopmarketing met een producttabel pusht naar een bestaande gegevensset.

Voordat u aan de slag gaat, hebt u een Azure Active Directory (Azure AD) en een [Power BI-account](../embedded/create-an-azure-active-directory-tenant.md) nodig.

## <a name="steps-to-push-data-into-a-dataset"></a>Stappen om gegevens naar een gegevensset te pushen

* Stap 1: [Een app bij Azure AD registreren](../embedded/register-app.md)
* Stap 2: [Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md)
* Stap 3: [Create a dataset in Power BI](walkthrough-push-data-create-dataset.md) (Een gegevensset maken in Power BI)
* Stap 4: [Een gegevensset ophalen om rijen toe te voegen aan een Power BI-tabel](walkthrough-push-data-get-datasets.md)
* Stap 5: [Add rows to a Power BI table](walkthrough-push-data-add-rows.md) (Rijen toevoegen aan een Power BI-tabel)

Het volgende gedeelte bevat een algemene bespreking van Power BI API-bewerkingen die gegevens pushen.

## <a name="power-bi-api-operations-to-push-data"></a>Power BI API-bewerkingen om gegevens te pushen

Met de REST-API voor Power BI kunt u gegevensbronnen pushen naar Power BI. Wanneer een app rijen toevoegt aan een gegevensset, worden dashboardtegels automatisch bijgewerkt met de nieuwe gegevens. Gebruik de bewerkingen [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) en [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows) om gegevens te pushen. Als u een gegevensset zoekt, gebruikt u de bewerking [Gegevenssets ophalen](/rest/api/power-bi/datasets/getdatasets). U kunt een groeps-id doorvoeren om met een groep te werken voor elk van deze bewerkingen. Gebruik de bewerking [Groepen ophalen](/rest/api/power-bi/groups/getgroups) om een lijst met groeps-id's op te halen.

Met de volgende bewerkingen kunt u gegevens naar een gegevensset pushen:

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Gegevenssets ophalen](/rest/api/power-bi/datasets/getdatasets)
* [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Groepen ophalen](/rest/api/power-bi/groups/getgroups)

U maakt u een gegevensset in Power BI door een JSON-tekenreeks (JavaScript Object Notation) door te geven aan de Power BI-service. Zie [Inleiding tot JSON](https://json.org/) voor meer informatie over JSON.

De JSON-tekenreeks voor een gegevensset heeft de volgende indeling:

**JSON-object voor Power BI-gegevensset**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

Voor de voorbeeldgegevensset Sales Marketing moet u een JSON-tekenreeks doorgeven zoals hieronder wordt weergegeven. In dit voorbeeld is **SalesMarketing** de naam van de gegevensset en **Product** is de naam van de tabel. Nadat u de tabel hebt gedefinieerd, definieert u het tabelschema. Voor de gegevensset **SalesMarketing** heeft het tabelschema deze kolommen: ProductID, Manufacturer, Category, Segment, Product en IsCompete.

**Voorbeeld van JSON-object voor gegevensset**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

Voor een Power BI-tabelschema kunt u de volgende gegevenstypen gebruiken.

## <a name="power-bi-table-data-types"></a>Gegevenstypen voor Power BI-tabellen

| **Gegevenstype** | **Beperkingen** |
| --- | --- |
| Int64 |Int64.MaxValue en Int64.MinValue zijn niet toegestaan. |
| Dubbel |Double.MaxValue en Double.MinValue zijn niet toegestaan. NaN wordt niet ondersteund. +Infinity en -Infinity worden niet ondersteunt door sommige functies (bijvoorbeeld Min, Max). |
| Booleaans |Geen |
| Datum/tijd |Tijdens het laden van gegevens worden waarden met breuken voor de dag afgerond tot veelvouden van 1/300 seconde (3,33 ms). |
| Tekenreeks |Momenteel zijn maximaal 128.000 tekens toegestaan. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Meer informatie over het pushen van gegevens naar Power BI

Als u gegevens in een gegevensset wilt pushen, raadpleegt u [Stap 1: Een app registreren met Azure AD](../embedded/register-app.md) in het navigatievenster.

## <a name="next-steps"></a>Volgende stappen

* [Registreren voor Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [Inleiding tot JSON](https://json.org/)  
* [Overview of Power BI REST API](overview-of-power-bi-rest-api.md) (Overzicht van de REST-API voor Power BI)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)