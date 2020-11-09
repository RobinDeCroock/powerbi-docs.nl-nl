---
title: Uw eigen versleutelingssleutels gebruiken voor Power BI
description: Informatie over het gebruik van uw eigen versleutelingssleutels in Power BI Premium.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/13/2020
LocalizationGroup: Premium
ms.openlocfilehash: 449721a13a126344f3ef8334e63f64579a98ec20
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916148"
---
# <a name="bring-your-own-encryption-keys-for-power-bi"></a>Uw eigen versleutelingssleutels gebruiken voor Power BI

In Power BI worden gegevens _in rust_ en _in verwerking_ versleuteld. In Power BI wordt standaard gebruikgemaakt van door Microsoft beheerde sleutels om uw gegevens te versleutelen. In Power BI Premium kunt u ook uw eigen sleutels gebruiken voor gegevens in rust die worden geïmporteerd in een gegevensset (Zie [Aandachtspunten voor gegevensbronnen en opslag](#data-source-and-storage-considerations) voor meer informatie). Deze methode wordt vaak beschreven als _Bring Your Own Key_ (BYOK).

## <a name="why-use-byok"></a>Redenen om BYOK te gebruiken

Met BYOK kunt u gemakkelijker voldoen aan nalevingsvereisten waarin sleutelafspraken met de cloudserviceprovider (in dit geval Microsoft) zijn opgegeven. Met BYOK levert en beheert u de versleutelingssleutels voor uw Power BI-gegevens in rust op toepassingsniveau. Hierdoor kunt u controle uitoefenen op en de sleutels van uw organisatie intrekken als u besluit de service af te sluiten. Als u sleutels intrekt, worden de gegevens binnen dertig minuten onleesbaar voor de service.

## <a name="data-source-and-storage-considerations"></a>Aandachtspunten voor gegevensbronnen en opslag

Voor het gebruik van BYOK moet u gegevens via een Power BI Desktop-bestand (PBIX) uploaden naar de Power BI-service. U kunt BYOK niet kunt gebruiken in de volgende scenario's:

- Liveverbindingen van Analysis Services
- Excel-werkmappen (tenzij de gegevens eerst zijn geïmporteerd in Power BI Desktop)
- [Push-gegevenssets](/rest/api/power-bi/pushdatasets)
- [Streaminggegevenssets](../connect-data/service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)


BYOK is alleen van toepassing op gegevenssets. Push-gegevenssets, Excel-bestanden en CSV-bestanden die gebruikers naar de service kunnen uploaden, worden niet versleuteld met uw eigen sleutel. Gebruik de volgende PowerShell-opdracht om te bepalen welke artefacten zijn opgeslagen in uw werkruimten:

```PS C:\> Get-PowerBIWorkspace -Scope Organization -Include All```

> [!NOTE]
> Voor deze cmdlet is Power BI-beheermodule v 1.0.840 vereist. U kunt zien welke versie u hebt door Get-InstalledModule -Name MicrosoftPowerBIMgmt uit te voeren. Installeer de nieuwste versie door Install-Module -Name MicrosoftPowerBIMgmt uit te voeren. Meer informatie over de Power BI-cmdlet en de bijbehorende parameters vindt u in de [Power BI PowerShell-cmdletmodule](/powershell/power-bi/overview).

## <a name="configure-azure-key-vault"></a>Azure Key Vault configureren

In dit gedeelte krijgt u meer informatie over het configureren van Azure Key Vault, een hulpprogramma om geheimen, zoals versleutelingssleutels, veilig op te slaan en te openen. U kunt een bestaande sleutelkluis gebruiken om versleutelingssleutels op te slaan, of kunt u een nieuwe maken, specifiek voor Power BI-gebruik.

Bij de instructies in deze sectie wordt ervan uitgegaan dat u beschikt over basiskennis van Azure Key Vault. Zie [Wat is Azure Key Vault?](/azure/key-vault/key-vault-whatis) voor meer informatie. Configureer uw sleutelkluis als volgt:

1. Voeg de Power BI-service toe als een service-principal voor de sleutelkluis, met machtigingen voor verpakken en uitpakken.

1. Maak een RSA-sleutel met een lengte van 4096 bits (of gebruik een bestaande sleutel van dit type), met machtigingen voor verpakken en uitpakken.

    > [!IMPORTANT]
    > Power BI BYOK biedt alleen ondersteuning voor RSA-sleutels met een lengte van 4096 bits.

1. Aanbevolen: Controleer of de optie _Voorlopig verwijderen_ is ingeschakeld voor de sleutelkluis.

### <a name="add-the-service-principal"></a>De service-principal toevoegen

1. Selecteer in uw sleutelkluis in Azure Portal onder **Toegangsbeleid** de optie **Nieuwe toevoegen**.

1. Zoek en selecteer Microsoft.Azure.AnalysisServices onder **Principal selecteren**.

    > [!NOTE]
    > Als u 'Microsoft.Azure.AnalysisServices' niet kunt vinden, is er waarschijnlijk nooit een Power BI-resource gekoppeld aan het Azure-abonnement dat aan uw Azure Key Vault is gekoppeld. Zoek in plaats daarvan naar de volgende tekenreeks: 00000009-0000-0000-c000-000000000000.

1. Selecteer onder **sleutelmachtigingen** de opties **Sleutel uitpakken** en **Sleutel verpakken**.

    ![PBIX-bestand, service-principal selecteren en cryptografische bewerkingen](media/service-encryption-byok/service-principal.png)

1. Selecteer **OK** en vervolgens **Opslaan**.

> [!NOTE]
> Als u de toegang van Power BI tot uw gegevens wilt intrekken, verwijdert u de toegangsrechten voor deze service-principal uit Azure Key Vault.

### <a name="create-an-rsa-key"></a>Een RSA-sleutel maken

1. Selecteer in uw sleutelkluis onder **Sleutels** de optie **Genereren/importeren**.

1. Selecteer RSA als **Sleuteltype** en 4096 als **Grootte van RSA-sleutel**.

    ![Een sleutel maken met sleuteltype en -grootte gemarkeerd](media/service-encryption-byok/create-rsa-key.png)

1. Selecteer **Maken**.

1. Selecteer onder **Sleutels** de sleutel die u hebt gemaakt.

1. Selecteer de GUID voor de **Huidige versie** van de sleutel.

1. Controleer of **Sleutel verpakken** en **Sleutel uitpakken** beide zijn geselecteerd. Kopieer de te gebruiken **Sleutel-id** bij het inschakelen van BYOK in Power BI.

    ![Eigenschappen met sleutel-id en toegestane bewerkingen gemarkeerd](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>De optie Voorlopig verwijderen

Het is raadzaam [Voorlopig verwijderen](/azure/key-vault/key-vault-ovw-soft-delete) in te schakelen voor uw sleutelkluis als beveiliging tegen gegevensverlies voor het geval de sleutel of sleutelkluis per ongeluk wordt verwijderd. U moet gebruikmaken van [PowerShell om de eigenschap 'Voorlopig verwijderen' in te schakelen](/azure/key-vault/key-vault-soft-delete-powershell) voor de sleutelkluis omdat deze optie nog niet beschikbaar is via Azure Portal.

Nu Azure Key Vault correct is geconfigureerd, kunt u BYOK inschakelen voor uw tenant.

## <a name="enable-byok-on-your-tenant"></a>BYOK inschakelen voor uw tenant

U kunt BYOK op tenantniveau inschakelen met [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin) door eerst de versleutelingssleutels die u hebt gemaakt en opgeslagen in Azure Key Vault te introduceren bij uw Power BI-tenant. Vervolgens wijst u deze versleutelingssleutels per Premium-capaciteit toe om inhoud in de capaciteit te versleutelen.

### <a name="important-considerations"></a>Belangrijke overwegingen

Let op de volgende aandachtspunten voordat u BYOK inschakelt:

- Op dit moment kunt u BYOK na inschakeling niet uitschakelen. Afhankelijk van hoe u parameters voor `Add-PowerBIEncryptionKey` opgeeft, kunt u bepalen hoe u BYOK gebruikt voor een of meer van uw capaciteiten. U kunt de introductie van sleutels bij uw tenant echter niet ongedaan maken. Zie [BYOK inschakelen](#enable-byok) voor meer informatie.

- U kunt een werkruimte die gebruikmaakt van BYOK niet _rechtstreeks_ verplaatsen van een capaciteit in Power BI Premium naar een gedeelde capaciteit. U moet de werkruimte eerst verplaatsen naar een capaciteit waarvoor BYOK niet is ingeschakeld.

- Als u een werkruimte die gebruikmaakt van BYOK verplaatst van een capaciteit in Power BI Premium naar gedeelde capaciteit, worden rapporten en gegevenssets ontoegankelijk, omdat ze zijn versleuteld met de sleutel. U kunt deze situatie voorkomen door de werkruimte eerst te verplaatsen naar een capaciteit waarvoor BYOK niet is ingeschakeld.

### <a name="enable-byok"></a>BYOK inschakelen

Om BYOK te kunnen inschakelen, moet u een Power BI-beheerder zijn en zich hebben aangemeld met de cmdlet `Connect-PowerBIServiceAccount`. Gebruik vervolgens [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey) om BYOK in te schakelen, zoals weergegeven in het volgende voorbeeld:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Voer `Add-PowerBIEncryptionKey` uit met waarden voor -`-Name` en `-KeyVaultKeyUri` om meerdere sleutels toe te voegen. 

U kunt twee schakelparameters opgeven voor de cmdlet om de versleuteling voor huidige en toekomstige capaciteit te beïnvloeden. Standaard is geen van de schakelparameters ingesteld:

- `-Activate`: geeft aan dat deze sleutel wordt gebruikt voor alle bestaande capaciteiten in de tenant die nog niet zijn versleuteld.

- `-Default`: geeft aan dat deze sleutel nu de standaardwaarde voor de gehele tenant is. Als u een nieuwe capaciteit maakt, wordt deze sleutel overgenomen door de capaciteit.

> [!IMPORTANT]
> Als u `-Default` opgeeft, worden alle capaciteiten die voor uw tenant worden gemaakt vanaf dit moment versleuteld met behulp van de sleutel die u opgeeft (of een bijgewerkte standaardsleutel). U kunt de standaardbewerking niet ongedaan maken en verliest dus de mogelijkheid om een Premium-capaciteit te maken in uw tenant die niet gebruikmaakt van BYOK.

Stel na het inschakelen van BYOK in uw tenant de versleutelingssleutel voor een of meer Power BI-capaciteiten in:

1. Gebruik [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) om de vereiste capaciteits-ID voor de volgende stap op te halen.

    ```powershell
    Get-PowerBICapacity -Scope Individual
    ```

    De cmdlet retourneert uitvoer die vergelijkbaar is met de volgende uitvoer:

    ```
    Id              : xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
    DisplayName     : Test Capacity
    Admins          : adam@sometestdomain.com
    Sku             : P1
    State           : Active
    UserAccessRight : Admin
    Region          : North Central US
    ```

1. Gebruik [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) om de versleutelingssleutel in te stellen:

    ```powershell
    Set-PowerBICapacityEncryptionKey -CapacityId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -KeyName 'Contoso Sales'
    ```

U kunt zelf bepalen hoe u BYOK binnen uw tenant gebruikt. Als u bijvoorbeeld een enkele capaciteit wilt versleutelen, roept u `Add-PowerBIEncryptionKey` aan zonder `-Activate` of `-Default`. Roep vervolgens `Set-PowerBICapacityEncryptionKey` aan voor de capaciteit waarvoor u BYOK wilt inschakelen.

## <a name="manage-byok"></a>BYOK beheren

Power BI biedt aanvullende cmdlets om BYOK te beheren in uw tenant:

- Gebruik [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) om de sleutel op te halen die momenteel in gebruik is door een capaciteit:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- Gebruik [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey) om de sleutel op te halen die momenteel in gebruik is bij uw tenant:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Gebruik [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus) om te zien of de gegevenssets in een werkruimte zijn versleuteld en of de versleutelingsstatus is gesynchroniseerd met de werkruimte:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Houd er rekening mee dat versleuteling is ingeschakeld op capaciteitsniveau, maar dat u de versleutelingsstatus verkrijgt voor het gegevenssetniveau van de opgegeven werkruimte.

- Gebruik [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey) om de versie van de sleutel die voor versleuteling wordt gebruikt te wisselen (of _draaien_ ). Met deze cmdlet werkt u de `-KeyVaultKeyUri` voor een sleutel `-Name` bij:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```



## <a name="next-steps"></a>Volgende stappen

* [Power BI PowerShell-cmdletmodule](/powershell/power-bi/overview) 

* [Manieren om uw werk te delen in Power BI](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)

* [Een rapport filteren door queryreeksparameters in de URL te gebruiken](../collaborate-share/service-url-filters.md)

* [Insluiten met webonderdeel Rapport in SharePoint Online](../collaborate-share/service-embed-report-spo.md)

* [Publiceren op internet vanuit Power BI](../collaborate-share/service-publish-to-web.md)