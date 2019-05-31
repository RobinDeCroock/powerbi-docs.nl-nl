---
title: Cortana gebruiken om te zoeken en weergeven van rapporten en dashboards - Power BI
description: Gebruik Cortana met Power BI om antwoorden uit uw gegevens te halen. Werkt momenteel alleen met rapporten en dashboards.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 6d53ddcfc4121e8937810bd6f734f91cd7a9fa39
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375291"
---
# <a name="find-and-view-your-power-bi-data-with-cortana-for-power-bi"></a>Zoeken en weergeven van uw Power BI-gegevens met Cortana voor Power BI
Gebruik Cortana op uw Windows 10-apparaten om direct antwoord te krijgen op uw belangrijke zakelijke vragen. Door de integratie met Power BI kan Cortana belangrijke gegevens rechtstreeks ophalen uit Power BI-dashboards en -rapporten. U hebt alleen maar Windows 10, versie november 2015 of later, Cortana, Power BI en toegang tot minimaal één gegevensset nodig.

> [!IMPORTANT]
> Integratie van Cortana wordt in Power BI afgeschaft. Vanaf 11 juni, werkt Cortana niet meer voor alle dashboards en rapporten.

![Zoekveld van Cortana](media/service-cortana-intro/power-bi-cortana-searchbox.png)

## <a name="preview-the-new-cortana-dashboard-search-experience-for-windows-10"></a>Bekijk een voorbeeld van de nieuwe Cortana-zoekervaring voor *dashboards* voor Windows 10
U kunt nu al een tijdje [met Cortana gebruiken bepaalde typen rapportpagina's ophalen](service-cortana-answer-cards.md). Er is nu een **nieuwe ervaring** toegevoegd: de mogelijkheid om ook dashboards op te halen. Uitproberen en [Stuur ons feedback op Power BI ideeën](https://ideas.powerbi.com/forums/265200-power-bi). De *nieuwe ervaring* wordt op termijn uitgebreid zodat u ook met Cortana kunt zoeken in rapporten.  Een van de belangrijkste voordelen van de nieuwe ervaring is dat u er niets speciaals voor hoeft te doen: u hoeft Cortana niet in te schakelen of Windows 10 te configureren. Het werkt gewoon.

> [!NOTE]
> Als het niet 'gewoon werkt', raadpleegt u het [artikel Probleemoplossing](service-cortana-troubleshoot.md) voor hulp.
> 
> 

De onderliggende technologie maakt gebruikt van [Microsoft Azure Search Service](https://docs.microsoft.com/azure/search/). Deze zoekservice biedt extra mogelijkheden, zoals slimme classificatie, foutcorrectie en automatisch aanvullen.

Beide Cortana-ervaringen kunnen naast elkaar bestaan.

## <a name="cortana-for-power-bi-documentation"></a>Cortana voor Power BI-documentatie
Vier documenten begeleiden u bij het instellen en gebruiken van Cortana voor Power BI.

**Artikel 1** (dit artikel): informatie over hoe Cortana en Power BI samenwerken

**Artikel 2**: [Zoeken naar Power BI-rapporten: de integratie van Cortana - Power BI - Windows inschakelen](service-cortana-enable.md)

**Artikel 3**: [Zoeken in Power BI-rapporten: speciale maken *Cortana-antwoordkaarten*](service-cortana-answer-cards.md)

**Artikel 4**: [Problemen oplossen](service-cortana-troubleshoot.md)

## <a name="how-cortana-and-power-bi-work-together"></a>Hoe Cortana en Power BI samenwerken
Wanneer u met Cortana een vraag stelt, kan Cortana in Power BI zoeken naar antwoorden. In Power BI kan Cortana uitgebreide gegevensgestuurde antwoorden vinden in Power BI-rapporten (die een speciaal type rapportpagina bevatten genaamd een *Cortana-antwoordkaart*) en in Power BI-dashboards.

Als Cortana een overeenkomst vindt, geeft het de naam van het dashboard of de rapportpagina weer in uw Cortana-scherm. Het dashboard of de rapportpagina kan worden geopend in Power BI. Rapportpagina's kunnen ook direct in Cortana worden bestudeerd: ze zijn interactief.

![interactieve rapportpagina wordt weergegeven in Cortana](media/service-cortana-intro/power-bi-report-cortana-s.png)

### <a name="cortana-and-dashboards-the-new-experience"></a>Cortana en dashboards (de *nieuwe ervaring*)
Cortana vindt antwoorden in de dashboards die van u zijn en in dashboards die met u zijn gedeeld. Stel Cortana vragen met behulp van titels, trefwoorden, namen van eigenaren, werkruimtenamen, app-namen en meer.

Uw vraag moet uit ten minste twee woorden bestaan aan de hand waarvan Cortana een antwoord zoekt. Dus als u in een dashboard met een naam van één woord (Marketing) zoekt, voegt u het woord 'toon' of 'Power BI' of de naam van de eigenaar toe aan uw vraag, zoals in 'toon Marketing weer' of 'michele hart voorbeeld'. 

Als uw dashboardtitel uit meer dan één woord bestaat, retourneert Cortana dat dashboard alleen als uw zoekopdracht overeenkomt met ten minste twee van de woorden of een van de woorden plus de naam van de eigenaar. Voor een dashboard met de naam 'Voorbeeld van klantwinstgevendheid': 

* 'Toon klant' *niet* resultaat met een Power BI-dashboard.   
* "uitingen zoals 'Toon klantwinstgevendheid ', 'klant p', 'klant s', 'winstgevendheid voorbeeld', 'michele hart voorbeeld', 'Toon klantwinstgevendheid voorbeeld' en 'Toon klant p' *doen* een Power BI-resultaat te retourneren.
* Het woord 'powerbi' toevoegt, telt als een van de twee vereiste woorden, dit het geval is 'Power BI voorbeeld' *heeft* een Power BI-resultaat te retourneren. 
  
    ![Cortana-zoeken met ten minste twee woorden](media/service-cortana-intro/power-bi-cortana-2-words.png)

### <a name="cortana-and-reports"></a>Cortana en rapporten
 Cortana kan antwoorden vinden in rapporten met [pagina's die speciaal zijn ontworpen voor weergave door Cortana](service-cortana-answer-cards.md). Stel eenvoudig vragen door de titel of trefwoorden uit een van deze speciale rapportpagina's te gebruiken.  

De onderliggende technologie voor het gebruik van rapporten [Power BI Q & A](power-bi-tutorial-q-and-a.md).

Wanneer u een vraag stelt in Cortana, beantwoordt Power BI die vraag aan de hand van rapportpagina's die speciaal zijn ontworpen voor Cortana. Mogelijke antwoorden worden door Cortana direct bepaald aan de hand van de Cortana-*antwoordkaarten* die al zijn gemaakt in Power BI.  Als u een antwoord verder wilt bestuderen, opent u een resultaat in Power BI.

> [!NOTE]
> Voordat Cortana naar antwoorden kan zoeken in uw Power BI-rapporten, [schakelt u deze functie in met de Power BI-service en stelt u Windows in om te communiceren met Power BI](service-cortana-enable.md).  
> 
> 

## <a name="using-cortana-to-get-answers-from-power-bi"></a>Met Cortana antwoorden krijgen vanuit Power BI
1. Begin in Cortana. U kunt op veel verschillende manieren Cortana *openen*: Selecteer het Cortana-pictogram in de taakbalk (hieronder afgebeeld), gebruik spraakopdrachten of tik op het zoekpictogram op uw mobiele Windows-apparaat.
   
     ![](media/service-cortana-intro/power-bi-cortana-searchbox.png)
2. Als Cortana gereed is, typt of spreekt u uw vraag op de zoekbalk van Cortana. Cortana geeft de beschikbare resultaten weer. Als er een Power BI-dashboard is dat overeenkomt met de vraag, wordt dit weergegeven onder **Beste match** of **Power BI**.
   
     ![Zoeken met Cortana vindt Power BI-dashboard](media/service-cortana-intro/power-bi-cortana-search-hr.png "Cortana vindt een Power BI-dashboard")
   
   > [!NOTE]
   > Op dit moment wordt alleen Engels ondersteund.
   > 
   > 
3. Selecteer het dashboard om dit te openen in Cortana.

    ![Het Power BI-dashboard selecteren](media/service-cortana-intro/power-bi-cortana-dashboard.png "Het Power BI-dashboard selecteren")

    U kunt de indeling wijzigen door [de *telefoonweergave* van het dashboard](service-create-dashboard-mobile-phone-view.md) te wijzigen. 

1. Met Cortana hebt u ook de opties om het dashboard in de Power BI-service of de mobiele Power BI-app te openen. Open het dashboard in de Power BI-service door **Openen op het web** te selecteren. 
   
   ![Het dashboard openen vanuit Cortana](media/service-cortana-intro/power-bi-dashboard-opens.png "Het dashboard openen vanuit Cortana")   
4. We gebruiken Cortana nu om een rapport te zoeken. We moeten iets weten uit een [rapport dat een pagina heeft met een Cortana-antwoordkaart ](service-cortana-answer-cards.md). In dit voorbeeld heeft een rapport met de naam 'Cortana-nieuwe-winkels' een Cortana-antwoordkaartpagina met de naam 'cortana winkels'.  
   
     Typ of spreek uw vraag in de zoekbalk van Cortana. Cortana geeft de beschikbare resultaten weer. Als er een Power BI-rapportpagina is die overeenkomt met de vraag, wordt deze weergegeven onder **Beste match** of **Power BI**. En in dit voorbeeld worden het .pbix-bestand (met de back-up) die ik heb gebruikt om de antwoordkaart te maken, ook weergegeven -- onder **Documenten**.
   
     ![Zoeken naar een rapport](media/service-cortana-intro/power-bi-cortana-search3-m.png "zoeken naar een rapport") 
5. Selecteer de rapportpagina **Cortana winkels** om deze weer te geven in het Cortana-venster.
   
    ![rapportpagina wordt geopend in Cortana](media/service-cortana-intro/power-bi-report-cortana-opens.png "rapportpagina wordt geopend in Cortana")   
   
    Vergeet niet dat een *antwoordkaart* een speciaal type Power BI-rapportpagina is die is gemaakt door de eigenaar van een gegevensset.  Zie [Een Cortana-antwoordkaart maken](service-cortana-answer-cards.md) voor meer informatie.
6. Maar dat is niet alles. Werk met de visualisaties op de antwoordkaart zoals u dat ook in Power BI zou doen.
   
   * Selecteer bijvoorbeeld een element op één visualisatie om kruislings te filteren en markeer de andere visualisaties op de antwoordkaart.
     
     ![](media/service-cortana-intro/power-bi-cortana-filtered-new.png)
   * Of gebruik natuurlijke taal om de resultaten te filteren.  Vraag bijvoorbeeld 'Cortana winkels voor Lindseys' en u ziet dat de kaart wordt gefilterd zodat alleen de gegevens voor de keten Lindseys worden weergegeven.
     
     ![kruislings filteren in Cortana](media/service-cortana-intro/power-bi-cortana-filtered-2.png "kruislings filteren in Cortana")
7. Ga verder met verkennen. Schuif omlaag in het Cortana-venster en selecteer **Openen in Power BI**.
   
     ![](media/service-cortana-intro/power-bi-cortana-open-new.png)
8. De rapportpagina wordt geopend in Power BI.    
     ![Het rapport openen vanuit Cortana](media/service-cortana-intro/power-bi-cortana-open2.png "Cortana-antwoordkaart wordt geopend in Cortana zoeken")

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
* Cortana heeft geen toegang tot Cortana-kaarten die nog niet is [ingeschakeld voor Power BI](service-cortana-enable.md).
* Lukt het niet om Cortana samen met Power BI te gebruiken?  Probeer de [probleemoplosser van Cortana](service-cortana-troubleshoot.md).
* Cortana voor Power BI is momenteel alleen beschikbaar in het Engels.
* Cortana voor Power BI is alleen beschikbaar op mobiele Windows-apparaten.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/).
Feedback? [Feedback verzenden naar Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi).

## <a name="next-steps"></a>Volgende stappen
[De integratie van Cortana - Power BI - Windows voor rapporten inschakelen](service-cortana-enable.md)

