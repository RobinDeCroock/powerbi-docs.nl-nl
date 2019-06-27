---
title: Problemen oplossen met geneste waarden die worden geretourneerd als tekst in de Power BI-service
description: Meer informatie over het oplossen van problemen met geneste waarden die worden geconverteerd naar een tekenreeks bij het gebruik van onjuiste privacy-instellingen voor een gegevensbron
author: cpopell
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 6/4/2019
ms.author: gepopell
LocalizationGroup: Reports
ms.openlocfilehash: e30a79796fd4d5538406a85a3297a23b2c09a61a
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751404"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Problemen oplossen met geneste waarden die worden geretourneerd als tekst in de Power BI-service

## <a name="cause"></a>Oorzaak

In het verleden is het voorgekomen dat een Power BI-rapport op de desktop correct werd vernieuwd, maar dat dit in de Power BI-service mislukte met een fout als 'Kan de waarde [Table] niet converteren naar type Table'. Een van de oorzaken van deze fout is dat wanneer door de Data Privacy Firewall (koppeling hier?) een gegevensbron wordt gebufferd, geneste niet-scalaire waarden (zoals tabellen, records, lijsten en functies) automatisch worden geconverteerd naar tekstwaarden (zoals [Table] of [Record]).

Nu de Power BI-service ondersteuning biedt voor het instellen van privacyniveaus (of volledige uitschakeling van de firewall), kunnen dergelijke fouten worden vermeden door in de Power BI-service [de privacy-instellingen voor de gegevensbron in te stellen](https://powerbi.microsoft.com/en-us/blog/privacy-levels-for-cloud-data-sources/) op Niet-privé.

Als door de firewall geneste tabellen, records, lijsten en dergelijke worden gebufferd, worden deze waarden vanaf Power BI van juni niet op de achtergrond geconverteerd naar tekst, maar wordt de volgende fout geproduceerd: 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>Effect op het laden/vernieuwen

Hoewel deze wijziging is aangebracht vanwege het bufferen door de firewall, heeft deze ook invloed op het laden/vernieuwen. Omdat we het buffergedrag van de firewall wilden aanpakken, moesten we ook het gedrag van het laden van geneste tabellen, records en dergelijke in het Power BI-model en het Excel-gegevensmodel in PQ voor Excel wijzigen. Voorheen werden geneste tabellen, records en dergelijke geladen als tekstwaarden (zoals [Table] of [Record]). Nu zullen deze worden behandeld als fouten, die leiden tot een null-waarde in de geladen tabel en een toename van het aantal fouten in de laadresultaten.

Omdat deze fouten alleen tijdens het laden/vernieuwen optreden, worden deze niet weergegeven in de Power Query-editor.

### <a name="before"></a>Vóór

- Laden/vernieuwen zonder fouten
- De geladen tabel bevat [Table], [Record] enzovoort.
 

### <a name="after"></a>Na

- Laden/vernieuwen met fouten
- De geladen tabel bevat null-waarden (in plaats van [Table], [Record] enzovoort.)
 

## <a name="resolution"></a>Oplossing

Gaat u een kolom met niet-scalaire waarden (bijvoorbeeld tabellen, lijsten, records enzovoort) laden?
Zo ja, dan kunt u de fouten vermijden door de kolom te verwijderen.
Als u de kolom niet verwijdert, moet u het oude gedrag kunnen repliceren door een aangepaste kolom toe te voegen en gebruik te maken van logica zoals het volgende voorbeeld:

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

Wordt het probleem gereproduceerd in Power BI Desktop als u alle privacy-instellingen voor uw gegevensbron instelt op Privé?
Zo ja, dan moet u het probleem kunnen oplossen door in Power BI [de privacyinstellingen voor de gegevensbron in te stellen](https://powerbi.microsoft.com/en-us/blog/privacy-levels-for-cloud-data-sources/) op Niet-privé.
