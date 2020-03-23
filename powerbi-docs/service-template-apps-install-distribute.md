---
title: Sjabloon-apps in uw organisatie installeren en distribueren - Power BI
description: Meer informatie over het installeren, aanpassen en distribueren van sjabloon-apps in uw organisatie in Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 03/15/2020
ms.author: painbar
ms.openlocfilehash: 08aadc3027c5b265194e4239b150ea5d27fe2e43
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436106"
---
# <a name="install-and-distribute-template-apps-in-your-organization"></a>Sjabloon-apps in uw organisatie installeren en distribueren

Bent u een Power BI-analist? In dat geval leest u in dit artikel hoe u [sjabloon-apps](service-template-apps-overview.md) kunt installeren om in verbinding te komen met de vele services waarmee u uw bedrijfsactiviteiten uitvoert, zoals Salesforce, Microsoft Dynamics en Google Analytics. U kunt de vooraf gemaakte dashboards en rapporten van de sjabloon-app wijzigen om aan de behoeften van uw organisatie te voldoen en deze als [app](consumer/end-user-apps.md) naar uw collega's distribueren. 

![Geïnstalleerde Power BI-apps](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Zie [Een sjabloon-app maken in Power BI](service-template-apps-create.md) als u meer wilt weten over het maken van sjabloon-apps die u buiten uw organisatie kunt distribueren. Power BI-partners kunnen Power BI-apps bouwen met weinig of geen code en deze beschikbaar stellen voor Power BI-klanten. 

## <a name="prerequisites"></a>Vereisten  

Als u een sjabloon-app wilt installeren, aanpassen en distribueren, hebt u het volgende nodig: 

* Een [Power BI Pro-licentie](service-self-service-signup-for-power-bi.md).
* Machtigingen om sjabloon-apps te installeren op uw tenant.
* Een geldige installatiekoppeling voor de app, die u ophaalt uit AppSource of van de maker van de app.
* Bekendheid met de [basisconcepten van Power BI](service-basic-concepts.md).

## <a name="install-a-template-app"></a>Een sjabloon-app installeren

1. Selecteer in de Power BI-service in het navigatievenster **Apps** > **Apps ophalen**.

    ![Apps ophalen](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

1. Selecteer **Apps** in het venster AppSource dat wordt weergegeven. Blader of zoek naar de gewenste app en selecteer vervolgens **Nu downloaden**.

    ![Zoeken in AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

1. Selecteer in het dialoogvenster dat verschijnt de optie **Installeren**.

    ![App installeren](media/service-template-apps-install-distribute/power-install-dialog.png)
    
    De app wordt geïnstalleerd met een gekoppelde werkruimte. **Als u besluit de app aan te passen, kunt u dit doen in deze gekoppelde werkruimte**.

    > [!NOTE]
    > Als u een installatiekoppeling gebruikt voor een app die niet in AppSource wordt vermeld, wordt u in het dialoogvenster voor validatie gevraagd uw keuze te bevestigen.
    >
    >Als u een sjabloon-app wilt installeren die niet wordt vermeld op AppSource, moet u de relevante machtigingen aanvragen bij uw beheerder. Zie de [Instellingen voor sjabloon-apps](service-admin-portal.md#template-apps-settings) in de Power BI-beheerportal voor meer informatie.

    Wanneer de installatie is voltooid, krijgt u een melding dat de nieuwe app gereed is.

    ![Naar de app](media/service-template-apps-install-distribute/power-bi-go-to-app.png)

## <a name="connect-to-data"></a>Verbinding maken met gegevens

1. Selecteer **Naar de app**. Het venster **Aan de slag met uw nieuwe app** wordt weergegeven.

   ![Aan de slag met uw app](media/service-template-apps-install-distribute/power-bi-template-app-get-started.png)

1. Klik op **Verbinding maken**.
    
    Hiermee opent u een dialoogvenster of een reeks dialoogvensters waarin u de gegevensbron van de voorbeeldgegevens kunt wijzigen in uw eigen gegevensbron. Over het algemeen betekent dit dat u parameters van de gegevensset en referenties van de gegevensbron opnieuw definieert. Raadpleeg [Bekende beperkingen](service-template-apps-tips.md#known-limitations).
    
    In het onderstaande voorbeeld zijn twee dialoogvensters betrokken bij het maken van verbinding met gegevens.

   ![Verbinding maken met gegevensdialoogvensters](media/service-template-apps-install-distribute/power-bi-template-app-connect-to-data-dialogs.png)

    Wanneer u klaar bent met het invullen van de verbindingsdialoogvensters, wordt het verbindingsproces gestart. Met een banner wordt u geïnformeerd dat u voorbeeldgegevens bekijkt.

    ![Voorbeeldgegevens weergeven](media/service-template-apps-install-distribute/power-bi-template-app-viewing-sample-data.png)

    Wacht totdat de gegevens zijn verbonden en bijgewerkt. Als u wilt weten wanneer dit proces is voltooid, bekijkt u de voortgangsindicator op de gegevenssetrij (nieuw uiterlijk) of tabblad (oud uiterlijk).

   Wanneer de verbinding en het vernieuwen van gegevens is voltooid, vernieuwt u de browser. In de banner wordt nu gemeld dat u de app moet bijwerken om eventuele wijzigingen toe te passen die u hebt aangebracht in de app en om deze te delen.

    ![App aanpassen en delen](media/service-template-apps-install-distribute/power-bi-template-app-customize-share.png)

## <a name="customize-and-share-the-app"></a>De app aanpassen en delen

Nadat u de browser hebt vernieuwd na verbinding te hebben gemaakt met gegevens en de gegevens zijn vernieuwd, ziet u de werkruimte die aan de app is gekoppeld. U kunt de artefacten daar dan bewerken, net zoals u dat in een andere werkruimte zou doen. Houd er echter rekening mee dat eventuele wijzigingen die u aanbrengt, worden overschreven wanneer u de app bijwerkt met een nieuwe versie, tenzij u de gewijzigde items opslaat onder andere namen. [Zie informatie over overschrijven](#overwrite-behavior).

Raadpleeg voor meer informatie over het bewerken van artefacten in de werkruimte het artikel
* [Rondleiding door de rapporteditor in Power BI](service-the-report-editor-take-a-tour.md)
* [Basisconcepten voor ontwerpers in de Power BI-service](service-basic-concepts.md)

Zodra u klaar bent met het maken van wijzigingen in de artefacten in de werkruimte, kunt u de app publiceren en delen. Zie [Uw app publiceren](service-create-distribute-apps.md#publish-your-app) om te leren hoe u dit doet.

## <a name="update-a-template-app"></a>Een sjabloon-app bijwerken

Van tijd tot tijd brengen makers van sjabloon-apps nieuwe versies van hun sjabloon-apps uit, via AppSource, directe koppeling of beide.

Als u de app oorspronkelijk hebt gedownload vanaf AppSource, wordt er een updatebanner weergegeven in de Power BI-service wanneer een nieuwe versie van de sjabloon-app beschikbaar is. Met de banner wordt u geïnformeerd dat een nieuwe versie van de sjabloon beschikbaar is.

  ![Updatemelding van sjabloon-app](media/service-template-apps-install-distribute/power-bi-new-app-version-notification.png)

>[!NOTE]
>Als u de app oorspronkelijk hebt ontvangen via een directe koppeling in plaats van via AppSource, is de enige manier om te weten te komen of een nieuwe versie beschikbaar is, door contact op te nemen met de maker van de sjabloon-app.

  Als u de update wilt installeren, klikt u op **Downloaden** op de meldingsbanner of zoekt u de app weer op in AppSource en kiest u **Nu downloaden**. Als u een directe koppeling voor de update hebt gekregen van de maker van de sjabloon-app, klikt u gewoon op de koppeling.
  
  U wordt gevraagd of u de huidige versie wilt overschrijven, of dat u de nieuwe versie wilt installeren in een nieuwe werkruimte. Standaard is Overschrijven geselecteerd.

  ![Een sjabloon-app bijwerken](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Een bestaande versie overschrijven:** hiermee wordt de bestaande werkruimte overschreven met de bijgewerkte versie van de sjabloon-app. [Zie informatie over overschrijven](#overwrite-behavior).

- **Installeren in een nieuwe werkruimte:** hiermee wordt een nieuwe versie van de werkruimte en app geïnstalleerd die u moet opnieuw configureren (dat wil zeggen, verbinding maken met gegevens, navigatie en machtigingen definiëren).

### <a name="overwrite-behavior"></a>Gedrag voor overschrijven

* Bij het overschrijven worden de rapporten, de dashboards en de gegevensset in de werkruimte bijgewerkt en niet de app zelf. Wanneer u overschrijft, worden de navigatie van de app, de instellingen en de machtigingen niet gewijzigd.
* Nadat u de werkruimte hebt bijgewerkt, moet u **de app bijwerken om wijzigingen voor de werkruimte toe te passen in de app**.
* Bij het overschrijven blijven geconfigureerde parameters en verificatie behouden. Na de update wordt automatisch gestart met het vernieuwen van de gegevensset. **Tijdens deze vernieuwing worden in de app, rapporten en dashboards voorbeeldgegevens weergegeven**.

  ![Voorbeeldgegevens](media/service-template-apps-install-distribute/power-bi-sample-data.png)

* Tijdens het overschrijven worden er altijd voorbeeldgegevens weergegeven tot het vernieuwen is voltooid. Als de auteur van de sjabloon-app wijzigingen heeft aangebracht aan de gegevensset of parameters, zien gebruikers van de werkruimte en app de nieuwe gegevens pas wanneer de vernieuwing is voltooid. In plaats daarvan blijven ze de voorbeeldgegevens zien gedurende deze periode.
* Als u overschrijft, worden nooit nieuwe rapporten en dashboards overschreven die u hebt toegevoegd aan de werkruimte. Alleen de oorspronkelijke rapporten en dashboards worden overschreven met wijzigingen van de oorspronkelijke auteur.

>[!IMPORTANT]
>Vergeet niet om [de app bij te werken](#customize-and-share-the-app) na het overschrijven, om wijzigingen aan te brengen in de rapporten en dashboards voor de gebruikers van de organisatie-app.

## <a name="next-steps"></a>Volgende stappen

[Werkruimten maken met uw collega's in Power BI](service-create-workspaces.md)
