---
title: Een gepagineerd rapport publiceren in de Power BI-service
description: In deze zelfstudie leert u hoe een gepagineerd rapport kunt publiceren in de Power BI-service door het te uploaden vanaf de lokale computer.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: 0207cbdbc3fae8636f8fd73a008d54ee7d10c5f9
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/07/2020
ms.locfileid: "78921603"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Een gepagineerd rapport publiceren in de Power BI-service

In dit artikel krijgt u informatie over het publiceren van een gepagineerd rapport in de Power BI-service door het te uploaden vanaf de lokale computer. U kunt gepagineerde rapporten uploaden naar Mijn werkruimte of een andere ruimte, zolang deze werkruimte zich maar in een Premium-capaciteit bevindt. Ga naar het ruitvormige pictogram ![Ruitvormig pictogram voor de Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) naast de naam van een werkruimte. 

Als de gegevensbron van het rapport on-premises is, moet u een gateway maken nadat u het rapport hebt geüpload. Zie de sectie [Een gateway maken](#create-a-gateway) verderop in dit artikel.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Een werkruimte toevoegen aan een Premium-capaciteit

Als u naast de naam van de werkruimte het ruitvormige pictogram ![Ruitvormig pictogram voor de Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) niet ziet, moet u de werkruimte toevoegen aan een Premium-capaciteit. 

1. Selecteer **Werkruimten** en selecteer het beletselteken ( **...** ) naast de naam van de werkruimte. Selecteer vervolgens **Werkruimte bewerken**.

    ![Werkruimte bewerken selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Vouw in het dialoogvenster **Werkruimte bewerken** de optie **Geavanceerd** uit. Schuif **Toegewezen capaciteit** vervolgens naar **Aan**.

    ![Toegewezen capaciteit selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Mogelijk kunt u dit niet wijzigen. Zo niet, vraag de beheerder van de Power BI Premium-capaciteit dan om u toewijzingsrechten te verlenen om uw werkruimte toe te voegen aan een Premium-capaciteit.

## <a name="from-report-builder-publish-a-paginated-report"></a>Vanuit Report Builder een gepagineerd rapport publiceren

1. Maak uw gepagineerde rapport in Report Builder en sla het op de lokale computer op.

1. Selecteer in het menu **Bestand** van Report Builder de optie **Opslaan als**.

    ![Menu Bestand > Opslaan > Opslaan als](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Als u nog niet bent aangemeld bij Power BI, moet u zich nu aanmelden of een nieuw account maken. Selecteer **Aanmelden** in de rechterbovenhoek van Report Builder en voer de stappen uit.

2. Selecteer in de lijst met werkruimten aan de linkerkant een werkruimte met het ruitpictogram ![ruitpictogram voor Power BI Premium-capaciteit](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) naast de naam. Typ een **Bestandsnaam** in het vak > **Opslaan**. 

    ![Een Premium-werkruimte selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Open de Power BI-service in een browser en blader naar de Premium-werkruimte waarin u het gepagineerde rapport hebt gepubliceerd. Op het tabblad **Rapporten** wordt het rapport weergegeven.

    ![Gepagineerd rapport in de lijst met rapporten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Selecteer het gepagineerde rapport om dit in de Power BI-service te openen. Als het rapport parameters bevat, moet u deze selecteren voordat u het rapport kunt weergeven.

    ![Parameters selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Als de gegevensbron van uw rapport zich on-premises bevindt, leest u in dit artikel hoe u [een gateway maakt](#create-a-gateway) om toegang te krijgen tot de gegevensbron.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Een gepagineerd rapport uploaden vanuit de Power BI-service

U kunt ook beginnen met de Power BI-service en een gepagineerd rapport uploaden.

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

   Op het tabblad **Rapporten** wordt het rapport weergegeven.

    ![Gepagineerd rapport in de lijst met rapporten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecteer het rapport om het te openen in de Power BI-service. Als het rapport parameters bevat, moet u deze selecteren voordat u het rapport kunt weergeven.
 
    ![Parameters selecteren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Als de gegevensbron van uw rapport zich on-premises bevindt, leest u in dit artikel hoe u [een gateway maakt](#create-a-gateway) om toegang te krijgen tot de gegevensbron.

## <a name="create-a-gateway"></a>Een gateway maken

Als de gegevensbron van het rapport on-premises is, moet u, net als bij elk ander Power BI-rapport, een gateway maken of verbinding maken met een gateway om de gegevens te openen.

1. Selecteer naast de rapportnaam de optie **Beheren**.

   ![Het gepagineerde rapport beheren](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Zie het artikel van de Power BI-service [Wat is een on-premises gegevensgateway?](../service-gateway-onprem.md) voor details en volgende stappen.

### <a name="gateway-limitations"></a>Beperkingen van een gateway

Momenteel bieden gateways geen ondersteuning voor parameters met meerdere waarden.


## <a name="next-steps"></a>Volgende stappen

- [Een gepagineerd rapport weergeven in de Power BI-service](../consumer/paginated-reports-view-power-bi-service.md)
- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Zelfstudie: Gepagineerde Power BI-rapporten insluiten in een toepassing voor uw klanten](../developer/embed-paginated-reports-customers.md)

