---
title: Een app publiceren in Power BI
description: Meer informatie over hoe u de nieuwe apps, die verzamelingen dashboards en rapporten omvatten, kunt publiceren.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: eccda071b6c6abc92640024c3587bafa71038dee
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66826650"
---
# <a name="publish-an-app-in-power-bi"></a>Een app publiceren in Power BI

In Power BI kunt u officieel verpakte inhoud maken en deze als een *app* naar een brede doelgroep distribueren. U maakt apps in *app-werkruimten*, waar u samen met uw collega's aan Power BI-inhoud kunt werken. Vervolgens kunt u de voltooide apps naar grote groepen mensen in uw organisatie publiceren. 

![Power BI-apps](media/service-create-distribute-apps/power-bi-new-apps.png)

Uw zakelijke gebruikers hebben vaak meerdere Power BI-dashboards en rapporten nodig voor hun bedrijfsvoering. Met Power BI-apps kunt u verzamelingen van dashboards en rapporten maken en deze apps naar uw hele organisatie of naar specifieke personen of groepen publiceren. Apps maken het u als beheerder of rapportmaker gemakkelijker om machtigingen voor deze verzamelingen te beheren.

Zakelijke gebruikers kunnen uw apps op een aantal verschillende manieren installeren:

- Ze kunnen uw app zoeken en installeren via Microsoft AppSource.
- U kunt ze een rechtstreekse koppeling sturen.
- U kunt de app automatisch installeren in de Power BI-accounts van uw collega's als uw Power BI-beheerder u hiervoor toestemming geeft.

U kunt de app maken met een eigen ingebouwde navigatie, zodat uw gebruikers eenvoudig de weg in uw inhoud kunnen vinden. Ze kunnen de inhoud van de app niet wijzigen. Ze kunnen wel bepaalde acties uitvoeren in de Power BI-service of een van de mobiele apps: filteren, markeren en de gegevens sorteren. Ze ontvangen automatisch updates en u kunt bepalen hoe vaak de gegevens worden vernieuwd. Meer informatie over de [app-ervaring voor zakelijke gebruikers](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenties voor apps
U hebt een Power BI Pro-licentie nodig om apps bij te werken of te maken. Voor*app-consumenten* zijn er twee opties.

* Optie 1: alle zakelijke gebruikers moeten **Power BI Pro**-licenties hebben om uw app te bekijken. 
* Optie 2: als uw app-werkruimte zich in een Power BI Premium-capaciteit bevindt, kunnen gratis gebruikers in uw organisatie de app-inhoud bekijken. Lees [Wat is Power BI Premium?](service-premium.md) voor meer informatie.

## <a name="publish-your-app"></a>Uw app publiceren
Wanneer de dashboards en rapporten in uw werkruimte klaar zijn, kiest u welke dashboards en rapporten u wilt publiceren en publiceert u deze vervolgens als een app. 

1. Kies in de lijstweergave van de werkruimte welke dashboards en rapporten moeten worden **opgenomen in de app**.

     ![Het dashboard selecteren om te publiceren](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Als u ervoor kiest om een rapport waaraan een dashboard is gekoppeld, niet op te nemen, wordt er een waarschuwing naast het rapport weergegeven. U kunt de app nog steeds publiceren, maar het bijbehorende dashboard bevat dan niet de tegels uit het rapport.

     ![Waarschuwing over bijbehorend dashboard](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecteer de knop **App publiceren** in de rechterbovenhoek om vanuit de werkruimte een app te maken en te publiceren.
   
     ![App publiceren](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Geef bij **Setup** de naam en een beschrijving op, zodat mensen de app kunnen vinden. U kunt een themakleur instellen om de app te personaliseren. U kunt ook een koppeling naar een ondersteuningssite toevoegen.
   
     ![Uw app maken](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Bij **Navigatie** selecteert u de inhoud die moet worden gepubliceerd als onderdeel van de app. Vervolgens voegt u app-navigatie toe om de inhoud in de secties te ordenen. Zie [De navigatie-ervaring voor uw app ontwerpen](#design-the-navigation-experience-for-your-app) in dit artikel voor meer informatie.
   
     ![App-navigatie](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Bepaal bij **Machtigingen** wie toegang heeft tot de app en wat ze ermee kunnen doen. 
    - In [klassieke werkruimten](service-create-workspaces.md): iedereen in uw organisatie, specifieke personen of AAD-beveiligingsgroepen (Azure Active Directory).
    - In de [nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md): specifieke personen, AAD-beveiligingsgroepen en -distributielijsten en Office 365-groepen. Alle werkruimtegebruikers krijgen automatisch toegang tot de app voor de werkruimte.
    - U kunt app-gebruikers toestaan verbinding te maken met de onderliggende gegevenssets van de app met behulp van de machtiging Samenstellen. Deze gegevenssets worden weergegeven in de zoekervaringen voor gegevenssets.
    - U kunt app-gebruikers toestaan in hun Mijn werkruimte een kopie van rapporten in deze app te maken. 
    
    >[!IMPORTANT]
    >Als uw app afhankelijk is van gegevenssets uit andere werkruimten, is het uw verantwoordelijkheid om te controleren of alle app-gebruikers toegang tot de onderliggende gegevenssets hebben.
> 
>     


6. Als u deze instelling in de Power BI-beheerportal door uw Power BI-beheerder is ingeschakeld, kunt u de app automatisch voor de ontvangers installeren. Raadpleeg dit artikel voor meer informatie over het [automatisch installeren van een app](#automatically-install-apps-for-end-users).

     ![App-machtigingen](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Wanneer u **App publiceren** selecteert, wordt er een bevestigingsbericht weergegeven dat de app gereed is om te publiceren. In het dialoogvenster **Deze app delen** kunt u de URL kopiëren. De URL is een rechtstreekse koppeling naar deze app.
   
     ![App voltooien](media/service-create-distribute-apps/power-bi-apps-success.png)

U kunt deze rechtstreekse koppeling naar de mensen sturen waarmee u de app wilt delen. Ze kunnen uw app ook op het tabblad Apps vinden door naar **Download and explore more apps from AppSource** (Meer apps downloaden en verkennen vanuit AppSource) te gaan. Meer informatie over de [app-ervaring voor zakelijke gebruikers](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Uw gepubliceerde app wijzigen
Nadat u uw app hebt gepubliceerd, kunt u deze wijzigen of bijwerken. Als u een beheerder of lid van de nieuwe app-werkruimte bent, kunt u de app eenvoudig bijwerken. 

1. Open de app-werkruimte die bij de app hoort. 
   
     ![Werkruimte openen](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. U kunt de dashboards of rapporten naar wens aanpassen.
 
     De app-werkruimte is uw faseringsplek. Uw wijzigingen worden pas live in de app wanneer u de app opnieuw publiceert. Dit betekent dat u wijzigingen kunt aanbrengen zonder dat dit de gepubliceerde apps beïnvloedt.  
 
    > [!IMPORTANT]
    > Als u een rapport verwijdert en de app bijwerkt, verliezen de gebruikers van uw app alle aanpassingen, zoals bladwijzers, opmerkingen, enzovoort, zelfs als u het rapport later weer aan de app toevoegt.  
 
3. Ga terug naar de werkruimtelijst met inhoud en selecteer in de rechterbovenhoek **App bijwerken**.
   
1. Bijwerken **Setup**, **Navigatie** en **Machtigingen** en selecteer vervolgens zo nodig **App bijwerken**.
   
De mensen waarnaar u de app heeft gepubliceerd, zien automatisch de bijgewerkte versie van de app. 

## <a name="design-the-navigation-experience-for-your-app"></a>De navigatie-ervaring voor uw app ontwerpen
Met de optie **Nieuwe opbouwfunctie voor navigatie** kunt u een aangepaste navigatie voor uw app maken. De aangepaste navigatie zorgt ervoor dat uw gebruikers eenvoudiger inhoud in de app kunnen vinden en gebruiken. Voor bestaande apps is deze optie uitgeschakeld, maar voor nieuwe apps is deze optie standaard ingeschakeld.

Als de optie uitgeschakeld is, kunt u voor **Landingspagina van app** **Specifieke inhoud** selecteren, zoals een dashboard of rapport of **Geen** selecteren om eenvoudige lijst met inhoud voor de gebruiker weer te geven.

Wanneer u **Nieuwe opbouwfunctie voor navigatie** inschakelt, kunt u een aangepaste navigatie ontwerpen. Alle rapporten, dashboards en Excel-werkmappen die u opneemt in uw app, worden standaard weergegeven als een platte lijst. 

![App-navigatie](media/service-create-distribute-apps/power-bi-apps-navigation.png)

U kunt de app-navigatie als volgt verder aanpassen:
* U kunt met de pijl-omhoog of pijl-omlaag de volgorde van de items aanpassen. 
* U kun de namen van items in **Rapportdetails**, **Dashboarddetails** en **Werkmapdetails** wijzigen.
* U kun bepaalde items in de navigatie verbergen.
* U kunt de optie **Nieuw** gebruiken om **secties** aan groepsgerelateerde inhoud toe te voegen.
* U kunt met de optie **Nieuw** een **koppeling** naar een externe resource aan de linkernavigatie toevoegen. 

Wanneer u een **koppeling** aan **Koppelingsdetails** toevoegt, kunt u kiezen waar de koppeling wordt geopend. De standaardinstelling voor het openen van koppelingen is **Huidig tabblad**, maar u kunt ook de optie **Nieuw tabblad** of **Inhoudsgebied** selecteren. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Overwegingen voor het gebruik van de optie Nieuwe opbouwfunctie voor navigatie
Hier vindt u enkele algemene zaken waarmee u rekening moet houden wanneer u Nieuwe opbouwfunctie voor navigatie gebruikt:
* De rapportpagina's worden in het navigatiegebied van de app weergegeven als een uitvouwbare sectie
* Als u de optie Nieuwe opbouwfunctie voor navigatie uitschakelt en uw app vervolgens publiceert of bijwerkt, verliest u alle aanpassingen die u hebt aangebracht. U verliest bijvoorbeeld de secties, volgorde, koppelingen en aangepaste namen voor navigatie-items.

Wanneer u koppelingen aan uw app-navigatie toevoegt en de optie Inhoudsgebied selecteert:
* Zorg ervoor dat de koppeling kan worden ingesloten. Sommige services zorgen ervoor dat hun inhoud niet kan worden ingesloten in sites van derden, zoals Power BI.
* Het insluiten van inhoud van de Power BI-service, zoals rapporten of dashboards, in andere werkruimten wordt niet ondersteund. 
* Gebruik de systeemeigen insluitings-URL om vanaf de on-premises implementatie Power BI Report Server-inhoud in te sluiten. Gebruik de stappen in het gedeelte over [het maken van de Power BI Report Server-URL](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) om de URL te verkrijgen. Let erop dat de reguliere verificatieregels van toepassing zijn. Er is dus een VPN-verbinding met de on-premises server vereist om de inhoud weer te geven. 
* Bovenaan de ingesloten inhoud wordt een beveiligingswaarschuwing weergegeven om aan te geven dat de inhoud zich niet in Power BI bevindt.



## <a name="automatically-install-apps-for-end-users"></a>Automatisch apps voor eindgebruikers installeren
Als een beheerder machtigingen aan u toekent, kunt u de apps automatisch installeren door ze naar de eindgebruikers te *pushen*. Met deze pushfunctie kunt u gemakkelijker de juiste apps naar de juiste mensen of groepen distribueren. Uw app wordt automatisch weergegeven in de lijst met app-inhoud van uw eindgebruikers. Ze hoeven de app niet te zoeken in Microsoft AppSource en ze hoeven geen installatiekoppeling te volgen. Zie in het artikel over de Power BI-beheerportal hoe beheerders de functie voor het [pushen van apps naar eindgebruikers](service-admin-portal.md#push-apps-to-end-users) inschakelen.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Automatisch een app naar eindgebruikers pushen
Nadat de beheerder u machtigingen heeft verleend, hebt u een nieuwe optie om **de app automatisch te installeren**. Wanneer u het selectievakje inschakelt en **App publiceren** (of **App bijwerken** selecteert voor bestaande apps), wordt de app naar alle gebruikers of groepen gepusht die zijn gedefinieerd in de sectie **Machtigingen** van de app op het tabblad **Toegang**.

![Het pushen van apps inschakelen](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Hoe krijgen gebruikers de apps die u naar ze pusht?
Nadat u een app hebt gepusht, wordt deze automatisch weergegeven in hun lijst met apps. Zodoende kunt u de apps cureren die specifieke gebruikers of gebruikersrollen in uw organisatie paraat moeten hebben.

![Het pushen van apps inschakelen](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Overwegingen voor het automatisch installeren van apps
Hier volgt een aantal zaken waarmee u rekening moet houden wanneer u apps naar eindgebruikers pusht:

* Het automatisch installeren van apps voor gebruikers kan enige tijd in beslag nemen. De meeste apps worden direct voor gebruikers geïnstalleerd, maar het pushen van apps kan enige tijd duren.  Hoe lang dit duurt, is afhankelijk van het aantal items in de app en het aantal personen dat toegang tot de app heeft. U wordt aangeraden apps buiten bedrijfsuren te pushen en te zorgen dat er voldoende tijd voor de installatie is voordat gebruikers de app nodig hebben. Voordat u een algemene mededeling over de beschikbaarheid van de app verzendt, kunt u bij meerdere gebruikers controleren of de app is geïnstalleerd.

* Vernieuw de browser. Voordat de gepushte app in de lijst Apps wordt weergegeven, kan het zijn dat gebruikers de browser moeten vernieuwen of moeten sluiten en vervolgens opnieuw moeten openen.

* Als gebruikers de app niet direct in de lijst met apps zien, moeten ze de browser vernieuwen of sluiten en opnieuw openen.

* Probeer gebruikers niet te overspoelen met apps. Zorg ervoor dat u niet te veel apps pusht, zodat gebruikers het gevoel hebben dat de vooraf geïnstalleerde apps ook daadwerkelijk nuttig voor ze zijn. Voor een goed afstemming van de timing is het verstandig te bepalen wie apps naar eindgebruikers mag pushen. Wijs een contactpersoon binnen uw organisatie aan die verantwoordelijk is voor het pushen van apps naar eindgebruikers.

* Gastgebruikers die een uitnodiging niet hebben geaccepteerd, ontvangen geen apps die automatisch voor hen worden geïnstalleerd.  

## <a name="allowing-users-to-connect-to-the-apps-underlying-datasets"></a>Gebruikers toestaan verbinding te maken met de onderliggende gegevenssets van de app
Als u de optie selecteert waarmee u alle gebruikers toestaat verbinding te maken met de onderliggende gegevenssets van de app, ontvangen de app-gebruikers de machtiging Samenstellen voor de onderliggende gegevensset. Hiermee kunnen gebruikers [de app-gegevenssets in werkruimten gebruiken](service-datasets-across-workspaces.md) om te zoeken naar deze gegevenssets in Power BI Desktop en de ervaringen voor het ophalen van gegevens van de service, en om rapporten en dashboards met behulp van deze gegevenssets te maken. 

Wanneer u deze optie uitschakelt, krijgen de nieuwe gebruikers die u aan de app toevoegt, de machtiging Samenstellen niet meer. De bestaande machtigingen voor de onderliggende gegevenssets worden echter niet gewijzigd. U kunt de geleverde gebruikersinterface gebruiken om de machtiging Samenstellen handmatig van app-gebruikers te verwijderen die de machtiging niet langer mogen hebben. Meer informatie over de [Samenstellingsmachtiging](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="allowing-users-to-make-a-copy-of-the-reports-in-the-app"></a>Gebruikers toestaan een kopie van de rapporten in de app te maken
Door de optie **Gebruikers mogen een kopie van de rapporten in deze app maken** in te schakelen staat u gebruikers toe om rapporten in de app op te slaan in hun Mijn werkruimte. Ze kunnen vervolgens de rapporten aan hun unieke behoeften aanpassen. Voor deze optie moet **Gebruikers mogen verbinding maken met onderliggende gegevenssets van de app met de machtiging Samenstellen** zijn ingeschakeld. Deze mogelijkheid werkt op dezelfde manier als de nieuwe mogelijkheid om [rapporten van andere werkruimten te kopiëren](service-datasets-copy-reports.md).

## <a name="unpublish-an-app"></a>Een app publiceren ongedaan maken
Elk lid van een app-werkruimte kan het publiceren van de app ongedaan maken.

>[!IMPORTANT]
>Wanneer u de publicatie van een app ongedaan maakt, verliezen gebruikers van de app hun aanpassingen. Ze verliezen alle persoonlijke bladwijzers, opmerkingen of abonnementen die bij de inhoud van de app horen. Maak de publicatie van een app alleen ongedaan als u deze moet verwijderen.
> 
> 

* Selecteer in een app-werkruimte het weglatingsteken ( **...** ) in de rechterbovenhoek > **Publicatie van app ongedaan maken**.
  
     ![Publicatie van app ongedaan maken](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Met deze actie wordt de app verwijderd voor iedereen waarnaar u deze hebt gepubliceerd, waarna ze geen toegang meer tot de app hebben. De app-werkruimte en de inhoud ervan worden niet verwijderd.

## <a name="view-your-published-app"></a>Uw gepubliceerde app weergeven

Wanneer gebruikers uw app openen, zien ze in plaats van het standaard Power BI-navigatiedeelvenster aan de linkerkant de navigatie die u hebt gemaakt. De app-navigatie bevat de rapporten en dashboards in de secties die u hebt gedefinieerd. Dit gedeelte bevat ook de afzonderlijke pagina's in elk rapport, in plaats van alleen de naam van het rapport.

![App met navigatie](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Volgende stappen
* [Een app-werkruimte maken](service-create-workspaces.md)
* [Apps in Power BI installeren en gebruiken](consumer/end-user-apps.md)
* [Power BI-apps voor externe services](service-connect-to-services.md)
* [Power BI-beheerportal](https://docs.microsoft.com/power-bi/service-admin-portal)
* Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
