---
title: Overwegingen voor het genereren van een insluittoken in ingesloten analyses voor Power BI
description: Lees hier meer over de overwegingen, beperkingen en vereiste machtigingen voor het genereren van een insluittoken
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 45a88d93e7ac5a63b269350451f39991ba153dd5
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098025"
---
# <a name="considerations-when-generating-an-embed-token"></a>Overwegingen bij het genereren van een insluittoken

[GenerateToken](/rest/api/power-bi/embedtoken) is een REST-API waarmee u een token kunt genereren voor het insluiten van een Power BI-item in een web-app of een portal. Het token wordt gebruikt om uw aanvraag te autoriseren bij de Power BI-service.

De API GenerateToken maakt gebruik van één identiteit (een hoofdgebruiker of service-principal) voor het genereren van een token voor een afzonderlijke gebruiker, afhankelijk van de referenties van de gebruiker in de app (effectieve id).

Als de verificatie is geslaagd, wordt er toegang tot de relevante gegevens verleend.

>[!NOTE]
>GenerateToken is alleen van toepassing wanneer u inhoud [*insluit voor uw klanten*](embed-sample-for-customers.md) (ook wel bekend als het scenario waarin de *app eigenaar is van gegevens*).

U kunt de volgende API's gebruiken om een token te genereren:

* [Dashboards](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [Gegevenssets](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [GenerateToken voor meerdere rapporten](/rest/api/power-bi/embedtoken/generatetoken)


* [Rapport maken](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [Rapporten](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Tiles](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>Werkruimteversies

Power BI heeft twee werkruimteversies, een *klassieke* werkruimte en een *nieuwe* werkruimte. Lees hier meer over de verschillen tussen [de nieuwe en klassieke werkruimten](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences).

Bij het maken van een insluittoken gelden voor verschillende werkruimten verschillende overwegingen en vereisen ze andere machtigingen.

|                  |*Klassieke* werkruimte |*Nieuwe* werkruimte|
|------------------|---------|--------|
|**Overwegingen**|<li>De gegevensset en het item moeten zich in dezelfde werkruimte bevinden</li><li>De service-principal kan niet worden gebruikt</li>  |De gegevensset en het item kunnen zich in twee verschillende *nieuwe* werkruimten bevinden |
|**Werkruimtemachtigingen**|De hoofdgebruiker moet een beheerder van de werkruimte zijn  |De service-principal of hoofdgebruiker moet ten minste lid zijn van beide werkruimten |

>[!NOTE]
>* U kunt geen insluittoken maken voor [Mijn werkruimte](../../consumer/end-user-workspaces.md#types-of-workspaces).
>* Het woord *item* verwijst naar een Power BI-item, zoals een dashboard, tegel, Q&A of een rapport.

## <a name="securing-your-data"></a>Uw gegevens beveiligen

Wanneer u een oplossing bouwt, zijn dit twee benaderingen voor het beveiligen van uw gegevens:

* [Isolatie op basis van werkruimte](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [Isolatie op basis van beveiliging op rijniveau](embed-multi-tenancy.md#row-level-security-based-isolation)

Als u de methode voor beveiliging op rijniveau wilt gebruiken, raadpleegt u de [aandachtspunten voor beveiliging en beperkingen](generate-embed-token.md#row-level-security) aan het einde van dit artikel.

## <a name="token-permissions"></a>Tokenmachtigingen

In de API's voor het genereren van tokens worden de tokenmachtigingen beschreven in de sectie *GenerateTokenRequest*.

>[!NOTE]
>De tokenmachtigingen die in deze sectie worden vermeld, zijn niet van toepassing op de API [GenerateToken](/rest/api/power-bi/embedtoken/generatetoken).

### <a name="access-level"></a>Toegangsniveau

Gebruik de parameter *accessLevel* om het toegangsniveau van de gebruiker te bepalen.

* **allowView**: de gebruiker weergavemachtigingen geven.

* **allowEdit**: de gebruiker machtigingen geven voor weergeven en bewerken (alleen van toepassing bij het genereren van een insluittoken voor een rapport).

    Als u de API [GenerateToken](/rest/api/power-bi/embedtoken/generatetoken) gebruikt, kunt u met de parameter *allowEdit* de gebruiker machtigen voor weergeven en bewerken.

* **allowCreate**: de gebruiker machtigingen geven om een rapport te maken (alleen van toepassing bij het genereren van een insluittoken voor het maken van een rapport).

    Voor het maken van rapporten moet u ook de parameter *datasetId* opgeven.

### <a name="saving-a-copy-of-the-report"></a>Een kopie van het rapport opslaan

Gebruik de Booleaanse waarde *allowSaveAs* om gebruikers de mogelijkheid te bieden het rapport als een nieuw rapport op te slaan. Deze waarde is standaard ingesteld op *false*.

Deze parameter is alleen van toepassing bij het genereren van een insluittoken voor een rapport.

### <a name="row-level-security"></a>Beveiliging op rijniveau

Met [beveiliging op rijniveau](embedded-row-level-security.md) kunt u kiezen voor het gebruik van een andere identiteit dan de identiteit van de service-principal of de hoofdgebruiker waarmee u het token wilt genereren. Met deze optie kunt u ingesloten gegevens weergeven op basis van de gebruiker waarop u zich wilt richten. Zo kunt u gebruikers in uw toepassing vragen zich aan te melden en kunt u vervolgens een rapport weergeven dat alleen verkoopgegevens bevat als de aangemelde gebruiker een verkoopmedewerker is.

Als u beveiliging op rijniveau gebruikt, kunt u in sommige gevallen de identiteit van de gebruiker (de parameter *EffectiveIdentity*) weglaten. Het token biedt dan toegang tot de gehele database. Deze methode kan worden gebruikt om toegang te verlenen aan gebruikers zoals beheerders en managers, die bevoegd zijn om de volledige gegevensset te raadplegen. U kunt deze methode echter niet in elk scenario gebruiken. In de volgende tabel ziet u de verschillende typen beveiliging op rijniveau, met voor elk type de verificatiemethode die kan worden gebruikt zonder de identiteit van een gebruiker op te geven.

De tabel bevat ook de overwegingen en beperkingen die van toepassing zijn op elk type beveiliging op rijniveau.

|Type beveiliging op rijniveau  |Kan ik een insluittoken genereren zonder de effectieve gebruikers-id op te geven?  |Overwegingen en beperkingen  |
|---------|---------|---------|
|Beveiliging op rijniveau in de cloud      |✔ Hoofdgebruiker<br/>✖ Service-principal          |         |
|RDL (gepagineerde rapporten)     |✖ Hoofdgebruiker<br/>✔ Service-principal        |U kunt niet een hoofdgebruiker gebruiken om een insluittoken te genereren voor RDL.         |
|On-premises liveverbinding met Analysis Services (AS)    |✔ Hoofdgebruiker<br/>✖ Service-principal         |De gebruiker die het insluittoken genereert, moet ook een van de volgende machtigingen hebben:<li>Machtigingen voor gatewaybeheerder</li><li>Machtiging voor imiteren van gegevensbron (*ReadOverrideEffectiveIdentity*)</li>         |
|Liveverbinding vanuit Azure met Analysis Services (AS)    |✔ Hoofdgebruiker<br/>✖ Service-principal         |De identiteit van de gebruiker die het insluittoken genereert, kan niet worden overschreven. Er kunnen aangepaste gegevens worden gebruikt voor het implementeren van dynamische beveiliging op rijniveau of veilig filteren.<br/><br/>**Opmerking:** De service-principal moet de object-id opgeven als de effectieve id (gebruikersnaam voor beveiliging op rijniveau).         |
|Eenmalige aanmelding     |✔ Hoofdgebruiker<br/>✖ Service-principal         |Er kan een expliciete identiteit (voor eenmalige aanmelding) worden aangeboden met behulp van de eigenschap voor de id-blob in een effectief id-object         |
|Eenmalige aanmelding en beveiliging op rijniveau in de cloud     |✔ Hoofdgebruiker<br/>✖ Service-principal         |U moet het volgende opgeven:<li>Expliciete identiteit (voor eenmalige aanmelding) met behulp van de eigenschap voor de id-blob in een effectief id-object</li><li>Effectieve id (beveiliging op rijniveau) (gebruikersnaam)</li>         |

>[!NOTE]
>De service-principal moet altijd het volgende doorgeven:
>* Een identiteit voor elk item met een gegevensset met beveiliging op rijniveau.
>* Voor een gegevensset met eenmalige aanmelding moet effectieve id voor beveiliging op rijniveau zijn gedefinieerd met de eigenschap username.

## <a name="next-steps"></a>Volgende stappen

>[!div class="nextstepaction"]
>[Een app registreren](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded voor uw klanten](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Toepassings- en service-principal-objecten in Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Beveiliging op rijniveau met on-premises gegevensgateway met service-principal](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Power BI-inhoud met service-principal insluiten](embed-service-principal.md)