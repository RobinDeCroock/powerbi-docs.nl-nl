---
title: Gegevens uit bestanden ophalen voor Power BI
description: Lees hier hoe u gegevens uit Excel, Power BI Desktop en CSV-bestanden overbrengt naar Power BI.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b7b886b5e0c21c77e0a5a6aca83fa0ae0751f435
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264111"
---
# <a name="get-data-from-files-for-power-bi"></a>Gegevens uit bestanden ophalen voor Power BI
![Het Excel-, Power BI Desktop- en CSV-pictogram](media/service-get-data-from-files/file_icons.png)

Power BI ondersteunt drie soorten bestanden waarmee verbinding kan worden gemaakt of waaruit gegevens en rapporten kunnen worden geïmporteerd.

* Microsoft Excel (.xlsx of .xlsm)
* Power BI Desktop (.pbix)
* Door komma's gescheiden waarden (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Wat betekent gegevens ophalen uit een bestand eigenlijk?
De gegevens die u verkent in Power BI zijn afkomstig uit een gegevensset. Maar om een gegevensset te maken, moet u wel eerst wat gegevens hebben. In dit artikel besteden we aandacht aan het ophalen van gegevens uit bestanden.

Om het belang van gegevenssets beter te begrijpen, en hoe we gegevens voor ze ophalen, maken we de vergelijking met een auto. Ga lekker zitten in uw auto en kijk naar het dashboard. In een moderne auto heeft dat wel wat weg van het zitten achter uw computer terwijl u naar een dashboard in Power BI kijkt. Het dashboard laat alle dingen zien die uw auto doet; het toerental van de motor, de temperatuur, de gekozen versnelling, de rijsnelheid, enzovoort.

In Power BI is een gegevensset vergelijkbaar met de motor in uw auto. De gegevensset bevat de gegevens, metrische gegevens en informatie die worden weergegeven in uw Power BI-dashboard. Natuurlijk heeft uw motor, of gegevensset, brandstof nodig en in Power BI bestaat die brandstof uit gegevens. Uw auto heeft een brandstoftank die de brandstof voor de motor bevat. Zo werkt het ook in Power BI. Daar bevat de brandstoftank de gegevens waarmee u de gegevensset kunt vullen. In ons geval is die brandstoftank een Power BI Desktop-bestand, een Excel-werkmapbestand of een CSV-bestand.

We kunnen zelfs nog een stapje verder gaan. Een brandstoftank in een auto moet met brandstof worden gevuld. De brandstof voor ons Power BI Desktop-, Excel- of CSV-bestand bestaat uit gegevens uit een andere gegevensbron. We halen gegevens op uit een andere gegevensbron en plaatsen deze in een Excel-, Power BI Desktop- of CSV-bestand. Als het een Excel-werkmap of CSV-bestand is, kunnen we handmatig rijen met gegevens invoeren. We kunnen ook verbinding maken met een externe gegevensbron om gegevens op te vragen en in ons bestand te laden. Als we een bestand met gegevens hebben, kunnen we dat als een gegevensset overbrengen naar Power BI.

> [!NOTE]
> Gegevens in Excel-werkmappen moeten in een tabel staan, of in het gegevensmodel, om te kunnen worden geïmporteerd door Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>Waar uw bestand wordt opgeslagen maakt het verschil
**Lokaal**: Als u het bestand opslaat op een lokaal station op uw computer of op een andere locatie binnen uw organisatie, kunt het bestand *importeren* in Power BI. Het bestand blijft op het lokale station staan. Het bestand wordt dus eigenlijk niet echt geïmporteerd in Power BI. Wat er wel gebeurt, is dat er een nieuwe gegevensset wordt gemaakt in uw Power BI-site en dat de gegevens, en in sommige gevallen het gegevensmodel, in de gegevensset worden geladen. Als uw bestand rapporten bevat, worden deze weergegeven in de Power BI-site, onder Rapporten.

**OneDrive voor Bedrijven**: Als u OneDrive voor Bedrijven hebt en zich aanmeldt met hetzelfde account als voor Power BI, is dit verreweg de meest efficiënte manier om uw werk in Excel Power BI Desktop te houden of om een CSV-bestand gesynchroniseerd te houden met uw gegevensset, rapporten en dashboards in Power BI. Omdat zowel Power BI als OneDrive zich in de cloud bevinden, maakt Power BI ongeveer om het uur verbinding met uw bestand in OneDrive. Als er wijzigingen worden gevonden, worden uw gegevensset, rapporten en dashboards in Power BI automatisch bijgewerkt.

**OneDrive - Persoonlijk** Als u de bestanden opslaat in uw eigen OneDrive-account, geniet u veelal dezelfde voordelen als met OneDrive voor Bedrijven. Het belangrijkste verschil is dat wanneer u voor het eerst verbinding maakt met het bestand (met Gegevens ophalen > Bestanden > OneDrive - Persoonlijk), u zich bij OneDrive moet aanmelden met uw Microsoft-account. Dit is doorgaans een ander account dan het account dat u gebruikt om u aan te melden bij Power BI. Wanneer u zich met uw Microsoft-account aanmeldt bij OneDrive, moet u ervoor zorgen dat u het selectievakje Aangemeld blijven inschakelt. Op deze manier kan er om het uur verbinding via Power BI worden gemaakt met uw bestand en zorgt u ervoor dat uw gegevensset in Power BI wordt gesynchroniseerd.

**SharePoint - Teamsites**: als u uw Power BI Dekstop-bestanden wilt opslaan naar SharePoint - Teamsites, doet u dit op vrijwel dezelfde manier als bij OneDrive voor Bedrijven. Het grootste verschil is de manier waarop u vanuit Power BI verbinding maakt met het bestand. U kunt een URL opgeven of verbinding maken met de hoofdmap.

## <a name="ready-to-get-started"></a>Klaar om te beginnen?
Raadpleeg de volgende artikelen voor meer informatie over het ophalen van bestanden in Power BI.

* [Gegevens ophalen uit Excel-werkmappen](service-excel-workbook-files.md)
* [Gegevens ophalen uit Power BI Desktop-bestanden](service-desktop-files.md)
* [Gegevens ophalen uit CSV-bestanden (bestand met door komma's gescheiden waarden)](service-comma-separated-value-files.md)

