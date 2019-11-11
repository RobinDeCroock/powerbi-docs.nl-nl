---
title: Uitbreidbaarheid van connectors in Power BI
description: Uitbreidingsmogelijkheden voor connectors, kenmerken, beveiligingsinstellingen en gecertificeerde connectors
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: e493e4a41e7b357a23677c1c50f654dbee51e0ca
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878426"
---
# <a name="connector-extensibility-in-power-bi"></a>Uitbreidbaarheid van connectors in Power BI

In Power BI kunnen klanten en ontwikkelaars de gegevensbronnen uitbreiden waarmee ze op verschillende manieren verbinding maken. Ze gebruiken bestaande connectors en algemene gegevensbronnen (zoals ODBC, OData, OLEDB, Web, CSV, XML, JSON). Of ontwikkelaars maken gegevensextensies, ook wel **Aangepaste connectors** genoemd, en stellen deze in als **Gecertificeerde connectors**.

Op dit moment schakelt u **Aangepaste connectors** in met een menu waarmee u veilig het niveau kunt beheren van aangepaste code die u op uw systeem wilt laten uitvoeren. U kunt kiezen voor alle aangepaste connectors of alleen door Microsoft gecertificeerde en gedistribueerde connectors in het dialoogvenster **Gegevens ophalen**.

## <a name="custom-connectors"></a>Aangepaste connectors

**Aangepaste connectors** kunnen vele verschillende zaken omvatten, van kleine API's die van groot belang zijn voor uw bedrijf tot grote, branchespecifieke services waarvoor Microsoft nog geen connector beschikbaar heeft gesteld. Veel connectors worden gedistribueerd door de leverancier. Als u behoefte hebt aan een specifieke gegevensconnector, neemt u contact op met een leverancier.

Als u een **aangepaste connector** wilt gebruiken, plaatst u deze in de map *\[Documenten]\\Power BI Desktop\\Aangepaste connectors*. Pas de beveiligingsinstellingen aan zoals wordt beschreven in het volgende gedeelte.

U hoeft de beveiligingsinstellingen niet aan te passen als u **gecertificeerde connectors** wilt gebruiken.

## <a name="data-extension-security"></a>Beveiliging van gegevensextensies

Als u de beveiligingsinstellingen van een gegevensextensie wilt wijzigen, selecteert u in **Power BI Desktop** achtereenvolgens **Bestand > Opties en instellingen > Opties > Beveiliging**.

![Bepalen of u aangepaste connectors wilt kunnen laden met de beveiligingsopties voor gegevensextensies](media/desktop-connector-extensibility/data-extension-security-1.png)

Bij **Gegevensextensies** kunt u uit twee beveiligingsniveaus kiezen:

* (Aanbevolen) Toestaan dat alleen gecertificeerde extensies worden geladen
* (Niet aanbevolen) Toestaan dat een extensie wordt geladen zonder waarschuwing

Als u van plan bent om **aangepaste connectors**, zelf ontwikkelde connectors of connectors van derden te gebruiken, moet u **(Niet aanbevolen) Toestaan dat een extensie wordt geladen zonder waarschuwing** selecteren. Het wordt afgeraden deze beveiligingsinstelling te gebruiken, tenzij u uw aangepaste connectors absoluut vertrouwt. Omdat de code hierin referenties kan verwerken, waaronder de verzending via HTTP, en de privacyniveaus kan negeren.

Als er bij de beveiligingsinstelling **(Aanbevolen)** aangepaste connectors op uw systeem zijn, krijgt u de fout 'The following connector has not been certified, and we are unable to verify that is secure to use' (De volgende connector is niet gecertificeerd en we kunnen niet controleren of het veilig is deze te gebruiken), gevolgd door een lijst met connectors die niet veilig kunnen worden geladen.

![Er wordt een dialoogvenster weergegeven met de melding dat aangepaste connectors niet kunnen worden geladen vanwege de beveiligingsinstellingen, in dit geval TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Verwijder de niet-ondertekende connectors uit de map Aangepaste connectors om de fout op te lossen zonder de beveiliging te wijzigen.

Als u deze fout wilt verhelpen en u de connectors wilt gebruiken, moet u de beveiligingsinstellingen wijzigen in de instelling **(Niet aanbevolen) Toestaan dat een extensie wordt geladen zonder waarschuwing** zoals eerder is beschreven. Start **Power BI Desktop** vervolgens opnieuw.

## <a name="certified-connectors"></a>Gecertificeerde connectors

Een beperkte subset gegevensextensies wordt als **Gecertificeerd** beschouwd. Krijg toegang tot de gecertificeerde connectors in het dialoogvenster **Gegevens ophalen**. De externe ontwikkelaar die de connector heeft gemaakt, is echter verantwoordelijk voor het onderhoud en de ondersteuning van de connector. Microsoft distribueert deze connectors wel, maar kan niet verantwoordelijk worden gehouden voor de prestaties of de functionaliteit op de lange termijn.

Als u een aangepaste connector wilt laten certificeren, laat u uw leverancier contact opnemen met dataconnectors@microsoft.com.
