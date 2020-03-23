---
title: Richtlijnen voor het ophalen van gegevens voor gepagineerde rapporten
description: Richtlijnen voor het maken van gegevensbronnen en gegevenssets voor gepagineerde rapporten in Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 067171f7ec74beccdb5a312c1cac5bbc6c87541f
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79377645"
---
# <a name="data-retrieval-guidance-for-paginated-reports"></a>Richtlijnen voor het ophalen van gegevens voor gepagineerde rapporten

Dit artikel is bedoeld voor u wanneer u als auteur [gepagineerde rapporten](../paginated-reports/paginated-reports-report-builder-power-bi.md) in Power BI gaat ontwerpen. U vindt hierin aanbevelingen voor het effectief en efficiënt ophalen van gegevens.

## <a name="data-source-types"></a>Typen gegevensbronnen

Gepagineerde rapporten ondersteunen standaard zowel relationele als analytische gegevensbronnen. Deze bronnen worden verder ingedeeld in cloudbronnen en on-premises bronnen. Voor on-premises gegevensbronnen, ongeacht of deze on-premises of op een virtuele machine worden gehost, is een gegevensgateway nodig zodat Power BI verbinding kan maken. Cloudbron houdt in dat Power BI rechtstreeks verbinding kan maken door middel van een internetverbinding.

Als u het type gegevensbron kunt kiezen (dit is mogelijk het geval in een nieuw project), is het raadzaam cloudgegevensbronnen te gebruiken. Gepagineerde rapporten kunnen verbinding maken met een kortere netwerklatentie, vooral wanneer de gegevensbronnen zich in dezelfde regio bevinden als uw Power BI-tenant. Het is ook mogelijk om verbinding te maken met deze bronnen door middel van eenmalige aanmelding (Single Sign-On of SSO). Dit betekent dat de identiteit van de rapportgebruiker aan de gegevensbron kan worden doorgegeven, zodat machtigingen op rijniveau en per gebruiker kunnen worden afgedwongen. Op dit moment wordt SSO niet ondersteund voor on-premises gegevensbronnen (wat betekent dat SQL Server Analysis Services geen machtigingen op rijniveau en per gebruiker kan afdwingen).

> [!NOTE]
> Het is momenteel niet mogelijk om via SSO verbinding te maken met on-premises databases, maar u kunt nog steeds machtigingen op rijniveau afdwingen. Dit doet u door het ingebouwde veld **UserID** door te geven aan een gegevenssetqueryparameter. De gegevensbron moet UPN-waarden (User Principal Name) op zo'n manier opslaan dat de queryresultaten op juiste wijze kunnen worden gefilterd.
>
> Stel bijvoorbeeld dat elke verkoper als een rij wordt opgeslagen in de tabel **Salesperson**.  De tabel bevat kolommen voor UPN en ook voor de verkoopregio van de verkoper. Bij het uitvoeren van de query wordt de tabel gefilterd op de UPN van de rapportgebruiker en is deze ook gekoppeld aan de verkoopfeiten door middel van een inner join. Op deze manier worden met de query de rijen met de verkoopfeiten op effectieve wijze gefilterd op de verkoopfeiten voor de verkoopregio van de rapportgebruiker.

### <a name="relational-data-sources"></a>Relationele gegevensbronnen

Over het algemeen zijn relationele gegevensbronnen zeer geschikt voor operationele rapporten, zoals facturen. Ze zijn ook geschikt voor rapporten waarvoor zeer grote gegevenssets moeten worden opgehaald (meer dan 10.000 rijen). Relationele gegevensbronnen kunnen ook opgeslagen procedures definiëren die door rapportgegevenssets kunnen worden uitgevoerd. Opgeslagen procedures bieden verschillende voordelen:

- Parameterisering
- Inkapseling van programmeerlogica, waardoor een complexere gegevensvoorbereiding mogelijk is (bijvoorbeeld tijdelijke tabellen, cursors of scalaire functies die door de gebruiker zijn gedefinieerd)
- Ze zijn onderhoudsvriendelijk, zodat logica van opgeslagen procedures eenvoudig kan worden bijgewerkt. In sommige gevallen kan dit worden gedaan zonder dat de gepagineerde rapporten hoeven te worden gewijzigd en opnieuw hoeven te worden gepubliceerd (op voorwaarde dat de kolomnamen en gegevenstypen ongewijzigd blijven).
- Betere prestaties, omdat de uitvoeringsplannen in de cache worden opgeslagen zodat deze meermaals kunnen worden gebruikt
- Opgeslagen procedures opnieuw gebruiken in meerdere rapporten

In Power BI Report Builder kunt u de ontwerpfunctie voor relationele query's gebruiken om grafisch een queryinstructie te maken. Dit geldt echter uitsluitend voor Microsoft-gegevensbronnen.

### <a name="analytic-data-sources"></a>Analytische gegevensbronnen

Analytische gegevensbronnen zijn zeer geschikt voor zowel operationele als analytische rapporten en er kan hiermee snel een samenvatting met queryresultaten worden geleverd, zelfs bij zeer grote gegevensvolumes. Met modelmetingen en KPI's kunnen complexe bedrijfsregels worden ingekapseld om overzichten met gegevens te realiseren. Deze gegevensbronnen zijn echter niet geschikt voor rapporten waarvoor zeer grote gegevenssets moeten worden opgehaald (meer dan 10.000 rijen).

In Power BI Report Builder kunt u kiezen uit twee queryontwerpfuncties: De Analysis Services DAX-queryontwerpfunctie en de Analysis Services MDX-queryontwerpfunctie. Deze ontwerpfuncties kunnen worden gebruikt voor gegevensbronnen voor Power BI-gegevenssets of SQL Server Analysis Services- of Azure Analysis Services-modellen, in tabelvorm of multidimensionaal.

We raden u aan om de DAX-queryontwerpfunctie te gebruiken, indien deze volledig voldoet aan uw querybehoeften. Als in het model niet de benodigde metingen worden gedefinieerd, moet u overschakelen naar de querymodus. In deze modus kunt u de queryinstructie aanpassen door expressies toe te voegen (om de gewenste samenvatting te realiseren).

Voor de MDX-queryontwerpfunctie moet uw model metingen bevatten. De ontwerpfunctie beschikt over twee mogelijkheden die niet door de DAX-queryontwerpfunctie worden ondersteund. U kunt met name het volgende doen:

- Op queryniveau berekende leden definiëren (in MDX).
- Gegevensregio's configureren om [serveraggregaties](/sql/reporting-services/report-design/report-builder-functions-aggregate-function) op te vragen in andere groepen dan detailgroepen. Als uw rapport overzichten moet bevatten van semi-additieve metingen (metingen die in sommige dimensies kunnen worden opgeteld) of niet-additieve metingen (metingen die in geen enkele dimensie kunnen worden opgeteld), zoals tijdsintelligente berekeningen of afzonderlijke tellingen, is het waarschijnlijk efficiënter om serveraggregaties te gebruiken dan detailrijen op een laag niveau op te halen en de overzichten door het rapport te laten berekenen.

## <a name="query-result-size"></a>Omvang van queryresultaten

Over het algemeen kunt u het beste alleen de gegevens ophalen die nodig zijn voor uw rapport. Haal daarom geen kolommen of rijen op die niet nodig zijn voor het rapport.

Als u het aantal rijen wilt beperken, moet u altijd de meest beperkende filters toepassen en aggregatiequery's definiëren. Met aggregatiequery's worden brongegevens gegroepeerd en samengevat om gedetailleerdere resultaten op te halen. Stel bijvoorbeeld dat uw rapport een samenvatting van de verkoopgegevens van verkopers moet weergeven. In plaats van alle rijen met verkooporders op te halen, maakt u een gegevenssetquery waarmee de gegevens op verkoper worden gegroepeerd en de verkoopgegevens voor elke groep worden samengevat.

## <a name="expression-based-fields"></a>Velden die op expressies zijn gebaseerd

Het is mogelijk om een rapportgegevensset uit te breiden met velden die op expressies zijn gebaseerd. Als in uw gegevensset bijvoorbeeld de voornaam en achternaam van de klant wordt opgehaald, wilt u misschien dat deze twee velden worden samengevoegd in een veld dat de volledige naam van de klant bevat. U kunt deze berekening op twee manieren realiseren. U kunt:

- Een _berekend veld_ maken, dat een gegevenssetveld is dat is gebaseerd op een expressie.
- Voeg een expressie rechtstreeks in de gegevenssetquery toe (door middel van de systeemeigen taal van uw gegevensbron), hetgeen resulteert in een normaal gegevenssetveld.

We raden u aan om waar mogelijk de laatste optie te gebruiken. Er zijn twee goede redenen waarom het rechtstreeks in uw gegevenssetquery toevoegen van expressies beter is:

- Het is mogelijk dat uw gegevensbron is geoptimaliseerd om de expressie efficiënter te evalueren dan Power BI (dit is vooral het geval voor relationele databases).
- De rapportprestaties zijn beter omdat Power BI geen berekende velden hoeft te verwerken voordat het rapport wordt weergegeven. Bij berekende velden kan de tijdsduur voor het genereren van rapporten aanmerkelijk toenemen wanneer door de gegevenssets een groot aantal rijen wordt opgehaald.

## <a name="field-names"></a>Veldnamen

Wanneer u een gegevensset maakt, krijgen de velden ervan automatisch de namen van de querykolommen. Deze namen zijn mogelijk geen beschrijvende of intuïtieve namen. Het is ook mogelijk dat de kolomnamen in de bronquery's tekens bevatten die niet zijn toegestaan in de RDL-object-id's (Report Definition Language), zoals spaties en symbolen. In dat geval worden de niet-toegestane tekens vervangen door een onderstrepingsteken (_).

Het wordt aanbevolen om eerst te controleren of alle veldnamen beschrijvend, beknopt en toch betekenisvol zijn. Als dat niet het geval is, is het raadzaam de naam te wijzigen _voordat_ u met de indeling van het rapport begint. De reden hiervoor is dat wijzigingen in de veldnamen geen gevolgen hebben voor de expressies die in de rapportindeling worden gebruikt. Als u besluit om de namen van velden te wijzigen nadat u met de rapportindeling bent begonnen, moet u alle verbroken expressies zoeken en bijwerken.

## <a name="filter-vs-parameter"></a>Filter versus parameter

De ontwerpen voor uw gepagineerde rapporten bevatten waarschijnlijk rapportparameters. Rapportparameters worden meestal gebruikt om de rapportgebruiker te vragen het rapport te filteren. Als auteur van een gepagineerd rapport kunt u er op twee manieren voor zorgen dat rapporten worden gefilterd. U kunt een rapportparameter toewijzen aan:

- Een gegevensset_filter_. In dat geval wordt (worden) met de rapportparameterwaarde(n) de gegevens gefilterd die al door de gegevensset zijn opgehaald.
- Een gegevensset_parameter_. In dat geval wordt (worden) de rapportparameterwaarde(n) toegevoegd aan de systeemeigen query die naar de gegevensbron wordt verzonden.

> [!NOTE]
> Alle rapportgegevenssets worden _per sessie_ en gedurende maximaal tien minuten _na het laatste gebruik_ in de cache opgeslagen. Een gegevensset kan opnieuw worden gebruikt wanneer nieuwe parameterwaarden worden ingediend (filteren), het rapport in een andere indeling wordt weergegeven of het rapportontwerp op een of andere manier wordt bewerkt, zoals het in- of uitschakelen van de weergave of sorteren van gegevens.

Nemen we als voorbeeld een verkooprapport met één rapportparameter om het rapport te filteren op één jaar. De gegevensset haalt de verkoopgegevens voor _alle jaren_ op. Dit gebeurt omdat de rapportparameter is toegewezen aan de gegevenssetfilters. In het rapport worden de gegevens voor het aangevraagde jaar weergegeven. Dit is een subset van de gegevenssetgegevens. Wanneer de rapportgebruiker de rapportparameter wijzigt in een ander jaar en vervolgens het rapport weergeeft, hoeft Power BI geen brongegevens op te halen. In plaats daarvan wordt een ander filter toegepast op de gegevensset die al in de cache is opgeslagen. Wanneer de gegevensset in de cache is opgeslagen, kan het filteren zeer snel worden uitgevoerd.

Laten we eens een ander rapportontwerp bespreken. Deze keer wordt in het rapportontwerp de rapportparameter Omzetjaar toegewezen aan een gegevenssetparameter. Op deze manier wordt door Power BI de waarde voor het jaar toegevoegd aan de systeemeigen query en haalt de gegevensset alleen gegevens voor dat jaar op. Steeds wanneer de rapportgebruiker de waarde voor de rapportparameter Omzetjaar wijzigt en vervolgens het rapport weergeeft, haalt de gegevensset een nieuw queryresultaat voor alleen dat jaar op.

Met beide ontwerpmethoden kunnen rapportgegevens worden gefilterd. Beide ontwerpen kunnen geschikt zijn voor uw rapportontwerpen. Een geoptimaliseerd ontwerp is echter afhankelijk van de verwachte hoeveelheden gegevens, gegevensschommelingen en het verwachte gedrag van uw rapportgebruikers.

Het wordt aanbevolen _filteren van gegevenssets_ te gebruiken wanneer u verwacht dat een andere subset van de gegevenssetrijen vaak opnieuw wordt gebruikt (waardoor tijd wordt bespaard bij het genereren van het rapport omdat er geen nieuwe gegevens hoeven te worden opgehaald). In dit scenario gaat u ervan uit dat de kosten voor het ophalen van een grotere gegevensset kan worden weggestreept tegen het aantal keren dat deze opnieuw kan worden gebruikt. Het is dus handig in het geval van query's waarvan de uitvoering veel tijd in beslag neemt. Houd er echter rekening mee dat het in de cache opslaan van grote gegevenssets per gebruiker negatieve gevolgen kan hebben op de prestaties en de doorvoercapaciteit.

Het wordt aanbevolen _gegevenssetparameterisering_ te gebruiken wanneer het onwaarschijnlijk is dat een andere subset van gegevenssetrijen wordt opgevraagd of wanneer het aantal gegevenssetrijen dat moet worden gefilterd waarschijnlijk erg groot is (en inefficiënt om in de cache op te slaan). Deze ontwerpmethode is ook geschikt wanneer er schommelingen zijn in uw gegevensopslag. In dit geval heeft elke wijziging in de rapportparameterwaarde tot gevolg dat actuele gegevens worden opgehaald.

## <a name="non-native-data-sources"></a>Andere gegevensbronnen dan systeemeigen gegevensbronnen

Als u gepagineerde rapporten wilt ontwikkelen op basis van gegevensbronnen die niet [standaard worden ondersteund door gepagineerde rapporten](../paginated-reports/paginated-reports-data-sources.md), kunt u eerst een Power BI Desktop-gegevensmodel ontwikkelen. Op die manier kunt u verbinding maken met meer dan 100 [Power BI-gegevensbronnen](../power-bi-data-sources.md). Nadat u dit model naar de Power BI-service hebt gepubliceerd, kunt u vervolgens een gepagineerd rapport ontwikkelen dat verbinding maakt met de Power BI-gegevensset.

## <a name="data-integration"></a>Gegevensintegratie

Als u gegevens uit meerdere gegevensbronnen wilt combineren, kunt u twee dingen doen:

- **Rapportgegevenssets combineren**: Als de gegevensbronnen [standaard worden ondersteund door gepagineerde rapporten](../paginated-reports/paginated-reports-data-sources.md), kunt u berekende velden maken die gebruikmaken van de Power BI Report Builder-functies [Lookup](/sql/reporting-services/report-design/report-builder-functions-lookup-function) of [LookupSet](/sql/reporting-services/report-design/report-builder-functions-lookupset-function).
- **Een Power BI Desktop-model ontwikkelen**: Het is waarschijnlijk echter efficiënter om een gegevensmodel te ontwikkelen in Power BI Desktop. Met Power Query kunt u query's combineren die zijn gebaseerd op [ondersteunde gegevensbronnen](../power-bi-data-sources.md). Nadat u dit model naar de Power BI-service hebt gepubliceerd, kunt u vervolgens een gepagineerd rapport ontwikkelen dat verbinding maakt met de Power BI-gegevensset.

## <a name="sql-server-complex-data-types"></a>Complexe gegevenstypen van SQL Server

Omdat SQL Server een on-premises gegevensbron is, moet Power BI verbinding maken via een gateway. De gateway biedt echter geen ondersteuning voor het ophalen van gegevens voor complexe gegevenstypen. Voorbeelden van complexe gegevenstypen zijn ingebouwde typen, zoals de [ruimtelijke gegevenstypen](/sql/relational-databases/spatial/spatial-data-sql-server) GEOMETRY en GEOGRAPHY, en [hierarchyid](/sql/t-sql/data-types/hierarchyid-data-type-method-reference). Andere voorbeelden zijn door de gebruiker gedefinieerde typen die worden geïmplementeerd via een klasse van een assembly in Microsoft.NET Framework Common Language Runtime (CLR).

Voor het in kaart brengen van ruimtelijke gegevens en analyses in de kaartvisualisatie moeten ruimtelijke gegevens van SQL Server worden gebruikt. Daarom is het niet mogelijk om met de kaartvisualisatie te werken wanneer SQL Server uw gegevensbron is. Het werkt wel als uw gegevensbron Azure SQL Database is, omdat Power BI geen verbinding maakt via een gateway.

## <a name="data-related-images"></a>Afbeeldingen die zijn gerelateerd aan gegevens

U kunt afbeeldingen gebruiken om logo's of foto's aan uw rapportindeling toe te voegen. Wanneer afbeeldingen zijn gerelateerd aan de rijen die worden opgehaald door een rapportgegevensset, hebt u twee opties:

- Het is mogelijk dat afbeeldingsgegevens ook kunnen worden opgehaald uit uw gegevensbron (als deze al in een tabel zijn opgeslagen).
- Wanneer de afbeeldingen op een webserver zijn opgeslagen, kunt u een dynamische expressie gebruiken om het URL-pad voor de afbeeldingen te maken.

Zie [Richtlijnen voor afbeeldingen voor gepagineerde rapporten](report-paginated-image.md) voor meer informatie en suggesties.

## <a name="redundant-data-retrieval"></a>Het ophalen van redundante gegevens

Het is mogelijk dat uw rapport redundante gegevens ophaalt. Dit kan gebeuren wanneer u velden van de gegevenssetquery verwijdert of als het rapport ongebruikte gegevenssets bevat. Vermijd deze situaties, omdat ze leiden tot een onnodige belasting van uw gegevensbronnen, het netwerk en Power BI-capaciteitsresources.

### <a name="deleted-query-fields"></a>Verwijderde queryvelden

Op de pagina **Velden** van het venster **Gegevensseteigenschappen** kunt u _queryvelden_ voor de gegevensset verwijderen (queryvelden worden toegewezen aan kolommen die zijn opgehaald door de gegevenssetquery). Power BI Report Builder verwijdert de bijbehorende kolommen echter niet uit de gegevenssetquery.

Als u queryvelden uit uw gegevensset wilt verwijderen, is het raadzaam om de bijbehorende kolommen uit de gegevenssetquery te verwijderen. Eventuele redundante queryvelden worden automatisch door Power BI Report Builder verwijderd. Wanneer u besluit om queryvelden te verwijderen, moet u ook de gegevenssetqueryinstructie aanpassen door de kolommen te verwijderen.

### <a name="unused-datasets"></a>Ongebruikte gegevenssets

Wanneer een rapport wordt uitgevoerd, worden alle gegevenssets geëvalueerd, zelfs als deze niet aan rapportobjecten zijn gekoppeld. Zorg er daarom voor dat u test- of ontwikkelingsgegevenssets verwijdert voordat u een rapport publiceert.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI](../paginated-reports/paginated-reports-data-sources.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
