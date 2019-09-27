---
title: Geautomatiseerde Machine Learning in Power BI (preview)
description: Lees hoe u geautomatiseerde machine learning (AutoML) gebruikt in Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236269"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Geautomatiseerde Machine Learning in Power BI (preview)

Met geautomatiseerde machine learning (AutoML) voor gegevensstromen kunnen bedrijfsanalisten rechtstreeks in Power BI machine learning-modellen trainen, valideren en aanroepen. De service bevat een eenvoudige ervaring voor het maken van een nieuw ML-model, waarbij analisten hun gegevensstromen kunnen gebruiken om de invoergegevens op te geven voor het trainen van het model. De service extraheert automatisch de meest relevante functies en selecteert een geschikt algoritme, waarna het ML-model wordt afgestemd en gevalideerd. Nadat een model is getraind, genereert Power BI automatisch een rapport dat de resultaten van de validatie bevat waarin de prestaties en resultaten worden uitgelegd aan analisten. Het model kan vervolgens worden aangeroepen voor nieuwe of bijgewerkte gegevens in de gegevensstroom.

![Scherm voor machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Geautomatiseerde machine learning is alleen beschikbaar voor gegevensstromen die worden gehost in Power BI Premium of Embedded. In deze preview kunt u met AutoML machine learning-modellen trainen voor binaire voorspelling, classificatie en regressie.

## <a name="working-with-automl"></a>Werken met AutoML

Bij [Power BI-gegevensstromen](service-dataflows-overview.md) kunt u zelf gegevens voorbereiden voor big data. Met AutoML kunt u de taken voor gegevensvoorbereiding ook inzetten voor het bouwen van machine learning-modellen, rechtstreeks vanuit Power BI.

Met AutoML in Power BI kunnen gegevensanalisten aan de hand van gegevensstromen op een vereenvoudigde manier machine learning-modellen bouwen, met alleen maar hun Power BI-vaardigheden. Het grootste deel van de gegevenswetenschap achter het maken van de ML modellen wordt geautomatiseerd door Power BI, met ingebouwde mechanismen om ervoor te zorgen dat het geproduceerde model van goede kwaliteit is en zichtbaarheid om u volledig inzicht te geven in het proces dat wordt gebruikt om uw ML-model te maken.

AutoML biedt ondersteuning voor het maken van modellen van het type **Binaire voorspelling**, **Classificatie** en **Regressie** voor gegevensstromen. Dit zijn gecontroleerde ('supervised') typen machine learning-modellen, wat betekent dat ze leren van de bekende resultaten van eerdere waarnemingen om de resultaten van andere waarnemingen te voorspellen. De gegevensset die als invoer fungeert voor het trainen van een AutoML-model bestaat uit een set records die worden **gelabeld** met de bekende resultaten.

AutoML in Power BI integreert [geautomatiseerde ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) vanuit de [Azure Machine Learning-service](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) om uw ML-modellen te maken. U hebt echter geen Azure-abonnement nodig om AutoML te gebruiken in Power BI. Het proces van het trainen en hosten van de ML-modellen wordt volledig beheerd door de Power BI-service.

Nadat een ML-model is getraind, genereert AutoML automatisch een Power BI-rapport waarin de waarschijnlijke prestaties van uw ML-model worden uitgelegd. AutoML benadrukt de verklaarbaarheid door het accentueren van de belangrijkste beïnvloeders in de invoer die van invloed zijn op de voorspellingen die worden geretourneerd door uw model. Het rapport bevat ook belangrijke metrische gegevens voor het model, afhankelijk van het type ML-model.

Andere pagina's van het gegenereerde rapport bevatten het statistische overzicht van het model en de trainingsdetails. Het statistisch overzicht is van belang voor gebruikers die de standaardprestatiemetingen voor het model willen zien die worden gehanteerd in de gegevenswetenschap. De trainingsdetails geven een overzicht van alle iteraties die zijn uitgevoerd om het model te maken, met de bijbehorende modelleringsparameters. Hier wordt ook beschreven hoe elke invoer is gebruikt voor het maken van het ML-model.

U kunt het ML-model vervolgens toepassen op uw gegevens om een score te verkrijgen. Wanneer de gegevensstroom wordt vernieuwd, worden de voorspellingen van uw ML-model automatisch toegepast op uw gegevens. Power BI bevat ook een afzonderlijke uitleg voor elke specifieke voorspellingsscore die het ML-model produceert.

## <a name="creating-a-machine-learning-model"></a>Een machine learning-model maken

In dit gedeelte wordt beschreven hoe u een AutoML-model maakt. 

### <a name="data-prep-for-creating-an-ml-model"></a>Gegevens voorbereiden voor het maken van een ML-model

Als u een machine learning-model wilt maken in Power BI, moet u eerst een gegevensstroom maken voor de gegevens met de historische resultaatgegevens. Dit zijn de gegevens die worden gebruikt voor het trainen van het ML-model. Zie [Zelf gegevens voorbereiden in Power BI](service-dataflows-overview.md) voor meer informatie over het configureren van een gegevensstroom.

In de huidige release gebruikt Power BI gegevens uit slechts één entiteit om het ML-model te trainen. Dit betekent dat als uw historische gegevens uit meerdere entiteiten bestaan, u de gegevens handmatig moet samenvoegen in één gegevensstroomentiteit. Bovendien moet u berekende kolommen toevoegen voor metrische gegevens van het bedrijf die belangrijke voorspellingsfactoren kunnen zijn voor het resultaat dat u wilt voorspellen.

AutoML hanteert specifieke gegevensvereisten voor het trainen van een machine learning-model. Deze vereisten worden hieronder beschreven voor de verschillende modeltypen.

### <a name="configuring-the-ml-model-inputs"></a>Invoer voor ML-model configureren

Als u een AutoML-model wilt maken, selecteert u het ML-pictogram in de kolom **Acties** van de gegevensstroomentiteit met de historische gegevens en selecteert u vervolgens **Een Machine Learning-model toevoegen**.

![Een machine learning-model toevoegen](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Er wordt een vereenvoudigde ervaring gestart, die bestaat uit een wizard die u door het proces van het maken van het ML-model leidt. De wizard bestaat uit de volgende eenvoudige stappen.

1. Selecteer de entiteit met de historische resultaatgegevens en het veld waarvoor u een voorspelling wilt.
2. Kies een modeltype op basis van het type voorspelling dat u wilt zien.
3. Selecteer de invoer die door het model moet worden gebruikt als voorspellende signalen.
4. Geef uw model een naam en sla de configuratie op.

Bij 'Het veld Historisch resultaat' wordt het labelkenmerk voor het trainen van het ML-model weergegeven, zoals u kunt zien in de volgende afbeelding.

![Gegevens voor historisch resultaat selecteren](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

Wanneer u een kenmerk opgeeft voor 'Het veld Historisch resultaat', analyseert AutoML de labelgegevens om de type ML-modellen te identificeren die kunnen worden getraind voor die gegevens. Vervolgens wordt het meest waarschijnlijke type ML-model voorgesteld dat kan worden getraind. 

> [!NOTE]
> Sommige modeltypen worden mogelijk niet ondersteund voor de gegevens die u hebt geselecteerd.

AutoML analyseert ook alle velden in de geselecteerde entiteit om de invoer voor te stellen die kan worden gebruikt voor het trainen van het ML-model. Dit proces werkt bij benadering en is gebaseerd op statistische analyse. Dit betekent dat u de gebruikte invoer moet controleren. Invoer die afhankelijk is van de waarde in 'Het veld Historisch resultaat' (het labelveld) mag niet worden gebruikt voor het trainen van het ML-model, aangezien deze invoer invloed heeft op de prestaties.

![Invoervelden aanpassen](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

In de laatste stap kunt u het model een naam geven en de instellingen opslaan.

U wordt nu gevraagd om de gegevensstroom te vernieuwen, waarna het trainingsproces voor het ML-model wordt gestart.

### <a name="ml-model-training"></a>Training van ML-model

De training van AutoML-modellen vindt plaats tijdens het vernieuwen van een gegevensstroom. AutoML bereidt uw gegevens eerst voor op de training.

AutoML splitst de historische gegevens die u opgeeft in gegevenssets voor trainingsdoeleinden en voor testdoeleinden. De set voor testdoeleinden is een evaluatieset die wordt gebruikt om de modelprestaties na de training te valideren. Deze worden gerealiseerd als **Training- en Testing**-entiteiten in de gegevensstroom. AutoML maakt gebruik van kruisvalidatie voor de modelvalidatie.

Vervolgens wordt elk invoerveld geanalyseerd en wordt er imputatie toegepast, waarbij eventuele ontbrekende waarden worden vervangen door vervangende waarden. Er worden een aantal verschillende imputatiestrategieën gebruikt door AutoML. Daarna worden steekproeven en normalisatie toegepast op uw gegevens, indien nodig.

AutoML past verschillende transformaties toe op elke geselecteerd invoerveld, op basis van het gegevenstype en de statistische eigenschappen van het veld. AutoML gebruikt deze transformaties voor het extraheren van functies die kunnen worden gebruikt bij het trainen van uw ML-model.

Het trainingsproces voor AutoML-modellen bestaat uit maximaal 50 iteraties met verschillende modelleringsalgoritmen en hyperparameter-instellingen om het model met de beste prestaties te vinden. De prestaties van elk van deze modellen worden beoordeeld door validatie aan de hand van de set met evaluatiegegevens. Tijdens deze trainingsstap maakt AutoML verschillende pijplijnen voor de training en validatie van deze iteraties. Het proces van het beoordelen van de prestaties van de modellen kan enige tijd duren, van enkele minuten tot enkele uren, afhankelijk van de grootte van de gegevensset en de gereserveerde capaciteitsresources.

In sommige gevallen kan het uiteindelijke gegenereerde model gebruikmaken van 'ensemble learning', waarbij meerdere modellen worden gebruikt om betere voorspellende prestaties te bieden.

### <a name="automl-model-explainability"></a>Verklaarbaarheid van AutoML-model

Nadat het model is getraind, analyseert AutoML de relatie tussen de invoerfuncties en de modeluitvoer. Daarnaast worden voor elke invoerfunctie de magnitude en de richting van de wijziging van de modeluitvoer beoordeeld voor de set met evaluatiegegevens. Dit staat bekend als de *functie-urgentie*.

![Functie-urgentie](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>Rapport voor AutoML-model

AutoML genereert een Power BI-rapport met een overzicht van de prestaties van het model tijdens validatie, samen met het belang van globale functies. Het rapport geeft een overzicht van de resultaten van het toepassen van het ML-model op de testgegevens voor evaluatie en het vergelijken van de voorspellingen met de bekende resultaatwaarden.

U kunt het modelrapport bekijken om inzicht in de prestaties te krijgen. U kunt ook controleren of de belangrijkste beïnvloeders van het model overeenkomen met de zakelijke inzichten over de bekende resultaten.

De diagrammen en metingen die worden gebruikt om de prestaties van het model te beschrijven in het rapport, zijn afhankelijk van het modeltype. Deze prestatiediagrammen en metingen worden beschreven in de volgende secties.

Het rapport kan extra pagina's bevatten met statistische metingen van het model gezien vanuit het perspectief van de gegevenswetenschap. Zo bevat het rapport voor **binaire voorspellingen** bijvoorbeeld een toenamediagram en de ROC-curve voor het model.

De rapporten bevatten ook een pagina met **trainingsdetails** met een beschrijving van hoe het model is getraind, evenals een diagram met een beschrijving van de modelprestaties voor elke iteratie.

![Trainingsdetails](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Een ander gedeelte van deze pagina beschrijft de imputatiemethode die is gebruikt voor het invullen van ontbrekende waarden in de invoervelden, maar ook hoe de invoervelden zijn getransformeerd om de functies te extraheren die in het model worden gebruikt. De pagina bevat ook de parameters die worden gebruikt door het uiteindelijke model.

![Meer informatie voor het model](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Als het geproduceerde model gebruikmaakt van 'ensemble learning', bevat de pagina met **trainingsdetails** ook een gedeelte met een beschrijving van de weging van elk samenstellend model in het ensemble, samen met de bijbehorende parameters.

![Weging in het ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Toepassen van AutoML-model

Als u tevreden bent met de prestaties van het gemaakte ML-model, kunt u het model toepassen op nieuwe of bijgewerkte gegevens wanneer uw gegevensstroom wordt vernieuwd. Dit kunt u doen vanuit het modelrapport door in de rechterbovenhoek de knop **Toepassen** te selecteren.

Om het ML-model toe te passen, geeft u de naam op van de entiteit waarop u het model wilt toepassen en een voorvoegsel voor de kolommen die aan deze entiteit worden toegevoegd voor de modeluitvoer. Het standaardvoorvoegsel voor de kolomnamen is de modelnaam. De functie *Apply* kan aanvullende parameters bevatten die specifiek zijn voor het modeltype.

Als het ML-model wordt toegepast, wordt er een nieuwe gegevensstroomeenheid gemaakt met het achtervoegsel **enriched <naam_model>**. Als u bijvoorbeeld het model _PurchaseIntent_ toepast op de entiteit _OnlineShoppers_, is het resultaat **OnlineShoppers enriched PurchaseIntent**.

Op dit moment kan de uitvoerentiteit niet worden gebruikt om een voorbeeld van de resultaten van het ML-model te bekijken in de Power Query-editor. In de uitvoerkolommen wordt namelijk altijd null weergegeven als het resultaat. Om de resultaten te bekijken, wordt er een tweede uitvoerentiteit met het achtervoegsel **enriched <naam_model> Preview** gemaakt wanneer het model wordt toegepast.

U moet de gegevensstroom vernieuwen om de resultaten te kunnen bekijken in de query-editor.

![Query-editor](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Wanneer u het model toepast, zorgt AutoML ervoor dat uw voorspellingen altijd actueel zijn wanneer de gegevensstroom wordt vernieuwd.

AutoML voegt ook een afzonderlijke uitleg toe voor elke rij die een score krijgt in de uitvoerentiteit.

Als u de inzichten en voorspellingen uit het ML-model wilt gebruiken in een Power BI-rapport, kunt u vanuit Power BI Desktop verbinding maken met de uitvoerentiteit met behulp van de connector **dataflows**.

## <a name="binary-prediction-models"></a>Model van het type Binaire voorspelling

Modellen van het type Binaire voorspelling, formeel ook bekend als **binaire classificatiemodellen**, worden gebruikt om een gegevensset in twee groepen te classificeren. Ze worden gebruikt om gebeurtenissen te voorspellen die een binair resultaat kunnen hebben, zoals of een verkoopkans wordt geconverteerd, of een account wordt opgezegd, of een factuur op tijd wordt betaald, of een transactie frauduleus is, enzovoort.

Omdat het resultaat binair is, verwacht Power BI dat het label voor een binair voorspellingsmodel een Booleaanse waarde is, waarbij bekende resultaten worden gelabeld als **waar** of **onwaar**. In een model dat de conversie van verkoopkansen moet voorspellen, worden geconverteerde verkoopkansen bijvoorbeeld aangeduid als waar, terwijl niet-geconverteerde kansen worden gelabeld als niet waar. Openstaande verkoopkansen krijgen het label null.

De uitvoer van een binair voorspellingsmodel is een waarschijnlijkheidsscore, die de waarschijnlijkheid aangeeft dat het resultaat dat overeenkomt met de label werkelijkheid zal worden.

### <a name="training-a-binary-prediction-model"></a>Trainen van een binair voorspellingsmodel

Als u een binair voorspellingsmodel wilt maken, moet de invoerentiteit met uw trainingsgegevens een Booleaans veld bevatten als het veld met het historische resultaat om de eerdere bekende resultaten te identificeren.

Vereisten:

* Een Booleaans veld moet worden gebruikt als het veld met het historische resultaat
* Voor elke klasse met resultaten zijn minimaal 50 rijen met historische gegevens vereist

Als de eerdere resultaten worden aangeduid door velden van een ander gegevenstype, is het over het algemeen zo dat u een berekende kolom kunt toevoegen om deze velden met behulp van Power Query te transformeren in een Booleaanse waarde.

Het proces van het maken van een binair voorspellingsmodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven.

### <a name="binary-prediction-model-report"></a>Rapport voor binair voorspellingsmodel

Het binaire voorspellingsmodel produceert als uitvoer een waarschijnlijkheidsscore dat een record het resultaat bereikt dat door de Booleaanse labelwaarde als waar is gedefinieerd. Het rapport bevat een slicer voor de waarschijnlijkheidsdrempel, die van invloed is op de manier waarop de scores boven en onder de drempel worden geïnterpreteerd.

In het rapport worden de prestaties van het model beschreven in termen van *terecht positieven* (True Positives), *fout-positieven* (False Positives), *terecht negatieven* (True Negatives) en *fout-negatieven* (False Negatives). Terecht positieven en terecht negatieven zijn correct voorspelde resultaten voor de twee klassen in de resultaatgegevens. Fout-positieven zijn resultaten met de waarde Fase voor het Booleaanse label, maar die als waar zijn voorspeld. Fout-negatieven daarentegen zijn resultaten met de waarde True voor het Booleaanse label, maar die als onwaar zijn voorspeld.

Metingen, zoals Precisie en Terughalen, beschrijven het effect van de waarschijnlijkheidsdrempel op de voorspelde resultaten. U kunt de slicer met de waarschijnlijkheidsdrempel gebruiken om een drempel te selecteren die een compromis oplevert tussen Precisie en Terughalen.

![Voorbeeld van nauwkeurigheid](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

De pagina **Nauwkeurigheidsrapport** van het modelrapport bevat het diagram *Cumulatieve toenames* en de ROC-curve voor het model. Dit zijn statistische metingen van modelprestaties. De rapporten bevatten beschrijvingen van de weergegeven diagrammen.

![Scherm met nauwkeurigheidsrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Een binair voorspellingsmodel toepassen

Als u een binair voorspellingsmodel wilt toepassen, moet u de entiteit opgeven die de gegevens bevat waarop u de voorspellingen uit het ML-model wilt toepassen. Andere parameters zijn het voorvoegsel voor de naam van de uitvoerkolom en de waarschijnlijkheidsdrempel voor het classificeren van het voorspelde resultaat.

![Voorspellingsinvoer](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

Bij het toepassen van een binair voorspellingsmodel, worden er drie uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer. Dit zijn de kolommen **PredictionScore**, **PredictionOutcome** en **PredictionExplanation**. Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

De kolom **PredictionOutcome** bevat het label voor het voorspelde resultaat. Als records waarschijnlijkheidsscores hebben die de drempel overschrijden, wordt voorspeld dat ze het resultaat waarschijnlijk behalen. Voor records met scores onder de drempel geldt het omgekeerde en wordt voorspeld dat het onwaarschijnlijk is dat ze het resultaat behalen.

De kolom **PredictionExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **PredictionScore**. Dit is een met de JSON-indeling opgemaakte verzameling wegingen van de invoerfuncties voor de voorspelling.

## <a name="classification-models"></a>Classificatiemodellen

Classificatiemodellen worden gebruikt om een gegevensset in meerdere groepen of klassen te classificeren.  Ze worden gebruikt om gebeurtenissen te voorspellen die een van meerdere mogelijke resultaten kan hebben, zoals of een klant waarschijnlijk een zeer hoge, hoge, gemiddelde of lage levensduur heeft, of het risico voor betalingsverzuim hoog, gemiddeld, laag of zeer laag is, enzovoort.

De uitvoer van een classificatiemodel is een waarschijnlijkheidsscore die de kans aangeeft of een record de criteria voor een bepaalde klasse gaat behalen.

### <a name="training-a-classification-model"></a>Trainen van een classificatiemodel

De invoerentiteit met de trainingsgegevens voor een classificatiemodel moet een tekstveld of numeriek veld bevatten als het veld met het historische resultaat, waarin de eerdere bekende resultaten worden geïdentificeerd.

Vereisten:

* Voor elke klasse met resultaten zijn minimaal 50 rijen met historische gegevens vereist

Het proces van het maken van een binair classificatiemodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven.

### <a name="classification-model-report"></a>Rapport voor classificatiemodel

Het rapport voor een classificatiemodel wordt geproduceerd door het ML-model toe te passen op de evaluatiegegevens en de voorspelde klasse voor een record te vergelijken met de daadwerkelijk bekende klasse.

Het modelrapport bevat een diagram met een uitsplitsing van de juist en onjuist geclassificeerde records voor elke bekende klasse.

![Modelrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

U kunt verder inzoomen op een bepaalde klasse om een analyse mogelijk te maken van de manier waarop de voorspellingen voor een bekende klasse worden gedistribueerd. Dit omvat de andere klassen waarin records van die bekende klasse naar alle waarschijnlijkheid onjuist worden geclassificeerd.

![Analyserapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

De toelichting van het model in het rapport bevat ook de belangrijkste voorspellingsfactoren voor elke klasse.

Het rapport voor het classificatiemodel bevat ook een pagina met trainingsdetails die vergelijkbaar is met de pagina's voor andere modeltypen, zoals wordt beschreven in het gedeelte **Rapport voor AutoML-model** eerder in dit artikel.

### <a name="applying-a-classification-model"></a>Toepassen van een classificatiemodel

Als u een classificatiemodel wilt toepassen, moet u de entiteit opgeven met de invoergegevens en het voorvoegsel voor de naam van de uitvoerkolom.

Bij het toepassen van een classificatiemodel, worden er drie uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer. Dit zijn de kolommen **PredictionScore**, **PredictionClass** en **PredictionExplanation**. Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

De kolom **PredictionClass** bevat de meest waarschijnlijke voorspelde klasse voor de record. De kolom **PredictionScore** bevat de lijst met waarschijnlijkheidsscores voor de record voor elke mogelijke klasse.

De kolom **PredictionExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **PredictionScore**. Dit is een met de JSON-indeling opgemaakte verzameling wegingen van de invoerfuncties voor de voorspelling.

## <a name="regression-models"></a>Regressiemodellen

Regressiemodellen worden gebruikt om een waarde te voorspellen, zoals de omzet die waarschijnlijk zal worden gerealiseerd met een verkoop, de levensduur van een account, het bedrag van een factuur die waarschijnlijk zal worden betaald, de datum waarop een factuur kan worden betaald , enzovoort.

De uitvoer van een regressiemodel is de voorspelde waarde.

### <a name="training-a-regression-model"></a>Trainen van een regressiemodel

De invoerentiteit met de trainingsgegevens voor een regressiemodel moet een numeriek veld bevatten als het veld met het historische resultaat, waarin de eerdere bekende waarden worden geïdentificeerd.

Vereisten:

* Voor een regressiemodel zijn minimaal 100 rijen met historische gegevens vereist

Het proces van het maken van een regressiemodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven.

### <a name="regression-model-report"></a>Rapport van regressiemodel

Net als de andere AutoML-modelrapporten, wordt het regressierapport gebaseerd op de resultaten van het toepassen van het model op de evaluatiegegevens.

Het modelrapport bevat een diagram waarin de voorspelde waarden worden vergeleken met de werkelijke waarde. In dit diagram geeft de afstand vanaf de diagonaal de fout in de voorspelling aan.

In het diagram met resterende fouten ziet u de verdeling van het percentage van gemiddelde fouten voor verschillende waarden in de set met evaluatiegegevens. De horizontale as vertegenwoordigt het gemiddelde van de werkelijke waarde voor de groep, waarbij de grootte van de bel de frequentie of het aantal waarden in dat bereik aangeeft. De verticale as vertegenwoordigt de gemiddelde restfouten.

![Diagram met restfouten](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Het rapport voor het regressiemodel bevat ook een pagina met trainingsdetails, net zoals de rapporten voor andere modeltypen, zoals wordt beschreven in het gedeelte **Rapport voor AutoML-model** eerder in dit artikel.

### <a name="applying-a-regression-model"></a>Toepassen van een regressiemodel

Als u een regressiemodel wilt toepassen, moet u de entiteit opgeven met de invoergegevens en het voorvoegsel voor de naam van de uitvoerkolom.

![Een regressie toepassen](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Bij het toepassen van een regressiemodel, worden er twee uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer. Dit zijn **PredictionValue**en **PredictionExplanation.** Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

De kolom **PredictionValue** bevat de voorspelde waarde voor de record op basis van de invoervelden. De kolom **PredictionExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **PredictionValue**. Dit is een met de JSON-indeling opgemaakte verzameling wegingen van de invoerfuncties.

## <a name="next-steps"></a>Volgende stappen

In dit artikel hebt u een overzicht van geautomatiseerde machine learning voor gegevensstromen in de Power BI-service. De volgende artikelen kunnen ook van pas komen.

* [Zelfstudie: Een machine learning-model bouwen in Power BI (preview)](service-tutorial-build-machine-learning-model.md)
* [Zelfstudie: Cognitive Services gebruiken in Power BI](service-tutorial-use-cognitive-services.md)
* [Zelfstudie: Een Machine Learning Studio-model aanroepen in Power BI (preview)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services in Power BI (preview)](service-cognitive-services.md)
* [Azure Machine Learning-integratie in Power BI (preview)](service-machine-learning-integration.md)

Raadpleeg de volgende artikelen voor meer informatie over gegevensstromen:
* [Gegevensstromen maken en gebruiken in Power BI](service-dataflows-create-use.md)
* [Berekende entiteiten gebruiken in Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Gegevensstromen gebruiken met on-premises gegevensbronnen](service-dataflows-on-premises-gateways.md)
* [Resources voor ontwikkelaars voor Power BI-gegevensstromen](service-dataflows-developer-resources.md)
* [Integratie van gegevensstromen en Azure Data Lake (preview)](service-dataflows-azure-data-lake-integration.md)


