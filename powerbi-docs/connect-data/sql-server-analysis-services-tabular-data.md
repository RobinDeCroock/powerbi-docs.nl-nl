---
title: Live SQL Server Analysis Services-gegevens in Power BI
description: Live SQL Server Analysis Services-gegevens in Power BI. Dit wordt gedaan via een gegevensbron die is geconfigureerd voor een bedrijfsgateway.
author: Minewiskan
ms.author: davidi
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.reviewer: ''
ms.custom: ''
ms.date: 08/10/2017
LocalizationGroup: Data from databases
ms.openlocfilehash: 81d2f350c524335d3aa8c7fbb9c82a6cb045e9e5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96391893"
---
# <a name="sql-server-analysis-services-live-data-in-power-bi"></a>Live SQL Server Analysis Services-gegevens in Power BI

U kunt in Power BI op twee manieren verbinding maken met een live SQL Server Analysis Services-server. In **Gegevens ophalen** kunt u verbinding maken met een SQL Server Analysis Services-server of u kunt verbinding maken met een [Power BI Desktop-bestand](service-desktop-files.md) of [Excel-werkmap](service-excel-workbook-files.md) die al verbonden is met een Analysis Services-server. Microsoft raadt als best practice sterk aan om Power BI Desktop te gebruiken vanwege de uitgebreide functionaliteit van de set hulpmiddelen en de mogelijkheid om lokaal een back-up van het Power BI Desktop-bestand te onderhouden.

>[!IMPORTANT]
> * Als u verbinding wilt maken met een live Analysis Services-server, moet er een on-premises gegevensgateway zijn geïnstalleerd en geconfigureerd door een beheerder. Zie [On-premises gegevensgateway](service-gateway-onprem.md) voor meer informatie.
> * Wanneer u de gateway gebruikt, blijven uw gegevens on-premises.  De rapporten die u maakt op basis van die gegevens, worden opgeslagen in de Power BI-service. 
> * [Q&A-query's in natuurlijke taal](../create-reports/service-q-and-a-direct-query.md) bevindt zich in de preview-fase voor Analysis Services-liveverbindingen.

## <a name="to-connect-to-a-model-from-get-data"></a>Verbinding met een model maken via Gegevens ophalen

1. Selecteer in **Mijn werkruimte** de optie **Gegevens ophalen**. U kunt ook naar een groepswerkruimte schakelen als deze beschikbaar is.

   ![Knop om verbinding te maken en gegevens op te halen](media/sql-server-analysis-services-tabular-data/connecttoas_getdatabutton.png)

2. Selecteer **Databases en meer**.

   ![Verbinding maken om gegevens op te halen 1](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_1.png)

3. Selecteer **SQL Server Analysis Services** > **Verbinding maken**.

   ![Verbinding maken om gegevens op te halen 2](media/sql-server-analysis-services-tabular-data/connecttoas_getdata_2.png)

4. Selecteer een server. Als hier geen servers worden weergegeven, betekent dit dat er geen gateway en gegevensbron zijn geconfigureerd of dat uw account niet wordt vermeld op het tabblad **Gebruikers** van de gegevensbron in de gateway. Neem contact op met uw beheerder.

5. Selecteer het model waarmee u verbinding wilt maken. Dit kan een model in tabelvorm of een multidimensionaal model zijn.

Nadat u verbinding met het model hebt gemaakt, wordt deze weergegeven in uw Power BI-site in **Mijn werkruimte/gegevenssets**. Als u bent overgeheveld naar een groepswerkruimte, wordt de gegevensset weergegeven in de groep.

![Verbinding maken met gegevensset](media/sql-server-analysis-services-tabular-data/connecttoas_dataset_5.png)

## <a name="dashboard-tiles"></a>Dashboardtegels

Als u visuals uit een rapport aan een dashboard vastmaakt, worden de vastgemaakte tegels automatisch elke tien minuten vernieuwd. Als de gegevens in uw on-premises Analysis Services-server zijn bijgewerkt, worden de tegels na tien minuten automatisch bijgewerkt.

## <a name="common-issues"></a>Veelvoorkomende problemen

* Fout: kan het modelschema niet laden: deze fout treedt op wanneer de gebruiker die verbinding maakt met SSAS geen toegang heeft tot SSAS-database, -kubus en -model.

## <a name="next-steps"></a>Volgende stappen

* [On-premises gegevensgateway](service-gateway-onprem.md)  
* [Uw Analysis Services-gegevensbronnen beheren](service-gateway-enterprise-manage-ssas.md)  
* [Problemen met de on-premises gegevensgateway oplossen](service-gateway-onprem-tshoot.md)  

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
