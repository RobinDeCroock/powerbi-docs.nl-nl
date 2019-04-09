---
title: Power Bi-gebruikers zoeken die zich hebben aangemeld
description: Als u tenantbeheerder bent en u wilt zien wie zich heeft aangemeld bij Power BI, kunt u met behulp van de toegangs- en gebruiksrapporten van Azure Active Directory meer zichtbaarheid krijgen.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 12a15360efbff62c40f5bd1098886ee046661e4f
ms.sourcegitcommit: 5222bc6a8336acc77c8e22db57ea6a7bf7daea57
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59290737"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Power Bi-gebruikers zoeken die zich hebben aangemeld

Als u tenantbeheerder bent en u wilt zien wie zich heeft aangemeld bij Power BI, kunt u met behulp van de [toegangs- en gebruiksrapporten van Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) meer zichtbaarheid krijgen.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Het activiteitenrapport biedt nuttige informatie, maar vermeldt niet het type licentie van de afzonderlijke gebruikers. Gebruik het Microsoft 365-beheercentrum om licenties te bekijken.

## <a name="requirements"></a>Vereisten

Alle gebruikers (met inbegrip van niet-beheerders) kunnen een rapport inzien van hun eigen aanmeldingen, maar u moet voldoen aan de volgende vereisten om een rapport voor alle gebruikers te zien.

* Er moet een Azure AD Premium-licentie zijn gekoppeld aan uw tenant.

* U moet een van de volgende rollen hebben: Globale beheerder, Beveiligingsbeheerder of Beveiligingslezer.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Aanmeldingen bekijken in de Azure-portal

Volg deze stappen om aanmeldingsactiviteiten te bekijken.

1. Selecteer **Azure Active Directory** in de **Azure-portal**.

1. Selecteer **Aanmeldingen** onder **Bewaking**.
   
    ![Azure AD-aanmeldingen](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filter de toepassing op **Microsoft Power BI** of **Power BI Gateway** en selecteer **Toepassen**.

    Kies **Microsoft Power BI** om te filteren op aanmeldingsactiviteit met betrekking tot de service. Kies **Power BI Gateway** om te filteren op specifieke aanmeldingsactiviteit voor de on-premises gegevensgateway.
   
    ![Aanmeldingen filteren](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>De gegevens exporteren

U hebt twee opties om de aanmeldingsgegevens te exporteren: een CSV-bestand downloaden of PowerShell gebruiken. Selecteer een van de volgende opties boven aan het rapport:

* **Downloaden**: hiermee downloadt u een CSV-bestand voor de uitgefilterde gegevens.

* **Script**: hiermee downloadt u een PowerShell-script voor de uitgefilterde gegevens. U kunt het filter in het script desgewenst bijwerken.

![CSV-bestand of script downloaden](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Bewaartijd voor gegevens

Gegevens van aanmeldingen zijn maximaal 30 dagen beschikbaar. Zie [Bewaarbeleid Azure Active Directory-rapporten](/azure/active-directory/reports-monitoring/reference-reports-data-retention) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Auditing gebruiken binnen uw organisatie](service-admin-auditing.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

