---
title: Aan de slag met het opmaken van Power BI-visualisaties
description: De titel, achtergrond en legenda van een visualisatie aanpassen
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6228ed70dd78ffca6cd3c8803518b2b27674576f
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389880"
---
# <a name="customize-visualization-titles-legends-and-backgrounds"></a>Titels, legenda's en achtergronden van visualisaties aanpassen

In deze zelfstudie leert u een aantal verschillende manieren om uw visualisaties aan te passen. Er zijn heel veel mogelijkheden voor het aanpassen van uw visualisaties. De beste manier om ze allemaal te leren is door het deelvenster **Indeling** te verkennen (selecteer het pictogram van een verfroller). Dit artikel helpt u op weg door te laten zien hoe u de titel, legenda en achtergrond van een visualisatie kunt aanpassen.

U kunt niet alle visualisaties aanpassen. Zie de [volledige lijst](#visualization-types-that-you-can-customize) met visualisaties voor meer informatie.

Spoel vooruit naar 04:50 in de video voor een demonstratie van het aanpassen van visualisaties:

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

Volg nu de instructies hieronder om het zelf te proberen met uw eigen gegevens.

## <a name="prerequisites"></a>Vereisten

- De Power BI-service of Power BI Desktop

- Het rapport Voorbeeld van een retailanalyse

## <a name="customize-visualization-titles-in-reports"></a>Visualisatietitels in rapporten aanpassen

Als u mee wilt doen, meld u zich aan bij de [Power BI-service](https://app.powerbi.com) en opent u het rapport [Voorbeeld van een retailanalyse](../sample-datasets.md) in de weergave [Rapport bewerken](../service-interact-with-a-report-in-editing-view.md).

> [!NOTE]
> Wanneer u een visualisatie aan een dashboard vastmaakt, wordt deze dashboardtegel. U kunt ook de tegels zelf aanpassen met [nieuwe titels, ondertitels en hyperlinks, en het formaat ervan kan worden gewijzigd](../service-dashboard-edit-tile.md).

1. Ga naar de pagina **New Stores** van het rapport **Voorbeeld van een retailanalyse**.

1. Selecteer het gegroepeerde kolomdiagram **Open Store Count by Open Month and Chain**.

1. Selecteer in het deelvenster **Visualisaties** het verfrollerpictogram om de opmaakopties weer te geven.

1. Selecteer **Titel** om die sectie uit te vouwen.

   ![Schermopname van het deelvenster Indeling met het verfrollerpictogram omkaderd en een pijl naar de vervolgkeuzelijst Titel.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-formatting-menu.png)

1. Zet de schuifregelaar **Titel** op **Aan**.

   ![Schermopname van de schuifregelaar bij Aan.](media/power-bi-visualization-customize-title-background-and-legend/onoffslider.png)

1. Als u de titel wilt wijzigen, typt u *Store count by month opened* in het veld **Titeltekst**.

1. Selecteer oranje voor **Tekenkleur** en wijzig de waarde voor **Achtergrondkleur** in geel.

    1. Selecteer de vervolgkeuzelijst en kies een kleur bij **Themakleuren**, **Recente kleuren** en **Aangepaste kleur**.

        ![Schermopname van de opties voor tekenkleur en achtergrondkleur.](media/power-bi-visualization-customize-title-background-and-legend/customizecolorpicker.png)

    1. Selecteer de vervolgkeuzelijst om het kleurvenster te sluiten.

       Sla de wijzigingen op.

       Als u om wat voor reden dan ook alle wijzigingen ongedaan wilt maken, kunt u teruggaan naar de standaardkleuren door **Standaardinstelling herstellen** te selecteren in het kleurvenster.

1. Vergroot de tekengrootte naar **12 pt**.

1. De laatste aanpassing van de grafiektitel die we doen is het uitlijnen ervan op het midden van de visualisatie.

    ![Schermopname van de uitlijningsopties met de optie Centreren geselecteerd.](media/power-bi-visualization-customize-title-background-and-legend/customizealign.png)

Op dit punt in de zelfstudie ziet de titel van uw gegroepeerde kolomdiagram er ongeveer als volgt uit:

![Schermopname van het zojuist geconfigureerde gegroepeerd kolomdiagram.](media/power-bi-visualization-customize-title-background-and-legend/tutorialprogress1.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Titel**.

![Schermopname van de optie Standaardinstelling herstellen.](media/power-bi-visualization-customize-title-background-and-legend/revertall.png)

## <a name="customize-visualization-backgrounds"></a>Visualisatieachtergrond aanpassen

Vouw met hetzelfde gegroepeerde kolomdiagram geselecteerd de opties voor  **Achtergrond** uit.

1. Zet de schuifregelaar **Achtergrond** op **Aan**.

1. Selecteer de vervolgkeuzelijst en kies een grijze kleur.

1. Wijzig de waarde voor **Doorzichtigheid** in **74%** .

Op dit punt in de zelfstudie ziet de achtergrond van uw gegroepeerde kolomdiagram er ongeveer als volgt uit:

![Schermopname van het gegroepeerde kolomdiagram met de achtergrondkleur bijgewerkt.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-customize-background.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Achtergrond**.

## <a name="customize-visualization-legends"></a>Visualisatielegenda aanpassen

1. Open de rapportpagina **Overview** en selecteer de grafiek **Total Sales Variance by FiscalMonth and District Manager**.

1. Selecteer op het tabblad **Visualisaties** het pictogram met de verfroller om het deelvenster Indeling te openen.

1. Vouw de opties bij **Legenda** uit:

      ![Schermopname van de legenda-opties.](media/power-bi-visualization-customize-title-background-and-legend/legend.png)

1. Zet de schuifregelaar **Legenda** op **Aan**.

1. Verplaats de legenda naar de linkerkant van de visualisatie.

1. Voeg een legendatitel in door **Titel** op **Aan** te zetten.

1. Typ *Managers* in het veld **Legendanaam**.

Op dit punt in de zelfstudie ziet de legenda van uw gegroepeerde kolomdiagram er ongeveer als volgt uit:

![Schermopname van de bijgewerkte legenda in het gegroepeerde kolomdiagram.](media/power-bi-visualization-customize-title-background-and-legend/legend-move.png)

Sla de wijzigingen op die u hebt aangebracht en ga naar de volgende sectie.

Als u om wat voor reden dan ook alle wijzigingen omgedaan wilt maken, selecteert u **Standaardinstelling herstellen** onderaan het aanpassingsvenster **Legenda**.

## <a name="visualization-types-that-you-can-customize"></a>Visualisatietypen die kunnen worden aangepast

Hier ziet u een lijst van de visualisaties en de aanpassingsopties die per visualisatie beschikbaar zijn:

| Visualisatie | Titel | Achtergrond | Legenda |
|:--- |:--- |:--- |:--- |
| Oppervlakte | ja | ja |ja |
| Staafdiagram | ja | ja |ja |
| Kaart | ja | ja |n.v.t. |
| Kaart met meerdere rijen | ja | ja | n.v.t. |
| Kolom | ja | ja | ja |
| Keuzelijst met invoervak | ja | ja | ja |
| Ringdiagram | ja | ja | ja |
| Choropletenkaart | ja | ja | ja |
| Trechterdiagram | ja | ja | n.v.t. |
| Meter | ja | ja | n.v.t. |
| KPI | ja | ja | n.v.t. |
| Lijn | ja | ja | ja |
| Kaart | ja | ja | ja |
| Matrix | ja | ja | n.v.t. |
| Cirkeldiagram | ja | ja | ja |
| Spreidingsdiagram | ja | ja | ja |
| Slicer | ja | ja | n.v.t. |
| Tabel | ja | ja | n.v.t. |
| Tekstvak | nee | ja | n.v.t. |
| Treemap | ja | ja | ja |
| Waterval | ja | ja | ja |

## <a name="next-steps"></a>Volgende stappen

- [Eigenschappen van X-as en Y-as aanpassen](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Aan de slag met de kleuropmaak en de eigenschappen van assen](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Basisconcepten voor gebruikers van de Power BI-service](../consumer/end-user-basic-concepts.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
