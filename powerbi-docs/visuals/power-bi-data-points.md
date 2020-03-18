---
title: Grote gegevenssets, gegevenspuntlimieten en gegevensstrategieën
description: Gegevenslimieten voor visuals en strategieën voor gegevensreductie
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 98af83c726cfd4e5b4e6744cbcfa1f7e5a69f57b
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79381440"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Gegevenspuntlimieten en strategieën op visualtype toepassen

Bij het weergeven van een visual in Power BI, moet de visualisatie snel en nauwkeurig zijn. Hiervoor moeten voor elk visualtype onderliggende algoritmen zijn geconfigureerd. Visuals in Power BI moeten flexibel genoeg zijn om gegevenssets van verschillende grootten af te handelen. Sommige gegevenssets hebben slechts een handvol gegevenspunten, terwijl andere gegevenssets petabytes aan gegevenspunten hebben. In dit artikel worden de strategieën beschreven die door Power BI worden gebruikt om visualisaties weer te geven.

## <a name="data-reduction-strategies"></a>Strategieën voor gegevensreductie
Elke visual maakt gebruik van een of meer *gegevensreductiestrategieën* om de mogelijk grote hoeveelheden gegevens die worden geanalyseerd af te handelen. Zelfs een eenvoudige tabel maakt gebruik van een strategie om te voorkomen dat de volledige gegevensset naar de client wordt geladen.  De reductiestrategie die wordt gebruikt, is afhankelijk van het visualtype. Elke visual maakt een keuze uit de ondersteunde *gegevensreductiestrategieën* als onderdeel van het genereren van de gegevensaanvraag die naar de server wordt verzonden. 

Elke visual bepaalt de parameters die in deze strategieën worden gebruikt om de totale hoeveelheid gegevens te beïnvloeden.   

## <a name="strategies"></a>Strategieën
Voor elke strategie zijn er standaardinstellingen op basis van de vorm en het type van de gegevens die worden gevisualiseerd. De standaardinstellingen kunnen echter worden overschreven in het deelvenster voor opmaak van Power BI om de juiste gebruikerservaring te bieden. 

* **Gegevens in vensters** (segmentering): Hiermee kunnen gebruikers door de gegevens in een visual bladeren door geleidelijk fragmenten van de gehele gegevensset te laden.
* **Bovenste N**: Alleen de eerste N items weergeven
* **Eenvoudige sampling**: De eerste, laatste en N evenredig verdeelde items ertussen weergeven.
* **Onderste N**: Alleen de laatste N items weergeven.  Dit is handig voor het controleren van gegevens die regelmatig worden bijgewerkt.
* **High-densitysampling** - een verbeterd densitysampling-algoritme dat uitbijters en/of de vorm van een curve beter respecteert.
    * **Sampling van lijnen waarop binning is toegepast**  - voorbeeldgegevenspunten op basis van uitbijters in opslaglocaties voor een as
    * **Sampling van overlappende punten** - sampling van gegevenspunten op basis van overlappende waarden om uitbijters te behouden

## <a name="statistics"></a>Statistieken
Bepaalde modellen kunnen statistieken verstrekken over het aantal waarden voor bepaalde kolommen. Wanneer deze gegevens aanwezig zijn, gebruiken we die gegevens voor een betere verdeling over meerdere hiërarchieën, als een visual het aantal waarden voor een strategie niet expliciet overschrijft.

Zie [Wat is nieuw in Analysis Services](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017) voor meer informatie

## <a name="dynamic-limits"></a>Dynamische limieten
Naast de bovenstaande strategieën maken visuals met twee hiërarchieën van groeperende kolommen (as en legenda of categorie en reeks) gebruik van een aanvullende strategie met de naam *dynamische limieten*.  Dynamische limieten zijn ontworpen voor een betere balans van gegevenspunten. 

Dynamische limieten bieden een betere selectie van punten voor sparse gegevens dan vaste limieten. Er kan bijvoorbeeld een visual worden geconfigureerd om 100 categorieën en 10 reeksen met een totaal van 1000 punten te selecteren. Maar de werkelijke gegevens hebben 50 categorieën en 20 reeksen.  Tijdens de uitvoering van de query selecteren dynamische limieten alle 20 reeksen om de aangevraagde 1000 punten op te vullen.

Dynamische limieten worden automatisch toegepast wanneer de server het volgende kan afhandelen, zoals hieronder aangegeven:

* In Power BI Desktop met On-premises SSAS-versie 2016 of hoger [ waarbij gebruik wordt gemaakt van de SuperDax-mogelijkheden van de server](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* In Desktop- en Power BI-service wanneer een geïmporteerd model, DirectQuery, live verbinding maken met de service of live verbinding maken met AS PaaS wordt gebruikt. 

* In de Power BI-service, wanneer u verbinding maakt via een on-premises gateway naar on-premises SSAS, kunnen we geen dynamische limieten gebruiken. Door de on-premises gateway wordt de strategie voor dynamische limieten die een andere structuur van resultatensets uit de on-premises SSAS retourneert niet volledig ondersteund.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Strategieën en gegevenspuntlimieten op visualtype

### <a name="area-chart"></a>Vlakdiagram
Zie [De werking van sampling van lijnen](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Staaf-/kolomdiagram
- In de categorische modus
    - Categorieën: Virtualisatie met behulp van een venster van 500 rijen tegelijk
    - Reeks: Bovenste 60
    - In de scalaire modus (kan dynamische limieten gebruiken)
        - Maximum aantal punten: 10.000
        - Categorieën: Voorbeeld van 500 waarden
        - Reeks: Bovenste 20 waarden

### <a name="card-multirow"></a>Kaart (meervoudige rij) 
- Waarden: Virtualisatie met behulp van een venster van 200 rijen tegelijk

### <a name="combo-chart"></a>Combinatiegrafiek
 Maakt gebruik van dezelfde strategieën als kolomdiagram. U ziet dat de regel in de **combinatiegrafiek** geen gebruik maakt van het algoritme voor high-densitysampling dat het **lijndiagram** gebruikt.

### <a name="power-bi-visuals"></a>Power BI-visuals
Kunnen maximaal 30.000 ophalen, maar het is aan de auteurs van de visual om aan te geven welke strategieën moeten worden gebruikt. De standaardlimiet is 1000, maar de maker van de visual kan dat wijzigen tot een maximum van 30.000.

### <a name="doughnut"></a>Ring
- Maximum aantal punten: 3500
- Groep: Bovenste 500
- Details: Bovenste 20

### <a name="filled-map-choropleth"></a>Gevulde choropletenkaart 
De choropletenkaart kan statistieken of dynamische limieten gebruiken. Power BI probeert gebruik te maken van reductie in de volgende volgorde: dynamische limieten, statistieken en ten slotte configuratie. 
- Maximum aantal punten: 10000
- Categorieën: Bovenste 500
- Reeks (als zowel X als Y aanwezig is): Bovenste 20

### <a name="funnel"></a>Trechterdiagram
- Maximum aantal punten: 3500
- Categorieën: Bovenste 3500

### <a name="kpi"></a>KPI
- Trendas
- Onderste 3500

### <a name="line-chart"></a>Lijndiagram
Zie [De werking van sampling van lijnen](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Lijndiagram, high-density
Zie [High-densitysampling](../desktop-high-density-sampling.md)

### <a name="map"></a>Kaart 
- Maximum aantal punten: 3500

Afhankelijk van de configuratie, kan een kaart het volgende bevatten:
- Locatie: Bovenste 3500
- Locatie, grootte: Bovenste 3500
- Locatie, breedtegraad en lengtegraad als statistische functies (+/- grootte): Bovenste 3500
- Breedtegraad, lengtegraad: Zie [high-density spreidingsdiagrammen](desktop-high-density-scatter-charts.md)
- Breedtegraad, lengtegraad, grootte: Bovenste 3500
- Legenda, breedtegraad, lengtegraad: Zie [high-density spreidingsdiagrammen](desktop-high-density-scatter-charts.md)
- Legenda, breedtegraad, lengtegraad, grootte: Bovenste 233 legenda's, bovenste 15 breedtegraad en lengtegraad (kan statistieken of dynamische limieten gebruiken)
- Locatie, legenda, breedtegraad en lengtegraad als statistische functies (+/-grootte): Bovenste 233 locaties, bovenste 15 legenda's (kan statistieken of dynamische limieten gebruiken)

### <a name="matrix"></a>Matrix
- Rijen: Virtualisatie met behulp van een venster van 500 rijen tegelijk
- Kolommen: Bovenste 100 groeperende kolommen 
- Waarden: meerdere waarden worden niet meegeteld voor de gegevensreductie

### <a name="powerapps-visual"></a>PowerApps-visual
Kunnen maximaal 30.000 ophalen, maar het is aan de auteurs van de visual om aan te geven welke strategieën moeten worden gebruikt. De standaardlimiet is 1000, maar de maker van de visual kan dat wijzigen tot een maximum van 30.000.

### <a name="radial-gauge"></a>Radiale meter
Geen strategie voor gegevensreductie

### <a name="slicer"></a>Slicer
- Waarden: Virtualisatie met behulp van een venster van 200 rijen tegelijk

### <a name="scatter-chart-high-density"></a>Spreidingsdiagrammen (high-density)
Zie [High-density spreiding](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Cirkeldiagram
- Maximum aantal punten: 3500
- Groep: Bovenste 500
- Details: Bovenste 20

### <a name="r--python-visuals"></a>R & Python-visuals
Beperkt tot 150.000 rijen. Als meer dan 150.000 rijen zijn geselecteerd, worden alleen de bovenste 150.000 rijen gebruikt

### <a name="ribbon-chart"></a>Lintgrafiek
- In de categorische modus
    - Categorieën: Virtualisatie (gegevens in vensters) met behulp van een venster van 500 rijen tegelijk
    - Reeks: Bovenste 60
    - In de scalaire modus (kan dynamische limieten gebruiken)
        - Maximum aantal punten: 10.000
        - Categorieën: Voorbeeld van 500 waarden
        - Reeks: Bovenste 20 waarden

### <a name="shape-map-preview"></a>Shape-kaart (voorbeeld)
De shape-kaart kan statistieken of dynamische limieten gebruiken. 
- Maximum aantal punten: 1500
- Categorieën: Bovenste 500

### <a name="table"></a>Tabel
- Waarden: Virtualisatie (gegevens in vensters) met behulp van een venster van 500 rijen tegelijk

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Structuurkaart (kan statistieken of dynamische limieten gebruiken)
- Maximum aantal punten: 3500
- Groep: Bovenste 500
- Details: Bovenste 20

### <a name="waterfall-chart"></a>Watervalgrafiek
- Als er alleen de categoriebucket is
    - Maximum aantal punten: 3500
    - Alleen categorie - bovenste 3500
- Als zowel categorie als uitsplitsing aanwezig zijn
    - Categorie: Virtualisatie (gegevens in vensters) met behulp van een venster van 30 rijen tegelijk
    - Uitsplitsing - bovenste 200 waarden


## <a name="next-steps"></a>Volgende stappen
[Visualisatietypen](power-bi-report-visualizations.md)
