---
title: 'Gepagineerde rapporten in Power BI: Veelgestelde vragen'
description: In dit artikel vindt u antwoorden op veelgestelde vragen over gepagineerde rapporten. Deze rapporten bevatten een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer die is geoptimaliseerd voor afdrukken of het genereren van PDF's.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/09/2021
ms.openlocfilehash: d8460fe1a3eb199848f47181837225f1e540bb08
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/10/2021
ms.locfileid: "100013631"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Gepagineerde rapporten in Power BI: Veelgestelde vragen 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

In dit artikel vindt u antwoorden op veelgestelde vragen over gepagineerde rapporten. Deze rapporten bevatten een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer die is geoptimaliseerd voor afdrukken of het genereren van PDF's. Ze worden 'gepagineerd' genoemd, omdat ze zo zijn opgemaakt dat ze op meerdere pagina's passen. Gepagineerde rapporten zijn gebaseerd op de RDL-rapporttechnologie in SQL Server Reporting Services. 

In dit artikel vindt u antwoorden op veelvoorkomende vragen over gepagineerde rapporten in Power BI Premium, en over Report Builder, het zelfstandige hulpprogramma voor het ontwerpen van gepagineerde rapporten. U hebt een Power BI Pro-licentie nodig om een rapport te publiceren in de service. U kunt gepagineerde rapporten publiceren en delen in Mijn werkruimte of in de werkruimten, zolang de werkruimte zich in een Power BI Premium-capaciteit bevindt. 

## <a name="administration"></a>Beheer

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Hoe groot moet de Premium-capaciteit zijn voor gepagineerde rapporten?

De werkbelasting van gepagineerde rapporten is beschikbaar op P1 – P3 SKU's.  U kunt deze ook gebruiken voor test-/ontwikkelscenario's met A4 – A6-SKU's.

> [!NOTE]
> Power BI onlangs een nieuwe release van Premium uitgebracht, de zogeheten **Premium Gen2**, die momenteel als preview-versie beschikbaar is. In **Premium Gen2** is de werk belasting gepagineerde rapporten beschikbaar op P1-P3 Sku's en a1-A6 sku's. 
>
>Premium Gen2 vereenvoudigt het beheer van Premium-capaciteiten en vermindert de beheer overhead. Zie [Power BI Premium Generation 2 (preview-versie)](../admin/service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie.
>
>Raadpleeg [Power bi embedded Generation 2](../developer/embedded/power-bi-embedded-generation-2.md)om de Power bi embedded verbeteringen van Gen2 te bekijken.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Wat is de maximum drempelwaarde van het geheugen dat ik voor gepagineerde rapporten in mijn capaciteit kan reserveren?

U kunt maximaal 100% van het geheugen voor deze workload verbruiken.

### <a name="how-does-user-access-work-for-paginated-reports"></a>Hoe werkt gebruikerstoegang voor gepagineerde rapporten?

Gebruikerstoegang voor gepagineerde rapporten is hetzelfde als gebruikerstoegang voor alle andere inhoud in de Power BI-service 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Hoe schakel ik de werkbelasting voor mijn gepagineerde rapporten in of uit?

De capaciteitsbeheerder kan de werkbelasting voor de gepagineerde rapporten in- of uitschakelen op de portalpagina van de capaciteitsbeheerder.  De werkbelasting is standaard ingeschakeld voor alle nieuwe mogelijkheden die u maakt, maar deze verbruikt geen geheugen tot u het eerste gepagineerde rapport hebt geüpload.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Hoe kan ik het gebruik van gepagineerd rapporten in mijn tenant in de gaten houden?

Het gebruik van dit rapporttype wordt in de auditlogboeken onder de volgende gebeurtenissen uitgebreid vermeld:

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

U kunt gepagineerde rapporten zonder een Pro-licentie uploaden naar Mijn werkruimte, op voorwaarde dat uw werkruimte deel uitmaakt van een Premium-capaciteit.  Voor andere werkruimten hebt u een Pro-licentie nodig voor het maken en publiceren van inhoud. We raden u aan om Power BI Report Builder te downloaden en te gebruiken, zelfs zonder de Pro-licentie, maar u kunt de gepagineerde rapporten die u ermee maakt dan niet publiceren. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>Wat gebeurt er als ik een gepagineerd rapport in een werkruimte heb en de werkbelasting van het gepagineerde rapport wordt uitgeschakeld?

U ontvangt een foutbericht en u kunt uw rapport pas weergeven als de werkbelasting opnieuw wordt ingeschakeld. U kunt het rapport wel uit de werkruimte verwijderen.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>Wat is de standaardgeheugenruimte in elk van de Premium SKU's die ondersteuning bieden voor gepagineerde rapporten?

Standaardgeheugenruimte in elke Premium-SKU voor gepagineerde rapporten:

- **P1/A4**: standaard 20%; minimaal 10%
- **P2/A5**: standaard 20%; minimaal 5%
- **P3/A6**: standaard 20%; minimaal 2,5%

Power BI-beheerders kunnen het maximale standaardgeheugenpercentage wijzigen in de beheerportal. Zie het workloadgedeelte **Gepagineerde rapporten** onder **Power BI Premium** op het tabblad **Capaciteitsinstellingen**.

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="Tabblad Capaciteitsinstellingen voor gepagineerde rapporten":::

> [!NOTE]
> **Premium-Gen2**, die momenteel als preview-versie beschikbaar zijn, hoeven de geheugen instellingen niet te wijzigen. Het onderliggende systeem beheert automatisch het geheugen in Premium Gen2. De werk belasting voor gepagineerde rapporten is beschikbaar op P1-P3 Sku's en a1-A6 Sku's in **Premium Gen2**.

## <a name="general"></a>Algemeen

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Wanneer moet ik een gepagineerd rapport gebruiken in plaats van een Power BI-rapport?

Gepagineerde rapporten zijn het geschiktst voor scenario's waarvoor een uitgebreid opgemaakte, tot op de pixel nauwkeurige uitvoer is vereist, die is geoptimaliseerd voor afdrukken of het genereren van PDF's.  Een verlies- en winstrekening is een goed voorbeeld van het type rapport dat u waarschijnlijk als een gepagineerd rapport wilt opmaken.  

Power BI-rapporten zijn geoptimaliseerd voor verkenning en interactiviteit.  Een Power BI-rapport is ideaal voor een verkooprapport waarin verschillende verkopers de gegevens in hetzelfde rapport voor hun specifieke regio/branche/klant willen onderbrengen en willen bekijken hoe de cijfers veranderen.

Zie [Wanneer u gepagineerde rapporten gebruikt in Power BI](../guidance/report-paginated-or-power-bi.md) voor meer informatie.

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>In de documentatie staat dat Power BI Report Builder het geadviseerde bewerkingsprogramma is. Kan ik gepagineerde rapporten maken in SQL Server Data Tools voor Power BI?

Ja, maar met de Power BI-service kunt u slechts één item per keer uploaden, dus veel scenario's die ontwerpers gebruiken met SQL Server Data Tools (SSDT) worden nog niet ondersteund. Zie de volledige [lijst met ondersteunde functies](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) verderop in deze Veelgestelde vragen.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Welke versie(s) van Report Builder worden ondersteund?

We hebben Power BI Report Builder uitgebracht als het belangrijkste bewerkingsprogramma voor gepagineerde rapporten in de Power BI-service. Installeer [Power BI Report Builder vanuit het Microsoft Downloadcentrum](https://aka.ms/pbireportbuilder).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Hoe kan ik bestaande rapporten die in SQL Server Reporting Services zijn opgeslagen, naar Power BI verplaatsen?

Met een project op GitHub wordt nu het migreren van inhoud van SQL Server Reporting Services naar Power BI ondersteund.  Bekijk de details en download het hulpprogramma hier: [https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Kan ik rapporten openen en rechtstreeks in de service publiceren?

Ja. We hebben de mogelijkheid toegevoegd om rapporten rechtstreeks vanuit Power BI Report Builder te openen en te publiceren.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Welke functies van gepagineerde rapporten in SSRS worden nog niet in Power BI ondersteund?

Momenteel worden de volgende items nog niet door gepagineerde rapporten ondersteund:

- Gedeelde gegevensbronnen
- Gedeelde gegevenssets
- Drillthrough en doorklikken naar andere rapporten
- Gekoppelde rapporten
- Aangepaste lettertypen

U krijgt een foutbericht als u een bestand met een niet-ondersteunde functie anders dan sorteren met in- en uitschakelen, in de Power BI-service wilt uploaden.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Welke gegevensbronnen worden op dit moment voor gepagineerde rapporten ondersteund?

Zie het artikel [Ondersteunde gegevensbronnen voor gepagineerde rapporten in Power BI](paginated-reports-data-sources.md) voor een lijst met gegevensbronnen. 

### <a name="what-authentication-methods-do-you-support"></a>Welke verificatiemethoden worden ondersteund?

We ondersteunen SSO voor Azure Analysis Services, Azure SQL Database en Power BI-gegevensbronnen.  We ondersteunen ook OAuth voor Azure SQL Database en Azure Analysis Services.  Voor andere gegevensbronnen moet u op dit moment een gebruikersnaam en een wachtwoord opslaan in de portal of gateway, samen met de gegevensbron.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Kan ik een Power BI-gegevensset als een gegevensbron gebruiken voor mijn gepagineerde rapport?

Ja, we ondersteunen Power BI-gegevenssets als gegevensbronnen voor uw gepagineerde rapporten.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Kan ik opgeslagen procedures via de gateway gebruiken?

Ja, opgeslagen procedures via de gateway worden ondersteund voor SQL Server-gegevensbronnen, waaronder ook de gegevensbronnen die parameters gebruiken.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Welke exportindelingen zijn voor mijn rapport in de Power BI-service beschikbaar?

U kunt exporteren naar Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, CSV, XML en MHTML.

### <a name="can-i-print-paginated-reports"></a>Kan ik gepagineerde rapporten afdrukken?

Ja, afdrukken is beschikbaar voor gepagineerde rapporten. Gebruikers hebben toegang tot een nieuwe en verbeterde functie voor afdrukvoorbeelden. 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>Zijn er e-mailabonnementen beschikbaar voor gepagineerde rapporten?

Ja, e-mailabonnementen worden volledig ondersteund voor gepagineerde rapporten en omvatten ondersteuning voor zes verschillende bestandsindelingen en parameterwaarden.

### <a name="can-i-run-custom-code-in-my-report"></a>Kan ik aangepaste code in mijn rapport uitvoeren?

Ja, de mogelijkheid code in uw rapporten uit te voeren, net zoals in SSRS, wordt ondersteund.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Kan ik Power BI Embedded gebruiken voor het insluiten van gepagineerde rapporten in een app die ik zelf host?

SaaS-insluiting, inclusief ondersteuning voor Beveiligd insluiten, is al beschikbaar. Raadpleeg de zelfstudie [Gepagineerde Power BI-rapporten insluiten in een toepassing voor uw klanten](../developer/embedded/embed-paginated-reports-customers.md) voor PaaS-insluiting.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Kan ik vanaf een Power BI-rapport inzoomen op een gepagineerd rapport?

Ja, u kunt dit doen met URL-parameters met uw gepagineerde rapporten.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Kan ik de inhoud van mijn gepagineerde rapport delen via een Power BI-app?

Ja, gepagineerde rapporten kunnen worden geïmplementeerd met apps uit werkruimten van zowel v1 als v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-report-tiles-to-dashboards-work-with-paginated-reports"></a>Werken andere rapportfuncties in Power BI, zoals het vastmaken van rapporttegels aan dashboards en werken met gepagineerde rapporten?

De bedoeling is dat de rapporten dezelfde belangrijke scenario's in de service zoveel mogelijk ondersteunen.  Hoewel het hulpprogramma om de rapporten te ontwerpen verschilt, is het vanuit het standpunt van de gebruiker in het ideale geval gewoon een ander rapport in de lijst in de portal. Voor de gebruikers is het niet van belang hoe het is gemaakt; zij kunnen gewoon doen wat ze moeten doen.  Een goed voorbeeld van deze functiepariteit is de geplande ondersteuning via opmerkingen. Hoewel de functie zelf iets anders werkt voor elk rapporttype, kunt u opmerkingen voor beide gebruiken.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Is er een besturingselement voor het weergeven van gepagineerde rapporten in de Power BI-service?

Nee, er is momenteel geen besturingselement voor het weergeven van gepagineerde rapporten.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Kan ik naar gepagineerde rapporten zoeken vanaf de nieuwe startpagina in de Power BI-service?

Ja, u kunt nu vanaf de startpagina zoeken naar gepagineerde rapporten.  U kunt ze ook zien in andere onderdelen van de nieuwe startpagina.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
Onthoud het volgende wanneer u met Datum/tijd-velden werkt in gepagineerde rapporten.

- Er zijn momenteel enkele globaliseringsbeperkingen met betrekking tot Datum/tijd-parameters. Alle Datum/tijd-parameters in de Power BI-service worden opgehaald in Amerikaanse indeling (MM/DD/JJJJ), ongeacht hoe u de Datum/tijd in Power BI Report Builder ontwerpt.

Wanneer u gepagineerde rapporten bekijkt in de Power BI-service, kan er een time-out optreden in sessies. De gebruiker ziet dan de volgende melding:

:::image type="content" source="media/paginated-reports-faq/expired-session-notification.png" alt-text="Melding over verlopen sessie met gepagineerde rapporten":::

- De sessie verloopt na 60 minuten inactiviteit of eerder als het apparaat is vergrendeld of niet actief is, of wanneer het rapport niet wordt weergegeven op het actieve tabblad van de browser.

## <a name="next-steps"></a>Volgende stappen

- [Power BI Report Builder installeren vanuit het Microsoft Downloadcentrum](https://aka.ms/pbireportbuilder)
- [Zelfstudie: een gepagineerd rapport maken](paginated-reports-quickstart-aw.md)
