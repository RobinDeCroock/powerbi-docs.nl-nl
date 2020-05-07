---
title: Abonneren op gepagineerde rapporten in de Power BI-service
description: Dit artikel bevat aandachtspunten omtrent abonnementen op gepagineerde rapporten in de Power BI-service.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: d3813636010dcbf5c866248111755beb0dca99b8
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "74834627"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Uzelf en anderen abonneren op gepagineerde rapporten in de Power BI-service 

U kunt nu e-mailabonnementen maken voor uzelf en anderen voor gepagineerde rapporten in de Power BI-service. Over het algemeen is dit hetzelfde proces als voor [abonneren op rapporten en dashboard in de Power BI-service](end-user-subscribe.md). In dit artikel worden de verschillen en aandachtspunten beschreven. 

Wanneer u abonnementen instelt, kiest u hoe vaak u de e-mails wilt ontvangen: dagelijks, wekelijks, maandelijks of per uur. U kunt ook de tijdstippen kiezen waarop het abonnement moet worden uitgevoerd. Alles met elkaar kunt u maximaal 24 verschillende abonnementen voor elk rapport instellen. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Overwegingen voor abonnementen op gepagineerde rapporten 

- In tegenstelling tot abonnementen voor dashboards of Power BI-rapporten bevat uw abonnement een bijlage van de gehele rapportuitvoer.  De volgende bijlagentypen worden ondersteund: PDF, PowerPoint-presentaties (PPTX), Excel-werkmappen (XLSX), Word-documenten (DOCX), CSV-bestanden en XML.

- U kunt een voorbeeldafbeelding van het rapport opnemen in de hoofdtekst van een e-mailbericht.  Dit is optioneel en kan enigszins afwijken van de eerste pagina van het rapportdocument dat u bijvoegt, afhankelijk van de geselecteerde bijlage-indeling. 

- De maximale grootte voor rapportbijlagen is 25 MB. 

- U kunt andere gebruikers abonneren op gepagineerde rapporten die verbinding maken met momenteel ondersteunde gegevensbronnen, waaronder Azure Analysis Services en Power BI-gegevenssets. Onthoud dat gegevens in de rapportbijlage net zo zijn gebaseerd op uw machtigingen als bij SQL Server Reporting Services. 

- E-mailabonnementen kunnen worden verzonden met de momenteel geselecteerde of standaardparameters voor uw rapport.  U kunt verschillende parameterwaarden instellen voor elk abonnement dat u voor uw rapport maakt. 

- Als de auteur van het rapport parameters op basis van een expressie heeft ingesteld (bijvoorbeeld dat de standaardwaarde altijd de huidige datum is), worden deze gebruikt als de standaardinstellingen voor het abonnement. U kunt andere parameterwaarden wijzigen en ervoor kiezen om huidige waarden te gebruiken, maar voor het abonnement wordt de op de expressie gebaseerde parameter gebruikt, tenzij u deze waarde ook expliciet wijzigt.

- De frequentie-optie **Nadat de gegevens zijn vernieuwd** is niet beschikbaar voor gepagineerde rapporten. U krijgt altijd de meest recente waarden uit de onderliggende gegevensbron. 

## <a name="next-steps"></a>Volgende stappen

[Uzelf en anderen abonneren op rapporten en dashboards in de Power BI-service](../service-report-subscribe.md)

[Gepagineerde rapporten in de Power BI-service](end-user-paginated-report.md)

