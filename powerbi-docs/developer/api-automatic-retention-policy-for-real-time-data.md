---
title: Power BI-API's die gebruikmaken van automatisch bewaarbeleid voor realtime-gegevens
description: Meer informatie over het automatisch bewaarbeleid in de Power BI-service
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 07726535246f8b115402373c315062151177d27c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61347304"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Automatisch bewaarbeleid voor realtime-gegevens

Het automatische bewaarbeleid in de Power BI-service is een querytekenreeksparameter waarmee een standaardbewaarbeleid wordt ingeschakeld om automatisch oude gegevens op te ruimen, terwijl er een constante stroom nieuwe gegevens in uw dashboard binnenkomt. Het eerste bewaarbeleid heet *first in first out (FIFO)* . Wanneer dit beleid is ingeschakeld, worden de gegevens verzameld in een tabel totdat er 200.000 rijen zijn gevuld. Nadat er meer dan 200.000 rijen met gegevens zijn gevuld, worden de oudste rijen verwijderd uit de gegevensset. Zo worden er 200.000 tot 210.000 rijen bewaard met alleen de meest recente gegevens.  
  
<center>

![bewaarbeleid](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Bewaarbeleid wordt ingeschakeld wanneer u uw eerste gegevenssets maakt. Het enige wat u moet doen is de queryparameter 'standaardbewaarbeleid' toevoegen aan uw aanroep NA gegevenssets en deze gelijkstellen aan *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}