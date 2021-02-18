---
title: Meer informatie over de machtigings tokens die nodig zijn voor het insluiten van een Power BI-toepassing
description: Meer informatie over de tokens die uw Power BI-toepassing nodig heeft om te verifiëren bij Azure en Power BI-service.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: amshuste
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/17/2021
ms.openlocfilehash: 6a7847b0e89086094220a51a4893ffffd59d5642
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2021
ms.locfileid: "100656571"
---
# <a name="embedded-analytics-application-tokens"></a>Embedded Analytics-toepassings tokens

Als u Power BI inhoud wilt gebruiken, hebt u een toegangs token nodig. Afhankelijk van uw oplossing kan dit token een [Azure AD-token](#azure-ad-token) of een [insluit token](#embed-token)zijn.

Als u de oplossing *insluiten voor uw klanten* gebruikt, krijgen uw web app-gebruikers toegang tot Power bi inhoud (zoals rapporten, Dash boards en tegels), op basis van het *insluit token* dat is gegenereerd door uw toepassing.

>[!NOTE]
>Wanneer u de oplossing *insluiten voor uw klanten* gebruikt, kunt u elke verificatie methode gebruiken om toegang tot uw web-app toe te staan.

Als u de oplossing *insluiten voor uw organisatie* gebruikt, worden uw web-app-gebruikers geverifieerd op basis van hun eigen referenties voor Azure AD. Uw app-gebruikers hebben toegang tot de inhoud van de Power BI ze toegang hebben op Power BI-service.

## <a name="azure-ad-token"></a>Azure AD-token

U hebt een [Azure AD-token](#azure-ad-token)nodig voor zowel *insluiten voor uw klanten* als voor *het insluiten van uw organisatie* oplossingen. Dit token is vereist voor alle [rest API](/rest/api/power-bi/) bewerkingen en verloopt na een uur.

* In het *insluiten voor uw klanten* wordt het Azure AD-token gebruikt voor het genereren van het *insluit token*.

* In de *insluiting voor uw organisatie* wordt het Azure AD-token gebruikt voor toegang tot Power bi.

## <a name="embed-token"></a>Token insluiten

Wanneer u de oplossing *insluiten voor uw klanten* gebruikt, moet u in uw web-app weten van welke Power bi inhoud de gebruiker toegang heeft. Gebruik de [insluit token](/rest/api/power-bi/embedtoken) rest api's om een *insluit token* te genereren, waarmee het volgende wordt opgegeven:

* Welke inhoud uw web-app-gebruiker kan openen.

* Het toegangs niveau van de web-app-gebruiker (weer geven, maken of bewerken).

Zie [overwegingen bij het genereren van een insluit token](generate-embed-token.md)voor meer informatie.

## <a name="authentication-flows"></a>Verificatie stromen

In deze sectie worden de verificatie stromen voor de *insluiting voor uw klanten* beschreven en worden de oplossingen *voor uw organisatie* Inge sloten.

### <a name="embed-for-your-customers"></a>Insluiten voor uw klanten

De oplossing *insluiten voor uw klanten* maakt gebruik van een niet-interactieve verificatie stroom. Gebruikers hoeven zich niet aan te melden bij Azure AD om toegang te krijgen tot Power BI. In plaats daarvan gebruikt uw web-app een specifieke Azure AD-identiteit voor verificatie bij Azure AD, en wordt het *insluit token* gegenereerd. De toegewezen identiteit kan een van de volgende zijn:

* **[Service-Principal](embed-service-principal.md)**

    Uw web-app maakt gebruik van het Azure AD- [Service-Principal-object](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) om te verifiëren bij Azure AD en een *Azure AD-token voor alleen apps* ophalen. Dit is een verificatie methode die alleen geldt voor een *app* , die wordt aanbevolen door Azure AD.

    Wanneer u een *Service-Principal* gebruikt, moet u de [toegang tot Power bi api's inschakelen](embed-sample-for-customers.md#step-6---service-principal-api-access) in de Power bi-service *beheer* instellingen. Hiermee kan uw web-app toegang krijgen tot de Power BI REST-Api's. De *Service-Principal* moet *lid* of *beheerder* van de werk ruimte zijn om API-bewerkingen op een werk ruimte te kunnen gebruiken.

* **Hoofdgebruiker**

    Uw web-app gebruikt een gebruikers account om te verifiëren bij Azure AD en de *Azure AD-token* op te halen. De *hoofd gebruiker* moet een licentie voor [Power bi Pro](/power-bi/admin/service-admin-purchasing-power-bi-pro) of een [Premium per gebruiker (PPU)](/power-bi/admin/service-premium-per-user-faq) hebben.

    Wanneer u een *hoofd gebruiker* gebruikt, moet u de [gedelegeerde machtigingen](/azure/active-directory/develop/v2-permissions-and-consent) van uw app definiëren (ook wel scopes genoemd). De *hoofd gebruiker* of *Tenant beheerder* is verplicht toestemming te verlenen voor het gebruik van deze machtigingen met behulp van de Power bi rest-api's.

Nadat de verificatie voor Azure AD is geslaagd, genereert uw web-app een [insluit token](/rest/api/power-bi/embedtoken) waarmee de gebruikers toegang kunnen krijgen tot specifieke Power bi inhoud.

>[!NOTE]
>* Als u wilt insluiten met behulp van de oplossing *insluiten voor uw klanten* , hebt u een capaciteit nodig met een-, em-of P-SKU.
>* Als u [wilt overstappen op productie](move-to-production.md) , hebt u een capaciteit nodig.

In het volgende diagram ziet u de verificatie stroom voor de oplossing *insluiten voor uw klanten* .

>[!div class="mx-imgBorder"]
>:::image type="content" source="media\embed-tokens\paas-authentiction.png" alt-text="Een diagram van de verificatie stroom in een insluiting voor uw klanten Power B I embedded Analytics-oplossing.":::

1. Web app-gebruiker wordt geverifieerd op basis van uw web-app (met uw verificatie methode).

2. Uw web-app maakt gebruik van een *Service-Principal* of een *hoofd gebruiker* om te verifiëren bij Azure AD.

3. Uw web-app krijgt een *Azure AD-token* van Azure AD en gebruikt deze om toegang te krijgen tot Power bi rest-api's. Toegang tot de Power BI REST-Api's wordt gegeven volgens uw verificatie methode, ofwel *Service Principal* of *hoofd gebruiker*.

4. Uw web-app roept een [insluit token](/rest/api/power-bi/embedtoken) rest API bewerking aan, waarbij het *insluit token* wordt aangevraagd. Het *insluit token* geeft aan welke Power bi inhoud kan worden inge sloten.

5. De REST API retourneert de *insluit token* naar uw web-app.

6. De web-app geeft het insluit token door aan de webbrowser van de gebruiker.

7. De web-app-gebruiker gebruikt het insluit token voor toegang tot Power BI.

### <a name="embed-for-your-organization"></a>Insluiten voor uw organisatie

De oplossing *voor insluiten voor uw organisatie* maakt gebruik van een interactieve verificatie stroom. Uw gebruikers verifiëren met Azure AD met behulp van hun Power BI referenties. Gebruikers moeten toestemming geven voor de API-machtigingen die zijn ingesteld bij het registreren van de app bij Azure AD. Toestemming wordt verleend in het pop-upvenster micro soft-machtigingen die zijn *aangevraagd* . Nadat toestemming is verleend, kan Power BI inhoud zoals rapporten en dash boards waartoe de web app-gebruiker toegang heeft, worden inge sloten.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/requested-premissions.png" alt-text="Scherm opname van het pop-upvenster micro soft-machtigingen waarvoor klanten toestemming geven om toegang te krijgen tot Power B I.":::

>[!NOTE]
>* De *insluiting voor uw organisatie* oplossing biedt geen ondersteuning voor een SKU.
>* Als u [wilt overstappen op productie](move-to-production.md) , hebt u een van de volgende configuraties nodig:
>    * Alle gebruikers met Pro-licenties.
>    * Alle gebruikers met PPU-licenties.
>    * Een [capaciteit](embedded-capacity.md). Met deze configuratie kunnen alle gebruikers gratis licenties hebben.

Dit diagram toont een voor beeld van de verificatie stroom voor de oplossing *insluiten voor uw organisatie* .

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/saas-authentiction.png" alt-text="Een diagram van de verificatie stroom in een invoeg toepassing voor de Power B I embedded Analytics-oplossing van uw organisatie.":::

1. Web app-gebruiker krijgt toegang tot de web-app.

2. De web-app leidt de gebruiker van de web-app om naar Azure AD.

3. De web-app-gebruiker wordt met behulp van zijn Power BI referenties geverifieerd op basis van Azure AD.

4. Azure AD omleidt de gebruiker van de web-app terug naar de web-app met het Azure AD-token (in een impliciet toekennings scenario wordt het toegangs token geretourneerd naar de browser van de gebruiker).

5. De web-app stuurt het Azure AD-token door naar de webbrowser van de gebruiker.

6. Uw Power BI Web-App maakt gebruik van het Azure AD-token om Power BI inhoud in te sluiten, zoals rapporten en dash boards, waarmee de gebruiker van de web-app toegang heeft.

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Overwegingen bij het genereren van een insluittoken](generate-embed-token.md)

>[!div class="nextstepaction"]
>[Capaciteit en SKU's in Power BI Embedded-analyses](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Hebt u nog vragen? Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)