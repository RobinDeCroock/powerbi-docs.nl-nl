---
title: Modelweergave gebruiken in Power BI Desktop
description: Een Modelweergave gebruiken om complexe gegevenssets in een visual weer te geven in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: b9df4398c410f52e3d5cdd51a99a40de107f5867
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760877"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>Werken met de modelweergave in Power BI Desktop

Met de **Modelweergave** in **Power BI Desktop** kunt u complexe gegevenssets met veel tabellen bekijken en gebruiken.


## <a name="using-modeling-view"></a>Modelweergave gebruiken

Selecteer het pictogram Modelweergave aan de linkerzijde van **Power BI Desktop**, die in de volgende afbeelding wordt weergegeven, om de Modelweergave te openen.

![Het pictogram Modelweergave in Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Afzonderlijke diagrammen maken

Met de Modelweergave kunt u diagrammen van uw model maken die alleen een subset van de tabellen in uw model bevatten. Hiermee krijgt u een duidelijker beeld van de tabellen waarmee u wilt werken en is het eenvoudiger om met complexe gegevenssets te werken. Als u een nieuw diagram wilt maken met alleen een subset van de tabellen, klikt u op het teken **+** naast het tabblad **Alle tabellen** aan de onderkant van het Power BI Desktop-venster.

![Een nieuw diagram maken door te klikken op het plusteken in de sectie tabbladen](media/desktop-modeling-view/modeling-view_03.png)

Vervolgens is het mogelijk om de tabel vanuit de lijst **Velden** naar het oppervlak van de diagram te slepen. Klik met de rechtermuisknop op de tabel en selecteer vervolgens **Gerelateerde tabellen toevoegen** in het menu dat verschijnt.

![Klik met de rechtermuisknop op een tabel en selecteer Gerelateerde tabellen toevoegen](media/desktop-modeling-view/modeling-view_04.png)

Wanneer u dit doet worden aan de originele tabel gerelateerde tabellen weergegeven in een nieuw diagram. In de volgende afbeelding ziet u hoe gerelateerde tabellen worden weergegeven nadat u de menu-optie **Gerelateerde tabellen toevoegen** hebt geselecteerd.

![Gerelateerde tabellen weergeven](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Algemene eigenschappen instellen

U kunt meerdere objecten tegelijkertijd selecteren in de Modelweergave door de toets **CTRL** in te houden en meerdere tabellen aan te klikken. Wanneer u meerdere tabellen selecteert, worden deze gemarkeerd in de Modelweergave. Wanneer er meerdere tabellen zijn gemarkeerd, worden wijzigingen in het venster **Eigenschappen** ook toegepast op de geselecteerde tabellen.

U kunt bijvoorbeeld de [opslagmodus](desktop-storage-mode.md) voor meerdere tabellen in de diagramweergave wijzigen door de toets **CTRL** in te houden, tabellen te selecteren en vervolgens de instelling Opslagmodus te wijzigen in het venster **Eigenschappen**.

![Meerdere tabellen selecteren door CTRL in te houden en vervolgens algemene eigenschappen in meerdere geselecteerde tabellen instellen](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Volgende stappen

De volgende artikelen bevatten meer informatie over gegevensmodellen, evenals een gedetailleerde beschrijving van DirectQuery.

* [Aggregaties in Power BI Desktop (preview-versie)](desktop-aggregations.md)
* [Samengestelde modellen in Power BI Desktop](desktop-composite-models.md)
* [Opslagmodus in Power BI Desktop (preview-versie)](desktop-storage-mode.md)
* [Veel-op-veel-relaties in Power BI Desktop](desktop-many-to-many-relationships.md)


DirectQuery-artikelen:

* [DirectQuery gebruiken in Power BI](desktop-directquery-about.md)
* [Gegevensbronnen die worden ondersteund door DirectQuery in Power BI](desktop-directquery-data-sources.md)
