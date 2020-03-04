---
title: Rapportprestaties bewaken in Power BI
description: Richtlijnen voor het bewaken van de rapportprestaties in Power BI.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: b1ab74ec7f7f6594450ec2cf95528d06dc45f613
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77610013"
---
# <a name="monitor-report-performance-in-power-bi"></a>Rapportprestaties bewaken in Power BI

Bewaak rapportprestaties in Power BI Desktop met behulp van de [Power BI Premium Metrics-app](../service-premium-metrics-app.md), leer wat de knelpunten zijn, en leer hoe u rapportprestaties kunt verbeteren.

Bewakingsprestaties zijn relevant in de volgende situaties:

- Het vernieuwen van Gegevensmodel importeren is traag.
- De DirectQuery- of LiveConnection-rapporten zijn traag.
- De modelberekeningen zijn traag.

Trage query’s (of trage rapportvisuals) moet u in de gaten houden voor doorlopende optimalisatie.

## <a name="use-query-diagnostics"></a>Querydiagnose gebruiken

Gebruik [Querydiagnose](/power-query/QueryDiagnostics) in Power BI Desktop om het gedrag van Power Query te bepalen bij het bekijken van een voorbeeld van query’s of het uitvoeren van query’s. Gebruik daarnaast de functie _Diagnosestap_ om gedetailleerde evaluatiegegevens voor elke querystap vast te leggen. De resultaten zijn beschikbaar in een Power-query, en u kunt transformaties toepassen om de uitvoering van query’s beter te begrijpen.

> [!NOTE]
> Querydiagnose is momenteel een preview-functie, daarom moet u deze functie inschakelen in _Opties en instellingen_. Nadat de functie is ingeschakeld, zijn de bijbehorende opdrachten beschikbaar in het venster van de Power Query-editor op het tabblad **Hulpprogramma’s**.

![Afbeelding van het linttabblad Hulpprogramma’s voor de Power Query-editor. Op het lint worden de opdracht Diagnosestap, de opdracht Diagnostische gegevens starten, en de opdracht Diagnostische gegevens stoppen weergegeven.](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>Performance Analyzer gebruiken

Gebruik [Performance Analyzer](../desktop-performance-analyzer.md) in Power BI Desktop om te zien hoe het gaat met elk van de rapportelementen, zoals visuals en DAX-formules. Het is vooral handig om te bepalen of het de query- of de visualweergave is die bijdraagt aan prestatieproblemen.

## <a name="use-sql-server-profiler"></a>SQL Server Profiler gebruiken

U kunt ook [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) gebruiken om query's te identificeren die traag zijn.

> [!NOTE]
> SQL Server Profiler is beschikbaar als onderdeel van [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

Gebruik SQL Server Profiler als uw gegevensbron een van de volgende is:

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop ondersteunt verbindingen met een poort voor diagnostische gegevens. Via de poort voor diagnostische gegevens kunnen andere hulpprogramma's verbinding maken om traceringen uitvoeren voor diagnostische doeleinden. Het aanbrengen van wijzigingen in het Power Desktop-gegevensmodel wordt niet ondersteund. Wijzigingen in het gegevensmodel kunnen leiden tot beschadiging en verlies van gegevens.

Volg deze instructies om een SQL Server Profiler-tracering te maken:

1. Open het Power BI Desktop-rapport (en sluit alle eventuele geopende rapporten zodat u in de volgende stap de poort eenvoudig kunt vinden).
1. Voer de volgende opdracht uit om te bepalen welke poort wordt gebruikt in Power BI Desktop (met beheerdersbevoegdheden), of bij de Opdrachtprompt:
    ```powershell
    netstat -b -n
    ```
    De uitvoer is een lijst met toepassingen en de bijbehorende geopende poorten. Zoek de poort die wordt gebruikt voor **msmdsrv.exe**, en noteer het nummer voor later gebruik. Dit is uw exemplaar van Power BI Desktop.
1. Verbinding maken tussen SQL Server Profiler en het Power BI Desktop-rapport:
    1. Open SQL Server Profiler.
    1. Selecteer in SQL Server Profiler, in het menu _Bestand_, de optie _Nieuw tracering_.
    1. Selecteer voor **Servertype** de optie _Analysis Services_.
    1. Voer bij **Servernaam** in: _localhost:[poortnummer dat u eerder hebt genoteerd]_ .
    1. Klik op _Uitvoeren_. Nu is de SQL Server Profiler-tracering live, en worden Power BI-query’s actief geprofileerd.
1. Terwijl Power BI Desktop-query’s worden uitgevoerd, ziet u de respectieve duur en CPU-tijden. Afhankelijk van het type brongegevens ziet u mogelijk andere gebeurtenissen die aangeven hoe de query is uitgevoerd. Aan de hand van deze informatie kunt u bepalen welke query's de knelpunten vormen.

Een voordeel van het gebruik van SQL Server Profiler is dat het mogelijk is om een (relationele) SQL Server-databasetracering op te slaan. De tracering kan invoer worden voor de [Database Engine Tuning Advisor](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor). Op deze manier kunt u aanbevelingen ontvangen voor het afstemmen van uw gegevensbron.

## <a name="monitor-premium-metrics"></a>Metrische Premium-gegevens bewaken

Voor Power BI Premium-capaciteiten kunt u de **Power BI Premium Metrics-app gebruiken** om de status en capaciteit van uw Power BI Premium-abonnement te bewaken. Zie [Power BI Premium Metrics-app](../service-premium-metrics-app.md) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Querydiagnose](/power-query/QueryDiagnostics)
- [Performance Analyzer](../desktop-performance-analyzer.md)
- [Power BI Premium Metrics-app](../service-premium-metrics-app.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
