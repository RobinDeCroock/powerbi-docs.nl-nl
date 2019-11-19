---
title: Beperkingen van Power BI Q&A
description: Huidige beperkingen van Power BI Q&A
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9f1beed3408d53a58a0fb725f9d98a4a95bb1b7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874905"
---
# <a name="limitations-of-power-bi-qa"></a>Beperkingen van Power BI Q&A

Power BI Q&A heeft momenteel enkele beperkingen.

## <a name="data-sources"></a>Gegevensbronnen

### <a name="supported-data-sources"></a>Ondersteunde gegevensbronnen

Power BI Q&A ondersteunt de volgende configuraties van gegevensbronnen in de Power BI-service:

- Importmodus
- Live verbinding maken met Azure Analysis Services
- Live verbinding maken met SQL Server Analysis Services (met een gateway)
- Power BI-gegevenssets. Power BI Desktop meldt een fout met Q&A wanneer een Power BI-gegevensset wordt gebruikt. Wanneer u het rapport publiceert naar de Power BI-service, verdwijnt de fout echter.

In elk van deze configuraties wordt beveiliging op rijniveau ook ondersteund.

### <a name="data-sources-not-supported"></a>Gegevensbronnen worden niet ondersteund

Power BI Q&A ondersteunt momenteel de volgende configuraties niet:

- Beveiliging op objectniveau met elk type gegevensbron
- DirectQuery op basis van een willekeurige bron. Een tijdelijke oplossing ter ondersteuning hiervan is het gebruik van Live Connect met Azure Analysis Services, dat DirectQuery gebruikt.
- Samengestelde modellen
- Reporting Services 

## <a name="tooling-limitations"></a>Beperkingen van hulpprogramma's

In het nieuwe dialoogvenster voor hulpprogramma's kunnen gebruikers de natuurlijke taal in Q&A aanpassen en verbeteren. Lees de [Inleiding tot Q&A-hulpprogramma's](q-and-a-tooling-intro.md)voor meer informatie over hulpprogramma's.

## <a name="review-question-limitations"></a>Beperkingen van vragen beoordelen

In de beoordelingsvragen worden vragen die zijn gesteld voor uw gegevensmodel maar 28 dagen bewaard. Wanneer u de nieuwe functie voor beoordelingsvragen gebruikt, ziet u mogelijk dat sommige vragen niet worden vastgelegd. Dit is volgens ontwerp, omdat de engine voor natuurlijke taal een reeks stappen voor het opschonen van gegevens uitvoert om ervoor te zorgen dat niet alle toetsaanslagen van een gebruiker worden vastgelegd of weergegeven.

Tenantbeheerders kunnen de instellingen voor tenantbeheerders gebruiken om de mogelijkheid om vragen op te slaan te beheren. Machtigingen zijn gebaseerd op beveiligingsgroepen. 

Gebruikers kunnen er ook voor zorgen dat hun vragen niet worden vastgelegd door **Instellingen** > **Algemeen** te selecteren en de selectie van **Q&A toestaan om mijn uiting te registreren** op te heffen. 

## <a name="teach-qa-limitations"></a>Beperkingen van Q&A trainen

Met Q&A trainen kunt u twee soorten fouten oplossen:

- Wijs een woord toe aan een veld.
- Wijs een filtervoorwaarde toe aan een woord.

Momenteel wordt er geen ondersteuning geboden voor het opnieuw definiëren van een herkende term of het definiëren van andere typen voorwaarden of zinsdelen. Wanneer u filtervoorwaarden definieert, kunt u ook slechts een beperkt deel van een taal gebruiken, met inbegrip van:

- 'Land' dat 'VS' is
- 'Land' dat niet 'VS' is
- 'Gewicht' > 2000
- 'Gewicht' = 2000
- 'Gewicht' < 2000

> [!NOTE]
> Q&A-hulpprogramma ondersteunt alleen importmodus. Er wordt nog geen ondersteuning geboden voor het maken van een verbinding met een on-premises of Azure Analysis Services-gegevensbron. Deze huidige beperking wordt verwijderd in latere releases van Power BI.

### <a name="statements-not-supported"></a>Instructies worden niet ondersteund

- Het gebruik van metingen in voorwaarden wordt momenteel niet ondersteund. In plaats daarvan kunt u metingen omzetten in berekende kolommen om ze te laten werken.
- Meerdere voorwaarden worden niet ondersteund. Als tijdelijke oplossing maakt u een berekende DAX-kolom waarin u een Boolean-instructie met meerdere voorwaarden evalueert. U kunt dan dat veld gebruiken.
- Als u geen filtervoorwaarde opgeeft wanneer Q&A vraagt om een subset van gegevens, kunt u de definitie niet opslaan, ook niet als de hele instructie geen rode onderstrepingen heeft.
