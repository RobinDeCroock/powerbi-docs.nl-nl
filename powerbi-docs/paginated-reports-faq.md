---
title: 'Gepagineerde rapporten in Power BI: veelgestelde vragen (preview)'
description: In dit artikel vindt u antwoorden op veelgestelde vragen over gepagineerde rapporten. Deze rapporten bevatten een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer die is geoptimaliseerd voor afdrukken of het genereren van PDF's.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.openlocfilehash: cedf72585d7aa4f2ece39739dc0bdba33ca66e21
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "60987780"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Gepagineerde rapporten in Power BI: veelgestelde vragen (preview)

In dit artikel vindt u antwoorden op veelgestelde vragen over gepagineerde rapporten. Deze rapporten bevatten een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer die is geoptimaliseerd voor afdrukken of het genereren van PDF's. Ze worden 'gepagineerd' genoemd, omdat ze zo zijn opgemaakt dat ze op meerdere pagina's passen. Gepagineerde rapporten zijn gebaseerd op de RDL-rapporttechnologie in SQL Server Reporting Services. 

In dit artikel vindt u antwoorden op veelvoorkomende vragen over gepagineerde rapporten in Power BI Premium, en over Report Builder, het zelfstandige hulpprogramma voor het ontwerpen van gepagineerde rapporten. U hebt een Power BI Pro-licentie nodig om een rapport te publiceren in de service. U kunt gepagineerde rapporten publiceren en delen in Mijn werkruimte of in de app-werkruimten, zolang de werkruimte zich in een Power BI Premium-capaciteit bevindt. 

## <a name="administration"></a>Beheer

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Hoe groot moet de Premium-capaciteit zijn voor gepagineerde rapporten?

De werkbelasting van gepagineerde rapporten is beschikbaar op P1 – P3 SKU's voor openbare preview.  U kunt deze ook gebruiken voor test-/ontwikkelscenario's met A4 – A6-SKU's.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Wat is de maximum drempelwaarde van het geheugen dat ik voor gepagineerde rapporten in mijn capaciteit kan reserveren?

Momenteel kunt u slechts vijftig procent van het geheugen voor deze werkbelasting reserveren. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hoe werkt gebruikerstoegang voor gepagineerde rapporten?

Gebruikerstoegang voor gepagineerde rapporten is hetzelfde als gebruikerstoegang voor alle andere inhoud in de Power BI-service 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hoe schakel ik de werkbelasting voor mijn gepagineerde rapporten in of uit?

De capaciteitsbeheerder kan de werkbelasting voor de gepagineerde rapporten in- of uitschakelen op de portalpagina van de capaciteitsbeheerder.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Hoe kan ik het gebruik van gepagineerd rapporten in mijn tenant in de gaten houden?

Het gebruik van dit rapporttype wordt in de Office 365-auditlogboeken onder de volgende gebeurtenissen uitgebreid vermeld: 

- Power BI-rapport weergeven
- Power BI-rapport verwijderen
- Power BI-rapport maken
- Power BI-rapport gedownload

Het veld ReportType heeft de waarde PaginatedReport voor het identificeren van gepagineerde rapporten in plaats van Power BI-rapporten.

De auditlogboeken vermelden de volgende gebeurtenissen voor gepagineerde rapporten:

- Verbonden Power BI-gegevensset aan gateway
- Power BI-gegevensbron detecteren
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Kan ik deze werkbelasting bewaken via de bewakings-app voor Premium-capaciteit?

Ja, bewaking is via een nieuw tabblad beschikbaar met dezelfde relevante gegevens als die uit de Power BI-gegevenssets.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Heb ik een Pro-licentie nodig om gepagineerde rapporten te maken en publiceren?

Ja. U kunt zonder Pro-licentie geen rapporten naar de werkruimte uploaden. We raden u aan het downloaden en gebruiken van Power BI Report Builder zelfs zonder de Pro-licentie, maar u kunt de gepagineerde rapporten die u zonder dat deze maakt niet publiceren. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Wat gebeurt er als ik een gepagineerd rapport in een werkruimte heb en de werkbelasting van het gepagineerde rapport wordt uitgeschakeld?

U ontvangt een foutbericht en u kunt uw rapport pas weergeven als de werkbelasting opnieuw wordt ingeschakeld. U kunt het rapport wel uit de werkruimte verwijderen.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Wat is de standaardgeheugenruimte in elk van de Premium SKU's die voor gepagineerde rapporten worden ondersteund?

Standaardgeheugenruimte in elke Premium-SKU voor gepagineerde rapporten:

- **P1/A4**: standaard 20%; minimaal 10%
- **P2/A5**: standaard 20%; minimaal 5%
- **P3/A6**: standaard 20%; minimaal 2,5%

## <a name="general"></a>Algemeen

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Wanneer moet ik een gepagineerd rapport gebruiken in plaats van een Power BI-rapport?

Gepagineerde rapporten zijn het geschiktst voor scenario's waarvoor een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer is vereist, die is geoptimaliseerd voor afdrukken of het genereren van PDF's.  Een verlies- en winstrekening is een goed voorbeeld van het type rapport dat u waarschijnlijk als een gepagineerd rapport wilt opmaken.  

Power BI-rapporten zijn geoptimaliseerd voor verkenning en interactiviteit.  Een Power BI-rapport is ideaal voor een verkooprapport waarin verschillende verkopers de gegevens in hetzelfde rapport voor hun specifieke regio/branche/klant willen onderbrengen en willen bekijken hoe de cijfers veranderen.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>De documentatie vertelt dat Power BI Report Builder is voorkeur authoring tool. Kan ik gepagineerde rapporten maken in SQL Server Data Tools voor Power BI?

Ja, maar met de Power BI-service kunt u slechts één item per keer uploaden, dus veel scenario's die ontwerpers gebruiken met SQL Server Data Tools (SSDT) worden nog niet ondersteund. Zie de volledige [lijst met ondersteunde functies](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) verderop in deze Veelgestelde vragen.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Welke versie(s) van Report Builder worden ondersteund?

We Power BI Report Builder onlangs uitgebracht als primaire authoring tool voor gepagineerde rapporten in Power BI-Service. Installeer [Power BI Report Builder vanuit het Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hoe kan ik bestaande rapporten die in SQL Server Reporting Services zijn opgeslagen, naar Power BI verplaatsen?

U dient het rapport van de server te downloaden en vervolgens via de portal naar Power BI te uploaden.  Er is momenteel geen migratiehulpprogramma beschikbaar, maar mogelijk wordt er een gemaakt nadat de openbare preview is voltooid en de functiepariteit tussen de producten het juiste niveau heeft.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kan ik rapporten openen en rechtstreeks in de service publiceren?

Dat kan op dit moment niet. We voegen ondersteuning voor het openen van rapporten en het publiceren van ze rechtstreeks naar de service van Power BI Report Builder vóór de algemene beschikbaarheid, zoals u met Power BI Desktop kunt toe.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Welke functies van gepagineerde rapporten in SSRS worden nog niet in Power BI ondersteund?

Momenteel worden de volgende items nog niet door gepagineerde rapporten ondersteund:

- Gedeelde gegevensbronnen
- Gedeelde gegevenssets
- Subrapporten
- Doorklik- en drillthrough-acties
- Gekoppelde rapporten
- Bladwijzers
- Lagen in Bing-kaarten
- Aangepaste lettertypen

U krijgt een foutbericht als u een bestand met een niet-ondersteunde functie anders dan sorteren met in- en uitschakelen, in de Power BI-service wilt uploaden.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Welke gegevensbronnen worden op dit moment voor gepagineerde rapporten ondersteund?

We bieden ondersteuning voor de volgende gegevensbron: 

- Power BI Premium Datasets
- Azure Analysis Services (via eenmalige aanmelding (SSO))
- Azure SQL Database
- SQL Server*
- SQL Server Analysis Services (SSAS) in tabelvorm (DAX) en multidimensionale modellen van (MDX) * 
- Oracle * 
- Teradata* 

* de on-premises Gateway vereist.

Bij het openen van SSAS via de gateway, heeft de gebruiker wiens referenties zijn opgeslagen, verhoogde machtigingen in SSAS nodig om via de gateway te werken.

### <a name="what-authentication-methods-do-you-support"></a>Welke verificatiemethoden worden ondersteund?

Eenmalige aanmelding bieden we ondersteuning voor Azure Analysis Services- en Power BI Premium-gegevensbronnen.  Voor alle andere gegevensbronnen moet u momenteel voor het opslaan van een gebruikersnaam en wachtwoord met de gegevensbron in de portal of de gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kan ik een Power BI-gegevensset als een gegevensbron gebruiken voor mijn gepagineerde rapport?

Ja, we nu ondersteuning voor Power BI Premium-gegevenssets als gegevensbronnen voor gepagineerde rapporten.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kan ik opgeslagen procedures via de gateway gebruiken?

U kunt via de gateway een opgeslagen procedure gebruiken, maar in sommige scenario's kunnen er problemen ontstaan, bijvoorbeeld als een opgeslagen procedure beschikt over parameters.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Welke exportindelingen zijn voor mijn rapport in de Power BI-service beschikbaar?

U kunt exporteren naar Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML en MHTML.

### <a name="can-i-print-paginated-reports"></a>Kan ik gepagineerde rapporten afdrukken?

Ja, afdrukken is beschikbaar voor gepagineerde rapporten, met inbegrip van een nieuwe en verbeterde afdrukken preview-ervaring. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>Zijn er al e-mailabonnementen beschikbaar voor gepagineerde rapporten?

Nee, e-mailabonnementen worden echter binnenkort beschikbaar.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Welke functies in SSRS worden ondersteund in de Power BI-service?

Het staat op de planning om functiepariteit te bieden voor de meeste scenario's, maar bij bepaalde kenmerken van SSRS en Power BI is het mogelijk niet logisch om de situatie aan bestaande SSRS-patronen aan te passen.  De verschillende machtigingsmodellen in Power BI kunnen bijvoorbeeld niet worden toegewezen aan SSRS.  Beslissingen over deze zaken worden genomen op basis van feedback van klanten en partners.

### <a name="can-i-run-custom-code-in-my-report"></a>Kan ik aangepaste code in mijn rapport uitvoeren?

Ja, de mogelijkheid code in uw rapporten uit te voeren, net zoals in SSRS, wordt ondersteund.

### <a name="does-this-mean-ssrs-is-going-away"></a>Betekent dit dat SSRS verdwijnt?

Zeker niet.  Deze nieuwe aanbieding biedt klanten een optie in de cloud voor hun gepagineerde rapporten.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kan ik Power BI Embedded gebruiken voor het insluiten van gepagineerde rapporten in een app die ik zelf host?

Het is de bedoeling dit scenario te ondersteunen met de bestaande Power BI-API's, maar er is nog keen tijdsbestek waarbinnen dit scenario beschikbaar zal zijn.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kan ik vanaf een Power BI-rapport inzoomen op een gepagineerd rapport?

Dat kan nog niet, maar de ondersteuning van dit scenario staat gepland.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kan ik de inhoud van mijn gepagineerde rapport delen via een Power BI-app?

Ja, gepagineerde rapporten om te worden geïmplementeerd met apps uit werkruimten zowel v1 als v2 worden ondersteund. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Werken andere rapportfuncties in Power BI, zoals het vastmaken aan rapporttegel aan dashboards, met gepagineerde rapporten?

De bedoeling is dat de rapporten dezelfde belangrijke scenario's in de service zoveel mogelijk ondersteunen.  Hoewel het hulpprogramma om de rapporten te ontwerpen verschilt, is het vanuit het standpunt van de gebruiker in het ideale geval gewoon een ander rapport in de lijst in de portal. Voor de gebruikers is het niet van belang hoe het is gemaakt; zij kunnen gewoon doen wat ze moeten doen.  Een goed voorbeeld van deze functiepariteit is de geplande ondersteuning via opmerkingen. Hoewel de functie zelf iets anders werkt voor elk rapporttype, kunt u opmerkingen voor beide gebruiken.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>Staat er een migratieprogramma gepland, zodat klanten van SSRS hun bestaande rapporten en assets naar Power BI kunnen verplaatsen?

Momenteel wordt onderzocht welke inhoud automatisch naar Power BI kan worden verplaatst. Deze functionaliteit wordt pas na GA beschikbaar.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>Zal het ooit mogelijk zijn zowel gepagineerde rapporten als Power BI-rapporten in één bewerkingsprogramma te maken?

Mogelijk.  Er wordt gezocht naar manieren waarop dit scenario kan worden waargemaakt. Er wordt ook gekeken naar manieren om de bewerkingsprogramma's gezamenlijk te distribueren als één BI-suite of als afzonderlijke downloads/huisstijl.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Is er een besturingselement voor het weergeven van gepagineerde rapporten in de Power BI-service?

Nee, er is momenteel geen besturingselement voor het weergeven van gepagineerde rapporten.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kan ik naar gepagineerde rapporten zoeken vanaf de nieuwe startpagina in de Power BI-service?

Nee, u kunt momenteel niet vanaf de startpagina naar uw gepagineerde rapporten zoeken.  U kunt ze echter wel zien in de andere onderdelen van de nieuwe startpagina.

## <a name="next-steps"></a>Volgende stappen

- [Power BI Report Builder installeren vanuit het Microsoft Downloadcentrum](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Zelfstudie: een gepagineerd rapport maken](paginated-reports-quickstart-aw.md)
