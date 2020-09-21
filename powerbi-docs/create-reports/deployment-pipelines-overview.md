---
title: Overzicht van implementatiepijplijnen
description: Meer informatie over implementatiepijplijnen in Power BI
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 09/09/2020
ms.openlocfilehash: 3994a5cdad4d80c87d4153ffe57af685d7a21d36
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2020
ms.locfileid: "90008578"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Inleiding tot implementatiepijplijnen (preview-versie)

Tegenwoordig vormt analyse een belangrijk onderdeel van het besluitvormingsproces in vrijwel elke organisatie. Het groeiende gebruik van Power BI als hulpprogramma voor analyse betekent dat het meer gegevens moet kunnen verwerken en aantrekkelijk en gebruiksvriendelijk moet zijn. Bovenal moet Power BI altijd beschikbaar en betrouwbaar zijn. Om aan deze vereisten te voldoen, moeten BI-ontwikkelaars effectief kunnen samenwerken.

Met het hulpprogramma voor implementatiepijplijnen kunnen BI-auteurs de levenscyclus van organisatie-inhoud beheren. Het hulpprogramma is efficiënt en opnieuw te gebruiken voor auteurs in een onderneming met Premium-capaciteit. Met het hulpprogramma kunnen auteurs Power BI-inhoud ontwikkelen en testen voordat deze inhoud wordt gebruikt door gebruikers. De inhoudstypen zijn onder meer rapporten, dashboards en gegevenssets.

Het hulpprogramma is ontworpen als een pijplijn met drie fasen:

* **<a name="development"></a>Ontwikkeling**
    
    Deze fase wordt gebruikt voor het ontwerpen, bouwen en uploaden van nieuwe inhoud met andere ontwikkelaars. Dit is de eerste fase in een implementatiepijplijn.

* **<a name="test"></a>Test**

    U bent klaar voor de testfase als u alle wijzigingen hebt aangebracht in uw inhoud. U uploadt de gewijzigde inhoud zodat deze naar deze testfase kan worden verplaatst. Hier volgen drie voorbeelden van wat u kunt doen in de testomgeving:

    * Inhoud delen met testers en revisoren

    * Grotere gegevensvolumes laden en testen

    * Testen hoe uw app eruitziet voor uw eindgebruikers

* **<a name="production"></a>Productie**

    Nadat u de inhoud hebt getest, gebruikt u de productiefase om de uiteindelijke versie van uw inhoud te delen met zakelijke gebruikers in de hele organisatie.

![Een schermopname van een werkende implementatiepijplijn met alle drie de fasen ingevuld: ontwikkeling, testen en productie.](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Aan de slag gaan met implementatiepijplijnen](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Uitleg over het proces van implementatiepijplijnen](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Problemen met implementatiepijplijnen oplossen](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Best practices voor implementatiepijplijnen](deployment-pipelines-best-practices.md)
