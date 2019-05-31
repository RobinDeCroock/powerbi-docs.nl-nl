---
title: Power BI Pro-licenties kopen en toewijzen
description: Leer hoe u Power BI Pro-licenties koopt en toewijst, zodat uw gebruikers toegang hebben tot alle inhoud en mogelijkheden van de Power BI-service.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/21/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 15cd5e021969a050937b9d67eb7695f4fcde07c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61188430"
---
# <a name="purchase-and-assign-power-bi-pro-licenses"></a>Power BI Pro-licenties kopen en toewijzen

Power BI Pro is een afzonderlijke licentie waarmee toegang kan worden verkregen tot alle inhoud en mogelijkheden in de Power BI-service, inclusief de mogelijkheid voor het delen van inhoud en samenwerken met andere Pro-gebruikers. Alleen Pro-gebruikers kunnen inhoud naar app-werkruimten publiceren en deze inhoud gebruiken, dashboards delen en zich abonneren op dashboards en rapporten. Zie [Power BI Free vs Pro](service-features-license-type.md) voor meer informatie.

In dit artikel wordt eerst uitgelegd hoe u Power BI Pro-licenties kunt kopen in Office 365. Vervolgens worden de twee opties besproken die u hebt om deze licenties toe te wijzen aan afzonderlijke gebruikers: Office 365 en Azure (u moet een van deze opties kiezen).

## <a name="prerequisites"></a>Vereisten

U moet lid zijn van de rol [**Globale beheerder** of **Factureringsbeheerder**](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) in Office 365.

Als u licenties wilt toewijzen in Azure, moet u eigenaar zijn van het Azure-abonnement dat Power BI gebruikt voor zoekacties in Active Directory.

## <a name="purchase-licenses-in-office-365"></a>Licenties kopen in Office 365

Voer de volgende stappen uit om Power BI Pro-licenties te kopen:

1. Open het [Microsoft 365-beheercentrum](https://portal.office.com/adminportal/home#/homepage).

2. Selecteer in het linkernavigatievenster **Facturering** > **Abonnementen**.

    ![Navigatiedeelvenster](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

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

## <a name="assign-licenses-in-office-365"></a>Licenties toewijzen in Office 365

Voer de volgende stappen uit om Power BI Pro-licenties toe te wijzen aan afzonderlijke gebruikersaccounts:

1. Open het [Microsoft 365-beheercentrum](https://portal.office.com/adminportal/home#/homepage).

2. Vouw **Gebruikers** uit in het linkernavigatiedeelvenster en selecteer **Actieve gebruikers**.

    ![Actieve gebruikers](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Selecteer een gebruiker en selecteer vervolgens **Bewerken** onder **Productlicenties**.

    ![Productlicenties bewerken](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Zet de instelling onder **Power BI Pro** op **Aan** en selecteer vervolgens **Opslaan**.

    ![Productlicenties op Aan](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Controleer onder **Status** voor het geselecteerde account of de Power BI Pro-licentie is toegewezen.

    ![Licentiestatus controleren](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

## <a name="assign-licenses-in-azure"></a>Licenties toewijzen in Azure

Voer de volgende stappen uit om Power BI Pro-licenties toe te wijzen aan afzonderlijke gebruikersaccounts:

1. Open [Azure Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Selecteer in de linkernavigatiebalk **Azure Active Directory**.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Selecteer onder **Azure Active Directory** de optie **Licenties**.

    ![Licenties](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Selecteer onder **Licenties** de optie **Alle producten**. Selecteer vervolgens **Power BI Pro** om de lijst met gebruikers weer te geven die beschikken over een licentie.

    ![Licenties - alle producten](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Selecteer **Toewijzen** om een Power BI Pro-licentie toe te voegen aan een extra gebruikersaccount.

    ![Licentie toewijzen](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Volgende stappen

Nu u licenties hebt toegewezen, kunt u meer te weten komen over Power BI Pro.

[Power BI-licenties in uw organisatie](service-admin-licensing-organization.md)

[Power BI-gebruikers vinden die zijn aangemeld](service-admin-access-usage.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
