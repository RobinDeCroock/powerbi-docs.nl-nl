---
title: Rapporten kopiëren uit andere werkruimten (preview) - Power BI
description: Ontdek hoe u een gegevensset kunt delen met gebruikers in de hele organisatie. Daarna kunnen ze rapporten samenstellen op basis van uw gegevensset in hun eigen werkruimten.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 2fc33c8adcaed35dab8fc9d81ab28fa314f42e3b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881929"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Rapporten kopiëren uit andere werkruimten (preview)

Wanneer u in een werkruimte of app een rapport hebt gevonden dat u interessant vindt, kunt u er een kopie van maken en deze opslaan in een andere werkruimte. Vervolgens kunt u uw kopie van het rapport wijzigen en visuals en andere elementen toevoegen of verwijderen. U hoeft zich geen zorgen te maken over het maken van het gegevensmodel. Dit is al voor u gemaakt. En het is veel gemakkelijker een bestaand rapport aan te passen dan een compleet nieuw rapport te maken. Wanneer u echter een app vanuit de nieuwe werkruimte maakt, is het soms niet mogelijk om uw kopie van het rapport in de app te publiceren. Zie [Overwegingen en beperkingen in het artikel Gegevenssets in werkruimten gebruiken](service-datasets-across-workspaces.md#considerations-and-limitations) voor meer informatie.

> [!NOTE]
> Als u een kopie maakt, hebt u een Pro-licentie nodig, zelfs als het oorspronkelijke rapport zich in een werkruimte in een Premium-capaciteit bevindt.

## <a name="save-a-copy-of-a-report"></a>Een kopie van een rapport opslaan

1. Ga naar de lijstweergave Rapporten in een app of een werkruimte.

1. Selecteer onder **Acties** **Een kopie opslaan**.

    ![Een kopie van een rapport opslaan](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    U ziet alleen het pictogram **Een kopie opslaan** als het rapport zich in een nieuwe werkruimte-ervaring bevindt en u over [samenstellingsmachtigingen](service-datasets-build-permissions.md) beschikt. Zelfs als u toegang tot de werkruimte hebt, hebt u samenstellingsmachtigingen nodig voor de gegevensset.

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

## <a name="delete-a-report-and-its-shared-dataset"></a>Een rapport en de bijbehorende gedeelde gegevensset verwijderen

Het kan gebeuren dat u een rapport en de bijbehorende gedeelde gegevensset niet meer nodig hebt in de werkruimte.

1. U kunt het rapport dan verwijderen. Selecteer in de lijst met rapporten in de werkruimte het pictogram **Verwijderen**.

    ![Het pictogram voor het verwijderen van een rapport](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. In de lijst met gegevenssets ziet u dat er bij de gedeelde gegevenssets geen pictogram **Verwijderen** staat. Vernieuw de pagina of ga naar een andere pagina en keer hier weer terug. De gegevensset is nu verdwenen. Als dat niet zo is, selecteert u **Gerelateerde items weergeven**. Het is mogelijk dat de gegevensset is gerelateerd aan een andere tabel in uw werkruimte.

    ![pictogram Gerelateerde items weergeven](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > Het verwijderen van de gedeelde gegevensset in deze werkruimte, betekent niet dat de gegevensset wordt verwijderd. Alleen de verwijzing naar de gegevensset wordt verwijderd.


## <a name="next-steps"></a>Volgende stappen

- [Gegevenssets in meerdere werkruimten gebruiken (preview)](service-datasets-across-workspaces.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
