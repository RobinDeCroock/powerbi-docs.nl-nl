---
title: Multidimensionale gegevens van Analysis Services in Power BI Desktop
description: Multidimensionale gegevens van SQL Server Analysis Services (SSAS) in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: eac1134ff12025d05cd59e86b7538cde58e3a2ee
ms.sourcegitcommit: 08f65ea314b547b41b51afef6876e56182190266
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/25/2020
ms.locfileid: "76753144"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Verbinding maken met multidimensionale modellen van SSAS in Power BI Desktop

Met Power BI Desktop hebt u toegang tot *multidimensionale modellen van SSAS*, vaak *SSAS MD* genoemd.

Als u verbinding wilt maken met een SSAS MD-database, selecteert u **Gegevens ophalen**, **Database** > **SQL Server Analysis Services-database** en kiest u vervolgens **Verbinding maken**:

![SQL Server Analysis Services-database (SSAS), het dialoogvenster Gegevens ophalen, Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

In zowel de Power BI-service als in Power BI Desktop worden multidimensionale modellen van SSAS in de live-verbindingsmodus ondersteund. U kunt rapporten die gebruikmaken van **multidimensionale modellen van SSAS** in de livemodus publiceren en uploaden naar de Power BI-service.

## <a name="capabilities-and-features-of-ssas-md"></a>Mogelijkheden en functies van SSAS MD

In de volgende secties worden onderdelen en functies van Power BI- en SSAS MD-verbindingen beschreven.

### <a name="tabular-metadata-of-multidimensional-models"></a>Metagegevens van de multidimensionale modellen in tabelvorm

In de volgende tabel wordt de overeenkomst weergegeven tussen multidimensionale objecten en de metagegevens in tabelvorm die worden geretourneerd naar Power BI Desktop. Power BI voert query's uit op het model voor metagegevens in tabelvorm. Op basis van de geretourneerde metagegevens worden in Power BI Desktop de betreffende DAX-query's uitgevoerd op SSAS wanneer u een visualisatie (zoals een tabel, matrix, grafiek of slicer) maakt.

| Multidimensionaal BISM-object | Metagegevens in tabelvorm |
| --- | --- |
| Kubus |Model |
| Kubusdimensie |Tabel |
| Dimensiekenmerken (sleutels), naam |Kolommen |
| Meetgroep |Tabel |
| Meting |Meting |
| Metingen zonder gekoppelde meetgroep |In de tabel met de naam *Metingen* |
| Relatie meetgroep -> kubusdimensie |Relatie |
| Perspectief |Perspectief |
| KPI |KPI |
| Gebruiker/bovenliggende en onderliggende hiërarchieën |Hiërarchieën |

### <a name="measures-measure-groups-and-kpis"></a>Metingen, meetgroepen en KPI 's

Meetgroepen in een multidimensionale kubus worden weergegeven als tabellen met het sigmateken (∑) ernaast in het deelvenster **Velden**. Berekende metingen zonder gekoppelde meetgroep worden gegroepeerd onder een speciale tabel met de naam *Metingen* in de metagegevens in tabelvorm.

Om complexe modellen in een multidimensionaal model te vereenvoudigen, kunt u een set metingen of KPI's in een kubus definiëren met als locatie een *weergavemap*. Power BI herkent weergavemappen in metagegevens in tabelvorm en toont metingen en KPI's in de weergavemappen. KPI's in multidimensionale databases ondersteunen *Waarde*, *Doel*, *Statusgrafiek* en *Trendgrafiek*.

### <a name="dimension-attribute-type"></a>Dimensiekenmerktype

Multidimensionale modellen ondersteunen ook het koppelen van dimensiekenmerken aan specifieke dimensiekenmerktypen. Bijvoorbeeld een dimensie **Geografie**, waarin de dimensiekenmerken *Stad*, *Staat-provincie*, *Land* en *Postcode*, waaraan de betreffende geografietypen zijn gekoppeld, worden weergegeven in de metagegevens in tabelvorm. Power BI herkent de metagegevens. zodat u kaartvisualisaties kunt maken. U herkent deze koppelingen aan het *kaart*pictogram naast het element in het deelvenster **Veld** in Power BI.

Power BI kan ook afbeeldingen weergeven wanneer u een veld met URL's (Uniform Resource Locators) van de afbeeldingen opgeeft. U kunt deze velden opgeven als *ImageURL*-typen in SQL Server Data Tools (of vervolgens in Power BI). Het type gegevens wordt vervolgens verstrekt aan Power BI in de metagegevens in tabelvorm. Power BI kan deze afbeeldingen vervolgens ophalen van de URL en weergeven als visuals.

### <a name="parent-child-hierarchies"></a>Bovenliggende en onderliggende hiërarchieën

Multidimensionale modellen ondersteunen bovenliggende en onderliggende hiërarchieën die worden weergegeven als een *hiërarchie* in de metagegevens in tabelvorm. Elk niveau van de bovenliggende/onderliggende hiërarchie wordt weergegeven als een verborgen kolom in de metagegevens in tabelvorm. Het sleutelkenmerk van de bovenliggende/onderliggende dimensie wordt niet weergegeven in de metagegevens in tabelvorm.

### <a name="dimension-calculated-members"></a>Berekende leden van dimensies

Multidimensionale modellen ondersteunen het maken van verschillende typen *berekende leden*. De twee meest voorkomende typen berekende leden zijn:

* Berekende leden in kenmerkhiërarchieën die zich niet op hetzelfde niveau als *Alle* bevinden
* Berekende leden in gebruikershiërarchieën

In multidimensionale modellen worden *berekende leden in kenmerkhiërarchieën* weergegeven als waarden van een kolom. U hebt een paar extra opties en beperkingen als u dit type berekend lid weergeeft:

* Een dimensiekenmerk kan een optioneel *UnknownMember* hebben.

* Een kenmerk dat berekende leden bevat, kan niet het hoofdkenmerk van de dimensie zijn, tenzij dit het enige kenmerk van de dimensie is.

* Een kenmerk dat berekende leden bevat, kan niet een bovenliggend/onderliggend kenmerk zijn.

De berekende leden van de gebruikershiërarchieën worden niet weergegeven in Power BI. In plaats daarvan kunt u verbinding maken met een kubus die berekende leden in gebruikershiërarchieën bevat. Het is echter niet mogelijk om berekende leden te zien als ze niet voldoen aan de beperkingen die we in de vorige lijst met opsommingstekens hebben genoemd.

### <a name="security"></a>Beveiliging

Multidimensionale modellen ondersteunen beveiliging op dimensie- en celniveau via *rollen*. Wanneer u verbinding met een kubus met Power BI maakt, wordt u geverifieerd en geëvalueerd op de juiste machtigingen. Als op een gebruiker *dimensiebeveiliging* is toegepast, worden de leden van de respectieve dimensie niet zichtbaar voor de gebruiker in Power BI. Wanneer voor een gebruiker echter de machtiging *celbeveiliging* is gedefinieerd, waarbij bepaalde cellen zijn beperkt, kan die gebruiker geen verbinding maken met de kubus via Power BI.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Er gelden bepaalde beperkingen voor het gebruik van SSAS MD:

* Alleen Enterprise- en BI-edities van SQL Server 2014 bieden ondersteuning voor liveverbindingen. Voor de standaardeditie van SQL Server is SQL Server 2016 of hoger vereist voor liveverbindingen.

* *Acties* en *benoemde sets* zijn niet beschikbaar in Power BI. Als u visuals en rapporten wilt maken, kunt u nog wel verbinding maken met kubussen die ook acties of benoemde sets bevatten.

* Wanneer in Power BI metagegevens voor een SSAS-model worden weergegeven, kan het voorkomen dat u geen gegevens uit het model kunt ophalen. Dit scenario kan zich voordoen als u de 32-bits versie van de MSOLAP-provider hebt geïnstalleerd, maar niet de 64-bits versie. Het probleem kan wellicht worden opgelost door de 64-bits versie te installeren.

* U kunt geen metingen op *rapportniveau* maken bij het ontwerpen van een rapport dat live is verbonden met een multidimensionaal SSAS-model. De enige metingen die beschikbaar zijn, zijn de metingen die in het MD-model zijn gedefinieerd.

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Ondersteunde functies van SSAS MD in Power BI Desktop

Het verbruik van de volgende elementen wordt ondersteund in deze versie van SSAS MD. Zie [Power View voor multidimensionale modellen](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014) voor meer informatie over deze functies.

* Standaardleden
* Dimensiekenmerken
* Dimensiekenmerktypen
* Berekende leden van dimensies, die:
  * een enkel echt lid moeten zijn wanneer de dimensie meer dan één kenmerk heeft;
  * niet het sleutelkenmerk van de dimensie mogen zijn, tenzij dit het enige kenmerk is; en
  * geen bovenliggend/onderliggend kenmerk mogen zijn.
* Dimensiebeveiliging
* Mappen weergeven
* Hiërarchieën
* ImageUrls
* KPI's
* KPI-trends
* Metingen (met of zonder meetgroepen)
* Metingen als variant

## <a name="troubleshooting"></a>Problemen oplossen

De volgende lijst bevat alle bekende problemen bij het verbinden met SQL Server Analysis Services (SSAS).

* **Fout: kan het modelschema niet laden**: deze fout treedt doorgaans op wanneer de gebruiker die verbinding maakt met Analysis Services geen toegang heeft tot de database/kubus.
