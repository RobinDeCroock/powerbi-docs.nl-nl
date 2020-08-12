---
title: Een trechtertekening bouwen van R-script naar R-visual
description: In dit artikel wordt beschreven hoe u een trechtertekening bouwt van R-script naar R Power BI visual.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: 2cc37d1296d7f170bf8c6280465e7a3f1aa52e33
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878707"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Zelfstudie: Een trechtertekening bouwen van R-script naar R-visual
In dit artikel wordt stap voor stap beschreven hoe u een trechtertekening bouwt met R-script in R visual.

In dit artikel leert u het volgende:

> [!div class="checklist"]
>
> * een R-script voor RStudio maken
> * een R-visual in Power BI maken
> * een *op PNG gebaseerde* R-visual in Power BI maken
> * een *op HTML gebaseerde* R-visual in Power BI maken

De trechtertekening biedt een eenvoudige manier om de hoeveelheid verwachte variatie te consumeren, te interpreteren en weer te geven. De **trechter** wordt gevormd met betrouwbaarheidslimieten en uitschieters worden weergegeven als stippen buiten de trechter.

In dit voorbeeld wordt de trechtertekening gebruikt om verschillende set gegevens te vergelijken en te analyseren.  

> [!NOTE]
> De bronbestanden kunnen worden gedownload onder elke reeks stappen.

## <a name="build-an-r-script-with-dataset"></a>Een R-script met gegevensset maken

1. Download een [minimaal R-script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) en de bijbehorende gegevenstabel, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Bewerk vervolgens het script om [dit script ](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r)te spiegelen. Hiermee worden invoerfoutverwerking en gebruikersparameters toegevoegd om het uiterlijk van de tekening te bepalen.

## <a name="build-a-report"></a>Een rapport maken

Bewerk vervolgens het script om [dit script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r)te spiegelen. Hierdoor wordt *dataset.csv* in plaats van *read.csv* in de Power BI-desktopwerkruimte geladen en wordt een **Cancer Mortality**-tabel gemaakt. Bekijk de resultaten in het volgende [PBIX-bestand](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix).

> [!NOTE]
> De `dataset` is een in code vastgelegde naam voor de invoer `data.frame` van een willekeurige R-visual. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Een R-visual en -pakket maken in R-code

1. Voordat u begint, moet u [PBIVIZ-hulpprogramma’s](./custom-visual-develop-tutorial.md#installing-packages) installeren.

1. Voer de volgende opdracht uit om een nieuwe R-visual te maken:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Met deze opdracht wordt de map *trechter-visual* gemaakt met de eerste sjabloonvisual (`-t` voor **sjabloon**). De PBIVIZ is te vinden in de map *dist*, de R-code in het *script.r*-bestand. Probeer deze te importeren in Power BI en kijk wat er gebeurt.

1. Bewerk het *script.r*-bestand en vervang de inhoud door het vorige script.

1. Bewerk *capabilities.json* en vervang de tekenreeks `Values` door `dataset`. Hiermee vervangt u de naam van Rol in de sjabloon, zoals in de R-code.

   ![voor versus na](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(optioneel)* Bewerk *dependencies.json* en voeg een sectie toe voor elk R-pakket dat vereist is voor het R-script. Hiermee wordt Power BI gevraagd deze pakketten automatisch te importeren wanneer de visual voor de eerste keer wordt geladen.

   ![voor versus na](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Verpak de visual opnieuw met de opdracht `pbiviz package` en probeer deze in Power BI te importeren.

> [!NOTE]
> Zie [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) en [broncode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) om te downloaden.

## <a name="make-r-based-visual-improvements"></a>Op R gebaseerde visuele verbeteringen aanbrengen

De visual is nog niet gebruiksvriendelijk omdat de gebruiker de volgorde van kolommen in de invoertabel moet kennen.

1. Deel het invoerveld `dataset` in drie velden (rollen): `Population`, `Number`en `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Bewerk *capabilities.json* en vervang de `dataset` rol door de drie nieuwe rollen, of download [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   U moet secties bijwerken: `dataRoles` en `dataViewMappings`, waarmee namen, typen, knopinfo en maximum kolommen voor elk invoerveld worden gedefinieerd.

   ![eerder en later](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Voor meer informatie, zie [capabilities](./capabilities.md).

1. Bewerk *script.r* ter ondersteuning van `Population`,`Number` en `Tooltips` als invoergegevensframes in plaats van `dataset`, of download [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Als u de wijzigingen in het R-script wilt volgen, zoekt u naar opmerkingsblokken: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Verpak de visual opnieuw met de opdracht `pbiviz package` en probeer deze in Power BI te importeren.

> [!NOTE]
> Zie [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) en [broncode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) om te downloaden.

## <a name="add-user-parameters"></a>Gebruikersparameters toevoegen

1. Voeg mogelijkheden toe voor de gebruiker om kleuren en grootte van visuele elementen te beheren, inclusief interne parameters uit de gebruikersinterface.

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. Bewerk *capabilities.json* en werk de sectie `objects` bij. Hier definiëren we namen, knopinfo en typen van elke parameter en beslissen we ook over de verdeling van parameters in groepen (drie groepen in dit geval).

   download [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json), zie [objecteigenschappen](./objects-properties.md) voor meer informatie

   ![mogelijkheden](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Bewerk *src/settings.ts* om [ deze settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts) te spiegelen. Dit bestand is geschreven in TypeScript.  

   Hier vindt u twee blokken van de code toegevoegd aan:
   - Nieuwe interface declareren om de eigenschapswaarde vast te houden
   - Een lideigenschap en standaardwaarden definiëren

   ![instellingen](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Bewerk *script.r* om [dit script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r) te spiegelen. Hiermee voegt u ondersteuning toe voor de parameters in de gebruikersinterface door `if.exists`-aanroepen per gebruikersparameter toe te voegen.

   > [!TIP]
   > Als u de wijzigingen in het R-script wilt volgen, zoekt u naar opmerkingen:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![Script eerder en later](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   U kunt besluiten de parameters niet beschikbaar te maken voor de gebruikersinterface, zoals wij hebben gedaan.  

1. Verpak de visual opnieuw met de opdracht `pbiviz package` en probeer deze in Power BI te importeren.

> [!NOTE]
> Zie [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) en [broncode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) om te downloaden.

> [!TIP]
> Hier hebben we parameters van verschillende typen (booleaans, numeriek, tekenreeks en kleur) in één keer toegevoegd. Voor een eenvoudig geval, zie [dit voorbeeld](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) over hoe u een enkele parameter toe kunt voegen. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Visueel element converteren naar RHTML-gebaseerde visual

Aangezien deze visual op PNG gebaseerd is, reageert het niet op muisaanwijzing, kan niet worden ingezoomd, enzovoort, dus moet het worden geconverteerd naar een op HTML gebaseerde visual. We maken een lege, op HTML-gebaseerde R-visual-sjabloon en kopiëren vervolgens enkele scripts van het op PNG gebaseerde project.

1. Voer de opdracht uit:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Open *capabilities.json* en noteer de `"scriptOutputType":"html"`-lijn.

1. Open *dependencies.json* en noteer de namen van de vermelde R-pakketten.

1. Open *script.r* en noteer de structuur. U kunt deze openen en uitvoeren in RStudio omdat deze geen externe invoer gebruikt. 

   Hiermee wordt *outout.html* gemaakt en opgeslagen. Dit bestand is onafhankelijk (zonder externe afhankelijkheden) en definieert de afbeeldingen in de HTML-widget. 

   > [!IMPORTANT]
   > Voor `htmlWidgets`-gebruikers worden R-hulpprogramma's in de map [r_files opgenomen](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) om `plotly`- of `widget`-objecten te converteren naar onafhankelijke HTML-inhoud. 
   > 
   > Deze versie van R-powered visual ondersteunt ook de `source`-opdracht (in tegenstelling tot eerdere typen visuals), om uw code leesbaarder te maken.   
 
1. Vervang *capabilities.json* door de *capabilities.json* van de vorige stap, of download [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Behoud het volgende:

   `"scriptOutputType": "html"`

1. Voeg de nieuwste versie van *script.r* samen met de *script.r* van de sjabloon of download [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   Het nieuwe script gebruikt het `plotly`-pakket om het object **ggplot** om te zetten in een **plotly**-object en vervolgens het`htmlWidgets`-pakket om het op te slaan in een HTML-bestand. 

   De meeste functies van het hulpprogramma worden verplaatst naar [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) en de functie `generateNiceTooltips` wordt toegevoegd voor het uiterlijk van het **plotly**-object.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Als u de wijzigingen in het R-script wilt volgen, zoekt u naar opmerkingen:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Voeg de nieuwste versie van *dependencies.json* samen met de *dependencies.json* van de sjabloon, om nieuwe R-pakket afhankelijkheden op te nemen of download [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Bewerk *src/settings.ts* op dezelfde manier als bij eerdere stappen.

1. Verpak de visual opnieuw met de opdracht `pbiviz package` en probeer deze in Power BI te importeren.

> [!NOTE]
> Zie [PBIX en broncode](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) om te downloaden.

## <a name="build-additional-examples"></a>Aanvullende voorbeelden bouwen

1. Voer de volgende opdracht uit om een leeg project te maken: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Neem code uit deze [showcase](http://www.htmlwidgets.org/showcase_networkD3.html) en breng de gemarkeerde wijzigingen aan:

   ![Gemarkeerde wijzigingen](./media/funnel-plot/diagram-three.PNG)

1. Vervang de *script.r* van uw sjabloon en voer `pbiviz package` opnieuw uit. Nu is de visual opgenomen in uw Power BI-rapport.

## <a name="tips-and-tricks"></a>Tips en trucs

* We raden ontwikkelaars aan *pbiviz.json* te bewerken om de juiste metagegevens op te slaan, zoals **versie**,**e-mail**,**naam**,**licentietype**, enzovoort.

   > [!IMPORTANT]
   > Het veld **guid** is de unieke id voor een visual. Als u voor elke visual een nieuw project maakt, is de GUID ook anders. Het is alleen hetzelfde bij het gebruik van een oud project gekopieerd naar een nieuwe visual, hetgeen u niet zou moeten doen.

* Bewerk [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) om unieke pictogrammen voor uw visual te maken. 

* Als u fouten wilt opsporen in R-code in RStudio met dezelfde gegevens als in uw Power BI-rapport, voegt u het volgende toe aan het begin van het R-script (bewerk de variabele `fileRda`):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Dit bewaart de omgeving van een Power BI-rapport en laadt deze in RStudio. 

* U hoeft geen R-visuals vanaf nul te ontwikkelen met code die beschikbaar is op [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). U kunt de visual selecteren die u als sjabloon wilt gebruiken en de code naar een nieuw project kopiëren.

   Gebruik bijvoorbeeld de[aangepaste spline-visual](https://github.com/Microsoft/PowerBI-visuals-spline).

* Elke R Visual past de operator `unique` toe op de invoertabel. Als u wilt voorkomen dat identieke rijen worden verwijderd, moet u overwegen een extra invoerveld met een unieke id toe te voegen en deze te negeren in de R-code.   

* Als u een Power BI-account hebt, gebruikt u de Power BI-service om een visual [direct](/power-bi/developer/visuals/custom-visual-develop-tutorial/) te ontwikkelen in plaats van ze opnieuw te verpakken met de opdracht `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galerie HTML-widgets
Bekijk visuals in de galerie [HTML-widgets](http://gallery.htmlwidgets.org/) voor gebruik in uw volgende visual. Om het gemakkelijk te maken, hebben we een [projectopslagplaats](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) met meer dan 20 interactieve HTML-visuals om uit te kiezen!

> [!TIP]
> Als u wilt schakelen tussen html-widgets, gebruikt u **Indeling** > **Instellingen** > **Type**. Probeer het uit met [dit PBIX-bestand](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Een voorbeeld gebruiken voor uw visual

1. Download de hele map.
1. Bewerk *script.r* en *dependencies.json* om slechts één widget te behouden.
1. Bewerk *capabilities.json* en *settings.ts* om de `Type`-selector te verwijderen.
1. Wijzig `const updateHTMLHead: boolean = true;` in `false` in *visual.ts*. *(voor betere prestaties)*
1. Wijzig metagegevens in *pbiviz.json*, vooral het veld `guid`.
1. Verpak opnieuw en blijf de visual aanpassen zoals gewenst. 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Niet alle widgets in dit project worden ondersteund door de service.

## <a name="next-steps"></a>Volgende stappen

Zie voor meer informatie aanvullende zelfstudies over [Power BI-visuals](./custom-visual-develop-tutorial.md) en [R-visuals](/power-bi/visuals/service-r-visuals).

Bekijk hoe u visuals kunt [ontwikkelen en verzenden](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) naar de [Office Store (galerie)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI) of voor andere voorbeelden de showcase [R-script bekijken](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)
