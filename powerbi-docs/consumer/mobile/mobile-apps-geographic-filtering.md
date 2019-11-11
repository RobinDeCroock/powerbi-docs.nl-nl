---
title: Rapport filteren op geografische locatie in een mobiele Power BI-app
description: Leer hoe u een rapport kunt filteren op uw geografische locatie in de mobiele Microsoft Power BI-apps, als de rapporteigenaar geografische labels heeft ingesteld.
author: mshenhav
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: mshenhav
ms.openlocfilehash: 1079b624ebab827b41f4da55095028796319fdcd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870641"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Een rapport filteren op geografische locatie in de mobiele Power BI-apps
Van toepassing op:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Windows 10-telefoons |

Ziet u, wanneer u een Power BI-rapport weergeeft op een mobiel apparaat, in de rechterbovenhoek een pictogram van een kleine punaise? Als dit het geval is, kunt u dit rapport filteren op basis van uw geografische locatie.

> [!NOTE]
> U kunt alleen filteren op locatie als de geografische namen in het rapport in het Engels zijn, bijvoorbeeld 'New York City' of 'Germany'. Windows 10-tablets en -pc's bieden geen ondersteuning voor geografische filtering, maar Windows 10-telefoons wel.
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>Een rapport filteren op uw geografische locatie
1. Open een rapport in de mobiele Power BI-app op uw mobiele apparaat.
2. Als het rapport geografische gegevens bevat, ziet u een bericht waarin u wordt gevraagd om Power BI toegang te verlenen tot uw locatie. Tik op **Toestaan** en vervolgens opnieuw op **Toestaan**.
3. Tik op de punaise ![Pictogram Punaise](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). U kunt filteren op stad, provincie of land/regio, afhankelijk van de gegevens in het rapport. Het filter biedt alleen opties die overeenkomen met uw huidige locatie.
   
    ![Punaisefilter](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>Waarom zie ik geen locatiecodes in een rapport?
Er moet aan alle drie onderstaande voorwaarden worden voldaan voordat de locatiecodes worden weergegeven. 

* De persoon die het rapport in Power BI Desktop heeft gemaakt, moet [geografische gegevens hebben gecategoriseerd](../../desktop-mobile-geofiltering.md) voor minstens één kolom, zoals stad, provincie of land/regio.
* U bevindt zich op een van de locaties met gegevens in deze kolom.
* U gebruikt een van deze mobiele apparaten:
  * iOS (iPad, iPhone, iPod).
  * Android-telefoon.
  * Windows 10-telefoon (andere Windows 10-apparaten zoals pc's en tablets bieden geen ondersteuning voor geografische filtering).

Lees meer over [het instellen van geografische filtering](../../desktop-mobile-geofiltering.md) in Power BI Desktop.

### <a name="next-steps"></a>Volgende stappen
* [Verbinding maken met Power BI-gegevens uit de praktijk](mobile-apps-data-in-real-world-context.md) met de mobiele apps
* [Gegevenscategorisatie in Power BI Desktop](../../desktop-data-categorization.md) 
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

