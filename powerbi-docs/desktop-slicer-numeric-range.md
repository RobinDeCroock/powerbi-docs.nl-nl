---
title: De slicer voor numeriek bereik in Power BI Desktop gebruiken
description: Informatie over het gebruik van een slicer voor het beperken van numerieke bereiken in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/02/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 68467894850248d6acb841dc2ed651f595f19b95
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61363392"
---
# <a name="use-the-numeric-range-slicer-in-power-bi-desktop"></a>De slicer voor numeriek bereik in Power BI Desktop gebruiken
Met de **slicer voor numeriek bereik**, kunt u allerlei filters toepassen op een van de numerieke kolommen in het gegevensmodel. U kunt er voor kiezen om te filteren **tussen** getallen, **minder dan of gelijk aan** een getal of **groter dan of gelijk aan** een getal. Hoewel dit eenvoudig klinkt, is het een zeer krachtige manier om uw gegevens te filteren.

![Visual met slicer voor numeriek bereik](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-0.png)

## <a name="using-the-numeric-range-slicer"></a>De slicer voor numeriek bereik gebruiken
U kunt de slicer voor numeriek bereik net als elke andere slicer gebruiken. Maak eenvoudig een visueel **slicer**-element voor uw rapport en selecteer vervolgens een numerieke waarde voor de waarde **Veld**. In de volgende afbeelding is het veld *LineTotal* geselecteerd.

![Een slicer voor numeriek bereik maken](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-1-create.png)

Selecteer koppeling met de pijl-omlaag in de rechterbovenhoek van de **slicer voor numerik bereik**. Er wordt een menu weergegeven.

![Menu met slicer voor numeriek bereik](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-2-between.png)

Voor het numerieke bereik kunt u een keuze maken uit de volgende drie opties:

* Tussen
* Kleiner dan of gelijk aan
* Groter dan of gelijk aan

Wanneer u **Tussen** selecteert in het menu, wordt een schuifregelaar weergegeven en kunt u filteren op numerieke waarden die tussen de getallen liggen. Naast het gebruik van de schuifregelaar zelf, kunt u ook in een vak klikken en de waarden typen. Dit is handig wanneer u wilt slicen op specifieke getallen, maar de granulatie van het bewegen van de slicerbalk maakt het lastig om precies op dat getal te belanden.

In de volgende afbeelding is de rapportpagina gefilterd voor *LineTotal*-waarden binnen een bereik van 2500.00 tot 6000.00.

![Slicer met numeriek bereik met Tussen](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-3-between-range.png)

Wanneer we **Kleiner dan of gelijk aan** selecteren, verdwijnt het besturingselement links (lagere waarde) van de schuifregelaar en kan alleen de bovengrens van de schuifregelaar worden aangepast. In de volgende afbeelding is het maximum van de schuifregelaar ingesteld op 5928.19.

![Slicer met numeriek bereik met Kleiner dan](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-4-less-than.png)

Ten slotte, als we **Groter dan of gelijk aan** selecteren, verdwijnt het besturingselement rechts van de schuifregelaar en kunnen we de lagere waarde aanpassen, zoals op de volgende afbeelding te zien is. Nu worden alleen items met een *LineTotal* meer of gelijk aan 4902.99 weergegeven in de visuele elementen op de rapportpagina.

![Slicer met numeriek bereik met Groter dan](media/desktop-slicer-numeric-range/desktop-slicer-numeric-range-5-greater-than.png)

## <a name="snap-to-whole-numbers-with-the-numeric-range-slicer"></a>Uitlijnen op hele getallen met de slicer met numeriek bereik

Een slicer met numeriek bereik lijnt uit op gehele getallen als het gegevenstype van het onderliggende veld **Geheel getal** is. Hierdoor kan uw slicer foutloos uitlijnen op gehele getallen. Met velden van het type **Decimaal getal** kunt u fracties van een getal invoer. De opmaak die is toegepast op het tekstvak komt overeen met de opmaak van het veld, hoewel u ook preciezere getallen kunt invoeren of selecteren.

## <a name="display-formatting-with-the-date-range-slicer"></a>Opmaak weergeven met de slicer voor het datumbereik

Wanneer u een slicer gebruikt om een datumbereik weer te geven of in te stellen, wordt de datumnotatie altijd weergegeven met behulp van de notatie **Korte datum**, op basis van de lokale instellingen van de browser of het besturingssysteem van de gebruiker. Dit is de weergavenotatie, ongeacht de instellingen voor het gegevenstype voor de onderliggende gegevens of het onderliggende model. 

U kunt bijvoorbeeld een lange datumnotatie gebruiken voor het onderliggende gegevenstype (zoals *dddd, d MMMM, jjjj*. Hiermee wordt de datum in andere visuals of in andere situaties weergegeven als *Woensdag, 14 maart 2001*), maar in de datumbereikslicer zou die datum worden weergegeven als *14/03/2001*.

Door de **Korte datumnotatie** in de slicer weer te geven, blijft de lengte van de tekenreeks consistent en compact in de slicer. 


## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen
De volgende beperkingen en overwegingen zijn momenteel van toepassing op de **slicer met numeriek bereik**:

* De **slicer voor numeriek bereik** filtert momenteel elke onderliggende rij in de gegevens, geen statische waarden. Als bijvoorbeeld een veld *Verkoopbedrag* wordt gebruikt, wordt elke transactie op basis van *Verkoopbedrag* gefilterd, niet de som van *Verkoopbedrag* voor elk gegevenspunt van een visueel element.
* Dit werkt momenteel niet met Measures.
* U kunt een willekeurig getal invoeren in de tekstvakken van een slicer met numeriek bereik, zelfs als dit getal buiten het bereik van de waarden in de onderliggende kolom ligt. Hiermee kunt u filters instellen als u weet dat de gegevens in de toekomst kunnen veranderen.
