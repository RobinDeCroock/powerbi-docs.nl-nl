---
title: Power BI Pro-licenties kopen en toewijzen
description: Leer hoe u Power BI Pro-gebruikerslicenties koopt en toewijst aan gebruikers, zodat ze toegang hebben tot inhoud en kunnen samenwerken met collega's in de Power BI-service.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 899055ea26d1f36592c426ba402aa363b65bfa15
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878360"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro-gebruikerslicenties kopen en toewijzen

>[!IMPORTANT]
>Dit artikel is bestemd voor beheerders. Bent u als gebruiker klaar om een upgrade naar een Power BI Pro-licentie uit te voeren? Ga rechtstreeks naar [Aan de slag met Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) om uw account in te stellen.

Power BI Pro is een afzonderlijke gebruikerslicentie waarmee gebruikers rapporten en dashboards kunnen lezen en gebruiken die anderen hebben gepubliceerd in de Power BI-service. Gebruikers met dit licentietype kunnen inhoud delen en samenwerken met andere Power BI Pro-gebruikers. Alleen Power BI Pro-gebruikers kunnen inhoud publiceren of delen met andere gebruikers, of inhoud gebruiken die is gemaakt door anderen, tenzij deze inhoud wordt gehost via een Power BI Premium-capaciteit. Zie [Power BI-licenties in uw organisatie](service-admin-licensing-organization.md) voor meer informatie over de beschikbare typen licenties en abonnementen.

## <a name="purchase-power-bi-pro-user-licenses"></a>Power BI Pro-gebruikerslicenties kopen

In dit artikel wordt uitgelegd hoe u Power BI Pro-gebruikerslicenties kunt kopen in het Microsoft 365-beheercentrum. Nadat u licenties hebt gekocht, kunt u deze toewijzen aan gebruikers in het Microsoft 365-beheercentrum of in de Azure-portal.

> [!NOTE]
> Vanaf 14 januari 2020 zijn mogelijkheden voor selfserviceaankopen, abonnementen en licentiebeheer voor Power Platform-producten (Power BI, Power Apps en Power Automate) beschikbaar voor klanten van de commerciële cloud. Zie [Veelgestelde vragen over aankopen via self-service](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq) voor meer informatie. Zie [Mogelijkheden voor aanmelden en aankopen via een self-service in- of uitschakelen](/power-bi/admin/service-admin-disable-self-service) voor het in- of uitschakelen van mogelijkheden voor aankopen via self-service.

### <a name="prerequisites"></a>Vereisten

Als u licenties wilt kopen en toewijzen in het Microsoft 365-beheercentrum, moet u lid zijn van de rol [Globale beheerder of Factureringsbeheerder](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) in Microsoft 365.

Als u licenties wilt toewijzen in Azure Portal, moet u eigenaar zijn van het Azure-abonnement dat Power BI gebruikt voor zoekacties in Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Licenties kopen in Microsoft 365

> [!NOTE]
> Als u meestal licenties koopt via een volumelicentieovereenkomst, zoals een Enterprise Agreement en een factuur wilt ontvangen in plaats van te kopen met een creditcard of bankrekening, moet u de order anders indienen. Werk samen met uw Microsoft Reseller of ga door het Volume Licensing Service Center om licenties toe te voegen of te verwijderen. Zie [Abonnementslicenties](https://docs.microsoft.com/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide) voor meer informatie.

Voer de volgende stappen uit om Power BI Pro-licenties te kopen in het Microsoft 365-beheercentrum:

1. Meld u aan bij het [Microsoft 365-beheercentrum](https://admin.microsoft.com).

2. Selecteer in het navigatiemenu **Facturering** > **Aankoopservices**.

3. Zoek of blader om het abonnement te vinden dat u wilt kopen. U vindt **Power BI** onder aan **Andere categorieën die u mogelijk interesseren** aan de onderkant aan de pagina. Selecteer de koppeling om de Power BI-abonnementen weer te geven die beschikbaar zijn voor uw organisatie.

4. Selecteer **Power BI Pro**.

5. Selecteer op de pagina **Services aanschaffen** de optie **Kopen**.

6. Kies **Maandelijks betalen** of **Voor een volledig jaar betalen**, afhankelijk van hoe u wilt betalen.

7. Voer onder **Voor hoeveel gebruikers?** het aantal licenties in dat u wilt kopen. Selecteer vervolgens **Nu uitchecken** om de transactie te voltooien.

8. Ga naar **Facturering** > **Producten en services** en zoek **Power BI Pro** om uw aankoop te verifiëren.

9. Als u later meer licenties wilt toevoegen, gaat u naar **Power BI Pro** op de pagina **Producten en services** en selecteert u vervolgens **Licenties toevoegen/verwijderen**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Licenties toewijzen in het Microsoft 365-beheercentrum

Zie [Licenties toewijzen aan gebruikers](/office365/admin/manage/assign-licenses-to-users) voor meer informatie over het toewijzen van licenties in het Microsoft 365-beheercentrum.

Zie voor gastgebruikers [Licenties toewijzen aan gebruikers op de pagina Licenties](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Voordat u Pro-licenties toewijst aan gastgebruikers, neemt u contact op met de Microsoft-accountvertegenwoordiger om te controleren of u voldoet aan de voorwaarden van uw overeenkomst met Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Licenties toewijzen in Azure Portal

Voer de volgende stappen uit om Power BI Pro-licenties toe te wijzen aan afzonderlijke gebruikersaccounts:

1. Meld u aan bij [Azure Portal](https://portal.azure.com/).

2. Zoek naar **Azure Active Directory** en selecteer deze optie.

3. Selecteer onder **Beheren** in het resourcemenu **Azure Active Directory** de optie **Licenties**.

4. Selecteer in het resourcemenu **Licenties - Overzicht** de optie **Alle producten**. Selecteer vervolgens **Power BI Pro** om de lijst met gelicentieerde gebruikers weer te geven.

5. Selecteer **+ Toewijzen** op de opdrachtbalk. Kies op de pagina **Licentie toewijzen** eerst een gebruiker. Selecteer vervolgens **Opties voor toewijzingen** om een Power BI Pro-licentie in te schakelen voor het geselecteerde gebruikersaccount.

## <a name="next-steps"></a>Volgende stappen

- [Power BI-licenties in uw organisatie](service-admin-licensing-organization.md)

 - [Power BI-gebruikers vinden die zijn aangemeld](service-admin-access-usage.md)

 - [Aanmelden voor Power BI (gratis) als individu](../fundamentals/service-self-service-signup-for-power-bi.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
