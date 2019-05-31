---
title: Een visual maken met Power BI Q & A
description: Meer informatie over het maken van een visueel element met Q & A in Power BI-service met behulp van de Retailanalyse als voorbeeld
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625264"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Een visual maken met Power BI Q & A

Soms krijgt u het snelst een antwoord uit uw gegevens wanneer u een vraag stelt in natuurlijke taal.  In dit artikel bekijken we twee verschillende manieren om dezelfde visualisatie te maken: eerst een vraag stellen met Q & A en het tweede, in een rapport op te bouwen. We Power BI-service gebruiken om u te maken van het visuele element in het rapport, maar het proces is bijna identiek zijn met Power BI Desktop.

![Power BI ingevuld grafiek](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Als u dit wilt volgen, moet u een rapport gebruiken dat u kunt bewerken. Daarom maken we gebruik van een van de voorbeelden die beschikbaar zijn met Power BI.

## <a name="create-a-visual-with-qa"></a>Maken van een visueel element met Q & A

Hoe gaan we over het maken van dit lijndiagram met Q & A?

1. Selecteer in de Power BI-werkruimte **Gegevens ophalen** \> **Voorbeelden** \> **Voorbeeld van een retailanalyse**  >  **Verbinding maken**.

1. Open het dashboard voorbeeld van een Retailanalyse en plaats de cursor in het Q & A-vak **een vraag stellen over uw gegevens**.

    ![Plaats de cursor in het Q & A-vak](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Typ in het vak Q & A, er ongeveer als deze vraag:
   
    **verkoop dit jaar en vorig jaar per maand als vlakdiagram**
   
    Als u een vraag typt, kiest de Q&A-functie de beste visualisatie om uw antwoord weer te geven. De visualisatie wordt dynamisch gewijzigd als u de vraag wijzigt. Q&A helpt u ook om uw vraag te formuleren door suggesties te bieden, de vraag automatisch aan te vullen en spellingcorrecties toe te passen. Q & A raadt aan om een wijziging kleine tekst: ' dit jaar en Verkoop vorig jaar per *tijd maand* als vlakdiagram '.  

    ![Q & A gecorrigeerde tekst](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Selecteer de zin om de suggestie te accepteren. 
   
   Wanneer u klaar bent met uw vraag te typen, is het resultaat hetzelfde diagram die u in het dashboard ziet.
   
   ![Q & A gevuld vlakdiagram](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Selecteer het speldpictogram om uw diagram aan het dashboard vast te maken ![Speldpictogram](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) in de rechterbovenhoek.

## <a name="create-a-visual-in-the-report-editor"></a>Een visual maken in de rapporteditor

1. Navigeer terug naar het dashboard Voorbeeld van een retailanalyse.
   
2. Het dashboard bevat de dezelfde diagramtegel voor 'Omzet van afgelopen jaar en verkoop dit jaar'.  Selecteer deze tegel. Selecteer niet de tegel die u hebt gemaakt met Q & A. Te selecteren wordt geopend Q & A. De oorspronkelijke diagramtegel is gemaakt in een rapport, zodat het rapport wordt geopend op de pagina met deze visualisatie.

    ![Voorbeelddashboard voor retailanalyse](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Open het rapport in de bewerkingsweergave en selecteer **Rapport bewerken**.  Als u niet de eigenaar van een rapport bent, kunt u het rapport niet openen in de bewerkingsweergave.
   
    ![De knop Rapport bewerken](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecteer het vlakdiagram en controleer de instellingen in het deelvenster **Velden**.  De rapportmaker dit diagram samengesteld door deze drie waarden te selecteren (**omzet van afgelopen jaar** en **omzet van dit jaar > waarde** uit de **verkoop** tabel, en  **FiscalMonth** uit de **tijd** tabel) en ze te ordenen in de **as** en **waarden** wells.
   
    ![Deelvenster Visualisaties](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    U ziet dat deze uiteindelijk met dezelfde visualisatie. Het maken ervan op deze manier niet is te gecompliceerd. Maar met Q & A te maken is eenvoudiger.

## <a name="next-steps"></a>Volgende stappen

- [Q & A gebruiken in dashboards en rapporten](power-bi-tutorial-q-and-a.md)  
- [Q & A voor consumenten](consumer/end-user-q-and-a.md)
- [Uw gegevens geschikt maken voor Q&A in Power BI](service-prepare-data-for-q-and-a.md)

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

