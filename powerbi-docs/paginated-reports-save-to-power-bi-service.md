---
title: Een gepagineerd rapport publiceren in de Power BI-service (preview)
description: In deze zelfstudie leert u hoe een gepagineerd rapport kunt publiceren in de Power BI-service door het te uploaden vanaf de lokale computer.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.openlocfilehash: 58fc7a6b8ebc5519c1c4bb1835758ca94ba225d2
ms.sourcegitcommit: 8fda7843a9f0e8193ced4a7a0e5c2dc5386059a6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58174540"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service-preview"></a>Een gepagineerd rapport publiceren in de Power BI-service (preview)

In dit artikel krijgt u informatie over het publiceren van een gepagineerd rapport in de Power BI-service door het te uploaden vanaf de lokale computer. U kunt gepagineerde rapporten uploaden naar Mijn werkruimte of een andere ruimte, zolang deze werkruimte zich maar in een Premium-capaciteit bevindt. Ga naar het ruitvormige pictogram ![Ruitvormig pictogram voor de Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) naast de naam van een werkruimte. 

Als de gegevensbron van het rapport on-premises is, moet u [een gateway maken](#create-a-gateway) nadat u het rapport hebt geüpload.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Een werkruimte toevoegen aan een Premium-capaciteit

Als u naast de naam van de werkruimte het ruitvormige pictogram ![Ruitvormig pictogram voor de Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) niet ziet, moet u de werkruimte toevoegen aan een Premium-capaciteit. 

1. Selecteer **Werkruimten** en selecteer het beletselteken (**...**) naast de naam van de werkruimte. Selecteer vervolgens **Werkruimte bewerken**.

    ![Werkruimte bewerken selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Vouw in het dialoogvenster **Werkruimte bewerken** de optie **Geavanceerd** uit. Schuif **Toegewezen capaciteit** vervolgens naar **Aan**.

    ![Toegewezen capaciteit selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Mogelijk kunt u dit niet wijzigen. Zo niet, vraag de beheerder van de Power BI Premium-capaciteit dan om u toewijzingsrechten te verlenen om uw werkruimte toe te voegen aan een Premium-capaciteit.


## <a name="upload-a-paginated-report"></a>Een gepagineerd rapport uploaden

1. Maak uw gepagineerde rapport in Report Builder en sla het op de lokale computer op.

1. Open de Power BI-service in een browser en blader naar de Premium-werkruimte waarin u het rapport wilt publiceren. U ziet nu het ruitvormige pictogram ![Ruitvormig pictogram voor de Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) naast de naam. 

1. Selecteer **Gegevens ophalen**.

    ![Gegevens ophalen in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Selecteer in het vak **Bestanden** de optie **Ophalen**.

    ![Bestanden ophalen in Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selecteer **Lokaal bestand** > blader naar het gepagineerde rapport > **Openen**.

    ![Lokaal bestand selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selecteer **Doorgaan** > **Referenties bewerken**.

    ![Referenties bewerken selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configureer uw referenties > **Aanmelden**.

    ![Referenties bewerken](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Het rapport wordt weergegeven in de lijst met rapporten.

    ![Gepagineerd rapport in de lijst met rapporten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecteer het rapport om het te openen in de Power BI-service. Als het rapport parameters bevat, moet u deze selecteren voordat u het rapport kunt weergeven.
 
    ![Parameters selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Een gateway maken

Als de gegevensbron van het rapport on-premises is, moet u, net als bij elk ander Power BI-rapport, een gateway maken of verbinding maken met een gateway om de gegevens te openen.

1. Selecteer naast de rapportnaam de optie **Beheren**.

   ![Het gepagineerde rapport beheren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Zie het artikel van de Power BI-service [Een gateway installeren](service-gateway-install.md) voor de details en de volgende stappen.

### <a name="gateway-limitations"></a>Beperkingen van een gateway

Momenteel bieden gateways geen ondersteuning voor parameters met meerdere waarden.


## <a name="next-steps"></a>Volgende stappen

- [Een gepagineerd rapport weergeven in de Power BI-service](paginated-reports-view-power-bi-service.md)
- [Wat zijn gepagineerde rapporten in Power BI Premium? (Preview)](paginated-reports-report-builder-power-bi.md)

