---
title: Kleine veelvouden in Power BI maken (preview)
description: Met kleine veelvouden of trellising kunt u een visueel element splitsen in meerdere versies van zichzelf, naast elkaar weer gegeven, met de gegevens die zijn gepartitioneerd in deze versies door middel van een gekozen dimensie.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: bc1f890e588227f9d0dc30202474a8f77f93fc38
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617343"
---
# <a name="create-small-multiples-in-power-bi-preview"></a>Kleine veelvouden in Power BI maken (preview)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Met kleine veelvouden of trellising splitst u een visueel element in meerdere versies van zichzelf. De versies worden naast elkaar weer gegeven, met gegevens die in deze versies zijn onderverdeeld door een gekozen dimensie. Zo kan een kleine veelvoud bijvoorbeeld een kolom diagram ' omzet per categorie ' splitsen over product lijnen of regio's. In deze preview-periode hebben kleine veelvouden een kleine set mogelijkheden, met meer informatie in latere versies.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Scherm opname van kleine veelvouden voor categorie en regio.":::

## <a name="enable-the-preview-feature"></a>De preview-functie inschakelen

Klik in het menu **bestand** op **Opties en instellingen**  >  **Opties**  >  **Preview-functies** en schakel het selectie vakje **kleine veelvouden** in.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-enable-preview.png" alt-text="Schakel de preview-versie in voor kleine veelvouden.":::

Start Power BI Desktop opnieuw op en u bent klaar om kleine veelvouden te proberen.

## <a name="create-small-multiples"></a>Kleine veelvouden maken

Op dit moment kunt u kleine veelvouden maken op staaf-, kolom-, lijn-en vlak diagrammen. 

Om aan de slag te gaan, maakt u een van de bovenstaande visuals en kiest u een veld waarmee u de gegevens wilt partitioneren. Sleep dat veld naar **kleine veelvouden** goed in het gedeelte velden van het deel venster visualisaties. Uw grafiek wordt gesplitst in een raster van 2 × 2, met de gegevens die zijn verdeeld over de gekozen dimensie. Het raster wordt gevuld met de kleine veelvouden grafieken. Ze worden gesorteerd op de gekozen sorteer volgorde, van links naar rechts en vervolgens van boven naar beneden.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-two-by-two-grid.png" alt-text="Kleine veelvouden in een raster met twee, twee.":::

U ziet dat de assen zijn gesynchroniseerd. Er bevindt zich één Y-as aan de linkerkant van elke rij en één X-as aan de onderkant van elke kolom.

Nu u kleine veelvouden hebt gemaakt, raadpleegt u hoe u [communiceert met kleine veelvouden in Power bi (preview)](power-bi-visualization-small-multiples-interact.md).

## <a name="format-a-small-multiples-visual"></a>Een kleine veelvouden Visual opmaken

Met een aantal nieuwe opties in het deel venster opmaak kunt u het uiterlijk van het raster beheren.

### <a name="change-the-grid-dimensions"></a>De raster afmetingen wijzigen

U kunt de afmetingen van het raster wijzigen op de kaart met de raster indeling:

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-grid-layout-card.png" alt-text="Indelings kaart voor klein meerdere rasters.":::

De standaard waarde is een raster van 2 × 2 met kleine veelvouden, maar u kunt het aantal rijen en kolommen aanpassen tot 6 × 6. Eventuele veelvouden die niet in dat raster passen, worden geladen terwijl u omlaag schuift.


### <a name="adjust-the-small-multiples-titles"></a>De kleine veelvouden titels aanpassen

Net als bij andere visuele titels kunt u de stijl en positie van de kleine veelvouden aanpassen op de **kleine** kaart met meerdere titels.

## <a name="preview-limitations"></a>Preview-beperkingen

Hoewel de functie in preview is, werken we voortdurend goed samen met de rest van onze functies. Hier volgen enkele actuele beperkingen.

### <a name="fields-pane"></a>Deelvenster Velden

- Datum en andere doorlopende hiërarchieën: Stel dat u een visueel element hebt als een lijn diagram met een datum hiërarchie in de X-as. Wanneer u kleine veelvouden uit het diagram maakt, wordt deze door Power BI geconverteerd van een doorlopend naar een categorische-as.
- Items zonder gegevens weer geven: de optie bestaat nog steeds, maar het gedrag kan niet worden uitgelijnd met uw verwachtingen.

### <a name="visual-interactions"></a>Visualinteracties

- Schuif omlaag om meer te laden op de categorische-as: in standaard visuals met veel categorieën in de as, wanneer u naar het einde van de as schuift, worden er meer categorieën geladen in de Visual. Op dit moment worden er in een klein aantal veelvouden niet meer categorieën geladen.
- Kleine veelvouden sorteren op meting: sorteren op kleine veelvouden is nieuwe functionaliteit. Mogelijk verwacht u dat u uw kleine veelvouden wilt sorteren op basis van een meting. Op dit moment kunt u alleen uw veelvouden sorteren op de natuurlijke sorteer volgorde van het veld.
- Klik met de rechter muisknop/context menu-> analyse: nu uitgeschakeld.
- Klik met de rechter muisknop/context menu-> samenvatten: nu uitgeschakeld.
- Meerdere gegevens punten selecteren met rechthoekige selectie: uitgeschakeld voor nu.
- Zoomen assen: nu uitgeschakeld.
- Toegankelijkheid: u kunt toetsenbord navigatie en scherm info aanpassen zodat de nieuwe ' grid-laag beter wordt ondersteund door kleine veelvouden naar visuals. Er ontbreekt een bepaald gedrag, zoals het toetsen bord navigeren via de ScrollBar van de categorische-as.

### <a name="formatting-options"></a>Opmaakopties

**Algemeen**

- Wissel knop voor reageren: de optie bestaat nog steeds, maar het gedrag kan niet worden uitgelijnd met uw verwachtingen. Omdat veel mobiele accommodaties zijn gekoppeld aan deze wissel knop, komt de mobiele ervaring ook overeen met de ervaring die u vindt in Power BI Desktop en de Power BI-service.
- Sampling van hoge dichtheid: voor lijn diagrammen is de steek proef met hoge dichtheid nog steeds aanwezig, maar deze wordt momenteel niet ondersteund door kleine veelvouden.

**As**

- Labels samen voegen: momenteel uitgeschakeld.

**Totaal aantal labels**

- Totaal aantal labels voor gestapelde grafieken: momenteel uitgeschakeld.

**Zoom schuifregelaar**

- Zoom schuifregelaars: momenteel uitgeschakeld.

**Deel venster analyse** 

- Trend lijnen: momenteel uitgeschakeld.
- Prognose: momenteel uitgeschakeld.

Dynamische opmaak voor labels markeren: momenteel niet ondersteund.
Beschikbaarheid van de service

## <a name="authoring-in-the-power-bi-service"></a>Ontwerpen in de Power BI-service

Het is niet mogelijk om kleine veelvouden te ontwerpen op het web terwijl de functie in preview is. U kunt een rapport met een kleine veelvouden visueel weer geven en het visuele element zelfs opmaken. U kunt een standaard visuele element echter niet converteren naar een klein aantal veelvouden in de Power BI-service. Een visueel element heeft al een veld in het veld met kleine veelvouden, of de kleine veelvouden worden niet weer gegeven voor dat visuele element.

## <a name="share-your-feedback"></a>Uw feedback delen

Laat ons weten wat het visuele element van meerdere veelvouden is:

- [Power BI-community](https://community.powerbi.com/)
- [Pagina ideeën Power BI](https://ideas.powerbi.com/ideas/) 

## <a name="next-steps"></a>Volgende stappen

[Interactie met kleine veelvouden in Power BI (preview-versie)](power-bi-visualization-small-multiples-interact.md)
