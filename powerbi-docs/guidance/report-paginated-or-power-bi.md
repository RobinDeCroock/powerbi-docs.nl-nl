---
title: Wanneer u gepagineerde rapporten gebruikt in Power BI
description: Richtlijnen voor het gebruik van gepagineerde rapporten in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 2e048c3aa2ebc6e51388be652234c2ccf2348663
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886131"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>Wanneer u gepagineerde rapporten gebruikt in Power BI

Dit artikel is bedoeld voor u wanneer u als auteur Power BI-rapporten gaat ontwerpen. Het biedt suggesties om u te helpen bij het ontwikkelen van [gepagineerde rapporten in Power BI](../paginated-reports-report-builder-power-bi.md).

> [!NOTE]
> Voor het publiceren van gepagineerde rapporten in Power BI is een Power BI Premium-abonnement vereist. Rapporten worden alleen weergegeven wanneer ze zich in een werkruimte bevinden op een toegewezen capaciteit waarbij [de workload gepagineerde rapporten is ingeschakeld](../service-admin-premium-workloads.md#paginated-reports).

Gepagineerde rapporten in Power BI zijn geoptimaliseerd voor **afdrukken** of **PDF-generatie**. Ze bieden u ook de mogelijkheid om pixel-perfecte indelingen met veel opmaak te produceren. Gepagineerde rapporten zijn dus ideaal voor operationele rapporten, zoals verkoopfacturen.

Power BI-rapporten daarentegen zijn geoptimaliseerd voor **verkenning en interactiviteit**. Ook kunnen ze uw gegevens presenteren met behulp van een uitgebreide reeks ultramoderne visuals. Power BI-rapporten zijn daarom ideaal voor analytische rapporten, zodat uw rapportgebruikers gegevens kunnen verkennen en relaties en patronen kunnen ontdekken.

Wij raden u aan om een gepagineerd Power BI-rapport te gebruiken wanneer:

* U weet dat het rapport moet worden afgedrukt, of als een PDF-document moet worden uitgevoerd.
* De indeling van het gegevensnetwerk zou kunnen uitbreiden en overlopen. Houd er rekening mee dat een tabel of matrix in een Power BI-rapport niet dynamisch kan worden aangepast om alle gegevens weer te geven, maar in plaats daarvan schuifbalken biedt. Maar als het wordt afgedrukt, is het niet mogelijk om te scrollen om gegevens die niet zichtbaar zijn te onthullen.
* Door Power BI gepagineerde functies en mogelijkheden werken in uw voordeel. Veel van dergelijke rapportscenario's worden later in dit artikel beschreven.

## <a name="legacy-reports"></a>Traditionele rapporten

Wanneer u al SQL Server Reporting Services (SSRS) [Report Definition Language (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs)-rapporten hebt, kunt u ervoor kiezen om ze opnieuw te ontwikkelen als [Power BI-rapporten](../consumer/end-user-reports.md), of ze te migreren als gepagineerde rapporten naar Power BI. Zie voor meer informatie [SQL Server Reporting Services-rapporten migreren naar Power BI](migrate-ssrs-reports-to-power-bi.md).

Na publicatie in een Power BI-werkruimte zijn gepagineerde rapporten naast Power BI-rapporten beschikbaar. Ze kunnen vervolgens eenvoudig worden gedistribueerd met behulp van [Power BI-apps](../service-create-distribute-apps.md).

U kunt SSRS-rapporten opnieuw ontwikkelen in plaats van ze te migreren. Dit geldt met name voor rapporten die zijn bedoeld voor het leveren van analytische ervaringen. In deze gevallen zullen Power BI-rapporten waarschijnlijk betere rapportervaringen van gebruikers opleveren.

## <a name="paginated-report-scenarios"></a>Scenario's gepagineerde rapporten

Er zijn veel boeiende scenario's waarin u misschien de voorkeur geeft aan het ontwikkelen van een gepagineerd Power BI-rapport. Veel functies of mogelijkheden worden niet ondersteund door Power BI-rapporten.

* **Print-ready**: Gepagineerde rapporten zijn geoptimaliseerd voor afdrukken of PDF-generatie. Indien nodig kunnen gegevensgebieden op een gecontroleerde manier worden uitgebreid en overlopen naar meerdere pagina's. In uw rapportindelingen kunt u marges en paginakopteksten en voetteksten definiëren.
* **Renderindelingen**: In Power BI kunnen gepagineerde rapporten in verschillende indelingen worden gerenderd. Indelingen zijn Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML en MHTML. (De MHTML-indeling wordt door de Power BI-service gebruikt voor het renderen van rapporten.) Uw rapportgebruikers kunnen besluiten om te exporteren in de indeling die bij hen past.
* **Precisie-indeling**: U kunt pixel-perfecte indelingen met veel opmaak ontwerpen, op de exacte grootte en locatie geconfigureerd in fracties van inches of centimeters.
* **Dynamische indeling**: U kunt zeer responsieve indelingen produceren door veel rapporteigenschappen in te stellen voor het gebruik van VB.NET-expressies. Expressies hebben toegang tot veel core .NET Framework-bibliotheken.
* **Render-specifieke indeling**: U kunt uitdrukkingen gebruiken om de rapportindeling te wijzigen op basis van de toegepaste renderindeling. U kunt bijvoorbeeld het rapport ontwerpen om de zichtbaarheid uit te schakelen (voor inzoomen en uitzoomen) wanneer het wordt gerenderd met een niet-interactieve indeling, zoals PDF.
* **Systeemeigen query's**: U hoeft niet eerst een Power BI-gegevensset te ontwikkelen. Het is mogelijk om systeemeigen query’s te maken (of opgeslagen procedures te gebruiken) voor elke [ondersteunde gegevensbron](../paginated-reports-data-sources.md). Query's kunnen betrekking hebben op parameterisering.
* **Ontwerpers van grafische query's**: Power BI Report Builder bevat ontwerpers van grafische query’s om u te helpen bij het schrijven en testen van uw gegevensset-query's.
* **Statische gegevens**: U kunt een gegevensset definiëren en gegevens rechtstreeks in de rapportdefinitie invoeren. Deze mogelijkheid is vooral handig voor het ondersteunen van een demo of voor het leveren van een proof of concept (POC).
* **Gegevensintegratie**: U kunt gegevens uit verschillende gegevensbronnen of met statische gegevenssets combineren. Dit wordt gedaan door het maken van aangepaste velden met behulp van VB.NET-expressies.
* **Parameterisering**: U kunt zeer aangepaste parametriseringservaringen ontwerpen, waaronder gegevensgestuurde en trapsgewijze parameters. Het is ook mogelijk om de standaardinstellingen van de parameters te definiëren. Deze ervaringen kunnen worden ontworpen om uw rapportgebruikers te helpen snel de juiste filters in te stellen. Ook hoeven parameters geen rapportgegevens te filteren; ze kunnen worden gebruikt om what-if-scenario's of dynamische filtering of styling te ondersteunen.
* **Afbeeldingsgegevens**: Uw rapport kan afbeeldingen renderen wanneer ze zijn opgeslagen in binaire indeling in een gegevensbron.
* **Aangepaste code**: U kunt codeblokken van VB.NET-functies in uw rapport ontwikkelen en deze in elke rapportexpressie gebruiken.
* **Subrapporten**: U kunt andere gepagineerde Power BI-rapporten (vanuit dezelfde werkruimte) in uw rapport opnemen.
* **Flexibele gegevensrasters**: U hebt een fijnmazige controle over de indeling van het raster door gebruik te maken van het tablix-gegevensgebied. Het ondersteunt ook complexe indelingen, inclusief geneste en aangrenzende groepen. En het kan worden geconfigureerd om koppen te herhalen wanneer deze over meerdere pagina's worden afgedrukt. Er kunnen ook subrapporten of andere visualisaties worden ingesloten, waaronder gegevensbalken, sparklines en indicatoren.
* **Ruimtelijke gegevenstypen**: Met het kaartgegevensgebied kunnen [ruimtelijke gegevenstypen van SQL Server](/sql/relational-databases/spatial/spatial-data-sql-server) worden gevisualiseerd. Dus de gegevenstypen GEOGRAFIE en GEOMETRIE kunnen worden gebruikt om punten, lijnen of polygonen te visualiseren. Het is ook mogelijk om polygonen te visualiseren die zijn gedefinieerd in ESRI-vormbestanden.
* **Moderne meters**: Radiale en lineaire meters kunnen worden gebruikt om KPI-waarden en -statussen weer te geven. Ze kunnen zelfs worden ingebed in rastergegevensgebieden en worden herhaald binnen groepen.
* **HTML-rendering**: U kunt rijkelijk opgemaakte tekst weergeven wanneer deze is opgeslagen als HTML.
* **Afdruk samenvoegen**: U kunt tijdelijke aanduidingen voor tekstvakken gebruiken om de gegevenswaarden in de tekst te injecteren. Op deze manier kunt u een samenvoegrapport voor afdrukken maken.
* **Interactiviteitsfuncties**: Interactieve functies omvatten het schakelen van zichtbaarheid (om inzoomen en inzoomen te bereiken), koppelingen, interactieve sortering en knopinfo. U kunt ook koppelingen toevoegen met drillthrough naar Power BI-rapporten of andere gepagineerde Power BI-rapporten. Koppelingen kunnen zelfs naar een andere locatie binnen hetzelfde rapport springen.
* **Abonnementen**: Power BI kan gepagineerde rapporten volgens een schema als e-mails leveren, met rapportbijlagen in elke ondersteunde indeling.
* **Indelingen per gebruiker**: U kunt responsieve rapportindelingen maken op basis van de geverifieerde gebruiker die het rapport opent. U kunt het rapport ontwerpen om gegevens anders te filteren, gegevensregio's of visualisaties te verbergen, verschillende indelingen toe te passen of gebruikersspecifieke parameterinstellingen in te stellen.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

* [Wat zijn gepagineerde rapporten in Power BI Premium?](../paginated-reports-report-builder-power-bi.md)
* Guy in a Cube-vide: [Introductie van gepagineerde rapporten in Power BI](https://www.youtube.com/watch?v=wfqn45XNK3M)
* [SQL Server Reporting Services-rapporten migreren naar Power BI](migrate-ssrs-reports-to-power-bi.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
* Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)
