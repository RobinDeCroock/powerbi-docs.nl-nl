---
title: Door de klant beheerde sleutels in Power BI gebruiken
description: Meer informatie over door de klant beheerde sleutels in Power BI gebruiken.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 215c84b9af9d3b785c055d633a41b99bbea2bb2f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512580"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Door de klant beheerde sleutels in Power BI gebruiken

In Power BI worden data-at-rest en tijdens verwerking versleuteld. In Power BI wordt standaard gebruikgemaakt van door Microsoft beheerde sleutels om uw gegevens te versleutelen. Organisaties kunnen ervoor kiezen om hun eigen sleutels te gebruiken voor het versleutelen van gebruikerscontent at-rest in Power BI, van rapportinstallatiekopieën tot geïmporteerde gegevenssets in Premium-capaciteiten. 

## <a name="why-use-customer-managed-keys"></a>Waarom door de klant beheerde sleutels gebruiken?

Met Power BI door de klant beheerde sleutels (CMK) kunnen organisaties voldoen aan de nalevingsvereisten voor gegevensversleuteling at-rest met hun cloudserviceprovider (in dit geval Microsoft). CMK wordt alleen aangeboden aan nieuwe Power BI Premium-klanten; organisaties kunnen ermee hun Power BI-gebruikersinhoud versleutelen met behulp van een sleutel die ze aanbieden en beheren. Het intrekken van een door de klant beheerde sleutel maakt de gebruikerscontent binnen Power BI binnen een uur onleesbaar voor iedereen, ook voor Microsoft. Vergeleken met de BYOK-aanbieding, bestrijkt CMK ook de gebruikersinhoud die door de service wordt gegenereerd, naast klantgegevens die worden geïmporteerd in rapporten en gegevenssets die worden gehost op Premium-capaciteiten, dwingt het ook strikter cachebeleid af en kan slechts één sleutel worden toegepast om alle gegevens te versleutelen.


## <a name="how-to-use-customer-managed-keys"></a>Hoe kunt u de door de klant beheerde sleutels gebruiken?
Als u zich wilt aanmelden voor door de klant beheerde Power BI-sleutels, moet uw organisatie contact opnemen met de Microsoft-accountmanager om te controleren of uw organisatie voldoet aan bepaalde groottevereisten die van toepassing zijn voor het inschakelen van CMK.  


## <a name="next-steps"></a>Volgende stappen

De volgende koppelingen bevatten informatie die nuttig kan zijn voor door de klant beheerde sleutels:

* [Uw eigen versleutelingssleutels gebruiken voor Power BI](service-encryption-byok.md)
* [Multi-Geo-ondersteuning voor Power BI Premium configureren](service-admin-premium-multi-geo.md)
* [Hoe capaciteiten functioneren](service-premium-what-is.md#how-capacities-function)
* [Incrementeel vernieuwen:](service-premium-incremental-refresh.md)
