---
title: Power BI Pro-licenties kopen en toewijzen
description: Leer hoe u Power BI Pro-gebruikerslicenties koopt en toewijst, zodat uw gebruikers toegang hebben tot inhoud en kunnen samenwerken met collega's in de Power BI-service.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 72a158e2dca32d2199fcd48e2cc37bf4c90778ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873545"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro-gebruikerslicenties kopen en toewijzen

Power BI Pro is een afzonderlijke gebruikerslicentie die gebruikers in staat stelt om rapporten en dashboards, die andere gebruikers hebben gepubliceerd in de Power BI-service, te lezen en te gebruiken, en om inhoud te delen en met andere Power BI Pro-gebruikers samen te werken. Alleen gebruikers met een Power BI Pro-gebruikerslicentie kunnen inhoud publiceren of delen met andere gebruikers of inhoud gebruiken die door andere gebruikers is gemaakt, tenzij de inhoud wordt gehost in een Power BI Premium-capaciteit. Zie [Power BI Free vs Pro](service-features-license-type.md) voor meer informatie.

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro-gebruikerslicenties kopen en toewijzen

In dit artikel wordt uitgelegd hoe u Power BI Pro-gebruikerslicenties koopt in het Microsoft 365-beheercentrum en worden vervolgens twee manieren beschreven waarop beheerders deze licenties kunnen toewijzen aan afzonderlijke gebruikers: in het Microsoft 365-beheercentrum en Azure Portal (kies één optie).

### <a name="prerequisites"></a>Vereisten

Als u licenties wilt kopen en toewijzen in het Microsoft 365-beheercentrum, moet u lid zijn van de rol **Globale beheerder[ of ](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)Factureringsbeheerder** in Microsoft 365.

Als u licenties wilt toewijzen in Azure Portal, moet u eigenaar zijn van het Azure-abonnement dat Power BI gebruikt voor zoekacties in Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Licenties kopen in Microsoft 365

Voer de volgende stappen uit om Power BI Pro-licenties te kopen in het Microsoft 365-beheercentrum:

1. Open het [Microsoft 365-beheercentrum](https://portal.office.com/adminportal/home#/homepage).

2. Selecteer in het navigatievenster **Facturering** > **Abonnementen**.

    ![Navigatievenster](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Klik op **Abonnementen toevoegen** in de rechterbovenhoek van de pagina **Abonnementen**.

    ![Abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Zoek de gewenste aanbieding voor een abonnement:

    Selecteer onder **Enterprise Suite** de optie **Office 365 Enterprise E5**.

    ![Office E5-abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Selecteer onder **Overige abonnementen** de optie **Power BI Pro**.

    ![Power BI-abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. Wijs de weglatingstekens ( **. . .** ) aan voor het gewenste abonnement en selecteer **Nu kopen**.

    ![Nu kopen](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Kies desgewenst voor **Maandelijks betalen** of **Voor een volledig jaar betalen**.

7. Onder **Voor hoeveel gebruikers?** voert u het gewenste aantal licenties in. Vervolgens selecteert u **Nu uitchecken** om de transactie te voltooien.

8. Controleer of het gekochte abonnement nu op de pagina **Abonnementen** wordt vermeld.

   ![Aangeschaft abonnement](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Als u na de initiële aankoop meer licenties wilt toevoegen, selecteert u **Power BI Pro** op de pagina **Abonnementen** en selecteert u vervolgens **Licenties toevoegen/verwijderen**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Licenties toewijzen in het Microsoft 365-beheercentrum

Voer de volgende stappen uit om Power BI Pro-licenties toe te wijzen aan afzonderlijke gebruikersaccounts:

1. Open het [Microsoft 365-beheercentrum](https://portal.office.com/adminportal/home#/homepage).

2. Vouw **Gebruikers** uit in het navigatievenster en selecteer **Actieve gebruikers**.

    ![Actieve gebruikers](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selecteer een gebruiker en selecteer vervolgens **Bewerken** onder **Productlicenties**.

    ![Productlicenties bewerken](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Zet de instelling onder **Power BI Pro** op **Aan** en selecteer vervolgens **Opslaan**.

    ![Productlicenties op Aan](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Controleer onder **Status** voor het geselecteerde account of de Power BI Pro-licentie is toegewezen.

    ![Licentiestatus controleren](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Licenties toewijzen in Azure Portal

Voer de volgende stappen uit om Power BI Pro-licenties toe te wijzen aan afzonderlijke gebruikersaccounts:

1. Open [Azure Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Selecteer in het navigatievenster **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Selecteer onder **Azure Active Directory** de optie **Licenties**.

    ![Licenties](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Selecteer onder **Licenties** de optie **Alle producten**. Selecteer vervolgens **Power BI Pro** om de lijst met gebruikers weer te geven die beschikken over een licentie.

    ![Licenties - alle producten](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selecteer **Toewijzen** om een Power BI Pro-licentie toe te voegen aan een gebruikersaccount.

    ![Licentie toewijzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Volgende stappen

Nu u licenties hebt toegewezen, kunt u meer te weten komen over Power BI Pro.

[Power BI-licenties in uw organisatie](service-admin-licensing-organization.md)

[Power BI-gebruikers vinden die zijn aangemeld](service-admin-access-usage.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
