---
title: Inhoud van de Power BI-werkruimteverzameling migreren naar Power BI
description: Informatie over het migreren van Power BI-werkruimteverzameling naar Power BI Embedded en hoe u gebruikmaakt van ontwikkelingen voor het insluiten van inhoud in apps.
author: KesemSharabi
ms.author: kesharab
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 06/30/2018
ms.openlocfilehash: f3f76bd7c422d07cb2b390c2aebd92a2d7fe4ef3
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91749041"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>Inhoud van de Power BI-werkruimteverzameling migreren naar Power BI Embedded

Informatie over het migreren van Power BI-werkruimteverzameling naar Power BI Embedded en hoe u gebruikmaakt van ontwikkelingen voor het insluiten van inhoud in apps.

Microsoft [introduceerde recentelijk Power BI Embedded](https://powerbi.microsoft.com/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/), een nieuw, op capaciteit gebaseerd licentiemodel met meer flexibiliteit voor het openen, delen en distribueren van inhoud. De aanbieding zorgt ook voor hogere schaalbaarheid en verbeterde prestaties.

Met Power BI Embedded beschikt u over één API-gebied, een consistente set mogelijkheden en toegang tot de nieuwste functies van Power BI (zoals dashboards, gateways en werkruimten) wanneer u uw inhoud insluit. Als u verder gaat, kunt u starten met Power BI Desktop en overstappen op implementatie met Power BI Embedded.

De huidige Power BI-werkruimteverzameling blijft beschikbaar gedurende een beperkte periode. Klanten die werken onder een Enterprise Agreement hebben toegang tot en met de vervaldatum van hun bestaande overeenkomsten; klanten die Power BI-werkruimteverzameling hebben verkregen via directe of CSP-kanalen behouden toegang tot één jaar na de release van de algemene beschikbaarheid van Power BI Embedded.  In dit artikel vindt u enkele richtlijnen voor het migreren van inhoud van Power BI-werkruimteverzameling naar de nieuwe Power BI Embedded-ervaring en welke wijzigingen u kunt verwachten in uw toepassing.

> [!IMPORTANT]
> Hoewel de migratie afhankelijk is van Power BI Embedded, zijn de gebruikers van uw toepassing niet afhankelijk van Power BI als deze een **insluittoken** gebruiken. Ze hoeven zich niet aan te melden voor Power BI om de ingesloten inhoud in uw toepassing te bekijken. U kunt deze aanpak voor insluiten gebruiken voor Embedded-gebruikers die niet beschikken over Power BI.

![Stroom insluiten](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

Voordat u aan de slag gaat met de migratie naar de nieuwe Power BI Embedded, kunt u snel een overzicht raadplegen voor hulp bij het instellen van uw nieuwe Power BI Embedded-omgeving met het [instelprogramma voor insluiten](https://aka.ms/embedsetup).

Kies de oplossing die het beste bij u past:
* **Insluiten voor uw klanten**: wanneer u geïnteresseerd bent in een oplossing [waarbij de app eigenaar van de gegevens is](https://aka.ms/embedsetup/AppOwnsData). [Door inhoud voor uw klanten in te sluiten](embedding.md#embedding-for-your-customers) kunt u dashboards en rapporten insluiten voor gebruikers die geen account voor Power BI hebben. 

* **Insluiten voor uw organisatie**: wanneer u geïnteresseerd bent in een oplossing [waarbij de gebruiker eigenaar van de gegeven is](https://aka.ms/embedsetup/UserOwnsData). [Met het insluiten van inhoud voor uw organisatie](embedding.md#embedding-for-your-organization) kunt u de Power BI-service uitbreiden.

## <a name="prepare-for-the-migration"></a>Voorbereiden voor de migratie

Er zijn enkele dingen die u moet doen om inhoud voor te bereiden op een migratie van Power BI-werkruimteverzameling naar Power BI Embedded. U moet een tenant hebben die beschikbaar is en een gebruiker die een licentie voor Power BI Pro heeft.

1. Controleer of u toegang hebt tot een Azure AD-tenant (Azure Active Directory).

    U moet bepalen welk tenant-instelling u wilt gebruiken.

   * Wilt u de bestaande Power BI-tenant van uw bedrijf gebruiken?
   * Wilt u een afzonderlijke tenant voor uw toepassing gebruiken?
   * Wilt u voor elke klant een andere tenant gebruiken?

     Als u een nieuwe tenant voor uw toepassing wilt maken, of een voor elke klant, bekijk dan [Een Azure Active Directory-tenant maken](create-an-azure-active-directory-tenant.md) of [Een Azure Active Directory-tenant verkrijgen](/azure/active-directory/develop/active-directory-howto-tenant) voor meer informatie.
2. Maak een gebruiker binnen deze nieuwe tenant die gaat fungeren als het ‘masteraccount’ van uw toepassing. Dit account moet zich aanmelden voor Power BI en moet beschikken over een Power BI Pro-licentie.

## <a name="accounts-within-azure-ad"></a>Accounts in Azure AD

De volgende accounts moet binnen uw tenant aanwezig zijn.

> [!NOTE]
> Deze accounts moeten over Power BI Pro-licenties beschikken om werkruimten te kunnen gebruiken.

1. Een Power BI-beheerder.

    Het wordt aanbevolen dat deze gebruiker lid is van alle werkruimten die worden gemaakt voor het insluiten van inhoud.

2. Accounts voor analisten die inhoud maken.

    Deze gebruikers moeten waar nodig worden toegewezen aan werkruimten.

3. Een *masteraccount* of Embedded-account voor de toepassing.

    De referenties voor dit account worden opgeslagen op de back-end van de toepassing en gebruikt voor het verkrijgen van een Azure AD-token voor de Power BI REST API's. Dit account wordt gebruikt voor het genereren van een insluittoken voor de toepassing. Dit account moet ook een beheerder zijn van de werkruimten die zijn gemaakt voor het insluiten van inhoud.

> [!NOTE]
> Dit is een normaal gebruikersaccount in uw organisatie dat wordt gebruikt voor het insluiten van inhoud.

## <a name="app-registration-and-permissions"></a>Registratie en machtigingen voor de app

U moet een toepassing in Azure AD registreren en bepaalde machtigingen verlenen.

### <a name="register-an-application"></a>Een toepassing registreren

U moet uw toepassing registreren bij Azure AD om REST-API-aanroepen te kunnen uitvoeren. Hierbij moet u naar de Azure portal gaan om een aanvullende configuratie toe te passen, naast de registratiepagina van de Power BI-app. Zie [Een Azure AD-app voor het insluiten van Power BI-inhoud registreren](register-app.md) voor meer informatie.

U moet de toepassing die gebruikmaakt van het **masteraccount** registreren.

## <a name="create-workspaces-required"></a>Werkruimten maken (vereist)

U kunt werkruimten gebruiken voor betere isolatie wanneer uw toepassing wordt gebruikt door meerdere klanten. Dashboards en rapporten zijn dan per klant geïsoleerd. U kunt vervolgens een Power BI-account per werkruimte gebruiken om het gebruik van de toepassing door de verschillende klanten verder te isoleren.

> [!IMPORTANT]
> U kunt een persoonlijke werkruimte niet gebruiken om inhoud in te sluiten voor gebruikers die niet over Power BI beschikken.

U hebt een gebruiker nodig die een Pro-licentie heeft om een werkruimte in Power BI te kunnen maken. De Power BI-gebruiker die de werkruimte maakt, wordt standaard een beheerder van deze werkruimte.

> [!NOTE]
> Het *masteraccount* van de toepassing moet een beheerder zijn van de werkruimte.

## <a name="content-migration"></a>Inhoud migreren

U kunt de inhoud van uw werkruimteverzamelingen naar Power BI Embedded parallel met uw huidige oplossing migreren. Hiervoor is geen uitvaltijd vereist.

U kunt een **hulpprogramma voor migratie** gebruiken om u te helpen bij het kopiëren van inhoud van Power BI-werkruimteverzameling naar Power BI Embedded. Met name als u veel inhoud hebt. Zie [Hulpprogramma voor migratie in Power BI Embedded](migrate-tool.md) voor meer informatie.

Het migreren van inhoud gebeurt hoofdzakelijk via twee API's.

1. Download PBIX: deze API kan PBIX-bestanden downloaden die na oktober 2016 zijn geüpload naar Power BI.
2. Import PBIX: deze API kan elk type PBIX-bestand uploaden naar Power BI.

Zie [Codefragmenten voor het migreren van inhoud in Power BI-werkruimteverzameling](migrate-code-snippets.md) voor een aantal gerelateerde codefragmenten.

### <a name="report-types"></a>Rapporttypen

Er zijn verschillende soorten rapporten en voor elk rapport is een enigszins verschillende migratiestroom vereist.

#### <a name="cached-dataset--report"></a>In het cachegeheugen opgeslagen gegevensset en rapport

In het cachegeheugen opgeslagen gegevenssets verwijzen naar PBIX-bestanden die gegevens in plaats van een live verbinding of DirectQuery-verbinding hebben geïmporteerd.

**Stroom**

1. Roep de Download PBIX API aan vanuit de PaaS-werkruimte.
2. Sla de PBIX op.
3. Roep de Import PBIX aan in de SaaS-werkruimte.

#### <a name="directquery-dataset--report"></a>DirectQuery-gegevensset en -rapport

**Stroom**

1. Roep GET `https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources` aan en sla de ontvangen verbindingsreeks op.
2. Roep de Download PBIX API aan vanuit de PaaS-werkruimte.
3. Sla de PBIX op.
4. Roep de Import PBIX aan in de SaaS-werkruimte.
5. Verbindingsreeks bijwerken door aanroepen - POST `https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections`
6. GW-id en gegevensbron-id ophalen door aanroepen - GET `https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources`
7. Referenties van gebruiker bijwerken door aanroepen - PATCH `https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}`

#### <a name="old-dataset--reports"></a>Oude gegevensset en rapport

Dit zijn gegevenssets/rapporten die zijn gemaakt vóór oktober 2016. Download PBIX biedt geen ondersteuning voor PBIX-bestanden die vóór oktober 2016 zijn geüpload

**Stroom**

1. Haal een PBIX-bestand op uit uw ontwikkelomgeving (uw interne bronbeheer).
2. Roep de Import PBIX aan in de SaaS-werkruimte.

#### <a name="push-dataset--report"></a>Pushgegevensset en rapport

Download PBIX biedt geen ondersteuning voor *Push API*-gegevenssets. Push API-gegevenssets kunnen niet worden overgezet van PaaS naar SaaS.

**Stroom**

1. Roep de Create dataset API aan met de gegevensset Json om een gegevensset te maken in de SaaS-werkruimte.
2. Maak het rapport voor de gemaakte gegevensset opnieuw*.

Er zijn een aantal tijdelijke oplossingen waarmee u het rapport van de Push API toch kunt migreren van PaaS naar SaaS. Probeer hiervoor het volgende.

1. Upload een PBIX-bestand bij wijze van test naar de PaaS-werkruimte.
2. Kloon het Push API-rapport en koppel het aan het PBIX-testbestand uit stap 1.
3. Download het Push API-rapport met het PBIX-testbestand.
4. Upload het PBIX-testbestand naar uw SaaS-werkruimte.
5. Maak een pushgegevensset in de SaaS-werkruimte.
6. Koppel het rapport opnieuw aan de Push API-gegevensset.

## <a name="create-and-upload-new-reports"></a>Nieuwe rapporten maken en uploaden

U kunt niet alleen inhoud migreren van de Power BI-werkruimteverzameling, maar ook rapporten en gegevenssets maken met Power BI Desktop en deze rapporten vervolgens publiceren naar een werkruimte. De eindgebruiker die de rapporten naar een werkruimte publiceert, moet beschikken over een Power BI Pro-licentie.

## <a name="rebuild-your-application"></a>Uw toepassing opnieuw bouwen

1. U moet uw toepassing wijzigen met de Power BI REST-API's en de rapportlocatie in powerbi.com.
2. Maak uw AuthN/AuthZ-verificatie opnieuw met behulp van het *masteraccount* voor uw toepassing. U een [insluittoken](/rest/api/power-bi/embedtoken) gebruiker om deze gebruiker te machtigen om te handelen namens andere gebruikers.
3. Sluit uw rapporten uit powerbi.com in uw toepassing in.

## <a name="map-your-users-to-a-power-bi-user"></a>Uw gebruikers toewijzen aan een Power BI-gebruiker

In uw toepassing wijst u gebruikers die u in de toepassing naar beheert toe aan een *masterreferentie* van Power BI voor uw toepassing. De referenties voor dit *masteraccount* van Power BI worden opgeslagen in uw toepassing en worden gebruikt voor het maken van insluittokens.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Wat u moet doen wanneer u klaar bent voor productie

Wanneer u klaar bent voor de productie, moet u het volgende te doen.

* Als u een afzonderlijke tenant voor ontwikkeling gebruikt, moet u ervoor zorgen dat de werkruimten, dashboards en rapporten beschikbaar zijn in uw productieomgeving. Bovendien moet u de toepassing maken voor uw productietenant in Azure AD en de juiste app-machtigingen toewijzen, zoals aangegeven in stap 1.
* Koop de capaciteit die past bij uw behoeften. Bekijk het [technisch document over capaciteitsplanning voor Power BI Embedded-analyses](./embedded-capacity-planning.md) voor meer inzicht in de hoeveelheid en het type capaciteit dat u nodig hebt. U kunt [capaciteit kopen](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) in Azure.
* Bewerk de werkruimte en wijs deze toe aan een Premium-capaciteit onder Geavanceerd.

    ![Premium-capaciteit](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)

* Implementeer uw bijgewerkte toepassing naar productie en begin met het insluiten van rapporten uit de Power BI Embedded.

## <a name="after-migration"></a>Na de migratie

Het is aan te raden om op te ruimen in Azure.

* Verwijder alle werkruimten uit de geïmplementeerde oplossing in de Azure Embedded van Power BI-werkruimteverzameling.
* Verwijder eventuele werkruimteverzamelingen die zijn opgeslagen in Azure.

## <a name="next-steps"></a>Volgende stappen

[Insluiten met Power BI](embedding.md)  
[Migratieprogramma voor Power BI-werkruimteverzameling](migrate-tool.md)  
[Codefragmenten voor het migreren van inhoud van Power BI-werkruimteverzameling](migrate-code-snippets.md)  
[Dashboards, rapporten en tegels van Power BI insluiten](embed-sample-for-your-organization.md)  
[Power BI Premium - wat is het?](../../admin/service-premium-what-is.md)  
[Git-opslagplaats voor JavaScript-API](https://github.com/Microsoft/PowerBI-JavaScript)  
[Git-opslagplaats voor Power BI C#](https://github.com/Microsoft/PowerBI-CSharp)  
[Voorbeeld van het insluiten van JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Technisch document over analysecapaciteitsplanning voor Power BI-werkruimteverzameling](./embedded-capacity-planning.md)  
[Technisch document over Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  

Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).