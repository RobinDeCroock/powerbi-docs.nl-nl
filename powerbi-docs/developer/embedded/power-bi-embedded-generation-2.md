---
title: Power BI Embedded-generatie 2 wordt uitgelegd als onderdeel van Power BI embedded Analytics
description: Meer informatie over de Power BI Embedded Generation 2-aanbieding in Power BI embedded Analytics.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2021
ms.locfileid: "99534491"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded generatie 2 (preview-versie)

Power BI Embedded onlangs een nieuwe versie van Power BI Embedded uitgebracht, **Power bi embedded tweede generatie 2**, aangeduid als **Inge sloten Gen2** voor het gemak. Inge sloten Gen2 is momenteel beschikbaar als preview-versie en kan worden gebruikt voor Inge sloten abonnees tijdens de preview-periode. U kunt nog steeds de oorspronkelijke versie van de Power BI Embedded resource met de naam *embedded gen 1* maken of een nieuwe *Inge sloten gen 2* -resource maken. Tijdens de preview-periode kunt u beide typen Power BI Embedded capaciteit parallel uitvoeren en een werk ruimte toewijzen aan een gen1 of een Gen2-capaciteit.

Alle mogelijkheden van Power BI Embedded gen 1, zoals het onderbreken en hervatten van de capaciteit, blijven bestaan in gen 2. Daarnaast biedt de capaciteits resource van de 2 de volgende updates en verbeterde ervaring:

* **Verbeterde prestaties** voor betere prestaties op elke capaciteits grootte, op elk moment. Bewerkingen worden altijd op de hoogste snelheid uitgevoerd en kunnen niet worden vertraagd wanneer de belasting van de capaciteit de capaciteitslimieten nadert.

* **Grotere schaal** , met inbegrip van de volgende verbeteringen:

    * *Geen limieten voor de gelijktijdigheid van vernieuwen* . u hoeft geen planningen te volgen voor gegevens sets die worden vernieuwd voor uw capaciteit

    * *Minder geheugenbeperkingen*

    * *Volledige scheiding tussen rapportinteractie en geplande vernieuwingen*

* **Lager invoer niveau voor gepagineerde rapporten en AI-workloads** – begin met een *a1* -SKU en verg root uw behoeften.

* **Een resource direct** schalen: u hoeft uw Power bi Embedded Resource direct te schalen. Het schalen van een gen1-resource in enkele minuten, om in een paar seconden een Gen2-resource te schalen.

* **Schalen zonder downtime** : met Inge sloten Gen2 kunt u uw Power bi Embedded-Resource schalen zonder uitval tijd.

* **Verbeterde metrische** gegevens: inclusief helder en genormaliseerd capaciteits gebruik, afhankelijk van de complexiteit van de analyse bewerkingen die de capaciteit uitvoert. Metrische gegevens worden niet beïnvloed door andere factoren, zoals de grootte van de capaciteit, en het niveau van de belasting van het systeem tijdens het uitvoeren van analyses. Wanneer u de verbeterde metrische gegevens gebruikt, kunt u met het ingebouwde rapportage programma duidelijk het volgende zien:
    * Analyse van gebruik
    * Budget planning
    * Toerekeningen
    * De nood zaak om uw capaciteit bij te werken

    >[!NOTE]
    >Tijdens de preview-periode zullen betere metrische gegevens beschikbaar worden gemaakt. Klanten die in de afgelopen zeven dagen toegang willen hebben tot de metrische gegevens over gebruik, kunnen dit doen door contact op te nemen met de klant ondersteuning.

## <a name="using-embedded-gen2"></a>Inge sloten Gen2 gebruiken

Maak een Inge sloten Gen2 capaciteits resource om te profiteren van de updates. Als u een Inge sloten Gen2-capaciteits resource wilt maken, volgt u de instructies in [Power bi embedded capaciteit maken in de Azure Portal](azure-pbie-create-capacity.md).

## <a name="known-limitations"></a>Bekende beperkingen

* Het capaciteits gebruik van Inge sloten Gen2 kan niet worden bijgehouden in de [metrieken-app](../../admin/service-admin-premium-monitor-capacity.md). Zie [Premium Gen2 monitor updates](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2)(Engelstalig) voor meer informatie.

* Geheugen toewijzings instellingen voor specifieke werk belastingen zijn niet van toepassing op Inge sloten Gen2-capaciteit. Zie voor meer informatie [embedded gen 2-geheugen uitbreidingen](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)

* Als u XMLA gebruikt met Inge sloten Gen2, moet u ervoor zorgen dat u de meest recente versies van de hulpprogram ma's voor gegevens modellering en-beheer gebruikt.

* Analysis Services-functies in embedded Gen2 worden alleen ondersteund in de meest recente client bibliotheken. Geschatte release datums voor afhankelijke hulpprogram ma's ter ondersteuning van deze vereiste worden vermeld in [bekende beperkingen in Premium Gen2](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2).

* Alle huidige Azure-metrische gegevens en logboek diagnostiek voor Power BI Embedded, ondersteunen alleen gen1-capaciteit.

## <a name="next-steps"></a>Volgende stappen

> [!div class="nextstepaction"]
> [Power BI Embedded-capaciteit maken in Azure Portal](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Capaciteit en SKU's in Power BI Embedded-analyses](embedded-capacity.md)

> [!div class="nextstepaction"]
> [Wat is Power BI Premium?](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw klanten](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insluiten voor uw organisatie](embed-sample-for-your-organization.md)