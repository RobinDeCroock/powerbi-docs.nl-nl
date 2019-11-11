---
title: Power BI Desktop downloaden
description: Power BI Desktop downloaden en installeren
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 9f503ad8d5ae7b26a87da4e1d6664315b6119652
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878234"
---
# <a name="get-power-bi-desktop"></a>Power BI Desktop downloaden
Met **Power BI Desktop** kunt u geavanceerde query's, modellen en rapporten samenstellen die gegevens visualiseren. Met **Power BI Desktop** kunt u gegevensmodellen bouwen, rapporten maken en uw werk delen door dit te publiceren naar de Power BI-service.  **Power BI Desktop** is gratis te downloaden.

U kunt **Power BI Desktop** downloaden op twee manieren die in de volgende secties worden beschreven:

* Rechtstreeks **downloaden** (een pakket downloaden en installeren op uw computer)
* Installeren als een app uit de **Microsoft Store**

In beide gevallen krijgt u de nieuwste versie van **Power BI Desktop** op uw computer, maar er zijn enkele verschillen waar u op moet letten. Deze worden beschreven in de volgende secties.

## <a name="download-power-bi-desktop"></a>Power BI Desktop downloaden
Als u de meest recente versie van **Power BI Desktop** wilt downloaden, selecteert het downloadpictogram in de rechterbovenhoek van de Power BI-service en selecteert u **Power BI Desktop**.

![De nieuwste versie van Power BI Desktop downloaden](media/desktop-get-the-desktop/getpbid_downloads.png)

U kunt de nieuwste versie van Power BI Desktop ook downloaden van de volgende downloadpagina:

* [**Power BI Desktop downloaden** (zowel de 32-bits als de 64-bits versie)](https://powerbi.microsoft.com/desktop).
  
  [![De nieuwste versie van Power BI Desktop downloaden](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Ongeacht de manier waarop u **Power BI Desktop** downloadt, wordt u, wanneer het eenmaal is gedownload, gevraagd het installatiebestand uit te voeren:

![Het Power BI Desktop-installatiebestand uitvoeren](media/desktop-get-the-desktop/download-desktop-exe.png)

Vanaf de release van juli 2019 wordt **Power BI Desktop** geleverd als één EXE-installatiepakket dat alle ondersteunde talen bevat. Er zijn afzonderlijke EXE-bestanden voor 32-bits en 64-bits versies. Vanaf de release van september 2019 zijn de .msi-pakketten afgeschaft en is er een .exe-bestand nodig voor de installatie. Deze aanpak maakt distributie, updates en installatie (met name voor beheerders) veel eenvoudiger en handiger. U kunt ook opdrachtregelparameters gebruiken om het installatieproces aan te passen, zoals beschreven in de sectie [Opdrachtregelopties gebruiken tijdens de installatie](#using-command-line-options-during-installation) verderop in dit artikel.

Zodra u het installatiepakket start, wordt **Power BI Desktop** als toepassing geïnstalleerd en wordt het op het bureaublad uitgevoerd.

![Power BI Desktop toepassing wordt op uw bureaublad uitgevoerd](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Het is niet mogelijk om zowel de gedownloade (MSI) versie als de **Microsoft Store**-versie van **Power BI Desktop** tegelijk op dezelfde computer te installeren (soms ook wel een *side-by-side* installatie genoemd).
> 
> 

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installeren als een app uit de Microsoft Store
U kunt **Power BI Desktop** ook downloaden uit de Microsoft Store via de volgende koppeling:

* [**Power BI Desktop** installeren via de **Microsoft Store**](https://aka.ms/pbidesktopstore)

  ![Power BI Desktop aanschaffen via de Microsoft Store](media/desktop-get-the-desktop/getpbid_04.png)

Er zijn enkele voordelen als u **Power BI Desktop** ophaalt vanuit de Microsoft Store:

* **Automatische updates**: Windows downloadt de nieuwste versie automatisch op de achtergrond zodra deze beschikbaar is, zodat uw versie altijd up-to-date is.
* **Kleinere downloads**: de **Microsoft Store** zorgt ervoor dat alleen de onderdelen die zijn gewijzigd in elke update naar uw computer worden gedownload, wat resulteert in kleinere downloads voor elke update.
* **Geen beheerdersbevoegdheden vereist**: wanneer u het pakket rechtstreeks downloadt en installeert, werkt de installatie alleen als u een beheerder bent. Wanneer u **Power BI Desktop** downloadt via de Microsoft Store, zijn beheerdersbevoegdheden *niet* vereist.
* **IT-distributie ingeschakeld**: de **Microsoft Store**-versie kan eenvoudiger worden geïmplementeerd of *gedistribueerd* naar iedereen in uw organisatie en **Power BI Desktop** kan beschikbaar worden gesteld via de **Microsoft Store voor bedrijven**.
* **Taaldetectie**: de **Microsoft Store**-versie omvat alle ondersteunde talen en controleert welke taal wordt gebruikt op de computer steeds wanneer het wordt gestart. Dit is ook van invloed op de lokalisatie van modellen die worden gemaakt in **Power BI Desktop**. Ingebouwde datumhiërarchieën komen bijvoorbeeld overeen met de taal die **Power BI Desktop** gebruikte toen het PBIX-bestand werd gemaakt.

Er gelden enkele overwegingen en beperkingen voor de installatie van **Power BI Desktop** vanuit de Microsoft Store, waaronder:

* Als u de SAP-connector gebruikt, moet u uw SAP-stuurprogrammabestanden mogelijk verplaatsen de map *Windows\System32*.
* Bij het installeren van **Power BI Desktop** vanuit de Microsoft Store worden gebruikersinstellingen uit de EXE-versie niet gekopieerd. Mogelijk moet u opnieuw verbinding maken met uw recente gegevensbronnen en uw referenties voor gegevensbronnen opnieuw invoeren. 

> [!NOTE]
> Het is niet mogelijk om zowel de gedownloade (MSI) versie als de **Microsoft Store**-versie van **Power BI Desktop** tegelijk op dezelfde computer te installeren (soms ook wel een *side-by-side* installatie genoemd). U moet **Power BI Desktop** handmatig verwijderen voordat u het downloadt uit de **Microsoft Store**
> 
> [!NOTE]
> De Power BI Report Server-versie van **Power BI Desktop** is een afzonderlijke installatie die verschilt van de versies die in dit artikel worden besproken. Zie [Een Power BI-rapport maken voor Power BI Report Server](report-server/quickstart-create-powerbi-report.md) voor informatie over de Report Server-versie van **Power BI Desktop**.
> 
> 

## <a name="using-power-bi-desktop"></a>Power BI Desktop gebruiken
Wanneer u **Power BI Desktop** start, wordt er een *welkomstscherm* weergegeven.

![Welkomstscherm Power BI Desktop](media/desktop-get-the-desktop/getpbid_05.png)

Als dit de eerste keer is dat u **Power BI Desktop** gebruikt (als de installatie geen upgrade is), wordt u gevraagd een formulier in te vullen en enkele vragen te beantwoorden of u aan te melden bij de **Power BI-service** voordat u kunt verdergaan.

Vervolgens kunt gegevensmodellen of rapporten gaan maken en deze delen met anderen in de Power BI-service. De koppelingen onder **Meer informatie** aan het einde van dit artikel leiden naar handleidingen die u helpen aan de slag te gaan met **Power BI Desktop**.

## <a name="minimum-requirements"></a>Minimale vereisten
De volgende lijst bevat de minimale vereisten voor het uitvoeren van **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 of hoger
* .NET 4.5
* Internet Explorer 10 of hoger
* **Werkgeheugen (RAM):** ten minste 1 GB beschikbaar, 1,5 GB of meer aanbevolen.
* **Beeldscherm:** ten minste 1440x900 of 1600x900 (16:9) aanbevolen. Lagere resoluties zoals 1024x768 of 1280x800 worden niet aanbevolen aangezien bepaalde besturingselementen (bijvoorbeeld om het opstartscherm te sluiten) buiten die resoluties worden weergegeven.
* **Beeldscherminstellingen van Windows:** als uw beeldscherminstellingen zo zijn geconfigureerd dat de grootte van tekst, apps en andere items wordt gewijzigd naar meer dan 100%, ziet u mogelijk bepaalde dialoogvensters niet die moeten worden gesloten of waarop u moet reageren om door te gaan met het gebruik van **Power BI Desktop**. Als u dit probleem ondervindt, controleert u uw **beeldscherminstellingen** door te gaan naar **Instellingen > Systeem > Beeldscherm** in Windows en met de schuifregelaar de weergave weer in te stellen op 100%.
* **CPU:** 1 GHz (gigahertz) of snellere x86- of x64-bits processor aanbevolen.

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

We willen dat uw ervaring met Power BI Desktop altijd fantastisch is. Het kan natuurlijk altijd gebeuren dat er een probleem is met Power BI Desktop. In dit gedeelte vindt u daarom oplossingen of suggesties voor eventuele problemen die kunnen optreden. 

### <a name="using-command-line-options-during-installation"></a>Opdrachtregelopties gebruiken tijdens de installatie 

Wanneer u Power BI Desktop installeert, kunt u eigenschappen en opties instellen met opdrachtregelschakelaars. Dit is vooral handig voor beheerders die de installatie van Power BI Desktop tussen organisaties beheren of faciliteren. Deze opties zijn van toepassing op MSI- en EXE-installaties. 


|Opdrachtregeloptie  |Gedrag  |
|---------|---------|
|-q, -quiet, -s, -silent     |installatie op de achtergrond         |
|-passive     |alleen de voortgangsbalk wordt weergegeven tijdens de installatie         |
|-norestart     |de vereiste voor opnieuw opstarten van de computer wordt onderdrukt         |
|-forcerestart     |de computer wordt na de installatie opnieuw opgestart zonder prompt         |
|-promptrestart     |de gebruiker wordt gevraagd of de computer opnieuw moet worden opgestart (standaard)         |
|-l<>, -log<>     |de installatie wordt vastgelegd in een specifiek bestand, met het bestand dat is opgegeven in < >         |
|-uninstall     |de installatie van Power BI Desktop wordt ongedaan gemaakt         |
|-repair     |de installatie wordt hersteld (of wordt geïnstalleerd als deze nog niet is geïnstalleerd)         |
|-package, -update     |Power BI Desktop wordt geïnstalleerd (standaard, zolang -uninstall of -repair niet is opgegeven)         |

U kunt ook de volgende **syntaxisparameters** gebruiken die worden opgegeven met de syntaxis "PROPERTY=VALUE":

|Parameter  |Betekenis  |
|---------|---------|
|ACCEPT_EULA     |Vereist een waarde van 1 om de gebruiksrechtovereenkomst automatisch te accepteren         |
|ENABLECXP     |Met een waarde van 1 wordt er ingeschreven in het klantervaringsprogramma dat de gebruikstelemetrie van het product vastlegt         |
|INSTALLDESKTOPSHORTCUT     |Met een waarde van 1 wordt een snelkoppeling op het bureaublad geplaatst         |
|INSTALLLOCATION     |Bestandspad naar de locatie waar u wilt installeren         |
|LANGUAGE     |Taalcode, bijvoorbeeld en-US, de-DE of pr-BR, om de standaardtaal van de toepassing te forceren. Als er geen taal wordt opgegeven, geeft Power BI Desktop de taal van het Windows-besturingssysteem weer. Dit kan door de gebruiker worden gewijzigd in het dialoogvenster Opties.         |
|REG_SHOWLEADGENDIALOG     |Met een waarde van 0 wordt het dialoogvenster dat zichtbaar is voordat u zich hebt aangemeld bij Power BI Desktop uitgeschakeld         |

U kunt het bijvoorbeeld uitvoeren met de volgende syntaxis om zonder gebruikersinterface en in het Duits te installeren: 

```“-quiet LANG=de-DE ACCEPT_EULA=1”```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Power BI Desktop installeren op externe machines

Als u Power BI Desktop implementeert bij uw gebruikers met een hulpprogramma waarvoor een Windows-installatiebestand (.msi-bestand) nodig is, kunt u het .msi-bestand uitpakken uit het .exe-bestand van de Power BI Desktop-installatie. Gebruik externe hulpprogramma's als bijvoorbeeld WiX Toolset om dit te doen.

> [!NOTE]
> Aangezien WiX Toolset een extern product is, kunnen de opties zonder kennisgeving worden gewijzigd. Raadpleeg hun documentatie voor de actueelste informatie en neem met hen contact op voor hulp.

* Download en installeer op de computer waarop u het Power BI Desktop-installatieprogramma hebt gedownload de nieuwste versie van de WiX Toolset van de WiX-website op https://wixtoolset.org/.
* Open als beheerder een opdrachtregelvenster en navigeer naar de map waar u de WiX Toolset hebt geïnstalleerd.
* Voer de volgende opdracht uit: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Voer bijvoorbeeld de volgende opdracht uit:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

* De uitvoermap bevat een map met de naam *AttachedContainer* waarin de .msi-bestanden zich bevinden.


### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problemen bij het gebruik van eerdere versies van Power BI Desktop

Sommige gebruikers ondervinden een fout die overeenkomt met de volgende als ze een verouderde versie van **Power BI Desktop** gebruiken: 

    "We weren't able to restore the saved database to the model" 

Dit probleem wordt meestal opgelost door de huidige versie van Power BI Desktop bij te werken.

### <a name="disabling-notifications"></a>Meldingen uitschakelen
Het is raadzaam om te upgraden naar de nieuwste versie van Power BI Desktop omdat u dan beschikt over verbeteringen op het gebied van functies, prestaties, stabiliteit en andere aspecten. Sommige organisaties willen mogelijk niet dat gebruikers kunnen upgraden naar elke nieuwe versie. U kunt meldingen voor nieuwe versies uitschakelen door met de volgende stappen het register aan te passen:

1. Ga in Register-editor naar *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop*.
2. Maak hier een nieuwe vermelding met de volgende instellingen: *REG_DWORD : DisableUpdateNotification*
3. Stel de waarde van deze nieuwe vermelding in op **1**.

U moet de computer opnieuw opstarten om de wijziging door te voeren.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop geladen met een gedeeltelijk scherm

In bepaalde omstandigheden, zoals bij bepaalde configuraties van de schermresolutie, bestaat de kans dat sommige gebruikers van Power BI Desktop inhoud zien bedekt met grote zwarte gebieden. Dit is meestal het gevolg van recente updates van het besturingssysteem die van invloed zijn op de manier waarop items worden weergegeven, en dit probleem wordt dus niet veroorzaakt door de manier waarop Power BI Desktop inhoud presenteert. Ongeacht de oorzaak zijn grote zwarte gebieden natuurlijk niet erg indrukwekkend als visualisaties. U kunt dit probleem oplossen door de volgende stappen uit te voeren:

1. Druk op de Start-toets en typ het woord *wazig* in de zoekbalk die wordt weergegeven.
2. Selecteer in het dialoogvenster dat verschijnt de optie: *Windows apps laten verbeteren zodat deze geen wazig beeld geven.*
3. Start Power BI Desktop opnieuw.

Dit probleem wordt mogelijk opgelost in een volgende versie van Windows. 
 

## <a name="next-steps"></a>Volgende stappen
Nadat u **Power BI Desktop** hebt geïnstalleerd, helpen de volgende onderwerpen u snel aan de slag te gaan:

* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
* [Query Overview with Power BI Desktop](desktop-query-overview.md) (Queryoverzicht met Power BI Desktop)
* [Data Sources in Power BI Desktop](desktop-data-sources.md) (Gegevensbronnen in Power BI Desktop)
* [Connect to Data in Power BI Desktop](desktop-connect-to-data.md) (Verbinding maken met gegevens in Power BI Desktop)
* [Shape and Combine Data with Power BI Desktop](desktop-shape-and-combine-data.md) (Gegevens vormgeven en combineren met Power BI Desktop)
* [Common Query Tasks in Power BI Desktop](desktop-common-query-tasks.md) (Algemene querytaken in Power BI Desktop)   

