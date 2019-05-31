---
title: Verbinding maken met QuickBooks Online via Power BI
description: QuickBooks Online voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ec13f396ea1a322a79263320a169330f24a2e5f0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61151110"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Verbinding maken met QuickBooks Online via Power BI
Wanneer u in Power BI verbinding maakt met uw QuickBooks Online-gegevens, worden direct een Power BI-dashboard en Power BI-rapporten weergegeven die inzicht geven in onder andere uw cashflow, winstgevendheid en klanten. U kunt het dashboard en de rapporten ongewijzigd gebruiken of deze aanpassen om de informatie die u het belangrijkst vindt eruit te laten springen. De gegevens worden eenmaal per dag automatisch vernieuwd.

Maak verbinding met het [QuickBooks Online-inhoudspakket](https://dxt.powerbi.com/getdata/services/quickbooks-online) voor Power BI.

>[!NOTE]
>Als u uw QuickBooks Online-gegevens in Power BI wilt importeren, moet u een beheerder zijn voor uw QuickBooks Online-account en u aanmelden met uw beheerdersreferenties voor het account. U kunt deze connector niet gebruiken in combinatie met QuickBooks Desktop-software. 

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Selecteer **QuickBooks Online** en vervolgens **Ophalen**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. Selecteer **oAuth2** als verificatiemethode en vervolgens **Aanmelden**. 
5. Geef desgevraagd uw QuickBooks Online-referenties op en voer het QuickBooks Online-verificatieproces uit. Als u al bent aangemeld bij QuickBooks Online in uw browser, wordt u mogelijk niet gevraagd om uw referenties in te voeren.
   >[!NOTE]
   >U moet over beheerdersreferenties beschikken voor uw QuickBooks Online-account.
6. Selecteer in het volgende scherm het bedrijf waarmee u via Power BI verbinding wilt maken.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Selecteer in het volgende scherm **Autoriseren** om het importeren te starten. Dit kan enkele minuten duren, afhankelijk van de omvang van uw bedrijfsgegevens. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   Nadat de gegevens in Power BI zijn geïmporteerd, ziet u een nieuw dashboard, een nieuw rapport en een nieuwe gegevensset in het navigatiedeelvenster aan de linkerzijde. Nieuwe items zijn gemarkeerd met een geel sterretje \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Selecteer het QuickBooks Online-dashboard. Dit is het dashboard dat automatisch door Power BI wordt gemaakt om de geïmporteerde gegevens weer te geven. U kunt dit dashboard wijzigen om uw gegevens weer te geven zoals u dat wilt. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="troubleshooting"></a>Problemen oplossen
**"Helaas, er is een fout opgetreden"**

Als u het volgende bericht krijgt wanneer u **Autoriseren** hebt geselecteerd:

"Helaas, er is een fout opgetreden. Sluit dit venster en probeer het opnieuw.

Er is al een andere gebruiker van dit bedrijf geabonneerd op de toepassing. Neem contact op met [e-mailadres van de beheerder] om dit abonnement te wijzigen."

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... houdt dit in dat een andere beheerder in uw bedrijf al via Power BI verbinding heeft gemaakt met uw bedrijfsgegevens. Vraag de beheerder om het dashboard met u te delen. Op dit moment kan slechts één beheerder een verbinding maken tussen een specifieke QuickBooks Online-bedrijfsgegevensset en Power BI. Nadat het dashboard door Power BI is gemaakt, kan de beheerder deze met meerdere collega's in dezelfde Power BI-tenants delen.

**"Er mag volgens de instellingen vanuit uw land geen verbinding worden gemaakt met deze app"**

Power BI ondersteunt momenteel alleen Amerikaanse edities van QuickBooks Online. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](power-bi-overview.md)

[Power BI - basisconcepten](consumer/end-user-basic-concepts.md)

