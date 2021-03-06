---
title: Verbinding maken met Azure Search met Power BI
description: Azure Search voor Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: 5c2c5d3b6382fdb85125a71829d62624dab31e83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403370"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Verbinding maken met Azure Search met Power BI
Met Azure Search Traffic Analytics kunt u het verkeer naar uw Azure Search-service volgen en begrijpen. Het Azure Search-inhoudspakket voor Power BI biedt gedetailleerde informatie over uw zoekgegevens, waaronder zoeken, indexeren, zoekstatistieken en latentie van de afgelopen 30 dagen. Meer informatie vindt u in het [Azure-blogbericht](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Verbinding maken met het [inhoudspakket van Azure Search](https://app.powerbi.com/getdata/services/azure-search) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onderaan het navigatievenster.
   
   ![Schermopname van het lint Gegevens ophalen in Power BI Desktop waarin de knop in het navigatievenster wordt weergegeven.](media/service-connect-to-azure-search/pbi_getdata.png) 
2. Selecteer **Ophalen** in het vak **Services**.
   
   ![Schermopname van het dialoogvenster Services met de knop Ophalen.](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Selecteer **Azure Search** \> **Ophalen**.
   
   ![Schermopname van het dialoogvenster Azure Services met de koppeling Ophalen.](media/service-connect-to-azure-search/azuresearch.png)
4. Geef de naam van het tabelopslagaccount waarop uw Azure Search-analyse is opgeslagen.
   
   ![Schermopname van het dialoogvenster Verbinding maken met Azure Search, waarin het veld met de naam van het Azure Storage-account wordt weergegeven.](media/service-connect-to-azure-search/params.png)
5. Selecteer **Sleutel** als verificatiemechanisme en voer de sleutel van uw opslagaccount in. Klik op **Aanmelden** om te beginnen met het laadproces.
   
   ![Schermopname van het dialoogvenster Verbinding maken met Azure Search, waarin de sleutel in het veld Verificatiemethode is ingevoerd.](media/service-connect-to-azure-search/creds.png)
6. Zodra het laden is voltooid, worden een nieuw dashboard, rapport en model in het navigatievenster weergegeven. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
    ![Schermopname van het navigatiedeelvenster, met het dashboard, het rapport en het model.](media/service-connect-to-azure-search/dashboard2.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](../consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](../create-reports/service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](../consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="system-requirements"></a>Systeemvereisten
Voor het inhoudspakket van Azure Search moet Azure Search Traffic Analytics ingeschakeld zijn op het account.

## <a name="troubleshooting"></a>Problemen oplossen
Controleer of de naam van het opslagaccount correct is opgegeven samen met de volledige toegangssleutel. De opslagaccountnaam moet overeenkomen met het account dat is geconfigureerd voor Azure Search Traffic Analytics.

## <a name="next-steps"></a>Volgende stappen
[Wat is Power BI?](../fundamentals/power-bi-overview.md)

[Basisconcepten voor ontwerpers in de Power BI-service](../fundamentals/service-basic-concepts.md)
