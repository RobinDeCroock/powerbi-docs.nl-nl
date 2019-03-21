---
title: Auditing gebruiken binnen uw organisatie
description: Lees hier meer over de manier waarop u auditing kunt gebruiken met Power BI om uitgevoerde acties te controleren en onderzoeken. U kunt de app Beveiliging- en compliance gebruiken of PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 59916f904c2905a6858e0c20a67a2c0eae9e8cca
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2019
ms.locfileid: "57980399"
---
# <a name="using-auditing-within-your-organization"></a>Auditing gebruiken binnen uw organisatie

Weten wie welke actie uitvoert op een item in uw Power BI-tenant kan essentieel zijn om uw organisatie te helpen te voldoen aan de vereisten, zoals het voldoen aan regelgeving en archiefbeheer. Gebruik Power BI-controles om acties van gebruikers te controleren, zoals Rapport weergegeven en Dashboard weergeven. U kunt de controlefunctie niet gebruiken om machtigingen te controleren.

U voert controles uit in het Office 365-centrum voor beveiliging en naleving of u gebruikt PowerShell. Controles zijn afhankelijk van de functionaliteit in Exchange Online, dat automatisch is ingericht ter ondersteuning van Power BI.

U kunt de auditgegevens filteren op datumbereik, gebruiker, dashboard, rapport, gegevensset en soort activiteit. U kunt de activiteiten ook downloaden in een CSV-bestand (bestand met door komma's gescheiden waarden) om de gegevens offline te analyseren.

## <a name="requirements"></a>Vereisten

U moet aan deze vereisten voldoen voor toegang tot de auditlogboeken:

* U moet een globale beheerder zijn of u moet de rol Auditlogboeken of Auditlogboeken alleen-lezen in Exchange Online hebben voor toegang tot het auditlogboek. Standaard zijn deze rollen toegewezen aan de rolgroepen Nalevingsbeheer en Organisatiebeheer op de pagina **Machtigingen** in het Exchange-beheercentrum.

    Als u niet-beheerdersaccounts toegang wilt geven tot de auditlogboeken, moet u de gebruiker als lid van een van deze rolgroepen toevoegen. U kunt anders ook een aangepaste rolgroep maken in het Exchange-beheercentrum, de rollen Auditlogboeken of Auditlogboeken alleen-lezen aan deze groep toewijzen en vervolgens het niet-beheerdersaccount toewijzen aan de nieuwe rolgroep. Raadpleeg [Rolgroepen beheren in Exchange Online](/Exchange/permissions-exo/role-groups) voor meer informatie.

    Als u geen toegang hebt tot het Exchange-beheercentrum vanuit het Office 365-beheercentrum, gaat u naar https://outlook.office365.com/ecp en meldt u zich aan met uw referenties.

* Als u wel toegang tot het auditlogboek hebt maar geen algemene beheerder of beheerder van de Power BI-service bent, krijgt u geen toegang tot het beheerportal van Power BI. In dit geval moet u een rechtstreekse koppeling gebruiken naar het [Office 365-centrum voor beveiliging en naleving](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="accessing-your-audit-logs"></a>Auditlogboeken raadplegen

Zorg ervoor dat logboekregistratie in Power BI is ingeschakeld als u de logboeken wilt raadplegen. Raadpleeg voor meer informatie [Auditlogboeken](service-admin-portal.md#audit-logs) in de documentatie voor de beheerportal. Er kan een vertraging tot 48 uur bestaan tussen het inschakelen van de controlefunctie en het kunnen weergeven van controlegegevens. Als u niet direct gegevens ziet, controleert u de controlelogboeken op een later tijdstip. Er kan een vergelijkbare vertraging optreden tussen het ophalen van machtiging voor het weergeven van controlelogboeken en het kunnen openen van de logboeken.

De Power BI-auditlogboeken zijn rechtstreeks beschikbaar via het [Office 365-centrum voor beveiliging en naleving](https://sip.protection.office.com/#/unifiedauditlog). Er is ook een koppeling vanuit de Power BI-beheerportal:

1. Selecteer in Power BI rechtsboven het **tandwielpictogram** en selecteer vervolgens **Beheerportal**.

   ![Beheerportal](media/service-admin-auditing/powerbi-admin.png)

1. Selecteer **Auditlogboeken**.

1. Selecteer **Naar het Office 365-beheercentrum**.

   ![Naar het beheercentrum van O365](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Alleen Power BI activiteiten zoeken

Volg deze stappen om de resultaten te beperken tot alleen Power BI-activiteiten. Raadpleeg voor een lijst activiteiten de [Lijst van activiteiten die worden gecontroleerd door Power BI](#activities-audited-by-power-bi). Deze lijst staat verderop in dit artikel.

1. Klik op de pagina **Auditlogboeken zoeken** onder **Zoeken** op de pijl omlaag bij **Activiteiten**.

2. Selecteer **Power BI-activiteiten**.

   ![Zoeken in auditlogboeken](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Maak een selectie buiten de vervolgkeuzelijst om deze te sluiten.

Uw zoekopdrachten worden nu gefilterd op alleen Power BI-activiteiten.

## <a name="search-the-audit-logs-by-date"></a>Op datum zoeken in auditlogboeken

U kunt op datumbereik zoeken in de logboeken met behulp van de velden **Begindatum** en **Einddatum**. De afgelopen zeven dagen zijn standaard geselecteerd. De datum en tijd worden weergegeven in de UTC-notatie (Coordinated Universal Time). Het maximale datumbereik dat u kunt opgeven is 90 dagen. 

Er wordt een fout weergegeven als het geselecteerde datumbereik groter is dan 90 dagen. Als u het maximale datumbereik van 90 dagen gebruikt, selecteert u de huidige tijd voor **Begindatum**. Anders krijgt u een foutmelding met de mededeling dat de begindatum voor de einddatum valt. Als u controles hebt ingeschakeld in de afgelopen 90 dagen, kan het datumbereik niet beginnen voor de datum waarop controles zijn ingeschakeld.

![Zoeken op datum](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Op gebruiker zoeken in auditlogboeken

U kunt zoeken naar vermeldingen in het auditlogboek voor activiteiten die zijn uitgevoerd door specifieke gebruikers. Hiervoor typt u een of meer gebruikersnamen in het veld **Gebruikers**. De gebruikersnaam ziet eruit als een e-mailadres: het is het account waarmee gebruikers zich aanmelden bij Power BI. Laat dit vak leeg om vermeldingen weer te geven voor alle gebruikers (en serviceaccounts) in uw organisatie.

![Zoeken op gebruikers](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Zoekresultaten weergeven

Nadat u **Zoeken** selecteert, worden de zoekresultaten geladen en ziet u deze na een paar seconden onder **Resultaten**. Wanneer de zoekopdracht is voltooid, wordt het aantal gevonden resultaten weergegeven. Er worden maximaal 1000 gebeurtenissen weergegeven. Als er meer dan 1000 gebeurtenissen aan de zoekcriteria voldoen, worden de 1000 nieuwste gebeurtenissen weergegeven.

### <a name="view-the-main-results"></a>De belangrijkste resultaten bekijken

Het gebied **Resultaten** bevat de volgende informatie voor elke gebeurtenis die door de zoekopdracht is geretourneerd. Selecteer een kolomkop onder **Resultaten** om de resultaten te sorteren.

| **Kolom** | **Beschrijving** |
| --- | --- |
| Datum |De datum en tijd (in UTC-notatie) wanneer de gebeurtenis heeft plaatsgevonden. |
| IP-adres |Het IP-adres van het apparaat waarmee de activiteit is uitgevoerd. Het IP-adres wordt weergegeven in de IPv4- of IPv6-adresindeling. |
| Gebruiker |De gebruiker (of het serviceaccount) die de actie heeft uitgevoerd die de gebeurtenis heeft veroorzaakt. |
| Activiteit |De activiteit die is uitgevoerd door de gebruiker. Deze waarde komt overeen met de activiteiten die u hebt geselecteerd in de vervolgkeuzelijst **Activiteiten**. Voor een gebeurtenis uit het auditlogboek van de Exchange-beheerder is de waarde in deze kolom een Exchange-cmdlet. |
| Item |Het object dat is gemaakt of gewijzigd als gevolg van de bijbehorende activiteit. Dit kan het bestand zijn dat is weergegeven of gewijzigd, of het gebruikersaccount dat is bijgewerkt. Niet alle activiteiten hebben een waarde in deze kolom. |
| Detail |Aanvullende details van een activiteit. Niet alle activiteiten hebben een waarde in deze kolom. |

### <a name="view-the-details-for-an-event"></a>Details van een gebeurtenis bekijken

U kunt meer informatie over een gebeurtenis bekijken door op de record van de gebeurtenis te klikken in de lijst met zoekresultaten. De pagina **Details** verschijnt met de gedetailleerde eigenschappen uit de gebeurtenisrecord. De eigenschappen die worden weergegeven, zijn afhankelijk van de Office 365-service waarin de gebeurtenis zich voordoet. 

Als u deze informatie wilt weergeven, selecteert u **Meer informatie**. Alle Power BI-vermeldingen hebben een waarde van 20 voor de eigenschap RecordType. Voor informatie over andere eigenschappen raadpleegt u [Gedetailleerde eigenschappen in het auditlogboek](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Details controleren](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Zoekresultaten exporteren

Als u het Power BI-auditlogboek als een csv-bestand wilt exporteren, volgt u deze stappen.

1. Selecteer **Resultaten exporteren**.

1. Selecteer **Geladen resultaten opslaan** of **Alle resultaten downloaden**.

    ![Resultaten exporteren](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Gebruik PowerShell om naar auditlogboeken te zoeken

U kunt PowerShell ook gebruiken om toegang tot de auditlogboeken te krijgen op basis van uw aanmeldingsgegevens. In het volgende voorbeeld ziet u hoe u verbinding maakt met Exchange Online PowerShell en vervolgens de opdracht [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) gebruikt om vermeldingen van Power BI-auditlogboeken op te halen. U moet de juiste machtigingen hebben om het script uit te voeren, zoals staat beschreven in de sectie [Vereisten](#requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Zie [Connect to Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/) (Verbinding maken met Exchange Online PowerShell) voor meer informatie over het maken van verbinding met Exchange Online. Voor een ander voorbeeld van hoe u PowerShell met auditlogboeken gebruikt, raadpleegt u [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Power BI-auditlogboeken en PowerShell gebruiken om Power BI Pro-licenties toe te wijzen).

## <a name="activities-audited-by-power-bi"></a>Activiteiten die worden gecontroleerd door Power BI

De volgende activiteiten worden gecontroleerd door Power BI.

| Beschrijvende naam                                     | Naam van bewerking                              | Opmerkingen                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Gegevensbron toegevoegd aan Power BI-gateway             | AddDatasourceToGateway                      |                                          |
| Toegang tot Power BI-map toegevoegd                      | AddFolderAccess                             | Momenteel niet gebruikt                       |
| Power BI-groepsleden toegevoegd                      | AddGroupMembers                             |                                          |
| Opslagaccount van gegevensstroom door beheerder aan tenant gekoppeld | AdminAttachedDataflowStorageAccountToTenant | Momenteel niet gebruikt                       |
| Power BI-gegevensset geanalyseerd                         | AnalyzedByExternalApplication               |                                          |
| Power BI-rapport geanalyseerd                          | AnalyzeInExcel                              |                                          |
| Verbonden Power BI-gegevensset aan gateway                | BindToGateway                               |                                          |
| Status van de capaciteit gewijzigd                            | ChangeCapacityState                         |                                          |
| Toewijzing van gebruiker van capaciteit gewijzigd                  | UpdateCapacityUsersAssignment               |                                          |
| Power BI-gegevenssetverbindingen gewijzigd              | SetAllConnections                           |                                          |
| Beheerders Power BI-gateway gewijzigd                   | ChangeGatewayAdministrators                 |                                          |
| Gebruikers van de Power BI-gateway-gegevensbron gewijzigd        | ChangeGatewayDatasourceUsers                |                                          |
| Organisatie-inhoudspakket voor Power BI gemaakt      | CreateOrgApp                                |                                          |
| Power BI-app gemaakt                              | CreateApp                                   |                                          |
| Power BI-dashboard gemaakt                        | CreateDashboard                             |                                          |
| Power BI-gegevensstroom gemaakt                         | CreateDataflow                              |                                          |
| Power BI-gegevensset gemaakt                          | CreateDataset                               |                                          |
| Power BI-e-mailabonnement gemaakt               | CreateEmailSubscription                     |                                          |
| Power BI-map gemaakt                           | CreateFolder                                |                                          |
| Power BI Gateway gemaakt                          | CreateGateway                               |                                          |
| Power BI-groep gemaakt                            | CreateGroup                                 |                                          |
| Power BI-rapport gemaakt                           | CreateReport                                |                                          |
| Gegevensstroom gemigreerd naar extern opslagaccount     | DataflowMigratedToExternalStorageAccount    | Momenteel niet gebruikt                       |
| Machtigingen voor gegevensstroom toegevoegd                        | DataflowPermissionsAdded                    | Momenteel niet gebruikt                       |
| Machtigingen voor gegevensstroom verwijderd                      | DataflowPermissionsRemoved                  | Momenteel niet gebruikt                       |
| Organisatie-inhoudspakket voor Power BI verwijderd      | DeleteOrgApp                                |                                          |
| Power BI-opmerking verwijderd                          | DeleteComment                               |                                          |
| Power BI-dashboard verwijderd                        | DeleteDashboard                             | Momenteel niet gebruikt                       |
| Power BI-gegevensstroom verwijderd                         | DeleteDataflow                              | Momenteel niet gebruikt                       |
| Power BI-gegevensset verwijderd                          | DeleteDataset                               |                                          |
| Power BI-e-mailabonnement verwijderd               | DeleteEmailSubscription                     |                                          |
| Power BI-map verwijderd                           | DeleteFolder                                |                                          |
| Toegang tot Power BI-map verwijderd                    | DeleteFolderAccess                          | Momenteel niet gebruikt                       |
| Power BI Gateway verwijderd                          | DeleteGateway                               |                                          |
| Power BI-groep verwijderd                            | DeleteGroup                                 |                                          |
| Power BI-rapport verwijderd                           | DeleteReport                                |                                          |
| Gegevensbronnen voor Power BI-gegevensset gedetecteerd          | GetDatasources                              |                                          |
| Power BI-rapport gedownload                        | DownloadReport                              |                                          |
| Machtiging voor Power BI-certificering bewerkt          | EditCertificationPermission                 | Momenteel niet gebruikt                       |
| Power BI-dashboard bewerkt                         | EditDashboard                               | Momenteel niet gebruikt                       |
| Power BI-gegevensset bewerkt                           | EditDataset                                 |                                          |
| Eigenschappen van Power BI-gegevensset bewerkt                | EditDatasetProperties                       | Momenteel niet gebruikt                       |
| Power BI-rapport bewerkt                            | EditReport                                  |                                          |
| Power BI-gegevensstroom geëxporteerd                        | ExportDataflow                              |                                          |
| Visuele gegevens van Power BI-rapport geëxporteerd              | ExportReport                                |                                          |
| Power BI-tegelgegevens geëxporteerd                       | ExportTile                                  |                                          |
| Kan machtigingen voor gegevensstroom niet toevoegen                | FailedToAddDataflowPermissions              | Momenteel niet gebruikt                       |
| Kan machtigingen voor gegevensstroom niet verwijderen             | FailedToRemoveDataflowPermissions           | Momenteel niet gebruikt                       |
| SAS-token van Power BI-gegevensstroom gegenereerd             | GenerateDataflowSasToken                    |                                          |
| Power BI-insluittoken gegenereerd                    | GenerateEmbedToken                          |                                          |
| Bestand naar Power BI geïmporteerd                         | Importeren                                      |                                          |
| Power BI-app geïnstalleerd                            | InstallApp                                  |                                          |
| Werkruimte gemigreerd naar een capaciteit                  | MigrateWorkspaceIntoCapacity                |                                          |
| Power BI-opmerking geplaatst                           | PostComment                                 |                                          |
| Power BI-dashboard afgedrukt                        | PrintDashboard                              |                                          |
| Pagina van Power BI-rapport afgedrukt                      | PrintReport                                 |                                          |
| Power BI-rapport gepubliceerd op internet                  | PublishToWebReport                          |                                          |
| Geheim van Power BI-gegevensstroom ontvangen uit Key Vault  | ReceiveDataflowSecretFromKeyVault           | Momenteel niet gebruikt                       |
| Gegevensbron verwijderd uit Power BI-gateway         | RemoveDatasourceFromGateway                 |                                          |
| Power BI-groepsleden verwijderd                    | DeleteGroupMembers                          |                                          |
| Werkruimte uit een capaciteit verwijderd                 | RemoveWorkspacesFromCapacity                |                                          |
| Power BI-dashboard hernoemd                        | RenameDashboard                             |                                          |
| Vernieuwing van Power BI-gegevensstroom aangevraagd               | RequestDataflowRefresh                      | Momenteel niet gebruikt                       |
| Vernieuwing van Power BI-gegevensset aangevraagd                | RefreshDataset                              |                                          |
| Power BI-werkruimten opgehaald                     | GetWorkspaces                               |                                          |
| Geplande vernieuwing van Power BI-gegevensstroom ingesteld        | SetScheduledRefreshOnDataflow               |                                          |
| Geplande vernieuwing van Power BI-gegevensset ingesteld         | SetScheduledRefresh                         |                                          |
| Power BI-dashboard gedeeld                         | ShareDashboard                              |                                          |
| Power BI-rapport gedeeld                            | ShareReport                                 |                                          |
| Verlengde proefversie Power BI gestart                   | OptInForExtendedProTrial                    | Momenteel niet gebruikt                       |
| Proefversie van Power BI gestart                            | OptInForProTrial                            |                                          |
| Power BI-gegevensbron overgenomen                   | TakeOverDatasource                          |                                          |
| Power BI-gegevensset overgenomen                        | TakeOverDataset                             |                                          |
| Publicatie van Power BI-app ongedaan gemaakt                          | UnpublishApp                                |                                          |
| Instellingen voor capaciteitbeheer bijwerken      | UpdateCapacityResourceGovernanceSettings    | Momenteel niet beschikbaar in de Office 365-beheerportal |
| Capaciteitsbeheerder bijgewerkt                            | UpdateCapacityAdmins                        |                                          |
| Weergavenaam van de capaciteit bijgewerkt                     | UpdateCapacityDisplayName                   |                                          |
| Power BI-instellingen van organisatie bijgewerkt          | UpdatedAdminFeatureSwitch                   |                                          |
| Power BI-app bijgewerkt                              | UpdateApp                                   |                                          |
| Power BI-gegevensstroom bijgewerkt                         | UpdateDataflow                              |                                          |
| Gegevensbronnen voor Power BI-gegevensset bijgewerkt             | UpdateDatasources                           |                                          |
| Parameters van Power BI-gegevensset bijgewerkt               | UpdateDatasetParameters                     |                                          |
| Power BI-e-mailabonnement bijgewerkt               | UpdateEmailSubscription                     |                                          |
| Power BI-map bijgewerkt                           | UpdateFolder                                |                                          |
| Toegang tot Power BI-map bijgewerkt                    | UpdateFolderAccess                          |                                          |
| Referenties van gegevensbron van Power BI-gateway bijgewerkt  | UpdateDatasourceCredentials                 |                                          |
| Power BI-dashboard bekeken                         | ViewDashboard                               |                                          |
| Power BI-gegevensstroom bekeken                          | ViewDataflow                                |                                          |
| Power BI-rapport bekeken                            | ViewReport                                  |                                          |
| Power BI-tegel bekeken                              | ViewTile                                    |                                          |
| Metrische gegevens over Power BI-gebruik bekeken                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Volgende stappen

[Wat is Power BI-beheer?](service-admin-administering-power-bi-in-your-organization.md)  

[Power BI-beheerportal](service-admin-portal.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)
