---
title: Een visueel Power BI-element optimaliseren voor elke grootte
description: Informatie over het optimaliseren van visuals in bestaande rapporten in Power BI Desktop en de Power BI-service voor de Power BI-telefoonapps.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 4372f37cf6afc8fe51d6650ddd888bd41d3ea678
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394899"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Een visueel Power BI-element optimaliseren voor elke grootte
Wanneer u een nieuw rapport maakt, zijn de visuele elementen standaard *responsief*: Ze kunnen dynamisch veranderen zodat de maximale hoeveelheid gegevens en inzichten wordt weergegeven, ongeacht de schermgrootte. Voor oudere rapporten kunt u de visuals ook zo instellen dat ze dynamisch kleiner of groter worden.

Als de grootte van een visueel element verandert, geeft Power BI de prioriteit aan de gegevensweergave, bijvoorbeeld door automatisch de opvulling te verwijderen en de legenda naar de bovenkant van het visuele element te verplaatsen, zodat het visuele element ook als het kleiner wordt informatief blijft. Reactietijd is met name nuttig in visuele elementen in de mobiele Power BI-app op telefoons.

![Reactietijd bij het wijzigen van de grootte van visuele elementen](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Elke visual met een X- en Y-as en slicers kan responsief groter of kleiner worden.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Reactietijd inschakelen in Power BI Desktop
1. Zorg er in een ouder rapport in Power BI Desktop op het tabblad **Beeld** voor dat u in de modus **Bureaubladindeling** bent.
   
    ![Het pictogram Bureaubladindeling](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Selecteer een visueel element en selecteer in het deelvenster **Visualisaties** de sectie **Indeling**.
3. Vouw **Algemeen** uit > schuif **Responsief** naar **Aan**.
   
    ![Responsief aan](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Wanneer u nu [een voor de telefoon geoptimaliseerd rapport maakt](../desktop-create-phone-report.md) en dit visuele element toevoegt, wordt de grootte ervan correct aangepast.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Reactietijd inschakelen in de Power BI-service
U kunt de functie Responsief voor een visual in een ouder rapport in de Power BI-service inschakelen. U moet het rapport kunnen bewerken.

1. Selecteer in een rapport in de Power BI-service ([https://powerbi.com](https://powerbi.com)) de optie **Rapport bewerken**.
2. Selecteer een visueel element en selecteer in het deelvenster **Visualisaties** de sectie **Indeling**.
3. Vouw **Algemeen** uit > schuif **Responsief** naar **Aan**.
   
    ![Responsief aan](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Wanneer u nu [een telefoonweergave van dit rapport maakt](../desktop-create-phone-report.md) en deze visual toevoegt, wordt de grootte ervan correct aangepast.

## <a name="next-steps"></a>Volgende stappen
* [Rapporten maken die zijn geoptimaliseerd voor de mobiele Power BI-apps](../desktop-create-phone-report.md)
* [Voor uw telefoon geoptimaliseerde Power BI-rapporten weergeven](../consumer/mobile/mobile-apps-view-phone-report.md)
* Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

