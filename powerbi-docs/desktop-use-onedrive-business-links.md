---
title: Koppelingen van OneDrive voor Bedrijven gebruiken in Power BI Desktop
description: Koppelingen van OneDrive voor Bedrijven gebruiken in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8597904e2753f198b3f99cdcad6062d756b734a0
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65513782"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Koppelingen van OneDrive voor Bedrijven gebruiken in Power BI Desktop
Veel gebruikers hebben Excel-werkmappen opgeslagen op hun OneDrive voor Bedrijven-station. Het zou mooi zijn deze met Power BI Desktop te gebruiken. Met **Power BI Desktop** kunt u onlinekoppelingen voor **Excel-bestanden** gebruiken die in **OneDrive voor Bedrijven** zijn opgeslagen en waar u rapporten en visuele elementen mee kunt maken. U kunt een **OneDrive voor Bedrijven** groepsaccount of een individueel account van **OneDrive voor Bedrijven** gebruiken.

Voor een onlinekoppeling van **OneDrive voor Bedrijven** zijn een paar specifieke stappen vereist. In de volgende sectie worden die stappen uitgelegd, zodat u de bestandskoppeling met groepen op verschillende computers en met uw collega's kunt delen.

## <a name="get-a-link-from-excel-starting-in-the-browser"></a>Een koppeling vanuit Excel ophalen, te beginnen in de browser
1. Ga via de browser naar uw locatie van OneDrive voor Bedrijven. Klik met de rechtermuisknop o het bestand dat u wilt gebruiken en selecteer **Openen in Excel**.
   
   > [!NOTE]
   > De interface van uw browser kan afwijken van de volgende afbeelding. U kunt **Openen in Excel** (voor bestanden) op diverse manieren selecteren in de browserinterface van **OneDrive voor Bedrijven**. U kunt elke optie gebruiken om het bestand in Excel te openen.
   > 
   > 
   
   ![](media/desktop-use-onedrive-business-links/odb-links_02.png)
2. In **Excel** selecteert u **Bestand > Info** en vervolgens de koppeling boven de knop **Werkmap beveiligen**. Selecteer **Koppeling naar het Klembord kopiëren** (mogelijk staat in uw versie **Pad naar het Klembord kopiëren**).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_03.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Koppeling gebruiken in Power BI Desktop
In Power BI Desktop kunt u de koppeling gebruiken die u zojuist naar Klembord hebt gekopieerd. Voer de volgende stappen uit:

1. In Power BI Desktop selecteert u **Gegevens ophalen > Web**.
   
   ![](media/desktop-use-onedrive-business-links/odb-links_04.png)
2. Plak de koppeling in het dialoogvenster **Vanaf web** (selecteer OK nog **niet**).
   
    ![](media/desktop-use-onedrive-business-links/odb-links_05.png)
3. Let op de tekenreeks *?web=1* aan het eind van de koppeling. *Verwijder dit gedeelte van de URL* **voordat** u **OK** selecteert, zodat **Power BI Desktop** het bestand kan vinden.
4. Als u door **Power BI Desktop** om uw referenties wordt gevraagd, kiest u **Windows** (voor on-premises SharePoint-sites) of **Organisatieaccount** (voor Office 365- of OneDrive voor Bedrijven-sites).
   
   ![](media/desktop-use-onedrive-business-links/odb-links_06.png)

Het **navigatievenster** verschijnt. Hier kunt u een selectie maken in een lijst met tabellen, werkbladen en bereiken uit de Excel-werkmap. Hier kunt u ook het OneDrive voor Bedrijven-bestand gebruiken, net zoals u dat met een ander Excel-bestand doet. U kunt er rapporten maken en deze gebruiken in gegevenssets, net zoals u dat met een andere gegevensbron zou doen.

> [!NOTE]
> Als u een bestand van **OneDrive voor Bedrijven** als een gegevensbron in de Power BI-service wilt gebruiken, waarbij **Service Refresh** voor dat bestand is ingeschakeld, moet u **OAuth2** als **verificatiemethode** selecteren bij het configureren van uw vernieuwingsinstellingen. Als u dat niet doet, krijgt u een foutmelding (bijvoorbeeld *Gegevensbronreferenties bijwerken is mislukt*) als u verbinding wilt maken of vernieuwen. Als u **OAuth2** als verificatiemethode selecteert, wordt deze fout voorkomen.
> 
> 

