---
title: Gegevensbronnen die worden ondersteund door DirectQuery in Power BI
description: Hier vindt u een lijst met ondersteunde gegevensbronnen voor DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 3bb7de9685a1e0fc9fa423328ad9e1e5faa53603
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61305450"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Gegevensbronnen die worden ondersteund door DirectQuery in Power BI

In **Power BI Desktop** en de **Power BI-service** kunt u met allerlei gegevensbronnen verbinding maken en toegang tot gegevens verkrijgen. In dit artikel wordt beschreven welke gegevensbronnen voor Power BI worden ondersteund voor de verbindingsmethode **DirectQuery**. Zie [**DirectQuery in Power BI**](desktop-directquery-about.md) voor meer informatie over DirectQuery.

De volgende gegevensbronnen worden ondersteund door DirectQuery in Power BI:

* Amazon Redshift
* AtScale (bèta)
* Azure HDInsight Spark
* Azure SQL Database
* Azure SQL Data Warehouse
* Google BigQuery
* HDInsight Interactive Query
* IBM DB2-database
* IBM Netezza
* Impala (versie 2.x)
* Oracle Database (versie 12 en hoger)
* Oracle Essbase
* SAP Business Warehouse-toepassingsserver
* SAP Business Warehouse-berichtenserver
* SAP HANA
* Snowflake
* Spark (versie 0.9 en hoger)
* SQL Server
* Teradata-database
* Vertica

Gegevensbronnen met **(bèta)** of **(preview)** achter de naam zijn onderhevig aan wijzigingen, en worden niet ondersteund voor productiegebruik. Mogelijk worden ze ook niet ondersteund na publicatie van een rapport naar de **Power BI-service**. Dit betekent dat het openen van een gepubliceerd rapport of het verkennen van de gegevensset kan resulteren in een fout.

Het enige verschil tussen **bèta**- en **voorbeeld**gegevensbronnen is dat **voorbeeld**bronnen moeten zijn ingeschakeld als voorbeeldfunctie voordat ze beschikbaar worden voor gebruik. U schakelt een **(voorbeeld)** gegevensconnector als volgt in: ga in **Power BI Desktop** naar **Bestand > Opties en instellingen > Opties** en kies **Voorbeeldfuncties**.

> [!NOTE]
> Voor DirectQuery-query's naar SQL Server is verificatie met behulp van huidige referenties voor Windows-verificatie of databasereferenties nodig om toegang tot stand te brengen. Alternatieve referenties worden niet ondersteund.
>

## <a name="on-premises-gateway-requirements"></a>Vereisten voor on-premises gateway
In de volgende tabel wordt aangegeven of u een **On-premises gegevensgateway** nodig hebt om verbinding te maken met de opgegeven gegevensbron, na publicatie van een rapport naar de **Power BI-service**.

| Bron | Gateway vereist? |
| --- | --- |
| SQL Server |Ja |
| Azure SQL Database |Nee |
| Azure SQL Data Warehouse |Nee |
| SAP HANA |Ja |
| Oracle Database |Ja |
| Teradata-database |Ja |
| Amazon Redshift |Nee |
| Impala (versie 2.x) |Ja |
| Snowflake |Ja |
| Spark (bèta), versie 0.9 en hoger |Ja |
| Azure HDInsight Spark (bèta) |Nee |
| IBM Netezza |Ja |
| SAP Business Warehouse-toepassingsserver |Ja |
| SAP Business Warehouse-berichtenserver |Nog niet ondersteund in de **Power BI-service** |
| Google BigQuery |Nee |


## <a name="next-steps"></a>Volgende stappen
Bekijk de volgende bronnen voor meer informatie over DirectQuery:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)
* [On-premises data gateway](service-gateway-onprem.md) (On-premises gegevensgateway)

