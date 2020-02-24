---
title: Power BI Premium aanschaffen
description: Lees hoe u Power BI Premium koopt en hoe u toegang tot inhoud voor uw hele organisatie inschakelt.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: 1bf7cc85411fef27e626c330cc07207187302bfc
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427732"
---
# <a name="how-to-purchase-power-bi-premium"></a>Power BI Premium aanschaffen

In dit artikel wordt beschreven hoe u Power BI Premium-capaciteit voor uw hele organisatie koopt. In het artikel worden twee scenario's behandeld:

- P SKU's gebruiken voor typische productiescenario's. Voor P SKU's zijn een maandelijks of jaarlijks bedrag vereist. Ze worden maandelijks gefactureerd.

- Met behulp van een A SKU voor het testen van scenario's en voor gevallen waarin u niet over de benodigde machtigingen beschikt om P SKU's te kopen (de rollen globale Microsoft 365-beheerder of factureringsbeheerder). Voor A SKU's zijn geen tijdtoezegging vereist. Ze worden per uur gefactureerd. U koopt A SKU's in [Azure Portal](https://portal.azure.com).

Zie [Wat is Power BI Premium?](service-premium-what-is.md) voor meer informatie over Power BI Premium. Zie de [pagina met Power BI-prijzen](https://powerbi.microsoft.com/pricing/) en de [Power BI Premium-rekenmachine](https://powerbi.microsoft.com/calculator/) voor informatie over de huidige prijzen en de planning. Ook als uw organisatie gebruikmaakt van Power BI Premium hebben makers van inhoud een [Power BI Pro-licentie](service-admin-purchasing-power-bi-pro.md) nodig. Zorg ervoor dat u ten minste één Power BI Pro-licentie voor uw organisatie koopt. Met A SKU's hebben _alle gebruikers_ die inhoud gebruiken ook Pro-licenties nodig.

> [!NOTE]
> Als een Premium-abonnement verloopt, houdt u dertig dagen volledige toegang tot uw capaciteit. Daarna keert uw inhoud terug naar een gedeelde capaciteit. Modellen groter dan 1 GB worden niet ondersteund in gedeelde capaciteit.

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>P SKU's kopen voor typische productiescenario's

U kunt een nieuwe tenant maken met een Power BI Premium P1 SKU die is geconfigureerd, of u kunt een Power BI Premium-capaciteit kopen voor een bestaande organisatie. In beide gevallen kunt u capaciteit toevoegen als u dat nodig hebt.

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Een nieuwe tenant maken met Power BI Premium P1

Als u geen bestaande tenant hebt en een tenant wilt maken, kunt u op hetzelfde moment Power BI Premium aanschaffen. Met de volgende koppeling gaat u stapsgewijs door het proces voor het maken van een nieuwe tenant en kunt u Power BI Premium aanschaffen: [Power BI Premium P1-aanbieding](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). Wanneer u een tenant maakt, wordt aan u automatisch de rol Globale Microsoft 365-beheerder voor die tenant toegewezen.

Nadat u capaciteit hebt aangeschaft, leert u hoe u [capaciteit kunt beheren](service-admin-premium-manage.md#manage-capacity) en [werkruimten kunt toewijzen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) aan een capaciteit.

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Een Power BI Premium-capaciteit voor een bestaande organisatie kopen

Als u over een bestaande organisatie (tenant) beschikt, moet u de rol Globale Microsoft 365-beheerder of Factureringsbeheerder hebben om abonnementen en licenties te kunnen aanschaffen. Zie [Microsoft 365-beheerdersrollen](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) voor meer informatie.

Volg deze stappen om een Premium-capaciteit aan te schaffen.

1. Selecteer in de Power BI-service de optie Kiezer voor Microsoft 365-apps en vervolgens **Beheerder**.

    ![Kiezer voor Microsoft 365-apps](media/service-admin-premium-purchase/o365-app-picker.png)

    U kunt ook naar het Microsoft 365-beheercentrum bladeren.

1. Selecteer **Facturering** > **Services aanschaffen**.

1. Zoek onder **Andere abonnementen** naar Power BI Premium-aanbiedingen. Hiermee worden P1 tot en met P3, EM3 en P1 (maandelijks) weergegeven.

1. Beweeg de muisaanwijzer over het beletselteken **(. . .)** en selecteer vervolgens **Nu kopen**.

    ![Nu kopen](media/service-admin-premium-purchase/premium-purchase.png)

1. Volg de stappen om de aankoop te voltooien.

Nadat u de aankoop hebt voltooid, wordt op de pagina **Services aanschaffen** weergegeven dat het item is gekocht en actief is.

![U hebt Power BI Premium aangeschaft](media/service-admin-premium-purchase/premium-purchased.png)

Nadat u capaciteit hebt aangeschaft, leert u hoe u [capaciteit kunt beheren](service-admin-premium-manage.md#manage-capacity) en [werkruimten kunt toewijzen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) aan een capaciteit.

### <a name="purchase-additional-capacities"></a>Meer capaciteiten kopen

Nu u over een capaciteit beschikt, kunt u er naar behoefte meer aan toevoegen. U kunt elke gewenste combinatie van SKU's voor Premium-capaciteit (P1 tot en met P3) binnen uw organisatie gebruiken. De verschillende SKU’s bieden verschillende resourcemogelijkheden.

1. Selecteer in het Microsoft 365-beheercentrum **Facturering** > **Services aanschaffen**.

1. Zoek het Power BI Premium-item waarvan u meer wilt kopen, onder **Andere abonnementen**.

1. Beweeg de muisaanwijzer over **Meer opties** (...) en selecteer vervolgens **Aantal licenties wijzigen**.

    ![Licentieaantal wijzigen](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Geef op hoeveel exemplaren u voor dit item wilt hebben. Selecteer vervolgens **Verzenden** wanneer u klaar bent.

   > [!IMPORTANT]
   > Bij het selecteren van **Verzenden** worden de kosten in rekening gebracht via de geregistreerde creditcard.

Op de pagina **Services aanschaffen** wordt aangegeven hoeveel exemplaren u hebt. In de Power BI-beheerportal wordt onder **Capaciteitsinstellingen** bij de beschikbare v-cores de nieuw gekochte capaciteit weergegeven.

![Beschikbare v-cores voor Power BI Premium-capaciteit](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>Uw abonnement annuleren

U kunt uw abonnement vanuit het Microsoft 365-beheercentrum annuleren. Als u uw Premium-abonnement wilt annuleren, gaat u als volgt te werk.

1. Blader naar het Microsoft 365-beheercentrum.

1. Selecteer **Facturering** > **Abonnementen**.

1. Selecteer uw Power BI Premium-abonnement in de lijst.

1. Selecteer **Meer acties** > **Abonnement annuleren**.

1. Op de pagina **Abonnement annuleren** wordt aangegeven of u wel of niet verantwoordelijk bent voor [de kosten voor vroegtijdige beëindiging](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3). Op deze pagina kunt u ook lezen wanneer de gegevens voor het abonnement worden verwijderd.

1. Lees de informatie en selecteer **Abonnement annuleren** als u wilt doorgaan.

#### <a name="when-canceling-or-your-license-expires"></a>Wanneer u annuleert of uw licentie verloopt

Wanneer u uw Premium-abonnement annuleert, of als u capaciteitslicentie verloopt, hebt u voor een periode van 30 dagen vanaf de annulering- of verloopdatum toegang tot uw Premium-capaciteiten. Na 30 hebt u geen toegang meer tot uw Premium-capaciteiten of de werkruimten daarin.

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>A SKU's aanschaffen voor testen en andere scenario's

A SKU's worden beschikbaar gesteld via de Azure Power BI Embedded-service. U kunt A SKU's op de volgende manieren gebruiken:

- Het insluiten van Power BI in toepassingen van derden inschakelen. Zie [Power BI Embedded](developer/azure-pbie-what-is-power-bi-embedded.md)voor meer informatie.

- Test de Premium-functionaliteit voordat u een P-SKU koopt.

- Ontwikkel- en testomgevingen maken naast een productieomgeving die P SKU's gebruikt.

- Koop Power BI Premium ook al bent u geen globale Microsoft 365-beheerder of factureringsbeheerder.

> [!NOTE]
> Als u een SKU van A4 of hoger aanschaft, kunt u profiteren van alle Premium-functies, met uitzondering van onbeperkt delen van inhoud. Met A SKU's hebben _alle gebruikers_ die inhoud gebruiken Pro-licenties nodig.

Volg deze stappen om A SKU's aan te schaffen in Azure Portal:

1. Meld u aan bij [Azure Portal](https://portal.azure.com) met een account met ten minste beheerdersmachtigingen in Power BI.

1. Zoek naar _Power BI Embedded_ en selecteer de service in de zoekresultaten.

    ![Zoeken in Azure Portal](media/service-admin-premium-purchase/azure-portal-search.png)

1. Selecteer **Power BI Embedded maken**.

    ![Power BI Embedded maken](media/service-admin-premium-purchase/create-power-bi-embedded.png)

1. Geef in het scherm **Power BI Embedded maken** de volgende gegevens op:

    - Het **Abonnement** waarin de Power BI Embedded-service wordt gemaakt.

    - De fysieke **Locatie** waarin de resourcegroep met de service wordt gemaakt. Voor betere prestaties moet deze locatie dicht bij de locatie zijn van uw Azure Active Directory-tenant voor Power BI.

    - De bestaande **Resourcegroep** om te gebruiken, of maak een nieuwe zoals wordt weergegeven in het voorbeeld.

    - De **Power BI-capaciteitsbeheerder**. De capaciteitsbeheerder moet een lidgebruiker zijn of een service-principal in uw Azure AD-Tenant.

    ![Abonnement en resourcegroep](media/service-admin-premium-purchase/subscription-resource-group.png)

1. Als u alle functies van Power BI Premium wilt gebruiken (met uitzondering van onbeperkt delen), hebt u ten minste een A4 SKU nodig. Selecteer **Formaat wijzigen**.

    ![Capaciteitsgrootte wijzigen](media/service-admin-premium-purchase/change-capacity-size.png)

1. Selecteer een capaciteitsgrootte van A4, A5 of A6, die overeenkomt met P1, P2 en P3.

    ![De capaciteit A3 selecteren](media/service-admin-premium-purchase/select-a3-capacity.png)

1. Selecteer **Beoordelen en maken**, controleer de opties die u hebt gekozen en selecteer vervolgens **Maken**.

    ![Bron maken](media/service-admin-premium-purchase/create-resource.png)

1. Het kan enkele minuten duren voordat de implementatie is voltooid. Als het klaar is, selecteert u **Ga naar resource**.

    ![Implementatie voltooid](media/service-admin-premium-purchase/deployment-complete.png)

1. Bekijk op het beheerscherm de opties die u hebt voor het beheren van de service, inclusief het onderbreken van de service wanneer u deze niet gebruikt.

    ![Capaciteit beheren](media/service-admin-premium-purchase/manage-capacity.png)

Nadat u capaciteit hebt aangeschaft, leert u hoe u [capaciteit kunt beheren](service-admin-premium-manage.md#manage-capacity) en [werkruimten kunt toewijzen](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity) aan een capaciteit.

## <a name="next-steps"></a>Volgende stappen

[Capaciteiten configureren en beheren in Power BI Premium](service-admin-premium-manage.md)\
[Pagina met Power BI-prijzen](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium-rekenmachine](https://powerbi.microsoft.com/calculator/)\
[Veelgestelde vragen over Power BI Premium](service-premium-faq.md)\
[Een technisch document over een Power BI-implementatie voor de onderneming plannen](https://aka.ms/pbienterprisedeploy)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
