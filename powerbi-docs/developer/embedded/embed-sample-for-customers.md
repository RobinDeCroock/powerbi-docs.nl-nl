---
title: Inhoud voor uw klanten insluiten in de toepassing voor het insluiten van analyses in Power BI
description: Lees hoe u een rapport, dashboard of tegel insluit in een Power BI Embedded-analysevoorbeeld.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/02/2020
ms.openlocfilehash: e79a73880b50a0edb5e507726cb0c995ba13cd77
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098416"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>Zelfstudie: Power BI-inhoud insluiten met een voorbeeld-app voor het *insluiten voor uw klanten*

Met **ingesloten analyses** en **Power BI Embedded** (het Azure-product) kunt u Power BI-inhoud zoals rapporten, dashboards en tegels insluiten in uw app.

In deze zelfstudie leert u het volgende:
>[!div class="checklist"]
>* Uw embedded omgeving instellen.
>* Een voorbeeld-app configureren voor het *insluiten voor uw klanten* (ook wel *gegevens zijn eigendom van app (app owns data)* genoemd).

Gebruikers hoeven zich niet aan te melden bij Power BI of een Power BI-licentie te hebben om uw app te gebruiken.

U kunt het beste de methode voor het *insluiten voor uw klanten* gebruiken om uw Power BI-inhoud in te sluiten, als u een onafhankelijke softwareleverancier (ISV) of een ontwikkelaar bent die apps voor derden wil maken.

## <a name="code-sample-specifications"></a>Specificaties voor codevoorbeeld

Deze zelfstudie bevat instructies voor het configureren van een voorbeeld-app voor het *insluiten voor uw klanten* in een van de volgende talen:

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

De codevoorbeelden ondersteunen de volgende browsers:

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>Vereisten

Voordat u met deze zelfstudie begint, controleert u of u over de Power BI- en codeafhankelijkheden beschikt die hieronder worden vermeld:

* **Power BI-afhankelijkheden**

    * Uw eigen [Azure Active Directory-tenant](create-an-azure-active-directory-tenant.md).

    * Als u uw app wilt verifiëren bij Power BI, moet u van een van de volgende opties gebruikmaken:

        * [Service-principal](embed-service-principal.md): een [Azure AD-object voor service-principal](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) (Microsoft Azure Active Directory), waarmee Azure AD uw app kan verifiëren.

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)-licentie: dit is uw **hoofdgebruiker** en uw app gebruikt deze om zich bij Power BI te verifiëren.

        * Een Power BI [Premium per gebruiker](../../admin/service-premium-per-user-faq.md)-licentie: dit is uw **hoofdgebruiker** en uw app gebruikt deze om zich bij Power BI te verifiëren.

    >[!NOTE]
    >Als u [wilt overgaan naar de productieomgeving](move-to-production.md) hebt u een [capaciteit](embedded-capacity.md) nodig.

* **Codeafhankelijkheden**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (of hoger)
    
    * Een geïntegreerde ontwikkelomgeving (IDE of Integrated Development Environment). Het is raadzaam een van de volgende opties te gebruiken:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (of JRE)](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/): controleer of u over *Eclipse voor Java EE-ontwikkelaars* (Enterprise Edition) beschikt
    
    * [Binaire distributies van Apache Tomcat](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * Een geïntegreerde ontwikkelomgeving (IDE of Integrated Development Environment). Het is raadzaam een van de volgende opties te gebruiken:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (of hoger)
    
        >[!NOTE]
        >* Als u *Python* voor de eerste keer installeert, selecteert u de optie **Python toevoegen aan PATH** om de installatie toe te voegen aan de variabele `PATH`.
        >* Als *Python* al is geïnstalleerd, controleert u of de variabele `PATH` het installatiepad daarvan bevat. Raadpleeg de Python-documentatie [Uitleg: Omgevingsvariabelen instellen](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) (deze koppeling verwijst naar Python 3) voor meer informatie.
    
    * Een geïntegreerde ontwikkelomgeving (IDE of Integrated Development Environment). Het is raadzaam een van de volgende opties te gebruiken:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Methode

Als u een voorbeeld-app voor het *insluiten voor uw klanten* wilt maken, voert u de volgende stappen uit:

1. [Selecteer uw verificatiemethode](#step-1---select-your-authentication-method).

2. [Registreer een Microsoft Azure Active Directory-app](#step-2---register-an-azure-ad-application).

3. [Maak een Power BI-werkruimte](#step-3---create-a-power-bi-workspace).

4. [Maak en publiceer een Power BI-rapport](#step-4---create-and-publish-a-power-bi-report).

5. [Haal de parameterwaarden voor de insluiting op](#step-5---get-the-embedding-parameter-values).

6. [API-toegang voor de service-principal](#step-6---service-principal-api-access)
 
7. [Schakel de toegang tot de werkruimte in](#step-7---enable-workspace-access).

8. [Sluit uw inhoud in](#step-8---embed-your-content).

## <a name="step-1---select-your-authentication-method"></a>Stap 1: Uw verificatiemethode selecteren

Uw ingesloten oplossing varieert, afhankelijk van de verificatiemethode die u selecteert. Daarom is het belangrijk dat u de verschillen tussen de verificatiemethoden kent, zodat u kunt bepalen welke het beste past bij uw oplossing.

In de onderstaande tabel worden enkele belangrijke verschillen tussen de verificatiemethoden voor de [service-principal](embed-service-principal.md) en **hoofdgebruiker** beschreven.

|Overweging  |Service-principal  |Hoofdgebruiker  |
|---------|---------|---------|
|Mechanisme     |Met het [object voor service-principal](/azure/active-directory/develop/app-objects-and-service-principals.md#service-principal-object) van uw Azure AD-app kan Microsoft Azure Active Directory uw app voor de ingesloten oplossing verifiëren bij Power BI.        |Uw Microsoft Azure Active Directory-app gebruikt de referenties (gebruikersnaam en wachtwoord) van een Power BI-gebruiker om zich te verifiëren bij Power BI.         |
|Beveiliging     |De *service-principal* is de aanbevolen verificatiemethode voor Microsoft Azure Active Directory. Als u een service-principal gebruikt,* kunt u de verificatie uitvoeren met behulp van een *app-geheim* of een *certificaat*.</br></br>In deze zelfstudie wordt alleen beschreven hoe u een *service-principal* gebruikt met een *app-geheim*. Als u inhoud wilt insluiten met een *service-principal* en een *certificaat*, raadpleegt u het artikel [Service-principal met een certificaat](embed-service-principal-certificate.md).         |Deze verificatiemethode wordt niet zo veilig beschouwd als het gebruik van een *service-principal*. Dit komt omdat u behoedzaam moet zijn met de referenties (gebruikersnaam en wachtwoord) voor de *hoofdgebruiker*. U moet deze bijvoorbeeld niet blootstellen in de app voor het insluiten en u moet het wachtwoord regelmatig wijzigen.         |
|Gedelegeerde machtigingen van Microsoft Azure Active Directory |Niet vereist. |Uw *hoofdgebruiker* of een beheerder moet voor uw app toegang verlenen tot Power BI REST API-[machtigingen](/azure/active-directory/develop/v2-permissions-and-consent) (ook wel bereiken genoemd). Bijvoorbeeld *Report.ReadWrite.All*. |
|Toegang tot de Power BI-service |U hebt geen toegang tot de Power BI-service met een *service-principal*.|U kunt toegang krijgen tot de Power BI-service met de referenties van uw *hoofdgebruiker*.|
|Licentie     |Hiervoor is geen Pro-licentie vereist. U kunt inhoud gebruiken uit elke werkruimte waarvan u lid of beheerder bent.         |Hiervoor is een [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)-licentie vereist.         |

## <a name="step-2---register-an-azure-ad-application"></a>Stap 2: Een Azure AD-app registreren

Door uw app te registreren bij Microsoft Azure Active Directory kunt u het volgende doen:
> [!div class="checklist"]
>* Een identiteit voor uw app instellen
>* Uw app toegang bieden tot de [Power BI REST API's](/rest/api/power-bi/)
>* Als u een *hoofdgebruiker* gebruikt: geef de [Power BI REST-machtigingen](/azure/active-directory/develop/v2-permissions-and-consent) van uw app op

Als u de app wilt registreren bij Microsoft Azure Active Directory, volgt u de instructies in [Uw app registreren](register-app.md).

>[!NOTE]
>Voordat u de app registreert, moet u beslissen welke verificatiemethode u gebruikt, *service-principal* of *hoofdgebruiker*.

## <a name="step-3---create-a-power-bi-workspace"></a>Stap 3: Een Power BI-werkruimte maken

Power BI bewaart uw rapporten, dashboards en tegels in een werkruimte. Als u deze items wilt insluiten, moet u ze maken en naar een werkruimte uploaden.

>[!TIP]
>Als u al een werkruimte hebt, kunt u deze stap overslaan.

Als u een werkruimte wilt maken, doet u het volgende:

1. Meld u aan bij Power BI.

2. Selecteer **Werkruimten**.

3. Selecteer **Een werkruimte maken**.

4. Geef uw werkruimte een naam en selecteer **Opslaan**.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>Stap 4: Een Power BI-rapport maken en publiceren

In de volgende stap maakt u een rapport en uploadt u dit naar uw werkruimte. U kunt [uw eigen rapport maken](/powerbi-docs/fundamentals/desktop-getting-started#build-reports) met behulp van Power BI Desktop en het vervolgens [publiceren](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) naar uw werkruimte. U kunt ook een voorbeeldrapport uploaden naar uw werkruimte.

>[!Tip]
>Als u al een werkruimte met een rapport hebt, kunt u deze stap overslaan.

Als u een voorbeeldrapport wilt downloaden en wilt publiceren naar uw werkruimte, voert u de volgende stappen uit:

1. Open de GitHub-map [Power BI Desktop-voorbeelden](https://github.com/microsoft/PowerBI-Developer-Samples).

2. Selecteer **Code** en vervolgens **ZIP-bestand downloaden**.

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Een schermopname met de optie voor het downloaden van een ZIP-bestand in de GitHub-map Power BI Desktop-voorbeelden":::

3. Pak het gedownloade ZIP-bestand uit en ga naar de map **Voorbeeldrapporten**.

4. Selecteer een rapport dat u wilt insluiten en [publiceer](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) het naar uw werkruimte.

## <a name="step-5---get-the-embedding-parameter-values"></a>Stap 5: De parameterwaarden voor het insluiten ophalen

Als u uw inhoud wilt insluiten, moet u bepaalde parameterwaarden ophalen. In de onderstaande tabel ziet u de vereiste waarden en wordt aangegeven of deze van toepassing zijn op de verificatiemethode met een *service-principal* of met een *hoofdgebruiker* of beide.

Zorg ervoor dat u over alle onderstaande waarden beschikt voordat u de inhoud insluit. Sommige waarden zullen verschillen, afhankelijk van de verificatiemethode die u gebruikt.

|Parameter   |Service-principal   |Hoofdgebruiker  |
|-------------------|---|---|
|[Client ID](#client-id) |![Is van toepassing op.](../../media/yes.png) |![Is van toepassing op.](../../media/yes.png) |
|[Werkruimte-id](#workspace-id)     |![Is van toepassing op.](../../media/yes.png) |![Is van toepassing op.](../../media/yes.png) |
|[Rapport-id](#report-id)           |![Is van toepassing op.](../../media/yes.png) |![Is van toepassing op.](../../media/yes.png) |
|[Clientgeheim](#client-secret) |![Is van toepassing op.](../../media/yes.png) |![Is niet van toepassing op.](../../media/no.png) |
|[Tenant ID](#tenant-id)                 |![Is van toepassing op.](../../media/yes.png) |![Is niet van toepassing op.](../../media/no.png) |
|[Power BI-gebruikersnaam](#power-bi-username-and-password)   |![Is niet van toepassing op.](../../media/no.png) |![Is van toepassing op.](../../media/yes.png) |
|[Power BI-wachtwoord](#power-bi-username-and-password)   |![Is niet van toepassing op.](../../media/no.png) |![Is van toepassing op.](../../media/yes.png) |

### <a name="client-id"></a>Client-id

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/yes.png)hoofdgebruiker

Als u de GUID van de client-id (ook wel de *app-id* genoemd) wilt ophalen, voert u de volgende stappen uit:

1. Meld u aan bij [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Ga naar **App-registraties** en selecteer de koppeling **App-registraties**.

3. Selecteer de Azure AD-app die u gebruikt voor het insluiten van uw Power BI-inhoud.

4. Kopieer in de sectie **Overzicht** de GUID van de **app-id (client)** .

### <a name="workspace-id"></a>Werkruimte-id

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/yes.png)hoofdgebruiker

Als u de GUID van de werkruimte-id wilt ophalen, voert u de volgende stappen uit:

1. Meld u aan bij de Power BI-service.

2. Open het rapport dat u wilt insluiten.

3. Kopieer de GUID van de URL. De GUID is de tekenreeks tussen **/groups/** en **/reports/** .

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Een schermopname met de GUID van de werkruimte-id in de URL van de Power BI-service":::

### <a name="report-id"></a>Rapport-id

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/yes.png)hoofdgebruiker

1. Meld u aan bij de Power BI-service.

2. Open het rapport dat u wilt insluiten.

3. Kopieer de GUID van de URL. De GUID is de tekenreeks tussen **/reports/** en **/ReportSection**.

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Een schermopname met de GUID van de rapport-id in de URL van de Power BI-service":::

### <a name="client-secret"></a>Clientgeheim

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/no.png)hoofdgebruiker

Als u het clientgeheim wilt ophalen, voert u de volgende stappen uit:

1. Meld u aan bij [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Ga naar **App-registraties** en selecteer de koppeling **App-registraties**.

3. Selecteer de Azure AD-app die u gebruikt voor het insluiten van uw Power BI-inhoud.

4. Selecteer onder **Beheren** de optie **Certificaten en geheimen**.

5. Selecteer onder **Clientgeheimen** de optie **Nieuw clientgeheim**.

6. Geef in het pop-upvenster **Een clientgeheim toevoegen** een beschrijving op voor uw app-geheim, selecteer wanneer het app-geheim verloopt en selecteer **Toevoegen**.

7. Kopieer in de sectie **Clientgeheimen** de tekenreeks in de kolom **Waarde** van het zojuist gemaakte app-geheim. De waarde van het clientgeheim is uw *client-id*.

### <a name="tenant-id"></a>Tenant-id

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/no.png)hoofdgebruiker

Als u de GUID van de tenant-id wilt ophalen, voert u de volgende stappen uit:

1. Meld u aan bij [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Ga naar **App-registraties** en selecteer de koppeling **App-registraties**.

3. Selecteer de Azure AD-app die u gebruikt voor het insluiten van uw Power BI-inhoud.

4. Kopieer in de sectie **Overzicht** de GUID van de **directory-id (tenant)** .

### <a name="power-bi-username-and-password"></a>Gebruikersnaam en wachtwoord voor Power BI

>[!TIP]
>**Van toepassing op:** ![Niet van toepassing op.](../../media/no.png)service-principal ![Van toepassing op.](../../media/yes.png)hoofdgebruiker

Zorg dat u over de *gebruikersnaam* en het *wachtwoord* beschikt van de Power BI-gebruiker die u gebruikt als uw **hoofdgebruiker**. Dit is dezelfde gebruiker als die u hebt gebruikt voor het maken van een werkruimte en naar wie u een rapport hebt geüpload, in de Power BI-service.

## <a name="step-6---service-principal-api-access"></a>Stap 6: API-toegang voor de service-principal

>[!TIP]
>**Van toepassing op:** ![Van toepassing op.](../../media/yes.png)service-principal ![Van toepassing op.](../../media/no.png)hoofdgebruiker
>
>Deze stap is alleen relevant als u de verificatiemethode voor *service-principal* gebruikt. Als u een *hoofdgebruiker* gebruikt, slaat u deze stap over en gaat u door met [Stap 7: De toegang tot de werkruimte inschakelen](#step-7---enable-workspace-access).

Voordat een Azure AD-app toegang kan krijgen tot de Power BI-inhoud en -API's, moet een Power BI-beheerder toegang tot de service-principal inschakelen in de Power BI-beheerportal. Als u niet de beheerder van uw tenant bent, vraagt u de beheerder van de tenant om de *tenantinstellingen* voor u in te schakelen.
        
1. Selecteer in de *Power BI-service* de opties **Instellingen** > **Instellingen** > **Beheerportal**.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Een schermopname met de menuoptie voor de beheerinstellingen in het menu Instellingen voor de Power BI-service":::
        
2. Selecteer **Tenantinstellingen** en schuif vervolgens omlaag naar de sectie **Ontwikkelaarsinstellingen**.
        
3. Vouw **Toestaan dat service-principals gebruikmaken van Power BI-API's** uit en schakel deze optie in.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Een schermopname waarin wordt getoond hoe u de optie voor ontwikkelaarsinstellingen inschakelt in de menuoptie Tenantinstellingen in de Power BI-service":::
        
>[!NOTE]
>Wanneer u een *service-principal* gebruikt, kunt u het beste hiervoor de toegang tot de tenantinstellingen beperken met behulp van een *beveiligingsgroep*. Zie voor meer informatie over deze functie de volgende secties in het artikel over de [service-principal](embed-service-principal.md):
> * [Een Azure AD-beveiligingsgroep maken](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [De beheerinstellingen voor de Power BI-service inschakelen](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>Stap 7: De toegang tot de werkruimte inschakelen

Als u uw Azure AD-app toegang wilt verlenen tot artefacten zoals rapporten, dashboards en gegevenssets in de Power BI-service, voegt u de *service-principal* of *hoofdgebruiker* als *lid* of *beheerder* toe aan uw werkruimte.

1. Meld u aan bij de Power BI-service.

2. Ga naar de werkruimte waarvoor u toegang wilt inschakelen, en selecteer in het menu **More** de optie **Workspace access**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Schermopname met de knop voor toegang tot een werkruimte in het menu More van een Power BI-werkruimte.":::

3. Kopieer in het deelvenster **Toegang**, afhankelijk van de verificatiemethode die u gebruikt, de *service-principal* of *hoofdgebruiker* naar het tekstvak **E-mailadres invoeren**.

    >[!NOTE]
    >Als u een *service-principal* gebruikt, heeft deze de naam die u voor de Azure AD-app hebt opgegeven.

5. Selecteer **Toevoegen**.

## <a name="step-8---embed-your-content"></a>Stap 8: Uw inhoud insluiten

Met de voorbeeld-app van Power BI Embedded kunt u een Power BI-app voor het *insluiten voor uw klanten* maken.

Voer de volgende stappen uit om de voorbeeld-app voor het *insluiten voor uw klanten* te wijzigen om uw Power BI-rapport in te sluiten.  

1. Open de map [Voorbeelden voor Power BI-ontwikkelaars](https://github.com/microsoft/PowerBI-Developer-Samples).

2. Selecteer **Code** en vervolgens **ZIP-bestand downloaden**.

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Een schermopname met de optie voor het downloaden van een ZIP-bestand in de GitHub-map Voorbeelden voor Power BI-ontwikkelaars":::

3. Pak het gedownloade ZIP-bestand uit en ga naar de map **PowerBI-Developer-Samples-master**.

4. Afhankelijk van de taal die u voor de app wilt gebruiken, opent u een van de volgende mappen:

* .NET Core
* .NET Framework
* Java
* Node JS
* Python
    >[!NOTE]
    >De voorbeeld-apps voor het *insluiten voor uw klanten* bieden alleen ondersteuning voor de talen die hierboven worden vermeld. De *React TS*-voorbeeld-app biedt alleen ondersteuning voor de oplossing voor het *[insluiten voor uw organisatie](embed-sample-for-your-organization.md)* .

5. Open de map **Insluiten voor uw klanten**.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. Open de *voorbeeld-app voor het insluiten voor uw klanten* met een van de volgende methoden:

    * Als u [Visual Studio](https://visualstudio.microsoft.com/) gebruikt, opent u het bestand **AppOwnsData.sln**.

    * Als u [Visual Studio Code](https://code.visualstudio.com/) gebruikt, opent u de map **App Owns Data**.

7. Open **appsettings.json**.

8. Afhankelijk van de verificatiemethode vult u de volgende parameterwaarden in:

    |Parameter            |Service-principal  |Hoofdgebruiker  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |De [client-id](#client-id) van uw Azure AD-app         |De [client-id](#client-id) van uw Azure AD-app         |
    |`TenantId`           |De [tenant-id](#tenant-id) van Azure Active Directory         |N.v.t.         |
    |`PbiUsername`        |N.v.t.         |De gebruikersnaam voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`PbiPassword`        |N.v.t.         |Het wachtwoord voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`ClientSecret`       |Uw Azure AD-[clientgeheim](#client-secret)         |N.v.t.         |
    |`WorkspaceId`        |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)          |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)         |
    |`ReportId`           |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)            |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)         |

9. Voer het project uit door de juiste optie te selecteren:

    * Als u **Visual Studio** gebruikt, selecteert u **IIS Express** (afspelen).

    * Als u **Visual Studio Code** gebruikt, selecteert u **Uitvoeren > Foutopsporing starten**.

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. Als u [Visual Studio](https://visualstudio.microsoft.com/) gebruikt, opent u het bestand **AppOwnsData.sln**.

7. Open **Web.config**.

8. Afhankelijk van de verificatiemethode vult u de volgende parameterwaarden in:

    |Parameter            |Service-principal  |Hoofdgebruiker  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |De [client-id](#client-id) van uw Azure AD-app         |De [client-id](#client-id) van uw Azure AD-app         |
    |`workspaceId`        |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)          |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)         |
    |`reportId`           |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)            |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)         |
    |`pbiUsername`        |N.v.t.         |De gebruikersnaam voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`pbiPassword`        |N.v.t.         |Het wachtwoord voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`applicationSecret`       |Uw Azure AD-[clientgeheim](#client-secret)         |N.v.t.         |
    |`tenant`           |De [tenant-id](#tenant-id) van Azure Active Directory         |N.v.t.         |

9. Voer het project uit door **IIS Express** (afspelen) te selecteren.

>[!NOTE]
>Als het ingesloten rapport niet wordt weergegeven wanneer u de voorbeeld-app uitvoert, moet u de Power BI-pakketten vernieuwen door de volgende stappen uit te voeren:
>1. Klik met de rechtermuisknop op de projectnaam (AppOwnsData) en selecteer **NuGet-pakketten beheren**.
>2. Zoek op **Power BI JavaScript** en installeer het pakket opnieuw.
>
>Zie [Pakketten opnieuw installeren en bijwerken](/nuget/consume-packages/reinstalling-and-updating-packages) voor meer informatie.

# <a name="java"></a>[Java](#tab/java)

6. Open **Eclipse** en volg de instructies die hieronder worden beschreven.

    >[!NOTE]
    >Voor de instructies voor de *Java-voorbeeld-app voor het insluiten voor uw klanten*, raadpleegt u [Eclipse IDE voor Java EE-ontwikkelaars](https://www.eclipse.org/downloads/packages/) (Enterprise Edition). Als u een andere app gebruikt, moet u deze zelf instellen.

7. Voeg de Tomcat-server toe aan Eclipse:

    a. Selecteer **Venster** > **Weergave tonen** > **Servers**.

    b. Selecteer op het tabblad Servers de optie **Geen servers beschikbaar. Klik op deze koppeling om een nieuwe server te maken**.

    c. Vouw **Apache** uit in het venster **Een nieuwe server definiëren** en selecteer de Tomcat-server die op uw computer wordt uitgevoerd. Bijvoorbeeld *Tomcat v9.0-server*.

    d. Selecteer **Next**.

    e. Selecteer in het venster **Tomcat-server** de optie **Bladeren** en ga naar de map die de Tomcat-server bevat.

    f. Selecteer in het venster **Tomcat-server** de optie **Geïnstalleerde JRE's**.

    g. Selecteer in het venster **Geïnstalleerde JRE's** de beschikbare *JRE* en selecteer **Toepassen en sluiten**.

    h. Selecteer **Voltooien** in het venster **Tomcat-server**. De Tomcat-server wordt nu weergegeven op het tabblad *Servers*.

8. Open het project in Eclipse:

    >[!IMPORTANT]
    >U kunt met Eclipse problemen ondervinden als de naam van het pad te lang is. Als u dit probleem wilt voorkomen, controleert u of de map van de voorbeeld-app niet te diep is genest in de mapstructuur van uw computer.

    a. Selecteer **Bestand** en vervolgens **Projecten uit het bestandssysteem openen**.

    b. Selecteer in het venster **Projecten uit het bestandssysteem of archief importeren** de optie **Map** en open de map **AppOwnsData**.

    c. Selecteer **Finish**.

9. Voeg de Tomcat-server toe aan het project:

    a. Klik in het deelvenster **Pakketverkenner** met de rechtermuisknop op **AppOwnsData** en selecteer **Eigenschappen**.

    b. Selecteer in het venster **Eigenschappen voor AppOwnesData** de optie **Beoogde runtimes** en selecteer vervolgens **Apache Tomcat**. Deze selectie bevat de versie van *Apache Tomcat* die u gebruikt, bijvoorbeeld *Apache Tomact v9.0*.

    c. Selecteer **Toepassen en sluiten**.

10. Vul de vereiste parameters in

    a. Vouw in de **Pakketverkenner** het project **AppOwnsData** uit.

    b. Vouw **Java-resources** uit.

    c. Vouw **src** uit.

    d. Vouw **com.embedsample.appoensdata.config** uit.

    e. Open **Config.java**.

    f. Afhankelijk van de verificatiemethode vult u de volgende parameterwaarden in:

    |Parameter            |Service-principal  |Hoofdgebruiker  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)          |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)         |
    |`reportId`           |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)            |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)         | 
    |`clientId`           |De [client-id](#client-id) van uw Azure AD-app         |De [client-id](#client-id) van uw Azure AD-app         |
    |`pbiUsername`        |N.v.t.         |De gebruikersnaam voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`pbiPassword`        |N.v.t.         |Het wachtwoord voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`tenantId`           |De [tenant-id](#tenant-id) van Azure Active Directory         |N.v.t.         |
    |`appSecret`       |Uw Azure AD-[clientgeheim](#client-secret)         |N.v.t.         |

11. Het project uitvoeren

    a. Klik in de **Pakketverkenner** met de rechtermuisknop op **AppOwnesData**.

    b. Selecteer **Uitvoeren als**  > **Uitvoeren op server**.

    c. Selecteer in het venster **Uitvoeren op server** de optie **Een bestaande server kiezen** en selecteer de *Tomcat*-server.

    d. Selecteer **Finish**.

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. Open de map **App Owns Data** met behulp van de IDE van uw keuze. Het is raadzaam een van de volgende opties te gebruiken:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. Open een terminal en installeer de vereiste afhankelijkheden door het volgende uit te voeren: `npm install`.

8. Vouw de map **Config** uit en open **config.json**.

9. Afhankelijk van de verificatiemethode vult u de volgende parameterwaarden in:

    |Parameter            |Service-principal  |Hoofdgebruiker  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |De [client-id](#client-id) van uw Azure AD-app         |De [client-id](#client-id) van uw Azure AD-app         |
    |`workspaceId`        |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)          |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)         |
    |`reportId`           |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)            |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)         |
    |`pbiUsername`        |N.v.t.         |De gebruikersnaam voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`pbiPassword`        |N.v.t.         |Het wachtwoord voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`clientSecret`       |Uw Azure AD-[clientgeheim](#client-secret)         |N.v.t.         |
    |`tenantId`           |De [tenant-id](#tenant-id) van Azure Active Directory         |N.v.t.         |

10. Voer het volgende uit om het project uit te voeren:

    a. Voer `npm start` uit in de IDE-terminal.

    b. Open een nieuw tabblad in de browser en navigeer naar [http://localhost:5300](http://localhost:5300).

# <a name="python"></a>[Python](#tab/python)

6. Open **PowerShell** of **Opdrachtprompt**.

7. Controleer of u zich in de map **Python** > **Insluiten voor uw klanten** bevindt en of het bestand **requirements.txt** in de map is opgenomen. Voer vervolgens `pip3 install -r requirements.txt` uit.

8. Open de map **App Owns Data** met behulp van de IDE van uw keuze. Het is raadzaam een van de volgende opties te gebruiken:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. Open **config.py**.

10. Afhankelijk van de verificatiemethode vult u de volgende parameterwaarden in:

    |Parameter            |Service-principal  |Hoofdgebruiker  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)          |De id van de werkruimte met uw ingesloten rapport, zie [Werkruimte-id](#workspace-id)         |
    |`REPORT_ID`           |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)            |De id van het rapport dat u wilt insluiten, zie [Rapport-id](#report-id)         |
    |`TENANT_ID`           |De [tenant-id](#tenant-id) van Azure Active Directory         |N.v.t.         |
    |`CLIENT_ID`           |De [client-id](#client-id) van uw Azure AD-app         |De [client-id](#client-id) van uw Azure AD-app         |
    |`CLIENT_SECRET`       |Uw Azure AD-[clientgeheim](#client-secret)         |N.v.t.         |
    |`POWER_BI_USER`        |N.v.t.         |De gebruikersnaam voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |N.v.t.         |Het wachtwoord voor uw *hoofdgebruiker*, zie [Power BI-gebruikersnaam en -wachtwoord](#power-bi-username-and-password)         |

11. Sla het bestand op.

12. Voer het volgende uit om het project uit te voeren:

    a. Ga in **PowerShell** of **Opdrachtprompt** naar de map **Python** > **Insluiten voor uw klanten** > **AppOwnesData** en voer `flask run` uit.

    b. Open een nieuw tabblad in de browser en navigeer naar [http://localhost:5300](http://localhost:5300).

---

## <a name="developing-your-application"></a>Uw toepassing ontwikkelen

Na het configureren en uitvoeren van de voorbeeld-app voor het *insluiten voor uw klanten*, kunt u beginnen met het ontwikkelen van uw eigen app.

Wanneer u klaar bent, controleert u de vereisten voor het [overgaan naar de productieomgeving](move-to-production.md). U hebt ook een [capaciteit](embedded-capacity.md) nodig. Neem het artikel over de [capaciteitsplanning](embedded-capacity-planning.md) door om na te gaan welke SKU het beste past bij uw behoeften.


## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
>[Verplaatsen naar productie](move-to-production.md)

>[!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Gepagineerde rapporten insluiten voor uw klanten](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Gepagineerde rapporten voor uw organisatie insluiten](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Stel een vraag aan de Power BI-community](https://community.powerbi.com/)