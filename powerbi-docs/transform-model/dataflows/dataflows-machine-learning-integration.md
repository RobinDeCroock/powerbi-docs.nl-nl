---
title: Machine Learning en Cognitive Services gebruiken met gegevensstromen
description: Overzicht van het gebruik van machine learning en geautomatiseerde machine learning met gegevensstromen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 703e87847f2f6dfb24040cc6532052b17d39086c
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668529"
---
# <a name="ai-with-dataflows"></a>AI met gegevensstromen

In dit artikel bespreken we manieren waarop u kunstmatige intelligentie (Artificial Intelligence, oftewel AI) kunt gebruiken met gegevensstromen. In dit artikel worden de volgende gebieden beschreven:

* Cognitive Services
* Geautomatiseerde machine learning
* Integratie van Azure Machine Learning

## <a name="cognitive-services-in-power-bi"></a>Cognitive Services in Power BI

Met Cognitive Services in Power BI kunt u verschillende algoritmen uit [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) toepassen om uw gegevens te verrijken in de selfservice voor gegevensvoorbereiding voor gegevensstromen.

De services die momenteel worden ondersteund zijn [Sentimentanalyse](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-sentiment-analysis), [Sleuteltermextractie](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-keyword-extraction), [Taaldetectie](/azure/cognitive-services/text-analytics/how-tos/text-analytics-how-to-language-detection) en [Afbeeldingen taggen](/azure/cognitive-services/computer-vision/concept-tagging-images). De transformaties worden uitgevoerd in de Power BI-service en vereisen geen Azure Cognitive Services-abonnement. Deze functie vereist Power BI Premium.

### <a name="enabling-ai-features"></a>**AI-functies inschakelen**

Cognitive Services worden ondersteund voor de Premium-capaciteitsknooppunten EM2, A2, P1 en hoger. Voor het uitvoeren van Cognitive Services wordt een afzonderlijke AI-werkbelasting op de capaciteit gebruikt. Tijdens de openbare preview (vóór juni 2019) is deze werkbelasting standaard uitgeschakeld. Voordat u Cognitive Services in Power BI gaat gebruiken, moet de AI-werkbelasting worden ingeschakeld in de capaciteitsinstellingen van de beheerportal. U kunt de AI-werkbelasting in de sectie Werkbelastingen inschakelen en de maximale hoeveelheid geheugen definiëren die deze werkbelasting mag gebruiken. De aanbevolen geheugenlimiet is 20%. Door deze limiet te overschrijden, vertraagt de query.

![Cognitive Services in Power BI](media/service-cognitive-services/cognitive-services-01.png)

### <a name="getting-started-with-cognitive-services-in-power-bi"></a>**Aan de slag met Cognitive Services in Power BI**

Cognitive Services-transformaties maken deel uit van de [selfservice voor gegevensvoorbereiding voor gegevensstromen](https://powerbi.microsoft.com/blog/introducing-power-bi-data-prep-wtih-dataflows/). Begin met het bewerken van een gegevensstroom om uw gegevens met Cognitive Services te verrijken.

![Een gegevensstroom bewerken](media/service-cognitive-services/cognitive-services-02.png)

Selecteer de knop **AI-inzichten** in het bovenste lint van de Power Query-editor.

![AI-inzichten in de Power Query-editor](media/service-cognitive-services/cognitive-services-03.png)

Selecteer in het pop-upvenster de functie die u wilt gebruiken en de gegevens die u wilt transformeren. In dit voorbeeld scoor ik het gevoel van een kolom die beoordelingstekst bevat.

![Selecteer een functie](media/service-cognitive-services/cognitive-services-04.png)

**Cultureinfo** is een optionele invoer om de taal van de tekst te bepalen. In dit veld moet een ISO-code worden ingevoerd. Als invoer voor Cultureinfo kunt u een kolom of een statisch veld gebruiken. In dit voorbeeld is de taal voor de hele kolom als Engels (en) opgegeven. Als u dit veld leeg laat, detecteert Power BI automatisch de taal voordat de functie wordt toepast. Selecteer vervolgens **Aanroepen.**

![Aanroepen selecteren](media/service-cognitive-services/cognitive-services-05.png)

Nadat de functie is aangeroepen, wordt het resultaat als een nieuwe kolom aan de tabel toegevoegd. De transformatie wordt ook als een toegepaste stap aan de query toegevoegd.

![Er wordt een nieuwe kolom gemaakt](media/service-cognitive-services/cognitive-services-06.png)

Als de functie meerdere uitvoervelden retourneert, wordt er door het aanroepen van de functie een nieuwe kolom met een record van de verschillende uitvoervelden toegevoegd.

Gebruik de uitvouwoptie om een of beide waarden als kolommen aan uw gegevens toe te voegen.

![Kolom uitvouwen](media/service-cognitive-services/cognitive-services-07.png)

### <a name="available-functions"></a>**Beschikbare functies**

Deze sectie beschrijft de beschikbare functies in Cognitive Services in Power BI.

#### <a name="detect-language"></a>**Taal detecteren**

De taaldetectiefunctie evalueert tekstinvoer en retourneert voor elk veld de taal en ISO-id. Deze functie is handig voor gegevenskolommen die willekeurige tekst verzamelen waarvan de taal onbekend is. Als invoer verwacht de functie gegevens in tekstindeling.

Text Analytics herkent maximaal 120 talen. Zie voor meer informatie [Ondersteunde talen](/azure/cognitive-services/text-analytics/text-analytics-supported-languages).

#### <a name="extract-key-phrases"></a>**Sleuteltermen ophalen**

De functie **Sleuteltermextractie** evalueert ongestructureerde tekst en retourneert voor elk tekstveld een lijst met sleuteltermen. De functie vereist als invoer een tekstveld en accepteert een optionele invoer voor **Cultureinfo**. (Zie de sectie **Aan de slag** eerder in dit artikel).

Sleuteltermextractie werkt het beste bij grotere lappen tekst. Dit is het tegenovergestelde van Sentimentanalyse, die beter presteert bij kleinere stukken tekst. Voor de beste resultaten bij beide activiteiten, zou u de invoeren dienovereenkomstig kunnen herstructureren.

#### <a name="score-sentiment"></a>**Gevoel scoren**

De functie **Gevoel scoren** evalueert tekstinvoer en retourneert een gevoelsscore voor elk document, variërend van 0 (negatief) tot 1 (positief). Deze functie is handig voor het detecteren van positieve en negatieve gevoelens op sociale media, klantbeoordelingen en discussiefora.

Text Analytics maakt gebruik van een machine learning-classificatiealgoritme voor het genereren van een gevoelsscore tussen 0 en 1. Scores dichter bij 1 duiden op een positief gevoel, scores dichter bij 0 op een negatief gevoel. Het model is vooraf getraind met een uitgebreide hoeveelheid tekst met gevoelsassociaties. Het is momenteel niet mogelijk om uw eigen trainingsgegevens te gebruiken. Het model maakt tijdens de tekstanalyse gebruik van een combinatie aan technieken, waaronder tekstverwerking, woordsoortanalyse, woordplaatsing en woordassociaties. Zie voor meer informatie over het algoritme [Introducing Text Analytics](/archive/blogs/machinelearning/machine-learning-and-text-analytics) (Maak kennis met Text Analytics).

Sentimentanalyse wordt uitgevoerd op het hele invoerveld en niet op een bepaalde entiteit in de tekst. In de praktijk verbetert het scoren van nauwkeurigheid wanneer documenten een of twee zinnen bevatten in plaats van een grote lap tekst. Tijdens een objectiviteitsevaluatie bepaalt het model of een invoerveld als geheel objectief is of gevoel bevat. Een invoerveld dat voornamelijk objectief is, gaat met een score van .50 niet door naar de gevoelsdetectiefase en wordt ook niet verder verwerkt. Voor invoervelden die doorgaan in de pijplijn, genereert de volgende fase een score die hoger of lager is dan .50, afhankelijk van de gevoelswaarde van het invoerveld.

Op dit moment ondersteunt Sentimentanalyse Engels, Duits, Spaans en Frans. Andere talen zijn beschikbaar als preview. Zie voor meer informatie [Ondersteunde talen](/azure/cognitive-services/text-analytics/text-analytics-supported-languages).

#### <a name="tag-images"></a>**Afbeeldingen taggen**

De functie **Afbeeldingen taggen** retourneert tags op basis van meer dan 2.000 herkenbare objecten, levende wezens, landschappen en acties. Wanneer tags ambigu of niet algemeen bekend zijn, biedt de uitvoer 'hints' om de betekenis van de tag in de context van een bekende instelling te duiden. Tags worden niet als taxonomie geordend en er bestaan geen overnamehiërarchieën. Een verzameling inhoudstags vormt de basis voor een 'beschrijving van de afbeelding, weergegeven als voor mensen leesbare taal opgemaakt in volledige zinnen.

Na het uploaden van een afbeelding of het specificeren van een afbeeldings-URL, leveren de algoritmen van Computer Vision als output tags die zijn gebaseerd op objecten, levende wezens en acties die in de afbeelding zijn herkend. Niet alleen het belangrijkste onderwerp, bijvoorbeeld een persoon op de voorgrond, maar ook de setting (binnen of buiten), meubels, hulpmiddelen, planten, dieren, accessoires, gadgets enz. kunnen worden getagd.

Als invoer vereist deze functie een afbeeldings-URL of een base 64-veld. Momenteel ondersteunt Afbeeldingen taggen Engels, Spaans, Japans, Portugees en vereenvoudigd Chinees. Zie voor meer informatie [Ondersteunde talen](/rest/api/cognitiveservices/computervision/tagimage/tagimage#uri-parameters).

## <a name="automated-machine-learning-in-power-bi"></a>Geautomatiseerde Machine Learning in Power BI

Met geautomatiseerde machine learning (AutoML) voor gegevensstromen kunnen bedrijfsanalisten rechtstreeks in Power BI machine learning-modellen (ML) trainen, valideren en aanroepen. De service bevat een eenvoudige ervaring voor het maken van een nieuw ML-model, waarbij analisten hun gegevensstromen kunnen gebruiken om de invoergegevens op te geven voor het trainen van het model. De service extraheert automatisch de meest relevante functies en selecteert een geschikt algoritme, waarna het ML-model wordt afgestemd en gevalideerd. Nadat een model is getraind, genereert Power BI automatisch een prestatierapport dat de resultaten van de validatie bevat. Het model kan vervolgens worden aangeroepen voor nieuwe of bijgewerkte gegevens in de gegevensstroom.

![Scherm voor machine learning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Geautomatiseerde machine learning is alleen beschikbaar voor gegevensstromen die worden gehost in Power BI Premium of Embedded.

### <a name="working-with-automl"></a>Werken met AutoML

Bij gegevensstromen kunt u zelf gegevens voorbereiden voor big data. Met AutoML, geïntegreerd in gegevensstromen, kunt u de taken voor gegevensvoorbereiding ook inzetten voor het bouwen van machine learning-modellen, rechtstreeks vanuit Power BI.

Met AutoML in Power BI kunnen gegevensanalisten aan de hand van gegevensstromen op een vereenvoudigde manier machine learning-modellen bouwen, met alleen maar hun Power BI-vaardigheden. Het grootste deel van de gegevenswetenschap achter het maken van de ML-modellen wordt geautomatiseerd door Power BI. Het heeft vangnetten om ervoor te zorgen dat het gegenereerde model van goede kwaliteit is en inzicht geeft in het proces dat wordt gebruikt om uw ML-model te maken.

AutoML biedt ondersteuning voor het maken van modellen van het type **Binaire voorspelling**, **Classificatie** en **Regressie** voor gegevensstromen. Dit zijn gecontroleerde ('supervised') typen machine learning-technieken, wat betekent dat ze leren van de bekende resultaten van eerdere waarnemingen om de resultaten van andere waarnemingen te voorspellen. De gegevensset die als invoer fungeert voor het trainen van een AutoML-model bestaat uit een set records die worden **gelabeld** met de bekende resultaten.

Met AutoML in Power BI integreert u [geautomatiseerde ML](/azure/machine-learning/service/concept-automated-ml) uit [Azure Machine Learning](/azure/machine-learning/service/overview-what-is-azure-ml) om uw ML-modellen te maken. U hebt echter geen Azure-abonnement nodig om AutoML te gebruiken in Power BI. Het proces van het trainen en hosten van de ML-modellen wordt volledig beheerd door de Power BI-service.

Nadat een ML-model is getraind, genereert AutoML automatisch een Power BI-rapport waarin de waarschijnlijke prestaties van uw ML-model worden uitgelegd. AutoML benadrukt de verklaarbaarheid door het accentueren van de belangrijkste beïnvloeders in de invoer die van invloed zijn op de voorspellingen die worden geretourneerd door uw model. Het rapport bevat ook belangrijke metrische gegevens voor het model.

Andere pagina's van het gegenereerde rapport bevatten het statistische overzicht van het model en de trainingsdetails. Het statistisch overzicht is van belang voor gebruikers die de standaardprestatiemetingen voor het model willen zien die worden gehanteerd in de gegevenswetenschap. De trainingsdetails geven een overzicht van alle iteraties die zijn uitgevoerd om het model te maken, met de bijbehorende modelleringsparameters. Hier wordt ook beschreven hoe elke invoer is gebruikt voor het maken van het ML-model.

U kunt het ML-model vervolgens toepassen op uw gegevens om een score te verkrijgen. Wanneer de gegevensstroom wordt vernieuwd, worden uw gegevens bijgewerkt met voorspellingen uit uw ML-model. Power BI bevat ook een afzonderlijke uitleg voor elke specifieke voorspelling die het ML-model produceert.

### <a name="creating-a-machine-learning-model"></a>Een machine learning-model maken

In dit gedeelte wordt beschreven hoe u een AutoML-model maakt.

#### <a name="data-prep-for-creating-an-ml-model"></a>Gegevens voorbereiden voor het maken van een ML-model

Als u een machine learning-model wilt maken in Power BI, moet u eerst een gegevensstroom maken voor de gegevens die de historische resultaatgegevens bevatten. Dit zijn de gegevens die worden gebruikt voor het trainen van het ML-model. Bovendien moet u berekende kolommen toevoegen voor metrische gegevens van het bedrijf die belangrijke voorspellingsfactoren kunnen zijn voor het resultaat dat u wilt voorspellen. Zie [Een gegevensstroom configureren en gebruiken](dataflows-configure-consume.md) voor meer informatie over het configureren van uw gegevensstroom.

AutoML hanteert specifieke gegevensvereisten voor het trainen van een machine learning-model. Deze vereisten worden hieronder beschreven voor de verschillende modeltypen.

#### <a name="configuring-the-ml-model-inputs"></a>Invoer voor ML-model configureren

Als u een AutoML-model wilt maken, selecteert u het ML-pictogram in de kolom **Acties** van de gegevensstroomentiteit en selecteert u vervolgens **Een Machine Learning-model toevoegen**.

![Een machine learning-model toevoegen](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Er wordt een vereenvoudigde ervaring gestart, die bestaat uit een wizard die u door het proces van het maken van het ML-model leidt. De wizard bestaat uit de volgende eenvoudige stappen.

**1. Selecteer de entiteit met de historische gegevens en het resultaatveld waarvoor u een voorspelling wilt**

Het resultaatveld geeft het labelkenmerk voor het trainen van het ML-model aan, zoals u kunt zien in de volgende afbeelding.

![Gegevens voor historisch resultaat selecteren](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

**2. Een modeltype kiezen**

Wanneer u het resultaatveld opgeeft, analyseert AutoML de labelgegevens om het meest waarschijnlijke ML-modeltype te adviseren dat kan worden getraind. U kunt een ander modeltype kiezen, zoals hieronder wordt weergegeven, door te klikken op 'Een ander model selecteren'.

![Een model selecteren](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

> [!NOTE]
> Sommige modeltypen worden mogelijk niet ondersteund voor de gegevens die u hebt geselecteerd en zijn dan ook uitgeschakeld. In het bovenstaande voorbeeld is Regressie uitgeschakeld, omdat een tekstkolom als resultaatveld is geselecteerd.

**3. Selecteer de invoer die door het model moet worden gebruikt als voorspellende signalen**

AutoML analyseert een sample van de geselecteerde entiteit om de invoer voor te stellen die kan worden gebruikt voor het trainen van het ML-model. Er wordt uitleg gegeven naast de velden die niet zijn geselecteerd. Als een bepaald veld te veel afzonderlijke waarden of slechts één waarde bevat, of een lage of hoge correlatie met het uitvoerveld heeft, wordt dit niet aanbevolen.

Invoer die afhankelijk is van de waarde in het resultaatveld (het labelveld) mag niet worden gebruikt voor het trainen van het ML-model, aangezien deze invoer invloed heeft op de prestaties. Dergelijke velden worden gemarkeerd met 'verdacht hoge correlatie met uitvoerveld'. De introductie van deze velden in de trainingsgegevens leidt tot labellekkage, waarbij het model goed wordt uitgevoerd op de validatie- of testgegevens, maar die prestaties niet kan evenaren indien gebruikt in productie om een score te berekenen. Labellekkage kan een mogelijke reden tot zorg zijn in AutoML-modellen, wanneer de prestaties van het trainingsmodel te mooi zijn om waar te zijn.

Deze functie-aanbeveling is gebaseerd op een sample van gegevens, waardoor u de gebruikte invoer moet controleren. U hebt de mogelijkheid om de selecties te wijzigen, zodat deze alleen de velden bevatten die door het model moeten worden onderzocht. U kunt ook alle velden selecteren door het selectievakje naast de naam van de entiteit in te schakelen.

![Invoervelden aanpassen](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

**4. Geef uw model een naam en sla de configuratie op**

In de laatste stap kunt u het model een naam geven en Opslaan en trainen selecteren. Hiermee wordt begonnen met de training van het ML-model. U kunt ervoor kiezen om de trainingstijd te verkorten om snel resultaten te bekijken of de hoeveelheid tijd die wordt besteed aan training te vergroten om het beste model te krijgen.

![Uw model een naam geven](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

#### <a name="ml-model-training"></a>Training van ML-model

De training van AutoML-modellen vindt plaats tijdens het vernieuwen van een gegevensstroom. AutoML bereidt uw gegevens eerst voor op de training.
AutoML splitst de historische gegevens die u opgeeft in gegevenssets voor trainingsdoeleinden en voor testdoeleinden. De set voor testdoeleinden is een evaluatieset die wordt gebruikt om de modelprestaties na de training te valideren. Deze worden gerealiseerd als **Training- en Testing**-entiteiten in de gegevensstroom. AutoML maakt gebruik van kruisvalidatie voor de modelvalidatie.

Vervolgens wordt elk invoerveld geanalyseerd en wordt er imputatie toegepast, waarbij eventuele ontbrekende waarden worden vervangen door vervangende waarden. Er worden een aantal verschillende imputatiestrategieën gebruikt door AutoML. In het geval van invoerkenmerken die als numerieke functies worden behandeld, wordt voor de imputatie het gemiddelde van de kolomwaarden genomen. In het geval van invoerkenmerken die als categorische functies worden behandeld, gebruikt AutoML de modus van de kolomwaarden voor de imputatie. Het gemiddelde en de modus van de waarden die worden gebruikt voor de imputatie, worden berekend door het AutoML-framework in de subgegevensset voor een subsample van de training.

Daarna worden, zoals vereist, steekproeven en normalisatie toegepast op uw gegevens. In het geval van classificatiemodellen voert AutoML de invoergegevens uit door middel van gelaagde steekproeven en worden de klassen gebalanceerd om ervoor te zorgen dat het aantal rijen gelijk is.

AutoML past verschillende transformaties toe op elke geselecteerd invoerveld, op basis van het gegevenstype en de statistische eigenschappen van het veld. AutoML gebruikt deze transformaties voor het extraheren van functies die kunnen worden gebruikt bij het trainen van uw ML-model.

Het trainingsproces voor AutoML-modellen bestaat uit maximaal 50 iteraties met verschillende modelleringsalgoritmen en hyperparameter-instellingen om het model met de beste prestaties te vinden. De training kan eerder eindigen met minder iteraties als AutoML merkt dat er geen prestatieverbetering wordt waargenomen. De prestaties van elk van deze modellen worden beoordeeld door validatie aan de hand van de set met evaluatiegegevens. Tijdens deze trainingsstap maakt AutoML verschillende pijplijnen voor de training en validatie van deze iteraties. Het proces van het beoordelen van de prestaties van de modellen kan enige tijd duren, van enkele minuten tot enkele uren tot de trainingstijd die is geconfigureerd in de wizard, afhankelijk van de grootte van de gegevensset en de capaciteitsresources.

In sommige gevallen kan het uiteindelijke gegenereerde model gebruikmaken van 'ensemble learning', waarbij meerdere modellen worden gebruikt om betere voorspellende prestaties te bieden.

#### <a name="automl-model-explainability"></a>Verklaarbaarheid van AutoML-model

Nadat het model is getraind, analyseert AutoML de relatie tussen de invoerfuncties en de modeluitvoer. Daarnaast worden voor elke invoerfunctie de magnitude van de wijziging van de modeluitvoer beoordeeld voor de set met evaluatiegegevens. Dit staat bekend als de _functie-urgentie_. Dit gebeurt als onderdeel van het vernieuwen zodra de training is voltooid. Het vernieuwen kan daarom langer duren dan de trainingstijd die in de wizard is geconfigureerd.

![Functie-urgentie](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

#### <a name="automl-model-report"></a>Rapport voor AutoML-model

AutoML genereert een Power BI-rapport met een overzicht van de prestaties van het model tijdens validatie, samen met het belang van globale functies. Dit rapport is toegankelijk vanaf het tabblad Machine Learning-model wanneer het vernieuwen van de gegevensstroom is geslaagd. Het rapport geeft een overzicht van de resultaten van het toepassen van het ML-model op de testgegevens voor evaluatie en het vergelijken van de voorspellingen met de bekende resultaatwaarden.

U kunt het modelrapport bekijken om inzicht in de prestaties te krijgen. U kunt ook controleren of de belangrijkste beïnvloeders van het model overeenkomen met de zakelijke inzichten over de bekende resultaten.

De diagrammen en metingen die worden gebruikt om de prestaties van het model te beschrijven in het rapport, zijn afhankelijk van het modeltype. Deze prestatiediagrammen en metingen worden beschreven in de volgende secties.

Het rapport kan extra pagina's bevatten met statistische metingen van het model gezien vanuit het perspectief van de gegevenswetenschap. Zo bevat het rapport voor **binaire voorspellingen** bijvoorbeeld een toenamediagram en de ROC-curve voor het model.

De rapporten bevatten ook een pagina met **trainingsdetails** met een beschrijving van hoe het model is getraind en een diagram met een beschrijving van de modelprestaties voor elke iteratie.

![Trainingsdetails](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

In een andere sectie op deze pagina worden het gedetecteerde type van het invoerveld en de imputatiemethode die wordt gebruikt voor het vullen van ontbrekende waarden, beschreven. De pagina bevat ook de parameters die worden gebruikt door het uiteindelijke model.

![Meer informatie voor het model](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

Als het geproduceerde model gebruikmaakt van 'ensemble learning', bevat de pagina met **trainingsdetails** ook een grafiek met de weging van elk samenstellend model in het ensemble, samen met de bijbehorende parameters.

![Weging in het ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

### <a name="applying-the-automl-model"></a>Toepassen van AutoML-model

Als u tevreden bent met de prestaties van het gemaakte ML-model, kunt u het model toepassen op nieuwe of bijgewerkte gegevens wanneer uw gegevensstroom wordt vernieuwd. U kunt dit doen vanuit het modelrapport, door de knop **Toepassen** te selecteren in de rechterbovenhoek of de knop ML-model toepassen onder acties op het tabblad Machine Learning-modellen.

Om het ML-model toe te passen, geeft u de naam op van de entiteit waarop u het model wilt toepassen en een voorvoegsel voor de kolommen die aan deze entiteit worden toegevoegd voor de modeluitvoer. Het standaardvoorvoegsel voor de kolomnamen is de modelnaam. De functie _Apply_ kan aanvullende parameters bevatten die specifiek zijn voor het modeltype.

Door het ML-model toe te passen, worden twee nieuwe gegevensstroomentiteiten gemaakt die de voorspellingen en de individuele uitleg bevatten voor elke rij die in de uitvoerentiteit wordt gescoord. Als u bijvoorbeeld het model _PurchaseIntent_ toepast op de entiteit _OnlineShoppers_, worden de entiteiten **OnlineShoppers enriched PurchaseIntent** en **OnlineShoppers enriched PurchaseIntent explanations** gegenereerd. Voor elke rij in de verrijkte entiteit wordt de **Uitleg** opgesplitst in meerdere rijen in de entiteit met de verrijkte uitleg op basis van de invoerfunctie. Met een **ExplanationIndex** kunt u de rijen van de verrijkte uitlegentiteit toewijzen aan de rij in een verrijkte entiteit.

![Query-editor](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

U kunt ook elk gewenst Power BI AutoML-model toepassen op entiteiten in een willekeurige gegevensstroom in dezelfde werkruimte, met behulp van AI Insights in de PQO-functiebrowser. Op deze manier kunt u modellen die door anderen zijn gemaakt, gebruiken in dezelfde werkruimte, zonder u dat de eigenaar bent van de gegevensstroom die het model bevat. Met Power Query worden alle Power BI ML-modellen in de werkruimte gedetecteerd en weergegeven als dynamische Power Query-functies.  U kunt deze functies aanroepen door ze te openen vanuit het lint in de Power Query-editor, of door de ML-functie rechtstreeks aan te roepen. Deze functionaliteit wordt momenteel alleen ondersteund voor Power BI-gegevensstromen en voor Power Query Online in de Power BI-service. Houd er rekening mee dat dit verschilt van het toepassen van ML-modellen binnen een gegevensstroom met behulp van de AutoML-wizard. Er wordt bij het gebruik van deze methode geen entiteit voor toelichtingen gemaakt, en tenzij u de eigenaar van de gegevensstroom bent, hebt u geen toegang tot modeltrainingsrapporten en kunt u het model niet opnieuw trainen. Als het bronmodel wordt bewerkt (toevoegen of verwijderen van invoervelden), of als het model of de brongegevensstroom worden verwijderd, wordt deze afhankelijke gegevensstroom onderbroken.

![Een model toepassen met behulp van de PQO-functiebrowser](media/service-machine-learning-automated/automated-machine-learning-power-bi-20.png)

Nadat u het model hebt toegepast, zorgt AutoML ervoor dat uw voorspellingen altijd actueel zijn wanneer de gegevensstroom wordt vernieuwd.

Als u de inzichten en voorspellingen uit het ML-model wilt gebruiken in een Power BI-rapport, kunt u vanuit Power BI Desktop verbinding maken met de uitvoerentiteit met behulp van de connector **dataflows**.

### <a name="binary-prediction-models"></a>Modellen van het type Binaire voorspelling

Modellen van het type Binaire voorspelling, formeel ook bekend als **binaire classificatiemodellen**, worden gebruikt om een gegevensset in twee groepen te classificeren. Ze worden gebruikt om gebeurtenissen te voorspellen die een binaire uitkomst kunnen hebben. Bijvoorbeeld of een verkoopkans wordt geconverteerd, of een account wordt opgezegd, of een factuur op tijd wordt betaald, of een transactie frauduleus is, enzovoort.

De uitvoer van een binair voorspellingsmodel is een waarschijnlijkheidsscore, die de waarschijnlijkheid aangeeft dat het doelresultaat werkelijkheid zal worden.

#### <a name="training-a-binary-prediction-model"></a>Trainen van een binair voorspellingsmodel

Vereisten:

- Voor elke klasse met resultaten zijn minimaal 20 rijen met historische gegevens vereist

Het proces van het maken van een binair voorspellingsmodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven. Het enige verschil zit in de stap Een model kiezen, waarin u de waarde voor het doelresultaat kunt selecteren waarin u het meest geïnteresseerd bent. U kunt ook beschrijvende labels opgeven voor de resultaten die moeten worden gebruikt in het automatisch gegenereerde rapport waarin de resultaten van de modelvalidatie worden samengevat.

![Wizard Binaire voorspelling](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

#### <a name="binary-prediction-model-report"></a>Rapport voor binair voorspellingsmodel

Het binaire voorspellingsmodel produceert als uitvoer een waarschijnlijkheidsscore dat een record het doelresultaat bereikt. Het rapport bevat een slicer voor de waarschijnlijkheidsdrempel, die van invloed is op de manier waarop de scores boven en onder de drempel worden geïnterpreteerd.

In het rapport worden de prestaties van het model beschreven in termen van _terecht positieven (True Positives), fout-positieven (False Positives), terecht negatieven (True Negatives) en fout-negatieven (False Negatives)_. Terecht positieven en terecht negatieven zijn correct voorspelde resultaten voor de twee klassen in de resultaatgegevens. Fout-positieven zijn records waarvan is voorspeld dat ze het doelresultaat hebben, maar dat uiteindelijk niet hebben. Fout-negatieven zijn daarentegen records die het doelresultaat hadden, maar waarvan werd voorspeld dat ze dat niet zouden hebben.

Metingen, zoals Precisie en Terughalen, beschrijven het effect van de waarschijnlijkheidsdrempel op de voorspelde resultaten. U kunt de slicer met de waarschijnlijkheidsdrempel gebruiken om een drempel te selecteren die een compromis oplevert tussen Precisie en Terughalen.

![Voorbeeld van nauwkeurigheid](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

Het rapport bevat ook een hulpprogramma voor een kosten-batenanalyse waarmee u de subset van de populatie kunt identificeren waarop moet worden ingezet om de hoogste winst te krijgen. Aan de hand van de geschatte kosten per eenheid en een eenheidsvoordeel door het bereiken van een doelresultaat, wordt getracht met de kosten-batenanalyse de winst te maximaliseren. U kunt dit hulpprogramma gebruiken om uw waarschijnlijkheidsdrempelwaarde te kiezen op basis van het maximumpunt in de grafiek om de winst te maximaliseren. U kunt de grafiek ook gebruiken om de winst of kosten voor uw keuze van de waarschijnlijkheidsdrempelwaarde te berekenen.

![Kosten/baten](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

De pagina **Nauwkeurigheidsrapport** van het modelrapport bevat het diagram _Cumulatieve toenames_ en de ROC-curve voor het model. Dit zijn statistische metingen van modelprestaties. De rapporten bevatten beschrijvingen van de weergegeven diagrammen.

![Scherm met nauwkeurigheidsrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

#### <a name="applying-a-binary-prediction-model"></a>Een binair voorspellingsmodel toepassen

Als u een binair voorspellingsmodel wilt toepassen, moet u de entiteit opgeven die de gegevens bevat waarop u de voorspellingen uit het ML-model wilt toepassen. Andere parameters zijn het voorvoegsel voor de naam van de uitvoerkolom en de waarschijnlijkheidsdrempel voor het classificeren van het voorspelde resultaat.

![Voorspellingsinvoer](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

Bij het toepassen van een binair voorspellingsmodel, worden er vier uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer: **Outcome**, **PredictionScore**, **PredictionExplanation** en **ExplanationIndex**. Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

**PredictionScore** is een waarschijnlijkheidspercentage waarmee de waarschijnlijkheid wordt aangegeven dat het doelresultaat werkelijkheid zal worden.

De kolom **Outcome** bevat het label voor het voorspelde resultaat. Als records waarschijnlijkheidsscores hebben die de drempel overschrijden, wordt voorspeld dat ze het doelresultaat waarschijnlijk behalen en krijgen ze het label Waar. Van records onder de drempelwaarde wordt voorspeld dat het onwaarschijnlijk is dat ze het resultaat kunnen bereiken; deze krijgen het label Onwaar.

De kolom **PredictionExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **PredictionScore**.

### <a name="classification-models"></a>Classificatiemodellen

Classificatiemodellen worden gebruikt om een gegevensset in meerdere groepen of klassen te classificeren. Ze worden gebruikt om gebeurtenissen te voorspellen die een van de verschillende mogelijke resultaten kunnen hebben. Bijvoorbeeld of een klant waarschijnlijk een zeer hoge, hoge, gemiddelde of lage levensduur heeft, of het risico voor betalingsverzuim hoog, gemiddeld, laag of zeer laag is, enzovoort.

De uitvoer van een classificatiemodel is een waarschijnlijkheidsscore die de kans aangeeft of een record de criteria voor een bepaalde klasse gaat behalen.

#### <a name="training-a-classification-model"></a>Trainen van een classificatiemodel

De invoerentiteit met de trainingsgegevens voor een classificatiemodel moet een tekstveld of heel numeriek veld bevatten als het resultaatveld, waarin de eerdere bekende resultaten worden geïdentificeerd.

Vereisten:

- Voor elke klasse met resultaten zijn minimaal 20 rijen met historische gegevens vereist

Het proces van het maken van een binair classificatiemodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven.

#### <a name="classification-model-report"></a>Rapport voor classificatiemodel

Het rapport voor een classificatiemodel wordt geproduceerd door het ML-model toe te passen op de evaluatiegegevens en de voorspelde klasse voor een record te vergelijken met de daadwerkelijk bekende klasse.

Het modelrapport bevat een diagram met een uitsplitsing van de juist en onjuist geclassificeerde records voor elke bekende klasse.

![Modelrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-17.png)

U kunt verder inzoomen op een bepaalde klasse om een analyse mogelijk te maken van de manier waarop de voorspellingen voor een bekende klasse worden gedistribueerd. Dit geeft de andere klassen aan waarin records van die bekende klasse naar alle waarschijnlijkheid onjuist worden geclassificeerd.

De toelichting van het model in het rapport bevat ook de belangrijkste voorspellingsfactoren voor elke klasse.

Het rapport voor het classificatiemodel bevat ook een pagina met trainingsdetails die vergelijkbaar is met de pagina's voor andere modeltypen, zoals wordt beschreven in het gedeelte **Rapport voor AutoML-model** eerder in dit artikel.

#### <a name="applying-a-classification-model"></a>Toepassen van een classificatiemodel

Als u een classificatiemodel wilt toepassen, moet u de entiteit opgeven met de invoergegevens en het voorvoegsel voor de naam van de uitvoerkolom.

Bij het toepassen van een classificatiemodel worden er vijf uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer: **ClassificationScore**, **ClassificationResult**, **ClassificationExplanation**, **ClassProbabilities** en **ExplanationIndex**. Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

De kolom **ClassProbabilities** bevat de lijst met waarschijnlijkheidsscores voor de record voor elke mogelijke klasse.

De **ClassificationScore** is een waarschijnlijkheidspercentage dat de kans aangeeft of een record de criteria voor een bepaalde klasse gaat behalen.

De kolom **ClassificationResult** bevat de meest waarschijnlijke voorspelde klasse voor de record.

De kolom **ClassificationExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **ClassificationScore**.

### <a name="regression-models"></a>Regressiemodellen

Regressiemodellen worden gebruikt om een numerieke waarde te voorspellen. Bijvoorbeeld: de omzet die waarschijnlijk zal worden gerealiseerd met een verkoop, de levensduur van een account, het bedrag van een factuur die waarschijnlijk zal worden betaald, de datum waarop een factuur kan worden betaald, enzovoort.

De uitvoer van een regressiemodel is de voorspelde waarde.

#### <a name="training-a-regression-model"></a>Trainen van een regressiemodel

De invoerentiteit met de trainingsgegevens voor een regressiemodel moet een numeriek veld bevatten als het resultaatveld, dat de bekende resultaatwaarden identificeert.

Vereisten:

- Voor een regressiemodel zijn minimaal 100 rijen met historische gegevens vereist

Het proces van het maken van een regressiemodel bestaat uit dezelfde stappen als voor andere AutoML modellen, zoals wordt beschreven in het gedeelte **Invoer voor ML-model configureren** hierboven.

#### <a name="regression-model-report"></a>Rapport van regressiemodel

Net als de andere AutoML-modelrapporten, wordt het regressierapport gebaseerd op de resultaten van het toepassen van het model op de evaluatiegegevens.

Het modelrapport bevat een diagram waarin de voorspelde waarden worden vergeleken met de werkelijke waarden. In dit diagram geeft de afstand vanaf de diagonaal de fout in de voorspelling aan.

In het diagram met resterende fouten ziet u de verdeling van het percentage van gemiddelde fouten voor verschillende waarden in de set met evaluatiegegevens. De horizontale as vertegenwoordigt het gemiddelde van de werkelijke waarde voor de groep, waarbij de grootte van de bel de frequentie of het aantal waarden in dat bereik aangeeft. De verticale as vertegenwoordigt de gemiddelde restfouten.

![Diagram met restfouten](media/service-machine-learning-automated/automated-machine-learning-power-bi-18.png)

Het rapport voor het regressiemodel bevat ook een pagina met trainingsdetails, net zoals de rapporten voor andere modeltypen, zoals wordt beschreven in het gedeelte **Rapport voor AutoML-model** eerder in dit artikel.

#### <a name="applying-a-regression-model"></a>Toepassen van een regressiemodel

Als u een regressiemodel wilt toepassen, moet u de entiteit opgeven met de invoergegevens en het voorvoegsel voor de naam van de uitvoerkolom.

![Een regressie toepassen](media/service-machine-learning-automated/automated-machine-learning-power-bi-19.png)

Bij het toepassen van een regressiemodel worden er drie uitvoerkolommen toegevoegd aan de entiteit met verrijkte uitvoer: **RegressionResult**, **RegressionExplanation** en **ExplanationIndex**. Het voorvoegsel voor de kolomnamen in de entiteit wordt opgegeven bij het toepassen van het model.

De kolom **RegressionResult** bevat de voorspelde waarde voor de record op basis van de invoervelden. De kolom **RegressionExplanation** bevat een uitleg met de specifieke invloed van de invoerfuncties op de **RegressionResult**.

## <a name="azure-machine-learning-integration-in-power-bi"></a>Azure Machine Learning-integratie in Power BI

Talloze organisaties gebruiken **Machine Learning-modellen** voor beter inzicht in en nauwkeurige voorspellingen over hun bedrijf. De mogelijkheid om deze modellen te visualiseren in uw rapporten, dashboards en andere analyses en daar inzicht uit op te doen, helpt deze inzichten te verspreiden onder gebruikers in het bedrijf die daar het meest behoefte aan hebben.  Power BI maakt het nu gemakkelijk om de inzichten van modellen in Azure Machine Learning te gebruiken en doet dat aan de hand van eenvoudige muisbewegingen en -acties.

Een gegevenswetenschapper kan om deze mogelijkheid te gebruiken de BI-analist eenvoudigweg toegang geven tot het Azure ML-model met behulp van de Azure-portal.  Vervolgens ontdekt Power Query aan het begin van elke sessie alle modellen waar de gebruiker toegang tot heeft en weergeeft deze als dynamische Power Query-functies.  De gebruiker roept deze functies vervolgens aan door ze te openen vanuit het lint in Power Query-editor, of door de ML-functie rechtstreeks aan te roepen. Ook voegt Power BI toegangsaanvragen automatisch samen wanneer het Azure ML-model wordt aangeroepen voor een set rijen en dat zorgt voor betere prestaties.

Deze functionaliteit wordt momenteel alleen ondersteund voor Power BI-gegevensstromen en voor Power Query online in de Power BI-service.

Zie [Inleiding tot gegevensstromen en selfservice voor gegevensvoorbereiding](dataflows-introduction-self-service.md) voor meer informatie over gegevensstromen.

Voor meer informatie over Azure Machine Learning raadpleegt u:

- Overzicht:  [Wat is Azure Machine Learning?](/azure/machine-learning/service/overview-what-is-azure-ml)
- Quick Starts en zelfstudies voor Azure Machine Learning:  [Documentatie voor Azure Machine Learning](/azure/machine-learning/)

> [!NOTE]
> Een Power BI Premium-abonnement is vereist voor het gebruik van de Azure Machine Learning-integratie.

### <a name="granting-access-to-the-azure-ml-model-to-a-power-bi-user"></a>Een Power BI-gebruiker toegang geven tot het Azure ML-model

Als een gebruiker toegang wil tot een Azure ML-model vanuit Power BI, moet deze **leestoegang** hebben tot het Azure-abonnement.  Daarnaast:

- **Leestoegang** tot de Machine Learning Studio-webservice (klassiek) voor Machine Learning Studio-modellen (klassiek)
- **Leestoegang** tot de Machine Learning-werkruimte voor Machine Learning-modellen

In de stappen in dit artikel wordt beschreven hoe een Power BI-gebruiker toegang krijgt tot een model in de Azure ML-service, zodat ze toegang hebben tot dit model als een Power Query-functie.  Voor meer informatie raadpleegt u [Toegang beheren met RBAC en de Azure-portal](/azure/role-based-access-control/role-assignments-portal).

1. Meld u aan bij [Azure Portal](https://portal.azure.com).

2. Ga naar de pagina **Abonnementen**. U vindt de pagina **Abonnementen** via de lijst **Alle services** in het navigatievenstermenu van de Azure-portal.

    [ ![Pagina met Azure-abonnementen](media/service-machine-learning-integration/machine-learning-integration-01.png) ](media/service-machine-learning-integration/machine-learning-integration-01.png#lightbox)

3. Selecteer uw abonnement.

    [ ![Uw abonnement selecteren](media/service-machine-learning-integration/machine-learning-integration-02.png) ](media/service-machine-learning-integration/machine-learning-integration-02.png#lightbox)

4. Selecteer **Toegangsbeheer (IAM)** en vervolgens de knop **Toevoegen**.

    [ ![Toegangsbeheer IAM](media/service-machine-learning-integration/machine-learning-integration-03.png) ](media/service-machine-learning-integration/machine-learning-integration-03.png#lightbox)

5. Selecteer **Lezer** als de rol. Selecteer de Power BI-gebruiker die u toegang wilt geven tot het Azure ML-model.

    [ ![Lezer selecteren als de rol](media/service-machine-learning-integration/machine-learning-integration-04.png) ](media/service-machine-learning-integration/machine-learning-integration-04.png#lightbox)

6. Selecteer **Opslaan**.

7. Herhaal stap drie tot en met zes om **leestoegang** te verlenen aan de gebruiker voor de specifieke Machine Learning Studio-webservice (klassiek) *of* de Machine Learning-werkruimte waarin het model wordt gehost.

### <a name="schema-discovery-for-machine-learning-models"></a>Schemadetectie voor Machine Learning-modellen

Gegevenswetenschappers gebruiken voornamelijk Python om hun machine learning-modellen voor Machine Learning te ontwikkelen en zelfs te implementeren.  In tegenstelling tot de Machine Learning Studio (klassiek), waarmee de taak voor het maken van een schemabestand kan worden geautomatiseerd, moet de gegevenswetenschapper in het geval van Machine Learning het schemabestand expliciet genereren met Python.

Dit schemabestand moet worden opgenomen in de geïmplementeerde webservice voor Machine Learning-modellen. Als u wilt dat het schema voor de webservice automatisch wordt geautomatiseerd, moet u een voorbeeld opgeven van de invoer/uitvoer in het script van de vermelding voor het geïmplementeerd model. Zie de subsectie over het [(optioneel) automatisch genereren van Swagger-schema's in de implementatiemodellen met de Azure Machine Learning Service-documentatie](/azure/machine-learning/how-to-deploy-and-where#optional-define-model-web-service-schema). De koppeling bevat het voorbeeldscript van de vermelding met de instructies voor het genereren van schema's. 

Met name de functies *\@input_schema* en *\@output_schema* in het script van de vermelding verwijzen naar de voorbeeldindelingen van invoer en uitvoer in de variabelen *input_sample* en *output_sample* en genereren met behulp van deze voorbeelden een OpenAPI-specificatie (Swagger) voor de webservice tijdens de implementatie.

Deze instructies voor het genereren van schema's door het bijwerken van het script van de vermelding moeten ook worden toegepast op modellen die zijn gemaakt met behulp van geautomatiseerde Machine Learning-experimenten via de Azure Machine Learning-SDK.

> [!NOTE]
> Modellen die zijn gemaakt met behulp van de visuele interface van Azure Machine Learning bieden momenteel geen ondersteuning voor het genereren van schema's, maar dat zal in toekomstige releases wel het geval zijn. 

### <a name="invoking-the-azure-ml-model-in-power-bi"></a>Azure ML-model aanroepen in Power BI

U kunt elk Azure ML-model waar u toegang tot hebt rechtstreeks aanroepen vanuit de Power Query-editor in uw gegevensstroom. Als u toegang wilt tot de Azure ML-modellen, selecteert u de knop **Bewerken** voor de entiteit die u wilt opmaken met inzichten uit uw Azure ML-model, zoals wordt weergegeven in de volgende afbeelding.

[ ![Power BI-service - de entiteit bewerken](media/service-machine-learning-integration/machine-learning-integration-05.png) ](media/service-machine-learning-integration/machine-learning-integration-05.png#lightbox)

Als u de knop **Bewerken** selecteert, wordt de Power Query-editor geopend voor de entiteiten in uw gegevensstroom.

[ ![Power Query-editor](media/service-machine-learning-integration/machine-learning-integration-06.png) ](media/service-machine-learning-integration/machine-learning-integration-06.png#lightbox)

Selecteer in het lint de knop **AI-inzichten** en selecteer vervolgens de map _Azure Machine Learning-modellen_ in het navigatievenstermenu. Alle Azure ML-modellen waar u toegang tot hebt, zijn hier vermeld als Power Query-functies. De invoerparameters voor het Azure ML-model worden automatisch toegewezen als parameters van de bijbehorende Power Query-functie.

Als u een Azure ML-model wilt aanroepen, kunt u vanuit het vervolgkeuzemenu een van de geselecteerde kolommen van de entiteit als invoer opgeven. U kunt ook een constante waarde opgeven die als invoer wordt gebruikt door het kolompictogram aan de linkerzijde van de het invoerdialoogvenster in te schakelen.

[ ![de kolom selecteren](media/service-machine-learning-integration/machine-learning-integration-07.png) ](media/service-machine-learning-integration/machine-learning-integration-07.png#lightbox)

Selecteer **Aanroepen** om een voorbeeld van de uitvoer van het Azure ML-model weer te geven als een nieuwe kolom in de entiteitstabel. U ziet de aanroep aan het model ook als een toegepaste stap voor de query.

[ ![Aanroep selecteren](media/service-machine-learning-integration/machine-learning-integration-08.png) ](media/service-machine-learning-integration/machine-learning-integration-08.png#lightbox)

Als het model meerdere uitvoerparameters retourneert, worden ze gegroepeerd als een record in de uitvoerkolom. U kunt een kolom uitbreiden om afzonderlijke uitvoerparameters te produceren in afzonderlijke kolommen.

[ ![de kolom uitbreiden](media/service-machine-learning-integration/machine-learning-integration-09.png) ](media/service-machine-learning-integration/machine-learning-integration-09.png#lightbox)

Nadat u uw gegevensstroom hebt opgeslagen, wordt het model automatisch aangeroepen wanneer de gegevensstroom wordt vernieuwd voor nieuwe of bijgewerkte rijen in de entiteitstabel.

## <a name="next-steps"></a>Volgende stappen

In dit artikel hebt u een overzicht van geautomatiseerde machine learning voor gegevensstromen in de Power BI-service. De volgende artikelen kunnen ook van pas komen.

- [Zelfstudie: Een machine learning-model bouwen in Power BI ](../../connect-data/service-tutorial-build-machine-learning-model.md)
- [Zelfstudie: Cognitive Services gebruiken in Power BI](../../connect-data/service-tutorial-use-cognitive-services.md)
- [Zelfstudie: Een Machine Learning Studio-model (klassiek) aanroepen in Power BI (preview)](../../connect-data/service-tutorial-invoke-machine-learning-model.md)

De volgende artikelen bieden meer informatie over gegevensstromen en Power BI:

* [Inleiding tot gegevensstromen en selfservice voor gegevensvoorbereiding](dataflows-introduction-self-service.md)
* [Een gegevensstroom maken](dataflows-create.md)
* [Een gegevensstroom configureren en gebruiken](dataflows-configure-consume.md)
* [Gegevensstroomopslag configureren voor gebruik van Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Premium-functies van gegevensstromen](dataflows-premium-features.md)
* [Beperkingen en overwegingen van gegevensstromen](dataflows-features-limitations.md)
* [Best practices voor gegevensstromen](dataflows-best-practices.md)