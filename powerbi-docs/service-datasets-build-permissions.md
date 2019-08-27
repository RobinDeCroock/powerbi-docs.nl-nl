---
title: Een gegevensset delen (preview)
description: U kunt als gegevensseteigenaar zelf gegevenssets maken en delen zodat anderen er ook gebruik van kunnen maken. Ontdek hoe u de controle houdt over wie toegang heeft tot de gegevens met behulp van de samenstellingsmachtiging.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/14/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17c3322ed5f24d106412bafb9c4235ee15a626aa
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530514"
---
# <a name="share-a-dataset-preview"></a>Een gegevensset delen (preview)

Als maker van *gegevensmodellen* in Power BI Desktop kunt u de gegevensmodellen in de Power BI-service ook delen als *gegevenssets*. Makers van rapporten kunnen vervolgens eenvoudig de gegevenssets die u hebt gedeeld ontdekken en hergebruiken. Ontdek hoe u ze kunt delen en hoe u de controle houdt over wie toegang heeft tot de gegevens met behulp van de bouwmachtiging.

## <a name="steps-to-sharing-your-dataset"></a>Stappen voor het delen van uw gegevensset

1. U begint met het maken van een pbix-bestand met een gegevensmodel in Power BI Desktop. Als u van plan bent de gegevensset aan te bieden aan anderen zodat ze rapporten kunnen maken, mag u zelfs geen rapport ontwerpen in het pbix-bestand.

    Een van de best practices is om het pbix-bestand op te slaan in een Office 365-groep.

1. Publiceer het pbix-bestand in een [nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md) in de Power BI-service.
    
    Andere leden van deze werkruimte kunnen op basis van de gegevensset nu rapporten maken in andere werkruimten.

1. U kunt vanuit deze werkruimte ook [een app publiceren](service-create-distribute-apps.md). Als u dit doet, geeft u op de pagina **Machtigingen** aan wie welke machtigingen krijgt.

    > [!NOTE]
    > Als u **Hele organisatie** selecteert, krijgt niemand in de organisatie de build-machtiging. Dit probleem is al bekend. Geef in plaats daarvan e-mailadressen op in **Specifieke personen of groepen**.  Als u de gehele organisatie samenstellingsmachtigingen wilt geven, geeft u voor de gehele organisatie een e-mailalias op.

    ![App-machtigingen instellen](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Selecteer **App publiceren** (of **App bijwerken**, als deze al is gepubliceerd).

## <a name="build-permissions-for-shared-datasets"></a>Samenstellingsmachtigingen voor gedeelde gegevenssets

Het machtigingstype Samenstellen is alleen relevant voor gegevenssets. Hiermee kunnen gebruikers nieuwe inhoud samenstellen op basis van een gegevensset, zoals rapporten, dashboards, tegels die zijn vastgemaakt vanuit Q&A en statistieken. Zij kunnen ook nieuwe inhoud ontwikkelen op basis van de gegevensset buiten Power BI, zoals Excel-bladen via Analyseren in Excel, XMLA en deze exporteren.

Gebruikers kunnen op verschillende manieren samenstellingsmachtigingen verkrijgen:

- Als u lid bent van een werkruimte met minimaal de rol van Inzender, beschikt u automatisch over de samenstellingsmachtiging voor een gegevensset en de machtiging om een rapport te kopiëren.
 
- Een lid van de werkruimte waarin de gegevensset zich bevindt, kan de machtiging in het machtigingencentrum toewijzen aan specifieke gebruikers en beveiligingsgroepen. Selecteer het beletselteken (...) naast de gegevensset > **Machtigingen beheren**.

    ![Selecteer het beletselteken](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Hiermee wordt het machtigingencentrum voor de gegevensset geopend; hier kunt u machtigingen instellen en wijzigen.

    ![Machtigingencentrum](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- Beheerders en leden van de werkruimte waarin de gegevensset zich bevindt, kunnen tijdens het publiceren van apps besluiten dat gebruikers met machtigingen voor de app ook de samenstellingsmachtiging krijgen voor onderliggende gegevenssets. Zie [Stappen voor het delen van uw gegevensset](#steps-to-sharing-your-dataset) in dit artikel voor meer informatie.

- Stel dat er machtigingen voor opnieuw delen en bouwen zijn voor een gegevensset. Wanneer u een rapport of dashboard deelt dat is samengesteld op basis van die gegevensset, kunt u opgeven dat de ontvangers ook samenstellingsmachtigingen krijgen voor de onderliggende gegevensset.

    ![Samenstellingsmachtigingen](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

U kunt de samenstellingsmachtigingen die iemand voor een gegevensset heeft ook verwijderen. Als u dit doet, kunnen ze het rapport dat is samengesteld op basis van de gedeelde gegevensset nog steeds zien, maar ze kunnen de set niet meer bewerken.

## <a name="more-granular-permissions"></a>Meer gedetailleerde machtigingen

De machtiging Samenstellen is in juni 2019 geïntroduceerd in Power BI als aanvulling op de bestaande machtigingen voor lezen en opnieuw delen. Alle gebruikers die via app-machtigingen, delen of toegang tot werkruimten al leesmachtiging hadden voor gegevenssets, hebben op dat moment ook samenstellingsmachtiging gekregen voor die gegevenssets. Ze hebben de samenstellingsmachtiging automatisch gekregen omdat ze met de leesmachtiging sowieso al het recht hadden om nieuwe inhoud samen te stellen op basis van de gegevensset (bijvoorbeeld via In Excel analyseren of Exporteren).

Met deze meer gedetailleerde samenstellingsmachtiging kunt u selecteren wie alleen de inhoud van de rapporten en dashboards mag bekijken en wie ook inhoud mag samenstellen op basis van de onderliggende gegevenssets.

Als uw gegevensset voor een rapport buiten de werkruimte van de gegevensset wordt gebruikt, kunt u die gegevensset niet verwijderen. In plaats daarvan krijgt u een foutmelding te zien.

U kunt samenstellingsmachtigingen verwijderen. Als u dit doet, kunnen de mensen van wie u de machtigingen hebt ingetrokken het rapport wel nog bekijken, maar het kan niet meer bewerken.

## <a name="track-your-dataset-usage"></a>Het gebruik van uw gegevensset bijhouden

Als er een gedeelde gegevensset in uw werkruimte staat, wilt u mogelijk weten welke rapporten in andere werkruimten hierop zijn gebaseerd.

1. Selecteer in de lijstweergave Gegevenssets de optie **Gerelateerde items weergeven**.

    ![pictogram Gerelateerde items weergeven](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. In het dialoogvenster **Gerelateerde inhoud** worden alle verwante items weergegeven. In deze lijst ziet u de gerelateerde items in deze werkruimte en in **andere werkruimten**.
 
    ![Dialoogvenster voor gerelateerde inhoud](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in meerdere werkruimten gebruiken (preview)](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
