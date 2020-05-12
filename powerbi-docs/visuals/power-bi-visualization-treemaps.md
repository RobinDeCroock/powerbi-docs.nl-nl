---
title: Treemaps in Power BI
description: Treemaps in Power BI
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 189cc784577df277b0b0517253699ae06842b30c
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866881"
---
# <a name="treemaps-in-power-bi"></a>Treemaps in Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

In treemaps worden hiërarchische gegevens weergegeven als een set van geneste rechthoeken. Elk niveau van de hiërarchie wordt weergegeven als een gekleurde rechthoek (een vertakking) die kleinere rechthoeken (bladeren) bevat. Power BI baseert de grootte van de ruimte in elke rechthoek op de gemeten waarde. De rechthoeken worden op grootte gerangschikt van linksboven (grootste) naar rechtsonder (kleinste).

![Schermopname van de treemap Count of Product by Category, and Manufacturer.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Als u bijvoorbeeld uw verkopen gaat analyseren, kunt u vertakkingen op het hoogste niveau maken voor de volgende kledingcategorieën: **Urban**, **Landelijk**, **Jeugd** en **Mix**. Power BI splitst de categorierechthoeken dan op in bladeren, voor de kledingfabrikanten binnen die categorie. En deze kleinere rechthoeken worden in grootte aangepast en gearceerd op basis van het aantal verkochte items.

In de vertakking **Urban** hierboven is er veel kleding van **VanArsdel** verkocht, en minder van **Natura** en **Fama**. Van het merk **Leo** zijn slechts een paar stuks verkocht. De vertakking **Urban** van uw treemap bevat:

* de grootste rechthoek voor **VanArsdel** in de linkerbovenhoek

* iets kleinere rechthoeken voor **Natura** en **Fama**

* een groot aantal andere rechthoeken voor alle andere verkochte kleding

* een heel klein rechthoekje voor **Leo**

U kunt het aantal verkochte items vergelijken met andere kledingcategorieën door de grootte en inkleuring van elk bladknooppunt met elkaar te vergelijken. Hoe groter de rechthoek en hoe donkerder de kleur, hoe hoger de waarde.


## <a name="when-to-use-a-treemap"></a>Wanneer u een treemap gebruikt

In de volgende gevallen komen treemaps goed van pas:

* wanneer u grote hoeveelheden hiërarchische gegevens wilt weergeven

* wanneer een staafdiagram niet geschikt is om het grote aantal waarden effectief te verwerken

* wanneer u de verhoudingen tussen de samenstellende delen en het geheel wilt weergeven

* wanneer u het patroon van de distributie van de meting tussen de verschillende niveaus van categorieën in de hiërarchie wilt weergeven

* wanneer u kenmerken wilt weergeven met grootte- en kleurcoderingen

* wanneer u patronen, uitbijters, de belangrijkste bijdragers en uitzonderingen wilt identificeren

## <a name="prerequisite"></a>Vereiste

In deze zelfstudie wordt gebruikgemaakt van het [PBIX-bestand met het voorbeeld van een retailanalyse](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Selecteer linksboven in de menubalk **Bestand** > **Openen**
   
2. Ga naar uw kopie van het **PBIX-bestand met het voorbeeld van een retailanalyse**

1. Open het **PBIX-bestand met het voorbeeld van een retailanalyse** in de rapportweergave ![Schermopname van het pictogram voor de rapportweergave.](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. Selecteren ![Schermopname van het gele tabblad.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) om een nieuwe pagina toe te voegen.

> [!NOTE]
> Voor het delen van uw rapport met een Power BI-collega moeten u beiden beschikken over een afzonderlijke Power BI Pro-licentie of moet het rapport zijn opgeslagen in Premium-capaciteit.    



Nadat u de gegevensset **Voorbeeld van een retailanalyse** hebt opgehaald, kunt u aan de slag.

## <a name="create-a-basic-treemap"></a>Een eenvoudige treemap maken

U gaat een rapport maken en vervolgens een eenvoudige treemap toevoegen.


1. Selecteer in het deelvenster **Velden** de meting **Sales** > **Last Year Sales**.

   ![Schermopname van Sales > Last Tear Sales geselecteerd en de resulterende visualisatie.](media/power-bi-visualization-treemaps/treemapfirstvalue-new.png)

1. Selecteer het pictogram Treemap ![Schermafbeelding van het pictogram Treemap](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) om de grafiek te converteren naar een treemap.

   ![Schermopname van de treemap zonder configuratie.](media/power-bi-visualization-treemaps/treemapconvertto-new.png)

1. Selecteer **Artikel** > **Categorie** waarmee **Categorie** ook aan de **Groep** wordt toegevoegd.

    Er wordt een treemap in Power BI gemaakt waarbij de grootte van de rechthoeken is gebaseerd op de totale omzet en de kleur een categorie vertegenwoordigt. In wezen hebt u een hiërarchie gemaakt die op visuele wijze de relatieve grootte van het totale aantal verkopen per categorie beschrijft. De categorie **Heren** is de categorie met de meeste verkopen en de categorie **Kousen** is de categorie met de minste verkopen.

    ![Schermopname van de geconfigureerde treemap.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Selecteer **Winkel** > **Keten** waarmee **Keten** ook aan **Details** wordt toegevoegd zodat de treemap is voltooid. U kunt nu de omzet van het afgelopen jaar vergelijken op basis van de categorie en de keten.

   ![Schermopname van de treemap met Store > Chain toegevoegd aan de details.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Kleurverzadiging en Details kunnen niet tegelijkertijd worden gebruikt.

1. Beweeg de cursor over het gebied **Keten** om de knopinfo voor dat gedeelte van de **Categorie** weer te geven.

    Als u bijvoorbeeld de muisaanwijzer boven **Fashions Direct** in de rechthoek **090-startpagina** houdt, ziet u in de knopinfo het aandeel van Fashions Direct in de categorie Home.

   ![Schermopname van de knopinfo voor Home.](media/power-bi-visualization-treemaps/treemaphoverdetail-new.png)


## <a name="highlighting-and-cross-filtering"></a>Markeren en kruislings filteren

Wanneer u een **categorie** of **detail** in een treemap markeert, worden de andere visualisaties op de rapportpagina kruislings gemarkeerd en gefilterd. Als u wilt meedoen, voegt u enkele visualisaties toe aan deze rapportpagina of kopieert u de treemap naar een van de andere pagina’s in dit rapport. In de onderstaande afbeelding is de treemap gekopieerd naar de pagina **Overzicht**. 

1. Selecteer in de treemap een **categorie** of een **keten** binnen een **categorie**. Hiermee worden de andere visualisaties op de pagina kruislings gemarkeerd. Wanneer u bijvoorbeeld **050-Schoenen** selecteert, kunt u zien dat er het afgelopen jaar voor **$ 16.352.432** aan schoenen is verkocht, waarvan **$ 2.174.185** afkomstig was van **Fashions Direct**.

   ![Schermopname van het rapport Store Sales Overview met kruislingse markeringen.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. Als u in het cirkeldiagram **Omzet afgelopen jaar per keten** het segment **Fashions Direct** selecteert, wordt de treemap kruislings gefilterd.
   ![Animatie ter illustratie van de functie voor kruislings filteren.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. Zie [De interactie tussen visuals in een Power BI-rapport wijzigen](../service-reports-visual-interactions.md) om te beheren hoe grafieken elkaar kruislings markeren en filteren.

## <a name="next-steps"></a>Volgende stappen

* [Watervalgrafieken in Power BI](power-bi-visualization-waterfall-charts.md)

* [Visualization types in Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md) (Typen visualisaties in Power BI)
