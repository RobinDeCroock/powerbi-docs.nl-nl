---
title: Beperkingen van REST-API's van Power BI
description: 'De Power BI REST-API bevat de volgende beperkingen:'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 97745d93de771d4888dd97717a5e8a8d2d6f5c7c
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265648"
---
# <a name="power-bi-rest-api-limitations"></a>Beperkingen van REST-API's van Power BI  
  
**Voor POSTen van rijen**
  
* Maximaal 75 kolommen
* Maximaal 75 tabellen
* Maximaal 10.000 rijen per POST-rijaanvraag  
* 1\.000.000 rijen per uur toegevoegd per gegevensset  
* Maximaal vijf POST-rijaanvragen in behandeling per gegevensset  
* 120 POST-rijaanvragen per minuut per gegevensset
* 120 POST-rijaanvragen per uur per gegevensset, als een tabel 250.000 rijen of meer bevat
* Maximaal 200.000 rijen opgeslagen per tabel in een FIFO-gegevensset
* Maximaal 5.000.000 rijen opgeslagen per tabel in gegevensset zonder bewaarbeleid  
* 4000 tekens per waarde voor de kolom met tekenreeksen in POST-rijbewerkingen
  
## <a name="see-also"></a>Zie ook

[Azure AD service limits and restrictions](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)  (Limieten en beperkingen voor de Azure AD-service)  
[Overview of Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) (Overzicht van de REST-API voor Power BI)