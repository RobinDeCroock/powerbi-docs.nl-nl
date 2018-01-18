---
title: Verbinding met Salesforce maken via Power BI
description: SalesForce voor Power BI
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
ms.openlocfilehash: 6998f273a7e40cae2c7a50f043f79eec540b4789
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-salesforce-with-power-bi"></a>Verbinding met Salesforce maken via Power BI
Met Power BI kunt u eenvoudig verbinding maken met uw Salesforce.com-account. Door deze verbinding te maken worden uw gegevens opgehaald en wordt er automatische een dashboard met de bijbehorende rapporten op basis van uw gegevens gemaakt.

Maak verbinding met het [Salesforce-inhoudspakket](https://app.powerbi.com/getdata/services/salesforce) voor Power BI of lees meer over de [integratie van Salesforce](https://powerbi.microsoft.com/integrations/salesforce) met Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Klik op **Salesforce** en selecteer **Ophalen**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Selecteer **Aanmelden** om de aanmeldingsprocedure te starten.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. Geef desgevraagd uw Salesforce-referenties op. Klik op **Toestaan** zodat Power BI toegang heeft tot uw basisinformatie en -gegevens van Salesforce.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Gebruik de vervolgkeuzelijst om te configureren wat u wilt importeren in Power BI:
   
   * **Dashboard**
     
     Selecteer een vooraf gedefinieerde dashboard op basis van een persoon (zoals **salesmanager**). Met deze dashboards importeert u een specifieke set standaardgegevens van Salesforce. Deze dashboards bevatten geen aangepaste velden.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Rapporten**
     
     Selecteer een of meer aangepaste rapporten in uw Salesforce-account. Deze rapporten komen overeen met de weergaven in Salesforce en kunnen gegevens uit aangepaste velden of objecten bevatten.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Als er geen rapporten worden weergegeven, voegt u ze toe aan of maakt u ze in uw Salesforce-account en maakt u opnieuw verbinding.
7. Klik op **Verbinding maken** om het importproces te starten. Tijdens het importeren wordt er een melding weergegeven dat er een importbewerking wordt uitgevoerd. Zodra het importeren is voltooid, ziet u een dashboard, rapport en gegevensset voor uw Salesforce-gegevens in het navigatiedeelvenster aan de linkerkant.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

U kunt dit dashboard wijzigen om uw gegevens weer te geven zoals u dat wilt. U kunt vragen stellen met Q & A of op een tegel klikken om [het onderliggende rapport te openen](service-dashboard-tiles.md) en [de tegels wijzigen](service-dashboard-edit-tile.md) in het dashboard.

**Wat nu?**

* [Stel vragen in het vak Q&A](service-q-and-a.md) boven in het dashboard
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](service-dashboard-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**.

## <a name="system-requirements"></a>Systeemvereisten
* Verbinding met een productieaccount van Salesforce waarvoor API-toegang is ingeschakeld.
* Er moet tijdens het aanmelden een machtiging aan de BI-app worden verleend.
* Het account beschikt over voldoende beschikbare API-aanroepen om de gegevens op te halen en te vernieuwen.
* Er is een geldig verificatietoken nodig om de gegevens te kunnen vernieuwen. Zorg ervoor dat u maximaal Salesforce-gegevenssets importeert, aangezien er een limiet van vijf verificatietokens per toepassing geldt voor Salesforce.

## <a name="troubleshooting"></a>Probleemoplossing
Als er fouten optreden, raadpleegt u de bovenstaande vereisten. Houd er ook rekening mee dat er geen ondersteuning wordt geboden voor aanmelden bij een aangepast of sandbox-domein.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag met Power BI](service-get-started.md)

[Gegevens ophalen](service-get-data.md)
