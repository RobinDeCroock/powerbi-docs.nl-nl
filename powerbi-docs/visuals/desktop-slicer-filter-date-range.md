---
title: Een relatieve datumslicer of -filter in Power BI gebruiken
description: Informatie over het gebruik van een slicer of filter om relatieve datumbereiken te beperken in Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: rien
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 09/09/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 8d83a2b655c7a4dd788e34ce5744daaac0f73f63
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397436"
---
# <a name="creating-a-relative-date-slicer-and-filter-in-power-bi"></a>Een relatieve datumslicer en -filter in Power BI maken

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Met de **relatieve datumslicer** of het **relatieve datumfilter** kunt u tijdgebaseerde filters toepassen op een datumkolom in het gegevensmodel. U kunt bijvoorbeeld de **relatieve datumslicer** gebruiken om alleen gegevens weer te geven over verkopen die hebben plaatsgevonden in de afgelopen 30 dagen (of maand, kalendermaanden enzovoort). Als u de gegevens vernieuwt, wordt de juiste relatieve datumbeperking automatisch toegepast door de relatieve periode.

![Schermopname van een rapport met een pijl die wijst naar de relatieve datumslicer.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-01.png)

Voor het delen van uw rapport met een Power BI-collega moeten u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in Premium-capaciteit.

## <a name="create-the-relative-date-range-slicer"></a>De slicer voor het relatieve datumbereik maken

U kunt de relatieve datumslicer net als elke andere slicer gebruiken. Maak een **slicer**-visual voor uw rapport en selecteer vervolgens een datumwaarde voor de waarde **Veld**. In de volgende afbeelding selecteerden we het veld *OrderDate*.

![Schermopname van het deelvenster Visualisaties met pijlen die wijzen op het pictogram voor de slicer en op het Veld.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-02.png)

Selecteer de slicer op uw canvas en vervolgens het dakje in de rechterbovenhoek van de visual van de slicer. Als de visual datumgegevens bevat, geeft het menu de optie voor **Relatief** weer.

![Schermopname van de slicer-visual met een kader rond het dakje en een pijl die wijst naar Relatief.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-03.png)

Selecteer *Relatief* voor de relatieve datumslicer.

Vervolgens kunt u de instellingen selecteren.

Voor de eerste instelling in de *relatieve datumslicer* hebt u de volgende opties:

![Schermopname van de relatieve configuratieopties, waarbij de eerste instelling is gemarkeerd.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04.png)

* Laatste
* Volgende
* Deze

Voor de tweede (middelste) instelling in de *relatieve datumslicer* kunt u een getal invoeren om het relatieve datumbereik te definiëren.

![Schermopname van de relatieve configuratieopties, waarbij de tweede instelling is gemarkeerd.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-04a.png)

Met de derde instelling kunt u de datummeting kiezen. U hebt de volgende opties:

![Schermopname van de relatieve configuratieopties, waarbij de derde instelling is gemarkeerd.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-05.png)

* Dagen
* Weken
* Weken (kalender)
* Maanden
* Maanden (kalender)
* Jaren
* Jaren (kalender)

Als u **Maanden** in die lijst selecteert en voor de middelste instelling *2* invoert, gebeurt het volgende:

* Als het vandaag 20 juli is,

    - worden in visuals die door de slicer zijn beperkt, gegevens weergegeven voor de vorige twee maanden,
    - vanaf 21 mei tot en met 20 juli (de datum van vandaag).

Ter vergelijking: als u *Maanden (kalender)* hebt geselecteerd, geven de visuele elementen die worden beperkt gegevens weer van 1 mei tot en met 30 juni (de laatste twee volledige kalendermaanden).

## <a name="create-the-relative-date-range-filter"></a>Het relatieve datumbereikfilter maken

U kunt ook een relatief datumbereikfilter voor uw rapportpagina of het hele rapport maken. Sleep daarvoor een datumveld naar het gebied **Filters op paginaniveau** of **Filters op rapportniveau** in het deelvenster **Veld**:

![Schermopname van het veld OrderDate dat naar het gebied Filters op paginaniveau wordt gesleept.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-06.png)

U kunt daar het relatieve datumbereik wijzigen. Dit is vergelijkbaar met de manier waarop u de **relatieve datumslicer** kunt aanpassen. Selecteer **Relatieve datumfilter** in de vervolgkeuzelijst **Filtertype**.

![Schermopname met de vervolgkeuzelijst voor het filtertype en de muisaanwijzer op Relatieve datumfilter.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-07.png)

Als u **Relatieve datumfilter** hebt geselecteerd, ziet u drie secties die u kunt wijzigen, inclusief een numeriek middelste vak, net als bij de slicer.

![Schermopname van de filters op rapportniveau, met pijlen die wijzen naar opties voor Items weergeven als de waarde.](media/desktop-slicer-filter-date-range/relative-date-range-slicer-filter-08.png)

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

De volgende beperkingen en overwegingen zijn momenteel van toepassing op de **relatieve datumbereikslicer** en het relatieve datumbereikfilter.

* Het gegevenstype voor het veld in de slicer moet een datum zijn en mag niet de standaard, tekst, zijn. Anders worden de relatieve opties niet weergegeven in de slicer.
* Gegevensmodellen in **Power BI** bevatten geen informatie over de tijdzone. De modellen kunnen tijden opslaan, maar er is geen indicatie van de tijdzone waarin ze zich bevinden.
* De slicer en het filter zijn altijd gebaseerd op de tijd in UTC. Als u een filter in een rapport instelt en het rapport naar een collega in een andere tijdzone stuurt, ziet u beide dezelfde gegevens. Tenzij u zich in de UTC-tijdzone bevindt, moeten u en uw collega rekening houden met de verschillen in tijd.
* U kunt gegevens die in een lokale tijdzone zijn vastgelegd, omzetten naar UTC met behulp van de **Query-editor**.

## <a name="next-steps"></a>Volgende stappen

- [Een relatieve tijdslicer en -filter in Power BI gebruiken](../create-reports/slicer-filter-relative-time.md)
- [Slicers in Power BI](power-bi-visualization-slicers.md)
