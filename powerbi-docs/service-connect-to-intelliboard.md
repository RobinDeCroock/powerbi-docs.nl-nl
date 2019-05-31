---
title: Verbinding met IntelliBoard maken met Power BI
description: IntelliBoard voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6f3a335bea711f1785f498caf7fbc828abb01c18
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61172354"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Verbinding met IntelliBoard maken met Power BI
IntelliBoard biedt vereenvoudigde toegang tot uw Moodle LMS-gegevens (Learning Management System) via Reporting Services. Het IntelliBoard-inhoudspakket voor Power BI biedt aanvullende analyses, inclusief metrische gegevens over uw cursussen, geregistreerde gebruikers, prestaties in het algemeen en uw LMS-activiteit.

Maak verbinding met het [IntelliBoard-inhoudspakket](https://app.powerbi.com/getdata/services/intelliboard) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.  
   
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

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
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
[Wat is Power BI?](power-bi-overview.md)

[Power BI - basisconcepten](consumer/end-user-basic-concepts.md)

