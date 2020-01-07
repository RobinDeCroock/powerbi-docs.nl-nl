---
title: Query opslaan in cache in Power BI Premium
description: Query opslaan in cache in Power BI Premium
author: KesemSharabi
ms.author: kesharab
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/04/2019
LocalizationGroup: ''
ms.openlocfilehash: 1f1d88e2484d48e1f479523dddf6bb0cb63e5d0f
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2020
ms.locfileid: "73875193"
---
# <a name="query-caching-in-power-bi-premiumembedded"></a>Query opslaan in cache in Power BI Premium/Embedded

Organisaties met Power BI Premium of Power BI Embedded kunnen gebruikmaken van *query opslaan in cache* om rapporten die zijn gekoppeld aan een gegevensset sneller weer te geven. Hierbij kan de Premium-/Embedded-capaciteit gebruikmaken van de lokale cacheservice om de queryresultaten op te slaan, zodat de onderliggende gegevensbron deze resultaten niet meer hoeft te berekenen.

> [!IMPORTANT]
> Query opslaan in cache is alleen beschikbaar in Power BI Premium en Power BI Embedded. Het is niet van toepassing op Live Connect-gegevenssets die gebruikmaken van Azure Analysis Services of SQL Server Analysis Services.

Queryresultaten in cache zijn specifiek voor de gebruiker en gegevensset en volgen altijd de beveiligingsregels. Momenteel wordt alleen een query in de cache opgeslagen voor de oorspronkelijke pagina waarop u terechtkomt. Met andere woorden, query's worden niet in de cache opgeslagen wanneer u werkt met het rapport. In de querycache worden [persoonlijke bladwijzers](consumer/end-user-bookmarks.md#personal-bookmarks) en [permanente filters](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) aangehouden, zodat query's die worden gegenereerd door een persoonlijk rapport in de cache worden opgeslagen. [Dashboardtegels](service-dashboard-tiles.md) die worden aangestuurd door de dezelfde query's profiteren er ook van wanneer de query in de cache is opgeslagen. Het levert met name een voordeel op met betrekking tot de prestaties wanneer een gegevensset vaak wordt geopend en niet vaak hoeft te worden vernieuwd. Als u query's in de cache opslaat, kan de belasting op uw Premium-/Embedded-capaciteit ook worden teruggedrongen door het totale aantal query's te reduceren.

U kunt de instellingen voor query's in de cache opgeven op de pagina **Instellingen** voor de gegevensset in de Power BI-service. Er zijn drie instellingen mogelijk:

- **Standaardinstelling voor capaciteit**: Query's in cache opslaan - Uit
- **Uit**: Voor deze gegevensset worden geen query's in de cache opgeslagen.
- **Aan**: Voor deze gegevensset worden query's in de cache opgeslagen.

    ![Dialoogvenster voor query's in cache opslaan](media/power-bi-query-caching/power-bi-query-3-options.png)

## <a name="considerations-and-limitations"></a>Overwegingen en beperkingen

- Wanneer u de cache-instellingen wijzigt van **Aan** naar **Uit**, worden alle eerder opgeslagen queryresultaten voor de gegevensset verwijderd uit de cache van de capaciteit. U kunt het opslaan van query's in de cache expliciet uitschakelen of de standaardinstelling voor een capaciteit gebruiken, die door een beheerder is ingesteld op **Uit**. Wanneer u de cache-instelling uitschakelt, vindt er mogelijk een kleine vertraging plaats wanneer een rapport query's op deze gegevensset uitvoert. De vertraging wordt veroorzaakt door de rapportquery's die op aanvraag worden uitgevoerd en geen gebruikmaken van de opgeslagen resultaten. Bovendien moet de vereiste gegevensset mogelijk in het geheugen geladen zijn voordat u hiervoor query's kunt uitvoeren.
- Wanneer de querycache wordt vernieuwd, moeten query's in Power BI worden uitgevoerd op de onderliggende gegevensmodellen om de recentste resultaten te krijgen. Als voor een groot aantal gegevenssets querycaching is ingeschakeld en de Premium-/Embedded-capaciteit zwaar wordt belast, kan er tijdens het vernieuwen van de cache prestatievermindering optreden. Dat komt door het verhoogde volume aan query's die worden uitgevoerd.

## <a name="next-steps"></a>Volgende stappen

* [Wat is Power BI Premium?](service-premium-what-is.md)
* [Wat is Power BI Embedded in Azure?](developer/azure-pbie-what-is-power-bi-embedded.md)
