---
title: Build-machtiging voor gedeelde gegevenssets
description: Ontdek hoe u toegang tot de gegevens beheert met behulp van de samenstellingsmachtiging.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d602c97384f42bdd35f12052f67b15a0ca7bae38
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236901"
---
# <a name="build-permission-for-shared-datasets"></a>Build-machtiging voor gedeelde gegevenssets

Wanneer u een rapport in Power BI Desktop maakt, worden de gegevens in dat rapport opgeslagen in een *gegevensmodel*. Wanneer u uw rapporten publiceert in de Power BI-service, publiceert u de gegevens ook als een *gegevensset*. U kunt anderen de *samenstellingsmachtiging* voor dat rapport geven zodat zij de gegevensset die u hebt gedeeld kunnen detecteren en hergebruiken. In dit artikel wordt uitgelegd hoe u toegang tot de gegevens beheert met behulp van de samenstellingsmachtiging.

De samenstellingsmachtiging is van toepassing op gegevenssets. Met de samenstellingsmachtiging kunnen gebruikers nieuwe inhoud samenstellen op basis van uw gegevensset, zoals rapporten, dashboards, tegels die zijn vastgemaakt vanuit Q&A, en Inzichtdetectie. 

Gebruikers moeten ook beschikken over samenstellingsmachtigingen om *buiten* Power BI met de gegevens te kunnen werken:

- Om de onderliggende gegevens te exporteren.
- Om nieuwe inhoud in de gegevensset te maken, zoals bij [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md).
- Om toegang tot de gegevens te krijgen via het XMLA-eindpunt.

## <a name="ways-to-give-build-permission"></a>Manieren om een samenstellingsmachtiging te geven

U kunt een samenstellingsmachtiging voor een gegevensset op een aantal verschillende manieren opgeven:

- Leden van een werkruimte met minimaal de rol van Inzender beschikken automatisch over de samenstellingsmachtiging voor gegevenssets in die werkruimte en de machtiging om een rapport te kopiëren.
 
- Leden van de werkruimte waarin de gegevensset zich bevindt, kunnen de machtiging in het machtigingencentrum toewijzen aan specifieke gebruikers en beveiligingsgroepen. Selecteer als u een lid van de werkruimte bent **Meer opties** (...) naast de gegevensset > **Machtigingen beheren**.

    ![Selecteer het beletselteken](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

    Hiermee wordt het machtigingencentrum voor de gegevensset geopend; hier kunt u machtigingen instellen en wijzigen.

    ![Machtigingencentrum](media/service-datasets-build-permissions/power-bi-dataset-remove-permissions-no-callouts.png)

- Beheerders en leden van de werkruimte waarin de gegevensset zich bevindt, kunnen tijdens het publiceren van apps besluiten dat gebruikers met machtigingen voor de app ook de samenstellingsmachtiging krijgen voor onderliggende gegevenssets. Zie [Een gegevensset delen](service-datasets-share.md) voor meer informatie.

- Stel dat u een machtiging voor opnieuw delen en een samenstellingsmachtiging hebt voor een gegevensset. Wanneer u een rapport of dashboard deelt dat is samengesteld op basis van die gegevensset, kunt u opgeven dat de ontvangers ook een samenstellingsmachtiging krijgen voor de onderliggende gegevensset.

    ![Samenstellingsmachtiging](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

U kunt de samenstellingsmachtiging die iemand voor een gegevensset heeft ook verwijderen. Als u dit doet, kunnen ze het rapport dat is samengesteld op basis van de gedeelde gegevensset nog steeds zien, maar ze kunnen de set niet meer bewerken. Zie de volgende sectie voor details.

## <a name="remove-build-permission-for-a-dataset"></a>Samenstellingsmachtiging voor een gegevensset verwijderen

Op een bepaald punt moet u mogelijk de samenstellingsmachtiging verwijderen voor sommige gebruikers van een gedeelde gegevensset. 

1. Ga in een werkruimte naar de lijstpagina **Gegevenssets**. 
1. Selecteer **Meer opties** (...) naast de gegevensset > **Machtigingen beheren**.

    ![Machtigingen beheren](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Selecteer **Meer opties** (...) naast een naam > **Build verwijderen**.

    ![Samenstellingsmachtiging verwijderen](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    Gebruikers kunnen het rapport dat is samengesteld op basis van de gedeelde gegevensset nog steeds zien, maar ze kunnen de set niet meer bewerken.

### <a name="remove-build-permission-for-a-dataset-in-an-app"></a>Samenstellingsmachtiging voor een gegevensset in een app verwijderen

Stel dat u een app vanuit een werkruimte naar een groep personen hebt gedistribueerd. Later besluit u om toegang tot de app voor sommige personen te verwijderen. Wanneer toegang tot de app wordt verwijderd, worden de samenstellingsmachtiging en machtiging voor opnieuw delen niet automatisch ook verwijderd. Dat is een extra stap. 

1. Selecteer **App bijwerken** op een werkruimtepagina. 

    ![App bijwerken](media/service-datasets-build-permissions/power-bi-app-update.png)

1. Selecteer op het tabblad **Machtigingen** de **X** om de persoon of groep te verwijderen. 

    ![Selecteer de X](media/service-datasets-build-permissions/power-bi-app-delete-user.png)
1. Selecteer **App bijwerken**.

    Er wordt een bericht weergegeven met de melding dat u naar **Machtigingen beheren** moet gaan om de samenstellingsmachtiging te verwijderen voor gebruikers die toegang hebben. 

    ![Bericht over het beheren van machtigingen](media/service-datasets-build-permissions/power-bi-dataset-app-remove-message.png)

1. Selecteer **Bijwerken**.

1. Ga in de werkruimte naar de lijstpagina **Gegevenssets**. 
1. Selecteer **Meer opties** (...) naast de gegevensset > **Machtigingen beheren**.

    ![Machtigingen beheren](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. Selecteer **Meer opties** (...) naast de naam > **Build verwijderen**.

    ![Samenstellingsmachtiging verwijderen](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    Gebruikers kunnen het rapport dat is samengesteld op basis van de gedeelde gegevensset nog steeds zien, maar ze kunnen de set niet meer bewerken.

## <a name="more-granular-permissions"></a>Meer gedetailleerde machtigingen

De samenstellingsmachtiging is in juni 2019 geïntroduceerd in Power BI als aanvulling op de bestaande machtigingen voor lezen en opnieuw delen. Alle gebruikers die via app-machtigingen, delen of toegang tot werkruimten al leesmachtiging hadden voor gegevenssets, hebben op dat moment ook de samenstellingsmachtiging gekregen voor die gegevenssets. Ze hebben de samenstellingsmachtiging automatisch gekregen omdat ze met de leesmachtiging sowieso al het recht hadden om nieuwe inhoud samen te stellen op basis van de gegevensset (bijvoorbeeld via In Excel analyseren of Exporteren).

Met deze meer gedetailleerde samenstellingsmachtiging kunt u selecteren wie alleen de inhoud van de rapporten en dashboards mag bekijken en wie ook inhoud mag samenstellen op basis van de onderliggende gegevenssets.

Als uw gegevensset voor een rapport buiten de werkruimte van de gegevensset wordt gebruikt, kunt u die gegevensset niet verwijderen. In plaats daarvan krijgt u een foutmelding te zien.

U kunt samenstellingsmachtigingen verwijderen. Als u dit doet, kunnen de mensen van wie u de machtigingen hebt ingetrokken het rapport wel nog bekijken, maar ze kunnen het rapport niet langer bewerken of onderliggende gegevens exporteren. Gebruikers met alleen een leesmachtiging kunnen nog wel samengevatte gegevens exporteren. 

## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in werkruimten gebruiken](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
