---
title: Rapporten scheiden van modellen in Power BI Desktop
description: Richtlijnen voor het scheiden van rapporten van modellen in Power BI Desktop.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 04/11/2020
ms.openlocfilehash: 20e674765d2a908ff1952b0f316d125d0e3c5bd3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088299"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Rapporten scheiden van modellen in Power BI Desktop

Bij het maken van een nieuwe Power BI Desktop-oplossing is het ophalen van gegevens een van de eerste taken die u moet uitvoeren. Het ophalen van gegevens kan leiden tot twee verschillende resultaten. Het volgende is mogelijk:

- Maak een [liveverbinding](../connect-data/desktop-report-lifecycle-datasets.md) met een reeds gepubliceerd model. Dit kan een Power BI-gegevensset of een extern gehost Analysis Services-model zijn.
- Begin met het ontwikkelen van een nieuw model dat een Import-, DirectQuery- of Composite-model kan zijn.

Dit artikel heeft betrekking op het tweede scenario. Het bevat richtlijnen over of een rapport en model moeten worden gecombineerd in één Power BI Desktop-bestand.

## <a name="single-file-solution"></a>Oplossing met één bestand

Een _oplossing met één bestand_ werkt goed als er altijd sprake is van slechts één rapport op basis van het model. In dit geval is het waarschijnlijk dat zowel het model als het rapport van één persoon zijn. We definiëren dit als een _Personal BI_-oplossing, hoewel het rapport wel met anderen kan worden gedeeld. Dergelijke oplossingen kunnen rapporten voor het bereik van een rol of eenmalige evaluaties van een bedrijfsuitdaging vertegenwoordigen (vaak aangeduid als _ad-hoc_ rapporten).

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Eén bestand bevat een model en rapport die zijn ontwikkeld door dezelfde persoon." border="true":::

## <a name="separate-report-files"></a>Afzonderlijke rapportbestanden

Het is zinvol om de ontwikkeling van modellen en rapporten te scheiden in afzonderlijke Power BI Desktop-bestanden in de volgende gevallen:

- Gegevensmodelleurs en rapportauteurs zijn verschillende personen.
- Het is duidelijk dat een model de bron is voor meerdere rapporten, nu of in de toekomst.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Er zijn drie PBIX-bestanden. Het eerste bevat alleen een model. De andere twee bevatten alleen rapporten en ze maken live verbinding met het model dat wordt gehost in de Power BI-service. De rapporten worden ontwikkeld door verschillende personen." border="true":::

Gegevensmodelleurs kunnen de ervaring voor het ontwerpen van Power BI Desktop-rapporten nog steeds gebruiken om hun modelontwerpen te testen en te valideren. Maar ze moeten het rapport direct na publicatie naar de Power BI-service uit de werkruimte verwijderen. Bovendien moeten ze niet vergeten het rapport te verwijderen steeds wanneer ze de gegevensset opnieuw publiceren en overschrijven.

### <a name="preserve-the-model-interface"></a>De modelinterface behouden

Soms zijn modelwijzigingen onvermijdelijk. Gegevensmodelleurs moeten ervoor zorgen dat ze de modelinterface niet zo wijzigen dat er fouten ontstaan. Als dat wel gebeurt, is het mogelijk dat gerelateerde rapportvisuals of dashboardtegels tot fouten leiden. Verbroken visuals worden weergegeven als fouten en kunnen leiden tot frustraties bij rapportontwerpers en consumenten. En erger: ze kunnen het vertrouwen in de gegevens beschadigen.

Daarom moet u modelwijzigingen zorgvuldig beheren. Vermijd indien mogelijk de volgende wijzigingen:

- De naam van tabellen, kolommen, hiërarchieën, hiërarchieniveaus of metingen wijzigen.
- Kolomgegevenstypen wijzigen.
- Metingexpressies wijzigen zodat ze een ander gegevenstype retourneren.
- Metingen naar een andere starttabel verplaatsen. Door het verplaatsen van een meting kunnen metingen voor een rapport die volledig zijn gekwalificeerd met de naam van hun starttabel, tot fouten leiden. Het is niet raadzaam om DAX-expressies te schrijven met volledig gekwalificeerde metingnamen. Zie voor meer informatie [DAX: Verwijzingen naar kolommen en metingen](dax-column-measure-references.md).

Het toevoegen van nieuwe tabellen, kolommen, hiërarchieën, hiërarchieniveaus of metingen is veilig, met één uitzondering: Het is mogelijk dat een nieuwe metingnaam conflicteert met een metingnaam van het rapport. Om conflicten te voorkomen, raden wij rapportauteurs aan een naamgevingsconventie te gebruiken bij het definiëren van metingen in hun rapporten. Ze kunnen de metingnamen voor rapporten vooraf laten gaan door een onderstrepingsteken of een of meer andere tekens.

Als u wijzigingen aan uw modellen moet aanbrengen die tot fouten leiden, wordt het volgende aanbevolen:

- [Bekijk gerelateerde inhoud voor de gegevensset](../consumer/end-user-related.md) in de Power BI-service.
- Verken de weergave [Gegevensherkomst](../collaborate-share/service-data-lineage.md) in de Power BI-service.

Met beide opties kunt u snel gerelateerde rapporten en dashboards identificeren. De weergave Gegevensherkomst is waarschijnlijk de beste keuze, omdat hierin gemakkelijk de contactpersoon voor elk gerelateerd artefact te zien is. Dit is in feite een hyperlink waarmee een e-mailbericht wordt geopend dat is geadresseerd aan de contactpersoon.

Het wordt aanbevolen contact op te nemen met de eigenaar van elk gerelateerd artefact om hem/haar op de hoogte te stellen van de geplande wijzigingen die fouten veroorzaken. Op deze manier is deze erop voorbereid dat rapporten moeten worden hersteld en opnieuw moeten worden gepubliceerd, waardoor downtime en frustraties tot een minimum worden beperkt.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Verbinding maken met gegevenssets in de Power BI-service vanuit Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
- [Gerelateerde inhoud in de Power BI-service bekijken](../consumer/end-user-related.md)
- [Gegevensherkomst](../collaborate-share/service-data-lineage.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
