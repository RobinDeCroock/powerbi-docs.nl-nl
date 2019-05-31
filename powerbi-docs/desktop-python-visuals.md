---
title: Power BI-visuals maken met Python
description: Power BI-visuals maken met Python
author: otarb
manager: rajatt
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Create reports
ms.openlocfilehash: 7390f029144e5cb37830921071ad5c2c678b2d4d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61285582"
---
# <a name="create-power-bi-visuals-using-python"></a>Power BI-visuals maken met Python
In combinatie met **Power BI Desktop** kunt u **Python** gebruiken om uw gegevens te visualiseren.

## <a name="install-python"></a>Python installeren
**Power BI Desktop** bevat, implementeert of installeert niet de **Python**-engine. Als u Python-scripts wilt uitvoeren in **Power BI Desktop**, moet u **Python** afzonderlijk installeren op uw lokale computer. U kunt **Python** gratis downloaden en installeren vanaf tal van locaties, waaronder de [officiële Python-downloadpagina](https://www.python.org/) en de [Anaconda](https://anaconda.org/anaconda/python/). De huidige release van Python-scripts in Power BI Desktop biedt ondersteuning voor Unicode-tekens en spaties (lege tekens) in het installatiepad.

## <a name="enable-python-visuals"></a>Python-visuals inschakelen
Als u Python-visuals wilt inschakelen, selecteert u **Bestand > Opties en instellingen > Opties** en controleert u op de pagina **Opties** of uw lokale Python-installatie is opgegeven in de sectie **Python-script** van het venster **Opties**, zoals weergegeven in de volgende afbeelding. In de volgende afbeelding is **C:\Python27** het lokale installatiepad van Python, dat expliciet is opgegeven in het tekstvak. Zorg ervoor dat het weergegeven pad op de juiste manier verwijst naar de lokale Python-installatie die u **Power BI Desktop** wilt laten gebruiken.
   
   ![](media/desktop-python-visuals/python-visuals-1.png)

Nadat u uw Python-installatie hebt opgegeven, bent u klaar om Python-visuals te gaan maken.

## <a name="create-python-visuals-in-power-bi-desktop"></a>Python-visuals maken in Power BI Desktop
1. Selecteer het pictogram **Python-visual** in het deelvenster **Visualisatie**, zoals weergegeven in de volgende afbeelding, om een Python-visual toe te voegen.
   
   ![](media/desktop-python-visuals/python-visuals-2.png)

   Wanneer u een Python-visual aan een rapport toevoegt, doet **Power BI Desktop** het volgende:
   
   - Een tijdelijke aanduiding voor een Python-visual wordt weergegeven op het rapportcanvas.
   
   - De **Python-scripteditor** wordt onderin het middelste deelvenster weergegeven.
   
   ![](media/desktop-python-visuals/python-visuals-3.png)

2. Vervolgens voegt u velden toe die u in uw Python-script wilt gebruiken. Dat doet u in de sectie **Waarden** onder **Velden**, net zoals bij andere visuele elementen van **Power BI Desktop**. 
    
    Alleen velden die zijn toegevoegd aan de verdieping **Velden**, zijn beschikbaar voor uw Python-script. U kunt ook nieuwe velden toevoegen aan of onnodige velden verwijderen uit de verdieping **Velden** terwijl u aan uw Python-script werkt in de **Python-scripteditor van Power BI Desktop**. **Power BI Desktop** detecteert automatisch welke velden u hebt toegevoegd of verwijderd.
   
   > [!NOTE]
   > Het standaardtype voor aggregatie voor Python-visuals is *niet samenvatten*.
   > 
   > 
   
3. U kunt nu de gegevens gebruiken die u hebt geselecteerd voor het maken van een diagram. 

    Terwijl u velden selecteert, genereert de **Python-scripteditor** ondersteunende bindingcode voor Python-scripts op basis van uw selecties in de grijze sectie aan de bovenkant van het editorvenster. Tijdens het selecteren of verwijderen van extra velden wordt ondersteunende code in de Python-scripteditor automatisch gegenereerd of verwijderd, naar gelang van toepassing.
   
   In het voorbeeld in de volgende afbeelding zijn drie velden geselecteerd: hp, gear en drat. Op basis van deze selectie heeft de Python-scripteditor de volgende bindingcode gegenereerd:
   
   * Er is een gegevensframe met de naam **gegevensset** gemaakt
     * Dat gegevensframe bestaat uit de verschillende velden die door de gebruiker zijn geselecteerd
   * Het standaard aggregatietype is *Niet samenvatten*
   * Net als bij visuele tabel-elementen worden velden gegroepeerd en komen dubbele rijen slechts eenmaal voor
   
   ![](media/desktop-python-visuals/python-visuals-4.png)
   
   > [!TIP]
   > In bepaalde gevallen wilt u geen automatische groepering of wilt u dat alle rijen worden weergegeven, met inbegrip van duplicaten. In dat geval kunt u aan uw gegevensset een indexveld toevoegen dat ervoor zorgt dat alle rijen als uniek worden beschouwd en groepering wordt voorkomen.
   > 
   > 
   
   Het gegenereerde gegevensframe wordt een **gegevensset** genoemd en de geselecteerde kolommen zijn toegankelijk op basis van hun respectieve namen. Het veld gear bijvoorbeeld is toegankelijk door *dataset[”gear”]* in uw Python-script te schrijven.

4. Met behulp van het gegevensframe dat automatisch wordt gegenereerd door de velden die u hebt geselecteerd, kunt u een Python-script schrijven dat resulteert in plotten naar het standaard-Python-apparaat. Wanneer het script voltooid is, selecteert u **Uitvoeren** in de titelbalk van **Python-scripteditor** (**Uitvoeren** bevindt zich rechts op de titelbalk).
   
    Wanneer u **Uitvoeren** selecteert, identificeert **Power BI Desktop** de plot en wordt deze op het canvas weergegeven. Omdat het proces wordt uitgevoerd op uw lokale Python-installatie, moet u ervoor zorgen dat de vereiste pakketten zijn geïnstalleerd.
   
   **Power BI Desktop** plot het visuele element opnieuw wanneer een van de volgende gebeurtenissen optreedt:
   
   * Wanneer u **Uitvoeren** selecteert in de titelbalk van **Python-scripteditor**
   * Wanneer een gegevenswijziging plaatsvindt, als gevolg van het vernieuwen, filteren of markeren van gegevens

    In de volgende afbeelding ziet u een voorbeeld van de plotcode van de correlatie en wordt de correlatie tussen kenmerken van verschillende typen auto's weergegeven.

    ![](media/desktop-python-visuals/python-visuals-5.png)

5. Als u een grotere weergave van de visualisaties wilt, minimaliseert u de **Python-scripteditor**. En net zoals andere visuals in **Power BI Desktop** kunt u de correlatieplot kruislings filteren door alleen sportauto's in de ringgrafiek (de ronde visual aan de rechterkant, zoals weergegeven in het bovenstaande voorbeeld) te selecteren.

    ![](media/desktop-python-visuals/python-visuals-6.png)

6. U kunt het Python-script ook wijzigen om het visuele element aan te passen en Python in te zetten door parameters toe te voegen aan de plotting-opdracht.

    Dit was de oorspronkelijke plotting-opdracht:

    plt.matshow(dataset.corr('pearson'))

    Na enkele wijzigingen in het Python-script ziet de opdracht er nu zo uit:

    plt.matshow(dataset.corr('kendall'))

    Als gevolg plot de Python-visual nu met gebruik van de Kendall tau-correlatiecoëfficiënt, zoals wordt weergegeven in de volgende afbeelding.

    ![](media/desktop-python-visuals/python-visuals-7.png)

    Wanneer bij het uitvoeren van een Python-script een fout optreedt, wordt de Python-visual niet geplot en wordt er een foutbericht op het canvas weergegeven. Als u meer wilt weten over de fout, selecteert u **Details bekijken** in de fout op het canvas van de Python-visual.

    ![](media/desktop-python-visuals/python-visuals-8.png)

    > **Beveiliging van Python-scripts:** Python-visuals worden gemaakt op basis van Python-scripts, die code kunnen bevatten met beveiligings- of privacyrisico's. Wanneer een gebruiker voor het eerst een Python-visual probeert weer te geven of ermee probeert te werken, wordt er een beveiligingswaarschuwing weergegeven. Schakel Python-visuals alleen in als u de auteur en bron vertrouwt, of nadat u het Python-script hebt bekeken en begrijpt.
    > 
    > 

## <a name="known-limitations"></a>Bekende beperkingen
Python-visuals in **Power BI Desktop** kennen enkele beperkingen:

* Beperkingen voor gegevensgrootte: de grootte van gegevens die door de Python-visual worden gebruikt voor het uitzetten, is beperkt tot 150.000 rijen. Als er meer dan 150.000 rijen zijn geselecteerd, worden alleen de bovenste 150.000 rijen gebruikt en wordt er een bericht weergegeven op de afbeelding.
* Tijdslimiet voor berekening: als de berekening van een Python-visual langer duurt dan vijf minuten, treedt er een time-out op, met een fout tot gevolg.
* Relaties: net als bij andere Power BI Desktop-visuals geldt dat als er gegevensvelden uit verschillende tabellen zonder gedefinieerde relatie worden geselecteerd, er een fout optreedt.
* Python-visuals worden vernieuwd op het moment dat gegevens worden bijgewerkt, gefilterd en gemarkeerd. De afbeelding zelf is echter niet interactief en kan niet de bron van kruislings filteren zijn.
* Python-visuals reageren op de markering van andere visuele elementen, maar u kunt niet klikken op elementen in de Python-visual om kruislings te filteren op andere elementen.
* Alleen plots die worden weergegeven op het standaard-Python-apparaat voor weergave worden correct weergegeven op het canvas. Vermijd expliciet het gebruik van een ander Python-apparaat voor weergave.

## <a name="next-steps"></a>Volgende stappen
Raadpleeg de volgende aanvullende informatie over Python in Power BI.

* [Python-scripts uitvoeren in Power BI Desktop](desktop-python-scripts.md)
* [Een externe Python IDE met Power BI gebruiken](desktop-python-ide.md)

