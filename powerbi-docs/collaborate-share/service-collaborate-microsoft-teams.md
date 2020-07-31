---
title: Samenwerken in Microsoft Teams met Power BI
description: U kunt eenvoudig interactieve Power BI-inhoud delen en hieraan samenwerken in Microsoft Teams-kanalen en -chats.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87253992"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Samenwerken in Microsoft Teams met Power BI

U hebt verschillende mogelijkheden om interactieve Power BI-inhoud te delen en hieraan samen te werken in Microsoft Teams-kanalen en -chats. 

- Met het **Power BI**-tabblad voor Microsoft Teams kunt u eenvoudig [interactieve rapporten insluiten in Microsoft Teams](service-embed-report-microsoft-teams.md)-kanalen en -chats. Op het **Power BI**-tabblad kunnen uw collega's de gegevens van uw team vinden en die gegevens via uw teamkanalen met elkaar bespreken. 
- Wanneer u een koppeling naar uw rapporten, dashboards en apps in het Microsoft Teams-berichtvak plakt, wordt een [koppelingsvoorbeeld](service-teams-link-preview.md) gemaakt. Het koppelingsvoorbeeld toont informatie over de koppeling. 
- Gebruik [Delen met Teams](service-share-report-teams.md) wanneer u rapporten en dashboards in de Power BI-service bekijkt om snel gesprekken in Teams te starten.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Schermopname van een Power BI-rapport dat in een Teams-kanaal is ingesloten.":::

## <a name="requirements"></a>Vereisten

Over het algemeen geldt dat Power BI in Microsoft Teams werkt als u de volgende elementen kunt garanderen:

- Uw gebruikers over een Power BI Pro-licentie beschikken, of dat het rapport is ingesloten in een [Power BI Premium-capaciteit (EM of P SKU)](../admin/service-premium-what-is.md) met een Power BI-licentie.
- Gebruikers zich hebben aangemeld bij de Power BI-service om hun Power BI-licentie te activeren.
- Gebruikers voldoen aan de vereisten voor het gebruik van het **Power BI**-tabblad in Microsoft Teams.

Als u het tabblad **Power BI** in Microsoft Teams wilt gebruiken, moet u ervoor zorgen dat:

- Microsoft Teams het **Power BI**-tabblad bevat.
- Als u een rapport wilt toevoegen aan Microsoft Teams met het **Power BI**-tabblad, moet u ten minste de rol Kijker hebben in de werkruimte die als host voor het rapport fungeert. Zie [Rollen in de nieuwe werkruimten](service-new-workspaces.md#roles-in-the-new-workspaces) voor informatie over de verschillende rollen.
- Als gebruikers het rapport willen bekijken op het **Power BI**-tabblad in Microsoft Teams, moeten ze gemachtigd zijn om het rapport te bekijken.
- Gebruikers moeten gebruikers van Microsoft Teams zijn met toegang tot kanalen en chats.

Als u de functionaliteit **Delen met Teams** in Power BI wilt gebruiken, moet u deze instelling configureren:

- Power BI-beheerders hebben de tenantinstelling **Delen met Teams** niet uitgeschakeld in de Power BI-beheerportal. Door deze instelling kunnen organisaties de knoppen **Delen met Teams** verbergen. Zie het artikel over de [Power BI-beheerportal](../admin/service-admin-portal.md#share-to-teams-tenant-setting) voor meer informatie.

## <a name="grant-access-to-reports"></a>Toegang verlenen tot rapporten

Wanneer een rapport wordt ingesloten in Microsoft Teams of een koppeling naar een item wordt verzonden, zijn gebruikers niet automatisch gemachtigd om het rapport te bekijken. U moet [gebruikers toestaan om het rapport in Power BI te bekijken](service-share-dashboards.md). U kunt een Microsoft 365-groep voor uw team gebruiken om dat gemakkelijker te maken.

> [!IMPORTANT]
> Controleer wie het rapport kan raadplegen in de Power BI-service en verleen toegang tot personen die niet worden vermeld.

Eén manier om ervoor te zorgen dat iedereen in een team toegang heeft tot rapporten, is door de rapporten in één werkruimte te plaatsen en de Microsoft 365-groep voor uw team toegang te geven.

## <a name="known-issues-and-limitations"></a>Bekende problemen en beperkingen

- Power BI ondersteunt niet dezelfde gelokaliseerde talen als Microsoft Teams. U kunt hierdoor mogelijk niet de juiste lokalisatie in het ingesloten rapport zien.
- Power BI-dashboards kunnen niet worden ingesloten in het **Power BI**-tabblad voor Microsoft Teams.
- Gebruikers zonder een Power BI-licentie of machtiging voor toegang tot het rapport krijgen een bericht dat de inhoud niet beschikbaar is.
- Mogelijk ontstaan er problemen als u Internet Explorer 10 gebruikt. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL-filters](service-url-filters.md) worden niet ondersteund voor het **Power BI**-tabblad voor Microsoft Teams.
- In nationale clouds is het nieuwe **Power BI**-tabblad niet beschikbaar. Er is mogelijk een oudere versie beschikbaar die geen ondersteuning biedt voor de nieuwe werkruimte of rapporten in Power BI-apps.
- Nadat u het tabblad hebt opgeslagen, kunt u de naam van het tabblad niet wijzigen via de instellingen op het tabblad. Gebruik de optie **Naam wijzigen** om deze te wijzigen.
- Eenmalige aanmelding wordt niet ondersteund voor de service voor koppelingsvoorbeelden.
- Koppelingsvoorbeelden werken niet in chat- of privé-kanalen voor vergaderingen.

## <a name="next-steps"></a>Volgende stappen

- [Power BI-inhoud insluiten in Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Een voorbeeld krijgen van een Power BI-koppeling in Microsoft Teams](service-teams-link-preview.md)
- [Rechtstreeks delen met Teams vanuit de Power BI-service](service-share-report-teams.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/).
