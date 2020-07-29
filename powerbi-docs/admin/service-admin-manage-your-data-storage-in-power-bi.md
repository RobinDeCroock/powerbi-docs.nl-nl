---
title: Gegevensopslag in uw werkruimten beheren
description: Ontdek hoe u de gegevensopslag beheert in uw persoonlijke werkruimte of een werkruimte, zodat u rapporten en gegevenssets kunt blijven publiceren.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/27/2020
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: eb59359497dec351c960ce0c6a3ce11b4f6eab0d
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87252102"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gegevensopslag in Power BI-werkruimten beheren

Ontdek hoe u de gegevensopslag beheert in uw persoonlijke werkruimte of een werkruimte, zodat u rapporten en gegevenssets kunt blijven publiceren.

## <a name="capacity-limits"></a>Capaciteitslimieten

Limieten voor opslag van werkruimten hangen af van de vraag of de werkruimte zich in een [gedeelde of Premium-capaciteit](../fundamentals/service-basic-concepts.md#capacities) bevindt. Dit geldt zowel voor Mijn werkruimte als app-werkruimten.

### <a name="shared-capacity-limits"></a>Limieten voor gedeelde capaciteit
Voor werkruimten in gedeelde capaciteit: 

- Er geldt een opslaglimiet van 10 GB per werkruimte.
- Voor app-werkruimten mag het totale gebruik niet groter zijn dan de opslaglimiet van 10 GB voor de tenant, vermenigvuldigd met het aantal Pro-licenties in de tenant.

### <a name="premium-capacity-limits"></a>Limieten voor Premium-capaciteit
Voor werkruimten in Premium-capaciteit:
- Er geldt een limiet van 100 TB per Premium-capaciteit.
- Er geldt geen opslaglimiet per gebruiker.

Meer informatie over andere functies van het [Power BI-prijsmodel](https://powerbi.microsoft.com/pricing).

## <a name="whats-included-in-storage"></a>Wat is opgenomen in de opslag

Tot uw gegevensopslag behoren uw eigen gegevenssets en Excel-rapporten en items die iemand met u heeft gedeeld. Gegevenssets zijn alle gegevensbronnen die u hebt geüpload of waarmee u verbonden bent. Deze gegevensbronnen bevatten de Power BI Desktop-bestanden en Excel-werkmappen die u gebruikt. Het volgende is ook opgenomen in uw gegevenscapaciteit.

* Excel-adresbereiken die zijn vastgemaakt aan een dashboard.
* On-premises visualisaties van Reporting Services die zijn vastgemaakt aan een Power BI-dashboard.
* Geüploade afbeeldingen.

De grootte van een dashboard dat u deelt, is afhankelijk van hetgeen eraan is vastgemaakt. Als u bijvoorbeeld items uit twee rapporten vastmaakt die deel uitmaken van twee verschillende gegevenssets, omvat de grootte beide gegevenssets.

## <a name="manage-items-you-own"></a>Items beheren waarvan u de eigenaar bent

Zie hoeveel gegevensopslag u gebruikt in uw Power BI-account en beheer uw account.

1. Om uw eigen opslag te beheren, gaat u naar **Mijn werkruimte** in het navigatiedeelvenster.
   
    ![Schermopname van het navigatiedeelvenster waarin Mijn werkruimte is omkaderd.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. Selecteer het ![tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in de rechterbovenhoek **Persoonlijke opslag beheren**.
   
    In de bovenste balk ziet u hoeveel u hebt gebruikt van uw opslaglimiet.
   
    ![Schermopname van de optie Opslaglimiet beheren, met de hoeveelheid opslagruimte die is gebruikt.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    De gegevenssets en rapporten worden gescheiden op twee tabbladen:
   
    **Items waarvan ik eigenaar ben:** Dit zijn de rapporten en gegevenssets die u hebt geüpload naar uw Power BI-account, waaronder servicegegevenssets zoals Salesforce en Dynamics CRM.  

    **Items waarvan anderen eigenaar zijn:** Anderen hebben deze rapporten en gegevenssets met u gedeeld.
1. Als u een gegevensset of rapport wilt verwijderen, selecteert u het prullenbakpictogram ![Prullenbakpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Bedenk dat u of iemand anders mogelijk rapporten en dashboards heeft die zijn gebaseerd op een gegevensset. Als u de gegevensset verwijdert, werken die rapporten en dashboards niet meer.

## <a name="manage-your-workspace"></a>Uw werkruimte beheren
1. Selecteer de pijl naast **Werkruimten** en selecteer de naam van de werkruimte.
   
    ![Schermopname waarin Werkruimte is geselecteerd, waarin de werkruimte Verkoopgroep wordt weergegeven.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selecteer het tandwielpictogram ![Tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in de rechterbovenhoek **Groepsopslag beheren**.
   
    In de bovenste balk ziet u hoeveel opslaglimiet van de groep is gebruikt.
   
    ![Schermopname van de optie Opslaglimiet beheren, met de hoeveelheid opslagruimte die de Verkoopgroep heeft gebruikt.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    De gegevenssets en rapporten worden gescheiden op twee tabbladen:
   
    **Items waarvan wij eigenaar zijn:** Dit zijn rapporten en gegevenssets die door u of iemand anders zijn geüpload naar het Power BI-account van de groep, waaronder servicegegevenssets zoals Salesforce en Dynamics CRM.

    **Items waarvan anderen eigenaar zijn:** Anderen hebben deze rapporten en gegevenssets met uw groep gedeeld.

3. Als u een gegevensset of rapport wilt verwijderen, selecteert u het prullenbakpictogram ![Prullenbakpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Bedenk dat u of iemand anders in de groep mogelijk rapporten en dashboards heeft die zijn gebaseerd op een gegevensset. Als u de gegevensset verwijdert, werken die rapporten en dashboards niet meer.
   
   Elk lid met de rol van beheerder, lid of inzender in een werkruimte is gemachtigd om gegevenssets en rapporten in de werkruimte te verwijderen.

## <a name="dataset-limits"></a>Limieten voor de gegevensset
Er is een limiet van 1 GB per gegevensset die wordt geïmporteerd in Power BI. Als u ervoor hebt gekozen om de Excel-ervaring te houden, in plaats van de gegevens te importeren, is 250 MB de limiet voor de gegevensset.

## <a name="what-happens-when-you-reach-a-limit"></a>Wat er gebeurt wanneer u een limiet bereikt
Als u de gegevenscapaciteitslimiet bereikt, ziet u instructies in de service. 

Wanneer u het tandwielpictogram ![Tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)selecteert, ziet u een rode balk die aangeeft dat u de limiet van uw gegevenscapaciteit hebt overschreden.

![Schermopname van de opslagcapaciteit, waarin wordt weergegeven dat de limiet is bereikt.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Deze limiet wordt ook aangeduid in **Persoonlijke opslag beheren**.

 ![Schermopname van de persoonlijke opslagcapaciteit, waarin wordt weergegeven dat de limiet van Jane is bereikt.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Wanneer u een actie uitvoert waarmee u een van de limieten bereikt, wordt een bericht weergegeven dat u de limiet hebt overschreden. U kunt [uw opslag beheren](#manage-items-you-own) om de hoeveelheid opgeslagen gegevens te verkleinen en zo binnen de limiet te blijven.

 ![Schermopname van het dialoogvenster Uw opslaglimiet is overschreden, waarin wordt weergegeven dat de limieten zijn bereikt.](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>Volgende stappen

 Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
