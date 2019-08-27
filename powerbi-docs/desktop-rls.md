---
title: Beveiliging op rijniveau (RLS) met Power BI begrijpen
description: Hoe u de beveiliging op rijniveau voor de geïmporteerde gegevenssets en DirectQuery configureert in Power BI Desktop.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 08/14/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 91f2da65764480a0cf9cf298a052436b27e18c83
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560978"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Beveiliging op rijniveau (RLS) met Power BI

U kunt beveiliging op rijniveau (RLS) in Power BI Desktop gebruiken om de toegang tot gegevens voor bepaalde gebruikers te beperken. Filters beperken gegevens op rijniveau. U kunt filters definiëren in rollen.

U kunt RLS nu configureren voor gegevensmodellen die met Power BI Desktop zijn geïmporteerd in Power BI. U kunt RLS ook configureren voor gegevenssets die gebruikmaken van [DirectQuery](desktop-use-directquery.md), zoals SQL Server. Voorheen kon u RLS alleen implementeren binnen on-premises Analysis Services-modellen buiten Power BI. Voor Analysis Services-liveverbindingen configureert u beveiliging op rijniveau voor het on-premises model. De beveiligingsoptie wordt niet weergegeven voor gegevenssets met een liveverbinding.

> [!IMPORTANT]
> Als u rollen en regels hebt gedefinieerd binnen de Power BI-service moet u deze rollen opnieuw maken binnen Power BI Desktop en het rapport publiceren in de service.

Meer informatie over opties voor [RLS in de Power BI-service](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Volgende stappen

[Beveiliging op rijniveau (RLS) met de Power BI-service](service-admin-rls.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)