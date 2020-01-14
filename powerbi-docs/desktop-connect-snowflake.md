---
title: Verbinding maken met een Snowflake Computing-magazijn in Power BI Desktop
description: Eenvoudig verbinding maken met een Snowflake Computing-magazijn in Power BI Desktop en dit gebruiken
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a62d1cf6d21df822265c3c41d4e74e74181b7051
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885196"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Verbinding met een Snowflake Computing-magazijn maken in Power BI Desktop
In Power BI Desktop kunt u verbinding maken met een **Snowflake** Computing-magazijn en gebruikmaken van de onderliggende gegevens, net zoals elke andere gegevensbron in Power BI Desktop. 

> [!NOTE]
> Hiervoor *moet* u het **Snowflake ODBC-stuurprogramma** installeren op computers die de **Snowflake**-connector gebruiken. Gebruik hiervoor de architectuur die overeenkomt met de installatie van **Power BI Desktop**, hetzij de 32-bits, hetzij de 64-bits versie. Klik op de volgende koppeling (Engelstalig) en [download het desbetreffende Snowflake ODBC-stuurprogramma](https://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Verbinding maken met een Snowflake Computing-magazijn
Als u verbinding wilt maken met een **Snowflake** Computing-magazijn, selecteert u **Gegevens ophalen** in het lint **Start** in Power BI Desktop. Selecteer **Database** uit de categorieën aan de linkerkant en u ziet **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

In het venster **Snowflake** dat verschijnt, typt of plakt u de naam van het Snowflake Computing-magazijn in het vak en selecteert u **OK**. U kunt desgewenst de gegevens rechtstreeks **importeren** in Power BI. U kunt ook **DirectQuery** gebruiken. Over het [gebruik van DirectQuery](desktop-use-directquery.md) kunt u meer informatie vinden (Engelstalig).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Voer uw gebruikersnaam en wachtwoord in als u daarom wordt gevraagd.

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> Als u uw gebruikersnaam en wachtwoord voor een bepaalde **Snowflake**-server hebt ingevoerd, worden deze referenties gebruikt bij volgende pogingen verbinding te maken. U kunt de referenties wijzigen via **Bestand > Opties en instellingen > Instellingen voor gegevensbron**.
> 
> 

Als u de Microsoft-accountoptie wilt gebruiken, laat u uw Snowflake-beheerder contact opnemen met Snowflake over het deelnemen aan de beperkte preview voor deze functie.

![Verificatietype via Microsoft-account in Snowflake-connector.](media/desktop-connect-snowflake/connect-snowflake-6.png)


Als u verbinding hebt gemaakt, verschijnt er een **Navigator**-scherm waarin de gegevens worden getoond die op de server beschikbaar zijn. Hier kunt u een of meer elementen selecteren die u in **Power BI Desktop** wilt importeren en gebruiken.

![ODBC-fout 28000 veroorzaakt een fout bij het maken van een verbinding.](media/desktop-connect-snowflake/connect_snowflake_5.png)

U kunt de geselecteerde tabel **laden**, waarna de hele tabel in **Power BI Desktop** wordt geladen. U kunt de query ook **bewerken**. Hiervoor wordt **Query Editor** geopend, zodat u de gewenste set gegevens kunt filteren en verfijnen, om deze verfijnde gegevensset vervolgens in **Power BI Desktop** te laden.

## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   

