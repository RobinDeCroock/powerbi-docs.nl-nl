---
title: Visuals in Power BI
description: Aangepaste visualisaties in Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 68048968bf6a3f85f2bc24e55fd1288073be1d56
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415407"
---
# <a name="visuals-in-power-bi"></a>Visuals in Power BI

Als u een Power BI-rapport maakt of bewerkt, kunt u verschillende soorten visuals gebruiken. De pictogrammen voor deze visuals worden weergegeven in het deelvenster **Visualisaties**. Wanneer u [Power BI Desktop](https://powerbi.microsoft.com/desktop/) downloadt of de [Power BI-service](https://app.powerbi.com) opent, zijn deze visuals standaard beschikbaar.

![visualizations](media/power-bi-custom-visuals/power-bi-visualizations.png)

U bent echter niet beperkt tot deze set visuals. Als u het beletselteken (...) aan de onderkant selecteert, komt er een andere bron met rapportvisuals beschikbaar, *aangepaste visuals*.

Ontwikkelaars maken aangepaste visuals met SDK voor aangepaste visuals. Dankzij deze visuals kunnen zakelijke gebruikers hun gegevens weergeven op een manier die het beste aansluit bij hun bedrijf. Auteurs van rapporten kunnen de bestanden met aangepaste visuals vervolgens in hun rapporten importeren en op dezelfde manier gebruiken als alle andere Power BI-visuals. Aangepaste visuals zijn zeer belangrijke elementen in Power BI en kunnen worden gefilterd, gemarkeerd, bewerkt, gedeeld enzovoort.

Aangepaste visuals worden op drie manieren geïmplementeerd:

* Bestanden met aangepaste visuals
* Organisatievisuals
* Visuals uit de marketplace

## <a name="custom-visual-files"></a>Bestanden met aangepaste visuals

Aangepaste visuals zijn pakketten met code voor het renderen van de gegevens die ze ontvangen. Iedereen kan een aangepaste visual maken en die inpakken als één `.pbiviz`-bestand dat in een Power BI-rapport kan worden geïmporteerd.

> [!WARNING]
> Een aangepaste visual kan code bevatten met beveiligings- of privacyrisico's. Controleer of u de auteur en bron van de aangepaste visuals vertrouwt voordat u ze in uw rapport importeert.

## <a name="organizational-visuals"></a>Organisatievisuals

Power BI-beheerders kunnen aangepaste visuals voor hun organisatie goedkeuren en implementeren. Auteurs kunnen deze visuals eenvoudig vinden, bijwerken en gebruiken. Beheerders kunnen deze visuals eenvoudig beheren (bijvoorbeeld versie bijwerken, uitschakelen/inschakelen).

 [Meer informatie over organisatievisuals](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Visuals uit de marketplace

Communityleden en Microsoft hebben ten behoeve van het algemene belang beide hun aangepaste visuals bijgedragen en gepubliceerd naar de [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)-marketplace. U kun deze visuals downloaden en toevoegen aan uw Power BI-rapporten. Deze aangepaste visuals zijn door Microsoft getest en goedgekeurd op het gebied van functionaliteit en kwaliteit.

Wat is [AppSource](developer/office-store.md)? Hier vindt u apps, invoegtoepassingen en uitbreidingen voor uw Microsoft-software. AppSource is de plek waar miljoenen gebruikers van producten zoals Office 365, Azure, Dynamics 365, Cortana en Power BI oplossingen vinden die hen helpen efficiënter, slimmer of netter te werken.

### <a name="certified-visuals"></a>Gecertificeerde visuals

Visuals die zijn gecertificeerd voor Power BI, komen uit de marketplace en zijn extra uitvoerig getest op kwaliteit en worden ondersteund in aanvullende scenario's, zoals [e-mailabonnementen](service-report-subscribe.md) en [exporteren naar PowerPoint](service-publish-to-powerpoint.md).
Zie [Getting a custom visual certified](power-bi-custom-visuals-certified.md) (Aangepaste visualisaties insturen voor certificering) voor de lijst met gecertificeerde aangepaste visualisaties. Hier leest u ook hoe u uw eigen aangepaste visualisaties kunt insturen.

Bent u een webontwikkelaar en bent u geïnteresseerd in het maken van uw eigen visualisaties en wilt u deze toevoegen aan AppSource? Zie [Een aangepaste visual voor Power BI ontwikkelen](developer/custom-visual-develop-tutorial.md) als u wilt weten hoe u [aangepaste visuals naar AppSource kunt publiceren](developer/office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Een aangepaste visual vanuit een bestand importeren

1. Selecteer het beletselteken (...) onderaan het deelvenster **Visualisaties**.

    ![visualizations2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Selecteer **Importeren vanuit bestand** in de vervolgkeuzelijst.

    ![import from file](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. Selecteer in het menu **Bestand openen** het `.pbiviz`-bestand dat u wilt importeren en selecteer vervolgens **Openen**. Het pictogram voor de aangepaste visualisatie wordt toegevoegd aan de onderkant van het deelvenster **Visualisaties** en is nu beschikbaar voor gebruik in uw rapport.

    ![cv imported](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Organisatievisuals importeren

1. Selecteer het beletselteken (...) onderaan het deelvenster **Visualisaties**.

    ![visual org 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. Selecteer **Importeren uit de marketplace** in de vervolgkeuzelijst.

    ![visual org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Selecteer **MIJN ORGANISATIE** in het menu met tabbladen bovenaan.

    ![visual org 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Blader door de lijst om de visualisatie te vinden die u wilt importeren.

    ![visual org 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Selecteer **Toevoegen** om de aangepaste visual te importeren. Het bijbehorende pictogram wordt toegevoegd aan de onderkant van het deelvenster **Visualisaties** en is nu beschikbaar voor gebruik in uw rapport.

    ![visual org 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Aangepaste visualisaties downloaden of importeren uit Microsoft AppSource

Er zijn twee manieren om aangepaste visualisaties te downloaden en te importeren; vanuit Power BI en vanaf de [AppSource-website](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Aangepaste visualisaties importeren vanuit Power BI

1. Selecteer het beletselteken (...) onderaan het deelvenster **Visualisaties**.

    ![visualizations 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Selecteer **Importeren uit de marketplace** in de vervolgkeuzelijst.

    ![visual org 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Blader door de lijst om de visualisatie te vinden die u wilt importeren.

    ![import visual](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Als u meer wilt weten over een van de visualisaties, selecteert u deze.

    ![Selecteren](media/power-bi-custom-visuals/power-bi-select.png)

5. Op de detailpagina kunt u vervolgens schermafbeeldingen, video's, gedetailleerde beschrijvingen en meer bekijken.

    ![Synoptic](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Schuif naar beneden om beoordelingen te bekijken.

    ![Beoordelingen](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Selecteer **Toevoegen** om de aangepaste visual te importeren. Het bijbehorende pictogram wordt toegevoegd aan de onderkant van het deelvenster **Visualisaties** en is nu beschikbaar voor gebruik in uw rapport.

    ![visual imported](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Aangepaste visualisaties downloaden en importeren uit Microsoft AppSource

1. Ga naar [Microsoft AppSource](https://appsource.microsoft.com) en selecteer het tabblad **Apps**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Ga naar de[overzichtspagina met apps](https://appsource.microsoft.com/marketplace/apps), waar de belangrijkste apps voor elke categorie worden weergegeven, inclusief *Power BI-apps*. Aangezien we op zoek zijn naar aangepaste visuals, selecteren we in de navigatielijst aan de linkerkant de optie **Power BI-visuals** om de resultaten te beperken.

    ![AppSource-visuals](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. In AppSource ziet u nu een tegel voor elke aangepaste visualisatie.  Elke tegel bevat een momentopname van de aangepaste visual plus een korte beschrijving en een downloadkoppeling. Selecteer de tegel als u meer informatie wilt bekijken.

    ![Aangepaste visual selecteren](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. Op de detailpagina kunt u vervolgens schermafbeeldingen, video's, gedetailleerde beschrijvingen en meer bekijken. Selecteer **Nu downloaden** om de aangepaste visual te selecteren en vervolgens akkoord te gaan met de Gebruiksvoorwaarden.

    ![AppSource Get](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Selecteer de koppeling om de aangepaste visualisatie te downloaden.

    ![Downloaden](media/power-bi-custom-visuals/powerbi-custom-download.png)

    De downloadpagina bevat ook instructies voor het importeren van de aangepaste visual in Power BI Desktop en de Power BI-service.

    U kunt ook een voorbeeldrapport downloaden waarin de mogelijkheden van de aangepaste visualisatie worden gedemonstreerd.

    ![Voorbeeld proberen](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Sla het `.pbiviz`-bestand op en open vervolgens Power BI.

7. Importeer het `.pbiviz`-bestand naar uw rapport. (Raadpleeg de bovenstaande sectie [Een aangepaste visual vanuit een bestand importeren](#import-a-custom-visual-from-a-file).)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Een aangepaste visualisatie wordt bij het importeren toegevoegd aan een specifiek rapport. Als u de visualisatie in een ander rapport wilt gebruiken, moet u de visualisatie ook in dat rapport importeren. Wanneer een rapport met een aangepaste visualisatie wordt opgeslagen met de optie **Opslaan als**, wordt er een kopie van de aangepaste visualisatie opgeslagen met het nieuwe rapport.

* Als u geen deelvenster **Visualisaties** ziet, betekent dit dat u niet bevoegd bent om het rapport te bewerken.  U kunt alleen aangepaste visualisaties toevoegen aan rapporten die u kunt bewerken, niet aan rapporten die alleen met u zijn gedeeld.

## <a name="troubleshoot"></a>Problemen oplossen

Zie [Problemen met aangepaste visuals voor Power BI oplossen](power-bi-custom-visuals-troubleshoot.md) voor meer informatie.

## <a name="faq"></a>Veelgestelde vragen

Voor meer informatie en antwoorden op vragen gaat u naar [Veelgestelde vragen over aangepaste visuals voor Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Volgende stappen

* [Visualisaties in Power BI-rapporten](visuals/power-bi-report-visualizations.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/).
