---
title: Berekende kolommen in Power BI Desktop gebruiken
description: Berekende kolommen in Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: c7a2b3580516c563d8a2a6d79fdc48d241e89849
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239867"
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Berekende kolommen in Power BI Desktop gebruiken
Met berekende kolommen kunt u nieuwe gegevens toevoegen aan een tabel die al in het model is opgenomen. In dit geval laadt u echter geen query's en waarden in de nieuwe kolom van een gegevensbron, maar maakt u een DAX-formule (Data Analysis Expressions) die de waarden van de kolom definieert. In Power BI Desktop worden berekende kolommen gemaakt met behulp van de functie Nieuwe kolom in de rapportweergave.

Berekende kolommen die zijn gemaakt in de rapportweergave of gegevensweergave zijn gebaseerd op gegevens die u al in het model hebt geladen. Dit in tegenstelling tot aangepaste kolommen die zijn gemaakt als onderdeel van een query met behulp van Aangepaste kolom toevoegen in de Query Editor. U kunt bijvoorbeeld waarden uit twee verschillende kolommen in twee verschillende maar gerelateerde tabellen samenvoegen, waarden toevoegen of subtekenreeksen extraheren.

Berekende kolommen die u maakt, worden weergegeven in de lijst met velden, net zoals andere velden. Ze hebben echter een speciaal pictogram dat de waarden weergeeft. Dit is het resultaat van een formule. U kunt de uw kolommen elke naam geven die u wilt en ze toevoegen aan een rapportvisualisatie, net zoals elk ander veld.

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

Berekende kolommen berekenen resultaten met behulp van [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX), een formuletaal die is bedoeld om te werken met relationele gegevens, zoals in Power BI Desktop. DAX bevat een bibliotheek met meer dan 200 functies, operatoren en constructies. Het biedt zodoende een uitgebreide flexibiliteit bij het maken van formules voor het berekenen van resultaten voor vrijwel elke gegevensanalyse. Zie de sectie Meer informatie aan het einde van dit artikel voor meer informatie over DAX.

DAX-formules zijn vergelijkbaar met Excel-formules. In feite heeft DAX veel functies die Excel ook heeft. DAX-functies zijn echter bedoeld om te werken met gegevens die interactief zijn gesegmenteerd of gefilterd in een rapport, zoals in Power BI Desktop. In tegenstelling tot Excel, waarbij u een andere formule kunt hebben voor elke rij in een tabel, berekent een DAX-formule voor een nieuwe kolom het resultaat van elke rij in de tabel. Kolomwaarden worden herberekend indien nodig, zoals wanneer de onderliggende gegevens worden vernieuwd en de waarden zijn gewijzigd.

## <a name="lets-look-at-an-example"></a>Hier volgt een voorbeeld
Jeff is een transportmanager bij Contoso. Hij wil een rapport maken met het aantal verzendingen naar verschillende steden. Hij heeft de tabel Geografie met afzonderlijke velden voor de plaats en provincie. Maar Jeff wil dat in zijn rapporten om de plaats en provincie worden weergegeven als één waarde in dezelfde rij. De tabel Geografie beschikt nu niet over het veld dat Jeff wil gebruiken.

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

Maar met een berekende kolom kan Jeff de plaatsen uit de kolom Plaats en de provincies uit de kolom Provincie gewoon samen gebruiken, of samenvoegen.

Jeff klikt met de rechtermuisknop op de tabel Geografie en klikt vervolgens op Nieuwe kolom. Hij voert de volgende DAX-formule in de formulebalk in:

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

Deze formule maakt een nieuwe kolom met de naam PlaatsProvincie. Voor elke rij in de tabel Geografie worden de waarden uit de kolom Plaats opgehaald en wordt er een komma en een spatie toegevoegd. Vervolgens worden de waarden in de kolom Provincie aan de nieuwe kolom toegevoegd.

Jeff heeft nu het veld dat hij wil.

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Hij kan deze toevoegen aan zijn rapportcanvas, samen met het aantal verzendingen. Jeff heeft nu zeer snel en met een minimale inspanning een veld Plaats, Provincie die hij aan bijna elk type visualisatie kan toevoegen. Jeff ziet dat Power BI Desktop zelfs weet hoe het de Plaats, Provincie-waarden moet lezen in zijn nieuwe kolom wanneer hij een kaartvisualisatie maakt.

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>Meer informatie
We hebben hier slechts een korte inleiding over berekende kolommen gegeven. Zorg ervoor dat u [Zelfstudie: Berekende kolommen maken in Power BI Desktop](desktop-tutorial-create-calculated-columns.md), waar u een voorbeeldbestand kunt downloaden en stapsgewijze lessen krijgt over het maken van meer kolommen. 

Zie [DAX-basisbeginselen in Power BI Desktop](desktop-quickstart-learn-dax-basics.md) voor meer informatie over DAX.

Zie de sectie Aangepaste kolommen maken in [Algemene querytaken in Power BI Desktop](desktop-common-query-tasks.md) voor meer informatie over de kolommen die u als onderdeel van een query maakt.  

