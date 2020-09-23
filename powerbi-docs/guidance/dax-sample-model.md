---
title: DAX-voorbeeldmodel
description: DAX-voorbeeldmodel ter ondersteuning van verwijzingsartikelen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 0efa26a6ef3e47272d1434fab453a17ad9823c8c
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965442"
---
# <a name="dax-sample-model"></a>DAX-voorbeeldmodel

Het **Adventure Works DW 2020**-voorbeeldmodel van Power BI Desktop is ontworpen ter ondersteuning van uw DAX-training. Het model is gebaseerd op de [Adventure Works Data Warehouse-voorbeeld](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) voor AdventureWorksDW2017. De gegevens zijn echter aangepast aan de doelstellingen van het voorbeeldmodel.

## <a name="scenario"></a>Scenario

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Er wordt een afbeelding van het bedrijfslogo van Adventure Works weergegeven.":::

Het bedrijf Adventure Works vertegenwoordigt een fietsfabrikant die fietsen en accessoires verkoopt aan wereldwijde markten. Het bedrijf heeft hun datawarehouse-gegevens opgeslagen in een Azure SQL Database.

## <a name="model-structure"></a>Modelstructuur

Het model heeft zeven tabellen:

|Tabel|Beschrijving|
|-----|-------|
|**Customer**|Hierin worden klanten en hun geografische locatie beschreven. Klanten kopen producten online (Internetverkoop).|
|**Date**|Er zijn drie relaties tussen de tabellen **datum** en **verkoop**, voor orderdatum, verzenddatum en vervaldatum. De relatie orderdatum is actief. De omzet van het bedrijf gebruikt een boekjaar dat elk jaar op 1 juli begint. De tabel is gemarkeerd als datumtabel met de kolom **datum**.|
|**Product**|Alleen voltooide producten worden opgeslagen.|
|**Reseller**|Hierin worden resellers en hun geografische locatie beschreven. Reseller over het verkopen van producten aan hun klanten.|
|**Sales**|Hiermee worden verkooporderregels nauwkeuriger opgeslagen. Alle financiële waarden zijn in Amerikaanse dollars (USD). De vroegste besteldatum is 1 juli 2017 en de laatste besteldatum is 15 juni 2020.|
|**Verkooporder**|Hierin worden verkooporder en orderregelnummers beschreven, evenals het verkoopkanaal. Dit is **Reseller** of **Internet**. Deze tabel heeft een één-op-een-relatie met de tabel **Verkoop**.|
|**Verkoopgebied**|Verkoopgebieden zijn ingedeeld in groepen (Noord-Amerika, Europa en Pacific), landen en regio's. Alleen de Verenigde Staten verkoopt producten op regio-niveau.|

Het model bevat geen DAX-berekeningen.

## <a name="download-sample"></a>Voorbeeld downloaden

U kunt het Power BI Desktop-voorbeeldmodel [hier](https://aka.ms/dax-docs-sample-file) downloaden.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over dit artikel:

- [Naslaginformatie voor Data Analysis Expressions (DAX)](/dax/)
- Leertraject: [DAX gebruiken in Power BI Desktop](/learn/paths/dax-power-bi/)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)