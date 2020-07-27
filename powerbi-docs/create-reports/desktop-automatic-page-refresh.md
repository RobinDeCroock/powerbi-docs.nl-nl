---
title: Automatisch pagina vernieuwen in Power BI Desktop
description: In dit artikel wordt beschreven hoe u pagina's voor DirectQuery-bronnen in Power BI Desktop automatisch kunt vernieuwen.
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9a1e42b4901e8659bb5d999294f29a80a0389280
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557228"
---
# <a name="automatic-page-refresh-in-power-bi-desktop"></a>Automatisch pagina vernieuwen in Power BI Desktop 

Bij het bewaken van kritieke gebeurtenissen is het belangrijk dat gegevens worden vernieuwd zodra de brongegevens worden bijgewerkt. In de productiebranche is het bijvoorbeeld belangrijk te weten wanneer een machine defect is, of op het punt staat kapot te gaan.

De functie Pagina automatisch vernieuwen in Power BI zorgt ervoor dat de actieve rapportpagina met een vooraf gedefinieerde frequentie nieuwe gegevens ophaalt voor [DirectQuery-bronnen ](https://docs.microsoft.com/power-bi/desktop-directquery-about).

## <a name="using-automatic-page-refresh"></a>Het gebruik van Pagina automatisch vernieuwen

Het automatisch vernieuwen van pagina's is alleen beschikbaar voor gegevensbronnen van DirectQuery.

Als u automatisch vernieuwen van pagina's wilt gebruiken, selecteert u de rapportpagina waarvoor u vernieuwen wilt inschakelen. Selecteer in het deelvenster **Visualisaties** de knop **Opmaak** (een verfroller) en zoek naar **Pagina vernieuwen** onder aan het deelvenster. 

![Locatie van Pagina vernieuwen](media/desktop-automatic-page-refresh/automatic-page-refresh-01.png)

Op de volgende afbeelding is het tabblad **Pagina vernieuwen** te zien. De genummerde elementen worden na de afbeelding beschreven.

![Kaart Pagina vernieuwen](media/desktop-automatic-page-refresh/automatic-page-refresh-02.png)

1.    Het vernieuwen van pagina's in- of uitschakelen
2.    Getalwaarde voor het vernieuwingsinterval van de pagina's
3.    Eenheid voor het vernieuwingsinterval van de pagina's

Op deze kaart kunt u Pagina vernieuwen inschakelen en de duur van de vernieuwingsactie selecteren. De standaardwaarde is 30 minuten. (Het minimale vernieuwingsinterval is één seconde.) Het vernieuwen van uw rapport begint op het interval dat u hebt ingesteld. 

## <a name="determining-the-page-refresh-interval"></a>Het interval voor Pagina vernieuwen bepalen

Als Pagina automatisch vernieuwen is ingeschakeld, verzendt Power BI Desktop voortdurend query's naar uw DirectQuery-bron. Nadat de query is verzonden, duurt het even voordat gegevens worden geretourneerd. Voor korte vernieuwingsintervallen moet u dus bevestigen dat query's de opgehaalde gegevens binnen het geconfigureerde interval hebben kunnen retourneren. Als er binnen het interval geen gegevens worden geretourneerd, worden de visuals minder vaak bijgewerkt dan u hebt geconfigureerd.

Als aanbevolen procedure geldt dat het vernieuwingsinterval ten minste moet overeenkomen met de verwachte snelheid waarmee de nieuwe gegevens worden ontvangen:

* Als er elke 20 minuten nieuwe gegevens binnenkomen bij de bron, mag het vernieuwingsinterval niet korter zijn dan 20 minuten. 

* Als er elke seconde nieuwe gegevens worden ontvangen, stelt u het interval in op één seconde. 

Voor lage vernieuwingsintervallen, zoals één seconde, moet u rekening houden met de volgende factoren:
- Het type DirectQuery-gegevensbron
- De werkbelasting van uw query's
- De afstand van uw rapportlezers tot het datacentrum van de capaciteit 

U kunt retourtijden schatten met behulp van Performance Analyzer in Power BI Desktop. Met Performance Analyzer kunt u controleren of elke visualquery voldoende tijd heeft om de resultaten van de bron te retourneren. U kunt hiermee ook bepalen waaraan de tijd wordt besteed. Op basis van de resultaten van Performance Analyzer kunt u de gegevensbron aanpassen of u kunt experimenteren met andere visuals en meetwaarden in uw rapport.

In deze afbeelding ziet u de resultaten van een DirectQuery in Performance Analyzer:

![Resultaten van Performance Analyzer](media/desktop-automatic-page-refresh/automatic-page-refresh-03.png)

Laten we eens kijken wat andere kenmerken van deze gegevensbron zijn: 

-    Gegevens worden elke 2 seconden ontvangen. 
-    In Performance Analyzer wordt een maximale queryduur + weergavetijd van ongeveer 4,9 seconden (4,688 milliseconden) weergegeven. 
-    De gegevensbron is geconfigureerd om ongeveer 1,000 gelijktijdige query's per seconde te verwerken. 
-    U verwacht dat er ongeveer 10 gebruikers het rapport gelijktijdig zullen bekijken.

Dat levert de volgende vergelijking op:

**5 visuals x 10 gebruikers = ongeveer 50 query's**

Het resultaat van deze berekening toont aan dat de belasting veel hoger uitvalt dan de gegevensbron aankan. De snelheid waarmee gegevens worden ontvangen is elke twee seconden, zodat dit dus de vernieuwingsfrequentie moet zijn. Maar omdat het ongeveer vijf seconden duurt om de query uit te voeren, moet u deze op meer dan vijf seconden instellen. 

Houd er ook rekening mee dat dit resultaat anders kan zijns wanneer u uw rapport naar de service publiceert. Dit verschil treedt op omdat in het rapport het Azure Analysis Services-exemplaar wordt gebruikt dat wordt gehost in de cloud. Mogelijk wilt u de vernieuwingsfrequentie aanpassen. 

Power BI houdt rekening met tijden voor query's en vernieuwingsacties door de query voor vernieuwen pas uit te voeren wanneer alle resterende query's voor vernieuwen zijn voltooid. Zelfs als het vernieuwingsinterval korter is dan de tijd die nodig is om uw query's te verwerken, vernieuwt Power BI pas weer als de resterende query's zijn voltooid. 

Nu gaan we kijken hoe u als capaciteitsbeheerder prestatieproblemen zou kunnen detecteren en diagnosticeren. Verderop in dit artikel kunt u ook het gedeelte [Veelgestelde vragen](#frequently-asked-questions) raadplegen voor meer vragen en antwoorden over prestaties en het oplossen van problemen.

## <a name="automatic-page-refresh-in-the-power-bi-service"></a>Automatisch pagina vernieuwen in de Power BI-service

U kunt ook intervallen voor het automatisch vernieuwen van pagina's instellen voor rapporten die zijn gemaakt in Power BI Desktop en die naar de Power BI-service zijn gepubliceerd. 

U configureert Pagina automatisch vernieuwen voor rapporten in de Power BI-service met behulp van stappen die vergelijkbaar zijn met de configuratiestappen in Power BI Desktop. Wanneer het automatisch vernieuwen van pagina's is geconfigureerd in de Power BI-service, wordt dit ook ondersteund voor [ingesloten Power BI-inhoud](../developer/embedded/embedding.md). Deze afbeelding toont de configuratie voor **Pagina vernieuwen**  voor de Power BI-service:

![Automatisch pagina vernieuwen in de Power BI-service](media/desktop-automatic-page-refresh/automatic-page-refresh-04.png)

Deze beschrijvingen komen overeen met de genummerde elementen: 

1.    Hiermee schakelt u het vernieuwen van pagina's in of uit.
2.    Getalwaarde voor het vernieuwingsinterval van de pagina's. Dit moet een geheel getal zijn.
3.    Eenheid voor het vernieuwingsinterval van de pagina's.

### <a name="page-refresh-intervals"></a>Intervallen voor Pagina vernieuwen

De intervallen die voor Pagina vernieuwen in de Power BI-service zijn toegestaan, worden beïnvloed door het type werkruimte van het rapport. Dit geldt voor deze rapporten:

* Een rapport publiceren naar een werkruimte waarvoor Pagina automatisch vernieuwen is ingeschakeld
* Het vernieuwingsinterval van een pagina bewerken die al in een werkruimte voorkomt
* Een rapport rechtstreeks in de service maken

Er zijn geen beperkingen voor vernieuwingsintervallen in Power BI Desktop. Het vernieuwingsinterval kan zo vaak als elke seconde zijn. Als er echter rapporten worden gepubliceerd naar de Power BI-service, zijn bepaalde beperkingen van toepassing. Deze beperkingen worden beschreven in de volgende secties.

### <a name="restrictions-on-refresh-intervals"></a>Beperkingen voor vernieuwingsintervallen

In de Power BI-service gelden beperkingen voor het automatisch vernieuwen van pagina's op basis van factoren zoals de werkruimte en of u Premium-services gebruikt.

Om te verduidelijken hoe deze beperkingen werken, beginnen we met wat achtergrondinformatie over capaciteiten en werkruimten.

*Capaciteiten* zijn een belangrijk concept in Power BI. Ze vertegenwoordigen bepaalde resources (opslag, processor en geheugen) die worden gebruikt om Power BI-inhoud te hosten en te leveren. Capaciteiten worden gedeeld of zijn toegewezen. Een *gedeelde capaciteit* wordt gedeeld met andere klanten van Microsoft. Een *toegewezen capaciteit* wordt volledig gereserveerd voor één klant. Zie [Premium-capaciteiten beheren](../admin/service-premium-capacity-manage.md) voor een introductie tot toegewezen capaciteiten.

Met gedeelde capaciteit worden workloads uitgevoerd via rekenresources die met andere klanten worden gedeeld. Omdat de capaciteit resources moet delen, worden er beperkingen opgelegd om ervoor te zorgen dat alles *op een rechtvaardige basis* gebeurt, bijvoorbeeld door het instellen van een maximale modelgrootte (1 GB) en van een maximale vernieuwingsfrequentie per dag (acht keer per dag).

Power BI-*werkruimten* bevinden zich in capaciteiten. Ze vertegenwoordigen de containers voor beveiliging, samenwerking en implementatie. Elke Power BI-gebruiker heeft een persoonlijke werkruimte die **Mijn werkruimte** heet. Er kunnen extra werkruimten worden gemaakt om samenwerking en implementatie mogelijk te maken. Deze worden *werkruimten* genoemd. Werkruimten, met inbegrip van persoonlijke werkruimten, worden standaard gemaakt in de gedeelde capaciteit.

Hier volgen enkele details met betrekking tot de twee werkruimtescenario's:

**Gedeelde werkruimten**. Voor reguliere werkruimten (werkruimten die geen deel uitmaken van een Premium-capaciteit), heeft automatische paginavernieuwing een minimum interval van 30 minuten (het kleinste interval dat is toegestaan).

**Premium-werkruimten**. De beschikbaarheid van automatische paginavernieuwing in Premium-werkruimten is afhankelijk van de workloadinstellingen die uw Premium-beheerder voor de Power BI Premium-capaciteit heeft ingesteld. Er zijn twee variabelen die van invloed kunnen zijn op de mogelijkheid om het automatisch vernieuwen van pagina's in te stellen:

 - **Functie aan/uit**. Als uw capaciteitsbeheerder heeft besloten de functie uit te schakelen, kunt u geen type paginavernieuwing instellen in het door u gepubliceerde rapport.

 - **Minimaal vernieuwingsinterval**. Als u de functie inschakelt, moet uw capaciteitsbeheerder een minimaal vernieuwingsinterval instellen. Als uw interval kleiner is dan het minimum, wordt het interval door de Power BI-service overschreven om prioriteit te geven aan het minimale interval dat is ingesteld door de capaciteitsbeheerder. Deze overschrijving wordt aangeduid als 'Overschrijving capaciteitsbeheerder' in de volgende tabel. 

In deze tabel wordt gedetailleerder beschreven waar deze functie beschikbaar is en wat de beperkingen zijn voor elk capaciteitstype en elke [opslagmodus](../connect-data/service-dataset-modes-understand.md):

| Opslagmodus | Toegewezen capaciteit | Gedeelde capaciteit |
| --- | --- | --- |
| DirectQuery | **Ondersteund**: Ja <br>**Minimaal vernieuwingsinterval**: 1 seconde <br>**Overschrijving capaciteitsbeheerder**: Ja | **Ondersteund**: Ja <br>**Minimaal vernieuwingsinterval**: 30 minuten <br>**Overschrijving capaciteitsbeheerder**: Nee |
| Importeren | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. |
| Gemengde modus (DirectQuery en andere gegevensbronnen) | **Ondersteund**: Ja <br>**Minimaal vernieuwingsinterval**: 1 seconde <br>**Overschrijving capaciteitsbeheerder**: Ja | **Ondersteund**: Ja <br>**Minimaal vernieuwingsinterval**: 30 minuten <br>**Overschrijving capaciteitsbeheerder**: Nee |
| Live Connect AS | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. |
| Live connect PBI | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. | **Ondersteund**: Nee <br>**Minimaal vernieuwingsinterval**: N.v.t. <br>**Overschrijving capaciteitsbeheerder**: N.v.t. |

> [!NOTE]
> Als u het rapport waarvoor u het automatisch vernieuwen van pagina's hebt ingeschakeld, van Power BI Desktop naar de service publiceert, moet u de referenties voor de DirectQuery-gegevensbron opgeven in het menu met gegevenssetinstellingen.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Er is een aantal dingen waar u aan moet denken als u het automatisch vernieuwen van pagina's gebruikt in Power BI Desktop of in de Power BI-service:

* De opslagmodi Importeren, LiveConnect en Push worden niet ondersteund voor Pagina automatisch vernieuwen.  
* Samengestelde modellen met minimaal één DirectQuery-gegevensbron worden ondersteund.
* Er zijn geen beperkingen voor vernieuwingsintervallen in Power BI Desktop. Het interval kan zo vaak als elke seconde zijn. Als er echter rapporten worden gepubliceerd naar de Power BI-service, zijn bepaalde beperkingen van toepassing, zoals [eerder](#restrictions-on-refresh-intervals) in dit artikel is beschreven.
* SharePoint Online insluiten, ondersteunt geen automatisch vernieuwen van pagina’s.

### <a name="performance-diagnostics"></a>Diagnostische gegevens over prestaties

Pagina automatisch vernieuwen is nuttig voor het bewaken van scenario's en het verkennen van gegevens die snel veranderen. Soms kan dit de capaciteit of de gegevensbron onnodig zwaar belasten.

In Power BI kan op de volgende manieren worden voorkomen dat gegevensbronnen onnodig worden belast:

- Alle query's die voor het automatisch vernieuwen van pagina's worden uitgevoerd, krijgen een lagere prioriteit zodat interactieve query's (zoals voor het laden van pagina's en visuals voor kruislings filteren) voorrang krijgen.
- Als een query niet is voltooid voordat de volgende vernieuwingscyclus start, start Power BI geen nieuwe vernieuwingsquery's totdat alle eerdere query's zijn voltooid. Als u een vernieuwingsinterval hebt van één seconde en uw query's gemiddeld vier seconden duren, start Power BI in feite alleen om de vier seconden een query.

Er zijn twee gebieden waar u nog steeds knelpunten tegenkomt die de prestaties beïnvloeden:

1. **De capaciteit**. De query bereikt eerst de Premium-capaciteit waardoor de DAX-query die van de rapportvisualisaties zijn gemaakt, wordt samengevouwen en geëvalueerd.
2. **Het type DirectQuery-gegevensbron**. de vertaalde query's uit de vorige stap worden dan op de bron uitgevoerd. Mogelijke bronnen zijn uw SQL-servers-exemplaren, SAP Hana-bronnen, enzovoort.

Met behulp van de [app Premium Capacity Metrics](../admin/service-admin-premium-monitor-capacity.md) (metrische gegevens voor Premium-capaciteit), die beschikbaar is voor beheerders, kunt u visualiseren hoeveel van de capaciteit wordt gebruikt door query's met een lage prioriteit.

Query's met een lage prioriteit zijn onder andere query's voor het automatisch vernieuwen van pagina's en query's voor het vernieuwen van modellen. Er bestaat momenteel geen manier om een onderscheid te maken tussen de belasting die wordt gevormd door query's voor het automatisch vernieuwen van pagina's en die voor het vernieuwen van modellen.

Als u merkt dat uw capaciteit overbelast wordt door query's met een lage prioriteit, kunt u een aantal dingen doen:

- Vraag een grotere Premium-SKU aan.
- Vraag de eigenaar van het rapport om het vernieuwingsinterval te verkleinen.
- In de portal voor de capaciteitsbeheerder kunt u het volgende doen:
   - Pagina automatisch vernieuwen voor die capaciteit uitschakelen.
   - Het minimale vernieuwingsinterval verhogen, wat gevolgen heeft voor alle rapporten in die capaciteit.


### <a name="frequently-asked-questions"></a>Veelgestelde vragen

**Ik ben een rapportauteur. Ik heb het vernieuwingsinterval van mijn rapport in Power BI Desktop ingesteld op één seconde, maar nadat mijn rapport is gepubliceerd wordt het niet vernieuwd in de service.**

* Zorg ervoor dat Pagina automatisch vernieuwen is ingeschakeld voor de pagina. Omdat deze instelling per pagina geldt, moet u ervoor zorgen dat deze is ingeschakeld voor elke pagina in het rapport die u wilt vernieuwen.
* Controleer of u het rapport hebt geüpload naar een werkruimte met een gekoppelde Premium-capaciteit. Als u dat nog niet hebt gedaan, wordt het vernieuwingsinterval op 30 minuten vergrendeld.
* Als uw rapport zich in een Premium-werkruimte bevindt, vraagt u uw beheerder of deze functie voor de gekoppelde capaciteit is ingeschakeld. Zorg er ook voor dat het minimale vernieuwingsinterval voor de capaciteit kleiner is dan of gelijk is aan het interval voor uw rapport.

**Ik ben een capaciteitsbeheerder. Ik heb de instellingen voor mijn automatische paginavernieuwingsinterval gewijzigd, maar de wijzigingen worden niet weergegeven. Met andere woorden, rapporten worden nog steeds vernieuwd met een onjuiste snelheid, of worden helemaal niet vernieuwd, zelfs nadat ik Pagina automatisch vernieuwen had ingeschakeld.**

* Het kan wel vijf minuten duren voordat gewijzigde instellingen in de gebruikersinterface voor de capaciteitsbeheerder in rapporten merkbaar zijn.
* Behalve dat u de functie Pagina automatisch vernieuwen voor de capaciteit moet inschakelen, moet u deze ook inschakelen voor de pagina's in een rapport waar u wilt dat dit zichtbaar is.

**Mijn rapport wordt in de gemengde modus uitgevoerd. (Gemengde modus betekent dat het rapport een DirectQuery-verbinding en een gegevensbron voor importeren heeft.) Sommige visuals worden niet vernieuwd.**

- Als uw visuals naar importtabellen verwijzen, is dit gedrag normaal. Pagina automatisch vernieuwen wordt niet ondersteund voor importeren.
- Zie de eerste vraag in deze sectie.

**Mijn rapport werd correct vernieuwd in de service, maar plotseling stopte het.**

* Vernieuw de pagina om te zien of het probleem zich vanzelf oplost.
* Neem contact op met uw capaciteitsbeheerder. Mogelijk heeft de beheerder de functie uitgeschakeld of het minimale vernieuwingsinterval verhoogd. (Zie de tweede vraag in deze sectie.)

**Ik ben een rapportauteur. Mijn visuals worden niet vernieuwd met de frequentie die ik heb opgegeven. Ze worden met een lagere snelheid vernieuwd.**

* Als uw query's langer duren, vertraagt het vernieuwingsinterval. Pagina automatisch vernieuwen wacht totdat alle query's zijn voltooid voordat nieuwe query's worden gestart.
* Uw capaciteitsbeheerder heeft mogelijk een minimaal vernieuwingsinterval ingesteld dat hoger is dan wat u voor uw rapport hebt ingesteld. Vraag uw capaciteitsbeheerder het minimale vernieuwingsinterval te verlagen.

**Maken query's voor het automatisch vernieuwen van pagina's gebruik van de cache?**

* Nee. Alle query's voor het automatisch vernieuwen van pagina's maken geen gebruik van gegevens in de cache.


## <a name="next-steps"></a>Volgende stappen

Raadpleeg deze artikelen voor meer informatie:

* [DirectQuery gebruiken in Power BI](../connect-data/desktop-directquery-about.md)
* [Samengestelde modellen in Power BI Desktop gebruiken](../transform-model/desktop-composite-models.md)
* [Performance Analyzer gebruiken om prestaties van rapportelementen te onderzoeken](desktop-performance-analyzer.md)
* [Power BI Premium-capaciteiten implementeren en beheren](../guidance/whitepaper-powerbi-premium-deployment.md)
* [Gegevensbronnen in Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Gegevens vormgeven en combineren in Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop](../connect-data/desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)   
* [Enter data directly into Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)   
