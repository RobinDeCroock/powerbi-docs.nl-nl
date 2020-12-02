---
title: Verbinding maken met een OData-feed in Power BI Desktop
description: Eenvoudig verbinding maken met een OData-feed in Power BI Desktop en deze gebruiken
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 5c7d9464e8d14354ba893dd80d11a46b8ea170cc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405831"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Verbinding maken met OData-feeds in Power BI Desktop
In Power BI Desktop kunt u verbinding maken met een **OData-feed** en gebruikmaken van de onderliggende gegevens, net zoals elke andere gegevensbron in Power BI Desktop.

Als u verbinding wilt maken met een OData-feed, selecteert u **Get Data > OData-feed** op het lint **Start** in Power BI Desktop.

![Schermopname van het lint Gegevens ophalen in Power BI Desktop waarbij OData-feed is geselecteerd.](media/desktop-connect-odata/connect-to-odata_1.png)

In het venster **OData-feed** dat verschijnt, typt of plakt u de URL naar de OData-feed in het vak en selecteert u **OK**.

![Schermopname van het dialoogvenster OData-feed waarin het veld URL wordt weergegeven.](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop maakt verbinding met de OData-feed en geeft de beschikbare tabellen en andere gegevenselementen weer in het venster **Navigator**. Als u een element selecteert, wordt in het rechter deelvenster van het venster **Navigator** een overzicht van de gegevens weergegeven. U kunt zoveel tabellen importeren als u wilt. In het venster **Navigator** wordt een voorbeeld getoond van de momenteel geselecteerde tabel.

![Schermopname van het dialoogvenster Navigator waarin een voorbeeld van de gegevens van de geselecteerde tabel wordt weergegeven.](media/desktop-connect-odata/connect-to-odata_3.png)

U kunt de knop **Bewerken** kiezen, waarmee **Query Editor** wordt gestart. Hierin kunt u de gegevens uit de OData-feed vormgeven en transformeren voordat u ze in Power BI Desktop importeert. U kunt ook de knop **Laden** selecteren en alle gegevenselementen importeren die u in het linker deelvenster hebt geselecteerd.

Als u **Laden** selecteert, worden de geselecteerde items geïmporteerd en wordt een venster **Laden** weergegeven waarop de voortgang van het importeren wordt getoond.

![Schermopname van het dialoogvenster Laden waarin de voortgang van importeren wordt weergegeven.](media/desktop-connect-odata/connect-to-odata_4.png)

Als het importeren is voltooid, komen de geselecteerde tabellen en overige gegevenselementen beschikbaar in het deelvenster **Velden** aan de rechterkant van de weergave *Rapporten* in Power BI Desktop.

![Schermopname van het deelvenster Velden, waarin de lijst met geselecteerde tabellen wordt weergegeven.](media/desktop-connect-odata/connect-to-odata_5.png)

Dat is alles.

U bent nu klaar om de geïmporteerde gegevens uit de OData-feed in Power BI Desktop te gebruiken om visuele elementen of rapporten te maken of te werken met andere gegevens waarmee u verbinding wilt maken en importeren, zoals andere Excel-werkmappen, databases of een andere gegevensbron.

## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   
