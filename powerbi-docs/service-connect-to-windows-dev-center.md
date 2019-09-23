---
title: Verbinding met Windows-ontwikkelaarscentrum maken via Power BI
description: Windows-ontwikkelaarscentrum voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 81498dff9c70deaf8135faf244db96509b1cf18d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61163887"
---
# <a name="connect-to-windows-dev-center-with-power-bi"></a>Verbinding met Windows-ontwikkelaarscentrum maken via Power BI
Verken en bewaak de analytische gegevens van uw Windows-ontwikkelaarscentrum-app in Power BI met het Power BI-inhoudspakket. De gegevens wordt een keer per dag automatisch vernieuwd.

Maak verbinding met het [inhoudspakket van Windows-ontwikkelaarscentrum](https://app.powerbi.com/getdata/services/devcenter) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-windows-dev-center/getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-windows-dev-center/services.png)
3. Selecteer **Windows-ontwikkelaarscentrum** \> **Ophalen**.
   
   ![](media/service-connect-to-windows-dev-center/windowsdev.png)
4. Voer de toepassings-id in van een app waarvan u de eigenaar bent en klik op Volgende. Hieronder vindt u meer informatie over [hoe u deze parameters kunt vinden](#FindingParams).
   
   ![](media/service-connect-to-windows-dev-center/params.png)
5. Selecteer voor de **verificatiemethode** **oAuth2**\> **Aanmelden**. Voer desgevraagd uw Azure Active Directory-referenties in die zijn gekoppeld aan uw account van Windows-ontwikkelaarscentrum (zie [Systeemvereisten](#Requirements) voor meer informatie).
   
    ![](media/service-connect-to-windows-dev-center/creds.png)
   
    ![](media/service-connect-to-windows-dev-center/creds2.png)
6. Nadat uw aanmelding is goedgekeurd, wordt het importeren automatisch gestart. Nadat het importeren is voltooid, bevat het navigatiedeelvenster een nieuw dashboard, rapport en model. Selecteer het dashboard om de geïmporteerde gegevens te bekijken en kies een tegel om naar de onderliggende rapporten te navigeren.
   
    ![](media/service-connect-to-windows-dev-center/dashboard.png)
   
    ![](media/service-connect-to-windows-dev-center/report.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
Het Power BI-inhoudspakket voor het ontwikkelaarscentrum bevat analytische gegevens voor uw app- en IAP-acquisities, beoordelingen, recensies en status van de app. De gegevens zijn beperkt tot de afgelopen drie maanden. Bovendien is dit een zwevend venster, zodat de opgenomen datums worden bijgewerkt zodra de gegevensset wordt vernieuwd.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systeemvereisten
Voor dit inhoudspakket moet er minimaal één app naar de Microsoft Store zijn gepubliceerd en is een Windows-ontwikkelaarscentrum-account vereist (u vindt [hier](https://msdn.microsoft.com/windows/uwp/publish/manage-account-users) meer informatie).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
De toepassings-id voor een app vindt u op de pagina App-id onder App-beheer.

De toepassings-id wordt weergegeven aan het eind van uw URL voor de Windows 10 Store, https://www.microsoft.com/store/apps/ **{applicationId}**

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

