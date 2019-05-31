---
title: Power Bi-gebruikers zoeken die zich hebben aangemeld
description: Als u een tenantbeheerder bent en wilt zien wie zich heeft aangemeld bij Power BI, kunt u de Azure Active Directory-toegang en gebruik rapporten inzicht krijgen.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906690"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Power Bi-gebruikers zoeken die zich hebben aangemeld

Als u een tenantbeheerder bent en wilt zien wie zich heeft aangemeld bij Power BI, gebruik de [Azure Active Directory-toegang en gebruik rapporten](/azure/active-directory/reports-monitoring/concept-sign-ins) inzicht krijgen.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> De **aanmeldingen** rapport bevat nuttige informatie, maar deze niet bepalen welk type licentie elke gebruiker heeft. Gebruik het Microsoft 365-beheercentrum om licenties te bekijken.

## <a name="requirements"></a>Vereisten

Alle gebruikers (met inbegrip van niet-beheerders) kunnen een rapport inzien van hun eigen aanmeldingen, maar u moet voldoen aan de volgende vereisten om een rapport voor alle gebruikers te zien.

* Uw tenant moet beschikken over een Azure Active Directory Premium-licentie die ermee verbonden zijn.

* U moet een van de volgende rollen hebben: Globale beheerder, Beveiligingsbeheerder of Beveiligingslezer.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Aanmeldingen bekijken in de Azure-portal

Volg deze stappen om aanmeldingsactiviteiten te bekijken.

1. Selecteer **Azure Active Directory** in de **Azure-portal**.

1. Selecteer **Aanmeldingen** onder **Bewaking**.
   
    ![Schermopname van de gebruikersinterface van Azure met de gemarkeerde opties van Azure Active Directory en -aanmeldingen.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filter de toepassing op **Microsoft Power BI** of **Power BI Gateway** en selecteer **Toepassen**.

    **Microsoft Power BI** filters voor aanmeldingsactiviteiten met betrekking tot de service, terwijl **Power BI Gateway** filters aanmeldingsactiviteiten specifiek zijn voor de on-premises gegevensgateway.
   
    ![Schermopname van het filter-aanmeldingen met het veld toepassingen is gemarkeerd.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>De gegevens exporteren

U kunt [downloaden van een rapport](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) in een van twee verschillende indelingen: een CSV-bestand of een JSON-bestand.

![Schermopname van de downloadknop.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Aan de bovenkant van de **aanmeldingen** rapport, selecteer **downloaden** en selecteer vervolgens een van de volgende opties:

* **CSV** voor het downloaden van een CSV-bestand voor de momenteel gefilterde gegevens.

* **JSON** een JSON-bestand voor de momenteel gefilterde gegevens te downloaden.

## <a name="data-retention"></a>Bewaartijd voor gegevens

Gegevens van aanmeldingen zijn maximaal 30 dagen beschikbaar. Zie voor meer informatie, [bewaarbeleid Azure Active Directory-rapporten](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Volgende stappen

[Auditing gebruiken binnen uw organisatie](service-admin-auditing.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)