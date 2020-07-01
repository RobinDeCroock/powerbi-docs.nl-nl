---
title: Capaciteiten configureren en beheren in Power BI Premium
description: Lees hoe u Power BI Premium beheert en hoe u toegang tot inhoud voor uw hele organisatie inschakelt.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 05/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: a5dba001247518c0d2c0329fcb0e90573934d30d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228243"
---
# <a name="configure-and-manage-capacities-in-power-bi-premium"></a>Capaciteiten configureren en beheren in Power BI Premium

Het beheer van Power BI Premium omvat het maken, beheren en bewaken van Premium-capaciteiten. In dit artikel krijgt u stapsgewijze instructies. Zie [Premium-capaciteiten beheren](service-premium-capacity-manage.md) voor algemene informatie over capaciteiten.

Meer informatie over het beheren van Power BI Premium- en Power BI Embedded-capaciteiten, die toegewezen resources voor uw inhoud bieden.

![Instellingenscherm voor Power BI-capaciteiten](media/service-admin-premium-manage/premium-capacity-management.png)

*Capaciteit* vormt het hart van de Power BI Premium- en Power BI Embedded-aanbiedingen. Het is een set resources die is gereserveerd voor exclusief gebruik door uw organisatie. Wanneer u over toegewezen capaciteit beschikt, kunt u dashboards, rapporten en gegevenssets publiceren voor gebruikers binnen uw organisatie zonder dat u een licentie per gebruiker voor hen hoeft aan te schaffen. Daarnaast krijgt u betrouwbare en consistente prestaties voor de inhoud die in capaciteit wordt gehost. Zie [Wat is Power BI Premium?](service-premium-what-is.md) voor meer informatie.

## <a name="manage-capacity"></a>Capaciteit beheren

Nadat u capaciteitsknooppunten in Microsoft 365 hebt aangeschaft, stelt u de capaciteit in de Power BI-beheerportal in. U beheert Power BI Premium-capaciteiten in de sectie **Capaciteitsinstellingen** van de portal.

![Capaciteitsinstellingen in de beheerportal](media/service-admin-premium-manage/admin-portal-premium.png)

U beheert een capaciteit door de naam van de capaciteit te selecteren. Vervolgens wordt het scherm voor capaciteitsbeheer weergegeven.

![Selecteer de naam van de capaciteit om het scherm voor capaciteitstoewijzing weer te geven](media/service-admin-premium-manage/capacity-assignment.png)

Als er geen werkruimten zijn toegewezen aan de capaciteit, wordt een bericht weergegeven over [het toewijzen van een werkruimte aan de capaciteit](#assign-a-workspace-to-a-capacity).

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>Een nieuwe capaciteit instellen (Power BI Premium)

In de beheerportal wordt het aantal *virtuele kernen* (v-cores) weergegeven dat u hebt gebruikt en dat nog beschikbaar is. Het totale aantal v-cores is gebaseerd op de Premium-SKU's die u hebt aangeschaft. Als u bijvoorbeeld een P3 en P2 aanschaft, resulteert dit in 48 beschikbare kernen: 32 voor de P3 en 16 voor de P2.

![Gebruikte en beschikbare v-cores voor Power BI Premium](media/service-admin-premium-manage/admin-portal-v-cores.png)

Als u beschikbare v-cores hebt, stelt u met de volgende stappen de nieuwe capaciteit in.

1. Selecteer **Nieuwe capaciteit instellen**.

1. Geef een naam op voor de capaciteit.

1. Definieer wie de beheerder voor deze capaciteit is.

1. Selecteer de grootte van uw capaciteit. Welke opties beschikbaar zijn, is afhankelijk van het aantal beschikbare v-cores. U kunt geen een optie selecteren die groter is dan het aantal beschikbare v-cores.

    ![Beschikbare Premium-capaciteitsgrootten](media/service-admin-premium-manage/premium-capacity-size.png)

1. Selecteer **Instellen**.

    ![Een nieuwe capaciteit instellen](media/service-admin-premium-manage/set-up-capacity.png)

Capaciteitsbeheerders, evenals Power BI-beheerders en globale beheerders, kunnen de capaciteit vervolgens bekijken in de beheerportal.

### <a name="capacity-settings"></a>Capaciteitsinstellingen

1. In het scherm voor het beheren van de Premium-capaciteit kunt u onder **Acties** het **tandwielpictogram** selecteren om instellingen te bekijken en bij te werken. 

    ![Capaciteitsacties in het gebied voor capaciteitsbeheer](media/service-admin-premium-manage/capacity-actions.png)

1. U kunt zien wie de servicebeheerders zijn, wat de SKU of de grootte van de capaciteit is en in welke regio de capaciteit zich bevindt.

    ![Capaciteitsinstellingen](media/service-admin-premium-manage/capacity-settings.png)

1. U kunt ook de naam van een capaciteit wijzigen of een capaciteit verwijderen.

    ![Knoppen verwijderen en toepassen voor capaciteitsinstellingen in Power BI Premium](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> De capaciteitsinstellingen voor Power BI Embedded worden beheerd in Microsoft Azure Portal.

### <a name="change-capacity-size"></a>Capaciteitsgrootte wijzigen

Power BI-beheerders en globale beheerders kunnen Power BI Premium-capaciteit wijzigen. Capaciteitsbeheerders die geen Power BI-beheerder of globale beheerder zijn, beschikken niet over deze optie.

1. Selecteer **Capaciteitsgrootte wijzigen**.

    ![De Power BI Premium-capaciteitsgrootte wijzigen](media/service-admin-premium-manage/change-capacity-size.png)

1. Op het scherm **Capaciteitsgrootte wijzigen** upgradet of downgradet u de capaciteit.

    ![Vervolgkeuzelijst het wijzigen van de Power BI Premium-capaciteitsgrootte](media/service-admin-premium-manage/change-capacity-size2.png)

    Beheerders kunnen naar wens knooppunten maken en verwijderen en de grootte van de knooppunten wijzigen, zolang ze maar over het vereiste aantal v-cores beschikken.

    U kunt P SKU's niet downgraden naar EM SKU's. U kunt de muisaanwijzer over uitgeschakelde opties bewegen voor een uitleg.



> [!IMPORTANT]
> Als er een hoog resourcegebruik is in uw Power BI Premium-capaciteit, wat leidt tot problemen met prestaties of betrouwbaarheid, kunt u e-mailmeldingen ontvangen om het probleem te identificeren en op te lossen. Zie [Meldingen over capaciteit en betrouwbaarheid](service-interruption-notifications.md#capacity-and-reliability-notifications) voor meer informatie.


### <a name="manage-user-permissions"></a>Gebruikersrechten beheren

U kunt extra capaciteitsbeheerders toewijzen en gebruikers toewijzen die beschikken over machtigingen voor *capaciteitstoewijzing*. Gebruikers die over toewijzingsmachtigingen beschikken, kunnen een werkruimte aan een capaciteit toewijzen als ze een beheerder van die werkruimte zijn. Ze kunnen ook hun persoonlijke *Mijn werkruimte* toewijzen aan de capaciteit. Gebruikers met toewijzingsmachtigingen hebben geen toegang tot de beheerportal.

> [!NOTE]
> Capaciteitsbeheerders voor Power BI Embedded worden gedefinieerd in Microsoft Azure Portal.

Vouw onder **Gebruikersmachtigingen** de optie **Gebruikers met toewijzingsmachtigingen** uit en voeg vervolgens naar behoefte gebruikers of groepen toe.

![Gebruikersmachtigingen beheren](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>Werkruimte toewijzen aan een capaciteit

Er zijn twee manieren om een werkruimte toe te wijzen aan een capaciteit: vanuit de beheerportal en vanuit een werkruimte.

### <a name="assign-from-the-admin-portal"></a>Toewijzen vanuit de beheerportal

Capaciteitsbeheerders, maar ook Power BI-beheerders en globale beheerders, kunnen bulksgewijs werkruimten toewijzen in de sectie voor het beheren van Premium-capaciteit in de beheerportal. Wanneer u een capaciteit beheert, kunt u in de sectie **Werkruimten** werkruimten toewijzen.

![Gedeelte van de capaciteitsbeheer voor het toewijzen van werkruimte](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. Selecteer **Werkruimten toewijzen**. Deze optie is op meerdere plekken beschikbaar.

1. Selecteer een optie voor **Toepassen op**.

    ![Werkruimten toewijzen](media/service-admin-premium-manage/assign-workspaces.png)

   | Selectie | Beschrijving |
   | --- | --- |
   | **Werkruimten per gebruiker** | Wanneer u werkruimten toewijst per gebruiker of groep, worden alle werkruimten die eigendom zijn van deze gebruikers, toegewezen aan Premium-capaciteit, met inbegrip van de persoonlijke werkruimte van de gebruiker. Deze gebruikers krijgen automatisch machtigingen om werkruimten toe te wijzen.<br>Dit geldt ook voor werkruimten die al zijn toegewezen aan een andere capaciteit. |
   | **Specifieke werkruimten** | Voer de naam in van een specifieke werkruimte die u wilt toewijzen aan de geselecteerde capaciteit. |
   | **Alle werkruimten van de organisatie** | Als u alle werkruimten van de organisatie toewijst aan Premium-capaciteit, worden alle werkruimten en Mijn werkruimten in uw organisatie toegewezen aan deze Premium-capaciteit. Daarnaast beschikken alle huidige en toekomstige gebruikers over de machtiging om afzonderlijke werkruimten aan deze capaciteit toe te wijzen. |
   | | |

1. Selecteer **Toepassen**.

### <a name="assign-from-workspace-settings"></a>Toewijzen vanuit de instellingen voor een werkruimte

U kunt ook een werkruimte aan een Premium-capaciteit toewijzen via de instellingen voor de desbetreffende werkruimte. Als u een werkruimte wilt overzetten naar een capaciteit, moet u over beheerdersmachtigingen voor die werkruimte en ook over machtigingen voor capaciteitstoewijzing voor die capaciteit beschikken. Houd er rekening mee dat werkruimtebeheerders altijd een werkruimte uit Premium-capaciteit kunnen verwijderen.

1. Bewerk een werkruimte door achtereenvolgens het beletselteken **(. . .)** en **Werkruimte bewerken** te selecteren.

    ![Een werkruimte bewerken via het contextmenu met het beletselteken](media/service-admin-premium-manage/edit-app-workspace.png)

1. Vouw onder **Werkruimte bewerken** de optie **Geavanceerd** uit.

1. Selecteer de capaciteit waaraan u deze werkruimte wilt toewijzen.

    ![Vervolgkeuzelijst voor het selecteren van de capaciteit](media/service-admin-premium-manage/app-workspace-advanced.png)

1. Selecteer **Opslaan**.

Na het opslaan wordt de werkruimte met alle bijbehorende inhoud overgezet naar Premium capaciteit, zonder dat de eindgebruikers hier iets van merken.

## <a name="power-bi-report-server-product-key"></a>Productcode van Power BI Report Server

U vindt de productcode van Power BI Report Server op het tabblad **Capaciteitsinstellingen** in de Power BI-beheerportal. Deze is alleen beschikbaar voor algemene beheerders of gebruikers die de rol Power BI-servicebeheerder toegewezen hebben gekregen en als u een Power BI Premium-SKU hebt gekocht.

![Power BI Report Server-sleutel in Capaciteitsinstellingen](media/service-admin-premium-manage/pbirs-product-key.png)

Als u **Power BI Report Server-sleutel** selecteert, wordt een dialoogvenster weergeven met uw productcode. U kunt deze kopiëren en gebruiken bij de installatie.

![Productcode van Power BI Report Server](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

Zie [Power BI Report Server installeren](../report-server/install-report-server.md) voor meer informatie.

## <a name="next-steps"></a>Volgende stappen

[Premium-capaciteiten beheren](service-premium-capacity-manage.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
