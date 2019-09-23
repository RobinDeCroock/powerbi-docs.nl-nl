---
title: Dashboardthema’s gebruiken in Power BI-service
description: Ontdek hoe u een aangepast kleurenpalet gebruikt en het toepast op een volledig dashboard in Power BI-service
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/22/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 8e444c78c1f6f9f3f0be1375f96f7381489cc069
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61143219"
---
# <a name="use-dashboard-themes-in-power-bi-service"></a>Dashboardthema’s gebruiken in Power BI-service
Met **Dashboardthema's** kunt u een kleurenthema op uw gehele dashboard toepassen, zoals zakelijke kleuren, seizoensgebonden kleuren of andere kleurthema's die u op een rapport zou willen toepassen. Bij het toepassen van een **Dashboardthema** worden voor alle visuals op het dashboard de kleuren van het geselecteerde thema gebruikt. Er zijn enkele uitzonderingen van toepassing, zoals verderop in dit artikel wordt beschreven.

![voorbeelddashboard met thema](media/service-dashboard-themes/power-bi-full-dashboard-theme.png)

Het wijzigen van de kleuren van de rapportvisuals op het dashboard heeft geen invloed op de visuals in het rapport. Ook als u tegels vastmaakt vanuit een rapport waarop al een [rapportthema is toegepast](desktop-report-themes.md), kunt u ervoor kiezen het huidige thema te behouden of het dashboardthema te gebruiken.


## <a name="prerequisites"></a>Vereisten
* Als u wilt volgen, opent u het [dashboard Voorbeeld van verkoop en marketing](sample-datasets.md).


## <a name="how-dashboard-themes-work"></a>Hoe dashboardthema's werken
Om te beginnen opent u een dashboard dat u hebt gemaakt (of waarvoor u een bewerkmachtiging hebt) en dat u wilt aanpassen. Selecteer het beletselteken (...) en kies **Dashboardthema**. 

![de optie Dashboardthema](media/service-dashboard-themes/power-bi-dashboard-theme.png)

In het dashboardvenster dat wordt weergegeven, selecteert u één van de vooraf gebouwde thema's.  In het onderstaande voorbeeld hebben we **Donker** geselecteerd.

![De optie Licht geselecteerd](media/service-dashboard-themes/power-bi-theme-menu.png)

![De optie Donker toegepast](media/service-dashboard-themes/power-bi-theme-dark.png)

## <a name="create-a-custom-theme"></a>Een aangepast thema maken

Het standaardthema voor Power BI-dashboards is **Licht**. Als u de kleuren wilt aanpassen of uw eigen thema wilt maken, selecteert u **Aangepast** in het vervolgkeuzemenu. 

![Selecteer Aangepast in het vervolgkeuzemenu](media/service-dashboard-themes/power-bi-theme-custom.png)

Gebruik de aangepaste opties om uw eigen dashboardthema te maken. Als u een achtergrondafbeelding wilt toevoegen, raden we aan een afbeelding met een minimale resolutie van 1920x1080 te gebruiken. Als u een afbeelding als achtergrond wilt gebruiken, kunt u de afbeelding uploaden naar een openbare website, de URL kopiëren en deze in het veld **Afbeeldings-URL** plakken. 

### <a name="using-json-themes"></a>JSON-thema's gebruiken
Een andere manier om een aangepast thema te maken is het uploaden van een JSON-bestand met instellingen voor alle kleuren die u maar wilt gebruiken voor uw dashboard. In Power BI Desktop gebruiken makers van rapporten JSON-bestanden om [thema's voor rapporten te maken](desktop-report-themes.md). Dezelfde JSON-bestanden kunnen worden geüpload voor dashboards of u kunt JSON-bestanden zoeken en uploaden via de [pagina met de themagalerie](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery) in de Power BI-community 

![Site met themagalerie](media/service-dashboard-themes/power-bi-theme-gallery.png)

U kunt uw aangepaste thema ook opslaan als een JSON-bestand en dit vervolgens delen met andere dashboardmakers. 

### <a name="use-a-theme-from-the-theme-gallery"></a>Een thema uit de themagalerie gebruiken

Net zoals de ingebouwde en aangepaste opties worden de kleuren automatisch toegepast op alle tegels op het dashboard zodra het thema wordt geüpload. 

1. Beweeg de muisaanwijzer over een thema en kies **Rapport weergeven**.

    ![Rapport weergeven](media/service-dashboard-themes/power-bi-choose-theme.png)

2. Schuif omlaag en zoek de koppeling naar het JSON-bestand.  Selecteer het downloadpictogram en sla het bestand op.

    ![Spring Day JSON](media/service-dashboard-themes/power-bi-theme-json.png)

3. Ga terug naar Power BI-service. In het venster Aangepast dashboardthema selecteert u **JSON-thema uploaden**.

    ![JSON uploaden](media/service-dashboard-themes/power-bi-upload-theme.png)

4. Navigeer naar de locatie waar u het JSON-themabestand hebt opgeslagen en selecteer **Openen**.

5. Op de pagina Dashboardthema selecteert u **Opslaan**. Het nieuwe thema wordt op uw dashboard toegepast.

    ![nieuw thema toegepast](media/service-dashboard-themes/power-bi-json.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

* Als uw rapport een ander thema gebruikt dan het dashboardthema, kunt u bepalen of het actuele visuele thema behouden blijft of dat het dashboardthema wordt gebruikt om consistentie te bereiken tussen visuals uit verschillende bronnen. Wanneer u een tegel op een dashboard vastmaakt, selecteert u **Huidige thema behouden** om het rapportthema te behouden. De visual, op het dashboard, behoudt het rapportthema, inclusief instellingen voor transparantie. 

    U ziet opties voor **Tegelthema’s** alleen als u het rapport in Power BI Desktop hebt gemaakt, [een rapportthema hebt toegevoegd](desktop-report-themes.md) en het rapport vervolgens naar Power BI-service hebt gepubliceerd. 

    ![Huidig geselecteerde thema behouden](media/service-dashboard-themes/power-bi-keep-current.png)

    Probeer de tegel opnieuw vast te maken en selecteer **Dashboardthema gebruiken**.

    ![Doelthema gebruiken](media/service-dashboard-themes/power-bi-use-destination.png)

* Dashboardthema's kunnen niet worden toegepast op vastgemaakte liverapportpagina’s, iframe-tegels, SSRS-tegels, werkboektegels of afbeeldingen.
* Dashboardthema's kunnen worden bekeken op mobiele apparaten, maar u kunt een dashboardthema alleen maken in Power BI-service. 
* Aangepaste dashboardthema's werken alleen met tegels die vanuit rapporten zijn vastgemaakt. 

