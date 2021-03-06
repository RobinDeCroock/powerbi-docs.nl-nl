---
title: Richtlijnen voor het oplossen van problemen met relaties
description: Richtlijnen voor het oplossen van problemen met modelrelaties.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 6018cf1b26f704efefd5ec9b9fd29e72ad0f3fef
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088230"
---
# <a name="relationship-troubleshooting-guidance"></a>Richtlijnen voor het oplossen van problemen met relaties

Dit artikel is geschreven voor iedereen die gegevensmodellen maakt met Power BI Desktop. Het biedt richtlijnen voor het oplossen van specifieke problemen die u mogelijk ondervindt bij het ontwikkelen van modellen en rapporten.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Controlelijst voor probleemoplossing

Wanneer een rapportvisual is geconfigureerd om velden uit twee (of meer) tabellen te gebruiken, en niet het juiste resultaat (of geen enkel resultaat) bevat, heeft het probleem mogelijk te maken met modelrelaties.

In dit geval is hier een algemene controlelijst die u kunt volgen. U kunt de controlelijst stapsgewijs doorlopen totdat u het probleem (of de problemen) hebt geïdentificeerd.

1. Schakel de visual over naar een tabel of matrix, of open het deelvenster Gegevens weergeven. Het is eenvoudiger om problemen op te lossen wanneer u het queryresultaat voor u hebt
1. Als het queryresultaat leeg is, schakelt u over naar de gegevensweergave, en controleert u of de tabellen zijn geladen met rijen gegevens
1. Schakel over naar de modelweergave. Hier kunt u eenvoudig de relaties bekijken en snel de bijbehorende eigenschappen bepalen
1. Controleer of relaties tussen de tabellen bestaan
1. Controleer of de eigenschappen van de kardinaliteit juist zijn geconfigureerd. De configuratie zou onjuist kunnen zijn als een kolom aan de 'veel'-zijde momenteel unieke waarden bevat en onjuist is geconfigureerd als een kolom aan de 'één'-zijde
1. Controleer of de relaties actief zijn (ononderbroken lijn)
1. Controleer of de filterrichtingen ondersteuning bieden voor doorgeven (pijlkoppen interpreteren)
1. Controleer of de juiste kolommen zijn gerelateerd. Selecteer de relatie, of beweeg de muisaanwijzer over de relatie om de gerelateerde kolommen te zien
1. Controleer of de gerelateerde gegevenstypen voor de kolommen gelijk (of minstens compatibel) zijn. U kunt een tekstkolom relateren aan een kolom met hele getallen, maar via filteren worden er dan geen overeenkomsten gevonden om door te geven
1. Schakel over naar de gegevensweergave en controleer of er overeenkomende waarden zijn in gerelateerde kolommen

## <a name="troubleshooting-guide"></a>Handleiding voor het oplossen van problemen

Hier volgt een lijst met problemen, samen met mogelijke oplossingen.

|Probleem|Mogelijke reden(en)|
|---------|---------|
|In de visual worden geen resultaten weergegeven|- Het model moet nog worden geladen met gegevens<br />- Er bestaan geen gegevens binnen de filtercontext<br />- Beveiliging op rijniveau is afgedwongen<br />- Er worden geen relaties doorgegeven tussen tabellen. _Volg de bovenstaande controlelijst_<br />- Beveiliging op rijniveau is afgedwongen, maar er is geen bidirectionele relatie voor doorgeven ingeschakeld. Raadpleeg [RLS (beveiliging op rijniveau) met Power BI Desktop](../create-reports/desktop-rls.md)|
|In de visual wordt voor elke groepering dezelfde waarde weergegeven |- Er bestaan geen relaties<br />- Er worden geen relaties doorgegeven tussen tabellen. _Volg de bovenstaande controlelijst_|
|In de visual worden resultaten weergegeven, maar deze kloppen niet|- Visual is onjuist geconfigureerd<br />- Metingslogica is onjuist<br />- Modelgegevens moeten worden vernieuwd<br />- Brongegevens zijn onjuist<br />- Relatiekolommen zijn onjuist gerelateerd (bijvoorbeeld de kolom **ProductID** is toegewezen aan **CustomerID**)<br />- Het is een relatie tussen twee DirectQuery-tabel, en de kolom aan de 'één'-zijde van een relatie bevat dubbele waarden|
|Er worden lege groeperingen of slicer-/filteritems weergegeven, en de bronkolommen bevatten geen lege waarden|- Het is een reguliere relatie en een kolom aan de 'veel'-zijde bevat waarden die niet zijn opgeslagen in een kolom aan de 'één'-zijde. Raadpleeg [Modelrelaties in Power BI Desktop (reguliere relaties)](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- Het is een reguliere één-op-één-relatie en gerelateerde kolommen bevatten lege waarden. Raadpleeg [Modelrelaties in Power BI Desktop (reguliere relaties)](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- Een niet-actieve relatiekolom aan de 'veel'-zijde bevat lege waarden, of waarden die niet zijn opgeslagen aan de 'één'-zijde|
|Er ontbreken gegevens in de visual|- Er zijn onjuiste/onverwachte filters toegepast<br />- Beveiliging op rijniveau is afgedwongen<br />- Het is een beperkte relatie en gerelateerde kolommen bevatten lege waarden, of er zijn problemen met de gegevensintegriteit. Raadpleeg [Modelrelaties in Power BI Desktop (beperkte relaties)](../transform-model/desktop-relationships-understand.md#limited-relationships)<br />- Het is een relatie tussen twee DirectQuery-tabellen. De relatie is geconfigureerd om [referentiële integriteit aan te nemen](../transform-model/desktop-relationships-understand.md#assume-referential-integrity), maar er zijn problemen met de gegevensintegriteit (niet overeenkomende waarden in gerelateerde kolommen)|
|Beveiliging op rijniveau wordt niet juist afgedwongen|- Er worden geen relaties doorgegeven tussen tabellen. _Volg de bovenstaande controlelijst_<br />- Beveiliging op rijniveau is afgedwongen, maar er is geen bidirectionele relatie voor doorgeven ingeschakeld. Raadpleeg [RLS (beveiliging op rijniveau) met Power BI Desktop](../create-reports/desktop-rls.md)|
|||

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Modelrelaties in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
