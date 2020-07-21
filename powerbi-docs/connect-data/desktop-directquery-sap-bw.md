---
title: DirectQuery en SAP Business Warehouse (BW) in Power BI
description: Overwegingen bij het gebruik van DirectQuery met SAP Business Warehouse (BW)
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b7cc8a159139cc53a0e243134b31305dff95812d
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216432"
---
# <a name="connect-to-sap-business-warehouse-by-using-directquery-in-power-bi"></a>Verbinding maken met SAP Business Warehouse met DirectQuery in Power BI
U kunt rechtstreeks verbinding maken met **SAP Business Warehouse (BW)** -gegevensbronnen met behulp van **DirectQuery**. Gezien de OLAP-/multidimensionale aard van SAP BW, zijn er veel belangrijke verschillen tussen DirectQuery via SAP BW en via relationele bronnen zoals SQL Server. Deze verschillen kunnen als volgt worden samengevat:

* In **DirectQuery** via relationele bronnen is er een set query's (zoals gedefinieerd in het dialoogvenster **Gegevens ophalen** of **Query-Editor**) waarmee de gegevens die in de lijst met velden beschikbaar zijn logisch worden gedefinieerd. Dit is *niet* het geval bij het verbinden met een OLAP-bron zoals SAP BW. In plaats daarvan wordt bij het verbinden met de SAP-server met **Gegevens ophalen** alleen de Infocube of BEx Query geselecteerd. Vervolgens zijn de sleutelgetallen en dimensies van de geselecteerde Infocube/BEx Query beschikbaar in de lijst met velden.   
* Er is ook geen **Query-Editor** wanneer u verbinding maakt met SAP BW. De instellingen voor de gegevensbron (bijvoorbeeld de servernaam) kunnen worden gewijzigd door **Query's bewerken > Gegevensbroninstellingen** te selecteren. De instellingen voor parameters kunnen worden gewijzigd door **Query's bewerken > Parameters beheren** te selecteren.
* Vanwege de unieke aard van OLAP-bronnen zijn er aanvullende beperkingen (voor zowel modellering als visualisaties) van toepassing, naast de normale beperkingen voor DirectQuery. Deze beperkingen worden verderop in dit artikel beschreven.

Bovendien is het *uiterst belangrijk* te weten dat er veel functies van SAP BW zijn die niet worden ondersteund in Power BI, en dat er vanwege de aard van de openbare interface met SAP BW belangrijke gevallen zijn waarin de resultaten die via Power BI worden gezien, niet overeenkomen met de resultaten zoals gezien met behulp van een SAP-programma. Deze beperkingen worden verderop in dit artikel beschreven. Bekijk deze beperkingen en verschillen in werking zorgvuldig om ervoor te zorgen dat de via Power BI waargenomen resultaten zoals die door de openbare SAP-interface worden geretourneerd, correct worden geïnterpreteerd.  

> [!NOTE]
> De mogelijkheid om gebruik te maken van DirectQuery via SAP BW was in preview tot de update van maart 2018 maart voor Power BI Desktop. Tijdens de preview hebben de feedback en voorgestelde verbeteringen de aanzet gegeven tot een wijziging die gevolgen heeft voor rapporten die zijn gemaakt met die preview-versie. Nu de release van de algemene beschikbaarheid (GA) van DirectQuery via SAP BW heeft plaatsgevonden, *moet* u eventuele bestaande (preview-)rapporten met DirectQuery via SAP BW die zijn gemaakt met de pre-GA-versie weggooien. In rapporten die zijn gemaakt met de pre-GA-versie van DirectQuery via SAP BW komen fouten met de pre-GA-rapporten voor bij het aanroepen van Vernieuwen. Dit is een gevolg van de poging om de metagegevens te vernieuwen met eventuele wijzigingen in de onderliggende SAP BW-kubus. Maak deze rapporten opnieuw met behulp van de GA-versie van DirectQuery via SAP BW vanuit een leeg rapport. 

## <a name="additional-modeling-restrictions"></a>Extra modelleringsbeperkingen
De primaire extra modelleringsbeperkingen bij het verbinden met SAP BW met behulp van DirectQuery in Power BI zijn als volgt:

* **Geen ondersteuning voor berekende kolommen:** de mogelijkheid voor het maken van berekende kolommen is uitgeschakeld. Dit betekent ook dat Groeperen en Clustering, waarmee berekende kolommen worden gemaakt, niet beschikbaar zijn.
* **Aanvullende beperkingen voor metingen:** er zijn extra beperkingen voor de DAX-expressies die kunnen worden gebruikt in metingen, overeenkomstig het door SAP BW geboden ondersteuningsniveau.
* **Geen ondersteuning voor het definiëren van relaties:** de relaties zijn inherent aan de externe SAP-bron, en er kunnen geen aanvullende relaties worden gedefinieerd in het model.
* **Geen gegevensweergave:** de **Gegevensweergave** geeft normaal gesproken de gegevens op detailniveau weer in de tabellen. Gezien de aard van OLAP-bronnen zoals SAP BW, is deze weergave niet beschikbaar via SAP BW.
* **Kolom- en metingsdetails zijn vast:** de lijst met kolommen en metingen in de lijst met velden wordt bepaald door de onderliggende gegevensbron en kan niet worden gewijzigd. Het is bijvoorbeeld niet mogelijk een kolom te verwijderen of het gegevenstype ervan te wijzigen (de naam kan wel worden gewijzigd).
* **Aanvullende beperkingen in DAX:** er zijn extra beperkingen met betrekking tot de DAX die kunnen worden gebruikt in metingdefinities, in overeenstemming met beperkingen in de bron. Het is bijvoorbeeld niet mogelijk een statistische functie over een tabel te gebruiken.

## <a name="additional-visualization-restrictions"></a>Extra visualisatiebeperkingen
De primaire extra beperkingen voor visualisaties bij het verbinden met SAP BW met behulp van DirectQuery in Power BI zijn als volgt:

* **Geen aggregatie van kolommen:** het is niet mogelijk de aggregatie voor een kolom in een visual te wijzigen, deze is altijd *Niet samenvatten*.
* **Filteren van metingen is uitgeschakeld:** het filteren van metingen is uitgeschakeld overeenkomstig de door SAP BW geboden ondersteuning.
* **Meerdere selecties en opnemen/uitsluiten:** de mogelijkheid om meerdere gegevenspunten in een visualisatie te selecteren is uitgeschakeld als de punten waarden uit meer dan één kolom vertegenwoordigen. Bijvoorbeeld: in een staafdiagram met verkopen per land met Categorie in de legenda, is het niet mogelijk het punt voor (Verenigde Staten, Fietsen) en (Frankrijk, Kleding) te selecteren. Op dezelfde manier is het niet mogelijk het punt voor (Verenigde Staten, Fietsen) te selecteren en dit uit te sluiten van de visualisatie. Beide beperkingen worden opgelegd overeenkomstig de ondersteuning die door SAP BW wordt geboden.

## <a name="support-for-sap-bw-features"></a>Ondersteuning voor SAP BW-functies
De volgende tabel bevat alle SAP BW-functies die niet volledig worden ondersteund of zich anders gedragen bij gebruik van Power BI.   

| Functie | Beschrijving |
| --- | --- |
| Lokale berekeningen |In een BEx-query gedefinieerde lokale berekeningen wijzigen de getallen zoals die worden weergegeven via hulpprogramma's als BEx Analyzer. Ze worden echter niet weerspiegeld in de cijfers die uit SAP worden geretourneerd via de openbare MDX-interface. <br/> <br/> **Daarom komen de getallen in een Power BI-visualisatie niet noodzakelijkerwijs overeen met die voor een overeenkomstige visualisatie in een SAP-hulpprogramma.**<br/> <br/>  Wanneer u bijvoorbeeld verbinding maakt met een querykubus uit een BEx-query waarin de aggregatie is ingesteld op cumulatief (d.w.z. lopend totaal), haalt Power BI de basiscijfers op en negeert die instelling.  Een analist kan vervolgens natuurlijk lokaal een berekening van een lopend totaal toepassen in Power BI, maar moet voorzichtig zijn bij het interpreteren van de getallen als dit niet wordt gedaan. |
| Aggregaties |In sommige gevallen (met name wanneer met meerdere valuta's wordt gewerkt) komen de cumulatieve cijfers die door de openbare SAP-interface worden geretourneerd, niet overeen met de cijfers die door SAP-hulpprogramma’s worden weergegeven. <br/> <br/> **Daarom komen de getallen in een Power BI-visualisatie niet noodzakelijkerwijs overeen met die voor een overeenkomstige visualisatie in een SAP-hulpprogramma.** <br/> <br/> Zo zouden totalen van verschillende valuta's in BEx Analyzer bijvoorbeeld worden weergegeven als *, maar gewoon worden geretourneerd door de openbare SAP-interface, zonder indicatie dat een dergelijk cumulatief getal geen betekenis heeft. Zo zou het getal (waarin bijvoorbeeld USD, EUR en AUD worden geaggregeerd) worden weergegeven door Power BI. |
| Valutanotatie |Valutanotatie (bijvoorbeeld $2,300 of 4000 AUD) wordt niet weergegeven in Power BI. |
| Maateenheden |Maateenheden (bijvoorbeeld 230 kg) worden niet weergegeven in Power BI. |
| Sleutel versus tekst (kort, gemiddeld, lang) |Voor een SAP BW-kenmerk zoals CostCenter wordt in de lijst met velden één kolom Kostenplaats weergegeven.  Door die kolom te gebruiken, wordt de standaardtekst weergeven.  Door verborgen velden weer te geven, is het ook mogelijk de kolom met de unieke naam te zien (die de door SAP BW toegewezen unieke naam retourneert en de basis is van de uniciteit).<br/> <br/>  De sleutel en andere tekstvelden zijn niet beschikbaar. |
| Meerdere hiërarchieën van een kenmerk |In **SAP** kan een kenmerk meerdere hiërarchieën hebben. Vervolgens kan de gebruiker in hulpprogramma's zoals BEx Analyzer de hiërarchie selecteren die moet worden gebruikt wanneer een kenmerk wordt opgenomen in een query. <br/> <br/> In **Power BI** zijn de verschillende hiërarchieën in de lijst met velden zichtbaar als verschillende hiërarchieën in dezelfde dimensie.  Wanneer echter meerdere niveaus van twee verschillende hiërarchieën in dezelfde dimensie worden geselecteerd, leidt dat ertoe dat er met SAP lege gegevens worden geretourneerd. |
| Behandeling van onregelmatige hiërarchieën |![Schermopname van onregelmatige inhoud, waarbij de behandeling van onregelmatige hiërarchieën wordt weergegeven.](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Schaalfactor/teken omkeren |In SAP kan voor een sleutelgetal een schaalfactor (bijvoorbeeld 1000) worden gedefinieerd als een opmaakoptie, wat inhoudt dat de schaal van alle weergaven wordt aangepast met die factor. <br/> <br/> Op dezelfde manier kan er een eigenschap worden ingesteld waarmee het teken wordt omgekeerd. Wanneer een dergelijk sleutelgetal in Power BI wordt gebruikt (in een visualisatie of als onderdeel van een berekening), wordt het ongeschaalde getal gebruikt (en wordt het teken niet omgekeerd). De onderliggende schaalfactor is niet beschikbaar. In Power BI-visualisaties kunnen de op de as weergegeven schaaleenheden (K, M, B) worden ingesteld als deel van de visuele opmaak. |
| Hiërarchieën waar niveaus dynamisch worden weergegeven/verborgen |Wanneer verbinding wordt gemaakt met SAP BW, wordt eerst de informatie over de niveaus van een hiërarchie opgehaald, wat resulteert in een set velden in de lijst met velden. Deze wordt in de cache geplaatst, en als de set met niveaus verandert, wordt de set met velden pas gewijzigd wanneer de lijst wordt vernieuwd. <br/> <br/> Dit is alleen mogelijk in **Power BI Desktop**. Dergelijke vernieuwingen om de wijzigingen in de niveaus weer te geven, kunnen niet worden aangeroepen in de Power BI-service na publiceren. |
| Standaardfilter |Een BEx-query kan standaardfilters bevatten, die automatisch door SAP BEx Analyzer worden toegepast. Deze worden niet ontsloten, en daarom worden bij het equivalente gebruik in Power BI standaard niet dezelfde filters toegepast. |
| Verborgen sleutelgetallen |In een BEx-query kan de zichtbaarheid van sleutelgetallen worden bepaald, en verborgen sleutelgetallen worden niet weergegeven in SAP BEx Analyzer. Dit wordt niet weerspiegeld in de openbare API, en daarom worden dergelijke verborgen sleutelgetallen wel weergegeven in de lijst met velden. Ze kunnen vervolgens wel worden verborgen in Power BI. |
| Getalnotatie |Getalnotaties (aantallen decimalen, decimaalteken enzovoort) worden niet automatisch weerspiegeld in Power BI. Deze opmaak kan vervolgens wel binnen Power BI worden bepaald. |
| Hiërarchieversiebeheer |Met SAP BW kunnen verschillende versies van een hiërarchie worden bijgehouden, bijvoorbeeld de kostenplaatshiërarchie in 2007 en in 2008. Alleen de meest recente versie is beschikbaar in Power BI, omdat informatie over versies niet wordt ontsloten in de openbare API. |
| Tijdafhankelijke hiërarchieën |Wanneer u Power BI gebruikt, worden tijdafhankelijke hiërarchieën geëvalueerd op de huidige datum. |
| Valutaconversie |SAP BW biedt ondersteuning voor valutaconversie op basis van tarieven in de kubus. Dergelijke mogelijkheden worden niet ontsloten in de openbare API en zijn daardoor niet beschikbaar in Power BI. |
| Sorteervolgorde |De sorteervolgorde (op tekst of op sleutel) voor een kenmerk kan worden gedefinieerd in SAP. Deze sorteervolgorde wordt niet weerspiegeld in Power BI. Zo kunnen maanden mogelijk worden weergegeven als ‘april’, ‘aug.’ enzovoort. <br/> <br/> Het is niet mogelijk deze sorteervolgorde in Power BI te wijzigen. |
| Technische namen |In **Gegevens ophalen** zijn zowel de namen (beschrijvingen) van de kenmerken/metingen als de technische namen zichtbaar. De lijst met velden bevat alleen de kenmerk-/metingnamen (beschrijvingen). |
| Attributen |Het is niet mogelijk om toegang te krijgen tot de attributen van een kenmerk in Power BI. |
| Taalinstelling eindgebruiker |De landinstelling die wordt gebruikt om verbinding te maken met SAP BW wordt ingesteld als onderdeel van de verbindingsgegevens, en weerspiegelt niet de landinstelling van de gebruiker van het uiteindelijke rapport. |
| Tekstvariabelen |In SAP BW kunnen veldnamen plaatsaanduidingen voor variabelen bevatten (bijvoorbeeld "Werkelijke waarden $YEAR$") die worden vervangen door de geselecteerde waarde. Als bijvoorbeeld het jaar 2016 wordt geselecteerd voor de variabele, wordt het veld in BEx-hulpprogramma's weergegeven als Werkelijke waarden 2016. <br/> <br/> De kolomnaam in Power BI wordt niet gewijzigd afhankelijk van de variabele waarde, en wordt weergegeven als "Werkelijke waarden $YEAR$".  De kolomnaam kan vervolgens wel worden gewijzigd in Power BI. |
| Uitgangsvariabelen van klanten | Uitgangsvariabelen van klanten worden niet ontsloten door de openbare API en worden daarom niet ondersteund door Power BI. |
| Kenmerkstructuren | Kenmerkstructuren in de onderliggende bron van SAP BW zullen leiden tot een ‘explosie’ van metingen die in Power BI worden weergegeven. Bijvoorbeeld met twee metingen, Verkoop en Kosten, en een kenmerkstructuur met Begroot en Feitelijk, worden er vier metingen weergegeven: Verkoop.Begroot, Verkoop.Feitelijk, Kosten.Begroot, Kosten.Feitelijk. |


## <a name="next-steps"></a>Volgende stappen
Bekijk de volgende bronnen voor meer informatie over DirectQuery:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Gegevensbronnen die worden ondersteund door DirectQuery](power-bi-data-sources.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
