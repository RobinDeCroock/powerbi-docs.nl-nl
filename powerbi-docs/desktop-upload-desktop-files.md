---
title: Publiceren vanuit Power BI Desktop
description: Publiceren vanuit Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f67f73dd66da7f1d3e8d84a3373a15d20f81645e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513807"
---
# <a name="publish-from-power-bi-desktop"></a>Publiceren vanuit Power BI Desktop
Als u een **Power BI Desktop**-bestand publiceert naar de **Power BI-service**, worden de gegevens in het model en eventuele rapporten die u in de **rapportweergave** hebt gemaakt, gepubliceerd naar uw Power BI-werkruimte. U ziet een nieuwe gegevensset met dezelfde naam (en eventuele rapporten) in uw werkruimtenavigator.

Het publiceren vanuit **Power BI Desktop** heeft hetzelfde effect als **Gegevens ophalen** gebruiken in Power BI om verbinding te maken met een **Power BI Desktop**-bestand en er gegevens naar te uploaden.

> [!NOTE]
> Als u wijzigingen aanbrengt aan het rapport in Power BI (bijvoorbeeld visuals toevoegen aan, verwijderen uit of wijzigen in rapporten), worden deze niet opgeslagen in het oorspronkelijke **Power BI Desktop**-bestand.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Power BI Desktop-gegevenssets en -rapporten publiceren
1. Power BI Desktop selecteert u in **bestand** \> **publiceren** \> **publiceren naar Power BI** of klik op **publiceren** op de lint.  

   ![De knop Publiceren](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Meld u aan bij Power BI.
3. Selecteer het doel.

   ![Publicatiebestemming selecteren](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

Wanneer u klaar bent, ontvangt u een koppeling naar uw rapport. Klik op de koppeling om het rapport in uw Power BI-site te openen.

![Het dialoogvenster Publiceren geslaagd](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Een vanuit Power BI Desktop gepubliceerde gegevensset opnieuw publiceren of vervangen
Als u een **Power BI Desktop**-bestand publiceert, worden de gegevensset en eventuele rapporten die u in **Power BI Desktop** hebt gemaakt, geüpload naar uw Power BI-site. Als u uw **Power BI Desktop**-bestand opnieuw publiceert, wordt de gegevensset op uw Power BI-site vervangen door de bijgewerkte gegevensset uit het **Power BI Desktop**-bestand.

Dit is allemaal vrij eenvoudig, maar er zijn enkele dingen die u moet weten:

* Als u al twee of meer gegevenssets in Power BI hebt met dezelfde naam als het **Power BI Desktop**-bestand, kan het publiceren mislukken. Zorg ervoor dat u slechts één gegevensset in Power BI hebt met dezelfde naam. U kunt het bestand ook een andere naam geven en dit publiceren, waardoor u een nieuwe gegevensset maakt met dezelfde naam als het bestand.
* Als u een kolom of meting verwijdert of een andere naam geeft, raken eventuele visuele elementen die al in Power BI met dat veld voorkomen, beschadigd. 
* Power BI negeert een aantal wijzigingen aan de indeling van bestaande kolommen. Bijvoorbeeld als u de indeling van een kolom wijzigt van 0,25 in 25%.
* Als u een vernieuwingsschema voor uw bestaande gegevensset in Power BI hebt geconfigureerd en u voegt nieuwe gegevensbronnen aan uw bestand toe om ze vervolgens opnieuw te publiceren, moet u zich bij deze gegevensbronnen aanmelden in *Gegevensbronnen beheren* voordat u een nieuwe, geplande vernieuwing uitvoert.

