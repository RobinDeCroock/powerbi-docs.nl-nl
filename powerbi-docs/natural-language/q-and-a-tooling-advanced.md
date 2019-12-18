---
title: Het taalkundige Q&A-schema bewerken en formuleringen toevoegen in Power BI Desktop
description: Instructies voor het gebruik van Power BI Desktop om het taalkundige schema dat door Power BI Q&A wordt gebruikt, te bewerken.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 64a6294ca30901c61928eca068ab4ebbb3d39638
ms.sourcegitcommit: 320d83ab392ded71bfda42c5491acab3d9d357b0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74958512"
---
# <a name="edit-qa-linguistic-schema-and-add-phrasings-in-power-bi-desktop"></a>Het taalkundige Q&A-schema bewerken en formuleringen toevoegen in Power BI Desktop 
Normale zinnen en natuurlijke taal gebruiken om informatie uit uw gegevens te kunnen opvragen, is uiterst nuttig. Het is zelfs nog krachtiger wanneer u antwoorden kunt krijgen uit uw gegevens. Wanneer u Power BI Q&A een vraag stelt, wordt geprobeerd een zo goed mogelijk antwoord te geven. Maar voor nóg betere Q&A-interacties kunt u de antwoorden verbeteren. U kunt dit bijvoorbeeld doen door het taalkundige schema te bewerken. 

Het begint allemaal met uw bedrijfsgegevens.  Hoe beter het gegevensmodel is, hoe eenvoudiger gebruikers antwoorden van een goede kwaliteit kunnen krijgen. Het model kan bijvoorbeeld worden verbeterd door een taalkundig schema toe te voegen dat terminologie en relaties tussen tabellen en kolomnamen in uw gegevensset definieert en categoriseert. In Power BI Desktop kunt u uw taalkundige schema’s beheren. 

Q&A kent twee kanten.  Ten eerste is er het voorbereiden, of het *maken van een model*.  Daarnaast is er een deel voor het stellen van vragen en het verkennen van de gegevens, oftewel het *verbruiken*. Bij een aantal bedrijven zijn mogelijk werknemers als *gegevensmodelleerder* of IT-beheerder in dienst die de gegevenssets samenstellen, de gegevensmodellen maken en de gegevenssets naar Power BI publiceren.  Een andere set werknemers zijn dan de personen die de gegevens online 'verbruiken'.  Bij andere bedrijven zijn deze rollen wellicht gecombineerd. 

Dit artikel is bedoeld voor de gegevensmodelleerders, de mensen die gegevenssets optimaliseren om de best mogelijke Q&A-resultaten te bieden. 

## <a name="what-is-a-linguistic-schema"></a>Wat is een taalkundig schema?
Een taalkundig schema beschrijft termen en frasen die Q&A moet begrijpen voor objecten in een gegevensset, zoals woordsoorten, synoniemen en formuleringen die betrekking hebben op die gegevensset. Wanner u een gegevensset importeert of hiermee verbinding maakt, maakt Power BI een taalkundig schema op basis van de structuur van de gegevensset. Wanneer u Q&A een vraag stelt, wordt gezocht naar overeenkomsten en relaties in de gegevens om de intentie van uw vraag te ontdekken. Er wordt bijvoorbeeld gezocht naar zelfstandige naamwoorden, werkwoorden, bijvoeglijke naamwoorden, formuleringen en andere elementen. Er wordt naar relaties gezocht, zoals welke kolommen objecten van een werkwoord zijn. 

U bent waarschijnlijk bekend met woordsoorten (zie hieronder als dat niet het geval is), maar *formuleringen* is mogelijk een nieuwe term.  Een *formulering* is de manier waarop u de relatie tussen bepaalde dingen formuleert. U kunt bijvoorbeeld de relatie tussen klanten en producten omschrijven als 'klanten die producten kopen'. Of u zegt bijvoorbeeld 'leeftijden die aangeven hoe oud klanten zijn' om de relatie tussen klanten en leeftijden te beschrijven. Of zeg 'klanten hebben telefoonnummers' om de relatie tussen klanten en telefoonnummers te beschrijven.

Deze formuleringen zijn beschikbaar in vele vormen en maten. Een aantal komt direct overeen met relaties in het gegevensmodel. Een aantal koppelt kolommen aan hun ingesloten tabellen. Andere koppelen meerdere tabellen aan kolommen in complexe relaties. In alle gevallen beschrijven formuleringen de relatie tussen zaken aan de hand van dagelijkse termen.

Taalkundige schema's worden opgeslagen in een .yaml-indeling. Deze indeling is verwant aan de populaire JSON-indeling maar biedt een flexibelere en eenvoudiger te lezen syntaxis. Taalkundige schema's kunnen worden bewerkt, geëxporteerd en geïmporteerd in Power BI Desktop.

## <a name="prerequisites"></a>Vereisten

- Als u het artikel over [het verbeteren van uw gegevensmodel voor Q&A](q-and-a-best-practices.md) nog niet hebt gelezen, wilt u dit wellicht eerst doen. Hieraan staan talloze tips voor het ontwerpen en verbeteren van uw gegevensmodel en een belangrijke sectie over het toevoegen van synoniemen.  
- Download [.yaml- en .pbix-voorbeeldbestanden](https://go.microsoft.com/fwlink/?linkid=871858).   
- Installeer een .yaml-bestandseditor. Hiervoor wordt [Visual Studio Code](https://code.visualstudio.com/) aanbevolen.

### <a name="set-up-an-editor-for-yaml-files"></a>Een editor voor .yaml-bestanden instellen
Het wordt aangeraden Visual Studio Code te gebruiken om .yaml-bestanden voor taalkundige schema's te bewerken. Visual Studio Code bevat kant-en-klare ondersteuning voor .yaml-bestanden en kan worden uitgebreid om specifiek de Power BI-indeling voor taalkundige schema's te valideren.
1. Installeer [Visual Studio Code](https://code.visualstudio.com/).    

2. Selecteer het taalkundige voorbeeldschema dat u eerder hebt opgeslagen: [.yaml-bestand](https://go.microsoft.com/fwlink/?linkid=871858) (SummerOlympics.lsdl.yaml).    
4. Selecteer **Visual Studio Code** en **Altijd deze app gebruiken om .yaml-bestanden te openen**.

    ![Hoe wilt u dit bestand openen](media/q-and-a-tooling-advanced/power-bi-visual-code.png)

4. Installeer in Visual Studio Code de YAML-ondersteuning van de Red Hat-extensie.    
    a. Selecteer het tabblad **Extensies** (laatste aan de linkerkant) of druk op CTRL+SHIFT+X.    
    ![Het pictogram Extensies](media/q-and-a-tooling-advanced/power-bi-extensions.png)    
    b. Zoek 'yaml' en selecteer **YAML-ondersteuning door Red Hat** in de lijst.    
    c. Selecteer **Installeren > Opnieuw laden**.


## <a name="working-with-linguistic-schemas"></a>Werken met taalkundige schema's

U kunt op twee manieren met taalkundige schema's werken. De eerste methode is het bewerken, importeren en exporteren van het .yaml-bestand vanaf het lint in Power BI Desktop. Deze manier wordt besproken in het Power BI-artikel [Q&A Tooling experience](q-and-a-tooling-intro.md) (Ervaring met het Q&A-hulpprogramma). U hoeft het .yaml-bestand niet te openen om Q&A te verbeteren. 

U kunt een taalkundig schema ook bewerken door het .yaml-bestand te exporteren en rechtstreeks te bewerken.  Wanneer u het .yaml-bestand van een taalkundig schema bewerkt, voegt u een tag toe aan kolommen in de tabel als verschillende grammaticale elementen en definieert u woorden die een collega zou kunnen gebruiken om een vraag te formuleren. U noemt bijvoorbeeld de kolommen die het onderwerp en het lijdende voorwerp van het werkwoord zijn. U voegt alternatieve woorden toe die collega's kunnen gebruiken om te verwijzen naar tabellen, kolommen en metingen in uw model. 

![Yaml-voorbeeldbestand van taalkundig schema](media/q-and-a-tooling-advanced/power-bi-linguistic-schema.png)

Voordat u een taalkundig schema kunt bewerken, moet u deze openen (exporteren) vanaf Power BI Desktop. Het .yaml-bestand weer op dezelfde locatie opslaan, wordt als importeren beschouwd.  Maar u kunt ook andere .yaml-bestanden importeren.  Als u bijvoorbeeld een vergelijkbare gegevensset hebt en u al veel tijd hebt besteed aan het toevoegen van woordsoorten, het identificeren van relaties, het maken van formuleringen en het maken van synoniemen, kunt u dat .yaml-bestand gebruiken in een ander Power BI Desktop-bestand. 

Q&A gebruikt al deze informatie in combinatie met eventuele verbetering die u aanbrengt om betere antwoorden te geven, vragen automatisch aan te vullen en vragen samen te vatten.

## <a name="edit-a-linguistic-schema"></a>Taalkundig schema bewerken
Wanneer u eerst uw taalkundige schema vanaf Power BI Desktop exporteert, wordt de inhoud in het bestand grotendeels of volledig automatisch gegenereerd door de Q&A-engine. Deze gegenereerde entiteiten, woorden (synoniemen), relaties en formuleringen worden aangeduid met de tag **Status: gegenereerd**. Ze worden vooral ter informatie in het bestand opgenomen, maar kunnen ook een nuttig beginpunt zijn voor uw eigen wijzigingen. 

> [!NOTE]
> Het .yaml-voorbeeldbestand in deze zelfstudie bevat niet de tags **Status: gegenereerd** of **Status: verwijderd** aangezien deze speciaal zijn voorbereid voor deze zelfstudie. Als u deze tags wilt zien, opent u een onbewerkt .pbix-bestand in de weergave Relatie en exporteert u het taalkundige schema.

![YAML met de Status: gegenereerd](media/q-and-a-tooling-advanced/power-bi-generated-state.png)

Wanneer u uw taalkundige schemabestand weer in Power BI Desktop importeert, worden alle elementen met de markering **Status: gegenereerd** genegeerd en later opnieuw gegenereerd. Dus als u gegenereerde inhoud wilt wijzigen, verwijdert u de bijbehorende **Status: Label** ook gegenereerd. Evenzo moet u, als u gegenereerde inhoud wilt verwijderen, wijzigingen aanbrengen aan de tag **Status: Label** gegenereerd in status **: verwijderd**, zodat deze niet opnieuw wordt gegenereerd wanneer u uw taalkundige schemabestand importeert.

### <a name="export-then-import-a-yaml-file"></a>Een .yaml-bestand exporteren en vervolgens importeren

1. Open de gegevensset in de Modelweergave in Power BI Desktop. 
2. Op het tabblad **Model maken** selecteert u **Taalkundig schema** > **Taalkundig schema exporteren**.
3. Sla het schema op. De bestandsnaam eindigt op .lsdl.yaml.
4. Open het bestand in Visual Code of een andere editor.
4. In de Modelweergave in Power BI Desktop selecteert u op het tabblad **Model maken** de optie **Taalkundig schema** > **Taalkundig schema importeren**. 
6. Navigeer naar de locatie waar u het bewerkte .yaml-bestand hebt opgeslagen en selecteer het. Een bevestigingsbericht vertelt u dat het .yaml-bestand van het taalkundige schema is geïmporteerd.

    ![Het bericht Geslaagd](media/q-and-a-tooling-advanced/power-bi-success.png)

## <a name="phrasings-in-the-linguistic-schema"></a>Formuleringen in het taalkundige schema
Een formulering is de manier waarop u de relatie tussen bepaalde dingen formuleert. U kunt bijvoorbeeld de relatie tussen klanten en producten omschrijven als 'klanten die producten kopen'.

## <a name="where-do-phrasings-come-from"></a>Waar komen formuleringen vandaan?
Veel eenvoudige formuleringen worden in Power BI automatisch aan het taalkundige schema toegevoegd, op basis van de structuur van het model en een aantal gokken op basis van kolomnamen. Bijvoorbeeld:
- De meeste kolommen zijn gekoppeld aan hun ingesloten tabel met een eenvoudige formulering zoals 'producten hebben beschrijvingen'.
- Modelrelaties leiden tot standaardformuleringen voor beide kanten van de relatie zoals 'orders hebben producten' en 'producten hebben orders'.
- Een aantal modelrelaties kan, op basis van hun kolomnamen, een ingewikkeldere standaardformulering krijgen zoals 'orders worden verzonden naar steden'.

Uw gebruikers kunnen echter op tal van manieren over zaken praten, die door Q&A niet te raden zijn. U kunt daarom uw eigen formuleringen handmatig toevoegen.

## <a name="why-add-phrasings"></a>Waarom zou u formuleringen toevoegen?
De eerste reden voor het toevoegen van een formulering is dat u een nieuwe term definieert. Als u bijvoorbeeld de vraag 'maak een lijst van de oudste klanten' wilt stellen, moet u eerst Q&A laten weten wat u met 'oud' bedoelt. Hiervoor moet u een formulering zoals 'leeftijden geven aan hoe oud klanten zijn' toevoegen.

De tweede reden voor het toevoegen van een formulering is dat u onduidelijkheden kunt oplossen. Basiszoekopdrachten naar trefwoorden worden moeilijker als woorden meerdere betekenissen hebben. ‘Vluchten naar Chicago’ is bijvoorbeeld niet hetzelfde als 'vluchten van Chicago'. Q&A weet echter niet welke van de twee u bedoelt, tenzij u de formuleringen 'vluchten komen uit vertreksteden' en 'vluchten komen aan in aankomststeden' toevoegt. Evenzo begrijpt Q&A alleen het onderscheid tussen ‘auto’s die Jan aan Marije verkocht’ en ‘auto’s die Jan van Marije heeft gekocht’ als u de formuleringen ‘klanten kopen auto's van werknemers’ en ‘werknemers verkopen auto's aan klanten’ toevoegt.

De laatste reden voor het toevoegen van een formulering is dat u nieuwe formuleringen verbetert. In plaats van Q&A 'Laat de klanten en hun producten zien' te laten herhalen, is het duidelijker als u terugkrijgt: 'Laat de klanten en de producten die ze hebben gekocht zien' of 'Laat de klanten en de producten die ze hebben beoordeeld zien', afhankelijk van hoe de vraag is begrepen. Door aangepaste formuleringen toe te passen, kunnen nieuwe formuleringen explicieter en minder verwarrend zijn.


## <a name="kinds-of-phrasings"></a>Soorten formuleringen
Om de verschillende soorten formuleringen te leren begrijpen, moet u eerst een aantal basale grammaticatermen onthouden:
- Een *zelfstandig naamwoord* is een persoon, plaats of voorwerp. 
    Voorbeelden: auto, tiener, Marty, fluxcompensator
- Een *werkwoord* is een actie of een staat. 
    Voorbeelden: uitkomen, barsten, verslinden, uitwerpen
- Een *bijvoeglijk naamwoord* is een beschrijvend woord waarmee zelfstandige naamwoorden worden aangepast. 
    Voorbeelden: krachtig, magisch, gouden, gestolen
- Een *voorzetsel* is een woord dat wordt gebruikt vóór een zelfstandig naamwoord om het te koppelen aan een eerder zelfstandig naamwoord, werkwoord of bijvoeglijk naamwoord    Voorbeelden: van, voor, naast, vanaf
-  Een *kenmerk* is een kwaliteit of functie van iets.
-  Een *naam* is een woord of reeks woorden waarmee naar een persoon, dier, plaats of voorwerp wordt verwezen.   


### <a name="attribute-phrasings"></a>Kenmerkformuleringen
Kenmerkformuleringen zijn de kracht van Q&A en worden gebruikt wanneer het ene ding fungeert als kenmerk van een ander ding. Ze zijn eenvoudig en duidelijk en voeren het zware werk uit wanneer u geen gedetailleerdere formulering hebt gedefinieerd. Kenmerkformulekringen worden beschreven met behulp van het basiswerkwoord ‘hebben’ (‘producten hebben categorieën’ en ‘gastlanden hebben gaststeden’). Kenmerkformuleringen kunnen ook automatisch vragen toestaan met de voorzetsels 'van' en 'voor' ('categorieën van producten', 'orders voor producten') en bezittelijk voornaamwoorden ('Jans orders'). Kenmerkformuleringen worden gebruikt in dit soort vragen:

- Welke klanten hebben orders?
- Maak een lijst met hoststeden per land in oplopende volgorde
- Laat orders met thee zien
- Maak een lijst van klanten met orders
- Wat is de categorie of elk product?
- De orders van graaf Robert King    

De overgrote meerderheid van de kenmerkformuleringen die nodig zijn in uw model wordt door Power BI gegenereerd, op basis van de tabel/kolominsluiting en modelrelaties. U hoeft ze doorgaans dus niet zelf te maken.
Hier is een voorbeeld van hoe een kenmerkformulering eruitziet in het taalkundige schema:

```json
product_has_category:
  Binding: {Table: Products}
  Phrasings:
  - Attribute: {Subject: product, Object: product.category}
```
 
### <a name="name-phrasings"></a>Naamformuleringen
Naamformuleringen zijn nuttig wanneer uw gegevensmodel een tabel bevat die benoemde objecten bevat, zoals de namen van sporters of klanten. De formulering 'productnamen zijn namen van producten' is bijvoorbeeld essentieel om productnamen in vragen te kunnen gebruiken. Als naamformulering is ook het werkwoord ‘genaamd’ mogelijk (bijvoorbeeld ‘maak een lijst met klanten genaamd Jan Smits’). Bij gebruik in combinatie met andere formuleringen is het echter uiterst belangrijk om het gebruik van een naamwaarde toe te staan om naar een specifieke tabelrij te verwijzen. Zo kan Q&A uit 'Klanten die thee hebben gekocht' halen dat de waarde 'thee' naar de hele rij van de producttabel verwijst en niet slechts naar een waarde in de kolom productnaam. Naamformuleringen worden gebruikt in dit soort vragen:    
- Welke werknemers heten Robert King
- Wie heet Ernst Handel
- De sporten van Fernand De Montigny
- Aantal atleten genaamd Marije
- Wat heeft Robert King gekocht?

Ervan uitgaande dat u een logische naamconventie gebruikt voor naamkolommen in uw model (bijvoorbeeld 'Naam' of 'Productnaam' in plaats van 'PrdNm'), zal het merendeel van de naamformuleringen die u voor uw model nodig hebt, automatisch door Power BI worden gegenereerd. U hoeft ze dus niet zelf te maken.

Hier is een voorbeeld van hoe een naamformulering er in het taalkundige schema uitziet:

```json
employee_has_name:
  Binding: {Table: Employees}
  Phrasings:
  - Name:
      Subject: employee
      Name: employee.name
```

 
### <a name="adjective-phrasings"></a>Formuleringen van bijvoeglijk naamwoorden
Formuleringen van bijvoeglijke naamwoorden definiëren nieuwe bijvoeglijke naamwoorden die worden gebruikt om dingen in uw model te beschrijven. De formulering 'tevreden klanten zijn klanten met een beoordeling > 6' is bijvoorbeeld nodig om vragen te stellen zoals 'maak een lijst van de tevreden klanten in Rotterdam'. Er zijn verschillende vormen voor formuleringen van bijvoeglijke naamwoorden, die in verschillende situaties worden gebruikt.

*Eenvoudige formuleringen van bijvoeglijke naamwoorden* definiëren een nieuw bijvoeglijk naamwoord op basis van een voorwaarde, zoals 'uit de handel genomen producten zijn producten met de status = D'. Eenvoudige formuleringen van bijvoeglijke naamwoorden worden gebruikt in dit soort vragen:
- Welke producten zijn uit de handel genomen?
- Maak een lijst van de uit de handel genomen producten
- Maak een lijst van de winnaars van een gouden medaille
- Producten die zijn nabesteld

Hier is een voorbeeld van hoe een eenvoudige formulering van een bijvoeglijk naamwoord er in het taalkundige schema uitziet:

product_is_discontinued:

```json
Binding: {Table: Products}
  Conditions:
  - Target: product.discontinued
    Operator: Equals
    Value: true
  Phrasings:
  - Adjective:
      Subject: product
      Adjectives: [discontinued]
```

*Formuleringen van bijvoeglijke naamwoorden voor meetwaarden* definiëren een nieuw bijvoeglijk naamwoord op basis van een numerieke waarde die de mate aangeeft waarin het bijvoeglijke naamwoord van toepassing is, zoals 'lengtes geven aan hoe lang een rivier is' en 'kleine landen/regio's hebben kleine landoppervlakken'. Formuleringen van bijvoeglijke naamwoorden voor meetwaarden worden gebruikt in dit soort vragen:
- Maak een lijst van de lange rivieren
- Welke rivieren zijn het langst?
- Maak een lijst met de kleinste landen/regio's die een gouden medaille voor basketbal hebben gewonnen
- Hoe lang is de Rio Grande?

Hier is een voorbeeld hoe een formulering van een bijvoeglijk naamwoord voor meetwaarden er in het taalkundige schema uitziet:

river_has_length:

 ```json
Binding: {Table: Rivers}
  Phrasings:
  - Adjective:
      Subject: river
      Adjectives: [long]
      Antonyms: [short]
      Measurement: river.length
```

*Dynamische formuleringen van bijvoeglijke naamwoorden* definiëren een reeks nieuwe bijvoeglijke naamwoorden op basis van waarden in een kolom in het model, zoals 'kleuren beschrijven producten' en 'evenementen hebben geslachten per evenement'. Dynamische formuleringen van bijvoeglijke naamwoorden worden gebruikt in dit soort vragen:
- Maak een lijst van de rode producten
- Welke producten zijn groen?
- Laat schaatsevenementen voor vrouwen zien
- Tel het aantal problemen dat actief is

Hier is een voorbeeld van hoe een dynamische formulering van bijvoeglijke naamwoorden er in het taalkundige schema uitziet:

product_has_color:
```json
Binding: {Table: Products}
  Phrasings:
  - DynamicAdjective:
      Subject: product
      Adjective: product.color
```

 
### <a name="noun-phrasings"></a>Formuleringen van zelfstandige naamwoorden
Formuleringen van zelfstandige naamwoorden definiëren nieuwe zelfstandige naamwoorden die subsets van dingen in uw model beschrijven. Ze bevatten vaan een soort modelspecifieke meetwaarde of voorwaarde. Voor ons Olympische model willen we bijvoorbeeld formuleringen toevoegen waarin een onderscheid wordt gemaakt tussen kampioenen en medaillewinnaars, balsporten en watersporten, teams en afzonderlijke sporters, leeftijdscategorieën voor sporters (tieners, volwassenen, senioren), enzovoort. Voor onze filmdatabase willen we misschien formuleringen van zelfstandige naamwoorden toevoegen voor 'flops zijn films met een nettowinst < 0' zodat we vragen kunnen stellen zoals 'tel het aantal flops per jaar'. Er zijn twee soorten formuleringen van zelfstandige naamwoorden, die in verschillende situaties worden gebruikt.

*Eenvoudige formuleringen van zelfstandige naamwoorden* definiëren een nieuw zelfstandig naamwoord op basis van een voorwaarde, zoals 'aannemers zijn werknemers waarbij fulltime = false' en 'een kampioen is een atleet waarbij het aantal medailles >5'. Eenvoudige formulering van zelfstandige naamwoorden worden gebruikt in dit soort vragen:

- Welke werknemers zijn aannemer?
- Tel het aantal aannemers in Amsterdam
- Hoeveel kampioenen in 2016

Hier is een voorbeeld van hoe een eenvoudige formulering van een zelfstandig naamwoord er in het taalkundige schema uitziet:

employee_is_contractor:

```json
Binding: {Table: Employees}
  Conditions:
  - Target: employee.full_time
    Operator: Equals
    Value: false
  Phrasings:
  - Noun:
      Subject: employee
      Nouns: [contractor]
```

*Dynamische formuleringen van zelfstandige naamwoorden* definiëren een reeks nieuwe zelfstandig naamwoorden op basis van waarden in een kolom in het model, zoals 'banen definiëren subsets van werknemers'. Dynamische formuleringen van zelfstandige naamwoorden worden gebruikt in dit soort vragen:

- Maak een lijst van de caissières in Zwolle
- Welke werknemers zijn barista?
- Maak een lijst van de scheidsrechters in 1992

Hier is een voorbeeld van hoe een dynamische formulering van zelfstandige naamwoorden er in het taalkundige schema uitziet: employee_has_job:

 ```json
Binding: {Table: Employees}
  Phrasings:
  - DynamicNoun:
      Subject: employee
      Noun: employee.job
```

### <a name="preposition-phrasings"></a>Voorzetselformuleringen
Voorzetselformuleringen worden gebruikt om te beschrijven hoe dingen in uw model zijn gekoppeld via voorzetsels. De formulering 'steden zijn in landen' biedt bijvoorbeeld meer duidelijkheid bij vragen zoals 'tel de steden in Overijssel'. Een aantal voorzetselformuleringen worden automatisch gemaakt zodra een kolom als geografische entiteit is herkend. Voorzetselformuleringen worden gebruikt in dit soort vragen:

- Tel de klanten in Apeldoorn
- Maak een lijst van de boeken over taalkunde
- In welke stad bevindt Robert King zich?
- Hoeveel boeken zijn geschreven door Stephen Pinker?
 
Hier is een voorbeeld van hoe een voorzetselformulering er in het taalkundige schema uitziet: customers_are_in_cities:

 ```json
Binding: {Table: Customers}
  Phrasings:
  - Preposition:
      Subject: customer
      Prepositions: [in]
      Object: customer.city
```

 
### <a name="verb-phrasings"></a>Werkwoordformuleringen
Werkwoordformuleringen worden gebruikt om te beschrijven hoe dingen in uw model zijn gekoppeld via werkwoorden. De formulering 'klanten kopen producten' biedt bijvoorbeeld meer duidelijkheid bij vragen zoals 'wie kocht kaas?' en 'wat heeft Jan gekocht?' Werkwoordformuleringen zijn de meest flexibele soorten formuleringen, omdat ze vaak meer dan twee dingen aan elkaar koppelen, zoals in 'werknemers verkopen producten aan klanten'. Voorzetselformuleringen worden gebruikt in dit soort vragen:

- Wie heeft wat aan wie verkocht?
- Welke werknemer heeft thee aan Jan verkocht?
- Aan hoeveel klanten heeft Marije thee verkocht?
- Maak een lijst van de producten die Marije aan Jan heeft verkocht.
- Welke uit de handel genomen producten zijn verkocht aan klanten in Zwolle door werknemers uit Amersfoort?

Werkwoordformuleringen kunnen ook voorzetselbepalingen bevatten, wat de flexibiliteit van deze formuleringen nog eens versterkt. Denk bijvoorbeeld aan 'atleten winnen medailles bij wedstrijden' of 'klanten krijgen restitutie voor producten'. Werkwoordformuleringen met voorzetselbepalingen worden gebruikt in dit soort vragen:

- Hoeveel atleten hebben een gouden medaille gewonnen bij de Visa Championships?
- Aan welke klanten is een restitutie gegeven voor kaas?
- Tijdens welke wedstrijd heeft Danell Leyva een bronzen medaille gewonnen?

Een aantal werkwoordformuleringen wordt automatisch gemaakt zodra wordt herkend dat een kolom zowel een werkwoord als een voorzetsel bevat.

Hier is een voorbeeld van hoe een werkwoordformulering er in het taalkundige schema uitziet: customers_buy_products_from_salespeople:

```json
Binding: {Table: Orders}
  Phrasings:
  - Verb:
      Subject: customer
      Verbs: [buy, purchase]
      Object: product
      PrepositionalPhrases:
      - Prepositions: [from]
        Object: salesperson
```

### <a name="relationships-with-multiple-phrasings"></a>Relaties met meerdere formuleringen
In veel gevallen kan één relatie op meerdere manieren worden beschreven. In dit geval kan één relatie meerdere formuleringen hebben. Het is gebruikelijk dat de relatie tussen een tabelentiteit en een kolomentiteit zowel een kenmerkformulering als een andere formulering bevat. In de relatie tussen klant en klantnaam wilt u bijvoorbeeld gebruikmaken van zowel een kenmerkformulering (bijvoorbeeld 'klanten hebben namen') als een naamformulering (bijvoorbeeld 'klantnamen zijn de namen van klanten'), zodat u beide soorten vragen kunt stellen.

Hier is een voorbeeld van hoe een relatie met twee formuleringen er in het taalkundige schema uitziet: customer_has_name:

  ```json
Binding: {Table: Customers}
  Phrasings:
    - Attribute: {Subject: customer, Object: customer.name}
    - Name:
        Subject: customer
        Object: customer.name
```

Een ander voorbeeld is het toevoegen van de alternatieve formulering 'werknemers verkopen producten aan klanten' aan de relatie 'klanten kopen producten van werknemers'. Let op: u hoeft geen varianten zoals 'werknemers verkopen producten *aan klanten*' of 'producten worden verkocht aan klanten *door werknemers*' toe te voegen,aangezien de varianten 'door' en 'aan' van het onderwerp en meewerkend voorwerp automatisch door Q&A worden afgeleid.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
Als u een .lsdl.yaml-bestand wijzigt dat niet voldoet aan de indeling van het taalkundige schema, ziet u nu validatielijntjes om problemen aan te geven: 

![yaml-bestand met fouten](media/q-and-a-tooling-advanced/power-bi-yaml-errors.png)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
