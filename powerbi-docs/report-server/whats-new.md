---
title: Wat is er nieuw in Power BI Report Server
description: Meer informatie over wat er nieuw is in de meest recente versie van Power BI Report Server. Dit artikel gaat over de primaire functiegebieden. Het wordt bijgewerkt wanneer nieuwe versies worden uitgebracht.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/27/2021
ms.openlocfilehash: a0e5ced79c5aee6d6392b3d52fcc8e6d638faf27
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531925"
---
# <a name="whats-new-in-power-bi-report-server"></a>Wat is er nieuw in Power BI Report Server

Meer informatie over wat er nieuw is in de nieuwste versies van Power BI Report Server en Power BI Desktop voor Power BI Report Server. Dit artikel gaat over de primaire functiegebieden. Het wordt bij elke nieuwe versie bijgewerkt. Zie voor meer informatie over wat er nieuw is in Power BI Report Server het [Wijzigingslogboek voor Power BI Report Server](changelog.md).

Down load [Power bi Report Server en Power bi Desktop voor Power bi Report Server](https://powerbi.microsoft.com/report-server/).

## <a name="january-2021"></a>Januari 2021

Hier volgt een lijst met nieuwe en bijgewerkte functies. Zie het [blog bericht Power bi Report Server voor januari 2021](https://powerbi.microsoft.com/blog/power-bi-report-server-january-2021-feature-summary/)voor meer informatie.

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop voor Power BI Report Server

Hier volgen enkele hoogtepunten uit de nieuwe functies.

**Power BI-rapporten**

- Alle filters toep assen is nu algemeen beschikbaar
- Schuif regelaar voor visueel zoomen
- Intrekkings controle van certificaten voor Internet verbindingen
- Selectie deel venster in de weer gave voor mobiele indeling
- ArcGIS voor Power BI-ondersteuning

**Gegevens connectiviteit**

- Hive LLAP-connector algemeen beschikbaar
- Nieuwe connectors: Actian, Anaplan, sterren explosie Presto

### <a name="new-connection-metadata-format-preview"></a>Nieuwe meta gegevens indeling voor verbinding (preview-versie)

De manier waarop de meta gegevens van de verbinding worden opgeslagen in de pbix-bestands indeling in oktober, zijn bijgewerkt. Deze update maakt deel uit van een lange termijn om. pbix-bestanden via een programma toegankelijker en bewerkbaar te maken. De wijziging in de versie van Power BI Desktop die maandelijks wordt uitgebracht, is al ingeschakeld in overeenstemming met de Power BI-service. We bekijken een voor beeld van de wijzigingen in deze release van Power BI Desktop voor rapport server, beginnend bij deze maand.

Vanaf deze versie ziet u de volgende melding waarin u wordt gevraagd het voor beeld in te scha kelen en de uitgebreide indeling te upgraden:

"Binnenkort beschikbaar: Schakel het verbeterde voor beeld van de meta gegevens indeling in om betere prestaties en beveiligings updates in Power BI te krijgen."

Houd rekening met het volgende:

- Bestaande gegevens sets blijven werken, zelfs zonder upgrades. Er wordt een upgrade uitgevoerd wanneer de uitgebreide indeling algemeen beschikbaar wordt gemaakt.
- Power BI Desktop voor rapport server wordt een bestaande gegevensset automatisch bijgewerkt naar de uitgebreide indeling voor u. Het wordt aangeraden bestaande rapporten op de rapport server niet te overschrijven met deze bijgewerkte versie, als u wilt terugkeren naar de vorige indeling.
- Deelname aan dit voor beeld is optioneel, maar we raden u aan om het uit te proberen en ons feedback te geven. We streven ernaar de uitgebreide indeling algemeen beschikbaar te maken als de enige optie in de volgende release van de rapport server.
 
Als beheerder kunt u deze preview uitschakelen, het geforceerde v3 uitschakelen en het selectie vakje preview-functie verbergen. Stel de volgende DWORD-waarde in op 0 in het REGI ster: AllowV3Models in:

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop SSRS]
"AllowV3Models"=dword:00000000
```

of

```
[HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop SSRS]
"AllowV3Models"=dword:00000000
```

Zie [uitgebreide meta gegevens van gegevensset gebruiken](../connect-data/desktop-enhanced-dataset-metadata.md) voor meer informatie.

### <a name="power-bi-report-server"></a>Power BI Report Server

**Browser ondersteuning voor afschaffing**

Als u Edge verouderd of Internet Explorer 11 gebruikt, is het tijd om uw browser bij te werken. De ondersteuning voor de Edge legacy browser eindigt vanaf 9 maart 2021. Ondersteuning voor Internet Explorer 11 eindigt vanaf 17 augustus 2021. 

Er wordt een waarschuwing weer gegeven in de Power BI Report Server-webportal dat Internet Explorer 11 wordt afgeschaft. Tijd om bij te werken. Zie [browser ondersteuning voor Power bi Report Server](browser-support.md) voor meer informatie.

**Pictogram nieuw product**

Power BI Report Server heeft een nieuw product pictogram, bij het bijwerken van de nieuwe pictogrammen in alle micro soft-producten.

:::image type="content" source="media/whats-new/power-bi-report-server-new-logo.png" alt-text="Power BI Report Server nieuw logo.":::

## <a name="october-2020"></a>Oktober 2020

Hier volgt een volledige lijst met nieuwe en bijgewerkte functies. Zie de [blogpost van oktober 2020](https://powerbi.microsoft.com/blog/power-bi-report-server-october-2020-feature-summary/) over Power BI Report Server voor meer informatie. 

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop voor Power BI Report Server

Hier volgen enkele hoogtepunten uit de nieuwe functies.

**Modern lint**  

Het moderne lint komt Power BI Desktop voor Power BI Report Server. We blijven uitbreidingen en meer functies toevoegen aan het lint. Zie [Het bijgewerkte lint in Power BI Desktop gebruiken](../create-reports/desktop-ribbon.md) voor meer informatie over de wijzigingen en voordelen.

:::image type="content" source="media/whats-new/report-server-new-ribbon.png" alt-text="Scherm opname van het nieuwe lint in Power BI Desktop voor Power BI Report Server.":::

**Slicers voor hiërarchieën**

Als u meerdere gerelateerde velden wilt filteren binnen één slicer, kunt u een zogeheten *hiërarchieslicer* maken. Nu deze algemeen beschikbaar is, profiteert u van extra functionaliteit:

- Nieuwe opties voor het uitvouwen/samenvouwen van pictogrammen.
- Pictogrammen schalen nu mee met de tekengrootte.
- Aanpasbare inspringing voor onderliggende items.
- Verdere aanpassing van de kopteksttekst van de slicer.

:::image type="content" source="media/whats-new/report-server-slicer-hierarchy.png" alt-text="Hiërarchie slicer in Power BI Desktop voor Power BI Report Server.":::

Zie [Slicers in Power BI](../visuals/power-bi-visualization-slicers.md) in de documentatie voor meer informatie.

**Verbeterde mogelijkheden voor het ontwerpen op mobiele apparaten** 

In deze release introduceren we een verbeterde ontwerp ervaring voor mobiele indeling en meer mogelijkheden voor de indeling van mobiele apparaten. Omdat meer organisaties de Power BI mobiele apps hebben aangenomen, hebben we feedback ontvangen voor meer mogelijkheden en verbeteringen voor de mobiele ontwerp ervaring. Met de verbeteringen in deze release kunt u gemakkelijk aantrekkelijke, interactieve rapporten bouwen die zijn geoptimaliseerd voor mobiele apparaten.

Dit zijn de nieuwe ervaringen en mogelijkheden voor het bouwen van rapporten die zijn geoptimaliseerd voor mobiele apparaten:  

- Nieuwe telefoonemulator  
- Bijgewerkt visualisatiedeelvenster  
- Ondersteuning voor overlay-visuals  
- Bladwijzers in de weergave voor mobiele indeling  
- Rasterlijnen uitschakelen en vastmaken aan het raster  

:::image type="content" source="media/whats-new/report-server-mobile-layout.png" alt-text="Verbeterde mobiele indeling in Power BI Desktop voor Power BI Report Server.":::

Raadpleeg de blogpost [Verbeteringen in mobiel ontwerpen](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2020-feature-summary/#_mobile) voor meer informatie.

**Gegevensvoorbereiding: Automatische tabeldetectie vanuit Excel-bestanden**

Deze nieuwe functie van de Excel-connector identificeert automatisch secties van elk Excel-werkblad die in een tabel moeten worden uitgepakt. Ze worden weergegeven onder de groep 'Voorgestelde tabellen' in de Navigator. Voorheen moesten gegevens worden ingedeeld als tabel of benoemd bereik in Excel. Anders moest u de relevante rijen/kolommen met specifieke transformaties scrapen, zoals rijen overslaan en kolommen verwijderen van werkbladobjecten (vergelijk Blad1 in het volgende voorbeeld). Als u deze functie wilt gebruiken, moet u deze inschakelen in het dialoogvenster **Instellingen**.

:::image type="content" source="media/whats-new/report-server-excel-table.png" alt-text="Het herkennen van een Excel-tabel in Power BI Desktop voor Power BI Report Server.":::

**Modellering: Verbeterde metagegevens van gegevensset**

In het verleden werden alleen geladen query's die in Power Query waren gegenereerd, toegewezen aan het gegevensmodel. Nu zijn alle query's toegewezen aan objecten in het gegevensmodel. De query's worden opnieuw gegenereerd op basis van het gegevensmodel wanneer u dat PBIX-bestand opent.

Met deze back-endupdate worden en blijven toekomstige functies mogelijk. 

Bijvoorbeeld:

- Met het toevoegen van externe hulpprogramma's in Power BI Desktop (momenteel in preview), worden tabellen die u via deze externe hulpprogramma's toevoegt nu weergegeven als query's wanneer u het rapport opnieuw opent.
- Als u een PBIT-bestand hebt geëxporteerd en het bestand hebt uitgepakt, ziet u nu het model in JSON en worden er geen fouten over beschadigde bestanden meer ontvangen. 

Als u een oudere PBIX hebt die niet automatisch kan worden bijgewerkt, moet u, om redenen als niet-toegepaste wijzigingen, uw model upgraden voordat u andere modellerings wijzigingen kunt aanbrengen. 

**Ondersteuning voor Windows 7 eindigt**

Op 14 januari 2020 is, na 10 jaar, de ondersteuning voor Windows 7 geëindigd. In overeenstemming met deze wijziging wordt de ondersteuning voor Power BI Desktop op Windows 7 op 31 januari 2021 gestopt. Power BI Desktop wordt daarna alleen nog ondersteund in Windows 8 en recentere versies. De versie van Power BI Desktop van januari 2021 die is geoptimaliseerd voor de Report Server, wordt ondersteund op basis van het moderne beleid voor levenscyclus. Met andere woorden: deze wordt volledig ondersteund tot de volgende release (momenteel gepland voor mei 2021). Na mei 2021 worden tot januari 2022 alleen nog beveiligingsupdates ontvangen. Na januari 2022 wordt alle ondersteuning gestopt. Raadpleeg de [Ondersteuningstijdlijn voor Power BI Report Server](support-timeline.md) voor meer informatie. 

**Volledige lijst met updates**

Hier volgt een volledige lijst met de updates in de oktober Edition van Power BI Desktop voor Power BI Report Server. 

**Rapportage**

- Modern lint
- Watermerken op canvas
- Totaal aantal labels voor gestapelde visuals
- Extra optie voor algemene visual voor het bijhouden van laagvolgorde
- Verlooplegenda
- Filter voor relatieve tijd
- De mogelijkheid om de koptekstslicer te wijzigen
- Verbeteringen in de hiërarchieslicer

    - Nieuwe opties voor het uitvouwen/samenvouwen van pictogrammen
    - Pictogrammen schalen nu mee met de tekengrootte
    - Mogelijkheid om inspringing aan te passen voor onderliggende items

- Verbeterde mogelijkheden voor ontwerpen op mobiele apparaten

    - Nieuwe telefoonemulator
    - Bijgewerkt visualisatiedeelvenster
    - Ondersteuning voor overlay-visuals
    - Bladwijzers in de weergave voor mobiele indeling
    - Rasterlijnen uitschakelen en vastmaken aan het raster  

**Visualisaties**

- Opties voor formatteren van lijndiagrampunten 

**Modelleren**

- Verbeterde metagegevens van gegevensset
- Prestatieverbeteringen voor IF- en SWITCH-functies
- Ondersteuning voor financiële Excel-functies
- Modelweergave ingeschakeld voor liveverbinding
- Updates voor de Modelweergave 

**Gegevensvoorbereiding**

- Automatische tabeldetectie vanuit Excel-bestanden  
- Automatische tabeldetectie vanuit JSON-bestanden  
- Globale optie voor het uitschakelen van automatische typedetectie 

**Overige**  

- Gegevensbron exporteren naar PBIDS in Power BI Desktop
- Welkomstscherm op bureaublad sluiten 

### <a name="power-bi-report-server"></a>Power BI Report Server

**De verbindingsreeksen voor gegevensbronnen wijzigen in Power BI-rapporten met PowerShell**

In de oktoberrelease van Power BI Report Server schakelen we de mogelijkheid in om verbindingen bij te werken voor Power BI rapporten voor DirectQuery en Refresh. Deze mogelijkheid is ook een belang rijke wijziging in de manier waarop u deze in eerdere releases kunt instellen. Raadpleeg [De verbindingsreeksen voor gegevensbronnen wijzigen in Power BI-rapporten met PowerShell - Power BI Report Server](connect-data-source-apis.md) voor meer informatie. 

## <a name="may-2020"></a>Mei 2020

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop voor Power BI Report Server

Tot de hoogtepunten van deze update behoren de hiërarchische slicer- en ontledingsstructuurvisuals en querydiagnostiek. Hier volgt een volledige lijst met nieuwe en bijgewerkte functies. Zie de [blogpost van mei 2020](https://powerbi.microsoft.com/blog/power-bi-report-server-may-2020-feature-summary/) over Power BI Report Server voor meer informatie. 

#### <a name="reporting"></a>Rapportage

- Hiërarchische slicer
- Nieuwe actietypen voor knoppen:

    - Paginanavigatie
    - Analyseren

- Knoppen ondersteunen nu opvullen van afbeeldingen
- Meerdere kolommen sorteren voor tabellen
- Dubbele as voor lijndiagrammen
- Rechthoek selecteren voor visuele elementen
- Voorwaardelijke opmaak voor totalen en subtotalen in tabellen en matrix
- Dialoogvenster Thema aanpassen
- Detectie voorwaardelijke opmaak
- Uitgevouwen structuur
- Updates van filterdeelvenster:

    - Ervaring nieuw filterdeelvenster
    - Zoeken in filterdeelvenster
    
#### <a name="modeling"></a>Modellen maken

- Nieuwe DAX-functies:

    - FirstNonBlankValue
    - LastNonBlankValue
    - Coalesce

- Standaard DAX-scheidingstekens

#### <a name="visualizations"></a>Visualisaties

- Nieuwe visualisatiepictogrammen
- Visuele slagschaduwen

#### <a name="data-preparation"></a>Gegevensvoorbereiding

- Querydiagnose

#### <a name="other"></a>Overig

- Standaardsysteemreferenties voor webproxy's gebruiken

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="power-bi-visuals-api"></a>API voor Power BI-visuals

De API-versie die bij deze release wordt geleverd, is 3.2.

## <a name="january-2020"></a>Januari 2020

Zie de blogpost van januari 2020 over Power BI Report Server voor meer informatie.

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop voor Power BI Report Server

Deze release biedt veel nieuwe functies, zoals voorwaardelijke opmaak voor knoppen, verbeteringen van gegevensprofilering en meer opmaakinstellingen voor KPI's en tabelvisualisaties. Hier volgt een overzicht van de updates:

**Rapportage**

- Een tabelkolom of matrixwaarde instellen als een aangepaste URL
- Instellingen voor de visuele opmaak van KPI's
- Updates in filtervenster

**Analyse**

- Knoppen voorwaardelijk opmaken
- Meer laden voor het analyseren van inzichten
- Nieuwe DAX-functie: Kwartaal

**Gegevensvoorbereiding**

- Verbeteringen van gegevensprofilering

**Overige**

- Nieuwe bestandsindeling: .pbids
- Prestatieverbeteringen bij het uitvoeren van modelbewerkingen

**Rapportage**

*Een tabelkolom of matrixwaarde instellen als een aangepaste URL*

U kunt een tabelkolom of matrixwaarde instellen als een aangepaste URL. U vindt deze nieuwe optie onder de kaart Voorwaardelijke opmaak in het opmaakvenster.

*Instellingen voor de visuele opmaak van KPI's*

Met de release van deze maand zijn er nieuwe opmaakopties beschikbaar voor KPI's:

- Tekstopmaak van indicator (lettertypefamilie, kleur en uitlijning)
- Transparantie van trendas
- Opmaak van tekst voor doel en afstand (labeltekst, lettertypefamilie, kleur en grootte)
- Opmaak van tekst voor afstand (labeltekst, positieve richting, lettertypefamilie, kleur en grootte)
- Toevoegen van datumlabel met opmaak (lettertypefamilie, kleur en grootte)

U kunt een aantal van deze nieuwe opmaakopties voorwaardelijk opmaken:

- Tekstkleur van indicator
- Tekstkleur van doel en doelafstand
- Statuskleuren voor goed/slecht/neutraal
- Tekstkleur van datum

*Updates in filtervenster*

Als onderdeel van de algemene beschikbaarheid van de nieuwe filterervaring van de [laatste release](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane) hebben we het proces gestroomlijnd om huidige rapporten over te zetten naar het nieuwe deelvenster. Wanneer u Power BI Report Server de eerste keer opent, ziet u een dialoogvenster voor het automatisch bijwerken van het filtervenster. Deze updates omvatten ook banners in Report Server wanneer rapporten moeten worden gemigreerd naar de nieuwe ervaring.

**Analyse**

*Voorwaardelijke opmaak voor knoppen*

Deze updates voor voorwaardelijke opmaak hebben allemaal betrekking op knoppen. U kunt nu dynamisch opmaak instellen voor de volgende eigenschappen:

- Lettertypekleur van knoptekst
- Knoptekst
- Lijnkleur van pictogram
- Kleur van contour
- Opvulkleur
- Knopinfo (onder de actiekaart)

*Meer laden voor het analyseren van inzichten*

Wanneer u de functie Analyseren uitvoert om inzichten in uw gegevens te vinden, zoals Leg de toename uit, worden de machine learning-modellen slechts voor een bepaalde periode uitgevoerd zodat u binnen afzienbare tijd inzichten kunt verkrijgen. Als er veel gegevens moeten worden geanalyseerd, hebt u nu de mogelijkheid om na de eerste time-out verder te gaan met het uitvoeren van de analyse.

*Nieuwe DAX-functie: Quarter*

Deze maand hebben we een nieuwe DAX-functie, Quarter. De functie Quarter retourneert het kwartaal dat overeenkomt met een opgegeven datum.

**Gegevensvoorbereiding**

*Verbeteringen van gegevensprofilering*

Deze maand introduceren we een aantal belangrijke verbeteringen van de mogelijkheden voor gegevensprofilering in de editor van Power Query, waaronder:

- Meerdere groeperingsopties voor de visualisatie van waardedistributie in het deelvenster Kolomprofiel, specifiek op kolomtype, naast het bestaande criterium Op waarde.
- Tekst: Op tekstlengte (aantal tekens).
- Getal: Op teken (positief/negatief) en pariteit (even/oneven).
- Datum/Datum/tijd: Per jaar, maand, dag, Week van het jaar, Dag van de week, AM/PM-tijd en Uur binnen een dag.
- En meer voor andere gegevenstypen, bijvoorbeeld Logische Waar/onwaar.

*Filteropties*

Het was al mogelijk om verschillende type-specifieke groeperingscriteria te gebruiken in het deelvenster voor waardedistributie van kolomprofielen. Nu kunt u ook filteren vanuit de bijschriften voor elk van de waarden in het distributiediagram wanneer er groeperingscriteria worden toegepast. Zo kunt u vanuit het deelvenster Gegevensprofielen voor een kolom van het type Datum/Datum/tijd alle waarden uitsluiten die in een bepaalde maand vallen.

**Overige**

*Nieuwe bestandsindeling: .pbids*

Deze maand publiceren we een nieuwe bestandsindeling: .pbids. Deze indeling is bedoeld om de ervaring met Gegevens ophalen te stroomlijnen voor rapportontwerpers in uw organisatie. We adviseren dat beheerders deze bestanden maken voor veelgebruikte verbindingen.

Wanneer een maker van een rapport een PBIDS-bestand opent, vraagt Power BI Desktop om verificatie om verbinding te maken met de gegevensbron die in het bestand is opgegeven. Vervolgens selecteert de gebruiker de tabellen die in het model moeten worden geladen. De gebruiker moet wellicht ook de database selecteren als er geen is opgegeven in het bestand. Vervolgens kan de maker van het rapport beginnen met het bouwen van visualisaties.

Ga voor meer informatie en voorbeelden naar het gedeelte [Gegevens ophalen met behulp van PBIDS-bestanden](../connect-data/desktop-data-sources.md#using-pbids-files-to-get-data) van het artikel Gegevensbronnen in Power BI Desktop.

*Prestatieverbeteringen bij het uitvoeren van modelbewerkingen*

We hebben de prestaties verbeterd van de Analysis Services-engine om modelbewerkingen te versnellen, zoals het toevoegen van metingen of berekende kolommen en het maken van relaties. De mate van verbetering die u ziet, is afhankelijk van het model. We hebben echter voor sommige klanten 20x betere prestaties gezien voor acties zoals het openen van een bestand en het toevoegen van een meting.

Dat is alles voor de release van Power BI Report Server van januari 2020. Blijf feedback geven en vergeet niet om [te stemmen op functies die u graag wilt zien in Power BI](https://ideas.powerbi.com/forums/265200-power-bi).

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="export-to-excel-from-power-bi-reports"></a>Exporteren naar Excel vanuit Power BI-rapporten

Exporteren naar Excel vanuit een Power BI-rapport in Power BI Report Server werkt nu op dezelfde manier als het exporteren naar Excel vanuit een Power BI-rapport in de Power BI-service. U kunt rechtstreeks exporteren naar de indeling XLSX van Excel. De exportlimiet is 150.000 rijen.

#### <a name="azure-sql-managed-instance-support"></a>Ondersteuning van Azure SQL Managed Instance

U kunt nu een databasecatalogus hosten die wordt gebruikt voor Power BI Report Server in een Azure SQL Managed Instance (MI) die wordt gehost op een VM of in uw datacenter. De ondersteuning is beperkt tot het gebruik van databasereferenties voor de verbinding met SQL MI.

#### <a name="power-bi-premium-dataset-support"></a>Ondersteuning van Power BI Premium-gegevenssets

U kunt verbinding maken met Power BI-gegevenssets met behulp van Microsoft Report Builder of SQL Server Data Tools (SSDT). Vervolgens kunt u deze rapporten publiceren naar Power BI Report Server met behulp van SQL Server Analysis Services-connectiviteit. Gebruikers moeten een opgeslagen Windows-gebruikersnaam en -wachtwoord gebruiken om het scenario mogelijk te maken.

#### <a name="alttext-alternative-text-support-for-report-elements"></a>Ondersteuning voor AltText (alternatieve tekst) voor rapportelementen

Bij het ontwerpen van rapporten kunt u knopinfo gebruiken om voor elk element in het rapport tekst op te geven. Deze knopinfo wordt gebruikt door schermlezertechnologieën.

#### <a name="azure-active-directory-application-proxy-support"></a>Ondersteuning van Azure Active Directory-toepassingsproxy

Met de Azure Active Directory-toepassingsproxy hoeft u niet meer uw eigen webtoepassingsproxy te beheren om veilige toegang via het web of mobiele apps toe te staan. Zie [Externe toegang tot on-premises toepassingen via de toepassingsproxy van Azure Active Directory](/azure/active-directory/manage-apps/application-proxy) voor meer informatie.

#### <a name="custom-headers"></a>Aangepaste headers

U kunt nu header-waarden instellen voor alle URL's die overeenkomen met het opgegeven regex-patroon. Gebruikers kunnen de aangepaste header-waarde bijwerken met geldige XML om header-waarden in te stellen voor geselecteerde aanvraag-URL's. Beheerders kunnen een willekeurig aantal headers toevoegen aan de XML. Zie [CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders) (Aangepaste headers) in het artikel **Server Properties Advanced Page** (Pagina met geavanceerde servereigenschappen) voor meer informatie.

#### <a name="transparent-database-encryption"></a>Transparent Data Encryption

Power BI Report Server ondersteunt nu transparante databaseversleuteling (Transparent Data Encryption of TDE) voor de Power BI Report Server-catalogusdatabase voor de edities Enterprise en Standard.

#### <a name="power-bi-visuals-api"></a>API voor Power BI-visuals

De API-versie die bij deze release wordt geleverd, is 2.6.0.

#### <a name="microsoft-report-builder-update"></a>Update van Microsoft Report Builder

De nieuw uitgebrachte versie van Report Builder is volledig compatibel met de versies uit 2016, 2017 en 2019 van Reporting Services. De versie is ook compatibel met alle gepubliceerde en ondersteunde versies van Power BI Report Server.

## <a name="september-2019"></a>September 2019

Zie het blogbericht [Power BI Report Server september 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) voor meer informatie over alle nieuwe functies.

De update van september 2019 voor Power BI Report Server zit vol Power BI-rapportfuncties. Hier volgen enkele hoofdpunten:

- **Filters op het niveau van de visual voor slicers** U kunt een filter op het niveau van de visual toevoegen aan slicers. Het werkt net als elk ander filter op het niveau van de visual, maar hiermee wordt alleen de slicer zelf gefilterd en geen andere visuals. Dit filter is handig om lege waarden uit te filteren of als u een maateenheidsfilter wilt gebruiken.
- **Pictogrammensets voor tabellen en matrices** Met KPI-pictogrammen kunt u regels instellen voor het weergeven van verschillende groepen pictogrammen in uw tabel en matrix, net als bij pictogrammensets in Excel.
- **Visuals groeperen** U kunt nu visuals, vormen, tekstvakken, afbeeldingen en knoppen groeperen op een rapportpagina, net als in PowerPoint. Wanneer u objecten groepeert, kunt u deze allemaal tegelijk verplaatsen en hiervan de grootte aanpassen. Groeperen maakt het gemakkelijker om in een rapport met veel objecten in verschillende lagen op elke pagina te werken.
- **Nieuwe standaardthema's** In overeenstemming met de JSON-opties voor nieuwe thema's worden de beschikbare thema's voor rapporten bijgewerkt en het standaardthema voor nieuwe rapporten gewijzigd. Het nieuwe standaardthema is beter afgestemd op de ontwerptaal van Microsoft en volgt de best practices voor het ontwerpen van visuals. 
- **Bijgewerkt ontwerp van deelvensters** We hebben veel van onze interface vernieuwd. We hebben alle deelvensters bijgewerkt: de voettekst en de weergaveschakelaar hebben een lichtere kleur gekregen, de tussenruimten zijn bijgewerkt en we hebben nieuwe pictogrammen geïntroduceerd. Het nieuwe ontwerp is de eerste stap voor het vernieuwen van de gehele interface.

Hier volgt de volledige lijst met functies. 

### <a name="reporting"></a>Rapportage

- Bijgewerkt ontwerp van deelvensters
- Filters op het niveau van visuals voor slicers
- Sorteren voor het deelvenster voor prestatieanalyse
- Knopinfo voor visuele koptekst
- Aangepaste labels voor tabel- en matrixtotalen
- Ondersteuning voor synchroniseren van slicers voor hiërarchieslicer
- Consistente tekengrootten voor visuals
- Pictogrammensets voor tabellen en matrices
- Ondersteuning voor percentages voor voorwaardelijke opmaak op basis van regels
- Nieuw filterdeelvenster is nu algemeen beschikbaar
- Ondersteuning voor gegevenskleuren bij het gebruik van een afspeelas in spreidingsdiagrammen
- Prestatieverbeteringen bij het gebruik van relatieve datum en slicers met vervolgkeuzelijst
- Groeperen van visuals
- Kleur- en tekstklassen in thema's
- Nieuwe standaardthema's

### <a name="analytics"></a>Analyse

- Tekenreeksen met aangepaste notatie
- Updates van voorwaardelijke opmaak voor opmaakopties

    - Kleuren voor achtergrond en titel van visuals
    - Kaartkleuren
    - Vulling en kleuren voor meters
    - Alternatieve tekst
    - Randkleur

- Waarschuwingen voor voorwaardelijke opmaak
- Betere detectie bij detailanalyses
- Nieuwe DAX-expressies: REMOVEFILTERS en CONVERT
- Nieuwe DAX-vergelijkingsoperator: ==

### <a name="data-preparation"></a>Gegevensvoorbereiding

- Verbeteringen aan M Intellisense
- Nieuwe transformatie: Kolom splitsen op posities
- Kopiëren naar het klembord vanuit gegevensprofilering


## <a name="may-2019"></a>Mei 2019

### <a name="power-bi-desktop-for-power-bi-report-server"></a>Power BI Desktop voor Power BI Report Server

Zie het blogbericht [Power BI Report Server mei 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) voor meer informatie over alle nieuwe functies.

Hier volgen enkele hoofdpunten van deze versie:

#### <a name="performance-analyzer"></a>Performance Analyzer 

Als uw rapport langzamer dan verwacht wordt uitgevoerd, gebruikt u de Performance Analyzer in Power BI Desktop. Wanneer u deze functie start, wordt er een logboekbestand gemaakt met informatie over elke actie die u in het rapport uitvoert. Lees meer over de [Performance Analyzer](../create-reports/desktop-performance-analyzer.md).

#### <a name="new-modeling-view"></a>Nieuwe weergave voor modellen maken

In de nieuwe weergave voor modellen maken in Power BI Desktop kunt u complexe gegevenssets met veel tabellen bekijken en gebruiken. De belangrijkste kenmerken zijn meerdere diagramlay-outs en het bulksgewijs bewerken van kolommen, metingen en tabellen. Meer informatie over de [weergave voor modellen maken](../transform-model/desktop-modeling-view.md).

#### <a name="accessible-visual-interaction"></a>Interactie met toegankelijke visual

U hebt nu toegang tot gegevenspunten op veel van de ingebouwde visuals door middel van toetsenbordnavigatie. Meer informatie over [toegankelijkheid in Power BI-rapporten](../create-reports/desktop-accessibility-overview.md).

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>Titels voor voorwaardelijke opmaak en web-URL-acties

Power BI-rapporten zijn interactief. Het is logisch dat titels in een rapport dynamisch zijn, zodat ze de huidige status van het rapport weergeven. U kunt dezelfde expressieafhankelijke opmaak gebruiken om de URL's van uw knoppen, vormen en afbeeldingen dynamisch te maken. Meer informatie over [expressieafhankelijke titels](../create-reports/desktop-conditional-format-visual-titles.md).

#### <a name="cross-highlight-by-axis-labels"></a>Kruislings markeren door aslabels

Selecteer de ascategorielabels in een visual om de andere elementen op een pagina kruislings te markeren, net zoals u de gegevenspunten in een visual selecteert. Meer informatie over [kruislings markeren](../create-reports/power-bi-reports-filters-and-highlighting.md#cross-filter-and-cross-highlight-visuals).

#### <a name="all-the-new-features"></a>Alle nieuwe functies

Hier volgt een lijst met alle nieuwe functies:

#### <a name="reporting"></a>Rapportage

- Kruislings markeren op één punt in lijndiagrammen 
- Tekstterugloop in titels 
- Standaardinteractie van visual bijgewerkt met kruislings filteren
- Afgeronde hoeken voor randen van visual 
- Slicer waarbij slechts één waarde wordt geselecteerd  
- Heatmap-ondersteuning voor Bing-kaarten  
- Kruislings markeren door aslabels  
- Standaardopmaak voor knopinfo  
- Ondersteuning voor statische web-URL's voor knoppen, vormen en afbeeldingen  
- Opties voor pagina-uitlijning   
- Verbeterde selectievensters  
- Interactie met toegankelijke visual  
- Voorwaardelijke opmaak voor titels van visuals  
- Voorwaardelijke opmaak voor web-URL-acties voor knoppen, vormen en afbeeldingen
- Performance Analyzer-deelvenster
- Toetsenbordnavigatie voor tabellen en matrices
- Positiebeheer voor gegevenslabels van lijnen
- Beheer van tekengrootte voor visual met KPI-indicator

#### <a name="analytics"></a>Analyse

- Datums als een hiërarchie weergeven nu algemeen beschikbaar  

#### <a name="modeling"></a>Modellen maken

- Nieuwe weergave voor modellen maken nu algemeen beschikbaar
- Nieuwe DAX-functies
- Update met de DAX-functie ALLSELECTED
- Tabellen met automatische datum uitschakelen voor nieuwe rapporten

### <a name="power-bi-report-server"></a>Power BI Report Server

#### <a name="support-for-trusted-visuals"></a>Ondersteuning voor vertrouwde visuals

Er is ondersteuning toegevoegd voor vertrouwde visuals voor Power BI Report Server. Momenteel ondersteunen we Mapbox- en PowerOn-visuals. (ESRI, Visio en PowerApps worden niet ondersteund voor deze versie.)

#### <a name="improved-security-features"></a>Verbeterde beveiligingsfuncties

**RestrictedResourceMimeTypeForUpload**, die beheerders kunnen gebruiken om een lijst met door komma's gescheiden waarden op te geven voor uitgesloten MIME-typen, bijvoorbeeld text/html.

## <a name="january-2019"></a>Januari 2019

Ondersteuning voor deze functies in Power BI-rapporten:

[**Beveiliging op rijniveau**](row-level-security-report-server.md) Het instellen van beveiliging op rijniveau (RLS) met Power BI Report Server kan toegang tot gegevens beperken voor bepaalde gebruikers. Filters beperken de toegang tot gegevens op rijniveau en u kunt filters definiëren in rollen.

[**Uitvouwen of samenvouwen op rijkoppen van matrix**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) We hebben de mogelijkheid toegevoegd om afzonderlijke rijkoppen uit te vouwen en samen te vouwen, een van de meest aangevraagde visuele functies.

[**Kopiëren en plakken tussen .pbix-bestanden**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) U kunt visuele elementen kopiëren tussen .pbix-bestanden, vanuit het contextmenu van het visuele element of met de standaardsneltoets Ctrl + C, en deze elementen in een ander rapport plakken met Ctrl + V.

[**Slimme uitlijningshulplijnen**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) U ziet slimme uitlijningshulplijnen wanneer u objecten verplaatst op de rapportpagina, net als in PowerPoint. De hulplijnen helpen om alles op de pagina uit te lijnen. U ziet de slimme hulplijnen telkens wanneer u iets sleept of vergroot/verkleint op de pagina. Wanneer u een object in de buurt van een ander plaatst, klikt het automatisch vast op een positie die is uitgelijnd met het andere object.

**Toegankelijkheidsfuncties** Te veel toegankelijkheidsfuncties om op te noemen: een voorbeeld is [toegankelijkheidsondersteuning voor het lijstdeelvenster met velden](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList). Het lijstdeelvenster met velden is volledig toegankelijk. U kunt navigeren in het deelvenster met behulp van alleen het toetsenbord en een schermlezer en het contextmenu gebruiken om velden toe te voegen aan de rapportpagina.

#### <a name="power-bi-visuals"></a>Power BI-visuals

- De API-versie die bij deze release wordt geleverd, is 2.3.0.

### <a name="administrator-settings"></a>Beheerdersinstellingen

Beheerders kunnen de volgende eigenschappen instellen in geavanceerde SSMS-eigenschappen voor de serverfarm:

**AllowedResourceExtensionsForUpload** Extensies van resources instellen die kunnen worden geüpload naar de rapportserver. Extensies voor ingebouwde bestandstypen als &ast;.rdl en &ast;.pbix hoeven niet te worden opgenomen. Standaard is '&ast;, &ast;.xml, &ast;.xsd, &ast;.xsl, &ast;.png, &ast;.gif, &ast;.jpg, &ast;.tif, &ast;.jpeg, &ast;.tiff, &ast;.bmp, &ast;.pdf, &ast;.svg, &ast;.rtf, &ast;.txt, &ast;.doc, &ast;.docx, &ast;.pps, &ast;.ppt, &ast;.pptx'. 

**SupportedHyperlinkSchemes** Stelt een door komma's gescheiden lijst met de URI-schema's in die kan worden gedefinieerd op de Hyperlink-acties die kunnen worden weergegeven of '&ast;' om alle hyperlink-schema's in te schakelen. Door bijvoorbeeld 'http, https' in te stellen, worden hyperlinks mogelijk naar 'https://www. contoso.com', maar worden hyperlinks naar 'mailto:bill@contoso.com' of 'javascript:window.open ('www.contoso.com', '_blank')' verwijderd. De standaardwaarde is '&ast;'.

## <a name="august-2018"></a>Augustus 2018

In augustus 2018 ziet u veel nieuwe functies die zijn toegevoegd aan de versie van Power BI Desktop voor Power BI Report Server. Hieronder worden ze per gebied weergegeven:

- [Rapportage](#reporting)
- [Analyse](#analytics)
- [Modellen maken](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>Hoofdpunten van de release van augustus 2018

Uit de lange lijst met nieuwe functies volgen hier de interessantste functies. Zie dit [blogbericht](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/) voor meer informatie.

#### <a name="report-theming"></a>Rapportthema's

De release van augustus 2018 van Power BI Report Server bevat de mogelijkheid om rapporten thema's te geven: u kunt hiermee uw volledige rapport bijvoorbeeld snel de huisstijl geven. Wanneer u een thema importeert, worden alle grafieken automatisch bijgewerkt met de themakleuren. Via het kleurenpalet hebt u toegang tot de themakleuren. Thema's kunnen worden geüpload via de knop **Thema wisselen** > **Thema importeren**.

Een themabestand heeft de JSON-indeling en bevat alle kleuren die u in uw rapport wilt gebruiken en informatie over de gewenste opmaak van visuals.
Hieronder ziet u een eenvoudig JSON-voorbeeldthema waarmee alleen de standaardkleuren van het rapport worden bijgewerkt:

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>Voorwaardelijke opmaak op basis van een ander veld

Voorwaardelijke opmaak is enorm verbeterd dankzij onder andere de mogelijkheid om kolommen op te laten maken op basis van een ander veld in uw model.

#### <a name="conditional-formatting-by-values"></a>Voorwaardelijke opmaak op basis van waarden

U kunt nu ook de nieuwe optie **Opmaken op basis van veld** gebruiken voor voorwaardelijke opmaak. Met de optie Opmaken op basis van veld kunt u een meting of kolom gebruiken voor het opgeven van een kleur (via een hexadecimale code of een naam) en deze kleur vervolgens toepassen op de achtergrond of het lettertype.

#### <a name="report-page-tooltips"></a>Knopinfo rapportpagina

De knopinfofunctie voor rapportpagina's is vanaf de update van augustus 2018 van Power BI Report Server beschikbaar. Met deze functie kunt u een rapportpagina ontwerpen die als aangepaste knopinfo wordt gebruikt voor andere visuals in uw rapport.

#### <a name="log-axis-improvements"></a>Verbeteringen aan de assen met logaritmische schaal

De assen met logaritmische schaal van cartesische grafieken zijn aanzienlijk verbeterd. U kunt nu de logaritmische schaal selecteren voor de numerieke as van een cartesische grafiek (ook combinatiegrafieken) als u beschikt over gegevens die volledig positief of volledig negatief zijn.

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO DirectQuery

Er is nu SAP HANA SSO DirectQuery-ondersteuning met Kerberos beschikbaar voor Power BI-rapporten.

>[!Note]
>Dit scenario wordt alleen ondersteund als SAP HANA wordt behandeld als relationele gegevensbron voor rapporten die u in Power BI Desktop hebt gemaakt.  Als u dit in Power BI Desktop wilt inschakelen, gaat u naar het menu DirectQuery > Opties, schakelt u de optie SAP HANA behandelen als een relationele bron in en klikt u op OK.

#### <a name="power-bi-visuals"></a>Power BI-visuals

- De API-versie die bij deze release wordt geleverd, is 1.13.0.

- Er kan nu een oudere versie van de functie voor Power BI-visuals worden gebruikt die compatibel is met de huidige versie van de server-API (indien beschikbaar).

### <a name="reporting"></a>Rapportage 

- [Rapportthema's](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [Knoppen om acties te starten](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [Regelstijlen combinatiegrafiek](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [Verbeterde standaardsortering voor visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [Numerieke slicer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [Geavanceerde synchronisatiemogelijkheden slicer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [Verbeteringen aan de assen met logaritmische schaal](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [Gegevenslabelopties voor trechterdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [Streekdikte van de regel ingesteld op nul](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [Ondersteuning voor hoge contrasten in rapporten](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [Instellen van straal van ringdiagram](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [Instellen van positie van labels voor cirkel- en ringdiagrammen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [Gegevenslabels afzonderlijk voor elke meting opmaken in een combinatiegrafiek](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [Nieuwe koptekst voor visuals met meer flexibiliteit en opmaak](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [Achtergrond opmaken](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [Knopinfo voor tabellen en matrices](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [Knopinfo uitschakelen voor visuals](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [Toegankelijkheid van slicers](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [Verbeteringen van opmaakvenster](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [Ondersteuning van trapvormige lijnen voor lijn- en combinatiegrafieken](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [Verbetering van sorteerbewerkingen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [Rapporten afdrukken via Exporteren naar PDF (in Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [Bladwijzergroepen maken](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [Aanpassing van de slicer](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [Knopinfo rapportpagina](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>Analyse

- [Nieuwe DAX-functie: COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [Drillthrough voor metingen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [Voorwaardelijke opmaak op basis van een ander veld](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [Voorwaardelijke opmaak op basis van waarden](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>Modellen maken

- [Filteren en sorteren in de gegevensweergave](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [Verbeterde opmaak landinstellingen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [Gegevenscategorieën voor metingen](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [Statistische functies van DAX](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>Mei 2018

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>Power BI mobiele iOS-apps op afstand configureren voor rapportservers

Als IT-beheerder kunt u nu het MDM-hulpprogramma van uw organisatie gebruiken om op afstand toegang via de Power BI mobiele iOS-app tot een rapportserver te configureren. Zie [Toegang via Power BI mobiele iOS-apps tot rapportserver op afstand configureren](configure-powerbi-mobile-apps-remote.md) voor meer informatie.

## <a name="march-2018"></a>Maart 2018

In maart 2018 ziet u veel nieuwe functies die zijn toegevoegd aan de versie van Power BI Desktop voor Power BI Report Server. Hieronder worden ze per gebied weergegeven:

- [Visuals](#visuals-updates)
- [Rapportage](#reporting)
- [Analyse](#analytics)
- [Prestaties](#performance)
- [Rapportserver](#report-server)
- [Overige](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>Hoofdpunten van de release van maart 2018

Uit de lange lijst met nieuwe functies volgen hier de interessantste functies.

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[Voorwaardelijke opmaak op basis van regels voor tabel en matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

Maak op basis van specifieke bedrijfslogica regels die aan de hand van voorwaarden de achtergrondkleur of tekstkleur in de tabel of matrix bepalen.

#### <a name="show-and-hide-pages"></a>[Pagina's weergeven en verbergen](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

U wilt dat lezers toegang hebben tot uw rapport, maar sommige pagina's zijn niet voltooid. Nu kunt u deze verbergen totdat ze klaar zijn. U kunt de pagina's ook in de normale navigatie verbergen en de lezers naar de pagina laten gaan via bladwijzers of drillthrough.

#### <a name="bookmarking"></a>[Bladwijzers gebruiken](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

Maak bladwijzers en vertel een verhaal met de gegevens in uw rapport.

- [Kruislings markeren voor bladwijzers](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting): bladwijzers behouden de kruislings gemarkeerde status van de rapportpagina en geven deze weer op het moment dat u de bladwijzer maakt.
- [Meer flexibiliteit met bladwijzers](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility): bladwijzers weerspiegelen de eigenschappen die u instelt in het rapport en zijn alleen van invloed op de visuals die u kiest.

#### <a name="multi-select-data-points-across-multiple-charts"></a>[Meervoudige selectie van gegevenspunten in meerdere diagrammen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

Selecteer meerdere gegevenspunten in verschillende diagrammen en pas kruislings markeren toe op de hele pagina.

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[Slicers op meerdere pagina's van een rapport synchroniseren](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

Een slicer kan van toepassing zijn op één, twee of meer pagina's in een rapport.

#### <a name="quick-measures"></a>[Snelle metingen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

Maak nieuwe metingen op basis van bestaande metingen en numerieke kolommen in een tabel.

#### <a name="drilling-down-filters-other-visuals"></a>[Bij inzoomen andere visuals filteren](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

Wanneer u in een bepaalde categorie op één visual inzoomt, kunnen daarbij alle visuals op de pagina worden gefilterd op diezelfde categorie.

### <a name="visuals-updates"></a>Updates voor visuals

- [Celuitlijning voor tabel en matrix](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [Weergave-eenheden en precisiebeheer voor tabel- en matrixkolommen](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [Overloop van gegevenslabels voor staaf- en kolomdiagrammen](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [De achtergrondkleur van gegevenslabels regelen voor visuals met cartesische grafieken en kaarten](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [Regelen van de opvulling voor staven/kolommen](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [Het gebied vergroten dat wordt gebruikt voor de aslabels in grafieken](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [Visual met spreidingsdiagram uit x- en y-asgroeperingen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [High-densitysampling voor kaarten op basis van de breedte- en lengtegraad](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [Responsieve slicers](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [Een ankerdatum toevoegen voor een slicer voor relatieve datums](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>Rapportage

- [De koptekst van een visual uitschakelen in de leesmodus voor een rapport](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [Rapportopties voor trage gegevensbronnen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [Verbeterde plaatsing van standaardvisuals](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [De rangschikking van visuele elementen regelen via het selectievenster](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [Objecten in het rapport vergrendelen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [Het opmaak- en analysevenster doorzoeken](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [Het deelvenster Veldeigenschappen en veldbeschrijvingen](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>Analyse

- [UTCNOW() en UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [Aangepaste datumtabel markeren](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [Bij inzoomen andere visuals filteren](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [Opmaak op celniveau voor multidimensionale AS-modellen voor kaarten met meerdere rijen](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>Prestaties

- [Prestatieverbeteringen bij het filteren](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [Prestatieverbeteringen bij DirectQuery](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [Prestatieverbeteringen bij het openen en opslaan](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [Verbeteringen bij Items zonder gegevens weergeven](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>Rapportserver

#### <a name="export-to-accessible-pdf"></a>Exporteren naar toegankelijke PDF

Wanneer u een gepagineerd (RDL) rapport naar PDF exporteert, kunt u nu een toegankelijk/getagd PDF-bestand gebruiken. Het is groter, maar met schermlezers en andere ondersteunende technologieën is het eenvoudiger te lezen en kan hierin gemakkelijker worden genavigeerd. U kunt de toegankelijke PDF inschakelen door de apparaatgegevensinstelling **AccessiblePDF** in te stellen op **Waar**. Zie [PDF-apparaatgegevensinstellingen](/sql/reporting-services/pdf-device-information-settings) en [Apparaatgegevensinstellingen wijzigen](/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings).

### <a name="other-improvements"></a>Andere verbeteringen

- [Verbeteringen bij Kolom toevoegen uit voorbeelden](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [Snelkoppeling voor Consulting Services](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [Verbeterde foutrapportage](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [Fouten bekijken die zich eerder hebben voorgedaan](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>Oktober 2017

### <a name="power-bi-report-data-sources"></a>Power BI-rapportgegevensbronnen

Voor Power BI-rapporten in Power BI Report Server kan verbinding worden gemaakt met een groot aantal verschillende gegevensbronnen. U kunt gegevens importeren en vernieuwing van gegevens plannen, of rechtstreeks met DirectQuery of een liveverbinding met SQL Server Analysis Services een query op de gegevens uitvoeren. Zie de lijst met gegevensbronnen die geplande vernieuwing ondersteunen en bronnen die DirectQuery ondersteunen in 'Power BI-rapportgegevensbronnen in Power BI Report Server'.

### <a name="scheduled-data-refresh-for-imported-data"></a>Geplande gegevensvernieuwing voor geïmporteerde gegevens

In Power BI Report Server kunt u geplande gegevensvernieuwing instellen om gegevens up-to-date te houden in Power BI-rapporten met een ingesloten model in plaats van met een liveverbinding of DirectQuery. Met een ingesloten model importeert u de gegevens, wat betekent dat deze worden losgekoppeld van de oorspronkelijke gegevensbron. Het model moet worden bijgewerkt om de gegevens actueel te houden. Geplande vernieuwing is de aangewezen manier om dat te doen. Lees meer over geplande vernieuwing voor Power BI-rapporten in Power BI Report Server.

### <a name="editing-power-bi-reports-from-the-server"></a>Power BI-rapporten bewerken vanaf de server

U kunt Power BI-rapportbestanden (.pbix) openen en bewerken vanaf de server, maar u krijgt het oorspronkelijke bestand terug dat u hebt geüpload. **Als de gegevens zijn vernieuwd door de server, worden de gegevens niet bijgewerkt wanneer u het bestand voor het eerst opent**. U moet ze lokaal handmatig vernieuwen om de wijziging te zien.

### <a name="large-file-uploaddownload"></a>Grote bestanden uploaden/downloaden

U kunt bestanden van maximaal 2 GB uploaden, hoewel deze limiet standaard is ingesteld op 1 GB in de Report Server-instellingen in SQL Server Management Studio (SSMS).  Deze bestanden worden opgeslagen in de database, net als voor SharePoint. Er is geen speciale configuratie vereist voor de SQL Server-catalogus.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Toegang tot gedeelde gegevenssets als OData-feeds

Met een OData-feed hebt u toegang tot gedeelde gegevenssets van Power BI Desktop. Zie [Gedeelde gegevenssets openen als OData-feeds in Power BI Report Server](access-dataset-odata.md)voor meer informatie.

### <a name="scale-out"></a>Uitschalen

Deze versie biedt ondersteuning voor uitschalen. Gebruik voor de beste ervaring een load balancer en stel serveraffiniteit in. Het scenario is nog niet geoptimaliseerd voor uitschalen, waardoor modellen mogelijk op meerdere knooppunten worden gerepliceerd. Het scenario werkt zonder de Network Load Balancer en tijdelijke sessies. U ziet echter niet alleen een overmatig gebruik van geheugen op knooppunten wanneer het model N keer wordt geladen, maar de prestaties tussen verbindingen worden trager wanneer het model wordt gestreamd en een nieuw knooppunt aantreft tussen aanvragen.  

### <a name="administrator-settings"></a>Beheerdersinstellingen

Beheerders kunnen de volgende eigenschappen instellen in geavanceerde SSMS-eigenschappen voor de serverfarm:

- EnableCustomVisuals: Waar/onwaar
- EnablePowerBIReportEmbeddedModels: Waar/onwaar
- EnablePowerBIReportExportData: Waar/onwaar
- MaxFileSizeMb: de standaardwaarde is 1000
- ModelCleanupCycleMinutes: hoe vaak er wordt gecontroleerd om modellen uit het geheugen te verwijderen
- ModelExpirationMinutes: hoe lang het duurt tot het model is verlopen en wordt verwijderd, op basis van de laatste keer dat het is gebruikt
- ScheduleRefreshTimeoutMinutes: hoe lang het vernieuwen van gegevens kan duren voor een model. De standaardwaarde is twee uur.  Er is geen vaste bovengrens.

**Configuratiebestand rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>API voor ontwikkelaars

De API voor ontwikkelaars (REST API) die is geïntroduceerd voor SSRS 2017, is uitgebreid voor Power BI Report Server voor gebruik met zowel Excel-bestanden als .pbix-bestanden. Een mogelijk gebruiksvoorbeeld is het via programmacode downloaden van bestanden, het vernieuwen ervan en het vervolgens opnieuw publiceren. Dit is bijvoorbeeld de enige manier waarop Excel-werkmappen met PowerPivot-modellen kunnen worden vernieuwd.

Er is een nieuwe afzonderlijke API voor grote bestanden, die wordt bijgewerkt in de Power BI Report Server-versie van Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) en het geheugengebruik van Power BI Report Server

Power BI Report Server fungeert intern nu als host voor SQL Server Analysis Services (SSAS). Dit is niet specifiek voor geplande vernieuwing. Door SSAS te hosten, kunt u het geheugengebruik van de rapportserver aanzienlijk uitbreiden. Het configuratiebestand AS.ini is beschikbaar op de serverknooppunten. Als u bekend bent met SSAS, kunt u dus de instellingen bijwerken, inclusief de maximale geheugenlimiet en schijfopslag in de cache enzovoort. Zie [Servereigenschappen in Analysis Services](/sql/analysis-services/server-properties/server-properties-in-analysis-services) voor meer informatie.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Excel-werkmappen weergeven en ermee werken

Excel en Power BI bevatten een portfolio met hulpprogramma's die uniek is in de branche. Dankzij deze twee programma’s kunnen bedrijfsanalisten eenvoudiger hun gegevens verzamelen, vormgeven, analyseren en op een visuele manier verkennen. Zakelijke gebruikers kunnen nu niet alleen Power BI-rapporten weergeven in de webportal, maar ook hetzelfde doen met Excel-werkmappen in Power BI Report Server. Zo hebben ze één locatie waar ze hun selfservice Microsoft BI-inhoud kunnen publiceren en weergeven.

We hebben een [overzicht gepubliceerd hoe u Office Online Server (OOS) toevoegt aan de voorbeeldomgeving van uw Power BI Report Server](excel-oos.md). Klanten met een Volumelicentie-account kunnen OOS kosteloos downloaden uit het Volume License Servicing Center. Ze beschikken dan over alleen-lezenfunctionaliteit. Als de functionaliteit eenmaal is geconfigureerd, kunnen gebruikers Excel-werkmappen weergeven en werken met werkmappen die:

- Geen afhankelijkheden van de externe gegevensbron hebben
- Een liveverbinding hebben met een externe SQL Server Analysis Services-gegevensbron
- Een PowerPivot-gegevensmodel hebben

### <a name="support-for-new-table-and-matrix-visuals"></a>Ondersteuning voor nieuwe visuele tabel- of matrixelementen

Power BI Report Server ondersteunt nu de nieuwe visuele Power BI-tabel en -matrixelementen. Als u rapporten wilt maken met deze visuele elementen, hebt u een bijgewerkte versie van Power BI Desktop nodig voor de release van oktober 2017. Deze functie kan niet worden geïnstalleerd naast de Power BI Desktop-release (juni 2017). Selecteer op de [downloadpagina van Power BI Report Server](https://powerbi.microsoft.com/report-server/)**Geavanceerde downloadinstellingen** voor de meest recente versie van Power BI Desktop.

## <a name="june-2017"></a>Juni 2017

- Power BI Report Server algemeen beschikbaar gesteld (GA).

## <a name="may-2017"></a>Mei 2017

- Voorbeeld van Power BI Report Server beschikbaar gesteld
- Mogelijkheid om Power BI-rapporten on-premises te publiceren
  - ondersteuning voor Power BI-visuals
  - Alleen ondersteuning voor **live-verbindingen voor Analysis Services*, er volgen meer gegevensbronnen.
  - App Power BI - Mobiel bijgewerkt om Power BI-rapporten weer te geven die worden gehost in Power BI Report Server
- Verbeterde samenwerking in rapporten met opmerkingen

## <a name="next-steps"></a>Volgende stappen

Raadpleeg deze bronnen om op de hoogte te blijven van nieuwe functies in Power BI Report Server.

- [Microsoft Power BI-blog](https://powerbi.microsoft.com/blog/)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
