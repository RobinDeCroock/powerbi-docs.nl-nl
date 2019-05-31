---
title: Microsoft Power BI Premium-capaciteiten beheren
description: Beschrijving van beheertaken voor Power BI Premium-capaciteiten.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565249"
---
# <a name="managing-premium-capacities"></a>Premium-capaciteiten beheren

Power BI Premium beheren omvat het maken, beheren en controleren van Premium-capaciteiten.

## <a name="creating-and-managing-capacities"></a>Het maken en beheren van capaciteit

De **capaciteitsinstellingen** pagina van de Power BI-beheerportal geeft het aantal v-cores aangeschaft en Premium-capaciteiten beschikbaar. Op de pagina kunt Office 365 globale beheerders of Power BI-servicebeheerders aan Premium-capaciteiten van beschikbare v-cores maken of te wijzigen van bestaande Premium-capaciteiten.

Bij het maken van een Premium-capaciteit, wordt beheerders zijn vereist om te definiëren:

- Capaciteitsnaam (uniek zijn binnen de tenant).
- Capaciteit admin(s).
- Capaciteitsgrootte.
- Regio voor gegevensopslag.

Ten minste één Capaciteitsbeheerder moet worden toegewezen. Gebruikers die zijn toegewezen als Capaciteitsbeheerders kunt doen:

- Werkruimten toewijzen aan de capaciteit.
- Gebruikersmachtigingen, voor het toevoegen van extra Capaciteitsbeheerders of gebruikers met toewijzingsmachtigingen (zodat ze werkruimten toewijzen aan de capaciteit) beheren.
- Workloads voor het configureren van maximale geheugengebruik voor gepagineerde rapporten en gegevensstromen workloads beheren.
- Start opnieuw op de capaciteit, opnieuw instellen van alle bewerkingen vanwege een overbelasting van het systeem.

Capaciteitsbeheerders heeft geen toegang tot inhoud van de werkruimte, tenzij expliciet in de werkruimtemachtigingen zijn toegewezen. Ze ook geen toegang tot alle gebieden van de Power BI-beheerder (tenzij expliciet toegewezen), zoals metrische gegevens over gebruik, auditlogboeken of tenantinstellingen. Bovendien bent Capaciteitsbeheerders niet gemachtigd voor het maken van nieuwe capaciteiten of bestaande capaciteiten te schalen. Beheerders zijn toegewezen op basis van de capaciteit per, ervoor te zorgen dat ze kunnen alleen weergeven en beheren van de capaciteiten waarvoor ze zijn toegewezen.

Capaciteitsgrootte is geselecteerd in een lijst met beschikbare SKU-opties, die wordt beperkt door het aantal beschikbare v-cores in de groep. Het is mogelijk te maken van meerdere capaciteiten in de groep, die kan worden afkomstig is van een of meer SKU's die zijn aangeschaft. Bijvoorbeeld een P3 SKU (32 v-cores) kunnen worden gebruikt voor het maken van drie capaciteiten: één P2 (16 v-cores), en twee P1 (2 x 8 v-cores). Verbeterde prestaties en schaal kunnen worden bereikt door het maken van kleinere grootte capaciteiten, zoals beschreven in de [optimaliseren van Premium-capaciteiten](service-premium-capacity-optimize.md) artikel. De volgende afbeelding toont een voorbeeld van de instellingen voor de fictieve Contoso-organisatie die bestaat uit vijf Premium-capaciteiten (3 x P1 en 2 x P3) met elke met app-werkruimten en verschillende werkruimten in gedeelde capaciteit.

![Een voorbeeld van de instellingen voor de fictieve organisatie Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Een Premium-capaciteit kan worden toegewezen aan een andere regio dan de basisregio van de Power BI-tenant, bekend als meerdere geografische gebieden. Meerdere geografische gebieden biedt administratieve controle over welke datacenters in afgebakende geografische regio's uw Power BI-inhoud zich bevindt. De logica voor een implementatie van meerdere geografische gebieden wordt doorgaans gebruikt voor zakelijke of naleving van de overheid, in plaats van prestaties en schaalbaarheid. Rapport en dashboard laden omvat het nog steeds aanvragen voor de basisregio van voor metagegevens. Zie voor meer informatie, [ondersteuning voor meerdere geografische gebieden voor Power BI Premium](service-admin-premium-multi-geo.md).

Power BI-servicebeheerders en globale beheerders van Office 365 kunt Premium-capaciteiten wijzigen. Specifiek, kunnen ze:

- Wijzig de grootte van de capaciteit voor omhoog of omlaag schalen resources.
- Toevoegen of verwijderen van Capaciteitsbeheerders.
- Toevoegen of verwijderen van gebruikers die over toewijzingsmachtigingen beschikken.
- Toevoegen of verwijderen van extra werkbelasting.
- Regio's wijzigen.

Machtigingen voor capaciteitstoewijzingen zijn vereist voor een werkruimte toewijzen aan een specifieke Premium-capaciteit. De machtigingen kunnen worden verleend aan de hele organisatie, specifieke gebruikers of groepen.

Standaard ondersteuning voor Premium-capaciteiten werkbelastingen die zijn gekoppeld aan het uitvoeren van query's van Power BI. Premium-capaciteiten bieden ook ondersteuning voor extra workloads: **AI (Cognitive Services)** , **gepagineerde rapporten**, en **gegevensstromen**. Elke workload is vereist voor het configureren van de maximale hoeveelheid geheugen (als percentage van totale beschikbare geheugen) door de werkbelasting kan worden gebruikt. Het is belangrijk om te begrijpen dat maximale geheugentoewijzingen verhogen kan invloed hebben op het aantal actieve modellen die kan worden gehost en de doorvoer van wordt vernieuwd. 

Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar wordt statisch toegewezen aan gepagineerde rapporten. De reden voor het toewijzen van statisch de maximale hoeveelheid geheugen is dat gepagineerde rapporten worden uitgevoerd binnen een beveiligde ruimte van de capaciteit die wordt ingesloten. Zorg moet worden uitgevoerd wanneer de instelling gepagineerde rapporten geheugen als beperkt het beschikbare geheugen voor het laden van modellen. Zie voor meer informatie, de [geheugen standaardinstellingen](service-admin-premium-workloads.md#default-memory-settings).

Verwijderen van een Premium-capaciteit is mogelijk en wordt niet leiden tot het verwijderen van de werkruimten en de inhoud. In plaats daarvan wordt elk toegewezen werkruimten verplaatst naar gedeelde capaciteit. Wanneer de Premium-capaciteit is gemaakt in een andere regio, wordt de werkruimte wordt verplaatst naar gedeelde capaciteit van de eigen regio.

### <a name="assigning-workspaces-to-capacities"></a>Werkruimten toewijzen aan capaciteit

Werkruimten kunnen worden toegewezen aan een Premium-capaciteit in de Power BI-beheerportal of, voor een app-werkruimte de **werkruimte** deelvenster.

Capaciteitsbeheerders, evenals globale beheerders van Office 365 of Power BI-servicebeheerders kunnen bulksgewijs werkruimten toewijzen in de Power BI-beheerportal. Toegewezen bulksgewijs kunt toepassen op:

- **Werkruimten door gebruikers** -alle werkruimten die eigendom zijn van gebruikers, met inbegrip van persoonlijke werkruimten zijn toegewezen aan de Premium-capaciteit. Hierbij wordt het opnieuw toewijzen van werkruimten wanneer ze al zijn toegewezen aan een ander Premium-capaciteit. Bovendien zijn de gebruikers ook machtigingen voor capaciteitstoewijzingen werkruimte toegewezen.

- **Specifieke werkruimten**
- **Werkruimten van de hele organisatie** -alle werkruimten, met inbegrip van persoonlijke werkruimten zijn toegewezen aan de Premium-capaciteit. Alle huidige en toekomstige gebruikers zijn werkruimte toewijzingsmachtigingen toegewezen. Deze methode wordt niet aanbevolen. Een meer gerichte aanpak verdient de voorkeur.

Een werkruimte kan worden toegevoegd aan een Premium-capaciteit met behulp van de **werkruimte** deelvenster leveren van de gebruiker is zowel een beheerder van de werkruimte en machtigingen voor capaciteitstoewijzingen heeft.

![Met behulp van het deelvenster met een werkruimte toewijzen aan een Premium-capaciteit](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Werkruimtebeheerders kunnen een werkruimte van een capaciteit (naar gedeelde capaciteit) verwijderen zonder machtiging voor werkruimtetoewijzingen. De werkruimte voor het verwijderen van werkruimten uit toegewezen capaciteit is het effectief worden verplaatst naar gedeelde capaciteit. Houd er rekening mee dat een werkruimte verwijderen uit een Premium-capaciteit mogelijk negatieve gevolgen leidt, bijvoorbeeld gedeelde inhoud niet meer beschikbaar is voor Power BI Free licentiëren gebruikers of opschorting van geplande vernieuwing wanneer ze langer zijn dan de limiet die wordt ondersteund door gedeelde capaciteit.

In de Power BI-service wordt een werkruimte die is toegewezen aan een Premium-capaciteit eenvoudig geïdentificeerd door de ruitvormig pictogram die adorns naam van de werkruimte.

![Identificeren van een werkruimte die is toegewezen aan een Premium-capaciteit](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Bewaking van capaciteit

Premium-capaciteiten bewaking biedt beheerders met een goed begrip van hoe de capaciteiten uitvoert. Capaciteit kunnen worden bewaakt met behulp van de Power BI-beheerportal of de **metrische gegevens over Power BI Premium capaciteit** app (Power BI).

### <a name="power-bi-admin-portal"></a>Power BI-beheerportal

In het beheerportal voor elke capaciteit, het **Health** tabblad bevat een samenvatting metrische gegevens voor de capaciteit en elke ingeschakelde workload. Prestatiegegevens geven een gemiddelde gedurende de afgelopen zeven dagen.  

Metrische gegevens zijn op het capaciteitsniveau van de, cumulatieve van alle ingeschakelde werkbelastingen. de volgende metrische gegevens zijn beschikbaar:

- **CPU-gebruik** -gemiddelde CPU-gebruik als een percentage van totaal beschikbare CPU-capaciteit biedt voor de capaciteit.  
- **GEHEUGENGEBRUIK** -biedt gemiddelde geheugengebruik (in GB) als een totaal van het beschikbare geheugen voor de capaciteit. 

Voor elke ingeschakelde werkbelasting, CPU-gebruik en geheugengebruik worden geleverd, evenals een aantal specifieke metrische gegevens voor een werkbelasting. Bijvoorbeeld: voor de werkbelasting gegevensstroom **totaal aantal** toont totaal aantal vernieuwingen voor elke gegevensstroom en **gemiddelde duur** toont de gemiddelde duur van vernieuwen voor de gegevensstroom.

![Capaciteit Health tabblad in de portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Zie voor meer informatie over alle beschikbare metrische gegevens voor elke werkbelasting, [bewaken capaciteiten in de beheerportal](service-admin-premium-monitor-portal.md).

De mogelijkheden voor bewaking in de Power BI-beheerportal zijn ontworpen voor een snel overzicht van metrische gegevens over belangrijke capaciteit. Voor meer controle gedetailleerde, wordt het aanbevolen gebruiken de **metrische gegevens over Power BI Premium capaciteit** app.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium capaciteit metrische gegevens app

De [metrische gegevens over Power BI Premium capaciteit app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) een Power BI-app beschikbaar voor capaciteitsbeheerders en net als elke andere Power BI-app is geïnstalleerd. Het bevat een dashboard en rapport.

![Power BI Premium capaciteit metrische gegevens app](media/service-premium-capacity-manage/capacity-metrics-app.png)

Wanneer de app wordt geopend, wordt het dashboard geladen om te presenteren talrijke tegels uitdrukken van een samengevoegde weergave over alle capaciteiten waarvan de gebruiker een Capaciteitsbeheerder is. De indeling van het dashboard bevat vijf hoofdonderdelen:

- **Overzicht** -App-versie, het aantal capaciteiten en werkruimten
- **Systeemoverzicht** -geheugen en CPU-metrische gegevens
- **Samenvatting van de gegevensset** - nummer van gegevenssets, DQ/LC, vernieuwen en query metrische gegevens
- **Samenvatting van de gegevensstroom** - nummer van de gegevensstromen en metrische gegevens voor gegevensset
- **Gepagineerd rapport overzicht** - vernieuwen en metrische gegevens weergeven

Het onderliggende rapport, van waaruit de dashboard-tegels zijn vastgemaakt, kan worden geopend door te klikken op een dashboardtegel. Het biedt een meer gedetailleerde perspectief van elk van de secties van het dashboard en biedt ondersteuning voor interactieve filteren. 

Filteren kan worden bereikt door in te stellen van slicers op datumbereik, capaciteit, werkruimte en werkbelasting (rapport, gegevensset, gegevensstroom) en door het selecteren van elementen in rapport visuals overschrijden de rapportpagina filteren. Kruislings filteren kan is een krachtige techniek om te beperken voor specifieke perioden, capaciteit, werkruimten, gegevenssets, enz. en zeer nuttig zijn bij het uitvoeren van analyses van hoofdoorzaken.

Zie voor gedetailleerde informatie over het dashboard en rapport metrische gegevens in de app [Monitor Premium-capaciteiten met de app](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Metrische gegevens interpreteren

Metrische gegevens moeten worden gecontroleerd voor het maken van een basislijn begrip van de activiteit voor het gebruik en de werkbelasting van resources. Als de capaciteit traag wordt, is het belangrijk om te begrijpen welke metrische gegevens voor het bewaken van en de conclusies die u kunt maken.

In het ideale geval zou query's binnen een tweede responsieve ervaringen bieden aan gebruikers en het inschakelen van hogere querydoorvoer voltooid. Het is doorgaans minder problematisch wanneer achtergrondprocessen - inclusief vernieuwingen - langer duurt om te voltooien.

Trage rapporten kunnen in het algemeen een indicatie van een capaciteit te veel verwarming zijn. Wanneer rapporten niet worden geladen, is dit een indicatie van een te veel hete capaciteit. In beide gevallen kan de hoofdoorzaak worden toe te rekenen aan verschillende factoren, met inbegrip van:

- **Mislukte query's** zeker geven geheugendruk en die een model kan niet worden geladen in het geheugen. Power BI-service probeert te laden van een model voor 30 seconden voordat deze is mislukt.

- **Overmatige query wachttijden** kan worden veroorzaakt door verschillende redenen:
  - De noodzaak van Power BI-service naar het eerste onbeschikbaar maken van modellen en laad vervolgens het model naar-worden opgevraagd (intrekken dat alleen verwijdering tarieven hogere gegevensset niet een indicatie van capaciteit stress die gepaard gaat, zijn tenzij vergezeld gaan van lange query wachttijden die wijzen op geheugenthrashing).
  - Model laden tijden (met name de wachttijd voor het laden van een grote model in het geheugen).
  - Langlopende query's.
  - Te veel LC\DQ-verbindingen (meer dan de capaciteitslimieten).
  - Belasting van de CPU.
  - Complexe rapport ontwerpen met een uitzonderlijk groot aantal visualisaties op een pagina (intrekken dat elk visuele element een query is).

- **Lange duur query** kan erop wijzen dat model modellen zijn niet geoptimaliseerd, met name wanneer meerdere gegevenssets actief in een capaciteit zijn, en slechts één gegevensset wordt geproduceerd lange duur van de query. Dit kan erop wijzen dat de capaciteit is voldoende resources voorzien en dat de gegevensset in de vraag suboptimale of alleen traag is. Langlopende query's kan problematisch zijn, aangezien ze toegang tot resources die vereist zijn andere processen kunnen blokkeren.
- **Lange vernieuwen wachttijden** wijzen onvoldoende geheugen beschikbaar vanwege een groot aantal actieve modellen geheugen, of dat een lastig vernieuwen wordt geblokkeerd door andere wordt vernieuwd (meer dan parallelle vernieuwen limieten).

Een meer gedetailleerde uitleg van het gebruik van de metrische gegevens die wordt beschreven in de [optimaliseren van Premium-capaciteiten](service-premium-capacity-optimize.md) artikel.

## <a name="acknowledgements"></a>Bevestigingen

In dit artikel is geschreven door Peter Myers, Data Platform MVP en onafhankelijke BI deskundige met [Bitsgewijs oplossingen](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Workloads configureren in een Premium-capaciteit](service-admin-premium-workloads.md)   

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

||||||
