---
title: Scenario's voor Microsoft Power BI Premium-capaciteit
description: Beschrijving van algemene scenario's voor Power BI Premium-capaciteit.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565364"
---
# <a name="premium-capacity-scenarios"></a>Scenario's voor Premium-capaciteit

Dit artikel wordt beschreven echte scenario's waar Power BI premium-capaciteiten zijn geïmplementeerd. Veelvoorkomende problemen en uitdagingen worden beschreven, ook hoe u problemen identificeren en help op te lossen:

- [Gegevenssets up-to-date te houden](#keeping-datasets-up-to-date)
- [Gegevenssets langzaam reageert identificeren](#identifying-slow-responding-datasets)
- [Identificeren van oorzaken voor sporadisch langzaam reageert gegevenssets](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Bepalen of er voldoende geheugen](#determining-whether-there-is-enough-memory)
- [Bepalen of er voldoende CPU](#determining-whether-there-is-enough-cpu)

De stappen, samen met de grafiek en tabel voorbeelden zijn van de **metrische gegevens over Power BI Premium capaciteit app** een Power BI-beheerder heeft toegang tot.

## <a name="keeping-datasets-up-to-date"></a>Gegevenssets up-to-date te houden

Een onderzoek is in dit scenario wordt geactiveerd wanneer gebruikers klacht betrekking heeft dat rapportgegevens soms leek te zijn van de oude of 'verlopen'.

In de app, de beheerder de interactie met de **wordt vernieuwd** visueel element sorteren gegevenssets door de **maximale wachttijd** statistieken in aflopende volgorde. Dit visuele element helpt hen te onthullen gegevenssets met de langste wachttijden, gegroepeerd op de naam van de werkruimte.

![Gegevensset wordt vernieuwd gesorteerd op aflopende maximale wachttijd, gegroepeerd op de werkruimte](media/service-premium-capacity-scenarios/dataset-refreshes.png)

In de **per uur gemiddelde vernieuwen wacht tijden** visual, ze zoals u ziet dat de wachttijden vernieuwen consistent ongeveer 4 uur per dag pieken.

![Vernieuwen wacht piek periodiek om 4 uur](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Er zijn verschillende mogelijke oorzaken van deze resultaten:

- Te veel vernieuwingspogingen kunnen plaatsvinden op hetzelfde moment, de limieten die zijn gedefinieerd door het capaciteitsknooppunt. In dit geval standaard zes gelijktijdige wordt vernieuwd op een P1 met de toewijzing van geheugen.

- Gegevenssets worden vernieuwd kan worden te groot voor in het beschikbare geheugen (ten minste 2 x de hoeveelheid geheugen die nodig zijn voor volledig vernieuwen vereist).
- Inefficiënt Power Query-logica kan worden leidt tot een piek van geheugen tijdens het vernieuwen van de gegevensset. Deze piek op een bezet capaciteit kunt af en toe de fysieke limiet, mislukt het vernieuwen en mogelijk die betrekking hebben op andere bewerkingen voor het weergeven van rapport van de capaciteit bereiken.
- Vaak opgevraagde gegevenssets die u nodig hebt om in het geheugen blijven mogelijk invloed op de mogelijkheid van andere gegevenssets vernieuwen vanwege beperkte beschikbare geheugen.

Om te onderzoeken, kunt de Power BI-beheerder zoeken naar:

- Weinig geheugen beschikbaar op het moment van gegevens wordt vernieuwd wanneer het beschikbare geheugen kleiner dan 2 x de grootte van de gegevensset is wordt vernieuwd.
- Gegevenssets niet worden vernieuwd en niet in het geheugen voor vernieuwen, nog is gestart om interactieve verkeer tijdens zware vernieuwingstijden weer te geven. Als u wilt zien welke gegevenssets in het geheugen worden geladen op een bepaald moment, een Power BI-beheerder kunt kijken naar het gebied van gegevenssets van **gegevenssets** tabblad in de app. De beheerder kan vervolgens cross-filter op een bepaald moment door te klikken op een van de balken in de **per uur geladen gegevensset telt**. Een lokale piek, weergegeven in de onderstaande afbeelding geeft aan dat een uur wanneer meerdere gegevenssets zijn geladen in het geheugen, die het begin van de geplande vernieuwingen kan vertragen.
- Grotere gegevensset databasebestandspagina's te plaatsen wanneer gegevens worden vernieuwd zijn gepland om te starten. Databasebestandspagina's kunnen er geven hoge geheugenbelasting is veroorzaakt door te fungeren te veel verschillende interactieve rapporten voorafgaand aan het moment van vernieuwen. De **per uur gegevensset databasebestandspagina's en geheugenverbruik** visual kunt duidelijk pieken in databasebestandspagina's.

De volgende afbeelding ziet u een lokale piek in geladen gegevenssets, wat erop duidt interactieve query's uitvoeren begin van het vernieuwen uitgesteld. Selecteren van een bepaalde periode in de **per uur geladen gegevensset telt** visual wordt kruislings filteren de **omvang van gegevenssets** visual.

![Een lokale piek in geladen gegevenssets voorgesteld interactieve query vertraagd starten van vernieuwen](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

De Power BI-beheerder kunt proberen het probleem oplossen door te nemen stappen om ervoor te zorgen dat voldoende geheugen beschikbaar is voor gegevens worden vernieuwd om op te starten:

- Contact opnemen met de gegevensset vernieuwen eigenaren en waarin ze wordt gevraagd om te spreiden en ruimte gegevens schema's.
- Gegevensset verminderen querybelasting door het verwijderen van onnodige dashboards of dashboard-tegels, met name degenen die die beveiliging op rijniveau afdwingen.
- Versnellen van de gegevens worden vernieuwd door Power Query logica te optimaliseren. Verbeter de modellering van berekende kolommen of tabellen. Verminder omvang van gegevenssets of nemen uit grotere gegevenssets om uit te voeren van het vernieuwen van incrementele gegevens configureren.

## <a name="identifying-slow-responding-datasets"></a>Gegevenssets langzaam reageert identificeren

In dit scenario wordt een onderzoek is begonnen bij gebruikers klacht betrekking heeft dat bepaalde rapporten te lang om te openen duurt, en soms zou vastloopt.

In de app, de Power BI-beheerder kan gebruiken de **Query duur** visual om te bepalen van de slechtste presterende gegevenssets gegevenssets wordt gesorteerd in aflopende **gemiddelde duur**. Dit visuele element wordt ook weergegeven gegevensset aantal query's, zodat u kunt zien hoe vaak de gegevenssets worden opgevraagd.

![Slechtste presterende gegevenssets](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

De beheerder kan verwijzen naar de **Query Duurdistributie** visual, waarin een algehele verdeling van gerangschikte queryprestaties (< = 30ms, 0-100 ms) voor de gefilterde periode. In het algemeen, query's één seconde voor toets maken of minder zijn responsieve beschouwd door de meeste gebruikers. query's die langer duren meestal te maken van een perceptie van slechte prestaties.

De **per uur Query Duurdistributie** visual kan de Power BI-beheerder om één uur durende perioden wanneer de capaciteit prestaties kan hebben is waargenomen te identificeren als slecht. Hoe groter de balk segmenten die query vertegenwoordigen duur van meer dan één seconde, hoe groter het risico dat gebruikers slechte prestaties wordt waarneemt.

Het visuele element is interactief en wanneer een segment van de balk is ingeschakeld, de bijbehorende **Query duur** tabelvisualisatie op de pagina van het rapport wordt gefilterd om weer te geven van de gegevenssets die staat voor. Deze kruislings filteren, kunt de Power BI-beheerder om eenvoudig te identificeren die gegevenssets langzaam reageert.

De volgende afbeelding ziet u een visueel element gefilterd op **per uur Query duur distributies**, bundeling voor de slechtste presterende gegevenssets in één uur durende buckets. 

![Gefilterde per uur Query duur distributies visual bevat de nog erger gegevenssets uitvoeren](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Zodra de slecht presterende gegevensset in een specifieke één uur timespan wordt geïdentificeerd, wordt de Power BI-beheerder kunt onderzoeken of slechte prestaties wordt veroorzaakt door een overbelaste capaciteit of vanwege een slecht gegevensset of rapport ontworpen. Ze kunnen verwijzen naar de **uitvoertijden van Query wacht** visual en gegevenssets op gemiddelde Querytijd Aflopend sorteren. Als een groot percentage van query's wacht, wordt een hoog belasting voor de gegevensset is waarschijnlijk de oorzaak van te veel query wacht. Als de gemiddelde query wachttijd is aanzienlijk (> 100 ms), kan het zinvol controleren van de gegevensset en het rapport om te zien als optimalisaties kunnen worden gemaakt zijn. Bijvoorbeeld, minder visuals op rapportpagina's of de optimalisatie van een DAX-expressie opgegeven.

![De visual uitvoertijden van Query wacht helpt om weer te geven van slecht presterende gegevenssets](media/service-premium-capacity-scenarios/query-wait-times.png)

Er zijn verschillende mogelijke oorzaken voor query wacht tijd buildup in gegevenssets:

- Een modelontwerp suboptimale, metingexpressies of zelfs rapportontwerp - alle omstandigheden die kan bijdragen aan langlopende query's die een hoge mate van CPU in beslag nemen. Dit zorgt ervoor dat nieuwe query's moet worden gewacht tot threads CPU beschikbaar en een bus wordt vervangen effect (Beschouw verkeer is vastgelopen), die vaak gezien tijdens piek tijdens kantooruren maakt. De **Querywachttijden** pagina worden de belangrijkste bron om te bepalen of gegevenssets wachttijden hoge, gemiddelde query.
- Een groot aantal gelijktijdige capaciteit gebruikers (honderden tot duizenden) hetzelfde rapport of gegevensset verbruikt. Zelfs goed ontworpen gegevenssets kunt onjuist buiten een drempel voor gelijktijdigheid van taken uitvoeren. Dit wordt gewoonlijk aangegeven door een enkele gegevensset van een aanzienlijk hogere waarde voor query dan andere gegevenssets worden weergegeven telt (bijvoorbeeld: 300 kB voor één gegevensset in vergelijking met query's < 30K-query's voor alle andere gegevenssets). Op een bepaald moment de wacht query voor deze gegevensset spreiden te, die kunnen worden weergegeven de **Query duur** visual.
- Veel verschillende gegevenssets gelijktijdig, opgevraagd geheugenthrashing veroorzaakt, zoals gegevenssets cyclus vaak in en uit het geheugen. Dit resulteert in gebruikers met trage prestaties wanneer de gegevensset in het geheugen wordt geladen. Om te bevestigen, de Power BI-beheerder kan verwijzen naar de **per uur gegevensset databasebestandspagina's en geheugenverbruik** visual, die kan duiden dat een groot aantal gegevenssets in het geheugen geladen zijn herhaaldelijk verwijderd.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificeren van oorzaken voor sporadisch langzaam reageert gegevenssets

In dit scenario is een onderzoek wanneer gebruikers beschreven dat visuele rapportelementen soms zijn traag reageren of kunnen niet meer reageren, maar op andere momenten ze acceptabel responsieve konden begonnen.

In de app de **Query duur** sectie is gebruikt voor het vinden van de gegevensset overmatig in de volgende manier:

- In de **Query duur** visual admin gefilterde gegevensset met de gegevensset (vanaf de bovenste gegevenssets opgevraagd) en onderzoeken het kruislings gefilterd balken in de **per uur Query distributies** visual.
- Als een enkel één uur durende balk gebleken dat met belangrijke wijzigingen in de verhouding tussen de duur van alle querygroepen vergeleken met andere staven één uur voor deze gegevensset (bijvoorbeeld, de verhouding tussen de kleuren wijzigt drastisch), betekent dit dat deze gegevensset aangetoond sporadisch gewijzigd prestaties.
- Een TimeSpan-waarde waar deze gegevensset is beïnvloed door een effect ruis, veroorzaakt door de andere gegevenssets activiteiten heeft aangegeven dat de één uur durende balken met een onregelmatige gedeelte van slecht presterende query's.

De afbeelding hieronder toont één uur op 30 januari waar een aanzienlijke tegenslag in de prestaties van een gegevensset is opgetreden, aangegeven door de grootte van de '(3,10s] "uitvoering duurbucket. Te klikken op die één uur voor de balk ziet u alle gegevenssets in het geheugen geladen gedurende die tijd mogelijk gegevenssets die worden veroorzaakt door het effect van de ruis zichtbaar te maken.

![Met slechtste prestaties door een groot deel van de balk](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Zodra een problematische timespan wordt geïdentificeerd (bijvoorbeeld tijdens 30 jan in de bovenstaande afbeelding) kan de Power BI-beheerder verwijdert alle filters uit gegevensset vervolgens filteren alleen op dat timespan om te bepalen welke gegevenssets actief tijdens deze periode zijn opgevraagd. De gegevensset overmatig voor het effect van de ruis is meestal de belangrijkste aangevraagde gegevensset of één met de langste gemiddelde queryduur.

Een oplossing voor dit probleem kan worden voor het distribueren van het overmatig gegevenssets via verschillende werkruimten in verschillende Premium-capaciteiten, of in gedeelde capaciteit als de grootte van de gegevensset, verbruik vereisten en gegevens vernieuwen patronen worden ondersteund.

Omgekeerd kan ook waar zijn. De Power BI-beheerder kan identificeren tijden wanneer de prestaties van een gegevensset-query's aanzienlijk worden verbeterd en kijk wat is verdwenen. Als bepaalde informatie ontbreekt, wordt deze op dat moment mogelijk om te verwijzen naar het probleem waardoor die helpen.

## <a name="determining-whether-there-is-enough-memory"></a>Bepalen of er voldoende geheugen

Om te bepalen of er onvoldoende geheugen om de capaciteit is voor het voltooien van de werkbelasting, de Power BI-beheerder kan verwijzen naar de **verbruikte geheugen Percentages** visual in de **gegevenssets** tabblad van de app. **Alle** (totaal) geheugen vertegenwoordigt de hoeveelheid geheugen die worden gebruikt door de gegevenssets die worden geladen in het geheugen, ongeacht of ze actief wordt opgevraagd of verwerkt. **Actieve** geheugen vertegenwoordigt de hoeveelheid geheugen die worden gebruikt door de gegevenssets die actief worden verwerkt.

In een gezonde capaciteit het visuele element ziet er als u deze, met een kloof tussen alle (totaal) en actieve geheugen:

![Een gezonde capaciteit ziet u een kloof tussen alle (totaal) en actieve geheugen](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

In een capaciteit geheugendruk voordoet, wordt dezelfde visual duidelijk weergegeven actieve geheugen en het totale geheugen geconvergeerd, wat betekent dat het is niet mogelijk extra gegevenssets vervolgens in het geheugen laden. In dit geval de Power BI-beheerder kunt klikken op **capaciteit opnieuw** (in **geavanceerde opties** van het gebied van de instellingen voor capaciteit van de beheerportal). Opnieuw opstarten van de resultaten van de capaciteit in alle gegevenssets wordt leeggemaakt uit het geheugen en zodat ze opnieuw te laden in het geheugen zoals vereist (door query's of gegevens vernieuwen).

![** Actieve ** geheugen convergeert met ** alle ** geheugen](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Bepalen of er voldoende CPU

In het algemeen is moet de gemiddelde CPU-gebruik van een capaciteit blijven dan 80%. Meer dan deze waarde betekent dat de capaciteit bijna is bereikt voor belasting van de CPU.

Gevolgen van de belasting van de CPU worden uitgedrukt in door bewerkingen duurt langer dan het hoort, vanwege de capaciteit die veel CPU-contexten switches uitvoeren als wordt geprobeerd alle bewerkingen worden verwerkt. In een Premium-capaciteit met een groot aantal gelijktijdige query's, wordt dit aangegeven door de wachttijden hoge query. Een gevolg van wachttijden hoge query is trager reactiesnelheid dan normaal. De beheerder van de Power BI eenvoudig kunt herkennen wanneer de CPU is verzadigd hand de **per uur Query wacht tijd distributies** visual. Periodieke pieken van query wachttijd aantallen duiden op potentiële belasting van de CPU.

![Periodieke pieken van query wachttijd aantallen duiden op potentiële belasting van de CPU](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Een vergelijkbaar patroon kan soms worden gedetecteerd in bewerkingen op de achtergrond als de taalkenmerken aan de belasting van de CPU bijdragen. Een Power BI-beheerder kunt zoeken naar een periodieke piek in de tijdstippen voor vernieuwing voor een specifieke gegevensset, wat op belasting op het moment van de CPU (waarschijnlijk vanwege andere lopende gegevensset wordt vernieuwd en/of interactieve query's duiden kan). In dit geval verwijzen naar de **System** weergeven in de app kan niet per se blijkt dat de CPU 100% is. De **System** weergave worden weergegeven per uur gemiddelden, maar de CPU kan worden verzadigd voor enkele minuten van zware bewerkingen, die wordt weergegeven als pieken in de wachttijd.

Er zijn meer aspecten om te zien van het effect van de belasting van de CPU. Terwijl het aantal query's die wachten belangrijk is, de wachttijd query altijd gebeurt tot op zekere hoogte zonder aanmerkelijke prestatievermindering. Sommige gegevenssets (met een langere gemiddelde querytijd, complexiteit of grootte) zijn meer gevoelig zijn voor de gevolgen van de belasting van de CPU dan andere. Als u wilt deze gegevenssets eenvoudig kunt identificeren, de Power BI-beheerder kunt zoeken naar wijzigingen in de samenstelling van de kleur van de balken in de **per uur wachten verdeling** visual. Na een balk uitschieter ontdekken, kunnen ze zoeken naar de gegevenssets waarvoor query wacht gedurende die tijd en Bekijk ook de gemiddelde query wachttijd vergeleken met het gemiddelde queryduur van de. Wanneer deze twee metrische gegevens van dezelfde grootte zijn en de werkbelasting query voor de gegevensset essentieel is, is het waarschijnlijk dat de gegevensset wordt beïnvloed door onvoldoende CPU.

Dit effect is duidelijk is met name wanneer een gegevensset wordt gebruikt in korte pieken van high-frequency query's door meerdere gebruikers (bijvoorbeeld in een trainingssessie), wat resulteert in de belasting van de CPU tijdens elke burst. In dit geval kunnen wachttijden belangrijke query voor deze gegevensset worden ervaren en dat dit gevolgen heeft voor andere gegevenssets in de capaciteit (ruis werkt).

In sommige gevallen kan Power BI-beheerders kunnen aanvragen dat eigenaren van gegevenssets maken met een kleiner vluchtige queryworkload door het maken van een dashboard (query's die u regelmatig met een gegevensset vernieuwen voor tegels in de cache) in plaats van een rapport. Dit kan helpen pieken voorkomen wanneer het dashboard wordt geladen. Deze oplossing niet altijd mogelijk voor bepaalde zakelijke vereisten, maar een effectieve manier om te voorkomen dat de belasting van de CPU, zonder te wijzigen in de gegevensset.

## <a name="acknowledgements"></a>Bevestigingen

In dit artikel is geschreven door Peter Myers, Data Platform MVP en onafhankelijke BI deskundige met [Bitsgewijs oplossingen](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Premium-capaciteiten met de app controleren](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Monitor capaciteiten in de beheerportal](service-admin-premium-monitor-portal.md)   

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

||||||