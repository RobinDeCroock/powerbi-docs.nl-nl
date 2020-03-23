---
title: Power BI-API's die gebruikmaken van automatisch bewaarbeleid voor realtime-gegevens
description: Meer informatie over het automatisch bewaarbeleid in de Power BI-service
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 3ac4c28b3f07cb1a19e241089b54ee4594a7a7dd
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79378289"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatisch bewaarbeleid voor realtime-gegevens

Het automatische bewaarbeleid in de Power BI-service is een querytekenreeksparameter waarmee een standaardbewaarbeleid wordt ingeschakeld om automatisch oude gegevens op te ruimen, terwijl er een constante stroom nieuwe gegevens in uw dashboard binnenkomt. Het eerste bewaarbeleid heet *first in first out (FIFO)* . Wanneer dit beleid is ingeschakeld, worden de gegevens verzameld in een tabel totdat er 200.000 rijen zijn gevuld. Nadat er meer dan 200.000 rijen met gegevens zijn gevuld, worden de oudste rijen verwijderd uit de gegevensset. Zo worden er 200.000 tot 210.000 rijen bewaard met alleen de meest recente gegevens.  
  
<center>

![bewaarbeleid](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Bewaarbeleid wordt ingeschakeld wanneer u uw eerste gegevenssets maakt. Het enige wat u moet doen is de queryparameter 'standaardbewaarbeleid' toevoegen aan uw aanroep NA gegevenssets en deze gelijkstellen aan *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}