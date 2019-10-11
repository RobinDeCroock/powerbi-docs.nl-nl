---
title: De nieuwe werkruimten maken - Power BI
description: Informatie over het maken van de nieuwe werkruimten, verzamelingen dashboards, rapporten en gepagineerde rapporten die zijn gemaakt om belangrijke metrische gegevens voor uw organisatie te bieden.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5c50ec38da65573e085d9e27b0e31524256ac009
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715534"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>De nieuwe werkruimten maken in Power BI

Power BI introduceert een nieuwe werkruimte-ervaring. Werkruimten zijn nog steeds de plek waar u met collega's samenwerkt om verzamelingen dashboards, rapporten en gepagineerde rapporten te maken. Vervolgens kunt u die verzameling bundelen in een *app* en die verspreiden in uw hele organisatie, of bij specifieke mensen of groepen. 

Nu wordt uitgelegd wat anders is. In de nieuwe werkruimten is het volgende mogelijk:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Office 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een Office 365-groep te maken.
- Gedetailleerdere werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.

> [!NOTE]
> De gebruikers toewijzen aan de rol Kijker om de beveiliging op rijniveau (RLS) af te dwingen voor Power BI Pro-gebruikers die door inhoud in een werkruimte bladeren.

Lees het artikel [Nieuwe werkruimten](service-new-workspaces.md) voor meer achtergrondinformatie.

## <a name="create-one-of-the-new-workspaces"></a>Een van de nieuwe werkruimten maken

1. Maak eerst de werkruimte. Selecteer **Werkruimten** > **Werkruimte maken**.
   
     ![Werkruimte maken](media/service-create-the-new-workspaces/power-bi-workspace-create.png)

2. U maakt automatisch een bijgewerkte werkruimte, tenzij u kiest voor **Terugkeren naar klassieke werkruimte**.
   
     ![Nieuwe werkruimte-ervaring](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Als u **Terugkeren naar klassieke werkruimte** selecteert, maakt u een [werkruimte op basis van een Office 365-groep](service-create-workspaces.md). 

2. Geef een naam op voor de werkruimte. Als de naam niet beschikbaar is, bewerkt u deze tot een unieke naam.
   
     De app voor de werkruimte heeft dezelfde naam en hetzelfde pictogram als de werkruimte.
   
1. Dit zijn een paar optionele items die u kunt instellen voor uw werkruimte:

    Een **Werkruimteafbeelding** uploaden. Goedgekeurde bestanden zijn .png- of .jpg-bestanden. Het bestand moet kleiner zijn dan 45 kB.
    
    [Een **Lijst met contactpersonen** toevoegen](#workspace-contact-list). De werkruimtebeheerders zijn standaard contactpersonen. 
    
    [Een **OneDrive voor de werkruimte** opgeven](#workspace-onedrive) door de naam van een bestaande Office 365-groep te typen, niet de URL. Nu kan deze werkruimte gebruikmaken van de opslaglocatie van die Office 365-groep. 

    ![Een OneDrive-locatie opgeven](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Als u de werkruimte wilt toewijzen aan een **Toegewezen capaciteit**, selecteert u op het tabblad **Premium** de optie **Toegewezen capaciteit**.
     
    ![Toegewezen capaciteit](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Selecteer **Opslaan**.

    De werkruimte wordt gemaakt en in Power BI geopend. De werkruimte wordt weergegeven in de lijst met werkruimten waarvan u lid bent. 

## <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte

De lijst met contactpersonen in de nieuwe werkruimte maakt het mogelijk om op te geven welke gebruikers meldingen moeten ontvangen over problemen die optreden in de werkruimte. De standaardinstelling is dat elke gebruiker of groep die is ingesteld als een beheerder van de werkruimte een melding krijgt, maar u kunt de lijst aanpassen. Gebruikers of groepen die in de lijst met contactpersonen staan, worden weergegeven in de gebruikersinterface (UI) zodat gebruikers hulp kunnen krijgen met betrekking tot de werkruimte.

1. U opent de instellingen voor de nieuwe **Lijst met contactpersonen** op een van twee manieren:

    In het deelvenster **Een werkruimte maken** wanneer u voor het eerst een werkruimte maakt.

    Selecteer in het linkernavigatievenster de pijl naast **Werkruimten**, selecteer het beletselteken (...) naast de naam van de werkruimte > **Werkruimte-instellingen**. Het deelvenster **Instellingen** wordt geopend.

    ![Instellingen voor werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Onder **Geavanceerd** > **Lijst met contactpersonen** accepteert u de standaardinstellingen, **Werkruimtebeheerders** of voegt u uw eigen lijst of **Specifieke gebruikers of groepen** toe. 
3. Selecteer **Opslaan**.

## <a name="workspace-onedrive"></a>Werkruimte op OneDrive

Met de functie Werkruimte op OneDrive kunt u een Office 365-groep configureren waarvan de bestandsopslag uit de SharePoint-documentbibliotheek beschikbaar voor werkruimtegebruikers. Eerst maakt u de groep buiten Power BI. 

Power BI biedt geen synchronisatie voor machtigingen van gebruikers of groepen die zijn geconfigureerd voor werkruimtetoegang met behulp van het lidmaatschap van een Office 365-groep. Het beste is om dezelfde Office 365-groep, waarvan u de bestandsopslag configureert bij het instellen van deze Office 365-groep, [toegang te geven tot de werkruimte](#give-access-to-your-workspace). Vervolgens beheert u werkruimtetoegang via het lidmaatschapsbeheer van de Office 365-groep. 

1. U opent de instellingen van de **OneDrive voor de werkruimte** op een van twee manieren:

    In het deelvenster **Een werkruimte maken** wanneer u voor het eerst een werkruimte maakt.

    Selecteer in het linkernavigatievenster de pijl naast **Werkruimten**, selecteer het beletselteken (...) naast de naam van de werkruimte > **Werkruimte-instellingen**. Het deelvenster **Instellingen** wordt geopend.

    ![Instellingen voor werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Onder **Geavanceerd** > **OneDrive van werkruimte** voert u naam van de Office 365-groep in die u eerder hebt gemaakt. Power BI haalt automatisch de OneDrive voor de groep op.

    ![Een OneDrive-locatie opgeven](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Selecteer **Opslaan**.

### <a name="access-the-workspace-onedrive-location"></a>Toegang tot de OneDrive-locatie van de werkruimte

Nadat u de OneDrive-locatie hebt geconfigureerd, kunt u die vanuit een paar verschillende plekken in de werkruimte bereiken:

- Selecteer **Werkruimten** > *naam werkruimte* > het beletselteken ( **...** ) > **Bestanden**. 

    ![Locatie van werkruimtebestanden](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Selecteer het beletselteken ( **...** ) in de rechterbovenhoek van de werkruimte > **Bestanden**.

    ![Locatie van werkruimtebestanden](media/service-create-the-new-workspaces/power-bi-new-workspace-files-ellipsis.png)
    
- In de ervaring **Gegevens ophalen** > **Bestanden**. De invoer **OneDrive - Bedrijven** is uw eigen OneDrive voor Bedrijven. De tweede OneDrive is de OneDrive die u hebt toegevoegd.

    ![Locatie van werkruimtebestanden - gegevens ophalen](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-workspace"></a>Inhoud toevoegen aan uw werkruimte

Nadat u een werkruimte met de nieuwe werkruimte-ervaring hebt gemaakt, is het tijd om er inhoud aan toe te voegen. Inhoud toevoegen gaat op dezelfde manier in de nieuwe en klassieke werkruimten. Gebruik de knop Maken of gebruik Gegevens ophalen om inhoud toe te voegen aan uw werkruimte.

1. Op het scherm **Welkom** van uw nieuwe werkruimte voegt u inhoud toe. 

    ![Welkomstscherm voor nieuwe werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-get-data.png)

1. Selecteer bijvoorbeeld **Voorbeelden** > **Voorbeeld van klantwinstgevendheid**.

> [!NOTE]
> U kunt geen organisatie-inhoudspakketten of pakketten van externe partijen toevoegen aan de nieuwe werkruimten. Er zijn apps beschikbaar voor veel externe inhoudspakketten die u eerder hebt gebruikt. Gebruik klassieke werkruimten als u gebruik moet blijven maken van inhoudspakketten. Inhoudspakketten zijn verouderd, dus het beste is om apps te gebruiken.

Wanneer u inhoud bekijkt in de inhoudslijst van een werkruimte, wordt de naam van de werkruimte als eigenaar weergegeven.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Verbinding maken met services van derden in nieuwe werkruimten

In de nieuwe werkruimte-ervaring ligt de nadruk nu op *apps*. Gebruikers kunnen met apps voor services van derden gemakkelijk gegevens verkrijgen van de services die ze gebruiken, zoals Microsoft Dynamics CRM, Salesforce of Google Analytics.

In de nieuwe werkruimte-ervaring kunt u geen organisatie-inhoudspakketten maken of gebruiken. In plaats daarvan kunt u de geleverde apps gebruiken om verbinding te maken met services van derden, of u kunt uw interne teams vragen apps te leveren voor inhoudspakketten die u momenteel gebruikt. 

## <a name="give-access-to-your-workspace"></a>Toegang verlenen tot uw werkruimte

1. In de inhoudslijst van de werkruimte ziet u een nieuwe actie omdat u beheerder bent: **Toegang**.

    ![Inhoudslijst van werkruimte](media/service-create-the-new-workspaces/power-bi-new-workspace-files-ellipsis.png)

1. Selecteer **Toegang verkrijgen**.

1. Voeg aan deze werkruimten beveiligingsgroepen, distributielijsten, Office 365-groepen of personen toe als leden, inzenders of beheerders. Zie [Rollen in de nieuwe werkruimten](service-new-workspaces.md#roles-in-the-new-workspaces) voor een uitleg over de verschillende rollen.

    ![Werkruimten - leden, beheerders en inzenders toevoegen](media/service-create-the-new-workspaces/power-bi-workspace-add-members.png)

9. Selecteer **Toevoegen** > **Sluiten**.


## <a name="distribute-an-app"></a>Een app distribueren

Als u officiële inhoud wilt distribueren naar een grote doelgroep binnen uw organisatie, kunt u een app vanuit uw werkruimte publiceren.  Wanneer de inhoud klaar is, kunt u kiezen welke dashboards en rapporten u wilt publiceren. Vervolgens publiceert u deze als een *app*. U kunt vanuit elke werkruimte een app maken.

Meer informatie [over het publiceren van een app vanuit de nieuwe werkruimten](service-create-distribute-apps.md)

## <a name="next-steps"></a>Volgende stappen
* Lees meer over het [organiseren van werk in de nieuwe werkruimte-ervaring in Power BI](service-new-workspaces.md)
* [Klassieke werkruimten maken](service-create-workspaces.md)
* [Publish an app from the new workspaces in Power BI](service-create-distribute-apps.md) (Een app publiceren vanuit de nieuwe werkruimten in Power BI)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
