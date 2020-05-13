---
title: Verbinding met een Google BigQuery-database maken in Power BI Desktop
description: Eenvoudig verbinding maken met Google BigQuery in Power BI Desktop en het gebruiken
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b8d7c0db5a01d8f2e3781d3a8bf50899eb49841
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347833"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Verbinding met een Google BigQuery-database maken in Power BI Desktop
In Power BI Desktop kunt u verbinding maken met een Google **BigQuery**-database en gebruikmaken van de onderliggende gegevens, net zoals elke andere gegevensbron in Power BI Desktop.

## <a name="connect-to-google-bigquery"></a>Verbinding maken met Google BigQuery
Als u verbinding wilt maken met een Google **BigQuery**-database, selecteert u **Gegevens ophalen** op het lint **Start** in Power BI Desktop. Selecteer **Database** in de categorieën aan de linkerkant en u ziet **Google BigQuery**.

![Dialoogvenster Gegevens ophalen voor Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

In het **Google BigQuery**-venster dat wordt geopend meldt u zich aan bij uw Google BigQuery-account en selecteert u **Verbinden**.

![Aanmelden bij Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Wanneer u bent aangemeld ziet u het volgende venster, wat aangeeft dat u bent geverifieerd. 

![Aangemeld bij Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Als u verbinding hebt gemaakt, verschijnt er een **Navigator**-scherm waarin de gegevens worden getoond die op de server beschikbaar zijn. Hier kunt u een of meer elementen selecteren die u in **Power BI Desktop** wilt importeren en gebruiken.

![Gegevens uit Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
Houd rekening met enkele beperkingen en overwegingen als u de Google **BigQuery**-connector wilt gebruiken:

* De Google BigQuery-connector is beschikbaar in Power BI Desktop en in de Power BI-service. In de Power BI-service is de connector toegankelijk via de cloud-naar-cloud-verbinding vanuit Power BI met Google BigQuery.

U kunt Power BI gebruiken met het Google BigQuery **Factureringsproject**. Power BI maakt standaard gebruik van het eerste project in de lijst die voor de gebruiker wordt geretourneerd. Voor het aanpassen van het gedrag van het Factureringsproject wanneer u dat met Power BI opent, voert u de volgende stappen uit:

 * Opgeven van de volgende optie in de onderliggende M in de stap Bron, die kan worden aangepast met de **Power Query-editor** in Power BI Desktop:

    ```Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])```

## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Gegevensbronnen in Power BI Desktop](desktop-data-sources.md)
* [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   
