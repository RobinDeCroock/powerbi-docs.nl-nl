---
title: Ontwikkelen met de REST API's voor Power BI Report Server
description: De REST API biedt toegang op programmeerniveau tot de objecten in een Power BI Report Server-catalogus.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 8f35b7a3c19751b4537a49fa8cb30f4347f080ed
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770763"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Ontwikkelen met de REST API's voor Power BI Report Server

Power BI Report Server-ondersteuning voor REST API’s (Representational State Transfer). De REST API's zijn service-eindpunten die ondersteuning bieden voor een set HTTP-bewerkingen (methoden). Deze bewerkingen bieden de mogelijkheid om resources binnen een rapportserver te maken, op te halen, bij te werken of te verwijderen.

De REST API biedt toegang op programmeerniveau tot de objecten in een Power BI Report Server-catalogus. Voorbeelden van objecten zijn mappen, rapporten, KPI's, gegevensbronnen, gegevenssets, vernieuwingsplannen, abonnementen en meer. Met behulp van de REST API kunt u bijvoorbeeld door de maphiërarchie navigeren, de inhoud van een map ontdekken of een rapportdefinitie downloaden. U kunt ook objecten maken, bijwerken en verwijderen. Voorbeelden van het werken met objecten zijn een rapport uploaden, een plan vernieuwen, een map verwijderen, enzovoort.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Onderdelen van een REST API-aanvraag/antwoord

Een combinatie van REST API-aanvraag/antwoord kan worden opgesplitst in vijf onderdelen:

* De **Aanvraag-URI** die bestaat uit: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Hoewel de aanvraag-URI is opgenomen in de berichtkop van de aanvraag, wordt deze hier afzonderlijk aangeroepen omdat u deze voor de meeste talen of frameworks afzonderlijk moet doorgeven vanuit het aanvraagbericht.
  
  * URI-schema: Geeft het protocol aan dat wordt gebruikt voor het verzenden van de aanvraag. Bijvoorbeeld `http` of `https`.
  * URI-host: Geeft de domeinnaam of het IP-adres op van de server op waarop het REST-service-eindpunt wordt gehost, zoals `myserver.contoso.com`.
  * Resourcepad: Geeft de resource of resourceverzameling op, die verschillende segmenten kan bevatten die in de service worden gebruikt om de selectie van deze resources te bepalen. Bijvoorbeeld: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` kan worden gebruikt om de opgegeven eigenschappen voor CatalogItem op te halen.
  * Querytekenreeks (optioneel): Biedt extra eenvoudige parameters, zoals de API-versie of criteria voor resourceselectie.
* Berichtkopvelden voor de HTTP-aanvraag:
  
  * Een vereiste [HTTP-methode](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (ook wel een bewerking genoemd), die wordt gebruikt om de service te laten weten welk type bewerking u aanvraagt. Reporting Services REST API’s bieden ondersteuning voor de methoden DELETE, GET, HEAD, PUT, POST en PATCH.
  * Optionele extra kopvelden, zoals vereist voor de opgegeven URI en HTTP-methode.
* Optionele **berichttekstvelden voor de HTTP-aanvraag** ter ondersteuning van de URI en HTTP-bewerking. POST-bewerkingen bevatten bijvoorbeeld met MIME gecodeerde objecten die worden doorgevoerd als complexe parameters. Voor POST- of PUT-bewerkingen moet ook het MIME-coderingstype voor de berichttekst worden opgegeven in de `Content-type`-aanvraagkop. Voor sommige services moet u een specifiek MIME-type gebruiken, zoals `application/json`.
* **Berichtkopvelden voor het HTTP-antwoord**:
  
  * Een [HTTP-statuscode](http://www.w3.org/Protocols/HTTP/HTRESP.html), die ligt tussen 2xx-succescodes tot 4xx- of 5xx-foutcodes. Er kan ook een servicegedefinieerde statuscode worden geretourneerd, zoals aangegeven in de API-documentatie.
  * Optionele extra kopvelden, zoals vereist ter ondersteuning van het antwoord op de aanvraag, zoals een `Content-type`-antwoordkop.
* Optionele **berichttekstvelden voor het HTTP-antwoord**:
  
  * Met MIME gecodeerde antwoordobjecten worden geretourneerd in de berichttekst van het HTTP-antwoord, zoals een reactie via een GET-methode waarmee gegevens worden geretourneerd. Normaal gesproken worden deze objecten geretourneerd in een gestructureerde indeling (bijvoorbeeld JSON of XML), zoals aangegeven in de `Content-type`-antwoordkop.

## <a name="api-documentation"></a>API-documentatie

Een moderne REST API vraagt om moderne API-documentatie. De REST API is gebouwd op de OpenAPI-specificatie (ook wel de Swagger-specificatie genoemd) en documentatie is beschikbaar op [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Naast het bieden van documentatie over de API, helpt SwaggerHub ook bij het genereren van een clientbibliotheek in de taal naar keuze: JavaScript, TypeScript, C#, Java, Python, Ruby en meer.

## <a name="testing-api-calls"></a>API-aanroepen testen

Een hulpprogramma voor het testen van HTTP-aanvraag-/antwoordberichten is [Fiddler](http://www.telerik.com/fiddler). Fiddler is een gratis proxy voor webfoutopsporing waarmee uw REST-aanvragen kunnen worden onderschept, zodat u eenvoudig een diagnose kunt uitvoeren voor de HTTP-aanvraag-/antwoordberichten.

## <a name="next-steps"></a>Volgende stappen

Bekijk de beschikbare API's op [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Voorbeelden zijn beschikbaar op [GitHub](https://github.com/Microsoft/Reporting-Services). Het voorbeeld omvat een HTML5-app die is gebouwd op TypeScript, React en webpack, evenals een PowerShell-voorbeeld.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)