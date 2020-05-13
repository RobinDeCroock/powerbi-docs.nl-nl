---
title: Publiceren vanuit Power BI Desktop
description: Publiceren vanuit Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83333482"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Gegevenssets en rapporten van Power BI Desktop publiceren
Als u een Power BI Desktop-bestand publiceert naar de Power BI-service, publiceert u de gegevens in het model naar uw Power BI-werkruimte. Dit geldt ook voor rapporten die u in de **rapportweergave** hebt gemaakt. U ziet een nieuwe gegevensset met dezelfde naam (en eventuele rapporten) in uw werkruimtenavigator.

Het publiceren vanuit Power BI Desktop heeft hetzelfde effect als **Gegevens ophalen** gebruiken in Power BI om verbinding te maken met een Power BI Desktop-bestand en er gegevens naar te uploaden.

> [!NOTE]
> Wijzigingen die u in het rapport in Power BI aanbrengt, worden niet opnieuw opgeslagen in het oorspronkelijke Power BI Desktop-bestand. Dit geldt ook wanneer u visualisaties in rapporten toevoegt, verwijdert of wijzigt.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Power BI Desktop-gegevenssets en -rapporten publiceren
1. In Power BI Desktop kiest u **Bestand** \> **Publiceren** \> **Publiceren naar Power BI** of klikt u op **Publiceren** op het lint.  

   ![De knop Publiceren](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Meld u aan bij Power BI.
3. Selecteer het doel.

   ![Publicatiebestemming selecteren](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Wanneer de publicatie is voltooid, ontvangt u een koppeling naar uw rapport. Selecteer de koppeling om het rapport in uw Power BI-site te openen.

![Het dialoogvenster Publiceren geslaagd](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Een vanuit Power BI Desktop gepubliceerde gegevensset opnieuw publiceren of vervangen
De gegevensset en eventuele rapporten die u in Power BI Desktop hebt gemaakt, worden geüpload naar uw Power BI-site als u een Power BI Desktop-bestand publiceert. Als u uw Power BI Desktop-bestand opnieuw publiceert, wordt de gegevensset op uw Power BI-site vervangen door de bijgewerkte gegevensset uit het Power BI Desktop-bestand.

Dit proces is erg eenvoudig, maar u mag een paar dingen niet vergeten:

* Als er al twee of meer gegevenssets in Power BI zijn met dezelfde naam als het Power BI Desktop-bestand, kan het publiceren mislukken. Zorg ervoor dat u slechts één gegevensset in Power BI hebt met dezelfde naam. U kunt het bestand ook een andere naam geven en dit publiceren, waardoor u een nieuwe gegevensset maakt met dezelfde naam als het bestand.
* Als u een kolom of meting verwijdert of een andere naam geeft, raken eventuele visuele elementen die al in Power BI met dat veld voorkomen, beschadigd. 
* Power BI negeert een aantal wijzigingen aan de indeling van bestaande kolommen. Bijvoorbeeld als u de indeling van een kolom wijzigt van 0,25 in 25%.
* Stel dat u een vernieuwingsschema hebt dat is geconfigureerd voor uw bestaande gegevensset in Power BI. Wanneer u nieuwe gegevensbronnen aan uw bestand toevoegt en het bestand vervolgens opnieuw publiceert, moet u zich hierbij aanmelden vóór de volgende geplande vernieuwing.
* Wanneer u opnieuw een gegevensset publiceert die eerder vanaf Power BI Desktop is gepubliceerd en u een vernieuwingsschema hebt gedefinieerd, wordt het vernieuwen van de gegevensset gestart zodra u deze opnieuw hebt gepubliceerd. 

