---
title: DirectQuery gebruiken met gegevensstromen in Power BI (preview)
description: Leer DirectQuery te gebruiken met gegevensstromen in Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/19/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 9de8c9611b24eaa627b3ddf044f13d36d7b9a3d4
ms.sourcegitcommit: 250242fd6346b60b0eda7a314944363c0bacaca8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83694568"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>DirectQuery gebruiken met gegevensstromen in Power BI (preview)

U kunt DirectQuery gebruiken om rechtstreeks verbinding te maken met gegevensstromen en tegelijkertijd verbinding maken met uw gegevensstroom zonder dat u de gegevens erin hoeft te importeren. 

Door DirectQuery met gegevensstromen te gebruiken, worden de volgende verbeteringen aangebracht aan uw Power BI- en gegevensstroomprocessen:

* **Vermijd het gebruik van afzonderlijke vernieuwingsschema's**: DirectQuery maakt rechtstreeks verbinding met een gegevensstroom, waardoor het niet meer nodig is om een gegevensset te maken. Als zodanig betekent het dat als u DirectQuery met uw gegevensstromen gebruikt, u niet langer afzonderlijke vernieuwingsschema's nodig hebt voor de gegevensstroom en de gegevensset om er zeker van te zijn dat uw gegevens worden gesynchroniseerd.

* **Filteren van gegevens**: DirectQuery is handig als u wilt werken met een gefilterde weergave van gegevens in een gegevensstroom. Als u gegevens wilt filteren en u wilt werken met een kleinere subset van de gegevens in uw gegevensstroom, kunt u DirectQuery (en de berekeningsengine) gebruiken om gegevensstroomgegevens te filteren en te werken met de gefilterde subset die u nodig hebt.


## <a name="using-directquery-for-dataflows"></a>DirectQuery gebruiken voor gegevensstromen

Het gebruik van DirectQuery met gegevensstromen is een preview-functie die beschikbaar is vanaf de versie van Power BI Desktop die in mei 2020 wordt uitgebracht. 

Er zijn ook vereisten voor het gebruik van DirectQuery met gegevensstromen:

* Uw gegevensstroom moet zich in een werkruimte bevinden waarvoor Power BI Premium is ingeschakeld
* De **berekeningsengine** moet zijn ingeschakeld. Zie [De verbeterde berekeningsengine](service-dataflows-enhanced-compute-engine.md) voor meer informatie over de berekeningsengine.

## <a name="enable-directquery-for-dataflows"></a>DirectQuery inschakelen voor gegevensstromen

De status van de verbeterde berekeningsengine moet Geoptimaliseerd zijn, om uw gegevensstroom beschikbaar te kunnen maken voor toegang door DirectQuery. Stel de nieuwe optie **Instellingen voor de verbeterde berekeningsengine** in op **Geoptimaliseerd**, als u DirectQuery wilt inschakelen voor gegevensstromen. In de volgende afbeelding ziet u de instelling die juist is geselecteerd.

![De verbeterde berekeningsengine voor gegevensstromen inschakelen](media/service-dataflows-directquery/dataflows-directquery-01.png)

Zodra u deze instelling hebt toegepast, moet u de gegevensstroom vernieuwen om de optimalisatie van kracht te laten worden. 


## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Er zijn enkele bekende beperkingen met betrekking tot DirectQuery en gegevensstromen. Deze worden uitgelegd in de volgende lijst.

* DirectQuery voor gegevensstromen werkt niet als de previewversie van de functie **Verbeterde metagegevens** is ingeschakeld. Deze uitsluiting komt naar verwachting niet meer voor in een van de komende maandelijkse releases van Power BI Desktop.
* Tijdens de previewperiode van deze functie, krijgen sommige klanten mogelijk te maken met time-outs of prestatieproblemen als ze DirectQuery met gegevensstromen gebruiken. Tijdens deze previewperiode krijgen deze problemen de nodige aandacht.


## <a name="next-steps"></a>Volgende stappen

De volgende artikelen zijn nuttig voor aanvullende informatie en scenario's bij het gebruik van gegevensstromen:

* [Self-service data prep with dataflows](service-dataflows-overview.md) (Selfservice voor gegevensvoorbereiding met gegevensstromen)
* [Berekende entiteiten gebruiken in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Gegevensstromen gebruiken met on-premises gegevensbronnen](service-dataflows-on-premises-gateways.md)
* [Resources voor ontwikkelaars voor Power BI-gegevensstromen](service-dataflows-developer-resources.md)
* [Integratie van gegevensstromen en Azure Data Lake (preview)](service-dataflows-azure-data-lake-integration.md)

U kunt het overzichtsartikel lezen voor meer informatie over Common Data Model:
* [Overzicht van Common Data Model](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Meer informatie over het Common Data Model-schema en entiteiten op GitHub](https://github.com/Microsoft/CDM) (Engelstalig)

Gerelateerde artikelen over Power BI Desktop:

* [Verbinding maken met gegevenssets in de Power BI-service vanuit Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Queryoverzicht in Power BI Desktop](desktop-query-overview.md)

Gerelateerde artikelen over de Power BI-service:
* [Geplande vernieuwing configureren](../connect-data/refresh-scheduled-refresh.md)