---
title: Parameterinstellingen bewerken in de Power BI-service
description: Queryparameters worden gemaakt in Power BI Desktop, maar kunnen worden gecontroleerd en bijgewerkt in Power BI-service
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8db6f106ecc2285cb66ff980bc72fa666456f81a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61225978"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Parameterinstellingen bewerken in de Power BI-service
Rapportmakers voegen queryparameters toe aan rapporten in Power BI Desktop. Ze kunnen aan de hand van parameters gedeelten van rapporten maken die afhankelijk zijn van een of meerdere parameter*waarden*. Een maker van een rapport kan bijvoorbeeld een parameter maken waarmee de gegevens worden beperkt tot een land/regio of een parameter maken waarmee acceptabele indelingen worden opgegeven voor bijvoorbeeld datum-, tijd- en tekstvelden.

![Tabblad Start met de optie Parameters beheren in Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Parameters controleren en bewerken in Power BI-service

Als rapportmaker definieert u parameters in Desktop. Wanneer u [dat rapport naar Power BI-service publiceert](desktop-upload-desktop-files.md), worden ook de parameterinstellingen en selecties meegenomen. U kunt sommige parameterinstellingen controleren en bewerken in de Power BI-service: niet de parameters waarmee de beschikbare gegevens worden beperkt, maar wel de parameters waarmee acceptabele waarden worden gedefinieerd en beschreven.

1. Selecteer in Power BI-service het tandwielpictogram ![tandwielpictogram](media/service-parameters/power-bi-cog.png) om **Instellingen** te openen.

2. Selecteer het tabblad **Gegevenssets** en markeer een gegevensset in de lijst. 
    
    ![Het venster Instellingen waarin het tabblad Gegevenssets is geselecteerd](media/service-parameters/power-bi-select-dataset2.png)

3. Vouw **Parameters** uit.  Als de geselecteerde gegevensset geen parameters bevat, verschijnt een bericht met een koppeling naar Meer informatie over queryparameters. Als de gegevensset wel parameters bevat, worden deze weergegeven wanneer u **Parameters** uitvouwt. 

    ![Het venster Instellingen waarin Parameters is uitgevouwen](media/service-parameters/power-bi-settings.png)

    Controleer de parameterinstellingen en breng eventueel wijzigingen aan. Grijze velden kunnen niet worden bewerkt. 


## <a name="next-steps"></a>Volgende stappen
Een ad-hocmanier om eenvoudige parameters toe te voegen, is [de URL wijzigen](service-url-filters.md).