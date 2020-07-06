---
title: Excel-gegevens geschikt maken voor Q&A in Power BI
description: Uw gegevens geschikt maken voor Q&A in Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: f7760021966673b93313809a806473b94c7750d3
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85218695"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Excel-gegevens geschikt maken voor Q&A in Power BI
Lees verder als u gegevensmodellen maakt of Excel-werkmappen bouwt die worden gebruikt in Power BI.

De Q&A-functie in Power BI zoekt gestructureerde gegevens en kiest de juiste visualisatie voor uw vraag. Dit is precies waar het zo'n aantrekkelijke hulpprogramma is om te gebruiken.   

Q&A kan worden gebruikt voor elk geüpload Excel-bestand dat tabellen, bereiken of een PowerPivot-model bevat, maar hoe meer optimalisaties u uitvoert en gegevens u opschoont, hoe robuuster de prestaties Q&A levert.  Als u rapporten en dashboards op basis van uw gegevensset wilt delen, kunt u beter uw collega's vragen u ruim de tijd te geven om vragen te stellen en antwoorden van kwaliteit te krijgen.

## <a name="how-qa-works-with-excel"></a>Hoe Q&A met Excel samenwerkt
Q&A biedt u een reeks natuurlijke taalverwerkingsmogelijkheden die kunnen worden gebruikt voor al uw gegevens. U kunt contextafhankelijke trefwoorden zoeken in uw Excel-tabel, -kolom en namen van berekende velden. Tevens beschikt de functie over ingebouwde kennis op basis waarvan uw gegevens kunnen worden gefilterd, gesorteerd, geaggregeerd, gegroepeerd en weergegeven. 

Als u bijvoorbeeld een Excel-tabel met de naam Verkopen hebt die de kolommen Product, Maand, Verkochte eenheden, Brutoverkoop en Winst bevat, kunt u over elk van deze entiteiten vragen stellen.  U kunt bijvoorbeeld vragen om het aantal verkopen of de totale winst per maand weer te geven of om de producten te sorteren op basis van de verkochte eenheden. Meer informatie over [het gebruik van Q&A in dashboards en rapporten](power-bi-tutorial-q-and-a.md) en [de typen visualisaties die u kunt opgeven in een Q&A-query](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Een Excel-gegevensset voorbereiden voor Q&A
Q&A is afhankelijk van de namen van tabellen, kolommen en berekende velden om gegevensspecifieke vragen te kunnen beantwoorden. De entiteiten in u werkmap spelen dus een belangrijke rol.

Hier volgen enkele tips optimaal gebruik van Q&A te maken in uw werkmap.

* Zorg ervoor dat uw gegevens in een Excel-tabel staan. U kunt als volgt [een Excel-tabel maken](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Zorg ervoor dat de namen van tabellen, kolommen en het berekende veld logische klinken in natuurlijke taal.
  
  Als u bijvoorbeeld een tabel met verkoopgegevens hebt, geeft u de tabel de naam Verkoop. Kolomnamen zoals Jaar, Product, Vertegenwoordiger en Bedrag werken uitstekend in Q&A.

* Als uw werkmap een Power Pivot-gegevensmodel bevat, kunt u nog meer optimalisaties uitvoeren. Lees [Ontrafelen van Power BI Q&A deel 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/) van ons interne team van experts op het gebied van natuurlijk taalgebruik.

* Open de gegevensset in Power BI Desktop openen en maak nieuwe kolommen, maak eenheden en voeg velden samen om unieke waarden samen te stellen, classificeer gegevens op type (bijvoorbeeld datums, tekenreeksen, geografie, afbeeldingen of URL's), en meer.

## <a name="next-steps"></a>Volgende stappen

- [Q&A voor gebruikers](../consumer/end-user-q-and-a.md)  
- [Q&A in dashboards en rapporten gebruiken](power-bi-tutorial-q-and-a.md)
- [On-premises gegevenssets voorbereiden voor Q&A](service-q-and-a-direct-query.md)   
- [Gegevens ophalen (voor Power BI)](../connect-data/service-get-data.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
