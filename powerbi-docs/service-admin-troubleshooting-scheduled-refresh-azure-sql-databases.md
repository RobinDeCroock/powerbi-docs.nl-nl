---
title: Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen
description: Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen in Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0c22d005044c0ebddc242eb35908e26689fee597
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61186885"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen in Power BI
Voor gedetailleerde stappen voor het instellen van de geplande vernieuwing, kunt u [Gegevens vernieuwen in Power BI](refresh-data.md) raadplegen.

Als u tijdens het instellen van de geplande vernieuwing voor Azure SQL een fout met foutcode 400 krijgt bij het bewerken van de referenties, probeert u het volgende om de juiste firewallregel in te stellen:

1. Meld u aan bij de Azure Management Portal
2. Ga naar de Azure SQL-server waarvoor u de vernieuwing wilt configureren
3. Schakel 'Windows Azure-services' in het gedeelte Toegestane services in

![Toegestane services in Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

