---
title: Een upgrade uitvoeren voor Power BI Report Server
description: Leer hoe u een upgrade uitvoert voor Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 68494784e3c5b21c0c3e15bd5a3a816fd07e5f8b
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99043546"
---
# <a name="upgrade-power-bi-report-server"></a>Een upgrade uitvoeren voor Power BI Report Server

Leer hoe u een upgrade uitvoert voor Power BI Report Server.

 **Downloaden** ![pictogram downloaden](media/upgrade/download.png "pictogram downloaden")

Ga naar [on-premises rapportage met Power bi Report Server](https://powerbi.microsoft.com/report-server/)om Power bi Report Server te downloaden en Power BI Desktop voor Power bi Report Server.

## <a name="before-you-begin"></a>Voordat u begint

Voordat u een upgrade uitvoert van een rapportserver, is het raadzaam de volgende stappen uit te voeren om een back-up van de rapportserver te maken.

### <a name="backing-up-the-encryption-keys"></a>Een back-up van uw versleutelingsleutels maken

Maak een back-up van de versleutelingssleutels wanneer u voor het eerst een installatie van de rapportserver configureert. Maak ook steeds een back-up van de sleutels wanneer u de identiteit van de serviceaccounts of de naam van de computer wijzigt. Zie [Back-ups van Reporting Services-versleutelingssleutels maken en herstellen](/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys) voor meer informatie.

### <a name="backing-up-the-report-server-databases"></a>Back-ups van de rapportserverdatabases maken

Omdat een rapportserver is een staatloze server is, worden alle toepassingsgegevens opgeslagen in de **reportserver-** en **reportservertempdb-** databases die worden uitgevoerd op een exemplaar van SQL Server Database Engine. U kunt een van de ondersteunde methoden voor het maken van back-ups van SQL Server-databases gebruiken om een back-up te maken van de databases **reportserver** en **reportservertempdb**. Deze aanbevelingen zijn specifiek voor rapportserverdatabases:

* Gebruik het volledig-herstelmodel om een back-up van de database **reportserver** te maken.
* Gebruik het eenvoudig herstelmodel om een back-up van de database **reportservertempdb** te maken.
* U kunt voor elke database verschillend back-upschema's gebruiken. De enige reden om een back-up te maken van de database **reportservertempdb** is om te voorkomen dat u deze in het geval van een hardwarefout opnieuw moet maken. In het geval van een hardwarefout hoeft u de gegevens in **reportservertempdb** niet te herstellen, maar hebt u wel de tabelstructuur nodig. Als u **reportservertempdb** kwijtraakt, kunt u de database alleen herstellen door de rapportserverdatabase opnieuw te maken. Als u **reportservertempdb** opnieuw maakt, is het belangrijk dat deze dezelfde naam heeft als de primaire rapportserverdatabase.

Zie [Een back-up van SQL Server-databases maken en deze terugzetten](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases) voor meer informatie over het maken van back-ups en het terugzetten van relationele SQL Server-databases.

### <a name="backing-up-the-configuration-files"></a>Een back-up van de configuratiebestanden maken

Power BI-rapportserver gebruikt configuratiebestanden om de toepassingsinstellingen op te slaan. Maak een back-up van de bestanden wanneer u de server voor het eerst configureert en nadat u eventuele aangepaste extensies hebt geïmplementeerd. U moet back-ups maken van onder andere de volgende bestanden:

* config.json
* RSHostingService.exe.config
* Rsreportserver.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* Web.config voor de Report Server ASP.NET-toepassingen
* Machine.config voor ASP.NET

## <a name="upgrade-the-report-server"></a>Een upgrade voor de rapportserver uitvoeren

U kunt vrij eenvoudig een upgrade voor Power BI Reports Server uitvoeren. U hoeft slechts een paar stappen uit te voeren om de bestanden te installeren.

1. Zoek de locatie van PowerBIReportServer.exe en start het installatieprogramma.

2. Selecteer **Een upgrade voor Power BI Report Server uitvoeren**.

    ![Een upgrade uitvoeren van Power BI Report Server](media/upgrade/reportserver-upgrade1.png "Een upgrade uitvoeren voor Power BI Report Server")

3. Lees de licentievoorwaarden, ga hiermee akkoord en selecteer vervolgens **Upgrade uitvoeren**.

    ![Gebruiksrechtovereenkomst](media/upgrade/reportserver-upgrade-eula.png "Gebruiksrechtovereenkomst")

4. Nadat u de upgrade hebt uitgevoerd, kunt u **Report Server configureren** selecteren om Reporting Services Configuration Manager te starten of **Sluiten** selecteren om het installatieprogramma af te sluiten.

    ![Upgrade uitvoeren voor de configuratie](media/upgrade/reportserver-upgrade-configure.png)

## <a name="enable-microsoft-update-security-fixes-for-power-bi-report-server"></a>Microsoft Update-beveiligingspatches voor Power BI Report Server inschakelen

Power BI Report Server ontvangt beveiligingspatches via Microsoft Update. Als u deze wilt inschakelen, moet u zich handmatig aanmelden voor Microsoft Update.

1.  Open Windows Update in **Update- en beveiligingsinstellingen** op de computer waarop u zich wilt aanmelden.
2.  Selecteer **Geavanceerde opties**.
3.  Schakel het selectievakje **Updates voor andere Microsoft-producten ontvangen tijdens het bijwerken van Windows** in.

## <a name="upgrade-power-bi-desktop"></a>Een upgrade uitvoeren voor Power BI Desktop

Nadat u een upgrade van de rapport server hebt uitgevoerd, moet u ervoor zorgen dat alle Power BI rapport auteurs upgraden naar de versie van Power BI Desktop voor Power BI Report Server die overeenkomt met de-server.

## <a name="next-steps"></a>Volgende stappen

* [Administratoroverzicht](admin-handbook-overview.md)  
* [Power BI Desktop voor Power BI Report Server installeren](install-powerbi-desktop.md)  
* [Een installatie van Reporting Services verifiëren](/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
* [Het serviceaccount van de rapportserver configureren](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
* [De URL's van de rapportserver configureren](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
* [Configure a report server database connection](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager) (De verbinding van een rapportserverdatabase configureren)  
* [Een rapportserver initialiseren](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [SSL-verbindingen voor een rapportserver configureren](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [Windows-serviceaccounts en machtigingen configureren](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
* [Browserondersteuning voor Power BI Report Server](browser-support.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)