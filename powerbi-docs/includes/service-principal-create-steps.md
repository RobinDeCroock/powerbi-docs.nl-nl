---
title: App voor service-principal maken
description: App voor service-principal maken
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210737"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>Stap 2: een Azure AD-beveiligingsgroep maken

De service-principal heeft geen toegang tot uw Power BI-inhoud en -API's. Om de service-principal toegang te geven, maakt u een beveiligingsgroep in Azure AD en voegt u de gemaakte service-principal toe aan die beveiligingsgroep.

U kunt op twee manieren een Azure AD-beveiligingsgroep maken:
* Handmatig (in Azure)
* PowerShell gebruiken

### <a name="create-a-security-group-manually"></a>Handmatig een beveiligingsgroep maken

Als u handmatig een Azure-beveiligingsgroep wilt maken, volgt u de instructies in het artikel [Een basisgroep maken en leden toevoegen met Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Een beveiligingsgroep maken met PowerShell

Hieronder volgt een voorbeeldscript voor het maken van een nieuwe beveiligingsgroep en het toevoegen van een app aan die beveiligingsgroep.

>[!NOTE]
>Als u toegang tot service-principals wilt inschakelen voor de hele organisatie, slaat u deze stap over.

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Stap 3: de beheerdersinstellingen voor de Power BI-service inschakelen

Voordat een Azure AD-app toegang kan krijgen tot de Power BI-inhoud en -API's, moet een Power BI-beheerder toegang tot de service-principal inschakelen in de Power BI-beheerportal.

Voeg de beveiligingsgroep die u in Azure AD hebt gemaakt, toe aan de sectie Specifieke beveiligingsgroep in de **instellingen voor ontwikkelaars**.

>[!IMPORTANT]
>Service-principals hebben toegang tot alle tenantinstellingen waarvoor ze zijn ingeschakeld. Afhankelijk van uw beheerdersinstellingen bevat dit specifieke beveiligingsgroepen of de hele organisatie.
>
>Als u de toegang van de service-principal wilt beperken tot specifieke tenantinstellingen, staat u alleen toegang tot specifieke beveiligingsgroepen toe. U kunt ook een toegewezen beveiligingsgroep voor service-principals maken en deze uitsluiten van de gewenste tenantinstellingen.

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="Schermopname met de instellingen voor ontwikkelaars in de beheeropties in de Power BI-portal.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Stap 4: voeg de service-principal toe aan uw werkruimte

Als u uw Azure AD-app toegang wilt verlenen tot artefacten zoals rapporten, dashboards en gegevenssets in de Power BI-service, voegt u de entiteit van de service-principal toe als lid of beheerder aan uw werkruimte.

>[!NOTE]
>Deze sectie bevat instructies voor de gebruikersinterface. U kunt ook een service-principal aan een werkruimte toevoegen met behulp van de [API Groups - Add Group User](/rest/api/power-bi/groups/addgroupuser) (Groepen - Groepsgebruiker toevoegen).

1. Ga naar de werkruimte waarvoor u toegang wilt inschakelen, en selecteer in het menu **More** de optie **Workspace access**.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="Schermopname met de instellingen voor ontwikkelaars in de beheeropties in de Power BI-portal.":::

2. Voeg de service-principal als een **Admin** (beheerder) of **Member** (lid) toe aan de werkruimte.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="Schermopname met de instellingen voor ontwikkelaars in de beheeropties in de Power BI-portal.":::