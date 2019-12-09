---
title: Microsoft Power BI Premium-capaciteiten beheren
description: Beschrijft de beheertaken voor Power BI Premium-capaciteiten.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697469"
---
# <a name="managing-premium-capacities"></a>Premium-capaciteiten beheren

Het beheer van Power BI Premium omvat het maken, beheren en bewaken van Premium-capaciteiten. In dit artikel krijgt u een overzicht van capaciteiten. Raadpleeg [Capaciteiten configureren en beheren](service-admin-premium-manage.md) voor stapsgewijze instructies.

## <a name="creating-and-managing-capacities"></a>Capaciteiten maken en beheren

Op de pagina **Capaciteitsinstellingen** van de Power BI-portal wordt het aantal aangeschafte v-cores en beschikbare Premium-capaciteiten weergegeven. Op de pagina kunnen globale Office 365-beheerders of Power BI-servicebeheerders Premium-capaciteiten maken van beschikbare v-cores, of bestaande Premium-capaciteiten bewerken.

Wanneer u een Premium-capaciteit maakt, moeten beheerders het volgende definiëren:

- Capaciteitsnaam (uniek binnen de tenant).
- Capaciteitsbeheerder(s).
- Capaciteitsgrootte.
- Regio voor gegevensopslag.

Er moet minstens één capaciteitsbeheerder worden aangewezen. Gebruikers die zijn aangewezen als capaciteitsbeheerder kunnen het volgende doen:

- Werkruimten toewijzen aan de capaciteit.
- Gebruikersmachtigingen beheren om aanvullende capaciteitsbeheerders of -gebruikers toe te voegen met toewijzingsmachtigingen (zodat zij werkruimten kunnen toewijzen aan de capaciteit).
- Workloads beheren om het maximale geheugengebruik te configureren voor gepagineerde rapporten en workloads van gegevensstromen.
- De capaciteit opnieuw opstarten om bij overbelasting van het systeem alle bewerkingen opnieuw in te stellen.

Capaciteitsbeheerders hebben geen toegang tot inhoud in werkruimten, tenzij er expliciet werkruimtemachtigingen zijn toegewezen. Ze hebben ook geen toegang tot alle Power BI-beheergedeelten (tenzij expliciet toegewezen), zoals metrische gegevens over het gebruik, auditlogboeken of tenantinstellingen. Belangrijker is dat capaciteitsbeheerders geen machtigingen hebben om nieuwe capaciteiten te maken of bestaande capaciteiten te schalen. Beheerders worden toegewezen op capaciteitsbasis, zodat ze alleen de capaciteiten waaraan ze zijn toegewezen kunnen bekijken en beheren.

De capaciteitsgrootte wordt geselecteerd uit een beschikbare lijst SKU-opties die wordt beperkt door het aantal beschikbare v-cores in de pool. Het is mogelijk om meerdere capaciteiten te maken vanuit de pool, die kunnen worden gemaakt uit een of meer aangeschafte SKU's. Bijvoorbeeld een P3-SKU (32 v-cores) kan worden gebruikt om drie capaciteiten te maken: een P2 (16 v-cores) en twee keer een P1 (2 x 8 v-cores). Verbeterde prestaties en schaal kunnen worden bereikt door kleinere capaciteiten te maken, zoals wordt beschreven in het artikel [Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md). In de volgende afbeeldingen ziet u het voorbeeld van de fictieve organisatie Contoso, die bestaat uit vijf Premium-capaciteiten (drie keer P1 en twee keer P3). Elke capaciteit bevat werkruimten en verschillende werkruimten in een gedeelde capaciteit.

![Voorbeeld van de fictieve organisatie Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Een Premium-capaciteit kan worden toegewezen aan een regio anders dan de regio van de Power BI-tenant, ook wel multigeografie genoemd. Multigeografie zorgt voor administratieve controle over datacentra binnen gedefinieerde geografische regio's waarin uw Power BI-inhoud zich bevindt. De gedachte achter multigeografische implementatie is doorgaans zakelijke compliance of overheidsnaleving in plaats van prestaties en schaal. Voor het laden van rapporten en dashboards zijn nog steeds verzoeken bij de thuisregio van de metagegevens nodig. Raadpleeg [Ondersteuning van Multi-Geo voor Power BI Premium](service-admin-premium-multi-geo.md) voor meer informatie.

Power BI-servicebeheerders en globale Office 365-beheerders kunnen Premium-capaciteiten bewerken. In het bijzonder is het volgende mogelijk:

- De capaciteitsgrootte wijzigen om resources omhoog of omlaag te schalen.
- Capaciteitsbeheerders toevoegen of verwijderen.
- Gebruikers met toewijzingsmachtigingen toevoegen of verwijderen.
- Aanvullende workloads toevoegen of verwijderen.
- Regio's wijzigen.

Er zijn toewijzingsmachtigingen nodig om een werkruimte toe te wijzen aan een specifieke Premium-capaciteit. De machtigingen kunnen worden verleend aan de hele organisatie, specifieke gebruikers of groepen.

Standaard ondersteunen Premium-capaciteiten workloads die aan de uitvoering van Power BI-query's zijn gekoppeld. Premium-capaciteiten ondersteunen ook aanvullende workloads: **AI (Cognitive Services)** , **Gepagineerde rapporten** en **Gegevensstromen**. Voor elke workload moet u de maximale hoeveelheid geheugen configureren (als percentage van het totaal aan beschikbaar geheugen) die door de workload kan worden gebruikt. Het is belangrijk te begrijpen dat het verhogen van maximaal geheugen van invloed kan zijn op het aantal actieve modellen dat kan worden gehost en op de doorvoer van vernieuwingen. 

Geheugen wordt dynamisch toegewezen aan gegevensstromen, maar in het geval van gepagineerde rapporten betreft het een statische toewijzing. De reden voor een statische toewijzing van het maximumgeheugen is dat gepagineerde rapporten worden uitgevoerd binnen een beveiligde ruimte van de capaciteit. Het geheugen van gepagineerde rapporten moet zorgvuldig worden ingesteld, aangezien dat het beschikbare geheugen voor het laden van modellen beperkt. Raadpleeg de [standaard geheugeninstellingen](service-admin-premium-workloads.md#default-memory-settings) voor meer informatie.

Het is mogelijk een Premium-capaciteit te verwijderen, dat leidt niet tot de verwijdering van de werkruimten en inhoud daarin. In plaats daarvan worden toegewezen werkruimten verplaatst naar een gedeelde capaciteit. Wanneer de Premium-capaciteit is gemaakt in een andere regio, wordt de werkruimte verplaatst naar de gedeelde capaciteit van de thuisregio.

### <a name="assigning-workspaces-to-capacities"></a>Werkruimten toewijzen aan capaciteiten

Werkruimten kunnen worden toegewezen aan een Premium-capaciteit in de Power BI-beheerdersportal, of in het venster **Werkruimte** voor een werkruimte.

Capaciteitsbeheerders, evenals globale Office 365-beheerders of Power BI-servicebeheerders, kunnen werkruimten in bulk toewijzen in het Power BI-beheerdersportal. Bulksgewijs toewijzen is van toepassing op:

- **Werkruimten van gebruikers**: alle werkruimten van die gebruikers, inclusief persoonlijke werkruimtes, worden toegewezen aan de Premium-capaciteit. Werkruimten die al zijn toegewezen aan een andere Premium-capaciteit worden ook meegenomen. Bovendien krijgen ook de gebruikers toewijzingsmachtigingen voor werkruimten toegewezen.

- **Specifieke werkruimten**
- **Werkruimten van de hele organisatie**: alle werkruimten, inclusief persoonlijke werkruimtes, worden toegewezen aan de Premium-capaciteit. Alle huidige en toekomstige gebruikers krijgen toewijzingsmachtigingen voor werkruimten toegewezen. Deze methode wordt niet aanbevolen. Een meer gerichte aanpak verdient de voorkeur.

Er kan een werkruimte worden toegevoegd aan een Premium-capaciteit via het venster **Werkruimte**, mits de gebruiker een werkruimtebeheerder is en toewijzingsmachtigingen heeft.

![Het venster Werkruimte gebruiken om een werkruimte toe te wijzen aan een Premium-capaciteit](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Werkruimtebeheerders kunnen een werkruimte verwijderen uit een capaciteit (naar een gedeelde capaciteit) en hebben daar geen toewijzingsmachtigingen voor nodig. Als werkruimten worden verwijderd uit toegewezen capaciteiten, wordt de werkruimte in praktijk naar een gedeelde capaciteit verplaatst. Houd er rekening mee dat de verwijdering van een werkruimte uit een Premium-capaciteit mogelijk negatieve gevolgen heeft. Gedeelde inhoud is mogelijk niet meer beschikbaar voor gelicentieerde gebruikers van de gratis versie van Power BI, of gepland vernieuwen wordt mogelijk opgeschort wanneer de door gedeelde capaciteiten ondersteunde limieten worden overschreden.

In de Power BI-service is een werkruimte die is toegewezen aan een Premium-capaciteit makkelijk te herkennen aan een diamant naast de naam van de werkruimte.

![Een werkruimte die is toegewezen aan een Premium-capaciteit identificeren](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Capaciteiten bewaken

De bewaking van Premium-capaciteiten biedt beheerders inzicht in de prestaties van capaciteiten. U bewaakt capaciteiten via de Power BI-beheerdersportal of de app **Power BI Premium Capacity Metrics** (van Power BI).

### <a name="power-bi-admin-portal"></a>Power BI-beheerportal

In de beheerdersportal biedt het tabblad **Status** voor elke capaciteit een overzicht van metrische gegevens voor de capaciteit en elke ingeschakelde workload. Metrische gegevens weergeven een gemiddelde van de afgelopen zeven dagen.  

Op het capaciteitsniveau zijn metrische gegevens een optelsom van alle ingeschakelde workloads. De volgende metrische gegevens worden gegeven:

- **CPU-GEBRUIK**: geef het gemiddelde CPU-gebruik als percentage van de totale beschikbare CPU voor de capaciteit.  
- **GEHEUGENGEBRUIK**: geeft het gemiddelde geheugengebruik (in GB) als een totaal van beschikbaar geheugen van de capaciteit. 

Voor elke ingeschakelde workload worden het CPU-gebruik en geheugengebruik gegeven, evenals een aantal metrische gegevens die specifiek zijn voor een workload. Voor bijvoorbeeld de workload Gegevensstroom geeft **Totaalaantal** het aantal vernieuwingen voor elke gegevensstroom weer. **Gemiddelde duur** geeft de gemiddelde duur van een vernieuwing voor de gegevensstroom weer.

![Tabblad Capaciteitsstatus in de portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Voor meer informatie over alle beschikbare metrische gegevens voor elke workload raadpleegt u [Capaciteiten bewaken in de beheerdersportal](service-admin-premium-monitor-portal.md).

De bewakingsmogelijkheden in de Power BI-portal zijn ontworpen voor een snel overzicht van belangrijke metrische gegevens voor de capaciteit. Voor gedetailleerdere bewaking wordt het aanbevolen dat u gebruikmaakt van de app **Power BI Premium Capacity Metrics**.

### <a name="power-bi-premium-capacity-metrics-app"></a>De app Power BI Premium Capacity Metrics

De [Power BI Premium Capacity Metrics-app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) is een Power BI-app die beschikbaar is voor capaciteitsbeheerders en die net als andere Power BI-apps wordt geïnstalleerd. Het bevat een dashboard en een rapport.

![De app Power BI Premium Capacity Metrics](media/service-premium-capacity-manage/capacity-metrics-app.png)

Wanneer de app wordt geopend, wordt het dashboard geladen en worden er meerdere tegels weergegeven met een geaggregeerde weergave van alle capaciteiten waarvan de gebruiker capaciteitsbeheerder is. De indeling van het dashboard bevat vijf hoofdgedeeltes:

- **Overzicht**: app-versie, aantal capaciteiten en werkruimten
- **Systeemoverzicht**: metrische gegevens van geheugen- en CPU-gebruik
- **Samenvatting van gegevensset**: aantal gegevenssets, DQ/LC, vernieuwingen en metrische gegevens van query's
- **Samenvatting van gegevensstroom**: aantal gegevensstromen en metrische gegevens van gegevensset
- **Samenvatting van gepagineerd rapport**: metrische gegevens van vernieuwingen en weergaven

Het onderliggende rapport, waaruit de dashboardtegels zijn vastgemaakt, kan worden geopend door te klikken op een dashboardtegel. Het biedt een gedetailleerder perspectief van elke van de dashboardgegevens en ondersteunt interactieve filtering. 

U filtert door slicers in te stellen op datumbereik, capaciteit, werkruimte en workload (rapport, gegevensset gegevensstroom) en door elementen te selecteren binnen rapportvisuals om de rapportpagina kruislings te filteren. Kruislings filteren is een goede techniek om specifieke tijdsperioden, capaciteiten, werkruimten, gegevenssets enz. te beperken en kan erg nuttig zijn om hoofdoorzaakanalyses uit te voeren.

Raadpleeg [Premium-capaciteiten bewaken met de app](service-admin-premium-monitor-capacity.md) voor meer informatie over metrische gegevens van dashboards en rapporten in de app.

### <a name="interpreting-metrics"></a>Metrische gegevens interpreteren

Metrische gegevens moeten worden bewaakt voor een basisbegrip van resourcegebruik en workloadactiviteit. Als de capaciteit langzamer wordt, is het belangrijk te begrijpen welke metrische gegevens moeten worden bewaakt en welke conclusies u kunt trekken.

In het ideale geval moeten query's binnen een seconde zijn voltooid voor een reactieve ervaring bij rapportgebruikers en voor een hogere doorvoer van query's. Het is meestal minder erg dat processen op de achtergrond, waaronder vernieuwingen, langer duren.

Over het algemeen zijn langzame rapporten een indicatie van een overbelaste capaciteit. Wanneer rapporten niet worden geladen, is dit een indicatie van een overbelaste capaciteit. In beide gevallen kan de hoofdoorzaak in veel factoren worden gezocht, waaronder:

- **Mislukt query's**. Die geven een zekere geheugendruk aan en dat een model niet kan worden geladen in het geheugen. De Power BI-service probeert een model 30 seconden lang te laden voordat het mislukt.

- **Buitensporige querywachttijden**. Dit heeft mogelijk meerdere oorzaken:
  - De Power BI-service moet eerst modellen verwijderen en vervolgens het model laden waarop de query moet worden uitgevoerd (onthoud dat veel verwijderingen uit de gegevensset geen indicatie zijn van druk op de capaciteit, tenzij dit gepaard gaat met langere querywachttijden waaruit geheugenthrashing blijkt).
  - Modellaadtijden (in het bijzonder de wachttijd bij het laden van een groter model in het geheugen).
  - Langdurige query's.
  - Te veel LC\DQ-verbindingen (meer dan capaciteitslimieten).
  - CPU-verzadiging.
  - Complexe rapportontwerpen met veel visuals op een pagina (onthoud dat een visual een query is).

- **Een lange queryduur** geeft mogelijk aan dat modelontwerpen niet zijn geoptimaliseerd, in het bijzonder wanneer meerdere gegevenssets actief zijn in een capaciteit en maar één gegevensset voor een lange queryduur zorgt. Dit geeft aan dat de capaciteit voldoende resources heeft en dat de betreffende gegevensset suboptimaal of gewoon langzaam is. Langdurige query's kunnen problematisch zijn, omdat ze de toegang tot resources blokkeren die andere processen nodig hebben.
- **Lange vernieuwingswachttijden** geven onvoldoende geheugen aan door veel actieve modellen die geheugen gebruiken, of dat een vernieuwing met een fout andere vernieuwingen blokkeert (waardoor parallelle vernieuwingslimieten worden overschreden).

U vindt een gedetailleerdere uitleg over het gebruik van de metrische gegevens in het artikel [Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Erkenningen

Dit artikel is geschreven door Peter Myers, Data Platform MVP en onafhankelijk BI-expert bij [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Premium-capaciteiten optimaliseren](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Workloads configureren in een Premium-capaciteit](service-admin-premium-workloads.md)   

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

