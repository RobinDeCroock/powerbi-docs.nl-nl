---
title: Verbinding maken met GitHub via Power BI
description: GitHub voor Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/25/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 1be2d3db9dbf341def86c087344ef7a32cd006a0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337714"
---
# <a name="connect-to-github-with-power-bi"></a>Verbinding maken met GitHub via Power BI
In dit artikel wordt uitgelegd hoe u uw gegevens ophaalt uit uw GitHub-account met een Power BI-sjabloon-app. De sjabloon-app genereert een werkruimte met een dashboard, een set rapporten en een gegevensset waarmee u uw GitHub-gegevens kunt verkennen. De GitHub-app voor Power BI maakt het mogelijk om inzicht te verkrijgen in een GitHub-opslagplaats (ook wel een repository of repo genoemd) met gegevens van bijdragen, problemen, pull-aanvragen en actieve gebruikers.

Nadat u de sjabloon-app hebt geïnstalleerd, kunt u het dashboard en rapport wijzigen. Vervolgens kunt u deze als een app distribueren naar collega's in uw organisatie.

Maak verbinding met de [GitHub-sjabloon-app](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github) of lees meer over de [integratie van GitHub](https://powerbi.microsoft.com/integrations/github) met Power BI.

U kunt ook de [zelfstudie voor GitHub](service-tutorial-connect-to-github.md) gebruiken. Hiermee worden echte GitHub-gegevens over de openbare opslagplaats voor de Power BI-documentatie geïnstalleerd.

>[!NOTE]
>Deze sjabloon-app werkt alleen als het GitHub-account toegang heeft tot de opslagplaats. Meer informatie over de vereisten volgt hieronder.
>
>Deze sjabloon-app biedt geen ondersteuning voor GitHub Enterprise. 

## <a name="how-to-connect"></a>Verbinding maken
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]
   
3. Selecteer **GitHub** \> **Nu downloaden**.
4. Selecteer in **Deze Power BI-app installeren?** de optie **Installeren**.
4. Selecteer in het deelvenster **Apps** de tegel **GitHub**.

    ![Power BI GitHub-tegel](media/service-connect-to-github/power-bi-github-tile.png)

6. Selecteer in **Aan de slag met uw nieuwe app** de optie **Verbinding maken**.

    ![Aan de slag met uw nieuwe app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

5. Voer de naam in van de opslagplaats en de naam van de eigenaar van de opslagplaats. Hieronder vindt u informatie over [het vinden van deze parameters](#FindingParams).
   
    ![Naam Power BI GitHub-opslagplaats](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Geef uw referenties voor GitHub op (deze stap kan worden overgeslagen als u al bent aangemeld in uw browser). 
6. Selecteer bij **Verificatiemethode** de optie **oAuth2** \>**Aanmelden**. 
7. Volg de verificatie-instructies van GitHub. Verleen de GitHub-sjabloon-app voor Power BI machtiging voor de GitHub-gegevens.
   
   ![Power BI GitHub autoriseren](media/service-connect-to-github/github_authorize.png)
   
    Power BI maakt verbinding met GitHub en uw gegevens.  De gegevens worden eenmaal per dag vernieuwd. Nadat de gegevens zijn geïmporteerd in Power BI, wordt de inhoud van uw nieuwe GitHub-werkruimte weergegeven.

## <a name="modify-and-distribute-your-app"></a>Uw app wijzigen en distribueren

U hebt de GitHub-sjabloon-app geïnstalleerd. Dit betekent dat u ook de GitHub-werkruimte hebt gemaakt. In de werkruimte kunt u het rapport en dashboard wijzigen en deze vervolgens als een *app* naar collega's in uw organisatie distribueren. 

1. Selecteer de pijl naast de naam van de werkruimte in het navigatievenster. U ziet dat de werkruimte een dashboard en een rapport bevat.

    ![App in het navigatievenster](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Selecteer het nieuwe [GitHub-dashboard](https://powerbi.microsoft.com/integrations/github).    
    ![GitHub-dashboard in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Als u alle inhoud van de nieuwe GitHub-werkruimte wilt weergeven, selecteert u in het navigatievenster **Werkruimten** > **GitHub**.
 
   ![GitHub-werkruimte in het navigatievenster](media/service-connect-to-github/power-bi-github-left-nav.png)

    Deze weergave is de inhoudslijst voor de werkruimte. In de rechterbovenhoek ziet u **App bijwerken**. Wanneer u klaar bent om uw app naar uw collega's te distribueren, kunt u beginnen. 

    ![GitHub-inhoudslijst](media/service-connect-to-github/power-bi-github-content-list.png)

2. Selecteer **Rapporten** en **Gegevenssets** om de andere elementen in de werkruimte weer te geven.

    Meer informatie over [apps distribueren](../collaborate-share/service-create-distribute-apps.md) naar uw collega's.

## <a name="whats-included-in-the-app"></a>Wat is opgenomen in de app
De volgende gegevens van GitHub zijn beschikbaar in Power BI:     

| Tabelnaam | Beschrijving |
| --- | --- |
| Bijdragen |Deze tabel bevat het totale aantal toevoegingen, verwijderingen en wijzigingen dat een inzender per week heeft bijgedragen. De tabel bevat gegevens van de 100 actiefste medewerkers. |
| Problemen |Een overzicht van alle problemen voor de geselecteerde opslagplaats en berekeningen zoals de totale en gemiddelde tijd voor het afhandelen van een probleem, het totale aantal openstaande problemen en het totale aantal afgesloten problemen. Deze tabel is leeg wanneer er geen problemen zijn gemeld voor de opslagplaats. |
| Pull requests |Deze tabel bevat alle pull-aanvragen voor de opslagplaats en wie de aanvraag heeft gedaan. De tabel bevat daarnaast berekeningen van het aantal openstaande en gesloten pull-aanvragen, het totale aantal pull-aanvragen, hoe lang het heeft geduurd om aanvragen te verwerken en hoe lang de gemiddelde pull-aanvraag heeft geduurd. Deze tabel is leeg wanneer er geen problemen zijn gemeld voor de opslagplaats. |
| Gebruikers |Deze tabel bevat een lijst van GitHub-gebruikers of -inzenders die bijdragen hebben geleverd, problemen hebben gemeld of pull-aanvragen hebben opgelost voor de geselecteerde opslagplaats. |
| Milestones |Deze tabel bevat alle mijlpalen voor de geselecteerde opslagplaats. |
| DateTable |Deze tabel bevat datums vanaf vandaag tot jaren in het verleden waarmee u gegevens van GitHub kunt analyseren op datum. |
| ContributionPunchCard |Deze tabel kan worden gebruikt als een controlemiddel voor bijdragen aan de geselecteerde opslagplaats. U ziet hier 'commits' per dag van de week en tijdstip van de dag. Deze tabel is niet verbonden met andere tabellen in het model. |
| RepoDetails |Deze tabel bevat details voor de geselecteerde opslagplaats. |

## <a name="system-requirements"></a>Systeemvereisten
* Een GitHub-account met toegang tot de opslagplaats.  
* Machtiging verleend aan de app Power BI voor GitHub tijdens de eerste aanmelding. Zie de details hieronder om de toegang weer in te trekken.  
* Er zijn voldoende API-aanroepen beschikbaar om de gegevens op te halen en te vernieuwen.
>[!NOTE]
>Deze sjabloon-app biedt geen ondersteuning voor GitHub Enterprise.

### <a name="de-authorize-power-bi"></a>Autorisatie van Power BI intrekken
Als u Power BI geen toestemming meer wilt geven om verbinding te maken met uw GitHub-opslagplaats, kunt u de toegang intrekken in GitHub. Zie dit [Help-onderwerp over GitHub](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) voor meer informatie.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Parameters zoeken
U kunt de eigenaar en opslagplaats vaststellen door te kijken naar de opslagplaats in GitHub zelf:

![Naam en eigenaar van opslagplaats](media/service-connect-to-github/github_ownerrepo.png)

Het eerste deel, 'Azure', is de eigenaar en het tweede deel, 'azure-sdk-for-php', is de opslagplaats zelf.  Deze twee items komen ook terug in de URL van de opslagplaats:

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Problemen oplossen
Indien nodig kunt u uw GitHub-referenties controleren.  

1. Ga in een ander browservenster naar de website van GitHub en meld u aan bij GitHub. U kunt in de rechterbovenhoek van de GitHub-site zien of u bent aangemeld.    
2. Navigeer in GitHub naar de URL van de opslagplaats die u wilt raadplegen in Power BI, Bijvoorbeeld: https://github.com/dotnet/corefx.  
3. Ga terug naar Power BI en probeer verbinding te maken met GitHub. Gebruik in het dialoogvenster Configure GitHub de naam van de opslagplaats en de naam van de eigenaar van dezelfde opslagplaats.  

## <a name="next-steps"></a>Volgende stappen

* [Zelfstudie: Verbinding maken met een GitHub-opslagplaats met Power BI](service-tutorial-connect-to-github.md)
* [De nieuwe werkruimten maken in Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Apps in Power BI installeren en gebruiken](../consumer/end-user-apps.md)
* [Verbinding maken met Power BI-apps voor externe services](service-connect-to-services.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
