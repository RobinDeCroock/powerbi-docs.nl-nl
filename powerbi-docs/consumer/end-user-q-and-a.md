---
title: Q & A voor Power BI-gebruikers
description: Overzicht van de documentatie voor Power BI Q&A-query's in natuurlijke taal.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 05/01/2019
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 35ff71d5956c1c48c304324c121f79addf04cb56
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625116"
---
# <a name="qa-for-power-bi-consumers"></a>Q&A voor Power BI-**consumenten**
## <a name="what-is-qa"></a>Wat is Q&A?
Soms krijgt u het snelst een antwoord uit uw gegevens wanneer u een vraag stelt in natuurlijke taal. Bijvoorbeeld: "Wat was de totale omzet het afgelopen jaar?"

Gebruik Q&A om aan de hand van intuïtieve, natuurlijke taal uw gegevens te verkennen en antwoorden te krijgen in de vorm van diagrammen en grafieken. Q&A verschilt van een zoekmachine. Q&A retourneert alleen resultaten over de gegevens in Power BI.

**Power BI Q&A** ondersteunt alleen het beantwoorden van query's in natuurlijke taal gevraagd, die in het Engels zijn opgesteld. Er is een preview beschikbaar in het Spaans. Deze kan worden ingeschakeld door de Power BI-beheerder.

**Power BI Q&A** is beschikbaar met een Pro- of Premium-licentie. 
>

![in q&a gemaakte treemap](media/end-user-q-and-a/power-bi-qna.png)

Het stellen van de vraag is slechts het begin.  Leef u uit met uw gegevens en verfijn of verbreed uw vraag om betrouwbare nieuwe informatie aan het licht te brengen, in te zoomen op details of uit te zoomen voor een breder perspectief. U zult aangenaam verrast worden door de inzichten die u vergaart en de ontdekkingen die u doet.

De ervaring is volledig interactief... en snel. Dankzij de opslag in het geheugen, kunt u vrijwel onmiddellijk een respons verwachten.

## <a name="where-can-i-use-qa"></a>Waar kan ik Q&A gebruiken?
Vindt u Q & A voor dashboards en rapporten in Power BI-service, en aan de onderkant van het dashboard in Power BI mobiel. Tenzij de ontwerper u machtigingen voor bewerken heeft gegeven, kunt u gegevens verkennen met behulp van Q&A, maar kunt u geen visuals opslaan die met Q&A zijn gemaakt.

![vragenvak](media/end-user-q-and-a/powerbi-qna.png)

## <a name="how-does-qa-know-how-to-answer-questions"></a>Hoe weet Q&A hoe vragen moeten worden beantwoord?
Q&A zoekt naar antwoorden in alle gegevenssets die aan het dashboard zijn gekoppeld. Als een gegevensset een tegel op het dashboard heeft, kijkt Q&A in deze gegevensset voor antwoorden. 

## <a name="how-do-i-start"></a>Hoe kan ik beginnen?
Raak eerst vertrouwd met de inhoud. Kijk eens naar de visuals op het dashboard en in het rapport. Krijg een idee van het type en het bereik van de gegevens die voor u beschikbaar zijn. Ga dan terug naar het dashboard en plaats de cursor in het vragenvak. Hiermee opent u het Q&A-scherm.

![Q&A-scherm](media/end-user-q-and-a/power-bi-qna-screen.png) 

* Als de aslabels en -waarden van de visualisaties 'sales', 'account', 'month' en 'opportunities' bevatten, kunt u vragen stellen zoals: 'Which *account* has the highest *opportunity*, or show *sales* by month as a bar chart.'

* Als u prestatiegegevens van een website in Google Analytics hebt, kunt u Q&A vragen over de tijd die aan een webpagina is besteed, het aantal unieke paginabezoeken en de percentages gebruikersbetrokkenheid. Of als u query's hebt voor demografische gegevens, kunt u vragen stellen over leeftijd en huishoudinkomens per locatie.

Aan de onderkant van het scherm ziet u andere nuttige items. Voor elke gegevensset toont Q&A trefwoorden en soms zelfs enige voorbeeldvragen of voorgestelde vragen. Selecteer hier items die u aan het vraagvak wilt toevoegen. 

Een andere manier waarop Q&A u helpt vragen te stellen is met prompts, automatisch aanvullen en visuele aanwijzingen. 

![Video](media/end-user-q-and-a/qa.gif) 


### <a name="which-visualization-does-qa-use"></a>Welke visualisatie gebruikt Q&A?
Q&A kiest de beste visualisatie op basis van de gegevens die worden weergegeven. Soms worden gegevens in de onderliggende gegevensset(s) gedefinieerd als een bepaald type of een bepaalde categorie waardoor het voor Q&A duidelijker wordt hoe de gegevens moeten worden weergegeven. Als gegevens bijvoorbeeld zijn gedefinieerd als een gegevenstype, ligt het voor de hand ze als een lijndiagram weer te geven. Gegevens die zijn gecategoriseerd als een plaats, zullen eerder als een kaart worden weergegeven.

U kunt ook zelf bij de vraag opgeven welke visualisatie moet worden gebruikt. Het is echter niet altijd mogelijk de gegevens in het door u gevraagde type visualisatie weer te geven. Q&A biedt ook een lijst met werkbare visualtypen aan.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
**Vraag**: Ik zie geen Q&A op dit dashboard.    
**Antwoord 1**: Als u geen vraagvak ziet, controleert u eerst de instellingen. Selecteer hiertoe het tandwielpictogram in de rechterbovenhoek van de Power BI-werkbalk.   
![tandwielpictogram](media/end-user-q-and-a/power-bi-settings.png)

Kies vervolgens **Instellingen** > **Dashboards**. Zorg ervoor dat er een vinkje naast **Zoekvak van Q&A weergeven in dit dashboard** staat.    
![Q&A-instellingen voor dashboard](media/end-user-q-and-a/power-bi-turn-on.png)  


**Antwoord 2**: Soms schakelt de *ontwerper* van het dashboard of de beheerder Q&A uit. Vraag diegene of de functie weer mag worden ingeschakeld.   

**Vraag**: Ik krijg niet de resultaten die ik graag zou zien als ik een vraag typ.    
**Antwoord**: Neem contact op met de *ontwerper* van het dashboard. Er zijn veel dingen die de ontwerper kan doen om de Q&A-resultaten te verbeteren. De ontwerper kan bijvoorbeeld de namen van kolommen in de gegevensset wijzigen in termen die gemakkelijk te begrijpen zijn (`CustomerFirstName` in plaats van `CustFN`). Omdat de ontwerper de gegevensset heel goed kent, kan deze ook nuttige vragen bedenken en deze toevoegen aan het Q&A-canvas.

![aanbevolen vraag gemarkeerd](media/end-user-q-and-a/power-bi-featured-q.png)

## <a name="next-steps"></a>Volgende stappen

