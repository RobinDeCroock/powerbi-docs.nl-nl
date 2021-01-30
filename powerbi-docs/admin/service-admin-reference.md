---
title: PowerShell-cmdlets, REST-API's en .NET Client-bibliotheken voor beheerders
description: Meer informatie over de manieren waarop u Power BI kunt beheren via scripts en programmeer-API's.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 2218889e170519e651127d4246ab61a7505735fb
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085591"
---
# <a name="powershell-cmdlets-rest-apis-and-net-client-library-for-power-bi-administration"></a>PowerShell-cmdlets, REST-API's en .NET SDK-clientbibliotheek voor het beheer van Power BI
Met Power BI kunnen beheerders algemene taken uitvoeren met PowerShell-cmdlets. Verder biedt het REST-API's en een .NET Client-bibliotheek voor het ontwikkelen van beheerdersoplossingen. Dit onderwerp bevat een lijst met cmdlets met de bijbehorende API's en het REST API-eindpunt. Raadpleeg voor meer informatie:

- PowerShell [downloaden](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) en [documentatie](/powershell/power-bi/overview?view=powerbi-ps&preserve-view=true)
- REST API-[documentatie](/rest/api/power-bi/admin)
- [Downloaden](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) vanuit .NET Client-bibliotheek

> De onderstaande cmdlets moeten worden aangeroepen met `-Scope Organization` om voor beheerstaken te kunnen gebruiken op basis van de tenant.

| **Naam van cmdlet** | **Aliassen** | **API** | **REST API-eindpunt** | **Beschrijving** |
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