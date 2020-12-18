---
title: Detectie van gegevenssets met de datasets-hub
description: Meer informatie over hoe u de gegevenssets in uw organisatie en de gerelateerde rapporten kunt vinden, verkennen en gebruiken.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Share your work
ms.openlocfilehash: c6b7170df78b6d544f7eb97ec62516577f9267b6
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513799"
---
# <a name="datasets-discovery-using-the-datasets-hub"></a>Detectie van gegevenssets met de datasets-hub

Met de gegevenssets-hub kunt u eenvoudig de gegevenssets in uw organisatie vinden, verkennen en gebruiken. Het bevat informatie over de gegevenssets en ingangspunten voor het maken van rapporten boven op die gegevenssets of voor het gebruik van deze gegevenssets met Analyseren in Excel.

De gegevenssets-hub kan in veel scenario's handig zijn:
* Eigenaren van gegevenssets kunnen de metrische gegevens over het gebruik van gegevensset, statussen vernieuwen, gerelateerde rapporten en herkomst bekijken om de gegevenssets te controleren en te beheren.
* Makers van rapporten kunnen de hub gebruiken om geschikte gegevenssets te vinden om hun rapporten te maken en gebruiken om eenvoudig rapporten te maken gebaseerd op de gegevensset, volledig nieuw of via sjablonen.
* Rapportgebruikers kunnen deze pagina gebruiken om rapporten te vinden gebaseerd op betrouwbare gegevenssets.

Door het eenvoudig te maken om gegevenssets en de bijbehorende rapporten van goede kwaliteit te vinden, kunt u met de gegevenssets-hub voorkomen dat overbodige rapporten worden gemaakt. Daarnaast kunt u eenvoudig goede rapporten vinden die u kunt gebruiken als beginpunten voor het maken van nieuwe rapporten.

In dit artikel wordt uitgelegd wat u ziet op de gegevenssets-hub en wordt beschreven hoe u deze kunt gebruiken. Voor eigenaren van gegevenssets bevat het ook een aantal tips over het [verbeteren van de detectie en bruikbaarheid van hun gegevenssets](#make-your-dataset-discoverable).

**Welke gegevenssets zie ik in de gegevenssets-hub?**
* Voor een gegevensset die wordt weergegeven in de gegevenssets-hub, moet deze zich bevinden in een [nieuwe werkruimte-ervaring](../collaborate-share/service-new-workspaces.md).
* De gegevenssets die u kunt zien in de gegevenssets-hub zijn de sets waar u ten minste [samenstellingsmachtigingen](service-datasets-build-permissions.md) voor hebt.
* Als u een gratis gebruiker bent, ziet u alleen gegevenssets in uw *Mijn werkruimte*, of gegevenssets waarvoor u [samenstellingsmachtiging](service-datasets-build-permissions.md) hebt die zich in werkruimten met Premium-capaciteit bevinden.

## <a name="find-the-dataset-you-need"></a>Zoek de gegevensset-ID die u nodigt hebt

De detectie van de gegevensset wordt gestart op de pagina gegevenssets-hubs. Om naar de gegevenssets-hub te gaan:
* In de Power BI-service: Selecteer **gegevenssets** in het navigatiedeelvenster.
* In de Power BI-app in Teams: Selecteer het tabblad **Gegevenssets** of **Gegevenssets** in het navigatiedeelvenster.

In de onderstaande afbeelding ziet u de gegevenssets-hub in de Power BI-service.

![Schermopname van de pagina gegevenssets-hub](media/service-datasets-hub/datasets-hub-main-page.png)

De gegevenssets-hub biedt u een selectie van aanbevolen gegevenssets en een lijst van alle gegevenssets in de organisatie waar u toegang tot hebt.

In de volgende secties beschrijven we deze secties en de acties die u kunt uitvoeren.

### <a name="recommended-datasets"></a>Aanbevolen gegevenssets

Aanbevolen gegevenssets zijn goedgekeurde gegevenssets (niveau verhoogd of gecertificeerd) die aan u worden getoond gebaseerd op een berekening waarbij rekening wordt gehouden met hoe recent ze zijn vernieuwd en hoe recent u rapporten en/of dashboards die aan hen zijn gerelateerd, hebt bezocht.

### <a name="dataset-list"></a>Lijst met gegevenssets

In de lijst met gegevenssets ziet u gegevenssets in de organisatie waarvoor u op zijn minst [samenstellingsmachtigingen](service-datasets-build-permissions.md) hebt. De lijst bevat drie tabbladen waarmee de lijst met gegevenssets kan worden gefilterd.
* **Alle gegevenssets**: Toont alle gegevenssets in uw organisatie waarvoor u op zijn minst [samenstellingsmachtigingen](service-datasets-build-permissions.md) hebt.
* **Recent**: Toont gegevenssets waarvan u onlangs gerelateerde rapporten hebt bekeken. Wanneer u een rapport opent, kan het enkele minuten duren voordat de gerelateerde gegevensset wordt weergegeven in de kolom Recent.
* **Mijn gegevenssets**: Toont de gegevenssets waarvan u eigenaar bent. 

Gebruik het zoekvak om de items op het huidige tabblad verder te filteren.

De kolommen van de lijst worden hieronder beschreven. Klik op een kolomkop om gebaseerd op die kolom te sorteren. 
* **Naam**: Naam van gegevensset. Klik op de naam van de gegevensset om rapporten te verkennen die zijn samengesteld met deze gegevensset.
* **Aanbeveling**: Aanbevelingsstatus.
* **Eigenaar**: Eigenaar van gegevensset.
* **Werkruimte**: De werkruimte waarin de gegevensset te vinden is.
* **Vernieuwd**: Tijd van laatste vernieuwing (afgerond op uur, dag, maand en jaar. Bekijk info over de gegevensset op de detailpagina voor gegevenssets voor een exacte tijd van laatste vernieuwing).
* **Vertrouwelijkheid**: Vertrouwelijkheid, indien ingesteld. Klik op het pictogram info om de beschrijving van het vertrouwelijkheidslabel weer te geven.

### <a name="create-new-reports-or-pull-data-into-excel-via-analyze-in-excel"></a>Maak nieuwe rapporten of haal gegevens op in Excel via Analyseren in Excel

Als u een nieuw rapport wilt maken op basis van gegevensset of als u de gegevens in Excel wilt ophalen met [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md), selecteert u **Meer opties (...)** in de rechter benedenhoek van een tegel met aanbevolen gegevensset of op de regel van een gegevensset in de lijst met gegevenssets. Er worden mogelijk andere acties weergegeven in de vervolgkeuzelijst, afhankelijk van de machtigingen die u hebt op de gegevensset.

Wanneer u een nieuw rapport maakt op basis van de gegevensset, wordt het bewerkingsgedeelte van het rapport geopend. Wanneer u het nieuwe rapport opslaat, wordt dit opgeslagen in de werkruimte die de gegevensset bevat als u schrijfmachtigingen hebt voor die werkruimte. Als u geen schrijfmachtigingen hebt voor die werkruimte of als u een gratis gebruiker bent en de gegevensset zich in een werkruimte met een Premium-capaciteit bevindt, dan wordt het nieuwe rapport opgeslagen in *Mijn werkruimte*.

## <a name="view-dataset-details-and-explore-related-reports"></a>Geef de details van de gegevensset weergeven en verken gerelateerde rapporten

Als u meer informatie wilt weergeven over de gegevensset, gerelateerde rapporten wilt verkennen of een nieuw rapport wilt maken op basis van de gegevensset, volledig nieuw of via een sjabloon, kiest u een gegevensset uit de aanbevolen gegevenssets of uit de lijst met gegevenssets. Er wordt een pagina geopend met informatie over de gegevensset, een lijst met de rapporten die boven op de gegevensset zijn gebouwd en toegangspunten voor het maken van nieuwe rapporten op basis van de gegevensset of het ophalen van de gegevens in Excel via [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md).

![Schermopname van de gegevensset-hubpagina voor het verkennen van gerelateerde rapporten](media/service-datasets-hub/datasets-hub-explore-related-reports.png)

De paginakoptekst bevat de naam van de gegevensset, de goedkeuring, indien van toepassing, en de eigenaar van de gegevensset. Als u een e-mail wilt verzenden naar de eigenaar van de gegevensset of de degene die de gegevensset heeft gecertificeerd (indien van toepassing), dan klikt u op de koptekst en vervolgens op de naam van de eigenaar.

### <a name="dataset-details"></a>Details van de gegevensset

In de sectie details over gegevensset ziet u de naam van de werkruimte waarin de gegevensset zich bevindt, de exacte tijd van de laatste vernieuwing, vertrouwelijkheid (indien ingesteld), de beschrijving van de gegevensset (indien van toepassing) en de naam van de person die het heeft gecertificeerd (indien gecertificeerd). U kunt hier ook de herkomst van de gegevensset openen.

### <a name="related-reports"></a>Gerelateerde rapporten

In de sectie gerelateerde rapporten verkennen ziet u alle rapporten die op de geselecteerde gegevensset zijn gebaseerd. U kunt een kopie van een rapport maken door de rapportregel te selecteren in de lijst en vervolgens op het pictogram Een kopie van dit rapport opslaan te klikken.

De kolommen in de lijst met gerelateerde rapporten zijn:
* **Naam**: Rapportnaam. Als de naam eindigt op (sjabloon), dan betekent dit dat het rapport speciaal is geconstrueerd om als sjabloon te dienen.
* **Aanbeveling**: Aanbevelingsstatus.
* **Werkruimte**: De naam van de werkruimte waarin het rapport te vinden is.

### <a name="create-a-report-built-on-the-dataset"></a>Maak een rapport op basis van de gegevensset

Klik in de sectie Een rapport maken op de knop **Maken**. Als er een rapportsjabloon bestaat voor de gegevensset, zijn er twee opties beschikbaar in een vervolgkeuzelijst:
* **Via sjabloon**: Hiermee maakt u een kopie van de sjabloon in *Mijn werkruimte*.
* **Volledig nieuw**: Hiermee opent u het bewerkingsgedeelte van rapporten naar een nieuw rapport op basis van de gegevensset. Wanneer u uw nieuwe rapport opslaat, wordt dit opgeslagen in de werkruimte die de gegevensset bevat als u schrijfmachtigingen hebt voor die werkruimte. Als u geen schrijfmachtigingen hebt voor de werkruimte of als u een gratis gebruiker bent en de gegevensset zich in een werkruimte met een Premium-capaciteit bevindt, dan wordt het nieuwe rapport opgeslagen in *Mijn werkruimte*.

Als er geen rapportsjablonen zijn, klikt u op **Maken** en dit opent het bewerkingsgedeelte van rapporten direct.

>[!NOTE]
> Er wordt slechts één sjabloon weergegeven in de vervolgkeuzelijst Rapport maken, zelfs als er meerdere rapportsjablonen bestaan voor deze gegevensset. 

### <a name="pull-the-dataset-into-excel-via-analyze-in-excel"></a>De gegevensset in Excel ophalen via Analyseren in Excel

Selecteer in de sectie Analyseren in Excel **Analyseren** om de gegevensset in Excel op te halen via Analyseren in Excel.

## <a name="make-your-dataset-discoverable"></a>Uw gegevensset detecteerbaar maken

Er zijn een aantal manieren om de detectie van uw gegevens sets te verhogen:
* **Uw gegevensset goedkeuren**: U kunt het niveau van uw gegevensset verhogen of deze certificeren om te voorkomen dat gebruikers ze kunnen vinden en om hen te laten weten dat het een betrouwbare bron van gegevens is. De goedgekeurde gegevenssets zijn gelabeld met badges en zijn gemakkelijk te herkennen in Power BI. In de gegevenssets-hub worden alleen goedgekeurde gegevenssets weergegeven in de sectie aanbevolen gegevenssets, en in de lijst met gegevenssets worden standaard eerst de goedgekeurde gegevenssets vermeld.

    [Meer informatie over het goedkeuren van uw gegevenssets](../collaborate-share/service-endorse-content.md). 
* **Geef een duidelijke beschrijving op van de gegevensset**: U kunt gebruikers helpen de juiste gegevensset te ontdekken door nuttige, zinvolle beschrijvingen van uw gegevenssets te bieden. [U geeft de beschrijving op als onderdeel van het proces voor het goedkeuren van de gegevensset](../collaborate-share/service-endorse-content.md#promote-content). 
* **Geef uw gegevensset een memorabele afbeelding**: U kunt het voor gebruikers gemakkelijker maken om uw gegevensset te vinden en te onthouden door een memorabele afbeelding toe te voegen. Hierdoor gaat uw gegevensset opvallen op de pagina gegevenssets-hub en op elke willekeurige andere locatie die ondersteuning biedt voor het weergeven van gegevensset-afbeeldingen. Als u een afbeelding aan uw gegevensset wilt toevoegen, opent u de instellingen van uw gegevensset en vouwt u de sectie afbeelding van gegevensset uit.
* **Een rapportsjabloon maken op basis van de gegevensset**: U kunt een rapportsjabloon maken waarmee gebruikers aan de slag kunnen gaan om hun eigen rapporten samen te stellen op basis van uw gegevensset. Deze sjabloon is gewoon een normaal rapport dat u ontwerpt, met als doel dat het als sjabloon kan worden gebruikt. Wanneer u het bestand opslaat, moet u het achtervoegsel "(sjabloon)" toevoegen aan de naam van het rapport, bijvoorbeeld *Maandelijkse verkoop (sjabloon)* .

    Wanneer een gebruiker **Maken > Via sjabloon** in het gedeelte een rapport maken in de detailweergave voor de gegevensset van de gegevenssets-hub, wordt een kopie van de sjabloon gemaakt in de *Mijn werkruimte* van de gebruiker en deze wordt vervolgens geopend in het bewerkingsgedeelte van rapporten.

    Rapportsjablonen zijn ook gemakkelijk te herkennen in de lijst met gerelateerde rapporten in de detailweergave voor de gegevensset van de gegevenssets-hub.
  
## <a name="next-steps"></a>Volgende stappen
* [Gegevenssets in werkruimten gebruiken](service-datasets-across-workspaces.md)
* [Rapporten maken op basis van gegevenssets van verschillende werkruimten](service-datasets-discover-across-workspaces.md)
* [Uw gegevensset goedkeuren](../collaborate-share/service-endorse-content.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
