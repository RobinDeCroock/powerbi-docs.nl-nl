---
title: Verbinding maken met bestanden in OneDrive voor een Power BI-werkruimte
description: Meer informatie over het opslaan van en verbinding maken met uw Excel-, CSV- en Power BI Desktop-bestanden op de OneDrive voor uw Power BI-werkruimte.
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 62d0282af47b0d57a0b9ac307b422191b440b45c
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564100"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Verbinding maken met in OneDrive opgeslagen bestanden voor uw Power BI-werkruimte
Wanneer u [een werkruimte hebt gemaakt in Power BI](../collaborate-share/service-create-distribute-apps.md), kunt u uw Excel-, CSV- en Power BI Desktop-bestanden op de OneDrive voor bedrijven opslaan voor uw Power BI-werkruimte. U kunt de bestanden die u in OneDrive opslaat gewoon blijven bewerken. Wijzigingen worden automatisch doorgevoerd in de Power BI-rapporten en dashboards op basis van de bestanden. 

> [!NOTE]
> In de nieuwe werkruimte-ervaring is de relatie tussen Power BI-werkruimten en Microsoft 365-groepen gewijzigd. Er wordt niet automatisch een Microsoft 365-groep gemaakt wanneer u een van de nieuwe werkruimten maakt. Lees hier meer over [het maken van de nieuwe werkruimten](../collaborate-share/service-create-the-new-workspaces.md).

De bestanden worden in twee stappen toegevoegd aan uw werkruimte: 

1. Eerst [uploadt u bestanden naar de OneDrive voor bedrijven](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-workspace) voor uw werkruimte.
2. Vervolgens maakt u [vanuit Power BI verbinding met deze bestanden](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Werkruimten zijn alleen beschikbaar bij [Power BI Pro](../fundamentals/service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Upload bestanden naar de OneDrive voor bedrijven voor uw werkruimte
1. Selecteer de pijl naast Werkruimten in de Power BI-service > selecteer het weglatingsteken ( **…** ) naast de naam van uw werkruimte. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Selecteer **Bestanden** om de OneDrive voor bedrijven voor uw werkruimte in Microsoft 365 te openen.
   
   > [!NOTE]
   > Als in het menu van de werkruimte niet de optie **Bestanden** wordt weergegeven, moet u **Leden** selecteren om de OneDrive voor bedrijven voor uw werkruimte te openen. Selecteer hier **Bestanden**. Microsoft 365 installeert een opslaglocatie voor OneDrive voor bestanden van de groepswerkruimte van uw app. Dit proces kan enige tijd duren.
   > 
   > 
3. Hier kunt u uw bestanden uploaden naar de OneDrive voor bedrijven voor uw werkruimte. Selecteer **Uploaden**, en navigeer naar uw bestanden.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Excel-bestanden importeren als gegevenssets of Excel Online-werkmappen
Nu uw bestanden zijn opgeslagen in de OneDrive voor bedrijven voor uw werkruimte, kunt u kiezen. U kunt: 

* [De gegevens als een gegevensset importeren uit de Excel-werkmap](service-get-data-from-files.md). Vervolgens kunt u de gegevens gebruiken om rapporten en dashboards te maken die u in een webbrowser en op mobiele apparaten kunt weergeven.
* Of [verbinding maken met een complete Excel-werkmap in Power BI](service-excel-workbook-files.md) en deze precies weergeven als in Excel Online wordt weergegeven.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Bestanden importeren in uw werkruimte of hiermee verbinding maken
1. Schakel in Power BI over naar de werkruimte, zodat de naam van de werkruimte in de linkerbovenhoek wordt vermeld. 
2. Selecteer **Gegevens ophalen** onderaan het navigatievenster. 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Selecteer in het vak **Bestanden** de optie **Ophalen**.
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Selecteer **OneDrive** - *naam van uw werkruimte*.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Selecteer het gewenste bestand > **Verbinding maken**.
   
    U moet nu aangeven of u [de gegevens uit de Excel-werkmap wilt importeren](service-get-data-from-files.md) of [verbinding wilt maken met de complete Excel-werkmappen](service-excel-workbook-files.md).
6. Selecteer **Importeren** of **verbinding maken**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Als u **Importeren** selecteert, verschijnt de werkmap op het tabblad **Gegevenssets**. 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Als u **Verbinding maken** selecteert, bevindt de werkmap zich op het tabblad **Werkmappen**.
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Volgende stappen
* [Apps en werkruimten maken in Power BI](../collaborate-share/service-create-distribute-apps.md)
* [Gegevens importeren uit Excel-werkmappen](service-get-data-from-files.md)
* [Verbinding maken met complete Excel-werkmappen](service-excel-workbook-files.md)
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
* Feedback? Ga naar [Power BI ideeën](https://ideas.powerbi.com/forums/265200-power-bi)
