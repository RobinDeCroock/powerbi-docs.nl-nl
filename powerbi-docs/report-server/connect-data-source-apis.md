---
title: Verbindingsreeksen voor gegevensbronnen wijzigen met PowerShell
description: Wijzig de verbindingsreeksen voor gegevensbronnen met behulp van API's in PowerShell - Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: 4e1947abe0fa0f17e1db92619f0aa7fba5df5575
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415468"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Wijzig de verbindingsreeksen voor gegevensbronnen in Power BI-rapporten met PowerShell - Power BI Report Server


Vanaf de release van Power BI Report Server in oktober 2020 schakelen we de mogelijkheid in om verbindingen bij te werken voor Power BI rapporten voor DirectQuery en Refresh.

> [!IMPORTANT]
> Dit is ook een belangrijke wijziging ten opzichte van de manier waarop u dit in eerdere releases kunt instellen. Raadpleeg [De verbindingsreeksen wijzigen voor gegevensbronnen in Power BI-rapporten met PowerShell - Power BI Report Server vóór oktober 2020](connect-data-source-apis-pre-oct-2020.md) als u een versie van Power BI Report Server van vóór oktober 2020 gebruikt

## <a name="prerequisites"></a>Vereisten:
- Download de release [Power BI Report Server en Power BI Desktop geoptimaliseerd voor Power BI Report Server](https://powerbi.microsoft.com/report-server/) van oktober 2020.
- Een rapport dat is opgeslagen met de versie van Power BI Desktop geoptimaliseerd voor Report Server van oktober 2020, waarbij **Verbeterde metagegevens van gegevensset** is ingeschakeld.
- Een rapport dat gebruikmaakt van verbindingen met parameters. Alleen rapporten met geparametriseerde verbindingen en databases kunnen na publicatie worden bijgewerkt.
- In dit voorbeeld worden de PowerShell-hulpprogramma's van Reporting Services gebruikt. U kunt hetzelfde doen met behulp van de nieuwe REST API's.

## <a name="create-a-report-with-parameterized-connections"></a>Een rapport met verbindingen met parameters maken
    
1. Een SQL Server-verbinding maken met een server. In het onderstaande voorbeeld wordt er verbinding gemaakt met de localhost met een database met de naam ReportServer, waarna gegevens worden opgehaald uit ExecutionLog.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="Verbinding maken met de SQL Server-database":::

    De M-query ziet er nu als volgt uit:

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Selecteer **Parameters beheren** op het lint Power Query-editor.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="Selecteer Parameters beheren":::

1.  Maak parameters voor de servernaam en databasenaam.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="Parameters beheren, Servernaam en Databasenaam instellen.":::


3. Bewerk de query voor de eerste verbinding en wijs de database en servernaam toe.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="De naam van de server en de database toewijzen":::

    De query ziet er nu als volgt uit:

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. Publiceer dat rapport naar de server. In dit voorbeeld heeft het rapport de naam executionlogparameter. De volgende afbeelding toont een voorbeeld van een pagina voor het beheren van gegevensbronnen.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="De pagina Gegevensbron beheren.":::

## <a name="update-parameters-using-the-powershell-tools"></a>Parameters bijwerken met de PowerShell-hulpprogramma's

1. Open PowerShell en installeer de meest recente Reporting Services-hulpprogramma's, gevolgd door de instructies op [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools).
    
2.  Gebruik de nieuwe REST DataModelParameters-API met behulp van de volgende PowerShell-aanroep om de parameter voor het rapport op te halen:

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. Het resultaat van deze aanroep wordt opgeslagen in een variabele:

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. Deze variabele wordt bijgewerkt met de waarden die u moet wijzigen.
5. Het resultaat van deze aanroep wordt opgeslagen in een variabele:

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. Met de bijgewerkte waarden kunnen we de commandlet `Set-RsRestItemDataModelParameters` gebruiken om de waarden in de server bij te werken:

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. Zodra de parameters zijn bijgewerkt, worden alle gegevensbronnen die aan de parameters zijn gebonden, bijgewerkt door de server. Als u teruggaat naar het dialoogvenster **Gegevensbron bewerken**, moet u referenties kunnen instellen voor de bijgewerkte server en database.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="Referenties instellen voor de bijgewerkte server en database.":::

## <a name="next-steps"></a>Volgende stappen

[Gegevensbronnen voor gepagineerde rapporten in Power BI Report Server](connect-data-sources.md) 

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
