---
title: Power BI-inhoud als een externe gastgebruiker (Azure AD B2B) weergeven
description: Mobiele Power BI-apps gebruiken om inhoud die met u is gedeeld van externe organisatie weer te geven.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/27/2019
ms.author: mshenhav
ms.openlocfilehash: a15da4349ce97e34c8321909abc862e424b2839c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61338643"
---
# <a name="view-power-bi-content-shared-with-you-from-an-external-organization"></a>Power BI-inhoud van een weergave van een externe organisatie met u gedeeld

Power BI kan worden geïntegreerd met Azure Active Directory business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten uw organisatie. En externe gastgebruikers ook kunnen de mobiele Power BI-app kunnen gebruiken voor toegang tot die Power BI-inhoud met hen worden gedeeld. 


Van toepassing op:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Android-telefoon](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Android-tablet](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPads |Android-telefoons |Android-tablets |

## <a name="accessing-shared-content"></a>Toegang krijgen tot gedeelde inhoud

**Eerst moet u iemand van een externe organisatie die een item met u delen.** Wanneer iemand [een item met u deelt](../../service-share-dashboards.md), van dezelfde organisatie of van een externe organisatie ontvangt u een e-mail met een koppeling naar dat artikel gedeeld. Die koppeling in uw mobiele apparaat te volgen, opent de mobiele Power BI-app. Als de app heeft vastgesteld dat het item uit een externe organisatie is gedeeld, opnieuw de app verbinding maakt met uw organisatie. De app wordt vervolgens geladen voor alle items die met u zijn gedeeld van die organisatie.

![Power BI gedeelde item openen in e-mail ](./media/mobile-apps-b2b/mobile-b2b-open-item-email.png)

> [!NOTE]
> Als dit het eerste item gedeeld met u als een externe gastgebruiker, moet u de uitnodiging in een browser claim. U kunt de uitnodiging in de Power BI-app niet claimen.

Als u met een externe organisatie een zwarte koptekst wordt weergegeven in de app verbonden bent. Deze header geeft aan dat u niet met uw thuisorganisatie verbonden bent. Voor verbinding met uw thuisorganisatie terug, sluit af van de gastmodus.

![Power BI Gast gebruiker koptekst](./media/mobile-apps-b2b/mobile-b2b-exit-home.png)

Hoewel u nodig hebt om een koppeling voor het artefact van Power BI verbinding maken met een externe organisatie zodra uw app verandert, kunt u alle items die worden gedeeld met u (niet alleen het artikel die u hebt geopend vanuit het e-mailbericht) openen. Als u wilt weergeven van alle items die u hebt toegang tot in de externe organisatie, gaat u naar het menu van de app en selecteer **gedeeld met mij**. Onder **Apps** vindt u apps die u kunt ook gebruiken.

![Menu voor de Power BI-app als gast externe gebruiker](./media/mobile-apps-b2b/mobile-b2b-menu.png)

## <a name="limitations"></a>Beperkingen

- Voorwaardelijke toegang en andere Intune-beleidsregels worden niet ondersteund in Azure AD B2B en in Power BI-mobiel. Dit betekent dat de app worden alleen de thuisorganisatie beleidsregels afgedwongen die, indien aanwezig.
- Pushmeldingen worden ontvangen van de site thuisorganisatie alleen (zelfs wanneer de gebruiker verbonden als gast voor een externe organisatie). Openen van de melding opnieuw verbinding wordt gemaakt van de gebruiker thuisorganisatie site met de app.
- Als de gebruiker de app wordt afgesloten wanneer opnieuw geopend de app automatisch maakt verbinding met de thuis organisatie van de gebruiker.
- Wanneer verbonden met een externe organisatie, sommige acties zijn uitgeschakeld: favoriete items,-gegevens wordt geactiveerd, opmerkingen en delen.
- Offlinesynchronisatie van gegevens is niet beschikbaar terwijl u bent verbonden met een externe organisatie.
- Als u de bedrijfsportal-app op uw apparaat geïnstalleerd hebt, moet uw apparaat worden geregistreerd.
