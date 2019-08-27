---
title: Power BI-inhoud bekijken als externe gastgebruiker (Azure AD B2B)
description: Gebruik mobiele Power BI-apps om inhoud te bekijken die met u is gedeeld vanuit een externe organisatie.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: 900c7b57c2b6283c44e4a1923dd223d7dfd40ef7
ms.sourcegitcommit: d9755602235ba03594c348571b9102c9bf88d732
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490377"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>Power BI-inhoud bekijken die met u is gedeeld vanuit een externe organisatie

Power BI kan worden geïntegreerd met Azure actieve Directory Business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten uw organisatie. En externe gastgebruikers kunnen de mobiele Power BI-app gebruiken voor toegang tot die met hun gedeelde Power BI-inhoud. 


Van toepassing op:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Android-tablets |

## <a name="accessing-shared-content"></a>Toegang tot gedeelde inhoud

**Eerst moet iemand een item met u delen vanuit een externe organisatie.** Wanneer iemand [een item met u deelt](../../service-share-dashboards.md), ofwel vanuit dezelfde organisatie of vanuit een externe organisatie, ontvangt u een e-mail met een koppeling naar dat gedeelde item. Als u die koppeling op uw mobiele apparaat volgt, wordt de mobiele Power BI-app geopend. Als de app herkent dat het item is gedeeld vanuit een externe organisatie, maakt de app opnieuw verbinding met die organisatie met uw identiteit. Vervolgens worden alle items geladen die vanuit die organisatie met u zijn gedeeld.

![Gedeelde items openen in Power BI vanuit een e-mailbericht ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Als dit het eerste item is dat met u als een externe gastgebruiker is gedeeld, moet u de uitnodiging in een browser claimen. U kunt de uitnodiging niet claimen in de Power BI-app.

Zolang u bent verbonden met een externe organisatie, wordt een zwarte header in de app weergegeven. Deze header geeft aan dat u niet verbonden bent met uw thuisorganisatie. Als u opnieuw verbinding wilt maken met uw thuisorganisatie, moet u de gastmodus afsluiten.

![Header voor Power BI-gastgebruiker](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Zelfs als u een koppeling naar Power BI-artefacten nodig hebt om verbinding te maken met een externe organisatie, kunt u, zodra uw app is omgeschakeld, toegang krijgen tot alle items die met u zijn gedeeld (niet alleen het item dat u vanuit de e-mail hebt geopend). Als u alle items wilt weergeven waartoe u toegang hebt in de externe organisatie, gaat u naar het app-menu en selecteert u **Gedeeld met mij**. Onder **Apps** vindt u apps die u ook kunt gebruiken.

![Power BI-app-menu als externe gastgebruiker](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Beperkingen

- Gebruikers moeten over een actief Power BI-account en een starttenant beschikken.
- Gebruikers moeten bij hun Power BI-starttenant zijn aangemeld voordat ze toegang kunnen krijgen tot de inhoud die met ze is gedeeld vanuit een externe tenant.
- Voorwaardelijke toegang en andere Intune-beleidsregels worden niet ondersteund in Azure AD B2B en in Power BI Mobile. Dat betekent dat de app de beleidsregels van de thuisorganisatie afdwingt, als deze bestaan.
- Pushmeldingen worden alleen vanuit de thuisorganisatiesite ontvangen (zelfs wanneer de gebruiker als gast met een externe organisatie is verbonden). Als u de melding opent, wordt de app opnieuw verbonden met de thuisorganisatiesite van de gebruiker.
- Als de gebruiker de app uitschakelt en opnieuw opent, maakt de app automatisch verbinding met de thuisorganisatie van de gebruiker.
- Wanneer er een verbinding met een externe organisatie is gemaakt, zijn een aantal acties uitgeschakeld: favoriete items, gegevenswaarschuwingen, opmerkingen en delen.
- Offlinegegevens zijn niet beschikbaar wanneer u met een externe organisatie bent verbonden.
- Als u de bedrijfsportal-app hebt geïnstalleerd op uw apparaat, dan moet uw apparaat worden ingeschreven.
