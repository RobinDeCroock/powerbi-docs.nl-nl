---
title: Verbinding maken met Microsoft Azure Consumption Insights met Power BI
description: Microsoft Azure Consumption Insights voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020431"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Verbinding maken met Microsoft Azure Consumption Insights met Power BI
Verken en bewaak uw Microsoft Azure-verbruiksgegevens in de Power BI-service met het Power BI-inhoudspakket. De gegevens worden eenmaal per dag automatisch vernieuwd.

Maak verbinding met het [Microsoft Azure Consumption Insights-inhoudspakket](https://app.powerbi.com/getdata/services/azureconsumption) voor de Power BI-service.

> [!NOTE]
> Gebruik de [Azure Consumption Insights-connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop voor een meer aangepaste installatie.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer in de Power BI-service onder in het linkernavigatievenster de optie **Gegevens ophalen**.
   
    ![Gegevens ophalen](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Selecteer **Ophalen** in het vak **Services**.
   
   ![Services ophalen](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecteer **Microsoft Azure Consumption Insights** \> **Nu downloaden**. 
   
   ![Nu downloaden](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Geef het inschrijvingsnummer voor Azure Enterprise op en het aantal maanden waarvoor u gegevens wilt importeren. Hieronder vindt u informatie over [het vinden van deze parameters](#FindingParams).
   
    ![Verbinding maken met Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Geef uw toegangscode op om verbinding te maken. U vindt uw inschrijvingssleutel in de Azure EA-portal. 
   
    ![Microsoft Azure Consumption Insights: sleutel](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Het importproces wordt automatisch gestart. Als dit is voltooid, bevat het navigatievenster een nieuw dashboard, rapport en model. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
   ![Microsoft Azure Consumption Insights-dashboard](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Als uw gegevensset is ingesteld op dagelijks vernieuwen, kunt u het vernieuwingsschema wijzigen of de gegevensset handmatig vernieuwen met **Nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
Het Microsoft Azure Consumption Insights-inhoudspakket bevat maandelijkse rapportagegegevens voor het maandbereik dat u hebt opgegeven tijdens het verbinden. Het is een verschuivend bereik, wat betekent dat de opgenomen datums worden bijgewerkt zodra de gegevensset wordt vernieuwd.

## <a name="system-requirements"></a>Systeemvereisten
Voor het inhoudspakket is toegang vereist tot de Enterprise-functies van de Azure-portal. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
Power BI-rapportage is beschikbaar voor EA Direct, partners en indirecte klanten die factuurgegevens kunnen bekijken. Lees de sectie hieronder voor meer informatie over het vinden van elk van de waarden die voor de verbindingsstroom worden verwacht.

**Number of Months**

* Het aantal maanden (1-36) waarvoor u gegevens wilt importeren.

**Enrollment Number**

* Uw inschrijvingsnummer voor Azure Enterprise, dat u kunt vinden op het beginscherm van de [Azure Enterprise-portal](https://ea.azure.com/), onder **Inschrijvingsgegevens**.
  
    ![Inschrijvingsnummer](media/service-connect-to-azure-consumption-insights/params2.png)

**Access Key**

* U vindt uw toegangssleutel in de Azure Enterprise-portal, onder **Downloadgebruik** > **API-toegangssleutel**.
  
    ![Toegangssleutel](media/service-connect-to-azure-consumption-insights/creds2.png)

**Aanvullende informatie**

* Meld u aan bij de Azure Enterprise-portal en bekijk onder **Help** het API-Help-bestand voor aanvullende hulp bij het instellen van het Azure Enterprise Power BI-pakket. U kunt ook aanvullende instructies vinden onder **Rapporten** -> **Downloadgebruik** -> **API-toegangssleutel**.
* Gebruik de [Azure Consumption Insights-connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop voor een meer aangepaste installatie.

## <a name="next-steps"></a>Volgende stappen

[Azure Consumption Insights-connector](desktop-connect-azure-consumption-insights.md) in Power BI Desktop

[Gegevens ophalen in Power BI](service-get-data.md)

