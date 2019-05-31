---
title: Verbinding met comScore Digital Analytix maken via Power BI
description: comScore Digital Analytix voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 49ac1f917a5f3095c1dbc13c644061859389fe74
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61174709"
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Verbinding met comScore Digital Analytix maken via Power BI
Visualiseer en verken uw comScore Digital Analytix-gegevens in Power BI met het Power BI-inhoudspakket. De gegevens wordt een keer per dag automatisch vernieuwd.

Verbinding maken met het [comScore-inhoudspakket voor Power BI](https://app.powerbi.com/getdata/services/comscore).

>[!NOTE]
>U hebt een comScore DAx-gebruikersaccount en toegang tot comScore API nodig om verbinding met het inhoudspakket te maken. Zie hieronder voor [meer informatie](#Requirements).

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer Gegevens ophalen onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Selecteer **comScore Digital Analytix** \> **Ophalen**.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Geef het datacentrum, de client-id van comScore en de site waarmee u verbinding wilt maken op. Zie het gedeelte [Uw comScore-parameters zoeken](#FindingParams) hieronder voor meer informatie over de manier hoe u naar deze waarden kunt zoeken.
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. Geef uw gebruikersnaam en wachtwoord voor comScore op om verbinding te maken. Meer informatie over het zoeken van deze waarde vindt u hieronder.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. Het importproces wordt automatisch gestart. Nadat het importeren is voltooid, bevat het navigatiedeelvenster een nieuw dashboard, rapport en model. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systeemvereisten
U hebt een comScore DAx-gebruikersaccount en toegang tot de comScore DAx-API nodig om verbinding te kunnen maken. Neem contact op met uw comScore DAx-beheerder om uw account te bevestigen.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
Hieronder vindt u meer informatie hoe u naar elk van de comScore-parameters zoekt.

**Datacentrum**

Met welk datacentrum u verbinding maakt, wordt bepaald door de URL waarnaar u in comScore navigeert.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Client**

Dit is dezelfde client die u opgeeft wanneer u zich aanmeldt bij comScore DAx.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Site**

De comScore-site bepaalt van welke site u gegevens wilt zien. De lijst met sites vindt u in uw comScore-account.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

