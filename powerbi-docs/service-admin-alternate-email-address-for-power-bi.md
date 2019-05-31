---
title: Alternatief e-mailadres gebruiken
description: Alternatief e-mailadres gebruiken
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906654"
---
# <a name="use-an-alternate-email-address"></a>Alternatief e-mailadres gebruiken

Wanneer u zich registreert voor Power BI, geeft u een e-mailadres op. Power BI gebruikt dit adres standaard voor het verzenden van updates over de activiteit in de service. Wanneer iemand u bijvoorbeeld een uitnodiging stuurt om iets te delen, wordt deze naar dit adres verzonden.

In sommige gevallen hebt u liever dat deze e-mailberichten naar een ander e-mailadres worden gestuurd dan het adres waarmee u zich hebt geregistreerd. In dit artikel wordt uitgelegd hoe u in Office 365 en PowerShell een ander adres opgeeft. Het artikel wordt ook uitgelegd hoe een e-mailadres wordt omgezet in Azure Active Directory (Azure AD).

> [!NOTE]
> Het opgeven van een ander adres heeft geen invloed op het e-mailadres dat door Power BI wordt gebruikt voor service-updates, nieuwsbrieven en andere commerciële berichten. Deze berichten worden altijd verzonden naar het e-mailadres dat u hebt gebruikt toen u zich hebt geregistreerd voor Power BI.

## <a name="use-office-365"></a>Office 365 gebruiken

Volg deze stappen als u een ander adres wilt opgeven in Office 365.

1. Open de [pagina Persoonlijke gegevens in Office 365](https://portal.office.com/account/#personalinfo). Als u wordt gevraagd door de app, meld u aan met de e-mailadres en wachtwoord dat u voor Power BI gebruikt.

1. Selecteer in het menu links de optie **Persoonlijke gegevens**.

1. Selecteer in de sectie **Contactgegevens** de optie **Bewerken**.

    Als u uw gegevens niet bewerken, betekent dit dat uw Office 365-beheerder beheert uw e-mailadres. Neem contact op met uw beheerder voor het bijwerken van uw e-mailadres.

    ![Contactgegevens](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. In de **alternatief e-mailadres** en voer het e-mailadres dat u wilt dat Office 365 voor Power BI-updates te gebruiken.

## <a name="use-powershell"></a>PowerShell gebruiken

Als u een ander adres in PowerShell wilt opgeven, gebruikt u de opdracht [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>E-adresomzetting in Azure AD

Om vast te leggen van een Azure AD-token insluiten voor Power BI, kunt u een van drie verschillende typen e-mailadressen gebruiken:

* Het belangrijkste e-mailadres dat is gekoppeld aan een gebruikersaccount met Azure AD

* Het e-mailadres UserPrincipalName (UPN);

* Het matrixkenmerk *ander e-mailadres*.

Power BI selecteert welk e-mailadres moet worden gebruikt op basis van deze volgorde:

1. Als het e-mailkenmerk in het Azure AD-gebruikersobject aanwezig is, gebruikt Power BI dat e-mailkenmerk als e-mailadres.

1. Als het UPN-e-mailadres *niet* behoort tot het domein **\*.onmicrosoft.com** (de gegevens na het symbool \@), gebruikt Power BI dat e-mailkenmerk als e-mailadres.

1. Als de *andere e-mailadres* matrixkenmerk in de Azure AD-gebruikersobject aanwezig is, en vervolgens Power BI maakt gebruik van het eerste e-mailbericht in de lijst (omdat er een lijst van e-mailberichten in dit kenmerk zijn kan).

1. Als geen van de bovenstaande voorwaarden aanwezig zijn, gebruikt Power BI het UPN-adres.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)