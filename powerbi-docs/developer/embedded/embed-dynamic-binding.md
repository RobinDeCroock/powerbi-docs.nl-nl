---
title: Een Power BI-rapport verbinden met een gegevensset met behulp van dynamische binding
description: Leer hoe u een Power BI-rapport insluit met behulp van dynamische binding in ingesloten analyses in Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565808"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Een rapport verbinden met een gegevensset met behulp van dynamische binding 

Wanneer een rapport is verbonden met een gegevensset, kunt u dynamische binding gebruiken. De verbinding tussen het rapport en de gegevensset wordt *binding* genoemd. Wanneer de binding wordt vastgesteld op het moment van insluiten, in plaats van eerder te worden bepaald, wordt de binding ook wel dynamische binding genoemd.

Wanneer u een Power BI-rapport met *dynamische binding* insluit, kunt u hetzelfde rapport verbinden met verschillende gegevenssets, afhankelijk van de referenties van de gebruiker.

Dit betekent dat u één rapport kunt gebruiken om verschillende gegevens weer te geven, afhankelijk van de gegevensset waarmee deze is verbonden. Een rapport dat bijvoorbeeld de verkoopwaarden van de detailhandel weergeeft, kan worden verbonden met verschillende gegevenssets van wederverkopers, en kan andere resultaten opleveren, afhankelijk van de gegevensset van de wederverkoper waarmee deze is verbonden.

Het rapport en de gegevensset hoeven zich niet in dezelfde werkruimte te bevinden. Beide werkruimten (één met het rapport en één met de gegevensset) moeten worden toegewezen aan een [capaciteit](azure-pbie-create-capacity.md).

Zorg er als onderdeel van het insluitingsproces voor dat u *een token met voldoende machtigingen genereert* en *het configuratie-object aanpast*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Een token met voldoende machtigingen genereren

Dynamische binding wordt ondersteund voor de scenario's *Inhoud insluiten voor uw organisatie* en *Inhoud insluiten voor uw klanten*. In de volgende tabel worden de overwegingen voor elk scenario beschreven.

|Scenario  |Eigendom van gegevens  |Token  |Vereisten  |
|---------|---------|---------|---------|
|*Inhoud insluiten voor uw organisatie*    |Gebruiker is eigenaar van gegevens         |Toegangstoken voor Power BI-gebruikers         |De gebruiker van wie het Azure AD-token wordt gebruikt, moet over de juiste machtigingen voor alle artefacten beschikken.         |
|*Inhoud insluiten voor uw klanten*     |App is eigenaar van gegevens         |Toegangstoken voor niet-Power BI-gebruikers         |Moet machtigingen voor zowel het rapport als de dynamisch gebonden gegevensset bevatten. Gebruik de [-API voor het genereren van een insluittoken voor meerdere items](/rest/api/power-bi/embedtoken/generatetoken) om een insluittoken te genereren dat meerdere artefacten ondersteunt.         |

## <a name="adjusting-the-config-object"></a>Het configuratieobject aanpassen

Dynamische binding werkt alleen als u `datasetBinding` aan het configuratieobject toevoegt. Zie [Gegevenssets dynamisch aan een rapport binden](/javascript/api/overview/powerbi/bind-report-datasets) voor meer informatie. 

## <a name="next-steps"></a>Volgende stappen

Als u voor het eerst inhoud in Power BI gaat insluiten, leest u eerst deze zelfstudies voor informatie over het insluiten van uw Power BI-inhoud.

>[!div class="nextstepaction"]
>[Power BI-inhoud insluiten in een toepassing voor uw klanten](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Power BI-inhoud insluiten in een toepassing voor uw organisatie](embed-sample-for-your-organization.md)