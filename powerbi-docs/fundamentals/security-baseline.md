---
title: Azure-beveiligingsbasislijn voor Power BI
description: De Power BI-beveiligingsbasislijn biedt procedurele richtlijnen en resources voor het implementeren van de beveiligingsaanbevelingen die zijn opgegeven in Azure Security Benchmark.
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: a76c7f9d205fe47322768a514a1e5d89a36a2306
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565757"
---
# <a name="azure-security-baseline-for-power-bi"></a>Azure-beveiligingsbasislijn voor Power BI

Deze beveiligingsbasislijn past richtlijnen van [Azure Security Benchmark versie 2.0](/azure/security/benchmarks/overview) toe op Power BI. De Azure Security-benchmark biedt aanbevelingen voor hoe u uw cloudoplossingen in Azure kunt beveiligen. De inhoud is gegroepeerd op de **besturingselementen voor beveiliging** die worden gedefinieerd door Azure Security Benchmark en door de bijbehorende richtlijnen die van toepassing zijn op Power BI. **Besturingselementen** die niet van toepassing zijn op Power BI zijn uitgesloten.

Als u wilt zien hoe Power BI in zijn geheel is toegewezen aan Azure Security Benchmark, raadpleegt u het [bestand met de volledige toewijzingen van de Power BI-beveiligingsbasislijn](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Netwerkbeveiliging

*Zie [Azure Security Benchmark: netwerkbeveiliging](/azure/security/benchmarks/security-controls-v2-network-security) voor meer informatie.*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: Toegang tot Azure-services via particulier netwerk tot stand brengen

**Richtlijnen**: Power BI biedt ondersteuning voor het verbinden van uw Power BI-tenant met een eindpunt van een privékoppeling, en voor het uitschakelen van de openbare internettoegang.

- [Privékoppelingen voor toegang tot Power BI](../admin/service-security-private-links.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

## <a name="identity-management"></a>Identiteitsbeheer

*Zie [Azure Security Benchmark: Identiteitsbeheer](/azure/security/benchmarks/security-controls-v2-identity-management) voor meer informatie.*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Azure Active Directory standaardiseren als het centrale identiteits--en verificatiesysteem

**Richtlijnen**: Power BI is geïntegreerd met Azure Active Directory (Azure AD), de standaardservice voor identiteits- en toegangsbeheer van Azure. Gebruik Azure AD als de standaard voor het identiteits- en toegangsbeheer van uw organisatie.

Het beveiligen van Azure AD moet een hoge prioriteit hebben in de cloudbeveiligingsprocedure van uw organisatie. Azure AD biedt een id-beveiligingsscore om u te helpen beoordelen in hoeverre uw identiteitsbeveiliging voldoet aan de aanbevelingen op basis van best practices van Microsoft. Gebruik de score om te meten hoe nauwkeurig uw configuratie overeenkomt met aanbevelingen op basis van best practices, en om verbeteringen aan te brengen in uw beveiligingsaanpak.

Opmerking: Azure AD biedt ondersteuning voor externe identiteiten waardoor gebruikers zonder Microsoft-account zich met hun externe identiteit kunnen aanmelden bij hun toepassingen en resources.

- [Tenancy in Azure Active Directory](/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Een Azure AD-instantie maken en configureren](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Externe ID-providers voor een toepassing gebruiken](/azure/active-directory/b2b/identity-providers)

- [Wat is de id-beveiligingsscore in Azure Active Directory?](/azure/active-directory/fundamentals/identity-secure-score)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: Toepassingsidentiteiten veilig en automatisch beheren

**Richtlijnen**: Power BI en Power BI Embedded ondersteunen het gebruik van service-principals. Sla de referenties van de service-principal op die worden gebruikt voor het versleutelen of openen van Power BI in een sleutelkluis, wijs het juiste toegangsbeleid toe aan de kluis en controleer regelmatig de toegangsmachtigingen.

Taken voor Premium-werkruimten en -gegevenssets automatiseren met service-principals https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Eenmalige aanmelding (SSO) van Azure AD gebruiken voor toegang tot toepassingen

**Richtlijnen**: Power BI gebruikt Azure Active Directory voor het bieden van identiteits- en toegangsbeheer voor Azure-resources, cloudtoepassingen en on-premises toepassingen. Dit omvat ondernemingsidentiteiten zoals werknemers, maar ook externe identiteiten, zoals partners, verkopers en leveranciers. Zo kunt u eenmalige aanmelding (SSO) gebruiken voor het beheren en beveiligen van de gegevens en resources van uw organisatie, on premises en in de cloud. Verbind al uw gebruikers, toepassingen en apparaten met Azure AD voor naadloze, veilige toegang en meer zichtbaarheid en controle.

- [Inzicht in eenmalige aanmelding van toepassingen met Azure AD](/azure/active-directory/manage-apps/what-is-single-sign-on)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Gebruik krachtige besturingselementen voor verificatie voor alle op Azure Active Directory gebaseerde toegang

**Richtlijnen**: Power BI is geïntegreerd met Azure AD dat ondersteuning biedt voor krachtige besturingselementen voor verificatie via MFA (Multi-Factor Authentication) en krachtige methoden zonder wachtwoord.
- Meervoudige verificatie: schakel MFA in voor Azure AD en volg de aanbevelingen op van Azure Security Center met betrekking tot identiteits- en toegangsbeheer die gelden als best practices voor het instellen van uw MFA. MFA kan worden afgedwongen voor alle gebruikers, bepaalde gebruikers of op het niveau van individuele gebruikers, op basis van voorwaarden voor aanmelding en op basis van risicofactoren.
- Verificatie zonder wachtwoord: er zijn drie verificatieopties zonder een wachtwoord beschikbaar: Windows Hello voor Bedrijven, de Microsoft Authenticator-app en on-premises verificatiemethoden zoals smartcards.

Zorg ervoor dat voor beheerders en bevoegde gebruikers een krachtige verificatiemethode van het hoogste niveau wordt gebruikt, gevolgd door de implementatie van een verificatiemethode die voldoende sterk is voor de andere gebruikers.

Opmerking: MFA kan alleen worden afgedwongen voor gebruikersaccounts die zijn ingeschakeld in Azure AD. Power BI-service-principals bieden geen ondersteuning voor het gebruik van MFA.

- [MFA inschakelen in Azure](/azure/active-directory/authentication/howto-mfa-getstarted)

- [Inleiding tot verificatieopties zonder wachtwoord voor Azure Active Directory](/azure/active-directory/authentication/concept-authentication-passwordless)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Bewaken van accounts op afwijkingen en waarschuwingenbeheer

**Richtlijnen**: Definieer beleid voor anomaliedetectie in Microsoft Cloud App Security waarvoor het bereik onafhankelijk kan worden bepaald, zodat dit alleen van toepassing is op de gebruikers en groepen die u in het beleid wilt opnemen. Dit beleid voor anomaliedetectie helpt bij het detecteren en bewaken van afwijkingen in het gedrag van gebruikers die proberen toegang te krijgen tot Power BI of Power BI willen gebruiken.

- [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Toegang tot Azure-resource beperken op basis van voorwaarden

**Richtlijnen**: Power BI biedt ondersteuning voor voorwaardelijke toegang van Azure AD voor een meer gedetailleerd toegangsbeheer op basis van door de gebruiker gedefinieerde voorwaarden, zoals gebruikersaanmeldingen door IP-adressen uit bepaalde bereiken waarvoor MFA moet worden gebruikt. Gedetailleerd beheerbeleid voor verificatiesessies kan ook worden gebruikt voor verschillende scenario's.

- [Overzicht van voorwaardelijke toegang in Azure](/azure/active-directory/conditional-access/overview)

- [Veelvoorkomend beleid voor voorwaardelijke toegang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [Het beheer van verificatiesessies via voorwaardelijke toegang configureren](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Microsoft Cloud App Security-besturingselementen gebruiken in Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7: Onbedoelde blootstelling van referenties elimineren

**Richtlijnen**: Voor Power BI Embedded-toepassingen wordt aanbevolen om de Credential Scanner te implementeren om referenties in uw code te identificeren. Door het gebruik van Credential Scanner worden gebruikers ook aangemoedigd om gedetecteerde referenties naar veiligere locaties, zoals Azure Key Vault, te verplaatsen.

Sla eventuele versleutelingssleutels of referenties van de service-principal die worden gebruikt voor het versleutelen of openen van Power BI, op in een sleutelkluis, wijs het juiste toegangsbeleid toe aan de kluis en controleer regelmatig de toegangsmachtigingen.
 
Voor GitHub kunt u de systeemeigen functie voor het scannen op geheimen gebruiken om referenties of een andere vormen van geheimen binnen de code te identificeren.

- [Uw eigen versleutelingssleutels gebruiken voor Power BI](../admin/service-encryption-byok.md)

 
Credential instellen
- [Scanner](https://secdevtools.azurewebsites.net/helpcredscan.html) instellen 

- [Scannen op geheimen in GitHub](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

## <a name="privileged-access"></a>Uitgebreide toegang

*Zie [Azure Security Benchmark: uitgebreide toegang](/azure/security/benchmarks/security-controls-v2-privileged-access) voor meer informatie.*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Gebruikers met zeer uitgebreide bevoegdheden beveiligen en beperken

**Richtlijnen**: Ter beperking van risico's en om ervoor te zorgen dat het principe van minimale bevoegdheid wordt gevolgd, wordt aangeraden om het aantal personen met de bevoegdheden van Power BI-beheerders tot een klein groepje te beperken. Gebruikers met deze uitgebreide machtigingen hebben mogelijk toegang tot alle beheerfuncties van de organisatie, en kunnen deze wijzigen. Globale beheerders hebben via Microsoft 365 of Azure Active Directory ook impliciet beheerdersrechten voor de Power BI-service.

Power BI heeft de onderstaande accounts waarvoor zeer uitgebreide machtigingen van kracht zijn:
- Globale beheerder
- Factureringsbeheerder
- Licentiebeheerder
- Gebruikersbeheerder
- Power BI-beheerder
- Power BI Premium-capaciteitsbeheerder
- Power BI Embedded-capaciteitsbeheerder

Power BI biedt ondersteuning voor sessiebeleid in Azure AD, waardoor beleid voor voorwaardelijke toegang voor Power BI kan worden gebruikt, en waardoor in Power BI gebruikte sessies via de Cloud App Security-service worden omgeleid.

Schakel Just-In-Time (JIT) uitgebreide toegang in voor de Power BI-beheerdersaccounts met behulp van uitgebreid toegangsbeheer van M365.

- [Beheerdersrollen die betrekking hebben op Power BI](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)

- [Uitgebreid toegangsbeheer van M365](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)

- [Cloud App Security-besturingselementen in Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Beheerderstoegang tot essentiële bedrijfssystemen beperken

**Richtlijnen**: Beperk het aantal accounts of rollen die zeer uitgebreide toegang hebben tot Power BI.

U kunt Just-In-Time (JIT) uitgebreide toegang inschakelen met behulp van de richtlijnen voor uitgebreid toegangsbeheer van M365 die [hier](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)zijn te vinden.

Meer informatie vindt u [op pagina 183](https://aka.ms/PBIEnterpriseDeploymentWP) van het document over het implementeren van Power BI Enterprise.

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Gebruikerstoegang regelmatig controleren en afstemmen

**Richtlijnen**: Als Power BI-servicebeheerder kunt u het gebruik van alle Power BI-resources op tenantniveau analyseren door aangepaste rapporten te gebruiken op basis van het Power BI-activiteitenlogboek. U kunt de activiteiten downloaden met behulp van een REST API of PowerShell-cmdlet. U kunt ook de activiteitsgegeven filteren op datumbereik, gebruiker en type activiteit.

U moet aan deze vereisten voldoen om toegang te krijgen tot het Power BI-activiteitenlogboek:
- U moet een globale beheerder of een Power BI-servicebeheerder zijn.
- U hebt de [Power BI Management-cmdlets](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) lokaal geïnstalleerd of u gebruikt de Power BI Management-cmdlets in Azure Cloud Shell.

Zodra aan deze vereisten wordt voldaan, kunt u de onderstaande richtlijnen volgen voor het bijhouden van gebruikersactiviteiten binnen Power BI:

- [Gebruikersactiviteiten bijhouden in Power BI](../admin/service-admin-auditing.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Noodtoegang instellen in Azure AD

**Richtlijnen**: Power BI is geïntegreerd met Azure Active Directory en M365 voor het beheren van de bijbehorende resources. Als u wilt voorkomen dat uw M365-tenant of Azure AD-organisatie per ongeluk wordt vergrendeld, moet u een account voor noodtoegang instellen dat u kunt gebruiken als de reguliere beheerdersaccounts niet kunnen worden gebruikt. Accounts voor noodtoegang hebben meestal zeer uitgebreide bevoegdheden en kunnen beter niet aan specifieke personen worden toegewezen. Accounts voor noodtoegang zijn alleen bestemd voor echte noodsituaties waarin normale beheerdersaccounts niet kunnen worden gebruikt.

Zorg ervoor dat de referenties (zoals wachtwoord, certificaat of smartcard) voor accounts voor noodtoegang veilig worden bewaard en alleen bekend zijn bij personen die deze alleen in een noodgeval mogen gebruiken.

- [Accounts voor noodtoegang beheren in Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access)

- [Uw M365-accounts beschermen](/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: Werkstations met uitgebreide toegang gebruiken

**Richtlijnen**: Beveiligde, geïsoleerde werkstations zijn van cruciaal belang voor de beveiliging van gevoelige rollen als beheerders, ontwikkelaars en serviceoperators met vergaande bevoegdheden. Gebruik zeer goed beveiligde gebruikerswerkstations en/of Azure Bastion voor beheertaken voor Power BI. Gebruik Azure Active Directory, Microsoft Defender Advanced Threat Protection (ATP) en/of Microsoft Intune als u een beveiligd en beheerd gebruikerswerkstation voor beheertaken wilt implementeren. De beveiligde werkstations kunnen centraal worden beheerd en beveiligde configuraties afdwingen, waaronder krachtige verificatie, software- en hardwarebasislijnen, beperkte logische toegang en netwerktoegang.

Inzicht in uitgebreide toegang
- [werkstations](/azure/active-directory/devices/concept-azure-managed-workstation)

- [Een werkstation met uitgebreide toegang gebruiken](/azure/active-directory/devices/howto-azure-managed-workstation)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="data-protection"></a>Gegevensbeveiliging

*Zie [Azure Security Benchmark: gegevensbescherming](/azure/security/benchmarks/security-controls-v2-data-protection) voor meer informatie.*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Detectie, classificatie en labeling van gevoelige gegevens

**Richtlijnen**: Gebruik vertrouwelijkheidslabels voor Microsoft Information Protection op uw rapporten, dashboards, gegevenssets en gegevensstromen om uw gevoelige inhoud te beschermen tegen ongeautoriseerde toegang tot gegevens en lekkage.

Gebruik vertrouwelijkheidslabels voor Microsoft Information Protection voor het classificeren en labelen van uw rapporten, dashboards, gegevenssets en gegevensstromen in de Power BI-service, en om uw gevoelige inhoud te beschermen tegen onbevoegde toegang tot gegevens en lekkage als inhoud wordt geëxporteerd van de Power BI-service naar Excel-, PowerPoint- en PDF-bestanden.

- [Vertrouwelijkheidslabels toepassen in Power BI](../admin/service-security-apply-data-sensitivity-labels.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Gevoelige gegevens beschermen

**Richtlijnen**: De vertrouwelijkheidslabels van Microsoft Information Protection zijn geïntegreerd met Power BI voor de bescherming van gevoelige gegevens. Zie [Vertrouwelijkheidslabels voor Microsoft Information Protection in Power BI](../admin/service-security-sensitivity-label-overview.md) voor meer informatie

Met Power BI kunnen servicegebruikers hun eigen sleutel voor het beveiligen van data-at-rest gebruiken. Zie [Uw eigen versleutelingssleutels gebruiken voor Power BI](../admin/service-encryption-byok.md) voor meer informatie

Klanten hebben de mogelijkheid om gegevensbronnen on-premises te houden en DirectQuery of Live Connect te gebruiken met een on-premises gegevensgateway om de blootstelling van gegevens aan de cloudservice zo klein mogelijk te houden. Zie [Wat is een on-premises gegevensgateway?](/data-integration/gateway/service-gateway-onprem) voor meer informatie.

Power BI ondersteunt beveiliging op rijniveau. Zie [Beveiliging op rijniveau (RLS) met Power BI](../admin/service-admin-rls.md) voor meer informatie. Houd er rekening mee dat beveiliging op rijniveau zelfs kan worden toegepast op DirectQuery-gegevensbronnen waarin een PBIX-bestand fungeert als proxy die beveiliging mogelijk maakt.

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: Controleren of er niet-geautoriseerde overdrachten van gevoelige gegevens hebben plaatsgevonden

**Richtlijnen**: Dit besturingselement kan gedeeltelijk worden gerealiseerd door gebruik te maken van de Microsoft Cloud App Security-ondersteuning voor Power BI.

Met behulp van Cloud App Security met Power BI kunt u uw Power BI-rapporten, -gegevens en -services beveiligen tegen onbedoelde lekken of inbreuk. Met Cloud App Security maakt u beleidsregels voor voorwaardelijke toegang voor de gegevens van uw organisatie, met behulp van realtime sessiebesturingselementen in Azure Active Directory (Azure AD), waarmee u kunt garanderen dat uw Power BI-analyses veilig zijn. Zodra dit beleid is ingesteld, kunnen beveiligingsbeheerders gebruikerstoegang en -activiteit bijhouden, realtime risicoanalyse uitvoeren en labelspecifieke besturingselementen instellen.

Gebruiken
- [Microsoft Cloud App Security-besturingselementen in Power BI](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Gevoelige gegevens tijdens een overdracht versleutelen

**Richtlijnen**: Zorg ervoor dat het HTTP-verkeer alle clients en gegevensbronnen die verbinding maken met uw Power BI-resources, over TLS v1.2 of hoger kunnen onderhandelen.

- [Gebruik van TLS-versie afdwingen](../admin/service-admin-power-bi-security.md#enforcing-tls-version-usage)

- [Informatie over TLS-beveiliging](/security/engineering/solving-tls1-problem)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5: Gevoelige data-at-rest versleutelen

**Richtlijnen**: In Power BI worden data-at-rest en tijdens verwerking versleuteld. In Power BI wordt standaard gebruikgemaakt van door Microsoft beheerde sleutels om uw gegevens te versleutelen. Organisaties kunnen ervoor kiezen om hun eigen sleutels te gebruiken voor het versleutelen van gebruikerscontent at-rest in Power BI, van rapportinstallatiekopieën tot geïmporteerde gegevenssets in Premium-capaciteiten.

- [Gebruik uw eigen sleutel in Power BI](../admin/service-encryption-byok.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

## <a name="asset-management"></a>Asset-management

*Zie [Azure Security Benchmark: assetmanagement](/azure/security/benchmarks/security-controls-v2-asset-management) voor meer informatie.*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Zorg ervoor dat het beveiligingsteam inzicht heeft in risico's voor assets

**Richtlijnen**: Gebruik Azure Sentinel met uw Power BI Office-auditlogboeken om ervoor te zorgen dat uw beveiligingsteam inzicht heeft in risico's voor uw Power BI-assets.

- [Office 365-logboeken verbinden met Azure Sentinel](/azure/sentinel/connect-office-365)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: Controleer of het beveiligingsteam toegang heeft tot de asset-inventaris en metagegevens

**Richtlijnen**: Zorg ervoor dat beveiligingsteams toegang hebben tot een voortdurend bijgewerkte inventaris van Power BI Embedded-resources. Beveiligingsteams hebben deze inventaris vaak nodig om de mogelijke blootstelling van hun organisatie aan toekomstige risico's te evalueren, en willen deze inventaris gebruiken als invoer waarmee ze de beveiliging constant kunnen verbeteren. 

Azure Resource Graph kan alle Power BI Embedded-resources in uw abonnementen opvragen en detecteren.  

Organiseer op logische wijze assets op basis van de taxonomie van uw organisatie met behulp van tags en andere metagegevens in Azure (Naam, Beschrijving en Categorie).  

- [Query's maken met Azure Resource Graph Explorer](/azure/governance/resource-graph/first-query-portal)

- [Handleiding voor beslissingen over taggen en naamgeving voor resources](/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=%2fazure%2fazure-resource-manager%2fmanagement%2ftoc.json)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Gebruik alleen goedgekeurde Azure-Services

**Richtlijnen**: Power BI ondersteunt implementaties op basis van Azure Resource Manager voor Power BI Embedded. Ook kunt u de implementatie van de bijbehorende resources beperken via Azure Policy met behulp van een aangepaste beleidsdefinitie.

Gebruik Azure Policy om te controleren welke services gebruikers in uw omgeving kunnen inrichten en beperken. Gebruik Azure Resource Graph om resources binnen hun abonnementen op te vragen en te detecteren. U kunt Azure Monitor ook gebruiken om regels te maken voor het activeren van waarschuwingen wanneer een niet-goedgekeurde service wordt gedetecteerd.

- [Azure Policy configureren en beheren](/azure/governance/policy/tutorials/create-and-manage)

Een specifiek resourcetype weigeren met
- [Azure Policy](/azure/governance/policy/samples/built-in-policies#general)

Query's maken met Azure
- [Resource Graph Explorer](/azure/governance/resource-graph/first-query-portal)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="logging-and-threat-detection"></a>Logboekregistratie en detectie van bedreigingen

*Zie [Azure Security Benchmark: logboekregistratie en detectie van bedreigingen](/azure/security/benchmarks/security-controls-v2-logging-threat-detection) voor meer informatie.*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Detectie van bedreigingen inschakelen voor Azure identiteits- en toegangsbeheer

**Richtlijnen**: Stuur alle logboeken van Power BI door naar uw SIEM die kan worden gebruikt om aangepaste bedreigingsdetecties in te stellen. Daarnaast kunt u Microsoft Cloud App Security-besturingselementen (MCAS) in Power BI gebruiken om anomaliedetectie in te schakelen. Gebruik daarvoor [deze](../admin/service-security-using-microsoft-cloud-app-security-controls.md) handleiding.

- [Activiteiten van gebruikers bijhouden in Power BI](../admin/service-admin-auditing.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: Logboekregistratie inschakelen voor Azure-netwerkactiviteiten

**Richtlijnen**: Power BI is een volledig beheerde SaaS-aanbieding, en de onderliggende netwerkconfiguratie en logboekregistratie is een verantwoordelijkheid van Microsoft. Voor klanten die privékoppelingen gebruiken, is een bepaalde mate van configureerbare logboekregistratie en controle beschikbaar.

- [Logboekregistratie en controle voor privékoppelingen](/azure/private-link/private-link-overview#logging-and-monitoring)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Logboekregistratie inschakelen voor Azure-resources

**Richtlijnen**: Met Power BI hebt u twee opties om gebruikersactiviteiten bij te houden: Het Power BI-activiteitenlogboek en het gecombineerde auditlogboek. Deze logboeken bevatten beide een volledige kopie van de Power BI-controlegegevens. Er zijn echter een aantal belangrijke verschillen, zoals hieronder beschreven.
 
Gecombineerd auditlogboek:

 
- Bevat naast de Power BI-controlegebeurtenissen tevens gebeurtenissen van SharePoint Online, Exchange Online, Dynamics 365 en andere services.

 
- Alleen gebruikers met machtigingen voor Alleen-lezen auditlogboeken of Auditlogboeken hebben toegang, zoals globale beheerders en auditors.

 
- Globale beheerders en auditors kunnen in het gecombineerde auditlogboek zoeken met behulp van het Microsoft 365 Security Center en het Microsoft 365-compliancecentrum.

 
- Globale beheerders en auditors kunnen vermeldingen in controlelogboeken downloaden met behulp van Microsoft 365-beheer-API's en -cmdlets.

 
- Bewaart controlegegevens gedurende 90 dagen.

 
- Houdt controlegegevens bij, zelfs als de tenant wordt verplaatst naar een andere Azure-regio.
 
Power BI-activiteitenlogboek:

 
- Bevat alleen de Power BI-controlegebeurtenissen.

 
 
- Globale beheerders en Power BI-servicebeheerders hebben toegang.

 
- Er is nog geen gebruikersinterface om het activiteitenlogboek te doorzoeken.

 
- Globale beheerders en Power BI-servicebeheerders kunnen vermeldingen in het activiteitenlogboek downloaden met behulp van een Power BI REST API en beheer-cmdlet.

 
- Bewaart activiteitengegevens gedurende 30 dagen.

 
- Bewaart geen activiteitengegevens als de tenant wordt verplaatst naar een andere Azure-regio.

- [Power BI-controlegegevens](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI-activiteitenlogboek](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI-auditlogboek](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: Beheer en analyse van beveiligingslogboek centraliseren

**Richtlijnen**: Power BI centraliseert logboeken op twee locaties: het activiteitenlogboek van Power BI en het gecombineerde auditlogboek. Deze logboeken bevatten beide een volledige kopie van de Power BI-controlegegevens. Er zijn echter een aantal belangrijke verschillen, zoals hieronder beschreven.
 

Gecombineerd auditlogboek:

- Bevat naast de Power BI-controlegebeurtenissen tevens gebeurtenissen van SharePoint Online, Exchange Online, Dynamics 365 en andere services.

- Alleen gebruikers met machtigingen voor Alleen-lezen auditlogboeken of Auditlogboeken hebben toegang, zoals globale beheerders en auditors.

- Globale beheerders en auditors kunnen in het gecombineerde auditlogboek zoeken met behulp van het Microsoft 365 Security Center en het Microsoft 365-compliancecentrum.

- Globale beheerders en auditors kunnen vermeldingen in controlelogboeken downloaden met behulp van Microsoft 365-beheer-API's en -cmdlets.

- Bewaart controlegegevens gedurende 90 dagen.

- Houdt controlegegevens bij, zelfs als de tenant wordt verplaatst naar een andere Azure-regio.

 

Power BI-activiteitenlogboek:

- Bevat alleen de Power BI-controlegebeurtenissen.

- Globale beheerders en Power BI-servicebeheerders hebben toegang.

- Er is nog geen gebruikersinterface om het activiteitenlogboek te doorzoeken.

- Globale beheerders en Power BI-servicebeheerders kunnen vermeldingen in het activiteitenlogboek downloaden met behulp van een Power BI REST API en beheer-cmdlet.

- Bewaart activiteitengegevens gedurende 30 dagen.

- Houdt geen controlegegevens bij als de tenant wordt verplaatst naar een andere Azure-regio.

- [Power BI-controlegegevens](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI-activiteitenlogboek](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI-auditlogboek](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: Bewaarperiode voor logboek configureren

**Richtlijnen**: Configureer het bewaarbeleid voor de opslag van uw Office-auditlogboeken op basis van uw vereisten op het gebied van naleving, regelgeving en zakelijke behoeften.

- [Bewaarbeleid voor Office-auditlogboeken](/microsoft-365/compliance/audit-log-retention-policies)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="incident-response"></a>Reageren op incidenten

*Zie [Azure Security Benchmark: respons op incidenten](/azure/security/benchmarks/security-controls-v2-incident-response) voor meer informatie.*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Voorbereiding: responsproces voor incidenten bijwerken voor Azure

**Richtlijnen**: Zorg ervoor dat uw organisatie processen heeft gedefinieerd om te reageren op beveiligingsincidenten, dat deze processen voor Azure zijn bijgewerkt en dat ze regelmatig worden uitgevoerd om de gereedheid ervan te garanderen.

- [Beveiliging in de complete bedrijfsomgeving implementeren](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Naslaggids voor respons op incidenten](/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Voorbereiding: melding van incidenten instellen

**Richtlijnen**: Contactgegevens in Azure Security Center instellen in het geval van beveiligingsincidenten Deze contactgegevens worden door Microsoft gebruikt om contact met u op te nemen als het Microsoft Security Response Center (MSRC) vaststelt dat een niet-geautoriseerde partij toegang tot uw gegevens heeft gekregen. Er zijn ook opties waarmee u incidentwaarschuwingen en -meldingen in verschillende Azure-Services kunt aanpassen aan de hand van wat u als incidentrespons nodig acht. 

- [De Azure Security Center Security-contactpersoon instellen](/azure/security-center/security-center-provide-security-contact-details)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Detectie en analyse: incidenten maken op basis van waarschuwingen van hoge kwaliteit

**Richtlijnen**: Zorg ervoor dat u een proces hebt gedefinieerd om waarschuwingen van hoge kwaliteit te maken en de kwaliteit van waarschuwingen te meten. Zo kunt u op grond van wat u uit eerdere incidenten hebt geleerd een hogere prioriteit toekennen aan waarschuwingen die bestemd zijn voor analisten, zodat deze geen tijd hoeven te verspillen aan fout-positieven.

Controleer waarschuwingen die te maken hebben met Power BI in Microsoft Cloud App Security. Waarschuwingen van hoge kwaliteit kunnen worden samengesteld op basis van ervaringen uit eerdere incidenten, op grond van gevalideerde communitybronnen, en door tools te gebruiken die zijn ontworpen om waarschuwingen te genereren en op te schonen door diverse signaalbronnen samen te voegen en er correlaties tussen te ontdekken.

- [Waarschuwingen controleren in Cloud App Security](/cloud-app-security/monitor-alerts)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Detectie en analyse: een incident onderzoeken

**Richtlijnen**: Stel voor uw organisatie een responshandleiding op voor gebruik bij incidenten. Voer regelmatig oefeningen uit om de responsmogelijkheden van uw systeem te testen. Stel vast waar zich zwakke plekken en hiaten bevinden, en wijzig zo nodig het plan.

Zorg ervoor dat er schriftelijke responsplannen zijn waarin alle rollen van het personeel worden gedefinieerd, evenals alle fasen in het afhandelen/managen van incidenten, vanaf de detectie van het incident tot een evaluatie ervan achteraf.

- [Overzicht van incidenten in Microsoft Threat Protection](/microsoft-365/security/mtp/incidents-overview)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Detectie en analyse: prioriteiten toekennen aan incidenten

**Richtlijnen**: Bied op basis van de ernst van waarschuwingen en de gevoeligheid van een asset context aan analisten zodat deze weten op welke incidenten ze zich het eerst moeten richten. 

 
Microsoft Threat Protection analyseert correlaties en voegt alle verwante waarschuwingen van verschillende producten samen tot één incident. Microsoft Threat Protection activeert ook unieke waarschuwingen voor activiteiten die alleen als schadelijk kunnen worden geïdentificeerd op grond van het end-to-end inzicht dat Microsoft Threat Protection heeft in het hele machinepark en productarsenaal. Door dit te doen, maakt Microsoft Threat Protection het verhaal over de aanval inzichtelijker door er een bredere context aan te geven, zodat een beveiligingsanalist complexe bedreigingen voor de hele organisatie kan begrijpen en afhandelen.

- [In Microsoft Threat Protection prioriteiten toekennen aan incidenten ](/microsoft-365/security/mtp/incident-queue?amp;preserve-view=true&view=o365-worldwide)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Insluiting, uitschakeling en herstel: het afhandelen van incidenten automatiseren

**Richtlijnen**: Automatiseer handmatige, terugkerende taken om de responstijd te versnellen en de werklast van analisten te verlichten. Het uitvoeren van handmatige taken duurt langer, waardoor elk incident trager gaat en het aantal incidenten dat een analist kan afhandelen, kleiner wordt. Handmatige taken zorgen ook dat analisten sneller vermoeid raken, waardoor het risico op menselijke fouten toeneemt en vertragingen optreden. Daarnaast neemt het vermogen van analisten af om zich effectief te richten op complexe taken.  
 
Gebruik functies voor het automatiseren van werkstromen in Microsoft Threat Protection om automatisch onderzoeks- en herstelacties te activeren als reactie op binnenkomende beveiligingswaarschuwingen. 
 
- [Geautomatiseerd onderzoek en respons in Microsoft Threat Protection](/microsoft-365/security/mtp/mtp-autoir)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="posture-and-vulnerability-management"></a>Beveiligingspostuur en beveiligingsproblemen beheren

*Zie [Azure Security Benchmark: beveiligingspostuur en beveiligingsproblemen beheren](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management) voor meer informatie.*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Veilige configuraties tot stand brengen voor Azure-services 

**Richtlijnen**: Configureer uw Power BI-service met de instellingen die relevant zijn voor uw organisatie en uw standpunt ten aanzien van beveiliging. Instellingen voor toegang tot de service en inhoud, evenals de veiligheid van werkruimten en apps, moeten zorgvuldig worden overwogen. Zie het technisch document over Power BI-implementatie voor ondernemingen voor meer informatie over Power BI-beveiliging en -gegevensbescherming.

- [Technisch document over implementaties voor ondernemingen](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: Veilige configuraties onderhouden voor Azure-services

**Richtlijnen**: Controleer uw Power BI-instantie met behulp van de Power BI Admin REST API's.

- [Power BI Admin REST API's](/rest/api/power-bi/admin)

- [Technisch document over Power BI-implementatie voor ondernemingen](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: Voer regelmatige simulaties van aanvallen uit

**Richtlijnen**: Voer zo vaak u als u wilt penetratietests of Red Teaming-activiteiten uit op uw Azure-resources, en zorg ervoor dat alle kritieke beveiligingsbevindingen worden opgelost.

Ga te werk volgens de Microsoft Cloud Penetration Testing Rules of Engagement (Regels voor het inzetten van penetratietests voor Microsoft Cloud ) zodat u zeker weet dat uw penetratietests niet conflicteren met Microsoft-beleid. Gebruik de strategie van Microsoft en de uitvoering van Red Teaming-activiteiten, en voer een penetratietest van de live site uit op basis van een infrastructuur, services en toepassingen die door Microsoft worden beheerd.

- [Penetratietesten in Azure](/azure/security/fundamentals/pen-testing)

- [Regels voor het inzetten van penetratietests](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Gedeeld

## <a name="backup-and-recovery"></a>Back-up en herstel

*Zie [Azure Security Benchmark: back-up en herstel](/azure/security/benchmarks/security-controls-v2-backup-recovery) voor meer informatie.*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3: Valideer alle back-ups, inclusief door de klant beheerde sleutels

**Richtlijnen**: Als u de functie Bring Your Own Key (BYOK) in Power BI gebruikt, moet u regelmatig controleren of u toegang hebt tot uw door de klant beheerde sleutels en deze kunt herstellen.

- [BYOK in Power BI](../admin/service-encryption-byok.md)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: Het risico op verloren sleutels beperken

**Richtlijnen**: Als u de functie Bring Your Own Key (BYOK) in Power BI gebruikt, moet u ervoor zorgen dat de sleutelkluis die uw door de klant beheerde sleutels beheert, is geconfigureerd aan de hand van de richtlijnen in het document BYOK in Power BI hieronder. Schakel voorlopig verwijderen en bescherming tegen opschonen in Azure Key Vault in om sleutels te beschermen tegen onbedoelde of kwaadwillige verwijdering.

- [BYOK in Power BI](../admin/service-encryption-byok.md)

- [Voorlopig verwijderen en bescherming tegen opschonen in Azure Key Vault inschakelen](/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

Voor Gateway-sleutelresources moet u de volgende richtlijnen volgen in de documentatie over de Gateway-herstelsleutel.

- [On-premises gegevens Gateway-herstelsleutel](/data-integration/gateway/service-gateway-recovery-key)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="governance-and-strategy"></a>Governance en strategie

*Zie [Azure Security Benchmark: governance en strategie](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Strategie voor asset-management en gegevensbescherming definiëren 

**Richtlijnen**: Zorg ervoor dat u een duidelijke strategie voor de continue bewaking en bescherming van systemen en gegevens schriftelijk vastlegt en bekendmaakt. Ken hogere prioriteiten toe aan de detectie, beoordeling, beveiliging en bewaking van bedrijfskritieke gegevens en systemen. 

Deze strategie moet gedocumenteerde richtlijnen, beleid en standaarden bevatten voor de volgende elementen: 

-   Standaard voor gegevensclassificatie in overeenstemming met de bedrijfsrisico's

-   Inzicht van beveiligingsorganisaties in risico's en asset-inventaris 

-   Goedkeuring door beveiligingsorganisaties van Azure-services voor gebruik 

-   Beveiliging van assets op grond van hun levenscyclus

-   Vereiste strategie voor toegangsbeheer in overeenstemming met gegevensclassificatie van organisatie

-   Gebruik van systeemeigen beveiligingsmogelijkheden van Azure en van derde partijen

-   Vereisten voor gegevensversleuteling in gebruiksscenario's met gegevens tijdens een overdracht en data-at-rest

-   Juiste cryptografische standaarden

Raadpleeg de volgende bronnen voor meer informatie:
- [Azure Security Architecture Recommendation - Storage, data, and encryption](/azure/architecture/framework/security/storage-data-encryption?amp;bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json) (Aanbeveling voor Azure-beveiligingsarchitectuur: opslag, gegevens en versleuteling)

- [Azure Security Fundamentals - Azure Data security, encryption, and storage](/azure/security/fundamentals/encryption-overview) (Basisprincipes van Azure-beveiliging: Azure-gegevensbeveiliging, -versleuteling en -opslag)

- [Cloud Adoption Framework - Azure data security and encryption best practices](/azure/security/fundamentals/data-encryption-best-practices?amp;bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) (Cloud Adoption Framework: best practices voor Azure-gegevensbeveiliging en -versleuteling)

- [Azure Security Benchmark - Asset management](/azure/security/benchmarks/security-controls-v2-asset-management) (Azure Security Benchmark: assetmanagement)

- [Azure Security Benchmark - Data Protection](/azure/security/benchmarks/security-controls-v2-data-protection) (Azure Security Benchmark: gegevensbeveiliging)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Segmentatiestrategie van bedrijf definiëren 

**Richtlijnen**: Stel een bedrijfsstrategie op om de toegang tot assets te segmenteren door een combinatie van besturingselementen voor het beheer van identiteiten, netwerken, toepassingen, abonnementen, beheergroepen en andere besturingselementen te gebruiken.

Zorg dat u een nauwgezette afweging maakt tussen de noodzaak om de beveiliging van de rest te scheiden en de noodzaak om systemen die met elkaar moeten kunnen communiceren en toegang moeten hebben tot gegevens, in staat te stellen om hun dagelijkse werklast uit te voeren.

Zorg ervoor dat de segmentatiestrategie consistent wordt geïmplementeerd voor alle typen besturingselementen, zoals voor netwerkbeveiliging, identiteits- en toegangsmodellen, toepassingsbevoegdheden/toegangsmodellen evenals besturingselementen voor door mensen uitgevoerde processen.

- [Richtlijnen voor segmentatiestrategie in Azure (video)](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Richtlijnen voor segmentatiestrategie in Azure (document)](/security/compass/governance#enterprise-segmentation-strategy)

- [Netwerksegmentatie afstemmen op segmentatiestrategie van bedrijf](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Strategie voor het beheer van beveiligingspostuur definiëren

**Richtlijnen**: Meet en beperk voortdurend de risico's die alle individuele assets en de omgeving die ze hosten, lopen. Ken hogere prioriteiten toe aan hoogwaardige assets en assets die zeer kwetsbaar zijn voor aanvallen, zoals gepubliceerde toepassingen, punten voor binnenkomend en uitgaand netwerkverkeer, gebruikers- en beheerderseindpunten enzovoort.

- [Azure Security Benchmark: beveiligingspostuur en beveiligingsproblemen beheren](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Organisatierollen, verantwoordelijkheden en aansprakelijkheden afstemmen

**Richtlijnen**: Zorg ervoor dat u een duidelijke strategie voor rollen en verantwoordelijkheden in uw beveiligingsorganisatie schriftelijk vastlegt en bekendmaakt. Ken een hoge prioriteiten toe aan het verschaffen van duidelijkheid over wie aansprakelijk is voor beveiligingsbeslissingen. Bied opleidingen aan iedereen over het gedeelde verantwoordelijkheidsmodel en biedt technische teams trainingen over technologie ter beveiliging van de cloud.

- [Best practice voor Azure-beveiliging 1: personen: Teams trainen inzake het cloudbeveiligingstraject](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Best practice voor Azure-beveiliging 2: personen: Teams trainen inzake cloudbeveiligingstechnologie](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Azure Security Best Practice 3 - proces: Aansprakelijkheid toewijzen voor beslissingen over cloudbeveiliging](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Strategie voor netwerkbeveiliging definiëren

**Richtlijnen**: Stel een benadering op voor netwerkbeveiliging in Azure als onderdeel van de algehele strategie voor toegangsbeheer in uw organisatie.  

Deze strategie moet gedocumenteerde richtlijnen, beleid en standaarden bevatten voor de volgende elementen: 

-   Gecentraliseerd netwerkbeheer en verantwoordelijkheid voor beveiliging

-   Model voor segmentatie van virtueel netwerk afgestemd op segmentatiestrategie van bedrijf

-   Herstelstrategie voor verschillende scenario's met bedreigingen en aanvallen

-   Strategie voor internetrand en inkomend en uitgaand verkeer

-   Strategie voor hybride cloud- en on-premises interconnectiviteit

-   Up-to-date netwerkbeveiligingsartefacten (zoals netwerkdiagrammen, architectuur van referentienetwerk)

Raadpleeg de volgende bronnen voor meer informatie:
- [Azure Security Best Practice 11: architectuur. Eén uniforme beveiligingsstrategie](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark: netwerkbeveiliging](/azure/security/benchmarks/security-controls-v2-network-security)

- [Overzicht van Azure-netwerkbeveiliging](/azure/security/fundamentals/network-overview)

- [Strategie voor architectuur van bedrijfsnetwerk](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Strategie voor het gebruik van identiteiten en uitgebreide toegang definiëren

**Richtlijnen**: Stel een benadering op voor het gebruik van identiteiten en uitgebreide toegang als onderdeel van de algehele strategie voor toegangsbeheer in uw organisatie.  

Deze strategie moet gedocumenteerde richtlijnen, beleid en standaarden bevatten voor de volgende elementen: 

-   Een gecentraliseerd identiteits- en verificatiesysteem en bijbehorende interconnectiviteit met andere interne en externe identiteitssystemen

-   Krachtige verificatiemethoden in verschillende gebruiksscenario's en onder verschillende voorwaarden

-   Bescherming van gebruikers met zeer uitgebreide bevoegdheden

-   Bewaking en verwerking van afwijkende gebruikersactiviteiten  

-   Proces voor het beoordelen en op elkaar afstemmen van de identiteit en toegangsrechten van gebruikers

Raadpleeg de volgende bronnen voor meer informatie:

- [Azure Security Benchmark: Identity management](/azure/security/benchmarks/security-controls-v2-identity-management) (Azure Security Benchmark: identiteitsbeheer)

- [Azure Security Benchmark - Privileged access](/azure/security/benchmarks/security-controls-v2-privileged-access) (Azure Security Benchmark: uitgebreide toegang)

- [Azure Security Best Practice 11: architectuur. Eén uniforme beveiligingsstrategie](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Overzicht van beveiliging met Azure-identiteitsbeheer](/azure/security/fundamentals/identity-management-overview)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Strategie voor logboekregistratie en respons op bedreigingen definiëren

**Richtlijnen**: Stel een strategie op voor logboekregistratie en respons op bedreigingen om bedreigingen snel te detecteren en op te lossen terwijl tegelijkertijd aan alle nalevingsvereisten wordt voldaan. Ken een hoge prioriteit toe aan het bieden van waarschuwingen van hoge kwaliteit en naadloze ervaringen aan analisten, zodat ze zich kunnen concentreren op bedreigingen in plaats van op integraties en handmatig uit te voeren stappen. 

Deze strategie moet gedocumenteerde richtlijnen, beleid en standaarden bevatten voor de volgende elementen: 

-   De rol en verantwoordelijkheden van de personen of groepen die binnen de organisatie beveiligingsactiviteiten (SecOps) uitvoeren 

-   Een goed gedefinieerd proces voor het reageren op incidenten dat is afgestemd op het NIST of een ander framework binnen de branche 

-   Logboekregistratie en retentie om ondersteuning te bieden voor de detectie van bedreigingen, het reageren op incidenten en het naleven van regelgeving

-   Informatie en correlatiegegevens over bedreigingen die centraal beschikbaar zijn via SIEM, systeemeigen Azure-mogelijkheden en andere bronnen 

-   Communicatie- en meldingenplan met uw klanten, leveranciers en openbaar belanghebbenden

-   Gebruik van systeemeigen Azure-platforms en platforms van derden voor het afhandelen van incidenten, zoals logboekregistratie en detectie van bedreigingen, forensische onderzoeken en het oplossen en uitschakelen van aanvallen

-   Processen voor het afhandelen van incidenten en activiteiten na incidenten, zoals geleerde lessen en het bewaren van bewijsmateriaal

Raadpleeg de volgende bronnen voor meer informatie:

- [Azure Security Benchmark: logboekregistratie en detectie van bedreigingen](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)

- [Azure Security Benchmark: respons op incidenten](/azure/security/benchmarks/security-controls-v2-incident-response)

- [Azure Security Best Practice 4: proces. Processen voor respons op incidenten bijwerken voor de cloud](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Handleiding framework voor Azure-acceptatie, logboekregistratie en rapportagebeslissingen](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Schaalaanpassing, beheer en bewaking van Azure Enterprise](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Azure Security Center-bewaking**: Niet van toepassing

**Verantwoordelijkheid**: Klant

## <a name="next-steps"></a>Volgende stappen

- Zie [Overzicht Azure Security Benchmark V2](/azure/security/benchmarks/overview)
- Meer informatie over [Azure-beveiligingsbasislijnen](/azure/security/benchmarks/security-baselines-overview)