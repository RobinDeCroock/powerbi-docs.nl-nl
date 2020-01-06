---
title: Datumtabellen instellen en gebruiken in Power BI Desktop
description: Informatie over het instellen van een tabel als datumtabel, en wat dat betekent, in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: b2a7f4434ac82a125352eaefdd2417d9039b710f
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "73868607"
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Datumtabellen instellen en gebruiken in Power BI Desktop

**Power BI Desktop** werkt achter de schermen om automatisch kolommen te identificeren die datums voorstellen, en maakt vervolgens namens u datumhiërarchieën en andere ondersteunende metagegevens voor uw model. Vervolgens kunt u deze ingebouwde hiërarchieën gebruiken bij het maken van rapportfuncties zoals visuals, tabellen, snelle metingen, slicers, enzovoort. Power BI Desktop doet dit door namens u verborgen tabellen te maken, die u vervolgens voor uw rapporten en DAX-expressies kunt gebruiken.

Lees het artikel [Automatische datum/tijd in Power BI Desktop](desktop-auto-date-time.md) voor meer informatie over dit automatische gedrag.

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

Bij het opgeven van uw eigen datumtabel is het belangrijk om te weten dat **Power BI Desktop** de hiërarchieën die het anders namens u in uw model zou bouwen, nu niet automatisch maakt. Als u uw datumtabel later deselecteert (en niet meer over een handmatig ingestelde datumtabel beschikt), maakt Power BI Desktop de automatisch ingebouwde datumtabellen opnieuw voor de datumkolommen in de tabel.

Bij het markeren van een tabel als datumtabel is het ook belangrijk om te weten dat de ingebouwde (automatisch gemaakte) datumtabel die Power BI Desktop had gemaakt, wordt verwijderd, en dat alle visuals of DAX-expressies die u eerder op basis van deze ingebouwde tabellen had gemaakt, niet meer goed functioneren. 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>Uw datumtabel instellen op het goede gegevenstype

Als u uw eigen **datumtabel** opgeeft, moet u ervoor zorgen dat het gegevenstype goed is ingesteld. U moet het **Gegevenstype** instellen op **Datum/Tijd** of op **Datum**. Voer de volgende stappen uit om dit te doen:

1. Selecteer uw **datumtabel** in het deelvenster **Velden**, vouw het uit indien nodig en selecteer vervolgens de kolom die als datum moet worden gebruikt.
   
    ![](media/desktop-date-tables/date-tables_04.png) 

2. Op het tabblad **Model maken** selecteert u **Gegevenstype:** en klikt u vervolgens op de vervolgkeuzepijl om de beschikbare gegevenstypen weer te geven.

    ![](media/desktop-date-tables/date-tables_05.png)

3. Geef het gegevenstype voor uw kolom op. 


## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Automatische datum/tijd in Power BI Desktop](desktop-auto-date-time.md)
* [Gegevenstypen in Power BI Desktop](desktop-data-types.md)
