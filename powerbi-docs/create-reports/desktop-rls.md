---
title: Gegevenstoegang met beveiliging op rijniveau (RLS) beperken voor Power BI Desktop
description: Hoe u de beveiliging op rijniveau voor de geïmporteerde gegevenssets en DirectQuery configureert in Power BI Desktop.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 0d5501ba8929318081a5db7e34e80722f2ffbf70
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412846"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Gegevenstoegang met beveiliging op rijniveau (RLS) beperken voor Power BI Desktop

U kunt beveiliging op rijniveau (RLS) in Power BI Desktop gebruiken om de toegang tot gegevens voor bepaalde gebruikers te beperken. Filters beperken gegevens op rijniveau. U kunt filters definiëren in rollen.

U kunt RLS nu configureren voor gegevensmodellen die met Power BI Desktop zijn geïmporteerd in Power BI. U kunt RLS ook configureren voor gegevenssets die gebruikmaken van [DirectQuery](../connect-data/desktop-use-directquery.md), zoals SQL Server. Voorheen kon u RLS alleen implementeren binnen on-premises Analysis Services-modellen buiten Power BI. Voor Analysis Services-liveverbindingen configureert u beveiliging op rijniveau voor het on-premises model. De beveiligingsoptie wordt niet weergegeven voor gegevenssets met een liveverbinding.

> [!IMPORTANT]
> Als u rollen en regels hebt gedefinieerd binnen de Power BI-service moet u deze rollen opnieuw maken binnen Power BI Desktop en het rapport publiceren in de service. Meer informatie over opties voor [RLS in de Power BI-service](../admin/service-admin-rls.md).

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Beveiliging op rijniveau (RLS) met Power BI](../admin/service-admin-rls.md)
- [Richtlijnen voor beveiliging op rijniveau (RLS) in Power BI Desktop](../guidance/rls-guidance.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
