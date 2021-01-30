---
title: Implementatie voor migratie naar Power BI plannen
description: Begeleiding bij het plannen van de implementatie tijdens migratie naar Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f6b781d6b3f87587e7734d5f842a013fd6fb5c19
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086689"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>Implementatie voor migratie naar Power BI plannen

In dit artikel wordt **fase 2** beschreven die betrekking heeft op het plannen van de migratie voor één Power BI-oplossing.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Afbeelding van de fasen van een Power BI-migratie. Fase 2 wordt in dit artikel uitgelicht.":::

> [!NOTE]
> Zie [Overzicht van Power BI-migratie](powerbi-migration-overview.md) voor een volledige uitleg van de bovenstaande grafiek.

De focus van fase 2 ligt op het definiëren van de manier waarop de vereisten die zijn gedefinieerd in fase 1, worden gebruikt voor het migreren van een oplossing naar Power BI.

De uitvoer van fase 2 omvat zoveel mogelijk specifieke beslissingen om het implementatieproces te begeleiden.

Besluitvorming van deze aard is een herhalend en niet-lineair proces. Er heeft al planning plaatsgevonden in de [stappen voorafgaand aan de migratie](powerbi-migration-pre-migration-steps.md). Ervaringen die voortkomen uit het testen van een werkbaar concept (beschreven in [fase 3](powerbi-migration-proof-of-concept.md)) kunnen worden ingezet voor de implementatieplanning. Zelfs tijdens het maken van de oplossing (beschreven in [fase 4](powerbi-migration-create-validate-content.md)), is het mogelijk dat er aanvullende informatie aan het licht komt die invloed heeft op beslissingen ten aanzien van de implementatie.

> [!IMPORTANT]
> Fasen 1-5 vertegenwoordigen activiteiten die betrekking hebben op één specifieke oplossing. Er zijn beslissingen en activiteiten op het niveau van de organisatie/tenant die van invloed zijn op het proces op het niveau van de oplossing. Enkele van deze planningsactiviteiten op een hoger niveau worden besproken in het artikel [Overzicht van Power BI-migratie](powerbi-migration-overview.md). Raadpleeg indien van toepassing de beslissingen op organisatieniveau voor efficiëntie en consistentie.

> [!TIP]
> De onderwerpen die in dit artikel worden besproken, zijn ook van toepassing op een standaard Power BI-implementatieproject.

## <a name="choose-power-bi-product"></a>Power BI-product kiezen

Een van de eerste beslissingen is het kiezen van het Power BI-product. Het is een beslissing tussen de [Power BI-service](../fundamentals/power-bi-service-overview.md) en de [Power BI Report Server](../report-server/get-started.md). Zodra de inhoud is gepubliceerd, komen er veel extra opties beschikbaar, zoals insluiten, mobiele levering en e-mailabonnementen.

Zie **sectie 3** van het [Technisch document over het plannen van een Power BI Enterprise-implementatie](https://aka.ms/PBIEnterpriseDeploymentWP) voor meer informatie over overwegingen met betrekking tot architectuur.

> [!CAUTION]
> Als u geneigd bent om te vertrouwen op het gebruik van Power BI Desktop-bestanden die zijn opgeslagen in een bestandssysteem, moet u er rekening mee houden dat dit geen optimale aanpak is. Het gebruik van de Power BI-service (of Power BI Report Server) heeft aanzienlijke voordelen als het gaat om beveiliging, inhoudsdistributie en samenwerking. De mogelijkheid om activiteiten te beoordelen en controleren is ook ingeschakeld door de Power BI-service.

## <a name="decide-on-workspace-management-approach"></a>Bepalen hoe werkruimtebeheer moet worden benaderd

[Werkruimten](../collaborate-share/service-new-workspaces.md) zijn een kernconcept van de Power BI-service, waardoor het werkruimtebeheer een belangrijk onderdeel is van de planning. Te stellen vragen:

- Is er een nieuwe werkruimte nodig voor deze nieuwe oplossing?
- Zijn er afzonderlijke werkruimten nodig om ontwikkel-, test- en productiemogelijkheden te kunnen bieden?
- Worden er afzonderlijke werkruimten gebruikt voor gegevens en rapporten of is één werkruimte voldoende? Afzonderlijke werkruimten hebben talrijke voordelen, met name voor het beveiligen van gegevenssets. Indien nodig, kunnen deze afzonderlijk worden beheerd door de gebruikers die rapporten publiceren.
- Wat zijn de beveiligingsvereisten voor de werkruimte? Het is van invloed op het plannen van [werkruimterollen](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Als een app wordt gebruikt door inhoudsgebruikers, worden [machtigingen voor de app](../collaborate-share/service-create-distribute-apps.md#publish-your-app) afzonderlijk van de werkruimte beheerd. Afzonderlijke machtigingen voor alleen-lezengebruikers van de app zorgen ervoor dat dit soort gebruikers eenvoudiger aan de beveiligingseisen voor rapporten of dashboards kunnen voldoen.
- Kunnen bestaande groepen worden gebruikt voor het beveiligen van de nieuwe inhoud? Zowel Azure Active Directory- als Microsoft 365-groepen worden ondersteund. Door gebruik te maken van groepen die zijn uitgelijnd met de bestaande processen, in plaats van toewijzingen aan individuele gebruikers, wordt het machtigingenbeheer aanzienlijk vereenvoudigd.
- Zijn er beveiligingsoverwegingen met betrekking tot externe gastgebruikers? Mogelijk moet u samenwerken met uw Azure Active Directory-beheerder en uw Power BI-beheerder om de [toegang voor gastgebruikers](../admin/service-admin-azure-ad-b2b.md) te configureren.

> [!TIP]
> Overweeg om een werkruimte te maken voor een specifieke bedrijfsactiviteit of een specifiek bedrijfsproject. Misschien bent u geneigd om werkruimten te structureren op basis van uw organisatiestructuur (zoals een werkruimte per afdeling), maar deze benadering blijkt vaak te breed te zijn.

## <a name="determine-how-content-will-be-consumed"></a>Bepalen hoe inhoud wordt gebruikt

Het is handig om te weten hoe gebruikers het liefst rapporten en dashboards bekijken. Te stellen vragen:

- Is een [Power BI-app](../consumer/end-user-apps.md) (die rapporten en dashboards uit één werkruimte bevat) de beste manier om inhoud aan consumenten te leveren? Of is directe toegang tot een werkruimte voldoende voor gebruikers die inhoud bekijken?
- Worden bepaalde rapporten en dashboards elders ingesloten, zoals [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md)of een [beveiligde portal of website](../collaborate-share/service-embed-secure.md)?
- Hebben consumenten met [mobiele apparaten](../consumer/mobile/mobile-apps-for-mobile-devices.md) toegang tot inhoud? De vereisten voor het leveren van rapporten aan kleinere apparaten zijn van invloed op enkele [beslissingen over het ontwerpen van rapporten](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Bepalen of er andere inhoud kan worden gemaakt

Er zijn enkele belangrijke beslissingen die moeten worden genomen om gebruikers toe te staan nieuwe inhoud te maken, zoals:

- Kunnen gebruikers nieuwe rapporten maken op basis van de gepubliceerde gegevensset? Deze mogelijkheid kan worden ingeschakeld door gegevensset [Samenstellingsmachtiging](../connect-data/service-datasets-build-permissions.md) aan een gebruiker toe te wijzen.
- Als consumenten een rapport willen aanpassen, kunnen ze [een kopie opslaan](../connect-data/service-datasets-copy-reports.md) en deze aan hun eisen aanpassen?

> [!CAUTION]
> Hoewel _Kopie opslaan_ een handige functie is, moet deze met de nodige voorzichtigheid worden gebruikt als het rapport bepaalde afbeeldingen of koptekst-/voettekstberichten bevat. Omdat logo's, pictogrammen en tekstberichten vaak onderhevig zijn aan eisen op het gebied van huisstijl of compliance, is het van belang om goed in de gaten te houden hoe deze worden geleverd en gedistribueerd. Als de functie _Kopie opslaan_ wordt gebruikt, maar de oorspronkelijke afbeeldingen of koptekst-/voettekstberichten niet worden gewijzigd door de nieuwe auteur, kan dit tot verwarring leiden over wie het rapport werkelijk heeft opgesteld. Het kan ook de betekenis van de huisstijl verminderen.

## <a name="evaluate-needs-for-premium-capacity"></a>Behoeften aan Premium-capaciteit evalueren

Er zijn extra mogelijkheden beschikbaar wanneer een werkruimte wordt opgeslagen op een [Premium-capaciteit](../admin/service-premium-what-is.md). Hier volgen enkele redenen waarom werkruimten op een Premium-capaciteit van voordeel kunnen zijn:

- Inhoud kan worden geopend door gebruikers die geen Power BI Pro-licentie hebben.
- Ondersteuning voor grotere gegevenssets.
- Ondersteuning voor frequentere gegevensvernieuwingen.
- Ondersteuning voor het gebruik van de volledige functieset van gegevensstromen.
- Enterprise-functies, inclusief implementatiepijplijnen en het XMLA-eindpunt.
- Ondersteuning voor gepagineerde rapporten (wanneer de werkbelasting is ingeschakeld).

## <a name="determine-data-acquisition-method"></a>Methode voor ophalen gegevens bepalen

De gegevens die voor een rapport nodig zijn, kunnen van invloed zijn op verschillende beslissingen. Te stellen vragen:

- Kan een bestaande [gedeelde Power BI-gegevensset](../connect-data/service-datasets-share.md) worden gebruikt of moet een nieuwe Power BI-gegevensset worden gemaakt die geschikt is voor deze oplossing?
- Moet een bestaande gedeelde gegevensset worden uitgebreid met nieuwe gegevens of metingen om aan extra behoeften te voldoen?
- Welke [modus voor gegevensopslag](../transform-model/desktop-storage-mode.md) is het meest geschikt? Opties zijn onder andere Import, DirectQuery, Composite en Live Connection.
- Moeten [aggregaties](../transform-model/desktop-aggregations.md) worden gebruikt om de queryprestaties te verbeteren?
- Is het maken van een [gegevensstroom](../transform-model/dataflows/dataflows-introduction-self-service.md) nuttig en kan deze fungeren als een bron voor een groot aantal gegevenssets?
- Moet een nieuwe [gatewaygegevensbron](../connect-data/service-gateway-data-sources.md) worden geregistreerd?

## <a name="decide-where-original-content-will-be-stored"></a>Bepaal waar de oorspronkelijke inhoud wordt opgeslagen

Naast het plannen van de doelbestemming voor de implementatie, is het ook belangrijk om te plannen waar de oorspronkelijke inhoud (of broninhoud) wordt opgeslagen, zoals:

- Geef een goedgekeurde locatie op voor het opslaan van de originele Power BI Desktop-bestanden (.pbix). In het ideale geval is deze locatie alleen beschikbaar voor personen die de inhoud bewerken. Het moet worden uitgelijnd met de manier waarop de beveiliging is ingesteld in de Power BI-service.
- Gebruik een locatie voor de oorspronkelijke Power BI Desktop-bestanden met versiegeschiedenis of broncodebeheer. Met versiegeschiedenis kan de auteur van de inhoud, indien nodig, een eerdere bestandsversie terugzetten. OneDrive voor bedrijven of SharePoint zijn geschikt voor dit doel.
- Geef een goedgekeurde locatie op voor het opslaan van niet-gecentraliseerde brongegevens, zoals platte bestanden of Excel-bestanden. Dit moet een pad zijn dat een van de auteurs van de gegevensset zonder fouten kan bereiken en waarvan regelmatig een back-up wordt gemaakt.
- Geef een goedgekeurde locatie op voor inhoud die is geëxporteerd uit de Power BI-service. Het doel is om ervoor te zorgen dat de beveiliging die is gedefinieerd in de Power BI-service niet per ongeluk wordt omzeild.

> [!IMPORTANT]
> Het opgeven van een beveiligde locatie voor oorspronkelijke Power BI Desktop-bestanden is vooral belangrijk als deze geïmporteerde gegevens bevatten.

## <a name="assess-the-level-of-effort"></a>Het inspanningsniveau beoordelen

Als er voldoende informatie beschikbaar is over de vereisten (die zijn beschreven in [fase 1](powerbi-migration-requirements.md)) en het planningsproces voor de oplossingsimplementatie, is het mogelijk om het inspanningsniveau te beoordelen. Er kan dan een projectplan met taken, een tijdlijn en verantwoordelijkheid worden geformuleerd.

> [!TIP]
> Arbeidskosten (salarissen) vormen doorgaans de hoogste kosten van organisaties. Hoewel het lastig kan zijn om een nauwkeurige schatting te maken, leveren productiviteitsverbeteringen een uitstekend rendement op investeringen (ROI) op.

## <a name="next-steps"></a>Volgende stappen

In het [volgende artikel van deze serie over Power BI-migratie](powerbi-migration-proof-of-concept.md) vindt u meer informatie over fase 3, die is gericht op het testen van een werkbaar concept om risico's te beperken en zo snel mogelijk in te spelen op onbekende factoren als u naar Power BI migreert.

Andere nuttige informatiebronnen zijn o.a.:

- [BI-transformatie van Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/PBIEnterpriseDeploymentWP)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)

Ervaren Power BI-partners zijn beschikbaar om uw organisatie te helpen het migratieproces te laten slagen. Als u een Power BI-partner wilt inschakelen, gaat u naar de [Power BI-partnerportal](https://powerbi.microsoft.com/partners/).