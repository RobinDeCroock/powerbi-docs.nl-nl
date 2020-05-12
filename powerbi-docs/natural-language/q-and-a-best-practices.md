---
title: Best practices om Q&A te optimaliseren
description: Instructies voor het optimaliseren van Q&A in Power BI en het verbeteren van de prestaties
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: mohaali
ms.openlocfilehash: b5865219d84c8fa388f297824550fd715f0c2923
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866840"
---
# <a name="best-practices-to-optimize-qa-in-power-bi"></a>Best practices om Q&A in Power BI te optimaliseren
Normale zinnen en natuurlijke taal gebruiken om informatie uit uw gegevens te kunnen opvragen, is uiterst nuttig. Nog nuttiger is het wanneer uw gegevens antwoorden. Dit is wat u met Q&A in Power BI kunt doen.

Als u met Q&A het grote aantal vragen wilt interpreteren waarop de functie kan reageren, moet u met Q&A veronderstellingen over het model maken. Als de structuur van uw model niet voldoet aan een of meer van deze veronderstellingen, moet u het model aanpassen. Voor deze aanpassingen voor Q&A gebruikt u voor elk model in Power BI dezelfde optimalisaties voor aanbevolen procedures, ongeacht of u Q&A gebruikt.

In de volgende secties wordt beschreven hoe u uw model aanpast zodat dit goed samenwerkt met Q&A in Power BI.

## <a name="automatic-adjustments-that-qa-makes"></a>Automatische aanpassingen die door Q&A worden doorgevoerd

### <a name="measure-tables"></a>Meettabellen

In eerdere versies van Q&A konden meettabellen verwarrend werken in Q&A aangezien de onderliggende tabel was losgekoppeld. Q&A werkt nu prima met meettabellen.

### <a name="table-names-conflicting-with-column-names"></a>Conflicten tussen tabelnamen en kolomnamen

Als een tabel en een kolom in eerdere versies van Q&A dezelfde naam hadden, kreeg de tabel hogere prioriteit. Dit probleem is nu aangepakt, dus u hoeft dit probleem in uw modellen niet meer zelf op te lossen.

## <a name="manual-steps-to-improve-qa"></a>Handmatige stappen voor het verbeteren van Q&A

### <a name="use-the-new-qa-tooling-to-fix-your-questions"></a>Het nieuwe Q&A-hulpprogramma gebruiken om uw vragen te beantwoorden

Met het Q&A-hulpprogramma kunt u uw belangrijkste zakelijke voorwaarden voor Q&A trainen en vragen van eindgebruikers beantwoorden. In sommige gevallen kan een aantal vragen nog steeds niet worden beantwoord omdat de gegevens niet de juiste vorm hebben of omdat gegevens ontbreken. In dit geval leest u de andere secties hieronder om u bij de optimalisatie te helpen. Lees meer over het [Q&A-hulpprogramma](q-and-a-tooling-intro.md).

## <a name="add-missing-relationships"></a>Ontbrekende relaties toevoegen

Als in uw model relaties tussen tabellen ontbreken, kunt u noch met Power BI-rapporten noch met Q&A interpreteren hoe deze tabellen moeten worden samengevoegd. Relaties vormen de basis van een goed model. U kunt bijvoorbeeld geen vragen stellen over de 'totale verkoop voor klanten in Amsterdam' als de relatie tussen de tabel *bestellingen* en de tabel *klanten* ontbreekt. In de volgende afbeeldingen ziet u een model waarvoor nog actie is vereist en een model dat gereed is voor Q&A. 

**Actie vereist**

In de eerste afbeelding zijn er geen relaties tussen de tabellen Klanten, Verkoop en Producten.

![Relaties waarvoor actie is vereist voor Q&A](media/q-and-a-best-practices/desktop-qna-01.png)

**Gereed voor Q&A**

In de eerste afbeelding worden relaties gedefinieerd tussen de tabellen.

![relaties in orde voor Q&A](media/q-and-a-best-practices/desktop-qna-02.png)


## <a name="rename-tables-and-columns"></a>De naam van tabellen en kolommen wijzigen

De keuze van tabellen en kolommen is belangrijk voor Q&A. Stel dat u een tabel hebt met de naam *CustomerSummary*. Deze bevat een lijst met uw klanten. U zou vragen moeten stellen als 'Vermeld de klantoverzichten in Rotterdam' in plaats van 'Vermeld de klanten in Rotterdam'. 

Met Q&A kunt u enkele eenvoudige analyses van woorden en detectie van meervouden uitvoeren. Q&A gaat er echter van uit dat uw tabel- en kolomnamen een goed beeld vormen van de inhoud ervan.

Kijk nu eens naar een ander voorbeeld. Stel dat u een tabel hebt met de naam *Personeelsbestand*, die voor- en achternamen en werknemernummers bevat. Stel dat u nog een tabel hebt, *Werknemers*, die werknemernummers, taaknummers en begindatums bevat. Wie met het model bekend is, weet hoe deze structuur in elkaar zit. Als iemand anders vraagt 'tel de werknemers', dan krijgt hij of zij een telling van het aantal rijen in de tabel Werknemers. Het resultaat is waarschijnlijk niet wat er werd bedoeld, omdat het een telling is van elke taak die elke werknemer ooit heeft gehad. Het is beter om de naam van de tabellen te wijzigen zodat deze de gegevens weergeven die ze daadwerkelijk bevatten.

**Actie vereist**

Voor tabelnamen zoals *StoreInfo* en *Product List* is actie vereist.

![Tabelnamen waarvoor actie is vereist voor Q&A](media/q-and-a-best-practices/desktop-qna-03.png)

**Gereed voor Q&A**

Tabellen met de naam *Store* en *Producten* werken beter.

![Tabelnamen in orde voor Q&A](media/q-and-a-best-practices/desktop-qna-04.png)

## <a name="fix-incorrect-data-types"></a>Onjuiste gegevenstypen corrigeren

Geïmporteerde gegevens kunnen ongeldige gegevenstypen hebben. Met name kolommen met *datum* en *aantal* die worden geïmporteerd als *reeksen*, worden niet door Q&A geïnterpreteerd als datums en aantallen. Zorg ervoor dat u het juiste gegevenstype selecteert in uw Power BI-model.

![Het juiste gegevenstype kiezen zodat dit beschikbaar is voor Q&A](media/q-and-a-best-practices/desktop-qna-05.png)

## <a name="mark-year-and-identifier-columns-as-dont-summarize"></a>Jaar- en id-kolommen markeren als Niet samenvatten

Power BI aggregeert numerieke kolommen standaard op agressieve wijze, zodat vragen als 'totale verkoop per jaar' soms kan resulteren in zowel een totaal van verkopen als een totaal van jaren. Als u specifieke kolommen hebt waarin u niet wilt dat Power BI dit gedrag vertoont, stelt u de eigenschap **Standaardoverzicht** van de kolom in op **Niet samenvatten**. Let goed op met kolommen voor **jaar**, **maand**, **dag** en **Id**, aangezien deze kolommen het vaakst problemen opleveren. Ook voor andere kolommen met gegevens die minder gevoelig zijn voor optellen, zoals *leeftijd*, kan het gunstig zijn om **Standaardoverzicht** in te stellen op **Niet samenvatten** of **Gemiddeld**. U vindt deze instelling op het tabblad **Model maken**.

![Kolommen niet samenvatten voor Q&A als deze gegevens bevatten voor jaar, maand en dag](media/q-and-a-best-practices/desktop-qna-06.png)

## <a name="choose-a-data-category-for-each-date-and-geography-column"></a>Een gegevenscategorie kiezen voor elke datum- en geografiekolom

De **gegevenscategorie** biedt aanvullende semantische kennis over de inhoud van een kolom afgezien van het gegevenstype. U kunt bijvoorbeeld een kolom met gehele getallen markeren als een postcode, een tekenreekskolom als een stad, land/regio, enzovoort. Deze informatie wordt door Q&A op twee belangrijke manieren gebruikt: Voor selectie van visualisaties en voor taalvooroordelen.

Ten eerste gebruikt Q&A de informatie in de **gegevenscategorie** om te bepalen op welke manier de visuals moeten worden weergegeven. De functie herkent bijvoorbeeld dat kolommen met de **gegevenscategorieën** voor datum of tijd meestal een goede keuze vormen voor de horizontale as van een lijndiagram of de afspeelas van een bellendiagram. De functie gaat tevens ervan uit dat resultaten met kolommen met geografische **gegevenscategorieën** op een kaart goed overkomen.

Ten tweede kan met Q&A redelijk goed worden ingeschat hoe gebruikers waarschijnlijk zullen praten over datum- en geografiekolommen. Hierdoor kan de functie bepaalde soorten vragen beter begrijpen. Bijvoorbeeld het woord 'wanneer' in de vraag 'Wanneer is Jan Smit in dienst gekomen?' kan bijna zeker worden toegewezen aan een datumkolom en het woord 'Brown' in 'Aantal klanten in Brown' slaat waarschijnlijk op de Amerikaanse plaats Brown, in plaats van op een haarkleur.

![Gegevenscategorieën kiezen die geschikt zijn voor Q&A](media/q-and-a-best-practices/desktop-qna-07.png)

## <a name="choose-a-sort-by-column-for-relevant-columns"></a>De optie Op kolom sorteren kiezen voor relevante kolommen

Met de eigenschap **Op kolom sorteren** kunt u sorteren op één kolom, zodat in plaats daarvan automatisch op een andere kolom kan worden gesorteerd. Wanneer u bijvoorbeeld vraagt 'klanten sorteren op overhemdgrootte', wilt u waarschijnlijk uw kolom Overhemdgrootte sorteren op de onderliggende grootten (XS, S, M, L, XL) in plaats van alfabetisch (L, M, S, XL, XS).

![Kies Op kolom sorteren die past bij Q&A](media/q-and-a-best-practices/desktop-qna-08.png)

## <a name="normalize-your-model"></a>Het model normaliseren

Schrik niet, dit betekent niet dat u uw gehele model moet aanpassen. Bepaalde structuren zijn echter zo ingewikkeld dat Q&A ze niet goed verwerkt. Als u eenvoudige normalisering uitvoert op de structuur van uw model, neemt de bruikbaarheid van Power BI-rapporten aanzienlijk toe, evenals de nauwkeurigheid van de resultaten van Q&A.

Volg deze algemene regel: Elk uniek 'ding' waarover de gebruiker spreekt, moet worden voorgesteld door precies één modelobject (tabel of kolom). Als uw gebruikers over klanten communiceren, moet er dus slechts één object *Klant* zijn. Als uw gebruikers over verkoop communiceren, moet er dus slechts één object *Verkoop* zijn. Klinkt eenvoudig, of niet? Afhankelijk van de vorm van de gegevens waarmee u begint, kan het inderdaad eenvoudig zijn. In **Query-editor** zijn uitgebreide mogelijkheden beschikbaar voor het vormgeven van gegevens. Voor eenvoudigere transformaties kunt u berekeningen gebruiken in het Power BI-model.

De volgende secties bevatten enkele algemene transformaties die u kunt uitvoeren.

### <a name="create-new-tables-for-multi-column-entities"></a>Nieuwe tabellen maken voor entiteiten met meerdere kolommen

Als u meerdere kolommen hebt die als een afzonderlijke eenheid binnen een grotere tabel fungeren, moeten deze kolommen worden opgesplitst in hun eigen tabel. Stel dat u een naam, een titel en een telefoonnummer van een contactpersoon in uw tabel *Bedrijven* hebt. Het zou beter zijn om een aparte tabel *Contactpersonen* te hebben die de naam, de titel en het telefoonnummer bevat, en tevens een koppeling naar de tabel *Bedrijven*. Op deze manier wordt het eenvoudiger om vragen te stellen over contactpersonen zonder vragen te stellen over de bedrijven waarvoor zij de contactpersoon zijn. Hiermee verbetert u de flexibiliteit van de weergave.

**Actie vereist**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-09.png)

**Gereed voor Q&A**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-10.png)

### <a name="pivot-to-eliminate-property-bags"></a>Draaien om eigenschappenverzamelingen te elimineren

Als uw model *eigenschappenverzamelingen* bevat, moeten deze opnieuw worden gestructureerd zodat ze één kolom per eigenschap bevatten. Eigenschappenverzamelingen zijn wellicht handig voor het beheren van grote aantallen eigenschappen, maar veroorzaken ook een aantal beperkingen waarmee zowel Power BI-rapporten als Q&A niet overweg kan.

Neem bijvoorbeeld een tabel *KlantenDemografie* met de kolommen Klant-id, Eigenschap en Waarde, waarbij elke rij een andere eigenschap van de klant bevat (bijvoorbeeld, leeftijd, huwelijkse staat, plaats enzovoort). Door overbelasting van de betekenis van de kolom Waarde op basis van de inhoud van de kolom Eigenschap wordt het voor Q&A onmogelijk om de meeste query's te interpreteren die ernaar verwijzen. Eenvoudige vragen zoals 'toon de leeftijd van elke klant' leveren mogelijk een zinnig antwoord op, omdat dit kan worden geïnterpreteerd als 'toon de klanten en demografische klantgegevens waarbij de eigenschap Leeftijd is'. De structuur van het model ondersteunt echter geen complexere vragen zoals 'gemiddelde leeftijd van klanten in Chicago'. Hoewel gebruikers die rechtstreeks in Power BI-rapporten werken soms met slim zoekwerk de gewenste gegevens kunnen vinden, werkt Q&A alleen wanneer voor elke kolom slechts één betekenis wordt gebruikt.

**Actie vereist**

![Gebruik geen eigenschappenverzamelingen in modellen voor Q&A](media/q-and-a-best-practices/desktop-qna-11.png)

**Gereed voor Q&A**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-12.png)

### <a name="union-to-eliminate-partitioning"></a>Samenvoegen om partitioneren te elimineren

Als u uw gegevens hebt gepartitioneerd over meerdere tabellen, of waarden hebt gedraaid in meerdere kolommen, kan een aantal algemene bewerkingen voor uw gebruikers moeilijk of zelfs onmogelijk worden. Voer eerst standaardtabelpartities door: een tabel *Verkoop2000-2010* en een tabel *Verkoop2011-2020*. Als al uw belangrijke rapporten zijn beperkt tot een specifiek decennium, kunt u dit waarschijnlijk zo laten voor Power BI-rapporten. Door de flexibiliteit van Q&A verwachten uw gebruikers echter mogelijk antwoorden op vragen als 'totale verkoop per jaar'. Om deze query te kunnen uitvoeren, moet u de gegevens samenvoegen in één Power BI-modeltabel.

Kijk op dezelfde manier eens naar een gedraaide waardenkolom: een tabel *BookTour* met de kolommen Auteur, Adresboek, Plaats1, Plaats2 en Plaats3. Met een dergelijke structuur kunnen zelfs eenvoudige vragen als 'aantal boeken per plaats tellen' niet correct worden geïnterpreteerd. Om deze query te laten uitvoeren, maakt u een afzonderlijke tabel *BookTourCities*, waarin de plaatswaarden zijn samengevoegd in één kolom.

**Actie vereist**

![Gebruik geen gedraaide waardekolommen in modellen voor Q&A](media/q-and-a-best-practices/desktop-qna-13.png)

**Gereed voor Q&A**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-14.png)

### <a name="split-formatted-columns"></a>Opgemaakte kolommen splitsen

Als de bron van waaruit u uw gegevens wilt importeren opgemaakte kolommen bevat, kunnen Power BI-rapporten en Q&A niet in de kolom lezen om de inhoud ervan te parseren. Als u bijvoorbeeld een kolom **Volledig adres** hebt met het adres, de plaats en het land, moet u deze splitsen in kolommen met het adres, de plaats en het land, zodat uw gebruikers query’s kunnen uitvoeren op de afzonderlijke gegevens.

**Actie vereist**

![Gebruik geen enkele kolommen voor meerdere gegevenselementen voor Q&A](media/q-and-a-best-practices/desktop-qna-15.png)

**Gereed voor Q&A**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-16.png)

Als u soortgelijke kolommen hebt met de volledige naam van een persoon, moet u kolommen toevoegen met **Voornaam** en **Achternaam**, voor het geval iemand vragen stelt met betrekking tot gedeelten van namen. 


### <a name="create-new-tables-for-multi-value-columns"></a>Nieuwe tabellen maken voor kolommen met meerdere waarden

Als in een soortgelijke situatie de bron van waaruit u uw gegevens wilt importeren kolommen met meerdere waarden bevat, kunnen Power BI-rapporten en Q&A niet in de kolom lezen om de inhoud ervan te parseren. Als u bijvoorbeeld een kolom Componist hebt die de namen van meerdere componisten voor een nummer bevat, moet u deze opsplitsen in meerdere rijen in een afzonderlijke tabel *Componisten*.

**Actie vereist**

![Gebruik geen kolommen met meerdere waarden voor Q&A](media/q-and-a-best-practices/desktop-qna-17.png)

**Gereed voor Q&A**

![Meerdere tabellen voor Q&A gebruiken](media/q-and-a-best-practices/desktop-qna-18.png)

### <a name="denormalize-to-eliminate-inactive-relationships"></a>Denormaliseren om inactieve relaties te elimineren

De enige uitzondering op de regel 'normalisatie is beter' treedt op wanneer er meerdere manieren zijn om van de ene tabel naar de andere te gaan. Stel dat u een tabel met *Vluchten* hebt, met kolommen voor zowel BronStad-id als DoelStad-id, die elk zijn verbonden met de tabel *Steden*. Een van deze relaties moet worden gemarkeerd als niet-actief. Aangezien met Q&A alleen actieve relaties kunnen worden gebruikt, kunt u geen vragen stellen over de bron- of doellocatie, afhankelijk van uw keuze. Als u in plaats daarvan de kolommen met plaatsnamen denormaliseert naar de tabel *Vluchten*, kunt u vragen stellen als: 'maak een lijst met vluchten voor morgen met als bronlocatie Amsterdam en als doellocatie Wenen'.

**Actie vereist**

![slechts één pad voor elke tabel voor Q&A](media/q-and-a-best-practices/desktop-qna-19.png)

**Gereed voor Q&A**

![gebruik meerdere tabellen voor Q&A](media/q-and-a-best-practices/desktop-qna-20.png)

### <a name="add-synonyms-to-tables-and-columns"></a>Synoniemen toevoegen aan tabellen en kolommen

Deze stap geldt specifiek voor Q&A (en niet voor Power BI-rapporten in het algemeen). Gebruikers gebruiken vaak tal van termen om te verwijzen naar hetzelfde, zoals totale verkoop, net verkoop, totale net verkoop. U kunt deze synoniemen toevoegen aan tabellen en kolommen in het Power BI-model. 

Deze stap kan belangrijk zijn. Zelfs met eenvoudige tabel- en kolomnamen, stellen gebruikers van Q&A vragen waarin ze de woorden gebruiken die als eerste in hen opkomen. Ze kiezen niet uit een vooraf gedefinieerde lijst met kolommen. Hoe meer logische synoniemen u kunt toevoegen, hoe beter de ervaring van uw gebruikers met het rapport is. U kunt synoniemen toevoegen door in Power BI Desktop naar Modelweergave te gaan. Selecteer daar het tabblad Model maken en selecteer een veld of tabel. In het deelvenster Eigenschappen ziet u het vak **Synoniemen**. Hier kunt u synoniemen toevoegen.

![Synoniemen in het deelvenster Eigenschappen van Q&A](media/q-and-a-best-practices/qna-modelling-pane-synonyms.png)

 Wees voorzichtig met het toevoegen van synoniemen. Als u hetzelfde synoniem aan meer dan één kolom of tabel toevoegt, ontstaat ambiguïteit. Met Q&A maakt u waar mogelijk gebruik van context om te kiezen tussen niet-eenduidige synoniemen. Niet alle vragen bieden echter voldoende context. Wanneer de gebruiker bijvoorbeeld vraagt 'tel het aantal klanten', en u in het model drie items met het synoniem 'klant' hebt, krijgt de gebruiker mogelijk niet het gewenste antwoord. Zorg er in dergelijke gevallen voor dat het primaire synoniem uniek is, aangezien dit wordt gebruikt in de aanpassing. Dit kan worden gebruikt om de gebruiker te waarschuwen voor dubbelzinnigheid (bijvoorbeeld een aanpassing van 'toon het aantal gearchiveerde klantrecords'), waarmee wordt aangegeven dat de vraag wellicht beter op een andere manier kan worden gesteld.

## <a name="next-steps"></a>Volgende stappen

[Inleiding tot Power BI Q&A](q-and-a-intro.md)
