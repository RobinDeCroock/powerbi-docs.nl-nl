---
title: Aangepaste organisatievisuals in Power BI
description: Gebruik, beheer en maak aangepaste visuals voor organisaties in Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 157b20107a5be106ac97e0cb927b1e496e1ba115
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61421880"
---
# <a name="organizational-custom-visuals-in-power-bi"></a>Aangepaste organisatievisuals in Power BI

U kunt aangepaste visuals gebruiken in Power BI om een uniek soort visual te maken die aan uw behoeften is aangepast. Aangepaste visuals worden door ontwikkelaars gemaakt wanneer het grote aantal visuals in Power BI niet helemaal aan de behoefte voldoet.

In sommige organisaties zijn aangepaste visuals nog belangrijker. Ze kunnen nodig zijn om bepaalde gegevens of inzichten die uniek zijn voor de organisatie naar voren te brengen, hebben misschien speciale vereisten voor gegevens of kunnen unieke methoden van het bedrijf onderstrepen. Zulke organisaties moeten aangepaste visuals ontwikkelen, die in de hele organisatie delen en ervoor zorgen dat ze goed worden onderhouden. Met aangepaste visuals van Power BI kunnen organisaties precies dat doen.

De volgende afbeelding toont via welk proces aangepaste visuals voor organisaties in Power BI vanaf de beheerder, via ontwikkeling en onderhoud, ten slotte allemaal bij de gegevensanalist aankomen.

![Afbeelding van aangepaste visual](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Organisatievisuals worden door de Power BI-beheerder geïmplementeerd en beheerd vanuit de beheerportal. Zodra de visuals in de opslagplaats van de organisatie zijn geïmplementeerd, kunnen gebruikers in de organisatie de visuals eenvoudig vinden en de aangepaste visuals voor organisaties direct vanuit Power BI Desktop in hun rapporten importeren.

Raadpleeg het volgende artikel voor meer informatie over het gebruik van aangepaste organisatievisuals in rapporten die u hebt gemaakt: [Meer informatie over organisatievisuals importeren in uw rapporten](power-bi-custom-visuals.md).

## <a name="administer-organizational-custom-visuals"></a>Aangepaste visuals van organisaties beheren

Raadpleeg het volgende artikel voor meer informatie over het beheren en implementeren van aangepaste organisatievisuals: [Meer informatie over de implementatie en het beheer van organisatievisuals](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Een aangepaste visual kan code bevatten met beveiligings- of privacyrisico's. Ga na of u de auteur en de bron van een aangepaste visual vertrouwt voordat u deze implementeert in de opslagplaats van de organisatie.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

Er zijn enkele overwegingen en beperkingen waarmee u rekening moet houden.

Beheerder:

* Verouderde aangepaste visuals (zoals aangepaste visuals die niet op de nieuwe API-versies zijn gebouwd) worden niet ondersteund

* Als een aangepaste visual uit de opslagplaats wordt verwijderd, zullen de bestanden die de verwijderde visual gebruiken, de rendering stoppen. De verwijderingsbewerking vanuit de opslagplaats is niet omkeerbaar. Als u een aangepast visueel element tijdelijk moet uitschakelen, gebruikt u de functie ‘Uitschakelen’.

Eindgebruiker:

* Aangepaste visuals van organisaties zijn persoonlijke visuals uit de organisatieopslagplaats. Evenmin als persoonlijke visuals kunnen ze niet worden [geëxporteerd naar PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) of worden weergegeven in ontvangen e-mails als een gebruiker zich [abonneert op rapportpagina's](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Alleen [gecertificeerde aangepaste visuals](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) die rechtstreeks vanuit de marketplace worden geïmporteerd, ondersteunen deze functies.

* De Visio-visual, PowerApps-visual, Map box-visual en GlobeMap-visual uit de AppSource-marketplace worden niet weergegeven als ze worden geïmplementeerd via de opslagplaats van de organisatie.

## <a name="troubleshoot"></a>Problemen oplossen

Ga naar [Problemen met aangepaste visuals voor Power BI oplossen](power-bi-custom-visuals-troubleshoot.md) voor informatie over het oplossen van problemen.

## <a name="faq"></a>Veelgestelde vragen

Voor meer informatie en antwoorden op vragen gaat u naar [Veelgestelde vragen over aangepaste visuals voor Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/).
