---
title: Uitbreidbaarheid van connectors in Power BI
description: Uitbreidingsmogelijkheden voor connectors, kenmerken, beveiligingsinstellingen en gecertificeerde connectors
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413003"
---
# <a name="connector-extensibility-in-power-bi"></a>Uitbreidbaarheid van connectors in Power BI

In Power BI, kunnen klanten en ontwikkelaars de gegevensbronnen waarmee ze verbinding op tal van manieren maken uitbreiden. Ze gebruiken bestaande connectors en algemene gegevensbronnen (zoals ODBC, OData-, Oledb, Web, CSV, XML, JSON). Ontwikkelaars maken gegevensextensies, aangeduid als **aangepaste Connectors**, en ze **gecertificeerde Connectors**.

Momenteel kunt u inschakelen **aangepaste Connectors** met behulp van een menu zien waarmee u veilig bepalen het niveau van aangepaste code die u wilt laten uitvoeren op uw systeem. U kunt alle aangepaste connectors of alleen verbindingslijnen gecertificeerd en gedistribueerd door Microsoft in de **gegevens ophalen** dialoog.

## <a name="custom-connectors"></a>Aangepaste connectors

**Aangepaste Connectors** een breed scala aan mogelijkheden kunt opnemen, variërend van kleine essentiële API's voor uw bedrijf, tot grote branche-specifieke services die door Microsoft een connector voor nog niet is vrijgegeven. Verschillende connectors die worden gedistribueerd door de leverancier. Als u behoefte hebt aan een specifieke connector hebt, neemt u contact op met een leverancier.

Gebruik een **aangepaste Connector**, plaatst deze in de  *\[documenten]\\Power BI Desktop\\aangepaste Connectors* map, en de beveiligingsinstellingen aanpassen zoals beschreven in de volgende sectie.

U hoeft de beveiligingsinstellingen niet aan te passen als u **gecertificeerde connectors** wilt gebruiken.

## <a name="data-extension-security"></a>Beveiliging van gegevensextensies

Voor het wijzigen van beveiligingsinstellingen voor uitbreiding van gegevens, in **Power BI Desktop** Selecteer **bestand > Opties en instellingen > Opties > beveiliging**.

![Bepalen of u wilt laden, aangepaste connectoren met extensie-gegevensbeveiliging-opties](media/desktop-connector-extensibility/data-extension-security-1.png)

Bij **Gegevensextensies** kunt u uit twee beveiligingsniveaus kiezen:

* (Aanbevolen) Toestaan dat alleen gecertificeerde extensies worden geladen
* (Niet aanbevolen) Toestaan dat een extensie wordt geladen zonder waarschuwing

Als u van plan over het gebruik van bent **aangepaste Connectors** of connectors die u of een derde partij hebben ontwikkeld, moet u **"(Not Recommended) toestaan elke extensie laden zonder waarschuwing"** . Deze beveiligingsinstelling wordt niet aanbevolen, tenzij u uw aangepaste Connectors, volledig vertrouwt. Omdat de code er referenties, zoals ze worden verzonden via HTTP, verwerkt en privacyniveaus negeert.

Op de **'(aanbevolen)'** beveiliging instelt, als er aangepaste connectors op uw systeem, er een fout weergegeven die worden beschreven de connectors op die kunnen niet worden geladen vanwege de beveiliging.

![Een dialoogvenster Beschrijving van aangepaste Connectors die niet wegens de beveiligingsinstellingen in dit geval TripPin laden](media/desktop-connector-extensibility/data-extension-security-2.png)

Los de fout en het gebruik van deze connectors, wijzigt u de beveiligingsinstellingen op de **"(Not Recommended) toestaan elke extensie laden zonder waarschuwing"** instellen, zoals eerder beschreven. Start **Power BI Desktop**.

## <a name="certified-connectors"></a>Gecertificeerde connectors

Een beperkte subset van gegevensextensies wordt beschouwd als **gecertificeerd**. Toegang tot de gecertificeerde connectors in de **gegevens ophalen** dialoog. Maar de ontwikkelaars van derden die het maken van de connector is verantwoordelijk voor het onderhoud en ondersteuning. Terwijl Microsoft de connectors distribueert, is het niet verantwoordelijk voor hun prestaties of een permanente functie.

Als u een aangepaste connector wilt laten certificeren, laat u uw leverancier contact opnemen met dataconnectors@microsoft.com.
