---
title: Inhoud met Azure AD B2B distribueren naar externe gastgebruikers
description: Power BI kan worden geïntegreerd met Azure Active Directory Business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten de organisatie.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101807"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers

Power BI kan worden geïntegreerd met Azure Active Directory Business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten uw organisatie, zonder de controle over de interne gegevens te verliezen.  

Daarnaast kunt u toestaan dat gastgebruikers buiten uw organisatie inhoud in uw organisatie kunnen bewerken en beheren.

## <a name="enable-access"></a>Toegang inschakelen

Zorg ervoor dat u inschakelen de [inhoud delen met externe gebruikers](service-admin-portal.md#export-and-sharing-settings) functie in de Power BI-beheerportal voordat u gastgebruikers uitnodigt.

U kunt ook de [externe gastgebruikers ook kunnen bewerken en beheren van inhoud in de organisatie toestaan](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) functie. Hiermee kunt u selecteren welke gastgebruiker kan zien en inhoud maken in werkruimten, met inbegrip van uw organisatie Power BI te bladeren.

## <a name="who-can-you-invite"></a>Wie kunt u uitnodigen?

U kunt gastgebruikers met elk e-mailadres, met inbegrip van persoonlijke accounts zoals gmail.com, outlook.com en hotmail.com uitnodigen. Azure AD B2B roept deze adressen *sociale identiteiten*.

## <a name="invite-guest-users"></a>Gastgebruikers uitnodigen

Gastgebruikers ook kunnen vereisen uitnodigingen alleen de eerste keer dat u ze voor uw organisatie uitnodigen. Er zijn twee manieren om gebruikers uitnodigen: geplande uitnodigingen en ad-hoc uitnodigingen.

### <a name="planned-invites"></a>Geplande uitnodigingen

Gebruik een geplande uitnodiging als u weet welke gebruikers u wilt uitnodigen. U kunt de uitnodiging verzenden via de Azure-portal of PowerShell. U moet een tenantbeheerder zijn om anderen te kunnen uitnodigen.

Volg deze stappen om een uitnodiging te verzenden via de Azure-portal.

1. Selecteer **Azure Active Directory** in de [Azure-portal](https://portal.azure.com).

1. Onder **beheren**, selecteer **gebruikers** > **alle gebruikers** > **nieuwe gastgebruiker**.

    ![Schermafbeelding van de Azure portal met de nieuwe optie voor de Gast-gebruiker wordt genoemd.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Voer een **e-mailadres** en het **persoonlijke bericht** in.

    ![Schermopname van het dialoogvenster Azure AD Portal nieuwe gastgebruiker.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selecteer **Uitnodigen**.

Als u meerdere gastgebruikers wilt uitnodigen, gebruikt u PowerShell. Zie [Azure Active Directory B2B-samenwerkingscode en voorbeelden van PowerShell](/azure/active-directory/b2b/code-samples/) voor meer informatie.

De gastgebruiker moet in de e-mailuitnodiging die is ontvangen, de optie **Aan de slag** selecteren. De gastgebruiker wordt vervolgens toegevoegd aan de tenant.

![Schermafbeelding van de Gast gebruiker e-mailbericht.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Ad-hoc uitnodigingen

Als u een externe gebruiker uitnodigen op elk gewenst moment, zeker van wilt zijn dat ze naar uw dashboard of rapport via de gebruikersinterface voor delen of uw app via de toegangspagina toevoegen. Hier volgt een voorbeeld van wat te doen wanneer u een externe gebruiker uitnodigt om een app te gebruiken.

![Schermafbeelding van de externe gebruiker is toegevoegd aan App-toegangslijst in Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

De gastgebruiker ontvangt een e-mailbericht dat aangeeft dat u de app met hen hebt gedeeld.

![Schermafbeelding van de e-mailadres voor app die wordt gedeeld met een gastgebruiker](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

De gastgebruiker moet zich aanmelden met het e-mailadres van de organisatie. Ze ontvangt een prompt om de uitnodiging na de aanmelding te accepteren. Na zich heeft aangemeld, wordt de app geopend voor de gastgebruiker. De gastgebruiker kan een bladwijzer naar deze koppeling maken of de e-mail bewaren om terug te keren naar de app.

## <a name="licensing"></a>Licentieverlening

De gastgebruiker moet de juiste licenties om de inhoud die u hebt gedeeld weer te geven. Er zijn drie manieren om te controleren of de gebruiker heeft een juiste licentie: Power BI Premium gebruiken, Power BI Pro-licentie toewijzen of van de Gast Power BI Pro-licentie gebruiken.

Wanneer u de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruikt, hebben gastgebruikers die inhoud aan werkruimten bijdragen of inhoud met anderen delen een Power BI Pro-licentie nodig.

### <a name="use-power-bi-premium"></a>Power BI Premium gebruiken

De app-werkruimte toewijzen [Power BI Premium-capaciteit](service-premium-what-is.md) kunt u de gastgebruiker de app gebruiken zonder een Power BI Pro-licentie. Power BI Premium kunt ook apps te profiteren van andere mogelijkheden, zoals verhoogde vernieuwingsfrequentie, toegewezen capaciteit en grote modellen.

![Diagram van de gebruikerservaring Gast met Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Een Power BI Pro-licentie toewijzen aan een gastgebruiker

Een Power BI Pro-licentie toewijzen aan de gastgebruiker binnen uw tenant, kunt die inhoud Gast gebruiker weergeven in de tenant.

![Diagram van de gebruikerservaring Gast met toewijzen Pro-licentie uit uw tenant.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>De gastgebruiker beschikt over een eigen Power BI Pro-licentie

De gastgebruiker beschikt al over een Power BI Pro-licentie die is toegewezen in hun eigen tenant.

![Diagram van Gast-gebruikerservaring wanneer ze hun eigen licentie meenemen.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Gastgebruikers die inhoud kunnen bewerken en beheren 

Wanneer u de [externe gastgebruikers ook kunnen bewerken en beheren van inhoud in de organisatie toestaan](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) functie, de opgegeven gastgebruikers krijgen toegang tot uw organisatie Power BI. Alle inhoud waarvoor ze gemachtigd, kunnen zij zien. Ze kunnen toegang krijgen tot start, werkruimten bladeren, apps installeren, zien waar ze zich bevinden in de toegangslijst met en inhoud voor werkruimten inzenden. Ze kunnen een beheerder maken of zijn voor werkruimten waarvoor de nieuwe werkruimte-ervaring wordt gebruikt. Er gelden enkele beperkingen. De sectie overwegingen en beperkingen worden deze beperkingen.
 
Om te helpen deze gebruikers zich aanmelden bij Power BI, hen voorzien van de Tenant-URL. Volg deze stap om de tenant-URL te zoeken.

1. Selecteer in de Power BI-service in het bovenste menu Help ( **?** ) en vervolgens **Over Power BI**.

2. Zoek de waarde naast **Tenant-URL**. De waarde is de tenant-URL die u met uw gastgebruikers delen kunt.

    ![Schermafbeelding van over de Power BI-dialoogvenster met de tenant van de gebruiker guest die URL wordt genoemd.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Standaard beperkt de externe Azure AD B2B gasten alleen inhoud. Externe Azure AD B2B-gasten vindt apps, dashboards, rapporten, e-mailabonnementen voor dashboards en rapporten maken en exporteren van gegevens. Ze hebben geen toegang tot werkruimten en kunnen hun eigen inhoud niet publiceren. Maar deze beperkingen gelden niet voor gastgebruikers die toegang krijgen tot en met de [externe gastgebruikers ook kunnen bewerken en beheren van inhoud in de organisatie toestaan](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) functie.

* Gastgebruikers ingeschakeld via de [externe gastgebruikers ook kunnen bewerken en beheren van inhoud in de organisatie toestaan](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) functie, sommige ervaringen zijn niet beschikbaar voor deze. Als ze rapporten willen bijwerken of publiceren, hebben ze de webgebruikersinterface van de Power BI-service nodig, inclusief Gegevens ophalen om de Power BI Desktop-bestanden te uploaden.  De volgende ervaringen worden niet ondersteund:
    * Rechtstreeks publiceren van Power BI Desktop naar de Power BI-service
    * Gastgebruikers ook kunnen Power BI desktop verbinding maken met servicegegevenssets in Power BI-service niet gebruiken
    * Klassieke werkruimten die aan Office 365-groepen zijn gekoppeld:
        * Kan de gastgebruiker maken of beheerders van deze werkruimten
        * Gastgebruikers kunnen lid zijn van
    * Ad-hoc uitnodigingen verzenden wordt niet ondersteund voor toegang tot een lijst met werkruimte
    * Power BI Publisher voor Excel wordt niet ondersteund voor gastgebruikers
    * Gastgebruikers ook kunnen niet mogelijk een Power BI Gateway installeren en verbinding te maken met uw organisatie
    * Gastgebruikers ook kunnen niet installeren apps publiceren naar de hele organisatie
    * Gastgebruikers ook kunnen niet kunnen gebruiken, maken, bijwerken of installeren van de organisatie-inhoudspakketten
    * Gastgebruikers ook kunnen kunnen niet analyseren in Excel gebruiken
    * Gastgebruikers kunnen niet worden @mentioned in opmerkingen
    * Gastgebruikers kunnen niet gebruikmaken van abonnementen
    * Gastgebruikers die deze mogelijkheid gebruiken, moeten over een werk- of schoolaccount beschikken. Gastgebruikers met behulp van persoonlijke accounts te maken met meer beperkingen vanwege beperkingen aanmelden.

* Deze functie is momenteel niet beschikbaar met de Power BI SharePoint Online webonderdeel rapport.

* Er zijn Active Directory-instellingen die de externe gastgebruikers kunnen doen binnen uw organisatie kunt beperken. Dat geldt ook voor uw Power BI-omgeving. De instellingen worden in de volgende documentatie besproken:
    * [Instellingen voor externe samenwerking beheren](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Uitnodigingen aan B2B-gebruikers van specifieke organisaties toestaan of blokkeren](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Volgende stappen

Raadpleeg het technische document voor meer gedetailleerde informatie, hoe beveiliging op rijniveau beveiliging werkt, waaronder: [Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers](https://aka.ms/powerbi-b2b-whitepaper).

Zie voor meer informatie over Azure AD B2B [wat is Azure AD B2B-samenwerking?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
