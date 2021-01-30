---
title: Richtlijnen voor veel-op-veel-relaties
description: Richtlijnen voor het ontwikkelen van veel-op-veel-modelrelaties.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 654c5ad71d7629fba1bf17b28e9e21370ebee0c3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087954"
---
# <a name="many-to-many-relationship-guidance"></a>Richtlijnen voor veel-op-veel-relaties

Dit artikel is geschreven voor iedereen die gegevensmodellen maakt met Power BI Desktop. Er worden drie verschillende veel-op-veel-modelleringsscenario's beschreven. Ook worden er richtlijnen gegeven voor hoe u voor deze scenario's kunt ontwerpen in uw modellen.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

Er zijn drie veel-op-veel-scenario's. Deze kunnen zich voordoen als u het volgende moet doen:

- [Twee dimensietabellen relateren](#relate-many-to-many-dimensions)
- [Twee feitentabellen relateren](#relate-many-to-many-facts)
- [Nauwkeurigere feitentabellen relateren](#relate-higher-grain-facts), wanneer in de feitentabel nauwkeurigere rijen zijn opgeslagen dan in de dimensietabel

## <a name="relate-many-to-many-dimensions"></a>Veel-op-veel-dimensies relateren

Laten we het eerste veel-op-veel-scenariotype eens gaan bekijken op basis van een voorbeeld. In het klassieke scenario worden twee entiteiten gerelateerd: klanten van een bank en bankrekeningen. Bedenk dat klanten meerdere rekeningen kunnen hebben en dat een rekening aan meerdere klanten kan toebehoren. Wanneer een rekening aan meerdere klanten toebehoort, worden deze gewoonlijk _gemeenschappelijke rekeninghouders genoemd_.

Het modelleren van deze entiteiten is eenvoudig. Rekeningen worden in één dimensietabel opgeslagen en klanten in een andere dimensietabel. Zoals kenmerkend is voor dimensietabellen bevat elke tabel een id-kolom. Als u de relatie tussen de twee tabellen wilt modelleren, is er een derde tabel nodig. Deze tabel wordt gewoonlijk een _overbruggingstabel_ genoemd. In dit voorbeeld dient de brugtabel om er één rij voor elke klant-rekeningkoppeling in op te slaan. Als deze tabel alleen id-kolommen bevat, wordt deze een [_feitloze feitentabel_](star-schema.md#factless-fact-tables) genoemd.

Hier volgt een vereenvoudigd modeldiagram van de drie tabellen.

![Diagram met een model met drie tabellen. Het ontwerp wordt beschreven in de volgende alinea.](media/relationships-many-to-many/bank-account-customer-model-example.png)

De eerste tabel heet **Account** en bevat twee kolommen: **AccountID** en **Account**. De tweede tabel heet **AccountCustomer** en bevat twee kolommen: **AccountID** en **CustomerID**. De derde tabel heet **Customer** en bevat twee kolommen: **CustomerID** en **Customer**. Er zijn geen relaties tussen de tabellen.

Er worden een-op-veel-relaties toegevoegd om de tabellen te koppelen. Hier volgt een bijgewerkt modeldiagram van de gerelateerde tabellen. De feitentabel **Transaction** is toegevoegd. Hierin worden rekeningtransacties opgeslagen. De overbruggingstabel en alle id-kolommen zijn verborgen.

![Diagram met het model dat nu de vier tabellen bevat. Er zijn een-op-veel-relaties toegevoegd om alle tabellen te koppelen.](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

Het modeldiagram is zodanig gewijzigd dat de tabelrijen worden weergegeven om aan te geven hoe de doorgifte van relatiefilters werkt.

> [!NOTE]
> Het is niet mogelijk om tabelrijen weer te geven in het Power BI Desktop-modeldiagram. Het wordt wel gedaan in dit artikel om duidelijke voorbeelden te kunnen geven.

![Diagram met het model dat nu de tabelrijen bevat. De rijgegevens voor de vier tabellen worden beschreven in de volgende alinea.](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

De rijgegevens voor de vier tabellen worden beschreven in de volgende lijst:

- De tabel **Account** (rekening) heeft twee rijen:
  - **AccountID** 1 is voor Account-01
  - **AccountID** 2 is voor Account-02
- De tabel **Customer** (klant) heeft twee rijen:
  - **CustomerID** 91 is voor Customer-91
  - **CustomerID** 92 is voor Customer-92
- De tabel **AccountCustomer** heeft drie rijen:
  - **AccountID** 1 is gekoppeld aan **CustomerID** 91
  - **AccountID** 1 is gekoppeld aan **CustomerID** 92
  - **AccountID** 2 is gekoppeld aan **CustomerID** 92
- De tabel **Transaction** (transactie) heeft drie rijen:
  - **Date** (datum) 1 januari 2019, **AccountID** (rekening-id) 1, **Amount** (bedrag) 100
  - **Date** 2 februari 2019, **AccountID** 2, **Amount** 200
  - **Date** 3 maart 2019, **AccountID** 1, **Amount** -25

Laten we eens kijken wat er gebeurt wanneer er een query op het model wordt uitgevoerd.

Hieronder staan twee visuals waarin de kolom **Amount** van de tabel **Transaction** wordt samengevat. De eerste visual is gegroepeerd op rekening zodat de som van de kolommen **Amount** het _rekeningsaldo_ aangeeft. De tweede visual is gegroepeerd op klant zodat de som van de kolommen **Amount** het _klantsaldo_ aangeeft.

![Diagram met twee rapportvisualisaties die naast elkaar worden weergegeven. De visuals worden in de volgende alinea beschreven.](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

De eerste visual heet **Account Balance** (rekeningsaldo) en bevat twee kolommen: **Account** en **Amount**. Het volgende resultaat wordt erin weergegeven:

- Het saldo van Account-01 is 75
- Het saldo van Account-02 is 200
- Het totaal is 275

De tweede visual heet **Customer Balance** (klantsaldo) en bevat twee kolommen: **Customer** en **Amount**. Het volgende resultaat wordt erin weergegeven:

- Het saldo van Customer-91 is 275
- Het saldo van Customer-92 is 275
- Het totaal is 275

Een korte blik op de tabelrijen en de visual **Account Balance** wijst uit dat de resultaten voor elke rekening en het totaalbedrag kloppen. Dat komt doordat elke groepering van rekeningen resulteert in filterdoorgifte naar de tabel **Transaction** voor die rekening.

Er lijkt echter iets mis met de visual **Customer Balance**. Elke klant in de visual **Customer Balance** heeft hetzelfde saldo als het totaalsaldo. Dit resultaat kan alleen kloppen als elke klant een gemeenschappelijke rekeninghouder van elke rekening is. Dat is in dit voorbeeld niet het geval. Het probleem heeft te maken met filterdoorgifte. Die loopt niet helemaal door tot aan de tabel **Transaction**.

Volg maar eens de richtingen van het relatiefilter van de tabel **Customer** naar de tabel **Transaction**. Het moet duidelijk zijn dat de relatie tussen de tabel **Account** en de tabel **AccountCustomer** in de verkeerde richting wordt doorgegeven. De filterrichting voor deze relatie moet worden ingesteld op **Beide**.

![Diagram met het model dat is bijgewerkt. Het filter werkt nu in beide richtingen.](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![Diagram met dezelfde twee rapportvisuals naast elkaar. De eerste visual is niet gewijzigd, maar de tweede visual wel.](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

Zoals verwacht is er niets gewijzigd aan de visual **Account Balance**.

De visual **Customer Balance** bevat nu echter het volgende resultaat:

- Het saldo van Customer-91 is 75
- Het saldo van Customer-92 is 275
- Het totaal is 275

De visual **Customer Balance** bevat nu het juiste resultaat. Volg de filterrichtingen voor uzelf en zie hoe de klantsaldi zijn berekend. Begrijp ook dat het visualtotaal _alle klanten_ betekent.

Iemand die niet bekend is met de modelrelaties zou kunnen concluderen dat het resultaat onjuist is. Diegene kan vragen: _Waarom is het totaal voor **Customer-91** en **Customer-92** niet gelijk aan 350 (75 + 275)?_

Voor het antwoord op deze vraag is kennis van de veel-op-veel-relatie nodig. Elk klantsaldo kan de toevoeging van meerdere rekeningsaldi vertegenwoordigen, waardoor de klantsaldi _niet-additief_ zijn.

### <a name="relate-many-to-many-dimensions-guidance"></a>Richtlijnen voor het relateren van veel-op-veel-dimensies

Voor veel-op-veel-relaties tussen dimensietabellen gelden de volgende richtlijnen:

- Voeg elke veel-op-veel-gerelateerde entiteit toe als een modeltabel, zodat deze een unieke id-kolom heeft
- Voeg een overbruggingstabel toe om gekoppelde entiteiten in op te slaan
- Maak een-op-veel-relaties tussen de drie tabellen
- Configureer **één** bidirectionele relatie zodat de filterdoorgifte helemaal doorloopt naar de feitentabellen
- Stel de eigenschap **Null-waarde toegestaan** van id-kolommen in op FALSE als u geen ontbrekende id-waarden wilt. Anders mislukt het vernieuwen van gegevens als er waarden ontbreken
- Verberg de overbruggingstabel (tenzij deze aanvullende kolommen of metingen bevat die nodig zijn voor rapportage)
- Verberg alle id-kolommen die niet geschikt zijn voor rapportage (bijvoorbeeld wanneer id's surrogaatsleutels zijn)
- Als het zinvol is om een id-kolom zichtbaar te laten, zorg er dan voor dat deze zich aan de 'een'-zijde van de relatie bevindt. Verberg altijd de kolom aan de 'veel'-zijde. Dit geeft de beste filterprestaties.
- Geef uitleg aan uw rapportgebruikers om verwarring of misinterpretatie te voorkomen. U kunt beschrijvingen met tekstvakken of [knopinfo voor visuele koptekst](report-page-tooltips.md) toevoegen

Het is niet raadzaam om veel-op-veel-dimensietabellen rechtstreeks te relateren. Voor deze ontwerpbenadering moet u een relatie met een veel-op-veel-kardinaliteit configureren. Dit is te realiseren, maar dat impliceert wel dat de gerelateerde kolommen dubbele waarden krijgen. Het is echter een gangbare ontwerppraktijk om dimensietabellen een id-kolom te geven. Zorg ervoor dat dimensietabellen de id-kolom gebruiken als de 'een'-zijde van een relatie.

## <a name="relate-many-to-many-facts"></a>Veel-op-veel-feiten relateren

Het tweede veel-op-veel-scenario heeft betrekking op het relateren van twee feitentabellen. Twee feitentabellen kunnen rechtstreeks worden gerelateerd. Deze ontwerptechniek kan handig zijn om snel en eenvoudig gegevens te verkennen. Deze ontwerpbenadering is over het algemeen echter niet aan te raden. Verderop in deze sectie wordt uitgelegd waarom.

Laten we eens kijken naar een voorbeeld met twee feitentabellen: **Order** (order) en **Fulfillment** (levering). De tabel **Order** bevat één rij per orderregel en de tabel **Fulfillment** kan nul of meer rijen per orderregel bevatten. Rijen in de tabel **Order** vertegenwoordigen verkooporders. Rijen in de tabel **Fulfillment** vertegenwoordigen orderitems die zijn verzonden. Een veel-op-veel-relatie heeft betrekking op de twee **OrderID**-kolommen, met alleen filterdoorgifte vanuit de tabel **Order** (filtering van **Order** naar **Fulfillment**).

![Diagram met een model met twee tabellen: Order en Fulfillment.](media/relationships-many-to-many/order-fulfillment-model-example.png)

De relatiekardinaliteit is ingesteld op veel-op-veel om ondersteuning te bieden voor het opslaan van dubbele **OrderID**-waarden in beide tabellen. In de tabel **Order** kunnen dubbele **OrderID**-waarden aanwezig zijn omdat een order meerdere regels kan hebben. In de tabel **Fulfillment** kunnen dubbele **OrderID**-waarden aanwezig zijn omdat orders meerdere regels kunnen hebben en orderregels kunnen worden geleverd via meerdere zendingen.

Nu gaan we de tabelrijen bekijken. In de tabel **Fulfillment** ziet u dat orderregels kunnen worden geleverd via meerdere zendingen. (Het ontbreken van een orderregel betekent dat de order nog moet worden geleverd.)

![Diagram met het model dat nu de tabelrijen bevat. De rijgegevens voor de twee tabellen worden beschreven in de volgende alinea.](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

De rijgegevens voor de twee tabellen worden beschreven in de volgende lijst:

- De tabel **Order** heeft vijf rijen:
  - **OrderDate** (orderdatum) 1 januari 2019, **OrderID** (order-id) 1, **OrderLine** (orderregel) 1, **ProductID** (product-id) Prod-A, **OrderQuantity** (orderaantal) 5, **Sales** (verkoop) 50
  - **OrderDate** 1 januari 2019, **OrderID** 1, **OrderLine** 2, **ProductID** Prod-B, **OrderQuantity** 10, **Sales** 80
  - **OrderDate** 2 februari 2019, **OrderID** 2, **OrderLine** 1, **ProductID** Prod-B, **OrderQuantity** 5, **Sales** 40
  - **OrderDate** 2 februari 2019, **OrderID** 2, **OrderLine** 2, **ProductID** Prod-C, **OrderQuantity** 1, **Sales** 20
  - **OrderDate** 3 maart 2019, **OrderID** 3, **OrderLine** 1, **ProductID** Prod-C, **OrderQuantity** 5, **Sales** 100
- De tabel **Fulfillment** heeft vier rijen:
  - **FulfillmentDate** (leverdatum) 1 januari 2019, **FulfillmentID** (lever-id) 50, **OrderID** (order-id) 1, **OrderLine** (orderregel) 1, **FulfillmentQuantity** (leveringsaantal) 2
  - **FulfillmentDate** 2 februari 2019, **FulfillmentID** 51, **OrderID** 2, **OrderLine** 1, **FulfillmentQuantity** 5
  - **FulfillmentDate** 2 februari 2019, **FulfillmentID** 52, **OrderID** 1, **OrderLine** 1, **FulfillmentQuantity** 3
  - **FulfillmentDate** 1 januari 2019, **FulfillmentID** 53, **OrderID** 1, **OrderLine** 2, **FulfillmentQuantity** 10

Laten we eens kijken wat er gebeurt wanneer er een query op het model wordt uitgevoerd. Hier volgt een tabelvisual waarin de order- en leveringsaantallen worden vergelijken via de kolom **OrderID** van de tabel **Order**.

![Diagram met een tabelvisual met drie kolommen: OrderID, OrderQuantity en FulfillmentQuantity.](media/relationships-many-to-many/order-fulfillment-model-queried.png)

Het resultaat in de visual klopt. Het nut van het model is echter beperkt: u kunt alleen filteren of groeperen op de kolom **OrderID** van de tabel **Order**.

### <a name="relate-many-to-many-facts-guidance"></a>Richtlijnen voor het relateren van veel-op-veel-feiten

Over het algemeen is het niet aan te raden om twee feitentabellen rechtstreeks te relateren via veel-op-veel-kardinaliteit. De belangrijkste reden hiervoor is dat het model geen flexibiliteit biedt in de manieren waarop u het rapport kunt filteren of groeperen. In het voorbeeld is het alleen mogelijk om visuals te filteren of te groeperen op de kolom **OrderID** van de tabel **Order**. Een andere reden heeft betrekking op de kwaliteit van uw gegevens. Als er integriteitsproblemen zijn met uw gegevens, worden er tijdens het uitvoeren van query's mogelijk rijen weggelaten vanwege de aard van de _beperkte relatie_. Raadpleeg [Modelrelaties in Power BI Desktop (evaluatie van relaties)](../transform-model/desktop-relationships-understand.md#relationship-evaluation) voor meer informatie.

In plaats van feitentabellen te relateren, is het raadzaam om de ontwerpprincipes van [stervormige schema's](star-schema.md) te volgen. Dit doet u door dimensietabellen toe te voegen. De dimensietabellen zijn dan via een-op-veel-relaties gerelateerd aan de feitentabellen. Deze ontwerpbenadering is robuust vanwege de flexibele rapportageopties. U kunt filteren of groeperen met behulp van een van de dimensiekolommen en u kunt elke gerelateerde feitentabel samenvatten.

Laten we eens kijken naar een betere oplossing.

![Diagram met een model met zes tabellen: OrderLine, OrderDate, Order, Fulfillment, Product en FulfillmentDate.](media/relationships-many-to-many/order-fulfillment-model-improved.png)

Let op de volgende ontwerpwijzigingen:

- Het model bevat nu vier extra tabellen: **OrderLine**, **OrderDate**, **Product** en **FulfillmentDate**
- De vier extra tabellen zijn allemaal dimensietabellen, en met een-op-veel-relaties worden deze tabellen gekoppeld aan de feitentabellen
- De tabel **OrderLine** bevat de kolom **OrderLineID** met daarin de waarde van **OrderID** vermenigvuldigd met 100, plus de waarde **OrderLine**, een unieke id voor elke orderregel
- De tabellen **Order** en **Fulfillment** bevatten nu een kolom **OrderLineID** en bevatten niet meer de kolommen **OrderID** en **OrderLine**
- De tabel **Fulfillment** bevat nu de kolommen **OrderDate** en **ProductID**
- De tabel **FulfillmentDate** heeft alleen een relatie met de tabel **Fulfillment**
- Alle kolommen met unieke id's zijn verborgen

Het toepassen van de ontwerpprincipes van het stervormige schema biedt de volgende voordelen:

- Uw rapportvisuals zijn te _filteren of te groeperen_ op elke zichtbare kolom van de dimensietabellen
- In uw rapportvisuals zijn alle zichtbare kolommen van de feitentabellen _samen te vatten_
- Filters die worden toegepast op de tabellen **OrderLine**, **OrderDate** of **Product** worden doorgegeven aan beide feitentabellen
- Alle relaties zijn een-op-veel en elke relatie is een _normale relatie_. Problemen met gegevensintegriteit worden niet gemaskeerd. Raadpleeg [Modelrelaties in Power BI Desktop (evaluatie van relaties)](../transform-model/desktop-relationships-understand.md#relationship-evaluation) voor meer informatie.

## <a name="relate-higher-grain-facts"></a>Nauwkeurigere feiten relateren

Dit veel-op-veel-scenario is heel anders dan de twee die al eerder in dit artikel zijn beschreven.

Laten we eens kijken naar een voorbeeld met vier tabellen: **Date** (datum), **Sales** (verkoop), **Product** (product) en **Target** (doel). **Date** en **Product** zijn dimensietabellen en hebben een-op-veel-relaties met de feitentabel **Sales**. Tot nu toe is het een goed ontwerp voor een stervormig schema. De tabel **Target** moet echter nog worden gerelateerd aan de andere tabellen.

![Diagram met een model met vier tabellen: Date, Sales, Product en Target.](media/relationships-many-to-many/sales-targets-model-example.png)

De tabel **Target** bevat drie kolommen: **Category** (categorie), **TargetQuantity** (doelaantal) en **TargetYear** (doeljaar). De tabelrijen geven een granulariteit aan op jaar en productcategorie. Met andere woorden: doelen, waarmee de verkoopprestaties worden gemeten, worden elk jaar ingesteld voor elke productcategorie.

![Diagram met de Doeltabel met drie kolommen: TargetYear, Category en TargetQuantity.](media/relationships-many-to-many/sales-targets-model-target-rows.png)

Omdat in de tabel **Target** gegevens op een hoger niveau worden opgeslagen dan in de dimensietabellen, kan er geen een-op-veel-relatie worden gemaakt. Dat geldt althans voor een van de relaties. Laten we eens kijken hoe de tabel **Target** kan worden gerelateerd aan de dimensietabellen.

### <a name="relate-higher-grain-time-periods"></a>Nauwkeurigere perioden relateren

Een relatie tussen de tabellen **Date** en **Target** moet een een-op-veel-relatie zijn. De reden hiervoor is dat de waarden van de kolom **TargetYear** datums zijn. In dit voorbeeld is elke waarde van de kolom **TargetYear** de eerste datum van het doeljaar.

> [!TIP]
> Bij het opslaan van feiten met een hogere tijdgranulatie dan dag, stelt u het kolomgegevenstype in op **Datum** (of **Geheel getal** als u datumsleutels gebruikt). In de kolom slaat u een waarde op die de eerste dag van de tijdsperiode representeert. Een jaarperiode wordt bijvoorbeeld vastgelegd als 1 januari van dat jaar en een maandperiode als de eerste dag van die maand.

Zorg er echter voor dat de filters op maand- of datumniveau een zinvol resultaat opleveren. Zonder speciale berekeningslogica kan in visuals worden gerapporteerd dat de doeldatums letterlijk de eerste dag van elk jaar zijn. Alle andere dagen, plus alle maanden behalve januari, krijgen een leeg samengevat doelaantal.

In de volgende matrixvisual ziet u wat er gebeurt wanneer de rapportgebruiker de details van de maanden van een jaar weergeeft. In de visual wordt de kolom **TargetQuantity** samengevat. (De optie [Items zonder gegevens weergeven](../create-reports/desktop-show-items-no-data.md) is ingeschakeld voor de matrixrijen.)

![Diagram met een matrixvisual waarin het doelaantal van het jaar 2020 wordt weergegeven als 270.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

We raden u aan het samenvatten van uw feitgegevens te beheren met metingen om dit gedrag te voorkomen. Een van de manieren om de samenvatting te beheren, is BLANK (leeg) te retourneren als er een query wordt uitgevoerd op tijdsperioden van een lager niveau. Een andere manier, gedefinieerd met enige geavanceerde DAX, is het verdelen van waarden over perioden van een lager niveau.

Overweeg de volgende metingsdefinitie met de DAX-functie [ISFILTERED](/dax/isfiltered-function-dax). Er wordt alleen een waarde geretourneerd wanneer de kolommen **Date** of **Month** niet worden gefilterd.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

In de volgende matrixvisual is nu gebruikgemaakt van de meting **Target Quantity**. U ziet dat alle maandelijkse doelaantallen leeg zijn.

![Diagram met een matrixvisual waarin het doelaantal van het jaar 2020 wordt weergegeven als 270, met lege maandelijkse waarden.](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>Nauwkeuriger relateren (geen datums)

Er is een andere ontwerpbenadering nodig bij het relateren van een niet-datumkolom van een dimensietabel met die van een feitentabel (die ook nauwkeuriger is dan de dimensietabel).

De kolommen **Category** (van zowel de tabel **Product** als **Target**) bevatten dubbele waarden. Er is dus geen 'een' voor een een-op-veel-relatie. In dit geval moet u een veel-op-veel-relatie maken. Bij deze relatie moeten filters in één richting worden doorgeven, van de dimensietabel naar de feitentabel.

![Diagram met een model van de tabellen Doel en Product. Een veel-op-veel-relatie verbindt de twee tabellen.](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

Nu gaan we de tabelrijen bekijken.

![Diagram met een model met twee tabellen: Target en Product. Een veel-op-veel-relatie verbindt de twee Category-kolommen.](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

In de tabel **Target** bevinden zich vier rijen: twee rijen voor elk doeljaar (2019 en 2020) en twee categorieën (Clothing (kleding) en Accessories (accessoires)). Er zijn drie producten in de tabel **Product**. Twee behoren er tot de categorie kleding en een hoort er bij de categorie accessoires. Een van de kledingkleuren is groen en de resterende twee zijn blauw.

Het groeperen van een tabelvisual op de kolom **Category** van de tabel **Product** geeft het volgende resultaat.

![Diagram met een tabelvisual met twee kolommen: Category en TargetQuantity. Accessories is 60, Clothing is 40 en het totaal is 100.](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

Het resultaat in deze visual klopt. Laten we nu gaan kijken wat er gebeurt wanneer de kolom **Color** (kleur) van de tabel **Product** wordt gebruikt om het doelaantal te groeperen.

![Diagram met een tabelvisual met twee kolommen: Color en TargetQuantity. Blue (blauw) is 100,Green (groen) is 40 en het totaal is 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

In deze visual zijn de gegevens verkeerd weergegeven. Wat is hier gebeurd?

Een filter op de kolom **Color** van de tabel **Product** levert twee rijen op. Een van de rijen is voor de categorie Clothing en de andere is voor de categorie Accessories. Deze twee categoriewaarden worden doorgegeven als filters voor de tabel **Target**. Met andere woorden, omdat de kleur blauw wordt gebruikt door producten uit twee categorieën, worden _die categorieën_ gebruikt om de doelen te filteren.

Zoals eerder beschreven, is het raadzaam het samenvatten van uw feitgegevens te beheren met metingen om dit gedrag te voorkomen.

Denk eens na over de volgende metingsdefinitie. Zoals u ziet, worden alle kolommen van de tabel **Product** die zich onder het categorieniveau bevinden getest op filters.

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

In de volgende tabelvisual is nu gebruikgemaakt van de meting **Target Quantity**. U ziet dat alle kleurdoelaantallen leeg zijn.

![Diagram met een tabelvisual met twee kolommen: Color en TargetQuantity. Blue is leeg, Green is leeg en het totaal is 100.](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

Het uiteindelijke modelontwerp ziet er als volgt uit.

![Diagram met een model met de tabellen Datum en Doel die zijn gerelateerd via aan een een-op-veel-relatie.](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>Richtlijnen voor het relateren van nauwkeurigere feiten

Hier volgen richtlijnen voor het koppelen van een dimensietabel aan een feitentabel als in de feitentabel nauwkeurigere rijen worden opgeslagen dan in de dimensietabel:

- Voor nauwkeurigere datums:
  - Sla de eerste datum van de periode op in de feitentabel
  - Maak een een-op-veel-relatie tussen de datumtabel en de feitentabel
- Voor andere nauwkeurigere feiten:
  - Maak een veel-op-veel-relatie tussen de dimensietabel en de feitentabel
- Voor beide typen:
  - Beheer het samenvatten met metingslogica: retourneer BLANK als er dimensiekolommen van een lager niveau worden gebruikt om te filteren of te groeperen
  - Verberg samen te vatten kolommen van feitentabellen, zodat er alleen metingen kunnen worden gebruikt om de feitentabel samen te vatten

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Modelrelaties in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- [Meer informatie over stervormige schema's en het belang daarvan voor Power BI](star-schema.md)
- [Richtlijnen voor het oplossen van problemen met relaties](relationships-troubleshoot.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
