---
title: Problemen oplossen bij het starten van Power BI Desktop
description: Problemen oplossen bij het starten van Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 01/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8d33973f1a11050d104399c98866fdae0ffb1f8a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404888"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Problemen oplossen met het openen van Power BI Desktop

In Power BI Desktop kunnen gebruikers die een eerdere versie van de *On-premises gegevensgateway van Power BI* hebben geïnstalleerd en deze uitvoeren, Power BI Desktop mogelijk niet openen, vanwege beheerbeleidsbeperkingen die met de On-premises gateway van Power BI zijn ingesteld voor named pipes op de lokale computer.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Problemen met de On-premises gegevensgateway en Power BI Desktop oplossen

U kunt het probleem met de On-premises gegevensgateway op drie manieren oplossen, zodat Power BI Desktop weer kan worden geopend:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Oplossing 1: De nieuwste versie van de On-premises gegevensgateway van Power BI installeren

In de nieuwste versie van de On-premises gegevensgateway van Power BI worden geen named pipe-beperkingen op de lokale computer ingesteld, en kan Power BI Desktop juist worden geopend. Als u de On-premises gegevensgateway van Power BI wilt blijven gebruiken, is de aanbevolen oplossing om deze bij te werken. U kunt de [nieuwste versie van de On-premises gegevensgateway van Power BI](https://go.microsoft.com/fwlink/?LinkId=698863) downloaden. Dit is een rechtstreekse downloadkoppeling naar het uitvoerbare bestand voor de installatie.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Oplossing 2: De Microsoft-service voor de On-premises gegevensgateway van Power BI verwijderen of stoppen

U kunt de On-premises gegevensgateway van Power BI verwijderen wanneer u deze niet meer nodig hebt. Of u kunt de Microsoft-service voor de On-premises gegevensgateway van Power BI stoppen. Hierdoor wordt de beleidsbeperking verwijderd en kan Power BI Desktop worden geopend.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Oplossing 3: Power BI Desktop uitvoeren met administratorbevoegdheden

U kunt in plaats hiervan Power BI Desktop starten als beheerder. Ook dan kan Power BI Desktop zonder problemen worden geopend. De aanbevolen oplossing is en blijft echter het installeren van de meest recente versie van de On-premises gegevensgateway van Power BI, zoals eerder is beschreven.

Power BI Desktop is ontworpen met een architectuur op basis van meerdere processen, en verschillende van deze processen communiceren met behulp van named pipes van Windows. Er kunnen andere processen zijn die deze named pipes verstoren. De meestvoorkomende reden voor dergelijke interferentie is beveiliging, waaronder situaties waarin antivirussoftware of firewalls de pipes blokkeren of verkeer omleiden naar een specifieke poort. Dit probleem kan mogelijk worden opgelost door Power BI Desktop te openen met administratorbevoegdheden. Als u niet kunt openen met administratorbevoegdheden, vraagt u de beheerder om te bepalen op basis van welke beveiligingsregels named pipes niet juist communiceren. Voeg Power BI Desktop en de bijbehorende respectieve subprocessen vervolgens toe aan acceptatielijsten.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Problemen oplossen bij het verbinden met SQL Server

Als u verbinding wilt maken met een SQL Server-database, ziet u mogelijk een foutbericht met tekst die lijkt op de volgende tekst:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

U kunt het probleem vaak oplossen door Power BI Desktop als beheerder te openen voordat u de SQL Server-verbinding tot stand brengt.

Nadat u Power BI Desktop hebt geopend als beheerder en de verbinding tot stand hebt gebracht, worden de vereiste DLL-bestanden juist geregistreerd. Hierna hoeft u Power BI Desktop niet meer te openen als beheerder.

## <a name="get-help-with-other-launch-issues"></a>Hulp krijgen bij andere problemen

Wij proberen zo veel mogelijk problemen met Power BI Desktop te behandelen. Wij kijken regelmatig naar problemen waar veel klanten last van hebben en nemen ze in onze artikelen op.

Als het probleem met het openen van Power BI Desktop niet is gerelateerd aan de On-premises gegevensgateway, of als de eerder beschreven oplossingen niet werken, kunt u een ondersteuningsincident indienen bij de *ondersteuning voor Power BI* (<https://support.powerbi.com>) zodat wij u kunnen helpen bij het identificeren en oplossen van het probleem.

Als u in de toekomst meer problemen ondervindt met Power BI Desktop, is het handig om tracering in te schakelen en logboekbestanden te verzamelen. Logboekbestanden kunnen helpen bij het isoleren en identificeren van het probleem. Als u tracering wilt inschakelen, kiest u **Bestand** > **Opties en instellingen** > **Opties**. Selecteer **Diagnostische gegevens**, en selecteer vervolgens **Tracering inschakelen**. Power BI Desktop moet worden uitgevoerd om deze optie te kunnen instellen. Dit is handig bij toekomstige problemen met betrekking tot het openen van Power BI Desktop.
