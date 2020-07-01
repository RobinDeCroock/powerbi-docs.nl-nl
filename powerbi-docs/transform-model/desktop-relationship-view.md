---
title: Modelweergave in Power BI Desktop
description: Modelweergave in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1c580d403ef33f1c61d5fcd0707d78b4b331da5d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239859"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Werken met de modelweergave in Power BI Desktop

In de *modelweergave* worden alle tabellen, kolommen en relaties in uw model weergegeven. Deze weergave kan met name handig zijn als uw model complexe relaties heeft tussen veel tabellen.

Selecteer het pictogram **Model** aan de zijkant van het venster om een weergave van het bestaande model te bekijken. Beweeg uw cursor over een relatieregel om de gebruikte kolommen weer te geven.

![Modelweergave, Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

In de afbeelding bevat de tabel *Stores* een kolom *StoreKey* die is gerelateerd aan de tabel *Sales* die ook een kolom *StoreKey* bevat. De twee tabellen hebben een *veel-op-een* (\*: 1)-relatie. Een pijl in het midden van de regel geeft de richting van de filtercontextstroom aan. De dubbele pijl betekent dat de richting voor kruislings filteren is ingesteld op *Beide*.

U kunt dubbelklikken op een relatie om deze te openen in het dialoogvenster **Relatie bewerken**. Zie [Relaties maken en beheren in Power BI Desktop](desktop-create-and-manage-relationships.md) voor meer informatie over relaties.
