---
title: Ingesloten analyses met Power BI
description: Power BI biedt API's voor het gebruik van ingesloten analyse voor uw dashboards en rapporten in toepassingen. Meer informatie over insluiten met Power BI in zowel een PaaS-omgeving als een SaaS-omgeving met behulp van software voor ingesloten analyses, hulpprogramma's voor ingesloten analyses of hulpprogramma's voor ingesloten business intelligence.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051069"
---
# <a name="embedded-analytics-with-power-bi"></a>Ingesloten analyses met Power BI

De Power BI-service (SaaS) en de Power BI Embedded-service in Azure (PaaS) bevatten API's voor het insluiten van uw dashboards en rapporten. Wanneer u inhoud insluit, biedt dit u toegang tot de nieuwste Power BI-functies zoals dashboards, gateways en app-werkruimten.

U kunt het [installatieprogramma voor insluiten](https://aka.ms/embedsetup) uitvoeren om snel aan de slag te gaan en een voorbeeldtoepassing te downloaden.

Kies de oplossing die het beste bij u past:

* [Met het insluiten van inhoud voor uw organisatie](embedding.md#embedding-for-your-organization) kunt u Power BI-service uitbreiden. U doet dit door implementeert de [insluiten voor uw organisatie](https://aka.ms/embedsetup/UserOwnsData) oplossing.
* [Insluiten van inhoud voor uw klanten](embedding.md#embedding-for-your-customers) kunt u insluiten van dashboards en rapporten voor gebruikers die geen Power BI-account. U doet dit door implementeert de [insluiten voor uw klanten](https://aka.ms/embedsetup/AppOwnsData) oplossing.

![Voorbeeld van PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>API's gebruiken

Er zijn twee hoofdscenario's voor het insluiten van Power BI-inhoud:
- Inhoud insluiten voor gebruikers van uw organisatie (met Power BI-licenties). 
 
- Insluiten van inhoud voor uw gebruikers en klanten die geen Power BI-licenties nodig hebben. 

De [Power BI REST-API](https://docs.microsoft.com/rest/api/power-bi/) kunt beide scenario's.

Voor klanten en gebruikers zonder een Power Bi-licentie kunt u met dezelfde API dashboards en rapporten insluiten in uw aangepaste toepassing voor zowel uw organisatie als uw klanten. De beheerde toepassing gegevens zichtbaar voor uw klanten. Ook Power BI-gebruikers van uw organisatie hebben aanvullende opties om weer te geven *hun gegevens* rechtstreeks in Power BI of in de context van de ingesloten toepassing. U kunt profiteren van de JavaScript- en REST-API's voor uw behoeften bij het insluiten van inhoud.

Zie voor meer informatie over het insluiten van inhoud werkt, de [insluitvoorbeeld voor JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inhoud insluiten voor uw organisatie

**Met het insluiten van inhoud voor uw organisatie** kunt u Power BI-service uitbreiden. Deze insluiten vereist van uw toepassing gebruikers aanmelding in de Power BI-service om de inhoud weer te geven. Als iemand in uw organisatie zich heeft aangemeld, heeft hij alleen toegang tot zijn eigen dashboards en rapporten of de dashboards en rapporten die met hem zijn gedeeld in de Power BI-service.

Insluiten voorbeelden van organisatie zijn interne toepassingen zoals [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [Microsoft Teams-integratie (u moet beschikken over beheerdersrechten)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), en [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Als u wilt insluiten voor uw organisatie, Zie [zelfstudie: Power BI-inhoud insluiten in een toepassing voor uw organisatie](embed-sample-for-your-organization.md).

Mogelijkheden voor selfservice, zoals bewerken, opslaan en meer, zijn beschikbaar via de [JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript) wanneer u inhoud insluit voor Power BI-gebruikers.

U kunt doorlopen de [Embedding setup-hulpprogramma](https://aka.ms/embedsetup/UserOwnsData) aan de slag en downloaden van een voorbeeldtoepassing die u begeleidt bij het integreren van een rapport voor uw organisatie.

## <a name="embedding-for-your-customers"></a>Inhoud voor uw klanten insluiten

**Insluiten van inhoud voor uw klanten** kunt u insluiten van dashboards en rapporten voor gebruikers die geen Power BI-account. Ook wel bekend als dit het insluiten is *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) is een **Microsoft Azure** service waarmee independent software vendors (ISV's) en ontwikkelaars snel visuele elementen, rapporten en dashboards insluiten in een toepassing. Deze insluiten vindt plaats via een gecontroleerde model op basis van capaciteit, per uur.

![Stroom voor het insluiten van inhoud voor uw klanten](media/embedding/powerbi-embed-flow.png)

Power BI Embedded biedt voordelen voor ISV's, ontwikkelaars en klanten. Een ISV kan bijvoorbeeld gratis visuals maken met Power BI Desktop. Door de analytische ontwikkeling van visuele minimaliseren, ISV's hun producten sneller op de markt brengen en van de concurrentie met hun onderscheidende gegevenservaringen opvallen. ISV's kunnen er ook voor kiezen om aan te brengen voor de meerwaarde die ze met ingesloten analyses maken.

Met Power BI Embedded hebben uw klanten geen voorkennis over Power BI nodig. U kunt twee verschillende methoden gebruiken om een ingesloten toepassing te maken:
- Power BI Pro account 
- Service-principal 

De Power BI Pro-account fungeert als hoofdaccount voor van uw toepassing (denk aan het als een proxyaccount). Dit account kunt u voor het genereren van tokens die toegang tot de Power BI-dashboards en rapporten van uw toepassing bieden insluiten.

Met een [service-principal](embed-service-principal.md) kan Power BI-inhoud worden ingesloten in een toepassing met behulp van een token dat **alleen voor een app kan worden gebruikt**. Ook kunt u voor het genereren van tokens die toegang tot de Power BI-dashboards en rapporten van uw toepassing bieden insluiten.

Ontwikkelaars die gebruikmaken van Power BI Embedded kunnen besteden aan de tijd op het maken van hun toepassing Kernfunctionaliteit in plaats van de bestedingslimiet ontwikkeling van visuele elementen en analytics. Ze kunnen snel voldoen aan de klant rapportage- en dashboardverwachtigingen en deze eenvoudig insluiten met volledig gedocumenteerde API's en SDK's. Door het verkennen van gegevens eenvoudig te maken in apps, kunnen ISV's ervoor zorgen dat klanten op welk apparaat dan ook snel goede beslissingen kunnen nemen in de juiste context.

> [!IMPORTANT]
> Tijdens het insluiten van Power BI-service vereist, hoeft uw klanten niet te hebben van een Power BI-account van uw toepassing ingesloten inhoud weer te geven. 

Wanneer u klaar bent om tot productie over te gaan, moet uw app-werkruimte worden toegewezen aan een speciale capaciteit. Power BI Embedded in Microsoft Azure biedt [toegewezen capaciteiten](azure-pbie-create-capacity.md) voor gebruik met uw toepassingen.

Voor het insluiten van informatie, Zie [Power BI-inhoud insluiten](embed-sample-for-customers.md).

## <a name="next-steps"></a>Volgende stappen

U kunt nu proberen om Power BI-inhoud in te sluiten in een toepassing of Power BI-inhoud in te sluiten voor uw klanten.

> [!div class="nextstepaction"]
> [Insluiten voor uw organisatie](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Wat is Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
