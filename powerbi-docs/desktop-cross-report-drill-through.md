---
title: Drillthrough voor meerdere rapporten gebruiken in Power BI Desktop
description: Meer informatie over drillthrough van het ene naar het andere rapport in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 6424180dde3dac0d6d2b66c8a9303810b6aa0dc6
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71100106"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Drillthrough voor meerdere rapporten gebruiken in Power BI Desktop

Met de functie Drillthrough voor meerdere rapporten in Power BI Desktop kunt u contextafhankelijk van het ene rapport naar een ander rapport gaan. Dit geldt zolang de rapporten zich binnen dezelfde werkruimte of app in de Power BI-service bevinden. Gebruik drillthrough voor meerdere rapporten om twee of meer rapporten met gerelateerde inhoud te verbinden, en de filtercontext samen met de verbinding voor de rapporten door te geven. In dit artikel leert u hoe u drillthrough voor meerdere rapporten in Power BI-rapporten kunt instellen, en hoe gebruikers het ervaren als ze de drillthrough voor meerdere rapporten zelf gebruiken.

![Schermopname van de drillthroughoptie in Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Het is belangrijk dat u de volgende definities begrijpt voordat we beginnen met het instellen en gebruiken van drillthrough voor meerdere rapporten:

* **Bronvisual:** Het visuele element waarmee de drillthroughactie wordt aangeroepen met behulp van het visuele contextmenu.
* **Bronrapport:** Het rapport met de bronvisual voor drillthrough voor meerdere rapporten.
* **Doelpagina:** De pagina waarnaar een gebruiker wordt geleid na het initiëren van een drillthroughactie.
* **Doelrapport:** Het rapport met de doelpagina voor drillthrough voor meerdere rapporten.


> [!NOTE]
> Met de functie Drillthrough voor meerdere rapporten in Power BI Desktop kunt u contextafhankelijk van het ene rapport naar een ander rapport gaan. Dit geldt zolang de rapporten zich binnen dezelfde werkruimte of app in de Power BI-service bevinden. Dit is niet van toepassing bij het openen van individueel gedeelde rapporten in *Mijn werkruimte* ([Rapporten gedeeld met mij](service-share-dashboards.md#share-a-dashboard-or-report)). In plaats daarvan moet u het rapport openen in de werkruimte van waaruit het oorspronkelijk is gedeeld.


## <a name="enable-cross-report-drillthrough"></a>Drillthrough voor meerdere rapporten inschakelen

Als u een rapport wilt instellen als het doel van een drillthrough voor meerdere rapporten, moet u de functie voor dat rapport inschakelen in het venster **Opties**. Ga naar **Bestand** > **Opties en instellingen** > **Opties**, en ga vervolgens naar **Rapportinstellingen** linksonder op de pagina.

Schakel het selectievakje **Visuals in dit rapport toestaan om drillthroughdoelen van andere rapporten te gebruiken** in, zoals aangegeven in de volgende afbeelding.

![Schermopname van het venster Opties, waarin Rapportinstellingen is gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Drillthrough voor meerdere rapporten is nu ingeschakeld.

## <a name="set-up-cross-report-drillthrough"></a>Drillthrough voor meerdere rapporten instellen

Het instellen van drillthrough voor meerdere rapporten is vergelijkbaar met het instellen van drillthrough in een rapport. Drillthrough wordt ingeschakeld op de doelpagina, zodat andere visuals de pagina die is ingeschakeld voor drillthrough kunnen bereiken. Zie [Drillthrough gebruiken in Power BI Desktop](desktop-drillthrough.md) voor de benodigde stappen voor het maken van drillthrough binnen één rapport.

Om het instelproces te starten, moet u eerst deze stappen uitvoeren:

* Stel een drillthroughdoelpagina in, zodat deze toegankelijk is vanuit andere rapporten in de werkruimte of app.
* Sta toe dat in een rapport drillthroughpagina's van andere rapporten kunnen worden weergegeven.

Zoek drillthroughopties in de sectie **Velden** van het deelvenster **Visualisaties**, zoals aangegeven in de volgende afbeelding.

![Schermopname van het deelvenster Visualisaties, waarin Drillthroughopties is gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

De eerste stap voor het inschakelen van drillthrough voor een pagina is het valideren van de gegevensmodellen voor de bron- en doelrapporten. Vereisten: 

* De velden die u wilt doorgeven, moeten bestaan in beide gegevensmodellen.
* De namen van de velden en de namen van de tabellen waartoe ze behoren, moeten identiek zijn (de tekenreeksen moeten ook overeenkomen en zijn hoofdlettergevoelig).

Als u bijvoorbeeld een filter wilt doorgeven voor het veld *Land* in de tabel *Geografie*, moeten beide modellen de tabel *Geografie* en het veld *Land* in die tabel bevatten. Anders moet u de veld- of tabelnaam in het onderliggende model bijwerken. Het bijwerken van de weergavenaam van de velden werkt niet goed voor drillthrough voor meerdere rapporten. (De schema's in elk rapport hoeven niet precies hetzelfde te zijn.)

Voordat u kunt beginnen met het instellen, moet u de doelpagina voorbereiden. Ga in Power BI Desktop naar de pagina en zorg ervoor dat de schakeloptie **Drillthrough verschillende rapporten** is ingesteld op **Aan**. 

![Schermopname van de schakeloptie voor meerdere rapporten, ingesteld op Aan](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Sleep vervolgens de velden die u wilt gebruiken als drillthrough-doel naar het canvas. Selecteer of het veld moeten worden gebruikt als categorie of moet worden samengevat als een meting. Op dit punt kunt u selecteren of u de schakeloptie **Alle filters behouden** wilt uitschakelen voor de visual. Als u geen andere toegepaste filters van de bronvisual wilt doorgeven aan uw doelvisual, selecteert u **Uit**.

> [!NOTE]
> Als u de pagina alleen gebruikt voor drillthrough voor meerdere rapporten, moet u de automatisch toegevoegde knop **Terug** verwijderen. De knop **Terug** werkt alleen voor navigatie binnen één rapport. 

Nadat u de Visual hebt geconfigureerd, moet u het rapport opslaan als u zich in de Power BI-service bevindt, of het rapport opslaan en publiceren als u Power BI Desktop gebruikt.

In de vorige sectie is beschreven hoe u drillthrough voor meerdere rapporten inschakelt voor Power BI Desktop (in het venster **Opties**). Als u de Power BI-service gebruikt voor het maken van een drillthroughdoel voor meerdere rapporten, moet u het volgende doen: 

1. Selecteer de werkruimte waarin het doelrapport en het bronrapport zich bevinden.
2. Selecteer **Rapporten**.
3. Selecteer het pictogram **Instellingen** voor het bronrapport.
4. Zorg ervoor dat de schakeloptie voor drillthrough voor meerdere rapporten is ingesteld op **Aan**.
5. Sla het rapport op.

Dat is alles. Het rapport is nu gereed voor drillthrough voor meerdere rapporten. 

In de volgende sectie ziet u de ervaring vanuit het perspectief van de gebruiker.

## <a name="cross-report-drillthrough-experience"></a>Drillthrough-ervaring voor verschillende rapporten

Wanneer u de functie voor drillthrough in meerdere rapporten voor een rapport configureert, kunt u de functie ook toepassen.

Selecteer het bronrapport in de Power BI-service en selecteer vervolgens een visual die gebruikmaakt van het veld of de velden op de manier die u hebt opgegeven bij het instellen van de doelpagina. Klik vervolgens met de rechtermuisknop op een gegevenspunt om contextmenu van de visual te openen en selecteer **Drillthrough**.

![Schermopname van het bronrapport in de Power BI-service, waarin Drillthrough is gemarkeerd](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Vervolgens ziet u de resultaten op de doelpagina van het drillthroughrapport, precies zoals u deze hebt ingesteld tijdens het maken van het doel. De resultaten worden gefilterd op basis van de drillthroughinstellingen.

> [!IMPORTANT]
> Drillthroughdoelen voor meerdere rapporten worden in de Power BI-cache opgeslagen. Als u wijzigingen aanbrengt, moet u uw browser vernieuwen als de drillthroughdoelen niet worden weergegeven zoals u verwacht. 

Doelen voor verschillende rapporten worden op de volgende manier ingedeeld: 

`Target Page Name [Target Report Name]`

Als u de doelpagina voor de drillthrough selecteert, wordt u naar die pagina geleid. De filtercontext wordt doorgegeven op basis van de instellingen van de doelpagina. 

De filtercontext van de bronvisual kan het volgende omvatten: 

* Filters op rapport-, pagina- en visualniveau die van invloed zijn op de bronvisual. 
* Kruisfilters en kruismarkeringen die van invloed zijn op de bronvisual. 
* Slicers op de pagina en synchronisatieslicers.
* URL-parameters.

Wanneer u naar het doelrapport voor de drillthrough bent geleid, worden alleen filters toegepast op velden waarvoor exacte overeenkomsten met de tekenreeksen voor de veldnaam en tabelnaam worden gevonden. Er worden geen sticky-filters toegepast vanuit het doelrapport. Uw persoonlijke standaardbladwijzer wordt echter wel toegepast als er een bestaat. Bijvoorbeeld: als uw persoonlijke standaardbladwijzer het rapportfilter *Land = NL* bevat, wordt dat filter eerst toegepast voordat de filtercontext van de bronvisual wordt gepast. 

Voor een drillthrough voor meerdere rapporten wordt de filtercontext doorgegeven aan alle standaardpagina's in het doelrapport. Er wordt geen filtercontext doorgegeven voor knopinfo-pagina's, omdat knopinfo-pagina's worden gefilterd op basis van de bronvisual die de knopinfo aanroept.

Als u wilt terugkeren naar het bronrapport na de drillthroughactie voor meerdere rapporten, gebruikt u de knop **Terug**. 

## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Slicers Power BI Desktop gebruiken](visuals/power-bi-visualization-slicers.md)
* [Drillthrough gebruiken in Power BI Desktop](desktop-drillthrough.md)

