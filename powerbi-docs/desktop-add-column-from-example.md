---
title: Een kolom uit een voorbeeld toevoegen in Power BI Desktop
description: Maak snel een nieuwe kolom in Power BI Desktop met bestaande kolommen als voorbeelden.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: b10bbaa4158e6c5392cb6ed937c54bdbb5d555d2
ms.sourcegitcommit: 02342150eeab52b13a37b7725900eaf84de912bc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/23/2020
ms.locfileid: "76538480"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Een kolom uit voorbeelden toevoegen in Power BI Desktop
Met *Een kolom uit voorbeelden toevoegen* in Power Query-editor kunt u nieuwe kolommen toevoegen aan uw gegevensmodel door simpelweg een of meer voorbeeldwaarden voor de nieuwe kolommen op te geven. U kunt de nieuwe kolomvoorbeelden maken op basis van een selectie of invoer opgeven die is gebaseerd op alle bestaande kolommen in de tabel.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

Met behulp van *Een kolom uit een voorbeeld toevoegen* kunt u snel en eenvoudig nieuwe kolommen maken. Dit is handig in de volgende gevallen:

- U weet welke gegevens uw nieuwe kolom moet bevatten, maar u weet niet met welke transformatie(s) u dat resultaat bereikt.
- U weet al welke transformaties u nodig hebt, maar weet niet zeker wat u in de gebruikersinterface moet selecteren om die transformaties te bewerkstelligen.
- U weet alles over de benodigde transformaties met behulp van een *Aangepaste kolom*-expressie in de *M*-taal, maar een of meer expressies komen niet voor in de gebruikersinterface.

Het toevoegen van een kolom uit een voorbeeld is gemakkelijk en eenvoudig. In de volgende secties ziet u hoe eenvoudig het is.

## <a name="add-a-new-column-from-examples"></a>Een nieuwe kolom uit een voorbeeld toevoegen

Als u voorbeeldgegevens van Wikipedia wilt ophalen, selecteert u **Gegevens ophalen** > **Internet** op het tabblad **Start** van het Power BI Desktop-lint. 

![Gegevens ophalen van internet](media/desktop-add-column-from-example/add-column-from-example_02.png)

Plak de volgende URL in het dialoogvenster dat wordt weergegeven en selecteer **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

Selecteer in het dialoogvenster **Navigator** de tabel **States of the United States of America** en selecteer vervolgens **Gegevens transformeren**. De tabel wordt geopend in de Power Query-editor.

Als u al geladen gegevens van Power BI Desktop wilt openen, selecteert u **Query's bewerken** op het tabblad **Start** van het lint. De gegevens worden geopend in de Power Query-editor. 

![Query's bewerken selecteren in Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

Zodra de voorbeeldgegevens in de Power Query-editor zijn geopend, selecteert u het tabblad **Kolom toevoegen** op het lint en selecteert u **Kolom vanuit voorbeelden**. Selecteer het pictogram **Kolom uit voorbeelden** zelf om de kolom te maken op basis van alle bestaande kolommen, of selecteer de vervolgkeuzepijl om te kiezen tussen **Vanuit alle kolommen** of **Vanuit selectie**. Gebruik voor deze walkthrough **Vanuit alle kolommen**.

![Kolom toevoegen uit voorbeelden selecteren](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Het deelvenster Kolom toevoegen uit voorbeelden
Wanneer u **Kolom toevoegen** > **Vanuit voorbeelden** selecteert, wordt in het deelvenster **Kolom toevoegen uit voorbeelden** bovenaan de tabel weergegeven. De nieuwe **Kolom 1** wordt rechts van de bestaande kolommen weergegeven (mogelijk moet u scrollen om ze allemaal weer te geven). Wanneer u de voorbeeldwaarden in de lege cellen van **Kolom 1** invoert, worden er door Power BI regels en transformaties gemaakt die overeenkomen met uw voorbeelden; deze worden gebruikt om de rest van de kolom in te vullen.

U ziet dat ook **Kolommen vanuit voorbeelden** wordt weergegeven als een **toegepaste stap** in het deelvenster **Query-instellingen**. Zoals altijd worden uw transformatiestappen vastgelegd in Power Query-editor en op de query toegepast in de volgorde waarin ze zijn vastgelegd.

![Het deelvenster Kolom toevoegen uit voorbeelden](media/desktop-add-column-from-example/add-column-from-example_04.png)

Terwijl u uw voorbeeld in de nieuwe kolom typt, wordt in Power BI getoond hoe de rest van de kolom eruit komt te zien op basis van de gemaakte transformaties. Bijvoorbeeld: als u op de eerste rij *Alabama* typt, komt dit overeen met de waarde **Alabama** in de eerste kolom van de tabel. Zodra u op Enter drukt, wordt in Power BI de rest van de nieuwe kolom ingevuld op basis van de eerste kolomwaarde en wordt een naam gegeven aan de kolom **Naam en postafkorting[12] - Kopiëren**.

Ga nu naar de rij **Massachusetts [E]** van de nieuwe kolom en verwijder het gedeelte **[E]** van de tekenreeks. De wijziging wordt gedetecteerd door Power BI en het voorbeeld wordt gebruikt om een transformatie te maken. In Power BI worden de transformaties beschreven in het deelvenster **Kolom toevoegen uit voorbeelden** en wordt de naam van de kolom gewijzigd in **Tekst vóór scheidingsteken**. 

![Getransformeerde kolom uit voorbeelden](media/desktop-add-column-from-example/add-column-from-example_06.png)

Elk voorbeeld dat u opgeeft, wordt in Power Query-editor toegevoegd aan de transformaties. Wanneer u tevreden bent, selecteert u **OK** om uw wijzigingen op te slaan. 

U kunt de naam van de nieuwe kolom wijzigen door op de kolomkop te dubbelklikken of door er met de rechtermuisknop op te klikken en **Naam wijzigen** te selecteren. 

Bekijk deze video om de functie **Kolom toevoegen uit voorbeelden** in actie te zien, met behulp van de voorbeeldgegevensbron: 

[Power BI Desktop: Kolom toevoegen uit voorbeelden](https://www.youtube.com/watch?v=-ykbVW9wQfw). 

## <a name="list-of-supported-transformations"></a>Lijst met ondersteunde transformaties
Veel, maar niet alle, transformaties zijn beschikbaar wanneer u **Kolom toevoegen uit voorbeelden** gebruikt. De volgende lijst bevat alle ondersteunde transformaties:

**Algemeen**

- Voorwaardelijke kolom

**Verwijzing**
  
- Verwijzing naar een specifieke kolom, inclusief transformaties zoals het inkorten of verwijderen van tekst en het wijzigen van hoofdletters in kleine letters of omgekeerd

**Teksttransformaties**

- Combineren (ondersteunt het combineren van letterlijke waarden en hele-kolomwaarden)
- Vervangen
- Lengte
- Extraheren   
  - Eerste tekens
  - Laatste tekens
  - Bereik
  - Tekst voor scheidingsteken
  - Tekst na scheidingsteken
  - Tekst tussen scheidingstekens
  - Lengte
  - Tekens verwijderen
  - Tekens behouden

> [!NOTE]
> Bij alle *tekst*transformaties wordt rekening gehouden met de mogelijke noodzaak tot inkorting, verwijdering of wijziging van hoofdletters in kleine letters of omgekeerd.

**Gegevenstransformaties**

- Dag
- Dag van de week
- Naam van de dag van de week
- Dag van het jaar
- Maand
- Naam van de maand
- Kwartaal van het jaar
- Week van de maand
- Week van het jaar
- Jaar
- Ouderdom
- Begin van het jaar
- Einde van het jaar
- Begin van de maand
- Einde van de maand
- Begin van het kwartaal
- Dagen in de maand
- Einde van het kwartaal
- Begin van de week
- Einde van de week
- Dag van de maand
- Begin van de dag
- Einde van de dag

**Tijdstransformaties**

- Hour
- Minuut
- Second  
- Naar lokale tijd

> [!NOTE]
> Bij alle transformaties van *datum* en *tijd* wordt rekening gehouden met de mogelijke noodzaak tot conversie van de kolomwaarde naar een *datum* of *tijd* of *datum en tijd*.

**Getaltransformaties** 

- Absolute waarde
- Arccosinus
- Arcsinus
- Arctangens
- Converteren naar getal
- Cosinus
- Kubus
- Delen
- Exponent
- Faculteit
- Delen door geheel getal
- Is even
- Is oneven
- Ln
- Logaritme met grondtal 10
- Modulo
- Vermenigvuldigen
- Naar beneden afronden
- Naar boven afronden
- Teken
- Sinus
- Vierkantswortel
- Kwadraat
- Aftrekken
- Som
- Tangens
- Bucketing/Bereiken

