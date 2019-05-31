---
title: Performance Analyzer gebruiken om te controleren van element rapportprestaties in Power BI Desktop
description: Ontdek hoe visuele elementen en rapportelementen worden uitgevoerd in termen van Resourcegebruik en reactiesnelheid
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854408"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Performance Analyzer gebruiken om te onderzoeken rapportprestaties-element

In **Power BI Desktop** vindt u uit hoe elk van de rapportelementen, zoals visuele elementen en DAX-formules worden uitgevoerd. Met behulp van de **Performance Analyzer**, u kunt zien en record geregistreerd die meten hoe elk van de rapportelementen worden uitgevoerd als gebruikers mee werken en welke aspecten van de prestaties zijn de meeste (of minimale) resource-intensief.

![Prestatie-analyse](media/desktop-performance-analyzer/performance-analyzer-01.png)

Performance Analyzer inspecteert en geeft de tijdsduur die nodig is voor het bijwerken of vernieuwen van alle visuele elementen die gebruikersinteracties initiëren, en de gegevens worden weergegeven, zodat u kunt weergeven, inzoomen, of de resultaten exporteren. Performance Analyzer kunt u visuele elementen die de prestaties van uw rapporten van invloed zijn op identificeren en de reden voor de impact te identificeren.

## <a name="displaying-the-performance-analyzer-pane"></a>Het deelvenster Performance Analyzer weergeven

In **Power BI Desktop** selecteert u de **weergave** lint. In de **weergeven** gebied van de **weergave** lint kunt u het selectievakje in naast **Performance Analyzer** om het deelvenster Performance Analyzer weer te geven.

![Performance analyzer in het lint selecteren](media/desktop-performance-analyzer/performance-analyzer-02.png)

Nadat u hebt geselecteerd, wordt de Prestatie-analyse in een eigen deelvenster aan de rechterkant van het rapportcanvas weergegeven.

## <a name="using-performance-analyzer"></a>Met behulp van prestatie-analyse

Prestatiemeters analyzer de verwerkingstijd (met inbegrip van de tijd voor het maken of bijwerken van een visueel element) nodig voor het bijwerken van rapportelementen gestart als gevolg van interactie met de gebruiker die resulteert in een query uit te voeren. Bijvoorbeeld: een slicer passen heeft de slicer visual moet worden gewijzigd, een query moet worden verzonden naar het gegevensmodel, en de betreffende visuele elementen die moeten worden bijgewerkt als gevolg van de nieuwe instellingen. 

Als u wilt Performance Analyzer beginnen met opnemen, selecteert u gewoon **opname starten**

![Opname starten](media/desktop-performance-analyzer/performance-analyzer-03.png)

Acties die u in het rapport uitvoert worden weergegeven en vastgelegd in het deelvenster Performance Analyzer in de volgorde die het visuele element zijn geladen door Power BI. Bijvoorbeeld, wellicht hebt u een rapport die gebruikers hebben laten weten dat het lang duurt om te vernieuwen. Of bepaalde visuele elementen in een rapport erg lang duren om weer te geven wanneer een schuifregelaar wordt gecorrigeerd. Prestatieanalyse ziet u welke visual u het overmatig is en welke aspecten van het visuele element identificeert de langste duur voor het verwerken van duurt. 

Nadat u de opname, start de **opname starten** knop is uitgeschakeld out (inactief, omdat u al met het vastleggen van gegevens begonnen hebt) en de **stoppen** knop actief is. 

Prestatieanalyse verzameld en weergegeven van de prestatiegegevens van de meting in realtime. Dus telkens wanneer u klikt op een visueel element, verplaatsen van een slicer of communiceren op een andere manier weergegeven Performance Analyzer de prestatieresultaten onmiddellijk in het deelvenster.

Als het deelvenster meer informatie bevat, dan kunnen worden weergegeven, is een schuifbalk wordt weergegeven om te navigeren naar aanvullende informatie.

Elke interactie is een id in de sectie in het deelvenster met een beschrijving van de actie die de logboekvermeldingen gestart. In de volgende afbeelding is de interactie dat de gebruikers een slicer gewijzigd.

![Op basis van het type interactie secties](media/desktop-performance-analyzer/performance-analyzer-04.png)

De logboekgegevens van elk visuele element bevat de tijd besteed (duur) voor het voltooien van de volgende categorieën van taken:

* **DAX-query** -als een DAX-query vereist is, dit is de tijd tussen het visuele element de query wordt verzonden, en voor Analysis Services om de resultaten te retourneren.
* **Visuele weergave** -tijd die nodig is voor het visuele element op het scherm, met inbegrip van de tijd die nodig is om op te halen van alle webafbeeldingen en geocodering tekenen. 
* **Andere** -tijd die nodig is door het visuele element voor het voorbereiden van query's, wachten op andere visuele elementen om uit te voeren of andere verwerking op de achtergrond uitvoeren.

![elementen van logboekgegevens](media/desktop-performance-analyzer/performance-analyzer-06.png)

Nadat u aan de slag met elementen van het rapport dat u wilt meten met Performance Analyzer kunt hebt, selecteert u de **stoppen** knop. De informatie over de prestaties in het deelvenster blijft nadat u hebt geselecteerd **stoppen** voor u om te analyseren.

Selecteer om te wissen van de informatie in het deelvenster Performance Analyzer, **wissen**. Alle gegevens worden gewist en wordt niet opgeslagen wanneer u selecteert **wissen**. Zie de volgende sectie voor informatie over het opslaan van gegevens in Logboeken. 

## <a name="refreshing-visuals"></a>Vernieuwen van visuele elementen

U kunt selecteren **vernieuwen van visuele elementen** in het deelvenster Performance Analyzer voor alle visuele elementen op de huidige pagina van het rapport vernieuwen, en zodoende Performance Analyzer informatie verzamelen over alle dergelijke visuele elementen.

U kunt ook afzonderlijke visuele elementen vernieuwen. Wanneer Performance Analyzer opneemt, kunt u selecteren **vernieuwen van deze visual** gevonden in de rechterbovenhoek van elk visuele element, vernieuwen van deze visual en de informatie over de prestaties vast te leggen.

![vernieuwen van een afzonderlijk visueel element](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Opslaan van prestatiegegevens voor

U kunt de informatie die Performance Analyzer maakt over een rapport opslaan door het selecteren van de **exporteren** knop. Selecteren **exporteren** maakt u een .json-bestand met de informatie in het deelvenster Performance Analyzer. 

![Sla het logboekbestand voor prestaties analyzer](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Volgende stappen
Lees de volgende artikelen voor meer informatie over **Power BI Desktop** en hoe u aan de slag kunt.

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Query Overview with Power BI Desktop](desktop-query-overview.md) (Queryoverzicht met Power BI Desktop)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Connect to Data in Power BI Desktop](desktop-connect-to-data.md) (Verbinding maken met gegevens in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Common Query Tasks in Power BI Desktop](desktop-common-query-tasks.md) (Algemene querytaken in Power BI Desktop)   

