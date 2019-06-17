---
title: Rapporten kopiëren uit andere werkruimten (preview) - Power BI
description: Ontdek hoe u een gegevensset kunt delen met gebruikers in de hele organisatie. Daarna kunnen ze rapporten samenstellen op basis van uw gegevensset in hun eigen werkruimten.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461460"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Rapporten kopiëren uit andere werkruimten (preview)

Ontdek hoe u een rapport kunt kopiëren van een werkruimte en kunt opslaan in een andere werkruimte. Vervolgens kunt u het rapport wijzigen, en visuals en andere elementen toevoegen of verwijderen.

Wanneer u in een werkruimte of een app een rapport hebt gevonden dat u leuk vindt, kunt u er een kopie van maken en deze vervolgens aanpassen aan uw behoeften. U hoeft zich geen zorgen te maken over het maken van het gegevensmodel. Dit is al voor u gemaakt. En het is veel gemakkelijker een bestaand rapport aan te passen dan een compleet nieuw rapport te maken.

## <a name="save-a-copy-of-a-report"></a>Een kopie van een rapport opslaan

1. Ga naar de lijstweergave Rapporten in een app of een werkruimte.

1. Selecteer onder **Acties** **Een kopie opslaan**.

    ![Een kopie van een rapport opslaan](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    U ziet alleen het pictogram **Een kopie opslaan** als het rapport zich in een nieuwe werkruimte-ervaring-werkruimte bevindt en u over [Samenstellingsmachtigingen](service-datasets-build-permissions.md#build-permissions-for-shared-datasets) beschikt. Zelfs als u toegang tot de werkruimte hebt, hebt u samenstellingsmachtigingen nodig voor de gegevensset.

3. Geef in **Een kopie van dit rapport opslaan** een naam op voor het rapport en selecteer de doelwerkruimte.

    ![Het dialoogvenster Een kopie opslaan](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    U kunt het rapport opslaan in de huidige werkruimte of een andere werkruimte in de Power BI-service. U ziet alleen nieuwe werkruimte-ervaring-werkruimten waarin u lid bent.
  
4. Selecteer **Opslaan**.

    Wanneer u een kopie van het rapport opslaat, maakt u een live-verbinding met de gegevensset en kunt u de interface voor het maken van het rapport openen met de volledige, beschikbare gegevensset. U hebt geen kopie van de gegevensset gemaakt. De gegevensset bevindt zich nog steeds op de oorspronkelijke locatie. U kunt alle tabellen en metingen in de gegevensset gebruiken in uw eigen rapporten. Er zijn beperkingen ten aanzien van RLS (Beveiliging op rijniveau) voor de gegevensset van kracht, zodat u alleen gegevens ziet waarvoor u gemachtigd bent om deze te zien op basis van uw RLS-rol.

    Power BI maakt automatisch een vermelding in de lijst met gegevenssets als het rapport is gebaseerd op een gegevensset buiten de werkruimte. Het pictogram voor deze gegevensset wijkt af van het pictogram voor gegevenssets in de werkruimte: ![Pictogram van een gedeelde gegevensset](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    Op die manier kunnen leden van de werkruimte zien welke rapporten en dashboards gebruikmaken van gegevenssets die zich buiten de werkruimte bevinden. De vermelding toont informatie over de gegevensset en een aantal bijzondere acties.

    ![Acties gegevensset](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Verwante gegevenssets weergeven

Wanneer u een rapport in uw werkruimte hebt, moet u wellicht weten op welke gegevensset het is gebaseerd.

1. Selecteer in de lijstweergave Rapporten **Gerelateerde items weergeven**.

    ![pictogram Gerelateerde items weergeven](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. Het dialoogvenster **Gerelateerde inhoud** geeft alle verwante items weer. In deze lijst ziet de gegevensset er net zo uit als de andere. U weet niet of deze zich in een andere werkruimte bevindt. Dit is een bekend probleem.
 
    ![Dialoogvenster voor gerelateerde inhoud](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in meerdere werkruimten gebruiken (preview)](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
