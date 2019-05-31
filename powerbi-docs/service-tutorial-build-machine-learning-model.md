---
title: 'Zelfstudie: Bouw een Machine Learning-model in Power BI (Preview)'
description: In deze zelfstudie bouwt u een Machine Learning-model in Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406744"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Zelfstudie: Bouw een Machine Learning-model in Power BI (Preview)

In deze zelfstudie-artikel, gebruikt u **geautomatiseerde Machine Learning** maken en toepassen van een binaire voorspellingsmodel in Power BI. De zelfstudie bevat richtlijnen voor het maken van een Power BI-gegevensstroom, en met behulp van de entiteiten gedefinieerd in de gegevensstroom te trainen en een machine learning-model rechtstreeks in Power BI te valideren. Vervolgens gebruiken we dit model voor het scoren van voor het genereren van voorspellingen.

Eerst maakt u een binaire voorspelling machine learning-model, om te voorspellen van het doel van de aankoop van online shoppers op basis van een set van hun kenmerken online sessie. Een benchmark-machine learning-gegevensset wordt gebruikt voor deze oefening. Nadat een model wordt getraind, genereert Power BI automatisch een validatierapport uitleg over de modelresultaten. U kunt vervolgens het rapport bekijken en het model toepassen op uw gegevens voor het scoren.

In deze zelfstudie bestaat uit de volgende stappen uit:

> [!div class="checklist"]
> * Maken van een gegevensstroom met de ingevoerde gegevens
> * Maken en een machine learning-model trainen
> * Bekijk het rapport van de validatie van model
> * Het model toepassen op een entiteit gegevensstroom
> * Met behulp van de beoordeelde uitvoer van het model in een Power BI-rapport

## <a name="create-a-dataflow-with-the-input-data"></a>Maken van een gegevensstroom met de ingevoerde gegevens

Het eerste deel van deze zelfstudie is het maken van een gegevensstroom met invoergegevens. Dit proces duurt een paar stappen, zoals wordt weergegeven in de volgende secties, beginnen met het ophalen van gegevens.

### <a name="get-data"></a>Gegevens ophalen

De eerste stap bij het maken van een gegevensstroom is dat uw gegevensbronnen gereed. In ons geval gebruiken we een machine learning-gegevensset uit een set met online-sessies, waarvan sommige geleid een aankoop tot. De gegevensset bevat een set kenmerken voor deze sessies, we gebruiken het model te trainen.

U kunt de gegevensset van de website UC Irvine downloaden.  We hebben ook dit beschikbaar is, ten behoeve van deze zelfstudie, via de volgende koppeling: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>De entiteiten maken

Als u entiteiten in uw gegevensstroom wilt maken, meldt u zich aan bij de Power BI-service en gaat u naar een werkruimte in uw toegewezen capaciteit waarvoor AI-preview is ingeschakeld.

Als u nog een werkruimte hebt, kunt u maken door het selecteren van **werkruimten** in het navigatiemenu links in de Power BI-service en selecteer **app-werkruimte maken** aan de onderkant van het paneel die wordt weergegeven. Hiermee opent u een deelvenster op het recht om de details van de werkruimte invoeren. Voer de Werkruimtenaam van een en selecteer **Geavanceerd**. Bevestig dat de werkruimte maakt gebruik van toegewezen capaciteit die gebruikmaakt van het keuzerondje, en dat deze toegewezen aan een toegewezen capaciteit-exemplaar waarvoor de Preview-versie AI ingeschakeld. Selecteer vervolgens **Opslaan**.

![Een werkruimte maken](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Nadat de werkruimte is gemaakt, kunt u **overslaan** in de onderaan, rechts van het welkomstscherm wordt weergegeven, zoals wordt weergegeven in de volgende afbeelding.

![Als u een werkruimte hebt overslaan](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selecteer de **gegevensstromen (preview)** tabblad. Selecteer de **maken** bovenaan op de knop rechts van de werkruimte en selecteer vervolgens **gegevensstroom**.

![Maken van de gegevensstroom](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecteer **Nieuwe entiteiten toevoegen**. Dit start een **Power Query** -editor in de browser.

![Nieuwe entiteit toevoegen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selecteer **Text/CSV-bestand** weergegeven als een gegevensbron in de volgende afbeelding.

![Geselecteerde tekst/CSF-bestand](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

In de **verbinding maken met een gegevensbron** dat verschijnt het volgende, plak de volgende koppeling naar de *online_shoppers_intention.csv* in de **bestandspad of URL** vak en selecteer vervolgens  **Volgende**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Pad naar bestand](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

De Power Query-Editor bevat een voorbeeld van de gegevens uit het CSV-bestand. Selecteer **tabel transformeren** in het lint van de opdracht uit en selecteer vervolgens **gebruik eerste rij als veldnamen** in het menu dat wordt weergegeven. Hiermee voegt u toe de _gepromoveerd headers_ querystap in de **toegepaste stappen** sectie aan de rechterkant van het scherm. U kunt de query naar een toegankelijkere naam wijzigen door het wijzigen van de waarde in de **naam** vak gevonden in het rechter deelvenster. Bijvoorbeeld, u de naam van de Query kan wijzigen _Online bezoeker_.

![Wijzig in een beschrijvende naam](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Sommige van de kenmerk-gegevenstypen in deze gegevensset zijn _numerieke_ of _Booleaanse_, maar deze kunnen worden geïnterpreteerd als tekenreeksen door **Power Query**. Selecteer het pictogram voor het type van kenmerk aan de bovenkant van elke kolomkop om de hieronder vermelde naar de volgende typen kolommen wijzigen:

* **Decimaal getal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False:** Weekend; Revenue

![Gegevenstype wijzigen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

De **binaire voorspelling** we zullen train model is een Boole-veld vereist als een identificeren van de resultaten van de afgelopen opmerkingen label. In deze gegevensset de _omzet_ kenmerk geeft aan dat de aankoop en dit kenmerk is al beschikbaar als een Booleaanse waarde. Ja, moeten we niet een berekende kolom voor het label toevoegen. Mogelijk moet u bestaande labelkenmerken omzetten in een Booleaanse kolom in andere gegevenssets.

Selecteer de **gedaan** om te sluiten van Power Query-Editor. Hier worden de entiteiten met de _Online bezoekers_ gegevens die we hebben toegevoegd. Selecteer **opslaan** Geef een naam op voor de gegevensstroom in de rechterbovenhoek en selecteer vervolgens **opslaan** in het dialoogvenster, zoals wordt weergegeven in de volgende afbeelding.

![Opslaan van de gegevensstroom](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>De gegevensstroom vernieuwen

Opslaan van de resultaten van de gegevensstroom in een melding wordt weergegeven, waarin wordt vermeld dat de gegevensstroom is opgeslagen. Selecteer **nu vernieuwen** voor het opnemen van de gegevens van de bron in de gegevensstroom.

![Nu vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecteer rechtsboven **Sluiten** en wacht tot de gegevensstroom is vernieuwd.

U kunt ook uw gegevensstroom vernieuwen met behulp van de **acties** opdrachten. De gegevensstroom geeft het tijdstempel weer voor het vernieuwen is voltooid.

![Tijdstempel van vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Maken en een machine learning-model trainen

Selecteer de gegevensstroom na het vernieuwen is voltooid. Als u wilt toevoegen een machine learning-model, selecteer de **toepassen ML-model** knop in de **acties** lijst voor de basis-entiteit die uw gegevens en het label trainingsinformatie bevat en selecteer vervolgens **toevoegen een machine learning-model**.

![Een Machine Learning-model toevoegen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

De eerste stap voor het maken van onze machine learning-model is het identificeren van de historische gegevens, inclusief het labelveld dat u wilt voorspellen. Het model wordt gemaakt door learning uit deze gegevens.

In het geval van de gegevensset die we maken gebruik van dit is de **omzet** veld. Selecteer **omzet** als de waarde 'historische resultaat veld' en selecteer vervolgens **volgende**.

![Historische gegevens selecteren](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Vervolgens selecteren we het type van de machine learning-model te maken. Power BI analyseert de waarden in het veld historische resultaten die u hebt geïdentificeerd en stelt de typen van machine learning-modellen die kunnen worden gemaakt om te voorspellen dat veld.

In dit geval, omdat we een binaire resultaten van of een gebruiker een aankoop of niet maakt voorspellen nu, selecteert **binaire voorspelling** voor het modeltype en selecteer volgende.

![Binaire voorspelling geselecteerd](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Vervolgens Power BI is een voorlopige scan van de gegevens en stelt de invoer waarmee het model kan worden gebruikt. U hebt de mogelijkheid om aan te passen van de velden die worden gebruikt voor het model. In onze gecureerde gegevensset om te selecteren van alle velden, schakel het selectievakje naast de naam van de entiteit. Selecteer **volgende** te accepteren van de invoer.

![Het volgende selectievakje](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

In de laatste stap bieden we een naam voor het model, evenals de beschrijvende labels voor de resultaten moet worden gebruikt in de automatisch gegenereerde rapport worden de resultaten van de modelvalidatie om samen te vatten. Vervolgens hebben we om de naam van het model _aankoop bedoeling voorspelling_, en de labels true en false als _aankoop_ en _Nee-aankoop_. Selecteer vervolgens **Opslaan**.

![Sla het model](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Ons model voor machine learning is nu gereed voor training. Selecteer **nu vernieuwen** om te beginnen met het model te trainen.

![Nu vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

De trainingsproces wordt gestart door steekproeven en normaliseren van uw historische gegevens en uw gegevensset splitsen in twee nieuwe entiteiten *aankoop bedoeling voorspelling trainingsgegevens* en *aankoop bedoeling voorspelling testen Gegevens*.

Afhankelijk van de grootte van de gegevensset, kan de training duren overal in een paar minuten in een paar uur. Op dit moment ziet u het model in de **Machine learning-modellen** tabblad van de gegevensstroom. De _gereed_ status geeft aan dat het model in de wachtrij voor training geplaatst is of onder de training ligt.

![Gereed voor training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Het model is training, kunt u zich niet weergeven of bewerken van de gegevensstroom. U kunt bevestigen dat het model wordt getraind en gevalideerd tot en met de status van de gegevensstroom. Dit wordt weergegeven als een vernieuwen van gegevens wordt uitgevoerd in de **gegevensstromen** tabblad van de werkruimte.

![In proces](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Zodra het trainen van het model is voltooid, wordt een bijgewerkte vernieuwingstijd weergegeven in de gegevensstroom. U kunt bevestigen dat het model wordt getraind, door te navigeren naar de **Machine learning-modellen** tabblad in de gegevensstroom. Als de status moet worden weergegeven in het model dat u hebt gemaakt **Trained** en de **laatste getrainde** tijd moet nu worden bijgewerkt.

![Laatste getraind op](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Bekijk het rapport van de validatie van model

Om te controleren van het validatierapport model in de **Machine learning-modellen, s** er ook voor kiezen de **prestatierapport weergeven en toepassen van model** knop in de **acties** kolom voor het model . Dit rapport wordt beschreven hoe uw machine learning-model is het waarschijnlijk om uit te voeren.

In de **Modelprestaties** pagina van het rapport, selecteer **sleutel testteam** om de bovenste voorspellingsfactoren voor uw model weer te geven. U kunt een van de voorspellingsfactoren om te zien hoe de resultaat-distributie die is gekoppeld aan deze voorspelde selecteren.

![Modelprestaties](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

U kunt de **drempelwaarde voor waarschijnlijkheid** slicer op de pagina Modelprestaties om te onderzoeken haar invloed op de nauwkeurigheid en intrekken voor het model.

![Drempelwaarde waarschijnlijkheid](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

De andere pagina's van het rapport wordt de statistische prestatiegegevens voor het model beschreven.

Het rapport bevat ook een pagina met Details van de Training die de verschillende iteraties die zijn uitgevoerd beschrijft, hoe functies zijn opgehaald uit de invoer en de hyperparameters voor het uiteindelijke model dat wordt gebruikt.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Het model toepassen op een entiteit gegevensstroom

Selecteer de **toepassen model** knop aan de bovenkant van het rapport om aan te roepen van dit model wanneer de gegevensstroom wordt vernieuwd. In de **toepassen** dialoogvenster kunt u de doelentiteit die de brongegevens waarnaar het model moet worden toegepast.

![Het model toepassen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Als u hierom wordt gevraagd, moet u **vernieuwen** de gegevensstroom om een voorbeeld van de resultaten van uw model.

Toepassen van het model wordt een nieuwe entiteit maken met het achtervoegsel **verrijkt < modelnaam >** toegevoegd aan de entiteit waarop u het model toegepast. In ons geval toepassen van het model aan de **OnlineShoppers** entiteit maakt **OnlineShoppers verrijkt aankoop bedoeling voorspelling**, waaronder de verwachte uitvoer van het model.

Toepassen van een binaire voorspellingsmodel voegt drie kolommen met voorspelde resultaten, kans score en de eerste record specifieke testteam voor de voorspelling, elk voorafgegaan door de naam van de kolom opgegeven.

![Drie kolommen uitkomst](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

De beoordeelde uitvoerkolommen in de geavanceerde entiteit zijn alleen toegankelijk is vanuit Power BI Desktop vanwege een bekend probleem. Preview-versie van deze in de service, moet u een speciale preview-entiteit.

Zodra het vernieuwen van de gegevensstroom is voltooid, kunt u de **OnlineShoppers verrijkt aankoop bedoeling voorspelling Preview** entiteit de resultaten wilt weergeven.

![De resultaten bekijken](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Met behulp van de beoordeelde uitvoer van het model in een Power BI-rapport

Voor het gebruik van de beoordeelde uitvoer van uw machine learning-model, u kunt verbinding maken met uw gegevensstroom vanuit de Power BI desktop, met behulp van de connector gegevensstromen. De **OnlineShoppers verrijkt aankoop bedoeling voorspelling** entiteit kan nu worden gebruikt om op te nemen van de voorspellingen op basis van uw model in Power BI-rapporten.

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt gemaakt en een binaire voorspellingsmodel in Power BI met behulp van deze stappen toegepast:

* Maken van een gegevensstroom met de ingevoerde gegevens
* Maken en een machine learning-model trainen
* Bekijk het rapport van de validatie van model
* Het model toepassen op een entiteit gegevensstroom
* Met behulp van de beoordeelde uitvoer van het model in een Power BI-rapport

Zie voor meer informatie over automatisering in Machine Learning in Power BI [geautomatiseerde Machine Learning in Power BI (Preview)](service-machine-learning-automated.md).
