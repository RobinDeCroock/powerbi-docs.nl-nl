---
title: Apps met dashboards en rapporten publiceren in Power BI
description: 'Informatie over het publiceren van apps: verzamelingen dashboards en rapporten die zijn gemaakt om belangrijke statistieken voor uw organisatie te bieden.'
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 051609c59e155cb6d5c2a982483a7e6d2d91a665
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964681"
---
# <a name="publish-apps-with-dashboards-and-reports-in-power-bi"></a>Apps met dashboards en rapporten publiceren in Power BI

In Power BI kunt u *apps* met verzamelingen gerelateerde dashboards en rapporten publiceren. U maakt apps in *app-werkruimten*, waar u samen met uw collega's aan Power BI-inhoud kunt werken. Vervolgens kunt u de voltooide apps naar grote groepen mensen in uw organisatie publiceren. Meer informatie over [app-werkruimten maken](service-create-workspaces.md).

![Power BI-apps](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Uw zakelijke gebruikers hebben vaak meerdere Power BI-dashboards en rapporten nodig voor hun bedrijfsvoering. Met Power BI-apps kunt u verzamelingen van dashboards en rapporten maken en deze apps naar uw hele organisatie of naar specifieke personen of groepen publiceren. Apps maken het u als beheerder of rapportmaker gemakkelijker om machtigingen voor deze verzamelingen te beheren.

Zakelijke gebruikers kunnen uw apps op een aantal verschillende manieren installeren. Als de Power BI-beheerder u toestemming geeft, kunt u apps automatisch installeren in de Power BI-accounts van uw collega's. Anders kunnen ze uw apps vanuit Microsoft AppSource installeren, of u kunt ze via een directe koppeling verzenden. Ze kunnen uw inhoud eenvoudig vinden en opnieuw bekijken, omdat alles op één plek staat. Ze kunnen de inhoud van de app niet wijzigen, maar ze kunnen wel bepaalde acties uitvoeren in de Power BI-service of een van de mobiele apps: filteren, markeren en de gegevens sorteren. Ze ontvangen automatisch updates en u kunt bepalen hoe vaak de gegevens worden vernieuwd. Meer informatie over de [app-ervaring voor zakelijke gebruikers](consumer/end-user-apps.md).

**Wist u dat?** Met Power BI is een preview-versie van een nieuwe werkruimte-ervaring beschikbaar. Lees [De nieuwe werkruimten maken (preview)](service-create-the-new-workspaces.md) om te zien hoe werkruimten in de toekomst worden gewijzigd. 

## <a name="apps-and-organizational-content-packs"></a>Apps en organisatie-inhoudspakketten
Apps zijn verbeterde organisatie-inhoudspakketten. Inhoudspakketten zijn niet beschikbaar in de preview voor nieuwe werkruimten. Nadat de nieuwe werkruimte-ervaring algemeen beschikbaar is gesteld, kunt u geen inhoudspakketten gebruiken in de nieuw gemaakte werkruimten. Begin met het migreren van uw inhoudspakketten naar apps als u dat nog niet hebt gedaan.

## <a name="video-apps-and-app-workspaces"></a>Video: apps en app-werkruimten
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licenties voor apps
Elk lid van een app-werkruimte heeft een Power BI Pro-licentie nodig. Voor app-gebruikers zijn er twee opties.

* Optie 1: alle zakelijke gebruikers moeten **Power BI Pro**-licenties hebben om uw app te bekijken. 
* Optie 2: als uw app zich in een Power BI Premium-capaciteit bevindt, kunnen gratis gebruikers in uw organisatie de app-inhoud bekijken. Lees [Wat is Power BI Premium?](service-premium.md) voor meer informatie.

## <a name="publish-your-app"></a>Uw app publiceren
Wanneer de dashboards en rapporten in uw werkruimte klaar zijn, kiest u welke dashboards en rapporten u wilt publiceren en publiceert u deze vervolgens als een app. U kunt een directe koppeling naar een breder publiek verzenden, of ze kunnen uw app vinden op het tabblad Apps door naar **Download and explore more apps from AppSource** (Meer apps downloaden en verkennen vanuit AppSource) te gaan. 

1. Kies in de lijstweergave van de werkruimte welke dashboards en rapporten u in de app wilt opnemen.

     ![Het dashboard selecteren om te publiceren](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Als u ervoor kiest om een rapport niet te publiceren, wordt er een waarschuwing naast het rapport en het bijbehorende dashboard weergegeven. U kunt de app nog steeds publiceren, maar in het bijbehorende dashboard ontbreken dan de tegels uit het rapport.

     ![Waarschuwing over bijbehorend dashboard](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecteer de knop **App publiceren** in de rechterbovenhoek om het proces voor het delen van alle inhoud in de werkruimte te starten.
   
     ![App publiceren](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Geef bij **Details** een beschrijving op om mensen te helpen de app te vinden. U kunt een achtergrondkleur instellen om de app te personaliseren.
   
     ![App-details](media/service-create-distribute-apps/power-bi-apps-details.png)

4. Bij **Inhoud** ziet u alle inhoud die wordt gepubliceerd als onderdeel van de app: alles wat u in de werkruimte hebt geselecteerd. U kunt ook de startpagina van de app instellen: het dashboard of rapport dat mensen als eerste zien wanneer ze naar uw app gaan. U kunt **Geen** kiezen. Vervolgens komen ze op een lijst van alle inhoud in de app te staan. 
   
     ![App-inhoud](media/service-create-distribute-apps/power-bi-apps-content.png)

5. Bepaal bij **Toegang** wie toegang tot de app heeft: ofwel iedereen in uw organisatie, of specifieke personen of Active Directory-beveiligingsgroepen. Als u toestemming hiervoor hebt, kunt u de app automatisch voor de ontvangers installeren. Een Power BI-beheerder kan deze instelling inschakelen in de Power BI-beheerportal. Lees meer over [hoe u automatisch een app installeert](#how-to-install-an-app-automatically-for-end-users).

    ![App-toegang](media/service-create-distribute-apps/power-bi-apps-access.png)

6. Wanneer u **Voltooien** selecteert, wordt er een bevestigingsbericht weergegeven dat de app gereed is om te publiceren. U kunt in het dialoogvenster dat na het voltooien wordt weergegeven, de URL voor de directe koppeling naar de app kopiëren en verzenden naar de personen waarmee u de app hebt gedeeld.
   
     ![App voltooien](media/service-create-distribute-apps/power-bi-apps-success.png)

Meer informatie over de [app-ervaring voor zakelijke gebruikers](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Uw gepubliceerde app wijzigen
Nadat u uw app hebt gepubliceerd, kunt u deze wijzigen of bijwerken. Het is gemakkelijk om de app bij te werken als u een beheerder of lid van de app-werkruimte of een inzender in een nieuwe app-werkruimte bent. 

1. Open de app-werkruimte die bij de app hoort. 
   
     ![Werkruimte openen](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Open het dashboard of het rapport. U kunt de gewenste wijzigingen aanbrengen.
   
     De app-werkruimte is uw faseringsplek. Uw wijzigingen worden pas live in de app wanneer u de app opnieuw publiceert. Dit betekent dat u wijzigingen kunt aanbrengen zonder dat dit de gepubliceerde apps beïnvloedt.  
 
3. Ga terug naar de lijst met inhoud van de app-werkruimte en selecteer **App bijwerken**.
   
     ![Knop App bijwerken](media/service-create-distribute-apps/power-bi-app-update-button.png)

4. Werk indien nodig **Details**, **Inhoud** en **Toegang** bij en selecteer **App bijwerken**.
   
     ![Knop App bijwerken](media/service-create-distribute-apps/power-bi-app-update-complete.png)

De mensen waarnaar u de app heeft gepubliceerd, zien automatisch de bijgewerkte versie van de app. 

## <a name="automatically-install-apps-for-end-users"></a>Automatisch apps voor eindgebruikers installeren
Apps leveren gegevens die uw eindgebruikers nodig hebben om hun werkzaamheden te kunnen uitvoeren. Als u toestemming van een beheerder krijgt, kunt u automatisch apps installeren voor eindgebruikers, zodat u eenvoudiger de juiste apps naar de juiste personen of groepen kunt distribueren. Uw app wordt automatisch weergegeven in de lijst met apps van uw eindgebruikers zodat het niet meer nodig is de apps in Microsoft AppSource te zoeken of een installatiekoppeling te volgen. Dit maakt het voor u eenvoudiger om standaardinhoud voor Power BI te implementeren voor uw gebruikers.

### <a name="how-to-install-an-app-automatically-for-end-users"></a>Procedure voor het automatisch installeren van een app voor eindgebruikers
Nadat de beheerder u machtigingen heeft verleend, hebt u een nieuwe optie om **de app automatisch te installeren**. Wanneer u het selectievakje inschakelt en **Voltooien** selecteert (of **App bijwerken** voor bestaande apps), wordt de app gepusht naar alle gebruikers of groepen die zijn gedefinieerd in de sectie **Machtigingen** van de app op het tabblad **Toegang**.

![Het pushen van apps inschakelen](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-were-pushed-to-them"></a>Hoe krijgen gebruikers de apps die naar ze zijn gepusht?
Nadat u een app hebt gepusht, wordt deze automatisch weergegeven in de lijst met apps. U kunt de apps cureren die specifieke gebruikers of gebruikersrollen in uw organisatie paraat moeten hebben.

![Het pushen van apps inschakelen](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Overwegingen voor het automatisch installeren van apps
Hier volgt een aantal zaken waarmee u rekening moet houden wanneer u apps naar eindgebruikers pusht:

* Het automatisch installeren van apps voor gebruikers kan enige tijd in beslag nemen. De meeste apps worden direct voor gebruikers geïnstalleerd, maar het pushen van apps kan enige tijd duren.  Hoe lang dit duurt, is afhankelijk van het aantal items in de app en het aantal personen dat toegang tot de app heeft. U wordt aangeraden apps buiten bedrijfsuren te pushen en te zorgen dat er voldoende tijd voor de installatie is voordat gebruikers de app nodig hebben. Voordat u een algemene mededeling over de beschikbaarheid van de app verzendt, kunt u bij meerdere gebruikers controleren of de app is geïnstalleerd.

* Vernieuw de browser. Voordat de gepushte app in de lijst Apps wordt weergegeven, kan het zijn dat gebruikers de browser moeten vernieuwen of moeten sluiten en vervolgens opnieuw moeten openen.

* Als gebruikers de app niet direct in de lijst met apps zien, moeten ze de browser vernieuwen of sluiten en opnieuw openen.

* Probeer gebruikers niet te overspoelen met apps. Zorg ervoor dat u niet te veel apps pusht, zodat gebruikers het gevoel hebben dat de vooraf geïnstalleerde apps ook daadwerkelijk nuttig voor ze zijn. Voor een goed afstemming van de timing is het verstandig te bepalen wie apps naar eindgebruikers mag pushen. U kunt in uw organisatie een contactpersoon toewijzen die verantwoordelijk is voor het pushen van apps naar eindgebruikers.

* Gastgebruikers die een uitnodiging niet hebben geaccepteerd, krijgen geen apps die automatisch voor hen worden geïnstalleerd.  

## <a name="unpublish-an-app"></a>Een app publiceren ongedaan maken
Elk lid van een app-werkruimte kan het publiceren van de app ongedaan maken.

>[!NOTE]
>Wanneer u de publicatie van een app ongedaan maakt, verliezen gebruikers van de app hun aanpassingen. Dit betekent dat persoonlijke bladwijzers, opmerkingen of abonnementen die bij de inhoud van de app horen, verloren gaan. Maak de publicatie van een app alleen ongedaan als u deze moet verwijderen.
> 
> 

* Selecteer in een app-werkruimte het weglatingsteken (**...**) in de rechterbovenhoek > **Publicatie van app ongedaan maken**.
  
     ![Publicatie van app ongedaan maken](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Met deze actie wordt de app verwijderd voor iedereen waarnaar u deze hebt gepubliceerd, waarna ze geen toegang meer tot de app hebben. De app-werkruimte en de inhoud ervan worden niet verwijderd.

## <a name="next-steps"></a>Volgende stappen
* [Een app-werkruimte maken](service-create-workspaces.md)
* [Apps in Power BI installeren en gebruiken](consumer/end-user-apps.md)
* [Power BI-apps voor externe services](service-connect-to-services.md)
* [Power BI-beheerportal](https://docs.microsoft.com/power-bi/service-admin-portal)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
