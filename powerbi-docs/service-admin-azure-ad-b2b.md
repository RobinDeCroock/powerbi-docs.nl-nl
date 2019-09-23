---
title: Inhoud met Azure AD B2B distribueren naar externe gastgebruikers
description: Power BI kan worden geïntegreerd met Azure Active Directory Business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten de organisatie.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b7327a7b32aacd222efc422263187f29285bd73
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075778"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers

Power BI kan worden geïntegreerd met Azure Active Directory Business-to-business (Azure AD B2B) voor een veilige distributie van Power BI-inhoud naar gastgebruikers buiten uw organisatie, zonder de controle over de interne gegevens te verliezen.  

Daarnaast kunt u toestaan dat gastgebruikers buiten uw organisatie inhoud in uw organisatie kunnen bewerken en beheren.

## <a name="enable-access"></a>Toegang inschakelen

Zorg ervoor dat u de functie [Inhoud delen met externe gebruikers](service-admin-portal.md#export-and-sharing-settings) in de Power BI-beheerdersportal inschakelt voordat u gastgebruikers uitnodigt.

U kunt ook de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruiken. Hiermee kunt u selecteren welke gastgebruiker inhoud kan zien en maken in werkruimten, en ook kan bladeren in de Power BI-omgeving van uw organisatie.

## <a name="who-can-you-invite"></a>Wie kunt u uitnodigen?

U kunt gastgebruikers met ongeacht welk e-mailadres uitnodigen, met inbegrip van persoonlijke accounts zoals gmail.com, outlook.com of hotmail.com. In Azure AD B2B worden deze adressen *sociale identiteiten* genoemd.

## <a name="invite-guest-users"></a>Gastgebruikers uitnodigen

Gastgebruikers hebben alleen een uitnodiging nodig wanneer u deze personen de eerste keer uitnodigt voor uw organisatie. Er zijn twee manieren om gebruikers uit te nodigen: met geplande uitnodigingen en met ad-hocuitnodigingen.

### <a name="planned-invites"></a>Geplande uitnodigingen

Gebruik een geplande uitnodiging als u weet welke gebruikers u wilt uitnodigen. U kunt de uitnodiging verzenden via de Azure-portal of PowerShell. U moet een tenantbeheerder zijn om anderen te kunnen uitnodigen.

Volg deze stappen om een uitnodiging te verzenden via de Azure-portal.

1. Selecteer **Azure Active Directory** in de [Azure-portal](https://portal.azure.com).

1. Selecteer onder **Beheren** **Gebruikers** > **Alle gebruikers** > **Nieuwe gastgebruiker**.

    ![Schermopname van de Azure-portal met de optie Nieuwe gastgebruiker omkaderd.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Voer een **e-mailadres** en het **persoonlijke bericht** in.

    ![Schermopname van het dialoogvenster Nieuwe gastgebruiker in de Azure AD-portal.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selecteer **Uitnodigen**.

Als u meerdere gastgebruikers wilt uitnodigen, gebruikt u PowerShell. Zie [Azure Active Directory B2B-samenwerkingscode en voorbeelden van PowerShell](/azure/active-directory/b2b/code-samples/) voor meer informatie.

De gastgebruiker moet in de e-mailuitnodiging die is ontvangen, de optie **Aan de slag** selecteren. De gastgebruiker wordt vervolgens toegevoegd aan de tenant.

![Schermopname van e-mailuitnodiging voor een gastgebruiker.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Ad-hocuitnodigingen

Als u een externe gebruiker wilt uitnodigen, voegt u de persoon toe aan uw dashboard of meldt u dit via de gebruikersinterface voor delen of uw app via de toegangspagina. Hier volgt een voorbeeld van wat te doen wanneer u een externe gebruiker uitnodigt om een app te gebruiken.

![Schermopname van externe gebruiker die is toegevoegd aan de app-toegangslijst in Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

De gastgebruiker krijgt een e-mail met het bericht dat u de app met hem of haar hebt gedeeld.

![Schermopname van e-mail voor delen van app met een gastgebruiker](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

De gastgebruiker moet zich aanmelden met het e-mailadres van de organisatie. Zodra de gastgebruiker zich heeft aangemeld, wordt deze gevraagd de uitnodiging te accepteren. Als het aanmelden is voltooid, wordt de app geopend voor de gastgebruiker. De gastgebruiker kan een bladwijzer naar deze koppeling maken of de e-mail bewaren om terug te keren naar de app.

## <a name="licensing"></a>Licentieverlening

De gastgebruiker moet over de juiste licenties beschikken om de inhoud te zien die u hebt gedeeld. Er zijn drie manieren om ervoor te zorgen dat de gebruiker een geschikte licentie heeft: door Power BI Premium te gebruiken, door een Power BI Pro-licentie toe te wijzen of door de Power BI Pro-licentie van de gast te gebruiken.

Wanneer u de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruikt, hebben gastgebruikers die inhoud aan werkruimten bijdragen of inhoud met anderen delen een Power BI Pro-licentie nodig.

### <a name="use-power-bi-premium"></a>Power BI Premium gebruiken

Door de app-werkruimte toe te wijzen aan [Power BI Premium-capaciteit](service-premium-what-is.md), kan de gastgebruiker de app gebruiken zonder een licentie voor Power BI Pro. Met Power BI Premium kunnen apps ook profiteren van andere mogelijkheden, zoals een verhoogde vernieuwingsfrequentie, toegewezen capaciteit en grote modellen.

![Diagram van de ervaring van gastgebruikers bij gebruik van Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Een Power BI Pro-licentie toewijzen aan een gastgebruiker

Als u in uw tenant een Power BI Pro-licentie toewijst aan een gastgebruiker, kan die gastgebruiker inhoud in de tenant bekijken.

![Diagram van de ervaring van gastgebruikers bij het toewijzen van een Pro-licentie vanuit uw tenant.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>De gastgebruiker beschikt over een eigen Power BI Pro-licentie

De gastgebruiker beschikt al over een Power BI Pro-licentie die is toegewezen in hun eigen tenant.

![Diagram van de ervaring van gastgebruikers wanneer ze hun eigen licentie meenemen.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Gastgebruikers die inhoud kunnen bewerken en beheren 

Wanneer u de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruikt, krijgen de opgegeven gastgebruikers toegang tot de Power BI van uw organisatie en kunnen ze alle inhoud zien waarvoor ze een machtiging hebben. Ze kunnen toegang krijgen tot de startpagina, door werkruimten browsen, apps installeren, kijken waar ze op de toegangslijst staan en inhoud bijdragen aan werkruimten. Ze kunnen een beheerder maken of zijn voor werkruimten waarvoor de nieuwe werkruimte-ervaring wordt gebruikt. Er gelden enkele beperkingen. Zie het gedeelte Overwegingen en beperkingen voor deze beperkingen.
 
Deze gebruikers hebben de tenant-URL nodig om zich te kunnen aanmelden bij Power BI. Volg deze stap om de tenant-URL te zoeken.

1. Selecteer in de Power BI-service in het bovenste menu Help ( **?** ) en vervolgens **Over Power BI**.

2. Zoek de waarde naast **Tenant-URL**. Deze waarde is de tenant-URL die u met uw gastgebruikers kunt delen.

    ![Schermopname van het dialoogvenster met informatie over Power BI, met de tenant-URL voor de gastgebruiker omkaderd.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Standaard mogen externe gasten van Azure AD B2B alleen inhoud gebruiken. Externe gasten van Azure AD B2B kunnen apps, dashboards en rapporten weergeven, gegevens exporteren en e-mailabonnementen instellen voor dashboards en rapporten. Ze hebben geen toegang tot werkruimten en kunnen hun eigen inhoud niet publiceren. Deze beperkingen zijn echter niet van toepassing op gastgebruikers die toegang krijgen via de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization).

* Voor gastgebruikers die via de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) zijn ingeschakeld, zijn mogelijk niet alle ervaringen beschikbaar. Als ze rapporten willen bijwerken of publiceren, hebben ze de webgebruikersinterface van de Power BI-service nodig, inclusief Gegevens ophalen om de Power BI Desktop-bestanden te uploaden.  De volgende ervaringen worden niet ondersteund:
    * Rechtstreeks publiceren van Power BI Desktop naar de Power BI-service
    * Gastgebruikers kunnen geen gebruikmaken van Power BI Desktop om verbinding te maken met servicegegevenssets in de Power BI-service
    * Klassieke werkruimten die aan Office 365-groepen zijn gekoppeld:
        * Gastgebruikers kunnen geen beheerders van deze werkruimten maken of zijn
        * Gastgebruikers kunnen lid zijn
    * Ad-hocuitnodigingen verzenden wordt niet ondersteund voor toegangslijsten van werkruimten
    * Power BI Publisher voor Excel wordt niet ondersteund voor gastgebruikers
    * Gastgebruikers kunnen geen Power BI Gateway installeren of deze aan uw organisatie koppelen
    * Gastgebruikers kunnen geen apps installeren en naar de hele organisatie publiceren
    * Gastgebruikers kunnen geen organisatie-inhoudspakketten gebruiken, maken, bijwerken of installeren
    * Gastgebruikers kunnen niet analyseren in Excel
    * Gastgebruikers kunnen niet met @mentioned worden genoemd in opmerkingen
    * Gastgebruikers kunnen geen abonnementen gebruiken
    * Gastgebruikers die deze mogelijkheid gebruiken, moeten over een werk- of schoolaccount beschikken. Gastgebruikers die persoonlijke accounts gebruiken, ondervinden meer beperkingen vanwege beperkte aanmeldingsmogelijkheden.

* Deze functie is momenteel niet beschikbaar in het webonderdeel voor Power BI SharePoint Online-rapporten.

* Er bestaan Active Directory-instellingen waardoor gastgebruikers mogelijk minder acties kunnen uitvoeren in uw totale organisatie en die ook van toepassing zijn op uw Power BI-omgeving. De instellingen worden in de volgende documentatie besproken:
    * [Instellingen voor externe samenwerking beheren](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [Uitnodigingen aan B2B-gebruikers van specifieke organisaties toestaan of blokkeren](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende whitepaper voor meer informatie, zoals informatie over hoe beveiliging op rijniveau werkt: [Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers](https://aka.ms/powerbi-b2b-whitepaper).

Zie [Wat is B2B-samenwerking van Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/) voor informatie over Azure AD B2B.
