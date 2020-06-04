---
title: Power BI voor klanten uit de Amerikaanse overheid - Overzicht
description: Amerikaanse overheidsklanten kunnen een Power BI Pro-abonnement toevoegen aan hun Microsoft 365 Government-abonnement. Meer informatie over het registreren en controleren van de beschikbaarheid van functies in deze servicebeschrijving.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/07/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 9f94d6a1b99bce40d3f901dd71877da3f6b236af
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83792880"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI voor klanten uit de Amerikaanse overheid
Dit artikel is voor Amerikaanse overheidsklanten die Power BI implementeren als onderdeel van een Microsoft 365 Government-abonnement. Overheidsplannen zijn ontworpen voor de unieke behoeften van organisaties die moeten voldoen aan Amerikaanse nalevings-en beveiligingsnormen. De Power BI-service die voor Amerikaanse overheidsklanten is ontworpen, verschilt van de commerciële versie van de Power BI-service. Deze functieverschillen en mogelijkheden worden beschreven in de volgende secties.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Power BI toevoegen een Microsoft 365 Government-abonnement toevoegen

Voordat u een abonnement op Power BI voor de Amerikaanse overheid krijgt en licenties aan gebruikers toewijst, moet u zich inschrijven voor een Microsoft 365 Government-abonnement. Als uw organisatie al een Microsoft 365 Government-abonnement heeft, gaat u naar [Een Power BI Pro-abonnement voor overheidsklanten aanschaffen](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Inschrijven voor een Microsoft 365 Government-abonnement

Als u een nieuwe klant bent, moet u de geschiktheid van uw organisatie valideren voordat u zich kunt aanmelden voor een Microsoft 365 Government-abonnement.  Begin door het [geschiktheidsformulier voor Microsoft 365 voor Government](https://www.microsoft.com/microsoft-365/government/eligibility-validation) in te vullen om te kijken of u wel in aanmerking komt. Raadpleeg de [Microsoft 365 US Government Service-beschrijvingen](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) om er zeker van te zijn dat u het juiste abonnement voor uw organisatie selecteert.

> [!NOTE]
> Als u Power BI al hebt geïmplementeerd in een commerciële omgeving en wilt migreren naar de cloud van de Amerikaanse overheid, moet u een nieuw Power BI Pro-abonnement toevoegen aan uw Microsoft 365 Government-abonnement. Repliceer vervolgens de commerciële gegevens naar de Power BI-service voor de Amerikaanse overheid, verwijder commerciële licentietoewijzingen van gebruikersaccounts en wijs vervolgens een Power BI Pro Government-licentie toe aan de gebruikersaccounts.
>
>
## <a name="government-cloud-instances"></a>Cloud van de Amerikaanse overheid
Microsoft 365 biedt verschillende omgevingen voor overheidsinstanties om te voldoen aan verschillende nalevingsvereisten. Raadpleeg voor meer informatie over elke omgeving:

* [Microsoft 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) is ontworpen voor federale, staats- en lokale overheden.

* [Microsoft 365 GCC High (Government Community High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is ontworpen voor federale agentschappen, de defensie-industrie, luchtvaart en andere organisaties die niet-geclassificeerde informatie hebben. Deze omgeving is geschikt voor nationale beveiligingsorganisaties en bedrijven met internationaal verkeer in ITAR-gegevens (International Traffic in Arms Regulations) of ingrijpende DFARS-vereisten (Defense Federal Acquisition Regulations Supplement).

* De [Microsoft 365 DoD-omgeving](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is uitsluitend ontworpen voor het Amerikaanse ministerie van defensie. 

## <a name="connect-to-power-bi-for-us-government"></a>Verbinding maken met Power BI voor de Amerikaanse overheid

De URL voor het verbinding maken met Power BI verschilt voor overheidsgebruikers en commerciële gebruikers. Als u zich wilt aanmelden bij Power BI, gebruikt u de volgende URL's:

| Commerciële versie  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Uw account is mogelijk ingesteld in meerdere clouds. Als uw account op deze manier is ingesteld, kunt u kiezen met welke cloud u verbinding wilt maken wanneer u zich aanmeldt bij Power BI Desktop.

## <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Een Power BI Pro-abonnement voor overheidsklanten aanschaffen

Nadat u Microsoft 365 hebt geïmplementeerd, kunt u een Power BI Pro-abonnement toevoegen. Volg de stapsgewijze instructies in [Uw Amerikaanse overheidsorganisatie registreren](service-govus-signup.md) om de Power BI Pro Government-service aan te schaffen. Schaf voldoende licenties aan voor alle gebruikers die Power BI nodig hebben, en wijs deze licenties vervolgens toe aan afzonderlijke gebruikersaccounts.

> [!IMPORTANT]
> Power BI voor de Amerikaanse overheid is niet beschikbaar als een *gratis* licentie. Aan elke gebruiker moet een *Pro*-licentie zijn toegewezen om toegang te krijgen tot de Government Community Cloud. Als aan een gebruikersaccount een gratis licentie is toegewezen, heeft de gebruiker alleen toegang tot de commerciële cloud en zal deze verificatie- en toegangsproblemen ondervinden. Als u Power BI Premium hebt aangeschaft, hoeft u geen Pro-licenties toe te wijzen om gebruikerstoegang in te schakelen.  Gebruikers in de organisatie hebben toegang tot rapporten die met hen zijn gedeeld, mits deze rapporten zijn gepubliceerd in een premium-capaciteit. Raadpleeg [Power BI-servicefuncties per licentietype](../fundamentals/service-features-license-type.md) om de verschillen tussen licentietypen te bekijken.
>

## <a name="connect-government-and-global-azure-cloud-services"></a>Azure Government en algemene Azure Cloud Services verbinden

Azure wordt gedistribueerd over meerdere clouds. Standaard kunt u firewallregels inschakelen om een verbinding met een Cloud-specifiek exemplaar te openen, maar dit is anders over verschillende cloud-netwerken.  Als u wilt communiceren tussen services in de openbare cloud en services in de Government Community Cloud, moet u specifieke firewallregels configureren. Als u bijvoorbeeld toegang wilt krijgen tot openbare cloudexemplaren van een SQL-database vanuit uw Power BI-implementatie in de cloud, hebt u een firewallregel in de SQL-database nodig. Configureer specifieke firewallregels voor SQL-databases om verbindingen met de Azure Government Cloud toe te staan voor de volgende datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

In de openbare cloud zijn de IP-ruimten beschikbaar. Als u de IP-adresbereiken voor de cloud van de Amerikaanse overheids wilt ophalen, downloadt u het bestand [Azure IP-bereiken en servicetags – Cloud van de Amerikaanse overheid](https://www.microsoft.com/download/details.aspx?id=57063). 

Raadpleeg [IP-firewallregels maken en beheren](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules) als u firewalls wilt instellen voor SQL-databases.

## <a name="power-bi-feature-availability"></a>Beschikbaarheid van Power BI-functies

Er zijn een aantal verschillen tussen overheidsplannen en commerciële abonnementen om te voldoen aan de vereisten van klanten in de Cloud. Raadpleeg de volgende tabel om te zien welke functies beschikbaar zijn in elke overheidsomgeving:

|Functie |   |GCC |GCC High |DoD|
|------|------|------|------|------|
|Beheer|Gratis licenties|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Limieten voor gegevensopslag instellen|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Active Directory Domain Services-groepen voor het delen en beheren van toegangsbeheer gebruiken|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Controleren via Office 365 Security en het Compliance-beheercentrum|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Delen met externe gebruikers|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gebruik metrische gegevens voor dashboards en rapporten|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure B2B tussen GCC en commerciële cloud|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|Rapport maken|Dashboards en rapporten maken en bekijken|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Geplande gegevensvernieuwing|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Vernieuwbare teamdashboards|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gepagineerde rapporten|Beschikbaar|In de roadmap|In de roadmap|
|  |Sjabloon-apps|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|Verbinding maken met gegevens|Gegevens en rapporten uit Excel importeren|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevens uit CSV-bestanden importeren|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevens ophalen uit Power BI Desktop-bestanden|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Connectiviteit met CDS|Beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure Data Lake Storage Gen2-connector|Beschikbaar|Niet beschikbaar|Niet beschikbaar|
|Gegevensbeheer|Gegevensbeheer-gateway|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensversleuteling in Azure SQL Database|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensversleuteling in Blob Storage voor Power BI|Beschikbaar|Beschikbaar|Beschikbaar|
|Integratie tussen verschillende producten|Insluiten in SharePoint online met het webonderdeel Power BI|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Insluiten in SharePoint online met het webonderdeel Embed|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensstromen en AI-functies|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Power Automate-connectiviteit voor gegevensgestuurde waarschuwingen|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Tabblad Power BI in Teams|Beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Geautomatiseerde Machine Learning|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure Cognitive Services|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure Machine Learning|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|

## <a name="next-steps"></a>Volgende stappen

* [Registreren voor Power BI voor de Amerikaanse overheid](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate voor de Amerikaanse overheid](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo van Power BI voor de Amerikaanse overheid</a>
