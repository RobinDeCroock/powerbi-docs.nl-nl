---
title: Eigenschappen van Power BI-gegevensset
description: Meer informatie over de eigenschappen van Power BI-gegevensset-API's
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9d0ab5bcffe3b0267b3e07a684c2c7c9bd0fd316
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "74265828"
---
# <a name="dataset-properties"></a>Eigenschappen van gegevensset

Met de huidige v1 van de gegevenssets-API kunt u alleen een gegevensset maken met een naam en een verzameling tabellen. Elke tabel kan een naam en een verzameling kolommen hebben. Elke kolom heeft een naam en een gegevenstype. Deze eigenschappen worden verder uitgebreid, met name met ondersteuning voor metingen en relaties tussen tabellen. De volledige lijst met ondersteunde eigenschappen voor deze versie is als volgt:

> [!IMPORTANT]
> Deze lijst is beschikbaar op de pagina [Datasets Operation Groups](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Gegevensset

Naam  |Type  |Beschrijving  |Alleen-lezen  |Vereist
---------|---------|---------|---------|---------
id     |  GUID       | Systeembrede unieke id voor de gegevensset.        | Waar        | Onwaar        
name     | Tekenreeks        | Door de gebruiker gedefinieerde naam van de gegevensset.        | Onwaar        | Waar        
tabellen     | Tabel[]        | Een verzameling tabellen.        |  Onwaar       | Onwaar        
relaties     | Relatie[]        | Verzameling van relaties tussen tabellen.        | Onwaar        |  Onwaar  
defaultMode     | Tekenreeks        | Hiermee bepaalt u of de gegevensset wordt gepusht, gestreamd of beide, met behulp van de waarden Push en Streaming.         | Onwaar        |  Onwaar

## <a name="table"></a>Tabel

Naam  |Type  |Beschrijving  |Alleen-lezen  |Vereist
---------|---------|---------|---------|---------
name     | Tekenreeks        |  Door de gebruiker gedefinieerde naam van de tabel. Deze wordt ook gebruikt als de id van de tabel.       | Onwaar        |  Waar       
kolommen     |  kolom[]       |  Een verzameling kolommen.       | Onwaar        |  Waar       
metingen     | meting[]        |  Een verzameling metingen.       | Onwaar        |  Onwaar       
isHidden     | Boolean        | Indien waar wordt de tabel verborgen in clienthulpprogramma's.        | Onwaar        | Onwaar        

## <a name="column"></a>Kolom

Naam  |Type  |Beschrijving  |Alleen-lezen  |Vereist
---------|---------|---------|---------|---------
name     |  Tekenreeks        | Door de gebruiker gedefinieerde naam van de kolom.        |  Onwaar       | Waar       
dataType     |  Tekenreeks       |  Ondersteunde [EDM-gegevenstypen](https://msdn.microsoft.com/library/ee382832.aspx) en -beperkingen. Zie [Beperkingen van gegevenstype](#DataTypeRestrictions).      |  Onwaar       | Waar        
formatString     | Tekenreeks        | Een tekenreeks die beschrijft hoe de waarde moet worden opgemaakt wanneer deze wordt weergegeven. Zie [Inhoud van FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx) voor meer informatie over het opmaken van tekenreeksen.      | Onwaar        | Onwaar        
sortByColumn    | Tekenreeks        |   De naam van de verbindingsreeks van een kolom in dezelfde tabel die moet worden gebruikt om de huidige kolom te rangschikken.     | Onwaar        | Onwaar       
dataCategory     | Tekenreeks        |  De waarde van de verbindingsreeks die moet worden gebruikt voor de gegevenscategorie die de gegevens in deze kolom beschrijft. Sommige algemene waarden zijn onder meer: Adres, plaats, continent, land, afbeelding, afbeeldings-URL, breedtegraad, lengtegraad, organisatie, plaats, postcode, staat of provincie, Web-URL       |  Onwaar       | Onwaar        
isHidden    |  Boolean       |  De eigenschap waarmee wordt aangegeven of de kolom wordt verborgen. De standaardinstelling is onwaar.       | Onwaar        | Onwaar        
summarizeBy     | Tekenreeks        |  Standaardaggregatiemethode voor de kolom. Mogelijke waarden zijn: standaard, geen, som, min, max, aantal, gemiddelde, uniek aantal     |  Onwaar       | Onwaar

## <a name="measure"></a>Meting

Naam  |Type  |Beschrijving  |Alleen-lezen  |Vereist
---------|---------|---------|---------|---------
name     | Tekenreeks        |  Door de gebruiker gedefinieerde naam van de meting.       |  Onwaar       | Waar        
expressie     | Tekenreeks        | Een geldige DAX-expressie.        | Onwaar        |  Waar       
formatString     | Tekenreeks        |  Een tekenreeks die beschrijft hoe de waarde moet worden opgemaakt wanneer deze wordt weergegeven. Zie [Inhoud van FORMAT_STRING](https://msdn.microsoft.com/library/ms146084.aspx) voor meer informatie over het opmaken van tekenreeksen.       | Onwaar        | Onwaar        
isHidden     | Tekenreeks        |  Indien waar wordt de tabel verborgen in clienthulpprogramma's.       |  Onwaar       | Onwaar       

## <a name="relationship"></a>Relatie

Naam  |Type  |Beschrijving  |Alleen-lezen  |Vereist 
---------|---------|---------|---------|---------
name     | Tekenreeks        | Door de gebruiker gedefinieerde naam van de relatie. Deze wordt ook gebruikt als de id van de relatie.        | Onwaar       | Waar        
crossFilteringBehavior     | Tekenreeks        |    De filterrichting van de relatie: OneDirection (default), BothDirections, Automatic       | Onwaar        | Onwaar        
fromTable     | Tekenreeks        | Naam van de refererende-sleuteltabel.        | Onwaar        | Waar         
fromColumn    | Tekenreeks        | Naam van de refererende-sleutelkolom.        | Onwaar        | Waar         
toTable    | Tekenreeks        | Naam van de primaire-sleuteltabel.        | Onwaar        | Waar         
toColumn     | Tekenreeks        | Naam van de primaire-sleutelkolom.        | Onwaar        | Waar        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Beperkingen van gegevenstype (van toepassing op de eigenschap dataType)

Gegevenstype  |Beperkingen  
---------|---------
Int64     |   Int64.MaxValue en Int64.MinValue zijn niet toegestaan.      
Double     |  Double.MaxValue en Double.MinValue zijn niet toegestaan. NaN wordt niet ondersteund. +Infinity en -Infinity worden niet ondersteunt door sommige functies (zoals Min, Max).       
Boolean     |   Waar of onwaar.
Datum/tijd    |   Tijdens het laden van gegevens worden waarden met breuken voor de dag afgerond tot veelvouden van 1/300 seconde (3,33 ms).      
Tekenreeks     |  Momenteel maximaal 4000 tekens per tekenreekswaarde.
Decimaal|precisie = 28, schaal = 4

## <a name="example"></a>Voorbeeld
De volgende voorbeeldcode bevat een aantal van deze eigenschappen:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```