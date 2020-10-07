---
title: Q&A in Power BI Embedded
description: Power BI Embedded biedt u de mogelijkheid tot het opnemen van Q&A in een toepassing zodat uw gebruikers vragen kunnen stellen in natuurlijke taal.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/20/2017
ms.openlocfilehash: 0106cc9ddb0e82a7b40e362342fce5196ef655c5
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91749271"
---
# <a name="qa-in-power-bi-embedded"></a>Q&A in Power BI Embedded

Power BI Embedded biedt u de mogelijkheid tot het opnemen van Q&A in een toepassing zodat uw gebruikers vragen kunnen stellen in natuurlijke taal en direct antwoord kunnen krijgen in de vorm van visuele elementen zoals diagrammen of grafieken.

![Interactieve Q&A-vraag in een ingesloten frame](media/qanda/embedded-qanda.gif)

Er zijn twee modi voor het insluiten van Q&A (vragen en antwoorden) in uw toepassing: **interactief** en **alleen resultaat**. In de modus **Interactief** kunt u vragen invoeren en deze laten weergeven in het visuele element. Als u een opgeslagen vraag hebt, of een vaste vraag die u wilt weergeven, kunt u de modus **Alleen resultaat** gebruiken door de vraag in te vullen uw ingesloten configuratie.

De JavaScript-code ziet er ongeveer als volgt uit.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Vaste vraag

Als u de **resultaatmodus** hebt gebruikt voor een vaste vraag, kunt u aanvullende vragen invoegen en deze direct laten beantwoorden, waarbij het eerdere resultaat wordt vervangen. Er wordt een nieuw visueel weergegeven dat overeenkomt met de nieuwe vraag.

Een voorbeeld hiervan is het gebruik van een lijst met veelgestelde vragen. De gebruiker kan de vragen doorlopen en deze laten beantwoorden binnen hetzelfde ingesloten deel.

**Codefragment voor het gebruik van JS SDK:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Gebeurtenis weergegeven visueel element

In de **interactieve** modus kan de toepassing telkens bericht ontvangen van een gebeurtenis dat gegevens zijn gewijzigd wanneer het weergegeven visuele element wordt aangepast aan de bijgewerkte invoerquery terwijl deze wordt getypt.

Door te luisteren naar de *visualRendered*-gebeurtenis kunt u vragen opslaan voor later gebruik. 

**Codefragment voor het gebruik van JS SDK:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Token insluiten

Maak een insluittoken op basis van een gegevensset om een Q&A-deel te starten. Zie [Token genereren](/rest/api/power-bi/embedtoken) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

Bekijk het [voorbeeld van het insluiten van JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/) als u overweegt Q&A te gaan insluiten.

Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).