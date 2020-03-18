---
title: Drillthrough gebruiken in Power BI Desktop
description: Informatie over drillthrough om in te zoomen op nieuwe gegevens op een nieuwe rapportpagina in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/05/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 020b7e0a5fd0c3372e3a83d9973a404978e56b7d
ms.sourcegitcommit: 743167a911991d19019fef16a6c582212f6a9229
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78401240"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Drillthrough gebruiken in Power BI Desktop
Met *drillthrough* in Power BI Desktop kunt u een pagina in uw rapport maken die zich richt op een bepaalde entiteit, zoals een leverancier, klant of fabrikant. U kunt drillthrough gebruiken door met de rechtermuisknop op een gegevenspunt in andere rapportpagina's te klikken en in te zoomen op die specifieke pagina voor gefilterde details met betrekking tot die context.

![Drillthrough gebruiken](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Drillthrough gebruiken
1. Als u drillthrough wilt gebruiken, maakt u een rapportpagina die de gewenste visuals bevat voor het type entiteit waarop u drillthrough wilt toepassen. 

    Stel, u wilt drillthrough toepassen voor fabrikanten. U kunt in dat geval een drillthrough-pagina maken met visuals die de totale omzet, het totale aantal verzonden eenheden, omzet per categorie of per regio, enzovoort tonen. Als u vervolgens op die pagina inzoomt, ziet u de visuals die specifiek zijn voor de fabrikant die u hebt geselecteerd.

2. Op de drillthrough-pagina gaat u vervolgens naar de sectie **Velden** van het deelvenster **Visualisaties** en sleept u het veld waarop u drillthrough wilt inschakelen eveneens naar de verdieping **Drillthrough-filters**.

    ![Verdieping Drillthrough](media/desktop-drillthrough/drillthrough_02.png)

    Als u een veld toevoegt aan de verdieping **Drillthrough-filters**, wordt in Power BI Desktop automatisch de knop *Terug* als visueel element gemaakt. Deze visual wordt een knop in gepubliceerde rapporten. Gebruikers die uw rapport gebruiken in de Power BI-service, kunnen deze knop gebruiken om naar de rapportpagina terug te gaan van waar ze vandaan komen.

    ![Afbeelding van Drillthrough](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> U kunt een drillthrough voor een pagina in hetzelfde rapport configureren en uitvoeren, maar niet voor een pagina in een ander rapport.  



## <a name="use-your-own-image-for-a-back-button"></a>Uw eigen afbeelding gebruiken voor een knop Terug    
 Omdat de knop Terug een afbeelding is, kunt u de afbeelding van die visual vervangen door elke andere gewenste afbeelding. Deze blijft gewoon werken als de knop Terug, zodat gebruikers terug kunnen gaan naar hun oorspronkelijke pagina. 

Als u uw eigen afbeelding wilt gebruiken voor de knop Terug, volgt u deze stappen:

1. Ga naar het tabblad **Start** en selecteer de optie **Afbeelding**. Zoek vervolgens de afbeelding en plaats deze op de drillthrough-pagina.

2. Selecteer de nieuwe afbeelding op de drillthrough-pagina. In het deelvenster **Afbeelding opmaken** stelt u de schuifregelaar **Actie** in op **Aan** en stelt u het **Type** in op **Terug**. De afbeelding fungeert nu als een knop Terug.

    ![Afbeelding laden en Type instellen op Terug](media/desktop-drillthrough/drillthrough_05.png)

    
     Nu kunnen gebruikers met de rechtermuisknop op een gegevenspunt in uw rapport klikken om een contextmenu te openen dat ondersteuning biedt om in te zoomen op die pagina. 

    ![Menu Drillthrough](media/desktop-drillthrough/drillthrough_04.png)

    Als rapportgebruikers willen inzoomen, wordt de pagina zo gefilterd dat informatie wordt weergegeven over het gegevenspunt waarop met de rechtermuisknop is geklikt. Stel, de gebruiker heeft met de rechtermuisknop geklikt op een gegevenspunt over Contoso, een fabrikant, en heeft drillthrough geselecteerd. De drillthrough-pagina die wordt weergegeven, is gefilterd op Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Alle filters in drillthrough goedkeuren

U kunt alle toegepaste filters doorgeven aan het drillthrough-venster. U kunt bijvoorbeeld alleen een bepaalde categorie van producten selecteren, waarna de visuals worden gefilterd voor die categorie. Daarna kunt u drillthrough selecteren. U bent wellicht geïnteresseerd in hoe drillthrough er uit ziet wanneer al deze filters toegepast worden.

Als u alle toegepaste filters wilt behouden, gaat u naar de sectie **Drillthrough** van het venster **Visualisaties** en stelt u **Alle filters behouden** in op **Aan**. 

![Alle filters behouden](media/desktop-drillthrough/drillthrough_06.png)


Wanneer u drillthrough toepast op een visual, kunt u zien welke filters er zijn toegepast als resultaat van tijdelijke filters die op de bronvisual zijn toegepast. In de sectie **Drillthrough** van het deelvenster **Visualisatie** worden deze tijdelijke filters cursief weergegeven. 

![Tijdelijke filters in cursief](media/desktop-drillthrough/drillthrough_07.png)

U kunt dit doen met tooltips-pagina’s, maar dat zou een vreemde ervaring zijn omdat de tooltip niet correct zou werken. Om deze reden wordt het gebruik van tooltips voor dit doel dus niet aanbevolen.

## <a name="add-a-measure-to-drillthrough"></a>Een meting aan drillthrough toevoegen

Naast het doorgeven van alle filters aan het drillthrough-venster, kunt u ook een meting (of een samengevatte numerieke kolom) toevoegen aan het drillthrough-gebied. Sleep het drillthrough-veld naar de kaart **Drillthrough** om het toe te passen. 

![Een meting aan drillthrough toevoegen](media/desktop-drillthrough/drillthrough_08.png)

Wanneer u een meting of samengevatte numerieke kolom toevoegt, kunt u inzoomen op de pagina als het veld wordt gebruikt in het gebied *Waarde* van een visual.

Meer hoeft u niet te doen om drillthrough in uw rapporten te gebruiken. Het is een uitstekende manier om een uitgebreid overzicht te krijgen van de entiteitsgegevens die u voor uw drillthrough-filter hebt geselecteerd.

## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Drillthrough voor meerdere rapporten gebruiken in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Slicers Power BI Desktop gebruiken](visuals/power-bi-visualization-slicers.md)

