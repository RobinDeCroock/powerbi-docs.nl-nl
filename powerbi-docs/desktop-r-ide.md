---
title: Een externe R IDE met Power BI gebruiken
description: U kunt een externe IDE starten en gebruiken met Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: ef64c802e2f231ce2632f4ed0a442a2a7bac3328
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514697"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Een externe R IDE met Power BI gebruiken
Met **Power BI Desktop** kunt u uw externe R IDE (Integrated Development Environment) gebruiken om R-scripts te maken en verfijnen, en deze scripts vervolgens gebruiken in Power BI.

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>Een externe R IDE inschakelen
Voorheen moest u de R-scripteditor in **Power BI Desktop** gebruiken om R-scripts te maken en uit te voeren. Met deze release kunt u uw externe R IDE starten vanuit **Power BI Desktop** en uw gegevens automatisch laten importeren en weergeven in de R IDE. Van daaruit kunt u het script in die externe R IDE wijzigen en het script vervolgens weer in **Power BI Desktop** plakken om visuals en rapporten voor Power BI te maken.

Sinds de release van september 2016 van **Power BI Desktop** (versie 2.39.4526.362) kunt u aangeven welke R IDE u wilt gebruiken en deze automatisch laten starten vanuit **Power BI Desktop**.

### <a name="requirements"></a>Vereisten
Als u deze functie wilt gebruiken, moet u een **R IDE** op uw lokale computer installeren. **Power BI Desktop** zorgt niet voor het opnemen, implementeren of installeren van de R-engine. Daarom moet u **R** afzonderlijk installeren op uw lokale computer. U kunt kiezen welke R IDE u wilt gebruiken, met de volgende opties:

* U kunt uw favoriete R IDE installeren. Veel daarvan zijn gratis verkrijgbaar, zoals de [Revolution Open-downloadpagina](https://mran.revolutionanalytics.com/download/) en de [CRAN-opslagplaats](https://cran.r-project.org/bin/windows/base/).
* **Power BI Desktop** biedt ook ondersteuning voor [R Studio](https://www.rstudio.com/) en **Visual Studio 2015** met [ *R-Tools voor Visual Studio*](https://beta.visualstudio.com/vs/rtvs/)-editors.
* U kunt ook een andere R IDE installeren en **Power BI Desktop** die **R IDE** op een van de volgende manieren laten starten:
  
  * U kunt **.R**-bestanden koppelen aan de externe IDE die **Power BI Desktop** moet starten.
  * U kunt opgeven welke .exe **Power BI Desktop** moet starten door *Overige* te selecteren in de sectie **Opties voor R-script** in het dialoogvenster **Opties**. U kunt het dialoogvenster **Opties** openen met **Bestand > Opties en instellingen > Opties**.
    
    ![](media/desktop-r-ide/r-ide_1b.png)

Als u meerdere R IDE’s hebt geïnstalleerd, kunt u opgeven welke daarvan wordt gestart door de gewenste R IDE selecteren in de vervolgkeuzelijst *Gedetecteerde R IDE's* in het dialoogvenster **Opties**.

De standaardinstelling is dat **Power BI Desktop** **R Studio** start als externe R IDE als deze op uw lokale computer is geïnstalleerd. Als **R Studio** niet is geïnstalleerd en u **Visual Studio 2015** met **R Tools voor Visual Studio** hebt, wordt dit hulpprogramma gestart. Als geen van deze R IDE’s is geïnstalleerd, wordt de toepassing gestart die gekoppeld is aan **.R**-bestanden.

En als er geen **.R**-bestandskoppeling bestaat, kunt u ook een pad opgeven naar een aangepaste IDE in de sectie *Blader naar de R IDE van uw voorkeur* van het dialoogvenster **Opties**. U kunt ook een andere R IDE starten door in **Power BI Desktop** het tandwielpictogram **Instellingen** naast de pijl **R IDE starten** te selecteren.

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>Een R IDE starten vanuit Power BI Desktop
U kunt als volgt een R IDE starten vanuit **Power BI Desktop**:

1. Laad gegevens in **Power BI Desktop**.
2. Selecteer in het deelvenster **Velden** enkele velden waarmee u wilt werken. Als u nog geen scriptelementen hebt ingeschakeld, wordt u gevraagd dat alsnog te doen.
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. Wanneer scriptelementen zijn ingeschakeld, kunt u een R-visual selecteren in het deelvenster **Visualisaties**, waarmee een lege R-visual wordt gemaakt die geschikt is om de resultaten van uw script weer te geven. Ook het deelvenster **R-scripteditor** wordt weergegeven.
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. U kunt nu de velden selecteren die u in uw R-script wilt gebruiken. Wanneer u een veld selecteert, maakt het veld **R-scripteditor** automatisch een scriptcode op basis van het veld of de velden die u selecteert. U kunt het R-script rechtstreeks in het deelvenster **R-scripteditor** maken (of plakken) of het deelvenster leeg laten.
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > Het standaardtype voor aggregatie voor R-visuals is *niet samenvatten*.
   > 
   > 
5. U kunt nu uw R IDE rechtstreeks vanuit **Power BI Desktop** starten. Selecteer de knop **R IDE starten** rechts van de titelbalk van **R-scripteditor**, zoals hieronder wordt weergegeven.
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. De opgegeven R IDE wordt gestart door Power BI Desktop, zoals wordt weergegeven in de volgende afbeelding (in deze afbeelding is **RStudio** de standaard R IDE).
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > **Power BI Desktop** voegt de eerste drie regels van het script toe zodat uw gegevens kunnen worden geïmporteerd uit **Power BI Desktop** zodra u het script uitvoert.
   > 
   > 
7. Een script dat u hebt gemaakt in het **R-scripteditor-venster** van **Power BI Desktop** wordt gestart op regel 4 in uw R IDE. Op dat punt kunt u uw R-script in de R IDE maken. Nadat uw R-script is voltooid in de R IDE, moet u het script terug kopiëren naar het deelvenster **R-scripteditor** van **Power BI Desktop**, *met uitzondering van* de eerste drie regels van het script dat **Power BI Desktop** automatisch heeft gegenereerd. Kopieer niet de eerste drie regels van het script terug naar **Power BI Desktop**. Deze regels zijn alleen gebruikt voor het importeren van uw gegevens naar uw R IDE vanuit **Power BI Desktop**.

### <a name="known-limitations"></a>Bekende beperkingen
Het starten van een R IDE rechtstreeks vanuit Power BI Desktop heeft enkele beperkingen:

* Automatisch exporteren van het script vanuit uw R IDE naar **Power BI Desktop** wordt niet ondersteund.
* De **R Client**-editor (RGui.exe) wordt niet ondersteund omdat de editor zelf geen ondersteuning biedt voor het openen van bestanden.

## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende aanvullende informatie over R in Power BI.

* [R-scripts uitvoeren in Power BI Desktop](desktop-r-scripts.md)
* [Power BI-visuals maken met R](desktop-r-visuals.md)

