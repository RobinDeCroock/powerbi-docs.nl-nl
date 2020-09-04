---
title: Verbindingsreeksen voor gegevensbronnen wijzigen met PowerShell
description: Wijzig de verbindingsreeksen voor gegevensbronnen met behulp van API's in PowerShell - Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 09/01/2020
ms.author: maggies
ms.openlocfilehash: 69aa11216624416f005dcb2e47d1b818204ae7ec
ms.sourcegitcommit: 89ce1777a85b9fc476f077cbe22978c6cf923603
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89286723"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Wijzig de verbindingsreeksen voor gegevensbronnen in Power BI-rapporten met PowerShell - Power BI Report Server


U kunt de verbindingsreeks van gegevensbronnen wijzigen van Power BI-rapporten die worden gehost in Power BI Report Server door PowerShell te gebruiken om met de nodige API's te communiceren. 

> [!NOTE]
> Deze functionaliteit werkt momenteel alleen voor DirectQuery. Binnenkort is ondersteuning beschikbaar voor importeren en gegevens vernieuwen.

1. Installeer de Power BI Report Server PowerShell-commandlets. Zoek de commandlets en installatie-instructies op [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

    Installeer de module `ReportingServicesTools` rechtstreeks uit de [PowerShell Gallery](https://www.powershellgallery.com/packages/ReportingServicesTools/) met de volgende opdracht.

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. Haal de bestaande gegevensbrongegevens op voor het Power BI-bestand via de PowerShell-commandlets:

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Voor het weergeven van informatie over de eerste gegevensbron in het Power BI-rapport: 

    ```powershell
    $dataSources[0]
    ```

3. Werk indien nodig de verbinding en referentiegegevens bij. Als u de verbindingsstring bijwerkt en de gegevensbron gebruikmaakt van opgeslagen gegevens, moet u het accountwachtwoord opgeven. 

    Een verbindingsreeks voor een gegevensbron bijwerken:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Het referentietype voor de gegevensbron wijzigen:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    De gebruikersnaam en het wachtwoord voor de gegevensbron wijzigen:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Sla de bijgewerkte referenties opnieuw op de server op.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Volgende stappen

[Gegevensbronnen voor gepagineerde rapporten in Power BI Report Server](connect-data-sources.md) 

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
