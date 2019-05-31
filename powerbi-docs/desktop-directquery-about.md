---
title: DirectQuery gebruiken in Power BI
description: Informatie over het gebruiken van DirectQuery met Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7f0fb4bfaad8d7035c5b6ed7a6db90c5303139ad
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61308505"
---
# <a name="using-directquery-in-power-bi"></a>DirectQuery gebruiken in Power BI
U kunt verbinding maken met allerlei verschillende gegevensbronnen wanneer u **Power BI Desktop** of de **Power BI-service** gebruikt; deze verbindingen kunt u op verschillende manieren tot stand brengen. U kunt gegevens *importeren* in Power BI, wat de meest voorkomende manier is om gegevens te verkrijgen, of u kunt rechtstreeks verbinding maken met gegevens in de oorspronkelijke opslagplaats, wat **DirectQuery** wordt genoemd. In dit artikel vindt u informatie over **DirectQuery** en de bijbehorende mogelijkheden:

* Verschillende verbindingsmogelijkheden voor DirectQuery
* Richtlijnen voor wanneer u beter DirectQuery kunt gebruiken in plaats van importeren
* Nadelen van het gebruik van DirectQuery
* Aanbevolen procedure voor het gebruik van DirectQuery

Hanteer de volgende richtlijnen om te kiezen tussen importeren en DirectQuery:

* Indien mogelijk moet u gegevens **importeren** in Power BI. U kunt bij het importeren gebruikmaken van de geavanceerde en krachtige query-engine van Power BI en u hebt op een zeer interactieve en volledig functionele manier toegang tot uw gegevens.
* Als uw doelstellingen niet kunnen worden gerealiseerd door gegevens te importeren, kunt u overwegen **DirectQuery** te gebruiken. Als de gegevens bijvoorbeeld vaak worden gewijzigd, en rapporten de meest recente gegevens moeten bevatten, is DirectQuery waarschijnlijk de beste keuze. In de meeste gevallen kunt u DirectQuery echter alleen gebruiken als de onderliggende gegevensbron interactieve query's kan aanbieden (minder dan vijf seconden) voor een standaard statistische query en overweg kan met de querybelasting die wordt gegenereerd. Daarnaast moet de lijst met beperkingen voor het gebruik van DirectQuery goed worden doorgenomen.

De set met mogelijkheden die door Power BI wordt aangeboden voor beide verbindingsmodi, importeren en DirectQuery, zal in de loop der tijd veranderen. Denk hierbij aan meer flexibiliteit bij het gebruik van geïmporteerde gegevens, zodat importeren in meer situaties kan worden gebruikt, evenals het wegnemen van enkele nadelen van het gebruik van DirectQuery. Ongeacht deze verbeteringen, zullen de prestaties van de onderliggende gegevensbron altijd de belangrijkste overweging blijven bij het gebruik DirectQuery. Als de onderliggende gegevensbron traag is, blijft het onwerkbaar om DirectQuery te gebruiken met die bron.

In dit artikel bevat informatie over DirectQuery met Power BI en geen SQL Server Analysis Services. DirectQuery is ook een functie van **SQL Server Analysis Services**, en hoewel veel van de hieronder beschreven informatie in beide scenario's van toepassing is, zijn er ook belangrijke verschillen. Meer informatie over het gebruik van DirectQuery met SQL Server Analysis Services vindt u [in dit Engelstalige document](http://download.microsoft.com/download/F/6/F/F6FBC1FC-F956-49A1-80CD-2941C3B6E417/DirectQuery%20in%20Analysis%20Services%20-%20Whitepaper.pdf).  

In dit artikel richten we ons op de aanbevolen workflow voor DirectQuery, waar het rapport wordt gemaakt in **Power BI Desktop**, maar er wordt ook aandacht besteed aan het rechtstreeks verbinding maken in de **Power BI-service**.

## <a name="power-bi-connectivity-modes"></a>Verbindingsmodi van Power BI
Power BI kan verbinding maken met een groot aantal verschillende gegevensbronnen, waaronder:

* Onlineservices (Salesforce, Dynamics 365, enzovoort)
* Databases (SQL Server, Access, Amazon Redshift, enzovoort)
* Eenvoudige bestanden (Excel, JSON, enzovoort)
* Andere gegevensbronnen (Spark, websites, Microsoft Exchange, enzovoort)

Voor deze bronnen is het meestal mogelijk de gegevens te importeren in Power BI. Voor sommige kan er ook verbinding worden gemaakt via DirectQuery. In het artikel [Gegevensbronnen die worden ondersteund door DirectQuery](desktop-directquery-data-sources.md) leest u welke bronnen ondersteuning bieden voor DirectQuery. In de toekomst zullen meer bronnen geschikt worden gemaakt voor DirectQuery, met name bronnen die naar verwachting goede prestaties voor interactieve query's kunnen bieden.

**SQL Server Analysis Services** is een speciaal geval. Wanneer u verbinding maakt met SQL Server Analysis Services, kunt u ervoor kiezen om de gegevens importeren of u kunt een *live-verbinding* gebruiken.  Het gebruik van een live-verbinding is vergelijkbaar met DirectQuery, omdat er in beide scenario's geen gegevens worden geïmporteerd en er altijd een query wordt uitgevoerd op de onderliggende gegevensbron om een visualisatie te vernieuwen. Een *live-verbinding* verschilt echter ook op veel andere punten en daarom wordt er een andere term (*live* versus *DirectQuery*) gebruikt.

Deze drie mogelijkheden om verbinding te maken met gegevens, **importeren**, **DirectQuery** en **live-verbinding**, worden in de volgende secties gedetailleerd beschreven.

### <a name="import-connections"></a>Importverbindingen
Wanneer u **Gegevens ophalen** in **Power BI Desktop** gebruikt om verbinding te maken met een gegevensbron zoals SQL Server, en u kiest **Importeren**, is het gedrag van die verbinding als volgt:

* Tijdens de eerste fase van **Gegevens ophalen** vormen de geselecteerde tabellen elk een query die een set gegevens retourneert (deze query's kunnen voorafgaand aan het laden van de gegevens worden bewerkt, bijvoorbeeld om filters toe te passen, de gegevens te aggregeren of verschillende tabellen samen te voegen).
* Bij het laden worden alle gegevens die zijn gedefinieerd met deze query's, geïmporteerd in de cache van Power BI.
* Bij het samenstellen van een visualisatie binnen **Power BI Desktop**, wordt er een query uitgevoerd op de geïmporteerde gegevens. De opslag in Power BI zorgt ervoor dat de query snel wordt uitgevoerd, waardoor alle wijzigingen in de visualisatie direct zichtbaar zijn.
* Eventuele wijzigingen in de onderliggende gegevens worden niet doorgevoerd in visualisaties. Het is nodig om *vernieuwen*kiezen om de gegevens worden geïmporteerd.
* Bij het publiceren van het rapport (het PBIX-bestand) naar de **Power BI-service**, wordt er een gegevensset gemaakt die wordt geüpload naar de Power BI-service.  De geïmporteerde gegevens maken deel uit van deze dataset. Vervolgens is het mogelijk voor het instellen van geplande vernieuwing van alle gegevens, bijvoorbeeld, importeer de gegevens elke dag. Afhankelijk van de locatie van de oorspronkelijke gegevensbron, kan het nodig zijn om een On-premises gegevensgateway te configureren.
* Wanneer er een bestaand rapport wordt geopend in de **Power BI-service**, of bij het ontwerpen van een nieuw rapport, worden de geïmporteerde gegevens opnieuw bevraagd, zodat er sprake is van interactiviteit.
* Het is mogelijk om visualisaties, maar ook volledige rapportpagina's, als tegels vast te maken aan een dashboard. De tegels worden automatisch vernieuwd wanneer de onderliggende gegevensset wordt vernieuwd.  

### <a name="directquery-connections"></a>DirectQuery-verbindingen
Wanneer u **Gegevens ophalen** gebruikt in **Power BI Desktop** om verbinding te maken met een gegevensbron, en u kiest **DirectQuery**, is het gedrag van die verbinding als volgt:

* Tijdens de eerste fase van **Gegevens ophalen** wordt de bron geselecteerd. Voor relationele bronnen betekent dit dat er een set met tabellen wordt geselecteerd en dat elke tabel nog steeds een query vertegenwoordigt die een logische set gegevens retourneert. Voor multidimensionale bronnen zoals SAP BW, wordt alleen de bron geselecteerd.
* Bij het laden worden er echter niet daadwerkelijk gegevens geïmporteerd in de opslaglocatie van Power BI. In plaats daarvan worden bij het bouwen van een visualisatie in **Power BI Desktop**, query's verzonden naar de onderliggende gegevensbron om de benodigde gegevens op te halen. De tijd die vervolgens nodig is om de visualisatie te vernieuwen, is afhankelijk van de prestaties van de onderliggende gegevensbron.
* Eventuele wijzigingen in de onderliggende gegevens worden niet direct doorgevoerd in bestaande visualisaties. Het is nog steeds nodig om Vernieuwen te kiezen, waarna de vereiste query's opnieuw worden verzonden voor de visualisaties en deze waar nodig worden bijgewerkt.
* Bij het publiceren van het rapport naar de **Power BI-service**, levert dit weer in een gegevensset in Power BI-service, hetzelfde als bij importeren. Er worden echter *geen* gegevens opgenomen in deze dataset.
* Bij het openen van een bestaand rapport in de **Power BI-service**, of bij het ontwerpen van een nieuw rapport, wordt de onderliggende gegevensbron opnieuw bevraagd om de benodigde gegevens op te halen. Afhankelijk van de locatie van de oorspronkelijke gegevensbron, kan het nodig zijn om een On-premises gegevensgateway te configureren, net als bij de importmodus om de gegevens te vernieuwen.
* Het is mogelijk om visualisaties, maar ook volledige rapportpagina's, als tegels vast te maken aan een dashboard. Om ervoor te zorgen dat een dashboard snel wordt geopend, worden de tegels automatisch vernieuwd volgens een bepaald schema (bijvoorbeeld elk uur). Deze frequentie kan worden aangepast om in te spelen op de snelheid waarmee gegevens worden gewijzigd en hoe belangrijk het is om de nieuwste gegevens te zien. Bij het openen van een dashboard, worden de tegels dus de gegevens vanaf het moment waarop de laatste vernieuwing en niet per se de meest recente wijzigingen aangebracht in de onderliggende gegevensbron bevatten. Een geopend dashboard kan altijd worden vernieuwd om de nieuwste gegevens te tonen.    

### <a name="live-connections"></a>Live-verbindingen
Bij het verbinden met **SQL Server Analysis Services** (SSAS) kunt u ervoor kiezen om gegevens te importeren uit het geselecteerde gegevensmodel of om een live-verbinding met de gegevens op te zetten. Als u kiest voor **importeren**, definieert u een query op die externe SSAS-bron en worden de gegevens zoals gebruikelijk geïmporteerd. Als u **live verbinding maken**, klikt u vervolgens is er geen query gedefinieerd en het hele externe model wordt weergegeven in de lijst met velden. Als u **DirectQuery** selecteert, worden er tijdens het samenstellen van visualisaties query's verzonden naar de externe SSAS-bron. In tegenstelling tot DirectQuery met Power BI, is er hier echter geen sprake van het maken van een nieuw *model*, in die zin dat het niet mogelijk is om nieuwe berekende kolommen, hiërarchieën, relaties en dergelijke te definiëren. Er wordt gewoon rechtstreeks verbinding gemaakt met het externe SSAS-model.

De situatie die wordt beschreven in de vorige alinea geldt ook voor het maken van verbinding met de volgende bronnen, behalve dat er geen mogelijkheid is om de gegevens te importeren:

* Power BI-gegevenssets (bijvoorbeeld bij het verbinden met een Power BI-gegevensset die eerder is gemaakt en gepubliceerd naar de service, om een nieuw rapport voor de set te maken)
* Common Data Services

Het gedrag van rapporten via SSAS, bij het publiceren naar de **Power BI-service**, is op de volgende punten vergelijkbaar met DirectQuery-rapporten:

* Bij het openen van een bestaand rapport in de **Power BI-service** of bij het ontwerpen van een nieuw rapport, wordt de onderliggende SSAS-gegevensbron bevraagd (waarvoor mogelijk een On-premises gegevensgateway nodig is)
* Dashboardtegels worden automatisch vernieuwd volgens een schema (bijvoorbeeld elk uur of met een andere frequentie)

Er zijn echter ook belangrijke verschillen, bijvoorbeeld dat voor live-verbindingen altijd de identiteit van de gebruiker die het rapport opent, wordt doorgegeven aan de onderliggende SSAS-gegevensbron.

U weet nu wat de verschillen en overeenkomsten zijn tussen de beschikbare verbindingsmogelijkheden. In de rest van dit artikel besteden we alleen nog aandacht aan **DirectQuery** in combinatie met Power BI.

## <a name="when-is-directquery-useful"></a>Wanneer is DirectQuery een geschikte oplossing?
De volgende tabel beschrijft scenario's waarin verbindingen met behulp van DirectQuery zeer zinvol kunnen zijn, inclusief situaties waarin het verstandig kan zijn om de gegevens niet op te halen uit de oorspronkelijke bron. In de beschrijving wordt besproken of het opgegeven scenario beschikbaar is in Power BI.

| Beperking | Beschrijving |
| --- | --- |
| Gegevens worden vaak gewijzigd en er is behoefte aan bijna 'realtime' rapportage |Modellen met geïmporteerde gegevens kunnen maximaal één keer per uur worden vernieuwd. Dus als de gegevens steeds veranderen en is het nodig zijn voor rapporten om de meest recente gegevens weer te geven, klikt u vervolgens met behulp van importeren met geplande vernieuwing voldoet niet aan deze behoeften. Het is trouwens ook mogelijk om gegevens rechtstreeks te streamen naar Power BI, maar hierbij gelden wel beperkingen ten aanzien van de gegevensvolumes. <br/> <br/> Bij gebruik van DirectQuery, daarentegen, bevat een geopend of vernieuwd rapport of dashboard altijd de meest recente gegevens uit de bron. Bovendien kunnen de tegels van een dashboard vaker worden bijgewerkt (maximaal elke 15 minuten). |
| Gegevens zijn erg groot |Als de gegevens erg groot zijn, is het importeren van alle gegevens sowieso niet haalbaar. Bij DirectQuery is het helemaal niet nodig om grote gegevensoverdrachten uit te voeren, aangezien deze lokaal worden opgevraagd. <br/> <br/> Echter grote hoeveelheden gegevens mogelijk ook impliceren dat de prestaties van de query's op deze onderliggende gegevensbron te langzaam zijn (zoals beschreven in *gevolgen van het gebruik van DirectQuery* sectie, verderop in dit artikel). En natuurlijk is het niet altijd nodig om de volledige gedetailleerde gegevens te importeren. In plaats daarvan kunnen de gegevens vooraf worden samengevoegd tijdens het importeren (en in **Query-editor** kunt u dit heel gemakkelijk doen). In theorie is het mogelijk om exact de aggregatiegegevens te importeren die nodig zijn voor elke visualisatie. Dus waar DirectQuery de eenvoudigste manier is voor grote hoeveelheden gegevens, moet u altijd in het achterhoofd houden dat het importeren van aggregatiegegevens een oplossing kan zijn als de onderliggende gegevensbron te langzaam is. |
| Er zijn beveiligingsregels zijn gedefinieerd in de onderliggende gegevensbron |Wanneer de gegevens worden geïmporteerd, maakt Power BI verbinding met de gegevensbron met behulp van de referenties van de huidige gebruiker (uit Power BI Desktop) of de referenties die zijn opgegeven tijdens het configureren van de geplande vernieuwing (uit de Power BI-service). Bij het publiceren en delen van een dergelijk rapport is het dan ook belangrijk om alleen te delen met gebruikers die dezelfde gegevens mogen zien. Een alternatief is om beveiliging op rijniveau als onderdeel van de gegevensset te definiëren. <br/> <br/> Omdat met DirectQuery altijd de onderliggende gegevensbron wordt bevraagd, kan hierdoor in het ideale geval elke beveiligingsregel uit deze onderliggende gegevensbron worden toegepast. Op dit moment maakt Power BI echter altijd verbinding met de onderliggende gegevensbron met de referenties die ook zouden worden gebruikt voor importeren. <br/> <br/> Totdat Power BI toestaat dat de identiteit van de rapportgebruiker wordt doorgeven aan de onderliggende gegevensbron, biedt DirectQuery dus geen voordelen met betrekking tot beveiliging van de gegevensbron. |
| Er gelden beperkingen ten aanzien van de onafhankelijkheid van gegevens |Sommige organisaties hanteren beleidsregels voor de onafhankelijkheid van gegevens, wat betekent dat gegevens de locatie van de organisatie niet mogen verlaten. Een oplossing op basis van importeren zal zeker problemen opleveren. Bij gebruik van DirectQuery, daarentegen, blijven die gegevens aanwezig in de onderliggende gegevensbron. <br/> <br/> Er moet echter wel worden opgemerkt dat zelfs met DirectQuery sommige caches met gegevens op het niveau van de visualisatie bewaard worden in de Power BI-service (vanwege geplande vernieuwing van tegels). |
| Onderliggende gegevensbron is een OLAP-bron, met metingen |Als de onderliggende gegevensbron *metingen* bevat (zoals SAP HANA of SAP Business Warehouse), ontstaan er andere problemen als de gegevens worden geïmporteerd. Dit betekent dat de gegevens die zijn geïmporteerd een bepaald niveau van aggregatie hebben, zoals gedefinieerd door de query. Denk aan metingen zoals meten Totaalomzet per klasse, jaar en plaats. Vervolgens als een visualisatie wordt gebouwd is voor gegevens op een hoger niveau statistische functie (zoals Totaalomzet per jaar), het verder geaggregeerd de statistische waarde. Dit is prima voor additieve metingen (zoals Som en Min), maar het is een probleem voor niet-additieve metingen (zoals Gemiddelde, Uniek aantal). <br/> <br/> Om de juiste aggregatiegegevens (zoals deze nodig zijn voor de specifieke visualisatie) rechtstreeks te verkrijgen vanuit de bron, zou het nodig zijn om query's per visualisatie te versturen, zoals in DirectQuery. <br/> <br/> Wanneer u verbinding maakt met SAP Business Warehouse (BW), biedt een keuze voor DirectQuery de mogelijkheid om metingen op deze manier te verwerken. Ondersteuning voor SAP BW wordt uitvoerig besproken in [DirectQuery en SAP BW](desktop-directquery-sap-bw.md). <br/> <br/> Op dit moment verwerkt DirectQuery via SAP HANA de gegevensbron op dezelfde manier als een relationele gegevensbron, en vertoont daarom soortgelijk gedrag als bij importeren. Dit wordt nader besproken in [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md). |

Op basis van de huidige mogelijkheden van DirectQuery in Power BI zijn dit kort gezegd de scenario's waarin DirectQuery dit voordelen biedt:

* Gegevens worden vaak gewijzigd en er is behoefte aan bijna 'realtime' rapportage
* Verwerking van zeer grote hoeveelheden gegevens, zonder de noodzaak van vooraf aggregeren
* Er gelden beperkingen ten aanzien van de onafhankelijkheid van gegevens
* De bron is een multidimensionale bron met metingen (zoals SAP BW)

De details in de vorige lijst hebben alleen betrekking op het gebruik van Power BI. Er is altijd de mogelijkheid om in plaats daarvan een extern SQL Server Analysis Services-model (of Azure Analysis Services-model) te gebruiken voor het importeren van gegevens om vervolgens met Power BI verbinding te maken met dat model. Hoewel voor deze aanpak aanvullende vaardigheden nodig zijn, krijgt u er meer flexibiliteit voor terug. Zo is het bijvoorbeeld mogelijk om veel grotere hoeveelheden gegevens te importeren en is er geen beperking voor de frequentie waarmee de gegevens kunnen worden vernieuwd.

## <a name="implications-of-using-directquery"></a>Gevolgen van het gebruik van DirectQuery
Het gebruik van **DirectQuery** heeft mogelijke negatieve gevolgen. Deze worden beschreven in deze sectie. Sommige van deze beperkingen verschillen enigszins afhankelijk van de exacte bron die wordt gebruikt. Dit genoemd waar van toepassing en er zijn afzonderlijke artikelen betrekking hebben op de bronnen die aanzienlijk verschillen.  

### <a name="performance-and-load-on-the-underlying-source"></a>Prestaties en belasting van de onderliggende gegevensbron
Bij gebruik van **DirectQuery** wordt de algehele ervaring voor een groot deel bepaald door de prestaties van de onderliggende gegevensbron. Als het vernieuwen van elke visualisatie (bijvoorbeeld na het wijzigen van een slicerwaarde) een paar seconden duurt (<5 s), is er sprake van een redelijke ervaring, hoewel deze traag kan aanvoelen in vergelijking met de onmiddellijke respons die we krijgen als de gegevens zijn geïmporteerd in Power BI. Als de gegevensbron echter zo traag is dat het laden van afzonderlijke visualisaties langer duurt (tientallen seconden), is er sprake van een zeer slechte ervaring en misschien wel zo slecht dat er zelfs time-outs optreden voor een query.

Samen met de prestaties van de onderliggende gegevensbron, moet met een zorgvuldige afweging aan de belasting die erop worden geplaatst (die vaak gevolgen heeft voor de prestaties) worden betaald. Zoals hieronder verder wordt besproken, wordt er per visualisatie ten minste één query naar de onderliggende gegevensbron verstuurd voor elke gebruiker die een gedeeld rapport opent en elke dashboardtegel die regelmatig wordt vernieuwd. Het is belangrijk dat de gegevensbron ook bij een dergelijke querybelasting redelijk blijft presteren.

### <a name="limited-to-a-single-source"></a>Beperkt tot één bron
Wanneer u gegevens importeert, is het mogelijk om gegevens uit meerdere bronnen te combineren in één model, bijvoorbeeld om gemakkelijk wat gegevens uit een SQL Server-database van uw bedrijf samen te voegen met lokale gegevens die worden bijgehouden in een Excel-bestand. Dit is niet mogelijk wanneer u DirectQuery gebruikt. Wanneer u DirectQuery selecteert voor een bron, kunt u vervolgens alleen gegevens uit die ene bron gebruiken (zoals een bepaalde SQL Server-database).

### <a name="limited-data-transformations"></a>Beperkte gegevenstransformaties
Op dezelfde manier gelden er ook beperkingen in de gegevenstransformaties die kunnen worden toegepast binnen **Query-editor**. Met geïmporteerde gegevens, kan eenvoudig een geavanceerde reeks transformaties worden toegepast als u wilt opschonen en zetten de gegevens voordat u deze visuele elementen (zoals bij het parseren van JSON-documenten, of het draaien van gegevens uit een kolom in een formulier met rijen) maken om. Deze transformaties zijn beperkter in DirectQuery. Bij het verbinden met een OLAP-bron zoals SAP Business Warehouse is het al helemaal niet mogelijk om transformaties te definiëren en wordt het externe 'model' in zijn geheel overgenomen van de bron. Voor relationele bronnen zoals SQL Server is het nog steeds mogelijk om per query een set transformaties te definiëren, maar deze transformaties zijn uit prestatieoverwegingen beperkt. Een dergelijke transformatie moet worden toegepast op elke query die wordt uitgevoerd op de onderliggende gegevensbron, in plaats van één keer bij het vernieuwen van de gegevens. Het gaat dus alleen om transformaties die redelijkerwijs kunnen worden vertaald naar een enkele, systeemeigen query. Als u een transformatie gebruikt die te complex is, ontvangt u een fout dat de transformatie moet worden verwijderd of dat het model moet worden overgeschakeld naar de importmodus.

Bovendien wordt de query die het resultaat is van de opdracht **Gegevens ophalen** of **Query-editor** gebruikt in een subselectie binnen de gegenereerde query's en wordt deze verzonden voor het ophalen van de benodigde gegevens voor een visualisatie. De query die is gedefinieerd in de Query-editor, moet dus geldig zijn in deze context. Dit betekent met name dat het niet mogelijk is om een query te gebruiken met behulp van algemene tabelexpressies, en ook geen query die opgeslagen procedures aanroept.

### <a name="modeling-limitations"></a>Modelleringsbeperkingen
De term *modellering* in deze context betekent de handeling van het verfijnen en verrijken van de onbewerkte gegevens, als onderdeel van het ontwerpen van een rapport waarin deze gegevens worden gebruikt. Enkele voorbeelden:

* Relaties tussen tabellen definiëren
* Nieuwe berekeningen toevoegen (berekende kolommen en metingen)
* Kolommen en metingen een andere naam geven en verbergen
* Hiërarchieën definiëren
* De opmaak, standaardsamenvatting en sorteervolgorde voor een kolom definiëren
* Waarden groeperen of clusteren

Wanneer u **DirectQuery** gebruikt, zijn er nog steeds mogelijkheden om het model te verrijken, en het principe van verrijking van de onbewerkte gegevens wordt zeker gehandhaafd, om het latere verbruik van de gegevens te verbeteren. Enkele modelleringsfuncties zijn echter niet beschikbaar, of in beperkte mate, wanneer u DirectQuery gebruikt. Deze beperkingen worden over het algemeen toegepast om prestatieproblemen te voorkomen. In de volgende lijst met opsommingstekens ziet u de set met beperkingen die gemeenschappelijk zijn voor alle DirectQuery bronnen. Er kunnen aanvullende beperkingen van toepassing zijn op afzonderlijke bronnen, zoals wordt beschreven in *Specifieke details van gegevensbron* aan het einde van dit artikel.

* **Er is geen ingebouwde datumhiërarchie:** Bij het importeren van gegevens geldt dat voor elke datum- of datum- en tijdkolom ook standaard een ingebouwde datumhiërarchie beschikbaar is. Als u bijvoorbeeld een tabel met verkooporders importeert, inclusief een kolom Orderdatum, en u die kolom vervolgens gebruikt in een visualisatie, kunt u het niveau (jaar, maand, dag) kiezen dat u wilt gebruiken. Deze ingebouwde datumhiërarchie is niet beschikbaar bij gebruik van de DirectQuery-modus. Als er echter een datumtabel beschikbaar is in de onderliggende gegevensbron (wat gebruikelijk is in veel datawarehouses), kunnen de DAX Time Intelligence-functies op de normale manier worden gebruikt.
* **Beperkingen in berekende kolommen:** Voor berekende kolommen geldt dat ze zijn beperkt tot intra-rij, wat inhoudt dat ze alleen kunnen verwijzen naar waarden van andere kolommen in dezelfde tabel, zonder het gebruik van een statistische functie. Bovendien geldt voor toegestane scalaire DAX-functies, zoals LEFT(), dat deze worden beperkt tot functies die simpelweg naar de onderliggende gegevensbron kunnen worden gepusht. De beschikbare DAX-functies verschillen dus naargelang de exacte mogelijkheden van de bron. Functies die niet worden ondersteund, worden niet weergegeven bij het automatisch aanvullen van de DAX voor een berekende kolom. Als een dergelijke functie toch wordt gebruikt, levert dit een fout op.
* **Geen ondersteuning voor bovenliggende-onderliggende DAX-functies:** In het DirectQuery-model is het niet mogelijk om de familie van DAX PATH()-functies te gebruiken, die doorgaans structuren op basis van bovenliggend/onderliggend afhandelen (zoals rekeningschema's of werknemershiërarchieën).
* **Beperkingen (standaard) voor metingen:** Er gelden standaard beperkingen voor de DAX-functies en expressies die kunnen worden gebruikt in metingen. Ook hier worden door automatisch aanvullen alleen de functies vermeld die zijn toegestaan en treedt er een fout op als er een ongeldige functie of expressie wordt gebruikt. Dit wordt gedaan om ervoor te zorgen dat er standaard alleen eenvoudige metingen worden gebruikt die waarschijnlijk niet op zichzelf prestatieproblemen zullen veroorzaken. Geavanceerde gebruikers kunnen ervoor kiezen deze beperking als volgt te omzeilen: selecteer achtereenvolgens **Bestand > Opties en instellingen > Opties**, **DirectQuery** en de optie *Onbeperkte metingen toestaan in de DirectQuery-modus*. Als deze optie is geselecteerd, kan elke DAX-expressie worden gebruikt die geldig is voor een meting. Gebruikers moeten echter wel beseffen dat bepaalde expressies die goed presteren als de gegevens worden geïmporteerd, in de DirectQuery-modus trage query's naar de back-endbron tot gevolg kunnen hebben.
  
  * Enkele voorbeelden:
    
    * Het is standaard mogelijk om een meting te maken die de verkoophoeveelheid berekent:
      
          SalesAmount = SUMX(Web_Sales, [ws_sales_price]* [ws_quantity])
    * Het is standaard *niet* mogelijk om een meting te ontwerpen die vervolgens de gemiddelde verkoophoeveelheid voor alle artikelen berekent:
      
          AverageItemSalesAmount = AVERAGEX('Item', [SalesAmount])
    
    De reden hiervoor is dat een dergelijke meting tot slechte prestaties kan leiden als er sprake is van een groot aantal artikelen.
* **Berekende tabellen worden niet ondersteund:** De mogelijkheid om een berekende tabel te definiëren met behulp van een DAX-expressie wordt niet ondersteund in de DirectQuery-modus.
* **Filteren van relatie werkt maar in één richting:** Bij gebruik van DirectQuery is het niet mogelijk om Kruisfilterrichting voor een relatie in te stellen op 'Beide'. Voor de drie onderstaande tabellen is het bijvoorbeeld niet mogelijk om een visualisatie te maken met daarin uitgesplitst voor alle mannelijke en vrouwelijke klanten (Customer[Gender]) het aantal artikelen dat ze per categorie hebben gekocht (Product[Category]). Het gebruik van dergelijke bidirectionele filters wordt beschreven [in dit gedetailleerde technisch document](http://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx). Het document bevat weliswaar voorbeelden in de context van SQL Server Analysis Services, maar de fundamentele punten gelden ook voor Power BI.
  
  ![](media/desktop-directquery-about/directquery-about_01.png)
  
  Ook hier geldt dat de beperking wordt afgedwongen om prestatieverlies te voorkomen. Deze beperking speelt met name een belangrijke rol bij het definiëren van beveiliging op rijniveau als onderdeel van het rapport. Het is namelijk gebruikelijk om veel-veel-relaties te leggen tussen gebruikers en de entiteiten waartoe ze toegang hebben, en het gebruik van bidirectionele filters is nodig om dit af te dwingen. Bij het gebruik van bidirectionele filters met DirectQuery-modellen moet echter zorgvuldig te werk worden gegaan, waarbij vooral goed moet worden gekeken naar eventuele nadelige gevolgen voor de prestaties.  
* **Geen clustering:** Wanneer u DirectQuery gebruikt, is het niet mogelijk om met behulp van de voorziening Clustering automatisch te zoeken naar groepen

### <a name="reporting-limitations"></a>Rapportagebeperkingen
Bijna alle rapportagemogelijkheden worden ondersteund voor DirectQuery-modellen. Dit betekent dat zolang de onderliggende gegevensbron een geschikt prestatieniveau biedt, dezelfde set visualisaties kan worden gebruikt. Er gelden echter enkele belangrijke beperkingen voor een aantal van de andere mogelijkheden die worden aangeboden in de **Power BI-service** nadat een rapport is gepubliceerd, zoals wordt beschreven in de onderstaande lijst met opsommingstekens:

* **Quick Insights wordt niet ondersteund:** Power BI Quick Insights doorzoekt verschillende subsets van uw gegevensset terwijl er tegelijkertijd geavanceerde algoritmen worden toegepast om potentieel interessante inzichten te detecteren. Gezien de noodzaak voor query's met een snelle respons, is deze mogelijkheid niet beschikbaar voor gegevenssets die DirectQuery gebruiken.
* **Q&A wordt niet ondersteund:** Met Q&A van Power BI kunt u met behulp van intuïtieve, natuurlijke taal uw gegevens verkennen en antwoorden krijgen in de vorm van diagrammen en grafieken. Deze voorziening wordt momenteel echter niet ondersteund voor gegevenssets die DirectQuery gebruiken.
* **Verkenning gebruiken in Excel leidt waarschijnlijk tot slechtere prestaties:** Het is mogelijk om uw gegevens te verkennen met de mogelijkheid 'Verkennen in Excel' in een gegevensset. Hierdoor kunt u draaitabellen en -grafieken maken in Excel. Hoewel deze mogelijkheid wordt ondersteund voor gegevenssets die DirectQuery gebruiken, zijn de prestaties meestal minder dan bij het maken van visualisaties in Power BI. Als het gebruik van Excel belangrijk is voor uw scenario's, moet u hiermee rekening houden in uw beslissing om DirectQuery te gebruiken.

### <a name="security"></a>Beveiliging
Zoals eerder in dit artikel is besproken, worden voor een rapport met **DirectQuery** altijd dezelfde vaste referenties gebruikt om verbinding te maken met de onderliggende gegevensbron, nadat deze is gepubliceerd naar de **Power BI-service**. Ook hier is van belang te weten dat dit specifiek geldt voor DirectQuery, niet voor live-verbindingen met SQL Server Analysis Services, waar dit anders is geregeld. Daarom is het direct na het publiceren van een DirectQuery-rapport nodig om de referenties te configureren van de gebruiker die zal worden gebruikt. Totdat dit is gebeurd, treedt er een fout op wanneer het rapport wordt geopend in de Power BI-service.

Zodra de gebruikersreferenties zijn opgegeven, worden deze referenties gebruikt, *ongeacht de gebruiker die het rapport opent*. In dit opzicht werkt het precies hetzelfde als bij geïmporteerde gegevens, namelijk dat elke gebruiker dezelfde gegevens ziet, tenzij beveiliging op rijniveau is gedefinieerd als onderdeel van het rapport. Daarom moet dezelfde zorgvuldigheid worden betracht bij het delen van het rapport, als er beveiligingsregels zijn gedefinieerd in de onderliggende gegevensbron.

### <a name="behavior-in-the-power-bi-service"></a>Gedrag in de Power BI-service
Deze sectie beschrijft het gedrag van een **DirectQuery**-rapport in de **Power BI-service**, voornamelijk om een beeld te geven van de mate van belasting die de gegevensbron in de back-end krijgt te verwerken, afhankelijk van het aantal gebruikers waarmee het rapport en het dashboard worden gedeeld, de complexiteit van het rapport en of beveiliging op rijniveau is ingesteld in het rapport.

#### <a name="reports--opening-interacting-with-editing"></a>Rapporten: openen, interactie en bewerken
Wanneer een rapport wordt geopend, worden alle visualisaties op de momenteel zichtbare pagina vernieuwd. Voor elke visualisatie moet ten minste één query op de onderliggende gegevensbron worden uitgevoerd. Sommige visualisaties hebben mogelijk meerdere query's nodig (bijvoorbeeld als deze aggregatiewaarden uit twee verschillende feitentabellen bevat, een meer complexe meting of totalen van een niet-additieve meting zoals Count Distinct). Het weergeven van een nieuwe pagina zorgt ervoor dat deze visualisaties worden vernieuwd, wat resulteert in een nieuwe set query's op de onderliggende gegevensbron.

Elke gebruikersinteractie met het rapport kan betekenen dat de visualisaties worden vernieuwd. Als er bijvoorbeeld een andere waarde wordt geselecteerd in een slicer, moet er een nieuwe set query's worden verzonden om alle betreffende visualisaties te vernieuwen. Hetzelfde geldt voor het klikken op een visualisatie voor het kruislings markeren van andere visualisaties of het wijzigen van een filter.  

Het bewerken van een nieuw rapport moeten op dezelfde manier, query's worden verzonden voor elke stap van het pad voor het produceren van de gewenste visualisatie.

Bepaalde resultaten worden in de cache opgeslagen, zodat het vernieuwen van een visualisatie direct plaatsvindt als onlangs exact dezelfde resultaten zijn verkregen. Deze caches worden echter niet gedeeld door gebruikers als er beveiliging op rijniveau is gedefinieerd als onderdeel van het rapport.

#### <a name="dashboard-refresh"></a>Dashboard vernieuwen
U kunt afzonderlijke visualisaties, of volledige pagina's, als tegels koppelen aan een dashboard. Tegels die zijn gebaseerd op **DirectQuery**-gegevenssets worden vervolgens automatisch vernieuwd volgens een schema, wat resulteert in het versturen van query's naar de gegevensbron in de back-end. De standaardinstelling is dat dit elk uur gebeurt, maar in de instellingen van de gegevensset kunt u een waarde opgeven tussen wekelijks en elke 15 minuten.

Als er geen beveiliging op rijniveau is gedefinieerd in het model, betekent dit dat elke tegel eenmaal wordt vernieuwd en dat de resultaten met alle gebruikers worden gedeeld. Als wel beveiliging op rijniveau is gedefinieerd, kan er een sneeuwbaleffect ontstaan: voor elke tegel moeten per gebruiker afzonderlijke query's worden verstuurd naar de onderliggende gegevensbron.  

Stel dat een dashboard tien tegels bevat en wordt gedeeld met 100 gebruikers. De tegels zijn gebaseerd op een gegevensset die is geconfigureerd met **DirectQuery**, beveiliging op rijniveau en vernieuwen om de 15 minuten. Het gevolg is dan dat er elke 15 minuten ten minste 1000 query's worden verzonden naar de bron in de back-end.

Het is dus belangrijk dat er zorgvuldig wordt gekeken naar het gebruik van beveiliging op rijniveau en de configuratie van het vernieuwingsschema.

#### <a name="timeouts"></a>Time-outs
Er is een time-out van vier minuten wordt toegepast op afzonderlijke query's in de **Power BI-service**, en query's langer duurt dan dat zal mislukken. Zoals eerder benadrukt, verdient het aanbeveling DirectQuery te gebruiken voor gegevensbronnen die query's bijna interactief kunnen verwerken. Deze limiet is dan ook bedoeld om problemen als gevolg van zeer lange uitvoeringstijden te voorkomen.

### <a name="other-implications"></a>Andere implicaties
Enkele andere algemene gevolgen van het gebruik van **DirectQuery** zijn als volgt:

* **Als gegevens worden gewijzigd, is het nodig om te vernieuwen om te controleren dat de recentste gegevens worden weergegeven:** Vanwege het gebruik van caches is er geen manier om te garanderen dat de visual altijd de recentste gegevens weergeeft. Stel dat een visualisatie de transacties van de afgelopen dag laat zien. Vanwege een slicer gewijzigd, klikt u vervolgens het mogelijk vernieuwen om de transacties weergeven voor de afgelopen twee dagen, met inbegrip van een recente, net ontvangen nieuwe transacties. Als de slicer dan weer op de oorspronkelijke waarde wordt gezet, worden opnieuw de eerder verkregen gegevens weergegeven die nog in de cache staan. De visualisatie bevat dan niet meer de zojuist binnengekomen transacties die eerder zichtbaar waren.
  
  Door handmatig Vernieuwen te selecteren, worden alle caches leeggemaakt en bevatten alle visualisaties de meest recente gegevens.
* **Als gegevens worden gewijzigd, kan consistentie tussen visuals niet worden gegarandeerd:** Verschillende visuals, of deze op dezelfde of op verschillende pagina's staan, worden mogelijk op verschillende tijdstippen vernieuwd. Dus als de gegevens in de onderliggende gegevensbron worden gewijzigd, is er geen garantie dat op enig moment exacte dezelfde gegevens worden weergegeven in de visualisaties. Het feit dat soms meerdere query's nodig zijn voor één visualisatie (bijvoorbeeld om de details en de totalen te verkrijgen), betekent dat zelfs consistentie binnen één visualisatie niet kan worden gegarandeerd. Om dit mogelijk te maken, zouden bij het vernieuwen van een bepaalde visualisatie alle visualisaties moeten worden vernieuwd, wat niet alleen veel overhead kost maar ook het gebruik vereist van dure functies zoals Snapshot Isolation in de onderliggende gegevensbron.
  
  Dit probleem kan grotendeels worden opgevangen door opnieuw handmatig Vernieuwen te selecteren om alle visualisaties op de pagina te vernieuwen. Bij gebruik van de importmodus is er trouwens een vergelijkbaar probleem en kan er geen consistentie worden gegarandeerd als gegevens uit meer dan één tabel worden geïmporteerd.
* **Vernieuwen in Power BI Desktop is nodig om wijzigingen in metagegevens te weergeven:** Nadat een rapport is gepubliceerd, worden de visuele elementen in het rapport vernieuwd in vernieuwen. Als het schema van de onderliggende bron is gewijzigd, worden deze wijzigingen niet automatisch toegepast om de beschikbare velden in de lijst met velden aan te passen. Dus als tabellen of kolommen zijn verwijderd uit de onderliggende gegevensbron, kan dit tot gevolg hebben dat een query mislukt na het vernieuwen van de gegevens. U kunt de velden in het model bijwerken met de wijzigingen door het rapport te openen in Power BI Desktop en Vernieuwen te kiezen.
* **Elke query kan maximaal één miljoen rijen opleveren:** Er geldt een vaste limiet van één miljoen rijen voor het aantal rijen dat met één query kan worden opgevraagd uit de onderliggende gegevensbron. Dit heeft meestal geen praktische gevolgen en in visualisaties zelf wordt nooit dit aantal gegevenspunten weergegeven. De limiet kan echter een rol spelen in situaties waarin Power BI de verzonden query's niet volledig optimaliseert en er een tussentijds resultaat wordt opgevraagde dat de limiet overschrijdt. Het kan ook gebeuren tijdens het bouwen van een visualisatie, op weg naar een meer redelijke eindstatus. Bijvoorbeeld, met inbegrip van de klant en totaleomzet worden opgevraagd terwijl deze limiet bereikt als er meer dan 1 miljoen klanten, totdat er een filter zijn toegepast.
  
  Er wordt dan een fout weergegeven met de mededeling dat de resultatenset van een query op een externe gegevensbron het maximaal toegestane aantal van '1000000' rijen heeft overschreden.
* **Importmodus kan niet worden gewijzigd in DirectQuery-modus:**  Hoewel het mogelijk is om een model over te schakelen van de DirectQuery-modus naar de importmodus, betekent dit dat alle benodigde gegevens moeten worden geïmporteerd. Het is trouwens niet mogelijk om terug te schakelen (voornamelijk als gevolg van een reeks functies die niet wordt ondersteund in de DirectQuery-modus). DirectQuery-modellen via multidimensionale bronnen zoals SAP BW, kunnen ook worden overgeschakeld van DirectQuery naar import, als gevolg van de verschillende behandeling van externe metingen.

## <a name="directquery-in-the-power-bi-service"></a>DirectQuery in de Power BI-service
Alle bronnen worden ondersteund vanuit **Power BI Desktop**. Sommige bronnen zijn ook rechtstreeks beschikbaar vanuit de **Power BI-service**. Zo kan een zakelijke gebruiker via Power BI verbinding maken met gegevens in Salesforce en onmiddellijk een dashboard weergeven, zonder het gebruik van **Power BI Desktop**.

Slechts twee bronnen die geschikt zijn voor DirectQuery zijn rechtstreeks beschikbaar in de service:

* Spark
* Azure SQL Data Warehouse

Het wordt echter aanbevolen om het gebruik van **DirectQuery** met deze twee bronnen te starten in **Power BI Desktop**. De reden is dat wanneer de verbinding in eerste instantie tot stand wordt gebracht in de **Power BI-service**, er een groot aantal belangrijke beperkingen gelden. Dit betekent dat het realiseren van de verbinding weliswaar gemakkelijk is (vanuit de Power BI-service), maar dat er vervolgens beperkingen gelden voor het verder verbeteren van het resulterende rapport. Zo is het bijvoorbeeld onmogelijk om berekeningen te maken en zijn veel analytische functies niet beschikbaar. Het is zelfs niet mogelijk om de metagegevens te vernieuwen om wijzigingen van het onderliggende schema door te voeren.   

## <a name="guidance-for-using-directquery-successfully"></a>Richtlijnen voor succesvol gebruik van DirectQuery
Als u **DirectQuery** wilt gaan gebruiken, leest u hier enkele algemene richtlijnen om dit met succes te gaan doen. De richtlijnen in deze sectie zijn afgeleid van de gevolgen van het gebruik van DirectQuery die eerder in dit artikel zijn beschreven.

### <a name="backend-data-source-performance"></a>Prestaties van gegevensbron in de back-end
U moet controleren of eenvoudige visuals binnen een redelijke tijd kunnen worden vernieuwd - dit moet binnen vijf seconden gebeuren om de interactieve ervaring prettig te maken. Als het opbouwen van visualisaties langer duurt dan 30 seconden, is de kans zeer groot dat er andere problemen zullen optreden na publicatie van het rapport, waardoor dit een onwerkbare oplossing is.

Als query's langzaam zijn, controleert u eerst de query's die naar de onderliggende gegevensbron worden verzonden en de reden voor de waargenomen prestaties van query's. We kunnen hier niet het volledige spectrum van aanbevolen procedures voor database-optimalisatie bespreken voor alle mogelijke onderliggende bronnen. De besproken informatie geldt voor de gangbare databaseprocedures die van toepassing zijn op de meeste situaties:

* Relaties op basis van integerkolommen presteren in het algemeen beter dan joins op kolommen van andere gegevenstypen
* Het is belangrijk dat de juiste indexen worden gemaakt, wat doorgaans neerkomt op het gebruik van columnstore-indexen in de bronnen die hiervoor ondersteuning bieden (bijvoorbeeld SQL Server).
* Eventuele benodigde statistieken in de bron moeten worden bijgewerkt

### <a name="model-design-guidance"></a>Richtlijnen voor modelontwerp
Overweeg de volgende punten bij het definiëren van het model:

* **Vermijd complexe query's in Query-editor.** De query die u definieert in de Query-editor wordt omgezet in een SQL-query, die vervolgens wordt opgenomen in de subselectie van elke query die naar deze tabel wordt verzonden. Als deze query complex is, kan dit leiden tot prestatieproblemen voor elke verzonden query. De werkelijke SQL-query voor een reeks stappen kan worden verkregen door de laatste stap in Query-editor te selecteren en vervolgens *Systeemeigen query weergeven* te kiezen in het contextmenu.
* **Houd metingen simpel.** Zeker in eerste instantie is het raadzaam om metingen te beperken tot eenvoudige statistische functies. Als de metingen vervolgens goed presteren, kunt u complexere metingen definiëren, maar let wel goed op de prestaties van elke meting.
* **Vermijd relaties tussen berekende kolommen.** Dit is relevant voor databases waarvoor het nodig is om joins op meerdere kolommen uit te voeren. Power BI biedt op dit moment geen ondersteuning voor relaties die gebaseerd zijn op meerdere kolommen als de FK/PK. Een tijdelijke oplossing is de kolommen samen te voegen met behulp van een berekende kolom en de join daarop te baseren. Hoewel deze tijdelijke oplossing acceptabel is voor geïmporteerde gegevens, is het resultaat in het geval van **DirectQuery** een join op een expressie. Dit heeft meestal als consequentie dat er geen indexen kunnen worden gebruikt, wat tot slechte prestaties leidt. De enige echte oplossing is om de meerdere kolommen daadwerkelijk te converteren naar één kolom in de onderliggende database.
* **Vermijd relaties tussen uniqueidentifier-kolommen.** Power BI biedt geen ingebouwde ondersteuning voor het gegevenstype uniqueidentifier. Het definiëren van een relatie tussen kolommen van het type uniqueidentifier resulteert daarom in een query met een join waarvoor een Cast nodig is. Een dergelijke situatie leidt vaak weer tot slechte prestaties. Totdat deze situatie speciaal is geoptimaliseerd, is de enige oplossing om kolommen van een alternatief type te gebruiken in de onderliggende database.
* **Verberg de *to*-kolom in relaties.** De *to*-kolom in relaties (meestal de primaire sleutel van de *to*-tabel) moet verborgen zijn, zodat deze niet wordt weergegeven in de lijst met velden en dus niet kan worden gebruikt in visualisaties. De kolommen waarop relaties zijn gebaseerd, zijn in de praktijk vaak *systeemkolommen* (bijvoorbeeld vervangend sleutels in een datawarehouse) en het is sowieso een goed idee om dergelijke kolommen te verbergen. Als de kolom wel een betekenis heeft, introduceert u een berekende kolom die zichtbaar is en die een eenvoudige expressie bevat die gelijk is aan de primaire sleutel. Bijvoorbeeld:
  
      ProductKey_PK   (Destination of a relationship, hidden)
      ProductKey (= [ProductKey_PK],   visible)
      ProductName
      ...
  
  De reden hiervoor is om prestatieproblemen te voorkomen die kunnen optreden als een visualisatie de primaire-sleutelkolom bevat.
* **Controleer alle berekende kolommen en wijzigingen van het gegevenstype.** Het gebruik van deze mogelijkheden hoeft niet per se schadelijk te zijn, maar ze hebben tot gevolg dat de query' die worden verzonden naar de onderliggende gegevensbron expressies bevatten in plaats van eenvoudige verwijzingen naar kolommen, wat weer tot gevolg kan hebben dat er geen indexen worden gebruikt.  
* **Vermijd het gebruik van bidirectioneel kruislings filteren (preview) in relaties.**
* **Experimenteer met de instelling *Referentiële integriteit aannemen*.** De instelling *Referentiële integriteit aannemen* voor relaties stelt query's in staat om INNER JOIN-instructies te gebruiken in plaats van OUTER JOIN. Dit is in het algemeen beter voor de queryprestaties, hoewel de specifieke gegevensbron hierbij ook een rol speelt.
* **Gebruik geen relatieve datumfiltering in Query-editor.** Het is mogelijk om relatieve datumfiltering te definiëren in Query-editor. U kunt zo bijvoorbeeld filteren op rijen waar de datum in de afgelopen 14 dagen ligt.
  
  ![](media/desktop-directquery-about/directquery-about_02.png)
  
  Dit wordt echter omgezet in een filter op basis van de vaste datum, zoals vastgesteld op het moment van ontwerp van de query. Dit kunt u zien door de systeemeigen query te bekijken.
  
  ![](media/desktop-directquery-about/directquery-about_03.png)
  
  Dit is bijna zeker niet de bedoeling. Om ervoor te zorgen dat het filter wordt toegepast op basis van de datum waarop het rapport wordt uitgevoerd, moet u het filter als een rapportfilter toepassen in het rapport. Momenteel kan dit door het maken van een berekende kolom die het aantal dagen geleden berekent, met de functie DAX DATE(), en die berekende kolom vervolgens in een filter te gebruiken.

### <a name="report-design-guidance"></a>Richtlijnen voor rapportontwerp
Hanteer de volgende richtlijnen als u een rapport met een DirectQuery-verbinding gaat maken:

* **Overweeg het gebruik van opties voor Query's beperken:** Power BI biedt opties in rapporten om minder query's te verzenden en om bepaalde interacties uit te schakelen die zouden resulteren in een slechte ervaring als de resulterende query's er lang over zouden doen om uitgevoerd te worden. Als u deze opties wilt instellen, gaat u in **Power BI Desktop** naar **Bestand > Opties en instellingen > Opties** en selecteert u **Query's beperken**. 

   ![](media/desktop-directquery-about/directquery-about_03b.png)

    U kunt kruislingse markering door uw hele rapport uitschakelen door selectievakjes aan te vinken in **Query's beperken**. U kunt ook een knop *Toepassen* tonen op slicer- en/of filterselecties, waarmee u vervolgens vele slicer- en filterselecties kunt maken voordat u ze toepast, waardoor er geen query's worden verzonden totdat u de knop **Toepassen** op de slicer selecteert. Uw selecties kunnen dan worden gebruikt om de gegevens te filteren.

    Deze opties zijn van toepassing op uw rapport terwijl u het rapport beheert in **Power BI Desktop**, ook als uw gebruikers het rapport in de **Power BI-service** gebruiken.

* **Pas eerst filters toe:** Als u filters wilt toepassen, moet u dit altijd aan het begin van het opbouwen van een visualisatie doen. In plaats van bijvoorbeeld TotalSalesAmount en ProductName naar de visualisatie te slepen en vervolgens te filteren op een bepaald jaar, past u het filter Year helemaal aan het begin toe. De reden hiervoor is dat bij elke stap van het bouwen van een visualisatie een query wordt verstuurd, en hoewel het mogelijk is om vervolgens een andere wijziging door te voeren voordat de eerste query is voltooid, wordt de onderliggende gegevensbron hierbij onnodig belast. Door filters in een vroeg stadium toe te passen, zijn de tussenliggende query's over het algemeen minder belastend. Bovendien kan niet vroeg toepassen van filters resulteren in de bovenstaande 1-m Rijlimiet hebt bereikt.
* **Beperk het aantal visualisaties op een pagina:** Als een pagina wordt geopend (of als een slicer of filter op de pagina wordt gewijzigd), worden alle visualisaties op de pagina vernieuwd. Er geldt ook een limiet voor het aantal query's dat tegelijk wordt verzonden, dus als het aantal visualisaties toeneemt, worden enkele visualisaties na elkaar vernieuwd, waardoor het langer duurt om de hele pagina te vernieuwen. Het is raadzaam om deze reden om moet in plaats daarvan meer, eenvoudigere pagina's te beperken van het aantal visualisaties op één pagina.
* **Overweeg interactie tussen visuals uit te schakelen:** Visualisaties op een rapportpagina kunnen standaard worden gebruikt voor het kruislings filteren en markeren van de andere visualisaties op de pagina. Als u bijvoorbeeld '1999' selecteert in het cirkeldiagram, ziet u in het kolomdiagram markeringen die de verkopen per categorie voor '1999' aangeven.                                                                  
  
  ![](media/desktop-directquery-about/directquery-about_04.png)
  
  In DirectQuery is kruislings filteren en markeren op deze manier alleen mogelijk als er query's worden ingediend bij de onderliggende gegevensbron. Deze interactie moet worden uitgeschakeld als het hierdoor te lang duurt om te reageren op de selectie van gebruikers. Deze interactie kan echter worden uitgeschakeld voor het volledige rapport (zoals hierboven beschreven voor de *opties voor Query's beperken*), of per geval zoals [in dit artikel](consumer/end-user-interactions.md) wordt beschreven.

Naast de bovenstaande lijst met suggesties, kunnen de volgende rapportagemogelijkheden prestatieproblemen veroorzaken:

* **Maateenheidsfilters:** Visualisaties met metingen (of totalen van kolommen) kunnen filters bevatten in die metingen. In de visualisatie hieronder ziet u bijvoorbeeld SalesAmount by category, maar alleen voor categorieën met meer dan 20 miljoen aan omzet.
  
  ![](media/desktop-directquery-about/directquery-about_05.png)
  
  Hiervoor moeten twee query's naar de onderliggende gegevensbron worden verzonden:
  
  * De eerste query haalt de categorieën op die voldoen aan de voorwaarde (Omzet > 20 miljoen)
  * Met de tweede query worden vervolgens de benodigde gegevens voor de visualisatie opgehaald, met inbegrip van de categorieën die voldoen aan de voorwaarde in de WHERE-component.  
  
  Dit voert meestal prima als er honderden of duizenden categorieën, zoals in dit voorbeeld. Prestaties kunnen echter afnemen als het aantal categorieën veel groter is (en inderdaad, dat de query mislukt als er meer dan een miljoen categorieën die voldoen aan de voorwaarde, vanwege de limiet van één miljoen-rijen die eerder zijn besproken).
* **TopN-filters:** U kunt geavanceerde filters definiëren om te filteren op alleen de bovenste (of onderste) N-waarden voor een bepaalde meting, bijvoorbeeld om in de bovenstaande visualisatie dat alleen de top 10 van categorieën op te nemen. Hiervoor moeten ook weer twee query's naar de onderliggende gegevensbron worden verzonden: De eerste query retourneert echter alle categorieën uit de onderliggende gegevensbron, waarna vervolgens de TopN wordt bepaald op basis van de geretourneerde resultaten. Afhankelijk van de kardinaliteit van de betrokken kolom, kan dit leiden tot prestatieproblemen (of mislukte query's door de limiet van 1 miljoen rijen).
* **Mediaan**: Over het algemeen wordt elke aggregatie (Sum, Count Distinct, enzovoort) naar de onderliggende gegevensbron gepusht. Dit geldt echter niet voor Median, omdat deze statistische functie doorgaans niet wordt ondersteund door de onderliggende gegevensbron. In dergelijke gevallen worden de detailgegevens opgehaald uit de onderliggende gegevensbron en wordt de mediaan berekend aan de hand van de geretourneerde resultaten. Dit is geen probleem wanneer de mediaan moet worden berekend voor een relatief klein aantal resultaten, maar prestatieproblemen (of mislukte query's door de limiet van 1 miljoen rijen) wordt uitgevoerd als de kardinaliteit groot is.  Zo kan het berekenen van de mediaan van het inwonertal van landen redelijk snel gaan, maar het berekenen van de mediaan van de verkoopprijs te lang duren.
* **Geavanceerde tekstfilters ('contains' en vergelijkbaar):** Bij het filteren op een tekstkolom zijn geavanceerde filters toegestaan zoals 'contains' en 'begins with'. Deze filters kunnen voor sommige gegevensbronnen zeker tot slechtere prestaties leiden. Het standaardfilter 'contains' moet in het bijzonder niet worden gebruikt als wat vereist is, is een exacte overeenkomst ('is' of 'is not'). Hoewel de resultaten mogelijk hetzelfde zijn, afhankelijk van de werkelijke gegevens, kunnen de prestaties aanzienlijk verschillen vanwege het gebruik van indexen.
* **Slicers met meervoudige selectie:** De standaardinstelling is dat in een slicer maar één selectie kan worden gemaakt. Het toestaan van meervoudige selectie in filters kan bepaalde prestatieproblemen veroorzaken. Als de gebruiker namelijk een verzameling items selecteert in de slicer (bijvoorbeeld de tien producten waarin hij is geïnteresseerd), moeten voor elke nieuwe selectie query's worden verzonden naar de bron in de back-end. Hoewel de gebruiker het volgende item kan selecteren terwijl de query nog niet is voltooid, leidt dit tot extra belasting van de onderliggende gegevensbron.

* **Overweeg om totalen in visuals uit te schakelen:** Standaard geven tabellen en matrices totalen en subtotalen weer. In veel gevallen moeten er afzonderlijke query's worden verzonden naar de onderliggende bron om de waarden voor deze totalen op te halen. Dit is van toepassing wanneer u gebruikmaakt van de samenvoeging *DistinctCount*, of in alle gevallen wanneer u DirectQuery gebruikt via SAP BW of SAP HANA. Dergelijke totalen moeten worden uitgeschakeld (met behulp van het deelvenster **Indeling**) als ze niet vereist zijn. 

### <a name="maximum-number-of-connections-option-for-directquery"></a>Optie voor een maximaal aantal verbindingen voor DirectQuery

U kunt instellen hoeveel verbindingen DirectQuery maximaal opent voor elke onderliggende gegevensbron; op deze manier kunt u bepalen hoeveel query's er gelijktijdig naar elke gegevensbron kunnen worden verzonden. 

De standaard maximum aantal gelijktijdige verbindingen die directquery wordt geopend is tien. U kunt het aantal voor het huidige bestand in **Power BI Desktop** wijzigen. Ga hiervoor naar **Bestand > Opties en instellingen > Opties**, ga naar het gedeelte **Huidig bestand** in het linkerdeelvenster en selecteer **DirectQuery**. 

![Een maximaal aantal DirectQuery-verbindingen inschakelen](media/desktop-directquery-about/directquery-about_05b.png)

Deze instelling wordt alleen ingeschakeld als er ten minste één DirectQuery-gegevensbron in het huidige rapport staat. De waarde is van toepassing op alle DirectQuery-bronnen en op eventuele nieuwe DirectQuery-bronnen die worden toegevoegd aan hetzelfde rapport.

Als u het **maximale aantal verbindingen** vergroot, kunnen er meer query's (tot het maximumaantal dat is opgegeven) worden verzonden naar de onderliggende gegevensbron, wat nuttig is als er meerdere visuals op één pagina staan, of als veel gebruikers een rapport tegelijk bekijken. Wanneer het maximale aantal verbindingen is bereikt, worden aanvullende query's in een wachtrij geplaatst tot er weer een verbinding beschikbaar is. Als u de limiet verhoogt, resulteert dit in een grotere belasting voor de onderliggende bron. Met de instelling worden de algehele prestaties dus niet gegarandeerd beter.

Wanneer er een rapport wordt gepubliceerd, is het maximale aantal query's dat gelijktijdig naar de onderliggende gegevensbron kan worden verzenden ook afhankelijk van de vastgestelde limieten. Deze limieten zijn afhankelijk van de doelomgeving waarin het rapport wordt gepubliceerd. In verschillende omgevingen (zoals Power BI, Power BI Premium en Power BI Report Server) kunnen verschillende beperkingen gelden.

### <a name="diagnosing-performance-issues"></a>Oorzaak van prestatieproblemen achterhalen
In dit gedeelte wordt beschreven hoe u de oorzaak van prestatieproblemen kunt achterhalen of hoe u meer gedetailleerde informatie kunt verzamelen met als doel de rapporten te optimaliseren.

Het wordt ten zeerste aangeraden om een diagnose van prestatieproblemen te beginnen in **Power BI Desktop**, niet in de **Power BI-service**. Het is vaak het geval dat prestatieproblemen het gevolg zijn van het prestatieniveau van de onderliggende gegevensbron. Deze problemen zijn eenvoudiger te identificeren en op te lossen in de meer geïsoleerde omgeving van **Power BI Desktop** en bovendien worden direct al bepaalde onderdelen uitgesloten (zoals de Power BI-gateway). Alleen als de prestatieproblemen niet optreden met Power BI Desktop moet de aandacht worden verlegd naar de details van het rapport in de Power BI-service.

Zo is het ook beter om eerst te proberen het probleem te beperken tot een bepaalde visualisatie, in plaats van een groot aantal visualisaties op dezelfde pagina.

Laten we er gemakshalve vanuit gaan dat die stappen (uit de vorige alinea's in dit gedeelte) zijn doorlopen en dat we het probleem hebben beperkt tot één visualisatie op een pagina in **Power BI Desktop** die nog steeds traag is. Om te zien welke query's naar de onderliggende gegevensbron worden verstuurd door Power BI Desktop, is het mogelijk om traceringen/diagnostische gegevens te bekijken die mogelijk door die bron worden verzonden. Dergelijke traceringen of traces bevatten mogelijk ook nuttige informatie over de manier waarop de query is uitgevoerd en hoe deze kan worden verbeterd.

Zelfs in de afwezigheid van dergelijk traceringen van de bron, is het mogelijk om de query's weer te geven die zijn verzonden door Power BI, samen met hun uitvoeringstijden, zoals hieronder wordt beschreven.

#### <a name="determining-the-queries-sent-by-power-bi-desktop"></a>Bepalen welke query's zijn verzonden door Power BI Desktop
De standaardinstelling is dat er tijdens een sessie gebeurtenissen worden vastgelegd door **Power BI Desktop**. Deze worden opgeslagen in het traceringsbestand FlightRecorderCurrent.trc.

Voor sommige **DirectQuery**-bronnen bevat dit logboek alle query's die zijn verzonden naar de onderliggende gegevensbron (de resterende DirectQuery-bronnen worden in de toekomst toegevoegd). Dit zijn de bronnen waarvoor de verzonden query's in het logboek worden vermeld:

* SQL Server
* Azure SQL Database
* Azure SQL Data Warehouse
* Oracle
* Teradata
* SAP HANA

Het traceringsbestand vindt u in de map **AppData** voor de huidige gebruiker:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces

Dit is een eenvoudige manier om bij de deze map te openen: Open **Power BI Desktop** en selecteer **Bestand > Opties en instellingen > Opties** > **Diagnostische gegevens**. Het volgende dialoogvenster wordt weergegeven:

![](media/desktop-directquery-about/directquery-about_06.png)

Als u de koppeling *Map met traceringen openen* selecteert, onder **Diagnostische opties**, wordt de volgende map geopend:

    \<User>\AppData\Local\Microsoft\Power BI Desktop\Traces

Als u naar de bovenliggende map van die map navigeert, komt u in een map met *AnalysisServicesWorkspaces*, met daarin één werkruimte-submap voor elk geopend exemplaar van **Power BI Desktop**. Deze submappen hebben een naam met een achtervoegsel dat bestaat uit een geheel getal, zoals *AnalysisServicesWorkspace2058279583*.

In deze map bevindt zich een submap *\\Data*, die het traceringsbestand FlightRecorderCurrent.trc bevat voor de huidige Power BI-sessie. De bijbehorende werkruimtemap wordt verwijderd wanneer de bijbehorende sessie van Power BI Desktop wordt beëindigd.

De traceringsbestanden kunnen worden gelezen met het hulpprogramma **SQL Server Profiler**, dat gratis kan worden gedownload als onderdeel van **SQL Server Management Studio**. U kunt het programma [hier downloaden](https://msdn.microsoft.com/library/mt238290.aspx).

Nadat u **SQL Server Management Studio** hebt gedownload en geïnstalleerd, voert u **SQL Server Profiler** uit.

![](media/desktop-directquery-about/directquery-about_07.png)

Ga als volgt te werk om het traceringsbestand te openen:

1. Selecteer in **SQL Server Profiler** achtereenvolgens **File > Open > Trace file**.
2. Voer het pad in naar het traceringsbestand voor de momenteel geopende Power BI-sessie, zoals:
   
         C:\Users\<user>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data
3. Open FlightRecorderCurrent.trc

Alle gebeurtenissen uit de huidige sessie worden weergegeven. Hieronder ziet u een voorbeeld waarin groepen gebeurtenissen zijn gemarkeerd. Voor elke groep zijn de volgende gegevens vastgelegd:

* Een gebeurtenis *Query Begin* en *Query End*, die het begin en het einde aangeven van een DAX-query die is gegenereerd door de gebruikersinterface (bijvoorbeeld van een visualisatie of door het invullen van een lijst met waarden in de filterinterface).
* Een of meer sets gebeurtenissen *DirectQuery Begin* en *DirectQuery End*, die een query voorstellen die is verzonden naar de onderliggende gegevensbron, als onderdeel van het evalueren van de DAX-query.

Er kunnen meerdere DAX-query's tegelijk worden uitgevoerd, wat betekent dat gebeurtenissen uit verschillende groepen elkaar kunnen overlappen. Aan de hand van de waarde van de ActivityID kan worden vastgesteld welke gebeurtenissen bij dezelfde groep horen.

![](media/desktop-directquery-about/directquery-about_08.png)

Andere interessante kolommen zijn als volgt:

* **TextData:** De tekstinhoud van de gebeurtenis. Voor 'Query Begin/End'-gebeurtenissen ziet u hier de DAX-query. Dit is voor ' DirectQuery Begin/End '-gebeurtenissen, de SQL-query naar de onderliggende gegevensbron verzonden. De TextData voor de geselecteerde gebeurtenis wordt ook onder aan het venster weergegeven.
* **EndTime:** Wanneer de gebeurtenis is voltooid.
* **Duration:** De duur in milliseconden die nodig is voor het uitvoeren van de DAX- of SQL-query.
* **Error:** Geeft aan of er een fout is opgetreden (in dat geval wordt de gebeurtenis ook in rood weergegeven).

In de bovenstaande afbeelding zijn enkele minder interessante kolommen smaller gemaakt, zodat de interessante kolommen beter te lezen zijn.

Dit is de aanbevolen aanpak voor het vastleggen van een tracering die u kan helpen bij het analyseren van een mogelijk prestatieprobleem:

* Open één **Power BI Desktop**-sessie (om verwarring door meerdere werkruimtemappen te voorkomen).
* Voer in **Power BI Desktop** de reeks acties uit waarin u bent geïnteresseerd. Voer nog enkele aanvullende acties uit, zodat u zeker weet dat de interessante gebeurtenissen worden weggeschreven naar het traceringsbestand.
* Open **SQL Server Profiler** en bekijk de tracering, volgens de eerder beschreven instructies. Vergeet niet dat het traceringsbestand wordt verwijderd zodra u **Power BI Desktop** afsluit. Ook verdere acties in Power BI Desktop niet meteen weergegeven: het traceringsbestand moet worden gesloten en heropend als u wilt zien van de nieuwe gebeurtenissen.
* Gebruik redelijk kleine, afzonderlijke sessies (met tien seconden aan acties en niet honderden) om het traceringsbestand makkelijker te kunnen interpreteren (en omdat er een limiet geldt voor de grootte van het traceringsbestand, waardoor het bij lange sessies mogelijk is dat er vroege gebeurtenissen worden verwijderd).

#### <a name="understanding-the-form-of-query-sent-by-power-bi-desktop"></a>Indeling van query's die worden verzonden door Power BI Desktop
De algemene indeling van query's die worden gemaakt en verzonden door **Power BI Desktop** is dat er subselecties worden gebruikt voor elk van de tabellen waarnaar wordt verwezen, waarbij de subselectie overeenkomt met de query die is gedefinieerd in **Query-editor**. Stel dat de volgende TPC DS-tabellen aanwezig zijn in SQL Server:

![](media/desktop-directquery-about/directquery-about_09.png)

Laten we nu eens naar deze query kijken:

![](media/desktop-directquery-about/directquery-about_10.png)

Deze query levert de volgende visualisatie op:

![](media/desktop-directquery-about/directquery-about_11.png)

Het vernieuwen van deze visualisatie resulteert in de SQL-query die wordt weergegeven onder de volgende alinea. Zoals u ziet, zijn er drie subselecties voor Web Sales, Item en Date_dim, die elk alle kolommen uit de bijbehorende tabel retourneren, ook al worden er maar vier kolommen daadwerkelijk gebruikt voor de visualisatie. Deze query's in de subselecties (ze zijn gearceerd) zijn exact het resultaat van de query's die zijn gedefinieerd in **Query-editor**. Het op deze manier gebruiken van subselecties is niet nadelig gebleken voor de prestaties, althans niet voor de gegevensbronnen die tot nu toe worden ondersteund voor DirectQuery. Gegevensbronnen, zoals SQL Server optimaliseren onmiddellijk de verwijzingen naar de andere kolommen.

Eén reden waarom in Power BI dit patroon wordt gehanteerd, is omdat de gebruikte SQL-query direct kan worden opgegeven door de analist. De query wordt dus gebruikt 'as is', zonder een poging om deze te herschrijven.

![](media/desktop-directquery-about/directquery-about_12.png)

## <a name="next-steps"></a>Volgende stappen
In dit artikel worden de aspecten van **DirectQuery** beschreven die door alle gegevensbronnen worden gedeeld. Er zijn echter ook bepaalde gegevens die specifiek zijn voor bepaalde gegevensbronnen. Raadpleeg de volgende artikelen voor informatie over deze specifieke bronnen:

* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)

Raadpleeg het volgende artikel voor meer informatie over **DirectQuery**:

* [Gegevensbronnen die worden ondersteund door DirectQuery](desktop-directquery-data-sources.md)

