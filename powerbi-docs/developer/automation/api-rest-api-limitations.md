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
ms.openlocfilehash: de9fd241959b679a0da7926cd6b2254689afbfd2
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747270"
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

* [Servicelimieten en -beperkingen voor Azure AD](/azure/active-directory/active-directory-service-limits-restrictions)   
* [Overview of Power BI REST API](/rest/api/power-bi/) (Overzicht van de REST-API voor Power BI)