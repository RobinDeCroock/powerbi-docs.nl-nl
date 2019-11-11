---
title: Berekende tabellen gebruiken in Power BI Desktop
description: Berekende tabellen in Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 4da25e0c6ea7115111bc057947183a8b86b5c2f4
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878694"
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Berekende tabellen gebruiken in Power BI Desktop
Met berekende tabellen kunt u een nieuwe tabel toevoegen aan het model. In dit geval laadt u echter geen query's en waarden in de kolommen van uw nieuwe tabel vanuit een gegevensbron, maar maakt u een DAX-formule (Data Analysis Expressions) die de waarden van de tabel definieert. In Power BI Desktop worden berekende tabellen gemaakt met behulp van de functie Nieuwe tabel in de rapportweergave of gegevensweergave.

In de meeste gevallen importeert u gegevens in het model vanuit een externe gegevensbron. Berekende tabellen bieden echter bepaalde voordelen. Berekende tabellen zijn gewoonlijk het beste voor tussenliggende berekeningen en gegevens die u wilt opslaan als onderdeel van het model in plaats van op elk gewenst moment te worden berekend of als onderdeel van een query.

Berekende tabellen die zijn gemaakt in de rapport- of gegevensweergave zijn, in tegenstelling tot tabellen die zijn gemaakt als onderdeel van een query, gebaseerd op gegevens die u al in het model hebt geladen. U kunt bijvoorbeeld kiezen om een UNION- of CROSSJOIN-bewerking op twee tabellen uit te voeren.

Net als normale tabellen kunnen berekende tabellen relaties met andere tabellen hebben. De kolommen in de berekende tabel bevatten gegevenstypen, opmaak, en kunnen deel uitmaken van een gegevenscategorie. U kunt de uw kolommen elke naam geven die u wilt en ze toevoegen aan een rapportvisualisatie, net zoals elk ander veld. Berekende tabellen worden opnieuw berekend als een van de tabellen waaruit gegevens worden opgehaald, wordt vernieuwd of op welke manier dan ook wordt bijgewerkt.

Berekende tabellen berekenen resultaten met behulp van [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX), een formuletaal die is bedoeld om te werken met relationele gegevens, zoals in Power BI Desktop. DAX bevat een bibliotheek met meer dan 200 functies, operatoren en constructies. Het biedt zodoende een uitgebreide flexibiliteit bij het maken van formules voor het berekenen van resultaten voor vrijwel elke gegevensanalyse.

## <a name="lets-look-at-an-example"></a>Hier volgt een voorbeeld
Jeff, een projectmanager bij Contoso, heeft een tabel met werknemers in het noordwesten en een andere tabel met werknemers in het zuidwesten. Jeff wil de twee tabellen samenvoegen tot één tabel.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SouthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Het samenvoegen van deze twee tabellen met een berekende tabel is heel eenvoudig. Jeff kan een berekende tabel maken in de rapportweergave of gegevensweergave. Het is echter iets eenvoudiger in de gegevensweergave omdat Jeff dan direct de nieuwe berekende tabel kan zien.

In de **gegevensweergave**op het tabblad **Model maken** klikt Jeff op **Nieuwe tabel**. Er wordt een formulebalk weergegeven.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff voert de volgende formule in:

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

Er wordt een nieuwe tabel met de naam Western Region Employees gemaakt.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

De nieuwe tabel Western Region Employees van Jeff wordt net als elke andere tabel in de lijst met velden weergegeven. Jeff kan zelfs relaties met andere tabellen maken, berekende kolommen en metingen toevoegen en de velden toevoegen aan rapporten, net als bij elke andere tabel.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Functies voor berekende tabellen
Berekende tabellen kunnen worden gedefinieerd met een DAX-expressie die een tabel retourneert, inclusief een eenvoudige verwijzing naar een andere tabel. Bijvoorbeeld:

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

U kunt berekende tabellen met DAX gebruiken om veel analytische problemen op te lossen. We hebben hier slechts een korte inleiding over berekende tabellen gegeven. Als u gaat werken met berekende tabellen, zijn hier enkele van de meest voorkomende DAX-tabelfuncties die u mogelijk van pas komen:

* DISTINCT
* WAARDEN
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Zie de [Naslag voor DAX-functies](https://msdn.microsoft.com/ee634396.aspx) voor deze en andere DAX-functies die tabellen retourneren.

