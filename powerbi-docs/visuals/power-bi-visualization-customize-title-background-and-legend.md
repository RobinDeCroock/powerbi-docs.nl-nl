---
title: Aan de slag met het opmaken van Power BI-visualisaties
description: Titels, labels, legenda's en achtergronden van visualisaties aanpassen
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.custom: video-OgjX-pFGgfM, video-RE4IY3L
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 1/13/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 8cfba48839f4055c7d48bf01a475cf2804053239
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422324"
---
# <a name="customize-visualization-titles-backgrounds-labels-and-legends"></a>Titels, labels, legenda's en achtergronden van visualisaties aanpassen

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

In deze zelfstudie leert u een aantal verschillende manieren om uw visualisaties aan te passen. Er zijn heel veel mogelijkheden voor het aanpassen van uw visualisaties. De beste manier om ze allemaal te leren is door het deelvenster **Indeling** te verkennen (selecteer het pictogram van een verfroller). Dit artikel helpt u op weg door te laten zien hoe u een titel, legenda, label, laag en achtergrond van een visualisatie kunt aanpassen en een thema kunt toevoegen.

U kunt niet alle visualisaties aanpassen. Zie de [volledige lijst](#visualization-types-that-you-can-customize) met visualisaties voor meer informatie.

## <a name="prerequisites"></a>Vereisten

- De Power BI-service of Power BI Desktop

- Het rapport Voorbeeld van een retailanalyse

> [!NOTE]
> Voor het delen van uw rapport met een Power BI-collega moet u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in Premium-capaciteit. Zie [Rapporten delen](../collaborate-share/service-share-reports.md) voor meer informatie.

## <a name="customize-visualization-titles-in-reports"></a>Visualisatietitels in rapporten aanpassen

Als u mee wilt doen, meld u dan aan bij Power BI Desktop en open het rapport [Voorbeeld van een retailanalyse](../create-reports/sample-datasets.md).

> [!NOTE]
> Wanneer u een visualisatie aan een dashboard vastmaakt, wordt deze dashboardtegel. U kunt ook de tegels zelf aanpassen met [nieuwe titels, ondertitels, hyperlinks, en door het formaat ervan te wijzigen](../create-reports/service-dashboard-edit-tile.md).

1. Ga naar de pagina **New Stores** van het rapport **Voorbeeld van een retailanalyse**.

1. Selecteer het gegroepeerde kolomdiagram **Open Store Count by Open Month and Chain**.

1. Selecteer in het deelvenster **Visualisaties** het verfrollerpictogram om de opmaakopties weer te geven.

1. Selecteer **Titel** om die sectie uit te vouwen.

   ![Schermopname van het deelvenster Indeling met het verfrollerpictogram omkaderd en een pijl naar de vervolgkeuzelijst Titel.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Zet de schuifregelaar **Titel** op **Aan**.

1. Als u de titel wilt wijzigen, typt u *Store count by month opened* in het veld **Titeltekst**.

    ![Schermopname van het deelvenster Indeling met de ingevoerde titeltekst.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Wijzig **Tekenkleur** in wit en **Achtergrondkleur** in blauw.

    a. Selecteer de vervolgkeuzelijst en kies een kleur bij **Themakleuren**, **Recente kleuren** en **Aangepaste kleur**.

    ![Schermopname van de opties voor tekenkleur en achtergrondkleur.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Selecteer de vervolgkeuzelijst om het kleurvenster te sluiten.

1. Vergroot de tekengrootte naar **16 pt**.

1. De laatste aanpassing van de grafiektitel die we doen is het uitlijnen ervan op het midden van de visualisatie.

    ![Schermopname van de uitlijningsopties met de optie Centreren geselecteerd.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    Op dit punt in de zelfstudie ziet de titel van uw gegroepeerde kolomdiagram er ongeveer als volgt uit:

    ![Schermopname van het zojuist geconfigureerde gegroepeerd kolomdiagram.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Titel**.

![Schermopname van de optie Standaardinstelling herstellen.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Visualisatieachtergrond aanpassen

Vouw met hetzelfde gegroepeerde kolomdiagram geselecteerd de opties voor  **Achtergrond** uit.

1. Zet de schuifregelaar **Achtergrond** op **Aan**.

1. Selecteer de vervolgkeuzelijst en kies een grijze kleur.

1. Wijzig de waarde voor **Doorzichtigheid** in **74%** .

Op dit punt in de zelfstudie ziet de achtergrond van uw gegroepeerde kolomdiagram er ongeveer als volgt uit:

![Schermopname van het gegroepeerde kolomdiagram met de achtergrondkleur bijgewerkt.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Achtergrond**.

## <a name="customize-visualization-legends"></a>Visualisatielegenda aanpassen

1. Open de rapportpagina **Overview** en selecteer de grafiek **Total Sales Variance by FiscalMonth and District Manager**.

1. Selecteer op het tabblad **Visualisaties** het pictogram met de verfroller om het deelvenster Indeling te openen.

1. Vouw de opties bij **Legenda** uit:

    ![Schermopname van de legendakaart.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Zet de schuifregelaar **Legenda** op **Aan**.

1. Verplaats de legenda naar de linkerkant van de visualisatie.

1. Voeg een legendatitel in door **Titel** op **Aan** te zetten.

1. Typ *Manager* in het veld **Legendanaam**.

1. Wijzig **Kleur** in zwart.

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Legenda**.

## <a name="customize-total-labels-for-stacked-visuals"></a>Totaal aantal labels voor gestapelde visuals aanpassen

In gestapelde visuals kunnen gegevenslabels en het totaal aantal labels worden weergeven. In een gestapeld kolomdiagram geven gegevenslabels de waarde aan voor elk deel van een kolom. Het totaal aantal labels geeft de totale waarde van de hele geaggregeerde kolom weer. 

Kijk hoe Egbert het totaal aantal labels aan een gestapeld diagram toevoegt en volg de onderstaande stappen om het zelf te doen.

> [!VIDEO https://www.youtube.com/embed/OgjX-pFGgfM]

1. Open de rapportpagina **Overzicht** en selecteer het staafdiagram **Gemiddelde grootte van verkoopgebied op keten en winkeltype**.

1. Selecteer op het tabblad **Visualisatie** ![ pictogram voor het gestapelde staafdiagram](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-bar.png) om dit staafdiagram om te zetten in een gestapeld staafdiagram. U ziet dat de visual de gegevenslabels heeft behouden.

    ![Schermopname van het nieuwe gestapelde staafdiagram.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-chart.png)

1. Selecteer op het tabblad **Visualisaties** het pictogram met de verfroller om het deelvenster Indeling te openen.

1. Verplaats de schuifregelaar **Totaal aantal labels** naar de positie **Aan**. 

    ![Schermopname van de schuifregelaar Totaal aantal labels op de positie Aan.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-totals.png)

1. U kunt eventueel het totaal aantal labels indelen. In dit voorbeeld hebben we de kleur gewijzigd in zwart, de tekengrootte vergroot en ervoor gekozen de waarden weer te geven als **duizendtallen**.

    ![Schermopname van het nieuwe gestapelde staafdiagram met het totaal aantal labels.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-bar-totals.png)

## <a name="customize-layer-order"></a>De laagvolgorde aanpassen

Wijzig de laagvolgorde van visuals en vormen in uw rapporten. Met de laagvolgorde bepaalt u welke objecten naar de voorgrond worden verplaatst wanneer u deze selecteert. Telkens wanneer u een object op het rapportcanvas selecteert, wordt dit actief en naar de bovenste laag verplaatst. Voor visuals betekent dit dat u gemakkelijker met de geselecteerde visual kunt werken. Maar voor vormen en achtergronden is het handiger om deze vast te maken aan de onderste laag, zodat u ze niet per ongeluk kunt selecteren en uw rapportvisuals bedekt of verbergt. 

Besturingselementen voor lagen zijn beschikbaar in de Power BI-service, Power BI Desktop, mobiele toepassingen en de rapportserver. In dit artikel leest u hoe u het gedrag van de laagvolgorde wijzigt in de Power BI-service.

Kijk hoe Egbert het gedrag van de laagvolgorde wijzigt en volg de onderstaande stappen om het zelf te doen.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4IY3L]

1. Voeg een nieuwe rapportpagina toe door het gele plusteken te selecteren.

1. Voeg een vorm toe aan het canvas. Hier is een blauwe rechthoek toegevoegd.

    ![Schermopname van de nieuwe rapportpagina met een blauwe rechthoek.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-shape.png)

1. Kopieer en plak een visual van een andere pagina in het rapport.

    ![Schermopname van de nieuwe rapportpagina met een blauwe rechthoek en een cirkeldiagram.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-layer.png)

    U hebt nu twee lagen. Probeer het cirkeldiagram en vervolgens de achtergrond te selecteren. Wanneer u het cirkeldiagram selecteert, wordt dat object in Power Bi geactiveerd en wordt het koptekstmenu van dat object weergegeven. Wanneer u de rechthoek selecteert, wordt dat object in Power Bi geactiveerd en naar voren gebracht, waar dit object het cirkeldiagram verbergt. U kunt dit standaardgedrag wijzigen.

1. Selecteer de rechthoek en open het deelvenster Opmaak. Vouw **Algemeen** uit en zoek de wisselknop **Laagvolgorde behouden**. Sla de rapportwijzigingen op en ga terug naar de leesweergave.

    ![Schermopname van de nieuwe rapportpagina, waarbij Laagvolgorde behouden is ingesteld op Aan.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-maintain-layer.png)

1. Wanneer u in de leesweergave de blauwe rechthoek selecteert, blijft deze nu in de achterste laag.

## <a name="customize-colors-using-a-theme"></a>Kleuren aanpassen met behulp van een thema

Met rapportthema's past u ontwerpwijzigingen toe op uw hele rapport. U kunt bijvoorbeeld uw bedrijfskleuren gebruiken, pictogrammen veranderen of een nieuwe indeling van visuals toepassen. Wanneer u een rapportthema toepast, worden voor alle visuals in het rapport de kleuren en indeling van het geselecteerde thema gebruikt.

Als u een thema wilt toepassen op uw rapport, selecteert u **Thema wisselen** in de menubalk. Kies een thema.  In het onderstaande rapport wordt gebruikgemaakt van het thema **Zon**.

![Rapporteren met behulp van thema Zon van gele, oranje en rode elementen](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Visualisatietypen die kunnen worden aangepast

Hier ziet u een lijst van de visualisaties en de aanpassingsopties die per visualisatie beschikbaar zijn:

| Visualisatie | Titel | Achtergrond | Legenda | Totaal aantal labels
|:--- |:--- |:--- |:--- |:--- |
| Gebied | ja | ja |ja | ja  |
| Staafdiagram | ja | ja |ja | ja |
| Kaart | ja | ja |n.v.t. | n.v.t. |
| Kaart met meerdere rijen | ja | ja | n.v.t. | n.v.t. |
| Kolom | ja | ja | ja |  ja |
| Keuzelijst met invoervak | ja | ja | ja | ja |
| Ringdiagram | ja | ja | ja | n.v.t. |
| Choropletenkaart | ja | ja | ja |n.v.t. |
| Trechterdiagram | ja | ja | n.v.t. |n.v.t. |
| Meter | ja | ja | n.v.t. |n.v.t. |
| Belangrijkste beïnvloeder | ja | ja | n.v.t. |n.v.t. |
| KPI | ja | ja | n.v.t. |n.v.t. |
| Lijn | ja | ja | ja |n.v.t. |
| Kaart | ja | ja | ja |n.v.t. |
| Matrix | ja | ja | n.v.t. |ja |
| Cirkeldiagram | ja | ja | ja |n.v.t. |
| Q&A | ja | ja | n.v.t. |n.v.t. |
| Spreidingsdiagram | ja | ja | ja |n.v.t. |
| Vorm | ja | ja | ja |n.v.t. |
| Slicer | ja | ja | n.v.t. |n.v.t. |
| Tabel | ja | ja | n.v.t. |ja |
| Tekstvak | nee | ja | n.v.t. |n.v.t. |
| Treemap | ja | ja | ja |n.v.t. |
| Waterval | ja | ja | ja |n.v.t. |

## <a name="next-steps"></a>Volgende stappen

- [Eigenschappen van X-as en Y-as aanpassen](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Aan de slag met de kleuropmaak en de eigenschappen van assen](service-getting-started-with-color-formatting-and-axis-properties.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
