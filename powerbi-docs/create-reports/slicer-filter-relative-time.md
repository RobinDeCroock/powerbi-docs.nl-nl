---
title: Een relatieve tijdslicer of -filter in Power BI gebruiken
description: Informatie over het gebruik van een slicer of filter om relatieve tijdsbereiken te beperken in Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: a8268af76472c91474f2f67bc256fcc0ddcc9768
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669219"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Een relatieve tijdslicer en -filter in Power BI gebruiken

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Met de snelle opkomst van scenario's waarin snel vernieuwen is vereist, kan de mogelijkheid om te filteren op een kleinere tijdperiode nuttig zijn. Met de relatieve tijdslicer of het relatieve tijdfilter kunt u tijdgebaseerde filters toepassen op een datum- of tijdkolom in uw gegevensmodel. U kunt de slicer voor relatieve tijd bijvoorbeeld gebruiken om alleen videoweergaven van de afgelopen minuut of het afgelopen uur weer te geven. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Schermopname van voorbeeld van relatieve tijd.":::

U hoeft de functie niet te gebruiken in combinatie met de functie voor het [automatisch vernieuwen van pagina's](../create-reports/desktop-automatic-page-refresh.md). Veel scenario's voor relatieve tijd gaan echter goed samen met de functie voor het automatisch vernieuwen van pagina's.  

> [!NOTE]
> Wanneer u een filter of slicer voor relatieve tijd op het niveau van de pagina of het rapport toepast, worden alle visuals op die pagina of in dat rapport gefilterd op exact hetzelfde tijdsbereik met behulp van een gedeelde *anker* tijd. Omdat visuals iets verschillende uitvoeringstijden kunnen hebben, zorgt deze gedeelde ankertijd ervoor dat visuals worden gesynchroniseerd op uw hele pagina of in uw hele rapport. Lees meer over [ankertijd](#understanding-anchor-time) in dit artikel.

## <a name="create-a-relative-time-slicer-or-filter"></a>Een relatieve tijdslicer of -filter maken

Nadat u de functie hebt ingeschakeld, kunt u het datum- of tijdveld slepen en dit op de veldbron van een slicer neerzetten, of in het neerzetgebied in het deelvenster Filters. 

### <a name="create-a-slicer"></a>Een slicer maken

1. Sleep een datum- of tijdveld naar het canvas.

2. Selecteer het visualisatietype **Slicer**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Schermopname van het maken van een tijdslicer.":::

### <a name="create-a-filter"></a>Een filter maken
 
- Sleep een datum- of tijdveld naar het deelvenster Filters, voor **deze visual**, **deze pagina** of **alle pagina's**.

### <a name="set-relative-time"></a>Relatief tijd instellen 

Vervolgens wijzigt u het filtertype in **Relatieve tijd**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Schermopname van wijzigen naar relatieve tijd.":::
 
Hier ziet u hoe het eruit ziet in een slicer:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Schermopname van relatieve tijd in een slicer.":::

Hier ziet u hoe het eruit ziet op een filterkaart: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Schermopname van relatieve tijd in een filter.":::
 
Met dit nieuwe filtertype kan u filteren op basis van **Laatste**, **Volgende** of **Deze tijdsperiode**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Schermopname van het kiezen van Laatste, Volgende of Deze tijdsperiode.":::
 
U geeft het tijdvenster op met een geheel getal en een tijdseenheid: **Minuten** of **Uren**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Schermopname van het kiezen van minuten of uren.":::

Als u ruimte op het canvas wilt besparen, kunt u ook het relatieve tijdfilter als filterkaart maken in het deelvenster Filters.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Schermopname van relatieve tijd in een filter instellen.":::
 
## <a name="understanding-anchor-time"></a>Informatie over ankertijd

Wanneer een filter wordt toegepast op pagina- of rapportniveau, worden alle visuals op die pagina of in dat rapport gesynchroniseerd voor hetzelfde exacte tijdsbereik. Deze query's worden allemaal relatief aan de zogenaamde *ankertijd* uitgevoerd. De ankertijd wordt automatisch vernieuwd in de volgende situaties:

- De eerste keer dat een pagina wordt geladen.
- Wanneer handmatig wordt vernieuwd.
- Bij het automatisch vernieuwen van een pagina of bij detectie van een wijziging.
- Een wijziging in het model.

### <a name="anchor-time-exceptions"></a>Uitzonderingen op ankertijd

- Het filteren van relatieve tijd met behulp van de Q&A-visual is pas relatief ten opzichte van deze ankertijd wanneer u de Q&A-visual converteert naar een standaardvisual. De andere AI-visuals, zoals belangrijkste beïnvloeders en de ontledingsstructuur, worden echter gesynchroniseerd met de ankertijd. 
- Daarnaast zijn relatieve datumfilters of -slicers niet relatief aan de ankertijd, tenzij er relatieve tijdfilters aanwezig zijn. Als een relatieve datum- en tijdfilter op dezelfde pagina staan, conformeert het relatieve datumfilter zich aan de ankertijd.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

De volgende beperkingen en overwegingen zijn momenteel van toepassing op de relatieve tijdslicer en -filter.

- **Overwegingen voor tijdzones**: Gegevensmodellen in Power BI bevatten geen informatie over de tijdzone. De modellen kunnen tijden opslaan, maar er is geen indicatie van de tijdzone waarin ze zich bevinden. De slicer en het filter zijn altijd gebaseerd op de tijd in UTC. Als u een filter in een rapport instelt en het rapport naar een collega in een andere tijdzone stuurt, ziet u beide dezelfde gegevens. Tenzij u of uw collega zich in de UTC-tijdzone bevindt, moeten jullie beiden rekening houden met de tijdsverschillen die jullie ervaren. U kunt gegevens die in een lokale tijdzone zijn vastgelegd, omzetten naar UTC met behulp van de Query-editor.
- Dit nieuwe filtertype wordt ondersteund in Power BI Desktop, de Power BI-service, Power BI Embedded en de mobiele Power BI-apps. Het wordt echter niet ondersteund voor Publiceren op internet.

- **Query's in cache opslaan**: We gebruiken de clientcache. Stel dat u 'laatste minuut' en vervolgens 'laatste vijf minuten' opgeeft, vervolgens weer 'laatste minuut.' Op dat moment ziet u dezelfde resultaten als toen de query voor eerste keer werd uitgevoerd, tenzij u de pagina vernieuwt of de pagina automatisch wordt vernieuwd.

## <a name="next-steps"></a>Volgende stappen

- [Een relatieve datumslicer en -filter in Power BI gebruiken](../visuals/desktop-slicer-filter-date-range.md)
- [Slicers in Power BI](../visuals/power-bi-visualization-slicers.md)
