---
title: Service-principalverificatie inschakelen voor alleen-lezen beheer-API's (preview)
description: Meer informatie over het inschakelen van Service-Principal-verificatie om het gebruik van alleen-lezen-beheer-API's toe te staan.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 02/04/2021
ms.author: painbar
ms.custom: ''
LocalizationGroup: Administration
ms.openlocfilehash: e255fbef8b29422ea7736e43adaa5e4197a6338f
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/05/2021
ms.locfileid: "99569940"
---
# <a name="enable-service-principal-authentication-for-read-only-admin-apis-preview"></a>Service-principalverificatie inschakelen voor alleen-lezen beheer-API's (preview)

Service-principal is een verificatiemethode die kan worden gebruikt om een Azure AD-toepassing (Azure Active Directory) toegang te geven tot inhoud en API's van de Power BI-service.
Wanneer u een Azure AD-app maakt, wordt er een [service-principal-object](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) gemaakt. Met het service-principal-object, ook wel de service-principal genoemd, kan Azure AD uw app verifiëren. Nadat de app is geverifieerd, heeft deze toegang tot Azure AD-tenantbronnen.

## <a name="method"></a>Methode

Voer de volgende stappen uit om service-principal-verificatie in te schakelen voor Power BI-API's met het kenmerk alleen-lezen:

1. [Maak een Azure AD-app](/azure/active-directory/develop/howto-create-service-principal-portal). U kunt deze stap overslaan als u al een Azure AD-app hebt die u wilt gebruiken. Noteer de app-id voor latere stappen. 
2. Maak een nieuwe **beveiligingsgroep** in Azure Active Directory. [Lees meer over het maken van een basisgroep en het toevoegen van leden met behulp van Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). U kunt deze stap overslaan als u al een beveiligingsgroep hebt die u wilt gebruiken.
    Zorg ervoor dat u **Beveiliging** selecteert als het groepstype.

    ![Schermopname van het dialoogvenster Nieuwe groep maken in de Azure-portal.](media/read-only-apis-service-principal-auth/azure-portal-new-group-dialog.png)

3. Voeg uw app-id toe als lid van de beveiligingsgroep die u hebt gemaakt. Hiervoor doet u het volgende:
    1. Ga naar **Azure Portal > Azure Active Directory > Groepen** en kies de beveiligingsgroep die u in stap 2 hebt gemaakt.
    1. Selecteer **Leden toevoegen**.
    Opmerking: Zorg ervoor dat voor de app die u gebruikt, geen Power BI-beheerdersrollen in de Azure-portal zijn ingesteld. U controleert dit als volgt: 
       * Meld u aan bij de **Azure-portal** als een globale beheerder, een toepassingsbeheerder of een cloudtoepassingsbeheerder. 
        * Selecteer achtereenvolgens **Azure Active Directory** en **Bedrijfstoepassingen**. 
        * Selecteer de toepassing die u toegang tot Power BI wilt verlenen. 
        * Selecteer **Machtigingen**. Zorg ervoor dat er geen Power BI-beheerderstoestemming-vereist-machtigingen zijn ingesteld voor deze toepassing. Zie [Het beheren van toestemming voor toepassingen en het evalueren van toestemmingsaanvragen](/azure/active-directory/manage-apps/manage-consent-requests) voor meer informatie. 
4. Schakel de beheerdersinstellingen voor de Power BI-service in. Om dit te doen:
    1. Meld u aan bij de Power BI-beheerportal. U moet een Power BI-beheerder zijn om de pagina met tenantinstellingen te kunnen weergeven.
    1. Onder **Instellingen voor beheerders-API** ziet u **Toestaan dat service-principals gebruikmaken van API's van Power BI (preview)** . Stel de wisselknop in op Ingeschakeld en selecteer het keuzerondje **Specifieke beveiligingsgroepen** en voeg de beveiligingsgroep die u in stap 2 hebt gemaakt toe in het tekstveld, zoals aangegeven in de volgende afbeelding.

        ![Schermopname van de tenantinstelling voor het toestaan van service-principals.](media/read-only-apis-service-principal-auth/allow-service-principals-tenant-setting.png)

 5. Begin met het gebruik van de beheer-API's met het kenmerk alleen-lezen. Hieronder ziet u de lijst met ondersteunde API's.

    >[!IMPORTANT]
    >Nadat u de service-principal voor gebruik met Power BI hebt ingeschakeld, zijn de Azure AD-machtigingen van de toepassing niet meer geldig. De machtigingen van de toepassing worden dan beheerd via de Power BI-beheerportal.

## <a name="supported-apis"></a>Ondersteunde API's

De service-principal ondersteunt momenteel de volgende API's:
* [GetGroupsAsAdmin](/rest/api/power-bi/admin/groups_getgroupsasadmin) met $expand voor dashboards, gegevenssets, rapporten en gegevensstromen 
* [GetDashboardsAsAdmin](/rest/api/power-bi/admin/dashboards_getdashboardsasadmin) met $expand-tegels
* [GetDatasourcesAsAdmin](/rest/api/power-bi/admin/datasets_getdatasourcesasadmin) 
* [GetDatasetToDataflowsLinksAsAdmin](/rest/api/power-bi/admin/datasets_getdatasettodataflowslinksingroupasadmin)
* [GetDataflowDatasourcesAsAdmin](/rest/api/power-bi/admin/dataflows_getdataflowdatasourcesasadmin) 
* [GetDataflowUpstreamDataflowsAsAdmin](/rest/api/power-bi/admin/dataflows_getupstreamdataflowsingroupasadmin) 
* [GetCapacitiesAsAdmin](/rest/api/power-bi/admin/getcapacitiesasadmin)
* [GetActivityLog](/rest/api/power-bi/admin/getactivityevents)
* [GetModifiedWorkspaces](/rest/api/power-bi/admin/workspaceinfo_getmodifiedworkspaces)
* [WorkspaceGetInfo](/rest/api/power-bi/admin/workspaceinfo_postworkspaceinfo)
* [WorkspaceScanStatus](/rest/api/power-bi/admin/workspaceinfo_getscanstatus)
* [WorkspaceScanResult](/rest/api/power-bi/admin/workspaceinfo_getscanresult)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* U kunt zich niet aanmelden bij de Power BI-portal met behulp van een service-principal.
* Power BI-beheerdersrechten zijn vereist voor het inschakelen van de service-principal in de instellingen voor de beheerders-API in de Power BI-beheerportal.