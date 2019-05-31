---
title: Cross-rapport drillthrough gebruiken in Power BI Desktop
description: Meer informatie over het in detail analyseren vanuit een rapport naar de andere in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375199"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Cross-rapport drillthrough gebruiken in Power BI Desktop

Met de functie voor cross-rapport drillthrough in Power BI Desktop, kunt u contextueel gaan van een rapport naar een ander rapport. Dit geldt zolang de rapporten binnen dezelfde werkruimte of -app in de Microsoft Power BI-service zijn. Cross-rapport drillthrough gebruiken om twee of meer rapporten die met inhoud gerelateerde verbinding te maken en om door te geven van de filtercontext samen met de cross-verbinding. In dit artikel leert u hoe u een drillthrough cross-rapport voor Power BI-rapporten kunt instellen en wat gebruikers ondervinden wanneer ze de drillthrough cross-rapport gebruiken om zelf.

![Schermafbeelding van de Power BI Desktop drillthrough-optie](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

De volgende definities zijn belangrijk om te begrijpen, voordat we beginnen instellen en gebruiken van cross-rapport drillthrough:

* **Bronvisual:** Het visuele element dat de drillthrough-actie aanroept met behulp van de visual contextmenu.
* **Rapport van de bron:** Het rapport met de bronvisual voor cross-rapport drillthrough.
* **Doelpagina:** De pagina die een gebruiker terechtkomt op na het initiëren van een drillthrough-actie.
* **Doelrapport:** Het rapport met de doelpagina voor cross-rapport drillthrough.

## <a name="enable-cross-report-drillthrough"></a>Cross-rapport drillthrough inschakelen

Om in te schakelen van een rapport om te worden van het doel van een drillthrough cross-rapport, moet u de functie voor het rapport in inschakelen de **opties** venster. Ga naar **bestand** > **opties en instellingen** > **opties**, en ga vervolgens naar **rapporteren instellingen** in de buurt van de onder aan de pagina aan de linkerkant.

Selecteer de **toestaan van visuele elementen in dit rapport gebruiken drillthrough doelen vanuit andere rapporten** selectievakje, zoals wordt weergegeven in de volgende afbeelding.

![Schermopname van opties venster met rapportinstellingen gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Cross-rapport drillthrough is nu ingeschakeld.

## <a name="set-up-cross-report-drillthrough"></a>Cross-rapport drillthrough instellen

Instellen van cross-rapport drillthrough is vergelijkbaar met het instellen van drillthrough in een rapport. Drillthrough is ingeschakeld op de doelpagina zodat andere visuele elementen om u te richten op de pagina worden ingeschakeld voor drillthrough. Zie voor de stappen voor het maken van drillthrough binnen één rapport, [drillthrough gebruiken in Power BI Desktop](desktop-drillthrough.md).

Voor het starten van het installatieproces, moet u een aantal initiële stappen uitvoeren:

* Instellen van een drillthrough-doel-pagina, die vervolgens kan worden benaderd vanuit andere rapporten in de werkruimte of een app.
* Toestaan dat een drillthrough pagina's van buiten de eigen rapport te zien.

Drillthrough-opties in de **velden** sectie van de **visualisaties** deelvenster, zoals wordt weergegeven in de volgende afbeelding.

![Schermafbeelding van de visualisaties in het deelvenster met opties voor Drillthrough is gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

De eerste stap bij het inschakelen van drillthrough voor een pagina is het valideren van de gegevensmodellen voor de bron- en -rapporten. Zorg ervoor dat: 

* Velden die u wilt doorgeven bestaat in zowel-gegevensmodellen.
* De namen van de velden en de namen van de tabellen waartoe ze behoren, identiek zijn (de tekenreeksen moet ook overeenkomen met en zijn hoofdlettergevoelig).

Bijvoorbeeld, als u wilt een filter doorgeven in veld *land* in tabel *Geografie*, beide modellen moeten hebben een *Geografie* tabel, en een *land* veld in die tabel. Als dat niet het geval is, moet u het veldnaam of de tabelnaam in het onderliggende model bijwerken. Bij te werken de weergavenaam van de velden goed niet voor cross-rapport drillthrough. (Houd er rekening mee dat de schema's in elk rapport hoeft te niet precies hetzelfde zijn.)

Om te beginnen met de installatie, moet u bereid u voor de doelpagina. In Power BI Desktop, gaat u naar de pagina en zorg ervoor dat de **Cross-rapport** drillthrough wisselknop is ingesteld op **op**. 

![Schermafbeelding van Cross-rapport in-/ uitschakelen is ingesteld op aan](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Sleep vervolgens de velden die u wilt gebruiken als de drillthrough-doel op het canvas. Selecteer of u wilt dat het veld moet worden gebruikt als een categorie, of als een meting wordt samengevat. Op dit moment kunt u selecteren of u wilt uitschakelen de **alle filters behouden** in-/ uitschakelen voor het visuele element. Als u niet wilt dat andere toegepaste filters van de bron-visual om aan te geven uw doel drillthrough visual, selecteert u **uit**.

> [!NOTE]
> Als u de pagina voor cross-rapport drillthrough alleen, verwijdert u de **terug** knop die automatisch wordt toegevoegd. De **terug** knop werkt alleen voor nagivation binnen één rapport. 

Nadat u het visuele element hebt geconfigureerd, zorg ervoor dat u het rapport opslaan als u zich in de Power BI-service of opslaan en publiceren van het rapport als u Power BI Desktop.

De vorige sectie beschreven hoe u cross-rapport drillthrough inschakelt voor Power BI Desktop (in de **opties** venster). Als u de Power BI-service gebruikt om te maken van een cross-rapport drillthrough-doel, om in te schakelen cross-rapport drillthrough moet u: 

1. Selecteer de werkruimte waarin uw doelrapport en bronrapport zich bevinden.
2. Selecteer **rapporten**.
3. Selecteer de **instellingen** pictogram voor het bronrapport.
4. Zorg ervoor dat de wisselknop cross-rapport drillthrough is **op**.
5. Uw rapport opslaan.

Dat is alles. Uw rapport is gereed voor de cross-rapport, drillthrough-ervaring. 

In de volgende sectie nemen we een overzicht van de ervaring voor het perspectief van de gebruiker.

## <a name="cross-report-drillthrough-experience"></a>Cross-rapport, drillthrough-ervaring

Wanneer u de cross-rapport, drillthrough-ervaring voor een rapport configureert, kunt u de functie te gebruiken kunt plaatsen.

Selecteer het bronrapport in Power BI-service en selecteer vervolgens een visueel element die gebruikmaakt van een of meer velden in de manier waarop die u hebt opgegeven bij het instellen van de doelpagina. Vervolgens met de rechtermuisknop op een gegevenspunt open het contextmenu van de visual en selecteer **Drillthrough**.

![Schermopname van het bronrapport in Power BI-service, met Drillthrough gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Vervolgens ziet u de resultaten in de cross-rapport drillthrough-pagina van het doel, net zoals u deze instellen tijdens het maken van het doel. De resultaten worden gefilterd op basis van de drillthrough-instellingen.

> [!IMPORTANT]
> Power BI in de cache opgeslagen cross-rapport, drillthrough-doelen. Als u wijzigingen aanbrengt, zorg er dan voor dat u uw browser vernieuwen als er geen de drillthrough-doelen zoals verwacht. 

Cross-rapport doelen worden ingedeeld in de volgende manier: 

`Target Page Name [Target Report Name]`

Nadat u de doelpagina waarop u wilt om een Drillthrough selecteert, gaat u Power BI naar die pagina. Wordt doorgegeven aan filtercontext op basis van de instellingen van de doelpagina. 

Filtercontext uit de bronvisual kan het volgende bevatten: 

* Rapport-, pagina- en filters op visueel niveau die betrekking hebben op de bronvisual. 
* Kruislings filteren en kruislings markeren die invloed hebben op de bronvisual. 
* Slicers op de pagina en slicers synchroniseren.
* URL-parameters.

Wanneer u op het doelrapport voor drillthrough land, wordt in Power BI alleen van toepassing filters voor velden waarvoor er exacte waarde komt overeen met voor veldnaam en de tabelnaam van de. Power BI toepassen niet sticky filters via het doelrapport. Deze verklaring, uw persoonlijke standaarddirectory voor bladwijzers echter toepassing als er een bestaat. Bijvoorbeeld, als uw persoonlijke standaarddirectory voor bladwijzers bevat een filter op rapportniveau voor *land = US*, Power BI met het filter eerst geldt voor het toepassen van de filtercontext uit de bronvisual. 

Voor cross-rapport drillthrough geeft Power BI de filtercontext door aan alle standard-pagina's in het doelrapport. Power BI overgedragen niet filtercontext voor de knopinfopagina's, omdat knopinfopagina's worden gefilterd op basis van de bronvisual die de knopinfo aanroept.

Als u terugkeren naar het bronrapport na de cross-rapport, drillthrough-actie wilt, gebruik van de browser **terug** knop. 

## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Slicers Power BI Desktop gebruiken](visuals/power-bi-visualization-slicers.md)
* [Drillthrough gebruiken in Power BI Desktop](desktop-drillthrough.md)

