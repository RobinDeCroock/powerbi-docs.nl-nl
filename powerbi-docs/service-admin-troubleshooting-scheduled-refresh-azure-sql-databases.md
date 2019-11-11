---
title: Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen
description: Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen in Power BI
author: mgblythe
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9846f65951c9cd45f011a2b5ec81852df10b063f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73855842"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Problemen met een geplande vernieuwing voor Azure SQL-databases oplossen in Power BI

Zie [Gegevens in Power BI vernieuwen](refresh-data.md) en [Geplande vernieuwing configureren](refresh-scheduled-refresh.md) voor gedetailleerde informatie over vernieuwen.

Als u tijdens het instellen van de geplande vernieuwing voor Azure SQL-database bij het bewerken van de referenties een fout met foutcode 400 krijgt, probeert u het volgende om de juiste firewallregel in te stellen:

1. Meld u aan bij [Azure Portal](https://portal.azure.com).

1. Ga naar de Azure SQL-database waarvoor u het vernieuwen aan het configureren bent.

1. Selecteer **Serverfirewall instellen** bovenaan de blade **Overzicht**.

1. Zorg ervoor dat **Toegang tot Azure-services toestaan** op de blade **Firewallinstellingen** is ingesteld op **AAN**.

    ![Toegestane services in Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
