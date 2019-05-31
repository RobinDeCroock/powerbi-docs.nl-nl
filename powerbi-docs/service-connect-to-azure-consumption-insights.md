---
title: Verbinding maken met Microsoft Azure Consumption Insights met Power BI
description: Microsoft Azure Consumption Insights voor Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222133"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Verbinding maken met Microsoft Azure Consumption Insights met Power BI
Verken en monitor uw Microsoft Azure-verbruiksgegevens in Power BI met het Power BI-inhoudspakket. De gegevens is één keer per dag automatisch vernieuwd.

Maak verbinding met het [Microsoft Azure Consumption Insights-inhoudspakket](https://app.powerbi.com/getdata/services/azureconsumption) voor Power BI.

## <a name="how-to-connect"></a>Verbinding maken
1. Selecteer **Gegevens ophalen** onder in het linkernavigatievenster.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Selecteer **Ophalen** in het vak **Services**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecteer **Microsoft Azure Consumption Insights** \> **nu downloaden**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Geef het inschrijvingsnummer voor Azure Enterprise op en het aantal maanden waarvoor u gegevens wilt importeren. Hieronder vindt u informatie over [het vinden van deze parameters](#FindingParams).
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Geef uw toegangscode op om verbinding te maken. U kunt de sleutel van uw inschrijving vinden in de Azure EA-Portal. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Het importproces wordt automatisch gestart. Als u klaar bent, wordt een nieuw dashboard, rapport en model in het navigatiedeelvenster weergegeven. Selecteer het dashboard om uw geïmporteerde gegevens weer te geven.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Wat nu?**

* [Stel vragen in het vak Q&A](consumer/end-user-q-and-a.md) boven in het dashboard.
* [Wijzig de tegels](service-dashboard-edit-tile.md) in het dashboard.
* [Selecteer een tegel](consumer/end-user-tiles.md) om het onderliggende rapport te openen.
* Terwijl uw gegevensset is volgens planning dagelijks vernieuwd, kunt u het vernieuwingsschema wijzigen of handmatig vernieuwen met behulp van aanvraag **nu vernieuwen**

## <a name="whats-included"></a>Wat is inbegrepen
Het Microsoft Azure Consumption Insights-inhoudspakket bevat maandelijkse rapportagegegevens voor de maandbereik dat u hebt opgegeven bij het verbinden. Het bereik is een zwevend venster, zodat de opgenomen datums worden bijgewerkt zodra de gegevensset wordt vernieuwd.

## <a name="system-requirements"></a>Systeemvereisten
Het inhoudspakket vereist toegang tot de Enterprise-functies in Azure portal. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Parameters zoeken
Power BI-rapportage is beschikbaar voor EA Direct, partners en indirecte klanten die factuurgegevens kunnen bekijken. Lees de sectie hieronder voor meer informatie over het vinden van elk van de waarden de verbindingsprocedure wordt verwacht.

**Number of Months**

* Het aantal maanden (1-36) aan gegevens van vandaag die u wilt importeren.

**Enrollment Number**

* Uw Azure Enterprise-inschrijvingsnummer, dat u kunt vinden in de [Azure Enterprise Portal](https://ea.azure.com/) startscherm onder **inschrijvingsgegevens**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Access Key**

* U kunt uw toegangssleutel vinden in de Azure Enterprise-portal, onder **gebruiksgegevens downloaden** > **API Access Key**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Aanvullende informatie**

* Voor extra hulp bij het instellen van de Azure Enterprise Power BI-Pack, moet u zich aanmelden bij de Azure Enterprise Portal en weergeven van de API Help-bestand onder **Help**. U vindt hier ook aanvullende instructies onder **rapporten** -> **gebruiksgegevens downloaden** -> **API Access Key**.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag in Power BI](service-get-started.md)

[Gegevens ophalen in Power BI](service-get-data.md)

