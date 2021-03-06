---
title: Verbinding maken met gegevens die zijn gemaakt met Power Platform-gegevensstromen in Power BI Desktop
description: Eenvoudig verbinding maken met gegevens in Power BI Desktop en deze gebruiken
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 5d9f477c8b058dbe9a71eec1307b4a32863307a1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392951"
---
# <a name="connect-to-data-created-by-power-platform-dataflows-in-power-bi-desktop"></a>Verbinding maken met gegevens die zijn gemaakt met Power Platform-gegevensstromen in Power BI Desktop
In **Power BI Desktop** kunt u verbinding maken met gegevens die zijn gemaakt door **Power Platform-gegevensstromen**, zoals met elke andere gegevensbron in Power BI Desktop.

![Verbinding maken met gegevensstromen](media/desktop-connect-dataflows/connect-dataflows_01.png)

Met de connector voor **Power Platform-gegevensstromen** kunt u verbinding maken met de entiteiten die zijn gemaakt met gegevensstromen in de Power BI-service. 

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

U moet een recente versie van **Power BI Desktop** uitvoeren om de **connector voor Power Platform-gegevensstromen** te gebruiken. U kunt altijd [Power BI Desktop downloaden](../fundamentals/desktop-get-the-desktop.md) en op uw computer installeren om ervoor te zorgen dat u de meest recente versie hebt.  

> [!NOTE]
> Voor de vorige versie van de connector voor Power Platform-gegevensstromen moest u een MEZ-bestand downloaden en opslaan in een map. Huidige versies van **Power BI Desktop** omvatten de connector voor Power Platform-gegevensstromen. Hierdoor is dit bestand niet meer vereist en kan het conflicten veroorzaken met de meegeleverde versie van de connector. Als u dit MEZ-bestand handmatig in een map hebt geplaatst, *moet* u het gedownloade MEZ-bestand verwijderen uit de map **Documenten > Power BI Desktop > Aangepaste connectors** om conflicten te voorkomen. 

## <a name="desktop-performance"></a>Desktopprestaties
**Power BI Desktop** wordt lokaal uitgevoerd op de computer waarop het is geïnstalleerd. De opnameprestaties van gegevensstromen worden bepaald door een aantal factoren. Deze factoren omvatten de grootte van de gegevens, de CPU en RAM van de computer, netwerkbandbreedte, afstand van het datacenter, en andere factoren.

U kunt de prestaties van gegevensopname voor gegevensstromen verbeteren. Als de opgenomen gegevens bijvoorbeeld te groot zijn om met **Power BI Desktop** te worden beheerd op de computer, kunt u gekoppelde en berekende entiteiten in gegevensstromen gebruiken om de gegevens (binnen gegevensstromen) samen te voegen en alleen de vooraf voorbereide en samengevoegde gegevens opnemen. 

Op deze manier wordt de verwerking van grote aantallen gegevens online uitgevoerd in gegevensstromen, in plaats van lokaal in het actieve exemplaar van **Power BI Desktop**. Met deze aanpak kunnen in Power BI Desktop kleinere aantallen gegevens worden opgenomen, en blijft het werken met gegevensstromen responsief en snel.

## <a name="additional-considerations"></a>Aanvullende overwegingen

De meeste gegevensstromen bevinden zich in de Power BI-service-tenant. Gebruikers van **Power BI Desktop** hebben echter geen toegang tot gegevensstromen die zijn opgeslagen in het Azure Data Lake Storage Gen2-account, tenzij ze eigenaar zijn van de gegevensstroom of ze expliciet geautoriseerd zijn voor de CDM-map van de gegevensstroom. Kijk eens naar de volgende situatie:

1.  Anna maakt een nieuwe werkruimte en configureert deze zodanig dat er gegevensstromen kunnen worden opgeslagen in de data lake van de organisatie.
2.  Ben, die ook lid is van de werkruimte die Anna heeft gemaakt, wil Power BI Desktop en de gegevensstroomconnector gebruiken om gegevens op te halen uit de gegevensstroom die Anna heeft gemaakt.
3.  Ben krijgt een foutmelding omdat hij niet als geautoriseerde gebruiker is toegevoegd aan de CDM-map van de gegevensstroom in de data lake.

Om dit probleem op te lossen, moeten aan Ben leesmachtigingen voor de CDM-map en de bijbehorende bestanden worden verleend. Meer informatie over het verlenen van toegang tot de CDM-map vindt u in [Een gegevensstroom configureren en gebruiken](dataflows/dataflows-configure-consume.md).




## <a name="next-steps"></a>Volgende stappen
U kunt allerlei interessante dingen doen met gegevensstromen. Bekijk de volgende resources voor meer informatie:

* [Inleiding tot gegevensstromen en selfservice voor gegevensvoorbereiding](dataflows/dataflows-introduction-self-service.md)
* [Een gegevensstroom maken](dataflows/dataflows-create.md)
* [Een gegevensstroom configureren en gebruiken](dataflows/dataflows-configure-consume.md)
* [Gegevensstroomopslag configureren voor gebruik van Azure Data Lake Gen 2](dataflows/dataflows-azure-data-lake-storage-integration.md)
* [Premium-functies van gegevensstromen](dataflows/dataflows-premium-features.md)
* [AI met gegevensstromen](dataflows/dataflows-machine-learning-integration.md)


Er zijn ook artikelen over **Power BI Desktop** die u misschien nuttig vindt:

* [Data Sources in Power BI Desktop](../connect-data/desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Enter data directly into Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)