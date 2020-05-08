---
title: Lege pagina's voorkomen bij het afdrukken van gepagineerde rapporten
description: Richtlijnen voor het ontwerpen van gepagineerde rapporten om te voorkomen dat lege pagina's worden afgedrukt.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: 349459b95a815a52665e50687554f81f90a9c81b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920847"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>Lege pagina's voorkomen bij het afdrukken van gepagineerde rapporten

Dit artikel is bedoeld voor u wanneer u als auteur [gepagineerde rapporten](../paginated-reports/paginated-reports-report-builder-power-bi.md) in Power BI gaat ontwerpen. Het biedt aanbevelingen om u te helpen lege pagina's te voorkomen wanneer uw rapport wordt geëxporteerd naar een harde pagina-indeling, zoals PDF of Microsoft Word, of wordt afgedrukt.

## <a name="page-setup"></a>Pagina-instelling

De paginaformaateigenschappen van het rapport bepalen de afdrukstand, afmetingen en marges van de pagina. U krijgt als volgt toegang tot deze rapporteigenschappen:

- Via de **eigenschappenpagina** van het rapport: Klik met de rechtermuisknop op het donkergrijze gebied buiten het rapportcanvas en selecteer vervolgens _Rapporteigenschappen_.
- Via het deelvenster [**Eigenschappen**](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane): Klik op het donkergrijze gebied buiten het rapportcanvas om het rapportobject te selecteren. Zorg ervoor dat het deelvenster **Eigenschappen** is geopend.

De pagina **Pagina-instelling** van de **eigenschappenpagina** van het rapport bevat een beschrijvende interface voor het weergeven en bijwerken van de eigenschappen van de pagina-instelling.

![Afbeelding met het venster Rapporteigenschappen, waarbij de pagina Pagina-instelling is gemarkeerd.](media/report-paginated-blank-page/report-page-setup-properties.png)

Zorg ervoor dat alle eigenschappen van het paginaformaat correct zijn geconfigureerd:

|Eigenschap|Aanbeveling|
|---------|---------|
|Pagina-eenheden|Selecteer de relevante eenheden: inches of centimeters.|
|Afdrukstand|Selecteer de juiste optie: staand of liggend.|
|Papierformaat|Selecteer een papierformaat of wijs aangepaste waarden voor breedte en hoogte toe.|
|Marges|Stel de juiste waarden in voor de linker-, rechter-, boven- en ondermarge.|
|||

## <a name="report-body-width"></a>Breedte van rapporthoofdtekst

De eigenschappen van het paginaformaat bepalen welke ruimte beschikbaar is voor rapportobjecten. Rapportobjecten kunnen gegevensgebieden, gegevensvisualisaties of andere rapportitems zijn.

Een veelvoorkomende reden waarom lege pagina's worden uitgevoerd, is dat de breedte van de rapporthoofdtekst _de beschik bare paginaruimte overschrijdt_.

U kunt de breedte van de rapporthoofdtekst alleen weergeven en instellen met behulp van het deelvenster **Eigenschappen**. Klik eerst ergens in een leeg gebied van de rapporthoofdtekst.

![Afbeelding met het deelvenster Eigenschappen, waarbij de eigenschap voor de breedte van de rapporthoofdtekst is gemarkeerd.](media/report-paginated-blank-page/report-body-properties-width.png)

Zorg ervoor dat de waarde voor de breedte niet groter is dan de beschikbare paginabreedte. Laat u leiden door de volgende formule:

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> Het is niet mogelijk om de breedte van de rapporthoofdtekst te verkleinen als er al rapportobjecten zijn in de ruimte die u wilt verwijderen. U moet eerst de positie of het formaat van de rapportobjecten wijzigen voordat u de breedte verkleint.
>
> De breedte van de rapporthoofdtekst kan ook automatisch toenemen wanneer u nieuwe objecten toevoegt, of het formaat of de positie van bestaande objecten wijzigt. De hoofdtekst wordt door de rapportontwerper altijd breder gemaakt om de positie en grootte van de ingesloten objecten passend te maken.

## <a name="report-body-height"></a>Hoogte van rapporthoofdtekst

Een andere reden waarom een lege pagina wordt uitgevoerd, is dat er na het laatste object overbodige ruimte in de hoofdtekst van het rapport is.

We raden u aan om altijd de hoogte van de hoofdtekst te verkleinen om eventuele navolgende ruimte te verwijderen.

![Afbeelding met een rapportontwerp. De ruimte onder het tablix-gegevensgebied wordt aangegeven en als onnodig gemarkeerd.](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>Opties voor pagina-einden

Elk gegevensgebied en elke gegevensvisualisatie hebben opties voor pagina-einden. U kunt deze opties openen op de eigenschappenpagina of in het deelvenster **Eigenschappen**.

Zorg ervoor dat de eigenschap **Pagina-einde toevoegen na inhoud** niet onnodig is ingeschakeld.

![Afbeelding met een tablix-eigenschappenvenster. De eigenschap Pagina-einde toevoegen na inhoud is ingeschakeld.](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>Containerwitruimte gebruiken

Als het probleem met lege pagina’s blijft bestaan, kunt u ook proberen om de rapporteigenschap **ConsumeContainerWhitespace** uit te schakelen. Deze eigenschap kan alleen worden ingesteld in het deelvenster **Eigenschappen**.

![Afbeelding met het deelvenster Eigenschappen, waarbij de eigenschap ConsumeContainerWhitespace is gemarkeerd.](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

Standaard is deze eigenschap ingeschakeld. Deze eigenschap bepaalt of de minimale witruimte in containers, zoals de rapporthoofdtekst of een rechthoek, moet worden verbruikt. Alleen witruimte rechts van en onder de inhoud wordt beïnvloed.

## <a name="printer-paper-size"></a>Papierformaat printer

Als u het rapport afdrukt op papier, moet u ervoor zorgen dat het juiste papier in de printer is geplaatst. Het fysieke papierformaat moet overeenkomen met het [papierformaat van het rapport](#page-setup).

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Wat zijn gepagineerde rapporten in Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Paginering in gepagineerde Power BI-rapporten](../paginated-reports/paginated-reports-pagination.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)
