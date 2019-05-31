---
title: PowerShell-cmdlets, REST-API's en .NET SDK voor Power BI-beheerders
description: Meer informatie over de manieren waarop u Power BI kunt beheren via scripts en programmeer-API's.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 86a90396c82a597e8b4f535b71e029bfa21328a4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187229"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>PowerShell-cmdlets, REST-API's en .NET SDK voor het beheer van Power BI
Met Power BI kunnen beheerders algemene taken uitvoeren met PowerShell-cmdlets. Verder biedt het REST-API's en een .NET SDK voor het ontwikkelen van beheerdersoplossingen. Dit onderwerp bevat een lijst met cmdlets met de bijbehorende SDK-methode en het REST API-eindpunt. Zie deze onderwerpen voor meer informatie:

- PowerShell [downloaden](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) en [documentatie](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API-[documentatie](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK [downloaden](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> De onderstaande cmdlets moeten worden aangeroepen met `-Scope Organization` om voor beheerstaken te kunnen gebruiken op basis van de tenant.

| **Naam van cmdlet** | **Aliassen** | **SDK-methode** | **REST API-eindpunt** | **Beschrijving** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N.v.t. | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Hiermee haalt u de gegevensbronnen voor een bepaalde gegevensset op. |
| `Get-PowerBIDataset` | N.v.t. | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Hiermee haalt u de volledige lijst met gegevenssets in een Power BI-tenant op. |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Hiermee haalt u de volledige lijst met werkruimten in een Power BI-tenant op. |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | Hiermee voegt u een gebruiker als lid aan een opgegeven werkruimte toe. |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Hiermee verwijdert u een gebruiker uit de lijst met leden van de opgegeven werkruimte. |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | Hiermee herstelt u een verwijderde werkruimte. |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | Hiermee werkt u de eigenschappen van een opgegeven werkruimte bij. |
| `Get-PowerBIDataset -WorkspaceId` | N.v.t. | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | Hiermee haalt u de gegevenssets binnen een opgegeven werkruimte op. |
| `Get-PowerBIReport` | N.v.t. | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Hiermee haalt u de volledige lijst met rapporten in een Power BI-tenant op. |
| `Get-PowerBIDashboard` | N.v.t. | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Hiermee haalt u de volledige lijst met dashboards in een Power BI-tenant op. |
| `Get-PowerBIDashboard -WorkspaceId` | N.v.t. | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Hiermee haalt u de dashboards binnen een opgegeven werkruimte op. |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Hiermee haalt u de tegels van een opgegeven dashboard op. |
| `Get-PowerBIReport` | N.v.t. | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | Hiermee haalt u de rapporten binnen een opgegeven werkruimte op. |
| `Get-PowerBIImport` | N.v.t. | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Hiermee haalt u de volledige lijst met importbewerkingen in een Power BI-tenant op. |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N.v.t. | N.v.t. | Meld u aan bij Power BI en start een sessie. |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N.v.t. | N.v.t. | Meld u af bij Power BI en sluit vervolgens de bestaande sessie. |
| `Invoke-PowerBIRestMethod`| N.v.t. | N.v.t. | N.v.t. | Verzend willekeurige REST API-aanroepen naar Power BI. |
| `Get-PowerBIAccessToken`| N.v.t. | N.v.t. | N.v.t. | Verkrijg het Power BI-toegangstoken in een sessie. |
| `Resolve-PowerBIError`| N.v.t. | N.v.t. | N.v.t. | Haal gedetailleerde gegevens over fouten voor mislukte cmdlet- aanroepen op. |
