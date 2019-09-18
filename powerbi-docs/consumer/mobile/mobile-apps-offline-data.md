---
title: Gegevens offline weergeven in de mobiele Power BI-apps
description: 'Hier leest u wat een voordeel is van het weergeven van Power BI in een mobiele app in plaats van een mobiele browser: u kunt uw gegevens ook zien wanneer u niet met een netwerk bent verbonden.'
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: mshenhav
ms.openlocfilehash: b4977bd043cec08c86fbd3c8893e8f1e185dc1fc
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/16/2019
ms.locfileid: "60972349"
---
# <a name="view-your-data-offline-in-the-power-bi-mobile-apps"></a>Gegevens offline weergeven in de mobiele Power BI-apps
Van toepassing op:

| ![iPhone](./media/mobile-apps-offline-data/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-offline-data/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-apps-offline-data/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-apps-offline-data/android-tablet-logo-50-px.png) | ![Windows 10](./media/mobile-apps-offline-data/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Android-tablets |Windows 10-apparaten |

Een voordeel van het weergeven van Power BI in een mobiele app in plaats van een mobiele browser is dat u uw gegevens zelfs kunt zien wanneer u niet met een netwerk bent verbonden. 

![Bericht over geen netwerk](./media/mobile-apps-offline-data/power-bi-iphone-no-network.png)

De standaardinstelling is dat Power BI de gegevens regelmatig vernieuwt, zodat u altijd actuele antwoorden krijgt op uw vragen, ook als u onderweg bent of aan het roamen bent.

## <a name="data-access-while-youre-offline"></a>Toegang tot gegevens terwijl u offline bent
Wanneer u offline bent, hebt u toegang tot de dashboards die u eerder hebt geopend vanuit de mobiele app en kunt u hiermee ook communiceren.

U hebt ook alleen-lezen toegang tot alle Power BI-rapporten die u eerder hebt geopend vanuit de mobiele app. U kunt het volledige rapport bekijken, maar het is niet mogelijk om te filteren, kruislings filteren, sorteren of segmenteren met behulp van slicers.

## <a name="background-data-refresh"></a>Gegevens vernieuwen op de achtergrond
Vernieuwen op de achtergrond betekent dat uw favoriete dashboards, plus dashboards en rapporten die u in de afgelopen twee weken hebt bekeken, worden bijgewerkt met de gegevens in de Power BI-service (niet de gegevensbron). Als u met wifi bent verbonden, worden gegevens om de twee uur op de achtergrond bijgewerkt. Als u bent verbonden met een 3G-netwerk, wordt de inhoud elke 24 uur bijgewerkt.

U kunt het vernieuwen van gegevens op de achtergrond uitschakelen, bijvoorbeeld om netwerkgebruik te voorkomen. Controleer hiervoor de instellingen op uw apparaat.

> [!NOTE]
> Als u de mobiele Power BI-app op een iOS-apparaat gebruikt en uw organisatie Microsoft Intune MAM heeft geconfigureerd, is het vernieuwen van gegevens op de achtergrond uitgeschakeld. De volgende keer dat u de app gebruikt, worden de gegevens vanuit de Power BI-service op het web vernieuwd.
> 
> Lees meer over [het configureren van mobiele Power BI-apps met Microsoft Intune](../../service-admin-mobile-intune.md). 
> 
> 

## <a name="offline-indicators"></a>Offline-indicatoren
In Power BI wordt duidelijk aangegeven wanneer u offline gaat en weer online komt. Er zijn ook indicatoren voor ontbrekende dashboards, rapporten en tegels die niet offline beschikbaar zijn.

## <a name="limitations"></a>Beperkingen
Wanneer u offline bent met Power BI op uw mobiele apparaat, kunnen deze beperkingen optreden:

* Power BI kan maximaal 250 MB aan gegevens offline cachen.
* Sommige tegeltypen vereisen een actieve serververbinding en zijn dus niet offline beschikbaar. Voorbeelden hiervan zijn tegels met Bing-kaarten en verschillende aangepaste tegels.
* Hele Excel-werkmappen zijn niet offline beschikbaar in Power BI.
* U kunt mobiele rapporten en KPI's van Reporting Services offline zien, maar alleen als u ze eerder hebt bekeken terwijl er verbinding was. Deze onderdelen worden niet op de achtergrond vernieuwd. Dit gebeurt alleen wanneer u ze opent.
* Power BI Desktop-bestanden (.pbix) die zijn opgeslagen naar Power BI Report Server, zijn niet zichtbaar in de mobiele Power BI-apps. 
* Gepagineerde rapporten (RDL) zijn niet beschikbaar wanneer het netwerk offline is.

## <a name="next-steps"></a>Volgende stappen
Op basis van uw feedback kunnen we bepalen wat in de toekomst moet worden geïmplementeerd. Vergeet dus niet op andere functies te stemmen die u graag in de mobiele Power BI-apps zou willen zien. 

* [Power BI-apps voor mobiele apparaten](mobile-apps-for-mobile-devices.md)
* Volg @MSPowerBI op Twitter
* Deelnemen aan conversaties in de [Power BI-community](http://community.powerbi.com/)
* [Wat is Power BI?](../../power-bi-overview.md)

