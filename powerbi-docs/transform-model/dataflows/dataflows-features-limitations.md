---
title: Gegevensstroomlimieten, beperkingen en ondersteunde connectors en functies
description: Overzicht van alle mogelijkheden van gegevensstromen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 89de77e65d8eb675d9e80c3b2497f39af7c32d33
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396582"
---
# <a name="dataflows-limitations-and-considerations"></a>Beperkingen en overwegingen van gegevensstromen

Er zijn enkele gegevensstroomlimieten voor het ontwerpen, vernieuwen en capaciteitsbeheer waarmee gebruikers rekening moeten houden, zoals beschreven in de volgende secties.

## <a name="dataflow-authoring"></a>Ontwerpen van gegevensstromen

Bij het ontwerpen van gegevensstromen moeten gebruikers rekening houden met de volgende zaken:

* Ontwerpen in gegevensstromen vindt plaats in de omgeving Power Query Online (PQO); zie de beperkingen die worden beschreven in [Power Query-limieten](/power-query/power-query-online-limits).
Omdat het ontwerpen van gegevensstromen plaatsvindt in de PQO-omgeving (Power Query Online), hebben de updates die worden uitgevoerd op de werkbelastingconfiguraties van gegevensstromen alleen invloed op vernieuwingen en heeft dit geen invloed op de ontwerpervaring

* Gegevensstromen kunnen alleen worden gewijzigd door hun eigenaren

* Gegevensstromen zijn niet beschikbaar in *Mijn werkruimte*

* Gegevensstromen waarvoor gateway-gegevensbronnen worden gebruikt, bieden geen ondersteuning voor meerdere referenties voor dezelfde gegevensbron

* Er is een gateway vereist om de Web.Page-connector te gebruiken

## <a name="api-considerations"></a>Overwegingen voor API's

Meer informatie over ondersteunde REST API's van gegevensstromen vindt u in de [REST API-naslaginformatie](/rest/api/power-bi/dataflows). Hierna volgen enkele aandachtspunten waarmee u rekening moet houden:

* Door een gegevensstroom te exporteren en importeren krijgt die gegevensstroom een nieuwe id

* Door het importeren van gegevensstromen die gekoppelde entiteiten bevatten, worden de bestaande verwijzingen in de gegevensstroom niet gecorrigeerd (deze query's moeten handmatig worden gecorrigeerd voordat de gegevensstroom wordt geïmporteerd)

* Gegevensstromen kunnen worden overschreven met de parameter *CreateOrOverwrite* als ze in eerste instantie zijn gemaakt met behulp van de API voor importeren

## <a name="dataflows-in-shared"></a>Gegevensstromen in Gedeeld

Er gelden beperkingen voor gegevensstromen in gedeelde capaciteiten:

* Bij het vernieuwen van gegevensstromen zijn time-outs in Gedeeld 2 uur per entiteit en 3 uur per gegevensstroom
* Gekoppelde entiteiten kunnen niet worden gemaakt in gedeelde gegevensstromen, hoewel ze in de gegevensstroom kunnen bestaan zolang de eigenschap *Load enabled* voor de query is uitgeschakeld
* Berekende entiteiten kunnen niet worden gemaakt in gedeelde gegevensstromen
* AutoML en Cognitive Services zijn niet beschikbaar in gedeelde gegevensstromen
* Incrementeel vernieuwen werkt niet in gedeelde gegevensstromen

## <a name="dataflows-in-premium"></a>Gegevensstromen in Premium

Gegevensstromen die in Premium bestaan, hebben de volgende beperkingen en overwegingen.

**Overwegingen met betrekking tot vernieuwingen en gegevens:**

* Bij het vernieuwen van gegevensstromen, duren time-outs 24 uur (geen onderscheid voor entiteiten en/of gegevensstromen)

* Als u een gegevensstroom wijzigt van een incrementeel vernieuwingsbeleid naar een normale vernieuwing, of andersom, worden alle gegevens verwijderd

* Als u het schema van een gegevensstroom wijzigt, worden alle gegevens verwijderd

**Gekoppelde en berekende entiteiten:**

* Gekoppelde entiteiten kunnen tot een diepte van 32 verwijzingen omlaag gaan

* Cyclische afhankelijkheden van gekoppelde entiteiten zijn niet toegestaan

* Een gekoppelde entiteit kan niet worden samengevoegd met een normale entiteit waarvoor de gegevens worden opgehaald uit een on-premises gegevensbron

* Wanneer een query (bijvoorbeeld query *A* ) wordt gebruikt voor de berekening van een andere query (query *B* ) in gegevensstromen, wordt query *B* een berekende entiteit. Berekende entiteiten kunnen niet verwijzen naar on-premises bronnen.


**Berekeningsengine:**

* Bij het gebruik van de berekeningsengine is er sprake van een toename van 10% tot 20% van de initiële tijd voor gegevensopname.

  1. Dit wordt alleen toegepast op de eerste gegevensstroom die zich op de berekeningsengine bevindt en gegevens leest uit de gegevensbron
  2. Op de volgende gegevensstromen die eenmaal gebruikmaken van de bron, wordt niet dezelfde vermindering toegepast

* Alleen bepaalde bewerkingen maken gebruik van de berekeningsengine en alleen wanneer ze worden gebruikt via een gekoppelde entiteit of als een berekende entiteit. Een volledige lijst met bewerkingen is te vinden in [deze blogpost](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html).


**Capaciteitsbeheer:**

* De Premium Power BI-capaciteiten hebben standaard een interne resourcebeheerder die de werkbelasting op verschillende manieren beperkt wanneer de capaciteit weinig geheugen heeft.

  1. In het geval van gegevensstromen vermindert deze beperkingsdruk het aantal beschikbare M-containers
  2. Het geheugen voor gegevensstromen kan worden ingesteld op 100%, met een geschikte container voor uw gegevensgroottes; de werkbelasting beheert dan het aantal containers op de juiste manier

* Het geschatte aantal containers kan worden gevonden door het totale geheugen dat aan de werkbelasting is toegewezen, te delen door de hoeveelheid geheugen die aan een container is toegewezen

## <a name="dataflow-usage-in-datasets"></a>Gebruik van gegevensstroom in gegevenssets

* Wanneer u een gegevensset maakt in Power BI Desktop en deze vervolgens publiceert naar de Power BI-service, moet u ervoor zorgen dat de referenties die in Power BI Desktop voor de gegevensbron Gegevensstroom worden gebruikt, dezelfde referenties hebben wanneer de gegevensset wordt gepubliceerd naar de service.
  1. Wanneer u er niet voor zorgt dat deze referenties hetzelfde zijn, resulteert dat in een fout *Sleutel niet gevonden* bij het vernieuwen van de gegevensset

## <a name="next-steps"></a>Volgende stappen
De volgende artikelen bieden meer informatie over gegevensstromen en Power BI:

* [Inleiding tot gegevensstromen en selfservice voor gegevensvoorbereiding](dataflows-introduction-self-service.md)
* [Een gegevensstroom maken](dataflows-create.md)
* [Een gegevensstroom configureren en gebruiken](dataflows-configure-consume.md)
* [Gegevensstroomopslag configureren voor gebruik van Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Premium-functies van gegevensstromen](dataflows-premium-features.md)
* [AI met gegevensstromen](dataflows-machine-learning-integration.md)