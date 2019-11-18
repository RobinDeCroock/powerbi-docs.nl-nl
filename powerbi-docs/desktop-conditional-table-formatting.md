---
title: Voorwaardelijke tabelopmaak in Power BI Desktop
description: Aangepaste opmaak toepassen op tabellen
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b715cd42ea221f62258b66eee71b6525b2015ae1
ms.sourcegitcommit: 01de0b01f66f28ca45b8d309d7864f261d6c9a85
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74128166"
---
# <a name="conditional-formatting-in-tables"></a>Voorwaardelijke opmaak in tabellen 
Met voorwaardelijke opmaak voor tabellen kunt u aangepaste celkleuren opgeven op basis van celwaarden of op basis van andere waarden of velden, waaronder het gebruik van kleurovergangen. U kunt ook celwaarden met gegevensbalken weergeven. 

Selecteer voor toegang tot voorwaardelijke opmaak in het venster **Velden** van het deelvenster **Visualisaties** in Power BI Desktop de pijl omlaag naast de waarde in het venster **Waarden** die u wilt opmaken (of klik met de rechtermuisknop op het veld). U kunt voorwaardelijke opmaak alleen beheren voor velden in het gebied **Waarden** van het venster **Velden**.

![Het menu Voorwaardelijke opmaak](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

In de volgende gedeelten worden deze voorwaardelijke opmaakopties behandeld. U kunt een of meer opties combineren in een afzonderlijke tabelkolom.

> [!NOTE]
> Wanneer voorwaardelijke opmaak wordt toegepast op een tabel, worden alle aangepaste tabelstijlen die zijn toegepast op de voorwaardelijk opgemaakte cellen overschreven.

Als u voorwaardelijke opmaak uit een visualisatie wilt verwijderen, klikt u eenvoudigweg opnieuw met de rechtermuisknop op het veld en selecteert u **Voorwaardelijke opmaak verwijderen**. Selecteer vervolgens het type opmaak dat u wilt verwijderen.

![Het menu Voorwaardelijke opmaak verwijderen](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>Achtergrondkleurschalen

Wanneer u **Voorwaardelijke opmaak** en vervolgens **Achtergrondkleurschalen** selecteert, wordt het volgende dialoogvenster geopend.

![Het dialoogvenster Achtergrondkleurschalen](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

U kunt een veld selecteren via uw gegevensmodel om daar de kleuren op te baseren door **Kleur gebaseerd op** in te stellen op dat veld. Daarnaast kunt u het aggregatietype opgeven voor het geselecteerde veld met de waarde **Samenvatting**. Het veld dat moet worden ingekleurd, wordt opgegeven in het veld **Kleur toepassen op**, zodat u dit kunt bijhouden. U kunt voorwaardelijke opmaak toepassen op tekst- en datumvelden, zo lang u maar een numerieke waarde als basis van de opmaak kiest.

![Het veld Kleur gebaseerd op](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Als u discrete kleurwaarden wilt gebruiken voor bepaalde waardebereiken, selecteert u **Kleur op regels**. Als u een kleurspectrum wilt gebruiken, laat u de optie **Kleur op regels** uitgeschakeld. 

![Het dialoogvenster Achtergrondkleurschalen](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>Kleur op regels

Wanneer u **Kleur op regels** selecteert, kunt u een of meer waardebereiken invoeren, elk met een ingestelde kleur.  Elk waardebereik begint met een voorwaarde met een *Als-waarde*, een voorwaarde met een *en*-waarde en een kleur.

![Het waardebereik van Kleur op regels](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Tabelcellen met waarden in elk bereik worden gevuld met de opgegeven kleur. De volgende afbeelding bevat drie regels.

![Voorbeeld van kleur op regels](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

De voorbeeldtabel ziet er nu als volgt uit:

![Voorbeeldtabel met kleur op regels](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>Minimum- tot maximumkleur

U kunt de waarden *Minimum* en *Maximum* en de bijbehorende kleuren configureren. Als u het vak **Afwijken** selecteert, kunt u desgewenst ook een waarde voor *Centreren* configureren.

![De knop Afwijken](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

De voorbeeldtabel ziet er nu als volgt uit:

![Voorbeeldtabel met afwijkende kleuren](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>Tekstkleurschalen

Als u **Voorwaardelijke opmaak** en vervolgens **Tekstkleurschalen** selecteert, wordt het volgende dialoogvenster geopend. Dit dialoogvenster is vergelijkbaar met het dialoogvenster**Achtergrondkleurschalen**. Hiermee kunt u echter de tekstkleur wijzigen in plaats van de achtergrondkleur van de cel.

![Het dialoogvenster Tekstkleurschalen](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

De voorbeeldtabel ziet er nu als volgt uit:

![Voorbeeldtabel met tekstkleurschalen](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>Gegevensbalken

Als u **Voorwaardelijke opmaak** en vervolgens **Gegevensbalken** selecteert, wordt het volgende dialoogvenster geopend. 

![Het dialoogvenster Gegevensbalken](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Standaard is de optie **Alleen balk weergeven** niet ingeschakeld; de tabelcel toont dus zowel de balk als de daadwerkelijke waarde.

![Voorbeeldtabel met gegevensbalken en waarden](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

Als de optie **Alleen balk weergeven** is ingeschakeld, toont de tabelcel alleen de balk.

![Voorbeeldtabel met alleen gegevensbalken](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="color-formatting-by-field-value"></a>Kleuropmaak op veldwaarde

U kunt een meting of een kolom waarin een kleur is opgegeven, gebruiken om die kleur via een tekstwaarde of een hex-code toe te passen op de achtergrond van de tekenkleur van een tabel of een matrixvisual. U kunt ook aangepaste logica voor een bepaald veld maken en ervoor zorgen dat deze logica de gewenste kleur toepast op het lettertype of de achtergrond.

Er is bijvoorbeeld in de volgende tabel een kleur gekoppeld aan elk productmodel. 

![Veld ProductName met kleurnaam](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Als u die cel wilt opmaken op basis van de veldwaarde, selecteert u het dialoogvenster **Voorwaardelijke opmaak** door met de rechtermuisknop op de kolom *Kleur* te klikken voor deze visual en in dit geval in het menu **Achtergrondkleur** te selecteren. 

![Achtergrondkleur selecteren in het menu](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

Selecteer in het dialoogvenster dat wordt weergegeven **Veldwaarde** in het vervolgkeuzevak **Opmaken door**, zoals wordt weergegeven in de volgende afbeelding.

![Opmaken door veldwaarde](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

U kunt deze procedure herhalen voor de tekenkleur, waarna het resultaat in de visual een effen kleur in de kolom **Kleur** wordt, zoals wordt weergegeven in het volgende scherm.

![Opmaken door veldwaarde](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

U kunt ook een DAX-berekening maken op basis van bedrijfslogica die verschillende hex-codes oplevert op basis van de voorwaarden van uw voorkeur. Dit is meestal gemakkelijker dan het maken van meerdere regels in het dialoogvenster voor voorwaardelijke opmaak. Bekijk het veld *ColorKPI* in de volgende voorbeeldafbeelding.

![DAX-berekeningen](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

U kunt vervolgens de veldwaarde voor **Achtergrondkleur** op de volgende manier instellen.

![De veldkleur instellen op basis van een KPI](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

En u kunt vervolgens resultaten als de volgende matrix krijgen.

![Matrixvisual met een op KPI-waarde gebaseerde kleur](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Er zijn veel meer variaties die u kunt maken door gewoon gebruik te maken van uw eigen verbeelding en een beetje DAX.

U kunt een van de waarden in de CSS-kleurspecificatie van [https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/) gebruiken om uw visuals in te kleuren:
* hexadecimale codes van 3, 6 of 8 cijfers, bijvoorbeeld #3E4AFF. Zorg ervoor dat u het symbool # aan het begin van de code opneemt. '3E4AFF' wordt niet geaccepteerd. 
* RGB- of RGBA-waarden, bijvoorbeeld RGBA(234, 234, 234, 0.5)
* HSL- of HSLA-waarden, bijvoorbeeld HSLA(123, 75%, 75%, 0.5)
* Kleurnamen zoals Green, SkyBlue en PeachPuff 

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen
Er zijn enkele overwegingen voor het werken met voorwaardelijke tabelopmaak:

* Voorwaardelijke opmaak wordt alleen toegepast op de waarden van een **Matrix**-visual en is niet van toepassing op subtotalen of eindtotalen. 
* Voorwaardelijke opmaak wordt niet toegepast op de rij **Totaal**
* Tabellen zonder groepering worden weergegeven als één rij die geen ondersteuning biedt voor voorwaardelijke opmaak.
* Als u voorwaardelijke opmaak met automatische maximum/min-waarden of op regels gebaseerde opmaak met percentageregels gebruikt, kan voorwaardelijke opmaak niet worden toegepast als uw gegevens NaN-waarden bevatten. NaN betekent 'geen getal', meestal veroorzaakt door een fout met delen door nul. U kunt de [DIVIDE () DAX-functie](https://docs.microsoft.com/dax/divide-function-dax) gebruiken om deze fouten te voorkomen.


## <a name="next-steps"></a>Volgende stappen
Raadpleeg voor meer informatie hete volgende artikel:  

* [Tips en trucs voor het gebruik van opmaak in Power BI](visuals/service-tips-and-tricks-for-color-formatting.md)  

