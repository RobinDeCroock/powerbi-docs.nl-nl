---
title: Lijndiagrammen in Power BI
description: Lijndiagrammen in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0f430747187729cbb939b67795ff0507770bb0f1
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867019"
---
# <a name="line-charts-in-power-bi"></a>Lijndiagrammen in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

Een lijndiagram is een reeks gegevenspunten die door punten weergegeven en door rechte lijnen verbonden worden. Een lijndiagram kan één of meerdere lijnen hebben. Lijndiagrammen hebben een X- en een Y-as. 

![eenvoudig lijndiagram](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>Een lijndiagram maken
Deze instructies gebruiken de app 'Voorbeeld van verkoop en marketing' om een lijndiagram te maken dat de verkopen van dit jaar per categorie weergeeft. Als u mee wilt doen, kunt u de voorbeeld-app downloaden vanaf appsource.com.

> [!NOTE]
> Voor het delen van uw rapport met een Power BI-collega moeten u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in Premium-capaciteit.

1. Begin op een nieuwe, lege rapportpagina. Als u de Power BI-service gebruikt, moet u het rapport openen in de [Bewerkingsweergave](../service-interact-with-a-report-in-editing-view.md).

2. Selecteer in het deelvenster Velden de opties **Verkoopgegevens** \> **Totaal aantal eenheden**, en selecteer **Datum** > **Maand**.  Power BI maakt een kolomdiagram op uw rapportcanvas.

    ![Selecteer deze uit het deelvenster Velden.](media/power-bi-line-charts/power-bi-step1.png)

4. Converteer het kolomdiagram naar een lijndiagram door het lijndiagramsjabloon te selecteren uit het deelvenster Visualisaties. 

    ![omzetten naar lijndiagram](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. Filter uw lijndiagram om gegevens weer te geven voor de jaren 2012-2014. Als uw filterdeelvenster is samengevouwen, vouw het dan nu uit. Selecteer in het deelvenster Velden **Datum** \> **Jaar**, en sleep dit naar het deelvenster Filters. Zet het neer onder het kopje **Filters op dit visuele element**. 
     
    ![lijn naast het deelvenster Velden](media/power-bi-line-charts/power-bi-year-filter.png)

    Wijzig **Geavanceerd filters** naar **Basisfilters** en selecteer **2012**, **2013** en **2014**.

    ![filteren op jaar](media/power-bi-line-charts/power-bi-filter-year.png)

6. U kunt desgewenst [de grootte en de kleur van de tekst van de grafiek aanpassen](power-bi-visualization-customize-title-background-and-legend.md). 

    ![Tekengrootte vergroten en lettertype Y-as wijzigen](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>Extra lijnen aan het diagram toevoegen
Lijndiagrammen kunnen veel verschillende lijnen bevatten. En in sommige gevallen zijn de waarden op de lijnen zo uiteenlopend dat ze samen niet overzichtelijk kunnen worden weergegeven. Laten we eens kijken naar het toevoegen van extra lijnen aan ons huidige diagram. We kunnen leren hoe we ons diagram moeten opmaken wanneer de waarden in de lijnen zeer verschillend zijn. 

### <a name="add-additional-lines"></a>Extra lijnen toevoegen
Het totaalaantal eenheden voor alle regio’s staat nu in één enkele lijn in het de diagram, maar in plaats daarvan kunnen we dit totaalaantal ook per regio uitsplitsen. Voeg extra lijnen toe door **Geo** > **Regio** ook naar de legenda te slepen.

   ![Aparte lijn per regio](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>Twee Y-assen gebruiken
Wat als u de totale verkoop en het totaalaantal eenheden in één diagram wilt bekijken? De verkoopcijfers zijn veel hoger dan de eenheidsnummers, waardoor het lijndiagram eigenlijk onbruikbaar wordt. De rode lijn voor het totaalaantal eenheden lijkt de hele tijd rond nul te liggen.

   ![sterk uiteenlopende waarden](media/power-bi-line-charts/power-bi-diverging.png)

Om sterk uiteenlopende waarden in één diagram weer te geven, gebruikt u een combinatiegrafiek. Meer informatie over combinatiegrafieken vindt u in [Combinatiegrafieken in Power BI](power-bi-visualization-combo-chart.md). In het onderstaande voorbeeld kunnen we de verkoop en het totaalaantal eenheden samen in één diagram weergeven door een tweede Y-as toe te voegen. 

   ![sterk uiteenlopende waarden](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren
Zie [Een filter aan een rapport toevoegen](../power-bi-report-add-filter.md) voor meer informatie over het gebruik van het deelvenster Filters.

Selectie van een gegevenspunt in een lijndiagram leidt tot een kruislingse markering en filtering van de andere visualisaties op de rapportpagina, en vice versa. Als u mee wilt doen, opent u het tabblad **Marktaandeel**.  

Op een lijndiagram is elk afzonderlijk gegevenspunt het snijpunt van een punt op de X-as en de Y-as. Wanneer u een gegevenspunt selecteert, voegt Power BI markeringen toe die aangeven welk punt (voor een enkele lijn) of welke punten (als er twee of meer lijnen zijn) de bron zijn voor het kruislings markeren en filteren van de andere visuele elementen op de rapportagepagina. Als uw visuele element zeer compact en vol is, zal Power BI het dichtstbijzijnde punt selecteren waar u op het visuele element klikt.

In dit voorbeeld hebben we een gegevenspunt geselecteerd dat het volgende omvat: juli 2014, %eenheden marktaandeel R12 van 33,16 en %eenheden marktaandeel van 34,74.

![afzonderlijk gegevenspunt op in een lijndiagram selecteren](media/power-bi-line-charts/power-bi-single-select.png)

Merk op hoe het kolomdiagram kruislings wordt gemarkeerd en hoe de meter kruislings wordt gefilterd.

Zie [Visualisatie-interacties in een Power BI-rapport](../service-reports-visual-interactions.md) als u wilt beheren hoe grafieken elkaar kruislings markeren en filteren.

## <a name="considerations-and-troubleshooting"></a>Aandachtspunten en probleemoplossing
* Eén lijndiagram kan geen dubbele Y-as hebben.  In plaats daarvan moet u een combinatiegrafiek gebruiken.
* In de bovenstaande voorbeelden zijn de diagrammen als volgt opgemaakt: grotere tekengrootte, andere tekstkleur, astitels toegevoegd, diagramtitel en -legenda gecentreerd, beide assen op nul beginnen, en nog meer. Het deelvenster Opmaak (pictogram met verfroller) bevat een vrijwel eindeloze reeks opties om uw diagrammen eruit te laten zien zoals u dat wilt. De beste manier om hiermee te leren omgaan, is het deelvenster Opmaak openen en dit verder te verkennen.

## <a name="next-steps"></a>Volgende stappen

[Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)


