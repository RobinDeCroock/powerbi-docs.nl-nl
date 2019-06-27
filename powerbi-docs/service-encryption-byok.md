---
title: Uw eigen versleutelingssleutels gebruiken voor Power BI (preview)
description: Informatie over het gebruik van uw eigen versleutelingssleutels in Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 7adcfeec771796aa9fe322512f8ca8584559cea0
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829383"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Uw eigen versleutelingssleutels gebruiken voor Power BI (preview)

In Power BI worden gegevens _in rust_ en _in verwerking_ versleuteld. In Power BI wordt standaard gebruikgemaakt van door Microsoft beheerde sleutels om uw gegevens te versleutelen. In Power BI Premium kunt u ook uw eigen sleutels gebruiken voor gegevens in rust die worden geïmporteerd in een gegevensset (Zie [Aandachtspunten voor gegevensbronnen en opslag](#data-source-and-storage-considerations) voor meer informatie). Deze methode wordt vaak beschreven als _Bring Your Own Key_ (BYOK).

## <a name="why-use-byok"></a>Redenen om BYOK te gebruiken

Met BYOK kunt u gemakkelijker voldoen aan nalevingsvereisten waarin sleutelafspraken met de cloudserviceprovider (in dit geval Microsoft) zijn opgegeven. Met BYOK levert en beheert u de versleutelingssleutels voor uw Power BI-gegevens in rust op toepassingsniveau. Hierdoor kunt u controle uitoefenen op en de sleutels van uw organisatie intrekken als u besluit de service af te sluiten. Door sleutels in te trekken worden de gegevens onleesbaar voor de service.

## <a name="data-source-and-storage-considerations"></a>Aandachtspunten voor gegevensbronnen en opslag

Voor het gebruik van BYOK moet u gegevens via een Power BI Desktop-bestand (PBIX) uploaden naar de Power BI-service. Wanneer u verbinding maakt met gegevensbronnen in Power BI Desktop, moet u een opslagmodus voor de invoer opgeven. U kunt BYOK niet kunt gebruiken in de volgende scenario's:

- DirectQuery
- Liveverbindingen van Analysis Services
- Excel-werkmappen (tenzij de gegevens eerst zijn geïmporteerd in Power BI Desktop)
- Push-gegevenssets

In de volgende sectie leert u hoe u Azure Key Vault configureert. Dat is de plaats waar u versleutelingssleutels voor BYOK opslaat.

## <a name="configure-azure-key-vault"></a>Azure Key Vault configureren

Azure Key Vault is een hulpprogramma om geheimen, zoals versleutelingssleutels, veilig op te slaan en te openen. U kunt een bestaande sleutelkluis gebruiken om versleutelingssleutels op te slaan, of kunt u een nieuwe maken, specifiek voor Power BI-gebruik.

Bij de instructies in deze sectie wordt ervan uitgegaan dat u beschikt over basiskennis van Azure Key Vault. Zie [Wat is Azure Key Vault?](/azure/key-vault/key-vault-whatis) voor meer informatie. Configureer uw sleutelkluis als volgt:

1. Voeg de Power BI-service toe als een service-principal voor de sleutelkluis, met machtigingen voor verpakken en uitpakken.

1. Maak een RSA-sleutel met een lengte van 4096 bits (of gebruik een bestaande sleutel van dit type), met machtigingen voor verpakken en uitpakken.

1. Aanbevolen: Controleer of de optie _Voorlopig verwijderen_ is ingeschakeld voor de sleutelkluis.

### <a name="add-the-service-principal"></a>De service-principal toevoegen

1. Selecteer in uw sleutelkluis in Azure Portal onder **Toegangsbeleid** de optie **Nieuwe toevoegen**.

1. Zoek en selecteer Microsoft.Azure.AnalysisServices onder **Principal selecteren**.

1. Selecteer onder **sleutelmachtigingen** de opties **Sleutel uitpakken** en **Sleutel verpakken**.

    ![Onderdelen van PBIX-bestanden](media/service-encryption-byok/service-principal.png)

1. Selecteer **OK** en klik vervolgens op **Opslaan**.

### <a name="create-an-rsa-key"></a>Een RSA-sleutel maken

1. Selecteer in uw sleutelkluis onder **sleutels** de optie **Genereren/importeren**.

1. Selecteer RSA als **Sleuteltype** en 4096 als **Grootte van RSA-sleutel**.

    ![Onderdelen van PBIX-bestanden](media/service-encryption-byok/create-rsa-key.png)

1. Selecteer **Maken**.

1. Selecteer onder **Sleutels** de sleutel die u hebt gemaakt.

1. Selecteer de GUID voor de **Huidige versie** van de sleutel.

1. Controleer of **Sleutel verpakken** en **Sleutel uitpakken** beide zijn geselecteerd. Kopieer de te gebruiken **Sleutel-id** bij het inschakelen van BYOK in Power BI.

    ![Onderdelen van PBIX-bestanden](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>De optie Voorlopig verwijderen

Het is raadzaam [Voorlopig verwijderen](/azure/key-vault/key-vault-ovw-soft-delete) in te schakelen voor uw sleutelkluis als beveiliging tegen gegevensverlies voor het geval de sleutel of sleutelkluis per ongeluk wordt verwijderd. U moet gebruikmaken van [PowerShell om de eigenschap 'Voorlopig verwijderen' in te schakelen](/azure/key-vault/key-vault-soft-delete-powershell) voor de sleutelkluis omdat deze optie nog niet beschikbaar is via Azure Portal.

Nu Azure Key Vault correct is geconfigureerd, kunt u BYOK inschakelen voor uw tenant.

## <a name="enable-byok-on-your-tenant"></a>BYOK inschakelen voor uw tenant

U kunt BYOK op tenantniveau inschakelen met PowerShell door eerst de versleutelingssleutels die u hebt gemaakt en opgeslagen in Azure Key Vault te introduceren bij uw Power BI-tenant. Vervolgens wijst u deze versleutelingssleutels per Premium-capaciteit toe om inhoud in de capaciteit te versleutelen.

### <a name="important-considerations"></a>Belangrijke overwegingen

Let op de volgende aandachtspunten voordat u BYOK inschakelt:

- Op dit moment kunt u BYOK na inschakeling niet uitschakelen. Afhankelijk van hoe u parameters voor `Add-PowerBIEncryptionKey` opgeeft, kunt u bepalen hoe u BYOK gebruikt voor een of meer van uw capaciteiten. U kunt de introductie van sleutels bij uw tenant echter niet ongedaan maken. Zie [BYOK inschakelen](#enable-byok) voor meer informatie.

- U kunt een werkruimte die gebruikmaakt van BYOK niet _rechtstreeks_ verplaatsen van een toegewezen capaciteit in Power BI Premium naar gedeelde capaciteit. U moet de werkruimte eerst verplaatsen naar een toegewezen capaciteit waarvoor BYOK niet is ingeschakeld.

### <a name="enable-byok"></a>BYOK inschakelen

Om BYOK in te schakelen moet u een tenantbeheerder van de Power BI-service zijn en zijn aangemeld met behulp van de cmdlet `Connect-PowerBIServiceAccount`. Gebruik vervolgens `Add-PowerBIEncryptionKey` om BYOK in te schakelen, zoals weergegeven in het volgende voorbeeld:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

U kunt drie schakelparameters opgeven voor de cmdlet om de versleuteling voor huidige en toekomstige capaciteit te beïnvloeden. Standaard wordt geen van de schakelparameters ingesteld:

- `-Activate`: geeft aan dat deze sleutel wordt gebruikt voor alle bestaande capaciteiten in de tenant.

- `-Default`: geeft aan dat deze sleutel nu de standaardwaarde voor de gehele tenant is. Als u een nieuwe capaciteit maakt, wordt deze sleutel overgenomen door de capaciteit.

- `-DefaultAndActivate`: geeft aan dat deze sleutel wordt gebruikt voor alle bestaande capaciteiten en alle nieuwe capaciteiten die u maakt.

Als u `-Default` of `-DefaultAndActivate` opgeeft, worden alle capaciteiten die voor deze tenant worden gemaakt vanaf dit moment versleuteld met behulp van de sleutel die u opgeeft (of een bijgewerkte standaardsleutel). U kunt de standaardbewerking niet ongedaan maken en verliest dus de mogelijkheid om een Premium-capaciteit te maken die niet gebruikmaakt van BYOK in uw tenant.

U kunt zelf bepalen hoe u BYOK binnen uw tenant gebruikt. Als u bijvoorbeeld een enkele capaciteit wilt versleutelen, roept u `Add-PowerBIEncryptionKey` aan zonder `-Activate`, `-Default` of `-DefaultAndActivate`. Roep vervolgens `Set-PowerBICapacityEncryptionKey` aan voor de capaciteit waarvoor u BYOK wilt inschakelen.

## <a name="manage-byok"></a>BYOK beheren

Power BI biedt aanvullende cmdlets om BYOK te beheren in uw tenant:

- Gebruik `Get-PowerBIEncryptionKey` om de sleutel op te halen die momenteel in gebruik is bij uw tenant:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Gebruik `Get-PowerBIWorkspaceEncryptionStatus` om te zien of de gegevenssets in een werkruimte zijn versleuteld en of de versleutelingsstatus is gesynchroniseerd met de werkruimte:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Houd er rekening mee dat versleuteling is ingeschakeld op capaciteitsniveau, maar dat u de versleutelingsstatus verkrijgt voor het gegevenssetniveau van de opgegeven werkruimte.

- Gebruik `Set-PowerBICapacityEncryptionKey` om de versleutelingssleutel bij te werken voor de Power BI-capaciteit:

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
    ```

- Gebruik `Use Switch-PowerBIEncryptionKey` om de sleutel die momenteel wordt gebruikt voor versleuteling om te schakelen (of om te _draaien_). Met deze cmdlet werkt u de `-KeyVaultKeyUri` voor een sleutel `-Name` bij:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```