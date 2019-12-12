---
title: Concept voor een Power BI-visual
description: In dit artikel wordt beschreven hoe visuals kunnen worden geïntegreerd met Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700841"
---
# <a name="power-bi-visual-concept"></a>Concept voor een Power BI-visual

In dit artikel wordt uitgelegd hoe een gebruiker en een visual communiceren met Power BI en hoe een gebruiker gebruik kan maken van een Power BI-visual. In het diagram ziet u welke acties rechtstreeks van invloed zijn op de visual of die via Power BI van invloed zijn (als de gebruiker bijvoorbeeld bladwijzers selecteert).

![Power BI-visual](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>De visual wordt bijgewerkt vanuit Power BI

De visual beschikt over de methode `update`. Deze methode bevat meestal de hoofdlogica van de visual en is verantwoordelijk voor het weergeven van het diagram of het visualiseren van gegevens.

Er worden meer updates aangeroepen met de methode `update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>De gebruiker communiceert via Power BI met de visual

* De gebruiker opent het deelvenster met visualeigenschappen.

    Power BI haalt ondersteunde objecten en eigenschappen op uit de visual `capabilities.json`. Voor het ontvangen van de daadwerkelijke waarden van eigenschappen roept Power BI de methode `enumerateObjectInstances` van de visual aan.

    De visual moet de daadwerkelijke waarden van eigenschappen retourneren.

    Lees over [de mogelijkheden van visuals](capabilities.md) voor meer informatie.

* [De gebruiker verandert een eigenschap van de visual](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) in het opmaakdeelvenster.

    Wanneer u de waarde van een eigenschap hebt gewijzigd, wordt door Power BI de methode `update` van de visual aangeroepen en worden de nieuwe `options` doorgegeven aan de methode 'update', met de nieuwe waarden van de objecten.

    Lees over [objecten en eigenschappen van visuals](objects-properties.md) voor meer informatie.

* De gebruiker wijzigt het formaat van de visual.

    Wanneer een gebruiker de grootte van een visual wijzigt, roept Power BI de methode `update` aan met het nieuwe object `option`. Opties hebben een genest `viewport`-object met daarin de nieuwe breedte en hoogte van de visual.

* De gebruiker past een filter op rapport-, pagina- of visualniveau toe.

    Power BI filtert gegevens op basis van de filtervoorwaarden. Verder wordt de methode `update` van de visual aangeroepen om nieuwe gegevens door te geven aan de visual.

    De visual ontvangt een nieuwe update van `options`, met nieuwe gegevens in een van de geneste objecten. Om welke gegevens het gaat, is afhankelijk van de configuratie van de gegevensweergavetoewijzing van de visual.

    Lees over [gegevensweergavetoewijzingen](dataview-mappings.md) voor meer informatie.

* De gebruiker selecteert een gegevenspunt in een andere visual van het rapport.

    Power BI filtert of markeert de geselecteerde gegevenspunten en roept de methode `update` van de visual aan.

    De visual ontvangt nieuwe gefilterde gegevens of juist dezelfde gegevens met een reeks markeringen.

    Lees over [markeren van gegevens in visuals](highlight.md) voor meer informatie.

* De gebruiker selecteert een bladwijzer in het bladwijzerdeelvenster van het rapport.

    Er kunnen twee dingen gebeuren:

    1. Power BI roept een functie aan die is geregistreerd door de methode `registerOnSelectionCallback`. De callbackfunctie haalt een reeks selecties op voor de bijbehorende bladwijzer.

    2. Power BI roept de methode `update` aan met het bijbehorende filterobject in `options`.

    In beide gevallen moet de visual een andere visualisatiestatus krijgen op basis van de ontvangen selecties of het filterobject.

    Lees over [werken met bladwijzers](filter-api.md) voor meer informatie over bladwijzers.

    Lees over [hoe Power BI-visuals gegevens in andere visuals kunnen filteren](filter-api.md) voor meer informatie over filters.

### <a name="user-interacts-with-visual-directly"></a>De gebruiker werkt rechtstreeks met de visual

* De gebruiker houdt de muisaanwijzer op het gegevenselement

    De visual kan aanvullende informatie weergeven over het gegevenspunt via de Power BI Tooltips-API.
    De gebruiker houdt de muisaanwijzer op de visual. De visual kan dan de gebeurtenis verwerken en gegevens weergeven over het knopinfo-element.

    De visual kan reguliere knopinfo weergeven of rapporteren over paginaknopinfo.

    Lees de handleiding over het [toevoegen van knopinfo](add-tooltips.md) voor meer informatie.

* De gebruiker wijzigt de eigenschappen van de visual (de gebruiker breidt bijvoorbeeld de boomstructuur uit en de visual slaat de status op in eigenschappen)

    In de visual kunnen eigenschapswaarden worden opgeslagen via de Power BI-API. Bijvoorbeeld wanneer de gebruiker communiceert met de visual. In de visual moeten eigenschapswaarden worden opgeslagen of bijgewerkt. Hiervoor kan de visual de methode `presistProperties` aanroepen.

* De gebruiker klikt op de URL.

    De visual kan standaard de URL niet openen. Als u de URL in een nieuw tabblad wilt openen, moet de visual de methode `launchURL` aanroepen en de URL doorgeven als parameter.

    Voor meer informatie opent u de [URL-API](launch-url.md).

* De gebruiker past een filter toe op de visual

    De visual roept `applyJSONFilter` aan en geeft filtervoorwaarden op zodat er op de filtergegevens wordt gefilterd in de andere visual.

    In de visual kunnen verschillende typen van het filter worden gebruikt, zoals het basisfilter, het geavanceerde filter en het tuplefilter.

    Lees over [hoe Power BI-visuals gegevens in andere visuals kunnen filteren](filter-api.md) voor meer informatie over filters.

* De gebruiker klikt op of selecteert elementen in de visual.

    Lees over [hoe visuals communiceren](selection-api.md) voor meer informatie over selecties.

### <a name="the-visual-interacts-with-power-bi"></a>De visual communiceert met Power BI

* De visual vraagt meer gegevens op bij Power BI.

    De visual kan gegevens langzaam maar zeker verwerken. Met de API-methode FetchMoreData wordt steeds het volgende onderdeel van de gegevensset opgevraagd.

    Als u meer wilt weten over `fetchMoreData`, leest u de informatie over het [ophalen van meer gegevens uit Power BI](fetch-more-data.md)

* Gebeurtenisservice

    In Power BI kunnen rapporten naar PDF worden geëxporteerd of per e-mail worden verzonden (alleen gecertificeerde visuals worden ondersteund). Om Power BI te laten weten dat het weergeven is voltooid en dat er een PDF of e-mail kan worden opgesteld, moet de visual de Rendering Events-API aanroepen.

    Lees over het [exporteren van rapporten van Power BI naar PDF](../../consumer/end-user-pdf.md) voor meer informatie

    Lees meet over de [gebeurtenisservice](event-service.md)

## <a name="next-steps"></a>Volgende stappen

Bent u een webontwikkelaar en bent u geïnteresseerd in het maken van uw eigen visualisaties en wilt u deze toevoegen aan AppSource? Zie [Een Power BI-visual ontwikkelen](./custom-visual-develop-tutorial.md) en lees hoe u [Power BI-visuals naar AppSource publiceert](../office-store.md).
