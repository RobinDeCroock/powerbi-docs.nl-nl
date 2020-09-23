---
title: Registratie en kopen via self-service in- of uitschakelen
description: Informatie voor beheerders over het uitschakelen van de mogelijkheid voor gebruikers om zich te registreren voor Power BI en een licentie te kopen of bij te werken.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 966699f20e83a7ea34140486f97f4491c4ba35e2
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857445"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Registratie en kopen via self-service in- of uitschakelen

In de meeste organisaties is registratie via self-service standaard ingeschakeld. Individuele gebruikers in uw organisatie kunnen zich registreren voor Power BI met hun werk- of schoolaccount. Gebruikers kunnen ook de mogelijkheid krijgen om direct een Power BI Pro-licentie te kopen als ze een functie proberen te gebruiken waarvoor Pro nodig is. Als beheerder kunt u bepalen of u registratie via self-service wilt in- of uitschakelen. Ook kunt u opgeven of gebruikers in uw organisatie een eigen licentie via self-service kunnen kopen.

> [!NOTE]
>Als u Power BI hebt verkregen via een Microsoft Cloud Solution Provider (CSP), is de instelling mogelijk uitgeschakeld om te voorkomen dat gebruikers zich individueel registreren. Uw CSP kan ook optreden als de globale beheerder voor uw organisatie. U moet dan contact opnemen met uw CSP om deze instelling te wijzigen.
>
>

U kunt PowerShell-opdrachten gebruiken om de instellingen te wijzigen waarmee de registratie en aanschaf via self-service worden beheerd. Er zijn twee instellingen waarmee wordt bepaald of het registreren of aanschaffen via self-service mogelijk is voor gebruikers in uw organisatie.

- Als u alle registraties via self-service wilt uitschakelen, wijzigt u een instelling in Azure Active Directory met de naam **AllowAdHocSubscriptions** met behulp van Azure AD PowerShell-opdrachten. Volg de stappen in dit artikel om [registratie via self-service in of uit te schakelen](#enable-or-disable-self-service-signup). Met deze optie wordt de registratie via self-service voor *alle* cloud-apps en -services van Microsoft uitgeschakeld.

- Als u wilt voorkomen dat gebruikers hun eigen Pro-licentie kopen, wijzigt u de instelling **AllowSelfServicePurchase** met behulp van MSCommerce PowerShell-opdrachten. Met deze instelling kunt u aankopen via self-service uitschakelen voor specifieke producten. Volg de stappen in dit artikel om [het aanschaffen van Power BI Pro-licenties via self-service in of uit te schakelen](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Registratie via self-service in -of uitschakelen

Als registratie via self-service is ingeschakeld, is **AllowAdHocSubscriptions** ingesteld op *true*. Laten we eens kijken wat er gebeurt wanneer u deze instelling wijzigt in *false*:

- Als u de instelling wijzigt van true in false, kunnen nieuwe gebruikers in uw organisatie zich niet individueel registreren. Gebruikers die zich hebben geregistreerd voor Power BI voordat u de instelling wijzigt, behouden hun licentie.

- Als u de instelling wijzigt in false, kunnen gebruikers die al een (gratis) Power BI-licentie hebben zich nog steeds registreren voor een individuele Power BI Pro-proefversie.

- Een beheerder moet alle Power BI-licenties toewijzen aan nieuwe gebruikers die er een nodig hebben.

### <a name="before-you-begin"></a>Voordat u begint

Bij deze stappen worden Azure Active Directory PowerShell-opdrachten gebruikt om de waarde van de instelling **AllowAdHocSubscriptions** te wijzigen. Deze opdrachten zijn alleen beschikbaar als de Azure AD PowerShell-module is geïnstalleerd. Zie [Aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7) voor meer informatie over het gebruik van PowerShell.

Als u de Azure AD-module wilt installeren, start u Windows PowerShell als beheerder. Zorg ervoor dat u met het lokale uitvoeringsbeleid scripts kunt uitvoeren. Als u problemen ondervindt, raadpleegt u [PowerShell-uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) voor meer informatie over het wijzigen van uw lokale beleid.

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

## <a name="enable-or-disable-self-service-purchase"></a>Aankopen via self-service in- of uitschakelen

Als aanschaffen via self-service is ingeschakeld, is **AllowSelfServicePurchase** ingesteld op *true*. Laten we eens kijken wat er gebeurt wanneer u deze instelling wijzigt in *false*:

- Als u de instelling wijzigt van true in false, kunnen gebruikers in uw organisatie geen eigen Power BI Pro-licentie aanschaffen. Gebruikers die een licentie hebben aangeschaft voordat u de instelling wijzigt, behouden hun licentie.

- Als u de instelling wijzigt in false, kunnen gebruikers die een (gratis) Power BI-licentie hebben geen individuele Power BI Pro-licentie aanschaffen. 

- Een beheerder moet een Pro-licentie toewijzen aan alle gebruikers die er één nodig hebben.

### <a name="before-you-begin"></a>Voordat u begint

Bij deze stappen worden MSCommerce PowerShell-opdrachten gebruikt om de waarde van de **AllowSelfServicePurchase**-instelling te wijzigen. Deze opdrachten zijn alleen beschikbaar als de MSCommerce PowerShell-module is geïnstalleerd. Zie [Aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7) voor meer informatie over het gebruik van PowerShell.

Als u de MSCommerce-module wilt installeren, start u Windows PowerShell als beheerder. Zorg ervoor dat u met het lokale uitvoeringsbeleid scripts kunt uitvoeren. Als u problemen ondervindt, raadpleegt u [PowerShell-uitvoeringsbeleid](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) voor meer informatie over het wijzigen van uw lokale beleid.

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

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende artikelen voor meer informatie over aankopen via self-service in Power BI en de rest van Power Platform:

- [Veelgestelde vragen over aankopen via self-service](/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [AllowSelfServicePurchase gebruiken voor de MSCommerce PowerShell-module](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)