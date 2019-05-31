---
title: 'Power BI beheren: veelgestelde vragen'
description: Meer informatie over de antwoorden op veelgestelde vragen over Power BI-aanmelding, beheer van tenants en andere beheertaken.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2e51017333a940bd9d7838e6a903c1a66ce2e342
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100792"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Power BI beheren: veelgestelde vragen

Dit artikel bevat veelgestelde vragen over Power BI-beheer. Zie [Wat is Power BI beheer?](service-admin-administering-power-bi-in-your-organization.md) voor een overzicht van Power BI-beheer.

## <a name="whats-in-this-article"></a>In dit artikel

### <a name="sign-up-for-power-bi-section"></a>Registreren voor Power BI

* [PowerShell gebruiken](#using-powershell)
* [Hoe kunnen gebruikers zich registreren voor Power BI?](#how-do-users-sign-up-for-power-bi)
* [Hoe kunnen afzonderlijke gebruikers in mijn organisatie zich registreren?](#how-do-individual-users-in-my-organization-sign-up)
* [Hoe kan ik voorkomen dat gebruikers lid worden van mijn bestaande Office 365-tenant?](#how-can-i-prevent-users-from-joining-my-existing-office-365-tenant)
* [Hoe kan ik toestaan dat gebruikers lid worden van mijn bestaande Office 365-tenant?](#how-can-i-allow-users-to-join-my-existing-office-365-tenant)
* [Hoe kan ik controleren of ik het blok op in de tenant hebben?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hoe voorkom ik dat mijn bestaande gebruikers Power BI gaan gebruiken?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hoe kan ik mijn bestaande gebruikers toestaan zich te registreren voor Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Beheer van Power BI

* [Heeft dit invloed op hoe ik nu identiteiten voor gebruikers in mijn organisatie beheer?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hoe beheer ik Power BI?](#how-do-we-manage-power-bi)
* [Wat is het proces voor het beheren van een tenant die door Microsoft voor mijn gebruikers is gemaakt?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Als ik meerdere domeinen, kan ik beheren aan welke gebruikers toegevoegd aan Office 365-tenant?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to)
* [Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Hoe weet ik wanneer nieuwe gebruikers lid zijn geworden van mijn tenants?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Zijn er nog andere zaken waarop die ik moet voorbereiden?](#are-there-any-additional-things-i-should-prepare-for)
* [Waar bevindt mijn Power BI-tenant zich?](#where-is-my-power-bi-tenant-located)
* [Wat is de Power BI SLA (Service Level Agreement)?](#what-is-the-power-bi-sla)
* [Hoe gaat Power BI om met hoge beschikbaarheid en failover?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Beveiliging in Power BI

* [Voldoet Power BI aan nationale, regionale en branchespecifieke nalevingsvereisten?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hoe werkt beveiliging in Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Registreren voor Power BI

### <a name="using-powershell"></a>PowerShell gebruiken

Voor sommige van de procedures in deze sectie zijn Windows PowerShell-scripts vereist. Als u niet bekend bent met PowerShell, is het raadzaam om eerst de handleiding [Aan de slag met Windows PowerShell](http://go.microsoft.com/fwlink/p/?LinkID=286814) door te nemen. Als u de scripts wilt uitvoeren, moet u eerst de meest recente 64-bits versie van [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/) installeren.

### <a name="how-do-users-sign-up-for-power-bi"></a>Hoe kunnen gebruikers zich registreren voor Power BI?

Als beheerder kunt u zich registreren voor Power BI via de [Power BI-website](https://powerbi.microsoft.com) of de [Aankoopservices](https://admin.microsoft.com/AdminPortal/Home#/catalog) pagina op de Microsoft 365-beheercentrum. Wanneer een beheerder zich registreert voor Power BI, kunnen ze gebruikerslicenties toewijzen aan gebruikers die toegang moeten hebben.

Bovendien kunnen afzonderlijke gebruikers in uw organisatie zich mogelijk registreren voor Power BI via de [Power BI-website](https://powerbi.microsoft.com). Wanneer een gebruiker in uw organisatie zich registreert voor Power BI, de service automatisch een Power BI-licentie toegewezen aan de gebruiker. Zie voor meer informatie, [zich registreren voor Power BI als afzonderlijke gebruiker](service-self-service-signup-for-power-bi.md) en [Power BI-licenties in uw organisatie](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hoe kunnen afzonderlijke gebruikers in mijn organisatie zich registreren?

Er zijn drie scenario's die mogelijk van toepassing zijn op gebruikers in uw organisatie:

* **Scenario 1**: Uw organisatie heeft al een bestaande Office 365-omgeving en de gebruiker die zich registreert voor Power BI heeft al een Office 365-account.
    In dit scenario, als een gebruiker al een werk heeft of school-account in de tenant (bijvoorbeeld contoso.com) maar niet nog Power BI, zijn activeert gewoon Microsoft het abonnement voor dat account. De gebruiker wordt automatisch een melding met informatie over het gebruik van Power BI-service.

* **Scenario 2**: Uw organisatie heeft een bestaande Office 365-omgeving, maar de gebruiker die zich registreert voor Power BI heeft geen Office 365-account.
    In dit scenario wordt de gebruiker heeft een e-mailadres in het domein van uw organisatie (bijvoorbeeld contoso.com) maar nog geen Office 365-account heeft. In dit geval kan de gebruiker zich registreren voor Power BI, waarna die persoon automatisch een account krijgt. Deze actie krijgt de gebruiker toegang tot de Power BI-service. Bijvoorbeeld, als een werknemer genaamd Nancy haar zakelijke e-mailadres (zoals nancy@contoso.com) om u te registreren, Microsoft automatisch toegevoegd Nancy als een gebruiker in Office 365-omgeving van Contoso en wordt Power BI voor dat account geactiveerd.

* **Scenario 3**: Uw organisatie geen Office 365-omgeving die zijn verbonden met uw e-maildomein.
    Er zijn geen beheeracties nodig is voor uw organisatie om te profiteren van Power BI. De service voegt gebruikers toe aan een nieuwe, alleen in de cloud gebruikerslijst. U kunt ook op als de tenantbeheerder overnemen en deze beheren.

> [!IMPORTANT]
> Als uw organisatie meerdere e-maildomeinen heeft en u alle e-mailadresextensies in dezelfde tenant wilt houden, voegt u alle e-mailadresdomeinen aan een Azure Active Directory-tenant toe voordat gebruikers zich registreren. Als u gebruikers hebt gemaakt, is er geen geautomatiseerd mechanisme om gebruikers te verplaatsen tussen tenants. Zie voor meer informatie over dit proces [als ik meerdere domeinen, kan ik bepalen welke gebruikers toegevoegd aan Office 365-tenant?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to) verderop in dit artikel en [een domein toevoegen aan Office 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Hoe kan ik voorkomen dat gebruikers lid worden van mijn bestaande Office 365-tenant?

Er zijn stappen die u als beheerder kunt uitvoeren om te voorkomen dat gebruikers lid worden van uw bestaande Office 365-tenant. Als u de toegang, pogingen van gebruikers om u te registreren mislukken, blokkeren en een bericht waarin weergegeven de accountinschrijving te contact op met van hun organisatie. U hoeft niet te dit proces herhalen als u automatische licentiedistributie (bijvoorbeeld via Office 365 voor onderwijs voor studenten, Onderwijsmedewerkers en personeel) al hebt uitgeschakeld.

Gebruik het volgende PowerShell-script om te voorkomen dat nieuwe gebruikers lid worden van een beheerde tenant. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Het blokkeren van toegang voorkomt dat nieuwe gebruikers in uw organisatie zich kunnen registreren voor Power BI. Gebruikers die zich registreren voor Power BI voordat nieuwe registraties voor uw organisatie worden uitgeschakeld, behouden hun licentie. Als u een gebruiker wilt verwijderen, leest u [Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) verderop in dit artikel.

### <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Hoe kan ik toestaan dat gebruikers lid worden van mijn bestaande Office 365-tenant?

Gebruik de volgende PowerShell-script om nieuwe gebruikers lid worden van een beheerde tenant te laten. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hoe kan ik controleren of ik het blok op in de tenant hebben?

De volgende PowerShell-script gebruiken om instellingen te controleren. *AllowEmailVerifiedUsers* moet false zijn. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hoe voorkom ik dat mijn bestaande gebruikers Power BI gaan gebruiken?

De Azure AD-instelling waarmee dit wordt bepaald, is **AllowAdHocSubscriptions**. De meeste tenants hebben dit ingesteld op true, wat betekent dat deze ingeschakeld. Als u Power BI hebt aangeschaft via een partner, kan dit worden ingesteld op false, wat betekent dat deze uitgeschakeld.

Gebruik het volgende PowerShell-script om ad hoc-abonnementen uit te schakelen. ([Meer informatie over PowerShell][1].)

1. Meld u aan bij Azure Active Directory met uw Office 365-referenties. Met de eerste regel van het volgende PowerShell-script wordt u om uw referenties gevraagd. De tweede regel maakt verbinding met Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Schermopname van Azure Active Directory-aanmelding in via PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Nadat u zich aanmeldt, voer de volgende opdracht uit om te zien hoe uw tenant momenteel is ingesteld.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Voer de volgende opdracht uit om in te schakelen (`$true`) in- of uitschakelen (`$false`) **AllowAdHocSubscriptions**.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Gebruik de **AllowAdHocSubscriptions** vlag voor het beheren van verschillende gebruikersmogelijkheden in uw organisatie, inclusief de mogelijkheid voor gebruikers zich aanmelden voor de Azure Rights Management-Service. Het wijzigen van deze vlag heeft invloed op al deze mogelijkheden.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hoe kan ik mijn bestaande gebruikers toestaan zich te registreren voor Power BI?

Als u wilt toestaan dat uw bestaande gebruikers zich registreren voor Power BI, voert u de opdracht die wordt vermeld voor de vorige vraag, maar doorgeven `$true` in plaats van `$false` in de vorige stap.

## <a name="administration-of-power-bi"></a>Beheer van Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Heeft dit invloed op hoe ik nu identiteiten voor gebruikers in mijn organisatie beheer?

Er zijn drie scenario's die mogelijk van toepassing zijn op gebruikers in uw organisatie:

* **Scenario 1**: Als uw organisatie al een bestaande Office 365-omgeving heeft en alle gebruikers in uw organisatie Office 365-account hebben, is er geen wijziging in het identiteitsbeheer.

* **Scenario 2**: Als uw organisatie al een bestaande Office 365-omgeving heeft, maar niet alle gebruikers in uw organisatie Office 365-accounts hebben, we een gebruiker in de tenant maken en toewijzen van licenties op basis van werk of school-e-mailadres.

    Als gevolg hiervan, neemt het aantal gebruikers die u op een bepaald moment beheert toe naarmate er gebruikers in uw organisatie zich registreren voor de service.

* **Scenario 3**: Als uw organisatie geen Office 365-omgeving die zijn verbonden met uw e-maildomein, is er geen wijziging in het identiteitsbeheer.

    De service voegt gebruikers toe aan een nieuwe, alleen in de cloud gebruikerslijst. U kunt ook overnemen als de tenantbeheerder en deze beheren.

### <a name="how-do-we-manage-power-bi"></a>Hoe beheer ik Power BI?

Power BI biedt een beheerportal waarmee u gebruiksstatistieken, bevat een koppeling naar het Microsoft 365-beheercentrum voor het beheren van gebruikers en groepen, en biedt de mogelijkheid voor het beheren van instellingen voor de gehele tenant.

Voor het gebruik van de Power BI-beheerportal, moet u uw account als markeren een **globale beheerder** in Office 365 of Azure Active Directory, of iemand moet de Power BI service beheerdersrol toewijzen aan uw gebruikersaccount. Zie voor meer informatie, [inzicht in de Power BI-beheerdersrol](service-admin-role.md) en [Power BI-beheerportal](service-admin-portal.md).

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Wat is het proces voor het beheren van een tenant die door Microsoft voor mijn gebruikers is gemaakt?

Wanneer een self-service gebruiker zich aanmeldt voor een cloudservice die gebruikmaakt van Azure AD, de service toegevoegd aan een niet-beheerde Azure AD-directory op basis van hun e-maildomein. U kunt claimen en beheren van de tenant die iemand heeft gemaakt met behulp van een proces dat ook wel een *beheerdersovername*. Afhankelijk van het type van de overname van u dat doet of er een bestaande is tenant die is gekoppeld aan uw domein beheerd:

* Voer een *interne overname* uit om een nieuwe beheerde tenant voor het domein te maken.

* Voer een *externe overname* uit om het domein naar een bestaande beheerde tenant te verplaatsen.

Zie voor meer informatie, [een niet-beheerde directory overnemen als in Azure Active Directory-beheerder](/azure/active-directory/users-groups-roles/domains-admin-takeover).

Als u een externe overname doet, de service plaatst Power BI-inhoud die is gemaakt vóór de overname in een [Power BI gearchiveerde werkruimte](service-admin-power-bi-archived-workspace.md). Inhoud die u wilt gebruiken in de nieuwe tenant, moet u handmatig migreren.

### <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-get-added-to"></a>Als ik meerdere domeinen, kan ik beheren aan welke gebruikers toegevoegd aan Office 365-tenant?

Als u niets doet, maakt de service een tenant voor elke gebruiker e-maildomein en het subdomein. Als u wilt dat alle gebruikers worden toegevoegd aan dezelfde tenant, ongeacht het domein van hun e-mailadres: Een doel-tenant tevoren maken, of gebruik een bestaande tenant. Voeg alle bestaande domeinen en subdomeinen toe die u wilt dat deze tenant. Elke gebruiker met e-mailadres dat eindigt op deze domeinen en subdomeinen automatisch lid van de doel-tenant wanneer ze zich aanmelden.

> [!IMPORTANT]
> Als u gebruikers hebt gemaakt, is er geen ondersteunde geautomatiseerde methode om gebruikers te verplaatsen tussen tenants. Zie [Add your users and domain to Office 365](/office365/admin/setup/add-domain/) (Uw gebruikers en domein toevoegen aan Office 365) voor meer informatie over het toevoegen van domeinen aan een enkele Office 365-tenant.

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?

Als een gebruiker zich heeft geregistreerd voor Power BI, maar u hem of haar geen toegang meer wilt geven tot Power BI, kunt u de Power BI-licentie voor die gebruiker verwijderen.

1. Ga naar het [Microsoft 365-beheercentrum](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Selecteer in de navigatiebalk **Gebruikers** > **Actieve gebruikers**.

1. Zoek de gebruiker waarvoor u de licentie wilt verwijderen en selecteer vervolgens de naam van die persoon.

    U kunt licentiebeheer voor gebruikers ook bulksgewijs uitvoeren. Als u dit wilt doen, selecteert u meerdere gebruikers en selecteert u **Productlicenties bewerken**.

1. Selecteer op de pagina met gebruikersgegevens **Bewerken** naast **Productlicenties**.

1. Afhankelijk van wat u licentie toegepast op het account, stelt u de **Power BI (gratis)** of **Power BI Pro** naar **uit**.

1. Selecteer **Opslaan**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hoe weet ik wanneer nieuwe gebruikers lid zijn geworden van mijn tenants?

Gebruikers die lid zijn geworden van uw tenant als onderdeel van dit programma krijgen een unieke licentie die u kunt filteren op in het deelvenster met actieve gebruikers in het Beheerdashboard in toegewezen. Volg deze stappen voor het maken van deze nieuwe weergave.

1. Navigeer naar het [Microsoft 365-beheercentrum](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Selecteer in de navigatiebalk **Gebruikers** > **Actieve gebruikers**.

1. Selecteer **Aangepaste weergave toevoegen** in het menu **Weergaven**.

1. Geef de nieuwe weergave een naam en selecteer onder **Toegewezen productlicentie** **Power BI (gratis)** of **Power BI Pro**.

    U kunt slechts één licentie per weergave selecteren. Als u licenties voor zowel **Power BI (gratis)** als **Power BI Pro** hebt voor uw organisatie, kunt u twee weergaven maken.

1. Voer desgewenst nog andere voorwaarden in en selecteer vervolgens **Toevoegen**.

1. Nadat u de nieuwe weergave maakt, is beschikbaar via de **weergaven** menu.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Zijn er nog andere zaken waarop die ik moet voorbereiden?

U kunt een toename in aanvragen voor het opnieuw instellen van wachtwoorden ervaren. Zie voor informatie over dit proces [opnieuw instellen van wachtwoord van een gebruiker](/office365/admin/add-users/reset-passwords).

U kunt een gebruiker uit uw tenant verwijderen via het standaardproces in het Microsoft 365-beheercentrum. Als de gebruiker echter nog steeds een actief e-mailadres van uw organisatie heeft, kan die persoon opnieuw lid worden, tenzij u dit blokkeert voor alle gebruikers.

### <a name="where-is-my-power-bi-tenant-located"></a>Waar bevindt mijn Power BI-tenant zich?

Zie voor informatie over welke gegevensregio uw Power BI-tenant bevindt zich in [waar bevindt mijn Power BI-tenant zich?](service-admin-where-is-my-tenant-located.md).

### <a name="what-is-the-power-bi-sla"></a>Wat is de SLA voor Power BI?

Zie voor informatie over de Power BI SLA (Service Level Agreement), de [licentievoorwaarden en documentatie](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) artikel in de **Licensing** sectie van de website Microsoft Licensing.

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hoe gaat Power BI om met hoge beschikbaarheid en failover?

Zie voor informatie over de hoge beschikbaarheid en failover [Power BI hoge beschikbaarheid, failover, en herstel na noodgevallen Veelgestelde vragen over](service-admin-failover.md).

## <a name="security-in-power-bi"></a>Beveiliging in Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Voldoet Power BI aan nationale, regionale en branchespecifieke nalevingsvereisten?

Lees meer informatie over Power BI-naleving in het [Microsoft Vertrouwenscentrum](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hoe werkt beveiliging in Power BI?

Power BI Microsoft gebouwd op basis van Office 365, dat op zijn beurt is gebaseerd op Azure-services zoals Azure Active Directory. Zie [Beveiliging van Power BI](service-admin-power-bi-security.md) voor een overzicht van Power BI-architectuur.

## <a name="next-steps"></a>Volgende stappen

[Power BI-beheerportal](service-admin-portal.md)  
[Understanding the Power BI admin role](service-admin-role.md) (Power BI-beheerdersrol)  
[Registreren voor Power BI via selfservice](service-self-service-signup-for-power-bi.md)  
[Purchasing Power BI Pro](service-admin-purchasing-power-bi-pro.md) (Power BI Pro kopen)  
[Wat is Power BI Premium?](service-premium-what-is.md)  
[Power BI Premium kopen](service-admin-premium-purchase.md)  
[Technisch document over Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Uw groep beheren in Power BI en Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 user account management](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/) (Beheer van Office 365-gebruikersaccounts)  
[Office 365 group management](/office365/admin/email/create-edit-or-delete-a-security-group/) (Beheer van Office 365-groepen)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview