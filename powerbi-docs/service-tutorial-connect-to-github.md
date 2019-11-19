---
title: 'Zelfstudie: Verbinding maken met een GitHub-opslagplaats met Power BI'
description: In deze zelfstudie gebruikt u echte gegevens in de GitHub-service met Power BI en Power BI maakt automatisch dashboards en rapporten.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 08/07/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 7f7fde7fcabc29238d9558739eff02519ef9cca3
ms.sourcegitcommit: 2aa83bd53faad6fb02eb059188ae623e26503b2a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73020021"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Zelfstudie: Verbinding maken met een GitHub-opslagplaats met Power BI
In deze zelfstudie gebruikt u echte gegevens in de GitHub-service met Power BI en Power BI maakt automatisch dashboards en rapporten. U maakt verbinding met de *opslagplaats* voor openbare Power BI-inhoud en kunt antwoorden zien op vragen als de volgende: Hoeveel mensen dragen bij aan de openbare Power BI-inhoud? Wie levert de meeste bijdragen? Op welke dag van de wek worden de meeste bijdragen geleverd? En andere vragen. 

![Het GitHub-rapport in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

In deze zelfstudie voert u de volgende stappen uit:

> [!div class="checklist"]
> * Meld u aan voor een GitHub-account als u dat nog niet hebt 
> * Meld u aan bij uw Power BI-account, of meld u aan voor een account als u dat nog niet hebt
> * De Power BI-service openen
> * De GitHub-app zoeken
> * De informatie voor de openbare GitHub-opslagplaats van Power BI invoeren
> * Het dashboard en rapport met GitHub-gegevens bekijken
> * De app verwijderen om resources te wissen

Als u zich niet hebt geregistreerd voor Power BI, kunt u zich hier [aanmelden voor een gratis proefversie](https://app.powerbi.com/signupredirect?pbi_source=web) voordat u begint.

## <a name="prerequisites"></a>Vereisten

Voor het voltooien van deze zelfstudie hebt u een GitHub-account nodig, als u dit nog niet hebt. 

- Meld u aan voor een [GitHub-account](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Verbinding maken
1. Aanmelden bij de Power BI-service (https://app.powerbi.com) ). 
2. Selecteer in het linkernavigatievenster de optie **Apps** en vervolgens **Apps downloaden**.
   
   ![Power BI Apps downloaden](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecteer **Apps**, typ **GitHub** in het zoekvak > **Nu downloaden**.
   
   ![Power BI GitHub downloaden](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Selecteer in **Deze Power BI-app installeren?** de optie **Installeren**.
5. Selecteer in **Uw nieuwe app is gereed** de optie **Naar app**.
6. Selecteer in **Aan de slag met uw nieuwe app** de optie **Verbinding maken**.

    ![Aan de slag met uw nieuwe app](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. Voer de naam in van de opslagplaats en de naam van de eigenaar van de opslagplaats. De URL voor deze opslagplaats is https://github.com/MicrosoftDocs/powerbi-docs , dus de **Eigenaar van opslagplaats** is **MicrosoftDocs** en de **Opslagplaats** is **powerbi-docs**. 
   
    ![Naam Power BI GitHub-opslagplaats](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Voer de GitHub-referenties die u hebt gemaakt in. Power BI kan deze stap overslaan als u zich al hebt aangemeld bij GitHub in uw browser. 

6. Houd bij **Verificatiemethode** de optie **oAuth2** geselecteerd \> **Aanmelden**.

7. Volg de verificatie-instructies van GitHub. Geef Power BI toestemming voor de GitHub-gegevens.
   
   Power BI kan nu verbinding maken met GitHub en de gegevens.  De gegevens worden eenmaal per dag vernieuwd.

8. Nadat de gegevens zijn geïmporteerd in Power BI, wordt de inhoud van uw nieuwe GitHub-werkruimte weergegeven. 
9. Selecteer de pijl naast de naam van de werkruimte in de linkernavigatiebalk. U ziet dat de werkruimte een dashboard en een rapport bevat. 

    ![App in het linkernavigatievenster](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selecteer **Meer opties** (...) naast de dashboardnaam > **Naam wijzigen** > typ **GitHub-dashboard**.
 
    ![Power BI GitHub-tegel](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selecteer het algemene navigatiepictogram om de navigatie aan de linkerkant te minimaliseren, zodat u meer ruimte hebt.

    ![Pictogram voor globale navigatie](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecteer uw GitHub-dashboard.
    
    Het GitHub-dashboard bevat livegegevens, dus de waarden die u ziet, kunnen afwijken.

    ![Het GitHub-dashboard in Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Een vraag stellen

1. Plaats de cursor in het vak **Een vraag stellen over uw gegevens**. Power BI biedt **Vragen om mee te beginnen**. 

1. Selecteer **Hoeveel gebruikers zijn er?** .
 
    ![Hoeveel gebruikers zijn er?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Tussen **Hoeveel** en **gebruikers zijn er?** typt u **pull-aanvragen per**. 

     Power BI maakt een staafdiagram met daarin het aantal pull-aanvragen per persoon.

    ![Hoeveel pull-aanvragen per gebruiker zijn er?](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selecteer de speld om het staafdiagram aan uw dashboard vast te maken en selecteer **Q&A afsluiten**.

## <a name="view-the-github-report"></a>Het GitHub-rapport weergeven 

1. In het GitHub-dashboard selecteert u de kolomgrafiek **Pull-aanvragen per maand** om het bijbehorende rapport te openen.

    ![Kolomdiagram met het aantal pull-aanvragen per maand](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selecteer een gebruikersnaam in het diagram **Totaal aantal pull-aanvragen per gebruiker**. In dit voorbeeld zien we dat de meeste uren in februari waren.

    ![Markeringen in Power BI GitHub-rapporten](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selecteer het tabblad **Perforatiekaart** om de volgende pagina in het rapport weer te geven. 
 
    ![Perforatiekaart in Power BI GitHub-rapporten](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Zo te zien is dinsdag om 15.00 uur het meest gangbare tijdstip en de meest gangbare dag van de week voor *doorvoerbewerkingen*, wanneer mensen hun werk inchecken.

## <a name="clean-up-resources"></a>Resources opschonen

Nu u de zelfstudie hebt voltooid, kunt u de GitHub-app verwijderen. 

1. Selecteer **Apps** in de linkernavigatiebalk.
2. Beweeg de cursor boven de GitHub-tegel en selecteer de prullenbak **Verwijderen**.

    ![De GitHub-app verwijderen](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt u verbinding gemaakt met een openbare GitHub-opslagplaats en gegevens gedownload, die door Power BI naar een dashboard en rapport zijn geformatteerd. U hebt een aantal vragen over de gegevens beantwoord door het dashboard en rapport te verkennen. U kunt nu meer leren over verbinding maken met andere services zoals Salesforce, Microsoft Dynamics en Google Analytics. 
 
> [!div class="nextstepaction"]
> [Verbinding maken met de onlineservices die u gebruikt](service-connect-to-services.md)


