---
title: Verbinding met ClickDimensions maken via Power BI
description: ClickDimensions voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 98be77e2cfe53e535dd322317246549a6b4324a4
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185956"
---
# <a name="connect-to-clickdimensions-with-power-bi"></a>Verbinding met ClickDimensions maken via Power BI
Met het ClickDimensions-inhoudspakket voor Power BI kunnen gebruikers hun marketinggegevens van ClickDimensions gebruiken in Power BI om managementteams meer inzicht te bieden in het succes van hun verkoop- en marketinginspanningen. Visualiseer en analyseer e-mailinteracties, webbezoeken en formulierinzendingen in Power BI-dashboards en rapporten.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Maak verbinding met het [ClickDimensions-inhoudspakket](https://app.powerbi.com/getdata/services/click-dimensions) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-clickdimensions/getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-clickdimensions/services.png)
3. Selecteer **ClickDimensions** \> **Ophalen**.
   
   ![](media/service-connect-to-clickdimensions/clickdimensions.png)
4. Geef de locatie op van uw datacenter (VS, EU of Australië) en selecteer **Volgende**.
   
   ![](media/service-connect-to-clickdimensions/params.png)
5. Selecteer voor **Verificatiemethode** de optie **Basis** \> **Aanmelden**. Voer desgevraagd uw ClickDimensions-referenties in. Hieronder vindt u meer informatie over [hoe u deze parameters kunt vinden](#FindingParams).
   
    ![](media/service-connect-to-clickdimensions/creds.png)
6. Nadat uw aanmelding is goedgekeurd, wordt het importeren automatisch gestart. Nadat het importeren is voltooid, bevat het navigatiedeelvenster een nieuw dashboard, rapport en model. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
     ![](media/service-connect-to-clickdimensions/dashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="system-requirements"></a>Systeemvereisten
U moet het datacentrum voor uw account opgeven en zich aanmelden met uw ClickDimensions-account om verbinding met het Power BI-pakket te maken. Als u niet zeker weet welk datacentrum u moet opgegeven, neemt u contact op met uw beheerder.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
De accountsleutel vindt u in CRM-instellingen \> ClickDimensions-instellingen. Kopieer de accountsleutel in de ClickDimensions-instellingen en plak deze in het veld Gebruikersnaam.  

![](media/service-connect-to-clickdimensions/crm.png)  

Kopieer het Power BI-token in de ClickDimensions-instellingen en plak dit in het veld Wachtwoord. Het Power BI-token vindt u in CRM-instellingen \> ClickDimensions-instellingen.  

![](media/service-connect-to-clickdimensions/crm2.png)  

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

