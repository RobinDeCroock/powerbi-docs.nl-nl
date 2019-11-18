---
title: Gearchiveerde Power BI-werkruimte
description: Gearchiveerde Power BI-werkruimte na het beheren van uw Office 365-tenant
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 66bf203cad577df0c985fbd73bcab3c6d79f6a95
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873574"
---
# <a name="power-bi-archived-workspace"></a>Gearchiveerde Power BI-werkruimte

> [!IMPORTANT]
> Power BI biedt geen ondersteuning meer voor de functie Gearchiveerde werkruimte, die aan het einde van 2019 wordt verwijderd. Als u een gearchiveerde werkruimte gebruikt, moet u alle inhoud die u wilt behouden, onmiddellijk opnieuw maken in een nieuwe werkruimte in uw huidige tenant. We kunnen namelijk niet garanderen dat u blijvend toegang zult hebben tot de gearchiveerde werkruimte. Power BI biedt ook geen ondersteuning meer voor de gerelateerde voorziening voor [externe overname van een Azure AD-tenant](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

Met Power BI kan iedereen zich aanmelden en de service binnen een paar minuten gaan gebruiken.  De IT-afdeling van uw organisatie kan er later voor kiezen om het beheer van Power BI over te nemen voor gebruikers in uw organisatie.  Het centraal beheren van gebruikers en machtigingen in uw organisatie biedt allerlei voordelen. Ook bestaat dan de mogelijkheid dat u gebruik kunt maken van gestroomlijnde aanmelding door dezelfde combinatie van gebruikersnaam en wachtwoord te gebruiken voor andere services in uw organisatie.

Alle inhoud die u hebt gemaakt voordat uw IT-afdeling Power BI beheerde, wordt geplaatst in een gearchiveerde Power BI-werkruimte, die toegankelijk is vanuit het navigatievenster van [Power BI](https://app.powerbi.com). U moet nieuwe Power BI-inhoud gaan maken in Mijn werkruimte, die wordt beveiligd en beheerd door de IT-afdeling van uw organisatie.  De gearchiveerde werkruimte blijft bestaan, maar er gelden beperkingen voor acties die u kunt uitvoeren op de inhoud in uw gearchiveerde werkruimte.  Om deze beperkingen weg te nemen, moet u de inhoud van uw gearchiveerde werkruimte migreren naar Mijn werkruimte, die wordt beheerd door uw IT-afdeling.

## <a name="restrictions-in-your-archived-workspace"></a>Beperkingen in uw gearchiveerde werkruimte

Er wordt door Power BI geen inhoud verwijderd uit uw gearchiveerde werkruimte. U kunt nog steeds gegevens ophalen, rapporten en dashboards maken en gegevenssets vernieuwen. Bestaande gebruikers waarmee u inhoud hebt gedeeld, kunnen de inhoud ook nog weergeven in hun gearchiveerde werkruimte. Er gelden echter enkele beperkingen met betrekking tot de inhoud in uw gearchiveerde werkruimte:

* **OneDrive voor Bedrijven**: In het geval van gegevenssets in uw gearchiveerde werkruimte is het niet meer mogelijk om gegevens op te halen of te vernieuwen vanuit OneDrive voor Bedrijven.  Als u probeert verbinding te maken met deze bron, ziet u een waarschuwing.

* **Dashboards delen**: U kunt geen dashboards delen met andere gebruikers vanuit uw gearchiveerde werkruimte.  Gebruikers die al toegang hebben, kunnen gedeelde dashboards nog steeds weergeven door hun gearchiveerde werkruimte te openen.

* **Groepen maken**: U kunt geen groepen maken in uw gearchiveerde werkruimte.

* **Toegang via mobiele Power BI-apps**: U kunt wel inhoud op het web bekijken in uw gearchiveerde werkruimte, maar deze inhoud wordt niet meer weergegeven in mobiele Power BI-apps.

## <a name="migrating-content-in-your-archived-workspace"></a>Inhoud in uw gearchiveerde werkruimte migreren

Als u Power BI wilt blijven gebruiken, moet u nieuwe inhoud maken in Mijn werkruimte. U moet ook plannen om inhoud in uw gearchiveerde werkruimte te migreren naar Mijn werkruimte.  Hoe u inhoud migreert, is afhankelijk van het type inhoud:

* **Excel- of Power BI Desktop- gegevenssets**: U kunt deze gegevenssets migreren door over te schakelen van uw Gearchiveerde werkruimte naar Mijn werkruimte en het Excel- of Power BI Desktop-bestand opnieuw te uploaden met behulp van de knop **Mijn gegevens**.  Als u geplande vernieuwing instelt, moet u die instellingen opnieuw configureren voor de nieuwe gegevensset in Mijn werkruimte.

* **Andere gegevenssets**: Schakel over naar Mijn werkruimte en selecteer de knop **Gegevens ophalen** om opnieuw verbinding te maken met andere gegevenssets die u hebt gemaakt in uw Gearchiveerde werkruimte.  Mogelijk moet u beveiligings- of verbindingsinformatie opnieuw invoeren.

* **Rapporten**: Rapporten die zijn opgenomen in Excel- of Power BI Desktop-bestanden, worden automatisch opnieuw gemaakt wanneer u het bijbehorende Excel- of Power BI Desktop-bestand opnieuw uploadt. Rapporten die zijn geïnstalleerd als onderdeel van een inhoudspakket worden ook opnieuw gemaakt wanneer u opnieuw verbinding maakt met het inhoudspakket. Als u uw eigen rapporten hebt gemaakt via de Power BI-service, moet u deze rapporten opnieuw maken in Mijn werkruimte.

* **Dashboards**: Dashboards die zijn geïnstalleerd als onderdeel van inhoudspakketten, worden automatisch opnieuw gemaakt wanneer u opnieuw verbinding maakt met het inhoudspakket in Mijn werkruimte. Als u uw eigen dashboards hebt gemaakt via de Power BI-service, moet u deze dashboards opnieuw maken in Mijn werkruimte.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

