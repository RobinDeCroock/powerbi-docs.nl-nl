---
title: Verbinding maken met Application Insights voor Power BI
description: Application Insights voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3a41b237ccc4e249d85385b54860f60460efbb31
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70186121"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Verbinding maken met Application Insights met Power BI
Power BI gebruiken voor het maken van krachtige aangepaste dashboards van de telemetrie van [Application Insights](/azure/application-insights/app-insights-overview/). Bekijk uw app-telemetrie op nieuwe manieren. Combineer metrische gegevens uit meerdere apps of componentservices op één dashboard. De eerste versie van het Power BI-inhoudspakket voor Application Insights omvat widgets voor aan algemeen gebruik gerelateerde metrische gegevens zoals actieve gebruikers, paginaweergave, sessies, browser en de versie van het besturingssysteem en geografische verdeling van gebruikers op een kaart.

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Maak verbinding met het [Application Insights-inhoudspakket voor Power BI](https://app.powerbi.com/getdata/services/application-insights).

>[!NOTE]
>Deze integratiemethode is nu **afgeschaft**. Voor meer informatie over de voorkeursmethode voor het koppelen van Application Insights aan Power BI gebruikt u de [functionaliteit voor het exporteren van analytische query's](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries).

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
    ![Knop Gegevens ophalen](media/service-connect-to-application-insights/pbi_getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
    ![Knop Services ophalen](media/service-connect-to-application-insights/pbi_getservices.png)
3. Selecteer **Application Insights** > **Ophalen**.
   
    ![Application Insights-inhoudspakket](media/service-connect-to-application-insights/appinsights.png)
4. Geef de details van de toepassing waarmee u verbinding wilt maken, met inbegrip van **Application Insights-resourcenaam**, **resourcegroep** en **abonnements-ID**. Zie [Zoeken naar uw Application Insights-parameters](#FindingAppInsightsParams) hieronder voor meer informatie.
   
    ![Dialoogvenster voor Application Insights-verbinding](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. Selecteer **Aanmelden** en volg de schermen om verbinding te maken.
   
    ![Aanmelden voor Application Insights-verbinding](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. Het importproces wordt automatisch gestart. Als het proces is voltooid, verschijnt een melding en worden een nieuw dashboard, rapport en gegevensset in het navigatiedeelvenster weergegeven. Deze zijn gemarkeerd met een sterretje.  Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
    ![Application Insights-dashboard](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
Het Application Insights-inhoudspakket bevat de volgende tabellen en metrische gegevens:  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
Uw resourcenaam, resourcegroep en abonnements-id zijn allemaal te vinden in de Azure-portal. Als u de naam selecteert, wordt een gedetailleerde weergave geopend en kunt u de keuzelijst Essentials gebruiken om alle waarden te vinden die u nodig hebt.

![Application Insights-parameters](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

Kopieer en plak deze in de velden in Power BI:

![Application Insights-parameters](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

