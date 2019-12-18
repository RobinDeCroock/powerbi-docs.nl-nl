---
title: Verbinding maken met de Microsoft Graph Security-API in Power BI Desktop
description: Eenvoudig verbinding maken met de Microsoft Graph Security-API in Power BI Desktop
author: preetikr
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: ef8e874c1f1a47d65845b87dccd441746651a68b
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999785"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Verbinding maken met de Microsoft Graph Security-API in Power BI Desktop

Gebruik de Microsoft Graph Security Power BI-connector van Power BI Desktop om verbinding te maken met de [Microsoft Graph Security-API](https://aka.ms/graphsecuritydocs). Vervolgens kunt u dashboards en rapporten maken om inzicht te krijgen in uw [beveiligingswaarschuwingen](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) en [beveiligingsscore](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta).

De Microsoft Graph Security-API koppelt [meerdere beveiligingsoplossingen](https://aka.ms/graphsecurityalerts) van Microsoft en haar ecosysteempartners om correlatie van waarschuwingen gemakkelijker te maken. Deze combinatie biedt toegang tot uitgebreide contextuele informatie en vereenvoudigt automatisering. Hiermee kunnen organisaties snel inzicht verkrijgen en handelen in meerdere beveiligingsproducten, en tegelijkertijd kosten en complexiteit reduceren.

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Vereisten om de Microsoft Graph Security-connector te gebruiken

Voor het gebruik van de Microsoft Graph Security-connector moet u *expliciet* toestemming verkrijgen van de tenantbeheerder van Azure Active Directory (Azure AD). Zie [verificatievereisten voor Microsoft Graph Security](https://aka.ms/graphsecurityauth).
Voor toestemming zijn de toepassings-ID en de naam van de connector vereist. Deze wordt hier vermeld en is beschikbaar in [Azure Portal](https://portal.azure.com):

| Eigenschap | Waarde |
|----------|-------|
| **Toepassingsnaam** | `MicrosoftGraphSecurityPowerBIConnector` |
| **Toepassings-id** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
|||

Uw Microsoft Azure Active Directory-tenantbeheerder kan een van de volgende methoden gebruiken om toestemming te verlenen voor de connector:

* [Toestemming verlenen voor Azure AD-toepassingen](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent)

* Reageren op een aanvraag die door uw logische app wordt verzonden tijdens de uitvoering via de [ervaring voor toepassingstoestemming](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience)
   
Aan het gebruikersaccount dat wordt gebruikt voor aanmelden bij de Microsoft Graph Security-connector moet de rol Azure AD-beveiligingslezer zijn toegewezen, **indien** de gebruiker geen lid is van de rol *Beveiligingsbeheerder*. Zie [Assign Azure AD roles to users](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users) (Azure AD-rollen toewijzen aan gebruikers).

## <a name="using-the-microsoft-graph-security-connector"></a>De Microsoft Graph-Security-connector gebruiken

Volg deze stappen voor het gebruik van de connector:

1. Selecteer **Gegevens ophalen** > **Meer** in het lint **Start** in Power BI Desktop.
2. Selecteer **Onlineservices** in de categorieënlijst aan de linkerkant van het venster.
3. Selecteer **Microsoft Graph Security (Beta)**.

    ![Het dialoogvenster Gegevens ophalen](media/desktop-connect-graph-security/GetData.PNG)
    
4. Selecteer in het venster **Microsoft Graph Security** de Microsoft Graph API-versie waarop query's moeten worden uitgevoerd: **v1.0** of **beta**.

    ![Het dialoogvenster Versie selecteren](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Meld u desgevraagd aan bij uw Azure Active Directory-account. Aan dit account moet de rol *Beveiligingslezer* of *Beveiligingsbeheerder* zijn toegewezen, zoals vermeld in de vorige sectie.

    ![Aanmelden](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. Als u de tenantbeheerder bent *en* als u nog geen toestemming hebt verleend voor de Microsoft Graph Security Power BI-connector (toepassing), wordt het volgende dialoogvenster geopend. Selecteer **Toestemming namens uw organisatie**.

    ![Het dialoogvenster Toestemming van een beheerder](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Wanneer u bent aangemeld, wordt in het volgende dialoogvenster aangegeven dat u bent geverifieerd. Selecteer **Verbinding maken**.

    ![Het dialoogvenster U bent momenteel aangemeld](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Nadat u verbinding hebt gemaakt, worden in het venster **Navigator** waarschuwingen, beveiligingsscores en andere entiteiten weergegeven die beschikbaar zijn in de [Microsoft Graph Security-API](https://aka.ms/graphsecuritydocs) voor de versie die u in stap 4 hebt geselecteerd. Selecteer een of meer entiteiten die u wilt importeren en gebruiken in Power BI Desktop. Selecteer **Laden** om de resultaatweergave te openen die wordt weergegeven na de stap 9.

    ![Dialoogvenster Navigator](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Als u een geavanceerde query wilt gebruiken met de Microsoft Graph Security-API, selecteert u de **Aangepaste Microsoft Graph Security-URL opgeven om resultaten te filteren**. Gebruik deze functie om met de vereiste machtigingen een [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata)-query te verzenden naar de Microsoft Graph Security-API.

   In het volgende voorbeeld wordt de `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'` *serviceUri* gebruikt. Zie [OData system query options](https://docs.microsoft.com/graph/query-parameters) (Opties voor OData-systeemquery's) voor meer informatie over het bouwen van query's voor het filteren, ordenen of ophalen van de recentste gegevens.

   ![OdataFeed-voorbeeld](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Wanneer u **Aanroepen** selecteert, wordt met de functie **OData.Feed** een aanroep verzonden naar de API, waardoor Query-Editor wordt geopend. U filtert en verfijnt de gegevensset die u wilt gebruiken. Laad deze gegevens vervolgens in Power BI Desktop.

Hieronder ziet u het venster met resultaten voor de Microsoft Graph Security-entiteiten waarop we een query hebben uitgevoerd:

   ![Voorbeeld van resultatenvenster](media/desktop-connect-graph-security/Result.PNG)
    

Nu kunt u de geïmporteerde gegevens uit de Microsoft Graph Security-connector gebruiken in Power BI Desktop. U kunt afbeeldingen of rapporten maken. Maar u kunt ook andere gegevens gebruiken die u importeert vanuit Excel-werkmappen, databases of andere gegevensbronnen.

## <a name="next-steps"></a>Volgende stappen
* Bekijk in [Microsoft Graph Security GitHub Power BI samples](https://aka.ms/graphsecuritypowerbiconnectorsamples) (Microsoft Graph Security GitHub Power BI-voorbeelden) Power BI-voorbeelden en -sjablonen waarvoor deze connector wordt gebruikt.

* Zie het [blogbericht over de Microsoft Graph Security Power BI-connector](https://aka.ms/graphsecuritypowerbiconnectorblogpost) voor enkele gebruikersscenario's en aanvullende informatie.

* Met Power BI Desktop kunt u verbinding maken met allerlei andere gegevens. Bekijk de volgende resources voor meer informatie:

    * [Wat is Power BI Desktop?](desktop-what-is-desktop.md)
    * [Gegevensbronnen in Power BI Desktop](desktop-data-sources.md)
    * [Gegevens vormgeven en combineren met Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Connect to Excel workbooks in Power BI Desktop](desktop-connect-excel.md) (Verbinding maken met Excel-werkmappen in Power BI Desktop)
    * [Enter data directly into Power BI Desktop](desktop-enter-data-directly-into-desktop.md) (Rechtstreeks gegevens in Power BI Desktop invoeren)
