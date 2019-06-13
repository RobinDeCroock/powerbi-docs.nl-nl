---
title: Rapporten of dashboards uit apps insluiten
description: Leer hoe u een rapport of dashboard integreert of insluit vanuit een Power BI-app en niet vanuit een app-werkruimte.
author: rkarlin
ms.author: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: mvc
manager: kfile
ms.date: 11/27/2018
ms.openlocfilehash: 5a988eb160ce772d2c2e70e8cba2c01d3f0a36a9
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750895"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Rapporten of dashboards uit apps insluiten

In Power BI kunt u apps maken om gerelateerde dashboards en rapporten bij elkaar te brengen, allemaal op één plek samen. Publiceer ze vervolgens naar grote groepen gebruikers in uw organisatie. Het gebruik van die apps is relevant wanneer al uw gebruikers Power BI-gebruikers zijn. U kunt dus inhoud met ze delen met behulp van Power BI-apps. In dit artikel vindt u een aantal korte stappen om inhoud uit een gepubliceerde Power BI-app in te sluiten in een externe toepassing.

## <a name="grab-a-report-embedurl-for-embedding"></a>Een rapport-embedURL ophalen om in te sluiten

1. Maak een exemplaar van de toepassing in de gebruikerswerkruimte **Mijn werkruimte**. Deel met uzelf of leid een andere gebruiker om door deze stroom te gaan.

2. Open het gewenste rapport in de Power BI-service.

3. Ga naar **Bestand** > **Insluiten in SharePoint Online** en haal de rapport-embedURL op. In de onderstaande momentopname ziet u een embedURL-voorbeeld. Of roep de GetReports/GetReport REST-API aan en extraheer het bijbehorende embedURL-veld voor rapporten uit het antwoord. De REST-aanroep mag geen werkruimte-id bevatten in de URL, aangezien er in de werkruimte van de gebruiker een exemplaar is gemaakt.

    ![Insluiten vanuit apps](media/embed-from-apps/embed-from-app.png)

4. Gebruik de embedURL die u bij stap 3 hebt opgehaald met de JavaScript-SDK.

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Een dashboard-embedURL ophalen om in te sluiten

1. Maak een exemplaar van de toepassing in de gebruikerswerkruimte **Mijn werkruimte**. Deel met uzelf of leid een andere gebruiker om door deze stroom te gaan.

2. Of roep de GetDashboards REST-API aan en extraheer het bijbehorende embedURL-veld voor dashboards uit het antwoord. De REST-aanroep mag geen werkruimte-id bevatten in de URL, aangezien er in de werkruimte van de gebruiker een exemplaar is gemaakt.

3. Gebruik de embedURL die u bij stap 2 hebt opgehaald met de JavaScript-SDK.

## <a name="next-steps"></a>Volgende stappen

Controleer hoe u inhoud uit app-werkruimten kunt insluiten voor uw externe klanten en uw organisatie:

> [!div class="nextstepaction"]
>[Insluiten voor externe klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)
