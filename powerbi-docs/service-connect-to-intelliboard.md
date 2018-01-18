---
title: Verbinding met IntelliBoard maken met Power BI
description: IntelliBoard voor Power BI
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
ms.openlocfilehash: f668a1c9bfefb1b0b0c7c15f9d68c82312d38105
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Verbinding met IntelliBoard maken met Power BI
IntelliBoard biedt vereenvoudigde toegang tot uw Moodle LMS-gegevens (Learning Management System) via Reporting Services. Het IntelliBoard-inhoudspakket voor Power BI biedt aanvullende analyses, inclusief metrische gegevens over uw cursussen, geregistreerde gebruikers, prestaties in het algemeen en uw LMS-activiteit.

Maak verbinding met het [IntelliBoard-inhoudspakket](https://app.powerbi.com/getdata/services/intelliboard) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linker navigatievenster.  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. Selecteer in het vak **Services** de optie **Ophalen**.  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. Selecteer **IntelliBoard** en selecteer vervolgens **Ophalen**.  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. Selecteer **OAuth 2** en vervolgens **Aanmelden**. Geef desgevraagd uw IntelliBoard-referenties op.
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. Nadat verbinding is gemaakt, worden automatisch een dashboard, rapport en gegevensset geladen. Vervolgens worden de tegels bijgewerkt met gegevens uit uw IntelliBoard-account.
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](service-q-and-a.md) boven in het dashboard
* [Wijzig de tegels ](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](service-dashboard-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is opgenomen
Het inhoudspakket bevat gegevens uit de volgende tabellen:  

    - Activiteit  
    - Agenten  
    - Verificatie  
    - Landen  
    - Cursusvoortgang  
    - Registratie
    - Taal  
    - Platform  
    - Totalen  
    - UsersProgress    

## <a name="system-requirements"></a>Systeemvereisten
Een IntelliBoard-account met machtigingen voor de bovenstaande tabellen is vereist om dit inhoudspakket te starten.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag met Power BI](service-get-started.md)

[Power BI - basisconcepten](service-basic-concepts.md)
