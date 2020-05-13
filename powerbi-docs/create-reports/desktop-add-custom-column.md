---
title: Aangepaste kolommen toevoegen in Power BI Desktop
description: Snel een aangepaste kolom maken in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 443053bc973005d3e2a655b1222d049a4251e7d7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83329066"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Aangepaste kolommen toevoegen in Power BI Desktop

In Power BI Desktop kunt u eenvoudig een nieuwe aangepaste kolom met gegevens aan uw model toevoegen door Queryeditor te gebruiken. Met Queryeditor maakt u de aangepaste kolom en wijzigt u de naam van deze kolom voor het maken van [PowerQuery M-formulequery's](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language) om uw aangepaste kolom te definiëren. PowerQuery M-formulequery's beschikken over een [uitgebreide naslag met functiebeschrijvingen](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference). 

Wanneer u een aangepaste kolom maakt in Queryeditor, wordt deze door Power BI Desktop toegevoegd als een **toegepaste stap** in de **queryinstellingen** van de query. Deze kan op elk gewenst moment worden gewijzigd, verplaatst of aangepast.

![De pagina Aangepaste kolom toevoegen](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Queryeditor gebruiken om een aangepaste kolom toe te voegen

Als u een aangepaste kolom wilt gaan maken, voert u de onderstaande stappen uit:

1. Start Power BI Desktop en laad wat gegevens.

2. Selecteer op het tabblad **Start** op het lint de optie **Query's bewerken** en selecteer vervolgens **Query's bewerken** in het menu.

   ![Query's bewerken selecteren](media/desktop-add-custom-column/add-column-from-example_02.png)

   Het venster **Queryeditor** wordt weergegeven. 

2. Selecteer op het tabblad **Kolom toevoegen** op het lint de optie **Aangepaste kolom**.

   ![Aangepaste kolom selecteren](media/desktop-add-custom-column/add-custom-column_02.png)

   Het venster **Aangepaste kolom toevoegen** wordt weergegeven.

## <a name="the-add-custom-column-window"></a>Het venster Aangepaste kolom toevoegen

Het venster **Aangepaste kolom toevoegen** bevat de volgende items: 
- Een lijst met beschikbare kolommen in de lijst **Beschikbare kolommen** aan de rechterkant.

- De oorspronkelijke naam van de aangepaste kolom in het vak **Nieuwe kolomnaam**. U kunt de naam van deze kolom wijzigen.

- [PowerQuery M-formulequery's](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) in het vak **Formule voor aangepaste kolom**. U maakt deze query's door de formule samen te stellen waarmee uw nieuwe aangepaste kolom is gedefinieerd. 

   ![De pagina Aangepaste kolom toevoegen](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Formules maken voor de aangepaste kolom

1. Selecteer een kolom in de lijst **Beschikbare kolommen** aan de rechterkant en selecteer vervolgens onder de lijst de optie **Invoegen** om de kolom toe te voegen aan de formule voor de aangepaste kolom. U kunt ook een kolom toevoegen door hierop in de lijst dubbel te klikken.

2. Let bij het invoeren van de formule en het maken van de kolom op de indicator onderaan het venster **Aangepaste kolom toevoegen**. 

   Als er geen fouten zijn, worden een groen vinkje en het bericht *Er zijn geen syntaxisfouten gedetecteerd* weergegeven.

   ![Controle zonder syntaxisfouten op de pagina Aangepaste kolom toevoegen](media/desktop-add-custom-column/add-custom-column_04.png)

   Als er een syntaxisfout is gedetecteerd, wordt er een geel waarschuwingspictogram weergegeven, samen met een koppeling naar de locatie waar de fout in de formule is opgetreden.

   ![Fout op de pagina Aangepaste kolom toevoegen](media/desktop-add-custom-column/add-custom-column_05.png)

3. Selecteer **OK**. 

   Power BI Desktop voegt uw aangepaste kolom toe aan het model en voegt de stap **Aangepaste kolom toegevoegd** toe aan de lijst **Toegepaste stappen** in **Queryinstellingen**.

   ![Aangepaste kolom toegevoegd aan Queryinstellingen](media/desktop-add-custom-column/add-custom-column_06.png)

4. Als u de aangepaste kolom wilt wijzigen, dubbelklikt u op de stap **Aangepaste kolom toegevoegd** in de lijst **Toegepaste stappen**. 

   Het venster **Aangepaste kolom toevoegen** wordt weergegeven met de formule voor de aangepaste kolom die u hebt gemaakt.

## <a name="use-the-advanced-editor-for-custom-columns"></a>De geavanceerde editor voor aangepaste kolommen gebruiken

Nadat u de query hebt gemaakt, kunt u met de **geavanceerde editor** ook een stap van uw query wijzigen. Volg hiervoor de onderstaande stappen:

1. Selecteer in het venster **Queryeditor** het tabblad **Weergeven** op het lint. 

2. Selecteer **Geavanceerde editor**.

   De pagina **Geavanceerde editor** wordt weergegeven die u volledig beheer over uw query biedt. 

   ![De pagina Geavanceerde editor](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>Volgende stappen

- U kunt een aangepaste kolom op andere manieren maken, bijvoorbeeld door een kolom te maken op basis van voorbeelden die u aan Queryeditor opgeeft. Zie [Een kolom uit een voorbeeld toevoegen in Power BI Desktop](desktop-add-column-from-example.md) voor meer informatie.

- Zie [Power Query M function reference](/powerquery-m/power-query-m-function-reference) (Naslag met beschrijvingen van Power Query M-functies) voor naslaginformatie over Power Query M.

