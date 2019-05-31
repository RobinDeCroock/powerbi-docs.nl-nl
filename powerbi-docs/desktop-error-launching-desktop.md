---
title: Problemen oplossen bij het starten van Power BI Desktop
description: Problemen oplossen bij het starten van Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 19dc98b4f402176b2ae511236015ea25d7e4178b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454427"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Problemen oplossen als Power BI Desktop niet kan worden gestart
In **Power BI Desktop** kunnen gebruikers die een eerdere versie van de **On-premises gegevensgateway van Power BI** hebben geïnstalleerd en uitvoeren, Power BI Desktop mogelijk niet starten vanwege beheerbeleidsbeperkingen die door de on-premises gateway van Power BI zijn ingesteld voor named pipes op de lokale computer. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Problemen met de On-premises gegevensgateway en Power BI Desktop oplossen
U kunt het probleem met de On-premises gegevensgateway op drie manieren oplossen, zodat Power BI Desktop weer kan worden gestart:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Oplossing 1: De nieuwste versie van de On-premises gegevensgateway van Power BI installeren
In de nieuwste versie van de On-premises gegevensgateway van Power BI worden geen named pipe-beperkingen op de lokale computer ingesteld, en kan Power BI Desktop correct worden gestart. Als u de On-premises gegevensgateway van Power BI wilt blijven gebruiken, wordt deze oplossing aanbevolen. U kunt de nieuwste versie van de On-premises gegevensgateway van Power BI downloaden vanaf [deze locatie](https://go.microsoft.com/fwlink/?LinkId=698863). Dit is een rechtstreekse downloadkoppeling naar het uitvoerbare bestand voor de installatie.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Oplossing 2: De Windows-service voor de On-premises gegevensgateway van Power BI verwijderen of stoppen
Als u de On-premises gegevensgateway van Power BI niet meer nodig hebt, kunt u deze verwijderen of kunt u de Windows-service voor de On-premises gegevensgateway van Power BI stoppen zodat de beleidsbeperking wordt verwijderd en Power BI Desktop kan worden gestart.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Oplossing 3: Power BI Desktop uitvoeren met administratorbevoegdheden
U kunt eventueel ook Power BI Desktop starten als beheerder. Ook dan kan Power BI Desktop zonder problemen worden gestart. De aanbevolen oplossing is en blijft echter de meest recente versie van de On-premises gegevensgateway van Power BI te installeren, zoals eerder in dit artikel is beschreven.

Het is belangrijk te weten dat Power BI Desktop is ontworpen met een architectuur op basis van meerdere processen, en dat verschillende van deze processen communiceren met behulp van named pipes van Windows. Er kunnen andere processen zijn die deze named pipes verstoren. De meestvoorkomende reden voor dergelijke interferentie is beveiliging, waaronder situaties waarin antivirussoftware of firewalls de pipes kunnen blokkeren of verkeer omleiden naar een specifieke poort. Dit probleem kan mogelijk worden opgelost door Power BI Desktop te starten met administratorbevoegdheden. Als opstarten met administratorbevoegdheden niet mogelijk is, neem dan contact op met de beheerder om te bepalen welke toegepaste beveiligingsregels de communicatie met named pipes verhinderen, en zet Power BI Desktop en de betreffende subprocessen op de whitelist.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Problemen oplossen bij het verbinden met SQL Server
Als er een foutbericht wordt weergegeven dat lijkt op het volgende terwijl u verbinding maakt met een SQL Server-database, kunt u dit probleem vaak verhelpen door **Power BI Desktop** als beheerder te openen en daarna verbinding te maken met SQL Server:

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

Na het openen als beheerder en het maken van de verbinding, worden de vereiste DLL-bestanden juist geregistreerd. Hierna hoeft u Power BI Desktop niet meer te openen als beheerder.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Hulp bij andere problemen met het starten van Power BI Desktop
Wij proberen zo veel mogelijk problemen met **Power BI Desktop** te behandelen. Wij kijken regelmatig naar problemen waar veel klanten last van hebben en nemen ze in onze artikelen op.

Als het probleem met het starten van **Power BI Desktop** niet ligt aan de on-premises gegevensgateway of als de eerder beschreven oplossingen niet werken, kunt u een ondersteuningsincident indienen bij de [ondersteuning voor Power BI](https://support.powerbi.com) (https://support.powerbi.com) zodat wij u kunnen helpen bij het identificeren en oplossen van uw probleem.

Voor andere problemen die zich in de toekomst kunnen voordoen in **Power BI Desktop** (hopelijk zijn dat er geen of slechts weinig), is het handig om tracering in te schakelen en logboekbestanden te verzamelen, zodat het probleem beter kan worden geïsoleerd en geïdentificeerd. U schakelt tracering als volgt in: selecteer **Bestand > Opties en instellingen > Opties** en selecteer vervolgens **Diagnose**. Schakel daarna het selectievakje **Tracering inschakelen** onder *Diagnostische opties* in. We beseffen dat **Power BI Desktop** actief moet zijn om deze optie te kunnen inschakelen, wat nuttiger is voor toekomstige problemen bij het starten van **Power BI Desktop**.

