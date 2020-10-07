---
title: Aanbevolen procedures voor de prestaties van Power BI Embedded
description: Dit artikel bevat richtlijnen voor aanbevolen procedures voor ingesloten analyses
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 2d33ed5a707a3b4bc3e0a77a38128e7e00154798
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746672"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Aanbevolen procedures voor de prestaties van Power BI Embedded

Dit artikel bevat aanbevelingen voor het sneller weergeven van rapporten, dashboards en tegels in uw toepassing.

> [!Note]
> Houd er rekening mee dat de laadtijd voornamelijk afhankelijk is van elementen die relevant zijn voor het rapport en de gegevens zelf, waaronder visualisaties, de grootte van de gegevens en de complexiteit van de query's en metingen. Raadpleeg de [Optimalisatiegids voor Power BI](../../guidance/power-bi-optimization.md) voor meer informatie.

## <a name="update-tools-and-sdk-packages"></a>Hulpprogramma's voor bijwerken en SDK-pakketten

Hiermee houdt u hulpprogramma's en SDK-pakketten bijgewerkt.

* Gebruik altijd de nieuwste versie van [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installeer de nieuwste versie van de [Power BI-client-SDK](https://github.com/Microsoft/PowerBI-JavaScript). Er worden doorlopend nieuwe verbeteringen geïntroduceerd. Het is dan ook raadzaam om hier regelmatig even naar te kijken.

## <a name="embed-parameters"></a>Ingesloten parameters

De methode `powerbi.embed(element, config)` ontvangt een element en een parameter config. De parameter config bevat velden die invloed hebben op de prestaties.

### <a name="embed-url"></a>Insluitings-URL

Genereer de insluitings-URL niet zelf. Haal in plaats daarvan de insluitings-URL op door de API [Rapporten ophalen](/rest/api/power-bi/reports/getreportsingroup), [Dashboards ophalen](/rest/api/power-bi/dashboards/getdashboardsingroup) of [Tegels ophalen](/rest/api/power-bi/dashboards/gettilesingroup) aan te roepen. Er is een nieuwe parameter toegevoegd aan de URL met de naam **_config_**. Deze wordt gebruikt voor prestatieverbeteringen.

### <a name="permissions"></a>Machtigingen

Wijs machtigingen van het type **Weergeven** toe als u niet van plan bent om een rapport in te sluiten in de bewerkingsmodus. Op deze manier worden er geen onderdelen geïnitialiseerd met invoegcode, die normaal in de bewerkingsmodus worden gebruikt.

### <a name="filters-bookmarks-and-slicers"></a>Filters, bladwijzers en slicers

Meestal worden rapportvisuals opgeslagen met gegevens in cache. De gegevens in cache worden gebruikt om te rapporteren over de prestaties. In rapporten worden de gegevens in cache weergegeven na het uitvoeren van query's. Als er filters, bladwijzers of slicers worden geleverd, zijn gegevens in de cache niet relevant en worden de visualisaties pas weergegeven nadat de visuele query is beëindigd.

Als u rapporten met dezelfde filters, bladwijzers en slicers insluit, kunt u de prestaties verbeteren door het rapport op te slaan terwijl de filters, bladwijzers en slicers al zijn toegepast. Het rapport wordt dan weergegeven met de gegevens in de cache, inclusief de filters, bladwijzers en slicers.

## <a name="switching-between-reports"></a>Schakelen tussen rapporten

Wanneer u meerdere rapporten in hetzelfde iframe insluit, moet u niet voor elk rapport een nieuw iframe genereren. Gebruik in plaats daarvan `powerbi.embed(element, config)` met een andere configuratie om het nieuwe rapport in te sluiten.

> [!NOTE]
> Wanneer u schakelt tussen rapporten bij het insluiten van inhoud voor uw klanten (ook wel bekend als een 'app is eigenaar van de gegevens'-scenario genoemd), is het gebruik van een insluittoken met machtigingen vereist voor alle rapporten en gegevenssets. Zie [token-API genereren](/rest/api/power-bi/embedtoken/generatetoken) voor meer informatie.

## <a name="query-caching"></a>Query's in cache opslaan

Organisaties met Power BI Premium of Power BI Embedded kunnen query's opslaan in de cache om rapporten die zijn gekoppeld aan een gegevensset sneller weer te geven.

[Lees hier meer over het in de cache opslaan van query's in Power BI](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Vooraf laden

Gebruik `powerbi.preload()` om de prestaties bij de eindgebruiker te verbeteren. Met de methode `powerbi.preload()` worden JavaScript, CSS-bestanden en andere artefacten gedownload. Deze worden later gebruikt voor het insluiten van een rapport.

Roep `powerbi.preload()` aan als u het rapport niet direct gaat insluiten. Als ingesloten Power BI-inhoud bijvoorbeeld niet verschijnt op de startpagina, gebruikt u `powerbi.preload()` om de artefacten die worden gebruikt om de inhoud op te slaan in de inhoud te downloaden en in de cache op te slaan.

## <a name="bootstrapping-the-iframe"></a>Het iframe bootstrappen

> [!NOTE]
> [Power BI client SDK](https://github.com/Microsoft/PowerBI-JavaScript) versie 2.9 is vereist om het iframe te bootstrappen.

Met `powerbi.bootstrap(element, config)` kunt u met insluiten beginnen voordat alle vereiste parameters beschikbaar zijn. De bootstrap-API bereidt het iframe voor en initialiseert het.
Wanneer u de bootstrap-API gebruikt, is het nog steeds nodig om `powerbi.embed(element, config)` aan te roepen voor hetzelfde HTML-element.

Een van de gebruiksvoorbeelden voor deze functie is bijvoorbeeld om de iframe-bootstrap en de back-endaanroepen voor insluiting tegelijkertijd uit te voeren.
> [!TIP]
> Gebruik de bootstrap-API wanneer het mogelijk is om het iframe te genereren voor het zichtbaar is voor de eindgebruiker.

[Lees hier meer over het bootstrappen van het iframe](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Prestaties meten

### <a name="performance-events"></a>Prestatiegebeurtenissen

Als u de ingesloten prestaties wilt meten, kunt u twee gebeurtenissen gebruiken:

1. Geladen gebeurtenis: De tijd tot het rapport wordt geïnitialiseerd (het Power BI-logo verdwijnt wanneer het laden is voltooid).
2. Weergegeven gebeurtenis: De tijd totdat het volledige rapport wordt weergegeven, met de feitelijke gegevens. De weergegeven gebeurtenis wordt steeds opnieuw geactiveerd wanneer het rapport wordt vernieuwd (bijvoorbeeld na het toepassen van filters). Als u een rapport wilt meten, moet u de berekeningen uitvoeren voor de eerste gebeurtenis.

Gegevens in de cache worden weergegeven als deze beschikbaar zijn, maar er wordt dan geen extra gebeurtenis gegenereerd.

[Lees hier meer over de afhandeling van gebeurtenissen](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Performance Analyzer

Als u de prestaties van de rapportelementen wilt controleren, kunt u hiervoor Performance Analyzer in Power BI Desktop gebruiken.
Met Performance Analyzer kunt u logboeken bekijken en vastleggen die meten hoe elk van de rapportelementen presteert.

[Lees hier meer over Performance Analyzer](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> Vergeet niet om de prestaties van het ingesloten rapport te vergelijken met de prestaties op powerbi.com. Dit kan helpen om een beeld te krijgen van de oorzaak van prestatieproblemen.

## <a name="next-steps"></a>Volgende stappen

* [Optimalisatiegids voor Power BI](../../guidance/power-bi-optimization.md)
* [Problemen met Power BI Embedded oplossen](embedded-troubleshoot.md)
* [Veelgestelde vragen over Power BI Embedded](embedded-faq.md)