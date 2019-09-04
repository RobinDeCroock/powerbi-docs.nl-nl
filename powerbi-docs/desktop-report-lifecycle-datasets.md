---
title: Verbinding maken met gegevenssets in de Power BI-service vanuit Power BI Desktop
description: Een algemene gegevensset gebruiken voor meerdere Power BI Desktop-rapporten in meerdere werkruimten en de levenscyclus van uw rapport beheren
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 5477d7772681f0dd5ac4426335521f6ab1a7844e
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160352"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Verbinding maken met gegevenssets in de Power BI-service vanuit Power BI Desktop
U kunt een live verbinding maken met een gedeelde gegevensset in de Power BI-service en veel verschillende rapporten maken op basis van dezelfde gegevensset. Dit betekent dat u in Power BI Desktop een perfect gegevensmodel kunt maken en het model vervolgens kunt publiceren naar de Power BI-service. Vervolgens kunnen u en anderen meerdere verschillende rapporten (in afzonderlijke .pbix-bestanden) op basis van hetzelfde algemene gegevensmodel maken en deze opslaan in verschillende werkruimten. Deze functie heet **Liveverbinding met Power BI-service**.

![Gegevens ophalen uit de Power BI-service](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

Deze functie heeft allerlei voordelen, waaronder best practices, die in dit artikel worden besproken. Er zijn ook enkele overwegingen en beperkingen, dus lees deze vooral door; ze staan aan het eind van dit artikel.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Een liveverbinding met de Power BI-service gebruiken voor het beheren van de levenscyclus van rapporten
Eén uitdaging waar de populariteit van Power BI toe leidt is de proliferatie van rapporten, dashboards en de onderliggende gegevensmodellen ervan. Het is gemakkelijk om overtuigende rapporten te maken in **Power BI Desktop**, die rapporten te delen ([publiceren](desktop-upload-desktop-files.md)) in de **Power BI-service**, en geweldige dashboards te maken op basis van die gegevenssets. Omdat zoveel mensen dit deden, vaak met (bijna) dezelfde gegevenssets, werd het een uitdaging om te weten welk rapport op welke gegevensset was gebaseerd, en hoe recent elke gegevensset was. De **liveverbinding met de Power BI-service** pakt deze uitdaging op en maakt het delen, maken en uitbreiden van rapporten en dashboards op basis van gemeenschappelijke gegevenssets gemakkelijker en consistent.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Maak een gegevensset die iedereen kan gebruiken, en deel deze
Stel dat Anna (een bedrijfsanalist) in uw team zit, en heel goed is in het maken van gegevensmodellen (vaak gegevenssets genoemd). Dankzij haar expertise kan Anna een gegevensset en rapport maken, en dat rapport vervolgens delen in de **Power BI-service**.

![Publiceren naar de Power BI-service](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Iedereen is dol op Anna's rapport en gegevensset; en dat is waar het probleem ontstaat: iedereen in Anna's team zou proberen *een eigen versie* van die gegevensset te maken en zijn of haar eigen rapporten met het team te delen. Opeens zou er een groot aantal rapporten (van verschillende gegevenssets) in de werkruimte van uw team in de **Power BI-service** zijn. Welk ervan was het meest recent? Waren de gegevenssets hetzelfde, of alleen bijna hetzelfde? Wat waren de verschillen? Met de functie **Liveverbinding met Power BI-service** kan dat allemaal ten goede veranderen. In de volgende sectie ziet u hoe anderen de gepubliceerde gegevensset van Anna voor hun eigen rapporten in hun eigen werkruimten kunnen gebruiken, en hoe iedereen dezelfde solide, goedgekeurde, gepubliceerde gegevensset kan gebruiken om eigen unieke rapporten samen te stellen.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Verbinding maken met een gegevensset van Power BI-service via een liveverbinding
Anna maakt een rapport (en maakt de gegevensset waarop het is gebaseerd), publiceert het vervolgens naar de **Power BI-service** waarop het wordt weergegeven in de werkruimte van haar team in de Power BI-service. Als Anna het rapport opslaat in een *werkruimte van de nieuwe ervaring*, kan Anna de machtiging Samenstellen instellen zodat het rapport door iedereen in en buiten hun werkruimte kan worden bekeken en gebruikt.

Zie [app-werkruimten](service-new-workspaces.md) voor meer informatie over de werkruimten van de nieuwe ervaring.

Andere leden in en buiten Anna's werkruimte kunnen nu een liveverbinding maken met het gedeelde gegevensmodel van Anna (met behulp van de functie **Liveverbinding met Power BI-service**) en eigen unieke rapporten maken op basis van *hun oorspronkelijke gegevensset* in *hun eigen werkruimten van de nieuwe ervaring*.

In de volgende afbeelding ziet u hoe Anna één **Power BI Desktop**-rapport maakt en het publiceert (met inbegrip van het gegevensmodel ervan) naar de **Power BI-service**. Vervolgens kunnen anderen verbinding maken met Anna's gegevensmodel via de **liveverbinding met de Power BI-service** en hun eigen unieke rapporten in hun eigen werkruimten maken op basis van Anna's gegevensset.

![Meerdere rapporten op basis van dezelfde gegevensset](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Als u uw gegevensset opslaat in een [klassieke gedeelde werkruimte](service-create-workspaces.md), kunnen alleen leden van die werkruimte rapporten op basis van uw gegevensset maken. Als u een liveverbinding met de Power BI-service wilt maken, moet de gegevensset waarmee u verbinding wilt maken zich in een gedeelde werkruimte bevinden waarvan u lid bent.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Stapsgewijze aanwijzingen voor het gebruik van de liveverbinding met de Power BI-service
Nu we weten hoe nuttig de **liveverbinding met de Power BI-service** is en hoe u deze kunt gebruiken als best-practicebenadering voor het beheren van de levenscyclus van rapporten, gaan we de stappen eens bekijken waarmee we van Anna's fantastisch rapport (en gegevensset) naar een gedeelde gegevensset gaan die haar teamgenoten met Power BI kunnen gebruiken.

### <a name="publish-a-power-bi-report-and-dataset"></a>Een Power BI-rapport en gegevensset publiceren
De eerste stap bij het beheren van de levenscyclus van een rapport met behulp van een **liveverbinding met de Power BI-service** is een rapport (met gegevensset) te hebben dat teamleden willen gebruiken. Anna moet het rapport dus eerst **publiceren** vanuit **Power BI Desktop**. Dit wordt gedaan door **Publiceren** te selecteren in het lint **Start** van Power BI Desktop.

![Een rapport publiceren](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Als Anna niet is aangemeld bij het Power BI-serviceaccount, wordt Anna in een pop-up gevraagd dit te doen.

![Aanmelden bij Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Van daaruit kan Anna de werkruimte kiezen waarnaar het rapport en de gegevensset worden gepubliceerd. Vergeet niet dat wanneer Anna het rapport opslaat in een werkruimte van de nieuwe ervaring, iedereen met de machtiging Samenstellen toegang tot die gegevensset heeft. De machtiging Samenstellen wordt na de publicatie ingesteld in de Power BI-service. Als werk wordt opgeslagen in een klassieke werkruimte, hebben alleen leden die toegang hebben tot de werkruimte waarin een rapport wordt gepubliceerd, toegang tot de gegevensset met behulp van een **liveverbinding met de Power BI-service**.

![Publiceren naar de Power BI-service](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Het publicatieproces begint, en **Power BI Desktop** laat de voortgang zien.

![Publiceren wordt uitgevoerd](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

Wanneer het klaar is, laat **Power BI Desktop** u zien dat het gelukt is, en geeft u enkele koppelingen naar het rapport zelf in de **Power BI-service** en een koppeling naar **Snelle inzichten** over het rapport.

![Publiceren geslaagd](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Nu u een rapport met een gegevensset in de Power BI-service hebt, kunt u het ook *naar een hoger niveau brengen* waarmee u de kwaliteit en betrouwbaarheid van het rapport bevestigt. U kunt zelfs aanvragen dat het wordt *gecertificeerd* door een centrale instantie in uw Power BI-tenant. In beide gevallen wordt uw gegevensset bovenaan de lijst weergegeven wanneer mensen op zoek zijn naar gegevenssets. Lees desgewenst meer over [het op een hoger niveau brengen van uw gegevensset](service-datasets-promote.md). 

De laatste stap is het instellen van de *machtiging Samenstellen* voor de gegevensset waarop het rapport is gebaseerd. Met de machtiging Samenstellen wordt bepaald wie uw gegevensset kan zien en gebruiken. U kunt deze in de werkruimte zelf instellen of wanneer u een app vanuit de werkruimte deelt. Meer informatie over het instellen van de [machtiging Samenstellen](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

Laten we nu eens kijken hoe andere teamgenoten die toegang hebben tot de werkruimte waar het rapport en de gegevensset zijn gepubliceerd, verbinding kunnen maken met de gegevensset en eigen rapporten maken.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Breng een liveverbinding met de Power BI-service tot stand
Als u verbinding wilt maken met het gepubliceerde rapport en een eigen rapport wilt maken op basis van de gepubliceerde gegevensset, selecteert u **Gegevens ophalen** in het lint **Start** van **Power BI Desktop**, selecteert u **Power BI** in het linkervenster en selecteert u vervolgens **Power BI-gegevenssets**.

Als u zich niet hebt aangemeld bij Power BI, wordt u gevraagd dit te doen. Nadat u bent aangemeld, krijgt u een venster te zien waarin wordt weergegeven van welke werkruimten u lid bent, en kunt u de werkruimte selecteren die de gegevensset bevat waarmee u een **liveverbinding met Power BI-service** tot stand wilt brengen.

De gegevenssets in de lijst zijn alle gedeelde gegevenssets waarvoor u de machtiging Samenstellen in elke werkruimte hebt. U kunt een specifieke gegevensset zoeken en de naam en de eigenaar van de gegevensset weergeven. Ook kunt u bekijken in welke werkruimte de gegevensset zich bevindt en wanneer deze voor het laatst is vernieuwd. U ziet ook de *goedgekeurde* gegevenssets (ofwel gecertificeerd of op een hoger niveau geplaatst) bovenaan de lijst. 

![Lijst met beschikbare gegevenssets](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

Wanneer u **Laden** selecteert in het venster, maakt u een liveverbinding met de geselecteerde gegevensset, wat betekent dat de gegevens die u ziet (de velden en hun waarden) in realtime in **Power BI Desktop** worden geladen.

![Velden van de gegevensset in het deelvenster Velden](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Nu kunt u (en kunnen anderen) aangepaste rapporten maken en delen, op basis van dezelfde gegevensset. Dit is een uitstekende manier om één deskundige persoon een goed ingedeelde gegevensset te laten maken (zoals Anna doet), en een groot aantal teamleden die gedeelde gegevensset te laten gebruiken om hun eigen rapporten te maken.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen
Wanneer u de **liveverbinding met de Power BI-service** gebruikt, zijn er enkele beperkingen en overwegingen waarmee u rekening moet houden.

* Alleen gebruikers met de machtiging Samenstellen voor een gegevensset kunnen verbinding maken met een gepubliceerde gegevensset met de **liveverbinding met de Power BI-service**. 
* Gebruikers van gratis versies zien alleen gegevenssets in Mijn werkruimte en in Premium-werkruimten.
* Aangezien dit een liveverbinding is, zijn de navigatie aan de linkerkant en modellering uitgeschakeld, vergelijkbaar met het gedrag bij een verbinding met **SQL Server Analysis Services**, en kunt u alleen verbinding maken met één gegevensset in elk rapport.
* Aangezien dit een liveverbinding is, worden RLS (beveiliging op rij- en rolniveau) en soortgelijke gedragingen afgedwongen, net als bij verbinding met **SQL Server Analysis Services**.
* Als de eigenaar het oorspronkelijke gedeelde .pbix-bestand wijzigt, worden de gegevensset en het rapport dat wordt gedeeld in de **Power BI-service** overschreven. Rapporten op basis van die gegevensset worden niet overschreven, maar eventuele wijzigingen in de gegevensset worden in het rapport doorgevoerd.
* Leden van een werkruimte kunnen het oorspronkelijk gedeelde rapport niet vervangen. Pogingen daartoe resulteren in een waarschuwing waarin u wordt gevraagd het bestand een andere naam te geven en het te publiceren.
* Als u de gedeelde gegevensset in de **Power BI-service** verwijdert, werken andere rapporten op basis van die gegevensset niet meer goed of worden de visuals van de gegevensset niet meer weergegeven.
* Voor inhoudspakketten moet u eerst een kopie van een inhoudspakket maken voordat u het gebruikt als basis voor het delen van een. pbix-rapport en gegevensset met de **Power BI service**.
* Nadat de inhoudspakketten van *Mijn organisatie* zijn gekopieerd,kunt u het rapport dat op de service is gemaakt en/of een rapport dat is gemaakt bij het kopiëren van een inhoudspakket met een liveverbinding niet meer vervangen. Pogingen daartoe resulteren in een waarschuwing waarin u wordt gevraagd het bestand een andere naam te geven en het te publiceren. In dit geval kunt u alleen gepubliceerde live gekoppelde rapporten vervangen.
* Wanneer u een gedeelde gegevensset in de **Power BI-service** verwijdert, heeft niemand meer toegang tot die gegevensset vanuit **Power BI Desktop**.
* Rapporten waarin een gegevensset op de Power BI-service wordt gedeeld, bieden geen ondersteuning voor geautomatiseerde implementaties met de REST-API van Power BI.

