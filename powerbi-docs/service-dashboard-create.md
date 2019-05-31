---
title: Een Power BI-dashboard maken op basis van een rapport
description: Een Power BI-dashboard maken op basis van een rapport
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/02/2018
ms.author: maggies
ms.openlocfilehash: c42aa07fd78430c5692067ae8476b22288470c8c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61152189"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>Een Power BI-dashboard maken op basis van een rapport
U hebt [Dashboards in Power BI](service-dashboards.md) gelezen en u wilt nu uw eigen dashboard maken. Er zijn veel verschillende manieren om een dashboard te maken: op basis van een rapport, helemaal vanaf het begin, op basis van een gegevensset, door een bestaand dashboard te dupliceren, en meer.  

Het kan overweldigend zijn wanneer u voor het eerst met een dashboard aan de slag gaat, dus we gaan eerst een klein en eenvoudig dashboard maken door visualisaties vast te maken van een rapport dat al gemaakt is. Zodra u de snelstartgids hebt voltooid, zult u goed kunnen begrijpen wat de relatie tussen dashboards en rapporten is, hoe u de bewerkweergave in de rapporteditor kunt openen, hoe u tegels kunt vastmaken en hoe u tussen een dashboard en een rapport kunt navigeren. Gebruik vervolgens de koppelingen in de Inhoudsopgave aan de linkerkant of de **Volgende stappen** onderaan om verder te gaan met de moeilijkere onderwerpen.

## <a name="who-can-create-a-dashboard"></a>Wie mag een dashboard maken?
Het maken van een dashboard is een functie die beschikbaar is voor **Makers** en er zijn machtigingen nodig om het rapport te kunnen bewerken. Bewerkingsmachtigingen zijn beschikbaar voor makers van rapporten en voor de collega's die toegang hebben gekregen van de maker. Als David bijvoorbeeld een rapport maakt in workspaceABC en u vervolgens als lid van deze werkruimte toevoegt, zullen David en u allebei bewerkingsmachtigingen krijgen. Maar indien een rapport rechtstreeks met u is gedeeld of als onderdeel van een [Power BI-app](service-create-distribute-apps.md) (u **gebruikt** het rapport), kunt u geen tegels aan een dashboard vastmaken.

> **OPMERKING**: Dashboards zijn een functie van Power BI-service, niet van Power BI Desktop. Dashboards kunnen niet worden gemaakt in Power BI - Mobiel, maar wel worden [bekeken en gedeeld](consumer/mobile/mobile-apps-view-dashboard.md).
>
> 

![dashboard](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>Video: Een dashboard maken door visualisaties en afbeeldingen van een rapport vast te maken
Kijk hoe Amanda een nieuw dashboard maakt door visualisaties van een rapport vast te maken. Probeer het vervolgens zelf uit door de stappen onder de video te volgen met behulp van het voorbeeld van een Inkoopanalyse.

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

### <a name="prerequisites"></a>Vereisten
Als u mee wilt doen, moet u de Excel-werkmap met het voorbeeld van een 'Inkoopanalyse' downloaden en die in de Power BI-service openen (app.powerbi.com).

## <a name="import-a-dataset-with-a-report"></a>Een gegevensset met een rapport importeren
We gaan een van de Power BI-voorbeeldgegevenssets importeren en gebruiken om ons nieuwe dashboard te maken. Het voorbeeld dat we gebruiken is een Excel-werkmap met twee PowerView-bladen. Als de werkmap wordt geïmporteerd in Power BI, wordt er een gegevensset en een rapport toegevoegd aan uw werkruimte.  Het rapport wordt automatisch gemaakt op basis van de PowerView-werkbladen.

1. [Selecteer deze koppeling](http://go.microsoft.com/fwlink/?LinkId=529784) om het Excel-bestand met het voorbeeld van een inkoopanalyse te downloaden en op te slaan. We raden u aan het op te slaan in uw OneDrive voor bedrijven.
2. Open de Power BI-service (app.powerbi.com) in uw browser en meld u aan.
3. Selecteer **Mijn werkruimte**.
4. Selecteer in de linker navigatie **Gegevens ophalen**.

    ![Linkernavigatiedeelvenster](media/service-dashboard-create/power-bi-get-data3.png)
5. Selecteer **Bestanden**.

   ![Bestanden ophalen](media/service-dashboard-create/power-bi-select-files.png)
6. Navigeer naar de locatie waar u het Excel-bestand met het voorbeeld van een inkoopanalyse hebt opgeslagen. Selecteer het en kies **Verbinding maken**.

   ![Verbinding maken met bestanden](media/service-dashboard-create/power-bi-connectnew.png)
7. Selecteer voor deze oefening **Importeren**.

    ![Venster OneDrive voor Bedrijven](media/service-dashboard-create/power-bi-import.png)
8. Wanneer het bericht wordt weergegeven dat het importeren is voltooid, selecteert u de **x** om het bericht te sluiten.

   ![Het bericht Geslaagd](media/service-dashboard-create/power-bi-view-datasetnew.png)

### <a name="open-the-report-and-pin-some-tiles-to-a-dashboard"></a>Open het rapport en maak enkele tegels vast aan een dashboard
1. Blijf in dezelfde werkruimte en selecteer het tabblad **Rapporten**. Het zojuist geïmporteerde rapport wordt weergegeven met een geel sterretje. Selecteer de naam van het rapport om het te openen.

    ![Tabblad Rapporten](media/service-dashboard-create/power-bi-reports.png)
2. Het rapport wordt geopend in de Leesweergave. U ziet twee tabbladen aan de onderkant: Kortingsanalyse en Uitgavenoverzicht. Elk tabblad vertegenwoordigt een pagina van het rapport.
    Selecteer **Rapport bewerken** om het rapport in de bewerkweergave te openen.

    ![Rapport in leesweergave](media/service-dashboard-create/power-bi-reading-view.png)
3. Wijs een visualisatie aan om de beschikbare opties zichtbaar te maken. Als u een visualisatie aan een dashboard wilt toevoegen, selecteert u het punaisepictogram ![](media/service-dashboard-create/power-bi-pin-icon.png).

    ![De muisaanwijzer over een tegel bewegen](media/service-dashboard-create/power-bi-hover.png)
4. Omdat we een nieuw dashboard maken, selecteert u de optie **Nieuw dashboard** en geeft u het een naam.

   ![Dialoogvenster Aan dashboard vastmaken](media/service-dashboard-create/power-bi-pin-tile.png)
5. Wanneer u **Vastmaken** selecteert, wordt het nieuwe dashboard in de huidige werkruimte gemaakt. Wanneer het bericht **Aan dashboard vastgemaakt** wordt weergegeven, selecteert u **Naar dashboard gaan**. Als u wordt gevraagd of u het rapport wilt opslaan, kiest u **Opslaan**.

     ![Het bericht Geslaagd](media/service-dashboard-create/power-bi-pin-success.png)
6. In Power BI wordt het nieuwe dashboard geopend en dat bevat één tegel - de visualisatie die u zojuist hebt vastgemaakt.

   ![Dashboard met één tegel](media/service-dashboard-create/power-bi-pinned.png)
7. Selecteer de tegel om terug te gaan naar het rapport. Maak nog een paar tegels vast aan het nieuwe dashboard. Wanneer het venster **Aan dashboard vastmaken** verschijnt, selecteert u deze keer **Bestaand dashboard**.  

   ![Dialoogvenster Aan dashboard vastmaken](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>Een volledige rapportpagina aan het dashboard vastmaken
U kunt [een hele rapportpagina vastmaken als *live-tegel*](service-dashboard-pin-live-tile-from-report.md) in plaats van één visueel element per keer vast te maken. Aan de slag.

1. Selecteer het tabblad **Uitgavenoverzicht** in de rapporteditor om de 2e pagina van het rapport te openen.

   ![Tabblad Rapport](media/service-dashboard-create/power-bi-page-tab.png)

2. Deze visuele elementen moeten allemaal op uw dashboard komen.  Selecteer **Live-pagina vastmaken** in de rechterbovenhoek van de menubalk. Op een dashboard worden tegels van live-pagina’s telkens bijgewerkt wanneer de pagina wordt vernieuwd.

   ![Rechterbovenhoek van rapporteditor](media/service-dashboard-create/power-bi-pin-live.png)

3. Wanneer het venster **Aan dashboard vastmaken** verschijnt, selecteert u **Bestaand dashboard**.

   ![Dialoogvenster Aan dashboard vastmaken](media/service-dashboard-create/power-bi-pin-live2.png)

4. Wanneer het bericht verschijnt dat de bewerking is voltooid, selecteert u **Naar dashboard gaan**. Daar ziet u de tegels die u uit het rapport hebt vastgemaakt. In het onderstaande voorbeeld hebben we 2 tegels van pagina 1 van het rapport vastgemaakt en 1 live-tegel van pagina 2 van het rapport.

   ![dashboard](media/service-dashboard-create/power-bi-dashboard.png)

Gefeliciteerd, u hebt uw eerste dashboard gemaakt! Nu u een dashboard hebt, kunt u er nog veel meer mee doen.  Probeer een van de voorgestelde **Volgende stappen** hieronder, of ga er zelf mee spelen en verkennen.   

## <a name="next-steps"></a>Volgende stappen
* [Het formaat van tegels bewerken en ze verplaatsen](service-dashboard-edit-tile.md)
* [Alles over dashboardtegels](service-dashboard-tiles.md)
* [Uw dashboard delen door een app te maken](service-create-workspaces.md)
* [Power BI - basisconcepten](service-basic-concepts.md)
* [Tips voor het ontwerpen van een geweldig dashboard](service-dashboards-design-tips.md)

Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
