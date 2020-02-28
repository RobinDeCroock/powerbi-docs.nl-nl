---
title: 'Service van derden: Facebook-connector voor Power BI Desktop'
description: 'Service van derden: Facebook-connector voor Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 882cddf7728a27e78056a35c14fde20f00678e33
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527697"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Facebook-connector voor Power BI Desktop gebruiken
De Facebook-connector in **Power BI Desktop** is afhankelijk van de Facebook Graph API. Als zodanig kunnen de functies en beschikbaarheid in de loop van de tijd worden gewijzigd.

U kunt een [zelfstudie over de Facebook-connector voor Power BI Desktop bekijken](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Mededeling over afschaffing van de Facebook-gegevensconnector:** Het importeren en vernieuwen van gegevens uit Facebook in Excel werkt vanaf april 2020 niet meer goed. U kunt tot dat moment de Facebook-connector *Ophalen en transformeren (Power Query)* gebruiken. Na die datum kunt u geen verbinding meer maken met Facebook en ziet u een foutmelding. Het wordt aanbevolen eventuele bestaande query's voor *Ophalen en transformeren (Power Query)* die gebruikmaken van de Facebook-connector, zo snel mogelijk te herzien of verwijderen om onverwachte resultaten te voorkomen.


Versie 1.0 van de Graph API van Facebook is op 30 april 2015 komen te vervallen. Power BI gebruikt de Graph API achter de schermen voor de Facebook-connector, zodat u verbinding met uw gegevens kunt maken en deze kunt analyseren.

Query's die zijn samengesteld vóór 30 april 2015 werken mogelijk niet meer of retourneren minder gegevens. Na 30 april 2015 maakt Power BI voor aanroepen naar de Facebook API gebruik van versie 2.8. Als uw query is samengesteld vóór 30 april 2015 en u deze sindsdien niet hebt gebruikt, moet u het verificatieproces mogelijk opnieuw uitvoeren om de nieuw set machtigingen goed te keuren waar wij u naar vragen.

Hoewel er wordt geprobeerd om updates uit te brengen in het geval van wijzigingen, is het mogelijk dat de API zodanig wordt gewijzigd dat dit van invloed is op de resultaten die worden gegenereerd. In sommige gevallen is het mogelijk dat bepaalde query's niet meer worden ondersteund. Vanwege deze afhankelijkheid kunnen er geen garanties worden gegeven voor de resultaten van uw query's bij gebruik van deze connector.

U vindt [hier](https://developers.facebook.com/docs/apps/changelog#v2_0) meer informatie over de wijzigingen in de Facebook API.

