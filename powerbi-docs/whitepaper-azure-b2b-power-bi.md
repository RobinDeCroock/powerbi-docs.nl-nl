---
title: Distribueren van Power BI-inhoud naar externe gastgebruikers met behulp van Azure Active Directory B2B
description: Technisch document waarin wordt beschreven hoe u Power BI distribueren naar externe gastgebruikers met Azure Active Directory B2B
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051598"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribueren van Power BI-inhoud naar externe gastgebruikers met behulp van Azure Active Directory B2B

**Samenvatting:** Dit is een technisch document met overzicht van hoe u inhoud distribueert naar gebruikers buiten de organisatie met behulp van de integratie van Azure Active Directory Business-to-business (Azure AD B2B).

**Schrijvers van:** Lukasz Pawlowski, Kasper de Jonge

**Technische controleurs:** Active Directory-toepassingsmodus Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Active Directory-toepassingsmodus Saxton, Maya Shenhav, Nimrod Shalit, voor Olson

> [!NOTE]
> U kunt dit technische document opslaan of afdrukken door in uw browser **Afdrukken** en vervolgens **Opslaan als PDF-bestand** te selecteren.

## <a name="introduction"></a>Inleiding

Power BI biedt organisaties een 360-graden weergave van hun bedrijf en gebruikers in deze organisaties om intelligente beslissingen te nemen met behulp van gegevens. Veel van deze organisaties hebben sterke en vertrouwde relaties met externe partners, clients en contractanten. Deze organisaties moeten beveiligde toegang tot Power BI-dashboards en rapporten voor gebruikers in deze externe partners.

Power BI kan worden geïntegreerd met [Azure Active Directory Business-to-business (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) om toe te staan veilige distributie van Power BI-inhoud naar gastgebruikers buiten de organisatie – terwijl nog steeds de controle behouden kan blijven en inzake de toegang tot interne gegevens.

Dit technische document bevat informatie over de alle benodigde informatie om te begrijpen van Power BI-integratie met Azure Active Directory B2B. Behandelen we de meest voorkomende use-case, installatie, licentie- en beveiliging op rijniveau.

> [!NOTE]
> In deze whitepaper verwijzen we naar Azure Active Directory als Azure AD en Azure Active Directory Business to Business als Azure AD B2B.

## <a name="scenarios"></a>Scenario 's

Contoso is een fabrikant van auto's en werkt met veel verschillende leveranciers die deze voorzien van alle onderdelen, materialen en services die nodig zijn voor de productie-bewerkingen uitvoeren. Contoso wil de supply chain logistiek en plannen voor Power BI gebruiken voor het bewaken van de toeleveringsketen te stroomlijnen. Contoso wil delen met externe supply chain partners analytics op een veilige en beheerbare manier.

Contoso kan de volgende ervaringen voor externe gebruikers met behulp van Power BI en Azure AD B2B inschakelen.

### <a name="ad-hoc-per-item-sharing"></a>Ad-hoc per item delen

Contoso werkt met de leverancier die radiatoren voor auto's van Contoso is gebaseerd. Vaak het geval is, moeten ze de betrouwbaarheid van de radiatoren met gegevens uit alle Contoso van auto's te optimaliseren. Een analist bij Contoso maakt gebruik van Power BI een rapport van de betrouwbaarheid straler delen met een Engineer bij de leverancier. De Engineer ontvangt een e-mailbericht met een koppeling om het rapport weer te geven.

Zoals hierboven beschreven, wordt ad-hoc delen uitgevoerd door zakelijke gebruikers op basis van wanneer dat nodig is. De koppeling die is verzonden door Power BI naar de externe gebruiker is de koppeling van een Azure AD B2B-uitnodiging. Wanneer de externe gebruiker de koppeling opent, wordt ze gevraagd om toe te voegen van Contoso Azure AD-organisatie als gastgebruiker. Nadat de uitnodiging is geaccepteerd, wordt de koppeling opent het specifieke rapport of dashboard. De Azure Active Directory-beheerder machtigingen voor externe gebruikers uitnodigen voor de organisatie voor netwerkapparaten delegeert en kiest die gebruikers kunnen doen wanneer ze de uitnodiging accepteren, zoals beschreven in de sectie beheer van dit document. De Contoso-analist kan de gastgebruiker uitnodigen alleen omdat de Azure AD-beheerder is toegestaan die actie en de Power BI-beheerder gebruikers toegestaan om uit te nodigen gasten om inhoud in Power BI tenant-instellingen weer te geven.

![Gasten uitnodigen voor Power BI met behulp van AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Het proces wordt gestart met een interne Contoso-gebruiker een dashboard of rapport delen met een externe gebruiker. Als de externe gebruiker nog niet een gast in de Contoso Azure AD, ze zijn uitgenodigd. Een e-mailbericht is verzonden naar het e-mailadres met een uitnodiging aan voor het Contoso Azure AD
2. De ontvanger accepteert de uitnodiging aan voor Contoso de Azure AD en wordt toegevoegd als een gastgebruiker in het Contoso Azure AD.
3. De ontvanger wordt vervolgens omgeleid naar de Power BI-dashboard, rapport of app, die alleen-lezen voor de gebruiker zijn.

Het proces wordt beschouwd als van ad-hoc omdat de actie uitnodigen als nodig zijn voor hun zakelijke doeleinden uitvoeren die zakelijke gebruikers in Contoso. Elk item gedeeld is de externe gebruiker toegang heeft tot één koppeling om de inhoud weer te geven.

Nadat de externe gebruiker is uitgenodigd voor toegang tot resources van Contoso, een schaduwkopie-account voor hen in Contoso Azure AD kan worden gemaakt en ze hoeven niet opnieuw worden uitgenodigd.  De eerste keer dat ze toegang krijgen tot een Contoso-bron, zoals Power BI-dashboard, proberen ze via een toestemming-proces, dat de uitnodiging wordt ingewisseld.  Als de toestemming niet is voltooid, hebben geen toegang tot een van de inhoud van Contoso.  Als ze problemen ondervindt bij het inwisselen van de uitnodiging via de oorspronkelijke koppeling, kan een Azure AD-beheerder een voor specifieke-uitnodigingskoppeling voor deze om in te wisselen verzonden.

### <a name="planned-per-item-sharing"></a>Geplande per item delen

Contoso werkt met een onderaannemer is voor analyse van radiatoren betrouwbaarheid. De toeleverancier heeft een team van 10 personen die toegang nodig tot de gegevens in Power BI-omgeving van Contoso. De beheerder van Contoso Azure AD is betrokken om uit te nodigen van alle gebruikers en om af te handelen toevoegingen/wijzigingen als personeel bij de wijziging toeleverancier. De Azure AD-beheerder maakt een beveiligingsgroep voor alle werknemers op de toeleverancier. Met behulp van de beveiligingsgroep, kunnen werknemers van Contoso eenvoudig toegang tot rapporten beheren en controleer of alle vereiste toeleverancier medewerkers hebben toegang tot alle vereiste rapporten, dashboards en Power BI-apps. De Azure AD-beheerder kan ook voorkomen worden betrokken bij het uitnodigingsproces helemaal door te kiezen om te delegeren van rechten van de uitnodiging naar een vertrouwde werknemer van Contoso of op de verantwoordelijkheid om ervoor te zorgen tijdige personeel management.

Sommige organisaties vereisen meer controle over wanneer externe gebruikers worden toegevoegd, worden veel gebruikers in een externe organisatie of veel externe organisaties uitnodigen. In dergelijke gevallen kan het delen van geplande worden gebruikt voor het beheren van de schaal van de organisatie beleid afdwingen, en zelfs voor het delegeren van rechten voor het vertrouwde personen uitnodigen en beheren van externe gebruikers delen. Geplande uitnodigingen worden rechtstreeks verzonden biedt ondersteuning voor Azure AD B2B [vanuit Azure portal door een IT-beheerder](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), of via [PowerShell met de uitnodiging manager API](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) waar een groep gebruikers in een kan worden uitgenodigd de actie. Met behulp van de geplande uitnodigingen benadering, de organisatie kan bepalen wie kan gebruikers uitnodigen en goedkeuringsprocessen implementeren. Geavanceerde Azure AD-functies zoals dynamische groepen kunnen eenvoudig het lidmaatschap van beveiligingsgroep automatisch onderhouden.


![Besturingselement voor welke gasten kunnen inhoud bekijken](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. De sterren proces met een IT-beheerder de gastgebruiker handmatig of via de API wordt geleverd door Azure Active Directory uitnodigen
2. De gebruiker accepteert de uitnodiging voor de organisatie.
3. Zodra de gebruiker de uitnodiging heeft geaccepteerd, kan een gebruiker in Power BI een rapport of dashboard delen met de externe gebruiker of een beveiligingsgroep die deel uitmaken van. Net als met reguliere delen in Power BI de externe gebruiker ontvangt een e-mailbericht met de koppeling naar het item.
4. Wanneer de externe gebruiker toegang krijgt tot de koppeling, de verificatie in de directory wordt doorgegeven aan Contoso Azure AD- en van gebruikt voor toegang tot de Power BI-inhoud.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>AD-hoctaak of geplande delen van Power BI-Apps

Contoso heeft een set met rapporten en dashboards die ze nodig hebben om te delen met een of meer leveranciers. Om te controleren of alle vereiste externe gebruikers toegang hebben tot deze inhoud, wordt deze geleverd als een Power BI-app. De externe gebruikers worden ofwel rechtstreeks naar de app-toegangslijst of via beveiligingsgroepen toegevoegd. Iemand bij Contoso verzendt vervolgens de app-URL op alle externe gebruikers, bijvoorbeeld in een e-mailbericht. Wanneer de externe gebruikers de koppeling openen, zien ze de inhoud in één eenvoudig te navigeren ervaring.

Met behulp van een Power BI-app, kunt u eenvoudig voor Contoso voor het bouwen van een BI-Portal voor haar leveranciers. Een toegangslijst met één beheert de toegang tot alle vereiste inhoud verspilling van tijd controleren en de item-level instellingsmachtigingen verminderen. Azure AD B2B onderhoudt toegang met behulp van de eigen identiteit van de leverancier, zodat gebruikers geen aanvullende aanmeldingsreferenties hoeft. Als u met behulp van geplande uitnodigingen met beveiligingsgroepen, wordt beheer van toegang tot de app zoals personeel naar of uit het project draaien vereenvoudigd. Lidmaatschap van security groups handmatig of met behulp van [dynamische groepen](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), zodat alle externe gebruikers van een andere leverancier worden automatisch toegevoegd aan de juiste beveiligingsgroep.


![Besturingselement voor inhoud met AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Het proces wordt gestart door de gebruiker wordt verzocht te van Contoso Azure AD-organisatie via Azure portal of PowerShell
2. De gebruiker kan worden toegevoegd aan een groep in Azure AD. Een statische of dynamische gebruikersgroep kan worden gebruikt, maar dynamische groepen te verminderen handmatig werk.
3. De externe gebruikers toegang krijgen tot de Power BI-App via de gebruikersgroep. De app URL moet worden verzonden rechtstreeks naar de externe gebruiker of op een site geplaatst dat ze toegang hebben. Power BI maakt een best-effort voor het verzenden van een e-mailbericht met de app-koppeling voor externe gebruikers, maar wanneer u groepen waarvan het lidmaatschap kunt wijzigen, is geen Power BI kunnen verzenden naar alle externe gebruikers die worden beheerd via gebruikersgroepen.
4. Wanneer de externe gebruiker toegang heeft tot de URL van de Power BI-app, worden ze geverifieerd door van Contoso Azure AD, de app is geïnstalleerd voor de gebruiker en de gebruiker kan zien alle ingesloten rapporten en dashboards in de app.

Apps hebben ook een unieke functie waarmee de app-auteurs voor het installeren van de toepassing automatisch voor de gebruiker, zodat deze beschikbaar is wanneer de gebruiker zich aanmeldt. Deze functie wordt alleen automatisch geïnstalleerd voor externe gebruikers die al deel uitmaakt van het Contoso-organisatie op het moment dat de toepassing wordt gepubliceerd of bijgewerkt. Daarom het beste kan worden gebruikt met de aanpak van geplande uitnodigingen en is afhankelijk van de app wordt gepubliceerd of bijgewerkt nadat de gebruikers zijn toegevoegd aan het Contoso Azure AD. Externe gebruikers kunnen de app via de koppeling van de app altijd installeren.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Opmerkingen en Abonneer u op inhoud tussen verschillende organisaties

Omdat Contoso blijft gewoon werken met de onderaannemers en leveranciers, moeten de externe Engineers werken nauw samen met de Contoso-analisten. Power BI biedt verschillende functies voor samenwerking, waarmee gebruikers kunnen communiceren over inhoud die ze kunnen gebruiken. Dashboard opmerkingen (en binnenkort rapporteren opmerkingen) kunnen gebruikers bespreken gegevenspunten ze zien en communiceren met auteurs van rapporten om vragen te stellen.

Op dit moment deel externe gastgebruikers ook kunnen uitmaken van opmerkingen door opmerkingen verlaten en de antwoorden te lezen. In tegenstelling tot interne gebruikers gastgebruikers kunnen echter niet @mentioned en ontvangt geen meldingen dat ze een opmerking hebt ontvangen. Gastgebruikers ook kunnen niet de functie voor abonnementen in Power BI gebruiken op het moment van schrijven. In een toekomstige release deze beperkingen wordt opgeheven en de gastgebruiker ontvangt een e-mail wanneer een opmerking @mentions , of wanneer een abonnement aan hun e-mailbericht met een koppeling naar de inhoud in Power BI wordt geleverd.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Toegang tot inhoud in de mobiele Power BI-apps

In een toekomstige release van Contoso gebruikers rapporten of dashboards met hun externe Gast collega's delen, Power BI wordt een e-mail verzenden wanneer de Gast de hoogte te brengen. Wanneer de gastgebruiker wordt geopend de koppeling naar het rapport of dashboard op hun mobiele apparaat, wordt de inhoud wordt geopend in de systeemeigen mobiele Power BI-apps op hun apparaat, als ze worden geïnstalleerd. De gastgebruiker wordt vervolgens mogelijk zijn om te navigeren tussen de inhoud die met hen worden gedeeld in de externe tenant en weer terug naar hun eigen inhoud uit de oorspronkelijke tenant.

> [!NOTE]
> De gastgebruiker kan niet open de mobiele Power BI-app en vervolgens direct naar de externe tenant, ze moeten beginnen met een koppeling naar een item in de externe tenant. Algemene oplossingen worden beschreven in de [distribueren van koppelingen naar inhoud in de bovenliggende organisatie Power BI](#distributing-links-to-content-in-the-parent-organizations-power-bi) verderop in dit document.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Binnen de organisatie bewerken en beheren van Power BI-inhoud

Contoso en haar leveranciers en onderaannemers steeds nauw samenwerken. Een analist van de onderaannemer moet vaak aanvullende metrische gegevens of gegevens visualisaties moeten worden toegevoegd aan een rapport die Contoso heeft gedeeld met hen. De gegevens moet zich in de Power BI-tenant van Contoso bevinden, maar externe gebruikers moeten kunnen bewerken, nieuwe inhoud maken en deze zelfs te distribueren naar de juiste personen.

Power BI biedt een optie waarmee **externe gastgebruikers kunnen bewerken en beheren van inhoud** in de organisatie. Externe gebruikers hebben standaard een alleen-lezen verbruik gebaseerde ervaring. Deze nieuwe instelling kan echter de Power BI-beheerder om te kiezen welke externe gebruikers kunnen bewerken en beheren van inhoud binnen hun organisatie. Zodra toegestaan, kunt de externe gebruiker bewerken van rapporten, dashboards, publiceren of apps bijwerken, werkt in werkruimten en verbinding maken met gegevens die ze gemachtigd zijn om te gebruiken.

In dit scenario wordt beschreven in de sectie inschakelen van externe gebruikers om te bewerken en beheren van inhoud in Power BI verderop in dit document.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Organisatie-relaties met behulp van Power BI en Azure AD B2B

Als alle gebruikers van Power BI intern gebruik binnen de organisatie, is er niet nodig om te gebruiken van Azure AD B2B. Echter, als twee of meer organisaties samenwerken aan gegevens en inzichten wilt, Power BI ondersteuning voor Azure AD B2B maakt het eenvoudig en efficiënt om dit te doen.

Hieronder vindt u doorgaans aangetroffen organisatiestructuren die geschikt voor Azure AD B2B-samenwerking stijl tussen verschillende organisaties in Power BI zijn. Azure AD B2B werkt goed in de meeste gevallen, maar in sommige gevallen de gemeenschappelijke alternatieve methoden aan het einde van dit document behandeld waard zijn.

### <a name="case-1-direct-collaboration-between-organizations"></a>Geval 1: Directe samenwerking tussen organisaties

Relatie met de leverancier straler van Contoso is een voorbeeld van directe samenwerking tussen organisaties. Aangezien er relatief weinig gebruikers bij Contoso zijn en de leverancier die toegang nodig tot straler betrouwbaarheid informatie, met behulp van Azure AD B2B op basis van extern delen is ideaal. Het is eenvoudig te gebruiken en eenvoudig te beheren. Dit is ook een algemeen patroon in adviesservices waar een consultant mogelijk te maken van inhoud voor een organisatie.

![Delen tussen organisaties](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Normaal gesproken delen hiervan vindt plaats in eerste instantie met behulp van Ad hoc per item delen. Echter, zoals teams vergroten of relaties verdiepen, de geplande per item delen wordt benadering van de aanbevolen methode om beheeroverhead te verminderen. De Ad-hoc of geplande delen van Power BI-Apps, opmerkingen en Abonneer u op inhoud tussen verschillende organisaties, kan bovendien toegang tot inhoud in de mobiele apps in de play ook, en binnen de organisatie bewerken en het beheer van Power BI-inhoud komen. Als beide organisaties gebruikers Power BI Pro-licenties in hun respectieve organisatie hebt, kunnen ze deze Pro-licenties echter gebruiken in elkaars Power BI-omgevingen. Dit biedt voordeligste licentieverlening omdat de uitnodigende organisatie niet wellicht te betalen voor Power BI Pro-licentie voor de externe gebruikers. Dit wordt in de sectie Licensing verderop in dit document uitvoeriger besproken.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Geval 2: Bovenliggende en haar dochterondernemingen of partners

Sommige organisatiestructuren zijn complexer worden, met inbegrip van geheel of gedeeltelijk dochterondernemingen, gelieerde ondernemingen of beheerde serviceprovider-relaties. Deze organisaties hebben een bovenliggende organisatie, zoals een holding, maar de onderliggende organisaties werkt autonoom puntkomma, soms onder verschillende regionale vereisten. Dit leidt tot elke organisatie met een eigen Azure AD-omgeving en de afzonderlijke Power BI-tenants.

![Werken met dochterondernemingen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


In deze structuur moet de bovenliggende organisatie doorgaans gestandaardiseerde inzichten aan haar dochterondernemingen distribueren. Normaal gesproken delen hiervan vindt plaats met behulp van de Ad-hoctaak of geplande delen van Power BI-Apps-benadering, zoals wordt geïllustreerd in de volgende afbeelding, aangezien hiermee distributie van gestandaardiseerde gezaghebbende inhoud naar grote doelgroepen. Een combinatie van alle scenario's die eerder in dit document worden vermeld in de praktijk is gebruikt.

![Scenario's te combineren](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Dit komt overeen met het volgende proces:

1. Gebruikers van elke vestiging worden uitgenodigd voor van Contoso Azure AD
2. Vervolgens is de Power BI-app gepubliceerd voor deze gebruikers toegang verleent tot de vereiste gegevens
3. Ten slotte openen de gebruikers de app via een koppeling die ze hebt gekregen om te zien van de rapporten

Enkele belangrijke uitdagingen worden geconfronteerd door organisaties in deze structuur:

- Het distribueren van koppelingen naar inhoud in de bovenliggende organisatie Power BI
- Ondergeschikte gebruikers toegang krijgen tot de gegevensbron die wordt gehost door de bovenliggende organisatie toestaan

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribueren van koppelingen naar inhoud in de bovenliggende organisatie Power BI

Drie manieren worden veelvuldig gebruikt om koppelingen naar de inhoud distribueren. De eerste en de meeste basic zich voor het verzenden van de koppeling naar de app en de vereiste gebruikers of plaats deze in een SharePoint Online-site waaruit kan worden geopend. Gebruikers kunnen vervolgens een bladwijzer voor de koppeling in de browser voor snellere toegang tot de gegevens die ze nodig hebben.

De tweede methode, is afhankelijk van de gehele organisatie bewerken en het beheer van Power BI-inhoud capaciteit. De bovenliggende organisatie kan gebruikers van de dochterondernemingen voor toegang tot de Power BI en bepaalt wat ze kunnen toegang tot en met de machtiging. Dit biedt toegang tot Power BI start wanneer de gebruiker van het filiaal een uitgebreide lijst van inhoud die aan hen zijn gedeeld in de tenant van de organisatie van de bovenliggende ziet. Vervolgens wordt de URL naar de Power BI-omgeving is de bovenliggende organisatie gegeven aan de gebruikers op de dochterondernemingen.

De laatste methode maakt gebruik van een Power BI-app gemaakt in de Power BI-tenant voor elke vestiging. De Power BI-app bevat een dashboard met [tegels die zijn geconfigureerd met de optie externe koppeling](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Wanneer de gebruiker op de tegel drukt, worden ze naar de juiste rapport, een dashboard of een app in de bovenliggende organisatie Power BI genomen. Deze methode heeft het bijkomende voordeel dat de app automatisch voor alle gebruikers in het filiaal kan worden geïnstalleerd en die voor hen beschikbaar is wanneer ze zich aanmelden bij hun eigen Power BI-omgeving. Een bijkomend voordeel van deze benadering is dat het werkt ook met de mobiele Power BI-apps die de koppeling systeemeigen kunnen openen. U kunt dit ook combineren met de tweede methode om in te schakelen eenvoudiger schakelen tussen Power BI-omgevingen.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Zodat gebruikers toegang tot gegevensbronnen die worden gehost door de bovenliggende organisatie een filiaal

Vaak analisten van een onderneming gelieerd aan hoeft te maken van hun eigen van analyses met gegevens die worden geleverd door de bovenliggende organisatie. In dit geval vaak gegevens in de cloud bronnen worden gebruikt om op te lossen de uitdaging.

De eerste methode maakt gebruik van [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) aan het bouwen van een datawarehouse voor ondernemingen kwaliteit die een registratiesysteem vormt van de behoeften van analisten in de bovenliggende en haar dochterondernemingen zoals wordt weergegeven in de volgende afbeelding. Contoso kan hosten van de gegevens en gebruik van de mogelijkheden, zoals beveiliging op rijniveau om te controleren of gebruikers in elke vestiging toegang alleen de gegevens tot. Analisten van elke organisatie kunnen toegang krijgen tot het datawarehouse via Power BI Desktop en resulterende analytics publiceren naar hun respectieve tenants van Power BI.

![Hoe delen plaatsvindt met Power BI-tenants](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


De tweede methode maakt gebruik van [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) aan het bouwen van een relationele datawarehouse voor toegang tot gegevens. Dit werkt op dezelfde manier naar de Azure Analysis Services-benadering, maar sommige mogelijkheden, zoals beveiliging op rijniveau mogelijk moeilijker te implementeren en onderhouden in dochterondernemingen.

Meer geavanceerde methoden zijn ook mogelijk, maar de bovenstaande verreweg de meest voorkomende zijn.

### <a name="case-3-shared-environment-across-partners"></a>Voorbeeld 3: Gedeelde omgeving voor partners

Contoso kan invoeren in een partnerschap met het bouwen van gezamenlijk een auto op een gedeelde assemblagelijn, maar voor het distribueren van het voertuig onder verschillende merken of in verschillende regio's van een concurrent. Hiervoor hebt u uitgebreide samenwerking en co-ownership van gegevens, informatie en analyse tussen verschillende organisaties. Deze structuur is ook veel voor in de bedrijfstak van de consulting services waar consultants van analyses op basis van een project voor een client kan doen.

![Gedeelde omgeving voor partners](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



In de praktijk deze structuren zijn complex zoals wordt weergegeven in de volgende afbeelding en personeel te handhaven vereist. Als u wilt worden van kracht deze structuur is afhankelijk van de gehele organisatie bewerken en het beheer van Power BI-inhoud mogelijkheid omdat organisaties om Power BI Pro-licenties aangeschaft voor hun respectieve tenants van Power BI opnieuw te gebruiken.

![Licenties en gedeelde organisatie inhoud](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Voor het maken van een gedeelde Power BI-tenant, een Azure Active Directory moet worden gemaakt en ten minste één Power BI Pro-gebruikersaccount moet worden aangeschaft voor een gebruiker in die active directory. Deze gebruiker uitnodigen de juiste gebruikers naar de gedeelde organisatie. Bovendien in dit scenario, worden Contoso gebruikers behandeld als externe gebruikers wanneer zij in de gedeelde organisatie Power BI werken.

Het proces is als volgt:

1. De organisatie gedeeld wordt ingesteld als een nieuwe Azure Active Directory en ten minste één gebruikersaccount dat is gemaakt in de nieuwe organisatie. Deze gebruiker moet een Power BI Pro-licentie aan hen toegewezen hebben.
2. Deze gebruiker vervolgens maakt een Power BI-tenant en de vereiste gebruikers van Contoso en de partnerorganisatie wordt uitgenodigd. De gebruiker wordt ook vastgelegd voor alle gedeelde gegevens-activa, zoals Azure Analysis Services. Contoso en gebruikers van de Partner toegang tot de gedeelde organisatie Power BI als gastgebruikers. Als toegestaan om te bewerken en beheren van inhoud in Power BI kunnen voor de externe gebruikers Power BI thuis gebruiken, werkruimten, uploaden of bewerken, inhoud gebruiken en delen van rapporten. Normaal gesproken worden alle gedeelde assets opgeslagen en geopend in de organisatie gedeeld.
3. Afhankelijk van hoe de partijen komen overeen om samen te werken, is het mogelijk voor elke organisatie voor het ontwikkelen van hun eigen eigen gegevens en analyses met behulp van gedeelde gegevens datawarehouse activa. Ze kunnen distribueren die voor hun respectieve interne gebruikers met behulp van hun interne Power BI-tenants.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Voorbeeld 4: Distributie naar honderden of duizenden externe partners

Hoewel Contoso een rapport van de betrouwbaarheid straler voor één leverancier gemaakt, nu wenst Contoso te maken van een set met gestandaardiseerde rapporten voor honderden leveranciers. Hiermee kunt Contoso om te controleren of dat alle leveranciers de analytics die ze nodig hebben verbeteringen te maken of om op te lossen productie defecte producten hebben.

![Distributie naar veel partners](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Wanneer een organisatie nodig heeft om te distribueren gestandaardiseerde gegevens en inzichten om veel externe gebruikers/organisaties, kunnen ze het Ad-hoctaak of geplande delen van Power BI-Apps scenario gebruiken voor het bouwen van een BI-beheerportal, snel en zonder uitgebreide verlagen. De procedure voor het bouwen van dergelijke een portal met behulp van een Power BI-app wordt beschreven in de casestudy over: Het bouwen van een BI-Portal met behulp van Power BI + Azure AD B2B: Stapsgewijze instructies verderop in dit document.

Een algemene variant van deze aanvraag is bij een organisatie is een poging om inzichten te delen met gebruikers, met name bij het zoeken naar voor het gebruik van Azure B2C met Power BI. Power BI biedt geen systeemeigen ondersteuning voor Azure B2C. Als u opties voor deze aanvraag evalueren wilt, kunt u overwegen alternatieve optie 2 in de algemene alternatieve methoden de sectie verderop in dit document.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Casestudy: Het bouwen van een BI-Portal met behulp van Power BI + Azure AD B2B: Stapsgewijze instructies

Power BI integratie met Azure AD B2B biedt Contoso een naadloze en probleemloze manier gastgebruikers voorzien van beveiligde toegang tot de BI-beheerportal. Contoso kunt dit instellen met drie stappen:

![Het bouwen van een portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. BI-portal maken in Power BI

    De eerste taak voor Contoso is het maken van de BI-beheerportal in Power BI. Contoso BI-portal bestaan uit een verzameling van speciale dashboards en rapporten die beschikbaar wordt gesteld aan veel interne en Gast-gebruikers. De aanbevolen manier om dit te doen in Power BI is een Power BI-App. Meer informatie over [apps in Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Contoso BI-team maakt u een App-werkruimte in Power BI

    ![App-werkruimte](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Andere auteurs zijn toegevoegd aan de werkruimte

    ![Auteurs toevoegen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Inhoud wordt in de werkruimte gemaakt

    ![De inhoud van de werkruimte maken](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Nu dat de inhoud is gemaakt in een app-werkruimte, is Contoso klaar voor uitnodigen van gastgebruikers in partnerorganisaties om deze inhoud te gebruiken.

2. Gastgebruikers uitnodigen

    Er zijn twee manieren voor Contoso voor het uitnodigen van gastgebruikers ook kunnen tot de BI-beheerportal in Power BI:

    * Geplande uitnodigingen
    * Ad-hoc uitnodigingen

    **Geplande uitnodigingen**

    In deze benadering Contoso nodigt de gastgebruiker voor de Azure AD vooraf en distribueert vervolgens Power BI-inhoud toe. Contoso kunt uitnodigen van gastgebruikers ook kunnen vanuit de Azure portal of met behulp van PowerShell. Hier volgen de stappen voor het uitnodigen van gastgebruikers ook kunnen vanuit de Azure-portal:

    - Azure AD-beheerder van Contoso navigeert naar **Azure portal > Azure Active Directory > gebruikers en groepen > alle gebruikers > nieuwe gastgebruiker**

    ![Gastgebruiker](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Een uitnodigingsbericht voor de gastgebruikers toevoegen en klik op uitnodiging

    ![Uitnodiging toevoegen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Als u wilt uitnodigen van gastgebruikers ook kunnen vanuit de Azure-portal, moet u een administrator is voor de Azure Active Directory van uw tenant.

    Als u Contoso wil veel gastgebruikers uitnodigen, kunnen ze dit doen met behulp van PowerShell. Azure AD-beheerder van Contoso slaat de e-mailadressen van alle gastgebruikers in een CSV-bestand. Hier vindt u [Azure Active Directory B2B-samenwerkingscode en voorbeelden van PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) en instructies.

    Na de uitnodiging ontvangt gastgebruikers ook kunnen een e-mailbericht met de uitnodigingskoppeling.

    ![Uitnodigingskoppeling](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Zodra de gastgebruikers ook kunnen op de koppeling klikken, hebben ze toegang tot inhoud in de Contoso Azure AD-tenant.

    > [!NOTE]
    > Het is mogelijk om te wijzigen van de indeling van de uitnodiging per e-mail met behulp van de functie van Azure AD-huisstijl zoals beschreven [hier](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Ad-hoc uitnodigingen**

    Contoso weet wat gebeurt er als niet alle gastgebruikers die het bedrijf wil tevoren uitnodigen? Of, wat gebeurt er als de analist in Contoso die heeft gemaakt van de BI-portal voor het distribueren van inhoud naar gastgebruikers zichzelf wil? We ondersteunen ook in dit scenario in Power BI met ad-hocuitnodigingen.

    De analist kan alleen de externe gebruikers toevoegen aan de toegangslijst van de app wanneer ze worden gepubliceerd. De gastgebruikers haalt een uitnodiging en wanneer ze deze accepteert, wordt deze automatisch doorverwezen naar de Power BI-inhoud.

    ![Externe gebruiker toevoegen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Uitnodigingen zijn alleen de eerste keer dat een externe gebruiker is uitgenodigd voor uw organisatie nodig.


3. Inhoud distribueren

    Nu dat de Contoso-BI-team heeft gemaakt van de BI-portal en gastgebruikers uitgenodigd, kunnen ze hun-portal voor hun eindgebruikers distribueren door gastgebruikers toegang geven tot de app en deze publiceren. Power BI worden automatisch aangevuld namen van gastgebruikers die eerder zijn toegevoegd aan de Contoso-tenant. Ad-hoc uitnodigingen voor andere gastgebruikers kunnen ook op dit moment worden toegevoegd.

    > [!NOTE]
    > Als u beveiligingsgroepen voor het beheren van toegang tot de app voor externe gebruikers, geplande uitnodigingen benadering gebruiken en de koppeling app rechtstreeks met elke externe gebruiker die toegang moet hebben tot deze delen. Anders de externe gebruiker wellicht geen te installeren of uit binnen de app-inhoud weergeven. _

    Gastgebruikers krijgen een e-mailbericht met een koppeling naar de app.

    ![E-mailuitnodiging koppeling](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Op deze koppeling klikt, wordt gastgebruikers gevraagd om u te verifiëren met hun eigen organisatie-identiteit.

    ![Meld u aan pagina](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Zodra ze zijn geverifieerd, worden ze omgeleid naar de Contoso BI-app.

    ![Gedeelde inhoud bekijken](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Gastgebruikers ook kunnen toegang vervolgens hebt tot de Contoso-app door te klikken op de koppeling in het e-mailbericht of de koppeling bladwijzers. Contoso kan ook het eenvoudiger voor gastgebruikers ook kunnen door deze koppeling toe te voegen aan een bestaande extranet portal die al gebruikmaken van de gastgebruikers.

4. Volgende stappen

    Met behulp van een Power BI-app en de Azure AD B2B, kan Contoso snel een BI-Portal voor haar leveranciers op een manier zonder code te maken. Dit wordt sterk vereenvoudigd distribueren gestandaardiseerde analytics voor alle leveranciers die deze nodig hebt.

    Terwijl het voorbeeld hebt u geleerd hoe een enkele algemene rapport kan worden verdeeld over leveranciers, kan Power BI veel verder gaan. Om ervoor te zorgen voor dat elke partner ziet die alleen gegevens die relevant zijn voor zichzelf, kunnen de beveiliging op rijniveau eenvoudig worden toegevoegd aan het rapport en gegevens-model. De beveiliging van gegevens voor externe partners sectie verderop in dit document wordt beschreven in dit proces in details.

    Vaak afzonderlijke rapporten en dashboards moeten worden ingesloten in een bestaande portal. Dit kan ook worden bereikt dat veel van de technieken die wordt weergegeven in het voorbeeld. Echter, in dergelijke situaties het kan eenvoudiger zijn voor het insluiten van rapporten of dashboards rechtstreeks vanuit een werkruimte. Het proces voor het uitnodigen en het toewijzen van machtigingen aan de vereisen dat gebruikers blijven hetzelfde.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Achter de schermen: Wat is het Lucy van Supplier1 toegang kunnen krijgen tot Power BI-inhoud van het Contoso-tenant?

Nu dat we hebben gezien hoe Contoso kunnen naadloos distribueren Power BI-inhoud naar gastgebruikers in partnerorganisaties is, laten we kijken hoe dit achter de schermen werkt.

Bij Contoso uitgenodigd [ lucy@supplier1.com ](mailto:lucy@supplier1.com) naar de map, maakt Azure AD een koppeling tussen [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) en de Contoso Azure AD-tenant. Deze koppeling kunnen Azure AD weten dat Lucy@supplier1.com hebben toegang tot inhoud in de Contoso-tenant.

Wanneer Lucy probeert te krijgen van Power BI-app van Contoso, wordt Azure AD verifieert dat Lucy toegang heeft tot de Contoso-tenant en vervolgens Power BI een token die aangeeft geeft dat Lucy wordt geverifieerd voor toegang tot de inhoud van de Contoso-tenant. Power BI gebruikt dit token toe te staan en ervoor te zorgen dat Lucy toegang tot de Power BI-app van Contoso heeft.

![Verificatie en autorisatie](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI integratie met Azure AD B2B werkt met alle zakelijke e-mailadressen. Als de gebruiker beschikt niet over een Azure AD-identiteit, kunnen ze gevraagd een te maken. De volgende afbeelding ziet u de gedetailleerde stroom:

![Stroomdiagram voor integratie](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Het is belangrijk voor het herkennen van dat de Azure AD-account wordt gebruikt of in de externe partij gemaakt de Azure AD, deze maken het mogelijk dat Lucy haar eigen gebruikersnaam en wachtwoord gebruiken kunt en haar referenties automatisch niet meer zal werken in andere tenants wanneer ze het bedrijf verlaat bij haar organisatie maakt ook gebruik van Azure AD.

## <a name="licensing"></a>Licentieverlening

Contoso kunt een van drie methoden licentie gastgebruikers ook kunnen kiezen uit de leveranciers en partnerorganisaties toegang hebben tot de Power BI-inhoud.

> [!NOTE]
> _De gratis laag van de Azure AD B2B is voldoende zijn voor Power BI gebruiken met Azure AD B2B. Sommige geavanceerde Azure AD B2B-functies zoals dynamische groepen vereist aanvullende licenties. Raadpleeg de Azure AD B2B-documentatie voor meer informatie:_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Methode 1: Contoso maakt gebruik van Power BI Premium

Met deze methode Contoso koopt van Power BI Premium-capaciteit en de inhoud van de portal BI toegewezen aan deze capaciteit. Hiermee kunnen gastgebruikers van partnerorganisaties voor toegang tot Power BI-app van Contoso zonder een licentie voor Power BI.

Externe gebruikers zijn ook afhankelijk van het verbruik alleen ervaringen aan gebruikers van de 'Gratis' in Power BI aangeboden bij het gebruiken van inhoud in Power BI Premium.

Contoso kan ook profiteren van andere Power BI premium-mogelijkheden voor de apps, zoals verhoogde vernieuwingsfrequentie, toegewezen capaciteit en grote modellen.

![Aanvullende mogelijkheden](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Methode 2: Contoso Power BI Pro-licenties toegewezen aan gastgebruikers

Met deze methode, Contoso wijst de pro-licenties voor gastgebruikers van partner organisaties – dit kan worden gedaan vanuit Contoso van Microsoft 365-beheercentrum. Hiermee kunnen gastgebruikers van partnerorganisaties toegang krijgen tot Power BI-app van Contoso zonder het aanschaffen van een licentie zelf. Dit kan zijn geschikt voor het delen met externe gebruikers waarvan de organisatie heeft Power BI niet nog vastgesteld.

> [!NOTE]
> _Pro-licentie van Contoso is van toepassing op gastgebruikers wanneer ze toegang inhoud in de Contoso-tenant tot. Pro-licenties inschakelen toegang tot inhoud die zich niet in een Power BI Premium-capaciteit. Externe gebruikers met een Pro-licentie zijn echter standaard beperkt tot een ervaring bij het alleen. Dit kan worden gewijzigd met behulp van de benadering die wordt beschreven in de_ _zodat externe gebruikers bewerken en beheren van inhoud in Power BI_ _verderop in dit document._

![Licentie-informatie](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Methode 3: Gastgebruikers ook kunnen meenemen hun eigen Power BI Pro-licentie

Met deze methode wordt door leverancier 1 aan Lucy Power BI Pro-licentie toegewezen. Ze hebben vervolgens toegang tot Power BI-app van Contoso met deze licentie. Aangezien Lucy haar Pro-licentie van haar eigen organisatie gebruiken kunt bij het openen van een externe Power BI-omgeving, deze benadering wordt soms aangeduid als _hun eigen licentie mee_ (BYOL). Als beide organisaties Power BI gebruikt, wordt dit biedt voordeligste licentieverlening voor de algehele analyseoplossing voor en minimaliseert de overhead van licenties toewijzen aan externe gebruikers.

> [!NOTE]
> _De pro-licentie gegeven aan Lucy door leverancier 1 is van toepassing op een Power BI-tenant waar Lucy een gastgebruiker is. Pro-licenties inschakelen toegang tot inhoud die zich niet in een Power BI Premium-capaciteit. Externe gebruikers met een Pro-licentie zijn echter standaard beperkt tot een ervaring bij het alleen. Dit kan worden gewijzigd met behulp van de benadering die wordt beschreven in de_ _zodat externe gebruikers bewerken en beheren van inhoud in Power BI_ _verderop in dit document._

![Pro-licentie-vereisten](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Beveiliging van gegevens voor externe partners

Vaak als u werkt met meerdere externe leveranciers, moet de Contoso om ervoor te zorgen dat elke leverancier ziet die gegevens alleen over een eigen producten. Beveiliging op basis van gebruikers en dynamische beveiliging op rijniveau kunnen dit eenvoudig doen met Power BI.

### <a name="user-based-security"></a>Beveiliging op basis van gebruiker

Een van de krachtigste functies van Power BI is beveiliging op rijniveau. Deze functie kunt Contoso voor het maken van een rapport en gegevensset, maar andere beveiligingsregels voor elke gebruiker nog steeds van toepassing. Zie voor een uitgebreidere uitleg [beveiliging op rijniveau (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Power BI integratie met Azure AD B2B kunt Contoso om toe te wijzen op rijniveau regels voor gastgebruikers zodra ze zijn uitgenodigd voor de Contoso-tenant. Zoals we hebben gezien voordat Contoso gastgebruikers ook kunnen via een toevoegen kunt geplande of een ad-hocuitnodigingen. Als Contoso wil om af te dwingen van beveiliging op rijniveau, moet het is raadzaam geplande uitnodigingen gebruiken om toe te voegen de gastgebruikers ook kunnen voor tijd en ze toewijst aan de beveiligingsrollen voor het delen van de inhoud. Als in plaats daarvan maakt gebruik van Contoso ad-hocuitnodigingen, is er mogelijk een korte periode waarin de gastgebruikers ook kunnen zich niet kunnen geen gegevens zien.

> [!NOTE]
> Deze vertraging bij het openen van gegevens die door beveiliging op Rijniveau is beveiligd wanneer met behulp van ad-hoc uitnodigingen kan leiden tot ondersteuningsaanvragen naar uw IT-team omdat gebruikers zien leeg of verbroken op rapporten/dashboards Zoek bij het openen van een delen van een koppeling in het e-mailbericht ontvangen. Daarom ten zeerste aanbevolen het gebruik van geplande uitnodigingen in deze scenario.* *

Laten we eens kijken deze met een voorbeeld.

Zoals al eerder vermeld, Contoso leveranciers over de hele wereld heeft en ze willen er zeker van te zijn dat de gebruikers van hun organisaties leverancier inzicht in gegevens van alleen hun gebied krijgen.  Maar gebruikers van Contoso kunnen alle gegevens openen. In plaats van meerdere verschillende rapporten maken, Contoso maakt u een rapport en filters de gegevens op basis van de gebruiker weergeven.

![Gedeelde inhoud](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Om ervoor te zorgen dat Contoso kunt filteren op basis van wie er verbinding maakt, worden twee gebruikersrollen gemaakt in Power BI desktop. Een voor het filteren van alle gegevens van de SalesTerritory "Europa" en een ander voor 'Noord-Amerika'.

![Rollen beheren](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Wanneer er rollen zijn gedefinieerd in het rapport, moet een gebruiker worden toegewezen aan een specifieke functie voor hen toegang te krijgen tot gegevens. De toewijzing van rollen gebeurt in de Power BI-service ( **gegevenssets > beveiliging** )

![Beveiliging instellen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Hiermee opent u een pagina waar BI-team van Contoso de twee ziet rollen die ze zijn gemaakt.  BI-team van Contoso kan gebruikers nu toewijzen aan de rollen.

![Beveiliging op rijniveau](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

In het voorbeeld is Contoso het toevoegen van een gebruiker in een partnerorganisatie met e-mailadres "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)' aan de rol van Europa:

![Instellingen voor beveiliging op rijniveau](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Wanneer dit wordt opgelost door Azure AD, ziet Contoso met de naam weergegeven in het venster gereed om te worden toegevoegd:

![Functies weergeven](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Wanneer deze gebruiker de app die met hem is gedeeld opent, ziet hij alleen nu een rapport met gegevens van Europa:

![Inhoud weergeven](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Dynamische beveiliging op rijniveau

Er is een andere interessante onderwerp om te zien hoe dynamische op rijniveau (RLS) in combinatie met Azure AD B2B rij.

Kort gezegd, werkt dynamische beveiliging op rijniveau volgens het filteren van gegevens in het model op basis van de gebruikersnaam van de persoon die verbinding maken met Power BI. In plaats van het toevoegen van meerdere functies voor groepen gebruikers, kunt u de gebruikers definiëren in het model. Het patroon in detail Hier wordt niet beschreven. Kasper de Jong biedt een gedetailleerde schrijven tot in alle versies van beveiliging op rijniveau in [referentiemateriaal voor Power BI Desktop dynamische beveiliging](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/), en in [dit technisch document](https://msdn.microsoft.com/library/jj127437.aspx) .

Hier volgt een kleine voorbeeld: Contoso heeft een eenvoudig rapport op de verkoop door groepen:

![Voorbeelden voor inhoud](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Nu dit rapport moet worden gedeeld met twee gastgebruikers en een interne gebruiker: de interne gebruiker kan alles zien, maar de gastgebruikers ook kunnen zien alleen de groepen die hebben ze toegang. Dit betekent dat we de gegevens alleen voor de gastgebruikers moet filteren. Als u wilt filteren op de juiste wijze de gegevens, Contoso maakt gebruik van het patroon voor dynamische beveiliging op Rijniveau zoals beschreven in het technisch document en blog-bericht. Dit houdt in dat Contoso de gebruikersnamen toegevoegd aan de gegevens zelf:

![Beveiliging op Rijniveau gebruikers weergeven in de gegevens zelf](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Contoso maakt vervolgens het juiste gegevensmodel dat de gegevens op de juiste wijze met de juiste relaties worden gefilterd:

![Relevante gegevens worden weergegeven](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Als u wilt filteren van de gegevens automatisch op basis van die zich heeft aangemeld, moet Contoso een rol die wordt doorgegeven in de gebruiker die verbinding maken. In dit geval Contoso maakt u twee rollen: de eerste is de 'securityrole' waarmee de gebruikers-tabel met de huidige gebruikersnaam van de gebruiker is aangemeld bij Power BI (dit werkt ook voor gastgebruikers ook kunnen Azure AD B2B) worden gefilterd.

![Rollen beheren](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso maakt ook een andere "AllRole' voor de interne gebruikers die alles kunnen zien: deze rol heeft geen eventuele beveiligingspredicaat.

Na het uploaden van de Power BI desktop-bestand met de service, toewijzen Contoso gastgebruikers aan de 'SecurityRole' en de interne gebruikers aan de 'AllRole"

Nu, wanneer de gastgebruikers ook kunnen het rapport opent, ze ziet alleen verkopen van groep a

![Alleen van groep A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

In de matrix aan de rechterkant ziet u het resultaat van de functie USERNAME() of USERPRINCIPALNAME(), retourneren beide dat de gastgebruikers ook kunnen e-mailadres.

Nu de interne gebruiker opgehaald om te zien van alle gegevens:

![Alle gegevens die worden weergegeven](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Zoals u ziet, is dynamische beveiliging op Rijniveau werkt samen met interne of Gast gebruikers.

> [!NOTE]
> In dit scenario werkt ook bij het gebruik van een model in Azure Analysis Services. Meestal uw Azure Analysis-Service is verbonden met de dezelfde Azure AD als uw Power BI - in dat geval weet Azure Analysis Services ook de gastgebruikers uitgenodigd via Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Verbinding maken met on premises gegevensbronnen

Power BI biedt de mogelijkheid voor Contoso gebruikmaken van op lokale gegevensbronnen, zoals [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) of [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) rechtstreeks dank aan de [On-Premises gegevensgateway](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Het is zelfs mogelijk aan te melden op deze gegevensbronnen en de dezelfde referenties die zijn gebruikt met Power BI.

> [!NOTE]
> Bij het installeren van een gateway verbinding maken met uw Power BI-tenant, moet u een gebruiker binnen uw tenant heeft gemaakt. Externe gebruikers niet mogelijk een gateway installeren en verbinden met uw tenant. _

Voor externe gebruikers, dit wordt mogelijk meer gecompliceerde als de externe gebruikers zijn meestal niet bekend bij de on-premises AD. Power BI biedt een oplossing voor dit doordat beheerders van Contoso de externe gebruikersnamen toewijzen aan interne gebruikersnamen, zoals beschreven in [uw gegevensbron beheren - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Bijvoorbeeld, [ lucy@supplier1.com ](mailto:lucy@supplier1.com) kunnen worden toegewezen aan [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Gebruikersnamen toewijzen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Deze methode is prima als Contoso slechts een handvol gebruikers of heeft als Contoso alle externe gebruikers aan een enkele interne account toewijzen kunt. Voor complexere scenario's waar de gebruikers hun eigen referenties nodig, er is een meer geavanceerde benadering die gebruikmaakt van [aangepaste AD-kenmerken](https://technet.microsoft.com/library/cc961737.aspx) doen van de toewijzing, zoals beschreven in [uw gegevensbron beheren - Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Hierdoor kan de beheerder van Contoso voor het definiëren van een toewijzing voor elke gebruiker in uw Azure AD (ook externe B2B-gebruikers).  Deze kenmerken kunnen worden ingesteld via de AD-objectmodel, zodat Contoso kan de toewijzing op uitnodiging of een geplande uitgebracht volledig automatiseren met behulp van de scripts of code.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Inschakelen van externe gebruikers om te bewerken en beheren van inhoud in Power BI

Contoso kan externe gebruikers toestaan om inhoud binnen de organisatie inzenden zoals eerder in het binnen de organisatie bewerken en beheren van Power BI-inhoud sectie beschreven.

> [!NOTE]
> Als u wilt bewerken en beheren van inhoud in Power BI voor uw organisatie, moet de gebruiker een licentie voor Power BI Pro hebben in een andere werkruimte dan mijn werkruimte. Gebruikers Pro-licenties kunnen ophalen, zoals beschreven in the_ _Licensing__section van dit document._

De Power BI-beheerportal biedt de **externe gastgebruikers ook kunnen bewerken en beheren van inhoud in de organisatie toestaan** instellen in de Tenant-instellingen. De instelling is standaard ingesteld op uitgeschakeld, wat betekent dat externe gebruikers krijgen een beperkte ervaring voor alleen-lezen standaard. De instelling is van toepassing op gebruikers met UserType aan Gast is ingesteld in Azure AD. De volgende tabel beschrijft de problemen die gebruikers ondervinden, afhankelijk van hun UserType en hoe de instellingen zijn geconfigureerd.

| **Type van de gebruiker in Azure AD** | **Toestaan van externe gastgebruikers ook kunnen bewerken en beheren van inhoud instellen** | **Gedrag** |
| --- | --- | --- |
| Gast | Uitgeschakeld voor de gebruiker (standaard) | Per item verbruik alleen weergeven. Geeft alleen-lezen toegang tot rapporten, dashboards en apps wanneer deze wordt bekeken via een URL die is verzonden naar de gastgebruiker. Power BI-mobiel-apps bieden een alleen-lezen weergave voor de gastgebruiker. |
| Gast | Ingeschakeld voor de gebruiker | De externe gebruiker beschikt over toegang tot de volledige Power BI-ervaring, hoewel sommige functies niet beschikbaar zijn voor hen. De externe gebruiker moet aanmelden bij Power BI met behulp van de URL van de Power BI-Service met de tenantinformatie opgenomen. De gebruiker krijgt de Home-ervaring, een mijn werkruimte en op basis van machtigingen kunnen bladeren, weergeven en inhoud maken. </br></br> Power BI-mobiel-apps bieden een alleen-lezen weergave voor de gastgebruiker. |

> [!NOTE]
> Externe gebruikers in Azure AD kunnen ook worden ingesteld op UserType-lid. Dit wordt momenteel niet ondersteund in Power BI.

In de Power BI-beheerportal, wordt de instelling weergegeven in de volgende afbeelding.

![Beheerdersinstellingen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Gastgebruikers krijgen standaard alleen-lezen en die kunt bewerken en beheren van inhoud. De standaardwaarde is uitgeschakeld, wat betekent dat alle gastgebruikers hebben de alleen-lezen-ervaring. De Power BI-beheerder kan de instelling voor alle gastgebruikers ook kunnen in de organisatie of voor specifieke beveiligingsgroepen die zijn gedefinieerd in Azure AD inschakelen. In de volgende afbeelding wordt in de Power BI-beheerder van Contoso een beveiligingsgroep gemaakt in Azure AD voor het beheren van welke externe gebruikers kunnen bewerken en beheren van inhoud in de Contoso-tenant.

Om te helpen deze gebruikers zich aanmelden bij Power BI, deze met de Tenant-URL te verstrekken. Volg deze stap om de tenant-URL te zoeken.

1. Selecteer in de Power BI-service in het bovenste menu help ( **?** ) vervolgens **over Power BI**.
2. Zoek naar de waarde naast **Tenant-URL**. Dit is de tenant-URL die u met uw gastgebruikers delen kunt.

    ![Tenant-URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Wanneer u de externe gastgebruikers toestaan om te bewerken en beheren van inhoud in de organisatie, wordt de opgegeven gastgebruikers ook kunnen toegang krijgen tot Power BI voor uw organisatie en Zie inhoud waartoe ze machtigingen hebben. Ze kunnen toegang krijgen tot start, blader en inhoud voor werkruimten inzenden, installeren apps waar ze zich in de lijst en hebben een mijn werkruimte. Ze kunnen een beheerder maken of zijn voor werkruimten waarvoor de nieuwe werkruimte-ervaring wordt gebruikt.

> [!NOTE]
> Wanneer u deze optie Zorg ervoor dat u de governance-sectie van dit document bekijken omdat de standaardinstellingen van Azure AD te voorkomen dat gastgebruikers ook kunnen voor het gebruik van bepaalde functies zoals mensen kleurenkiezer wat tot een lagere experience.* leiden kunnen *

Voor gastgebruikers ook kunnen via de externe gastgebruikers ook kunnen toestaan om te bewerken en beheren van inhoud in de instelling van de organisatie-tenant wordt ingeschakeld, zijn niet sommige ervaringen die voor hen beschikbaar. Als u wilt bijwerken of rapporten publiceren, moeten gastgebruikers ook kunnen gebruiken de Power BI-service-Webgebruikersinterface, met inbegrip van gegevens ophalen om Power BI Desktop-bestanden te uploaden. De volgende ervaringen worden niet ondersteund:

- Rechtstreeks publiceren van Power BI Desktop naar de Power BI-service
- Gastgebruikers kunnen geen gebruikmaken van Power BI Desktop om verbinding te maken met servicegegevenssets in de Power BI-service
- Klassieke werkruimten die aan Office 365-groepen zijn gekoppeld: Gastgebruikers kunnen geen beheerders van deze werkruimten maken of zijn. Ze kunnen alleen leden zijn.
- Ad-hocuitnodigingen verzenden wordt niet ondersteund voor toegangslijsten van werkruimten
- Power BI Publisher voor Excel wordt niet ondersteund voor gastgebruikers
- Gastgebruikers kunnen geen Power BI Gateway installeren of deze aan uw organisatie koppelen
- Gastgebruikers kunnen geen apps installeren en naar de hele organisatie publiceren
- Gastgebruikers kunnen geen organisatie-inhoudspakketten gebruiken, maken, bijwerken of installeren
- Gastgebruikers kunnen niet analyseren in Excel
- Gastgebruikers kunnen niet worden @mentioned in opmerkingen (deze functionaliteit wordt toegevoegd in een toekomstige release)
- Gastgebruikers abonnementen (deze functionaliteit wordt toegevoegd in een toekomstige release) niet gebruiken
- Gastgebruikers die deze mogelijkheid gebruiken, moeten over een werk- of schoolaccount beschikken. Gastgebruikers met behulp van persoonlijke accounts zich meer beperkingen vanwege beperkingen voor aanmelden.



## <a name="governance"></a>Governance

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Aanvullende instellingen voor Azure AD die invloed hebben op ervaringen in Power BI met betrekking tot Azure AD B2B

Wanneer u Azure AD B2B-delen, bepaalt de Azure Active Directory-beheerder aspecten van de ervaring van de externe gebruiker. Deze worden beheerd op de pagina van de instellingen voor externe samenwerking binnen de Azure Active Directory-instellingen voor uw Tenant.

Meer informatie over de instellingen die zijn hier beschikbaar:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Standaard de machtigingen van gastgebruikers zijn beperkt optie is ingesteld op Ja, zodat u gastgebruikers ook kunnen in Power BI beperkt ervaringen met name rondom delen waarbij personen selecteren gebruikersinterfaces niet werken voor gebruikers. Het is belangrijk om te werken met uw Azure AD-beheerder in te stellen op Nee, zoals hieronder wordt weergegeven om te controleren of een goede experience.* *

![Instellingen voor externe samenwerking](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Besturingselement Gast uitnodigingen

Power kunnen BI beheerders extern delen voor Power BI door naar de Power BI-beheerportal te gaan. Maar tenantbeheerders kunnen ook bepalen voor het extern delen met verschillende Azure AD-beleidsregels.  Met dit beleid kan tenant-beheerders

- Uitnodigingen door eindgebruikers uitschakelen
- Alleen beheerders en gebruikers in de rol Gastuitnodiging kunnen uitnodigingen versturen
- Beheerders, de rol Gastuitnodiging en leden kunnen uitnodigingen versturen
- Alle gebruikers, inclusief gasten, kunnen uitnodigingen versturen

U kunt meer lezen over deze beleidsregels in [uitnodigingen voor Azure Active Directory B2B-samenwerking delegeren](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Alle Power BI-acties van externe gebruikers zijn ook [gecontroleerd in onze controle portal](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Beleid voor voorwaardelijke toegang voor gastgebruikers

Contoso kan afdwingen van beleid voor voorwaardelijke toegang voor gastgebruikers die toegang inhoud van de Contoso-tenant tot. U vindt gedetailleerde instructies in [voorwaardelijke toegang voor gebruikers van B2B-samenwerking](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Algemene alternatieve methoden

Azure AD B2B kunt u eenvoudig gegevens en rapporten delen tussen verschillende organisaties, maar er zijn verschillende andere manieren die vaak worden gebruikt en superieure in bepaalde gevallen kunnen zijn.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Alternatieve optie 1: Dubbele identiteiten voor partner gebruikers maken

Met deze optie heeft Contoso dubbele id's voor elke partnergebruiker handmatig maken in de Contoso-Tenant, zoals wordt weergegeven in de volgende afbeelding. Klik vervolgens in Power BI, kunt Contoso delen met de toegewezen identiteiten de juiste rapporten, dashboards of apps.

![Juiste toewijzingen en namen in te stellen](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Redenen om deze alternatieve werkwijze kiezen:

- Omdat de identiteit van de gebruiker wordt beheerd door uw organisatie, alle verwante service, zoals e-mail, SharePoint, enzovoort, zijn ook controle van uw organisatie. Uw IT-beheerders kunnen wachtwoorden opnieuw instellen, de toegang tot accounts uitschakelen of activiteiten in deze services controleren.
- Gebruikers die persoonlijke accounts gebruiken voor hun bedrijf vaak worden beperkt tot bepaalde services mogelijk moet dus een organisatie-account.
- Sommige services werken alleen op gebruikers van uw organisatie. Bijvoorbeeld, met behulp van Intune voor het beheren van inhoud op de persoonlijke/mobile-apparaten van externe gebruikers met behulp van Azure B2B niet mogelijk.

Redenen niet aan deze alternatieve werkwijze kiezen:

- Gebruikers van partnerorganisaties moet twee sets met referenties: één voor toegang tot inhoud van hun eigen organisatie en de andere voor toegang tot inhoud van Contoso. Dit is een inspanningen voor deze gastgebruikers en veel gastgebruikers ook kunnen worden verward met deze ervaring.
- Contoso moet aanschaffen en gebruikerslicenties toewijzen aan deze gebruikers. Als een gebruiker moet het e-mailbericht ontvangt of office-toepassingen gebruiken, moeten ze de juiste licenties, met inbegrip van Power BI Pro om te bewerken en delen van inhoud in Power BI.
- Contoso wil strengere autorisatie en governancebeleid voor externe gebruikers in vergelijking met interne gebruikers afdwingen. Om dit te bereiken, Contoso moet maken van een interne naamgeving voor externe gebruikers en alle Contoso-gebruikers moeten worden over deze naamgeving te gaan.
- Wanneer de gebruiker de organisatie verlaat, ze blijven toegang houden tot resources van Contoso totdat de Contoso-beheerder hun account voor het handmatig verwijdert
- Contoso-beheerders hebben voor het beheren van de identiteit voor de Gast, met inbegrip van het maken, wachtwoord opnieuw instellen van wachtwoorden, enzovoort.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Alternatieve optie 2: Een aangepaste Power BI Embedded-toepassing met behulp van aangepaste verificatie maken

Een andere optie voor Contoso is het bouwen van een eigen aangepaste ingesloten Power BI-toepassing met aangepaste verificatie (['App is eigenaar van gegevens'](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Hoewel veel organisaties geen tijd of resources om te maken van een aangepaste toepassing voor het distribueren van Power BI-inhoud naar hun externe partners, voor sommige organisaties dit is de aanbevolen aanpak en verdient ernstige overweging.

Organisaties hebben vaak, bestaande partnerportals die toegang tot alle resources van de organisatie voor partners centraliseren, bieden isolatie van resources van de organisatie van de interne en gestroomlijnde ervaring voor partners om u te veel partners ondersteuning bieden en de afzonderlijke gebruikers.

![Veel partnerportals](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

In het voorbeeld hierboven gebruikers van elke leverancier-aanmelding voor Contoso Partner-Portal die gebruikmaakt van AAD als id-provider. Het kan AAD B2B, Azure B2C, systeemeigen identiteiten gebruiken of federeren met een willekeurig aantal andere id-providers. De gebruiker wilt aanmelden en toegang tot een partner portal-build met behulp van Azure-Web-App of een vergelijkbare infrastructuur.

Power BI-rapporten zijn binnen de web-app ingesloten in een implementatie van Power BI Embedded. De web-app zou stroomlijnen de toegang tot de rapporten en alle gerelateerde services in een samenhangend ervaring die gericht zijn om gemakkelijk voor leveranciers, om te communiceren met Contoso. In deze portal omgeving zou worden geïsoleerd van de interne AAD van Contoso en interne Power BI-omgeving van Contoso om ervoor te zorgen leveranciers heeft geen toegang tot deze resources. Normaal gesproken zou gegevens worden opgeslagen in een afzonderlijke Partner datawarehouse om isolatie van gegevens te garanderen. Deze isolatie biedt voordelen omdat deze wordt beperkt door het aantal externe gebruikers met directe toegang tot gegevens van uw organisatie, te beperken welke gegevens mogelijk niet beschikbaar voor de externe gebruiker en onopzettelijk wordt gedeeld met externe gebruikers te beperken.

Met behulp van Power BI Embedded, de portal kan gebruikmaken van voorkeur licentieverlening, met behulp van app-token of de hoofdgebruiker plus premium-capaciteit die is gekocht op Azure-model, vereenvoudigt de bezorgdheid over het toewijzen van licenties aan eindgebruikers, waardoor kan opschalen/omlaag op basis van op verwacht het gebruik. De portal kan bieden een algemene hogere kwaliteit en een consistente ervaring omdat partners toegang één portal met alle van de behoeften van de Partner waarmee u rekening moet worden ontworpen tot. Ten slotte, omdat Power BI Embedded op basis van oplossingen meestal ontworpen zijn om te worden meerdere tenants, het eenvoudiger om isolatie tussen partnerorganisaties te garanderen.

Redenen om deze alternatieve werkwijze kiezen:

- Gemakkelijker te beheren als het aantal partnerorganisaties groeit. Aangezien partners worden toegevoegd aan een afzonderlijke map geïsoleerd van de interne AAD-directory van Contoso, het vereenvoudigt de governance taken en helpt voorkomen dat onbedoeld delen van interne gegevens naar externe gebruikers.
- Typische Partnerportals zijn zeer merkproducten ervaringen met consistente ervaring voor partners en gestroomlijnd om te voldoen aan de behoeften van de typische partners. Contoso kan daarom een betere algehele ervaring bieden aan partners door alle benodigde services integreren in een centrale portal.
- Licentiekosten voor geavanceerde scenario's zoals de inhoud bewerken in de Power BI Embedded wordt gedekt door de Azure Power BI Premium aangeschaft en geen toewijzing van Power BI Pro-licenties aan deze gebruikers vereist.
- Biedt betere isolatie tussen partners als ontworpen als een oplossing voor meerdere tenants.
- De Partner-Portal bevat vaak andere hulpprogramma's voor partner buiten Power BI-rapporten, dashboards en apps.

Redenen niet aan deze alternatieve werkwijze kiezen:

- Aanzienlijke inspanningen is vereist voor het bouwen, te gebruiken en te onderhouden die een portal waardoor het een aanzienlijke investering in resources en -tijd.
- Tijd tot oplossing is veel langer is dan het gebruik van B2B-delen sinds zorgvuldige planning en uitvoering in meerdere IORP is vereist.
- Wanneer er een kleiner aantal partners is waarschijnlijk het werk dat nodig is voor deze alternatieve werkwijze te hoog is om te rechtvaardigen.
- Samenwerking met het ad-hoc delen is het primaire scenario geconfronteerd door uw organisatie.
- De rapporten en dashboards worden voor elke partner verschillen. Deze alternatieve werkwijze introduceert management overhead dan alleen het delen van rechtstreeks met Partners.



## <a name="faq"></a>Veelgestelde vragen

**Contoso een uitnodiging kunt verzenden die automatisch wordt ingewisseld, zodat de gebruiker alleen 'klaar is voor gebruik '? Of de gebruiker altijd hoeft door te klikken op de URL voor inschrijving?**

De eindgebruiker moet altijd klikken op via de toestemming voordat ze krijgen inhoud tot toegang.

Als u van gastgebruikers ook kunnen veel uitnodigen raden wij aan dat u dit van uw beheerders core Azure AD door delegeren [gebruiker toe te voegen aan de rol gastuitnodiging in de bronorganisatie](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Deze gebruiker kan andere gebruikers in de andere organisatie uitnodigen met behulp van de aanmelding-gebruikersinterface, PowerShell-scripts of API's. Dit vermindert de administratieve last van uw Azure AD-beheerders voor het uit te nodigen of opnieuw uitnodigingen verzonden naar gebruikers van de partnerorganisatie.

**Kan Contoso multi-factor authentication voor gastgebruikers dwingen als haar partners geen meervoudige verificatie?**

Ja. Zie voor meer informatie, [voorwaardelijke toegang voor gebruikers van B2B-samenwerking](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Hoe werkt B2B-samenwerking wanneer de uitgenodigde partner federation om toe te voegen van hun eigen on-premises verificatie?**

Als de partner een Azure AD-tenant die is gefedereerd naar de on-premises infrastructuur voor verificatie heeft, on-premises eenmalige aanmelding (SSO) automatisch bereikt. Als de partner niet over een Azure AD-tenant, kan een Azure AD-account worden gemaakt voor nieuwe gebruikers.

**Kan ik gastgebruikers met consumenten-e-mailaccounts uitnodigen?**

Uitnodigen van gastgebruikers met consumenten-e-mailaccounts wordt ondersteund in Power BI. Dit geldt ook voor domeinen, zoals hotmail.com, outlook.com en gmail.com. Echter die gebruikers kunnen ondervinden beperkingen dan wat gebruikers met werk of schoolaccounts optreden.
