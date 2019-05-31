---
title: Maak een koppeling naar een specifieke locatie in de Power BI - Mobiel-apps
description: Informatie over het maken van de dieptekoppeling naar een specifiek dashboard, tegel of rapport in de Power BI - Mobiel-app met een uniform resource identifier (URI).
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906536"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Maak een koppeling naar een specifieke locatie in de Power BI - Mobiel-apps
U kunt koppelingen voor rechtstreekse toegang tot specifieke items in Power BI gebruiken: Rapport, een Dashboard en een tegel.

Er zijn voornamelijk twee scenario's voor het gebruik van koppelingen in Power BI-mobiel: 

* Power BI vanuit openen **buiten de app**, en land op specifieke inhoud (rapport/dashboard/app). Dit is meestal een integratiescenario, als u wilt Power BI-mobiel openen vanuit andere Apps. 
* Naar **navigeren** binnen Power BI. Dit is meestal als u wilt maken van een aangepaste navigatie in Power BI.


## <a name="use-links-from-outside-of-power-bi"></a>Gebruik de koppelingen van buiten Power BI
Wanneer u een koppeling van buiten Power BI-app, die u wilt ervoor zorgen dat deze worden geopend door de app, en als de app is niet geïnstalleerd op het apparaat en klik vervolgens op het bieden van de gebruiker om het te installeren. We hebben de indeling van een speciale koppeling gemaakt ter ondersteuning van precies die. Deze indeling voor de koppeling, zorgt u ervoor dat het apparaat van de app gebruikmaakt om de koppeling te openen, en als de app is niet geïnstalleerd op het apparaat, gaat u naar de store downloaden van de gebruiker wordt aangeboden.

De koppeling moet beginnen met het volgende  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Als uw inhoud wordt gehost in speciale datacenter, zoals regering, China, enzovoort. De koppeling moet beginnen met het juiste adres van de Power BI, zoals `app.powerbigov.us` of `app.powerbi.cn`.   
>


De **QUERY PARAMS** zijn:
* **actie** (verplicht) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = als u wilt een rapport of dashboard die deel uitmaken van een app openen 
* **groupObjectId** = als u wilt openen van een rapport of dashboard die deel uitmaken van de werkruimte (maar niet mijn werkruimte)
* **dashboardObjectId** = dashboard-object-ID (als de actie is OpenDashboard of OpenTile)
* **reportObjectId** = rapport, object-ID (als actie OpenReport)
* **tileObjectId** = tegel object-ID (als actie OpenTile)
* **reportPage** = als u een sectie specifieke rapport openen wilt (als actie OpenReport)
* **ctid** = item organisatie-ID (dit is relevant voor B2B-scenario. Dit kan worden weggelaten als het item bij de organisatie van de gebruiker hoort).

**Voorbeelden:**

* Koppeling van de app openen 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Dashboard openen die deel uitmaakt van een app 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Rapport openen die deel uitmaakt van een werkruimte
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>Over het verkrijgen van de indeling voor de juiste koppeling

#### <a name="links-of-apps-and-items-in-app"></a>Koppelingen van apps en -items in-app

Voor **apps en rapporten en dashboards die deel uitmaken van een app**, de eenvoudigste manier om de koppeling is om te gaan naar de app-werkruimte en kiest u 'Update-app'. Hiermee opent u de 'App publiceren'-ervaring en in het tabblad toegang vindt u een **koppelingen** sectie. Uitbreiden dat gedeelte en u de lijst van de app ziet en alle bijbehorende inhoud die is gekoppeld kan worden gebruikt voor toegang tot deze rechtstreeks.

![Power BI app koppelingen publiceren ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Koppelingen van items niet in-app 

Voor rapporten en dashboards die geen deel uitmaken van een app, moet u de id's ophalen uit de URL van het item.

Bijvoorbeeld, vinden de 36 tekens **dashboard** object-ID, gaat u naar het specifieke dashboard in Power BI-service 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

De 36 tekens vinden **rapport** object-ID, gaat u naar het specifiek rapport in Power BI-service.
Dit is een voorbeeld van rapport van 'Mijn werkruimte'

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
De bovenstaande URL bevat ook specifieke rapportpagina **"ReportSection3"** .

Dit is een voorbeeld van een rapport uit een werkruimte (niet mijn werkruimte)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Gebruik de koppelingen in Power BI

Koppelingen in Power BI werkt in de mobiele apps precies zoals in Power BI-Service.

Als u koppelen aan uw rapport die naar een ander Power BI-item verwijst toevoegt wilt, kunt u alleen de URL van dat item kopiëren uit de adresbalk van de browser. Meer informatie over [een hyperlink toevoegen aan een tekstvak in een rapport](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="use-report-url-with-filter"></a>Rapport-URL met filter gebruiken
Hetzelfde als Power BI-service, Power BI-mobiel-apps ook ondersteuning voor rapport-URL die een filter-query-parameter bevat. U kunt een rapport openen in Power BI-mobiel-app en het filteren op specifieke status. Bijvoorbeeld: deze URL wordt geopend de verkooprapport en filteren per regio

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

Meer informatie over [over het bouwen van query-parameter voor het filteren van rapporten](https://docs.microsoft.com/power-bi/service-url-filters).

## <a name="next-steps"></a>Volgende stappen
Op basis van uw feedback kunnen we bepalen wat in de toekomst moet worden geïmplementeerd. Vergeet dus niet op andere functies te stemmen die u graag in de mobiele Power BI-apps zou willen zien. 

* [Power BI-apps voor mobiele apparaten](mobile-apps-for-mobile-devices.md)
* Volg @MSPowerBI op Twitter
* Deelnemen aan conversaties in de [Power BI-community](http://community.powerbi.com/)
* [Wat is Power BI?](../../power-bi-overview.md)

