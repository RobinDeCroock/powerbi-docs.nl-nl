---
title: Power BI voor klanten uit de Amerikaanse overheid - Overzicht
description: Klanten van de Amerikaanse overheid kunnen een Power BI Pro abonnement toevoegen aan hun abonnement op Office 365 Government. Meer informatie over het registreren en controleren van de beschikbaarheid van functies in deze servicebeschrijving.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: 26dabde3846ec33e2f5910de75fb8165cce6513a
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160760"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI voor klanten uit de Amerikaanse overheid
Dit artikel is voor Amerikaanse overheidsklanten die Power BI implementeren als onderdeel van een Office 365 Government-abonnement. Overheidsplannen zijn ontworpen voor de unieke behoeften van organisaties die moeten voldoen aan Amerikaanse nalevings-en beveiligingsnormen. De Power BI-service die voor Amerikaanse overheidsklanten is ontworpen, verschilt van de commerciële versie van de Power BI-service. Deze functieverschillen en mogelijkheden worden beschreven in de volgende secties.

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Power BI toevoegen aan uw Office 365 Government-abonnement

Voordat u een abonnement op Power BI US Government krijgt en licenties aan gebruikers toewijst, moet u zich inschrijven voor een Office 365 Government-abonnement. Als uw organisatie al een Office 365 Government-abonnement heeft, gaat u naar [Een Power BI Pro Government-abonnement aanschaffen](#purchase-a-power-bi-pro-government-subscription).

### <a name="enroll-in-office-365-government-plan"></a>Registreren in Office 365 Government-abonnement

Als u een nieuwe klant bent, moet u de geschiktheid van uw organisatie valideren voordat u zich kunt aanmelden voor een overheidsabonnement.  Ga aan de slag door het formulier [Office 365 for Government-geschiktheidsvalidatie](https://www.microsoft.com/microsoft-365/government/eligibility-validation) te voltooien. Om ervoor te zorgen dat u het juiste abonnement voor uw organisatie selecteert, raadpleegt u de [Office 365 US Government Service-beschrijvingen](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Als u Power BI al hebt geïmplementeerd in een commerciële omgeving en wilt migreren naar de cloud van de Amerikaanse overheid, moet u een nieuw Power BI Pro-abonnement toevoegen aan uw Office 365 Government-abonnement. Repliceer vervolgens de commerciële gegevens naar de Power BI-service voor de Amerikaanse overheid, verwijder commerciële licentietoewijzingen van gebruikersaccounts en wijs vervolgens een Power BI Pro Government-licentie toe aan de gebruikersaccounts.
>
>

### <a name="government-cloud-instances"></a>Cloud van de Amerikaanse overheid
Office 365 biedt verschillende omgevingen voor overheidsinstanties om te voldoen aan verschillende nalevingsvereisten. Raadpleeg de beschrijving van de gekoppelde service voor specifieke informatie over wat elke omgeving biedt.

* [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) is ontworpen voor federale, staats- en lokale overheden.

* [Office 365 Government Community High (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is ontworpen voor federale agentschappen, de defensie-industrie, luchtvaart en andere organisaties die niet-geclassificeerde informatie hebben. Deze omgeving is geschikt voor nationale beveiligingsorganisaties en bedrijven met internationaal verkeer in International Traffic in Arms Regulations (ITAR)-gegevens of ingrijpende Federal Acquisition Regulations (DFARS)-vereisten.

* De [Office 365 DoD-omgeving](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) is uitsluitend ontworpen voor het Amerikaanse ministerie van defensie. 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>Een Power BI Pro Government-abonnement kopen

Nadat u Office 365 hebt geïmplementeerd, kunt u een Power BI-abonnement toevoegen. Volg de stapsgewijze instructies in [Uw Amerikaanse overheidsorganisatie registreren](service-govus-signup.md#existing-office-government-cloud-customers) om de Power BI Pro Government-service te kopen. Koop voldoende licenties voor alle gebruikers die Power BI moeten gebruiken en wijs deze licenties vervolgens toe aan afzonderlijke gebruikersaccounts.

> [!IMPORTANT]
> Power BI US Government is niet beschikbaar als gratis licentie. Aan elke gebruiker moet een Pro-licentie worden toegewezen om toegang te krijgen tot de cloud van de regerings-community. Als aan een gebruikersaccount een gratis licentie is toegewezen, wordt deze geautoriseerd voor toegang tot de commerciële Cloud en worden er verificatie- en toegangsproblemen ondervonden. Zie [Power BI-servicefuncties per licentietype](service-features-license-type.md) om de verschillen tussen licentietypen te bekijken.
>
>

## <a name="connect-to-power-bi-for-us-government"></a>Verbinding maken met Power BI for US Government

U gebruikt een andere URL om verbinding te maken met Power BI for US Government dan commerciële gebruikers. Als u zich wilt aanmelden bij Power BI, gebruikt u de volgende URL's:

| URL van de commerciële versie | URL van de versie voor de Amerikaanse overheid | URL van de Amerikaanse overheid voor GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

Uw account kan aan meer dan één cloud worden ingericht. In dat geval kunt u, wanneer u Power BI Desktop gebruikt, kiezen met welke cloud u verbinding wilt maken wanneer u zich aanmeldt.

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Connectiviteit tussen Azure Government en algemene Azure Cloud Services

Azure wordt gedistribueerd over meerdere clouds. Standaard kunt u firewallregels inschakelen om een verbinding met een Cloud-specifiek exemplaar te openen, maar dit is anders over verschillende cloud-netwerken.  Als u wilt communiceren tussen services in de openbare cloud en services in de Government Community Cloud, moet u specifieke firewallregels configureren. Als u bijvoorbeeld toegang wilt krijgen tot openbare cloud-instanties van SQL vanuit uw cloud-implementatie van Power BI, hebt u een firewallregel in SQL nodig. Configureer specifieke firewallregels in SQL om verbindingen met de Azure Government Cloud toe te staan voor de volgende datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

In de openbare cloud zijn de IP-ruimten beschikbaar. Als u de IP-adresbereiken voor de cloud van de Amerikaanse overheids wilt ophalen, downloadt u het bestand [Azure IP-bereiken en-tags – Cloud van de Amerikaanse overheid](https://www.microsoft.com/download/details.aspx?id=57063). 

Als u firewalls in SQL wilt instellen, volgt u de stappen voor het [Maken en beheren van IP-firewall regels](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Beschikbaarheid van Power BI-functies

Er zijn een aantal verschillen tussen overheidsplannen en commerciële abonnementen om te voldoen aan de vereisten van klanten in de Cloud. Raadpleeg de volgende tabel om te zien welke functies beschikbaar zijn in elke overheidsomgeving.

|Functie |   |GCC |GCC-hoog |DoD|
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
|  |Gepagineerde rapporten|Alleen beschikbaar in USGov-Texas en USGov-Virginia |Beschikbaar|In de roadmap|
|  |Sjabloon-apps|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|Verbinding maken met gegevens|Gegevens en rapporten uit Excel importeren|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevens uit CSV-bestanden importeren|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevens ophalen uit Power BI Desktop-bestanden|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Connectiviteit met CDS|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure Data Lake Storage Gen2-connector|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|Gegevensbeheer|Gegevensbeheer-gateway|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensversleuteling in Azure SQL|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensversleuteling in Blob Storage voor Power BI|Beschikbaar|Beschikbaar|Beschikbaar|
|Integratie tussen verschillende producten|Insluiten in SharePoint online met het webonderdeel Power BI|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Insluiten in SharePoint online met het webonderdeel Embed|Beschikbaar|Beschikbaar|Beschikbaar|
|  |Gegevensstromen en AI-functies|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Power Automate-connectiviteit voor gegevensgestuurde waarschuwingen|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Tabblad Power BI in Teams|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Geautomatiseerde Machine Learning|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Cognitive Services|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|
|  |Azure ML|Niet beschikbaar|Niet beschikbaar|Niet beschikbaar|

## <a name="next-steps"></a>Volgende stappen

* [Registreren voor Power BI voor de Amerikaanse overheid](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo van Power BI voor de Amerikaanse overheid</a>
* [Aan de slag met de Power BI-service](service-get-started.md)
* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)

