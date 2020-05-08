---
title: Verwijzende Power Query-query's
description: Richtlijnen voor verwijzende Power Query-query's.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 49601798ae920d956441c5580079625bf7408e07
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "78290562"
---
# <a name="referencing-power-query-queries"></a>Verwijzende Power Query-query's

Dit artikel is geschreven voor iedereen die gegevensmodellen maakt met Power BI Desktop. U vindt hier richtlijnen voor het definiëren van Power Query-query's die verwijzen naar andere query's.

Dit houdt het volgende in: _Wanneer een query verwijst naar een andere query, is dit alsof de stappen in de tweede query worden gecombineerd met en worden uitgevoerd vóór, de stappen in de eerste query._

Bekijk de volgende query's: **Query1** haalt gegevens op van een webservice en het laden ervan is uitgeschakeld. **Query2**, **Query3**en **Query4** verwijzen allemaal naar **query1** en de uitvoergegevens ervan worden in het gegevensmodel geladen.

![Weergave van query-afhankelijkheden van de query's die zijn beschreven in de vorige alinea.](media/power-query-referenced-queries/query-dependencies-web-service.png)

Men gaat er vaak vanuit dat bij het vernieuwen van het gegevensmodel in Power Query het resultaat van **Query1** wordt opgehaald en opnieuw wordt gebruikt door query's waarnaar wordt verwezen. Dat is echter onjuist. In werkelijkheid worden **Query2**, **Query3** en **Query4** afzonderlijk uitgevoerd in Power Query.

U kunt het zien alsof **Query2** de stappen van **Query1** bevat. Dit geldt ook voor **Query3** en **Query4**. Het volgende diagram geeft een duidelijk beeld van hoe de query's worden uitgevoerd.

![Een gewijzigde versie van de weergave Query-afhankelijkheden, met query 2, query 3 en query 4. In elk van de drie query's is query 1 ingesloten.](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Query1** wordt drie keer uitgevoerd. De verschillende query-uitvoeringen kunnen resulteren in trage gegevensvernieuwing en slechte prestaties van de gegevensbron.

Het gebruik van de functie [Table.Buffer](/powerquery-m/table-buffer) in **Query1** voorkomt niet dat er aanvullende gegevens worden opgehaald. Deze functie buffert een tabel in het geheugen. De gebufferde tabel kan alleen worden gebruikt binnen dezelfde query-uitvoering. Dus als in het voorbeeld **Query1** wordt gebufferd wanneer **Query2** wordt uitgevoerd, kunnen de gebufferde gegevens niet worden gebruikt wanneer **Query3** en **Query4** worden uitgevoerd. Die query's bufferen de gegevens zelf tweemaal. (Dit kan ook negatieve gevolgen hebben voor de prestaties, omdat de tabel wordt gebufferd door elke verwijzende query.)

> [!NOTE]
> De cache-architectuur van Power Query is complex en het valt buiten het bereik van dit artikel om deze in detail te beschrijven. Power Query kan gegevens die zijn opgehaald uit een gegevensbron, opslaan in de cache. Bij het uitvoeren van een query kunnen de gegevens van de gegevensbron echter meermaals worden opgehaald.

## <a name="recommendations"></a>Aanbevelingen

Over het algemeen raden we u aan om naar query's te verwijzen om dubbele querylogica te voorkomen. Maar, zoals beschreven in dit artikel, kan deze methode leiden tot trage gegevensvernieuwing en overbelasting van gegevensbronnen.

U wordt aangeraden om in plaats daarvan een [gegevensstroom](../service-dataflows-overview.md) te maken. Het gebruik van een gegevensstroom kan de gegevensvernieuwingstijd verbeteren en de invloed op uw gegevensbronnen verminderen.

U kunt de gegevensstroom zo ontwerpen dat de brongegevens en transformaties worden ingekapseld. Omdat de gegevensstroom een blijvende opslag van gegevens in de Power BI-service is, gaat het ophalen van gegevens snel. Dus zelfs wanneer queryverwijzingen resulteren in meerdere aanvragen voor de gegevensstroom, kunnen de tijden voor het vernieuwen van gegevens worden verbeterd.

Als **Query1** opnieuw is ontworpen als een gegevensstroomentiteit, kunnen **Query2**, **Query3**en **Query4** deze gebruiken als een gegevensbron. In dit ontwerp wordt de bronentiteit van **Query1** slechts eenmaal geëvalueerd.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Selfservice voor gegevensvoorbereiding in Power BI](../service-dataflows-overview.md)
- [Gegevensstromen maken en gebruiken in Power BI](../service-dataflows-create-use.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
