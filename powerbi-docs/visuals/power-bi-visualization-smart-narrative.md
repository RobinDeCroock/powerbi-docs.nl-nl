---
title: Zelfstudie over slimme verhalen
description: 'Zelfstudie: Slimme verhalen maken in Power BI'
author: aphilip94
ms.reviewer: aphilip94
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 09/14/2020
ms.author: anphil
LocalizationGroup: Visualizations
ms.openlocfilehash: aef49d1528611a48eae21459f516bf3740987289
ms.sourcegitcommit: ff981839e805f523748b7e71474acccf7bdcb04f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91020679"
---
# <a name="create-smart-narratives-preview"></a>Slimme verhalen maken (preview)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Met de visualisatie van slimme verhalen kunt u snel visuals en rapporten samenvatten door relevante, kant-en-klare inzichten te bieden die kunnen worden aangepast.

![Slimme verhalen](media/power-bi-visualization-smart-narratives/1.png)

Met deze functie kunnen auteurs verhalen aan hun rapport toevoegen om belangrijke punten te benadrukken, trends aan te wijzen of de taal voor een specifieke doelgroep te bewerken en in te delen. In plaats van een schermopname van het rapport in PowerPoint te plakken met toevoeging van belangrijke punten, kunnen voortaan verhalen aan het rapport worden toegevoegd die bij elke vernieuwing worden bijgewerkt. De eindgebruikers kunnen de verhalen gebruiken om hun gegevens beter te begrijpen, sneller tot de belangrijkste punten te komen en anderen de gegevens uit te leggen.

>[!NOTE]
> Deze functie is in preview, dus u dient eerst de functieschakelaar in te schakelen via Bestand > Opties en instellingen > Opties > Preview-functie en ervoor te zorgen dat  **Visual van slimme verhalen** is ingeschakeld:

![Preview-vlag](media/power-bi-visualization-smart-narratives/2.png)

U kunt het PBIX-bestand dat voor het onlineverkoopscenario in deze documentatie wordt gebruikt, [hier](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Monthly%20Desktop%20Blog%20Samples/2020/2020SU09%20Blog%20Demo%20-%20September.pbix) vinden.

## <a name="get-started"></a>Aan de slag 

Klik op het nieuwe pictogram voor slimme verhalen in het visualisatiedeelvenster om automatisch een samenvatting te genereren.

![Pictogram Slimme verhalen](media/power-bi-visualization-smart-narratives/3.png)

 U krijgt een verhaal te zien dat is gemaakt op basis van alle visuals op de pagina. U kunt bijvoorbeeld op het pictogram klikken om automatisch een samenvatting te genereren van de visuals die over inkomsten, websitebezoeken en verkoop in dit rapport praten. U ziet dat Power BI automatisch een trendanalyse geeft om aan te tonen dat de inkomsten en bezoeken beide zijn toegenomen. Er wordt zelfs berekend hoe groot de toename is, in dit geval 72%.
 
 ![Slimme verhalen: samenvatting](media/power-bi-visualization-smart-narratives/4.gif)
 
 U kunt ook met de rechtermuisknop op de visual klikken en **samenvatten** selecteren. Hiermee wordt een automatische samenvatting van die visualisatie gegenereerd. Als u bijvoorbeeld met de rechtermuisknop klikt op > samenvatten in het spreidingsdiagram met de diverse transacties, worden de gegevens geanalyseerd en kunt u zien welke stad/regio de hoogste omzet per transactie en het hoogste aantal transacties heeft. U ziet ook het verwachte waardenbereik voor deze metrische gegevens, zodat u weet dat de meeste steden een omzet genereerden van minder dan €45 per transactie, en minder dan tien transacties hadden.
 
  
 ![Slimme verhalen: samenvatten](media/power-bi-visualization-smart-narratives/5.gif)
 
 ## <a name="edit-the-summary"></a>De samenvatting bewerken
 
 De samenvatting is uiterst **aanpasbaar**. Met behulp van dezelfde besturingselementen die in het normale tekstvak beschikbaar zijn, kunt u nieuwe tekst toevoegen of bestaande tekst bewerken. U kunt de tekst bijvoorbeeld vet maken of de tekstkleur wijzigen.
 
  ![Slimme verhalen: besturingselement voor een tekstvak](media/power-bi-visualization-smart-narratives/6.png)
  
  U kunt de samenvatting ook aanpassen en uw eigen inzichten toevoegen door **dynamische waarden** toe te voegen. U kunt tekst toewijzen aan bestaande velden en metingen, of natuurlijke taal gebruiken om een nieuwe meting te definiëren die aan tekst moet worden toegewezen. Als u bijvoorbeeld informatie over het aantal geretourneerde items wilt toevoegen, kunt u de methode voor het toevoegen van waarden gebruiken, zoals wordt weergegeven in de GIF-animatie. De Q&A is geïntegreerd om dynamische waarden toe te kunnen voegen. Terwijl u typt, krijgt u suggesties in een vervolgkeuzelijst, zoals in een Q&A-visual. U kunt dit gewoon opslaan als een waarde.  U kunt in de Q&A niet alleen vragen stellen over uw gegevens, maar u kunt voortaan ook uw eigen berekeningen maken, en zonder dat u DAX nodig hebt. 
  
   ![Dynamische waarde](media/power-bi-visualization-smart-narratives/7.gif)
  
  U kunt de dynamische waarden opmaken, bijvoorbeeld om als valuta weer te geven, decimale tekens op te geven, scheidingstekens voor duizend tallen te gebruiken, enzovoort. 
   
   ![Dynamische waarde opmaken](media/power-bi-visualization-smart-narratives/8.gif)
   
   U kunt dit doen door rechtstreeks op de waarde in de samenvatting te klikken om deze op te maken, of door te klikken op de bewerkingsknop die overeenkomt met de waarde op het tabblad Controle van het besturingselement voor het tekstvak. 
   
   ![Tabblad Controle in Dynamische waarde opmaken](media/power-bi-visualization-smart-narratives/9.png)
   
   U kunt het tabblad Controle ook gebruiken om eerder gedefinieerde waarden te controleren, te verwijderen of opnieuw te gebruiken.  Als u op het pluspictogram klikt, wordt de waarde in de samenvatting ingevoegd. U kunt ook automatisch gegenereerde waarden weergeven door de optie onderaan in of uit te schakelen.

Soms wordt het symbool voor verborgen samenvattingen weergegeven met de melding 'Huidige gegevens en filters genereren geen resultaat voor deze waarde'. Dit komt omdat sommige samenvattingen leeg kunnen zijn omdat er niets interessant valt te zeggen. Zo kan een samenvatting met hoge en lage waarden in een lijndiagram leeg zijn als het een vlakke lijn is, maar onder andere omstandigheden kan deze niet leeg zijn. Deze symbolen zijn alleen zichtbaar wanneer u probeert de samenvattingen te bewerken.


   ![Verborgen samenvatting](media/power-bi-visualization-smart-narratives/10.png)
   
   ## <a name="visual-interactions"></a>Visualinteracties
   De samenvatting is dynamisch en de gegenereerde tekst en dynamische waarden worden automatisch bijgewerkt wanneer u kruislings filtert. Als u bijvoorbeeld elektronicaproducten in het ringdiagram selecteert, wordt de rest van het rapport kruislings gefilterd en wordt de samenvatting ook kruislings gefilterd zodat u zich op de elektronicaproducten kunt focussen.  In dit geval geven de bezoeken en inkomsten verschillende trends te zien, dus de tekst wordt bijgewerkt om dit aan te geven. En het geretourneerde rendement dat u hebt toegevoegd, wordt bijgewerkt naar €4196. Een aantal lege samenvattingen kunnen ook worden bijgewerkt wanneer u kruislings filtert.
   
   ![Kruislings filteren](media/power-bi-visualization-smart-narratives/11.gif)
   
   U kunt ook geavanceerdere filters toepassen. Als u bijvoorbeeld alleen geïnteresseerd bent in de trend over een bepaald kwartaal in deze visual, waarin de trends van meerdere producten worden weergegeven, hoeft u alleen de relevante gegevenspunten te selecteren om de samenvatting van het fragment bij te laten werken.
   
   ![Filteren ](media/power-bi-visualization-smart-narratives/12.gif)
   
   ## <a name="limitations"></a>Beperkingen
   - Vastmaken aan het dashboard wordt niet ondersteund.
   - Het gebruik van dynamische waarden en voorwaardelijke opmaak (bijvoorbeeld de gegevensgebonden titel) wordt niet ondersteund.
   - Azure Analysis Services en on-premises Analysis Services worden niet ondersteund.
   - Visuals met KPI's, kaarten met meerdere rijen, kaarten, tabellen, matrices en R/Python alsmede aangepaste visuals bieden geen ondersteuning voor samenvattingen. Enkele van deze visuals worden in de toekomst toegevoegd.
   - Samenvatting wordt niet ondersteund voor visuals met kolommen die zijn gegroepeerd op andere kolommen en voor visuals die op basis van een gegevensgroepsveld zijn gebouwd. 
   - Kruislings filteren van de visual wordt niet ondersteund.
   - Het wijzigen van de naam van dynamische waarden of het bewerken van automatisch gegenereerde dynamische waarden wordt niet ondersteund.
   - Samenvatting van visuals die berekeningen á la minute bevatten, zoals QnA-rekenkunde, percentages van het eindtotaal, enzovoort, wordt niet ondersteund.
   

