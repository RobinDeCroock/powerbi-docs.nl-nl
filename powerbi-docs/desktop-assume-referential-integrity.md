---
title: De instelling Referentiële integriteit aannemen in Power BI Desktop
description: Via DirectQuery leren hoe u Power BI Desktop referentiële integriteit kunt laten aannemen
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1e4e13ddf098d68d48fcbe968c325e9a9458b3df
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239866"
---
# <a name="assume-referential-integrity-settings-in-power-bi-desktop"></a>De instellingen voor Referentiële integriteit aannemen in Power BI Desktop
Als u via **DirectQuery** verbinding maakt met een gegevensbron, kunt u de selectie **Referentiële integriteit aannemen** gebruiken om efficiëntere query's voor uw gegevensbron uit te voeren. Voor deze functie gelden enkele vereisten van de onderliggende gegevens en de functie is alleen beschikbaar wanneer u **DirectQuery** gebruikt.

Als u **Referentiële integriteit aannemen** instelt, kunnen query's op de gegevensbron gebruikmaken van **INNER JOIN**-instructies in plaats van **OUTER JOIN**-instructies, waardoor de efficiëntie van de query wordt verbeterd.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

## <a name="requirements-for-using-assume-referential-integrity"></a>Vereisten voor het gebruik van Referentiële integriteit aannemen
Dit is een geavanceerde instelling die alleen wordt ingeschakeld wanneer u verbinding maakt met gegevens via **DirectQuery**. De volgende vereisten zijn nodig om **Referentiële integriteit aannemen** goed te laten werken:

* Gegevens in de kolom **Van** in de relatie zijn nooit *Null* of *leeg*
* Voor elke waarde in de kolom **Van** is er een overeenkomstige waarde in de kolom **Aan**

In deze context is de kolom **Aan** de *veel* in een *een-op-veelrelatie* of het is de kolom in de eerste tabel in een *een-op-eenrelatie*.

## <a name="example-of-using-assume-referential-integrity"></a>Voorbeeld van het gebruik van Referentiële integriteit aannemen
In het volgende voorbeeld wordt het gedrag van **Referentiële integriteit aannemen** gedemonstreerd bij het gebruik in gegevensverbindingen. In het voorbeeld wordt verbinding gemaakt met een gegevensbron met een tabel **Orders**, een tabel **Products** en een tabel **Depots**.

1. In de volgende afbeelding, waarin de tabel **Orders** en de tabel **Products** wordt getoond, ziet u dat er referentiële integriteit bestaat tussen **Orders[ProductID]** en **Products[ProductID]** . De kolom **[ProductID]** in de tabel **Orders** is nooit *Null* en elke waarde wordt ook weergegeven in de tabel **Producten**. Daarom moet **Referentiële integriteit aannemen** zodanig worden ingesteld dat er efficiëntere query's kunnen worden opgehaald (met deze instelling worden de waarden in de visuele elementen niet gewijzigd).
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_2.png)
2. In de volgende afbeelding ziet u dat er geen referentiële integriteit bestaat tussen **Orders[DepotID]** en **Depots[DepotID]** , omdat **DepotID** *Null* is voor sommige *Orders*. Daarom moet **Referentiële integriteit aannemen** *niet* worden ingesteld.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_3.png)
3. Tot slot: er bestaat geen referentiële integriteit tussen **Orders[CustomerID]** en **Customers[CustID]** in de volgende tabellen; **CustomerID** bevat enkele waarden (in dit geval *CustX*) die niet voorkomen in de tabel *Klanten*. Daarom moet **Referentiële integriteit aannemen** *niet* worden ingesteld.
   
   ![](media/desktop-assume-referential-integrity/assume-referential-integrity_4.png)

## <a name="setting-assume-referential-integrity"></a>Referentiële integriteit aannemen instellen
Als u deze functie wilt inschakelen, schakelt u het selectievakje **Referentiële integriteit aannemen** in, zoals weergegeven in de volgende afbeelding.

![](media/desktop-assume-referential-integrity/assume-referential-integrity_1.png)

Als deze instelling is ingeschakeld, is de instelling gevalideerd tegen de gegevens om ervoor te zorgen dat er geen *Null-waarden* of niet-overeenkomende rijen voorkomen. *Echter*, in gevallen met een groot aantal waarden biedt de validatie geen garantie tegen problemen met de referentiële integriteit.

Bovendien vindt validatie plaats op het moment dat de relatie wordt bewerkt en worden eventuele latere gegevenswijzigingen dus *niet* doorgevoerd.

## <a name="what-happens-if-you-incorrectly-set-assume-referential-integrity"></a>Wat gebeurt er als u Referentiële integriteit aannemen per ongeluk instelt?
Als u **Referentiële integriteit aannemen** instelt als er sprake is van problemen met de referentiële integriteit in de gegevens, leidt dit niet tot fouten. Het kan wel tot inconsistenties in de gegevens leiden. Bijvoorbeeld in het geval van de relatie met de tabel **Opslagplaatsen** hierboven, kan het volgende optreden:

* Een visueel element met het totaal *Order Qty* toont in dat geval een waarde van 40
* Een visueel element met het totaal *Order Qty by Depot City* toont in dat geval een totaalwaarde van slechts *30* omdat Order ID 1 er niet in is opgenomen, waar **DepotID** *Null* is.

## <a name="next-steps"></a>Volgende stappen
Meer informatie over [DirectQuery](desktop-use-directquery.md)

Lees meer informatie over [relaties in Power BI](desktop-create-and-manage-relationships.md) (Engelstalig)

Meer informatie over [relatieweergave in Power BI Desktop](desktop-relationship-view.md) (Engelstalig).

