---
title: Opmaakopties toevoegen aan een aangepaste Power BI-visual
description: Een zelfstudie over hoe u opmaakopties ontwikkelt voor aangepaste Power BI-visuals
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 11/21/2018
ms.openlocfilehash: 5fa14e3aa8a303206d52359d04db05850e096d81
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194579"
---
# <a name="tutorial-adding-formatting-options-to-a-power-bi-visual"></a>Zelfstudie: Opmaakopties toevoegen aan een Power BI-visual

In deze zelfstudie leert u hoe u algemene eigenschappen toevoegt aan de visual.

In deze zelfstudie leert u het volgende:
> [!div class="checklist"]
> * Visuele eigenschappen toevoegen.
> * De visual verpakken.
> * De aangepaste visual importeren in een Power BI Desktop-rapport.

## <a name="adding-formatting-options"></a>Opmaakopties toevoegen

1. In **Power BI** selecteert u de pagina **Opmaak**.

    Als het goed is ziet u het bericht *Er zijn geen opmaakopties beschikbaar voor dit visuele element.*

    ![Opmaakpenseel](media/custom-visual-develop-tutorial-format-options/format-paintbrush.png)

2. In **Visual Studio Code** opent u het bestand *capabilities.json*.

3. Voor de matrix **dataViewMappings** voegt u **objects** toe (na regel 8).

    ```json
    "objects": {},
    ```
    ![Objecten toevoegen](media/custom-visual-develop-tutorial-format-options/add-objects.png)

4. Sla het bestand **capabilities.json** op.

5. Controleer in **Power BI** de opmaakopties opnieuw.

    > [!Note]
    > Als u de opmaakopties niet ziet, selecteert u **Aangepaste visual opnieuw laden**.

    ![Opmaakopties bekijken](media/custom-visual-develop-tutorial-format-options/view-formatting-options.png)

6. Stel de optie **Titel** in op *Uit*. U ziet dat de visual linksboven in de hoek niet langer de metingnaam weergeeft.

    ![Tegeloptie is uitgeschakeld](media/custom-visual-develop-tutorial-format-options/tile-option-off.png)

    ![Geen naamtegel](media/custom-visual-develop-tutorial-format-options/no-name-tile.png)

### <a name="adding-custom-formatting-options"></a>Aangepaste opmaakopties toevoegen

U kunt aangepaste eigenschappen toevoegen, zodat u de kleur van de cirkel en de randbreedte kunt configureren.

1. Stop de aangepaste visual in PowerShell.

2. Voeg in Visual Studio Code in het bestand **capabilities.json** het volgende JSON-fragment toe in het object **objects**.

    ```json
    "circle": {
     "displayName": "Circle",
     "properties": {
         "circleColor": {
             "displayName": "Color",
             "description": "The fill color of the circle.",
             "type": {
                 "fill": {
                     "solid": {
                         "color": true
                     }
                 }
             }
         },
         "circleThickness": {
             "displayName": "Thickness",
             "description": "The circle thickness.",
             "type": {
                 "numeric": true
                 }
             }
         }
     },
    ```

    Het JSON-fragment beschrijft een cirkel met een groepsnaam die uit twee opties bestaat, namelijk circleColor en circleThickness.

   ![De code voor Cirkeldikte](media/custom-visual-develop-tutorial-format-options/circle-thickness-code.png)

3. Sla het bestand **capabilities.json** op.

4. Selecteer in het venster **Explorer** de map **src** en vervolgens het bestand **settings.ts**. *Dit bestand staat voor de instellingen van de beginvisual*.

5. In het bestand **settings.ts** vervangt u de twee klassen door de volgende code.

    ```typescript
    export class CircleSettings {
     public circleColor: string = "white";
     public circleThickness: number = 2;
    }
    export class VisualSettings extends DataViewObjectsParser {
     public circle: CircleSettings = new CircleSettings();
    }
    ```

    ![Moduleklassen](media/custom-visual-develop-tutorial-format-options/module-classes.png)

    Deze module definieert de twee klassen. De klasse **CircleSettings** definieert twee eigenschappen met namen die overeenkomen met de objecten die in het bestand **capabilities.json** zijn gedefinieerd (**circleColor** en **circleThickness**) en stelt ook de standaardwaarden in. De klasse **VisualSettings** neemt de klasse **DataViewObjectParser** over en voegt een eigenschap met de naam **circle** toe die overeenkomt met het object dat in het bestand *capabilities.json* is gedefinieerd en retourneert een exemplaar van **CircleSettings**.

6. Sla het bestand **settings.ts** op.

7. Open het bestand **visual.ts**.

8. Voeg de volgende eigenschap in de klasse **Visual** toe.

    ```typescript
    private visualSettings: VisualSettings;
    ```
    Deze eigenschap bewaart een verwijzing naar het object **VisualSettings** en beschrijft de visuele instellingen.

    ![Visual klasse toevoegen](media/custom-visual-develop-tutorial-format-options/visual-class-add-on.png)

9. In de klasse **Visual** voegt u de volgende methode voor de **updatemethode** toe. Deze methode wordt gebruik om de opmaakinstellingen in te vullen.

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
     const settings: VisualSettings = this.visualSettings ||
    VisualSettings.getDefault() as VisualSettings;
     return VisualSettings.enumerateObjectInstances(settings, options);
    }
    ```
    Deze methode wordt gebruik om de opmaakinstellingen in te vullen.

    ![Object voor visuele instellingen](media/custom-visual-develop-tutorial-format-options/visual-settings-object.png)

10. Voeg de volgende code toe in de **updatemethode**, na de variabele **radius**.

    ```typescript
    this.visualSettings = VisualSettings.parse<VisualSettings>(dataView);

    this.visualSettings.circle.circleThickness = Math.max(0, this.visualSettings.circle.circleThickness);

    this.visualSettings.circle.circleThickness = Math.min(10, this.visualSettings.circle.circleThickness);
    ```
    Deze code haalt de indelingsopties op. De code past waarden aan die in de eigenschap **circleThickness** zijn opgegeven en converteert die waarden naar 0 als deze negatief zijn, of naar 10 als de waarde groter is dan 10.

    ![Radiusvariabele](media/custom-visual-develop-tutorial-format-options/radius.png)

11. Wijzig voor **circle element** de waarde voor **fill style** in de volgende expressie.

    ```typescript
    this.visualSettings.circle.circleColor
    ```

    ![Vult het cirkelelement op](media/custom-visual-develop-tutorial-format-options/circle-element-fill.png)

12. Wijzig voor **circle element** de waarde voor **stroke-width style** in de volgende expressie.

    ```typescript
    this.visualSettings.circle.circleThickness
    ```

    ![Circle Stroke-width](media/custom-visual-develop-tutorial-format-options/circle-stroke-width.png)

13. Sla het bestand visual.ts op.

14. Start de visual in PowerShell.

    ```powershell
    pbiviz start
    ```

15. Selecteer in **Power BI** **Automatisch opnieuw laden in-/uitschakelen** in de werkbalk die boven de visual zweeft.

16. In de opties voor **visual format** vouwt u **Circle** uit.

    ![Cirkelformaat](media/custom-visual-develop-tutorial-format-options/circle-format.png)

    Bewerk de opties **kleur** en **dikte**.

    Wijzig de waarde van **thickness** in een waarde minder dan 0 en een waarde hoger dan 10. U ziet dat de visual de waarde bijwerkt naar een toegestaan minimum of maximum.

## <a name="packaging-the-custom-visual"></a>De aangepaste visual verpakken

Voer de eigenschapswaarden in voor het aangepaste visualproject, werk het pictogrambestand bij en verpak vervolgens de visual.

1. Stop het de aangepaste visual in **PowerShell**.

2. Open het bestand **pbiviz.json** in **Visual Studio Code**.

3. Wijzig in het object **visual** de eigenschap **displayName** in *Circle Card*.

    Als u in het venster **Visualisaties** uw muiswijzer boven het pictogram houdt, verschijnt de weergavenaam.

    ![Weergavenaam van visual](media/custom-visual-develop-tutorial-format-options/display-name-viz.png)

4. Voer de volgende tekst in voor de eigenschap **beschrijving**.

    *Geeft een opgemaakte metingswaarde weer in een cirkel*

5. Voer eventueel uw eigen gegevens in het object **auteur** in.

6. Sla het bestand **pbiviz.json** op.

7. In het object **assets** ziet u dat het document een pad naar een pictogram definieert. Het pictogram is de afbeelding die in het venster **_Visualisaties_** verschijnt. Dit moet een **PNG**-bestand zijn van *20 pixels bij 20 pixels*.

8. Kopieer in Windows Explorer het bestand icon.png en plak het vervolgens om het standaardbestand in de assetmap te vervangen.

9. In Visual Studio Code, in het venster Explorer, vouwt u de map assets uit en selecteert u het bestand icon.png.

10. Bekijk het pictogram.

    ![Afbeelding van het venster visualisaties](media/custom-visual-develop-tutorial-format-options/viz-pane-image.png)

11. Zorg er in Visual Studio Code voor dat alle bestanden zijn opgeslagen.

12. Als u de aangepaste visual wilt verpakken in PowerShell, voert u de volgende opdracht uit.

    ```powershell
    pbiviz package
    ```

    ![Dist-map](media/custom-visual-develop-tutorial-format-options/dist-folder.png)

Het pakket is nu uitgepakt in de map **dist** van het project. Het pakket bevat alles dat nodig is om de aangepaste visual te importeren in de Power BI-service of een Power BI Desktop-rapport. U hebt de aangepaste visual nu verpakt en deze is nu klaar voor gebruik.

## <a name="importing-the-custom-visual"></a>De aangepaste visual importeren

U kunt het Power BI Desktop-rapport nu openen en de aangepaste visual Circle Card importeren.

1. Open **Power BI Desktop** en maak een nieuw rapport met een *voorbeeldgegevensset*

2. Selecteer in het venster **_Visualisaties_** de **weglatingstekens** en selecteer vervolgens **Importeren** in Bestand.

    ![Aangepaste visual toevoegen aan desktop](media/custom-visual-develop-tutorial-format-options/add-custom-viz-to-desktop.png)

3. Selecteer **Importeren** in het **importeervenster**.

4. Navigeer in het venster Openen naar de map **dist** in uw projectmap.

5. Selecteer het bestand **circleCard.pbiviz** en selecteer vervolgens **Openen**.

6. Selecteer **OK** wanneer de visual succesvol is geïmporteerd.

7. Controleer of de visual is toegevoegd aan het venster **_Visualisaties_** .

    ![Weergave in visualisatiepaneel in Power BI Desktop](media/custom-visual-develop-tutorial-format-options/view-in-desktop-viz-pane.png)

8. Bekijk hoe de knopinformatie verschijnt als u met uw muisaanwijzer over het pictogram **Circle Card** beweegt.

## <a name="debugging"></a>Foutopsporing

Zie de [handleiding voor foutopsporing](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/how-to-debug/) voor tips over het opsporen van fouten in uw aangepaste visual.

## <a name="next-steps"></a>Volgende stappen

U kunt uw pas ontwikkelde visuals voor anderen beschikbaar stellen door ze naar **AppSource** te verzenden. Raadpleeg [Power BI-visuals naar AppSource verzenden](office-store.md) voor meer informatie over dit proces.