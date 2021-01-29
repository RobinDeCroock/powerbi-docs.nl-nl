---
title: Intrekkings controle van certificaten in Power BI Desktop
description: Certificaten intrekken in Power BI Desktop in de gebruikers interface en in het REGI ster
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2021
ms.locfileid: "99057000"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Intrekken van certificaten in Power BI Desktop

Power BI biedt twee manieren om een certificaat controle in of uit te scha kelen. In november 2020 hebben we een eenvoudige controle op het intrekken van certificaten geïntroduceerd voor webverbindingen in Power BI Desktop. U kunt nu meer nauw keurige controle hebben over de intrekkings controle van het certificaat.

## <a name="simple-certificate-revocation"></a>Eenvoudige certificaat intrekking

In de gebruikers interface van Power BI Desktop kunt u de functie in-of uitschakelen.

- Selecteer in het menu **bestand** > **Opties en instellingen**  >  **Opties** **beveiliging** en schakel vervolgens **controle op certificaat intrekking inschakelen** in of uit.

## <a name="more-fine-grained-control"></a>Meer nauw keurig beheer

U kunt meer nauw keurige controle over de intrekkings controle voor certificaten met een derde optie hebben. 

- **Basis**  De basis controle accepteert certificaten waarvan de intrekkings status onbekend is, bijvoorbeeld omdat het certificaat niet is opgegeven. Deze controle is belang rijk voor organisaties die bedrijfs proxy servers gebruiken. Dit is hetzelfde als het selectie vakje in Power BI Desktop.
- **Uitgeschakeld** Hetzelfde als het uitschakelen van het selectie vakje in Power BI Desktop.
- **Uitgebreide** U kunt de intrekkings controle in de *uitgebreide* modus in-of uitschakelen, die geen certificaten accepteert met een onbekende intrekkings status. 


|Status van informatie voor het intrekken van certificaten | Uitgebreide controle | Basis controle | Geen |
|---------|---------|---------|---------|
|Revoked     |  ❌  | ❌  | ✔   |
|Onbekend  |  ❌    |  ✔   |    ✔  |
|Niet ingetrokken  | ✔  |    ✔ |    ✔  |

Het selectie vakje eenvoudig inschakelen of uitschakelen bevindt zich nog steeds in de Power BI Desktop gebruikers interface. Als u het uitgebreide besturings element wilt gebruiken, stelt u de volgende DWORD-register waarde in: `DisableCertificateRevocationCheck` . U kunt deze waarde instellen in de register sleutel Power BI Desktop. Dit is een van de volgende, afhankelijk van het besturings systeem:

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

Of

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

Stel de register waarde in op een van de volgende waarden: 

|Waarde  |Modus  |Configuratie  |
|---------|---------|---------|
|0     | Basic   | Certificaten met een onbekende intrekkings status worden geaccepteerd. Komt overeen met het inschakelen van het selectie vakje in Power BI Desktop. |
|1     | Uitgeschakeld  | Hiermee worden alle intrekkings controles genegeerd. Komt overeen met het uitschakelen van het selectie vakje in Power BI Desktop.  |
|2     | Uitgebreid  |  Vereist het niet intrekken van certificaten. Accepteert geen certificaten met een onbekende intrekkings status |

Configureer deze register instelling om vandaag nog te profiteren van meer nauw keurige controle.