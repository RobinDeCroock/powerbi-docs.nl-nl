---
title: Verbinding maken met Planview Enterprise met Power BI
description: Planview Enterprise voor Power BI
services: powerbi
documentationcenter: 
author: joeshoukry
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: yshoukry
ms.openlocfilehash: 12346c0a9a580b2c3dd36c61a00d27097e1b3937
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Verbinding maken met Planview Enterprise met Power BI
Met het inhoudspakket van Planview Enterprise kunt u resource- en werkbeheergegevens op geheel nieuwe manieren visualiseren, rechtstreeks in Power BI. Gebruik uw Planview Enterprise-referenties voor een interactieve weergave van de investeringen in uw beleggingsportefeuille, om inzicht te krijgen in waar u boven en onder uw budget zit en om te zien hoe goed uw projecten zijn afgestemd op de strategische prioriteiten van uw bedrijf. U kunt het kant-en-klare dashboard en de rapporten ook uitbreiden om de inzichten te krijgen die voor u het belangrijkst zijn.

Verbinding maken met de [inhoudspakket van Planview Enterprise in Power BI](https://app.powerbi.com/getdata/services/planview-enterprise)

>[!NOTE]
>Als u uw Planview Enterprise-gegevens wilt importeren in Power BI, moet u een Planview Enterprise-gebruiker zijn en moet de functie voor het bekijken van de rapportageportal zijn ingeschakeld voor uw rol. Zie hieronder voor aanvullende vereisten.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linker navigatievenster.
   
    ![](media/service-connect-to-planview/get.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
    ![](media/service-connect-to-planview/services.png)
3. Selecteer op de pagina van Power BI **Planview Enterprise** en daarna **Ophalen**:  
    ![](media/service-connect-to-planview/planview.png)
4. Voer in het tekstvak URL voor Planview Enterprise de URL in voor de Planview Enterprise-server die u wilt gebruiken. Voer de naam van de Planview Enterprise-database in het tekstvak Planview Enterprise-database en klik op Volgende.  
    ![](media/service-connect-to-planview/params.png)
5. Selecteer in de lijst Verificatiemethode **Basis** als dit nog niet is geselecteerd. Voer de **Gebruikersnaam** en het **Wachtwoord** voor uw account in en selecteer **Aanmelden**.  
   ![](media/service-connect-to-planview/creds.png)
6. Selecteer in het linkerdeelvenster Planview Enterprise in de lijst met dashboards.  
     De Planview Enterprise-gegevens worden geïmporteerd in het dashboard. Houd er rekening mee dat het laden van de gegevens even kan duren.  
    ![](media/service-connect-to-planview/dashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](service-q-and-a.md) boven in het dashboard
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](service-dashboard-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="system-requirements"></a>Systeemvereisten
Als u uw Planview Enterprise-gegevens wilt importeren in Power BI, moet u een Planview Enterprise-gebruiker zijn en moet de functie voor het bekijken van de rapportageportal zijn ingeschakeld voor uw rol. Zie hieronder voor aanvullende vereisten.

Deze procedure gaat ervan uit dat u zich al met een Power BI-account hebt aangemeld op de startpagina van Microsoft Power BI. Als u geen Power BI-account hebt, kunt u gratis een nieuw Power BI-account maken op de startpagina van Power BI. Klik vervolgens op Gegevens ophalen.

## <a name="next-steps"></a>Volgende stappen:

[Aan de slag met Power BI](service-get-started.md)

[Gegevens ophalen voor Power BI](service-get-data.md)