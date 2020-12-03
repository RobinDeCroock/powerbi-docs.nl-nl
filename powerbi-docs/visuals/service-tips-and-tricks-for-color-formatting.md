---
title: Tips en trucs voor opmaak in rapporten
description: Tips en trucs voor opmaak in Power BI-rapporten
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: conceptual
ms.date: 10/29/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 0ab6b799c8c78ab2e76a63a3ec5ee3f37f960b03
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415744"
---
# <a name="tips-and-tricks-for-formatting-in-reports"></a>Tips en trucs voor opmaak in rapporten

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

Power BI biedt veel verschillende manieren voor het aanpassen van uw rapporten. In dit artikel vindt u een verzameling tips die ervoor kunnen zorgen dat uw Power BI-visualisaties boeiend, interessant en afgestemd op uw behoeften zijn.

De volgende tips worden gegeven. Hebt u nog een goede tip? Mooi! Stuur de tip naar ons en we zullen kijken of deze aan de lijst kan worden toegevoegd.

* Een thema toepassen op het hele rapport
* De kleur van één gegevenspunt wijzigen
* Voorwaardelijke opmaak
* De kleuren van een grafiek baseren op een numerieke waarde
* De kleur van gegevenspunten baseren op een veldwaarde
* Kleuren in de kleurenschaal aanpassen
* Uiteenlopende kleurenschalen gebruiken
* Kleur toevoegen aan tabelrijen
* Hoe kunt u iets ongedaan maken in Power BI?

Als u wijzigingen wilt aanbrengen, moet u bewerkingsrechten voor het rapport hebben. Open het rapport in de **rapportweergave** van Power BI Desktop. In de Power BI-service betekent dit het openen van het rapport en het selecteren van **Bewerken** in de menubalk, zoals wordt weergegeven in de volgende afbeelding.

![locatie van het menu Bewerken](media/service-tips-and-tricks-for-color-formatting/power-bi-editing-view.png)

Wanneer de deelvensters **Filters** en **Visualisaties** worden weergegeven aan de rechterkant van het rapportcanvas, kunt u beginnen met aanpassen. Als de deelvensters niet worden weergegeven, selecteert u de pijl in de rechterbovenhoek om deze te openen.

![rapportcanvas in de bewerkweergave](media/service-tips-and-tricks-for-color-formatting/power-bi-edit-filter.png)

## <a name="apply-a-theme"></a>Een thema toepassen
Met rapportthema's past u ontwerpwijzigingen toe op uw hele rapport. U kunt bijvoorbeeld uw bedrijfskleuren gebruiken, pictogrammen veranderen of een nieuwe indeling van visuals toepassen. Wanneer u een rapportthema toepast, worden voor alle visuals in het rapport de kleuren en indeling van het geselecteerde thema gebruikt. Zie [Rapportthema's gebruiken](../create-reports/desktop-report-themes.md) voor meer informatie

![Pictogram voor Thema wisselen in de menu balk](media/service-tips-and-tricks-for-color-formatting/power-bi-themes.png)

Hier hebben we het thema **Innoveren** toegepast op het rapport Verkoop en marketing.

![Thema Innoveren toegepast](media/service-tips-and-tricks-for-color-formatting/power-bi-theme-innovate.png)

## <a name="change-the-color-of-a-single-data-point"></a>De kleur van één gegevenspunt wijzigen
Soms wilt u een bepaald gegevenspunt markeren. Misschien zijn het verkoopcijfers voor de lancering van een nieuw product, of hogere kwaliteitsscores na de lancering van een nieuw programma. Met Power BI kunt u een gegevenspunt markeren door de kleur ervan te wijzigen.

In de volgende visualisatie worden per productsegment verkochte eenheden gerangschikt. 

![Gegevenskleuren wijzigen naar grijs](media/service-tips-and-tricks-for-color-formatting/power-bi-format.png)

Stel u voor dat u het segment **Gemak** wilt aanroepen om op basis van kleur te zien hoe goed dit splinternieuw segment presteert. Dit zijn de stappen:

Vouw de kaart **Gegevenskleuren** uit en zet de schuifregelaar voor **Alles weergeven** op Aan. Hiermee worden de kleuren voor elk gegevenselement in de visualisatie weergegeven. U kunt nu een of meer van de gegevenspunten wijzigen.

![Deelvenster Opmaken met Alle weergeven ingesteld op Aan](media/service-tips-and-tricks-for-color-formatting/power-bi-show-all.png)

Stel **Gemak** in op oranje. 

![kolomdiagram met één oranje kolom](media/service-tips-and-tricks-for-color-formatting/power-bi-one-color.png)

Wanneer dit is geselecteerd, heeft het gegevenspunt **Gemak** een mooie oranje kleur die zeker opvalt.

Zelf als u visualisatietypen wijzigt en vervolgens terugkeert, onthoudt Power BI uw selectie en blijft **Gemak** oranje.

U kunt de kleur van een gegevenspunt voor één, meerdere of alle gegevenselementen in de visualisatie wijzigen. Wellicht wilt u dat uw visual uw bedrijfskleuren geel, groen en blauw bevat. 

![staafdiagram met staven die groen, geel en blauw zijn](media/service-tips-and-tricks-for-color-formatting/power-bi-corporate.png)

Er zijn veel verschillende dingen die u met kleuren kunt doen. In de volgende sectie gaan we in op voorwaardelijke opmaak.

## <a name="conditional-formatting-for-visualizations"></a>Voorwaardelijke opmaak voor visualisaties
Visualisaties profiteren vaak van dynamisch ingestelde kleuren op basis van de numerieke waarde van een veld. Hiermee kunt u een andere waarde laten zien dan welke is gebruikt voor de grootte van een balk en twee waarden in één grafiek weergeven. Of u kunt dit gebruiken om gegevenspunten boven (of onder) een bepaalde waarde te markeren - misschien om gebieden met een lage winstgevendheid te accentueren.

In de volgende secties worden verschillende manieren beschreven om kleur te baseren op een numerieke waarde.

### <a name="base-the-color-of-data-points-on-a-value"></a>De kleur van gegevenspunten baseren op een waarde
Als u de kleur wilt wijzigen op basis van een waarde, selecteert u een visualisatie om deze actief te maken. Open het opmaakvenster door het pictogram met de verfroller te selecteren en de kaart **Gegevenskleuren** te kiezen. Selecteer het fx-pictogram onder **Standaardkleur**.  

![selecteer de optie Voorwaardelijke opmaak door op de drie verticale puntjes te klikken](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional.png)

Gebruik de vervolgkeuzelijsten in het deelvenster **Standaardkleur** om de velden te identificeren die u voor voorwaardelijke opmaak wilt gebruiken. In dit voorbeeld hebben we het veld **Verkoopfeit** > **Totale eenheden** geselecteerd en lichtblauw voor de **Laagste waarde** en donkerblauw voor de **Hoogste waarde** gekozen. 

![instellingen voor voorwaardelijke opmaak op gegevenskleur](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting2-new.png)

![kolomdiagram waarop standaardkleuren zijn toegepast](media/service-tips-and-tricks-for-color-formatting/power-bi-default-colors.png)

U kunt de kleur van de visual ook opmaken met behulp van een veld dat geen deel uitmaakt van de visual. In de volgende afbeelding wordt **Marktaandeelpercentage SPLY YTD** gebruikt. 

![kolomdiagram met meerdere tinten blauw](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-colors.png)


U ziet dat, hoewel er meer eenheden van zowel **Productiviteit** als **Extreem** zijn verkocht (die kolommen zijn hoger), **Toezicht** een groter **Marktaandeelpercentage SPLY YTD** heeft (die kolom heeft meer kleurverzadiging).

### <a name="customize-the-colors-used-in-the-color-scale"></a>De kleuren in de kleurenschaal aanpassen
U kunt ook de manier wijzigen waarop de waarden aan deze kleuren worden toegewezen. In de volgende afbeelding zijn de kleuren voor **Minimum** en **Maximum** ingesteld op respectievelijk oranje en groen.

In deze eerste afbeelding ziet u hoe de balken in de grafiek het kleurverloop in de balk weergeven; de hoogste waarde is groen, de laagste is oranje en elke balk ertussen is gekleurd met een tint uit het spectrum tussen groen en oranje.

![kolomdiagram met een gradiënt aan kleuren van groen tot oranje](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional4.png)

Laten we eens kijken wat er gebeurt als we numerieke waarden opgeven in de waardevakken **Minimum** en **Maximum**. Selecteer **Aangepast** in de vervolgkeuzelijsten voor zowel **Minimum** als **Maximum**, en stel **Minimum** in op 3500 en **Maximum** op 6000.

![Voorwaardelijk opmaken op basis van getallen](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional-formatting-numbers.png)

Door het instellen van deze waarden wordt het verloop niet langer toegepast op de waarden in de grafiek die onder **Minimum** of boven **Maximum** liggen; een balk met een waarde boven **Maximum** is groen en een balk met een waarde onder **Minimum** is rood.

![resultaat van voorwaardelijke opmaak op basis van getallen](media/service-tips-and-tricks-for-color-formatting/power-bi-conditional3.png)

### <a name="use-diverging-color-scales"></a>Uiteenlopende kleurenschalen gebruiken
Soms kunnen uw gegevens van nature verschillen. Een temperatuurbereik heeft bijvoorbeeld een natuurlijk midden op het vriespunt en een rentabiliteitsscore heeft een natuurlijk middelpunt (nul).

Schakel het selectievakje voor **Afwijken** in als u afwijkende kleurenschalen wilt gebruiken. Wanneer **Afwijken** is ingeschakeld, verschijnt een extra kleurenkiezer, **Midden** genoemd (zie de volgende afbeelding).

![Dialoogvenster voor kleurinstelling met kleurenschaal geselecteerd](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging-colors.png)

Wanneer de schuifregelaar **Afwijken** is ingeschakeld, kunt u de kleuren afzonderlijk instellen voor **Minimum**, **Maximum** en **Midden**. In de volgende afbeelding is **Midden** ingesteld op 0,2 voor **marktaandeelpercentage SPLY YTD**, dus balken met waarden boven één hebben een groene kleurtint en balken onder één hebben een rode kleurtint.

![kolomdiagram met rode en groene balken](media/service-tips-and-tricks-for-color-formatting/power-bi-diverging.png)

## <a name="add-color-to-table-rows"></a>Kleur toevoegen aan tabelrijen
Tabellen en matrices bieden allerlei opties voor kleuropmaak. 

![Schermopname van een tabel met afwisselend witte en grijze rijen.](media/service-tips-and-tricks-for-color-formatting/power-bi-table.png)

Een van de snelste manieren om kleur toe te passen op een tabel of matrix is door het tabblad Opmaak te openen en **Stijl** te selecteren.  In de onderstaande afbeelding hebben we **Vetgedrukte koptekst met opvallende rijen** geselecteerd.

![Schermopname van de stijloptie Vetgedrukte koptekst met opvallende rijen die de koprij zwart en de andere rijen licht- en donkergroen maakt.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-style.png)

Experimenteer met andere opties voor kleuropmaak. In deze afbeelding hebben we de achtergrondkleur onder **Kolomkoppen** gewijzigd en de **Achtergrondkleur** en **Alternatieve achtergrondkleur** voor de **Waarden** (rijen) gewijzigd.

![Schermopname van waardeselecties voor Achtergrondkleur en Alternatieve achtergrondkleur.](media/service-tips-and-tricks-for-color-formatting/power-bi-table-rows.png)

## <a name="how-to-undo-in-power-bi"></a>Hoe kunt u iets ongedaan maken in Power BI?
Net als in veel andere services en software van Microsoft, biedt Power BI een eenvoudige manier om de laatst uitgevoerde opdracht ongedaan te maken. Laten we bijvoorbeeld zeggen dat u de kleur van een gegevenspunt of een reeks gegevenspunten wijzigt en dat de weergegeven kleur in de visualisatie u niet bevalt. U weet niet precies welke kleur het eerder was, maar u weet wel dat u die kleur terug wilt!

Als u uw laatste actie of acties **ongedaan wilt maken**, hoeft u alleen maar CTRL+Z in te typen.

Als u alle wijzigingen die u hebt aangebracht op een opmaakkaart ongedaan wilt maken, selecteert u **Standaardinstelling herstellen**.

![Opmaakkaart met onderaan Standaardinstelling herstellen](media/service-tips-and-tricks-for-color-formatting/power-bi-revert.png)

## <a name="give-us-your-feedback"></a>Stuur ons uw feedback
Hebt u een tip die u wilt delen? Stuur de tip naar ons en we zullen kijken of we deze kunnen toevoegen.

## <a name="next-steps"></a>Volgende stappen
[Aan de slag met de kleuropmaak en de eigenschappen van assen](service-getting-started-with-color-formatting-and-axis-properties.md)

[Rapporten delen](../collaborate-share/service-share-reports.md).

