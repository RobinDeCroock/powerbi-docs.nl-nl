---
title: Power BI voor Amerikaanse overheidsklanten - Overzicht
description: 'Voor Amerikaanse overheidsklanten: kom meer te weten over de kenmerken en limieten voor de Power BI-service voor de Amerikaanse overheid'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 748594dcf9f71677057b8641e44f1408bebd1b89
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715355"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI voor klanten uit de Amerikaanse overheid
Er is als onderdeel van **Office 365 US Government Community**-abonnement een versie van de **Power BI-service** beschikbaar voor Amerikaanse overheidsklanten. De versie van de **Power BI-service** die in dit artikel wordt besproken, is specifiek ontworpen voor Amerikaanse overheidsklanten en staat los en verschilt van de commerciële versie van de **Power BI-service**.

![](media/service-govus-overview/service_usgov_overview-1.png)

In de volgende secties wordt beschreven welke *functies* beschikbaar zijn in de versie voor de Amerikaanse overheid van de **Power BI-service**, wordt uitleg gegeven over enkele van de *beperkingen*, worden veelgestelde vragen (**FAQ**) vermeld met antwoorden (waaronder over het registreren) en worden koppelingen opgegeven naar meer informatie.

## <a name="features-of-power-bi-us-government"></a>Kenmerken van Power BI voor de Amerikaanse overheid
Het is belangrijk om te weten dat **Power BI voor de Amerikaanse overheid** alleen beschikbaar is met een **Pro-licentie** en niet beschikbaar is met een Free-licentie. Alleen bepaalde functies van de Power BI-service zijn beschikbaar in de **Power BI-versie voor de Amerikaanse overheid**.

De volgende functies beschikbaar zijn voor **Power BI voor Amerikaanse overheidsklanten**, in overeenstemming met de kenmerken van de **Pro**-licentie:

* Dashboards en rapporten maken en bekijken
* [Limieten voor gegevenscapaciteit](service-admin-manage-your-data-storage-in-power-bi.md)
* [Geplande gegevensvernieuwing](refresh-data.md)
* Vernieuwbare teamdashboards
* Active Directory-groepen voor het delen en beheren van toegangsbeheer
* [Gegevens en rapporten importeren](service-get-data.md) vanuit Excel-, CSV- en Power BI Desktop-bestanden
* Gegevensbeheergateway
* Alle gegevens worden voor Power BI versleuteld in zowel Azure SQL als Blob Storage
* Verbinding maken met services met [inhoudspakketten](service-connect-to-services.md)

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Connectiviteit tussen Azure Government en algemene Azure Cloud Services 

Azure wordt gedistribueerd over meerdere clouds. Standaard is het tenants toegestaan om firewallregels van een cloudspecifieke instantie te openen. Werken met netwerken binnen de cloud is echter anders; hiervoor is het openen van specifieke firewallregels voor de communicatie tussen services vereist. Als u een Power BI-klant bent en u over bestaande SQL-instanties beschikt in de openbare cloud die u dient te openen, moet u specifieke firewall-regels in SQL openen op de IP-adresruimte van de Azure Government-cloud voor de volgende datacenters:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

In de openbare cloud zijn de IP-ruimten beschikbaar. Raadpleeg voor Government Cloud de downloadbare [documentatie voor de Azure Government-service](https://www.microsoft.com/download/details.aspx?id=57063) voor de laatste informatie.

## <a name="limitations-of-power-bi-us-government"></a>Beperkingen van Power BI voor de Amerikaanse overheid
Enkele van de functies die beschikbaar in de commerciële versie van de **Power BI-service** zijn *niet* beschikbaar in de **Power BI-service** voor Amerikaanse overheidsklanten. Het Power BI-team is actief bezig met het beschikbaar maken van deze functies voor Amerikaanse overheidsklanten. Dit artikel wordt bijgewerkt zodra de functies beschikbaar zijn.

* **Insluiten in SharePoint Online**: het is niet mogelijk inhoud in te sluiten in SharePoint Online met het Power BI-webonderdeel. Beveiligd insluiten werkt echter wel als u het [webonderdeel *Insluiten*](https://docs.microsoft.com/power-bi/service-embed-secure) gebruikt. U moet *app.powerbigov.us* aan de lijst met uitzonderingen toevoegen. Volg hiervoor de instructies in het artikel [De mogelijkheid van het insluiten van inhoud op SharePoint-pagina's toestaan of beperken](https://support.office.com/article/allow-or-restrict-the-ability-to-embed-content-on-sharepoint-pages-e7baf83f-09d0-4bd1-9058-4aa483ee137b).
* **Power BI voor de Amerikaanse overheid** is alleen beschikbaar met een **Pro**-licentie. Power BI Free-licenties waarnaar wordt verwezen in een beheerportal (of een portal voor gebruikers) worden uitgevoerd in een commerciële Power BI-servicecloud.
* **Controleren**: controleren is nu, vanaf juni 2018, beschikbaar via de Office 365-portal Beveiliging en naleving.
* **Power BI-inhoud in Cortana** - resultaten voor Power BI wordt niet weergegeven in zoekresultaten van Cortana, waaronder resultaten voor uw Power BI-inhoud (dashboards, rapporten en apps) en tevens resultaten die voor Cortana geoptimaliseerde rapportpagina's weergeven voor specifieke trefwoorden.
* **Externe gebruiker delen**: delen is toegestaan binnen een Power BI-tenant en vanaf juni 2018 kunt u ook met gebruikers buiten uw Power BI-tenant delen. Zie [Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers](service-admin-azure-ad-b2b.md).
* **Metrische gegevens over het gebruik van dashboards en rapporten**: metrische gegevens over het gebruik zijn beschikbaar voor rapporten en dashboards. Klanten kunnen gegevens uit auditlogboeken gebruiken om informatie op te halen over inhoud in hun organisatie.
* **Gegevensstromen**: gegevensstromen zijn niet beschikbaar.

Als er **Power BI** Free-licenties zijn toegewezen aan uw account, worden die accounts uitgevoerd in een commerciële versie van de **Power BI**-service en maken ze geen deel uit van **Power BI voor de Amerikaanse overheid**. Bij deze Free-accounts kunnen de volgende problemen optreden:

* Gateway, Mobile en Desktop kunnen niet worden geverifieerd
* U hebt geen toegang tot de commerciële gegevensbronnen van Azure
* PBIX-bestanden moeten handmatig via de commerciële service worden geüpload
* Er zijn geen mobiele Power BI-apps beschikbaar

Neem contact op met uw accountvertegenwoordiger om mogelijke problemen op te lossen.

## <a name="frequently-asked-questions-faq-for-the-us-government-version-of-the-power-bi-service"></a>Veelgestelde vragen (FAQ) over de Power BI-service voor de Amerikaanse overheid
Met behulp van de volgende vragen (en antwoorden) kunt u snel de informatie over de service vinden die u nodig hebt.

**Vraag:** Hoe migreer ik mijn commerciële **Power BI**-gegevens naar de **Power BI-service** voor de Amerikaanse overheid?

**Antwoord**: Uw beheerder moet een nieuw exemplaar van **Power BI** maken via een afzonderlijk abonnement speciaal voor de Amerikaanse overheid. U kunt vervolgens uw commerciële gegevens repliceren in de **Power BI-service** voor de Amerikaanse overheid, uw commerciële licentie verwijderen en uw bestaande domein koppelen aan de nieuwe service speciaal voor de Amerikaanse overheid.

**Vraag:** Waarom kan ik geen verbinding maken met een specifiek inhoudspakket?

**Antwoord**: U moet ervoor zorgen dat uw abonnement is ingeschakeld. Daarna kunt u pas verbinding maken met inhoudspakketten.

**Vraag:** Ik wil graag **Power BI** gaan gebruiken in mijn organisatie binnen de Amerikaanse overheid. Hoe ga ik aan de slag?

**Antwoord**: Het registratieproces (ook wel *onboarding* genoemd) kan verschillen op basis van uw bestaande licentie en abonnement. Zie het artikel [Registreren voor Power BI voor de Amerikaanse overheid](service-govus-signup.md) voor meer informatie.

**Vraag:** Is de URL voor het verbinden met **Power BI** voor de Amerikaanse overheid anders dan de commerciële **Power BI**-URL? Is er een andere URL voor klanten van Government Community Cloud High (GCC High)?

**Antwoord**: Ja, de URL's verschillen. In de volgende tabel worden de URL's weergegeven:

| URL van de commerciële versie | URL van de versie voor de Amerikaanse overheid | URL van de Amerikaanse overheid voor GCC High |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

**Vraag:** Mijn account is in meer dan één nationale cloud ingericht. Hoe selecteer ik tijdens het gebruik van **Power BI Desktop** met welke cloud ik verbinding wil maken?

**Antwoord**: Vanaf de release van juli 2018 van **Power BI Desktop** kunt u kiezen welke cloud u wilt gebruiken tijdens het aanmelden bij **Power BI Desktop**.


## <a name="next-steps"></a>Volgende stappen
Er zijn veel verschillende dingen die u met Power BI kunt doen. Bekijk de volgende resources voor meer informatie en trainingen, inclusief een artikel waarin wordt uitgelegd hoe zich voor de service kunt aanmelden:

* [Registreren voor Power BI voor de Amerikaanse overheid](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demo van Power BI voor de Amerikaanse overheid</a>
* [Begeleide training voor Power BI](guided-learning/index.md)
* [Aan de slag met de Power BI-service](service-get-started.md)
* [Wat is Power BI Desktop?](desktop-what-is-desktop.md)

