---
title: Python gebruiken in Query-editor van Power BI
description: Python gebruiken in Query-editor van Power BI Desktop om geavanceerde analyses uit te voeren
author: otarb
manager: rajatt
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: 28463c065c965b90beb32feabcd5de029311c612
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61286545"
---
# <a name="using-python-in-query-editor"></a>Python gebruiken in Query-editor van Power BI
U kunt **Python**, een programmeertaal die veel door statistici, gegevenswetenschappers en gegevensanalisten wordt toegepast, gebruiken in **Query-editor** van Power BI Desktop. Dankzij de integratie van Python in **Query-editor** kunt u met Python gegevens opschonen en geavanceerde data shaping en analyses in gegevenssets uitvoeren, met inbegrip van het aanvullen van ontbrekende gegevens, voorspellingen en clustering. **Python** is een krachtige programmeertaal en kan in **Query-editor** worden gebruikt om uw gegevensmodel voor te bereiden en rapporten te maken.

## <a name="installing-python"></a>Python installeren
Als u **Python** wilt gebruiken in **Query-editor** van Power BI Desktop, moet u **Python** op de lokale computer installeren. U kunt **Python** gratis downloaden en installeren vanaf tal van locaties, waaronder de [officiële Python-downloadpagina](https://www.python.org/) en de [Anaconda](https://anaconda.org/anaconda/python/).

## <a name="using-python-in-query-editor"></a>Python gebruiken in Query-editor van Power BI
Bekijk aan de hand van dit voorbeeld hoe u **Python** in **Query-editor** kunt gebruiken voor een beursgegevensset, die is gebaseerd op een .CSV-bestand dat u [hier kunt downloaden](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv) en volgen. Hieronder volgen de stappen voor dit voorbeeld:

1. Laad eerst uw gegevens in **Power BI Desktop**. Laad in dit voorbeeld het bestand *EuStockMarkets_NA.csv* en selecteer **Gegevens ophalen > CSV** in het lint **Start** in **Power BI Desktop**.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-1.png)
2. Selecteer het bestand en selecteer **Openen**. De CSV wordt nu weergegeven in het dialoogvenster **CSV-bestand**.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-2.png)
3. Wanneer de gegevens zijn geladen, worden deze weergegeven in het deelvenster **Velden** in Power BI Desktop.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-3.png)
4. Open **Query-editor** door in het lint **Start** van **Power BI Desktop** **Query's bewerken** te selecteren.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-4.png)
5. Selecteer op het tabblad **Transformeren** de optie **Python-Script uitvoeren**. De editor **Python-script uitvoeren** wordt geopend (weergegeven in de volgende stap). U ziet dat er in de rijen 15 en 20 gegevens ontbreken, net als in andere rijen die niet in de volgende afbeelding te zien zijn. De stappen hieronder laten zien hoe Python die rijen voor u kan invullen.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-5.png)
6. Vul in dit voorbeeld de volgende scriptcode in:
   
    ```python
       import pandas as pd
       completedData = dataset.fillna(method='backfill', inplace=False)
       dataset["completedValues"] =  completedData["SMI missing values"]
   ```

   > [!NOTE]
   > Deze scriptcode werkt alleen goed als de bibliotheek *pandas* in uw Python-omgeving is geïnstalleerd. Als u pandas wilt installeren, voert u de volgende opdracht uit in uw Python-installatie: |      > install.packages('pandas')
   > 
   > 
   
   De code ziet er als volgt uit wanneer deze in het dialoogvenster **Python-script uitvoeren** wordt ingevoerd:
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-5b.png)
7. Wanneer u **OK** hebt geselecteerd, geeft **Query-editor** een waarschuwing over de privacy van gegevens weer.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-6.png)
8. Python-scripts werken alleen goed in de Power BI-service als alle gegevensbronnen op *openbaar* zijn ingesteld. Zie [Privacyniveaus](desktop-privacy-levels.md) voor meer informatie over privacy-instellingen en de implicaties ervan.
   
   ![](media/desktop-python-in-query-editor/python-in-query-editor-7.png)
   
   U ziet een nieuwe kolom in het deelvenster **Velden** met de naam *completedValues*. Er ontbreken een aantal gegevenselementen, bijvoorbeeld in rijen 15 en 18. Bekijk in het volgende gedeelte hoe Python hiermee omgaat.
   

Met slechts vijf regels Python-script kan **Query-editor** de ontbrekende waarden invullen met behulp van een voorspellend model.

## <a name="creating-visuals-from-python-script-data"></a>Visuals maken vanuit Python-scriptgegevens
U kunt nu een visual maken om te zien hoe de Python-scriptcode met behulp van de bibliotheek *pandas* de ontbrekende waarden voltooit, zoals weergegeven in de volgende afbeelding:

![](media/desktop-python-in-query-editor/python-in-query-editor-8.png)

Zodra deze visual en eventuele andere visuals die u met behulp van **Power BI Desktop** wilt maken zijn voltooid, kunt u het **Power BI Desktop**-bestand opslaan (als een .pbix-bestand) en vervolgens het gegevensmodel, met inbegrip van bijbehorende Python-scripts, in de Power BI-service gebruiken.

> [!NOTE]
> Wilt u een voltooid .pbix-bestand bekijken dat via deze stappen is gemaakt? Dat kan: u kunt het voltooide **Power BI Desktop**-bestand dat in deze voorbeelden wordt gebruikt [hier](http://download.microsoft.com/download/A/B/C/ABCF5589-B88F-49D4-ADEB-4A623589FC09/Complete%20Values%20with%20Python%20in%20PQ.pbix) downloaden.

Zodra u het .pbix-bestand in de Power BI-service hebt geüpload, zijn er nog een aantal stappen nodig om gegevensvernieuwing (in de service) mogelijk te maken en om ervoor te zorgen dat visuals in de service kunnen worden bijgewerkt (visuals worden alleen bijgewerkt als de gegevens toegang tot Python hebben). De extra stappen zijn de volgende:

* **Geplande vernieuwing voor de gegevensset inschakelen**: als u geplande vernieuwing wilt inschakelen voor de werkmap die uw gegevensset met Python-scripts bevat, bekijkt u [Configuring scheduled refresh](refresh-scheduled-refresh.md) (Geplande vernieuwing configureren). Hierin vindt u ook informatie over **Persoonlijke gateway**.
* **De persoonlijke gateway installeren**: er moet een **persoonlijke gateway** zijn geïnstalleerd op de computer waarop het bestand zich bevindt en waarop Python is geïnstalleerd. De Power BI-service heeft toegang tot die werkmap nodig om bijgewerkte visuals opnieuw te genereren. U kunt meer informatie krijgen over het [installeren en configureren van Personal Gateway](personal-gateway.md).

## <a name="limitations"></a>Beperkingen
Er gelden enkele beperkingen voor query's met Python-scripts die zijn gemaakt in **Query-editor**:

* Alle Python-gegevensbroninstellingen moeten op *Openbaar* zijn ingesteld, en alle overige stappen in een query gemaakt in **Query-editor** moeten ook openbaar zijn. Om de gegevensbroninstellingen te openen, selecteert u in **Power BI Desktop** **Bestand > Opties en instellingen > Instellingen voor gegevensbron**.
  
  ![](media/desktop-python-in-query-editor/python-in-query-editor-9.png)
  
  In het dialoogvenster **Instellingen voor gegevensbron** selecteert u de gegevensbron(nen) en vervolgens **Machtigingen bewerken...** . Controleer of **Privacyniveau** is ingesteld op *Openbaar*.
  
  ![](media/desktop-python-in-query-editor/python-in-query-editor-10.png)    
* Om geplande vernieuwing van uw Python-visuals of gegevensset in te schakelen, moet **Geplande vernieuwing** zijn ingeschakeld en moet er een **persoonlijke gateway** zijn geïnstalleerd op de computer waarop de werkmap en de Python-installatie staan. Zie het vorige gedeelte van dit artikel voor koppelingen naar meer informatie over beide vereisten.
* Geneste tabellen (tabel van tabellen) worden momenteel niet ondersteund 

U kunt verschillende handelingen uitvoeren met Python en aangepaste query's, dus verken uw gegevens en deel ze in zoals u wilt.

