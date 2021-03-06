---
title: Verbinding met CSV-bestanden maken in Power BI Desktop
description: Eenvoudig verbinding maken met gegevens uit een CSV-bestand in Power BI Desktop en deze gebruiken
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 3bb37d4ba3b3ca7d5fec3f8577b971432f5a9d0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411374"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Verbinding met CSV-bestanden maken in Power BI Desktop
Verbinding maken met een bestand met door komma's gescheiden waarden (*CSV*) vanuit Power BI Desktop lijkt erg veel op verbinding maken met een Excel-werkmap. Beide zijn erg eenvoudig uit te voeren en in dit artikel leert u de stappen kennen om verbinding te maken met een CSV-bestand waartoe u toegang hebt.

Selecteer vanuit Power BI Desktop eerst **Gegevens ophalen > CSV** op het lint **Start**.

![Schermopname van het menu Gegevens ophalen.](media/desktop-connect-csv/connect-to-csv_1.png)

Selecteer het CSV-bestand in het dialoogvenster **Openen** dat wordt weergegeven.

![Schermopname van het dialoogvenster Openen.](media/desktop-connect-csv/connect-to-csv_2.png)

Als u **Openen** selecteert, wordt het bestand geopend en worden bepaalde bestandskenmerken vastgesteld, zoals de oorsprong, het type scheidingsteken en hoeveel rijen er moeten worden gebruikt om de gegevenstypen in het bestand te kunnen detecteren.

Deze bestandskenmerken en opties worden weergegeven in de vervolgkeuzelijsten boven aan het dialoogvenster **CSV-import**, zoals hieronder weergegeven. U kunt deze gedetecteerde instellingen handmatig wijzigen door een andere optie te kiezen in een van de vervolgkeuzelijsten.

![Schermopname van het dialoogvenster CSV-import.](media/desktop-connect-csv/connect-to-csv_3.png)

Als u tevreden bent met uw selecties, kunt u **Laden** selecteren om het bestand in Power BI Desktop te importeren. U kunt ook **Bewerken** selecteren om **Query Editor** te selecteren en de gegevens verder vorm te geven en te transformeren voordat u ze importeert.

Als u de gegevens in Power BI Desktop laadt, ziet u de tabel en de bijbehorende kolommen (die in Power BI Desktop als velden worden voorgesteld) in het deelvenster **Velden** aan de rechterkant van de rapportweergave in Power BI Desktop.

![Schermopname van het venster van Power BI Desktop met het deelvenster Velden.](media/desktop-connect-csv/connect-to-csv_4.png)

Meer hoeft u niet te doen; de gegevens in uw CSV-bestand staan nu in Power BI Desktop.

U kunt deze gegevens in Power BI Desktop gebruiken om visuele elementen of rapporten te maken of te werken met andere gegevens waarmee u verbinding wilt maken en die u wilt importeren, zoals Excel-werkmappen, databases of een andere gegevensbron.

> [!IMPORTANT]
> Wanneer u een CSV-bestand importeert, wordt in Power BI Desktop een *kolommen=x* gemaakt als stap in Power Query-editor (waarbij *x* het aantal kolommen in het CSV-bestand is tijdens de initiële import). Als u daarna meer kolommen toevoegt en de gegevensbron is ingesteld op vernieuwen, worden alle kolommen die de initiële *x* kolommen overschrijden, niet vernieuwd. 


## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   
