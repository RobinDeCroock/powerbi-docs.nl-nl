---
title: Incrementeel vernieuwen in Power BI Premium
description: Leer hoe u zeer grote gegevenssets kunt inschakelen in de Power BI Premium-service.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: davidi
LocalizationGroup: Premium
ms.openlocfilehash: cc2b005ef72700891a603162a281fbba23aa5120
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699286"
---
# <a name="incremental-refresh-in-power-bi-premium"></a>Incrementeel vernieuwen in Power BI Premium

Incrementele vernieuwing maakt zeer grote gegevenssets in de Power BI Premium-service mogelijk, met de volgende voordelen:

> [!div class="checklist"]
> * **Vernieuwen gaat sneller**: alleen gegevens die zijn gewijzigd, hoeven te worden vernieuwd. Vernieuw bijvoorbeeld alleen de laatste vijf dagen van een gegevensset van tien jaar.
> * **Vernieuwen is betrouwbaarder**: het is niet meer nodig om langdurige verbindingen met vluchtige bronsystemen te onderhouden.
> * **Verbruik van resources is lager**: als er minder gegevens zijn om te vernieuwen, wordt het algemene verbruik van geheugen en andere resources verlaagd.

## <a name="configure-incremental-refresh"></a>Incrementeel vernieuwen configureren

Beleid voor incrementele vernieuwing wordt gedefinieerd in Power BI Desktop en toegepast zodra het beleid in de Power BI-service is gepubliceerd.

Begin door incrementele vernieuwingen in de **preview-functies** in te schakelen.

![Opties > Preview-functies](media/service-premium-incremental-refresh/preview-features.png)

### <a name="filter-large-datasets-in-power-bi-desktop"></a>Grote gegevenssets filteren in Power BI Desktop

Grote gegevenssets met potentieel miljarden rijen passen mogelijk niet in een Power BI Desktop-model omdat het PBIX-bestand meestal is beperkt door de geheugenresources die beschikbaar zijn op de desktop-pc. Dergelijke gegevenssets worden daarom doorgaans gefilterd tijdens de import. Er wordt op deze manier gefilterd, of er nu gebruik wordt gemaakt van incrementeel vernieuwen of niet. Bij incrementeel vernieuwen filtert u op basis van de datum-/tijdparameters van Power Query.

#### <a name="rangestart-and-rangeend-parameters"></a>De parameters RangeStart en RangeEnd

Als u gebruik wilt maken van incrementele vernieuwing, worden gegevenssets gefilterd op basis van de datum- en tijdparameters van Power Query in combinatie met de gereserveerde, hoofdlettergevoelige namen **RangeStart** en **RangeEnd**. Deze parameters worden gebruikt om de gegevens die naar Power BI Desktop te worden geïmporteerd te filteren. Ze worden ook gebruikt om de gegevens dynamisch te partitioneren in bereiken nadat ze in de Power BI-service zijn gepubliceerd. De parameterwaarden worden vervangen door de service om op elke partitie te kunnen filteren. U hoeft ze niet in te stellen bij de gegevenssetinstellingen in de service. Na publicatie worden de parameterwaarden automatisch door de Power BI-service overschreven.

Selecteer **Parameters beheren** in de Power Query-editor om parameters met standaardwaarden te definiëren.

![Parameters beheren](media/service-premium-incremental-refresh/manage-parameters.png)

Wanneer u de parameters hebt gedefinieerd, kunt u het filter toepassen door de menuoptie **Aangepast filter** voor een kolom te selecteren.

![Aangepast filter](media/service-premium-incremental-refresh/custom-filter.png)

Zorg ervoor dat rijen worden gefilterd waarbij de kolomwaarde *na of gelijk is aan* **RangeStart** en *voor* **RangeEnd**. Andere filtercombinaties kunnen ertoe leiden dat rijen dubbel worden geteld.

![Rijen filteren](media/service-premium-incremental-refresh/filter-rows.png)

> [!IMPORTANT]
> Controleer of de query's een isgelijkteken (=) bevatten voor **RangeStart** of **RangeEnd**, maar niet voor beide. Als het isgelijkteken (=) voor beide parameters bestaat, kan een rij voldoen aan de voorwaarden voor twee partities, wat kan leiden tot dubbele gegevens in het model. Bijvoorbeeld,  
> \#"Gefilterde rijen" = Table.SelectRows(dbo_Fact, each [OrderDate] **>= RangeStart** and [OrderDate] **<= RangeEnd**) kan leiden tot dubbele gegevens.

> [!TIP]
> Hoewel het gegevenstype van de parameters datum/tijd moet zijn, is het wel mogelijk om ze te converteren zodat ze voldoen aan de vereisten van de gegevensbron. De volgende Power Query-functie converteert bijvoorbeeld een datum/tijd-waarde zodat deze overeenkomt met een surrogaatsleutel voor gehele getallen in de indeling *jjjjmmdd*, die vaker wordt gebruikt voor gegevenswarehouses. De functie kan worden aangeroepen door de filterstap.
>
> `(x as datetime) => Date.Year(x)*10000 + Date.Month(x)*100 + Date.Day(x)`

Selecteer **Sluiten en toepassen** in de Power Query Editor. U moet een subset van de gegevensset in Power BI Desktop hebben.

#### <a name="filter-date-column-updates"></a>Filteren op updates in de datumkolom

Het gegevenskolomfilter wordt in de Power BI-service gebruikt om gegevens dynamisch de partitioneren in bereiken. Incrementeel vernieuwen is niet bedoeld ter ondersteuning van gevallen waarin de gefilterde datumkolom in het bronsysteem wordt bijgewerkt. Een update wordt beschouwd als een invoeging en een verwijdering en niet als een echte update. Als de verwijdering zich voordoet in het historische bereik en niet in het incrementele bereik, wordt het niet opgepikt. Dit kan leiden tot mislukte pogingen de gegevens te vernieuwen vanwege partitiesleutelconflicten.

#### <a name="query-folding"></a>Query's vouwen

Het is belangrijk dat de partitiefilters naar het bronsysteem wordt gepusht als er query's worden ingediend voor vernieuwingsbewerkingen. Het filteren naar beneden duwen (push down) houdt in dat de gegevensbron ondersteuning moet bieden aan het 'vouwen van query's'. De meeste gegevensbronnen die ondersteuning bieden voor SQL-query's, ondersteunen het vouwen van query’s. Voor gegevensbronnen zoals platte bestanden, blobs en web- en OData-feeds geldt dat echter doorgaans niet. In gevallen waarin het filter niet wordt ondersteund door de back-end van de gegevensbron, kan deze niet naar beneden worden gepusht. In dergelijke gevallen biedt de mashup-engine compensatie door het filter lokaal toe te passen, waarvoor het nodig kan zijn de volledige gegevensset uit de gegevensbron op te halen. Hierdoor kan incrementeel vernieuwen traag worden en kan het proces zonder resources komen te zitten, zowel in de Power BI-service als in de on-premises gegevensgateway, indien gebruikt.

Gezien de diverse ondersteuningsniveaus voor het vouwen van query's voor elke gegevensbron, wordt u aangeraden te controleren of de filterlogica in de bronquery's is opgenomen. Als u dit eenvoudiger wilt maken, kunt u ook proberen met Power BI Desktop de controle uit te voeren. Als er geen controle kan worden uitgevoerd, wordt er in het dialoogvenster Incrementeel vernieuwen een waarschuwing weergegeven bij het definiëren van het beleid voor incrementeel vernieuwen. Gegevensbronnen op basis van SQL, zoals SQL Oracle en Teradata, kunnen gebruikmaken van deze waarschuwing. Mogelijk kunnen andere gegevensbronnen geen controle uitvoeren zonder query's bij te houden. Als de controle niet met Power BI Desktop kan worden uitgevoerd, wordt de volgende waarschuwing weergegeven.

 ![Query's vouwen](media/service-premium-incremental-refresh/query-folding.png)

### <a name="define-the-refresh-policy"></a>Het vernieuwingsbeleid definiëren

Incrementele vernieuwing is beschikbaar in het contextmenu voor tabellen, met uitzondering van liveverbindingsmodellen.

![Beleid vernieuwen](media/service-premium-incremental-refresh/refresh-policy.png)

#### <a name="incremental-refresh-dialog"></a>Het dialoogvenster Incrementeel vernieuwen

Het dialoogvenster Incrementele vernieuwing wordt weergegeven. Gebruik de wisselknop om het dialoogvenster in te schakelen.

![Details vernieuwen](media/service-premium-incremental-refresh/refresh-details.png)

> [!NOTE]
> Als de Power Query-expressie voor de tabel niet naar de parameters met gereserveerde namen verwijst, wordt de wisselknop uitgeschakeld.

In de koptekst wordt het volgende uitgelegd:

- Incrementele vernieuwing wordt alleen ondersteund voor werkruimten met Premium-capaciteit. Vernieuwingsbeleid wordt gedefinieerd in Power BI Desktop; het wordt toegepast door vernieuwingsbewerkingen in de service.

- Als u het PBIX-bestand met een beleid voor incrementele vernieuwing uit de Power BI-service kunt downloaden, kan het niet worden geopend in Power BI Desktop. Dit wordt mogelijk in de toekomst wel ondersteund, maar vergeet niet dat deze gegevenssets zo groot kunnen worden dat het niet praktisch is om deze te downloaden en op een gewone desktop-pc te openen.

#### <a name="refresh-ranges"></a>Bereiken vernieuwen

In het volgende voorbeeld wordt vernieuwingsbeleid gedefinieerd voor het opslaan van in totaal vijf jaar aan gegevens plus de gegevens voor het huidige jaar tot aan de huidige datum, met incrementele vernieuwing van tien dagen aan gegevens. Met de eerste vernieuwingsbewerking worden historische gegevens geladen. De daaropvolgende vernieuwingen zijn incrementeel. Hiermee worden (indien gepland om dagelijks te worden uitgevoerd) de volgende bewerkingen uitgevoerd:

- Voeg een nieuwe dag aan gegevens toe.

- Vernieuw tien dagen tot aan de huidige datum.

- Verwijder kalenderjaren die ouder zijn dan vijf jaar voorafgaand aan de huidige datum. Als de huidige datum bijvoorbeeld 1 januari 2019 is, wordt het jaar 2013 verwijderd.

De eerste vernieuwing in de Power BI-service kan langer duren omdat alle vijf volledige kalenderjaren moeten worden geïmporteerd. Daarop volgende vernieuwingen kunnen in een fractie van die tijd worden voltooid.

![Bereiken vernieuwen](media/service-premium-incremental-refresh/refresh-ranges.png)

> [!NOTE]
> Definitie van deze bereiken is wellicht alles wat u nodig hebt. In dat geval kunt u meteen doorgaan naar de onderstaande publicatiestap. De extra vervolgkeuzelijsten zijn bedoeld voor geavanceerde functies.

### <a name="advanced-policy-options"></a>Geavanceerde beleidsopties

#### <a name="detect-data-changes"></a>Gegevenswijzigingen detecteren

Incrementele vernieuwing van tien dagen is veel efficiënter dan volledige vernieuwing van vijf jaar. Het kan echter nog beter. Als u het selectievakje **Gegevenswijzigingen detecteren** inschakelt, kunt u een datum/tijd-kolom selecteren voor de identificatie en die alleen wordt vernieuwd als er gegevens zijn gewijzigd. Hierbij wordt ervan uitgegaan dat een dergelijke kolom in het bronsysteem bestaat, wat gebruikelijk is voor controledoeleinden. **Dit mag niet dezelfde kolom zijn die wordt gebruikt voor het partitioneren van de gegevens met de parameters RangeStart/RangeEnd.** De maximumwaarde van deze kolom wordt geëvalueerd voor elke periode in het incrementele bereik. Als deze nog niet is gewijzigd sinds de laatste vernieuwing, hoeft u de periode niet te vernieuwen. In het voorbeeld kan hiermee het aantal dagen dat wordt vernieuwd nog eens verder worden beperkt van tien tot ongeveer twee dagen.

![Wijzigingen detecteren](media/service-premium-incremental-refresh/detect-changes.png)

> [!TIP]
> Voor het huidige ontwerp moet de kolom die gegevenswijzigingen detecteert persistent zijn en in het cachegeheugen worden geplaatst. U kunt overwegen een van de volgende technieken te gebruiken om de kardinaliteit en het geheugenverbruik te beperken.
>
> Behoud alleen de maximumwaarde van deze kolom op het moment van de vernieuwing, bijvoorbeeld met behulp van een Power Query-functie.
>
> Beperk de nauwkeurigheid naar een niveau dat acceptabel is gezien uw vereisten voor de vernieuwingsfrequentie.
>
> We willen op een later tijdstip de definitie van aangepaste query's voor gegevenswijzigingdetectie toestaan. Dit kan worden gebruikt om te voorkomen dat de kolomwaarde helemaal wordt behouden.

#### <a name="only-refresh-complete-periods"></a>Alleen volledige perioden vernieuwen

Stel dat u hebt gepland dat vernieuwing elke ochtend om 4:00 uur wordt uitgevoerd. Als gegevens in die vier uur in het bronsysteem worden weergegeven, wilt u mogelijk dat hier geen rekening mee wordt gehouden. Some zakelijke metrische gegevens, zoals vaten per dag in de olie- en gasindustrie, zijn niet logisch bij gedeeltelijke dagen.

Een ander voorbeeld is het vernieuwen van gegevens in een financieel systeem waar gegevens voor de vorige maand op de 12e kalenderdag van de maand worden goedgekeurd. U kunt het incrementele bereik instellen op 1 maand en de vernieuwing plannen op de twaalfde dag van de maand. Als u deze optie hebt ingeschakeld, worden bijvoorbeeld de gegevens van januari op 12 februari vernieuwd.

![Volledige perioden](media/service-premium-incremental-refresh/complete-periods.png)

> [!NOTE]
> Vernieuwingsbewerkingen in de service worden in UTC-tijd uitgevoerd. Dit kan invloed hebben op de ingangsdatum en op volledige perioden. We zullen de mogelijkheid om de ingangsdatum voor een vernieuwingsbewerking binnenkort toevoegen.

## <a name="publish-to-the-service"></a>Publiceren naar de service

Aangezien incrementele vernieuwing alleen een Premium-functie is, kunt u in het dialoogvenster Publiceren alleen werkruimten selecteren bij de Premium-capaciteit.

![Publiceren naar de service](media/service-premium-incremental-refresh/publish.png)

U kunt het model nu vernieuwen. De eerste vernieuwing kan langer duren omdat de historische gegevens moeten worden geïmporteerd. Daarop volgende vernieuwingen kunnen veel sneller worden uitgevoerd omdat hiervoor incrementele vernieuwing wordt gebruikt.

## <a name="query-timeouts"></a>Time-outs voor query’s

In het artikel [Problemen met vernieuwing oplossen](https://docs.microsoft.com/power-bi/refresh-troubleshooting-refresh-scenarios) wordt uitgelegd dat vernieuwingsbewerkingen in de Power BI-service onderhevig zijn aan time-outs. Voor query's kan ook de standaardtime-out voor de gegevensbron worden ingesteld. De meeste relationele bronnen staan het overschrijven van time-outs in de M-expressie toe. De onderstaande expressie gebruikt bijvoorbeeld de [SQL Server-functie voor toegang tot gegevens](https://msdn.microsoft.com/query-bi/m/sql-database) om dit op twee uur in te stellen. Elke periode die door de beleidsbereiken wordt gedefinieerd, stuurt een query in waarbij rekening wordt gehouden met de time-outinstelling voor de opdracht.

```powerquery-m
let
    Source = Sql.Database("myserver.database.windows.net", "AdventureWorks", [CommandTimeout=#duration(0, 2, 0, 0)]),
    dbo_Fact = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
    #"Filtered Rows" = Table.SelectRows(dbo_Fact, each [OrderDate] >= RangeStart and [OrderDate] < RangeEnd)
in
    #"Filtered Rows"
```

## <a name="limitations"></a>Beperkingen

Op dit moment wordt incrementeel vernieuwen voor [samengestelde modellen](desktop-composite-models.md) alleen ondersteund voor gegevensbronnen van SQL Server, Azure SQL Database, SQL Data Warehouse, Oracle en Teradata.

