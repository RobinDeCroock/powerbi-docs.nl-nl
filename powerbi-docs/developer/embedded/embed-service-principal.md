---
title: Service-principal met Power BI
description: Informatie over het registreren van een toepassing in Azure Active Directory met een service-principal en een toepassingsgeheim voor gebruik met ingesloten Power BI-inhoud.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 03/30/2020
ms.openlocfilehash: 7ae2752627e24c5de2feed372009061e523a3fc8
ms.sourcegitcommit: 34cca70ba84f37b48407d5d8a45c3f51fb95eb3c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80751627"
---
# <a name="embedding-power-bi-content-with-service-principal-and-application-secret"></a>Power BI-inhoud met service-principal en toepassingsgeheim insluiten

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

In dit artikel wordt de service-principal-verificatie met een *toepassings-id* en *toepassingsgeheim* beschreven.

## <a name="method"></a>Methode

Voer de volgende stappen uit om een service-principal en een toepassings-id met ingesloten analyses te gebruiken:

1. Maak een [Azure AD-app](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management).

    1. Maak het geheim van de Azure AD-app.
    
    2. Haal de *toepassings-id* en het *toepassingsgeheim* van de app op.

    >[!NOTE]
    >Deze stappen worden beschreven in **stap 1**. Zie het artikel [Een Azure AD-app maken](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal) voor meer informatie over het maken van een Azure AD-app.

2. Maak een Azure AD-beveiligingsgroep.

3. Schakel de beheerdersinstellingen voor de Power BI-service in.

4. Voeg de service-principal toe aan uw werkruimte.

5. Sluit uw inhoud in.

> [!IMPORTANT]
> Nadat u de service-principal voor gebruik met Power BI hebt ingeschakeld, zijn de AD-machtigingen van de toepassing niet meer geldig. De machtigingen van de toepassing worden dan beheerd via de Power BI-beheerportal.

## <a name="step-1---create-an-azure-ad-app"></a>Stap 1: een Azure AD-app maken

Maak een Azure AD-app met behulp van een van deze methoden:
* De app maken in de [Microsoft Azure-portal](https://portal.azure.com/#allservices)
* Maak de app met behulp van [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Een Azure AD-app maken in de Microsoft Azure-portal

1. Meld u aan bij [Microsoft Azure](https://portal.azure.com/#allservices).

2. Zoek naar **App-registraties** en klik op de koppeling **App-registraties**.

    ![Azure-app-registratie](media/embed-service-principal/azure-app-registration.png)

3. Klik op **Nieuwe registratie**.

    ![nieuwe registratie](media/embed-service-principal/new-registration.png)

4. Vul de vereiste gegevens in:
    * **Naam**: voer een naam in voor de toepassing
    * **Ondersteunde accounttypen**: selecteer het Azure AD-account dat u nodig hebt
    * (Optioneel) **Omleidings-URI**: voer een URI in, indien nodig

5. Klik op **Registreren**.

6. Na de app-registratie is de *toepassings-id* beschikbaar op het tabblad **Overzicht**. Kopieer de *toepassings-id* en sla deze op voor later gebruik.

    ![toepassings-id](media/embed-service-principal/application-id.png)

7. Klik op de tab **Certificaten en geheimen**.

     ![toepassings-id](media/embed-service-principal/certificates-and-secrets.png)

8. Klik op **Nieuw clientgeheim**

    ![nieuw clientgeheim](media/embed-service-principal/new-client-secret.png)

9. Voer in het venster *Een clientgeheim toevoegen* een beschrijving in, geef op wanneer u wilt dat het clientgeheim verloopt, en klik op **Toevoegen**.

10. Kopieer de waarde van *Clientgeheim* en sla deze op.

    ![waarde van clientgeheim](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Wanneer u dit venster verlaat, wordt de waarde van het clientgeheim verborgen en kunt u deze niet meer weergeven of kopiëren.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Een Azure AD-app maken met PowerShell

Deze sectie bevat een voorbeeldscript voor het maken van een nieuwe Azure AD-app met [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Stap 2: een Azure AD-beveiligingsgroep maken

De service-principal heeft geen toegang tot uw Power BI-inhoud en -API's. Om de service-principal toegang te geven, maakt u een beveiligingsgroep in Azure AD en voegt u de gemaakte service-principal toe aan die beveiligingsgroep.

U kunt op twee manieren een Azure AD-beveiligingsgroep maken:
* Handmatig (in Azure)
* PowerShell gebruiken

### <a name="create-a-security-group-manually"></a>Handmatig een beveiligingsgroep maken

Als u handmatig een Azure-beveiligingsgroep wilt maken, volgt u de instructies in het artikel [Een basisgroep maken en leden toevoegen met Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Een beveiligingsgroep maken met PowerShell

Hieronder volgt een voorbeeldscript voor het maken van een nieuwe beveiligingsgroep en het toevoegen van een app aan die beveiligingsgroep.

>[!NOTE]
>Als u toegang tot service-principals wilt inschakelen voor de hele organisatie, slaat u deze stap over.

```powershell
# Required to sign in as a tenant admin
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

![Beheerportal](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-as-an-admin-to-your-workspace"></a>Stap 4: de service-principal als een beheerder toevoegen aan uw werkruimte

Als u uw Azure AD-app toegang wilt verlenen tot artefacten zoals rapporten, dashboards en gegevenssets in de Power BI-service, voegt u de entiteit van de service-principal toe als lid of beheerder aan uw werkruimte.

>[!NOTE]
>Deze sectie bevat instructies voor de gebruikersinterface. U kunt ook een service-principal aan een werkruimte toevoegen met behulp van de [API Groups - Add Group User](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) (Groepen - Groepsgebruiker toevoegen).

1. Ga naar de werkruimte waarvoor u toegang wilt inschakelen, en selecteer in het menu **More** de optie **Workspace access**.

    ![Instellingen voor werkruimte](media/embed-service-principal/workspace-access.png)

2. Voeg de service-principal als een **Admin** (beheerder) of **Member** (lid) toe aan de werkruimte.

    ![Werkruimtebeheerder](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Stap 5: uw inhoud insluiten

U kunt nu uw inhoud insluiten in een voorbeeldtoepassing of in uw eigen toepassing.

* [Inhoud met behulp van de voorbeeldtoepassing insluiten](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Inhoud in uw toepassing insluiten](embed-sample-for-customers.md#embed-content-within-your-application)

Als de inhoud is ingesloten, bent u klaar voor de [overgang naar de productieomgeving](embed-sample-for-customers.md#move-to-production).

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* De service-principal werkt alleen met [nieuwe werkruimten](../../service-create-the-new-workspaces.md).
* **Mijn werkruimte** wordt niet ondersteund bij het gebruik van een service-principal.
* Toegewezen capaciteit is vereist voor het verplaatsen naar productie.
* U kunt zich niet aanmelden bij de Power BI-portal met behulp van een service-principal.
* Power BI-beheerdersrechten zijn vereist voor het inschakelen van de service-principal in instellingen voor ontwikkelaars in de Power BI-beheerportal.
* U kunt een on-premises gegevensgateway niet installeren of beheren met behulp van een service-principal.
* Voor [Insluiten voor uw organisatie](embed-sample-for-your-organization.md)-toepassingen kan geen service-principal worden gebruikt.
* Beheer van [gegevensstromen](../../service-dataflows-overview.md) wordt niet ondersteund.
* Service-principals bieden momenteel geen ondersteuning voor beheer-API's.
* Wanneer u de service-principal gebruikt met een [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)-gegevensbron, moet de service-principal zelf machtigingen hebben voor Azure Analysis Services-instanties. Het gebruik van een beveiligingsgroep die de service-principal voor dit doel bevat, werkt niet.

## <a name="next-steps"></a>Volgende stappen

* [Power BI Embedded voor uw klanten](embed-sample-for-customers.md)

* [Beveiliging op rijniveau met on-premises gegevensgateway met service-principal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)