---
title: Rapportgegevens in Power BI Report Builder
description: Uw eerste stap bij het ontwerpen van een rapport in de gepagineerde Report Builder voor Power BI is om gegevensbronnen en gegevenssets te maken die de onderliggende rapportgegevens representeren.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: cbcb710a806c400ea33ac4d605614b5325277d07
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860417"
---
# <a name="report-data-in-power-bi-report-builder"></a>Rapportgegevens in Power BI Report Builder

Rapportgegevens kunnen afkomstig zijn uit meerdere gegevensbronnen in uw organisatie. Uw eerste stap bij het ontwerpen van een Power BI Report Builder-rapport is om gegevensbronnen en gegevenssets te maken die de onderliggende rapportgegevens representeren. Elke gegevensbron bevat informatie over de gegevensverbinding. Elke gegevensset bevat een queryopdracht waarmee de set velden wordt gedefinieerd die moet worden gebruikt als gegevens uit een gegevensbron. Als u gegevens uit elke gegevensset wilt visualiseren, voegt u een gegevensgebied, zoals een tabel, matrix, grafiek of kaart, toe. Bij verwerking van het rapport worden de query's uitgevoerd op de gegevensbron en wordt elk gegevensgebied zo nodig uitgebreid om de queryresultaten voor de gegevensset weer te geven.  

Informatie over [het maken van een ingesloten gegevensbron voor gepagineerde rapporten in Power BI Report Builder](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Voorwaarden  
  
- **Gegevensverbinding.** Ook wel bekend als een *gegevensbron*. Een gegevensverbinding bevat een naam en verbindingseigenschappen die afhankelijk zijn van het verbindingstype. Standaard bevat een gegevensverbinding geen referenties. Een gegevensverbinding geeft niet aan welke gegevens er uit de externe gegevensbron moeten worden opgehaald. Daarvoor moet u een query opgeven bij het maken van een gegevensset.  
  
- **Verbindingsreeks.** Een verbindingsreeks is een tekenreeksversie van de verbindingseigenschappen die nodig zijn om verbinding te maken met een gegevensbron. Verbindingseigenschappen verschillen op basis van het type gegevensverbinding.  
  
- **Ingesloten gegevensbron.** Ook wel bekend als een *rapportspecifieke gegevensbron*. Een gegevensbron die is gedefinieerd in een rapport en alleen door dat rapport wordt gebruikt.  
  
- **Referenties.** Referenties zijn de verificatiegegevens die moeten worden opgegeven om toegang te krijgen tot externe gegevens.  
  
##  <a name="BkMk_ReportDataTips"></a> Tips voor het opgeven van rapportgegevens

 Gebruik de volgende informatie om een strategie voor uw rapportgegevens te ontwerpen.  
  
- **Gegevens filteren** Rapportgegevens kunnen worden gefilterd in de query of in het rapport. U kunt gegevenssets en queryvariabelen gebruiken om trapsgewijze parameters te maken en gebruikers de mogelijkheid bieden om keuzen uit duizenden selecties te beperken tot een beter beheersbaar aantal. U kunt gegevens in een tabel of grafiek filteren op basis van parameterwaarden of andere waarden die u opgeeft.  
  
- **Parameters** Queryopdrachten voor gegevenssets die queryvariabelen bevatten waarmee automatisch overeenkomende rapportparameters worden gemaakt. U kunt ook handmatig parameters maken. Wanneer u een rapport bekijkt, worden de parameters weergegeven op de werkbalk van het rapport. Gebruikers kunnen waarden selecteren om rapportgegevens of de rapportweergave te selecteren. Als u rapportgegevens wilt aanpassen voor specifieke doelgroepen, kunt u sets rapportparameters maken met andere standaardwaarden die aan dezelfde rapportdefinitie zijn gekoppeld of gebruikmaken van het ingebouwde veld **UserID**. 
  
- **Gegevens groeperen en aggregeren** Rapportgegevens kunnen worden gegroepeerd en geaggregeerd in de query of in het rapport. Als u de waarden in de query aggregeert, kunt u waarden blijven combineren in het rapport, binnen zinvolle beperkingen.  
  
- **Gegevens sorteren** Rapportgegevens kunnen worden gesorteerd in de query of in het rapport. U kunt ook een interactieve sorteerknop toevoegen aan tabellen, waarmee de gebruiker de sorteervolgorde kan bepalen.  
  
- **Gegevens op basis van expressies** Omdat de meeste rapporteigenschappen kunnen worden gebaseerd op expressies en omdat expressies verwijzingen naar velden van de gegevensset en rapportparameters kunnen bevatten, kunt u krachtige expressies schrijven om rapportgegevens en de weergave te beheren. U kunt gebruikers de mogelijkheid geven om te bepalen welke gegevens ze zien door parameters op te geven.  
  
- **Gegevens uit een gegevensset weergegeven** Gegevens uit een gegevensset worden doorgaans op een of meer gegevensgebieden weergegeven, bijvoorbeeld in een tabel en in een grafiek.  
  
- **Gegevens uit meerdere gegevenssets** U kunt in een gegevensgebied op basis van één gegevensset expressies schrijven waarmee waarden of aggregaties worden opgezocht in andere gegevenssets. U kunt in een tabel op basis van één gegevensset subrapporten opnemen om gegevens uit een andere gegevensbron weer te geven.  
  
 Gebruik de volgende lijst bij het definiëren van gegevensbronnen voor een rapport.  
  
- Krijg inzicht in de architectuur van de softwaregegevenslaag voor uw organisatie en de mogelijke problemen die voortvloeien uit de gegevenstypen. Krijg inzicht in hoe gegevensextensies en extensies voor gegevensverwerking queryresultaten kunnen beïnvloeden. Gegevenstypen verschillen binnen gegevensbronnen, gegevensproviders en de gegevenstypen die zijn opgeslagen in het rapportdefinitiebestand (.rdl).  
  
- Gegevensbronnen en gegevenssets worden gemaakt in een rapport en gepubliceerd in de Power BI-service. Na publicatie ervan kunt u referenties configureren, rechtstreeks in de Power BI-service of in uw Enterprise-gateway. 

## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
