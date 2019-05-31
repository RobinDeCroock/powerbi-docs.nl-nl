---
title: Verbinding maken met een Snowflake Computing-magazijn in Power BI Desktop
description: Eenvoudig verbinding maken met een Snowflake Computing-magazijn in Power BI Desktop en dit gebruiken
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c02eda44ec81fe31972055548996ae357bc4c4b9
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513826"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Verbinding maken met Snowflake in Power BI Desktop
In Power BI Desktop kunt u verbinding maken met een **Snowflake** Computing-magazijn en gebruikmaken van de onderliggende gegevens, net zoals elke andere gegevensbron in Power BI Desktop. 

> [!NOTE]
> Hiervoor *moet* u het **Snowflake ODBC-stuurprogramma** installeren op computers die de **Snowflake**-connector gebruiken. Gebruik hiervoor de architectuur die overeenkomt met de installatie van **Power BI Desktop**, hetzij de 32-bits, hetzij de 64-bits versie. Klik op de volgende koppeling (Engelstalig) en [download het desbetreffende Snowflake ODBC-stuurprogramma](http://go.microsoft.com/fwlink/?LinkID=823762).
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Verbinding maken met een Snowflake Computing-magazijn
Als u verbinding wilt maken met een **Snowflake** Computing-magazijn, selecteert u **Gegevens ophalen** in het lint **Start** in Power BI Desktop. Selecteer **Database** uit de categorieën aan de linkerkant en u ziet **Snowflake**.

![](media/desktop-connect-snowflake/connect_snowflake_2b.png)

In het venster **Snowflake** dat verschijnt, typt of plakt u de naam van het Snowflake Computing-magazijn in het vak en selecteert u **OK**. U kunt desgewenst de gegevens rechtstreeks **importeren** in Power BI. U kunt ook **DirectQuery** gebruiken. Over het [gebruik van DirectQuery](desktop-use-directquery.md) kunt u meer informatie vinden (Engelstalig).

![](media/desktop-connect-snowflake/connect_snowflake_3.png)

Voer uw gebruikersnaam en wachtwoord in als u daarom wordt gevraagd.

![](media/desktop-connect-snowflake/connect_snowflake_4.png)

> [!NOTE]
> Als u uw gebruikersnaam en wachtwoord voor een bepaalde **Snowflake**-server hebt ingevoerd, worden deze referenties gebruikt bij volgende pogingen verbinding te maken. U kunt de referenties wijzigen via **Bestand > Opties en instellingen > Instellingen voor gegevensbron**.
> 
> 

Als u verbinding hebt gemaakt, verschijnt er een **Navigator**-scherm waarin de gegevens worden getoond die op de server beschikbaar zijn. Hier kunt u een of meer elementen selecteren die u in **Power BI Desktop** wilt importeren en gebruiken.

![](media/desktop-connect-snowflake/connect_snowflake_5.png)

U kunt de geselecteerde tabel **laden**, waarna de hele tabel in **Power BI Desktop** wordt geladen. U kunt de query ook **bewerken**. Hiervoor wordt **Query Editor** geopend, zodat u de gewenste set gegevens kunt filteren en verfijnen, om deze verfijnde gegevensset vervolgens in **Power BI Desktop** te laden.

## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   

