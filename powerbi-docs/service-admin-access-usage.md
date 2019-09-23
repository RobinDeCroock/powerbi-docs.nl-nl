---
title: Power Bi-gebruikers zoeken die zich hebben aangemeld
description: Als u een tenantbeheerder bent en u wilt zien wie zich heeft aangemeld bij Power BI, kunt u met behulp van de toegangs- en gebruiksrapporten van Azure Active Directory meer zichtbaarheid krijgen.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8b1ebbfc323698ed8ab092b8396ef22e4199720e
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71075864"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Power Bi-gebruikers zoeken die zich hebben aangemeld

Als u een tenantbeheerder bent en u wilt zien wie zich heeft aangemeld bij Power BI, kunt u met behulp van de [toegangs- en gebruiksrapporten van Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) meer zichtbaarheid krijgen.

> [!NOTE]
> Het rapport **Aanmeldingen** bevat nuttige informatie, maar vermeldt niet het type licentie van de afzonderlijke gebruikers. Gebruik het Microsoft 365-beheercentrum om licenties te bekijken.

## <a name="requirements"></a>Vereisten

Alle gebruikers (met inbegrip van niet-beheerders) kunnen een rapport inzien van hun eigen aanmeldingen, maar u moet voldoen aan de volgende vereisten om een rapport voor alle gebruikers te zien.

* Er moet een Azure Active Directory Premium-licentie zijn gekoppeld aan uw tenant.

* U moet een van de volgende rollen hebben: Globale beheerder, Beveiligingsbeheerder of Beveiligingslezer.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Aanmeldingen bekijken in de Azure-portal

Volg deze stappen om aanmeldingsactiviteiten te bekijken.

1. Selecteer **Azure Active Directory** in de **Azure-portal**.

1. Selecteer **Aanmeldingen** onder **Bewaking**.
   
    ![Schermopname van de gebruikersinterface van Azure met de opties van Azure Active Directory en Aanmeldingen gemarkeerd.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filter de toepassing op **Microsoft Power BI** of **Power BI Gateway** en selecteer **Toepassen**.

    Kies **Microsoft Power BI** om te filteren op aanmeldingsactiviteit met betrekking tot de service. Kies **Power BI Gateway** om te filteren op specifieke aanmeldingsactiviteit voor de on-premises gegevensgateway.
   
    ![Schermopname van het filter Aanmeldingen met het veld Toepassingen gemarkeerd.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>De gegevens exporteren

U kunt [een aanmeldingsrapport downloaden](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) als een CSV-bestand of als een JSON-bestand.

![Schermopname van de downloadknop.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Selecteer bovenaan het rapport **Aanmeldingen** de optie **Downloaden** en selecteer vervolgens een van de volgende opties:

* **CSV** om een CSV-bestand voor de uitgefilterde gegevens te downloaden.

* **JSON** om een JSON-bestand voor de uitgefilterde gegevens te downloaden.

## <a name="data-retention"></a>Bewaartijd voor gegevens

Gegevens van aanmeldingen zijn maximaal 30 dagen beschikbaar. Zie [Azure Active Directory report retention policies](/azure/active-directory/reports-monitoring/reference-reports-data-retention) (Bewaarbeleid voor Azure Active Directory-rapporten) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Auditing gebruiken binnen uw organisatie](service-admin-auditing.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)