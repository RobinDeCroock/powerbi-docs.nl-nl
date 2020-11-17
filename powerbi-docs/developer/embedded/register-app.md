---
title: Een app registreren om Power BI-inhoud in te sluiten
description: Informatie over het registreren van een toepassing in Azure Active Directory voor gebruik met ingesloten Power BI-inhoud.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 52e835f4ff0d3dc4cad13c2e3ecc77d254f3be9d
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412187"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Een Azure AD-toepassing registeren om bij Power BI te gebruiken

Als u ingesloten analyse van Power BI wilt gebruiken, moet u een Azure Active Directory-toepassing (Azure AD) registreren in Azure. De Azure AD-app stelt machtigingen in voor Power BI REST-resources en biedt toegang tot de [Power BI REST API's](/rest/api/power-bi/).

## <a name="determine-your-embedding-solution"></a>Uw insluitoplossing bepalen

Voordat u uw app registreert, moet u bepalen welke van de volgende oplossingen het meest geschikt is voor u:

* Insluiten voor uw klanten
* Insluiten voor uw organisatie

### <a name="embed-for-your-customers"></a>Insluiten voor uw klanten

Gebruik de oplossing [Insluiten voor uw klanten](embed-sample-for-customers.md), ook wel bekend als *App is eigenaar van gegevens*, als u van plan bent om een toepassing te maken die is ontworpen voor uw klanten. Gebruikers hoeven zich niet aan te melden bij Power BI of een Power BI licentie te hebben om uw toepassing te gebruiken. Uw toepassing maakt gebruik van een van de volgende methoden om te verifiëren bij Power BI:

* Het account **Hoofdgebruiker** (een Power BI Pro-licentie die wordt gebruikt voor aanmelding bij Power BI)

*  [Service-principal](embed-service-principal.md)

De oplossing Insluiten voor uw klanten wordt doorgaans gebruikt door onafhankelijke software leveranciers (ISV's) en ontwikkelaars die toepassingen maken voor een derde partij.

### <a name="embed-for-your-organization"></a>Insluiten voor uw organisatie

Gebruik de oplossing [Insluiten voor uw organisatie](embed-sample-for-your-organization.md), ook wel bekend als *Gebruiker is eigenaar van de gegevens*, als u van plan bent om een toepassing te maken waarvoor gebruikers hun referenties moeten gebruiken om zich bij Power BI te verifiëren.

De oplossing Insluiten voor uw organisatie wordt doorgaans gebruikt door ondernemingen en grote organisaties en is bedoeld voor interne gebruikers.

## <a name="register-an-azure-ad-app"></a>Een Azure AD-app registreren

De eenvoudigste manier om een Azure AD-app te registreren, is met behulp van het [installatieprogramma voor insluiten van Power BI](https://app.powerbi.com/embedsetup). Het hulpprogramma biedt een snel registratieproces voor beide insluitoplossingen met behulp van een eenvoudige grafische interface.

Als u een *Insluiten voor uw organisatie*-toepassing maakt en meer controle wilt over uw Azure AD-app, kunt u deze handmatig registreren in Azure Portal.

> [!IMPORTANT]
> Voordat u een Power BI-app registreert, hebt u een [Azure Active Directory-tenant en een organisatiegebruiker](create-an-azure-active-directory-tenant.md) nodig.

# <a name="embed-for-your-customers"></a>[Insluiten voor uw klanten](#tab/customers)

In deze stappen wordt beschreven hoe u een Azure AD-toepassing registreert voor de Power BI-oplossing [Insluiten voor uw klanten](embed-sample-for-customers.md).

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Selecteer **Insluiten voor uw klanten** in het gedeelte *Een insluitoplossing kiezen*.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. In *Stap 2 - uw toepassing registreren* vult u de volgende velden in:

    * **Toepassingsnaam**: geef uw toepassing een naam.

    * **API-toegang**: selecteer de Power BI-API's (ook wel scopes genoemd) die uw toepassing nodig heeft. U kunt *Alles selecteren* gebruiken om alle API's te selecteren. Zie [Machtigingen en toestemming in het eindpunt van Microsoft identity platform](/azure/active-directory/develop/v2-permissions-and-consent) voor meer informatie over machtigingen voor Power BI-toegang.

5. Selecteer **Registreren**.

    De **toepassings-id** van uw Azure AD-app wordt weergegeven in het vak *Samenvatting*. Kopieer deze waarde voor later gebruik.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. In *Stap 5 - machtigingen verlenen* selecteert u **Machtigingen verlenen** en selecteert u **Accepteren** in het pop-upvenster. Hierdoor kan uw Azure AD-app toegang krijgen tot de API's die u hebt geselecteerd (ook bekend als scopes) met uw aangemelde gebruiker. Deze gebruiker wordt ook wel de **hoofdgebruiker** genoemd.

9. (Optioneel) Als u een Power BI-werkruimte hebt gemaakt en inhoud erin hebt geüpload met het hulpprogramma, kunt u nu **Voorbeeldtoepassing downloaden** selecteren. Zorg ervoor dat u alle gegevens in het vak *Samenvatting* kopieert.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[Insluiten voor uw organisatie](#tab/organization)

In deze stappen wordt beschreven hoe u een Azure AD-toepassing registreert voor de Power BI-oplossing [Insluiten voor uw organisatie](embed-sample-for-your-organization.md).

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. Selecteer **Insluiten voor uw organisatie** in het gedeelte *Een insluitoplossing kiezen*.

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. In *Stap 2 - uw toepassing registreren* vult u de volgende velden in:

    * **Toepassingsnaam**: geef uw toepassing een naam.

    * **URL van startpagina**: voer een URL in voor de startpagina.

    * **Omleidings-URL**: wanneer gebruikers van uw toepassing zich aanmelden, worden zij omgeleid naar dit adres terwijl uw toepassing een verificatiecode van Azure ontvangt. Selecteer een van deze opties:

        * **Een standaard-URL gebruiken**: met deze optie wordt automatisch een voorbeeldtoepassing voor ingesloten analyse gemaakt en gedownload. De standaard-URL is http://localhost:13526/.

        * **Een aangepaste URL gebruiken**: selecteer deze optie als u al een toepassing voor ingesloten analyse hebt en u al weet wat u wilt gebruiken als omleidings-URL.

    * **API-toegang**: selecteer de Power BI-API's (ook wel scopes genoemd) die uw toepassing nodig heeft. U kunt *Alles selecteren* gebruiken om alle API's te selecteren. Zie [Machtigingen en toestemming in het eindpunt van Microsoft identity platform](/azure/active-directory/develop/v2-permissions-and-consent) voor meer informatie over machtigingen voor Power BI-toegang.

5. Selecteer **Registreren**.

    De waarden **toepassings-id** en **toepassingsgeheim** van uw Azure AD-app worden weergegeven in het vak *Samenvatting*. Kopieer deze waarden voor later gebruik.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (Optioneel) Als u een Power BI-werkruimte hebt gemaakt en inhoud erin hebt geüpload met het hulpprogramma, kunt u nu **Voorbeeldtoepassing downloaden** selecteren. Zorg ervoor dat u alle gegevens in het vak *Samenvatting* kopieert.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[Handmatige registratie](#tab/manual)

Gebruik de handmatige app-registratie van Azure AD alleen als u een *Insluiten voor uw organisatie*-oplossing maakt. Zie [Een app registreren bij Azure Active Directory](/azure/active-directory/develop/quickstart-v2-register-an-app) voor meer informatie over het registreren van toepassingen in Azure Active Directory.

1. Meld u aan bij [Azure Portal](https://portal.azure.com).

2. Selecteer uw Azure AD-tenant door uw account te selecteren in de rechterbovenhoek van de pagina.

3. Selecteer **App-registraties**. Als deze optie niet wordt weergegeven, zoekt u deze op.
 
4. Selecteer in *App-registraties* **Nieuwe registratie**.

5. Vul de volgende velden in:

    * **Naam**: geef uw toepassing een naam.

    * **Ondersteund accounttype**: selecteer wie de toepassing kan gebruiken.

6. (Optioneel) Voeg in de **omleidings-URI** een omleidings-URL toe.

7. Selecteer **Registreren**. Nadat u uw app hebt geregistreerd, wordt u naar de overzichtspagina van uw app geleid, waar u de *toepassings-id* kunt verkrijgen.

---

## <a name="change-your-azure-ad-apps-permissions"></a>De machtigingen van uw Azure AD-app wijzigen

Nadat u uw toepassing hebt geregistreerd, kunt u wijzigingen aanbrengen in de machtigingen ervoor. Wijzigingen in machtigingen kunnen via een programma worden gemaakt of in Azure Portal.

# <a name="azure"></a>[Azure](#tab/Azure)

In Azure Portal kunt u uw app bekijken en wijzigingen aanbrengen in de machtigingen ervoor.

1. Meld u aan bij [Azure Portal](https://portal.azure.com).

2. Selecteer uw Azure AD-tenant door uw account te selecteren in de rechterbovenhoek van de pagina.

3. Selecteer **App-registraties**. Als deze optie niet wordt weergegeven, zoekt u deze op.

4. Selecteer uw app op het tabblad **Toepassingen in eigendom**. De toepassing wordt geopend op het tabblad *Overzicht*, waar u de *toepassings-id* kunt controleren.

5. Selecteer het tabblad **API-machtigingen**.

6. Voer de volgende stappen uit om machtigingen toe te voegen:

    1. Selecteer de optie **Een machtiging toevoegen** en selecteer vervolgens **Power BI-service**.

    2. Selecteer **Gedelegeerde machtigingen** en voeg de specifieke machtigingen toe die u nodig hebt, of verwijder deze.

    3. Wanneer u klaar bent, selecteert u **Machtigingen toevoegen** om uw wijzigingen op te slaan.

7. Voer de volgende stappen uit om een machtiging te verwijderen:

    1. Selecteer het beletselteken (...) aan de rechterkant van de machtiging.
    
    2. Selecteer **Machtiging verwijderen**.
    
    3. Selecteer **Ja, verwijderen** in het pop-upvenster *Machtiging verwijderen*.

# <a name="http"></a>[HTTP](#tab/HTTP)

Als u de machtigingen van uw Azure AD-app via een programma wilt wijzigen, moet u de bestaande service-principals (gebruikers) in uw Tenant ophalen. Zie [servicePrincipal](/graph/api/resources/serviceprincipal) voor informatie over hoe u dit kunt doen.

1. Als u alle service-principals in uw tenant wilt ophalen, roept u de `Get servicePrincipal`-API aan zonder `{ID}`.

2. Zoek naar een service-principal met de *toepassings-id* van uw app als `appId`-eigenschap.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` is optioneel.

3. Ken Power BI machtigingen toe aan uw app door een van deze waarden toe te wijzen aan `consentType`:

    * `AllPrincipals`: kan alleen worden gebruikt door een Power BI-beheerder om namens alle gebruikers in de tenant machtigingen te verlenen.

    * `Principal`: wordt gebruikt om machtigingen te verlenen namens een specifieke gebruiker. Als u deze optie gebruikt, voegt u de `principalId={User_ObjectId}`-eigenschap toe aan de hoofdtekst van de aanvraag.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* Als u een **hoofdgebruiker** gebruikt om te voorkomen dat u om toestemming wordt gevraagd door Azure AD, moet u machtigingen verlenen aan het hoofdaccount.
    >* De `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* is afhankelijk van de tenant en is niet universeel. Deze waarde is de *objectId* van de toepassing *Power BI Service* in Azure AD. Als u deze waarde wilt ophalen uit Azure Portal, gaat u naar [Enterprise-toepassingen > Alle toepassingen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps) en zoekt u naar *Power BI Service*.

4. Ken app-machtigingen toe aan Azure AD door een waarde toe te wijzen aan `consentType`.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

U kunt de machtigingen voor uw Azure AD-app ook wijzigen met C#. Deze methode kan nuttig zijn als u overweegt een aantal van uw processen te automatiseren.

Raadpleeg het tabblad [HTTP](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions) voor meer informatie over de HTTP-aanvragen.

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

```

---

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Een Azure AD-toegangstoken ophalen voor uw Power BI-toepassing](get-azuread-access-token.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)