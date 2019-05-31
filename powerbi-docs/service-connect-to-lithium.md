---
title: Verbinding met Lithium maken via Power BI
description: Lithium voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 9029d5b6268cacf17fc862a4c0a3d19f440f7de1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61163852"
---
# <a name="connect-to-lithium-with-power-bi"></a>Verbinding met Lithium maken via Power BI
Lithium bouwt vertrouwde relaties tussen de beste merken ter wereld en hun klanten en helpt mensen om antwoorden te vinden en hun ervaringen te delen. Door het Lithium-inhoudspakket te verbinden met Power BI, kunt u essentiële metrische gegevens over uw online community meten om zodoende de verkoop te stimuleren, de servicekosten te reduceren en de loyaliteit te verhogen. 

Maak verbinding met het [Lithium-inhoudspakket](https://app.powerbi.com/getdata/services/lithium) voor Power BI.

>[!NOTE]
>Het Power BI-inhoudspakket maakt gebruik van de Lithium-API. Wanneer de API overmatig vaak wordt aangeroepen, worden mogelijk extra kosten voor Lithium in rekening gebracht. U kunt dit navragen bij uw Lithium-beheerder.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-lithium/pbi_getdata.png) 
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-lithium/pbi_getservices.png) 
3. Selecteer **Lithium** \> **Ophalen**.
   
   ![](media/service-connect-to-lithium/lithiumconnect.png)
4. Geef de URL van de Lithium-community op. Dit heeft de volgende vorm: *https://community.yoursite.com* .
   
   ![](media/service-connect-to-lithium/params.png)
5. Geef desgevraagd uw Lithium-referenties op. Selecteer **oAuth 2** als verificatiemechanisme, klik op **Aanmelden** en volg de verificatiestroom van Lithium.
   
   ![](media/service-connect-to-lithium/creds.png)
   
   ![](media/service-connect-to-lithium/creds2.png)
6. Als het aanmeldingsproces is voltooid, wordt het importproces gestart. Nadat het importeren is voltooid, bevat het navigatiedeelvenster een nieuw dashboard, rapport en model. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
    ![](media/service-connect-to-lithium/lithium.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="system-requirements"></a>Systeemvereisten
Voor het Lithium-inhoudspakket is een Lithium Community v15.9 of hoger vereist. Neem contact op met uw Lithium-beheerder om dit te controleren.

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](power-bi-overview.md)

[Power BI - basisconcepten](consumer/end-user-basic-concepts.md)

