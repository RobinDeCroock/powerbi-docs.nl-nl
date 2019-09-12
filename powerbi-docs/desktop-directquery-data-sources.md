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
ms.date: 09/04/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 59c55d2e9322b0b7d76a35f4eec0863efe4959e0
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302644"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Gegevensbronnen die worden ondersteund door DirectQuery in Power BI

In **Power BI Desktop** en de **Power BI-service** kunt u met allerlei gegevensbronnen verbinding maken en toegang tot gegevens verkrijgen. In dit artikel wordt beschreven welke gegevensbronnen voor Power BI worden ondersteund voor de verbindingsmethode **DirectQuery**. Zie [**DirectQuery in Power BI**](desktop-directquery-about.md) voor meer informatie over DirectQuery.

De volgende gegevensbronnen worden ondersteund door DirectQuery in Power BI:

* Amazon Redshift
* AtScale (bèta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* HDInsight Interactive Query
* IBM DB2 (Microsoft Provider)
* IBM Netezza
* Impala (versie 2.x)
* MarkLogic
* Oracle Database (versie 12 en hoger)
* Oracle Essbase
* PostgreSQL
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
| Amazon Redshift |Nee |
| Azure HDInsight Spark (bèta) |Nee |
| Azure SQL Database |Nee |
| Azure SQL Data Warehouse |Nee |
| Google BigQuery |Nee |
| IBM Netezza |Ja |
| IBM DB2 (IBM Provider) |Ja |
| IBM DB2 (Microsoft Provider) |Nee |
| IBM Informix-database |Nee |
| Impala (versie 2.x) |Ja |
| MySQL |Ja |
| ODBC |Ja |
| Oracle Database |Ja |
| PostgreSQL |Ja |
| SAP Business Warehouse-toepassingsserver |Ja |
| SAP Business Warehouse-berichtenserver |Nog niet ondersteund in de **Power BI-service** |
| SAP HANA |Ja |
| Snowflake |Ja |
| Spark (bèta), versie 0.9 en hoger |Ja |
| SQL Server |Ja |
| Sybase |Ja |
| Teradata-database |Ja |
| Vertica |Ja |


## <a name="single-sign-on-sso-for-directquery-sources"></a>Eenmalige aanmelding (SSO) voor DirectQuery-bronnen

Wanneer de optie voor eenmalige aanmelding is ingeschakeld en uw gebruikers toegang hebben tot rapporten die op de gegevensbron zijn gebouwd, verzendt Power BI hun geverifieerde Azure AD-referenties in de query's naar de onderliggende gegevensbron. Hierdoor kan Power BI rekening houden met de beveiligingsinstellingen die op het niveau van de gegevensbronnen zijn geconfigureerd.

De optie voor eenmalige aanmelding heeft effect op alle gegevenssets die gebruikmaken van deze gegevensbron. Het heeft geen invloed op de verificatiemethode die wordt gebruikt om scenario's te importeren. De volgende gegevensbronnen ondersteunen SSO (eenmalige aanmelding) voor verbindingen via DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) wordt niet ondersteund. Gebruikers die gebruik willen maken van SSO met DirectQuery, moeten worden uitgesloten van MFA.

## <a name="next-steps"></a>Volgende stappen
Bekijk de volgende bronnen voor meer informatie over DirectQuery:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)
* [On-premises data gateway](service-gateway-onprem.md) (On-premises gegevensgateway)

