---
title: Always Encrypted bij Power BI Report Server
description: In dit artikel wordt Always Encrypted-ondersteuning voor Power BI Report Server beschreven bij het gebruik van de gegevensbrontypen Microsoft SQL Server en Microsoft Azure SQL Database.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f921d9dbeb16d1b960e22f228f7833c8fbf184b4
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861240"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted bij Power BI Report Server

In dit artikel wordt Always Encrypted-ondersteuning voor Power BI Report Server beschreven bij het gebruik van de gegevensbrontypen Microsoft SQL Server en Microsoft Azure SQL Database. Zie het artikel [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) voor meer informatie over de mogelijkheden van Always Encrypted in SQL Server.

## <a name="always-encrypted-user-isolation"></a>Always Encrypted-gebruikersisolatie

Op dit moment wordt in Power BI Report Server de toegang tot Always Encrypted-kolommen in rapporten niet beperkt als een gebruiker toegang heeft tot het rapport.  Als de server toegang heeft gekregen tot de kolom versleutelingssleutels via de hoofdsleutel van de kolom, hebben gebruikers daarom toegang tot alle kolommen ten aanzien van de rapporten waartoe ze toegang hebben.

## <a name="always-encrypted-column-usage"></a>Gebruik van Always Encrypted-kolom

### <a name="key-storage-strategies"></a>Strategieën voor sleutelopslag

|Opslag  |Ondersteund  |
|---------|---------|
|Windows-certificaatarchief | Ja |
|Azure Key Vault | Nee |
| Cryptography Next Generation (CNG) | Nee |

### <a name="certificate-storage-and-access"></a>Opslag van en toegang tot certificaten

Het account waarvoor toegang tot het certificaat is vereist, is het serviceaccount. Dit certificaat moet zijn opgeslagen in het certificaatarchief op de lokale computer. Raadpleeg voor meer informatie:

- [Het serviceaccount van de rapportserver configureren](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- De sectie [Certificaten beschikbaar maken voor toepassingen en gebruikers](/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) in het SQL Server-artikel 'Hoofdsleutels van kolommen voor Always Encrypted maken en opslaan.'

### <a name="column-encryption-strategy"></a>Strategie voor kolomversleuteling

In Power BI Report Server kan de kolomversleutelingsstrategie *deterministisch* of *willekeurig* zijn. In de volgende tabel worden de verschillen beschreven, afhankelijk van de strategie die wordt gebruikt.

|Gebruiken  |Deterministisch  |Willekeurig  |
|---------|---------|---------|
|Kan ongewijzigd worden gelezen in de resultaten van een query, bijvoorbeeld SELECT-instructies. | Ja  | Ja  |
|Kan worden gebruikt als een groeperen op-entiteit binnen de query. | Ja | Nee |
|Kan worden gebruikt als een aggregatieveld, met uitzondering van COUNT en DISTINCT. | Nee, behalve voor COUNT en DISTINCT | Nee |
|Kan worden gebruikt als rapportparameter | Ja | Nee |

Lees meer over [deterministische versus willekeurige versleuteling](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Parametergebruik

Het gebruik van parameters is alleen van toepassing op deterministische versleuteling.

**Parameter met één waarde**.  U kunt een parameter met één waarde gebruiken voor een Always Encrypted-kolom.

**Parameter met meerdere waarden**. U kunt voor een Always Encrypted-kolom geen parameter met meerdere waarden gebruiken waarin u meer dan één waarde gebruikt.

**Trapsgewijze parameters**. U kunt trapsgewijze parameters gebruiken met Always Encrypted als *alle* volgende beweringen waar zijn:

- Alle Always Encrypted-kolommen moeten Always Encrypted zijn met een deterministische strategie.
- Alle parameters die worden gebruikt voor Always Encrypted-kolommen zijn parameters met één waarde.
- Alle SQL-vergelijkingen gebruiken de operator Is gelijk aan (=).

## <a name="datatype-support"></a>Ondersteuning voor gegevenstype

| SQL-gegevenstype | Biedt ondersteuning voor lezen van veld | Biedt ondersteuning voor het gebruik als Groeperen op-element | Ondersteunde aggregaties (COUNT, DISTINCT, MAX, MIN, SUM, enzovoort) | Ondersteunt filteren via gelijkheid met behulp van parameters | Opmerkingen |
| --- | --- | --- | --- | --- | --- |
| int | Ja | Ja | COUNT, DISTINCT | Ja, als geheel getal |   |
| float | Ja | Ja | COUNT, DISTINCT | Ja, als drijvend getal |   |
| nvarchar | Ja | Ja | COUNT, DISTINCT | Ja, als tekst | Deterministische versleuteling moet een kolomsortering gebruiken met een binary2-sorteervolgorde voor tekenkolommen. Zie het SQL Server-artikel [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) voor meer informatie.  |
| varchar | Ja | Ja | COUNT, DISTINCT | Nee |   |
| decimal | Ja | Ja | COUNT, DISTINCT | Nee |   |
| numeriek | Ja | Ja | COUNT, DISTINCT | Nee |   |
| datum/tijd | Ja | Ja | COUNT, DISTINCT | Nee |   |
| datetime2 | Ja | Ja | COUNT, DISTINCT | Ja, als datum/tijd | Ondersteund als de kolom geen milliseconde-precisie heeft (met andere woorden, geen datetime2(0)) |

## <a name="aggregation-alternatives"></a>Alternatieven voor aggregatie

Momenteel zijn de enige ondersteunde aggregaties voor deterministische Always Encrypted-kolommen de aggregaties die de operator Is gelijk aan (=) rechtstreeks gebruiken. Deze SQL Server-beperking is te wijten aan de aard van Always Encrypted-kolommen. Gebruikers moeten in het rapport aggregaties uitvoeren in plaats van in de database.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted in verbindingsreeksen

U moet Always Encrypted in de verbindingsreeks inschakelen voor een SQL Server-gegevensbron. Meer informatie over het inschakelen van [Always Encrypted in toepassingsquery's](/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Volgende stappen

[Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) in SQL Server en Azure SQL Database

Nog vragen? [Misschien dat de community van Power BI het antwoord weet](https://community.powerbi.com/).