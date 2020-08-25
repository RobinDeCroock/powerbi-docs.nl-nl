---
title: Door de klant beheerde sleutels in Power BI gebruiken
description: Meer informatie over door de klant beheerde sleutels in Power BI gebruiken.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160923"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Door de klant beheerde sleutels in Power BI gebruiken

In Power BI worden data-at-rest en tijdens verwerking versleuteld. In Power BI wordt standaard gebruikgemaakt van door Microsoft beheerde sleutels om uw gegevens te versleutelen. Organisaties kunnen ervoor kiezen om hun eigen sleutels te gebruiken voor het versleutelen van gebruikerscontent at-rest in Power BI, van rapportinstallatiekopieën tot geïmporteerde gegevenssets in Premium-capaciteiten. 

## <a name="why-use-customer-managed-keys"></a>Waarom door de klant beheerde sleutels gebruiken?
Met Power BI door de klant beheerde sleutels (CMK) kunnen organisaties voldoen aan de nalevingsvereisten voor gegevensversleuteling at-rest met hun cloudserviceprovider (in dit geval Microsoft). CMK stelt organisaties in staat hun Power BI-gebruikersinhoud te versleutelen met een sleutel die ze verstrekken en beheren. Het intrekken van een door de klant beheerde sleutel maakt de gebruikerscontent binnen Power BI binnen een uur onleesbaar voor iedereen, ook voor Microsoft. Vergeleken met het BYOK-aanbod dekt CMK ook gebruikersinhoud buiten de Power BI Premium-capaciteiten, dwingt het strengere cachingbeleidsregels af en maakt het standaard BYOK op alle capaciteiten mogelijk. 
 
## <a name="how-to-use-customer-managed-keys"></a>Hoe kunt u de door de klant beheerde sleutels gebruiken?
Om in aanmerking te komen voor door de klant beheerde Power BI-sleutels, moet uw organisatie voldoen aan de groottevereisten. De wereldwijde beheerder van uw organisatie moet een ondersteuningsverzoek indienen bij Microsoft of ze kunnen contact opnemen met de Microsoft-accountmanager van uw organisatie voor meer informatie over het proces.  


## <a name="next-steps"></a>Volgende stappen

De volgende koppelingen bevatten informatie die nuttig kan zijn voor door de klant beheerde sleutels:

* [Uw eigen versleutelingssleutels gebruiken voor Power BI](service-encryption-byok.md)
* [Multi-Geo-ondersteuning voor Power BI Premium configureren](service-admin-premium-multi-geo.md)
* [Hoe capaciteiten functioneren](service-premium-what-is.md#how-capacities-function)
* [Incrementeel vernieuwen:](service-premium-incremental-refresh.md)
