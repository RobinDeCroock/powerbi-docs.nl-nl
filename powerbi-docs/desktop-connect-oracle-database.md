---
title: Verbinding maken met een Oracle-database
description: Stappen en downloads die nodig zijn om Oracle te verbinden met Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/22/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b28c4ea9b4cacc77a7f98af5bfc006670f40af94
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61314959"
---
# <a name="connect-to-an-oracle-database"></a>Verbinding maken met een Oracle-database
Om een Oracle-database te kunnen verbinden met **Power BI Desktop**, moet de juiste Oracle-clientsoftware worden geïnstalleerd op de computer waarop Power BI Desktop wordt uitgevoerd. Welke Oracle-clientsoftware u moet gebruiken, is afhankelijk van welke versie van Power BI Desktop u hebt geïnstalleerd: de **32-bits** versie of de **64-bits** versie.

**Ondersteunde versies**: Oracle 9 en hoger, Oracle-clientsoftware 8.1.7 en hoger.

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Bepalen welke versie van Power BI Desktop is geïnstalleerd
Om te bepalen welke versie van Power BI Desktop is geïnstalleerd, selecteert u **Bestand > Help > Info** en schakelt u de regel **Versie:** in. Op de volgende afbeelding is een 64-bits versie van Power BI Desktop geïnstalleerd:

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>De Oracle-client installeren
Gebruik voor **32-bits** versies van Power BI Desktop de volgende koppeling om de **32-bits** Oracle-client te downloaden en te installeren:

* [32-bits Oracle Data Access Components (ODAC) met Oracle-ontwikkelhulpprogramma's voor Visual Studio (12.1.0.2.4)](http://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Gebruik voor **64-bits** versies van Power BI Desktop de volgende koppeling om de **64-bits** Oracle-client te downloaden en installeren:

* [64-bits ODAC 12c release 4 (12.1.0.2.4) voor Windows x64](http://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Verbinding maken met een Oracle-database
Zodra het overeenkomende clientstuurprogramma is geïnstalleerd, kunt u verbinding maken met een Oracle-database. Voer de volgende stappen uit om de verbinding tot stand te brengen:

1. Selecteer vanuit het venster Gegevens ophalen **Database > Oracle-database**
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Geef in het dialoogvenster **Oracle-database** dat wordt weergegeven de naam van de server op en selecteer **Verbinding maken**. Als een SID vereist is, kunt u deze opgeven in de volgende indeling: *Servernaam/SID*, waar SID de unieke naam van de database is. Als de indeling *Servernaam/SID* niet werkt, probeert u *Servernaam/Servicenaam*, waarbij Servicenaam de alias is die wordt gebruikt om verbinding te maken.


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Als u problemen ondervindt bij het maken van een verbinding in deze stap, probeert u de volgende indeling in het veld Servernaam: (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. Als u gegevens wilt importeren met behulp van een systeemeigen databasequery, kunt u uw query in het vak **SQL-instructie** plaatsen. Dit vak is beschikbaar als u het gedeelte **Geavanceerde opties** van het dialoogvenster **Oracle-database** uitvouwt.
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Selecteer nadat u de Oracle-databasegegevens hebt ingevoerd in het dialoogvenster Oracle-database (inclusief eventuele optionele gegevens als een SID of een systeemeigen databasequery) **OK** om verbinding te maken.
5. Als de Oracle-database gebruikersreferenties vereist, voert u deze referenties in het dialoogvenster in als u er om wordt gevraagd.


## <a name="troubleshooting"></a>Problemen oplossen

Als u Power BI Desktop vanuit de Microsoft Store hebt gedownload, kunt u wegens een probleem met een Oracle-stuurprogramma mogelijk geen verbinding maken met Oracle-databases. Als u te maken krijgt met dit probleem, wordt het foutbericht 'Objectverwijzing is niet ingesteld' geretourneerd. Voor het oplossen van het probleem voert u een van de volgende handelingen uit:

* Download Power BI Desktop via https://powerbi.microsoft.com/desktop.

* Als u de versie uit de Microsoft Store wilt gebruiken: kopieer op uw lokale computer oraons.dll vanuit _12.X.X\client_X_ naar _12.X.X\client_X\bin_. De X-aanduidingen staan voor de versie- en mapnummers.
