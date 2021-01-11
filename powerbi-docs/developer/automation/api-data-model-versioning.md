---
title: Versiebeheer van Power BI-gegevensmodellen in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: Gegevensmodel extern weergegeven door een OData-service. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 0c645774f7af1a8575ca3c755a74fd65b652031a
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887702"
---
# <a name="data-model-versioning"></a>Versiebeheer gegevensmodel

Het gegevensmodel dat extern is weergegeven door een OData-service, zoals het Power BI-gegevensmodel, definieert een contract tussen de OData-service en zijn clients. Services mogen hun model alleen zo extern weergeven dat bestaande clients niet worden onderbroken. Wijzigingen die fouten veroorzaken, zoals eigenschappen die worden verwijderd of het type van bestaande eigenschappen wijzigen, vereisen dat een nieuwe serviceversie wordt geleverd op een ander basis-URL voor het nieuwe model.  
  
De volgende toevoegingen van gegevensmodellen worden veilig geacht en vereisen niet dat services hun toegangspunt bijwerken.  
  
* Als er een eigenschap wordt toegevoegd waarbij een null-waarde is toegestaan of die een standaardwaarde heeft. Als deze dezelfde naam heeft als een bestaande dynamische eigenschap, moet deze van hetzelfde type (of basistype) zijn als de bestaande dynamische eigenschap  
* Als er een navigatie-eigenschap wordt toegevoegd waarbij een null-waarde is toegestaan of die voor een verzameling waardevol is. Als deze dezelfde naam heeft als een bestaande dynamische navigatie-eigenschap, moet deze van hetzelfde type (of basistype) zijn als de bestaande dynamische navigatie-eigenschap  
* Een nieuw entiteitstype toevoegen aan het model  
* Een nieuw complextype toevoegen aan het model  
* Een nieuwe entiteitsset toevoegen  
* Een nieuwe singleton toevoegen  
* Een actie of functie toevoegen of een actie of functie importeren
* Een actieparameter toevoegen waarbij een null-waarde is toegestaan  
* Een typedefinitie of -inventarisatie toevoegen  
* Een annotatie toevoegen aan een modelelement die niet hoeft te worden begrepen door de client voor correcte interactie met de service  
  
Clients **MOETEN** _ worden voorbereid op services die dergelijke incrementele wijzigingen aanbrengen in het model. In het bijzonder moeten clients erop worden voorbereid eigenschappen en afgeleide typen te ontvangen die eerder niet werden gedefinieerd door de service.  
  
Services _ *_MOGEN NIET_** hun gegevensmodel afhankelijk van de geverifieerde gebruiker wijzigen. Als het gegevensmodel afhankelijk is van een gebruiker of gebruikersgroep, moeten, wanneer het volledig model wordt vergeleken met het model dat zichtbaar is voor gebruikers met beperkte machtigingen, alle wijzigingen veilige wijzigingen zijn, zoals is gedefinieerd in deze sectie.  
  
Voor meer informatie over OData-gegevensmodelstandaarden raadpleegt u [OData Version 4.0 Part 1: Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).  
  
## <a name="see-also"></a>Zie ook
[Overview of Power BI REST API](/rest/api/power-bi/) (Overzicht van de REST-API voor Power BI)