---
title: Via Power BI verbinding maken met Stripe
description: Stripe voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ddcbee2c6d60541db0d71ea5ccfbfd5e6cf037ac
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184576"
---
# <a name="connect-to-stripe-with-power-bi"></a>Via Power BI verbinding maken met Stripe
Visualiseer en verken uw Stripe-gegevens in Power BI met het Power BI-inhoudspakket. Met het Power BI Stripe-inhoudspakket haalt u gegevens op over uw klanten, kosten, gebeurtenissen en facturen. De gegevens bevatten de meest recente 10.000 gebeurtenissen en 5000 kostengegevens gedurende de afgelopen 30 dagen. De inhoud wordt automatisch een keer per dag vernieuwd volgens een schema dat u bepaalt. 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Maak verbinding met het [Stripe-inhoudspakket voor Power BI](https://app.powerbi.com/getdata/services/stripe).

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer Gegevens ophalen onder in het linkernavigatievenster.  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.  
   
    ![](media/service-connect-to-stripe/services.png)  
3. Selecteer **Stripe** &gt; **Ophalen**.  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. Geef de [API-sleutel](https://dashboard.stripe.com/account/apikeys) van Stripe op om verbinding te maken.  
   
    ![](media/service-connect-to-stripe/creds.png)
5. Het importproces wordt automatisch gestart. Als het proces is voltooid, worden een nieuw dashboard, rapport en model in het navigatiedeelvenster weergegeven. Deze zijn gemarkeerd met een sterretje. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
    ![](media/service-connect-to-stripe/dashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](power-bi-overview.md)

[Gegevens ophalen voor Power BI](service-get-data.md)

