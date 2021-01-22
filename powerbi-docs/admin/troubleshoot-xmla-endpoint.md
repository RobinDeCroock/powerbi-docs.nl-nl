---
title: Problemen met connectiviteit van XMLA-eindpunten in Power BI oplossen
description: Hierin wordt beschreven hoe u problemen met connectiviteit van het XMLA-eindpunt in Power BI Premium oplost.
author: Minewiskan
ms.author: kfollis
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 01/13/2021
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 0753a9c3d5b832275f65ac11b87f90c38606f289
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226980"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Problemen met connectiviteit van XMLA-eindpunten oplossen

XMLA-eindpunten in Power BI Premium zijn afhankelijk van het systeemeigen Analysis Services-communicatieprotocol voor toegang tot Power BI-gegevenssets. Daarom is het oplossen van een probleem met een XMLA-eindpunt vrijwel hetzelfde als het oplossen van probleem met een typische Analysis Services-verbinding. Er zijn echter enkele verschillen rond Power BI-specifieke afhankelijkheden van toepassing.

## <a name="before-you-begin"></a>Voordat u begint

Voordat u een probleem met een XMLA-eindpunt oplost, moet u de basisbeginselen in [Gegevenssetverbinding met het XMLA-eindpunt](service-premium-connect-tools.md) lezen. De meestvoorkomende use-cases voor het XMLA-eindpunt worden daarin besproken. Andere Power BI-gidsen voor probleemoplossing, zoals [Problemen met gateways oplossen - Power BI](../connect-data/service-gateway-onprem-tshoot.md) en [Problemen met Analyseren in Excel oplossen](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), kunnen ook handig zijn.

## <a name="enabling-the-xmla-endpoint"></a>Het XMLA-eindpunt inschakelen

Het XMLA-eindpunt kan worden ingeschakeld op zowel Power BI Premium- als Power BI Embedded-capaciteit. Op kleinere capaciteiten, zoals een A1-capaciteit met slechts 2,5 GB geheugen, kan er een fout optreden in capaciteitsinstellingen wanneer u het XMLA-eindpunt instelt op **Lezen/schrijven** en vervolgens **Toepassen** selecteert. U krijgt de foutmelding 'Er is een probleem met uw workloadinstellingen. Probeer het over enkele minuten opnieuw.'

U kunt de volgende dingen proberen:

- Beperk het geheugengebruik van andere services op de capaciteit, zoals Gegevensstromen, tot 40% of minder, of schakel onnodige services volledig uit.  
- Voer een upgrade van de capaciteit uit naar een grotere SKU. Als u bijvoorbeeld een upgrade van een A1-capaciteit naar een A3-capaciteit uitvoert, wordt dit configuratieprobleem opgelost zonder dat u Gegevensstromen hoeft uit te schakelen.

U moet ook de [instelling Gegevens exporteren](service-premium-connect-tools.md#security) op tenantniveau inschakelen in de Power BI-beheerportal. Deze instelling is ook vereist voor de functie Analyseren in Excel.

## <a name="establishing-a-client-connection"></a>Een clientverbinding tot stand brengen

Nadat het XMLA-eindpunt is ingeschakeld, is het een goed idee om de connectiviteit met een werkruimte op de capaciteit te testen. Zie [Verbinding maken met een Premium-werkruimte](service-premium-connect-tools.md#connecting-to-a-premium-workspace) voor meer informatie. Lees ook de sectie [Verbindingsvereisten](service-premium-connect-tools.md#connection-requirements) voor nuttige tips en informatie over actuele beperkingen voor XMLA-connectiviteit.

### <a name="connecting-with-a-service-principal"></a>Aanmelden met een service-principal

Als u tenantinstellingen hebt ingeschakeld zodat service-principals Power BI-API's kunnen gebruiken, zoals beschreven in [Service-principals inschakelen](service-premium-service-principal.md#enable-service-principals), kunt u verbinding maken met een XMLA-eindpunt met behulp van een service-principal. Bedenk dat voor de service-principal hetzelfde niveau van toegangsmachtigingen vereist is op het niveau van de werkruimte of gegevensset als voor normale gebruikers.

Als u een service-principal wilt gebruiken, moet u de toepassings-id-informatie in de verbindingsreeks opgeven als:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Bijvoorbeeld:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Mogelijk wordt de volgende fout weergegeven:

'Er kan geen verbinding worden gemaakt met de gegevensset vanwege onvolledige accountgegevens. Voor service-principals moet u de tenant-id samen met de app-id opgeven met behulp van de indelings-app:\<appId>@\<tenantId>. Probeer het vervolgens opnieuw.'

Zorg ervoor dat u de tenant-id samen met de app-id opgeeft in de juiste indeling.

U mag ook de app-id opgeven zonder de tenant-id. In dat geval moet u wel de alias `myorg` in de gegevensbron-URL vervangen door de werkelijke tenant-id. Zo kan Power BI de service-principal vinden in de juiste tenant. Maar als best practice gebruikt u de alias `myorg` en geeft u de tenant-ID samen met de app-id op in de parameter voor de gebruikers-id.

### <a name="connecting-with-azure-active-directory-b2b"></a>Verbinding maken met Azure Active Directory B2B

Met ondersteuning voor Azure Active Directory (Azure AD) Business-to-Business (B2B) in Power BI kunt u externe gastgebruikers toegang bieden tot gegevenssets via het XMLA-eindpunt. Zorg ervoor dat de instelling [Inhoud delen met externe gebruikers](service-admin-portal.md#export-and-sharing-settings) is ingeschakeld in de Power BI-beheerportal. Zie [Power BI-inhoud met Azure AD B2B distribueren naar externe gastgebruikers](service-admin-azure-ad-b2b.md) voor meer informatie.

## <a name="deploying-a-dataset"></a>Een gegevensset implementeren

U kunt een tabellair modelproject in Visual Studio (SSDT) op vrijwel dezelfde manier implementeren naar een Power BI Premium-werkruimte als naar Azure Analysis Services. Bij een implementatie naar een Power BI Premium-werkruimte zijn er echter enkele aanvullende overwegingen. Raadpleeg de sectie [Modelprojecten implementeren vanuit Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) in het artikel Gegevenssetconnectiviteit met het XMLA-eindpunt.

### <a name="deploying-a-new-model"></a>Een nieuw model implementeren

In de standaardconfiguratie probeert Visual Studio het model te verwerken als onderdeel van de implementatiebewerking om gegevens in de gegevensset van de gegevensbronnen te laden. Zoals beschreven in [Modelprojecten implementeren vanuit Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), kan deze bewerking mislukken omdat de gegevensbronreferenties niet kunnen worden opgegeven als onderdeel van de implementatiebewerking. Als de referenties voor uw gegevensbron nog niet zijn gedefinieerd voor een van de bestaande gegevenssets, moet u de gegevensbronreferenties opgeven in de instellingen van de gegevensset met behulp van de Power BI gebruikersinterface (**Gegevenssets** > **Instellingen** > **Referenties voor gegevensbron** > **Referenties bewerken**). Als u de referenties voor de gegevensbron hebt gedefinieerd, kan Power BI deze automatisch toepassen op elke nieuwe gegevensset nadat de metagegevens zijn geïmplementeerd en de gegevensset is gemaakt.

Als Power BI uw nieuwe gegevensset niet aan de referenties van de gegevensbron kunt binden, ontvangt u het foutbericht 'De database kan niet worden verwerkt. Reden: Kan de aanpassingen niet op de server opslaan.' met de foutcode DMTS_DatasourceHasNoCredentialError, zoals hieronder wordt weergegeven:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Modelimplementatiefout":::

Als u de verwerkingsfout wilt voorkomen, stelt u **Implementatieopties** > **Verwerkingsopties** in op **Niet verwerken**, zoals wordt weergegeven in de volgende afbeelding. In Visual Studio worden vervolgens alleen metagegevens geïmplementeerd. U kunt vervolgens de referenties voor de gegevensbron configureren en op **Nu vernieuwen** klikken voor de gegevensset in de Power BI-gebruikersinterface. Zie de sectie [Een gegevensset vernieuwen](#refreshing-a-dataset) verderop in dit artikel voor informatie over het oplossen van verwerkingsproblemen.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Optie Niet verwerken":::

### <a name="new-project-from-an-existing-dataset"></a>Nieuw project op basis van een bestaande gegevensset

Het maken van een nieuw tabellair project in Visual Studio door het importeren van de metagegevens uit een bestaande gegevensset op een Power BI Premium-werkruimte wordt niet ondersteund. U kunt echter verbinding maken met de gegevensset met behulp van SQL Server Management Studio, de metagegevens opnemen in een script en opnieuw gebruiken in andere tabellaire projecten.

## <a name="migrating-a-dataset-to-power-bi"></a>Een gegevensset migreren naar Power BI

Het is raadzaam om het compatibiliteitsniveau 1500 (of hoger) voor tabellaire modellen op te geven. Dit compatibiliteitsniveau ondersteunt de meeste mogelijkheden en gegevensbrontypen. Latere compatibiliteitsniveaus zijn achterwaarts compatibel met eerdere niveaus.

### <a name="supported-data-providers"></a>Ondersteunde gegevensproviders

Op het compatibiliteitsniveau 1500 worden de volgende typen gegevensbronnen ondersteund in Power BI:

- Gegevensbronnen van providers (verouderd met een verbindingsreeks in de metagegevens van het model).
- Gestructureerde gegevensbronnen (geïntroduceerd met het compatibiliteitsniveau 1400).
- Inline M-declaraties van gegevensbronnen (zoals Power BI Desktop ze declareert).

Het is raadzaam om gestructureerde gegevensbronnen te gebruiken, die door Visual Studio standaard worden gemaakt bij het doorlopen van de gegevensstroom Importeren. Als u echter van plan bent om een bestaand model te migreren naar Power BI waarin gebruik wordt gemaakt van een gegevensbron van een provider, moet u ervoor zorgen dat het een gegevensbron van een ondersteunde gegevensprovider is. Bijvoorbeeld, het Microsoft OLE DB-stuurprogramma voor SQL Server en eventuele externe ODBC-stuurprogramma's. Voor het OLE DB-stuurprogramma voor SQL Server moet u de definitie van de gegevensbron overschakelen naar de .NET Framework-gegevensprovider voor SQL Server. Voor externe ODBC-stuurprogramma's die mogelijk niet beschikbaar zijn in de Power BI-service, moet u overschakelen naar een gestructureerde gegevensbrondefinitie.

U wordt ook aangeraden het verouderde Microsoft OLE DB-stuurprogramma voor SQL Server (SQLNCLI11) in uw SQL Server-gegevensbrondefinities te vervangen door de .NET Framework-gegevensprovider voor SQL Server.

De volgende tabel bevat een voorbeeld van verbindingsreeks voor een .NET Framework-gegevensprovider voor SQL Server ter vervanging van een verbindingsreeks voor het OLE DB-stuurprogramma voor SQL Server.

|OLE DB-stuurprogramma voor SQL Server  |.NET Framework-gegevensprovider voor SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Kruislings verwijzen naar partitiebronnen

Net zoals er meerdere typen gegevensbronnen zijn, zijn er ook meerdere typen partitiebronnen die in een tabellair model kunnen worden opgenomen om gegevens te importeren in een tabel. Met name een partitie kan een querypartitiebron of een M-partitiebron gebruiken. Deze partitiebrontypen kunnen op hun beurt verwijzen naar gegevensbronnen van providers of gestructureerde gegevensbronnen. Hoewel in tabellaire modellen in Azure Analysis Services kruislingse verwijzingen naar deze verschillende gegevensbronnen en partitietypen worden ondersteund, wordt in Power BI een strengere relatie afgedwongen. Querypartitiebronnen moeten verwijzen naar providergegevensbronnen, en M-partitiebronnen moeten verwijzen naar gestructureerde gegevensbronnen. Anders combinaties worden niet ondersteund in Power BI. In de volgende tabel worden de ondersteunde configuraties beschreven voor het migreren van een gegevensset met kruislingse verwijzingen:  

|Gegevensbron   |Partitiebron   |Opmerkingen   |Ondersteund in Power BI Premium met een XMLA-eindpunt   |
|---------|---------|---------|---------|
|Providergegevensbron      |   Querypartitiebron      |   De AS-engine gebruikt de op cartridges gebaseerde connectiviteitsstack om toegang te krijgen tot de gegevensbron.       |     Ja     |
|Providergegevensbron      |   M-partitiebron       |   De AS-engine zet de providergegevensbron om in een algemene gestructureerde gegevensbron, waarna de gegevens worden geïmporteerd met behulp van de Mashup-engine.       |    Nee     |
|Gestructureerde gegevensbron      |     Querypartitiebron     |    De AS-engine verpakt de native query op de partitiebron in een M-expressie, waarna de gegevens worden geïmporteerd met behulp van de Mashup-engine.      |    Nee     |
|Gestructureerde gegevensbron      |    M-partitiebron      |     De AS-engine gebruikt de Mashup-engine om de gegevens te importeren.     |   Ja      |

## <a name="refreshing-a-dataset"></a>Een gegevensset vernieuwen​​

Met XMLA-eindpunten kunt u vernieuwingsbewerkingen uitvoeren op tabellaire modellen en op gegevenssets die zijn gemaakt in Power BI Desktop. Zorg ervoor dat u de instelling Uitgebreide opslag opgeeft als u de laatste indeling wilt ondersteunen. Deze instelling is vereist als u verwerkingen of andere lees-/schrijfbewerkingen wilt uitvoeren met behulp van het XMLA-eindpunt. U kunt de instelling vinden in Power BI Desktop onder Preview-functies. Na het instellen publiceert u de PBIX-oplossing opnieuw naar uw Power BI Premium-werkruimte.  

Power BI retourneert de volgende fout als u een vernieuwing uitvoert via het XMLA-eindpunt op basis van een model zonder uitgebreide metagegevens: De bewerking wordt alleen ondersteund voor het model waarvoor de eigenschap DefaultPowerBIDataSourceVersion is ingesteld op PowerBI_V3 in Power BI Premium.

### <a name="data-sources-and-impersonation"></a>Gegevensbronnen en imitatie

Imitatie-instellingen die u kunt definiëren voor gegevensbronnen van providers zijn niet relevant voor Power BI. Power BI gebruikt een ander mechanisme op basis van de instellingen van de gegevensset om referenties voor gegevensbronnen te beheren. Daarom moet u **Serviceaccount** selecteren als u een providergegevensbron maakt.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Serviceaccount imiteren":::

### <a name="fine-grained-processing"></a>Verfijnde verwerking

Wanneer een geplande vernieuwing of vernieuwing op aanvraag in Power BI wordt geactiveerd, wordt doorgaans de gehele gegevensset vernieuwd. In veel gevallen is het efficiënter om selectieve vernieuwingen uit te voeren. U kunt verfijnde verwerkingstaken uitvoeren in SQL Server Management Studio (SSMS), zoals hieronder wordt weergegeven, of met behulp van hulpprogramma's of scripts van derden.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Tabellen verwerken in SSMS":::

### <a name="overrides-in-refresh-tmsl-command"></a>Onderdrukkingen in de TMSL-opdracht Vernieuwen

Met onderdrukkingen in de [opdracht Vernieuwen (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) kunnen gebruikers een andere partitiequerydefinitie of gegevensbrondefinitie voor de vernieuwingsbewerking kiezen. Momenteel worden **onderdrukkingen niet ondersteund** in Power BI Premium. De fout 'De out-of-line-binding is niet toegestaan in Power BI Premium. Zie XMLA-lees/schrijf-ondersteuning in de productdocumentatie voor meer informatie." wordt geretourneerd.

## <a name="errors-in-ssms---premium-gen-2"></a>Fouten in SQL Server Management Studio (SMS)- Premium Gen 2

### <a name="query-execution"></a>Queryuitvoering

Wanneer SQL Server Management Studio is verbonden met een werkruimte in een capaciteit van [Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview), kan de volgende fout worden weergegeven:

```
Executing the query ...
Error -1052311437:
```

Deze fout treedt op omdat de clientbibliotheken die zijn geïnstalleerd met SQL Server Management Studio v18.7.1, geen ondersteuning bieden voor sessietracering. Dit probleem wordt opgelost in SQL Server Management Studio 18.8 en hoger. [Download de nieuwste SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

### <a name="refresh-operations"></a>Bewerkingen vernieuwen

Als u SQL Server Management Studio v18.7.1 of lager gebruikt om een langdurige vernieuwingsbewerking (meer dan 1 minuut) uit te voeren op een gegevensset in een Premium Gen2-capaciteit, wordt er mogelijk een foutbericht vergelijkbaar met dat hieronder weergeven ondanks dat de vernieuwingsbewerking is voltooid:

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

Dit wordt veroorzaakt door een bekend probleem in de clientbibliotheken waarbij de status van de vernieuwingsaanvraag onjuist wordt bijgehouden. Dit probleem wordt opgelost in SQL Server Management Studio 18.8 en hoger. [Download de nieuwste SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="editing-role-memberships-in-ssms"></a>Rollidmaatschappen bewerken in SQL Server Management Studio

Bij gebruik van de SQL Server Management Studio (SSMS) v18.8 voor het bewerken van een rollidmaatschap voor een gegevensset, wordt mogelijk de volgende fout weergegeven in SSMS:

```
Failed to save modifications to the server. 
Error returned: ‘Metadata change of current operation cannot be resolved, please check the command or try again later.’ 
```

Dit wordt veroorzaakt door een bekend probleem in de REST API van de app-services. Dit probleem wordt opgelost in een volgende versie. In de tussentijd kunt u als tijdelijke oplossing in **Eigenschappen van rol** klikken op **Script** en vervolgens de volgende TMSL-opdracht invoeren en uitvoeren:

```json
{ 
  "createOrReplace": { 
    "object": { 
      "database": "AdventureWorks", 
      "role": "Role" 
    }, 
    "role": { 
      "name": "Role", 
      "modelPermission": "read", 
      "members": [ 
        { 
          "memberName": "xxxx", 
          "identityProvider": "AzureAD" 
        }, 
        { 
          "memberName": “xxxx” 
          "identityProvider": "AzureAD" 
        } 
      ] 
    } 
  } 
} 
```

## <a name="publish-error---live-connected-dataset"></a>Publicatiefout - Live verbonden gegevensset

Bij het opnieuw publiceren van een live verbonden gegevensset met behulp van de Analysis Services-connector wordt mogelijk de volgende fout weergegeven:

:::image type="content" source="media/troubleshoot-xmla-endpoint/couldnt-publish-to-power-bi.png" alt-text="Fout bij het publiceren in Power BI.":::

Zoals vermeld in het foutbericht, moet u de bestaande gegevensset verwijderen of de naam ervan wijzigen om dit probleem op te lossen. Zorg er ook voor dat u alle apps die afhankelijk zijn van het rapport opnieuw publiceert. Als dat nodig is, moeten downstreamgebruikers ook worden geïnformeerd dat ze bladwijzers moeten bijwerken met het nieuwe rapportadres om ervoor te zorgen dat ze toegang hebben tot het nieuwste rapport.  

## <a name="workspaceserver-alias"></a>Alias van de werkruimte/server

In tegenstelling tot Azure Analysis Services worden de [aliassen](/azure/analysis-services/analysis-services-server-alias) van de servernaam **niet ondersteund** voor Power BI Premium-werkruimten. 

## <a name="dataset-refresh-through-the-xmla-endpoint"></a>Gegevenssets vernieuwen via het XMLA-eindpunt

Op een aantal plekken in Power BI worden de datum en het tijdstip van de laatste vernieuwing weergegeven, zoals Vernieuwde kolommen in rapporten en lijsten, Details van de gegevensset, Gegevenssetinstellingen en Vernieuwingsgeschiedenis van de gegevensset. Momenteel bevatten de vernieuwingsdatums en -tijden in Power BI **geen** vernieuwingsbewerkingen die via het XMLA-eindpunt zijn uitgevoerd met behulp van TMSL/TOM, SSMS of externe hulpprogramma's.

## <a name="see-also"></a>Zie ook

[Gegevenssetconnectiviteit met het XMLA-eindpunt](service-premium-connect-tools.md)  
[Taken voor Premium-werkruimten en -gegevenssets automatiseren met service-principals](service-premium-service-principal.md)  
[Probleemoplossing analyseren in Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[Tabular model solution deployment](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true) (Implementatie van oplossingen met tabellaire modellen)
