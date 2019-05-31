---
title: Gegevensopslag in uw werkruimten beheren
description: Meer informatie over hoe u uw persoonlijke of opslag van de app-werkruimte kunt beheren om ervoor te zorgen dat u rapporten en gegevenssets kunt blijven publiceren.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: a46fbb0679de30e554003d858e01756b9b242b1b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61189938"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gegevensopslag in Power BI-werkruimten beheren

Meer informatie over hoe u uw persoonlijke of opslag van de app-werkruimte kunt beheren om ervoor te zorgen dat u rapporten en gegevenssets kunt blijven publiceren.

Gebruikers en app-werkruimten hebben hun eigen gegevenscapaciteit:

* Alle gebruikers hebben maximaal 10 GB gegevensopslag.
* Gebruikers met een Power BI Pro-licentie kunnen app-werkruimten maken, die elk maximaal 10 GB gegevensopslag hebben.
* Een app-werkruimte in een Premium-capaciteit telt niet mee bij de opslagruimte van een Power BI Pro-gebruiker.

Op tenantniveau kan het totale gebruik niet 10 GB per Pro-gebruiker overschrijden over alle Pro-gebruikers van app-werkruimten in de tenant.

Meer informatie over andere functies van het [Power BI-prijsmodel](https://powerbi.microsoft.com/pricing).

Tot uw gegevensopslag behoren uw eigen gegevenssets en Excel-rapporten en items die iemand met u heeft gedeeld. Gegevenssets zijn alle gegevensbronnen die u hebt geüpload of waarmee u verbonden bent. Deze gegevensbronnen bevatten de Power BI Desktop-bestanden en Excel-werkmappen die u gebruikt. Het volgende is ook opgenomen in uw gegevenscapaciteit.

* Excel-adresbereiken die zijn vastgemaakt aan dashboard.
* On-premises visualisaties van Reporting Services die zijn vastgemaakt aan een Power BI-dashboard.
* Geüploade afbeeldingen.

De grootte van een dashboard dat u deelt, is afhankelijk van hetgeen eraan is vastgemaakt. Als u bijvoorbeeld items uit twee rapporten vastmaakt die deel uitmaken van twee verschillende gegevenssets, omvat de grootte beide gegevenssets.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Items beheren waarvan u de eigenaar bent

Zie hoeveel gegevensopslag u gebruikt in uw Power BI-account en beheer uw account.

1. Om uw eigen opslag te beheren, gaat u naar **Mijn werkruimte** in het navigatiedeelvenster links.
   
    ![Mijn werkruimte](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Selecteer het ![tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) in de rechterbovenhoek \> **Persoonlijke opslag beheren**.
   
    In de bovenste balk ziet u hoeveel u hebt gebruikt van uw opslaglimiet.
   
    ![Opslaglimiet beheren](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    De gegevenssets en rapporten worden gescheiden op twee tabbladen:
   
    **Items waarvan ik eigenaar ben:** Dit zijn de rapporten en gegevenssets die u hebt geüpload naar uw Power BI-account, waaronder servicegegevenssets zoals Salesforce en Dynamics CRM.  
    **Items waarvan anderen eigenaar zijn:** Anderen hebben deze rapporten en gegevenssets met u gedeeld.
1. Als u een gegevensset of rapport wilt verwijderen, selecteert u het prullenbakpictogram ![prullenbakpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Bedenk dat u of iemand anders mogelijk rapporten en dashboards heeft die zijn gebaseerd op een gegevensset. Als u de gegevensset verwijdert, werken die rapporten en dashboards niet meer.

## <a name="manage-your-app-workspace"></a>Uw app-werkruimte beheren
1. Selecteer de pijl naast **Werkruimten** \> en selecteer de naam van de app-werkruimte.
   
    ![Een app-werkruimte selecteren](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selecteer het tandwielpictogram ![tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) \> in de rechterbovenhoek **Persoonlijke opslag beheren**.
   
    In de bovenste balk ziet u hoeveel opslaglimiet van de groep is gebruikt.
   
    ![Opslag van app-werkruimte beheren](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    De gegevenssets en rapporten worden gescheiden op twee tabbladen:
   
    **Items waarvan wij eigenaar zijn:** Dit zijn rapporten en gegevenssets die door u of iemand anders zijn geüpload naar het Power BI-account van de groep, waaronder servicegegevenssets zoals Salesforce en Dynamics CRM.
    **Items waarvan anderen eigenaar zijn:** Anderen hebben deze rapporten en gegevenssets met uw groep gedeeld.
3. Als u een gegevensset of rapport wilt verwijderen, selecteert u het prullenbakpictogram ![prullenbakpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Elk lid, met bewerkingsmachtigingen, van een app-werkruimte is gemachtigd om gegevenssets en rapporten uit de app-werkruimte te verwijderen.
   > 
   > 

Bedenk dat u of iemand anders in de groep mogelijk rapporten en dashboards heeft die zijn gebaseerd op een gegevensset. Als u de gegevensset verwijdert, werken die rapporten en dashboards niet meer.

## <a name="dataset-limits"></a>Limieten voor de gegevensset
Er is een limiet van 1 GB per gegevensset die wordt geïmporteerd in Power BI. Als u ervoor hebt gekozen om de Excel-ervaring te houden, in plaats van de gegevens te importeren, is 250 MB de limiet voor de gegevensset.

## <a name="what-happens-when-you-reach-a-limit"></a>Wat er gebeurt wanneer u een limiet bereikt
Als u de gegevenscapaciteitslimiet bereikt, ziet u instructies in de service. 

Wanneer u het tandwielpictogram ![Tandwielpictogram](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)selecteert, ziet u een rode balk die aangeeft dat u de limiet van uw gegevenscapaciteit hebt overschreden.

![Opslaglimiet bereikt](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Deze limiet wordt ook aangeduid in **Persoonlijke opslag beheren**.

 ![Persoonlijke opslag beheren, opslaglimiet bereikt](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Wanneer u een actie uitvoert waarmee u een van de limieten bereikt, wordt een bericht weergegeven dat u de limiet hebt overschreden. U kunt uw opslag [beheren](#manage) om de hoeveelheid opgeslagen gegevens te verkleinen en zo binnen de limiet te blijven.

 ![De opslaglimiet is overschreden](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

