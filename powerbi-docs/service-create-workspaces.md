---
title: Klassieke werkruimten maken in Power BI
description: Informatie over het maken van werkruimten, verzamelingen dashboards, rapporten en gepagineerde rapporten die zijn gemaakt om belangrijke metrische gegevens voor uw organisatie te bieden.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 0bb8d796af5139cd89f4bdfa0a8da10603acb2ed
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530563"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Klassieke werkruimten maken in Power BI

U kunt in Power BI *werkruimten* maken. Dit zijn plaatsen waar u samen met collega's verzamelingen dashboards, rapporten en gepagineerde rapporten kunt maken en verfijnen. Vervolgens kunt u de verzameling bundelen in *apps* die u kunt distribueren naar uw hele organisatie of naar specifieke personen of groepen. 

**Wist u dat?** Power BI biedt een nieuwe werkruimte-ervaring, die nu standaard is. Lees [Werk organiseren in de nieuwe werkruimten](service-new-workspaces.md) voor meer informatie over de nieuwe werkruimten. 

Wanneer u een klassieke werkruimte maakt, maakt u een onderliggende, gekoppelde Office 365-groep. Alle werkruimtebeheer vindt plaats in Office 365. U kunt collega's als leden of beheerders toevoegen aan deze werkruimten. In de werkruimte kan iedereen samenwerken aan dashboards, rapporten en andere artikelen die u wilt publiceren naar een breder publiek. Iedereen die u aan een app-werkruimte toevoegt, heeft een Power BI Pro-licentie nodig. 

## <a name="video-apps-and-app-workspaces"></a>Video: apps en app-werkruimten
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Een klassieke app-werkruimte maken op basis van een Office 365-groep

Als u een app-werkruimte maakt, wordt deze gebaseerd op een Office 365-groep.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Wanneer u de werkruimte maakt, kan het ongeveer een uur duren voordat de werkruimte aan Office 365 is doorgegeven. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Een afbeelding toevoegen aan uw Office 365-app-werkruimte (optioneel)
Power BI maakt standaard een kleine gekleurde cirkel voor uw app met de initialen van de app. Maar misschien wilt u deze aanpassen met een afbeelding. U hebt een licentie voor Exchange Online nodig om een afbeelding toe te voegen.

1. Selecteer **Werkruimten**, selecteer het weglatingsteken (...) naast de naam van de werkruimte, en selecteer vervolgens **Leden**. 
   
     ![Werkruimteleden selecteren](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    Het Office 365 Outlook-account voor de werkruimte wordt in een nieuw browservenster geopend.
2. Wanneer u de muisaanwijzer op de gekleurde cirkel in de linkerbovenhoek plaatst, verandert deze in een potloodpictogram. Selecteer het.
   
     ![Office 365-potloodpictogram](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Selecteer het potloodpictogram opnieuw en zoek de afbeelding die u wilt gebruiken.
   
     ![Het potlood opnieuw selecteren](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

     Afbeeldingen kunnen PNG-, JPG- of BMP-bestanden zijn. De bestandsgrootte kan groot zijn, tot maximaal 3 MB. 

4. Selecteer **Opslaan**.
   
     ![Opslaan selecteren](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    De afbeelding vervangt de gekleurde cirkel in het Office 365 Outlook-venster. 
   
     ![Aangepaste afbeelding](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    In een paar minuten verschijnt de afbeelding ook in de app in Power BI.
   
     ![Aangepaste afbeelding](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Inhoud toevoegen aan uw app-werkruimte

Nadat u een app-werkruimte hebt gemaakt, is het tijd om er inhoud aan toe te voegen. Toevoegen van inhoud werkt hetzelfde als inhoud toevoegen aan uw Mijn werkruimte, behalve dat andere personen in de werkruimte de inhoud ook kunnen zien en bewerken. Een groot verschil is dat wanneer u klaar bent, u de inhoud als app kunt publiceren. Wanneer u inhoud bekijkt in de inhoudslijst van een app-werkruimte, wordt de naam van de app-werkruimte als eigenaar weergegeven.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Verbinding maken met services van derden in app-werkruimten

Apps worden geleverd voor alle services van derden die door Power BI worden ondersteund, zodat u eenvoudig de gegevens kunt ophalen uit de services die u gebruikt, zoals Microsoft Dynamics CRM, Salesforce of Google Analytics. U kunt organisatie-apps publiceren om uw gebruikers de gegevens te leveren die ze nodig hebben.

In de huidige werkruimten kunt u ook verbinding maken met organisatie-inhoudspakketten en inhoudspakketten van derden, zoals Microsoft Dynamics CRM, Salesforce of Google Analytics. Overweeg uw organisatie-inhoudspakketten naar apps te migreren.

## <a name="distribute-an-app"></a>Een app distribueren

Als u officiële inhoud wilt distribueren naar een grote doelgroep binnen uw organisatie, kunt u een app vanuit uw werkruimte publiceren.  Wanneer de inhoud klaar is, kunt u kiezen welke dashboards en rapporten u wilt publiceren. Vervolgens publiceert u deze als een *app*. U kunt vanuit elke werkruimte een app maken.

In de lijst met apps in het linkernavigatievenster worden alle apps weergegeven die u hebt geïnstalleerd. Uw collega's kunnen uw app op een aantal verschillende manieren verkrijgen. 
- Ze kunnen uw app zoeken en installeren via Microsoft AppSource.
- U kunt ze een rechtstreekse koppeling sturen. 
- U kunt de app automatisch installeren in de Power BI-accounts van uw collega's als uw Power BI-beheerder u hiervoor toestemming geeft. 

Gebruikers zien bijgewerkte app-inhoud automatisch nadat u een update vanuit uw werkruimte hebt gepubliceerd. U kunt bepalen hoe vaak de gegevens worden vernieuwd door het vernieuwingsschema in te stellen in de gegevenssets die worden gebruikt door de app-inhoud in uw werkruimte. Zie [Publish an app from the new workspaces in Power BI ](service-create-distribute-apps.md) (Een app publiceren vanuit de nieuwe werkruimten in Power BI) voor meer informatie.

## <a name="power-bi-classic-apps-faq"></a>Veelgestelde vragen over klassieke Power BI-apps

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Hoe verschillen apps van organisatie-inhoudspakketten?
Apps zijn verbeterde organisatie-inhoudspakketten. Als u al organisatie-inhoudspakketten hebt, blijven deze gewoon naast apps werken. Apps en inhoudspakketten verschillen op enkele belangrijke punten. 

* Nadat zakelijke gebruikers een inhoudspakket hebben geïnstalleerd, verliest deze de gegroepeerde identiteit; de groep is nu alleen nog een lijst met dashboards en rapporten afgewisseld met andere dashboards en rapporten. Apps behouden daarentegen ook na de installatie hun groepering en identiteit. Deze groepering maakt het eenvoudig voor zakelijke gebruikers om ze in de toekomst opnieuw te openen.
* U kunt meerdere inhoudspakketten vanuit elke werkruimte maken, maar een app heeft een een-op-eenrelatie met de werkruimte. 
* We willen organisatie-inhoudspakketten op termijn afschaffen. Daarom raden we u aan vanaf nu apps te maken.  
* Met de preview-versie voor een nieuwe werkruimte-ervaring maken wij een begin om de organisatie-inhoudspakketten af te schaffen. U kunt deze in de preview-werkruimten niet gebruiken of maken.

Zie [Hoe verschillen de nieuwe werkruimten van de huidige werkruimten?](service-new-workspaces.md#how-the-new-workspaces-are-different) om de twee te vergelijken. 

## <a name="next-steps"></a>Volgende stappen
* [Apps in Power BI installeren en gebruiken](service-create-distribute-apps.md)
- [De nieuwe werkruimten maken (preview)](service-create-the-new-workspaces.md)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
