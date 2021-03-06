---
title: Ondersteuning van Multi-Geo voor Power BI Premium
description: Lees hoe u inhoud kunt implementeren naar datacenters in andere regio's dan de basisregio van de Power BI-tenant.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 01/20/2021
LocalizationGroup: Premium
ms.openlocfilehash: f68c01e503400b83fe3e0488fdc49e15f55d7067
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687046"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Multi-Geo-ondersteuning voor Power BI Premium configureren

Ondersteuning voor meerdere geografische gebieden is een functie van Power BI Premium waarmee multinationale klanten kunnen inspelen op regionale en branchespecifieke vereisten of vereisten ten aanzien van de opslaglocatie van organisatiegegevens. Als een klant van Power BI Premium kunt u inhoud implementeren naar datacenters in andere regio's dan de basisregio van de Power BI-tenant. Een geografisch gebied kan meer dan één regio omvatten. De Verenigde Staten is bijvoorbeeld een geografische gebied, terwijl VS - west-centraal en VS - zuid-centraal regio's zijn in de Verenigde Staten. U kunt ervoor kiezen om inhoud te implementeren op een van de volgende geographs (geografische gebieden) die zijn gedefinieerd in de [regio van Azure](https://azure.microsoft.com/global-infrastructure/geographies/).

Soevereine Clouds bieden ondersteuning voor meerdere geo over regio's in die Cloud.

> [!NOTE]
> China-noord biedt momenteel geen ondersteuning voor multi geo voor Premium-Gen2 capaciteit.

Multi-Geo is nu ook beschikbaar in Power BI Embedded. Lees meer op [Ondersteuning voor Multi-Geo in Power BI Embedded](../developer/embedded/embedded-multi-geo.md).

> [!NOTE]
> Power BI Premium heeft onlangs een nieuwe versie van Premium uitgebracht, genaamd **Premium Gen2**, die momenteel beschikbaar is als preview. Premium Gen2 vereenvoudigt het beheer van Premium-capaciteiten en vermindert de overhead voor beheer. Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie.

## <a name="enable-and-configure"></a>Inschakelen en configureren

Voor een nieuwe capaciteit kunt u de ondersteuning voor meerdere geografische gebieden inschakelen door in de vervolgkeuzelijst een andere regio te selecteren dan de standaardregio.  Voor elke beschikbare capaciteit wordt aangegeven in welke regio zich deze momenteel bevindt, zoals **VS - west-centraal**.

![Capaciteitsgrootte: een regio selecteren. Power BI en meerdere geografische gebieden](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

Nadat u een capaciteit hebt gemaakt, blijft deze in die regio aanwezig. Voor alle gemaakte werkruimten geldt dat inhoud voor die ruimten wordt opgeslagen in die regio. U kunt werkruimten van de ene naar de andere regio migreren via de vervolgkeuzelijst in het scherm met werkruimte instellingen.

![Werkruimte bewerken: Een beschikbare capaciteit kiezen. Power BI en meerdere geografische gebieden](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

U ziet dit bericht om de wijziging te bevestigen.

![Bevestiging van wijzigen van toegewezen werkruimte](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Het is op dit moment niet nodig om de gatewayreferenties opnieuw in te stellen tijdens een migratie.  Nadat deze zijn opgeslagen in de regio van de Premium-capaciteit, moet u ze tijdens de migratie opnieuw instellen.

Tijdens de migratie kunnen bepaalde bewerkingen mislukken, zoals het publiceren van nieuwe gegevenssets of een geplande gegevensvernieuwing.  

De volgende items worden opgeslagen in de Premium-regio als ondersteuning voor meerdere geografische gebieden is ingeschakeld:

- Modellen (ABF-bestanden) voor importeren en DirectQuery-gegevenssets
- Query-cache
- R-afbeeldingen

Deze items blijven opgeslagen in de basisregio van de tenant:

- Push-gegevenssets
- Excel-werkmappen
- Metagegevens van dashboards/rapporten, zoals namen van tegels en tegelquery's
- Servicebussen voor gatewayquery's of geplande vernieuwingstaken
- Machtigingen
- Referenties van gegevenssets



## <a name="view-capacity-regions"></a>Capaciteitsregio's weergeven

In de beheerportal kunt u alle capaciteiten voor uw Power BI-tenant bekijken, evenals de regio's waar ze zich momenteel in bevinden.

![Premium-capaciteiten bekijken](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Regio wijzigen voor bestaande inhoud

Als u de regio voor bestaande inhoud moet wijzigen, hebt u twee mogelijkheden.

- Maak een tweede capaciteit en verplaats werkruimten. Gratis gebruikers merken niets van uitval, op voorwaarde dat de tenant over reserve-v-cores beschikt.
- Als het maken van een tweede capaciteit geen optie is, kunt u de inhoud tijdelijk vanuit Premium terug verplaatsen naar een gedeelde capaciteit. U hebt dan geen extra v-cores nodig, maar gratis gebruikers krijgen wel te maken met wat uitvaltijd.

## <a name="move-content-out-of-multi-geo"></a>Inhoud niet meer onderbrengen in meerdere geografische gebieden  

U kunt er op twee manieren voor zorgen dat werkruimten niet meer worden opgeslagen in Multi-Geo-capaciteit:

- Verwijder de huidige capaciteit waarin de werkruimte zich bevindt.  Hierdoor wordt de werkruimte terug verplaatst naar gedeelde capaciteit in de basisregio.
- Migreer afzonderlijke werkruimten terug naar Premium-capaciteit in de basistenant.

Gegevenssets met een grote opslagindeling moeten niet worden verplaatst uit de regio waarin ze zijn gemaakt. In rapporten op basis van een gegevensset met grote indeling kan de gegevensset niet worden geladen. De fout *Kan het model niet laden* wordt geretourneerd. Verplaats de gegevensset met een grote opslagindeling weer naar de oorspronkelijke regio om deze gegevensset weer beschikbaar te maken.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

- Controleer of alle verplaatsingen tussen regio's voldoen aan alle nalevingsvereisten van uw bedrijf en de overheid voordat u de gegevensoverdracht daadwerkelijk start.
- Een in de cache opgeslagen query in een verafgelegen regio blijft in die regio wanneer de query niet wordt gebruikt. Andere gegevens die onderweg zijn kunnen echter heen en weer worden verplaatst tussen meerdere geografische gebieden.
- Bij het verplaatsen van gegevens van de ene naar de andere regio in een omgeving met ondersteuning voor meerdere geografische gebieden, kunnen de brongegevens gedurende maximaal 30 dagen aanwezig blijven in de regio van waaruit de gegevens zijn verplaatst. Gedurende die periode hebben eindgebruikers geen toegang tot de gegevens. De gegevens worden gedurende deze periode van 30 dagen verwijderd uit deze regio en vernietigd.
- Verkeer als gevolg van queryteksten en queryresultaten voor geïmporteerde gegevensmodellen wordt niet via de thuisregio verzonden. De metagegevens van het rapport zijn nog steeds afkomstig uit de externe regio en bepaalde DNS-routeringsstatussen kunnen verkeer uit de regio halen. 
- De functie [gegevensstromen](../transform-model/dataflows/dataflows-introduction-self-service.md) wordt momenteel niet ondersteund in Multi-Geo.
- Wanneer gegevenssets met een grote opslagindeling worden verplaatst uit de regio waarin ze zijn gemaakt, kan de gegevensset niet in rapporten worden geladen. Verplaats de gegevensset met een grote opslagindeling terug naar de oorspronkelijke regio om deze set beschikbaar te maken. 

## <a name="next-steps"></a>Volgende stappen

- [Wat is Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo voor capaciteiten van Power BI Embedded](../developer/embedded/embedded-multi-geo.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

Power BI heeft Power BI Premium Gen2 geïntroduceerd als preview-aanbieding, waardoor de Power BI Premium-ervaring als volgt wordt aangepast met verbeteringen:
* Prestaties
* Licenties per gebruiker
* Grotere schaal
* Verbeterde metrische gegevens
* Automatisch schalen
* Minder beheeroverhead

Zie [Power BI Premium Generation 2 (preview-versie)](service-premium-what-is.md#power-bi-premium-generation-2-preview) voor meer informatie over Power BI Premium Gen2.
