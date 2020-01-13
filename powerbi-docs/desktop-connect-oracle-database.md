---
title: Verbinding maken met een Oracle-database
description: Stappen en downloads die nodig zijn om Oracle te verbinden met Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c2290963db54f150eed8176c2820c59f8f138666
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223268"
---
# <a name="connect-to-an-oracle-database"></a>Verbinding maken met een Oracle-database
Om een Oracle-database te kunnen verbinden met Power BI Desktop, moet de juiste Oracle-clientsoftware worden geïnstalleerd op de computer waarop Power BI Desktop wordt uitgevoerd. De Oracle-clientsoftware die u gebruikt, is afhankelijk van de door u geïnstalleerde versie van Power BI Desktop: 32-bits of 64-bits.

Ondersteunde Oracle-versies: 
- Oracle 9 en hoger
- Oracle-clientsoftware 8.1.7 en hoger

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Bepalen welke versie van Power BI Desktop is geïnstalleerd
Om te bepalen welke versie van Power BI Desktop is geïnstalleerd, selecteert u **Bestand** > **Help** > **Info** en schakelt u de regel **Versie** in. Op de volgende afbeelding is een 64-bits versie van Power BI Desktop geïnstalleerd:

![Power BI Desktop-versie](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>De Oracle-client installeren
- [Download en installeer de 32-bits Oracle-client](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html) voor de 32-bits versie van Power BI Desktop.

- [Download en installeer de 64-bits Oracle-client](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html) voor de 64-bits versie van Power BI Desktop.

## <a name="connect-to-an-oracle-database"></a>Verbinding maken met een Oracle-database
Nadat u het overeenkomende Oracle-clientstuurprogramma hebt geïnstalleerd, kunt u verbinding maken met een Oracle-database. Voer de volgende stappen uit om de verbinding tot stand te brengen:

1. Selecteer **Gegevens ophalen** op het tabblad **Start**. 

2. Selecteer in het venster **Gegevens ophalen** dat wordt weergegeven de optie **Meer** (indien nodig), selecteer **Database** > **Oracle-database** en selecteer vervolgens **Verbinding maken**.
   
   ![Verbinding maken met Oracle-database](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. Geef in het dialoogvenster **Oracle-database** dat wordt weergegeven de naam van de **server** op en selecteer **OK**. Als een SID vereist is, kunt u die opgeven in de volgende indeling: *Servernaam/SID*, waar *SID* de unieke naam van de database is. Als de indeling *Servernaam/SID* niet werkt, gebruikt u *Servernaam/Servicenaam*, waarbij *Servicenaam* de alias is die u gebruikt om verbinding te maken.


   ![Oracle-servernaam invoeren](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > Als u problemen ondervindt bij het maken van een verbinding in deze stap, gebruikt u de volgende indeling in het veld **Server**: *(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))*
   
3. Als u gegevens wilt importeren met behulp van een systeemeigen databasequery, plaatst u uw query in het vak **SQL-instructie**. Dit vak wordt weergegeven wanneer u het gedeelte **Geavanceerde opties** van het dialoogvenster **Oracle-database** uitvouwt.
   
   ![Geavanceerde opties uitvouwen](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. Nadat u de Oracle-databasegegevens hebt ingevoerd in het dialoogvenster **Oracle-database** (inclusief eventuele optionele gegevens als een SID of een systeemeigen databasequery) selecteert u **OK** om verbinding te maken.
5. Als de Oracle-database gebruikersreferenties vereist, voert u deze referenties in het dialoogvenster in als u er om wordt gevraagd.


## <a name="troubleshooting"></a>Problemen oplossen

Als u Power BI Desktop vanuit de Microsoft Store hebt gedownload, kunt u wegens een probleem met een Oracle-stuurprogramma mogelijk geen verbinding maken met Oracle-databases. Als u te maken krijgt met dit probleem, wordt het volgende foutbericht weergegeven: *Objectverwijzing is niet ingesteld*. Voor het oplossen van het probleem voert u een van de volgende stappen uit:

* Download Power BI Desktop via het [Downloadcentrum](https://www.microsoft.com/download/details.aspx?id=58494) in plaats van via de Microsoft Store.

* Als u de versie uit de Microsoft Store wilt gebruiken: kopieert u op uw lokale computer oraons.dll vanuit _12.X.X\client_X_ naar _12.X.X\client_X\bin_, waarbij _X_ staat voor de versie- en mapnummers.

Als u de foutmelding *Objectverwijzing is niet ingesteld* in de Power BI Gateway ziet wanneer u verbinding maakt met een Oracle-database, volgt u de instructies in [Uw gegevensbron beheren - Oracle](service-gateway-onprem-manage-oracle.md).
