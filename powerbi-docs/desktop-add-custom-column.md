---
title: Aangepaste kolommen toevoegen in Power BI Desktop
description: Snel een aangepaste kolom maken in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e2412fe72d62549277001b64121ecf9db2ea5502
ms.sourcegitcommit: b11e908650379913d00673215e3eaf25d712b122
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65239543"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Aangepaste kolommen toevoegen in Power BI Desktop
Met **Query-editor** in **Power BI Desktop** kunt u eenvoudig een nieuwe, aangepaste kolom met gegevens aan uw model toevoegen. De aangepaste kolom kan worden gemaakt en de naam ervan gewijzigd met behulp van handige knoppen om [M-formules](https://msdn.microsoft.com/library/mt270235.aspx) te maken waarmee de aangepaste kolom wordt gedefinieerd. De M-formule bevat een [uitgebreide naslag met functiebeschrijvingen](https://msdn.microsoft.com/library/mt779182.aspx) (Engelstalig). 

![](media/desktop-add-custom-column/add-custom-column_01.png)

Het maken van een aangepaste kolom is nog een **toegepaste stap** voor de query die u in **Query-editor** maakt. Dit houdt in dat de query op elk moment kan worden gewijzigd of eerder of later verplaatst.

## <a name="use-query-editor-to-add-a-new-custom-column"></a>Query-editor gebruiken om een nieuwe, aangepaste kolom toe te voegen
Start **Query-editor** als u een nieuwe, aangepaste kolom wilt maken. U kunt dit doen door **Query's bewerken** te selecteren in het lint **Start** van **Power BI Desktop**.

![](media/desktop-add-custom-column/add-column-from-example_02.png)

Als **Query-editor** is gestart en er al gegevens zijn geladen, kunt u een aangepaste kolom toevoegen door op het lint het tabblad **Kolom toevoegen** te selecteren en vervolgens de optie **Aangepaste kolom**.

![](media/desktop-add-custom-column/add-custom-column_02.png)

Het venster **Aangepaste kolom toevoegen** verschijnt. Dit wordt in de volgende sectie omschreven.

## <a name="the-add-custom-column-window"></a>Het venster Aangepaste kolom toevoegen
In het venster **Aangepaste kolom toevoegen** ziet u in het deelvenster aan de rechterkant de lijst met de beschikbare velden; bovenaan ziet u de naam van de aangepaste kolom (deze kunt u een andere naam geven door een naam in het tekstvak te typen). U ziet ook de [**M**-formule](https://msdn.microsoft.com/library/mt779182.aspx), die u maakt (of schrijft) op basis van het invoegen van velden vanaf de rechterkant, het toevoegen van operatoren en overige zaken voor het bouwen van de formule waarop de nieuwe, aangepaste kolom wordt gedefinieerd. 

![](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Formules maken voor de aangepaste kolom
U kunt een veld selecteren in de lijst **Beschikbare kolommen:** aan de rechterkant en **<<Invoegen** selecteren om een kolom toe te voegen aan de formule voor de aangepaste kolom. U kunt een kolom ook toevoegen door erop te dubbelklikken.

Als u de formule typt en de kolom bouwt, ziet u onderin het venster een indicator die in realtime (terwijl u typt) aangeeft of er syntaxisfouten zijn gemaakt. Als alles goed is gegaan, ziet u een groen vinkje.

![](media/desktop-add-custom-column/add-custom-column_04.png)

Als er een fout in de syntaxis is gemaakt, verschijnt er een geel waarschuwingspictogram met de gedetecteerde fout en een koppeling die de cursor (in de formule) op de positie zet waar de fout is gedetecteerd.

![](media/desktop-add-custom-column/add-custom-column_05.png)

Als u **OK** selecteert, wordt de aangepaste kolom toegevoegd aan het model en wordt de stap **Aangepaste kolom toegevoegd** toegevoegd aan **Toegepaste stappen** van uw query.

![](media/desktop-add-custom-column/add-custom-column_06.png)

Als u in het deelvenster **Toegepaste stappen** op de stap **Aangepaste kolom toegevoegd** dubbelklikt, verschijnt opnieuw het venster **Aangepaste kolom toevoegen** met de formule voor de aangepaste kolom die is geladen en desnoods kan worden aangepast.

## <a name="using-the-advanced-editor-for-custom-columns"></a>Geavanceerde editor voor aangepaste kolommen gebruiken
U kunt een aangepaste kolom ook maken met **Geavanceerde editor** (en er elke stap van de query trouwens ook mee wijzigen). In **Query-editor** selecteert u het tabblad **Weergave** en vervolgens **Geavanceerde editor** om **Geavanceerde editor** weer te geven.

![](media/desktop-add-custom-column/add-custom-column_07.png)

Met **Geavanceerde editor** hebt u volledige controle over uw query.

## <a name="next-steps"></a>Volgende stappen
Er zijn nog een paar manieren waarop u een aangepaste kolom kunt maken, waaronder het maken van een kolom op basis van voorbeelden die u opgeeft aan **Query-editor**. Zie het volgende artikel voor meer informatie over het maken van aangepaste kommen op basis van voorbeelden:

* [Add a column from an example in Power BI Desktop](desktop-add-column-from-example.md) (Een kolom uit een voorbeeld toevoegen in Power BI Desktop)
* [Introduction to M formula language](https://msdn.microsoft.com/library/mt270235.aspx) (Inleiding tot de taal voor M-formule)
* [M function reference](https://msdn.microsoft.com/library/mt779182.aspx) (Naslag voor M-functies)  

