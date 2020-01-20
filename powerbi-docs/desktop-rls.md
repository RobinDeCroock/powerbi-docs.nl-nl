---
title: Beveiliging op rijniveau (RLS) met Power BI begrijpen
description: Hoe u de beveiliging op rijniveau voor de geïmporteerde gegevenssets en DirectQuery configureert in Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 12/05/2019
LocalizationGroup: Create reports
ms.openlocfilehash: dc2c1e312592048c90643526a898ebe654907a68
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760653"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Gegevenstoegang met beveiliging op rijniveau (RLS) beperken voor Power BI Desktop

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

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)