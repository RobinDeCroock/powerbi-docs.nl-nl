---
title: Tips en trucs voor het maken van rapporten in Power BI
description: Informatie over aanbevolen procedures voor het maken van rapporten in de Power BI-service en Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: willthom
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
ms.openlocfilehash: 41e5ff75e9b6fd48e3101d30999e8d570f34a270
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514039"
---
# <a name="tips-and-tricks-for-creating-reports-in-power-bi-desktop"></a>Tips en trucs voor het maken van rapporten in Power BI Desktop
Als uw gegevens optimaal te kunnen gebruiken, hebt u soms wat extra hulp nodig. We hebben een aantal tips en trucs voor u verzameld om u te helpen bij het maken van rapporten in Microsoft Power BI Desktop *en* in Pro-Plus-edities van Microsoft Excel 2016 of Excel 2013 waar de Power Pivot-invoegtoepassing is ingeschakeld en Power Query is geïnstalleerd en ingeschakeld. 

## <a name="learning-to-use-the-query-editor"></a>De Query Editor leren gebruiken
De Query Editor in Power BI Desktop is vergelijkbaar met de Power Query-invoegtoepassing in Excel 2013. Hoewel er verschillende nuttige artikelen in te vinden zijn via de ondersteuning voor Power BI, kan het nuttig zijn de Power Query-documentatie op support.office.com raad te plegen voor een eerste introductie.

U kunt voor aanvullende informatie terecht bij het [Power Query Resource Center](https://support.office.com/article/Microsoft-Power-Query-for-Excel-Help-2b433a85-ddfb-420b-9cda-fe0e60b82a94).

U kunt ook de [Naslaginformatie voor formules](https://support.office.com/Article/Learn-about-Power-Query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f) bekijken.

## <a name="data-types-in-query-editor"></a>Gegevenstypes in de Query Editor
Wanneer u de Query Editor in Power BI Desktop gebruikt om gegevens te laden, bepalen wij zo goed mogelijk wat voor type gegevens het zijn. Wanneer u formules gebruikt, blijven kolominstellingen voor het gegevenstype soms niet behouden. Zorg ervoor dat het gegevenstype van kolommen juist zijn hierna de volgende bewerkingen:  Gegevens voor het eerst naar het query-tabblad laden, Eerste rij als kop, Kolom toevoegen, Groeperen op, Samenvoegen en Toevoegen en voordat u de eerste keer drukt om de gegevens te laden.

Het is belangrijk om het volgende te onthouden: als gegevens cursief worden weergegeven in het gegevensraster, betekent dit niet dat het gegevenstype correct is ingesteld, alleen dat de gegevens niet als tekst worden beschouwd.

## <a name="reference-queries-in-the-query-editor"></a>Naar query's verwijzen in de Query Editor
In Query-Editor-navigator in Power BI Desktop, wanneer u met de rechtermuisknop op een van de query's, een optie "Verwijzingen" is beschikbaar. Dit is nuttig vanwege de volgende reden:

* Wanneer u bestanden als gegevensbron voor een query gebruikt, wordt het absolute pad naar het bestand opgeslagen in de query. Wanneer u het Power BI Desktop-bestand of de Excel-werkmap deelt of verplaatst, bespaart u tijd wanneer u de paden met één handeling kunt bijwerken in plaats van per pad.

Standaard voeren alle query's hun gegevens uit naar een Excel-werkblad of een gegevensmodel (of beide). Aantal query's vormen tussenliggende stappen en niet is bedoeld voor eindgebruikers. Wanneer u naar query's verwijst zoals hierboven wordt beschreven, is dit vaak het geval. U kunt het laden van gedrag met de rechtermuisknop op de query in de navigator bij het omschakelen van de optie 'Laden inschakelen' query beheren. Wanneer *laden inschakelen* heeft geen een vinkje naast het, de query is nog steeds beschikbaar in het query-tabblad en kunt u deze gebruiken met andere query's. Dit is vooral nuttig in combinatie met de transformatiehandelingen Samenvoegen, Toevoegen en Verwijzen. Omdat de query-resultaten niet naar het gegevensmodel worden geladen, wordt de query echter niet opgenomen in uw lijst met rapportvelden of uw gegevensmodel. 

## <a name="scatter-charts-need-a-point-identifier"></a>Spreidingsdiagrammen hebben een punt-id nodig
We gebruiken hier een voorbeeld van een eenvoudige tabel met temperaturen en de tijdstippen waarop deze zijn uitgelezen. Als u deze gegevens rechtstreeks tot een spreidingsdiagram verwerkt, brengt Power BI alle waarden samen tot een centraal punt. Als u wilt weergeven van afzonderlijke gegevenspunten, moet u een veld ook toevoegen aan de bucket Details in het veld. Een eenvoudige manier om dit te doen is door in Power BI Desktop op het querytabblad de optie Indexkolom toevoegen op het lint Kolom toevoegen te gebruiken. 

## <a name="reference-lines-in-your-report"></a>Referentielijnen in uw rapport
U kunt een berekende kolom in Power BI Desktop gebruiken om een referentielijn te definiëren. Bepaal welke tabel en kolom waar u een referentielijn wilt maken. Selecteer in het lint 'Nieuwe kolom' en typ in de formulebalk de volgende formule:

    Target Value = 100

Deze berekende kolom retourneert de waarde 100, ongeacht waar deze wordt gebruikt. De nieuwe kolom wordt weergegeven in de veldenlijst. Voeg de berekende kolom Doelwaarde toe aan een lijndiagram om weer te geven hoe een reeks zich verhoudt tot die specifieke referentielijn. 

## <a name="sort-by-another-column"></a>Sorteren op een andere kolom
Wanneer u in Power BI een categorische (tekenreeks)waarde gebruikt voor grafiekassen of in een slicer of filter, wordt standaard op alfabetische volgorde gesorteerd. Als u onderdrukken deze volgorde wilt, kunt bijvoorbeeld voor zaken zoals dagen van de weken of maanden, klikt u vervolgens u zien Power BI Desktop om te sorteren op een andere kolom. Zie voor meer informatie, [sorteren op kolom in Power BI Desktop](desktop-sort-by-column.md).

## <a name="building-maps-more-easily-with-hints-to-bing"></a>Eenvoudiger maps maken met hints van Bing
Power BI biedt integratie met Bing om standaard kaartcoördinaten te bieden (een proces dat geocodering wordt genoemd) zodat u eenvoudiger kaarten kunt maken. Bing gebruikt bepaalde algoritmen en hints om de juiste locatie te bepalen, maar dit blijft een schatting. U kunt de volgende tips gebruiken om de kans te verhogen dat de geocodering goed verloopt:

Wanneer u een kaart maakt, zult u meestal landen, staten en plaatsen willen weergeven. Als u in Power BI Desktop kolommen een naam geeft op basis van de geografische aanduiding, kan Bing beter inschatten wat u wilt weergeven. Als u bijvoorbeeld een veld met namen van Amerikaans staten gebruikt, zoals 'Californië' en 'Washington', is het mogelijk dat Bing voor 'Washington' de locatie van Washington, DC, retourneert, in plaats van de staat Washington. Door een kolom 'Staat' toe te voegen, wordt de geocodering verbeterd. Datzelfde geldt voor kolommen met de naam Land en Plaats. 

Sommige aanduidingen zijn ambigu wanneer deze worden gebruikt in de context van meerdere landen. Wat in sommige landen/regio's als 'staat' wordt beschouwd, kan in andere landen/regio's een andere aanduiding krijgen, zoals 'provincie' of 'county'. U kunt de nauwkeurigheid van de geocodering vergroten door kolommen te maken die meerdere velden samenvoegen en deze vervolgens gebruiken om gegevenslocaties te visualiseren. Zo kunt u in plaats van alleen 'Wiltshire' door te geven, ervoor kiezen 'Wiltshire, Engeland' door te geven om nauwkeurigere geocoderingsresultaten te krijgen. 

Ook kunt u in de Power BI-service of Power BI Desktop altijd specifieke breedte- en lengtegraden opgeven voor een locatie. Wanneer u dit doet, moet u ook een locatieveld doorgeven, anders worden de gegevens standaard geaggregeerd, waardoor de locatie van de breedte- en lengtegraden mogelijk niet overeenkomt met wat u verwacht.

## <a name="categorizing-geographic-fields-to-hint-bings-geocoding"></a>Geografische velden categoriseren om hints te geven voor de geocodering van Bing
Een andere manier is te zorgen dat velden correct worden gegeocodeerd door de gegevenscategorie voor de gegevensvelden in te stellen. In Power BI Desktop, selecteert u de gewenste tabel, gaat u naar het lint Geavanceerd en stel de gegevenscategorie in op adres, plaats, Continent, land/regio, land/regio, postcode, staat of provincie. Deze gegevenscategorieën helpen Bing bij het correct coderen van de gegevens. Zie [Gegevenscategorisatie in Power BI Desktop](desktop-data-categorization.md) voor meer informatie.

## <a name="better-geocoding-with-more-specific-locations"></a>Betere geocodering met specifiekere locaties
Soms is zelfs het instellen van de gegevenscategorieën onvoldoende om correcte kaarten te maken. Maak met de query-editor in Power BI Desktop een specifiekere locatie, zoals een adres. Gebruik de functie Kolom toevoegen om een aangepaste kolom te maken. Maak de gewenste locatie vervolgens als volgt: 

    = [Field1] & " " & [Field2]

Vervolgens kunt u het resulterende veld gebruiken in kaartvisualisaties. Dit is zeer nuttig wanneer u straatadressen afleidt van velden voor een bezorgadres die veel in gegevenssets worden gebruikt. Houd er wel rekening mee dat deze samenvoeging alleen werkt met tekstvelden. Indien nodig dient u een huisnummer eerst te converteren naar een tekstgegevenstype, voordat u dit gebruikt om een adres te vormen.

## <a name="histograms-in-the-query-stage"></a>Histogrammen in de query-fase
Er zijn verschillende manieren om in Power BI Desktop histogrammen te maken. We beginnen met de eenvoudigste en bouwen het daarna op:

Eenvoudigste histogrammen: bepaal welke query het veld bevat dat u wilt gebruiken om een histogram te maken. Gebruik de optie 'Verwijzing' voor de query om een nieuwe query te maken en geef deze de naam 'FieldName Histogram'. Gebruik de optie 'Groeperen op' in het lint 'Transformatie' en selecteer de aggregatie 'Rijen tellen'. Zorg dat het gegevenstype een getal is voor de resulterende cumulatieve kolom. Visualiseer vervolgens deze gegevens op de rapportenpagina. Deze methode is snel en eenvoudig te maken, maar werkt niet goed als u veel gegevenspunten hebt en u kunt zo niet eenvoudig door visualisaties bladeren.

Buckets definiëren om een histogram te maken: bepaal welke query het veld bevat dat u wilt gebruiken om een histogram te maken. Gebruik de optie 'Verwijzing' voor de query om een nieuwe query te maken en geef deze de naam 'FieldName'. Definieer vervolgens de buckets met behulp van een regel. Gebruik de optie Aangepaste kolom toevoegen op het lint Kolom toevoegen en maak een aangepaste regel. Een eenvoudige bucket-regel kan er bijvoorbeeld als volgt uitzien:

    if([FieldName] \< 2) then "\<2 min" else
    if([FieldName] \< 5) then "\<5 min" else
    if([FieldName] \< 10) then "\<10 min" else
    if([FieldName] \< 30) then "\<30 min" else
    "longer")

Zorg dat het gegevenstype een getal is voor de resulterende cumulatieve kolom. U kunt nu de techniek voor Groeperen op gebruiken die wordt beschreven bij het Eenvoudigste histogram om het histogram te maken. Deze optie kan meer gegevenspunten verwerken, maar u kunt nog steeds niet eenvoudiger door visualisaties bladeren.

Een histogram definiëren met ondersteunt kunt - kunt is als visuele elementen bij elkaar zijn gekoppeld, zodat wanneer een gebruiker een gegevenspunt in een visueel element selecteert, andere visuele elementen op de rapportpagina uitgelicht of gefilterd van gegevenspunten die betrekking hebben op het geselecteerde gegevenspunt. Omdat we gegevens op query-niveau bewerken, moeten we een relatie maken tussen tabellen en zorgen dat we weten welk detailitem is gekoppeld aan de bucket in het histogram en vice versa.

U kunt dit proces beginnen met behulp van de optie 'Verwijzing' voor de query die het veld bevat waarop u een histogram wilt baseren. Noem de nieuwe query 'Buckets'. In dit voorbeeld noemen we de oorspronkelijke query 'Details'. Verwijder vervolgens alle kolommen behalve de kolom die u als bucket voor het histogram wilt gebruiken. Vervolgens klikt u met de rechtermuisknop op de kolom en selecteert u uit het query-menu de functie 'Duplicaten verwijderen', zodat alle overgebleven waarden in de kolom uniek zijn. Als de kolom decimale getallen bevat, kunt u om een beheerbare sets buckets te maken eerst de tip opvolgen die wordt genoemd bij Buckets definiëren om een histogram te maken. Controleer vervolgens de gegevens die in de query-preview worden weergegeven. Als u lege waarden of 'null' ziet, dient u deze eerst te corrigeren voordat u een relatie maakt. Raadpleeg 'Creating a relationship if my data has null or blank values' (Een relatie maken als mijn gegevens velden met 'null' of lege waarden bevatten). Deze benadering kan problematisch zijn vanwege de noodzaak om te sorteren. Raadpleeg 'Sorting order: make categories appear in the order I want' (Sorteervolgorde: zorgen dat categorieën worden weergegeven in de juiste volgorde) om te zorgen dat de buckets correct worden gesorteerd. 

>[!NOTE]
>We raden aan na te denken over de sorteervolgorde voordat u visualisaties maakt. 

De volgende stap in het proces is een relatie te definiëren tussen de query's 'Buckets' en 'Details', in de buckets-kolom. Klik in Power BI Desktop in het lint op **Relaties beheren**. Maak een relatie waarbij Buckets zich bevindt in de linkertabel en Details in de rechtertabel en selecteer vervolgens het veld dat u voor het histogram gebruikt. 

Tot slot maakt u het histogram. Sleep het veld Bucket uit de tabel 'Buckets'. Verwijder het standaardveld uit de resulterende kolomdiagram. Sleep nu het histogramveld uit de tabel 'Details' naar dezelfde visualisatie. Wijzig voor de velden de standaardaggregatie naar Aantal. Nu wordt het histogram gemaakt. Als u nog een visualisatie maakt, zoals een treemap van de tabel Details, kunt u een gegevenspunt in de treemap selecteren om dit gegevenspunt uit te lichten in het histogram en om het histogram weer te geven voor het geselecteerde gegevenspunt, ten opzichte van de trend voor de volledige gegevensset.

## <a name="histograms"></a>Histogrammen
U kunt in Power BI Desktop een berekend veld gebruiken om een histogram te definiëren. Bepaal op basis van welke tabel en kolom u een histogram wilt maken. Typ in het berekeningsgebied de volgende formule:

> Frequency:=COUNTROWS(\<Kolomnaam\>)
> 
> 

Sla de wijzigingen op en keer terug naar uw rapport. Voeg de \<Kolomnaam\> en de Frequentie toe aan een tabel converteer deze naar een staafdiagram. Controleer of de \<Kolomnaam\> op de x-as wordt weergegeven en het berekende veld Frequentie op de y-as.

## <a name="tips-and-tricks-for-creating-relationships-in-power-bi-desktop"></a>Tips en trucs voor het maken van relaties in Power BI Desktop
Vaak zorgen bij het laden van gedetailleerde gegevenssets uit meerdere bronnen problemen zoals null-waarden, lege waarden of dubbele waarden ervoor dat u geen relaties kunt maken. 

Hier volgt een voorbeeld. 

Als we gegevenssets laden, zoals een set over actieve klantenondersteuningsaanvragen en een andere gegevensset met werkitems, met de volgende schema's:

> CustomerInicdents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Als we alle incidenten en werkitems willen volgen die betrekking hebben op een specifieke CustomerName, kunnen we niet enkel een relatie tussen deze twee gegevenssets maken. Sommige WorkItems zijn misschien niet gekoppeld aan een CustomerName, dus dan is dat veld leeg of NULL. Ook kunnen er meerdere records in WorkItems en CustomerIncidents zijn voor een bepaalde CustomerName. 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-null-or-blank-values"></a>Een relatie maken in Power BI Desktop als de gegevens velden met lege of null-waarden bevatten
Vaak bevatten gegevenssets kolommen met lege of null-waarden. Dit kan problemen veroorzaken bij het gebruik van relaties. U kunt deze problemen eigenlijk op twee manieren oplossen. U kunt de rijen verwijderen die lege of null-waarden bevatten. U kunt doen dit met behulp van de filterfunctie in het query-tabblad of, als u query's samenvoegt, door de optie 'Alleen overeenkomende rijen behouden' te selecteren. De andere oplossing is de lege of null-waarde te vervangen door waarden die wel werken in relaties, doorgaans door tekenreeksen zoals 'NULL' of '(Leeg)'. Er bestaat hier geen correct antwoord: door de rijen op query-niveau te filteren worden rijen verwijdert, wat gevolgen kan hebben voor de samenvattende statistieken en berekeningen. De andere oplossing behoudt die gegevensrijen, maar kan ervoor zorgen dat niet-gerelateerde rijen worden weergegeven in het model, wat kan leiden tot fouten in de berekeningen. Als u de tweede methode gebruikt, dient u waar nodig filters voor de Weergave/Grafiek te gebruiken, om te zorgen dat u nauwkeurige resultaten krijgt. Zorg ook vooral dat u controleert welke regels worden behouden en/of verwijderd en dat u begrijpt wat de gevolgen zijn voor de analyse. 

### <a name="creating-relationships-in-power-bi-desktop-when-the-data-has-duplicate-values"></a>Een relatie maken in Power BI Desktop als de gegevens dubbele waarden bevatten
Vaak zorgen bij het laden van gedetailleerde gegevenssets uit meerdere bronnen dubbele waarden ervoor dat u geen relaties kunt maken. U kunt dit ondervangen door een dimensietabel te maken met de unieke waarden van beide gegevenssets. 

Hier volgt een voorbeeld. 

Als we gegevenssets laden, zoals een set over actieve klantenondersteuningsaanvragen en een andere gegevensset met werkitems, met de volgende schema's:

> CustomerInicdents: {IncidentID, CustomerName, IssueName, OpenedDate, Status} WorkItems: {WorkItemID, IncidentID, WorkItemName, OpenedDate, Status, CustomerName } 
> 
> 

Als we alle incidenten en werkitems willen volgen die betrekking hebben op een specifieke CustomerName, kunnen we niet enkel een relatie tussen deze twee gegevenssets maken. Sommige WorkItems zijn misschien niet gekoppeld aan een CustomerName, dus dan is dat veld leeg of NULL. Als de tabel CustomerNames lege of null-waarden bevat, kunt u mogelijk nog steeds geen relatie maken; zie in dat geval Een relatie maken als mijn gegevens lege of null-waarden bevatten. Ook kunnen er meerdere WorkItems en CustomerIncidents zijn voor een enkele CustomerName. 

Als u in dat geval een relatie wilt maken, dient u eerst een logische gegevensset te maken van de CustomerNames in beide gegevenssets. In het query-tabblad kunt u de volgende reeks gebruiken om de logische gegevensset te maken:

1. Dupliceer beide query's en geef de eerste de naam **Temp** en de tweede de naam **CustomerNames**.
2. Verwijder alle kolommen in elke query *behalve* de kolom CustomerName.
3. Gebruik vervolgens in elke query **Dubbele waarden verwijderen**.
4. Selecteer dan in de query **CustomerNames** in het lint de optie **Toevoegen** en voeg de query **Temp** toe.
5. Selecteer nu in de query **CustomerNames** **Dubbele waarden verwijderen**.

U hebt nu een dimensietabel gemaakt die u kunt gebruiken om relaties te maken met CustomerIndicents en WorkItems en die de waarden van beide tabellen bevat. 

## <a name="patterns-to-jump-start-your-use-of-the-query-editor"></a>Patronen om snel aan de slag te gaan met Query Editor
Query Editor is een zeer krachtig hulpmiddel om gegevens te bewerken en geschikt te maken voor gebruik in visualisaties of modellen. Er zijn enkele patronen om te onthouden.

### <a name="temporary-columns-can-be-deleted-after-computing-a-result"></a>Tijdelijke kolommen kunnen worden verwijderd na het berekenen van een resultaat
Vaak zult u in Power BI Desktop een berekening moeten maken waarmee gegevens uit meerdere kolommen worden omgezet naar één nieuwe kolom. Dit kan ingewikkeld zijn. Een gemakkelijke manier om dit te doen, is door de bewerking op te breken in stappen. Begin door de oorspronkelijke kolommen te dupliceren. Doorloop vervolgens de stappen om tijdelijke kolommen te maken. Maak dan pas de kolom voor het uiteindelijke resultaat. U kunt de tijdelijke kolommen nu verwijderen, om de uiteindelijke gegevensset op te ruimen. Dit is mogelijk omdat het query-tabblad stappen in volgorde uitvoert. 

### <a name="duplicate-or-reference-queries-followed-by-merge-to-original-query"></a>Query's dupliceren of ernaar verwijzen, en deze vervolgens samenvoegen met de oorspronkelijke query
Soms is het handig om samenvattende statistieken te berekenen voor een gegevensset. De eenvoudige manier om dit te doen is de query te dupliceren of ernaar te verwijzen in het query-tabblad. Gebruik vervolgens **Groeperen op** om samenvattende statistieken te berekenen. Samenvattende statistieken kunnen het makkelijker maken de gegevens in de oorspronkelijke gegevensset te normaliseren, zodat ze beter vergelijkbaar zijn, zoals in . Dit is vooral handig om afzonderlijke waarden te vergelijken met het totaal. Om dit te doen gaat u naar de oorspronkelijke query en selecteert u de optie Samenvoegen. Voeg de gegevens uit de query voor samenvattende statistieken daarna samen met de gegevens die een overeenkomend aanduiding hebben. U kunt nu de gegevens normaliseren tot de vorm die nodig is voor uw analyse.

## <a name="using-dax-for-the-first-time"></a>DAX voor het eerst gebruiken
DAX is de formuletaal voor berekeningen in Power BI Desktop. Deze is geoptimaliseerd voor BI-analyse. Dit kan anders zijn dan wat u gewend bent als u tot nu toe alleen query-talen hebt gebruikt die op SQL lijken. Er zijn zeer goede onlinebronnen en informatieve literatuur beschikbaar om te leren werken met DAX. 

[Standaard DAX-bewerkingen in Power BI Desktop leren gebruiken](desktop-quickstart-learn-dax-basics.md)

[Naslaginformatie voor Data Analysis Expressions (DAX)](https://msdn.microsoft.com/library/gg413422.aspx)

[DAX Resource Center](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)
