---
title: 'Zelfstudie: Een Azure Machine Learning-modellen gebruiken in Power BI'
titleSuffix: Azure Machine Learning
description: Meer informatie over hoe u Azure Machine Learning-modellen gebruikt in Power BI.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 02/17/2021
ms.openlocfilehash: 91ba29a09cfdd434c52794e83651736c2b796b1e
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/18/2021
ms.locfileid: "100655627"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>Zelfstudie: Azure Machine Learning-modellen gebruiken in Power BI

In deze zelfstudie wordt u begeleid bij het maken van een Power BI-rapport op basis van een Machine Learning-model. Aan het einde van deze zelfstudie kunt u:

> [!div class="checklist"]
> * Machine Learning-modellen (geïmplementeerd beoordelen met Azure Machine Learning) in Power BI.
> * Maak verbinding met een Azure Machine Learning-model in de Power Query-editor.
> * Een rapport met een visualisatie maken gebaseerd op het model.
> * Dat rapport publiceren in de Power BI-service.
> * Geplande vernieuwing instellen voor het rapport.

## <a name="prerequisites"></a>Vereisten

Voordat u aan deze zelfstudie begint, moet u het volgende doen:

- Een Machine Learning-model in Azure Machine Learning trainen en implementeren. Een van deze drie Azure Machine Learning-zelfstudies gebruiken: 

    - [Optie A: Code](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [Optie B: Ontwerper](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [Optie C: Geautomatiseerde ML](/azure/machine-learning/tutorial-power-bi-automated-model)

- Aanmelden voor een [gratis Power BI-proefversie](https://app.powerbi.com/signupredirect?pbi_source=web).
- [Installeer Power BI Desktop](https://powerbi.microsoft.com/desktop/) op een lokale computer.

## <a name="create-the-data-model"></a>Het gegevensmodel maken

Open Power BI Desktop en selecteer **Gegevens ophalen**. Zoek in het dialoogvenster **Gegevens ophalen** naar **Web**. Selecteer de bron **Web** > **Verbinden**.

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="Schermopname met webgegevens.":::

Kopieer in het dialoogvenster **Van internet** de volgende URL en plak deze in het vak:

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="Schermopname met web-URL.":::

Selecteer **OK**.

Selecteer in **Internet inhoud** de optie **anonieme**  >  **verbinding**.

:::image type="content" source="media/service-aml-integrate/anonymous-access-web-content.png" alt-text="Scherm afbeelding met anonieme toegang voor webinhoud.":::

Selecteer **Gegevens transformeren** om het venster **Power Query-editor** te openen.

Selecteert in de Home-lint van de Power Query-editor de knop **Azure Machine Learning**.

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="Schermopname van Power Query-editor.":::

Nadat u zich hebt aangemeld bij uw Azure-account met een eenmalige aanmelding, ziet u een lijst met beschikbare services. Selecteer de **my-sklearn-service** die u hebt gemaakt op basis van het model uit de zelfstudie Een machine trainen en implementeren. 

Power Query zal de kolommen automatisch voor u invullen. In ons schema voor de service hadden we een Python-decorator die de invoer heeft opgegeven. Selecteer **OK**.

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="Schermopname met de Azure Machine Learning-modellen.":::

Als u **OK** selecteert, wordt de Azure Machine Learning Service aangeroepen. Er wordt een waarschuwing voor gegevensprivacy geactiveerd voor zowel de gegevens als het eindpunt.

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="Schermopname met privacywaarschuwing.":::

Selecteer **Doorgaan**. Selecteer in het volgende scherm **Controles privacyniveaus voor dit bestand negeren** > **Opslaan**.

Zodra de gegevens een score hebben ontvangen, maakt Power Query een extra kolom met de naam **AzureML.my-diabetes-model**.

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="Schermopname van toegevoegde kolom met score.":::

De gegevens die door de service worden geretourneerd, zijn een **lijst**. 

> [!NOTE]
> Als u een speciaal ontworpen model hebt geïmplementeerd, ziet u een **record**.

Als u de voor spellingen wilt ophalen, selecteert u de dubbele pijl in de **AzureML.my-diabetes-model** header > **uit te breiden naar nieuwe rijen**.

:::image type="content" source="media/service-aml-integrate/expand-column.png" alt-text="Scherm afbeelding met het pictogram voor het uitbreiden van de kolom.":::

Nadat u deze heeft uitgevouwen, ziet u de voorspellingen in de kolom AzureML.my-diabetes-model.

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="Schermopname met uitgevouwen kolom.":::

Voer de volgende stappen uit om het opschonen van uw gegevensmodel te voltooien.

1. Wijzig de naam van de kolom **AzureML.my-diabetes-model** in **voorspeld**.
1. Wijzig de naam van de kolom **Y** in **werkelijk**.
1. Wijzig het type van de kolom **werkelijk**: Selecteer de kolom en selecteer vervolgens op het lint **Transformeren** **Gegevenstype** > **Decimaal getal**.
1. Wijzig het type van de kolom **voorspeld**: Selecteer die kolom en selecteer vervolgens op het lint **Transformeren** **Gegevenstype** > **Decimaal getal**.
1. Selecteer in het lint **Start** de optie **Sluiten en toepassen**.

## <a name="create-a-report-with-visualizations"></a>Maak een rapport met visualisaties

Nu kunt u een aantal visualisaties maken om uw gegevens weer te geven.

1. Selecteer in het deelvenster **Visualisaties** een **Lijndiagram**. 
1. Met de geselecteerde lijndiagram weergegeven:
1. Sleep het veld **LEEFTIJD** naar de **As**.
1. Sleep het veld **werkelijk** naar **Waarden**.
1. Sleep het veld **voorspeld** naar **Waarden**.

Wijzig de grootte van het lijndiagram om de pagina op te vullen. Uw rapport heeft nu één lijndiagram met twee regels, een voor de voorspelde en één voor de werkelijke waarden, gedistribueerd op leeftijd.

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="Schermopname van rapportvisualisatie.":::

## <a name="publish-the-report"></a>Het rapport publiceren

U kunt als u wilt meer visualisaties toevoegen. Om het kort te houden publiceren we in deze zelfstudie het rapport.

1. Sla het rapport op.
1. Selecteer **Bestand** > **Publiceren** > **Publiceren naar Power BI**.
1. Meld u aan bij de Power BI-service.
1. Selecteer **Mijn werkruimte**.
1. Wanneer het rapport is gepubliceerd, selecteert u de koppeling **<MY_PBIX_FILE.pbix> in Power BI**. Het rapport opent het rapport in Power BI in uw browser.

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="Schermopname van succesvol publiceren.":::

## <a name="enable-datasets-to-refresh"></a>Gegevenssets laten vernieuwen

In een scenario waarin de gegevensbron wordt vernieuwd met nieuwe gegevens om te beoordelen, moet u uw referenties bijwerken zodat de gegevens een score kunnen ontvangen. 

In Mijn werkruimte in de Power BI-service, in de zwarte headerbalk, selecteert u **Meer opties (...)**  > **Instellingen** > **Instellingen**.

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="Schermopname met instellingen.":::

Selecteer **Gegevenssets**, vouw **Gegevensbronreferenties** uit en klik of tik op **Referenties bewerken**.

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="Schermopname van het vernieuwen van referenties.":::

Volg de instructies voor zowel **azureMLFunctions** als **Web**. Zorg ervoor dat u een privacyniveau selecteert. U kunt nu een **Geplande vernieuwing** van de gegevens instellen. Selecteer een **Vernieuwingsfrequentie** en **Tijdzone**. U kunt ook een e-mailadres selecteren waarop Power BI-berichten over het vernieuwen van de fout kunt verzenden.

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="Schermopname van het vernieuwen van de gegevensset en scores.":::

Selecteer **Toepassen**.

>[!NOTE]
> Wanneer de gegevens worden vernieuwd, worden de gegevens ook naar het Azure Machine Learning-eindpunt verzonden voor een score.

## <a name="clean-up-resources"></a>Resources opschonen

>[!IMPORTANT]
>U kunt de resources die u hebt gemaakt, gebruiken als vereisten voor andere Azure Machine Learning-zelfstudies en artikelen met procedures.

Als u niet van plan bent om de resources die u hebt gemaakt te gebruiken, verwijdert u deze zodat u geen kosten hoeft te maken.

1. Selecteer **Resourcegroepen** links in Azure Portal.
 
1. Selecteer de resourcegroep die u hebt gemaakt uit de lijst.

1. Selecteer **Resourcegroep verwijderen**.

   ![Schermopname van de selecties voor het verwijderen van een resourcegroep in de Azure-portal.](./media/service-aml-integrate/delete-resources.png)

1. Voer de naam van de resourcegroup in. Selecteer vervolgens **Verwijderen**.
1. Verwijder het rapport en de gerelateerde gegevensset in Mijn werkruimte in de Power BI-service. Het is niet nodig om Power BI Desktop of het rapport op uw computer zelf te verwijderen. Power BI Desktop is gratis.

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie leert u hoe u een planning instelt in Power BI zodat nieuwe gegevens in Azure Machine Learning een score kunnen ontvangen van uw score-eindpunt.
