---
title: Datumtabellen instellen en gebruiken in Power BI Desktop
description: Informatie over het instellen van een tabel als datumtabel, en wat dat betekent, in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 9bbe302c7187419abae556bb34f991efa1fdae00
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454366"
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Datumtabellen instellen en gebruiken in Power BI Desktop

**Power BI Desktop** werkt achter de schermen voor kolommen die staan voor datums automatisch identificeren en maakt vervolgens datumhiërarchieën en andere ondersteunende metagegevens voor uw model uit uw naam. Vervolgens kunt u deze ingebouwde hiërarchieën gebruiken bij het maken van rapportfuncties zoals visuals, tabellen, snelle metingen, slicers, enzovoort. Power BI Desktop doet dit door namens u verborgen tabellen te maken, die u vervolgens voor uw rapporten en DAX-expressies kunt gebruiken.

Veel gegevensanalisten maken het liefst hun eigen datumtabellen. Hier is niets mis mee. In **Power BI Desktop** kunt u opgeven welke tabel u door uw model als **datumtabel** wilt laten gebruiken en vervolgens datumgerelateerde visuals, tabellen, snelle metingen, enzovoort maken met behulp van de datumgegevens van die tabel. Als u uw eigen datumtabel opgeeft, beheert u de datumhiërarchieën die in uw model zijn gemaakt en gebruikt u die in **snelle metingen** en andere bewerkingen die de datumtabel van uw model gebruiken. 

![](media/desktop-date-tables/date-tables_01.png)

## <a name="setting-your-own-date-table"></a>Uw eigen datumtabel instellen

Als u een **datumtabel** wilt instellen, selecteert u de tabel die u als datumtabel wilt gebruiken in het deelvenster **Velden**, klikt u met de rechtermuisknop op de tabel en selecteert u **Als datumtabel markeren > Als datumtabel markeren** in het menu dat verschijnt, zoals dat in de volgende afbeelding wordt weergegeven.

![](media/desktop-date-tables/date-tables_02.png)

U kunt ook de tabel selecteren en vervolgens **Als datumtabel markeren** selecteren op het lint **Model maken**, dat hier wordt weergegeven.

![](media/desktop-date-tables/date-tables_02b.png)

As u uw eigen **datumtabel** opgeeft, voert Power BI Desktop de volgende validaties uit voor die kolom en de bijbehorende gegevens om er zeker van te zijn dat de gegevens:

* unieke waarden bevatten
* geen null-waarden bevatten
* aaneengesloten datumwaarden bevatten (van begin tot eind)
* als het een gegevenstype **Datum/Tijd** betreft, heeft het dezelfde tijdstempel voor elke waarde

Er zijn twee aannemelijke scenario's voor het maken van uw eigen datumtabel. Beide benaderingen zijn redelijk:

* Het eerste scenario is wanneer u een canonieke, oftewel een eenvoudige datumtabel en -hiërarchie gebruikt. Dit is een tabel in uw gegevens die voldoet aan de eerder beschreven validatiecriteria voor een datumtabel. 

* Het tweede scenario is wanneer u een tabel van Analysis Services gebruikt, bijvoorbeeld met een veld *dimensie-datum* dat u wilt gebruiken als uw datumtabel. 

Zodra u een datumtabel hebt opgegeven, kunt u selecteren welke kolom in die tabel de datumkolom is. U kunt opgeven welke kolom moet worden gebruikt door de tabel te selecteren in het deelvenster **Velden**. Klik vervolgens met de rechtermuisknop op de tabel en selecteer **Als datumtabel markeren > Instellingen datumtabel**. Nu wordt het volgende venster weergegeven. Hier kunt u uit de vervolgkeuzelijst kiezen welke kolom u als datumtabel gaat gebruiken.

![](media/desktop-date-tables/date-tables_03.png)

Bij het opgeven van uw eigen datumtabel is het belangrijk om te weten dat **Power BI Desktop** de hiërarchieën die het anders namens u in uw model zou bouwen, nu niet automatisch maakt. Als u uw datumtabel later deselecteert (en hoeft niet langer een handmatig ingestelde datumtabel), Power BI Desktop maakt de automatisch ingebouwde datumtabellen opnieuw voor u, voor de datumkolommen in de tabel.

Bij het markeren van een tabel als datumtabel is het ook belangrijk om te weten dat de ingebouwde (automatisch gemaakte) datumtabel die Power BI Desktop had gemaakt, wordt verwijderd, en dat alle visuals of DAX-expressies die u eerder op basis van deze ingebouwde tabellen had gemaakt, niet meer goed functioneren. 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>Uw datumtabel instellen op het goede gegevenstype

Als u uw eigen **datumtabel** opgeeft, moet u ervoor zorgen dat het gegevenstype goed is ingesteld. U moet het **Gegevenstype** instellen op **Datum/Tijd** of op **Datum**. Voer de volgende stappen uit om dit te doen:

1. Selecteer uw **datumtabel** in het deelvenster **Velden**, vouw het uit indien nodig en selecteer vervolgens de kolom die als datum moet worden gebruikt.
   
    ![](media/desktop-date-tables/date-tables_04.png) 

2. Op het tabblad **Model maken** selecteert u **Gegevenstype:** en klikt u vervolgens op de vervolgkeuzepijl om de beschikbare gegevenstypen weer te geven.

    ![](media/desktop-date-tables/date-tables_05.png)

3. Geef het gegevenstype voor uw kolom op. 


## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen.

* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)

 
