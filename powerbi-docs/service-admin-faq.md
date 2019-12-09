---
title: 'Power BI beheren: veelgestelde vragen'
description: Lees de antwoorden op veelgestelde vragen over aanmelding bij Power BI, tenantbeheer en andere beheertaken.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 0c9d346017dc3b18abd6a56d0d3a62e1305e6575
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698734"
---
# <a name="administering-power-bi---frequently-asked-questions-faq"></a>Power BI beheren: veelgestelde vragen

Dit artikel bevat veelgestelde vragen over Power BI-beheer. Zie [Wat is Power BI beheer?](service-admin-administering-power-bi-in-your-organization.md) voor een overzicht van Power BI-beheer.

## <a name="whats-in-this-article"></a>In dit artikel

### <a name="sign-up-for-power-bi-section"></a>Registreren voor Power BI

* [PowerShell gebruiken](#using-powershell)
* [Hoe kunnen gebruikers zich registreren voor Power BI?](#how-do-users-sign-up-for-power-bi)
* [Hoe kunnen afzonderlijke gebruikers in mijn organisatie zich registreren?](#how-do-individual-users-in-my-organization-sign-up)
* [Hoe kan ik voorkomen dat gebruikers lid worden van mijn bestaande Office 365-tenant?](#how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant)
* [Hoe kan ik toestaan dat gebruikers lid worden van mijn bestaande Office 365-tenant?](#how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant)
* [Hoe kan ik controleren of blokkeren is ingeschakeld in de tenant?](#how-do-i-check-if-i-have-the-block-on-in-the-tenant)
* [Hoe voorkom ik dat mijn bestaande gebruikers Power BI gaan gebruiken?](#how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi)
* [Hoe kan ik mijn bestaande gebruikers toestaan zich te registreren voor Power BI?](#how-can-i-allow-my-existing-users-to-sign-up-for-power-bi)

### <a name="administration-of-power-bi-section"></a>Beheer van Power BI

* [Heeft dit invloed op hoe ik nu identiteiten voor gebruikers in mijn organisatie beheer?](#how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today)
* [Hoe beheer ik Power BI?](#how-do-we-manage-power-bi)
* [Wat is het proces voor het beheren van een tenant die door Microsoft voor mijn gebruikers is gemaakt?](#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users)
* [Kan ik beheren aan welke Microsoft 365-tenant gebruikers worden toegevoegd, als ik meerdere domeinen heb?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to)
* [Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?](#how-do-i-remove-power-bi-for-users-that-already-signed-up)
* [Hoe weet ik wanneer nieuwe gebruikers lid zijn geworden van mijn tenants?](#how-do-i-know-when-new-users-have-joined-my-tenant)
* [Zijn er nog andere zaken waarop ik me moet voorbereiden?](#are-there-any-additional-things-i-should-prepare-for)
* [Waar bevindt mijn Power BI-tenant zich?](#where-is-my-power-bi-tenant-located)
* [Wat is de Power BI SLA (Service Level Agreement)?](#what-is-the-power-bi-sla)
* [Hoe gaat Power BI om met hoge beschikbaarheid en failover?](#how-does-power-bi-handle-high-availability-and-failover)

### <a name="security-in-power-bi-section"></a>Beveiliging in Power BI

* [Voldoet Power BI aan nationale, regionale en branchespecifieke nalevingsvereisten?](#does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements)
* [Hoe werkt beveiliging in Power BI?](#how-does-security-work-in-power-bi)

## <a name="sign-up-for-power-bi"></a>Registreren voor Power BI

### <a name="using-powershell"></a>PowerShell gebruiken

Voor sommige van de procedures in deze sectie zijn Windows PowerShell-scripts vereist. Als u niet bekend bent met PowerShell, is het raadzaam om eerst de handleiding [Aan de slag met Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=286814) door te nemen. Als u de scripts wilt uitvoeren, moet u eerst de meest recente 64-bits versie van [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/) installeren.

### <a name="how-do-users-sign-up-for-power-bi"></a>Hoe kunnen gebruikers zich registreren voor Power BI?

Als Microsoft 365-beheerder kunt u zich registreren voor Power BI via de [Power BI-website](https://powerbi.microsoft.com) of [de pagina voor het kopen van services](https://admin.microsoft.com/AdminPortal/Home#/catalog) in het Microsoft 365-beheercentrum. Als een Microsoft 365-beheerder zich voor Power BI registreert, kan diegene gebruikerslicenties toewijzen aan gebruikers die toegang nodig hebben.

Bovendien kunnen afzonderlijke gebruikers in uw organisatie zich mogelijk registreren voor Power BI via de [Power BI-website](https://powerbi.microsoft.com). Wanneer een gebruiker in uw organisatie zich registreert voor Power BI, wordt automatisch een Power BI-licentie aan die gebruiker toegewezen. Meer informatie leest u in [Registreren voor Power BI als afzonderlijke gebruiker](service-self-service-signup-for-power-bi.md) en [Power BI-licenties in uw organisatie](service-admin-licensing-organization.md).

### <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hoe kunnen afzonderlijke gebruikers in mijn organisatie zich registreren?

Er zijn drie scenario's die mogelijk van toepassing zijn op gebruikers in uw organisatie:

* **Scenario 1**: Uw organisatie heeft al een bestaande Microsoft 365-omgeving en de gebruiker die zich registreert voor Power BI heeft al een Microsoft 365-account.
    Als een gebruiker in dit scenario al een werk- of schoolaccount in de tenant heeft (bijvoorbeeld contoso.com) maar niet beschikt over Power BI, wordt het gratis Power BI-abonnement voor dat account geactiveerd door Microsoft. De gebruiker wordt automatisch op de hoogte gesteld van het gebruik van de Power BI-service.

* **Scenario 2**: Uw organisatie heeft een bestaande Microsoft 365-omgeving, maar de gebruiker die zich voor Power BI registreert, heeft geen Microsoft 365-account.
    In dit scenario heeft de gebruiker een e-mailadres in het domein van uw organisatie (bijvoorbeeld contoso.com), maar nog geen Microsoft 365-account. In dit geval kan de gebruiker zich registreren voor Power BI, waarna die persoon automatisch een account krijgt. Door deze actie krijgt de gebruiker toegang tot de Power BI-service. Als een werknemer genaamd Nancy bijvoorbeeld haar zakelijke e-mailadres (zoals nancy@contoso.com) gebruikt om zich te registreren, voegt Microsoft Nancy automatisch toe als gebruiker in de Microsoft 365-omgeving van Contoso en wordt Power BI voor dat account geactiveerd.

* **Scenario 3**: Uw organisatie heeft nog geen Microsoft 365-omgeving die is gekoppeld aan uw e-maildomein.
    Uw organisatie hoeft geen acties op het gebied van beheer uit te voeren om Power BI te gebruiken. Door de service worden gebruikers toegevoegd aan een nieuwe gebruikersdirectory die uitsluitend in de cloud bestaat. U kunt er ook voor kiezen om het globale Microsoft 365-beheer voor de tenant over te nemen en de tenant te beheren.

> [!IMPORTANT]
> Als uw organisatie meerdere e-maildomeinen heeft en u alle e-mailadresextensies in dezelfde tenant wilt houden, voegt u alle e-mailadresdomeinen aan een Azure Active Directory-tenant toe voordat gebruikers zich registreren. Zodra u gebruikers hebt gemaakt, is er geen geautomatiseerd mechanisme om gebruikers over te plaatsen naar andere tenants. Voor meer informatie over dit proces bekijkt u [Kan ik beheren aan welke Microsoft 365-tenant gebruikers worden toegevoegd, als ik meerdere domeinen heb?](#if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to) verderop in dit artikel en [Een domein toevoegen aan Microsoft 365](/office365/admin/setup/add-domain/).

### <a name="how-can-i-prevent-users-from-joining-my-existing-microsoft-365-tenant"></a>Hoe kan ik voorkomen dat gebruikers lid worden van mijn bestaande Microsoft 365-tenant?

Er zijn stappen die u als globale Microsoft 365-beheerder kunt uitvoeren om te voorkomen dat gebruikers lid worden van uw bestaande Microsoft 365-tenant. Als u de toegang blokkeert, mislukken pogingen van gebruikers om zich te registreren en wordt een bericht weergegeven dat ze contact kunnen opnemen met de beheerder van hun organisatie. U hoeft dit proces niet te herhalen als u automatische distributie van licenties (zoals Office 365 voor onderwijs voor studenten, onderwijsmedewerkers en personeel) al hebt uitgeschakeld.

Gebruik het volgende PowerShell-script om te voorkomen dat nieuwe gebruikers lid worden van een beheerde tenant. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $false
```

> [!NOTE]
> Het blokkeren van toegang voorkomt dat nieuwe gebruikers in uw organisatie zich kunnen registreren voor Power BI. Gebruikers die zich registreren voor Power BI voordat nieuwe registraties voor uw organisatie worden uitgeschakeld, behouden hun licentie. Als u een gebruiker wilt verwijderen, leest u [Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) verderop in dit artikel.

### <a name="how-can-i-allow-users-to-join-my-existing-microsoft-365-tenant"></a>Hoe kan ik toestaan dat gebruikers lid worden van mijn bestaande Microsoft 365-tenant?

Gebruik het volgende PowerShell-script om toe te staan dat nieuwe gebruikers lid worden van een beheerde tenant. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Set-MsolCompanySettings -AllowEmailVerifiedUsers $true
```

### <a name="how-do-i-check-if-i-have-the-block-on-in-the-tenant"></a>Hoe kan ik controleren of blokkeren is ingeschakeld in de tenant?

Gebruik het volgende PowerShell-script om instellingen te controleren. *AllowEmailVerifiedUsers* moet false zijn. ([Meer informatie over PowerShell][1].)

```powershell
$msolcred = get-credential
connect-msolservice -credential $msolcred

Get-MsolCompanyInformation | fl allow*
```

### <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hoe voorkom ik dat mijn bestaande gebruikers Power BI gaan gebruiken?

De Azure AD-instelling waarmee dit wordt bepaald, is **AllowAdHocSubscriptions**. Bij de meeste tenants is deze instelling ingesteld op *true*, wat betekent dat de instelling is ingeschakeld. Als u Power BI hebt gekocht via een partner, kan deze instelling zijn ingesteld op *false*, wat betekent dat de instelling is uitgeschakeld.

Gebruik het volgende PowerShell-script om ad hocabonnementen uit te schakelen. ([Meer informatie over PowerShell][1].)

1. Meld u aan bij Azure Active Directory met uw Microsoft 365-referenties. Met de eerste regel van het volgende PowerShell-script wordt u om uw referenties gevraagd. De tweede regel maakt verbinding met Azure Active Directory.

    ```powershell
     $msolcred = get-credential
     connect-msolservice -credential $msolcred
    ```

   ![Schermopname van aanmelding bij Azure Active Directory via PowerShell](media/service-admin-licensing-organization/azure-ad-sign-in.png)

1. Nadat u bent aangemeld, voert u de volgende opdracht uit om te controleren hoe uw tenant momenteel is ingesteld.

    ```powershell
     Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
    ```

1. Voer de volgende opdracht uit om (`$true`) in te schakelen of (`$false`) **AllowAdHocSubscriptions** uit te schakelen.

    ```powershell
     Set-MsolCompanySettings -AllowAdHocSubscriptions $false
    ```

> [!NOTE]
> Gebruik de vlag **AllowAdHocSubscriptions** voor het beheren van verschillende gebruikersmogelijkheden in uw organisatie, inclusief de mogelijkheid voor gebruikers om zich te registreren voor de Azure Rights Management-service. Het wijzigen van deze vlag heeft invloed op al deze mogelijkheden. Als *false* is ingesteld, kunnen gebruikers zich nog steeds registreren voor een individuele Power BI Pro-proefversie.

### <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hoe kan ik mijn bestaande gebruikers toestaan zich te registreren voor Power BI?

Als u wilt toestaan dat uw bestaande gebruikers zich registreren voor Power BI, voert u de opdracht uit die wordt vermeld voor de vorige vraag, maar geeft u in de laatste stap `$true` op in plaats van `$false`.

## <a name="administration-of-power-bi"></a>Beheer van Power BI

### <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Heeft dit invloed op hoe ik nu identiteiten voor gebruikers in mijn organisatie beheer?

Er zijn drie scenario's die mogelijk van toepassing zijn op gebruikers in uw organisatie:

* **Scenario 1**: Als uw organisatie al een bestaande Microsoft 365-omgeving heeft en alle gebruikers in uw organisatie Microsoft 365-accounts hebben, verandert er niets aan het beheer van identiteiten.

* **Scenario 2**: Als uw organisatie al een bestaande Microsoft 365-omgeving heeft, maar niet alle gebruikers in uw organisatie een Microsoft 365-account hebben, maken we een gebruiker in de tenant en wijzen we licenties toe op basis van het e-mailadres voor werk of school van de gebruiker.

    Hierdoor zal het aantal gebruikers dat u beheert, toenemen naarmate er meer gebruikers in uw organisatie zich registreren voor de service.

* **Scenario 3**: Als uw organisatie nog geen Microsoft 365-omgeving aan uw e-maildomein heeft gekoppeld, verandert er niets aan uw identiteitsbeheer.

    De service voegt gebruikers toe aan een nieuwe adreslijst met uitsluitend cloudgebruikers, die u als globale Microsoft 365-beheerder kunt overnemen en beheren.

### <a name="how-do-we-manage-power-bi"></a>Hoe beheer ik Power BI?

Power BI biedt een Power BI-beheerportal voor gebruikers met de rol van globale Microsoft 365-beheerder en gebruikers met de rol van beheerder voor de Power BI-service. Als u de Power BI-beheerportal wilt gebruiken, moet u uw account als een **Globale beheerder** markeren in Microsoft 365 of Azure Active Directory, of iemand moet de rol van Power BI-servicebeheerder aan uw gebruikersaccount toewijzen. Zie [Uitleg over de Power BI-beheerdersrol](service-admin-role.md) en [Power BI-beheerportal](service-admin-portal.md) voor meer informatie. De portal biedt de mogelijkheid om instellingen voor de gehele tenant te beheren en gebruiksstatistieken voor Power BI te bekijken en een koppeling naar het Microsoft 365-beheercentrum om gebruikers en groepen te beheren.

### <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Wat is het proces voor het beheren van een tenant die door Microsoft voor mijn gebruikers is gemaakt?

Wanneer een selfservicegebruiker zich aanmeldt voor een cloudservice die gebruikmaakt van Azure AD, wordt de gebruiker toegevoegd aan een onbeheerde Azure AD-directory op basis van zijn e-maildomein. U kunt een tenant die iemand heeft gemaakt, claimen en beheren in een proces dat bekendstaat als *beheerdersovername*. Raadpleeg [Een onbeheerde directory overnemen als beheerder in Azure Active Directory](/azure/active-directory/users-groups-roles/domains-admin-takeover) voor meer informatie. Welk type overname u uitvoert, hangt af van het gegeven of er aan uw domein al een bestaande beheerde tenant is gekoppeld:

* Power BI ondersteunt interne beheerdersovername. Wanneer u een _interne_ beheerdersovername uitvoert van een niet-beheerde Azure-adreslijst, wordt u als de globale beheerder van de niet-beheerde adreslijst toegevoegd. Er worden geen gebruikers, domeinen of serviceabonnementen gemigreerd naar een andere adreslijst die u beheert.

* Power BI biedt geen ondersteuning meer voor externe beheerdersovername. Wanneer u een _externe_ beheerdersovername uitvoert voor een niet-beheerde Azure-adreslijst, voegt u de DNS-domeinnaam van de niet-beheerde adreslijst toe aan uw beheerde Azure-adreslijst. Een externe overname leidt tot verlies van toegang tot alle Power BI-inhoud van de oorspronkelijke onbeheerde tenant. Power BI-rapporten moeten opnieuw worden gepubliceerd naar de nieuwe tenant en Power BI-dashboards en -apps moeten opnieuw worden gemaakt in de nieuwe tenant.

### <a name="if-i-have-multiple-domains-can-i-control-the-microsoft-365-tenant-that-users-get-added-to"></a>Kan ik beheren aan welke Microsoft 365-tenant gebruikers worden toegevoegd als ik meerdere domeinen heb?

Als u niets doet, wordt er een tenant gemaakt voor elk domein en subdomein dat hoort bij de e-mailadressen van uw gebruikers. Als u wilt dat alle gebruikers worden toegevoegd aan dezelfde tenant, ongeacht het domein van hun e-mailadres: Maak vooraf een tenant of gebruik een bestaande tenant. Voeg vervolgens alle bestaande domeinen en subdomeinen die u wilt samenvoegen toe aan deze tenant. Alle gebruikers met een e-mailadres dat eindigt op deze domeinen en subdomeinen, worden automatisch lid van de doeltenant wanneer ze zich aanmelden.

> [!IMPORTANT]
> Zodra u gebruikers hebt gemaakt, is er geen ondersteund geautomatiseerd mechanisme om gebruikers over te plaatsen naar andere tenants. Zie [Uw gebruikers en domein toevoegen aan Microsoft 365](/office365/admin/setup/add-domain/) voor meer informatie over het toevoegen van domeinen aan een enkele Microsoft 365-tenant.

### <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hoe verwijder ik Power BI voor gebruikers die zich al hebben geregistreerd?

Als een gebruiker zich heeft geregistreerd voor Power BI, maar u hem of haar geen toegang meer wilt geven tot Power BI, kunt u de Power BI-licentie voor die gebruiker verwijderen.

1. Ga naar het [Microsoft 365-beheercentrum](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Selecteer in het navigatievenster **Gebruikers** > **Actieve gebruikers**.

1. Zoek de gebruiker waarvoor u de licentie wilt verwijderen en selecteer vervolgens de naam van die persoon.

    U kunt licentiebeheer voor gebruikers ook bulksgewijs uitvoeren. Als u dit wilt doen, selecteert u meerdere gebruikers en selecteert u **Productlicenties bewerken**.

1. Selecteer op de pagina met gebruikersgegevens **Bewerken** naast **Productlicenties**.

1. Stel **Power BI (gratis)** of **Power BI Pro** in op **Uit**, afhankelijk van welke licentie u op het account hebt toegepast.

1. Selecteer **Opslaan**.

### <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hoe weet ik wanneer nieuwe gebruikers lid zijn geworden van mijn tenants?

Gebruikers die lid van uw tenant zijn geworden door zichzelf te registreren, ontvangen een unieke licentie. U kunt hierop filteren in het beheerdashboard in het deelvenster met actieve gebruikers. Volg deze stappen voor het maken van deze nieuwe weergave.

1. Navigeer naar het [Microsoft 365-beheercentrum](https://admin.microsoft.com/AdminPortal/Home#/homepage).

1. Selecteer in het navigatievenster **Gebruikers** > **Actieve gebruikers**.

1. Selecteer **Aangepaste weergave toevoegen** in het menu **Weergaven**.

1. Geef de nieuwe weergave een naam en selecteer onder **Toegewezen productlicentie** **Power BI (gratis)** of **Power BI Pro**.

    U kunt slechts één licentie per weergave selecteren. Als u licenties voor zowel **Power BI (gratis)** als **Power BI Pro** hebt voor uw organisatie, kunt u twee weergaven maken.

1. Voer desgewenst nog andere voorwaarden in en selecteer vervolgens **Toevoegen**.

1. Zodra u de nieuwe weergave hebt gemaakt, is deze beschikbaar via het menu **Weergaven**.

### <a name="are-there-any-additional-things-i-should-prepare-for"></a>Zijn er nog andere zaken waarop ik me moet voorbereiden?

U kunt een toename in aanvragen voor het opnieuw instellen van wachtwoorden ervaren. Zie [Het wachtwoord van een gebruiker opnieuw instellen](/office365/admin/add-users/reset-passwords) voor meer informatie over dit proces.

U kunt een gebruiker uit uw tenant verwijderen via het standaardproces in het Microsoft 365-beheercentrum. Als de gebruiker echter nog steeds een actief e-mailadres van uw organisatie heeft, kan die persoon opnieuw lid worden, tenzij u dit blokkeert voor alle gebruikers.

### <a name="where-is-my-power-bi-tenant-located"></a>Waar bevindt mijn Power BI-tenant zich?

Zie [Waar bevindt mijn Power BI-tenant zich?](service-admin-where-is-my-tenant-located.md) voor informatie over de gegevensregio waarin uw Power BI-tenant zich bevindt.

### <a name="what-is-the-power-bi-sla"></a>Wat is de SLA voor Power BI?

Raadpleeg het artikel [Licentievoorwaarden en documentatie](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) in het gedeelte **Licentieverlening** van de website Microsoft Licensing voor meer informatie over de Power BI SLA (Service Level Agreement).

### <a name="how-does-power-bi-handle-high-availability-and-failover"></a>Hoe gaat Power BI om met hoge beschikbaarheid en failover?

Zie [Hoge beschikbaarheid en failover in Power BI en Veelgestelde vragen over herstel na noodgeval](service-admin-failover.md) voor meer informatie over de hoge beschikbaarheid en failover.

## <a name="security-in-power-bi"></a>Beveiliging in Power BI

### <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Voldoet Power BI aan nationale, regionale en branchespecifieke nalevingsvereisten?

Lees meer informatie over Power BI-naleving in het [Microsoft Vertrouwenscentrum](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/default.aspx).

### <a name="how-does-security-work-in-power-bi"></a>Hoe werkt beveiliging in Power BI?

Microsoft heeft Power BI gebouwd op basis van Microsoft 365, dat op zijn beurt is gebaseerd op Azure-services zoals Azure Active Directory. Zie [Beveiliging van Power BI](service-admin-power-bi-security.md) voor een overzicht van Power BI-architectuur.

## <a name="next-steps"></a>Volgende stappen

[Power BI-beheerportal](service-admin-portal.md)  
[Understanding the Power BI admin role](service-admin-role.md) (Power BI-beheerdersrol)  
[Registreren voor Power BI via selfservice](service-self-service-signup-for-power-bi.md)  
[Purchasing Power BI Pro](service-admin-purchasing-power-bi-pro.md) (Power BI Pro kopen)  
[Wat is Power BI Premium?](service-premium-what-is.md)  
[Hoe kan ik Power BI Premium kopen?](service-admin-premium-purchase.md)  
[Technisch document over Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Uw groep beheren in Power BI en Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md)  
[Office 365 user account management](/office365/servicedescriptions/office-365-platform-service-description/user-account-management/) (Beheer van Office 365-gebruikersaccounts)  
[Office 365 group management](/office365/admin/email/create-edit-or-delete-a-security-group/) (Beheer van Office 365-groepen)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

[1]: https://docs.microsoft.com/powershell/scripting/overview
