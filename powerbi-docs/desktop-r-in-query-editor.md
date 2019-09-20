---
title: R gebruiken in Power Query-editor
description: R gebruiken in Query-editor van Power BI Desktop om geavanceerde analyses uit te voeren
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b64b4b736291ce1c3bde02010b7e583a0c3dc406
ms.sourcegitcommit: 226b47f64e6749061cd54bf8d4436f7deaed7691
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/09/2019
ms.locfileid: "70841508"
---
# <a name="use-r-in-query-editor"></a>R gebruiken in Query-editor

[**R**](https://mran.microsoft.com/documents/what-is-r) is een krachtige computertaal die veel statistici, gegevenswetenschappers en gegevensanalisten gebruiken. U kunt **R** in **Query-editor** van Power BI Desktop gebruiken om het volgende te doen:

* Gegevensmodellen voorbereiden

* Rapporten maken

* Gegevens opschonen, geavanceerde data shaping en gegevenssetanalyse, waaronder aanvulling van ontbrekende gegevens, voorspellingen, clustering en meer.  

## <a name="install-r"></a>R installeren

U kunt **R** gratis downloaden van de [Revolution Open-downloadpagina](https://mran.revolutionanalytics.com/download/) en de [CRAN-opslagplaats](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>mice installeren

De [**mice**-bibliotheek](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice) moet zijn geïnstalleerd in uw R-omgeving. Zonder **mice**werkt de code van het voorbeeldscript niet goed. Met het **mice**-pakket implementeert u een methode om met ontbrekende gegevens om te gaan.

**mice** installeren:

1. Start het programma R.exe (bijvoorbeeld C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. Voer de installatieopdracht uit:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>R gebruiken in Query-editor

We demonstreren het gebruik van **R** in **Query-editor** door een voorbeeldset met beursgegevens in een CSV-bestand te gebruiken en de volgende stappen te doorlopen:

1. [Download het bestand **EuStockMarkets_NA.csv**](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Vergeet niet waar u dit opslaat.

1. Laad het bestand in **Power BI Desktop**: selecteer op het lint **Start** de optie **Gegevens ophalen > Tekst/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Selecteer het bestand en selecteer vervolgens **Openen**. De CSV-gegevens worden weergegeven in het dialoogvenster **Tekst-/CSV-bestand**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. Wanneer de gegevens zijn geladen, worden deze weergegeven in het deelvenster **Velden**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. U opent **Query-editor** door op het lint **Start** de optie **Query's bewerken** te selecteren.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. Op het lint **Transformeren** selecteert u **R-script uitvoeren**. De editor **R-script uitvoeren** wordt weergegeven.  

   In de rijen 15 en 20 ontbreken gegevens, net als in andere rijen die u niet in de afbeelding kunt zien. In de stappen hieronder ziet u hoe deze rijen in R worden aangevuld.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. Vul voor dit voorbeeld de onderstaande scriptcode in. Zorg ervoor dat u &lt;Uw bestandspad&gt; vervangt door het pad naar **EuStockMarkets_NA.csv** in uw lokale bestandssysteem, bijvoorbeeld C:/Users/John Doe/Documents/micro soft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Mogelijk moet u een variabele met de naam *output* overschrijven om de nieuwe gegevensset met de toegepaste filters op de juiste manier te maken.

7. Wanneer u **OK** hebt geselecteerd, geeft **Query-editor** een waarschuwing over de privacy van gegevens weer.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. U moet alle gegevensbronnen op **openbaar** instellen om ervoor te zorgen dat de R-scripts goed werken in de Power BI-service. Zie [Privacyniveaus](desktop-privacy-levels.md) voor meer informatie over privacy-instellingen en de implicaties ervan.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   Nadat u **Opslaan**hebt geselecteerd, wordt het script uitgevoerd. U ziet een nieuwe kolom in het deelvenster **Velden** met de naam **completedValues**. Er ontbreken een aantal gegevenselementen, bijvoorbeeld in rijen 15 en 18. Bekijk in het volgende gedeelte hoe R hiermee omgaat.

   Met slechts vijf regels R-script kan **Query-editor** de ontbrekende waarden invullen met behulp van een voorspellend model.

## <a name="create-visuals-from-r-script-data"></a>Visuals maken van R-scriptgegevens

U kunt nu een visual maken om te zien hoe de R-scriptcode met behulp van de bibliotheek **mice** de ontbrekende waarden voltooit, zoals weergegeven in de volgende afbeelding:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

U kunt alle voltooide visuals in één PBIX-bestand van **Power BI Desktop** opslaan en het gegevensmodel en de bijbehorende R-scripts gebruiken in de Power BI-service.

> [!NOTE]
> U kunt [een PBIX-bestand downloaden](http://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix) wanneer al deze stappen zijn voltooid.

Zodra u het PBIX-bestand hebt geüpload naar de Power BI-service, moet u extra stappen uitvoeren om vernieuwing van de servicegegevens en bijgewerkte visuals in te schakelen:  

* **Geplande vernieuwing voor de gegevensset inschakelen**: als u geplande vernieuwing wilt inschakelen voor de werkmap die uw gegevensset met R-scripts bevat, bekijkt u [Geplande vernieuwing configureren](refresh-scheduled-refresh.md). Hierin vindt u ook informatie over de **Persoonlijke gateway**.

* **De persoonlijke gateway installeren**: er moet een **Persoonlijke gateway** zijn geïnstalleerd op de computer waarop het bestand en **R** zich bevinden. Die werkmap wordt geopend en alle bijgewerkte visuals worden weergegeven in de Power BI-service. Zie [Persoonlijke gateway installeren en configureren](service-gateway-personal-mode.md) voor meer informatie.

## <a name="limitations"></a>Beperkingen

Er gelden enkele beperkingen voor query's met R-scripts die zijn gemaakt in **Query-editor**:

* Alle R-gegevensbroninstellingen moeten zijn ingesteld op **Openbaar**. Alle andere stappen in de **Query-editor**-query moeten ook openbaar zijn. Om de gegevensbroninstellingen te openen, selecteert u in **Power BI Desktop** de optie **Bestand > Opties en instellingen > Instellingen voor gegevensbron**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  Selecteer in het dialoogvenster **Instellingen voor gegevensbron** de gegevensbron(nen) en vervolgens **Machtigingen bewerken...**.  Stel het **Privacyniveau** in op **Openbaar**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* Om geplande vernieuwing van uw R-visuals of gegevensset in te schakelen, moet **Geplande vernieuwing** zijn ingeschakeld en moet er een **Persoonlijke gateway** zijn geïnstalleerd op de computer waarop de werkmap en **R** zich bevinden. Zie het vorige gedeelte van dit artikel voor koppelingen naar meer informatie over beide vereisten.

U kunt verschillende handelingen uitvoeren met R en aangepaste query's, dus verken uw gegevens en deel ze in zoals u wilt.

## <a name="next-steps"></a>Volgende stappen

* [Inleiding tot R](https://mran.microsoft.com/documents/what-is-r) 

* [R-scripts uitvoeren in Power BI Desktop](desktop-r-scripts.md) 

* [Gebruik een externe R IDE met Power BI](desktop-r-ide.md) 

* [R-pakketten in de Power BI-service](service-r-packages-support.md)
