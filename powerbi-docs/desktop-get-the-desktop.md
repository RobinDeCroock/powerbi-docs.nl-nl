---
title: Power BI Desktop gebruiken
description: Power BI Desktop downloaden en installeren
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 6c2c41221e4a199d6a5d3a800f3820746ef7389a
ms.sourcegitcommit: 8b300151b5c59bc66bfef1ca2ad08593d4d05d6a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2020
ms.locfileid: "76888357"
---
# <a name="get-power-bi-desktop"></a>Power BI Desktop gebruiken
Met Power BI Desktop kunt u geavanceerde query's, modellen en rapporten samenstellen die de gegevens visualiseren. Met Power BI Desktop kunt u gegevensmodellen bouwen, rapporten maken en uw werk delen door dit te publiceren naar de Power BI-service. Power BI Desktop is gratis te downloaden.

U kunt Power BI Desktop downloaden op twee manieren die in de volgende secties worden beschreven:

* [Installeren als een app uit de Microsoft Store](#install-as-an-app-from-the-microsoft-store).
* [Rechtstreeks downloaden, als uitvoerbaar bestand dat u downloadt en installeert op uw computer](#download-power-bi-desktop-directly).

In beide gevallen krijgt u de nieuwste versie van Power BI Desktop op uw computer, maar er zijn enkele verschillen waar u op moet letten. Deze worden beschreven in de volgende secties.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installeren als een app uit de Microsoft Store
Er zijn een aantal manieren om toegang te krijgen tot de meest recente versie van Power BI Desktop vanuit de Microsoft Store. 

1. Gebruik een van de volgende opties om de pagina **Power BI Desktop** van de Microsoft Store te openen:

   - Open een browser en ga rechtstreeks naar de [pagina Power BI Desktop](https://aka.ms/pbidesktopstore) van de Microsoft Store.

    - Selecteer in de [Power BI-service](https://docs.microsoft.com/power-bi/service-get-started) het pictogram **Downloaden** in de rechterbovenhoek en selecteer **Power BI Desktop**.

      ![Power BI Desktop via de Power BI-service downloaden](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Ga naar de [Power BI Desktop-productpagina](https://powerbi.microsoft.com/desktop/) en selecteer vervolgens **Gratis downloaden**.
  
2. Wanneer u op de pagina **Power BI Desktop** van de Microsoft Store bent, selecteert u **Installeren**.

     ![Power BI Desktop aanschaffen via de Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Er zijn enkele voordelen als u Power BI Desktop ophaalt vanuit de Microsoft Store:

* **Automatische updates**: Windows downloadt de nieuwste versie automatisch op de achtergrond zodra deze beschikbaar is, zodat uw versie altijd up-to-date is.
* **Kleinere downloads**: Microsoft Store zorgt ervoor dat alleen de onderdelen die zijn gewijzigd in elke update naar uw computer worden gedownload, wat resulteert in kleinere downloads voor elke update.
* **Geen beheerdersbevoegdheden vereist**: Wanneer u het pakket rechtstreeks downloadt en installeert, werkt de installatie alleen als u een beheerder bent. Als u Power BI Desktop downloadt via de Microsoft Store, zijn beheerdersbevoegdheden *niet* vereist.
* **IT-totalisatie is ingeschakeld**: Via de Microsoft Store voor Bedrijven kunt u Power BI Desktop eenvoudiger implementeren of *uitrollen* naar iedereen in uw organisatie

* **Taaldetectie**: De Microsoft Store-versie omvat alle ondersteunde talen en controleert elke keer dat het programma wordt gestart welke taal op de betreffende computer wordt gebruikt. Deze taalondersteuning is ook van invloed op de lokalisatie van modellen die zijn gemaakt in Power BI Desktop. Ingebouwde datumhiërarchieën komen bijvoorbeeld overeen met de taal die Power BI Desktop gebruikt wanneer het .pbix-bestand wordt gemaakt.

De volgende overwegingen en beperkingen zijn van toepassing wanneer u Power BI Desktop installeert vanuit de Microsoft Store:

* Als u de SAP-connector gebruikt, moet u uw SAP-stuurprogrammabestanden mogelijk verplaatsen de map *Windows\System32*.
* Bij het installeren van Power BI Desktop vanuit de Microsoft Store worden gebruikersinstellingen uit de EXE-versie niet gekopieerd. Mogelijk moet u opnieuw verbinding maken met uw recente gegevensbronnen en uw referenties voor gegevensbronnen opnieuw invoeren. 

> [!NOTE]
> De Power BI Report Server-versie van Power BI Desktop is een afzonderlijke installatie die verschilt van de versies die in dit artikel worden besproken. Zie [Een Power BI-rapport maken voor Power BI Report Server](report-server/quickstart-create-powerbi-report.md) voor informatie over de Report Server-versie van Power BI Desktop.
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Power BI Desktop rechtstreeks downloaden
  
  Als u het uitvoerbare bestand van Power BI Desktop wilt downloaden vanuit het Downloadcentrum, selecteert u **Downloaden** op de pagina [Downloadcentrum](https://www.microsoft.com/download/details.aspx?id=58494). Geef vervolgens een 32-bits of 64-bits installatiebestand op om te downloaden.

  ![Het Power BI Desktop-installatiebestand opgeven](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Power BI Desktop installeren na het downloaden
Nadat u het installatiebestand hebt gedownload, wordt u gevraagd het uit te voeren.

Vanaf de release van juli 2019 wordt Power BI Desktop geleverd als één EXE-installatiepakket dat alle ondersteunde talen bevat, met een apart .exe-bestand voor de 32-bits en 64-bits versies. Vanaf de release van september 2019 zijn de .msi-pakketten afgeschaft en is er een .exe-bestand nodig voor de installatie. Deze aanpak maakt distributie, updates en installatie (met name voor beheerders) veel eenvoudiger en handiger. U kunt ook opdrachtregelparameters gebruiken om het installatieproces aan te passen, zoals beschreven in [Opdrachtregelopties gebruiken tijdens de installatie](#using-command-line-options-during-installation).

Nadat u het installatiepakket hebt gestart, wordt Power BI Desktop als toepassing geïnstalleerd en wordt het op het bureaublad uitgevoerd.

![Power BI Desktop setup uitvoeren](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Het is niet mogelijk om zowel de gedownloade (MSI) versie (verouderd) als de Microsoft Store-versie van Power BI Desktop tegelijk op dezelfde computer te installeren (soms ook wel een *side-by-side* installatie genoemd). Verwijder Power BI Desktop handmatig voordat u het downloadt uit de Microsoft Store.
> 

## <a name="using-power-bi-desktop"></a>Power BI Desktop gebruiken
Wanneer u Power BI Desktop start, wordt er een welkomstscherm weergegeven.

![Welkomstscherm Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Als u Power BI Desktop voor de eerste keer gebruikt (dat wil zeggen: de installatie is geen upgrade), wordt u gevraagd een formulier in te vullen of u aan te melden bij de Power BI-service voordat u kunt doorgaan.

Vervolgens kunt gegevensmodellen of rapporten gaan maken en deze delen met anderen in de Power BI-service. Raadpleeg de sectie [Volgende stappen](#next-steps) voor koppelingen naar handleidingen waarmee u aan de slag kunt gaan met Power BI Desktop.

## <a name="minimum-requirements"></a>Minimale vereisten
De volgende lijst bevat de minimale vereisten voor het uitvoeren van Power BI Desktop:

* Windows 7 / Windows Server 2008 R2 of hoger
* .NET 4.5
* Internet Explorer 10 of hoger
* Werkgeheugen (RAM): ten minste 1 GB beschikbaar, 1,5 GB of meer aanbevolen.
* Weergave: ten minste 1440x900 of 1600x900 (16:9) aanbevolen. Lagere resoluties zoals 1024x768 of 1280x800 worden niet aanbevolen aangezien bepaalde besturingselementen (bijvoorbeeld om het opstartscherm te sluiten) buiten die resoluties worden weergegeven.
* Beeldscherminstellingen van Windows: Als uw beeldscherminstellingen zo zijn geconfigureerd dat de grootte van tekst, apps en andere items wordt gewijzigd naar meer dan 100%, ziet u mogelijk bepaalde dialoogvensters niet waarmee u moet werken om door te gaan met het gebruik van Power BI Desktop. Als u dit probleem ondervindt, controleert u uw beeldscherminstellingen in Windows door te gaan naar **Instellingen** > **Systeem** > **Beeldscherm** en met de schuifregelaar de weergave weer in te stellen op 100%.
* CPU: 1 GHz (gigahertz) of snellere 32- of 64-bits x86-processor aanbevolen.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

We willen dat uw ervaring met Power BI Desktop fantastisch is. Omdat het kan gebeuren dat er een probleem is met Power BI Desktop, vindt u in dit gedeelte oplossingen of suggesties voor eventuele problemen die kunnen optreden. 

### <a name="using-command-line-options-during-installation"></a>Opdrachtregelopties gebruiken tijdens de installatie 

Wanneer u Power BI Desktop installeert, kunt u eigenschappen en opties instellen met opdrachtregelschakelaars. Deze instellingen zijn vooral handig voor beheerders die de installatie van Power BI Desktop tussen organisaties beheren of faciliteren. Deze opties zijn van toepassing op MSI- en EXE-installaties. 


|Opdrachtregeloptie  |Gedrag  |
|---------|---------|
|-q, -quiet, -s, -silent     |Stille installatie         |
|-passive     |De voortgangsbalk alleen weergeven tijdens de installatie         |
|-norestart     |De vereiste voor opnieuw opstarten van de computer onderdrukken         |
|-forcerestart     |De computer na de installatie zonder te vragen opnieuw opstarten         |
|-promptrestart     |De gebruiker vragen of de computer opnieuw moet worden opgestart (standaard)         |
|-l<>, -log<>     |De installatie vastleggen in een specifiek bestand, met het bestand dat is opgegeven in < >         |
|-uninstall     |De installatie van Power BI Desktop ongedaan maken         |
|-repair     |De installatie herstellen (of installeren als deze nog niet is geïnstalleerd)         |
|-package, -update     |Power BI Desktop installeren (standaard, zolang -uninstall of -repair niet is opgegeven)         |

U kunt ook de volgende syntaxisparameters gebruiken, die u hebt opgegeven met de syntaxis *property=value*:

|Parameter  |Betekenis  |
|---------|---------|
|ACCEPT_EULA     |Vereist een waarde van 1 om de gebruiksrechtovereenkomst automatisch te accepteren         |
|ENABLECXP     |Met een waarde van 1 wordt er ingeschreven in het klantervaringsprogramma waarin de gebruikstelemetrie van het product is vastgelegd         |
|INSTALLDESKTOPSHORTCUT     |Met de waarde 1 wordt een snelkoppeling op het bureaublad geplaatst         |
|INSTALLLOCATION     |Bestandspad naar de locatie waar u wilt installeren         |
|LANGUAGE     |De taalcode (bijvoorbeeld en-US, de-DE of pr-BR) om de standaardtaal van de toepassing te forceren. Als u geen taal opgeeft, geeft Power BI Desktop de taal van het Windows-besturingssysteem weer. U kunt deze instelling wijzigen in het dialoogvenster **Opties**.         |
|REG_SHOWLEADGENDIALOG     |Met de waarde 0 wordt het dialoogvenster dat zichtbaar is voordat u zich hebt aangemeld bij Power BI Desktop uitgeschakeld.         |
|DISABLE_UPDATE_NOTIFICATION     |Met de waarde 1 worden meldingen over updates uitgeschakeld.         |


U kunt Power BI Desktop bijvoorbeeld uitvoeren met de volgende opties en parameters om zonder gebruikersinterface en in het Duits te installeren: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Power BI Desktop installeren op externe machines

Als u Power BI Desktop implementeert bij uw gebruikers met een hulpprogramma waarvoor een Windows-installatiebestand (.msi-bestand) nodig is, kunt u het .msi-bestand uitpakken uit het .exe-bestand van de Power BI Desktop-installatie. Gebruik een hulpprogramma van derden, zoals de WiX-toolset.

> [!NOTE]
> Aangezien WiX Toolset een extern product is, kunnen de opties zonder kennisgeving worden gewijzigd. Raadpleeg hun documentatie voor de meest actuele informatie en neem met hen contact op voor hulp.

1. Installeer op de computer waarop u het Power BI Desktop-installatieprogramma hebt gedownload de nieuwste versie van de [WiX Toolset](https://wixtoolset.org/).
2. Open als beheerder een opdrachtregelvenster en navigeer naar de map waar u de WiX Toolset hebt geïnstalleerd.
3. Voer de volgende opdracht uit: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Bijvoorbeeld:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    De uitvoermap bevat een map met de naam *AttachedContainer* waarin de .msi-bestanden zich bevinden.


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemen bij het gebruik van eerdere versies van Power BI Desktop

Sommige gebruikers zien een foutmelding die overeenkomt met het volgende bericht als ze een verouderde versie van Power BI Desktop gebruiken: 

*Kan de opgeslagen database niet terugzetten in het model* 

Dit probleem wordt meestal opgelost door de huidige versie van Power BI Desktop bij te werken.

### <a name="disabling-notifications"></a>Meldingen uitschakelen
Het is raadzaam om te upgraden naar de nieuwste versie van Power BI Desktop omdat u dan beschikt over verbeteringen op het gebied van functies, prestaties, stabiliteit en andere aspecten. Sommige organisaties willen mogelijk niet dat gebruikers kunnen upgraden naar elke nieuwe versie. U kunt meldingen voor nieuwe versies uitschakelen door met de volgende stappen het register aan te passen:

1. Ga in Register-editor naar de sleutel **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Maak een nieuwe **REG_DWORD**-vermelding in de sleutel met de volgende naam: **DisableUpdateNotification**.
3. Stel de waarde van deze nieuwe vermelding in op **1**.
4. Start de computer opnieuw op om de wijziging van kracht te laten worden.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop geladen met een gedeeltelijk scherm

In bepaalde omstandigheden, zoals bij bepaalde configuraties van de schermresolutie, bestaat de kans dat sommige gebruikers van Power BI Desktop inhoud zien bedekt met grote zwarte gebieden. Dit probleem is meestal het gevolg van recente updates van het besturingssysteem die van invloed zijn op de manier waarop items worden weergegeven; dit probleem wordt dus niet veroorzaakt door de manier waarop Power BI Desktop inhoud presenteert. Volg deze stappen om dit probleem op te lossen:

1. Druk op de toets **Start** en typ het woord *wazig* in de zoekbalk die wordt weergegeven.
2. Selecteer in het dialoogvenster dat verschijnt de optie: **Windows apps laten verbeteren zodat deze geen wazig beeld geven.**
3. Start Power BI Desktop opnieuw.

Dit probleem wordt mogelijk opgelost in een latere versie van Windows. 
 

## <a name="next-steps"></a>Volgende stappen
Nadat u Power BI Desktop hebt geïnstalleerd, kunt u het volgende materiaal raadplegen om snel aan de slag te gaan:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Queryoverzicht in Power BI Desktop](desktop-query-overview.md)
* [Gegevensbronnen in Power BI Desktop](desktop-data-sources.md)
* [Verbinding maken met gegevens in Power BI Desktop](desktop-connect-to-data.md)
* [Gegevens vormgeven en combineren in Power BI Desktop](desktop-shape-and-combine-data.md)
* [Algemene querytaken in Power BI Desktop](desktop-common-query-tasks.md)   

