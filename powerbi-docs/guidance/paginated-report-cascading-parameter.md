---
title: Trapsgewijze parameters in gepagineerde rapporten gebruiken
description: Richt lijnen voor het ontwerpen van gepagineerde rapporten met behulp van trapsgewijze parameters.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: f239622d8b6012913298212790f7f9aa8c3115a5
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197651"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>Trapsgewijze parameters in gepagineerde rapporten gebruiken

Dit artikel is bedoeld voor u wanneer u als auteur [gepagineerde rapporten](../paginated-reports/paginated-reports-report-builder-power-bi.md) in Power BI gaat ontwerpen. Het bevat scenario's voor het ontwerpen van trapsgewijze parameters. Trapsgewijze parameters zijn rapportparameters met afhankelijkheden. Wanneer een rapportgebruiker een parameterwaarde (of waarden) selecteert, wordt deze gebruikt om de beschikbare waarden voor een andere parameter in te stellen.

> [!NOTE]
> Een inleiding tot trapsgewijze parameters en hoe u deze kunt configureren, wordt niet behandeld in dit artikel. Als u niet volledig bekend bent met trapsgewijze parameters, raden we u aan eerst [trapsgewijze parameters toe te voegen aan een rapport (Power BI Report Builder en SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs).

## <a name="design-scenarios"></a>Ontwerpscenario's

Er zijn twee ontwerpscenario's voor het gebruik van trapsgewijze parameters. Ze kunnen effectief worden gebruikt voor het volgende:

- _Grote sets_ items filteren
- _Relevante_ items weergeven

### <a name="example-database"></a>Voorbeeld database

De voorbeelden die in dit artikel worden weergegeven, zijn gebaseerd op een Azure SQL Database. De database registreert verkoopbewerkingen en bevat verschillende tabellen waarin wederverkopers, producten en verkooporders worden opgeslagen.

Een tabel met de naam **Reseller** slaat een record voor elke wederverkoper op en bevat vele duizenden records. De tabel **Reseller** bevat de volgende kolommen:

- ResellerCode (geheel getal)
- ResellerName
- Land-regio
- Staat-Provincie
- Plaats
- PostalCode

Er is ook een tabel met de naam **Verkoop**. Hier worden Verkooporder-records opgeslagen en er is een refererende-sleutelrelatie met de **Reseller**-tabel in de kolom **ResellerCode**.

### <a name="example-requirement"></a>Voorbeeld vereiste

Er is een vereiste voor het ontwikkelen van een profielrapport voor wederverkopers. Het rapport moet zijn ontworpen voor het weergeven van informatie voor één reseller. Het is niet gebruikelijk om de gebruiker van het rapport een reseller-code te laten invoeren, omdat ze deze zelden onthouden.

## <a name="filter-large-sets-of-items"></a>Grote sets items filteren

Laten we eens kijken naar drie voorbeelden om u te helpen grote sets beschikbare items te beperken, zoals wederverkopers. Dit zijn:

- [Filteren op gerelateerde kolommen](#filter-by-related-columns)
- [Filteren op een groepeerkolom](#filter-by-a-grouping-column)
- [Filteren op zoekpatroon](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>Filteren op gerelateerde kolommen

In dit voorbeeld communiceert de gebruiker van het rapport met vijf rapportparameters. Ze moeten land/regio, staats provincie, plaats en vervolgens postcode selecteren. Een laatste parameter bevat vervolgens een lijst met wederverkopers die zich op die geografische locatie bevinden.

![Schermopname van door Power BI gepagineerde rapportparameters die zijn gefilterd op verwante kolom.](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

U kunt de trapsgewijze parameters als volgt ontwikkelen:

1. Maak de vijf rapportparameters, geordend in de juiste volgorde.
2. Maak de **CountryRegion**-gegevensset die de waarden van de land/regio ophaalt, met behulp van de volgende query-instructie:

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. Maak de **StateProvince**-gegevensset die afzonderlijke waarden voor de staat-provincie voor het geselecteerde land-regio ophaalt met de volgende query-instructie:

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. Maak de **City**-gegevensset die de waarden voor afzonderlijke steden voor het geselecteerde land/regio en de staat-provincie gebruikt, met behulp van de volgende query-instructie:

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. Ga door met dit patroon om de **PostalCode**-gegevensset te maken.
6. Maak de **Reseller**-gegevensset om alle resellers voor de geselecteerde geografische waarden op te halen met behulp van de volgende query-instructie:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. Voor elke gegevensset, met uitzondering van de eerste, wijst u de query-parameters toe aan de bijbehorende rapportparameters.

> [!NOTE]
> Alle query-parameters (voorafgegaan door het @-teken) die in deze voorbeelden worden weer gegeven, kunnen worden ingesloten in SELECT-instructies of doorgegeven aan opgeslagen procedures.
>
> Opgeslagen procedures zijn over het algemeen een betere ontwerpbenadering. De reden hiervoor is dat de query-plannen worden opgeslagen in de cache om sneller te kunnen worden uitgevoerd. In dat geval kunt u zo nodig meer geavanceerde logica ontwikkelen. Ze worden momenteel echter niet ondersteund voor gateway-relationele gegevensbronnen, dit zijn SQL Server, Oracle en Teradata.
>
> Ten slotte moet u er altijd voor zorgen dat er geschikte indexen bestaan om het efficiënt ophalen van gegevens te ondersteunen. Als dat niet het geval is, kunnen de rapportparameters slechts langzaam worden gevuld. De database kan worden overbelast. Zie [SQL Server index-architectuur en ontwerphandleiding](/sql/relational-databases/sql-server-index-design-guide) voor meer informatie over het indexeren van SQL Server.

### <a name="filter-by-a-grouping-column"></a>Filteren op een groepeerkolom

In dit voorbeeld communiceert de gebruiker van het rapport met een rapportparameter om de eerste letter van de reseller te selecteren. In een tweede parameter worden vervolgens de resellers weergegeven wanneer de naam begint met de geselecteerde letter.

![Schermopname van door Power BI gepagineerde rapportparameters die zijn gefilterd op groeperingskolom.](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

U kunt de trapsgewijze parameters als volgt ontwikkelen:

1. Maak de rapportparameters **ReportGroup** en **Reseller**, geordend in de juiste volgorde.
2. Maak de **ReportGroup**-gegevensset om de eerste letters op te halen die door alle wederverkopers worden gebruikt, met behulp van de volgende query-instructie:

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. Maak de **Reseller**-gegevensset om alle resellers die beginnen met de geselecteerde letter, op te halen met behulp van de volgende query-instructie:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. Wijs de query-parameter van de **Reseller**-gegevensset toe aan de bijbehorende rapportparameter.

Het is efficiënter om de kolomgroepering toe te voegen aan de tabel **Reseller**. Wanneer persistent en geïndexeerd, levert dit het beste resultaat op. Zie [Berekende kolommen opgeven in een tabel](/sql/relational-databases/tables/specify-computed-columns-in-a-table) voor meer informatie.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

Deze techniek kan nog meer mogelijkheden leveren. Bekijk het volgende script waarmee een nieuwe groepeerkolom wordt toegevoegd om resellers te filteren op _vooraf gedefinieerde kant-en-klare brieven_. Er wordt ook een index gemaakt voor het efficiënt ophalen van de gegevens die vereist zijn voor de rapportparameters.

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>Filteren op zoekpatroon

In dit voorbeeld communiceert de gebruiker van het rapport met een rapportparameter om een zoekpatroon te selecteren. In een tweede parameter worden vervolgens de resellers weergegeven wanneer de naam het patroon bevat.

![Schermopname van door Power BI gepagineerde rapportparameters die zijn gefilterd op zoekpatroon.](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

U kunt de trapsgewijze parameters als volgt ontwikkelen:

1. Maak de rapportparameters **Search** en **Reseller**, geordend in de juiste volgorde.
2. Maak de **Reseller**-gegevensset om alle resellers die de zoektekst bevatten, op te halen met behulp van de volgende query-instructie:

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. Wijs de query-parameter van de **Reseller**-gegevensset toe aan de bijbehorende rapportparameter.

> [!TIP]
> U kunt dit ontwerp verbeteren zodat u meer controle hebt over uw rapportgebruikers. Hiermee kunnen ze hun eigen patroon-vergelijkingswaarde definiëren. Met de zoekwaarde "rood%" wordt bijvoorbeeld gefilterd op resellers met namen die _beginnen_ met de tekens "rood".
>
> Zie [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql#using-the--wildcard-character) voor meer informatie.

Hier kunt u de rapportgebruikers de mogelijkheid geven hun eigen patroon te definiëren.

```sql
WHERE
  [ResellerName] LIKE @Search
```

Veel niet-database-professionals zijn echter niet bekend met het percentage(%)-Jokerteken. In plaats daarvan zijn ze bekend met het sterretje (*). Door de component WHERE te wijzigen, kunt u hen toestaan dit teken te gebruiken.

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>Relevante items weergeven

In dit scenario kunt u feitelijke gegevens gebruiken om de beschikbare waarden te beperken. Rapportgebruikers worden weergegeven met items waarin de activiteit is vastgelegd.

In dit voorbeeld communiceert de gebruiker van het rapport met drie rapportparameters. De eerste twee stellen een datumbereik van de verkooporderdatums in. De derde parameter bevat dan een lijst met wederverkopers waar orders zijn gemaakt tijdens die periode.

![Schermopname van door Power BI gepagineerde rapportparameters die drie rapportparameters bevatten: Startdatum van de order, Einddatum van de order en Reseller.](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

U kunt de trapsgewijze parameters als volgt ontwikkelen:

1. Maak de rapportparameters **OrderDateStart**, **OrderDateEnd** en **Reseller**, geordend in de juiste volgorde.
2. Maak de **Reseller**-gegevensset om alle resellers die in de gespecificeerde periode orders hebben aangemaakt, op te halen met behulp van de volgende query-instructie:

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>Aanbevelingen

U wordt aangeraden uw rapporten zo mogelijk te ontwerpen met parameters. Dit komt doordat ze:

- Een intuïtieve en nuttige ervaring bieden voor uw rapportgebruikers
- Efficiënt zijn, omdat ze kleinere sets beschikbare waarden ophalen

Zorg ervoor dat u uw gegevensbronnen optimaliseert door:

- Waar mogelijk opgeslagen procedures gebruiken
- Juiste indexen toevoegen voor het efficiënt ophalen van gegevens
- Kolomwaarden materialiseren—en zelfs-rijen—om te voorkomen dat er dure query-tijd evaluaties worden gedaan

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Rapportparameters in Power BI Report Builder](../paginated-reports/report-builder-parameters.md)
- [Trapsgewijze parameters toevoegen aan een rapport (Power BI Report Builder en SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com)
