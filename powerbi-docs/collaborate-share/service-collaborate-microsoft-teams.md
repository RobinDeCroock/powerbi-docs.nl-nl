---
title: Samenwerken in Microsoft Teams met Power BI
description: Naarmate verspreide werknemers meer en meer de norm worden, vertrouwen steeds meer organisaties op Microsoft Teams om werken op afstand mogelijk te maken en werknemers op één lijn te houden.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 7c8fa59521be1cfc8bb25fb04c3904f257fb62be
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926689"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Samenwerken in Microsoft Teams met Power BI

Naarmate verspreide werknemers meer en meer de norm worden, vertrouwen steeds meer organisaties op Microsoft Teams om werken op afstand mogelijk te maken en werknemers op één lijn te houden. In dit artikel worden opties beschreven om interactieve Power BI-inhoud te delen en hieraan samen te werken in Microsoft Teams-kanalen en -chats. 

- Met het tabblad **Power BI** voor Microsoft Teams kunt u [interactieve rapporten insluiten in Microsoft Teams-kanalen en -chats](service-embed-report-microsoft-teams.md). Op het Power BI-tabblad kunnen uw collega's de gegevens van uw team vinden en die gegevens via uw teamkanalen met elkaar bespreken. 
- Wanneer u een koppeling naar uw rapporten, dashboards en apps in het Microsoft Teams-berichtvak plakt, wordt een [koppelingsvoorbeeld](service-teams-link-preview.md) gemaakt. Het koppelingsvoorbeeld toont informatie over de koppeling. 
- Gebruik [Chatten in Microsoft Teams](service-share-report-teams.md) wanneer u rapporten en dashboards in de Power BI-service bekijkt om snel gesprekken in Microsoft Teams te starten.
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

## <a name="share-with-external-users"></a>Delen met externe gebruikers

U kunt een Power BI rapport integreren in Teams en delen met externe gebruikers. Dit zijn de stappen.

1.  U nodigt de externe gebruiker uit in uw organisatie en deze accepteert uw uitnodiging. Zie [Power BI-inhoud distribueren naar externe gastgebruikers met behulp van Azure Active Directory B2B](../guidance/whitepaper-azure-b2b-power-bi.md) voor meer informatie.
2.  Geef de externe gebruiker machtigingen voor het rapport. Toewijzing van afzonderlijke machtigingen werkt het beste.
3.  Zorg ervoor dat aan de externe gebruiker een Power BI-licentie is toegewezen. Als de inhoud zich in Premium-capaciteit bevindt, heeft de gebruiker alleen een gratis licentie nodig. Als dat niet het geval is, kan de gebruiker [zich registreren voor een individuele gratis proefversie van Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).

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
- [Chatten in Microsoft Teams vanuit de Power BI-service](service-share-report-teams.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).
