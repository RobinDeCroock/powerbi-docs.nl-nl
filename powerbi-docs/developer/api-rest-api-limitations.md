---
title: Beperkingen van REST-API's van Power BI
description: 'De Power BI REST-API bevat de volgende beperkingen:'
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385138"
---
# <a name="power-bi-rest-api-limitations"></a>Beperkingen van REST-API's van Power BI  
  
**Voor POSTen van rijen**
  
* Maximaal 75 kolommen
* Maximaal 75 tabellen
* Maximaal 10.000 rijen per POST-rijaanvraag  
* 1.000.000 rijen per uur toegevoegd per gegevensset  
* Maximaal vijf POST-rijaanvragen in behandeling per gegevensset  
* 120 POST-rijaanvragen per minuut per gegevensset
* 120 POST-rijaanvragen per uur per gegevensset, als een tabel 250.000 rijen of meer bevat
* Maximaal 200.000 rijen opgeslagen per tabel in een FIFO-gegevensset
* Maximaal 5.000.000 rijen opgeslagen per tabel in gegevensset zonder bewaarbeleid  
* 4000 tekens per waarde voor de kolom met tekenreeksen in POST-rijbewerkingen
  
## <a name="see-also"></a>Zie ook

[Azure AD service limits and restrictions](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)  (Limieten en beperkingen voor de Azure AD-service)  
[Overview of Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) (Overzicht van de REST-API voor Power BI)