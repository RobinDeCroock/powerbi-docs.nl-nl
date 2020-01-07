---
title: Een rapportparameter doorsturen in een URL voor een gepagineerd rapport - Power BI Report Builder
description: In dit onderwerp wordt beschreven hoe u rapportparameters doorvoert in een rapport door deze in te sluiten in een URL voor een gepagineerd rapport.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: 44e56613a69069351f21aa7d515fc2bb296e6728
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "74128271"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Een rapportparameter doorsturen in een URL voor een gepagineerd rapport in Power BI 

U kunt rapportparameters doorsturen door ze op te nemen in een gepagineerde rapport-URL. Aan alle queryparameters kunnen bijbehorende rapportparameters zijn gekoppeld. Daarom kunt u een queryparameter aan een rapport doorsturen door de bijbehorende rapportparameter door te sturen. U moet het voorvoegsel `rp:` aan de parameternaam toevoegen, zodat Power BI deze naam in de URL kan herkennen. 

Rapportparameters zijn hoofdlettergevoelig en hiervoor worden deze speciale tekens gebruikt: 

- Een spatie in het parameterdeel van de URL wordt vervangen door een plusteken (+).  Bijvoorbeeld: 

    ```rp:Holiday=Christmas+Day```

- Een puntkomma in een deel van de tekenreeks wordt vervangen door de tekens `%3A`.

In browsers moet de juiste URL-versleuteling automatisch worden uitgevoerd. U hoeft zelf geen tekens handmatig te versleutelen. 

Gebruik de volgende syntaxis om een rapportparameter in een URL in te stellen: 

```
rp:parameter=value
```

Als u bijvoorbeeld de twee parameters Verkoper en Staat, die in een rapport in uw Mijn werkruimte zijn gedefinieerd, wilt opgeven, gebruikt u de volgende URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Als u twee dezelfde parameters die in een rapport in een app zijn gedefinieerd, wilt opgeven, gebruikt u de volgende URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Gebruik de volgende syntaxis om de waarde null voor een parameter door te sturen: 

```
parameter:isnull=true
```

Bijvoorbeeld:

```
rp:SalesOrderNumber:isnull=true
```

Als u een Booleaanse waarde wilt doorsturen, gebruikt u 0 voor onwaar en 1 voor waar. Als u een Float-waarde wilt doorsturen, neemt u het decimale scheidingsteken van de landinstellingen van de server op.

> [!NOTE]
> Als uw rapport een rapportparameter bevat die een standaardwaarde heeft en de waarde van de eigenschap **Vragen** **Onwaar** is (dat wil zeggen dat de eigenschap **Vragen aan gebruiker** niet is geselecteerd in Report manager), kunt u geen waarde voor die rapportparameter in een URL doorsturen. Dit biedt beheerders de optie om te voorkomen dat eindgebruikers de waarden van bepaalde rapportparameters toevoegen of aanpassen.

## <a name="additional-examples"></a>Aanvullende voorbeelden 

Het volgende URL-voorbeeld bevat de parameter Verkoper, die meerdere waarden heeft. De indeling voor een parameter met meerdere waarden is de parameternaam voor elke waarde te herhalen. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

In het volgende URL-voorbeeld wordt één parameter, SellStartDate, met de waarde 7/1/2005 doorgestuurd voor een systeemeigen rapportserver.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Volgende stappen

- [URL-parameters in gepagineerde rapporten in Power BI](report-builder-url-parameters.md)
- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
