---
title: Verbinding maken met Twilio via Power BI
description: Twilio voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4537f2845d89361cf06bc93a6a9c435275d9464d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61171153"
---
# <a name="connect-to-twilio-with-power-bi"></a>Verbinding maken met Twilio via Power BI
Met het Microsoft Twilio-inhoudspakket voor Power BI kunt u uw gegevens in Power BI laden en maakt u een kant-en-klaar [Twilio-dashboard](https://powerbi.microsoft.com/integrations/twilio) en -rapport die inzicht geven in uw gegevens. U kunt ook uw aangepaste rapporten en dashboard maken op basis van de gegevensset die Power BI maakt. De gegevens worden eenmaal per dag vernieuwd zodat u altijd over de meest recente gegevens beschikt.

Verbinding maken met het [Twilio-inhoudspakket voor Power BI](https://app.powerbi.com/getdata/services/twilio).

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-twilio/pbi_getdata.png) 
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-twilio/pbi_getservices.png) 
3. Selecteer **Twilio** \> **Ophalen**.
   
   ![](media/service-connect-to-twilio/twilio.png)
4. Selecteer voor de **verificatiemethode** **oAuth2**\> Aanmelden. Geef uw Twilio-gegevens op en machtig de Power BI-toepassing om toegang te krijgen tot uw gegevens.
   
   ![](media/service-connect-to-twilio/pbi_twilio_login.png)
5. Hiermee wordt begonnen met het importeren van gegevens uit uw Twilio-account en uw dashboard wordt gevuld met uw oproepen- en berichtengebruik van de afgelopen 30 dagen. 
   
   ![](media/service-connect-to-twilio/pbi_twilio_db.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
De details voor alle oproepen- en berichtentransacties voor de afgelopen 30 dagen. Op deze gegevens kunt u allerlei analyses en aggregaties uitvoeren.

Een set van reeds samengevoegde statistieken die u in de gaten wilt houden. Deze set omvat:

        All Time Calls Count  
        All Time Calls Duration  
        All Time Calls Price  
        All Time Messages Price  
        All Time Messages Count  
        All Time Count of Phone Numbers  
        All Time Price of Phone Numbers  
        All Time Twilio Client Calls Price  
        All Time Twilio Client Calls Duration  
        All Time Twilio Client Calls Count  
        All Time Total Price  
        All Time Inbound Calls Price  
        All Time Inbound Calls Duration  
        All Time Inbound Calls Count  
        All Time Outbound Calls Price  
        All Time Outbound Calls Duration  
        All Time Outbound Calls Count  
        This Month Calls Price  
        This Month Calls Duration  
        This Month Calls Count  
        This Month Messages Count  
        This Month Messages Price  
        This Month Count of Phone Numbers  
        This Month Price of Phone Numbers  
        This Month Twilio Client Calls Price  
        This Month Twilio Client Calls Duration  
        This Month Twilio Client Calls Count  
        This Month Total Price  
        This Month Inbound Calls Price  
        This Month Inbound Calls Duration  
        This Month Inbound Calls Count  
        This Month Outbound Calls Price  
        This Month Outbound Calls Duration  
        This Month Outbound Calls Count  
        This Month Inbound Messages Price  
        This Month Inbound Messages Count  
        This Month Outbound Messages Price  
        This Month Outbound Messages Count

## <a name="troubleshooting"></a>Probleemoplossing
Als u in de afgelopen 30 dagen een zeer grote hoeveelheid gegevens hebt (honderdduizenden transacties), kan het ophalen van gegevens mislukken. We zijn ons bewust van het probleem en werken eraan om het op te lossen. Als u ondertussen op dit probleem stuit, kunt u de koppeling voor ondersteuning bovenaan uw Power BI-pagina gebruiken om het ons te laten weten en wij zullen contact met u opnemen voor verder onderzoek.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

