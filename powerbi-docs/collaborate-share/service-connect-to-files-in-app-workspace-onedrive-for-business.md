---
title: Verbinding maken met bestanden in OneDrive voor een klassieke werk ruimte
description: Meer informatie over het opslaan en maken van verbinding met uw Excel-, CSV-en Power BI Desktop-bestanden in de OneDrive voor uw klassieke Power BI-werk ruimte.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/28/2021
LocalizationGroup: Share your work
ms.openlocfilehash: f6544a137b8f656e938db4516de5e8c0685394b4
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085797"
---
# <a name="connect-to-files-stored-in-onedrive-for-a-classic-workspace"></a>Verbinding maken met bestanden die zijn opgeslagen in OneDrive voor een klassieke werk ruimte
Wanneer u [een *klassieke* werk ruimte in Power BI maakt](service-create-workspaces.md), maakt u ook een Microsoft 365 groep met een gekoppelde OneDrive voor bedrijven. In dit artikel wordt uitgelegd hoe u uw Excel-, CSV-en Power BI Desktop-bestanden opslaat en bijwerkt in OneDrive voor Bedrijven. Wijzigingen worden automatisch doorgevoerd in de Power BI-rapporten en dashboards op basis van de bestanden.

> [!NOTE]
> De *nieuwe* werk ruimte-ervaring wijzigt de relatie tussen Power bi-werk ruimten en Microsoft 365 groepen. Er wordt niet automatisch een Microsoft 365-groep gemaakt wanneer u een van de nieuwe werkruimten maakt. U kunt ook [een werk ruimte in OneDrive instellen voor een nieuwe werk ruimte](service-create-the-new-workspaces.md#set-a-workspace-onedrive).

Het toevoegen van bestanden aan de klassieke werk ruimte is een proces in twee stappen: 

1. Eerst [uploadt u bestanden naar de OneDrive voor bedrijven](#1-upload-files-to-the-onedrive-for-business-for-your-workspace) voor uw werkruimte.
2. Vervolgens maakt u [vanuit Power BI verbinding met deze bestanden](#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Werkruimten zijn alleen beschikbaar met een [Power BI Pro-licentie](../fundamentals/service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Upload bestanden naar de OneDrive voor bedrijven voor uw werkruimte
1. Selecteer de pijl naast Werkruimten in de Power BI-service > selecteer het weglatingsteken ( **…** ) naast de naam van uw werkruimte. 
   
   ![Schermopname van de Power BI-werkruimte met de naam van de geselecteerde werkruimte.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Selecteer **Bestanden** om de OneDrive voor bedrijven voor uw werkruimte in Microsoft 365 te openen.
   
   > [!NOTE]
   > Als in het menu van de werkruimte niet de optie **Bestanden** wordt weergegeven, moet u **Leden** selecteren om de OneDrive voor bedrijven voor uw werkruimte te openen. Selecteer hier **Bestanden**. Microsoft 365 installeert een opslaglocatie voor OneDrive voor bestanden van de groepswerkruimte van uw app. Dit proces kan enige tijd duren.
   > 
   > 
3. Hier kunt u uw bestanden uploaden naar de OneDrive voor bedrijven voor uw werkruimte. Selecteer **Uploaden**, en navigeer naar uw bestanden.
   
   ![Schermopname van OneDrive voor Bedrijven met de navigatie voor het uploaden van een bestand.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Excel-bestanden importeren als gegevenssets of Excel Online-werkmappen
Nu uw bestanden zijn opgeslagen in de OneDrive voor bedrijven voor uw werkruimte, kunt u kiezen. U kunt: 

* [De gegevens als een gegevensset importeren uit de Excel-werkmap](../connect-data/service-get-data-from-files.md). Vervolgens kunt u de gegevens gebruiken om rapporten en dashboards te maken die u in een webbrowser en op mobiele apparaten kunt weergeven.
* Of [verbinding maken met een complete Excel-werkmap in Power BI](../connect-data/service-excel-workbook-files.md) en deze precies weergeven als in Excel Online wordt weergegeven.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Bestanden importeren in uw werkruimte of hiermee verbinding maken
1. Schakel in Power BI over naar de werkruimte, zodat de naam van de werkruimte in de linkerbovenhoek wordt vermeld. 
2. Selecteer **Gegevens ophalen** onderaan het navigatievenster. 
   
   ![Schermopname van de knop Gegevens ophalen in het navigatiedeelvenster.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. Selecteer in het vak **Bestanden** de optie **Ophalen**.
   
   ![Schermopname van het dialoogvenster Bestanden met de knop Ophalen.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Selecteer **OneDrive** - *naam van uw werkruimte*.
   
    ![Schermopname van drie tegels om uw werkruimte te selecteren met Lokaal bestand, OneDrive en SharePoint.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Selecteer het gewenste bestand > **Verbinding maken**.
   
    U moet nu aangeven of u [de gegevens uit de Excel-werkmap wilt importeren](../connect-data/service-get-data-from-files.md) of [verbinding wilt maken met de complete Excel-werkmappen](../connect-data/service-excel-workbook-files.md).
6. Selecteer **Importeren** of **verbinding maken**.
   
    ![Schermopname van het dialoogvenster OneDrive voor Bedrijven met Importeren uit Excel of Verbinden met Excel.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Als u **Importeren** selecteert, verschijnt de werkmap op het tabblad **Gegevenssets**. 
   
    ![Schermopname van de werkruimten in Power BI met het tabblad Gegevenssets.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Als u **Verbinding maken** selecteert, bevindt de werkmap zich op het tabblad **Werkmappen**.
   
    ![Schermopname van de werkruimten in Power BI met het tabblad Workbooks.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Volgende stappen
* [Apps en werkruimten maken in Power BI](../collaborate-share/service-create-distribute-apps.md)
* [Gegevens importeren uit Excel-werkmappen](../connect-data/service-get-data-from-files.md)
* [Verbinding maken met complete Excel-werkmappen](../connect-data/service-excel-workbook-files.md
* Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
* Feedback? Ga naar [Power BI ideeën](https://ideas.powerbi.com/forums/265200-power-bi)
