---
title: Relatieweergave in Power BI Desktop
description: Relatieweergave in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a39f675077d72698b62138aa1b9d56c5bf6a6958
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877843"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Relatieweergave in Power BI Desktop
In de **relatieweergave** worden alle tabellen, kolommen en relaties in uw model weergegeven. Dit kan met name handig zijn als uw model complexe relaties heeft tussen veel tabellen.

Laten we dit eens bekijken.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Het pictogram Relatieweergave: klik hierop om uw model in de relatieweergave weer te geven

**B.** Relatie: u kunt uw cursor over een relatie bewegen om de gebruikte kolommen weer te geven. Dubbelklik op een relatie om deze te openen in het dialoogvenster **Relatie bewerken**. 

In de bovenstaande afbeelding kunt u zien dat de tabel *Stores* een kolom *StoreKey* bevat die is gerelateerd aan de tabel *Sales* die ook een kolom *StoreKey* bevat. We zien dat het een *veel-op-één*-relatie (\*:1) is, en het pictogram in het midden van de regel laat zien dat de richting van het kruisfilter is ingesteld op *beide*. De pijl op het pictogram geeft de richting van de filtercontextstroom aan.

Zie [Relaties maken en beheren in Power BI Desktop](desktop-create-and-manage-relationships.md) voor meer informatie over relaties.

