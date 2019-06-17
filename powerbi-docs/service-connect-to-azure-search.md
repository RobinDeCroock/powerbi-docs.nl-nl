---
title: Verbinding maken met Azure Search met Power BI
description: Azure Search voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 4756bcef5d50783940a9b9565d0af6b9978e52b7
ms.sourcegitcommit: 762857c8ca09ce222cc3f8b006fa1b65d11e4ace
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66721281"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Verbinding maken met Azure Search met Power BI
Met Azure Search Traffic Analytics kunt u het verkeer naar uw Azure Search-service volgen en begrijpen. Het Azure Search-inhoudspakket voor Power BI biedt gedetailleerde informatie over uw zoekgegevens, waaronder zoeken, indexeren, zoekstatistieken en latentie van de afgelopen 30 dagen. Meer informatie vindt u in het [Azure-blogbericht](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

Verbinding maken met het [inhoudspakket van Azure Search](https://app.powerbi.com/getdata/services/azure-search) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
   ![](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Selecteer in het vak **Services** de optie **Ophalen**.
   
   ![](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selecteer **Azure Search** \> **Ophalen**.
   
   ![](media/service-connect-to-azure-search/azuresearch.png)
4. Geef de naam van het tabelopslagaccount waarop uw Azure Search-analyse is opgeslagen.
   
   ![](media/service-connect-to-azure-search/params.png)
5. Selecteer **Sleutel** als verificatiemechanisme en voer de sleutel van uw opslagaccount in. Klik op **Aanmelden** om te beginnen met het laadproces.
   
   ![](media/service-connect-to-azure-search/creds.png)
6. Zodra het laden is voltooid, worden een nieuw dashboard, rapport en model in het navigatiedeelvenster weergegeven. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
    ![](media/service-connect-to-azure-search/dashboard2.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="system-requirements"></a>Systeemvereisten
Voor het inhoudspakket van Azure Search moet Azure Search Traffic Analytics ingeschakeld zijn op het account.

## <a name="troubleshooting"></a>Problemen oplossen
Controleer of de naam van het opslagaccount correct is opgegeven samen met de volledige toegangssleutel. De opslagaccountnaam moet overeenkomen met het account dat is geconfigureerd voor Azure Search Traffic Analytics.

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](power-bi-overview.md)

[Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md)

