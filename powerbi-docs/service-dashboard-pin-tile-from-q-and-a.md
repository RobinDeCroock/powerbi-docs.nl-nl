---
title: Een tegel vastmaken aan een dashboard vanuit Q&A
description: Documentatie over hoe u vanuit het vak met Q&A-vragen een tegel vastmaakt aan een Power BI-dashboard
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 77be727de3cda1d3b6fd5c34b6e572b1d505fc54
ms.sourcegitcommit: 313a5a6a01c09038a6152d681103accbd2faf437
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/20/2020
ms.locfileid: "76282009"
---
# <a name="pin-a-tile-to-a-dashboard-from-qa"></a>Een tegel vastmaken aan een dashboard vanuit Q&A
## <a name="how-to-pin-a-tile-from-qa"></a>Een tegel vastmaken vanuit Q&A
Q&A is het ad hoc rapportagehulpmiddel van Power BI. Hebt u een bepaald inzicht nodig? Stel een vraag over uw gegevens en krijg antwoord in de vorm van een visualisatie.

In deze instructies gaan we Power BI-service (app.powerbi.com) gebruiken om een dashboard te openen, een vraag stellen in natuurlijke taal voor het maken van een visualisatie en deze visualisatie aan een dashboard vastmaken. Dashboards zijn niet beschikbaar in Power BI Desktop. Zie [Overzicht van de Q&A-functie in Power BI](consumer/end-user-q-and-a.md) voor meer informatie over het gebruik van Q&A met andere Power BI-hulpprogramma's en -inhoud. 

Als u wilt volgen, opent u het [dashboard Voorbeeld van een retailanalyse](sample-retail-analysis.md).


1. Open een [dashboard](consumer/end-user-dashboards.md) waarop ten minste één tegel is vastgemaakt vanuit een rapport. Wanneer u een vraag stelt, zoekt Power BI het antwoord op in elke gegevensset waaraan een tegel is vastgemaakt in dat dashboard.  Zie [Gegevens ophalen](service-get-data.md) voor meer informatie.
2. Typ in het vak Vraag aan de bovenkant van het dashboard wat u wilt weten over uw gegevens.  
   ![Q&A-vragenvak](media/service-dashboard-pin-tile-from-q-and-a/power-bi-question-box.png)
3. Als u bijvoorbeeld typt 'Omzet afgelopen jaar per maand en gebied'...  
   ![Een vraag typen](media/service-dashboard-pin-tile-from-q-and-a/power-bi-type-q-and-a.png)

   geeft het vak Vraag u suggesties.
4. Als u de grafiek als een tegel aan uw dashboard wilt toevoegen, selecteert u de speld ![](media/service-dashboard-pin-tile-from-q-and-a/pbi_pintile.png) in de rechterbovenhoek van het canvas. Als het dashboard met u is gedeeld, kunt u geen visualisaties vastmaken.

5. Maak de tegel vast aan een bestaand dashboard of aan een nieuw dashboard.

   ![Dialoogvenster Aan dashboard vastmaken](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin-to-dashboard.png)

   * Bestaand dashboard: selecteer de naam van het dashboard in de vervolgkeuzelijst. Uw keuzes zijn beperkt tot alleen de dashboards in de huidige werkruimte.
   * Nieuw dashboard: typ de naam van het nieuwe dashboard en het wordt toegevoegd aan uw huidige werkruimte.

6. Selecteer **Vastmaken**.

   Een bericht (rechts bovenin) laat u weten dat de visualisatie als tegel aan uw dashboard is toegevoegd.  

   ![Aan dashboard vastgemaakt](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pin.png)
7. Selecteer **Naar dashboard gaan** om de nieuwe tegel te zien. Daar kunt u de tegel [een andere naam geven, vergroten of verkleinen, er een hyperlink aan toevoegen, de tegel verplaatsen en meer](service-dashboard-edit-tile.md) op uw dashboard.

   ![Dashboard met tegels](media/service-dashboard-pin-tile-from-q-and-a/power-bi-pinned.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
* Wanneer u begint met het typen van een vraag, zoekt Q&A direct naar het beste antwoord in alle gegevenssets die zijn gekoppeld aan het huidige dashboard.  Het 'huidige dashboard' is het dashboard dat in het bovenste navigatievenster staat vermeld. Deze vraag wordt bijvoorbeeld gesteld in het dashboard **Voorbeeld van een retailanalyse** dat deel uitmaakt van de werkruimte **mihart**.

  ![Breadcrumbs](media/service-dashboard-pin-tile-from-q-and-a/power-bi-navbar.png)
* **Hoe weet Q&A welke gegevenssets moeten worden gebruikt**?  Q&A heeft toegang tot alle gegevenssets waarvoor ten minste een visualisatie is vastgemaakt aan dat dashboard.

* **Is het vragenvak niet zichtbaar**? Neem contact op met uw Power BI-beheerder. De beheerder heeft de mogelijkheid om Q&A uit te schakelen.


## <a name="next-steps"></a>Volgende stappen
[De naam wijzigen, vergroten of verkleinen, een hyperlink toevoegen, de positie van de tegel wijzigen en meer](service-dashboard-edit-tile.md)    
[Een dashboardtegel weergeven in de focusmodus](consumer/end-user-focus.md)     
Terug naar [Q&A in Power BI](consumer/end-user-q-and-a.md)  
Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
