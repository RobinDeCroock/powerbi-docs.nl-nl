---
title: Werken met aggregaties (som, gemiddelde, enzovoort) in de Power BI-service
description: Leer hoe u de aggregatie in een grafiek kunt wijzigen (som, gemiddelde, maximum, enzovoort) in de Power BI-service.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/04/2019
ms.locfileid: "65710746"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Werken met aggregaties (som, gemiddelde, enzovoort) in de Power BI-service

## <a name="what-is-an-aggregate"></a>Wat is een statistische functie?

Soms wilt u de waarden in uw gegevens rekenkundig combineren. De rekenkundige bewerking kan een som, gemiddelde, maximum, aantal, enzovoort zijn. Wanneer u waarden in uw gegevens combineert, wordt dit *aggregeren* genoemd. Het resultaat van die rekenkundige bewerking is een *aggregatie*.

Wanneer Power BI-service en Power BI Desktop visualisaties maken, kunnen ze uw gegevens aggregeren. De aggregatie is vaak net wat u nodig hebt, maar soms wilt u de waarden op een andere manier aggregeren.  Bijvoorbeeld een som versus een gemiddelde. Er zijn verschillende manieren om de door Power BI gebruikte aggregatie in een visualisatie te beheren en wijzigen.

Laten we eerst kijken naar de *typen* gegevens, omdat het type gegevens bepaalt hoe, en of, deze gegevens kunnen worden geaggregeerd in Power BI.

## <a name="types-of-data"></a>Typen gegevens

De meeste gegevenssets hebben meer dan één type gegevens. Op het meest eenvoudige niveau zijn de gegevens numeriek of niet. Numerieke gegevens kunnen in Power BI worden geaggregeerd met behulp van een som, gemiddelde, aantal, minimum, afwijking en nog veel meer. Zelfs tekstgegevens, vaak *categorische* gegevens genoemd, kunnen worden geaggregeerd in de service. Als u probeert categorische velden te aggregeren door deze te plaatsen in een bucket met alleen numerieke waarden, zoals **Waarden** of **Tooltips**, wordt in Power BI geteld hoe vaak elke categorie voorkomt of hoeveel unieke exemplaren van elke categorie er zijn. Speciale typen gegevens, zoals datums, hebben enkele eigen aggregatieopties: oudste, nieuwste, eerste en laatste.

In het voorbeeld hieronder:

- zijn **Verkochte eenheden** en **Productieprijs** kolommen die numerieke gegevens bevatten

- bevatten **Segment**, **Land**, **Product**, **Maand** en **Naam van de maand** categorische gegevens

   ![Schermopname van een voorbeeldgegevensset.](media/service-aggregates/power-bi-aggregate-chart.png)

Wanneer u een visualisatie maakt in Power BI, worden numerieke velden geaggregeerd (de standaardwaarde is *som*) via een categorisch veld.  Bijvoorbeeld 'Verkochte eenheden ***per Product***', 'Verkochte eenheden ***per Maand***' en 'Productieprijs ***per Segment***'. In Power BI worden sommige numerieke velden aangeduid als **metingen**. U kunt metingen eenvoudig herkennen in de Power BI-rapporteditor. In de lijst **Velden** worden metingen weergegeven met het symbool ∑ ernaast. Zie [De rapporteditor... een rondleiding volgen](service-the-report-editor-take-a-tour.md) voor meer informatie.

![Schermopname van Power BI met de lijst Velden uitgelicht.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Waarom werken de statische functies niet zoals ik wil?

Het werken met aggregaties in Power BI-service kan verwarrend zijn. Misschien hebt u een numeriek veld en is het niet mogelijk de aggregatie te wijzigen in Power BI. Of misschien hebt u een veld, zoals een jaar, en wilt u dit niet aggregeren, omdat u alleen wilt tellen hoe vaak het jaar voorkomt.

Meestal is de velddefinitie in de gegevensset het onderliggende probleem. Misschien heeft de eigenaar van de gegevensset het veld gedefinieerd als tekst en kan er daarom geen som of gemiddelde van worden berekend in Power BI. Helaas kan [alleen de eigenaar van de gegevensset wijzigen hoe een veld is gecategoriseerd](desktop-measures.md). Als u dus eigenaarsmachtigingen hebt voor de gegevensset, in Desktop of het programma dat is gebruikt om de gegevensset te maken (bijvoorbeeld Excel), kunt u dit probleem oplossen. Anders moet u contact opnemen met de eigenaar van de gegevensset voor hulp.  

Aan het eind van dit artikel is er een speciale sectie, [**Aandachtspunten en probleemoplossing**](#considerations-and-troubleshooting). Hier vindt u tips en richtlijnen. Als u daar het antwoord niet vindt, kunt u uw vraag posten in het [Power BI-communityforum](http://community.powerbi.com). U krijgt een snelle reactie, rechtstreeks van het Power BI-team.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Wijzigen hoe een numeriek veld wordt samengevoegd

Stel u hebt een diagram waarin de verkochte eenheden voor de verschillende producten wordt opgesomd, maar u hebt liever het gemiddelde.

1. Maak een **Gegroepeerd kolomdiagram** met een meting en een categorie. In dit voorbeeld gebruiken we Verkochte eenheden per product.  In Power BI wordt standaard een grafiek gemaakt waarin de som van de verkochte eenheden wordt berekend (sleep de meting naar de bron **Waarde**) voor elk product (sleep de categorie naar de bron **As**).

   ![Schermopname van de grafiek, het deelvenster Visualisaties en de lijst Velden met Som uitgelicht.](media/service-aggregates/power-bi-aggregate-sum.png)

1. Klik in het deelvenster **Visualisaties** met de rechtermuisknop op de meting en selecteer het aggregatietype dat u nodig hebt. In dit geval selecteren we **Gemiddelde**. Als u de benodigde aggregatie niet ziet, raadpleegt u de sectie [**Aandachtspunten en probleemoplossing**](#considerations-and-troubleshooting).

   ![Schermopname van de aggregatielijst met Gemiddelde geselecteerd en uitgelicht.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > De beschikbare opties in de vervolgkeuzelijst variëren, afhankelijk van 1) het geselecteerde veld en 2) de wijze waarop de eigenaar van de gegevensset dat veld heeft gecategoriseerd.

1. De visualisatie gebruikt nu geaggregeerd op gemiddelde.

   ![Schermopname van de grafiek waarop nu het Gemiddelde van Verkochte eenheden per product wordt weergegeven.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Manieren om uw gegevens te aggregeren

Enkele opties die beschikbaar zijn voor de aggregatie van een veld:

- **Niet samenvatten**. Wanneer u deze optie kiest, wordt elke waarde in dat veld afzonderlijk verwerkt en niet samengevat in Power BI. Gebruik deze optie als er een numerieke id-kolom is die niet mag worden opgeteld.

- **Som**. Hiermee worden alle waarden in het veld opgeteld.

- **Gemiddelde**. Hiermee wordt het rekenkundige gemiddelde van de waarden berekend.

- **Minimum**. Geeft de kleinste waarde.

- **Maximum**. Geeft de grootste waarde.

- **Aantal (niet leeg)** . Hiermee wordt het aantal niet-lege waarden in het veld geteld.

- **Aantal (uniek)** . Hiermee wordt het aantal verschillende waarden in het veld geteld.

- **Standaarddeviatie**.

- **Afwijking**.

- **Mediaan**.  Hiermee wordt de mediaanwaarde (middelste waarde) weergegeven. Deze waarde heeft hetzelfde aantal boven- als onderliggende items.  Als er twee medianen zijn, wordt het gemiddelde hiervan genomen.

Neem bijvoorbeeld de volgende gegevens:

| Land | Bedrag |
|:--- |:--- |
| VS |100 |
| VK |150 |
| Canada |100 |
| Duitsland |125 |
| Frankrijk | |
| Japan |125 |
| Australië |150 |

Dit voorbeeld geeft de volgende resultaten:

- **Niet samenvatten**: elke waarde wordt afzonderlijk weergegeven

- **Som**: 750

- **Gemiddelde**: 125

- **Maximum**:  150

- **Minimum**: 100

- **Aantal (niet leeg)** : 6

- **Aantal (uniek)** : 4

- **Standaardafwijking**: 20,4124145...

- **Afwijking**: 416,666...

- **Mediaan**: 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Een statistische functie maken met een categorieveld (tekst)

U kunt ook een niet-numeriek veld aggregeren. Als u bijvoorbeeld een veld Productnaam hebt, kunt u dit toevoegen als een waarde en vervolgens instellen op **Aantal**, **Uniek aantal**, **Eerste** of **Laatste**.

1. Sleep het veld **Product** naar de bron **Waarden**. De bron **Waarden** wordt gewoonlijk gebruikt voor numerieke velden. Power BI herkent dat dit veld een tekstveld is, stelt de aggregatie in op **Niet samenvatten** en presenteert een tabel met één kolom.

   ![Schermopname van het veld Product in de bron Waarden.](media/service-aggregates/power-bi-aggregate-value.png)

1. Als u de aggregatie van de standaardwaarde **Niet samenvatten** wijzigt in **Aantal (uniek)** , wordt het aantal verschillende producten in Power BI geteld. In dat geval zijn dat er vier.
  
   ![Schermopname van het aantal unieke producten.](media/service-aggregates/power-bi-aggregate-count.png)

1. En als u wijzigt de aggregatie wijzigt in **Aantal**, wordt het totale aantal in Power BI geteld. In dit geval zijn er zeven vermeldingen voor **Product**.

   ![Schermopname van het aantal producten.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Door hetzelfde veld (in dit geval **Product**) naar de bron **Waarden** te slepen en de standaardaggregatie **Niet samenvatten** te laten staan, geeft Power BI een uitsplitsing van het aantal op product.

   ![Schermopname van het product en het aantal producten.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing

V:  Waarom beschik ik niet over de optie **Niet samenvatten**?

A:  Het veld dat u hebt geselecteerd, is waarschijnlijk een berekende meting of een geavanceerde meting die in Excel of in [Power BI Desktop](desktop-measures.md) is gemaakt. Elk berekende meting heeft een eigen in code vastgelegde formule. U kunt de aggregatie waarvan Power BI gebruikmaakt niet wijzigen. Als het bijvoorbeeld een som is, kan deze alleen een som zijn. In de lijsten **Velden** worden *berekende maateenheden* weergegeven met het calculatorsymbool.

V:  Mijn veld **is** numeriek, waarom kan ik alleen kiezen uit **Aantal** en **Uniek aantal**?

A1:  Waarschijnlijk heeft de eigenaar van de gegevensset het veld *niet* geclassificeerd als een getal. Als een gegevensset bijvoorbeeld een veld **Jaar** heeft, kan de eigenaar van de gegevensset de waarde als tekst categoriseren. De kans is groot dat in Power BI het veld **Jaar** wordt geteld (bijvoorbeeld het aantal mensen dat is geboren in 1974). Het is minder waarschijnlijk dat de som of het gemiddelde ervan wordt berekend. Als u de eigenaar bent, kunt u de gegevensset openen in Power BI Desktop en het tabblad **Modelleren** gebruiken om het gegevenstype te wijzigen.

A2: Als het veld een calculatorpictogram heeft, betekent dit dat het een *berekende maateenheid*is. Elke berekende maateenheid heeft een eigen, in code vastgelegde formule die alleen door de eigenaar van de gegevensset kan worden gewijzigd. De berekening die in Power BI wordt gebruikt, kan een eenvoudige aggregatie zijn, zoals een gemiddelde of som. Er kunnen ook complexe berekeningen worden gebruikt, zoals een percentage van de bijdrage aan de bovenliggende categorie of het voorlopige totaal vanaf het begin van het jaar. Er wordt in Power BI geen som of gemiddelde van de resultaten berekend. In plaats daarvan wordt er voor elk gegevenspunt opnieuw een berekening uitgevoerd (met behulp van de in code vastgelegde formule).

A3:  Een andere mogelijkheid is dat u het veld in een *bucket* hebt geplaatst waarin allee alleen categorische waarden zijn toegestaan.  In dat geval beschikt u alleen over de opties Aantal en Uniek aantal.

A4:  En een vierde mogelijkheid is dat u het veld gebruikt voor een as. Er wordt in Power BI bijvoorbeeld één staaf voor elke afzonderlijke waarde weergegeven op de as van een staafdiagram. De veldwaarden worden niet samengevoegd.

>[!NOTE]
>Spreidingsdiagrammen vormen een uitzondering op deze regel. Deze diagrammen *vereisen* geaggregeerde waarden voor de x- en y-as.

V:  Waarom kan ik geen tekstvelden optellen voor SSAS-gegevensbronnen (SQL Server Analysis Services)?

A:  Met liveverbindingen met multidimensionale SSAS-modellen kunnen geen aggregaties aan de clientzijde worden uitgevoerd, waaronder eerste, laatste, gemiddelde, minimum, maximum en som.

V:  Ik heb een spreidingsdiagram en ik wil *niet* dat mijn veld wordt geaggregeerd.  Hoe?

A:  Voeg het veld toe aan de bucket **Details** en niet aan de bucket van de x- of y-as.

V:  Wanneer ik een numeriek veld aan een visualisatie toevoeg, wordt meestal de som weergegeven, maar soms wordt ook het gemiddelde, het aantal of een andere aggregatie weergegeven.  Waarom is de standaardaggregatie niet altijd hetzelfde?

A:  Eigenaren van gegevenssets kunnen de standaardsamenvatting voor elk veld instellen. Als u eigenaar van een gegevensset bent, kunt u de standaardsamenvatting wijzigen op het tabblad **Modelleren** van Power BI Desktop.

V:  Ik ben de eigenaar van een gegevensset en ik wil er voor zorgen dat een veld nooit wordt samengevoegd.

A:  In Power BI Desktop kunt u op het tabblad **Model maken** de optie **Gegevenstype** instellen op **Tekst**.

V:  De optie **Niet samenvatten** wordt niet weergegeven in mijn vervolgkeuzelijst.

A:  Verwijder het veld en voeg het vervolgens opnieuw toe.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)