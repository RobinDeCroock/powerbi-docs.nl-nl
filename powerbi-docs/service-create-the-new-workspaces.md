---
title: De nieuwe werkruimten - Power BI maken
description: Informatie over het maken van de nieuwe werkruimten, verzamelingen van dashboards, rapporten en gepagineerde rapporten die zijn bedoeld voor belangrijke metrische gegevens voor uw organisatie.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61141947"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>De nieuwe werkruimten maken in Power BI

Power BI introduceert een nieuwe werkruimte-ervaring. Werkruimten zijn nog steeds de plaats voor het samenwerken met collega's om verzamelingen van dashboards, rapporten en gepagineerde rapporten te maken. Vervolgens kunt u deze verzameling in bundelen een *app* en deze distribueren naar uw hele organisatie of naar specifieke personen of groepen. 

Hier volgt wat is er anders. In de nieuwe werkruimten, kunt u het volgende doen:

- Werkruimterollen toewijzen aan gebruikersgroepen: beveiligingsgroepen, distributielijsten, Office 365-groepen en personen.
- Een werkruimte in Power BI maken zonder een Office 365-groep te maken.
- Gedetailleerdere werkruimterollen gebruiken voor flexibeler beheer van machtigingen in een werkruimte.

> [!NOTE]
> Als u beveiliging op rijniveau (RLS) voor Power BI Pro-gebruikers inhoud in een werkruimte te bladeren, echter ook doorgaan met [klassieke werkruimten](service-create-workspaces.md). Selecteer de **leden kunnen alleen Power BI-inhoud weergeven** optie. U kunt ook een Power BI-app publiceren voor gebruikers of delen gebruiken om inhoud te distribueren. De rol van toekomstige Viewer schakelt u dit scenario in de toekomst in nieuwe werkruimten van de werkruimte-ervaring.

Zie voor meer achtergrondinformatie de [nieuwe werkruimten](service-new-workspaces.md) artikel.

## <a name="create-one-of-the-new-app-workspaces"></a>Een van de nieuwe app-werkruimten maken

1. Maak eerst de app-werkruimte. Selecteer **Werkruimten** > **App-werkruimte maken**.
   
     ![App-werkruimte maken](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. U maakt automatisch een upgrade-werkruimte, tenzij u ervoor om te kiezen **terugkeren naar de klassieke**.
   
     ![Nieuwe werkruimte-ervaring](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Als u selecteert **terugkeren naar de klassieke**, u een werkruimte op basis van een Office 365-groep maken. Gebruik deze optie als u moet de **leden kunnen alleen Power BI-inhoud weergeven** optie voor het afdwingen van beveiliging op rijniveau (RLS) voor leden van de werkruimte.

2. Geef een naam op voor de werkruimte. Als de naam niet beschikbaar is, kunt deze te kunnen komen met een unieke naam te bewerken.
   
     De app voor de werkruimte heeft dezelfde naam en het pictogram als de werkruimte.
   
1. Hier volgen enkele optionele items die u voor uw werkruimte instellen kunt:

    Upload een **werkruimte installatiekopie**. Bestanden kunnen PNG of JPG-indeling zijn. Bestandsgrootte moet minder dan 45 KB zijn.
    
    [Voeg een **lijst met contactpersonen**](#workspace-contact-list). Standaard zijn de werkruimtebeheerders de contactpersonen. 
    
    [Geef een **werkruimte OneDrive** ](#workspace-onedrive) door alleen de naam van een bestaande Office 365-groep, niet de URL te typen. Deze werkruimte kunt nu de opslaglocatie die Office 365-groep gebruiken. 

    ![Geef een locatie op OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Toewijzen van de werkruimte bij naar een **toegewezen capaciteit**op de **Premium** Selecteer tabblad **toegewezen capaciteit**.
     
    ![Toegewezen capaciteit](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Selecteer **Opslaan**.

    De werkruimte wordt gemaakt en in Power BI geopend. De werkruimte wordt weergegeven in de lijst met werkruimten waarvan u lid bent. 

## <a name="workspace-contact-list"></a>Lijst met contactpersonen van werkruimte

De nieuwe lijst met contactpersonen in werkruimte kunt u opgeven welke gebruikers geïnformeerd over problemen die optreden in de werkruimte. Standaard opgegeven elke gebruiker of groep die als een werkruimte beheerder op de hoogte is gesteld, maar u kunt de lijst. Gebruikers of groepen die worden vermeld in de lijst met contactpersonen wordt weergegeven in de gebruikersinterface (UI) voor hulp bij gebruikers met betrekking tot de werkruimte.

1. Toegang tot de nieuwe **lijst met contactpersonen** instellen op twee manieren:

    In de **maken van een werkruimte** deelvenster wanneer u deze maakt.

    Selecteer in het linkernavigatievenster de pijl naast **werkruimten**, selecteer het weglatingsteken (...) naast de naam van de werkruimte > **werkruimte instellingen**. De **instellingen** deelvenster wordt geopend.

    ![Instellingen voor werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Onder **Geavanceerd** > **lijst met contactpersonen**, accepteer de standaardwaarde **werkruimtebeheerders**, of uw eigen lijst toe te voegen **specifieke gebruikers of groepen**. 
3. Selecteer **Opslaan**.

## <a name="workspace-onedrive"></a>Workspace OneDrive

De werkruimte OneDrive-functie kunt u een Office 365-groep waarvan bestandsopslag SharePoint-documentbibliotheek beschikbaar voor gebruikers van deze werkruimte is configureren. U maken eerst de groep buiten Power BI. 

Power BI biedt geen machtigingen van gebruikers of groepen die zijn geconfigureerd voor werkruimtetoegang met het groepslidmaatschap van Office 365 hebben gesynchroniseerd. De aanbevolen procedure is dezelfde Office 365-groep waarvan u in deze voor Office 365-instellingengroep configureren bestandsopslag geven [toegang tot de werkruimte](#give-access-to-your-workspace). Werkruimtetoegang beheren door het lidmaatschap van de Office 365-groep beheren. 

1. Toegang tot de nieuwe **werkruimte OneDrive** instellen op twee manieren:

    In de **maken van een werkruimte** deelvenster wanneer u deze maakt.

    Selecteer in het linkernavigatievenster de pijl naast **werkruimten**, selecteer het weglatingsteken (...) naast de naam van de werkruimte > **werkruimte instellingen**. De **instellingen** deelvenster wordt geopend.

    ![Instellingen voor werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Onder **Geavanceerd** > **werkruimte OneDrive**, typ de naam van de Office 365-groep die u eerder hebt gemaakt. Power BI hervat automatisch de OneDrive voor de groep.

    ![Geef een locatie op OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Selecteer **Opslaan**.

### <a name="access-the-workspace-onedrive-location"></a>Toegang tot de werkruimte OneDrive-locatie

Nadat u de OneDrive-locatie hebt geconfigureerd, kunt u naar het krijgen van een aantal verschillende plaatsen in de werkruimte:

- Selecteer **werkruimten** > *Werkruimtenaam* > het weglatingsteken ( **...** ) menu > **bestanden**. 

    ![De locatie van bestanden](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Selecteer het weglatingsteken ( **...** ) in het menu in de rechterbovenhoek van de werkruimte > **bestanden**.

    ![De locatie van bestanden](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- In de **gegevens ophalen** > **bestanden** optreden. De **OneDrive-bedrijven** vermelding is uw eigen OneDrive voor bedrijven. De tweede OneDrive is degene die u hebt toegevoegd.

    ![Locatie van bestanden - gegevens ophalen](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Inhoud toevoegen aan uw app-werkruimte

Nadat u een nieuwe werkruimte-ervaring-werkruimte hebt gemaakt, is het tijd om toe te voegen inhoud toe. Inhoud toevoegen is vergelijkbaar in de nieuwe en klassieke werkruimten. Gebruik de knop maken of gegevens ophalen gebruikt om inhoud toevoegen aan uw werkruimte.

1. In de **Welkom** scherm voor uw nieuwe werkruimte, kunt u inhoud toevoegen. 

    ![Welkomstscherm voor nieuwe werkruimte](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Selecteer bijvoorbeeld **Voorbeelden** > **Voorbeeld van klantwinstgevendheid**.

> [!NOTE]
> In de nieuwe werkruimten, kan niet u organisatie-inhoudspakketten of Apps voor organisaties van derden gebruiken. Apps zijn beschikbaar voor alle externe inhoud packs u eerder hebt gebruikt. Klassieke werkruimten gebruiken als u nodig hebt om door te gaan met behulp van inhoudspakketten. Inhoudspakketten zijn afgeschaft, dus het is een best practice om apps te gebruiken in plaats daarvan.

Wanneer u inhoud bekijkt in de inhoudslijst van een app-werkruimte, wordt de naam van de app-werkruimte als eigenaar weergegeven.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Verbinding maken met de services van derden in nieuwe werkruimten

In de nieuwe werkruimte-ervaring ligt de nadruk nu op *apps*. Gebruikers kunnen met apps voor services van derden gemakkelijk gegevens verkrijgen van de services die ze gebruiken, zoals Microsoft Dynamics CRM, Salesforce of Google Analytics.

U kunt in de nieuwe werkruimte-ervaring, maken of organisatie-inhoudspakketten in beslag nemen. In plaats daarvan kunt u de geleverde apps gebruiken om verbinding te maken met services van derden, of u kunt uw interne teams vragen apps te leveren voor inhoudspakketten die u momenteel gebruikt. 

## <a name="give-access-to-your-workspace"></a>Toegang geven tot uw werkruimte

1. In de lijst van de werkruimte-inhoud, omdat u een beheerder bent ziet u een nieuwe actie **toegang**.

    ![Lijst met werkruimten inhoud](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Selecteer **Toegang verkrijgen**.

1. Voeg aan deze werkruimten beveiligingsgroepen, distributielijsten, Office 365-groepen of personen toe als leden, inzenders of beheerders. Zie [Rollen in de nieuwe werkruimten](service-new-workspaces.md#roles-in-the-new-workspaces) voor een uitleg over de verschillende rollen.

    ![Werkruimten - leden, beheerders en inzenders toevoegen](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Selecteer **Toevoegen** > **Sluiten**.


## <a name="distribute-an-app"></a>Een app distribueren

Als u wilt de officiële inhoud distribueert naar een grote publiek binnen uw organisatie, kunt u een app publiceren vanuit uw werkruimte.  Wanneer de inhoud klaar is, u kiezen welke dashboards en rapporten die u wilt publiceren, en ten slotte publiceren als een *app*. U kunt vanuit elke werkruimte een app maken.

Meer informatie over [publiceren van een app uit de nieuwe werkruimten](service-create-distribute-apps.md)

## <a name="next-steps"></a>Volgende stappen
* Meer informatie over [ordent werk in het nieuwe werkruimten in Power BI](service-new-workspaces.md)
* [Klassieke werkruimten maken](service-create-workspaces.md)
* [Een app uit de nieuwe werkruimten in Power BI publiceren](service-create-distribute-apps.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
