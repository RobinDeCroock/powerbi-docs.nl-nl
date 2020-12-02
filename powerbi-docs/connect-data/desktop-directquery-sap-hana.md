---
title: DirectQuery voor SAP HANA in Power BI
description: Overwegingen bij het gebruik van DirectQuery met SAP HANA
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/10/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: f6cb4fa1ee35754d8ffe468ddb845089f26045a9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411167"
---
# <a name="connect-to-sap-hana-data-sources-by-using-directquery-in-power-bi"></a>Verbinding maken met SAP HANA-gegevensbronnen met DirectQuery in Power BI
Met behulp van **DirectQuery** kunt u rechtstreeks verbinding maken met **SAP HANA**-gegevensbronnen. Er zijn twee opties om verbinding te maken met SAP HANA:

* **SAP HANA behandelen als een multidimensionale bron (standaard):**  In dit geval is het gedrag vergelijkbaar met dat van Power BI wanneer Power BI verbinding maakt met andere multi-dimensionale bronnen, bijvoorbeeld SAP Business Warehouse of Analysis Services. Als u verbinding maakt met SAP HANA met behulp van deze instelling, wordt er één analytische of berekeningsweergave geselecteerd en alle metingen, hiërarchieën en kenmerken in dat overzicht zijn beschikbaar in de lijst met velden. Terwijl er visuele elementen worden gemaakt, worden de samengevoegde gegevens altijd opgehaald uit SAP HANA. Dit is de aanbevolen aanpak en standaard voor nieuwe DirectQuery-rapporten via SAP HANA.

* **SAP HANA behandelen als een relationele bron:** In dit geval behandelt Power BI SAP HANA als een relationele bron. Dit biedt meer flexibiliteit. Zorg er echter wel voor dat metingen worden samengevoegd zoals verwacht en vermijd prestatieproblemen.

De benadering die wordt gebruikt om verbinding te maken, wordt bepaald door een algemeen hulpmiddel dat u als volgt instelt. Selecteer **Bestand > Opties en instellingen**, kies vervolgens **Opties > DirectQuery** en selecteer tot slot de optie **SAP HANA behandelen als een relationele bron**, zoals hieronder in de afbeelding wordt weergegeven. 

![Schermopname van het dialoogvenster Opties, waarin de DirectQuery-opties worden weergegeven.](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

De optie om SAP HANA als relationele bron te behandelen, bepaalt de benadering die wordt gebruikt voor *nieuwe* rapporten met behulp van DirectQuery via SAP HANA. Deze optie heeft geen effect op bestaande SAP HANA-verbindingen in het huidige rapport, noch op verbindingen in andere geopende rapporten. Dus als de optie momenteel niet is aangevinkt, wordt een nieuwe verbinding die aan SAP HANA wordt toegevoegd met behulp van **Gegevens ophalen**, gemaakt met SAP HANA als multi-dimensionale bron. Als er echter een ander rapport wordt geopend dat ook verbinding maakt met SAP HANA, blijft dat rapport zich gedragen volgens de optie die is ingesteld *op het moment dat het rapport werd gemaakt*. Dit betekent dat rapporten die verbinding maken met SAP HANA en die vóór februari 2018 zijn gemaakt, SAP HANA blijven behandelen als een relationele bron. 

De twee benaderingen laten verschillend gedrag zien, en het is dan ook niet mogelijk om de benadering van een bestaand rapport te wijzigen. 

We gaan beide benaderingen grondiger bekijken.

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>SAP HANA behandelen als een multi-dimensionale bron (standaard)

Deze verbindingsmethode wordt standaard gebruikt voor alle nieuwe verbindingen met SAP HANA, waarbij SAP HANA wordt behandeld als een multi-dimensionale bron. Als u een verbinding met SAP HANA als relationele bron wilt behandelen, moet u **Bestand > Opties en instellingen > Opties** selecteren en het vakje onder **DirectQuery > SAP HANA behandelen als een relationele bron** inschakelen. Hoewel deze functie beschikbaar is als **Preview**-versie, kunnen rapporten die gebruikmaken van de multi-dimensionale benadering *niet* worden gepubliceerd in de Power BI-service. Als u dat wel doet, levert dat fouten op wanneer het rapport wordt geopend in de Power BI-service.  

Wanneer u verbinding maakt met SAP HANA als een multidimensionale bron, is het volgende van toepassing:

* In de navigator **Gegevens ophalen** kan één SAP HANA-weergave worden geselecteerd. Het is niet mogelijk om afzonderlijke metingen of kenmerken te selecteren. Op het moment van verbinden is er geen query gedefinieerd, wat niet het geval is bij het importeren van gegevens of wanneer DirectQuery wordt gebruikt wanneer SAP HANA als relationele bron wordt behandeld. Dit betekent ook dat het niet mogelijk is om rechtstreeks een SAP HANA SQL-query te gebruiken wanneer deze verbindingsmethode is geselecteerd.

* Alle metingen, hiërarchieën en kenmerken van de geselecteerde weergave worden weergegeven in de lijst met velden. 

* Als een meting wordt gebruik in een visual, wordt SAP HANA gevraagd om de berichtwaarde op te halen op het aggregatieniveau dat nodig is voor de visual. Dus wanneer er sprake is van niet-additieve metingen (tellers, ratio's, enzovoort) worden alle samenvoegingen uitgevoerd door SAP HANA en wordt er verder geen samenvoeging uitgevoerd door Power BI. 

* Er moeten bepaalde beperkingen worden opgelegd om ervoor te zorgen dat de juiste samengevoegde waarden altijd kunnen worden opgehaald van SAP HANA. Het is bijvoorbeeld niet mogelijk om berekende kolommen toe te voegen of om gegevens van meerdere SAP HANA-weergaven binnen hetzelfde rapport te combineren. 

SAP HANA behandelen als een multi-dimensionale bron biedt niet de grotere flexibiliteit die wordt geleverd door de alternatieve *relationele* benadering, maar het is eenvoudiger en zorgt voor correcte samengevoegde waarden voor complexere SAP HANA-metingen en resulteert over het algemeen in hogere prestaties. 

De lijst met **velden** bevat alle metingen, kenmerken en hiërarchieën uit de SAP HANA-weergave. Houd rekening met de volgende gedragingen die van toepassing zijn wanneer u deze verbindingsmethode gebruikt:

* Elk kenmerk dat is opgenomen in ten minste één hiërarchie wordt standaard verborgen. Als het nodig is, kunnen deze echter wel worden weergegeven door **Verborgen opties weergeven** te selecteren in het contextmenu in de lijst met velden. In hetzelfde contextmenu kunnen ze, indien nodig, zichtbaar worden gemaakt.

* In SAP HANA kan een kenmerk worden gedefinieerd om een ander kenmerk als label te gebruiken. Een **Product** (met de waarden 1, 2, 3, enzovoort) kan bijvoorbeeld **ProductName** (met de waarden Fiets, Shirt, Handschoenen, enzovoort) als label gebruiken. In dit geval wordt er één veld, **Product**, weergegeven in de lijst met velden, waarvan de waarden de labels Fiets, Shirt, Handschoenen, enzovoort zijn, maar dat wordt gesorteerd op, en met uniekheid bepaald door, de sleutelwaarden 1, 2, 3. Er wordt ook een verborgen kolom **Product.Key** gemaakt, zodat er, indien nodig, toegang tot de onderliggende sleutelwaarden kan worden verkregen. 

Eventuele variabelen die zijn gedefinieerd in de onderliggende SAP HANA-weergave, worden weergegeven op het moment van verbinden, waarna de vereiste waarden kunnen worden ingevoerd. Die waarden kunnen vervolgens worden gewijzigd door **Query's bewerken** te selecteren vanuit het lint en door vervolgens **Parameters beheren** te selecteren in de vervolgkeuzelijst die wordt weergegeven. 

De toegestane modelleringsbewerkingen zijn restrictiever dan dat normaal is wanneer er gebruik wordt gemaakt van DirectQuery, omdat ervoor moet worden gezorgd dat de juiste samengevoegde gegevens kunnen worden opgehaald van SAP HANA. Het is echter nog steeds mogelijk om vele toevoegingen te doen en wijzigingen aan te brengen, waaronder metingen definiëren, velden hernoemen en verbergen en weergave-indelingen maken. Al die veranderingen worden bewaard na vernieuwing en niet-conflicterende wijzigingen in de SAP HANA-weergave worden toegepast. 

### <a name="additional-modeling-restrictions"></a>Extra modelleringsbeperkingen

De primaire extra modelleringsbeperkingen bij het verbinden met SAP HANA met behulp van DirectQuery (behandeld als multi-dimensionale bron) zijn als volgt: 

* **Geen ondersteuning voor berekende kolommen:** de mogelijkheid voor het maken van berekende kolommen is uitgeschakeld. Dit betekent ook dat Groeperen en Clustering, waarmee berekende kolommen worden gemaakt, niet beschikbaar zijn.
* **Aanvullende beperkingen voor metingen:** Er zijn extra beperkingen voor de DAX-expressies die kunnen worden gebruikt in metingen, overeenkomstig het door SAP HANA geboden ondersteuningsniveau.
* **Geen ondersteuning voor het definiëren van relaties:** In een rapport kunnen query's slechts voor één weergave worden uitgevoerd. Daarom wordt het definiëren van relaties niet ondersteund.
* **Geen gegevensweergave:** De **Gegevensweergave** geeft normaal gesproken de gegevens op detailniveau weer in de tabellen. Gezien de aard van OLAP-bronnen zoals SAP HANA, is deze weergave niet beschikbaar via SAP HANA.
* **Kolom- en metingsdetails zijn vast:** De lijst met kolommen en metingen in de lijst met velden wordt bepaald door de onderliggende gegevensbron en kan niet worden gewijzigd. Het is bijvoorbeeld niet mogelijk om een kolom te verwijderen of het gegevenstype ervan te wijzigen (de naam kan wel worden gewijzigd).
* **Aanvullende beperkingen in DAX:** Er zijn extra beperkingen met betrekking tot de DAX die kunnen worden gebruikt in metingdefinities, in overeenstemming met beperkingen in de bron. Het is bijvoorbeeld niet mogelijk om een statistische functie over een tabel te gebruiken.

### <a name="additional-visualization-restrictions"></a>Extra visualisatiebeperkingen

Er zijn beperkingen in visuals bij het verbinden met SAP HANA met behulp van DirectQuery (behandeld als multi-dimensionale bron): 
* **Geen aggregatie van kolommen:** Het is niet mogelijk de aggregatie voor een kolom in een visual te wijzigen, deze is altijd *Niet samenvatten*.

## <a name="treat-sap-hana-as-a-relational-source"></a>SAP HANA behandelen als een relationele bron 

Wanneer u ervoor kiest om met SAP HANA als een relationele bron verbinding te maken, is er meer flexibiliteit. U kunt bijvoorbeeld berekende kolommen maken, gegevens opnemen uit meerdere SAP HANA-weergaven en relaties tussen de resulterende tabellen maken. Wanneer u SAP HANA op deze manier gebruikt, is het belangrijk om bepaalde aspecten te begrijpen van hoe verbindingen worden behandeld om zo voor het volgende te zorgen: 

* De resultaten zijn zoals ze worden verwacht als de SAP HANA-weergave niet-additieve metingen bevat (bijvoorbeeld unieke tellingen, of gemiddelden, in plaats van eenvoudige optellingen).
* De resulterende query's efficiënt zijn

Het is nuttig om het gedrag uit te leggen van een relationele bron als SQL Server als de query die in **Gegevens ophalen** of **Query-editor** is gedefinieerd, een aggregatie uitvoert. In het volgende voorbeeld retourneert een in **Query-editor** gedefinieerde query de gemiddelde prijs door middel van *ProductID*.  

![Diagram met een query die in de Query-editor is gedefinieerd waarmee de gemiddelde prijs wordt geretourneerd door middel van ProductID.](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Als de gegevens in Power BI worden geïmporteerd (versus gebruik van DirectQuery), gebeurt er het volgende:

* De gegevens worden geïmporteerd op het aggregatieniveau dat is gedefinieerd door de in **Query-editor** gemaakte query. Bijvoorbeeld gemiddelde prijs per product. Dit leidt tot een tabel met de twee kolommen *ProductID* en *AveragePrice*, die in visuele elementen kunnen worden gebruikt.
* In een visueel element wordt elke volgende samenstelling (zoals *Som*, *Gemiddelde*, *Minus* en overige) uitgevoerd op die geïmporteerde gegevens. Als bijvoorbeeld *AveragePrice* in een visual wordt opgenomen, wordt standaard de samenstelling *Som* gebruikt en wordt de som van *AveragePrice* voor elke *ProductID* geretourneerd, wat in dit voorbeeld 13,67 is. Het zelfde geldt voor elke alternatieve samengestelde functie (zoals *Minus*, *Gemiddelde* enzovoort) die voor het visuele element wordt gebruikt. Bijvoorbeeld: het *gemiddelde* van *AveragePrice* retourneert het gemiddelde van 6,66, 4 en 3, wat gelijk is aan 4,56 en niet het gemiddelde van *Price* van de zes records in de onderliggende tabel, wat 5,17 is.
  
Als **DirectQuery** (via diezelfde relationele bron) wordt gebruikt in plaats van Importeren, is dezelfde semantiek van toepassing en zouden de resultaten precies dezelfde zijn:  

* Gegeven dezelfde query worden logisch gezien exact de dezelfde gegevens aan de rapporterende laag gepresenteerd, hoewel de gegevens niet feitelijk worden geïmporteerd.

* In een visueel element wordt elke volgende samenstelling (*Som*, *Gemiddelde*, *Minus* en overige) opnieuw uitgevoerd voor die logische tabel van de query. En ook hier wordt in een visueel element met een *gemiddelde* van *AveragePrice* de waarde 4,56 geretourneerd.
  
Neem nu SAP HANA eens in overweging wanneer de verbinding wordt behandeld als een relationele bron. Power BI werkt in SAP HANA zowel met *analytische weergaven* als *berekeningsweergaven*. Beide kunnen metingen bevatten. Tegenwoordig volgt de werkwijze voor SAP HANA dezelfde principes die eerder in deze sectie zijn beschreven: de query die wordt gedefinieerd in **Gegevens ophalen** of **Query-editor**, bepaalt de beschikbare gegevens. Vervolgens vindt elke volgende samenstelling in een visueel element van die gegevens plaats. Hetzelfde geldt voor zowel Importeren als DirectQuery.  
Gezien de aard van SAP HANA is de query die in het eerste dialoogvenster **Gegevens ophalen** of **Query-editor** is gedefinieerd, echter altijd een combinatiequery. Deze bevat gewoonlijk alle metingen waarbij de feitelijk te gebruiken samenstelling door de SAP HANA-weergave wordt gedefinieerd.

Het equivalent van SQL Server in bovenstaand voorbeeld is dat er een SAP HANA-weergave is die *ID*, *ProductID*, *DepotID*, en metingen bevat, inclusief *AveragePrice*, gedefinieerd in de weergave als *Average of Price*.  
    
Als in **Gegevens ophalen** de gemaakte selecties voor **ProductID** en de meting **AveragePrice** zijn, dan wordt er een query over de weergave gedefinieerd, waarbij die samengestelde gegevens worden gevraagd (in het eerdere voorbeeld wordt ter verduidelijking pseudo-SQL gebruikt, wat niet overeenkomt met de exacte syntaxis van SAP HANA SQL). Vervolgens aggregeren eventuele verdere samenstellingen die in een visueel element worden gedefinieerd de resultaten van een dergelijke query. Dit is, net zoals hierboven beschreven voor SQL Server, opnieuw van toepassing op zowel het geval Importeren als DirectQuery. In het geval van DirectQuery wordt de query uit **Gegevens ophalen** of **Query-editor** gebruikt in een subselectie binnen één query die naar SAP HANA wordt verzonden. Het is dus niet feitelijk zo dat alle gegevens worden ingelezen voordat ze verder worden samengesteld.  

Al deze overwegingen en gedragen maken de volgende belangrijke overwegingen nodig wanneer u van DirectQuery via SAP HANA gebruikmaakt:  

* Er moet worden gelet op verdere samenstellingen die in visuele elementen worden uitgevoerd zodra de meting in SAP HANA niet-additief is (bijvoorbeeld geen eenvoudige *Som*, *Minus* of *Max*).

* In **Gegevens ophalen** of **Query-editor** mogen alleen de vereiste kolommen worden opgenomen om de vereiste gegevens op te halen. Dit weerspiegelt het feit dat het resultaat een query is en een redelijke query is die naar SAP HANA kan worden verzonden. Als bijvoorbeeld tientallen kolommen zouden worden geselecteerd (die eventueel nodig kunnen zijn voor verdere visuele elementen), dan houdt een eenvoudig visueel element ook voor DirectQuery in dat de in de subselectie gebruikte combinatiequery tientallen kolommen bevat, die over het algemeen slecht presteren.
  
We kijken naar een voorbeeld. In het volgende voorbeeld worden naast de meting *OrderQuantity* vijf kolommen geselecteerd in het dialoogvenster **Gegevens ophalen**: **CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**. Dit betekent dat als er later een eenvoudige visual wordt gemaakt met Minus OrderQuantity, dit resulteert in de volgende SQL-query naar SAP HANA. Het gearceerde gedeelte is de subselectie. Deze bevat de query van **Gegevens ophalen** / **Query-editor**. Als de subselectie een resultaat oplevert met hoge kardinaliteit, dan zijn de prestaties van SAP HANA waarschijnlijk erg slecht.  

![Schermopname van een queryvoorbeeld waarin de SQL-query naar SAP HANA wordt weergegeven.](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Vanwege dit gedrag wordt het aangeraden dat de in **Gegevens ophalen** of **Query-editor** geselecteerde items worden beperkt tot die items die nodig zijn, terwijl er nog wel een redelijke query voor SAP HANA uitrolt.  

## <a name="best-practices"></a>Aanbevolen procedures 

Voor beide benaderingen om met SAP HANA verbinding te maken, gelden de aanbevelingen voor het gebruik van DirectQuery ook voor SAP HANA, in het bijzonder die zijn gerelateerd aan het waarborgen van goede prestaties. Deze aanbevelingen zijn uitgebreid beschreven in het artikel [DirectQuery gebruiken in Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Beperkingen

De volgende lijst bevat alle SAP HANA-functies die niet volledig worden ondersteund of functies die zich anders gedragen bij gebruik van Power BI. 

* **Bovenliggende/onderliggende hiërarchieën**: bovenliggende/onderliggende hiërarchieën zijn niet zichtbaar in Power BI.
Dit is omdat Power BI toegang krijgt tot SAP HANA via de SQL-interface en er kan via SQL geen volledige toegang verkregen worden tot bovenliggende/onderliggende hiërarchieën.
* **Andere hiërarchiemetagegevens**: de basisstructuur van hiërarchieën wordt weergegeven in Power BI, maar sommige hiërarchiemetagegevens (zoals het gedrag controleren van niet-aaneengesloten hiërarchieën) hebben geen effect.
Ook dit komt door de beperkingen die door de SQL-interface zijn opgelegd.
* **Verbinding met SSL**: u kunt verbinding maken met behulp van importeren en multidimensie met SSL, maar u kunt geen verbinding maken met SAP HANA-exemplaren die zijn geconfigureerd voor het gebruik van SSL voor de relationele connector.
* **Ondersteuning voor kenmerkweergaven**: Power BI kan verbinding maken met analytische en berekeningsweergaven, maar niet rechtstreeks met kenmerkweergaven.
* **Ondersteuning voor catalogusobjecten**: Power BI kan geen verbinding met de catalogusobjecten.
* **Variabelen wijzigen na publicatie**: nadat het rapport is gepubliceerd, kunt u de waarden van SAP HANA-variabelen niet meer rechtstreeks wijzigen in de Power BI-service. 
 
## <a name="known-issues"></a>Bekende problemen 
De volgende lijst bevat alle bekende problemen die zich voor kunnen doen bij het verbinden met SAP HANA (DirectQuery) met behulp van Power BI. 

* **SAP HANA-probleem bij query voor tellers en andere metingen**: onjuiste gegevens worden geretourneerd door SAP HANA wanneer er verbinding wordt gemaakt met een analytische weergave en er in dezelfde visual een tellermeting en een andere ratiometing wordt opgenomen. Dit wordt behandeld in SAP-notitie 2128928 (Onverwachte resultaten bij het uitvoeren van een query voor een berekende kolom en een teller). In dit geval is de ratiometing onjuist. 

* **Meerdere Power BI-kolommen van één SAP HANA-kolom**: SAP HANA beschrijft sommige berekeningsweergaven waar een SAP HANA-kolom wordt gebruikt in meer dan één hiërarchie als twee afzonderlijke kenmerken. Dit resulteert erin dat er twee kolommen in Power BI worden gemaakt.  Deze kolommen zijn echter standaard verborgen en alle query's die betrekking hebben op de hiërarchieën, of rechtstreeks op de kolommen, gedragen zich correct. 
 
## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende bronnen voor meer informatie over DirectQuery:

* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](power-bi-data-sources.md) (Gegevensbronnen die worden ondersteund door DirectQuery)
* [DirectQuery and SAP BW](desktop-directquery-sap-bw.md) (DirectQuery en SAP BW)
* [On-premises data gateway](service-gateway-onprem.md) (On-premises gegevensgateway)
