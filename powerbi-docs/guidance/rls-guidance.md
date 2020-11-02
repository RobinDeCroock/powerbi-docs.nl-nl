---
title: Richtlijnen voor beveiliging op rijniveau (RLS) in Power BI Desktop
description: Richtlijnen voor het afdwingen van beveiliging op rijniveau (RLS) in uw gegevensmodellen met Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 644e4499a335f18febadf33c371bd15e01499701
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349616"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Richtlijnen voor beveiliging op rijniveau (RLS) in Power BI Desktop

Dit artikel is geschreven voor iedereen die gegevensmodellen maakt met Power BI Desktop. Er worden goede ontwerpprocedures beschreven voor het afdwingen van beveiliging op rijniveau (RLS) in uw gegevensmodellen.

Het is belangrijk dat u de werking van _tabelrijen_ van RLS-filters begrijpt. Deze kunnen niet worden geconfigureerd om de toegang tot modelobjecten, zoals tabellen, kolommen of maateenheden, te beperken.

> [!NOTE]
> In dit artikel wordt niet beschreven wat beveiliging op rijniveau is of hoe u deze kunt instellen. Zie [Gegevenstoegang met beveiliging op rijniveau (RLS) beperken voor Power BI Desktop](../create-reports/desktop-rls.md) voor meer informatie.
>
> Ook het afdwingen van beveiliging op rijniveau in live-verbindingen met extern gehoste modellen met Azure Analysis Services of SQL Server Analysis Services komt niet aan de orde in dit artikel. In die gevallen wordt beveiliging op rijniveau afgedwongen door Analysis Services. Als Power BI verbinding maakt met behulp van eenmalige aanmelding (SSO), dwingt Analysis Services beveiliging op rijniveau af (tenzij het account beheerdersbevoegdheden heeft).

## <a name="create-roles"></a>Rollen maken

Het is mogelijk om meerdere rollen te maken. Als u overweegt de machtigingsvereisten voor één rapportgebruiker te maken, dient u bij voorkeur één rol maken waarmee alle machtigingen worden verleend, in plaats van een ontwerp waarbij een rapportgebruiker lid is van meerdere rollen. De reden hiervoor is dat een rapportgebruiker kan zijn toegewezen aan meerdere rollen. Zo kunnen ze rechtstreeks toegang krijgen door gebruik te maken van hun gebruikersaccount, of indirect door het lidmaatschap van een beveiligingsgroep. Toewijzingen van meerdere rollen kunnen leiden tot onverwachte resultaten.

Wanneer een rapportgebruiker aan meerdere rollen wordt toegewezen, worden de filters voor beveiliging op rijniveau additief. Dit betekent dat rapportgebruikers tabelrijen kunnen zien die de combinatie van die filters vertegenwoordigen. In sommige scenario's is het niet mogelijk om te garanderen dat een rapportgebruiker geen rijen in een tabel ziet. In tegenstelling tot machtigingen die worden toegepast op SQL Server-databaseobjecten (en andere machtigingsmodellen), is het principe 'eenmaal geweigerd, altijd geweigerd ' niet van toepassing.

Overweeg een model met twee rollen: De eerste rol, met de naam **Workers** (Medewerkers), beperkt de toegang tot alle tabelrijen van **Payroll** (Salarisadministratie) met behulp van de volgende regelexpressie:

```dax
FALSE()
```

> [!NOTE]
> Een regel retourneert geen tabelrijen als de expressie wordt geëvalueerd als **onwaar** .

Een tweede rol, met de naam **Managers** , geeft toegang tot alle tabelrijen van **Payroll** met behulp van de volgende regelexpressie:

```dax
TRUE()
```

Let op: Als een rapportgebruiker aan beide rollen wordt toegewezen, ziet deze alle rijen van de tabel **Payroll** (Salarisadministratie).

## <a name="optimize-rls"></a>Beveiliging op rijniveau optimaliseren

Beveiliging op rijniveau werkt door automatisch filters toe te passen op elke DAX-query. Deze filters kunnen een negatieve invloed hebben op de queryprestaties. Een efficiënte beveiliging op rijniveau staat of valt dus met een goed modelontwerp. Het is belangrijk om de richtlijnen voor het ontwerpen van een model te volgen, zoals beschreven in de volgende artikelen:

- [Meer informatie over stervormige schema's en het belang daarvan voor Power BI](star-schema.md)
- Alle artikelen over richtlijnen voor relaties vindt u in [Documentatie voor Power BI-richtlijnen](./index.yml)

Over het algemeen is het vaak efficiënter om filters voor beveiliging op rijniveau af te dwingen voor dimensietabellen dan voor feitentabellen. Zorg ook voor goed ontworpen relaties zodat filters voor beveiliging op rijniveau worden doorgegeven aan andere modeltabellen. Vermijd daarom het gebruik van de DAX-functie [LOOKUPVALUE](/dax/lookupvalue-function-dax) als hetzelfde resultaat kan worden verkregen met modelrelaties.

Wanneer beveiliging op rijniveau wordt afgedwongen in DirectQuery-tabellen en er relaties zijn met andere DirectQuery-tabellen, moet u ervoor zorgen dat u de brondatabase optimaliseert. Dit kan inhouden dat u de juiste indexen moet ontwerpen of persistent berekende kolommen moet gebruiken. Zie [Richtlijnen voor het DirectQuery-model in Power BI Desktop](directquery-model-guidance.md) voor meer informatie.

### <a name="measure-rls-impact"></a>Impact op beveiliging op rijniveau meten

Het is mogelijk om de impact op de prestaties van filters voor beveiliging op rijniveau in Power BI Desktop te meten met behulp van [Performance Analyzer](../create-reports/desktop-performance-analyzer.md). Bepaal eerst de duur van query's op visuals in een rapport als beveiliging op rijniveau niet wordt afgedwongen. Gebruik vervolgens de opdracht **Weergeven als** op het linttabblad **Model maken** om beveiliging op rijniveau af te dwingen en bepaal en vergelijk de duur van de query's.

## <a name="configure-role-mappings"></a>Roltoewijzingen configureren

Nadat u ze naar Power BI hebt gepubliceerd, moet u leden toewijzen aan de gegevenssetrollen. Alleen eigenaren van een gegevensset of werkruimtebeheerders kunnen leden aan rollen toevoegen. Zie [Beveiliging op rijniveau (RLS) met Power BI (Beveiliging voor uw model beheren)](../admin/service-admin-rls.md#manage-security-on-your-model) voor meer informatie.

Leden kunnen gebruikersaccounts of beveiligingsgroepen zijn. U wordt aangeraden om waar mogelijk beveiligingsgroepen toe te wijzen aan gegevenssetrollen. Hiervoor moeten lidmaatschappen van beveiligingsgroepen worden beheerd in Azure Active Directory. Mogelijk wordt deze taak overgedragen aan uw netwerkbeheerders.

## <a name="validate-roles"></a>Rollen valideren

Test elke rol om ervoor te zorgen dat het model correct wordt gefilterd. U kunt dit eenvoudig doen met behulp van de opdracht **Weergeven als** opdracht op het linttabblad **Model maken** .

Wanneer het model dynamische regels bevat met de DAX-functie [USERNAME](/dax/username-function-dax), moet u testen op verwachte _en onverwachte_ waarden. Bij het insluiten van Power BI-inhoud, met name als de [app eigenaar is van gegevens](../developer/embedded/embedding.md#embedding-for-your-customers), kan de app-logica elke waarde doorgeven als effectieve gebruikersnaam voor een identiteit. Indien mogelijk, moet u ervoor zorgen dat onbedoelde of schadelijke waarden resulteren in filters die geen rijen retourneren.

Bekijk een voorbeeld waarin Power BI is ingesloten, waarbij de functierol van de gebruiker door de app wordt doorgegeven als de effectieve gebruikersnaam: Deze is 'Manager' of 'Worker'. Managers kunnen alle rijen zien, maar medewerkers kunnen alleen rijen zien waarin het **Type** van de kolomwaarde 'Internal' (intern) is.

De volgende regelexpressie is gedefinieerd:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

Het probleem met deze regelexpressie is dat alle waarden, met uitzondering van 'Worker', _alle tabelrijen_ retourneren. Een onbedoelde waarde, zoals 'Wrker', retourneert per ongeluk alle tabelrijen. Daarom is het veiliger om een expressie te schrijven waarmee een controle wordt uitgevoerd op elke verwachte waarde. In de volgende verbeterde regelexpressie heeft een onverwachte waarde als resultaat dat de tabel geen rijen retourneert.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Gedeeltelijke beveiliging op rijniveau ontwerpen

Soms zijn er waarden nodig voor berekeningen die niet worden beperkt door filters voor beveiliging op rijniveau. Zo moet een rapport mogelijk een verhouding weergeven tussen de verdiende omzet in de verkoopregio van de rapportgebruiker en _alle verdiende omzet_ .

Hoewel beveiliging op rijniveau niet kan worden overschreven door een DAX-expressie (of door een DAX-expressie kan worden bepaald of beveiliging op rijniveau wordt afgedwongen), kunt u een overzichtsmodeltabel gebruiken. Op de overzichtsmodeltabel wordt een query uitgevoerd om de omzet voor alle regio's op te halen. Deze wordt niet beperkt door filters voor beveiliging op rijniveau.

Laten we eens kijken hoe u deze ontwerpvereiste kunt implementeren. Bekijk eerst het volgende modelontwerp:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="Er wordt een afbeelding van een modeldiagram weergegeven. Het model wordt beschreven in de volgende alinea's.":::

Het model bestaat uit vier tabellen:

- In de tabel **Salesperson** (Verkoper) wordt één rij per verkoper opgeslagen. Het bevat de kolom **EmailAddress** , waarin het e-mailadres van elke verkoper wordt opgeslagen. Deze tabel is verborgen.
- In de tabel **Sales** (Verkoop) wordt één rij per order opgeslagen. Het bevat de meting **Revenue % All Region** (omzetpercentage van alle regio's), die is ontworpen om een verhouding te retourneren tussen de verdiende omzet van de regio van de rapportgebruiker en de verdiende omzet van alle regio's.
- In de tabel **Date** (Datum) wordt één rij per datum opgeslagen en kan worden gefilterd en gegroepeerd op jaar en maand.
- **SalesRevenueSummary** is een berekende tabel. Hierin wordt de totale omzet voor elke orderdatum opgeslagen. Deze tabel is verborgen.

Met de volgende expressie wordt de berekende tabel **SalesRevenueSummary** gedefinieerd:

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> U kunt ook een [aggregatietabel](../transform-model/desktop-aggregations.md) gebruiken voor deze ontwerpvereiste.

De volgende regel voor beveiliging op rijniveau wordt toegepast op de tabel **Salesperson** :

```dax
[EmailAddress] = USERNAME()
```

Elk van de drie modelrelaties wordt beschreven in de volgende tabel:

|Relatie|Beschrijving|
|---------|---------|
|![Stroomdiagramafsluiter 1.](media/common/icon-01-red-30x30.png)|Er is een veel-op-veel-relatie tussen de tabellen **Salesperson** en **Sales** . De regel voor beveiliging op rijniveau filtert de kolom **EmailAddress** van de verborgen tabel **Salesperson** met behulp van de DAX-functie [USERNAME](/dax/username-function-dax). De waarde van de kolom **Region** (voor de rapportgebruiker) wordt doorgevoerd in de tabel **Sales** .|
|![Stroomdiagramafsluiter 2.](media/common/icon-02-red-30x30.png)|Er is een een-op-veel-relatie tussen de tabellen **Date** en **Sales** .|
|![Stroomdiagramafsluiter 3.](media/common/icon-03-red-30x30.png)|Er is een een-op-veel-relatie tussen de tabellen **Date** en **SalesRevenueSummary** .|

Met de volgende expressie wordt de meting **Revenue % All Region** gedefinieerd:

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Voorkom dat gevoelige feiten worden weergegeven. Als er in dit voorbeeld slechts twee regio's waren,zou een rapport gebruiker de omzet van de andere regio kunnen berekenen.

## <a name="avoid-using-rls"></a>Geen beveiliging op rijniveau gebruiken

Vermijd het gebruik van beveiliging op rijniveau als dat zinvol is. Als u slechts een klein aantal vereenvoudigde beveiliging op rijniveau hebt waarmee statische filters worden toegepast, kunt u overwegen om in plaats daarvan meerdere gegevenssets te publiceren. Geen van de gegevenssets definiëren rollen, omdat elke gegevensset gegevens bevat voor een specifieke doelgroep van rapportgebruikers met dezelfde gegevensmachtigingen. Maak vervolgens één werkruimte per doelgroep en wijs toegangsmachtigingen toe aan de werkruimte of app.

Bijvoorbeeld, een bedrijf met slechts twee verkoopregio's besluit _voor elke verkoopregio_ een gegevensset te publiceren in verschillende werkruimten. Beveiliging op rijniveau wordt niet afgedwongen voor de gegevenssets. Ze gebruiken echter [queryparameters](/power-query/power-query-query-parameters) om brongegevens te filteren. Op deze manier wordt in elke werkruimte hetzelfde model gepubliceerd. Alleen de parameterwaarden verschillen per gegevensset. Verkopers krijgen slechts toegang tot één van de werkruimten (of gepubliceerde apps) toegewezen.

Het vermijden van beveiliging op rijniveau biedt verschillende voordelen:

- **Verbeterde queryprestaties:** De prestaties kunnen hoger zijn omdat er minder filters worden gebruikt.
- **Kleinere modellen:** Het resulteert in meer modellen, maar deze zijn wel kleiner. Kleinere modellen kunnen de reactiesnelheid van query's en gegevensvernieuwing verbeteren, met name als de hostcapaciteit voor resources onder druk staat. Bovendien is het eenvoudiger om de grootte van modellen onder uw capaciteitslimieten te houden. Ten slotte is het eenvoudiger om werkbelastingen te verdelen over verschillende capaciteiten, omdat u werkruimten kunt maken op of verplaatsen naar verschillende capaciteiten.
- **Aanvullende functies:** Power BI-functies die niet met beveiliging op rijniveau werken, zoals [Publiceren op internet](../collaborate-share/service-publish-to-web.md), kunnen worden gebruikt.

Het vermijden van beveiliging op rijniveau kent echter ook nadelen:

- **Meerdere werkruimten:** Voor elke gebruikersdoelgroep van het rapport is een werkruimte vereist. Als apps worden gepubliceerd, betekent dit ook dat er één app per rapportgebruikersdoelgroep is.
- **Duplicatie van inhoud:** Rapporten en dashboards moeten in elke werkruimte worden gemaakt. Het instellen en onderhouden hiervan kost extra moeite en tijd.
- **Gebruikers met hoge bevoegdheden:** Gebruikers met hoge bevoegdheden, die deel uitmaken van meerdere doelgroepen van rapportgebruikers, kunnen geen geconsolideerde weergave van de gegevens bekijken. Ze moeten meerdere rapporten (vanuit verschillende werkruimten of apps) openen.

## <a name="troubleshoot-rls"></a>Problemen met beveiliging op rijniveau oplossen

Als er onverwachte resultaten worden gegenereerd door beveiliging op rijniveau, voert u een controle uit op de volgende problemen:

- Er bestaan onjuiste relaties tussen modeltabellen, in termen van kolomtoewijzingen en filterrichtingen.
- De relatie-eigenschap **Beveiligingsfilter in beide richtingen toepassen** is niet juist ingesteld. Raadpleeg [Richtlijnen voor bidirectionele relaties](relationships-bidirectional-filtering.md) voor meer informatie.
- Tabellen bevatten geen gegevens.
- Onjuiste waarden worden in tabellen geladen.
- De gebruiker is toegewezen aan meerdere rollen.
- Het model bevat aggregatietabellen en de aggregaties en details worden niet consistent gefilterd door de regels voor beveiliging op rijniveau. Zie [Aggregaties gebruiken in Power BI Desktop (Beveiliging op rijniveau voor aggregaties)](../transform-model/desktop-aggregations.md#rls-for-aggregations) voor meer informatie.

Wanneer een specifieke gebruiker geen gegevens kan zien, is de UPN mogelijk niet opgeslagen of onjuist ingevoerd. Dit kan abrupt gebeuren omdat het gebruikersaccount is gewijzigd als gevolg van een naamswijziging.

> [!TIP]
> Voeg voor testdoeleinden een meting toe die de DAX-functie [USERNAME](/dax/username-function-dax) retourneert. U kunt deze bijvoorbeeld 'Wie ben ik' noemen. Vervolgens voegt u de meting toe aan een kaartvisual in een rapport en publiceert u deze naar Power BI.

Wanneer specifieke gebruikers alle gegevens kunnen zien, is het mogelijk dat ze rechtstreeks toegang hebben tot rapporten in de werkruimte en ze de eigenaar van de gegevensset zijn. Beveiliging op rijniveau wordt alleen afgedwongen in de volgende gevallen:

- Het rapport wordt geopend in een app.
- Het rapport wordt geopend in een werkruimte en de gebruiker is toegewezen aan de [rol Lezer](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Volgende stappen

Bekijk de volgende resources voor meer informatie over dit artikel:

- [Beveiliging op rijniveau (RLS) met Power BI](../admin/service-admin-rls.md)
- [Gegevenstoegang met beveiliging op rijniveau (RLS) beperken voor Power BI Desktop](../create-reports/desktop-rls.md)
- [Modelrelaties in Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
- Suggesties? [Ideeën bijdragen om Power BI te verbeteren](https://ideas.powerbi.com/)
