---
title: Abonneren op gepagineerde rapporten in de Power BI-service
description: Dit artikel bevat aandachtspunten omtrent abonnementen op gepagineerde rapporten in de Power BI-service.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839555"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Uzelf en anderen abonneren op gepagineerde rapporten in de Power BI-service 

U kunt nu e-mailabonnementen maken voor uzelf en anderen voor gepagineerde rapporten in de Power BI-service. Over het algemeen is dit hetzelfde proces als voor [abonneren op rapporten en dashboard in de Power BI-service](service-report-subscribe.md). In dit artikel worden de verschillen en aandachtspunten beschreven. 

Wanneer u abonnementen instelt, kiest u hoe vaak u de e-mails wilt ontvangen: dagelijks, wekelijks of per uur. Als u dagelijks of wekelijks kiest, kunt u de tijd kiezen waarop het abonnement moet worden uitgevoerd. Alles met elkaar kunt u maximaal 24 verschillende abonnementen per dag voor elk rapport instellen. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Overwegingen voor abonnementen op gepagineerde rapporten 

- In tegenstelling tot abonnementen voor dashboards of Power BI-rapporten bevat uw abonnement een bijlage van de gehele rapportuitvoer.  De volgende bijlagentypen worden ondersteund: PDF, PowerPoint-presentaties (PPTX), Excel-werkmappen (XLSX), Word-documenten (DOCX), CSV-bestanden en XML.

- In de hoofdtekst van het e-mailbericht wordt geen voorbeeldafbeelding getoond van het rapport.  We zijn van plan om een afbeelding van de eerste pagina van het rapport als optioneel item mogelijk te maken. 

- De maximale grootte voor rapportbijlagen is 25 MB. 

- U kunt andere gebruikers abonneren op gepagineerde rapporten die verbinding maken met momenteel ondersteunde gegevensbronnen, waaronder Azure Analysis Services en Power BI-gegevenssets. Onthoud dat gegevens in de rapportbijlage net zo zijn gebaseerd op uw machtigingen als bij SQL Server Reporting Services. 

- Abonnementen op rapportpagina's zijn gekoppeld aan de naam van het rapport.  

- E-mailabonnementen worden verzonden met de standaardparameterwaarden voor het rapport. 

- De frequentie-optie **Nadat de gegevens zijn vernieuwd** is niet beschikbaar voor gepagineerde rapporten. U krijgt altijd de meest recente waarden uit de onderliggende gegevensbron. 

## <a name="next-steps"></a>Volgende stappen

[Uzelf en anderen abonneren op rapporten en dashboards in de Power BI-service](service-report-subscribe.md)

[Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
