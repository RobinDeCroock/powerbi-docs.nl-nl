---
title: Inhoud met Azure AD B2B distribueren naar externe gastgebruikers
description: Met Power BI kunt u inhoud delen met externe gastgebruikers via Azure Active Directory Business-to-Business (Azure AD B2B).
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: d17c6bbe5ddf6cd39626ac0038595543cd2fecfb
ms.sourcegitcommit: 220910f0b68cb1e265ccd5ac0cee4ee9c6080b26
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82841061"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers

Met Power BI kunt u inhoud delen met externe gastgebruikers via Azure Active Directory Business-to-Business (Azure AD B2B).
Door Azure AD B2B te gebruiken, maakt uw organisatie het delen met externe gebruikers op een centrale locatie mogelijk. Standaard hebben externe gasten een alleen-verbruik-ervaring. Daarnaast kunt u toestaan dat gastgebruikers buiten uw organisatie inhoud in uw organisatie kunnen bewerken en beheren.

Dit artikel bevat een eenvoudige inleiding tot Azure AD B2B in Power BI. Zie [Power BI-inhoud distribueren naar externe gastgebruikers met behulp van Azure Active Directory B2B](guidance/whitepaper-azure-b2b-power-bi.md) voor meer informatie.

## <a name="enable-access"></a>Toegang inschakelen

Zorg ervoor dat u de functie [Inhoud delen met externe gebruikers](service-admin-portal.md#export-and-sharing-settings) in de Power BI-beheerdersportal inschakelt voordat u gastgebruikers uitnodigt. Zelfs wanneer deze optie is ingeschakeld, moet de gebruiker gemachtigd zijn in Azure Active Directory om gastgebruikers uit te nodigen. Deze machtiging wordt verleend via de rol Gastuitnodiging. 

Dankzij de optie om [externe gastgebruikers toe te staan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), hebben gastgebruikers de mogelijkheid om inhoud in werkruimten te zien en maken, en kunnen ze ook door de Power BI van uw organisatie browsen.

> [!NOTE]
> Met de instelling [Inhoud delen met externe gebruikers](service-admin-portal.md#export-and-sharing-settings) bepaalt u of u met Power BI externe gebruikers kunt uitnodigen voor uw organisatie. Zodra een externe gebruiker de uitnodiging accepteert, worden ze een gastgebruiker van Azure AD B2B in uw organisatie. Ze kunnen vervolgens overal in Power BI worden geselecteerd in vervolgkeuzelijsten voor het selecteren van personen. Als de instelling is uitgeschakeld, behouden bestaande gastgebruikers in uw organisatie toegang tot alle items waartoe ze toegang hadden en worden ze ook nog steeds weergegeven in vervolgkeuzelijsten voor het selecteren van personen. Als gasten worden toegevoegd via de benadering van [geplande uitnodigingen](#planned-invites), worden ze ook weergegeven in die vervolgkeuzelijsten. Als u wilt voorkomen dat gastgebruikers toegang hebben tot Power BI, gebruikt u een beleid van Azure AD voor voorwaardelijke toegang.

## <a name="who-can-you-invite"></a>Wie kunt u uitnodigen?

Gastgebruikers met de meeste e-mailadressen kunt u uitnodigen voor uw organisatie, met inbegrip van persoonlijke accounts zoals gmail.com, outlook.com en hotmail.com. In Azure AD B2B worden deze adressen *sociale identiteiten* genoemd.

U kunt geen gebruikers uitnodigen die zijn gekoppeld aan een overheidscloud, zoals [Power BI voor de Amerikaanse overheid](service-govus-overview.md).

## <a name="invite-guest-users"></a>Gastgebruikers uitnodigen

Gastgebruikers hebben alleen een uitnodiging nodig wanneer u deze personen de eerste keer uitnodigt voor uw organisatie. Gebruik geplande of ad-hocuitnodigingen om gebruikers uit te nodigen.

Als u ad-hocuitnodigingen wilt gebruiken, gebruikt u de volgende mogelijkheden:
* Delen van rapporten en dashboards
* Toegangslijst voor app

Ad-hocuitnodigingen worden niet ondersteund in de toegangslijsten van werkruimten. Gebruik de [methode met geplande uitnodigingen](#planned-invites) om deze gebruikers toe te voegen aan uw organisatie. Zodra de externe gebruiker een gast in uw organisatie is, voegt u deze toe aan de toegangslijst voor de werkruimte.

### <a name="planned-invites"></a>Geplande uitnodigingen

Gebruik een geplande uitnodiging als u weet welke gebruikers u wilt uitnodigen. U kunt de uitnodigingen verzenden via Azure Portal of PowerShell. U moet een tenantbeheerder zijn om anderen te kunnen uitnodigen.

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

[Gastgebruikers die inhoud in de organisatie kunnen bewerken en beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) hebben een Power BI Pro-licentie nodig om inhoud bij te dragen aan werkruimten of om inhoud te delen met anderen.

### <a name="use-power-bi-premium"></a>Power BI Premium gebruiken

Door de werkruimte toe te wijzen aan [Power BI Premium-capaciteit](service-premium-what-is.md) kan de gastgebruiker de app gebruiken zonder een licentie voor Power BI Pro. Met Power BI Premium kunnen apps ook profiteren van andere mogelijkheden, zoals een verhoogde vernieuwingsfrequentie, toegewezen capaciteit en grote modellen.

![Diagram van de ervaring van gastgebruikers bij gebruik van Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Een Power BI Pro-licentie toewijzen aan een gastgebruiker

Als u in uw tenant een Power BI Pro-licentie toewijst aan een gastgebruiker, kan die gastgebruiker inhoud in de tenant bekijken. Zie [Licenties toewijzen aan gebruikers op de pagina Licenties](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page) voor meer informatie over het toewijzen van licenties. Voordat u Pro-licenties toewijst aan gastgebruikers, neemt u contact op met uw Microsoft-accountvertegenwoordiger om te controleren of u voldoet aan de voorwaarden van uw overeenkomst met Microsoft.

![Diagram van de ervaring van gastgebruikers bij het toewijzen van een Pro-licentie vanuit uw tenant.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>De gastgebruiker beschikt over een eigen Power BI Pro-licentie

De gastgebruiker beschikt al over een Power BI Pro-licentie die is toegewezen in hun eigen tenant.

![Diagram van de ervaring van gastgebruikers wanneer ze hun eigen licentie meenemen.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Gastgebruikers die inhoud kunnen bewerken en beheren

Wanneer u de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruikt, krijgen de opgegeven gastgebruikers aanvullende toegang tot de Power BI van uw organisatie. Toegestane gasten kunnen alle inhoud zien waarvoor ze machtigingen hebben, ze kunnen toegang krijgen tot de startpagina, door werkruimten browsen, apps installeren, kijken waar ze op de toegangslijst staan en inhoud bijdragen aan werkruimten. Ze kunnen een beheerder maken of zijn voor werkruimten waarvoor de nieuwe werkruimte-ervaring wordt gebruikt. Er gelden enkele beperkingen. Zie het gedeelte Overwegingen en beperkingen voor deze beperkingen.
 
Toegestane gasten hebben de tenant-URL nodig om zich te kunnen aanmelden bij Power BI. Volg deze stap om de tenant-URL te zoeken.

1. Selecteer in de Power BI-service in het bovenste menu Help ( **?** ) en vervolgens **Over Power BI**.

2. Zoek de waarde naast **Tenant-URL**. Deel de tenant-URL met uw toegestane gastgebruikers.

    ![Schermopname van het dialoogvenster met informatie over Power BI, met de tenant-URL voor de gastgebruiker omkaderd.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Standaard mogen externe gasten van Azure AD B2B alleen inhoud gebruiken. Externe gasten van Azure AD B2B kunnen apps, dashboards en rapporten weergeven, gegevens exporteren en e-mailabonnementen instellen voor dashboards en rapporten. Ze hebben geen toegang tot werkruimten en kunnen hun eigen inhoud niet publiceren. U kunt de functie [Externe gastgebruikers toestaan om inhoud in de organisatie te bewerken en te beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) gebruiken om deze beperkingen te verwijderen.

* U hebt een Power BI Pro-licentie nodig om gastgebruikers uit te nodigen. Gebruikers van de Pro-proefversie kunnen geen gastgebruikers uitnodigen in Power BI.

* Sommige ervaringen zijn niet beschikbaar voor [gastgebruikers die inhoud in de organisatie kunnen bewerken en beheren](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization). Als ze rapporten willen bijwerken of publiceren, hebben ze de webgebruikersinterface van de Power BI-service nodig, inclusief Gegevens ophalen om de Power BI Desktop-bestanden te uploaden.  De volgende ervaringen worden niet ondersteund:
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
    * Gastgebruikers die deze mogelijkheid gebruiken, moeten over een werk- of schoolaccount beschikken. 
    
* Gastgebruikers die persoonlijke accounts gebruiken, ondervinden meer beperkingen vanwege beperkte aanmeldingsmogelijkheden.
    * Ze kunnen gebruikmaken van gebruikservaringen in de Power BI-service via een webbrowser
    * Ze kunnen geen Power BI - Mobiel-apps gebruiken.
    * Ze kunnen zich niet aanmelden om referenties op te geven wanneer een werk- of schoolaccount vereist is.

* Deze functie is momenteel niet beschikbaar in het webonderdeel voor Power BI SharePoint Online-rapporten.

* Er bestaan Active Directory-instellingen waardoor gastgebruikers mogelijk minder acties kunnen uitvoeren in uw totale organisatie en die ook van toepassing zijn op uw Power BI-omgeving. De instellingen worden in de volgende documentatie besproken:
    * [Instellingen voor externe samenwerking beheren](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [Uitnodigingen aan B2B-gebruikers van specifieke organisaties toestaan of blokkeren](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)
    * [Toestaan of weigeren dat gastgebruikers toegang hebben tot de Power BI-service](/azure/active-directory/conditional-access/overview)
    
* Delen buiten uw organisatie wordt niet ondersteund voor nationale clouds. Maak in plaats daarvan gebruikersaccounts in uw organisatie die externe gebruikers kunnen gebruiken om toegang te krijgen tot de inhoud. 

* Als u rechtstreeks deelt met een gastgebruiker, stuurt Power BI deze gebruiker een e-mail met de koppeling. Als u wilt voorkomen dat een e-mailbericht wordt verzonden, voegt u de gastgebruiker toe aan een beveiligingsgroep en deelt u met de beveiligingsgroep.  

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende whitepaper voor meer informatie, zoals informatie over hoe beveiliging op rijniveau werkt: [Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers](https://aka.ms/powerbi-b2b-whitepaper).

Zie [Wat is B2B-samenwerking van Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/) voor informatie over Azure AD B2B.
