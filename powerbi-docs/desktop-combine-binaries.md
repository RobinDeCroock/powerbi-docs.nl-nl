---
title: Bestanden (binaire) combineren in Power BI Desktop
description: Eenvoudig (binaire) bestandsgegevensbronnen combineren in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: f43bb105f7e17ce453e96c6eff875349efd45cb2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239631"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Bestanden (binaire) combineren in Power BI Desktop
Een krachtige aanpak voor het importeren van gegevens in **Power BI Desktop** bestaat uit het combineren van meerdere bestanden, die hetzelfde schema hebben, tot één logische tabel. Met de release van **Power BI Desktop** van november 2016 (en volgende releases) is deze aanpak nog eenvoudiger en uitgebreider gemaakt, zoals in dit artikel is beschreven.

Selecteer **Gegevens ophalen > Bestand > Map** om het proces van het combineren van bestanden vanuit dezelfde map te starten.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-files-binaries-behavior"></a>Gedrag van het vorige proces van het combineren van (binaire) bestanden
Vóór de release van **Power BI Desktop** van november 2016 werd deze functionaliteit **Binaire bestanden combineren** genoemd en kon u bepaalde bestandstypen combineren met de transformatie **Binaire bestanden combineren**. Dit had echter zijn beperkingen:

* De transformaties werden niet voor elk afzonderlijk bestand in overweging genomen voordat de bestanden tot één tabel werden gecombineerd. Daarom moesten bestanden vaak worden gecombineerd om vervolgens de *koptekstwaarden* eruit te filteren door rijen te filteren als onderdeel van het bewerkingsproces.
* De transformatie **Binaire bestanden combineren** werkte alleen voor *tekstbestanden* of *CSV-bestanden* en niet voor andere ondersteunde bestandsindelingen, zoals Excel-werkmappen, JSON-bestanden en andere.

Klanten vroegen om een meer intuïtieve benadering van de bewerking **Binaire bestanden combineren**. Daarom hebben we de transformatie uitgebreid en de nieuwe naam **Bestanden combineren** gegeven.

## <a name="current-combine-files-behavior"></a>Gedrag van het huidige proces van het combineren van bestanden
**Power BI Desktop** gaat nu efficiënter om met het **combineren van (binaire) bestanden**. Eerst selecteert u **Bestanden combineren** op het linttabblad **Start** in **Query-editor**, of in de kolom zelf.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

De transformatie **Bestanden combineren** werkt nu als volgt:

* De transformatie **Bestanden combineren** analyseert elk invoerbestand en bepaalt de juiste bestandsindeling, bijvoorbeeld *tekstbestand*, *Excel-werkmap* of *JSON-bestand*.
* Met de transformatie kunt u uit het eerste bestand een specifiek object selecteren, bijvoorbeeld om een *Excel-werkmap* te extraheren.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* Door **Bestanden combineren** worden vervolgens de volgende query's automatisch uitgevoerd:
  
  * Er wordt een voorbeeldquery gemaakt waarmee alle vereiste extractiestappen in één bestand worden uitgevoerd.
  * Er wordt een *functiequery* gemaakt waarmee de (binaire) bestandsinvoer in parameters wordt uitgedrukt voor de *voorbeeldquery*. De voorbeeldquery en de functiequery worden gekoppeld, zodat de wijzigingen aan de voorbeeldquery in de functiequery worden weerspiegeld.
  * De *functiequery* wordt toegepast op de oorspronkelijke query met binaire invoerbestanden (bijvoorbeeld de query *Map*). De functiequery wordt dus op elke rij toegepast voor binaire invoer. Vervolgens wordt de resulterende gegevensextractie als kolommen op het bovenste niveau uitgevouwen.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Dankzij het nieuwe gedrag van **Bestanden combineren** kunt u eenvoudig alle bestanden in een bepaalde map combineren, zolang ze hetzelfde bestandstype en dezelfde structuur hebben (zoals dezelfde kolommen).

Bovendien kunt u eenvoudig aanvullende transformaties of extractiestappen toepassen door de automatisch gemaakte *voorbeeldquery* te wijzigen, zonder dat u zich zorgen hoeft te maken over het wijzigen of maken van aanvullende stappen voor een *functiequery*. Wijzigingen aan de *voorbeeldquery* worden automatisch in de gekoppelde *functiequery* gegenereerd.

## <a name="next-steps"></a>Volgende stappen
Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende bronnen voor meer informatie over gegevensbronnen:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Connect to CSV files in Power BI Desktop](desktop-connect-csv.md) (Verbinding met CSV-bestanden maken in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   

