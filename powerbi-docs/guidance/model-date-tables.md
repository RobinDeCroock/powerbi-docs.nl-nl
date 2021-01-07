---
title: Datumtabellen in Power BI Desktop maken
description: Technieken en richtlijnen voor het maken van datumtabellen in Power BI Desktop.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: a2616b5f77a03056de03b213369d55e9b590b1b6
ms.sourcegitcommit: 7599622381f35a161bfc54726675ed3c9cf13816
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/31/2020
ms.locfileid: "97827567"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Datumtabellen in Power BI Desktop maken

Dit artikel is geschreven voor iedereen die gegevensmodellen maakt met Power BI Desktop. Er worden goede ontwerpmethoden beschreven voor het maken van datumtabellen in uw gegevensmodellen.

Als u wilt werken met DAX (Data Analysis Expressions) [Time Intelligence-functies](/dax/time-intelligence-functions-dax), is er een vereiste modelvereiste: Uw model moet ten minste één _datumtabel_ bevatten. Een datumtabel is een tabel die voldoet aan de volgende vereisten:

> [!div class="checklist"]
> - De tabel moet een kolom van het gegevenstype **datum** (of **datum/tijd**) bevatten, ook wel de _datumkolom_ genoemd.
> - De datumkolom moet unieke waarden bevatten.
> - De datumkolom mag geen lege waarden bevatten.
> - De datumkolom mag geen ontbrekende datums bevatten.
> - De datumkolom moet volledige jaren omvatten. Een jaar is niet noodzakelijkerwijs een kalenderjaar (januari-december).
> - De datumtabel moet [als datumtabel zijn gemarkeerd](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

U kunt een van de volgende technieken gebruiken om een datumtabel aan uw model toe te voegen:

- De optie voor automatische datum/tijd
- Power Query om verbinding te maken met een datumdimensietabel
- Power Query voor het genereren van een datumtabel
- DAX voor het genereren van een datumtabel
- DAX voor het klonen van een bestaande datumtabel

> [!TIP]
> Een datumtabel is misschien de meest consistente functie die u aan uw modellen gaat toevoegen. Bovendien moet een datumtabel in een organisatie consistent worden gedefinieerd. Welke techniek u ook gebruik, u wordt aangeraden om een [Power BI Desktop-sjabloon](../create-reports/desktop-templates.md) te maken die een volledig geconfigureerde datumtabel bevat. Deel de sjabloon met alle modelmakers in uw organisatie. Wanneer iemand een nieuw model ontwikkelt, kunnen ze dus beginnen met een consistent gedefinieerde datumtabel.

## <a name="use-auto-datetime"></a>Automatische datum/tijd gebruiken

De optie [Automatische datum/tijd](../transform-model/desktop-auto-date-time.md) biedt handige, snelle en gebruiksvriendelijke time intelligence. Rapportauteurs kunnen werken met time intelligence bij het filteren, groeperen en inzoomen op kalenderperioden.

We raden u aan de optie Automatische datum/tijd- alleen ingeschakeld te laten wanneer u met kalenderperioden werkt en wanneer u eenvoudige modelvereisten hebt met betrekking tot tijd. Het gebruik van deze optie kan ook handig zijn bij het maken van ad-hocmodellen of bij het verkennen of profileren van gegevens. Deze methode biedt echter geen ondersteuning voor één datumtabelontwerp waarmee filters kunnen worden doorgegeven aan meerdere tabellen. Zie [Richtlijnen voor automatische datum/tijd in Power BI Desktop](auto-date-time.md) voor meer informatie.

## <a name="connect-with-power-query"></a>Verbinding maken met Power Query

Als uw gegevensbron al een datumtabel heeft, raden we u aan deze te gebruiken als de bron van de modeldatumtabel. Dit is doorgaans het geval wanneer u verbinding maakt met een datawarehouse, omdat deze een datumdimensietabel bevat. Op deze manier maakt uw model gebruik van Single Source of Truth voor tijd in uw organisatie.

Als u een DirectQuery-model ontwikkelt en uw gegevensbron bevat geen datumtabel, wordt u ten zeerste aangeraden een datumtabel aan de gegevensbron toe te voegen. Deze moet voldoen aan alle modelvereisten van een datumtabel. Vervolgens kunt u Power Query gebruiken om verbinding te maken met de datumtabel. Op deze manier kunnen uw modelberekeningen gebruikmaken van de Time Intelligence-mogelijkheden van DAX.

## <a name="generate-with-power-query"></a>Genereren met Power Query

U kunt een datumtabel genereren met behulp van Power Query. Zie de blogpost van Chris Webb [Een datumdimensietabel genereren in Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) voor meer informatie.

> [!TIP]
> Als u geen datawarehouse of andere consistente definitie voor tijd in uw organisatie hebt, kunt u Power Query gebruiken om een [gegevensstroom](../transform-model/dataflows/dataflows-introduction-self-service.md) te publiceren. Laat alle makers van gegevensmodellen vervolgens verbinding maken met de gegevensstroom om datumtabellen toe te voegen aan hun modellen. De gegevensstroom wordt de Single Source of Truth voor tijd in uw organisatie.

Als u een datumtabel wilt genereren, kunt u hier eventueel DAX voor gebruiken. Dat kan makkelijker zijn. Het is waarschijnlijk ook handiger, omdat DAX ingebouwde intelligentie bevat om het maken en beheren van datumtabellen te vereenvoudigen.

## <a name="generate-with-dax"></a>Genereren met DAX

U kunt een datumtabel in uw model genereren door een berekende tabel te maken met behulp van de DAX-functies [CALENDAR](/dax/calendar-function-dax) of [CALENDARAUTO](/dax/calendarauto-function-dax). Elke functie retourneert een tabel met één kolom met datums. U kunt de berekende tabel vervolgens uitbreiden met berekende kolommen ter ondersteuning van de vereisten voor het filteren en groeperen van datumintervallen.

- Gebruik de functie **CALENDAR** wanneer u een datumbereik wilt definiëren. U geeft twee waarden op: de begindatum en de einddatum. Deze waarden kunnen worden gedefinieerd door andere DAX-functies, zoals `MIN(Sales[OrderDate])` of `MAX(Sales[OrderDate])`.
- Gebruik de functie **CALENDARAUTO** als u wilt dat het datumbereik automatisch alle datums omvat die in het model zijn opgeslagen. U kunt één optionele parameter opgeven als laatste maand van het jaar (als uw jaar een kalenderjaar is dat eindigt op december, hoeft u geen waarde op te geven). Het is een handige functie, omdat deze ervoor zorgt dat de volledige jaren met datums worden geretourneerd. Dit is een vereiste voor een gemarkeerde datumtabel. Bovendien hoeft u de tabel niet uit te breiden naar toekomstige jaren: Wanneer het vernieuwen van gegevens is voltooid, wordt de herberekening van de tabel geactiveerd. Bij een herberekening wordt het datumbereik van de tabel automatisch uitgebreid wanneer de datums voor een nieuw jaar in het model worden geladen.

## <a name="clone-with-dax"></a>Klonen met DAX

Als uw model al een datumtabel heeft en u een aanvullende datumtabel nodig hebt, kunt u de bestaande datumtabel gemakkelijk klonen. Dat is het geval wanneer de datum een [dimensie is met een actieve rol is](star-schema.md#role-playing-dimensions). U kunt een tabel klonen door een berekende tabel te maken. De expressie voor de berekende tabel is gewoon de naam van de bestaande datumtabel.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Automatische datum/tijd in Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Hulp met automatische datum/tijd in Power BI Desktop](auto-date-time.md)
- [Datumtabellen instellen en gebruiken in Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Selfservice voor gegevensvoorbereiding in Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [CALENDAR-functie (DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO-functie (DAX)](/dax/calendarauto-function-dax)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)