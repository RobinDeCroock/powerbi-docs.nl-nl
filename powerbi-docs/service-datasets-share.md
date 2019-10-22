---
title: Een gegevensset delen (preview)
description: U kunt als gegevensseteigenaar zelf gegevenssets maken en delen zodat anderen er ook gebruik van kunnen maken. Meer informatie over hoe u deze kunt delen.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c490228a1dfa1e6c842db3c41ab077a99f35f975
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021109"
---
# <a name="share-a-dataset-preview"></a>Een gegevensset delen (preview)

Als maker van *gegevensmodellen* in Power BI Desktop maakt u *gegevenssets* die u kunt distribueren in de Power BI-service. Vervolgens kunnen andere makers van rapporten uw gegevenssets gebruiken als basis voor hun eigen rapporten. In dit artikel leest u hoe u uw gegevenssets kunt delen. Meer informatie over het verlenen en intrekken van toegang tot uw gedeelde gegevenssets vindt u in het artikel over de [samenstellingsmachtiging](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Stappen voor het delen van uw gegevensset

1. U begint met het maken van een pbix-bestand met een gegevensmodel in Power BI Desktop. Als u van plan bent de gegevensset aan te bieden aan anderen zodat ze rapporten kunnen maken, mag u zelfs geen rapport ontwerpen in het pbix-bestand.

    Een van de best practices is om het pbix-bestand op te slaan in een Office 365-groep.

1. Publiceer het pbix-bestand in een [nieuwe werkruimte-ervaring](service-create-the-new-workspaces.md) in de Power BI-service.
    
    Andere leden van deze werkruimte kunnen op basis van de gegevensset nu rapporten maken in andere werkruimten.

1. U kunt vanuit deze werkruimte ook [een app publiceren](service-create-distribute-apps.md). Als u dit doet, geeft u op de pagina **Machtigingen** aan wie welke machtigingen krijgt.

    > [!NOTE]
    > Als u **Hele organisatie** selecteert, krijgt niemand in de organisatie de samenstellingsmachtiging. Dit probleem is al bekend. Geef in plaats daarvan e-mailadressen op in **Specifieke personen of groepen**.  Als u aan de hele organisatie samenstellingsmachtigingen wilt verlenen, geeft u voor de hele organisatie een e-mailalias op.

    ![App-machtigingen instellen](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. Selecteer **App publiceren** (of **App bijwerken**, als deze al is gepubliceerd).

## <a name="track-your-dataset-usage"></a>Het gebruik van uw gegevensset bijhouden

Als er een gedeelde gegevensset in uw werkruimte staat, wilt u mogelijk weten welke rapporten in andere werkruimten hierop zijn gebaseerd.

1. Selecteer in de lijstweergave Gegevenssets de optie **Gerelateerde items weergeven**.

    ![pictogram Gerelateerde items weergeven](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. In het dialoogvenster **Gerelateerde inhoud** worden alle verwante items weergegeven. In deze lijst ziet u de gerelateerde items in deze werkruimte en in **andere werkruimten**.
 
    ![Dialoogvenster voor gerelateerde inhoud](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in meerdere werkruimten gebruiken (preview)](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)