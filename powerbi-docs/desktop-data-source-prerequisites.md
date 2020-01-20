---
title: Vereisten voor Power BI-gegevensbronnen
description: Vereisten voor Power BI-gegevensbronnen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d118cae8cd4b6fbd95066b15819b1e798c8bbe0f
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761313"
---
# <a name="power-bi-data-source-prerequisites"></a>Vereisten voor Power BI-gegevensbronnen
Voor elke gegevensprovider ondersteunt Power BI een specifieke providerversie voor objecten. Zie [Gegevensbronnen](desktop-data-sources.md) voor meer informatie over de beschikbare gegevensbronnen voor Power BI. In de volgende tabel worden deze vereisten beschreven.

| Gegevensbron | Provider | Minimaal vereiste providerversie | Minimaal vereiste gegevensbronversie | Ondersteunde gegevensbronobjecten | Downloadkoppeling |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (ingebouwd in .Net Framework) |.Net Framework 3.5 (uitsluitend) |SQL Server 2005+ |Tabellen/weergaven, scalaire functies, tabelfuncties |Opgenomen in .NET Framework 3.5 en hoger |
| Toegang |Microsoft Access-database-engine (ACE) |ACE 2010 SP1 |Geen beperking |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Excel (uitsluitend XLS-bestanden) (zie opmerking 1) |Microsoft Access-database-engine (ACE) |ACE 2010 SP1 |Geen beperking |Tabellen, bladen |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=285987&clcid=0x409) |
| Oracle (zie opmerking 2) |ODP.NET |ODAC 11.2 Release 5 (11.2.0.3.20) |9.x+ |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=272376&clcid=0x409) |
| | System.Data.OracleClient (ingebouwd in .Net Framework) |.NET Framework 3.5 |9.x+ |Tabellen/weergaven |Opgenomen in .NET Framework 3.5 en hoger |
| IBM DB2 |ADO.Net-client van IBM (onderdeel van het stuurprogrammapakket voor de IBM-gegevensserver) |10.1 |9.1+ |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Connector/Net |6.6.5 |5.1 |Tabellen/weergaven, scalaire functies |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |NPGSQL ADO.NET-provider |2.0.12 |7.4 |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |.Net-gegevensprovider voor Teradata |14+ |12+ |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere voor .NET 3.5 |16+ |16+ |Tabellen/weergaven |[Downloadkoppeling](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Voor Excel-bestanden met een .xlsx-extensie is geen aparte providerinstallatie vereist.

>[!NOTE]
>Voor de Oracle-providers is ook Oracle-clientsoftware (versie 8.1.7+) vereist.
> 
> 

