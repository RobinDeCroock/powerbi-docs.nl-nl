---
title: Geografische filters in Power BI Desktop instellen voor de mobiele apps
description: Als u geografische filters in het model in Power BI Desktop instelt, kunt u gegevens voor uw locatie automatisch filteren in de mobiele Power BI-apps.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2018
ms.author: maggies
LocalizationGroup: Model your data
ms.openlocfilehash: b8887ba39d3c6d3123d3308eddba2994fbfe6485
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61295983"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-the-mobile-apps"></a>Geografische filters in Power BI Desktop instellen voor de mobiele apps
In Power BI Desktop kunt u [geografische gegevens categoriseren](desktop-data-categorization.md) voor een kolom, zodat Power BI Desktop weet hoe waarden in visuele elementen moeten worden afgehandeld in een rapport. Een extra voordeel is dat wanneer uw collega's het desbetreffende rapport weergeven in de mobiele Power BI-apps voor iOS, automatisch de geografische filters in Power BI worden verstrekt die overeenkomen met waar u zich bevindt. 

Stel dat u een verkoopmanager bent en reist om met klanten af te spreken en u snel de totale verkoop en omzet wilt filteren voor de specifieke klant die u een bezoek gaat brengen. U wilt de gegevens opsplitsen voor uw huidige locatie, of dit nu per provincie, plaats of een exact adres is. Later, als u tijd over hebt, wilt u andere klanten in de buurt een bezoek brengen. U kunt [het rapport filteren op uw locatie om die klanten te vinden](consumer/mobile/mobile-apps-geographic-filtering.md).

> [!NOTE]
> U kunt alleen filteren op locatie in de mobiele app als de geografische namen in het rapport in het Engels zijn, bijvoorbeeld ‘New York’ of ‘Germany’.
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>Geografische gegevens in uw rapport identificeren
1. Schakel over naar Gegevensweergave in Power BI Desktop ![Het pictogram Gegevensweergave](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png).
2. Selecteer een kolom met geografische gegevens, bijvoorbeeld de kolom Plaats.
   
    ![De kolom Plaats](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. Selecteer op het tabblad **Model maken** de optie **Gegevenscategorie**, en vervolgens de juiste categorie, in dit voorbeeld **Plaats**.
   
    ![Het vak Gegevenscategorie](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. Ga verder met het instellen van de categorieën met geografische gegevens voor alle andere velden in het model. 
   
   > [!NOTE]
   > U kunt meerdere kolommen voor elke gegevenscategorie instellen in een model, maar als u het model maakt, kunt u niet filteren op geografische locatie in de mobiele Power BI-app. Voor het gebruik van geografische filters in de mobiele apps, stelt u slechts één kolom in voor elke gegevenscategorie; bijvoorbeeld slechts één kolom **Plaats**, één kolom **Staat of provincie** en één kolom **Land**. 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>Visuele elementen maken bij uw geografische gegevens
1. Schakel over naar Rapportweergave ![Het pictogram Rapportweergave](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png)en maak visuele elementen die gebruikmaken van de geografische velden in uw gegevens. 
   
    ![Rapport met kaart](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    In dit voorbeeld bevat het model ook een berekende kolom, die de plaats en provincie in één kolom samenbrengt. Lees meer over [het maken van berekende kolommen in Power BI Desktop](desktop-calculated-columns.md).
   
    ![Het veld Plaats + Provincie](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Publiceer het rapport naar de Power BI-service.

## <a name="view-the-report-in-power-bi-mobile-app"></a>Het rapport weergeven in de mobiele Power BI-app
1. Open het rapport in een van de [mobiele Power BI-apps](consumer/mobile/mobile-apps-for-mobile-devices.md).
2. Als u zich op een geografische locatie bevindt waarover het rapport gegevens bevat, kunt u het automatisch filteren op uw locatie.
   
    ![Geofilter in mobiele app](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

Lees meer over het [filteren van een rapport op locatie in de mobiele Power BI-apps](consumer/mobile/mobile-apps-geographic-filtering.md).

## <a name="next-steps"></a>Volgende stappen
* [Gegevenscategorisatie in Power BI Desktop](desktop-data-categorization.md)  
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

