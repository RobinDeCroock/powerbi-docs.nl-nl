---
title: Gegevens naar een gegevensset pushen
description: Gegevens naar een Power BI-gegevensset pushen
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/05/2017
ms.author: asaxton
ms.openlocfilehash: aba135a0a790025f732379ecb07157f1150d999c
ms.sourcegitcommit: 7517c068db806f12bb0b953e9a1bd4249ca12da5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2018
---
# <a name="push-data-into-a-power-bi-dataset"></a>Gegevens naar een Power BI-gegevensset pushen
Met de Power BI API kunt u gegevens pushen naar een Power BI-gegevensset. Stel, u wilt een bestaande zakelijke werkstroom uitbreiden om belangrijke gegevens naar uw gegevensset te pushen. In dit geval wilt u de gegevensset Sales Marketing, die de tabel Product bevat, pushen naar een gegevensset.

Voordat u de gegevens naar een gegevensset gaat pushen, hebt u een Azure Active Directory (Azure AD) en een [Power BI-account](create-an-azure-active-directory-tenant.md) nodig.

## <a name="steps-to-push-data-into-a-dataset"></a>Stappen om gegevens naar een gegevensset te pushen
* Stap 1: [Een app bij Azure AD registreren](walkthrough-push-data-register-app-with-azure-ad.md)
* Stap 2: [Een toegangstoken voor verificatie ophalen](walkthrough-push-data-get-token.md)
* Stap 3: [Een gegevensset maken in Power BI](walkthrough-push-data-create-dataset.md)
* Stap 4: [Een gegevensset ophalen om rijen toe te voegen aan een Power BI-tabel](walkthrough-push-data-get-datasets.md)
* Stap 5: [Rijen toevoegen aan een Power BI-tabel](walkthrough-push-data-add-rows.md)

Het volgende gedeelte bevat een algemene bespreking van Power BI API-bewerkingen die gegevens pushen.

## <a name="power-bi-api-operations-to-push-data"></a>Power BI API-bewerkingen om gegevens te pushen
Met de REST-API voor Power BI kunt u gegevensbronnen pushen naar Power BI. Wanneer een app rijen toevoegt aan een gegevensset, worden de tegels op het dashboard automatisch bijgewerkt met de bijgewerkte gegevens. Als u gegevens wilt pushen, gebruikt u de bewerking [Gegevensset maken](https://msdn.microsoft.com/library/mt203562.aspx), samen met de bewerking [Rijen toevoegen](https://msdn.microsoft.com/library/mt203561.aspx). Als u een gegevensset zoekt, gebruikt u de bewerking [Gegevenssets ophalen](https://msdn.microsoft.com/library/mt203567.aspx). Voor elk van deze bewerkingen kunt u een groeps-id doorgeven als u wilt werken met een groep. Gebruik de bewerking [Groepen ophalen](https://msdn.microsoft.com/library/mt243842.aspx) om een lijst met groeps-id's op te halen.

Met de volgende bewerkingen kunt u gegevens naar een gegevensset pushen:

* [Gegevensset maken](https://msdn.microsoft.com/library/mt203562.aspx)
* [Gegevenssets ophalen](https://msdn.microsoft.com/library/mt203567.aspx)
* [Rijen toevoegen](https://msdn.microsoft.com/library/mt203561.aspx)
* [Groepen ophalen](https://msdn.microsoft.com/library/mt243842.aspx)

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

Voor de voorbeeldgegevensset Sales Marketing moet u dus een JSON-tekenreeks doorgeven zoals in het onderstaande voorbeeld. In dit voorbeeld is **SalesMarketing** de naam van de gegevensset en is **Product** de naam van de tabel. Nadat u de tabel hebt gedefinieerd, kunt u het tabelschema definiëren. Voor de gegevensset **SalesMarketing** heeft het tabelschema deze kolommen: ProductID, Manufacturer, Category, Segment, Product en IsCompete.

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
| Double |Double.MaxValue en Double.MinValue zijn niet toegestaan. NaN wordt niet ondersteund. +Infinity en -Infinity worden niet ondersteunt door sommige functies (zoals Min, Max). |
| Boolean |Geen |
| Datum/tijd |Tijdens het laden van gegevens worden waarden met breuken voor de dag afgerond tot veelvouden van 1/300 seconde (3,33 ms). |
| Tekenreeks |Momenteel zijn maximaal 128.000 tekens toegestaan. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Meer informatie over het pushen van gegevens naar Power BI
Als u gegevens wilt gaan pushen naar een gegevensset, leest u [Stap 1: Een app bij Azure AD registreren](walkthrough-push-data-register-app-with-azure-ad.md) in het navigatievenster links.

[Volgende stap >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Volgende stappen
[Aanmelden voor Power BI](create-an-azure-active-directory-tenant.md)  
[Gegevensset maken](https://msdn.microsoft.com/library/mt203562.aspx)  
[Gegevenssets ophalen](https://msdn.microsoft.com/library/mt203567.aspx)  
[Rijen toevoegen](https://msdn.microsoft.com/library/mt203561.aspx)  
[Groepen ophalen](https://msdn.microsoft.com/library/mt243842.aspx)  
[Inleiding tot JSON](http://json.org/)  
[Overview of Power BI REST API](overview-of-power-bi-rest-api.md) (Overzicht van de REST-API voor Power BI)  
Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
