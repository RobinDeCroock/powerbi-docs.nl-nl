---
title: 'Zelfstudie: Een machine learning-model bouwen in Power BI (preview)'
description: In deze zelfstudie gaat u een machine learning-model bouwen in Power BI.
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
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406744"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Zelfstudie: Een machine learning-model bouwen in Power BI (preview)

In dit artikel gebruikt u **geautomatiseerde machine learning** om een binair voorspellingsmodel te maken en toe te passen in Power BI. De zelfstudie bevat richtlijnen voor het maken van een Power BI-gegevensstroom, en voor het gebruiken van de entiteiten die in de gegevensstroom zijn gedefinieerd om een machine learning-model te trainen en te valideren, rechtstreeks in Power BI. We gebruiken dat model vervolgens om met behulp van scores voorspellingen te genereren.

Eerst maakt u een machine learning-model van het type Binaire voorspelling, om de aankoopintentie van onlineklanten te voorspellen op basis van een set met kenmerken van hun onlinesessie. Voor deze oefening gebruiken we een gegevensset voor machine learning die als benchmark is gedefinieerd. Zodra een model is getraind, genereert Power BI automatisch een validatierapport waarin de resultaten van het model worden uitgelegd. U kunt dit validatierapport bekijken en het model toepassen op uw gegevens om een score te berekenen.

Deze zelfstudie bestaat uit de volgende stappen:

> [!div class="checklist"]
> * Een gegevensstroom maken met de invoergegevens
> * Een machine learning-model maken en trainen
> * Het modelvalidatierapport bekijken
> * Het model toepassen op een gegevensstroomentiteit
> * De beoordeelde uitvoer van het model gebruiken in een Power BI-rapport

## <a name="create-a-dataflow-with-the-input-data"></a>Een gegevensstroom maken met de invoergegevens

In het eerste deel van deze zelfstudie gaat u een gegevensstroom met invoergegevens maken. Dit proces vereist enkele stappen, zoals u kunt zien in de volgende secties, te beginnen met het ophalen van gegevens.

### <a name="get-data"></a>Gegevens ophalen

De eerste stap bij het maken van een gegevensstroom is ervoor te zorgen dat uw gegevensbronnen klaar zijn. In ons geval gebruiken we een gegevensset voor machine learning uit een reeks onlinesessies, waarvan sommige een aankoop hebben opgeleverd. De gegevensset bevat een reeks kenmerken van deze sessies, die we gebruiken voor het trainen van het model.

U kunt de gegevensset downloaden van de website van UC Irvine.  We hebben de gegevensset speciaal voor deze zelfstudie ook beschikbaar gemaakt via deze koppeling: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>De entiteiten maken

Als u entiteiten in uw gegevensstroom wilt maken, meldt u zich aan bij de Power BI-service en gaat u naar een werkruimte in uw toegewezen capaciteit waarvoor AI-preview is ingeschakeld.

Als u nog geen werkruimte hebt, kunt u er een maken door in het linkermenu **Werkruimten** te selecteren en vervolgens **Een werkruimte maken** te kiezen in het deelvenster aan de onderkant. Hiermee opent u een deelvenster aan de rechterkant waarin u gegevens van de werkruimte kunt invoeren. Voer een naam in voor de werkruimte en selecteer **Geavanceerd**. Controleer of de werkruimte toegewezen capaciteit gebruikt (die optie staat op Aan) en of de werkruimte is toegewezen aan een capaciteitsinstantie waarvoor de AI-preview is ingeschakeld. Selecteer vervolgens **Opslaan**.

![Een werkruimte maken](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Nadat de werkruimte is gemaakt, kunt u in de rechterbenedenhoek van het welkomstscherm **Overslaan** selecteren, zoals wordt aangegeven in de volgende afbeelding.

![Overslaan als u al een werkruimte hebt](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selecteer het tabblad **Gegevensstromen (preview)**. Selecteer in de rechterbovenhoek van de werkruimte de knop **Maken** en selecteer vervolgens **Gegevensstroom**.

![Gegevensstroom maken](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecteer **Nieuwe entiteiten toevoegen**. Hiermee wordt de editor **Power Query** gestart in de browser.

![Nieuwe entiteit toevoegen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selecteer **Tekst-/CSV-bestand** als gegevensbron, zoals wordt weer gegeven in de volgende afbeelding.

![Tekst-/CSV-bestand geselecteerd](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

U ziet nu het scherm **Verbinding maken met een gegevensbron**. Plak de volgende koppeling naar *online_shoppers_intention.csv* in het vak **Bestandspad of URL** en selecteer daarna **Volgende**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Bestandspad](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

In de Power Query-editor ziet u een voorbeeld van de gegevens uit het CSV-bestand. Selecteer **Tabel transformeren** op het lint met opdrachten en selecteer vervolgens **De eerste rij als veldnamen gebruiken**. Hiermee wordt de querystap _Headers met verhoogd niveau_ toegevoegd aan de sectie **Toegepaste stappen** aan de rechterkant van het scherm. U kunt de naam van de query wijzigen in een beschrijvende naam door de waarde in het vak **Naam** in het rechterdeelvenster aan te passen. U kunt de naam van de query bijvoorbeeld wijzigen in _Online Visitor_.

![Wijzigen in een beschrijvende naam](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Sommige van de gegevenstypen voor kenmerken in deze gegevensset zijn _numeriek_ of _Booleaans_, maar kunnen als tekenreeksen worden geïnterpreteerd door **Power Query**. Selecteer het pictogram voor het type kenmerk bovenaan een kolomkop om de onderstaande kolommen te wijzigen in de volgende typen:

* **Decimaal getal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Waar/onwaar:** Weekend; Revenue

![Gegevenstype wijzigen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Het **binaire voorspellingsmodel** dat we gaan trainen, vereist een Booleaans veld als een label dat de resultaten van de eerdere waarnemingen identificeert. In deze gegevensset geeft het kenmerk _Revenue_ aankoop aan, en dit kenmerk is al beschikbaar als een Booleaanse waarde. Het is dus niet nodig om een berekende kolom toe te voegen voor het label. In andere gegevenssets kan het nodig zijn om bestaande labelkenmerken te transformeren naar een Booleaanse kolom.

Selecteer de knop **Gereed** om de Power Query-editor te sluiten. U ziet nu de lijst met entiteiten met de gegevens voor _Online Visitor_ die we hebben toegevoegd. Selecteer rechtsboven **Opslaan**, geef een naam voor de gegevensstroom op en selecteer **Opslaan** (zie de volgende afbeelding).

![De gegevensstroom opslaan](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>De gegevensstroom vernieuwen

Als u de resultaten voor de gegevensstroom opslaat, verschijnt er een melding om dit te bevestigen. Selecteer **Nu vernieuwen** om de gegevens uit de bron op te nemen in de gegevensstroom.

![Nu vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecteer rechtsboven **Sluiten** en wacht tot de gegevensstroom is vernieuwd.

U kunt de gegevensstroom ook vernieuwen met behulp van de opdrachten in **Acties**. De gegevensstroom wordt weergegeven met een tijdstempel die aangeeft wanneer het vernieuwen is voltooid.

![Tijdstempel van vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Een machine learning-model maken en trainen

Selecteer de gegevensstroom nadat het vernieuwen is voltooid. Als u een machine learning-model wilt toevoegen, selecteert u de knop **ML-model toepassen** in de lijst **Acties** voor de basisentiteit die uw trainings- en labelgegevens bevat, en selecteert u vervolgens **Een Machine Learning-model toevoegen**.

![Een Machine Learning-model toevoegen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

De eerste stap voor het maken van ons machine learning-model is het identificeren van de historische gegevens, inclusief het labelveld dat u wilt voorspellen. Het model wordt gemaakt door te leren van deze gegevens.

In het geval van de gegevensset die we gebruiken, is dit het veld **Revenue**. Selecteer **Revenue** als waarde voor 'Het veld Historisch resultaat' en selecteer vervolgens **Volgende**.

![Historische gegevens selecteren](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Vervolgens moeten we het type machine learning-model selecteren dat we willen maken. Power BI analyseert de waarden in het veld met historisch resultaten dat u hebt geïdentificeerd en stelt de typen machine learning-modellen voor die kunnen worden gemaakt om dat veld te voorspellen.

Aangezien we in dit geval een binair resultaat willen voor de vraag of een gebruiker al dan niet tot aankoop zal overgaan, selecteert u **Binaire voorspelling** als het type model en selecteert u vervolgens Volgende.

![Het modeltype Binaire voorspelling geselecteerd](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Power BI voert vervolgens een eerste scan uit van de gegevens en stelt de invoer voor die het model zou kunnen gebruiken. U hebt de mogelijkheid om de invoervelden die voor het model worden gebruikt, aan te passen. Als u in de gecureerde gegevensset alle velden wilt selecteren, schakel u het selectievakje naast de naam van de entiteit in. Selecteer **Volgende** om de invoer te accepteren.

![Het bovenste selectievakje inschakelen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

In de laatste stap moeten we een naam opgeven voor ons model, evenals de beschrijvende labels voor de resultaten die moeten worden gebruikt in het automatisch gegenereerde rapport waarin de resultaten van de modelvalidatie worden samengevat. We geven het model de naam _Purchase Intent Prediction_, en de waar- en onwaar-labels stellen we in op _Purchase_ en _No-Purchase_. Selecteer vervolgens **Opslaan**.

![Het model opslaan](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Het machine learning-model is nu klaar voor training. Selecteer **Nu vernieuwen** om het model te gaan trainen.

![Nu vernieuwen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Het trainingsproces begint met het bemonsteren en normaliseren van uw historische gegevens en het opsplitsen van de gegevensset in twee nieuwe entiteiten: *Purchase Intent Prediction Training Data* en *Purchase Intent Prediction Testing Data*.

Afhankelijk van de grootte van de gegevensset kan het trainingsproces enkele minuten tot enkele uren duren. Op dit moment kunt u het model zien op het tabblad **Machine Learning-modellen** van de gegevensstroom. De status _Gereed_ geeft aan dat het model in de wachtrij is geplaatst voor training of wordt getraind.

![Klaar voor training](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Terwijl het model wordt getraind, kunt u de gegevensstroom niet weergeven of bewerken. U kunt aan de status van de gegevensstroom zien of het model wordt getraind en gevalideerd. Dit wordt aangegeven als het vernieuwen van gegevens op het tabblad **Gegevensstromen** van de werkruimte.

![In verwerking](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Zodra de training van het model is voltooid, wordt voor de gegevensstroom een bijgewerkte tijd voor vernieuwing weergegeven. U kunt controleren of het model is getraind door naar het tabblad **Machine Learning-modellen** van de gegevensstroom te gaan. Het model dat u hebt gemaakt, moet de status **Getraind** hebben en de tijd bij **Laatst getraind** moet zijn bijgewerkt.

![Laatst getraind op](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Het modelvalidatierapport bekijken

Als u het validatierapport van het model wilt bekijken, selecteert u in **Machine Learning-modellen** de knop **Prestatierapport weergeven en model toepassen** in de kolom **Acties** voor het model. In dit rapport wordt beschreven hoe uw machine learning-model waarschijnlijk zal presteren.

Selecteer op de pagina **Modelprestaties** van het rapport **Belangrijkste beïnvloeders** om de belangrijkste voorspellingsfactoren voor uw model weer te geven. U kunt een van de voorspellingsfactoren selecteren om te zien hoe het resultaat van die factor is verdeeld.

![Modelprestaties](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

U kunt de slicer **Drempelwaarde waarschijnlijkheid** op de pagina Modelprestaties gebruiken om de invloed van de voorspellingsfactor op de waarden voor precisie en terughalen van het model te onderzoeken.

![Drempelwaarde waarschijnlijkheid](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

Op de andere pagina's van het rapport worden de statistische prestatiegegevens voor het model beschreven.

Het rapport bevat ook een pagina Trainingsdetails waarop de verschillende iteraties worden beschreven die zijn uitgevoerd, hoe functies zijn geëxtraheerd uit de invoer en de hyperparameters die voor het uiteindelijke model zijn gebruikt.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Het model toepassen op een gegevensstroomentiteit

Selecteer de knop **Model toepassen** bovenaan het rapport om dit model aan te roepen wanneer de gegevensstroom wordt vernieuwd. In het dialoogvenster **Toepassen** kunt u de doelentiteit opgeven die de brongegevens bevat waarop het model moet worden toegepast.

![Het model toepassen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Als dit wordt gevraagd, moet u de gegevensstroom **vernieuwen** om een voorbeeld van de resultaten van het model te kunnen bekijken.

Als het model wordt toegepast, wordt er een nieuwe entiteit gemaakt, waarbij het achtervoegsel **enriched <modelnaam>** wordt toegevoegd aan de entiteit waarop u het model hebt toegepast. In ons geval wordt het model toegepast op de entiteit **OnlineShoppers** en wordt er een nieuwe entiteit **OnlineShoppers enriched Purchase Intent Prediction** gemaakt die de voorspelde uitvoer van het model bevat.

Bij het toepassen van een binair voorspellingsmodel worden er drie kolommen toegevoegd met het voorspelde resultaat, een waarschijnlijkheidsscore en de belangrijkste, recordspecifieke beïnvloeders voor de voorspelling, ieder voorafgegaan door de opgegeven kolomnaam.

![Drie kolommen met resultaten](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Als gevolg van een bekend probleem zijn de beoordeelde uitvoerkolommen in de verrijkte entiteit alleen toegankelijk vanuit Power BI Desktop. Als u een voorbeeld wilt bekijken in de Power BI-service, moet u een speciale voorbeeldentiteit gebruiken.

Zodra het vernieuwen van de gegevensstroom is voltooid, kunt u de entiteit **OnlineShoppers enriched Purchase Intent Prediction Preview** selecteren om de resultaten te bekijken.

![De resultaten bekijken](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>De beoordeelde uitvoer van het model gebruiken in een Power BI-rapport

Als u de beoordeelde uitvoer van uw machine learning-model wilt gebruiken, kunt u vanuit Power BI Desktop verbinding maken met de gegevensstroom (met behulp van de connector Gegevensstromen). De entiteit **OnlineShoppers enriched Purchase Intent Prediction** kan nu worden gebruikt om de voorspellingen van uw model op te nemen in Power BI-rapporten.

## <a name="next-steps"></a>Volgende stappen

In deze zelfstudie hebt u een binair voorspellingsmodel gemaakt en toegepast in Power BI met behulp van de volgende stappen:

* Een gegevensstroom maken met de invoergegevens
* Een machine learning-model maken en trainen
* Het modelvalidatierapport bekijken
* Het model toepassen op een gegevensstroomentiteit
* De beoordeelde uitvoer van het model gebruiken in een Power BI-rapport

Zie [Geautomatiseerde machine learning in Power BI (preview)](service-machine-learning-automated.md) voor meer informatie over geautomatiseerde machine learning in Power BI.
