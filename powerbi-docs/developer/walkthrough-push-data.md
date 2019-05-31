---
title: Gegevens naar een gegevensset pushen
description: Gegevens naar een Power BI-gegevensset pushen
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222145"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Gegevens naar een Power BI-gegevensset pushen

De Power BI API kunt u gegevens naar een Power BI-gegevensset pushen. In dit artikel, we laten zien hoe u een gegevensset Sales Marketing met een producttabel in een bestaande gegevensset pushen.

Voordat u begint, moet u een Azure Active Directory (Azure AD) en een [Power BI-account](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Stappen om gegevens naar een gegevensset te pushen

* Stap 1: [Register an app with Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) (Een app bij Azure AD registreren)
* Stap 2: [Get an authentication access token](walkthrough-push-data-get-token.md) (Een verificatietoegangstoken ophalen)
* Stap 3: [Create a dataset in Power BI](walkthrough-push-data-create-dataset.md) (Een gegevensset maken in Power BI)
* Stap 4: [Get a dataset to add rows into a Power BI table](walkthrough-push-data-get-datasets.md) (Een gegevensset ophalen om rijen toe te voegen aan een Power BI-tabel)
* Stap 5: [Add rows to a Power BI table](walkthrough-push-data-add-rows.md) (Rijen toevoegen aan een Power BI-tabel)

Het volgende gedeelte bevat een algemene bespreking van Power BI API-bewerkingen die gegevens pushen.

## <a name="power-bi-api-operations-to-push-data"></a>Power BI API-bewerkingen om gegevens te pushen

Met de REST-API voor Power BI kunt u gegevensbronnen pushen naar Power BI. Wanneer een app rijen aan een gegevensset toevoegt, dashboard-tegels update automatisch met de nieuwe gegevens. Om gegevens te pushen, gebruikt u de [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) en [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows) bewerkingen. Als u een gegevensset zoekt, gebruikt u de [gegevenssets ophalen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets) bewerking. U kunt een groeps-ID om te werken met een groep voor elk van deze bewerkingen doorgeven. Als u een lijst met een groep-ID, gebruikt de [groepen ophalen](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) bewerking.

Met de volgende bewerkingen kunt u gegevens naar een gegevensset pushen:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Gegevenssets ophalen](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Groepen ophalen](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

U maakt u een gegevensset in Power BI door een JSON-tekenreeks (JavaScript Object Notation) door te geven aan de Power BI-service. Zie [Inleiding tot JSON](http://json.org/) voor meer informatie over JSON.

De JSON-tekenreeks voor een gegevensset heeft de volgende indeling:

**JSON-object voor Power BI-gegevensset**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

U zou bijvoorbeeld onze gegevensset Sales Marketing zoals hieronder wordt weergegeven een JSON-tekenreeks doorgeven. In dit voorbeeld **SalesMarketing** is de naam van de gegevensset en **Product** is de tabelnaam. Na het definiëren van de tabel, moet u het tabelschema definiëren. Voor de gegevensset **SalesMarketing** bevat het tabelschema de volgende kolommen: ProductID, Manufacturer, Category, Segment, Product en IsCompete.

**Voorbeeld van JSON-object voor gegevensset**

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

Voor een Power BI-tabelschema kunt u de volgende gegevenstypen gebruiken.

## <a name="power-bi-table-data-types"></a>Gegevenstypen voor Power BI-tabellen

| **Gegevenstype** | **Beperkingen** |
| --- | --- |
| Int64 |Int64.MaxValue en Int64.MinValue zijn niet toegestaan. |
| Double |Double.MaxValue en Double.MinValue zijn niet toegestaan. NaN wordt niet ondersteund. + Infinity en -Infinity niet ondersteund in sommige functies (bijvoorbeeld, Min, Max). |
| Boolean |Geen |
| Datum/tijd |Tijdens het laden van gegevens, quantize we waarden met breuken voor de dag hele veelvouden van 1/300 seconden (3,33 ms). |
| Tekenreeks |Momenteel kunt maximaal 128 K tekens. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Meer informatie over het pushen van gegevens naar Power BI

Als u gegevens in een gegevensset wilt pushen, raadpleegt u [Stap 1: Een app registreren met Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) in het linkernavigatiepaneel.

[Volgende stap >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Volgende stappen

[Registreren voor Power BI](create-an-azure-active-directory-tenant.md)  
[Inleiding tot JSON](http://json.org/)  
[Overview of Power BI REST API](overview-of-power-bi-rest-api.md) (Overzicht van de REST-API voor Power BI)  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)