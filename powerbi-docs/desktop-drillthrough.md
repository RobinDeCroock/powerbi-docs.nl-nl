---
title: Drillthrough gebruiken in Power BI Desktop
description: Informatie over inzoomen op nieuwe gegevens op een nieuwe rapportpagina in Power BI Desktop.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7c9d400b196366609caebe9f79bb9a8130a4ad11
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375177"
---
# <a name="use-drillthrough-in-power-bi-desktop"></a>Drillthrough gebruiken in Power BI Desktop
Met **drillthrough** in **Power BI Desktop** kunt u een pagina in uw rapport maken die zich richt op een bepaalde entiteit, zoals een leverancier, klant of fabrikant. Gebruikers kunnen met de rechtermuisknop op een gegevenspunt op andere rapportpagina's klikken. Vervolgens kunnen ze inzoomen op die specifieke pagina voor meer informatie die tot die context is gefilterd.

![Drillthrough gebruiken](media/desktop-drillthrough/drillthrough_01.png)

## <a name="using-drillthrough"></a>Drillthrough gebruiken
1. Als u **drillthrough** wilt gebruiken, maakt u een rapportpagina die de gewenste visuals bevat voor het type entiteit waarop u drillthrough wilt toepassen. 

    Stel, u wilt drillthrough toepassen voor fabrikanten. U kunt dan een drillthrough-pagina maken met visuals die de totale omzet, het totale aantal verzonden eenheden, omzet per categorie of per regio, enzovoort tonen. Als u vervolgens op die pagina inzoomt, ziet u de visuals die specifiek zijn voor de fabrikant die u hebt geselecteerd.

2. Op de drillthrough-pagina gaat u vervolgens naar de sectie **Velden** van het deelvenster **Visualisaties** en sleept u het veld waarop u drillthrough wilt inschakelen eveneens naar de verdieping **Drillthrough-filters**.

    ![Verdieping Drillthrough](media/desktop-drillthrough/drillthrough_02.png)

    Als u een veld toevoegt aan de verdieping **Drillthrough-filters**, wordt automatisch de knop *Terug* als visueel element gemaakt. Deze visual wordt een knop in gepubliceerde rapporten. Gebruikers die uw rapport gebruiken in de **Power BI-service**, kunnen deze knop gebruiken om naar de rapportpagina terug te gaan van waar ze vandaan komen.

    ![Afbeelding van Drillthrough](media/desktop-drillthrough/drillthrough_03.png)

## <a name="use-your-own-image-for-a-back-button"></a>Uw eigen afbeelding gebruiken voor een knop Terug    
 Omdat de knop Terug een afbeelding is, kunt u de afbeelding van die visual vervangen door elke andere gewenste afbeelding. Deze blijft gewoon werken als de knop Terug, zodat gebruikers terug kunnen gaan naar hun oorspronkelijke pagina. Als u uw eigen afbeelding wilt gebruiken voor een knop Terug, voert u de volgende stappen uit:

1. Ga naar het tabblad **Start** en selecteer de optie **Afbeelding**. Zoek de afbeelding en plaats deze op de drillthrough-pagina.

2. Selecteer de nieuwe afbeelding op de drillthrough-pagina. In de sectie **Afbeelding opmaken** stelt u de schuifregelaar **Koppeling** in op **Aan** en stelt u het **Type** in op **Terug**. De afbeelding fungeert nu als een knop Terug.

    ![Afbeelding gebruiken voor Terug](media/desktop-drillthrough/drillthrough_05.png)

    
     Nu kunnen gebruikers met de rechtermuisknop op een gegevenspunt in uw rapport klikken om een contextmenu te openen dat ondersteuning biedt om in te zoomen op die pagina. 

    ![Menu Drillthrough](media/desktop-drillthrough/drillthrough_04.png)

    Als rapportgebruikers willen inzoomen, wordt de pagina zo gefilterd dat informatie wordt weergegeven over het gegevenspunt waarop met de rechtermuisknop is geklikt. Stel, de gebruiker heeft met de rechtermuisknop geklikt op een gegevenspunt over Contoso (een fabrikant) en heeft drillthrough geselecteerd. De drillthrough-pagina die wordt weergegeven, is gefilterd op Contoso.

## <a name="pass-all-filters-in-drillthrough"></a>Alle filters in drillthrough goedkeuren

Vanaf de versie van mei 2018 van **Power BI Desktop**, kunt u alle filters die toegepast worden op het drillthrough-venster goedkeuren. U kunt bijvoorbeeld alleen een bepaalde categorie van producten selecteren, waarna de visuals worden gefilterd voor die categorie. Daarna kunt u drillthrough selecteren. U bent wellicht geïnteresseerd in hoe drillthrough er uit ziet wanneer al deze filters toegepast worden.

Als u alle toegepaste filters wilt behouden, gaat u naar de sectie **Drillthrough** van het venster **Visualisaties** en zet u de wisselknop **Alle filters goedkeuren** op **Aan**. 

![Alle filters behouden](media/desktop-drillthrough/drillthrough_06.png)

In **Power BI Desktop**-versies vóór mei 2018 werkt dit net als wanneer de wisselknop op **Uit** staat.

Wanneer u drillthrough toepast op een visual, kunt u zien welke filters er zijn toegepast als resultaat van tijdelijke filters die op de bronvisual zijn toegepast. In het venster drillthrough zijn deze tijdelijke filters cursief weergegeven. 

![Tijdelijke filters in cursief](media/desktop-drillthrough/drillthrough_07.png)

U kunt dit doen met tooltips-pagina’s, maar dat zou een vreemde ervaring zijn omdat de tooltip niet correct zou werken. Om deze reden wordt het gebruik van tooltips voor dit doel dus niet aanbevolen.

## <a name="add-a-measure-to-drillthrough"></a>Een meting aan drillthrough toevoegen

Naast het doorgeven van alle filters aan het drillthrough-venster, kunt u ook een meting (of een samengevatte numerieke kolom) toevoegen aan het drillthrough-gebied. Sleep het drillthrough-veld naar de drillthrough-kaart om het toe te passen. 

![Een meting aan drillthrough toevoegen](media/desktop-drillthrough/drillthrough_08.png)

Wanneer u een meting of samengevatte numerieke kolom toevoegt, kunt u inzoomen op de pagina als het veld wordt gebruikt in het gebied *Waarde* van een visual.

Meer hoeft u niet te doen om **drillthrough** in uw rapporten te gebruiken. Het is een uitstekende manier om een uitgebreid overzicht te krijgen van de entiteitsgegevens die u voor uw drillthrough-filter hebt geselecteerd.

## <a name="next-steps"></a>Volgende stappen

Wellicht bent u ook geïnteresseerd in de volgende artikelen:

* [Cross-rapport drillthrough gebruiken in Power BI Desktop](desktop-cross-report-drill-through.md)
* [Slicers Power BI Desktop gebruiken](visuals/power-bi-visualization-slicers.md)

