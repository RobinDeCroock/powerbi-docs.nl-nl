---
title: Veel-op-veel-relaties in Power BI Desktop
description: Relaties met een veel-op-veel-kardinaliteit gebruiken in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/19/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 7452879e47cd4b058fcdb3e08f0ded35a85da1aa
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761060"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Veel-op-veel-relaties toepassen in Power BI Desktop

Met *relaties met veel-op-veel-kardinaliteit* in Power BI Desktop kunt u tabellen samenvoegen die gebruikmaken van de kardinaliteit *Veel-op-veel*. U kunt gemakkelijker en intuïtief gegevensmodellen maken die twee of meer gegevensbronnen bevatten. *Relaties met een veel-op-veel-kardinaliteit* maken deel uit van de overkoepelende voorziening voor *samengestelde modellen* in Power BI Desktop.

![Een veel-op-veel-relatie in het deelvenster 'Relatie bewerken', Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Een *relatie met een veel-op-veel-kardinaliteit* in Power BI Desktop bestaat uit drie gerelateerde functies:

* **Samengestelde modellen**: Met een *samengesteld model* wordt het mogelijk dat een rapport twee of meer gegevensverbindingen heeft, inclusief DirectQuery-verbindingen of importverbindingen, in elke gewenste combinatie. Zie [Samengestelde modellen in Power BI Desktop gebruiken](desktop-composite-models.md) voor meer informatie.

* **Relaties met een veel-op-veel-kardinaliteit**: met samengestelde modellen kunt u *relaties met een veel-op-veel-kardinaliteit* tussen tabellen tot stand brengen. Door deze aanpak hoeven tabellen geen unieke waarden meer te bevatten. Ook zijn eerdere tijdelijke oplossingen niet meer nodig, zoals de introductie van nieuwe tabellen alleen maar om relaties tot stand te brengen. De functie wordt verderop in dit artikel beschreven.

* **Opslagmodus**: u kunt nu opgeven voor welke visualisaties een query naar de back-endgegevensbronnen is vereist. Visuals waarvoor geen query is vereist, worden geïmporteerd zelfs als ze zijn gebaseerd op DirectQuery. De functie helpt de prestaties te verbeteren en de back-end minder te belasten. Eerder werden zelfs voor eenvoudige visuals, zoals slicers, query's verzonden naar back-endbronnen. Zie [Opslagmodus in Power BI Desktop](desktop-storage-mode.md) voor meer informatie.

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>Wat u met een relatie met een veel-op-veel-kardinaliteit kunt oplossen

Voordat er *relaties met een veel-op-veel-kardinaliteit* beschikbaar waren, werd de relatie tussen twee tabellen gedefinieerd in Power BI. Ten minste één van de tabelkolommen in de relatie moest unieke waarden bevatten. Vaak bevatte echter geen enkele kolom unieke waarden.

Twee tabellen hebben bijvoorbeeld een kolom met het label Land. De waarden van Land zijn echter in geen van beide tabellen uniek. Er was een tijdelijke oplossing nodig om zulke tabellen samen te voegen. Een tijdelijke oplossing is het maken van extra tabellen met de benodigde unieke waarden. Met *relaties met een veel-op-veel-kardinaliteit* kunt u deze tabellen direct samenvoegen met behulp van een relatie met de kardinaliteit *veel-op-veel*.

## <a name="use-relationships-with-a-many-many-cardinality"></a>Relaties met een veel-op-veel-kardinaliteit gebruiken

Als u een relatie tussen twee tabellen wilt definiëren in Power BI, moet u de kardinaliteit van de relatie opgeven. De relatie tussen ProductSales en Product&mdash;met de kolommen ProductSales[ProductCode] en Product[ProductCode]&mdash;zou bijvoorbeeld worden gedefinieerd als *Veel-1*. De relatie wordt op deze manier gedefinieerd omdat er voor elk product veel verkopen zijn en de kolom in de tabel Product (ProductCode) uniek is. Als u een relatiekardinaliteit definieert als *Veel-1*, *1-veel* of *1-1* wordt dit door Power BI gevalideerd, zodat de kardinaliteit die u selecteert overeenkomt met de werkelijke de gegevens.

Laten we eens kijken naar het eenvoudige model in deze afbeelding:

![Tabellen ProductSales en Product, weergave Relatie, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

Stel nu dat de tabel **Product** slechts twee rijen bevat, zoals weergegeven:

![Visual van de tabel Product met twee rijen, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

Laten we er ook van uitgaan dat de tabel Sales maar vier rijen heeft, waaronder een voor een product C. Vanwege een fout met betrekking tot referentiële integriteit komt de rij voor product C niet voor in de tabel**Product**.

![Visual van de tabel Sales met vier rijen, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

De **ProductName** en **Price** (uit de tabel **Product**), samen met het totale aantal **Qty** voor elk product (uit de tabel ProductSales), zou als volgt worden weergegeven:

![Visual met de productnaam, prijs en hoeveelheid, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

Zoals u in de vorige afbeelding ziet, is er een lege rij **ProductName**, die is gekoppeld aan de verkoop van product C. Deze lege rij vertegenwoordigt het volgende:

* Alle rijen in de tabel **ProductSales** waarvoor geen overeenkomende rij bestaat in de tabel **Product**. Er is een probleem met betrekking tot referentiële integriteit, zoals we in dit voorbeeld zien voor product C.

* Alle rijen in de tabel **ProductSales** waarvoor de kolom met de refererende sleutel null is.

Om deze redenen vertegenwoordigt de lege rij in beide gevallen verkopen waarvoor de **ProductName** en **Price** onbekend zijn.

Soms worden de tabellen samengevoegd via twee kolommen, maar is geen van beide kolommen uniek. Laten we maar eens kijken naar de volgende twee tabellen:

* De tabel **Sales** bevat verkoopgegevens per **State**. Elke rij bevat de omzet voor het type verkoop in die staat. De staten zijn CA, WA en TX.

    ![De tabel Sales met de verkoop per staat, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* De tabel **CityData** bevat gegevens van steden, waaronder het aantal inwoners en de staat (zoals CA, WA en New York).

    ![De tabel Sales met de stad, staat en het aantal inwoners, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

Beide tabellen bevatten nu de kolom **State**. Het is handig om een rapport te maken van zowel de totale verkoop per staat als het totale inwonertal van elke staat. Er bestaat echter een probleem: de kolom **State** is in geen van de tabellen uniek.

## <a name="the-previous-workaround"></a>De vorige tijdelijke oplossing

Voor de versie van Power BI Desktop van juli 2018 konden gebruikers geen directe relatie tussen deze tabellen maken. Een veelgebruikte tijdelijke oplossing voor dit probleem was:

* Maak een derde tabel die alleen de unieke id's voor State bevat. Het mag een of alle van de volgende tabellen zijn:
  * Een berekende tabel (gedefinieerd met behulp van Data Analysis Expressions (DAX)).
  * Een tabel op basis van een query die is gedefinieerd in Query-editor, met de unieke id's die zijn opgehaald uit een van de tabellen.
  * De gecombineerde volledige set.

* Koppel de twee oorspronkelijke tabellen vervolgens aan de nieuwe tabel door algemene *Veel-1*-relaties te gebruiken.

U kunt de tijdelijke tabel zichtbaar laten. Of u kunt de tijdelijke tabel verbergen, zodat deze niet wordt weergegeven in de lijst **Velden**. Als u de tabel verbergt, worden de *Veel-1*-relaties gewoonlijk ingesteld op filteren in beide richtingen en u kunt het veld State uit elk van de tabellen gebruiken. Het daaropvolgende kruislingse filteren wordt doorgeven aan de andere tabel. Deze aanpak wordt weergegeven in de volgende afbeelding:

![Verborgen tabel State, weergave Relatie, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

Een visualisatie met **State** (uit de tabel **CityData**), samen met het totale aantal inwoners (**Population**) en de totale omzet (**Sales**) ziet er dan zo uit:

![Tabellen State, Population en Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> Omdat in deze tijdelijke oplossing de staat uit de tabel **CityData** wordt gebruikt, worden alleen de staten in die tabel weergegeven en wordt TX dus uitgesloten. In tegenstelling tot *Veel-1*-relaties bevat de totaalrij wel alle **Sales**, inclusief die van TX, maar bevatten de details geen lege rij om rijen zonder overeenkomst te vertegenwoordigen. Zo is er ook geen lege rij voor **Sales** met een null-waarde voor de **State**.

Stel dat u ook een plaats toevoegt aan die visual. In **Sales** voor City worden gewoon de **Sales** voor de bijbehorende **State** herhaald, ook al is de bevolking per City wel bekend. Dit scenario treedt normaal gesproken op wanneer de groepering van kolommen niet is gerelateerd aan een statistische meting, zoals hier wordt weergegeven:

![Staat, bevolking van de stad en verkoop, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

Stel dat u de nieuwe tabel Sales definieert als de combinatie van alle staten die hier worden vermeld en dat u deze zichtbaar maakt in de lijst **Velden**. In dezelfde visual worden **State** (in de nieuwe tabel), de totale **Population** en de totale **Sales** weergegeven:

![De visual voor staat, bevolking en verkoop, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

Zoals u ziet, is TX&mdash; afgebeeld met **Sales**-gegevens, maar onbekende *Population*-gegevens&mdash; en is &mdash;New York**afgebeeld met bekende**Population **-gegevens, maar zonder** Sales&mdash;-gegevens. Deze oplossing is niet optimaal en veroorzaakt veel problemen. Voor relaties met een veel-op-veel-kardinaliteit kunnen de resulterende problemen worden opgelost, zoals beschreven in de volgende sectie.

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>Een relatie met een veel-op-veel-kardinaliteit gebruiken in plaats van de tijdelijke oplossing

Vanaf de versie van juli 2018 van Power BI Desktop kunt u tabellen, zoals degene die eerder zijn beschreven, rechtstreeks koppelen, zonder dat u gebruik hoeft te maken van vergelijkbare tijdelijke oplossingen. Het is nu mogelijk om de relatiekardinaliteit in te stellen als *Veel-op-veel*. Deze instelling geeft aan dat geen van beide tabellen unieke waarden bevat. Voor dergelijke relaties kunt u nog steeds bepalen met welke tabel de andere tabel wordt gefilterd. U kunt ook bidirectionele filters toepassen, waarbij elke tabel door de andere tabel wordt gefilterd.

In Power BI Desktop wordt de kardinaliteit standaard ingesteld op *Veel-op-veel* als is vastgesteld dat geen van beide tabellen unieke waarden bevat voor de kolommen in de relatie. In dergelijke gevallen bevestigt een waarschuwingsbericht dat u een relatie wilt instellen; de wijziging is niet het onbedoelde effect van een probleem met gegevens.

Als u bijvoorbeeld een rechtstreekse relatie maakt tussen CityData en Sales&mdash;waarbij filters moeten worden doorgegeven van CityData naar Sales&mdash;wordt in Power BI Desktop het dialoogvenster **Relatie bewerken** weergegeven:

![Het dialoogvenster Relatie bewerken, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

De resulterende **Relatie**-weergave bevat dan de directe veel-op-veelrelatie tussen de twee tabellen. De weergave van de tabellen in de lijst **Velden** en het daaropvolgende gedrag bij het maken van de visuals, is vergelijkbaar met die na het toepassen van de tijdelijke oplossing. In de tijdelijke oplossing wordt de extra tabel die de afzonderlijke State-gegevens bevat, niet zichtbaar gemaakt. Zoals eerder beschreven, wordt een visual met gegevens over **State**, **Population** en **Sales** weergegeven:

![Tabellen State, Population en Sales, Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

Hier volgen de belangrijkste verschillen tussen *relaties met een veel-op-veel-kardinaliteit* en de meer gebruikelijke *Veel-1*-relaties:

* De weergegeven waarden bevatten geen lege rij die de niet-overeenkomende rijen in de andere tabel vertegenwoordigt. Ook vertegenwoordigen de waarden geen rijen waarvan de kolom die in de relatie in de andere tabel wordt gebruikt, null is.
* U kunt de functie `RELATED()` niet gebruiken, aangezien meer dan één rij gerelateerd kan zijn.
* Het gebruik van de functie `ALL()` voor een tabel betekent niet dat filters worden verwijderd die zijn toegepast op andere tabellen die via een veel-op-veelrelatie zijn gerelateerd. In het voorgaande voorbeeld heeft een meting die is gedefinieerd zoals hier is weergegeven, niet tot gevolg dat filters voor kolommen in de gerelateerde tabel CityData worden verwijderd:

    ![Voorbeeld van een script](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    Een visual met de gegevens **State**-, **Sales**- en **Sales total** zou dan deze grafische afbeelding opleveren:

    ![Visual van tabel](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

Zorg er, met de voorgaande verschillen in gedachten, voor dat de berekeningen die gebruikmaken van `ALL(<Table>)`, zoals *% van eindtotaal*, de beoogde resultaten retourneren.

## <a name="limitations-and-considerations"></a>Beperkingen en overwegingen

Er gelden enkele beperkingen voor deze *relaties met een veel-op-veel-kardinaliteit* en samengestelde modellen.

De volgende, multidimensionale Live Connect-bronnen kunnen niet worden gebruikt met samengestelde modellen:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI-gegevenssets
* Azure Analysis Services

Als u met behulp van DirectQuery verbinding maakt met deze multidimensionale bronnen, is het niet mogelijk om verbinding te maken met een andere DirectQuery-bron of deze te combineren met geïmporteerde gegevens.

De bestaande beperkingen voor het gebruik van DirectQuery gelden nog steeds wanneer u *relaties met een veel-op-veel-kardinaliteit* gebruikt. Veel van deze beperkingen gelden nu per tabel, al naargelang de opslagmodus van de tabel. Zo kan een berekende kolom in een geïmporteerde tabel verwijzen naar andere tabellen, maar kan een berekende kolom in een DirectQuery-tabel nog steeds alleen verwijzen naar kolommen in dezelfde tabel. Andere beperkingen gelden voor het gehele model als een van de tabellen in het model DirectQuery gebruikt. De functies QuickInsights en Q&A zijn bijvoorbeeld niet beschikbaar voor een model als een van de tabellen in het model de opslagmodus DirectQuery heeft.

## <a name="next-steps"></a>Volgende stappen

Zie de volgende artikelen voor meer informatie over samengestelde modellen en DirectQuery:
* [Samengestelde modellen in Power BI Desktop gebruiken](desktop-composite-models.md)
* [Opslagmodus in Power BI Desktop](desktop-storage-mode.md)
* [DirectQuery in Power BI gebruiken](desktop-directquery-about.md)
* [Power BI-gegevensbronnen](power-bi-data-sources.md)
