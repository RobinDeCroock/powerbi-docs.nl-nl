---
title: Automatische datum/tijd-hulp in Power BI Desktop
description: Richtlijnen voor gebruik van de functionaliteit voor automatische datum/tijd in Power BI Desktop.
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 10/23/2019
ms.openlocfilehash: e7fcab58dc61735639689c4574a9ce89757882ca
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088667"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Automatische datum/tijd-hulp in Power BI Desktop

Dit artikel is bedoeld voor gegevensmodelleerders die import- of samengestelde modellen in Power BI Desktop ontwikkelen. Het bevat richtlijnen, aanbevelingen en overwegingen voor het gebruik van de functionaliteit voor _automatische datum/tijd_ in Power BI Desktop in bepaalde situaties. Zie [Automatische datum/tijd in Power BI Desktop](../transform-model/desktop-auto-date-time.md) voor een overzicht en algemene inleiding tot _automatische datum/tijd_.

De optie _Automatische datum/tijd_ biedt handige, snelle en gebruiksvriendelijke time intelligence. Rapportauteurs kunnen werken met time intelligence bij het filteren, groeperen en inzoomen op kalenderperioden.

## <a name="considerations"></a>Overwegingen

In de volgende lijst met opsommingstekens worden overwegingen en mogelijke beperkingen ten aanzien van de optie _Automatische datum/tijd_ beschreven.

- **Van toepassing op alle of geen:** Als de optie _Automatische datum/tijd_ is ingeschakeld, is deze van toepassing op alle datumkolommen in importtabellen die zich niet aan de &quot;veel&quot;-zijde van een relatie bevinden. De optie kan niet selectief worden in- of uitgeschakeld per kolom.
- **Alleen kalenderperioden:** De jaar- en kwartaalkolommen zijn gerelateerd aan kalenderperioden. Dit betekent dat het jaar begint op 1 januari en eindigt op 31 december. Het is niet mogelijk om de begin- of einddatum van het jaar aan te passen.
- **Aanpassen:** Het is niet mogelijk om de beschrijvende waarden voor de tijdsperioden aan te passen. Het is ook niet mogelijk om extra kolommen toe te voegen om andere tijdsperioden, zoals weken, te beschrijven.
- **Jaar filteren:** De waarden van de kolommen **Kwartaal**, **Maand** en **Dag** bevatten niet de jaarwaarde. De kolom **Maand** bevat bijvoorbeeld alleen de namen van de maanden (Januari, Februari, enzovoort). De waarden zijn niet volledig zelf-beschrijvend en in sommige rapportontwerpen wordt de context van het jaarfilter mogelijk niet gecommuniceerd.

    Daarom is het belangrijk dat filters of groeperingen worden uitgevoerd op de kolom **Jaar**. Wanneer u inzoomt met behulp van de hiërarchie, wordt het jaar gefilterd, tenzij het niveau **Jaar** opzettelijk is verwijderd. Als er geen filter of groep per jaar is, worden in een groepering per maand bijvoorbeeld de waarden voor die maand van alle jaren samengevat.
- **Datum filteren met één tabel:** Omdat elke datumkolom een eigen (verborgen) Automatische datum/tijd-tabel produceert, is het niet mogelijk een tijdfilter toe te passen op één tabel en deze door te geven aan meerdere modeltabellen. Filteren op deze manier is een standaardmodelvereiste voor rapportages over meerdere objecten (feitentabellen), zoals verkoop en verkoopbudget. Wanneer u automatische datum/tijd gebruikt, moet de auteur van het rapport filters toepassen op elke afzonderlijke datumkolom.
- **Modelgrootte:** Voor elke datumkolom die een verborgen automatische datum/tijd-tabel genereert, neemt de grootte van het model toe en duurt ook het vernieuwen van gegevens langer.
- **Andere hulpprogramma's voor rapportage:** Het is niet mogelijk om met automatische datum/tijd-tabellen te werken wanneer:
  - U [Analyseren in Excel](../collaborate-share/service-analyze-in-excel.md) gebruikt.
  - U ontwerpfuncties gebruikt voor Analysis Services-query's van gepagineerde Power BI-rapporten.
  - U verbinding maakt met het model met behulp van niet-Power BI-rapportontwerpers.

## <a name="recommendations"></a>Aanbevelingen

We raden u aan de optie _Automatische datum/tijd-_ alleen ingeschakeld te laten wanneer u met kalenderperioden werkt en wanneer u eenvoudige modelvereisten hebt met betrekking tot tijd. Het gebruik van deze optie kan ook handig zijn bij het maken van ad-hocmodellen of bij het verkennen of profileren van gegevens.

Als uw gegevensbron al een tabel met datumdimensies definieert, moet deze tabel worden gebruikt om de tijd binnen uw organisatie consistent te definiëren. Dit is zeker het geval als uw gegevensbron een datawarehouse is. Anders kunt u datumtabellen in uw model genereren met behulp van de DAX-functies [CALENDAR](/dax/calendar-function-dax) of [CALENDARAUTO](/dax/calendarauto-function-dax). U kunt vervolgens berekende kolommen toevoegen ter ondersteuning van de bekende vereisten voor filtering en groepering op tijd. Met deze ontwerpmethode kunt u één datumtabel maken die wordt doorgegeven aan alle feitentabellen, waardoor u mogelijk maar één tabel nodig hebt voor het toepassen van tijdfilters. Lees het artikel [Datumtabellen instellen en gebruiken in Power BI Desktop](../transform-model/desktop-date-tables.md) voor meer informatie over het maken van datumtabellen.

Als de optie _Automatische datum/tijd_ niet van belang is voor uw projecten, raden we u aan de algemene optie _Automatische datum/tijd_ uit te schakelen. Dit zorgt ervoor dat bij alle nieuwe Power BI Desktop-bestanden die u maakt, de optie _Automatische datum/tijd_ wordt uitgeschakeld.

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Datumtabellen in Power BI Desktop maken](model-date-tables.md)
- [Automatische datum/tijd in Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Datumtabellen instellen en gebruiken in Power BI Desktop](../transform-model/desktop-date-tables.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
