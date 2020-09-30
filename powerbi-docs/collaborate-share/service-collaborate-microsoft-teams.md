---
title: Samenwerken in Microsoft Teams met Power BI
description: Naarmate verspreide werknemers meer en meer de norm worden, vertrouwen steeds meer organisaties op Microsoft Teams om werken op afstand mogelijk te maken en werknemers op één lijn te houden.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/15/2020
ms.openlocfilehash: 6539495fbd98cdb0af302e007a8f85c44430a048
ms.sourcegitcommit: 701dd80661a63c76d37d1e4f159f90e3fc8c3160
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135793"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Samenwerken in Microsoft Teams met Power BI

Naarmate verspreide werknemers meer en meer de norm worden, vertrouwen steeds meer organisaties op Microsoft Teams om werken op afstand mogelijk te maken en werknemers op één lijn te houden. In dit artikel worden opties beschreven om interactieve Power BI-inhoud te delen en hieraan samen te werken in Microsoft Teams-kanalen en -chats. 

- Met het tabblad **Power BI** voor Microsoft Teams kunt u [interactieve rapporten insluiten in Microsoft Teams-kanalen en -chats](service-embed-report-microsoft-teams.md). Op het Power BI-tabblad kunnen uw collega's de gegevens van uw team vinden en die gegevens via uw teamkanalen met elkaar bespreken. 
- Wanneer u een koppeling naar uw rapporten, dashboards en apps in het Microsoft Teams-berichtvak plakt, wordt een [koppelingsvoorbeeld](service-teams-link-preview.md) gemaakt. Het koppelingsvoorbeeld toont informatie over de koppeling. 
- Gebruik [Delen met Microsoft Teams](service-share-report-teams.md) wanneer u rapporten en dashboards in de Power BI-service bekijkt om snel gesprekken in Microsoft Teams te starten.
- Gebruik de [Power BI-app in Microsoft Teams](service-microsoft-teams-app.md) om de ervaring van uw Power BI-basisservice in Microsoft Teams onder te brengen.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Schermopname van een Power BI-rapport dat in een Microsoft Teams-kanaal is ingesloten.":::

## <a name="requirements"></a>Vereisten

Over het algemeen geldt dat Power BI in Microsoft Teams werkt als u de volgende elementen kunt garanderen:

- Uw gebruikers over een Power BI Pro-licentie beschikken, of dat het rapport is ingesloten in een [Power BI Premium-capaciteit (EM of P SKU)](../admin/service-premium-what-is.md) met een Power BI-licentie.
- Gebruikers zich hebben aangemeld bij de Power BI-service om hun Power BI-licentie te activeren.
- Gebruikers voldoen aan de vereisten voor het gebruik van het **Power BI**-tabblad in Microsoft Teams.

## <a name="grant-access-to-reports"></a>Toegang verlenen tot rapporten

Wanneer een rapport wordt ingesloten in Microsoft Teams of een koppeling naar een item wordt verzonden, zijn gebruikers niet automatisch gemachtigd om het rapport te bekijken. U moet [gebruikers toestaan om het rapport in Power BI te bekijken](service-share-dashboards.md). U kunt een Microsoft 365-groep voor uw team gebruiken om dat gemakkelijker te maken.

> [!IMPORTANT]
> Controleer wie het rapport kan raadplegen in de Power BI-service en verleen toegang tot personen die niet worden vermeld.

Eén manier om ervoor te zorgen dat iedereen in een team toegang heeft tot rapporten, is door de rapporten in één werkruimte te plaatsen en de Microsoft 365-groep voor uw team toegang te geven.

## <a name="known-issues-and-limitations"></a>Bekende problemen en beperkingen

- Power BI ondersteunt niet dezelfde gelokaliseerde talen als Microsoft Teams. U kunt hierdoor mogelijk niet de juiste lokalisatie in het ingesloten rapport zien.
- Power BI-dashboards kunnen niet worden ingesloten in het **Power BI**-tabblad voor Microsoft Teams.
- Gebruikers zonder een Power BI-licentie of machtiging voor toegang tot het rapport krijgen een bericht dat de inhoud niet beschikbaar is.
- Mogelijk ontstaan er problemen als u Internet Explorer 10 gebruikt. <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-filters](service-url-filters.md) worden niet ondersteund voor het **Power BI**-tabblad voor Microsoft Teams.
- In nationale clouds is het nieuwe **Power BI**-tabblad niet beschikbaar. Er is mogelijk een oudere versie beschikbaar die geen ondersteuning biedt voor de nieuwe werkruimte of rapporten in Power BI-apps.
- Nadat u het tabblad hebt opgeslagen, kunt u de naam van het tabblad niet wijzigen via de instellingen op het tabblad. Gebruik de optie **Naam wijzigen** om deze te wijzigen.
- Eenmalige aanmelding wordt niet ondersteund voor de service voor koppelingsvoorbeelden.
- Koppelingsvoorbeelden werken niet in chat- of privé-kanalen voor vergaderingen.

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Power Platform in Microsoft Teams

De overige Microsoft Power Platform-apps worden ook geïntegreerd met Microsoft Teams.

- [Power Platform-beheerervaring](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>Volgende stappen

- [Power BI-inhoud insluiten in Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Een voorbeeld krijgen van een Power BI-koppeling in Microsoft Teams](service-teams-link-preview.md)
- [Rechtstreeks delen met Microsoft Teams vanuit de Power BI-service](service-share-report-teams.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).