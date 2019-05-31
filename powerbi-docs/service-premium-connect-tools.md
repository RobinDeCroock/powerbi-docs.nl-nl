---
title: Verbinding maken met Power BI Premium-gegevenssets met client-toepassingen en hulpprogramma's (Preview)
description: Beschrijft hoe u vanaf de clienttoepassingen en hulpprogramma's verbinding maken met gegevenssets in Power BI Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/20/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 063f43cb2345ccb3d1fec5c414100beb8ccde451
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941507"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>Verbinding maken met gegevenssets met client-toepassingen en hulpprogramma's (Preview)

Power BI Premium-werkruimten en gegevenssets ondersteuning *alleen-lezen* verbindingen van Microsoft en derden client-toepassingen en hulpprogramma's. 

> [!NOTE]
> In dit artikel is uitsluitend bedoeld om alleen-lezen verbinding met Power BI Premium-werkruimten en gegevenssets te introduceren. Deze *is niet* bedoeld als gedetailleerde informatie over programmeren, specifieke hulpprogramma's en toepassingen, architectuur en werkruimte en de gegevensset. De hier beschreven onderwerpen vereist een goed begrip van Analysis Services tabellair model database-architectuur en het beheer.

## <a name="protocol"></a>Protocol

Power BI Premium gebruikt de [XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA)-protocol voor communicatie tussen client-toepassingen en de engine die u beheert u uw werkruimten en gegevenssets. Deze berichten zijn wat worden vaak aangeduid als XMLA-eindpunten. XMLA is dezelfde communicatieprotocol wordt gebruikt door de Microsoft Analysis Services-engine, die achter de schermen, Power BI functionaliteit voor semantische modellering, governance, levensduur en gegevens management wordt uitgevoerd. 

Het overgrote deel van de clienttoepassingen en hulpprogramma's niet expliciet communiceren met de engine met behulp van XMLA-eindpunten. In plaats daarvan gebruiken ze clientbibliotheken zoals MSOLAP ADOMD en AMO als een intermediair tussen de clienttoepassing en de engine, die uitsluitend via XMLA communiceert.


## <a name="supported-tools"></a>Ondersteunde hulpprogramma 's

Deze hulpprogramma's bieden ondersteuning voor alleen-lezen toegang tot Power BI Premium-werkruimten en gegevenssets:

**SQL Server Management Studio (SSMS)** -ondersteunt DAX, MDX XMLA en TraceEvent query's. Versie 18.0 vereist. Download [hier](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms). 

**SQL Server Profiler** -opgenomen met SSMS 18.0 (Preview), wordt dit hulpprogramma bevat traceren en foutopsporing van servergebeurtenissen. U kunt vastleggen en opslaan van gegevens over elke gebeurtenis die naar een bestand of de tabel voor het analyseren van later opnieuw. Terwijl officieel afgeschaft voor SQL Server, worden de Profiler blijft worden opgenomen in SSMS en blijft echter ondersteund voor Analysis Services en nu Power BI Premium. Zie voor meer informatie, [SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler).

**DAX-Studio** - Open-source, communityhulpprogramma voor het uitvoeren en analyseren van DAX query uitgevoerd op Analysis Services. Vereist versie 2.8.2 of hoger. Zie voor meer informatie, [daxstudio.org](https://daxstudio.org/).

**Excel-draaitabellen** -Klik-en-klaar-versie van Office 16.0.11326.10000 of hoger is vereist.

**Van derden** - client gegevensvisualisatie toepassingen en hulpprogramma's waarmee verbinding kunnen maken, query bevat, en gegevenssets in Power BI Premium gebruiken. De meeste hulpprogramma's vereist de meest recente versies van de MSOLAP-clientbibliotheken, maar sommige ADOMD mag gebruiken.

## <a name="client-libraries"></a>Clientbibliotheken

-Clientbibliotheken zijn nodig om de clienttoepassingen en hulpprogramma's verbinding maken met Power BI Premium-werkruimten. De clientbibliotheken gebruikt voor verbinding met Analysis Services worden ook ondersteund in Power BI Premium. Microsoft-clienttoepassingen, zoals Excel, SQL Server Management Studio (SSMS) en SQL Server Data Tools (SSDT) Installeer alle drie deze clientbibliotheken en werken ze samen met de reguliere toepassingsupdates. In sommige gevallen, met name met externe toepassingen en hulpprogramma's, moet u mogelijk nieuwere versies van de clientbibliotheken installeren. Clientbibliotheken worden maandelijks bijgewerkt. Zie voor meer informatie, [om verbinding te maken met Analysis Services-clientbibliotheken](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers).

## <a name="connecting-to-a-premium-workspace"></a>Verbinding maken met een Premium-werkruimte

U kunt verbinding maken met werkruimten die zijn toegewezen aan toegewezen Premium-capaciteit. Werkruimten die zijn toegewezen aan een toegewezen capaciteit hebben een verbindingsreeks in URL-indeling. 

In de verbindingsreeks van de werkruimte in Power BI kunt ophalen **werkruimte instellingen**op de **Premium** tabblad, in **werkruimte verbinding**, klikt u op **kopiëren**.

![Werkruimte-verbindingsreeks](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

Werkruimte-verbindingen gebruiken de volgende URL-indeling om een werkruimte alsof het naam van een Analysis Services-server:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

Bijvoorbeeld: `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`
> [!NOTE]
> `[workspace name]` geval gevoelige en kunnen spaties bevatten. 

### <a name="to-connect-in-ssms"></a>In SSMS verbinding kunnen maken

In **verbinding maken met Server** > **servertype**, selecteer **Analysis Services**. In **servernaam**, voert u de URL. In **verificatie**, selecteer **Active Directory - Universal met ondersteuning voor MFA**, en klik vervolgens in **gebruikersnaam**, Voer uw organisatie gebruikers-ID. 

Wanneer de verbinding is gemaakt, de werkruimte wordt weergegeven als een Analysis Services-server en gegevenssets in de werkruimte worden weergegeven als databases.  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>Oorspronkelijke catalogus

Sommige hulpmiddelen, zoals SQL Server Profiler, moet u mogelijk om op te geven een *Initial Catalog*. Geef een gegevensset (database) in uw werkruimte. In **verbinding maken met Server**, klikt u op **opties**. In de **verbinding maken met Server** dialoogvenster op de **verbindingseigenschappen** tabblad, in **verbinding maken met database**, voer de naam van de gegevensset.

### <a name="duplicate-workspace-name"></a>Dubbele naam van de werkruimte

Wanneer u verbinding maakt met een werkruimte met dezelfde naam als een andere werkruimte, krijgt u mogelijk de volgende fout: **Kan geen verbinding met powerbi://api.powerbi.com/v1.0/ [tenantnaam] / [workspace name].**

Geef de ObjectIDGuid, die kan worden gekopieerd vanuit de werkruimte-id in de URL als u lost deze fout, naast de naam van de werkruimte. De object-id toevoegen aan de verbindings-URL. Bijvoorbeeld 'powerbi://api.powerbi.com/v1.0/myorg/Contoso verkoop - 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>Dubbele naam van gegevensset

Bij het verbinden met een gegevensset met dezelfde naam als een andere gegevensset in dezelfde werkruimte, moet u de gegevensset-guid toevoegen aan de naam van de gegevensset. U kunt beide gegevenssetnaam ophalen *en* guid wanneer verbonden met de werkruimte in SSMS. 

### <a name="delay-in-datasets-shown"></a>Vertraging in de gegevenssets die worden weergegeven

Wanneer u verbinding maakt met een werkruimte, kunnen tot vijf minuten worden weergegeven duren voordat wijzigingen van de nieuwe, verwijderde en hernoemd gegevenssets. 

### <a name="unsupported-datasets"></a>Niet-ondersteunde gegevenssets

De volgende gegevenssets zijn niet toegankelijk met behulp van XMLA-eindpunten. Deze gegevenssets *niet* worden weergegeven onder de werkruimte in SSMS of in andere hulpprogramma's: 

- Gegevenssets met een Live-verbinding met een Analysis Services-modellen. 
- Gegevenssets met gegevens pushen met behulp van de REST-API.
- Excel-werkmap gegevenssets. 

De volgende gegevenssets worden niet ondersteund in Power BI-service:   

- Gegevenssets met een Live-verbinding met een Power BI-gegevensset.

## <a name="audit-logs"></a>Auditlogboeken 

Clienttoepassingen en hulpprogramma's verbinding met een werkruimte maakt, toegang via XMLA-eindpunten wordt geregistreerd in de Power BI-auditlogboeken onder de **GetWorkspaces** bewerking. Zie voor meer informatie, [Auditing Power BI](service-admin-auditing.md).

## <a name="see-also"></a>Zie ook

[Analysis Services-verwijzingen](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services Tabular Protocol](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[Dynamische beheerweergave (DMV's)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
