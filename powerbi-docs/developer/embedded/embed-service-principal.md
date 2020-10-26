---
title: Power BI-inhoud insluiten met service-principal en een toepassingsgeheim
description: Meer informatie over het verifiëren voor ingesloten analyses met behulp van een Azure Active Directory Application Service-Principal en een toepassingsgeheim.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197726"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Power BI-inhoud insluiten met service-principal en een toepassingsgeheim

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

In dit artikel wordt de service-principal-verificatie met een *toepassings-id* en *toepassingsgeheim* beschreven.

>[!NOTE]
>We raden u aan uw backend-services te beveiligen met behulp van certificaten, in plaats van geheime sleutels.
>* [Meer informatie over het verkrijgen van toegangstokens van Azure AD met behulp van geheime sleutels of certificaten](/azure/architecture/multitenant-identity/client-assertion).
>* [Power BI-inhoud met service-principal en een certificaat insluiten](embed-service-principal-certificate.md).

## <a name="method"></a>Methode

Voer de volgende stappen uit om een service-principal en een toepassings-id met ingesloten analyses te gebruiken:

1. Maak een [Azure AD-app](/azure/active-directory/manage-apps/what-is-application-management).

    1. Maak het geheim van de Azure AD-app.
    
    2. Haal de *toepassings-id* en het *toepassingsgeheim* van de app op.

    >[!NOTE]
    >Deze stappen worden beschreven in **stap 1**. Zie het artikel [Een Azure AD-app maken](/azure/active-directory/develop/howto-create-service-principal-portal) voor meer informatie over het maken van een Azure AD-app.

2. Maak een Azure AD-beveiligingsgroep.

3. Schakel de beheerdersinstellingen voor de Power BI-service in.

4. Voeg de service-principal toe aan uw werkruimte.

5. Sluit uw inhoud in.

> [!IMPORTANT]
> Nadat u de service-principal voor gebruik met Power BI hebt ingeschakeld, zijn de AD-machtigingen van de toepassing niet meer geldig. De machtigingen van de toepassing worden dan beheerd via de Power BI-beheerportal.

## <a name="step-1---create-an-azure-ad-app"></a>Stap 1: een Azure AD-app maken

Maak een Azure AD-app met behulp van een van deze methoden:

* De app maken in de [Microsoft Azure-portal](https://portal.azure.com/#allservices)

* Maak de app met behulp van [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Een Azure AD-app maken in de Microsoft Azure-portal

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Klik op de tab **Certificaten en geheimen**.

     ![Een schermopname van het deelvenster Certificaten en geheimen voor een app in de Azure-portal.](media/embed-service-principal/certificates-and-secrets.png)


8. Klik op **Nieuw clientgeheim**

    ![Een schermopname van de knop Nieuw clientgeheim in het deelvenster Certificaten en geheimen.](media/embed-service-principal/new-client-secret.png)

9. Voer in het venster *Een clientgeheim toevoegen* een beschrijving in, geef op wanneer u wilt dat het clientgeheim verloopt, en klik op **Toevoegen**.

10. Kopieer de waarde van *Clientgeheim* en sla deze op.

    ![Een schermopname met een onleesbaar gemaakte geheime waarde in het deelvenster Certificaten en geheimen.](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Wanneer u dit venster verlaat, wordt de waarde van het clientgeheim verborgen en kunt u deze niet meer weergeven of kopiëren.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Een Azure AD-app maken met PowerShell

Deze sectie bevat een voorbeeldscript voor het maken van een nieuwe Azure AD-app met [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

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
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

## <a name="step-5---embed-your-content"></a>Stap 5: uw inhoud insluiten

U kunt nu uw inhoud insluiten in een voorbeeldtoepassing of in uw eigen toepassing.

* [Inhoud met behulp van de voorbeeldtoepassing insluiten](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Inhoud in uw toepassing insluiten](embed-sample-for-customers.md#embed-content-within-your-application)

Als de inhoud is ingesloten, bent u klaar voor de [overgang naar de productieomgeving](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Een app registreren](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded voor uw klanten](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Toepassings- en service-principal-objecten in Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Beveiliging op rijniveau met on-premises gegevensgateway met service-principal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Power BI-inhoud met service-principal en een certificaat insluiten](embed-service-principal-certificate.md)