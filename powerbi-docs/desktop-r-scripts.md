---
title: R-scripts uitvoeren in Power BI Desktop
description: R-scripts uitvoeren in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 188669525a210afc516cc9740d5d7e7c5682ea93
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514719"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>R-scripts uitvoeren in Power BI Desktop
U kunt R-scripts rechtstreeks in **Power BI Desktop** uitvoeren en de resulterende gegevenssets in een Power BI Desktop-gegevensmodel importeren.

## <a name="install-r"></a>R installeren
Als u R-scripts wilt uitvoeren in Power BI Desktop, moet u **R** afzonderlijk installeren op de lokale computer. U kunt **R** gratis downloaden en installeren vanaf tal van locaties, waaronder de [Revolution Open-downloadpagina](https://mran.revolutionanalytics.com/download/) en de [CRAN-opslagplaats](https://cran.r-project.org/bin/windows/base/). De huidige release van R-scripts in Power BI Desktop biedt ondersteuning voor Unicode-tekens en spaties (lege tekens) in het installatiepad.

## <a name="run-r-scripts"></a>R-scripts uitvoeren
In Power BI Desktop kunt in slechts enkele stappen R-scripts uitvoeren en een gegevensmodel maken. Hiermee kunt u rapporten maken en deze via de Power BI-service delen. R-scripts in Power BI Desktop bieden nu ondersteuning voor getalnotaties met decimalen (,) en punten (.).

### <a name="prepare-an-r-script"></a>R-scripts voorbereiden
Als u een R-script wilt uitvoeren in Power BI Desktop, maakt u het script in uw lokale omgeving voor R-ontwikkeling en controleert u of het foutloos wordt uitgevoerd.

Als u het script wilt uitvoeren in Power BI Desktop, dient u ervoor te zorgen dat het foutloos in een nieuwe en ongewijzigde werkruimte wordt uitgevoerd. Dat betekent dat alle pakketten en afhankelijkheden expliciet moeten worden geladen en uitgevoerd. U kunt *source()* gebruiken om afhankelijke scripts uit te voeren.

Als u een R-script in Power BI Desktop voorbereidt en uitvoert, gelden er enkele beperkingen:

* Er worden alleen gegevensframes geïmporteerd. Zorg er dus voor dat de gegevens die u in Power BI wilt importeren, in een gegevensframe worden weergegeven
* Kolommen van het type Complex of Vector worden niet geïmporteerd maar in de gemaakte tabel vervangen door foutwaarden
* In Power BI worden afwezige waarden vertaald naar NULL-waarden
* R-scripts waarvan het uitvoeren langer duurt dan dertig minuten, worden door een time-out afgebroken
* Bij interactieve aanroepen in het R-script, zoals het wachten op gebruikersinvoer, wordt het uitvoeren van het script onderbroken
* Als de werkmap in het R-script wordt ingesteld, *moet* u een volledig pad naar de werkmap definiëren in plaats van een relatief pad

### <a name="run-your-r-script-and-import-data"></a>R-script uitvoeren en gegevens importeren
1. In Power BI Desktop bevindt de R-scriptgegevensconnector zich in **Gegevens ophalen**. Als u het R-script wilt uitvoeren, selecteert u **Gegevens ophalen &gt; Meer...** en vervolgens **Overige &gt; R-script**, zoals in de volgende afbeelding is weergegeven:
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. Als R op de lokale computer is geïnstalleerd, wordt de meest recente installatie geselecteerd als de R-engine. Kopieer het script in het scriptvenster en selecteer **OK**.
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. Als R niet is geïnstalleerd, niet wordt herkend of als er meerdere installaties op de lokale computer aanwezig zijn, vouwt u **Installatie-instellingen voor R** uit om de installatieopties weer te geven of om te selecteren welke met installatie u het R-script wilt uitvoeren.
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   Als R is geïnstalleerd maar niet wordt herkend, kunt u de locatie expliciet in het tekstvak opgeven als u **Installatie-instellingen voor R** uitvouwt. In de bovenstaande afbeelding wordt het pad *C:\Program Files\R\R-3.2.0* expliciet in het tekstvak opgegeven.
   
   Installatie-instellingen voor R bevinden zich centraal in de sectie R-script van het dialoogvenster Opties. Als u de installatie-instellingen voor R wilt opgeven, selecteert u **Bestand > Opties en instellingen** en vervolgens **Opties > R-script**. Als er meerdere installaties van R beschikbaar zijn, verschijnt er een vervolgkeuzemenu waarin u de gewenste installatie kunt selecteren.
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. Selecteer **OK** om het R-Script uit te voeren. Wanneer het script wordt uitgevoerd, kunt u vervolgens de resulterende gegevensframes toevoegen aan het Power BI-model.

### <a name="refresh"></a>Vernieuwen
U kunt een R-script in Power BI Desktop vernieuwen. Als u een R-script vernieuwt, wordt het R-script opnieuw uitgevoerd in de Power BI Desktop-omgeving.

## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende aanvullende informatie over R in Power BI.

* [Create R Visuals in Power BI Desktop](desktop-r-visuals.md) (Visuele R-elementen maken in Power BI Desktop)
* [Use an external R IDE with Power BI](desktop-r-ide.md) (Een externe R IDE gebruiken in Power BI)

