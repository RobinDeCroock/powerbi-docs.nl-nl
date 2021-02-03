---
title: Registratie en kopen via self-service in- of uitschakelen
description: Informatie voor beheerders over het uitschakelen van de mogelijkheid voor gebruikers om zich te registreren voor Power BI en een licentie te kopen of bij te werken.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/31/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 80e263cc6e67c28b7593fcf10aea4c81c9f4af86
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494300"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Registratie en kopen via self-service in- of uitschakelen

## <a name="what-is-self-service"></a>Wat is self-service?

Self-service verwijst naar de mogelijkheid van personen in een organisatie (werk of school) om zich aan te melden voor het gebruik van services die zijn betaald door het abonnement van de organisatie, of om gratis services te gebruiken zonder dat hun organisatie actie namens u hoeft te ondernemen. De persoon gaat naar een micro soft-website, zoekt een Cloud service die de organisatie levert en maakt gebruik van het e-mail adres van hun organisatie om zich aan te melden voor die service. 

In veel gevallen heeft de organisatie een vergoeding betaald voor een abonnement op die service. In andere gevallen is de persoon de eerste gebruiker en wordt de beheerder voor de service. Voor een proef-of gratis licentie is geen aankoop vereist. Voor Power BI Pro is de organisatie echter verantwoordelijk voor het betalen van de maandelijkse kosten. 

Als Microsoft 365 beheerder kunt u zien wie zich aanmeldt voor experimenten, licenties en abonnementen.

> [!NOTE]
> Aanmelding via selfservice is alleen van toepassing op commerciële Cloud klanten en niet op nationale Clouds of overheids klanten.

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>Wanneer moet u aanmelden en kopen via self-service?

### <a name="self-service-is-a-good-idea"></a>Self-service is een goed idee: 

- In grotere en gedecentraliseerde organisaties (werk of school), waarbij individuen vaak de flexibiliteit krijgen om SaaS-licenties (software als een service) aan te schaffen voor eigen gebruik. 
- Voor een of meer organisaties die slechts één Power BI Pro licentie of slechts een paar licenties moeten aanschaffen.
- Voor personen die geïnteresseerd zijn in het Power BI, het verkrijgen van een beslag voordat ze een abonnement voor de hele organisatie aanschaffen.
- Voor huidige gebruikers met een Power BI gratis licentie, die nu inhoud wil maken en delen en zelf kunt upgraden naar een Power BI Pro proef versie. 

### <a name="you-may-want-to-disable-self-service-when"></a>Mogelijk wilt u self-service uitschakelen wanneer:

- Uw organisatie heeft aanbestedings processen om te voldoen aan de vereisten voor naleving, regelgeving, beveiliging en governance. U moet ervoor zorgen dat alle Power BI Pro-licenties worden goedgekeurd en beheerd volgens gedefinieerde processen. 
- Uw organisatie heeft vereisten voor nieuwe Power BI Pro gebruikers, zoals verplichte training of gebruikers bevestiging van beleids regels voor gegevens bescherming.
- Uw organisatie verbiedt het gebruik van de Power BI-service vanwege gegevens privacy of andere problemen en moet de toewijzing van Power BI gratis licenties zeer nauw keurig beheren.
- om ervoor te zorgen dat alle Power BI Pro licenties onder de Enter prise Agreement vallen om te profiteren van de tarieven voor onderhandelen/korting.
- Voor huidige gebruikers met een Power BI gratis licentie, die wordt gevraagd om een Power BI Pro licentie rechtstreeks te kopen. Uw organisatie wil mogelijk niet dat deze gebruikers bijwerken vanwege beveiliging, privacy of onkosten.


## <a name="enable-and-disable-self-service"></a>Self-service in-en uitschakelen

Als beheerder kunt u bepalen of u registratie via self-service wilt in- of uitschakelen. U kunt ook bepalen of gebruikers in uw organisatie self-service aankopen kunnen maken om hun eigen licentie te verkrijgen. 

Als u de aanmelding via self-service uitschakelt, voorkomt u dat gebruikers Power BI voor gegevensvisualisatie en -analyse verkennen. Als u afzonderlijke aanmelding blokkeert, wilt u mogelijk Power BI (gratis)-licenties voor uw organisatie ontvangen en aan alle gebruikers toewijzen. 

> [!NOTE]
>Als u Power BI hebt verkregen via een Microsoft Cloud Solution Provider (CSP), is de instelling mogelijk uitgeschakeld om te voor komen dat gebruikers afzonderlijk worden aangemeld. Uw CSP kan ook optreden als de globale beheerder voor uw organisatie. U moet dan contact opnemen met uw CSP om deze instelling te wijzigen.
>


 U kunt Power shell-opdrachten gebruiken om de instellingen te wijzigen waarmee de registratie en aankoop van selfservice worden beheerd. 

- Als u alle registraties via self-service wilt uitschakelen, wijzigt u een instelling in Azure Active Directory met de naam **AllowAdHocSubscriptions** met behulp van Azure AD PowerShell-opdrachten. Volg de stappen in dit artikel om [registratie via self-service in of uit te schakelen](#enable-or-disable-self-service-sign-up-for-your-organization). Met deze optie wordt de registratie via self-service voor *alle* cloud-apps en -services van Microsoft uitgeschakeld.

- Als u wilt voorkomen dat gebruikers hun eigen Pro-licentie kopen, wijzigt u de instelling **AllowSelfServicePurchase** met behulp van MSCommerce PowerShell-opdrachten. Met deze instelling kunt u aankopen via self-service uitschakelen voor specifieke producten. Volg de stappen in dit artikel om [het aanschaffen van Power BI Pro-licenties via self-service in of uit te schakelen](#enable-or-disable-self-service-purchase-in-your-organization).

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>Registratie van self-service voor uw organisatie in-of uitschakelen

Als registratie via self-service is ingeschakeld, is **AllowAdHocSubscriptions** ingesteld op *true*. Laten we eens kijken wat er gebeurt wanneer u deze instelling wijzigt in *false*:

- Nieuwe gebruikers in uw organisatie zijn geblokkeerd om zich afzonderlijk aan te melden. Gebruikers die zich hebben aangemeld voor Power BI voordat u de instelling hebt gewijzigd, blijven hun licenties.

- Gebruikers die al een Power BI (gratis) licentie hebben, kunnen zich nog steeds registreren voor een individuele Power BI Pro proef versie.

- Een beheerder moet alle Power BI-licenties toewijzen aan nieuwe gebruikers die er één nodig hebben.

### <a name="before-you-begin"></a>Voordat u begint

Bij deze stappen worden Azure Active Directory PowerShell-opdrachten gebruikt om de waarde van de instelling **AllowAdHocSubscriptions** te wijzigen. Deze opdrachten zijn alleen beschikbaar als de Azure AD PowerShell-module is geïnstalleerd. Zie [Aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) voor meer informatie over het gebruik van PowerShell.

Als u de Azure AD-module wilt installeren, start u Windows PowerShell als beheerder. Zorg ervoor dat u met het lokale uitvoeringsbeleid scripts kunt uitvoeren. Als u problemen ondervindt, raadpleegt u [PowerShell-uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) voor meer informatie over het wijzigen van uw lokale beleid.

Voer de volgende opdracht uit om de Azure AD-module te installeren:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Het beleid voor registratie via self-service wijzigen

Voer in PowerShell de volgende opdracht uit om verbinding te maken met Azure AD:

```powershell
Connect-MsolService
```

Voer uw beheerdersreferenties in het aanmelddialoogvenster in, waarbij u zo nodig de tweeledige verificatie voltooit. Na de verificatie keert u terug naar het PowerShell-venster.

Als u de huidige instelling wilt weergeven, voert u de volgende opdracht uit. De uitvoer wordt naar een opgemaakte lijst geleid met behulp van de fl-switch.

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Als u de huidige instelling wilt wijzigen, voert u deze opdracht uit:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Nadat deze opdracht is uitgevoerd, is registratie via self-service uitgeschakeld voor alle gebruikers. Als u dit weer wilt inschakelen, voert u deze opdracht opnieuw uit en stelt u de waarde in op $true.

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>Self-service aankopen in uw organisatie in-of uitschakelen

Als aanschaffen via self-service is ingeschakeld, is **AllowSelfServicePurchase** ingesteld op *true*. Laten we eens kijken wat er gebeurt wanneer u deze instelling wijzigt in *false*:

- Gebruikers in uw organisatie zijn geblokkeerd om hun eigen Power BI Pro licentie te kopen. Alle gebruikers die een licentie hebben gekocht voordat u de instelling hebt gewijzigd, blijven hun licenties.

- Gebruikers met een Power BI (gratis) licentie kunnen geen individuele Power BI Pro licentie ophalen. 

- Een beheerder moet een Pro-licentie toewijzen aan alle gebruikers die er één nodig hebben.

### <a name="before-you-begin"></a>Voordat u begint

Bij deze stappen worden MSCommerce PowerShell-opdrachten gebruikt om de waarde van de **AllowSelfServicePurchase**-instelling te wijzigen. Deze opdrachten zijn alleen beschikbaar als de MSCommerce PowerShell-module is geïnstalleerd. Zie [Aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) voor meer informatie over het gebruik van PowerShell.

Als u de MSCommerce-module wilt installeren, start u Windows PowerShell als beheerder. Zorg ervoor dat u met het lokale uitvoeringsbeleid scripts kunt uitvoeren. Als u problemen ondervindt, raadpleegt u [PowerShell-uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) voor meer informatie over het wijzigen van uw lokale beleid.

Voer de volgende opdracht uit om de MSCommerce-module te installeren:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Het beleid voor registratie via self-service wijzigen

Voer in PowerShell de volgende opdracht uit om verbinding te maken:

```powershell
Connect-MSCommerce
```

Voer uw beheerdersreferenties in het aanmelddialoogvenster in, waarbij u zo nodig de tweeledige verificatie voltooit. Na de verificatie wordt in het PowerShell-venster een geslaagde verbinding weergegeven.

Als u de huidige instelling wilt weergeven, voert u de volgende opdracht uit. Om te voorkomen dat tekst wordt afgekapt, wordt de uitvoer naar een opgemaakte lijst geleid met behulp van de fl-switch.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

U kunt de instelling voor het toestaan van aankopen via self-service voor een afzonderlijk product uitschakelen door de bijbehorende **ProductId** op te geven. Als u de huidige instelling voor de Power BI-service wilt wijzigen, voert u de volgende opdracht uit:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Nadat deze opdracht is uitgevoerd, zijn aankopen via self-service voor Power BI uitgeschakeld voor alle gebruikers. Als u dit weer wilt inschakelen, voert u deze opdracht opnieuw uit en stelt u de waarde in op $true.

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>Wat te doen als personen al zelf service hebben gebruikt

Aanmelden en kopen voor selfservice Services zijn standaard ingeschakeld. Dit maakt het mogelijk dat personen in uw organisatie al Power BI licenties en abonnementen hebben. Of u wel of geen actie onderneemt, u hebt een duidelijke afbeelding nodig van wat er al bestaat.

Gebruikers die lid van uw tenant zijn geworden door zichzelf te registreren, ontvangen een unieke licentie. U kunt hierop filteren in het beheerdashboard in het deelvenster met actieve gebruikers. Volg deze stappen voor het maken van deze nieuwe weergave.

1. Navigeer naar het Microsoft 365-beheercentrum.

1. Selecteer in het navigatievenster **Gebruikers** > **Actieve gebruikers**.

1. Selecteer Aangepaste weergave toevoegen in het menu **Weergaven**.

1. Geef de nieuwe weergave een naam en selecteer onder Toegewezen productlicentiePower BI (gratis) of Power BI Pro.

    U kunt slechts één licentie per weergave selecteren. Als u licenties voor zowel Power BI (gratis) als Power BI Pro hebt voor uw organisatie, kunt u twee weergaven maken.

1. Voer desgewenst nog andere voorwaarden in en selecteer vervolgens **Toevoegen**.

    Zodra u de nieuwe weergave hebt gemaakt, is deze beschikbaar via het menu Weergaven.


    > [!NOTE]
    > Als uw organisatie geen Microsoft 365 omgeving heeft die is verbonden met uw e-mail domein, zijn selfservice gebruikers toegevoegd aan een nieuwe gebruikers lijst in de Cloud. Mogelijk moet u [de tenants die al zijn gemaakt](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover), zoeken, claimen en overnemen. 

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende artikelen voor meer informatie over aankopen via self-service in Power BI en de rest van Power Platform:

- [Veelgestelde vragen over aankopen via self-service](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities)
- [AllowSelfServicePurchase gebruiken voor de MSCommerce PowerShell-module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell)