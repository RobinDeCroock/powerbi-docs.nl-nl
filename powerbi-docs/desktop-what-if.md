---
title: What if-parameters gebruiken om variabelen te visualiseren
description: Uw eigen what-if-variabele maken om variabelen in Power BI-rapporten voor te stellen en te visualiseren
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 8a72bc43bcceae6e676728934ceec81c8cb27d04
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "76539378"
---
# <a name="create-and-use-what-if-parameters-to-visualize-variables-in-power-bi-desktop"></a>What if-parameters maken en gebruiken om variabelen in Power BI Desktop te visualiseren

Vanaf de release van augustus 2018 van *Power BI Desktop* kunt u *what-if*-variabelen voor uw rapporten maken, communiceren met de variabele als een slicer en verschillende sleutelwaarden in uw rapporten visualiseren en kwantificeren.

![De optie Nieuwe parameter](media/desktop-what-if/what-if_01.png)

Maak een *what-if*-parameter op het tabblad **Model maken** in Power BI Desktop. Wanneer u deze selecteert, wordt een dialoogvenster weergegeven waarin u de parameter kunt configureren.

## <a name="creating-a-what-if-parameter"></a>Een what-if-parameter maken

Als u een what-if-parameter wilt maken, selecteert u **Nieuwe parameter** op het tabblad **Model maken** van Power BI Desktop. In de volgende afbeelding hebben we een parameter met de naam *Discount percentage* gemaakt en is het gegevenstype ingesteld op **Decimaal getal**. De **minimumwaarde** is nul. Het **maximum** is 0,50 (50 procent). Bovendien hebben we de **Verhoging** ingesteld op 0,05, ofwel vijf procent. Dat is hoeveel de parameter wordt aangepast bij interactie met een rapport.

![What-if-parameterwaarden](media/desktop-what-if/what-if_02.png)

> [!NOTE]
> Zorg er bij decimale getallen voor dat u de waarde vooraf laat gaan door een nul, zoals 0,50, en dus niet ,50. Anders wordt het getal niet gevalideerd en kan de knop **OK** niet worden geselecteerd.
> 
> 

Om het u gemakkelijk te maken, wordt door het selectievakje **Slicer toevoegen aan deze pagina** automatisch een slicer bij uw what-if-parameter op de huidige rapportpagina geplaatst.

![Nieuwe slicer op de huidige rapportpagina](media/desktop-what-if/what-if_03.png)

Door een what-if-parameter te maken wordt ook een meting gemaakt, waarmee u de huidige waarde van de what-if-parameter kunt visualiseren.

![Meting gemaakt voor what-if-parameter](media/desktop-what-if/what-if_04.png)

Het is belangrijk en handig te weten dat wanneer u een what-if-parameter maakt, zowel de parameter als de meting deel van het model worden. Ze zijn beschikbaar in het hele rapport en kunnen derhalve op andere rapportpagina's worden gebruikt. En omdat ze deel uitmaken van het model, kunt u de slicer verwijderen van de rapportpagina. Als u de slicer terug wilt hebben, sleept u de what-if-parameter van de lijst **Velden** naar het canvas. Vervolgens wijzigt u de visual in een slicer.

## <a name="using-a-what-if-parameter"></a>Een what-if-parameter gebruiken

Laten we een eenvoudig voorbeeld van het gebruik van een what-if-parameter maken. In de vorige sectie hebben we de what-if-parameter gemaakt. Nu gaan we deze parameter gebruiken door een nieuwe meting te maken waarvan de waarde wordt aangepast met de schuifregelaar.

![Een nieuwe meting toevoegen voor gebruik met de parameter](media/desktop-what-if/what-if_05.png)

De nieuwe meting bestaat alleen maar uit de totale omzet, waarvoor het kortingstarief wordt toegepast. U kunt ook complexe en interessante metingen maken waarmee de gebruikers van uw rapporten de variabele van uw what-if-parameter kunnen visualiseren. U kunt bijvoorbeeld een rapport maken waarmee verkoopmedewerkers hun bonus kunnen bekijken als ze voldoen aan bepaalde verkoopdoelstellingen of -percentages, of het effect kunnen zien van gestegen verkoop en hogere kortingen.

Voer de formule van de meting in de formulebalk in en geef deze de naam *Sales after Discount*.

![Definities van Sales after Discount](media/desktop-what-if/what-if_06.png)

Vervolgens maken we een kolomvisual met **OrderDate** op de as en zowel **SalesAmount** als de zojuist gemaakte meting **Sales after Discount** als waarden.

![Visualisatie voor SalesAmount](media/desktop-what-if/what-if_07.png)

Als de slicer wordt verschoven, kunt u zien dat de kolom **Sales after Discount** de gereduceerde verkoopcijfers weerspiegelt.

![De slider werkt met de visualisatie](media/desktop-what-if/what-if_08.png)

Zo eenvoudig werkt dat. U kunt what-if-parameters gebruiken in allerlei situaties. Met deze parameters kunnen gebruikers van rapporten werken met verschillende scenario's die u in uw rapporten maakt.
