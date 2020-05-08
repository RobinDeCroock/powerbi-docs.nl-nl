---
title: Richtlijnen voor Query Folding in Power BI Desktop
description: Richtlijnen voor het realiseren van Query Folding van Power Query in Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: e8123bba9f68305e1944dbfb280b5255e4fb9b48
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "75622144"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Richtlijnen voor Query Folding in Power BI Desktop

Dit artikel is bedoeld voor Power BI Desktop-gegevensmodelleerders die Importmodellen ontwikkelen. Er worden richtlijnen beschreven waarin wordt uitgelegd wanneer en hoe u Query Folding van Power Query kunt realiseren.

_Query Folding_ is de mogelijkheid om met een Power Query-query één query-instructie te genereren waarmee brongegevens worden opgehaald en getransformeerd. Zie [Query Folding van Power Query](/power-query/power-query-folding) voor meer informatie.

## <a name="guidance"></a>Hulp

De richtlijnen voor Query Folding verschillen, afhankelijk van de modelmodus.

Voor een **DirectQuery**-tabel of tabel met een modus voor **hybride** opslag moet Query Folding kunnen worden gerealiseerd door de Power Query-query.

Voor een **import**tabel kan het mogelijk zijn om Query Folding te realiseren. Wanneer de query is gebaseerd op een relationele bron, en als één SELECT-instructie kan worden samengesteld, realiseert u de _beste gegevensvernieuwingsprestaties_ door ervoor te zorgen dat Query Folding wordt toegepast. Als de mashup-engine van Power Query nog steeds nodig is om transformaties te verwerken, moet u ernaar streven om het werk dat deze moet verrichten te minimaliseren, vooral voor grote gegevenssets.

In de volgende opsommingslijst worden specifieke richtlijnen beschreven.

- **Delegeer zoveel mogelijk verwerking naar de gegevensbron**: Wanneer geen Query Folding kan worden toegepast voor alle stappen van een Power Query-query, zoek dan naar de stap die voorkomt dat Query Folding wordt toegepast. Verplaats, indien mogelijk, de latere stappen naar voren in de reeks, zodat deze in de Query Folding kunnen worden meegenomen. De mashup-engine van Power Query kan overigens slim genoeg zijn om de volgorde van de querystappen te wijzigen wanneer de bronquery wordt gegenereerd.

    Als voor een relationele gegevensbron de stap die de Query Folding voorkomt, kan worden gerealiseerd in één SELECT-instructie of binnen de procedurele logica van een opgeslagen procedure, kunt u een systeemeigen SQL-query gebruiken, zoals hierna wordt beschreven.

- **Gebruik een systeemeigen SQL-query**: Wanneer een Power Query-query gegevens ophaalt uit een relationele bron, is het voor sommige bronnen mogelijk om een systeemeigen SQL-query te gebruiken. De query kan in feite elke geldige instructie zijn, inclusief een opgeslagen procedure-uitvoering. Als de instructie meerdere resultatensets produceert, wordt alleen de eerste geretourneerd. Parameters kunnen worden gedeclareerd in de instructie en het wordt aanbevolen om de M-functie [Value.NativeQuery](/powerquery-m/value-nativequery) te gebruiken. Met deze functie worden veilig en eenvoudig parameterwaarden doorgegeven. Het is van belang om te weten dat de mashup-engine van Power Query geen Query Folding kan uitvoeren voor latere querystappen. Het is dus belangrijk om alle (of evenveel) transformatielogica op te nemen in de systeemeigen query-instructie.

    Er zijn twee belangrijke overwegingen die u in gedachten moet houden bij het gebruik van systeemeigen SQL-query's:

    - Voor een DirectQuery-modeltabel moet de query een SELECT-instructie zijn en kan deze geen algemene tabelexpressies (CTE's) of een opgeslagen procedure gebruiken.
    - Bij incrementeel vernieuwen kan geen systeemeigen SQL-query worden gebruikt. De mashup-engine van Power Query wordt dus gedwongen om alle bronrijen op te halen en vervolgens filters toe te passen om de incrementele wijzigingen te bepalen.

    > [!IMPORTANT]
    > Met een systeemeigen SQL-query kunt u mogelijk meer doen dan gegevens ophalen. Een geldige instructie kan worden uitgevoerd (en mogelijk meerdere malen), met inbegrip van een die gegevens wijzigt of verwijdert. Het is van belang dat u het principe van de minste rechten toepast om ervoor te zorgen dat aan het account dat wordt gebruikt om toegang te krijgen tot de database alleen leesrechten voor de vereiste gegevens zijn toegewezen.

- **Gegevens in de bron voorbereiden en transformeren**: Als u vaststelt dat er voor bepaalde Power Query-querystappen geen Query Folding kan worden uitgevoerd, is het wellicht mogelijk de transformaties in de gegevensbron toe te passen. De transformaties kunnen worden gerealiseerd door een databaseweergave te schrijven waarin de brongegevens logisch worden getransformeerd. Ze kunnen ook worden gerealiseerd door gegevens fysiek voor te bereiden en te materialiseren, voordat hierop query's worden uitgevoerd door Power BI. Een relationeel datawarehouse is een uitstekend voorbeeld van voorbereide gegevens, meestal bestaande uit vooraf geïntegreerde bronnen van organisatiegegevens.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- Conceptartikel over [Query Folding](/power-query/power-query-folding) van Power Query
- [Incrementeel vernieuwen in Power BI Premium](../service-premium-incremental-refresh.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
