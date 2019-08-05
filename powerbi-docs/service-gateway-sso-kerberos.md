---
title: Kerberos gebruiken voor SSO (eenmalige aanmelding) bij on-premises gegevensbronnen
description: De gateway configureren met Kerberos om SSO in te schakelen vanuit Power BI naar on-premises gegevensbronnen
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/25/2019
LocalizationGroup: Gateways
ms.openlocfilehash: bea8b954cb1c0743745ef6d3bf9d48aa8513f2fe
ms.sourcegitcommit: bc688fab9288ab68eaa9f54b9b59cacfdf47aa2e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68624063"
---
# <a name="use-kerberos-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Kerberos gebruiken voor eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI

Gebruik [beperkte delegatie van Kerberos](/windows-server/security/kerberos/kerberos-constrained-delegation-overview) om naadloze connectiviteit dankzij eenmalige aanmelding (SSO) mogelijk te maken. Met inschakeling van SSO is het eenvoudiger om gegevens van on-premises gegevensbronnen te vernieuwen in Power BI-rapporten en -dashboards.

## <a name="supported-data-sources"></a>Ondersteunde gegevensbronnen

Momenteel worden de volgende gegevensbronnen ondersteund:

* SQL Server
* SAP HANA
* SAP BW
* Teradata
* Spark
* Impala

Ook SAP HANA met [Security Assertion Markup Language (SAML)](service-gateway-sso-saml.md) wordt ondersteund.

### <a name="sap-hana"></a>SAP HANA

Volg eerst deze stappen om SSO in te schakelen voor SAP HANA:

* Zorg ervoor dat de SAP HANA-server de vereiste minimumversie uitvoert die afhankelijk is van het platform-niveau van uw SAP HANA-server:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Installeer op de gatewaycomputer het meest recente HANA ODBC-stuurprogramma van SAP.  De minimaal vereiste versie is HANA ODBC versie 2.00.020.00, vrijgegeven in augustus 2017.

Zie [Eenmalige aanmelding met behulp van Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) in de SAP HANA-beveiligingshandleiding voor meer informatie over het instellen van eenmalige aanmelding voor SAP HANA met behulp van Kerberos. Zie ook de koppelingen vanaf die pagina, met name SAP Note 1837331: HOWTO HANA DBSSO Kerberos/Active Directory.

## <a name="prepare-for-kerberos-constrained-delegation"></a>Voorbereiden voor beperkte Kerberos-delegering

U moet meerdere items configureren om ervoor te zorgen dat beperkte Kerberos-delegering goed werkt, waaronder *Service Principal Names* (SPN) en delegeringsinstellingen voor serviceaccounts.

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>Vereiste 1: De on-premises gegevensgateway van Microsoft installeren en configureren

Deze versie van de on-premises gegevensgateway biedt ondersteuning voor een upgrade ter plekke, evenals voor het overnemen van de instellingen van bestaande gateways.

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>Vereiste 2: De gatewayservice in Windows moet worden uitgevoerd als een domeinaccount

In een standaardinstallatie wordt de gateway uitgevoerd als een lokaal serviceaccount (namelijk *NT Service\PBIEgwService*).

![Schermopname van het serviceaccount](media/service-gateway-sso-kerberos/service-account.png)

Om beperkte Kerberos-delegering in te schakelen, moet de gateway worden uitgevoerd als een domeinaccount, tenzij uw Azure AD-exemplaar (Azure Active Directory) al wordt gesynchroniseerd met uw lokale Active Directory-exemplaar (via Azure AD DirSync/Connect). Zie [Gatewayserviceaccount wijzigen](/data-integration/gateway/service-gateway-service-account) om te schakelen naar een domeinaccount.

> [!NOTE]
> Als Azure AD Connect is geconfigureerd en gebruikersaccounts zijn gesynchroniseerd, hoeft de gatewayservice tijdens runtime geen lokale Azure AD-zoekacties uit te voeren. U kunt de lokale service-SID gebruiken (in plaats van een domeinaccount) voor de gatewayservice. De stappen voor het configureren van beperkte Kerberos-delegering die in dit artikel worden beschreven zijn verder hetzelfde als voor die configuratie. Ze worden nu op het computerobject van de gateway in Azure AD toegepast in plaats van op het domeinaccount.

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>Vereiste 3: U moet beschikken over domeinbeheerdersrechten om instellingen voor SPN's (SetSPN) en de beperkte Kerberos-delegering te configureren

Het is niet aan te raden dat een domeinbeheerder iemand anders tijdelijk of permanent rechten geeft om SPN-namen en Kerberos-delegatie te configureren zonder dat daarbij domeinbeheerdersrechten vereist zijn. In het volgende gedeelte worden de aanbevolen configuratiestappen in meer detail besproken.

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>Beperkte Kerberos-delegering configureren voor de gateway en de gegevensbron

Configureer als domeinbeheerder een SPN-naam voor het domeinaccount van de gatewayservice en configureer delegeringsinstellingen in het domeinaccount van de gatewayservice.

### <a name="configure-an-spn-for-the-gateway-service-account"></a>Een SPN voor het gatewayserviceaccount configureren

Bepaal eerst of er al een SPN is gemaakt voor het domeinaccount dat wordt gebruikt als gatewayserviceaccount:

1. Open **Active Directory: gebruikers en computers** als domeinbeheerder.

2. Klik met de rechtermuisknop op het domein, selecteer **Zoeken** en voer de accountnaam van het gatewayserviceaccount in.

3. Klik in de zoekresultaten met de rechtermuisknop op het gatewayserviceaccount en selecteer **Eigenschappen**.

4. Als het tabblad **Delegering** zichtbaar is in het dialoogvenster **Eigenschappen**, is er al een SPN-naam gemaakt. U kunt direct doorgaan naar het configureren van de delegeringsinstellingen.

    Als het dialoogvenster **Eigenschappen** geen tabblad **Delegering** bevat, kunt u voor dat account handmatig een SPN-naam maken. Hierdoor wordt het tabblad **Delegering** toegevoegd. Gebruik het [setspn-hulpprogramma](https://technet.microsoft.com/library/cc731241.aspx) dat standaard deel uitmaakt van Windows (u moet domeinbeheerdersrechten hebben om de SPN te maken).

    Stel u bijvoorbeeld voor dat het gatewayserviceaccount 'PBIEgwTest\GatewaySvc' heet en de naam van de computer waarop de gatewayservice wordt uitgevoerd **Machine1** heet. Om de SPN voor het gatewayserviceaccount in te stellen voor de computer in dit voorbeeld, voert u de volgende opdracht uit:

    ![Afbeelding van de opdracht SPN-naam instellen](media/service-gateway-sso-kerberos/set-spn.png)

    Nu deze stap is voltooid, kunnen we verdergaan met het configureren van de delegeringsinstellingen.

### <a name="configure-delegation-settings-on-the-gateway-service-account"></a>De delegeringsinstellingen configureren voor het gatewayserviceaccount

De tweede configuratievereiste betreft de delegeringsinstellingen voor het gatewayserviceaccount. Er zijn verschillende hulpprogramma's die u kunt gebruiken om deze stappen uit te voeren. Hier gebruiken we Active Directory: gebruikers en computers, een MMC-module (Microsoft Management Console) om informatie in de directory te beheren en te publiceren. Deze module is standaard beschikbaar op domeincontrollers. U kunt deze ook inschakelen via de configuratie van Windows-onderdelen op andere computers.

We moeten beperkte Kerberos-delegering met protocoldoorvoer configureren. Met beperkte delegatie moet u expliciet zijn wat betreft de services waarnaar u wilt delegeren. Zo worden delegatieaanroepen vanuit het gatewayserviceaccount alleen geaccepteerd door SQL-server of uw SAP HANA-server.

In deze sectie wordt ervan uitgegaan dat u al SNP's hebt geconfigureerd voor uw onderliggende gegevensbronnen (zoals SQL Server, SAP HANA, Teradata en Spark). Raadpleeg de technische documentatie voor de desbetreffende gegevensbronserver voor meer informatie over het configureren van SPN-namen voor de gegevensbronserver. U kunt ook kijken bij de kop *Welke SPN-naam heeft uw app nodig?* in het blogbericht [Mijn Kerberos-controlelijst](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160).

In de volgende stappen wordt uitgegaan van een on-premises omgeving met twee computers: een gatewaycomputer en een databaseserver met SQL Server. In dit voorbeeldscenario worden de volgende instellingen en namen gebruikt:

* Naam van de gatewaymachine: **PBIEgwTestGW**
* Gatewayserviceaccount: **PBIEgwTest\GatewaySvc** (weergavenaam account: Gateway Connector)
* Computernaam SQL Server-gegevensbron: **PBIEgwTestSQL**
* Serviceaccount voor SQL Server-gegevensbron: **PBIEgwTest\SQLService**

U kunt de delegeringsinstellingen als volgt configureren:

1. Start als domeinbeheerder **Active Directory: gebruikers en computers**.

2. Klik met de rechtermuisknop op het gatewayserviceaccount (**PBIEgwTest\GatewaySvc**) en selecteer **Eigenschappen**.

3. Selecteer het tabblad **Delegering**.

4. Selecteer **Deze computer mag alleen aan opgegeven services delegeren** > **Elk protocol voor authenticatie gebruiken**.

5. Selecteer **Toevoegen** onder **Services waaraan dit account gedelegeerde referenties kan presenteren**.

6. Selecteer **Gebruikers of computers** in het nieuwe dialoogvenster.

7. Voer het serviceaccount voor de gegevensbron in. Een SQL Server-gegevensbron kan bijvoorbeeld een serviceaccount **PBIEgwTest\SQLService** hebben. Zodra het account is toegevoegd, selecteert u **OK**.

8. Selecteer de SPN die u hebt gemaakt voor de databaseserver. In ons voorbeeld begint de SPN-naam met **MSSQLSvc**. Als u zowel de FQDN als de NetBIOS SPN voor uw databaseservice hebt toegevoegd, selecteert u deze hier allebei. Mogelijk ziet u er maar één.

9. Selecteer **OK**. De SPN staat nu in de lijst.

    U kunt optioneel ook **Uitgevouwen** selecteren om zowel de FQDN als de SPN-naam van NetBIOS weer te geven. Het dialoogvenster ziet er als volgt uit als u **Uitgevouwen** hebt ingeschakeld. Selecteer **OK**.

    ![Schermopname van het dialoogvenster Connectoreigenschappen van de gateway](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

Ten slotte moet u op de computer waarop de gatewayservice wordt uitgevoerd (**PBIEgwTestGW** in ons voorbeeld), het lokale beleid **Een client nabootsen na verificatie** en **Funtioneren als deel van het besturingssysteem (SeTcbPrivilege)** aan het gatewayserviceaccount toewijzen. U kunt deze configuratie bewerkstelligen en controleren met de Lokale groepsbeleidobjecteditor (**gpedit**).

1. Voer op de gatewaycomputer *gpedit.msc* uit.

1. Ga naar **Lokaal computerbeleid** > **Computerconfiguratie** > **Windows-instellingen** > **Beveiligingsinstellingen** > **Lokaal beleid** > **Toewijzing van gebruikersmachtigingen**.

    ![Schermopname van de mapstructuur voor Lokaal computerbeleid](media/service-gateway-sso-kerberos/user-rights-assignment.png)

1. Selecteer onder **Toewijzing van gebruikersrechten** in de lijst met beleidsregels de optie **Een client nabootsen na verificatie**.

    ![Schermopname van het beleid Een client imiteren](media/service-gateway-sso-kerberos/impersonate-client.png)

    Klik met de rechtermuisknop om **Eigenschappen** te openen. Controleer de lijst met accounts. Hier moet het gatewayserviceaccount (**PBIEgwTest\GatewaySvc**) op staan.

1. Selecteer onder **Toewijzing van gebruikersrechten** in de lijst met beleidsregels de optie **Functioneren als deel van het besturingssysteem (SeTcbPrivilege)** . Zorg ervoor dat het gatewayserviceaccount ook wordt opgenomen in de lijst met accounts.

1. Start het serviceproces van de **on-premises gegevensgateway** opnieuw op.

Als u van SAP HANA gebruikmaakt, is het aan te raden de volgende aanvullende stappen te volgen om de prestaties mogelijk iets te kunnen verbeteren.

1. Zoek en open dit configuratiebestand in de installatiemap van de gateway: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

1. Zoek de eigenschap *FullDomainResolutionEnabled* en wijzig de waarde ervan in *True*.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

## <a name="run-a-power-bi-report"></a>Een Power BI-rapport uitvoeren

Nadat alle configuratiestappen zijn voltooid, kunt u de pagina **Gateway beheren** in Power BI gebruiken om de gegevensbron te configureren. Schakel onder de **Geavanceerde instellingen** SSO in en publiceer rapporten en gegevenssets die een binding met die gegevensbron hebben.

![Schermopname van de optie Geavanceerde instellingen](media/service-gateway-sso-kerberos/advanced-settings.png)

Deze configuratie werkt in de meeste gevallen. Er kunnen echter andere Kerberos-configuraties nodig zijn, afhankelijk van uw omgeving. Als het rapport nog steeds niet wordt geladen, neemt u contact op met uw domeinbeheerder voor verdere hulp.

## <a name="configure-sap-bw-for-sso-using-commoncryptolib"></a>SAP BW configureren voor SSO met behulp van CommonCryptoLib

Nu u inzicht hebt in de werking van Kerberos met een gateway, kunt u SSO configureren voor uw SAP Business Warehouse (SAP BW). In de volgende stappen wordt ervan uitgegaan dat u al bent [voorbereid voor beperkte delegatie van Kerberos](#prepare-for-kerberos-constrained-delegation), zoals eerder in dit artikel beschreven.

> [!NOTE]
> Deze instructies gaan over de SSO-installatie voor SAP BW-**toepassingsservers**. Microsoft biedt momenteel geen ondersteuning voor SSO-verbindingen met SAP BW-**berichtservers**.

1. Zorg ervoor dat uw BW-server op de juiste manier is geconfigureerd voor Kerberos-SSO. Als dit het geval is, moet u SSO kunnen gebruiken voor toegang tot uw BW-server met een SAP-hulpprogramma zoals SAP GUI. Zie voor meer informatie over de installatiestappen [Eenmalige aanmelding van SAP: verificatie met Kerberos/SPNEGO](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/). Voor uw BW-server moet CommonCryptoLib als SNC-bibliotheek worden gebruikt. De server moet een SNC-naam hebben die begint met ‘CN=’, zoals ’CN=BW1’. Zie [SNC-parameters voor Kerberos-configuratie](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html) (de snc/identity/as-parameter) voor meer informatie over vereisten voor SNC-namen.

1. Als u dit niet al hebt gedaan, voltooit u de stappen onder [Voorbereiden voor beperkte Kerberos-delegering](https://docs.microsoft.com/power-bi/service-gateway-sso-kerberos#prepare-for-kerberos-constrained-delegation). Zorg ervoor dat uw gatewayservicegebruiker is geconfigureerd om gedelegeerde referenties aan te bieden aan de servicegebruiker die uw BW-toepassingsserver in uw Active Directory-omgeving vertegenwoordigt.

1. Als u dit nog niet hebt gedaan, installeert u nu de 64-bitsversie van de [SAP .NET Connector](https://support.sap.com/en/product/connectors/msnet.html) op de computer waarop de gateway is geïnstalleerd. U kunt controleren of het onderdeel is geïnstalleerd door verbinding te maken met uw BW-server in Power BI Desktop. Als u geen verbinding kunt maken met behulp van de 2.0-implementatie, is de .NET Connector niet geïnstalleerd.

1. Zorg ervoor dat SAP Secure Login Client (SLC) niet wordt uitgevoerd op de computer waarop de gateway is geïnstalleerd. Via SLC worden Kerberos-tickets zodanig in de cache geplaatst dat dit invloed kan hebben op het vermogen van de gateway om Kerberos voor SSO te gebruiken. Als SLC is geïnstalleerd, verwijdert u dit of sluit u SAP Secure Login Client af: klik met de rechtermuisknop op het pictogram in het systeemvak en selecteer Afmelden en Afsluiten voordat u probeert een SSO-verbinding te maken met behulp van de gateway. SLC wordt niet ondersteund voor gebruik op Windows Server-computers. Zie [SAP-notitie 2780475](https://launchpad.support.sap.com/#/notes/2780475) (s-gebruiker vereist) voor meer informatie.

    ![SAP-client voor beveiligde aanmelding](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    Als u SLC verwijdert of **Afmelden** en **Afsluiten** selecteert, opent u een cmd-venster en voert u `klist purge` in om alle gecachte Kerberos-tickets te wissen voordat u probeert een SSO-verbinding tot stand te brengen via de gateway.

1. Download CommonCryptoLib (sapcrypto.dll) versie **8.5.25 of hoger** via het SAP Launchpad en kopieer deze versie naar een map op uw gatewaycomputer. In dezelfde map waarnaar u sapcrypto.dll hebt gekopieerd, maakt u een bestand met de naam sapcrypto.ini, met de volgende inhoud:

    ```
    ccl/snc/enable\_kerberos\_in\_client\_role = 1
    ```

    Het .ini-bestand bevat configuratie-informatie die voor CommonCryptoLib vereist is om SSO in te schakelen in het gatewayscenario.

    > [!NOTE]
    > Deze bestanden moeten worden opgeslagen op dezelfde locatie; met andere woorden: _/pad/naar/sapcrypto/_ moet zowel sapcrypto.ini als sapcrypto.dll bevatten.

    Zowel de gatewayservicegebruiker als de Active Directory-gebruiker (AD) die door de servicegebruiker wordt geïmiteerd hebben lees- en uitvoermachtigingen nodig voor beide bestanden. U wordt aangeraden machtigingen voor zowel het .ini- als het .dll-bestand toe te wijzen aan de geverifieerde gebruikersgroep. Voor testdoeleinden kunt u deze machtigingen ook expliciet toewijzen aan zowel de gatewayservicegebruiker als de geïmiteerde gebruiker. In het onderstaande schermopname zijn aan de geverifieerde gebruikersgroep **lees- &amp; uitvoer**machtigingen voor sapcrypto.dll toegewezen:

    ![Geverifieerde gebruikers](media/service-gateway-sso-kerberos/authenticated-users.png)

1. Als u geen SAP Business Warehouse Server-gegevensbron hebt, kunt u op de pagina **Gateways beheren** in de Power BI-service een gegevensbron toevoegen. Als u al een BW-gegevensbron hebt gekoppeld aan de gateway waarlangs de SSO-verbinding moet stromen, moet u het bewerken hiervan voorbereiden.

    Voor **SNC-bibliotheek** selecteert u **SNC\_LIB of SNC\_LIB\_64 omgevingsvariabele** of **Aangepast**. Als u de optie **SNC\_LIB** selecteert, moet u de waarde van de SNC\_LIB\_64-omgevingsvariabele op de gatewaycomputer instellen op het absolute pad van de kopie van sapcrypto.dll op de gatewaycomputer, zoals C:\Gebruikers\Test\Desktop\sapcrypto.dll. Als u **Aangepast** kiest, plakt u het absolute pad naar sapcrypto.dll in het veld Pad naar aangepaste SNC-bibliotheek dat op de pagina **Gateways beheren** wordt weergegeven.

    Onder **Geavanceerde instellingen** controleert u of het selectievakje **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery-query's** is ingeschakeld. Voor de gebruikersnaam die u invoert, is alleen een machtiging nodig om verbinding te maken met de BW-server. Deze wordt voornamelijk gebruikt om de gegevensbronverbinding te testen nadat deze tot stand is gebracht. De gebruiker wordt ook gebruikt om eventuele rapporten te vernieuwen die zijn gemaakt op basis van op import gebaseerde gegevenssets. Als u **Basisverificatie** selecteert, moet u een BW-gebruiker opgeven. Als u **Windows**-authenticatie selecteert, moet u een Windows Active Directory-gebruiker opgeven die via de SU01-transactie in SAP GUI aan een BW-gebruiker is toegewezen. De rest van de velden (**Systeemnummer **,** Client-id **,** SNC-partnernaam**, enzovoort) moet overeenkomen met de informatie die u in Power BI Desktop moet invoeren om verbinding te maken met uw BW-server via SSO. Selecteer **Toepassen** en controleer of de testverbinding tot stand is gebracht.

    ![Verificatiemethode](media/service-gateway-sso-kerberos/authentication-method.png)

1. Maak een omgevingsvariabele voor het CCL\_PROFILE-systeem en richt deze op sapcrypto.ini:

    ![Omgevingsvariabele voor CCL\_PROFILE-systeem](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    Let op: de bestanden sapcrypto.dll en sapcrypto.ini moeten zich op dezelfde locatie bevinden. In het bovenstaande voorbeeld, waarin sapcrypto.ini zich op het bureaublad bevindt, moet sapcrypto.dll ook op het bureaublad staan.

1. Start de gatewayservice opnieuw op:

    ![Gatewayservice opnieuw opstarten](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. Publiceer een **op DirectQuery gebaseerd** BW-rapport vanuit Power BI Desktop. Voor dit rapport moeten gegevens worden gebruikt die toegankelijk zijn voor de BW-gebruiker die is toegewezen aan de Azure Active Directory-gebruiker (AAD) die zich bij de Power BI-service aanmeldt. Gebruik DirectQuery in plaats van importeren; dit heeft te maken met de manier waarop gegevens worden vernieuwd. Wanneer u op import gebaseerde rapporten vernieuwt, worden op de gateway de referenties gebruikt die u in de velden **Gebruikersnaam** en **Wachtwoord** hebt ingevoerd toen u de BW-gegevensbron hebt gemaakt. Met andere woorden: Kerberos SSO wordt **niet** gebruikt. Bovendien moet u er tijdens het publiceren voor zorgen dat u de gateway selecteert die u voor BW SSO hebt geconfigureerd (indien u meerdere gateways hebt). In de Power BI-service kunt u nu het rapport vernieuwen of een nieuw rapport maken op basis van de gepubliceerde gegevensset.

### <a name="troubleshooting"></a>Problemen oplossen

Als u het rapport niet kunt vernieuwen in de Power BI-service, kunt u gatewaytracering, CPIC-tracering en CommonCryptoLib-tracering gebruiken om het probleem te diagnosticeren. CPIC-tracering en CommonCryptoLib zijn SAP-producten. Microsoft kan hiervoor dus geen directe ondersteuning bieden. Active Directory-gebruikers aan wie SSO-toegang tot BW wordt verleend, moeten voor een aantal Active Directory-configuraties mogelijk lid zijn van de beheerdersgroep op de computer waarop de gateway is geïnstalleerd.

1. **Gatewaylogboeken:** Reproduceer het probleem, open de [gateway-app](https://docs.microsoft.com/data-integration/gateway/service-gateway-app), ga naar het tabblad **Diagnostiek** en selecteer **Logboeken exporteren**:

    ![Gatewaylogboeken exporteren](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **CPIC-tracering:** Als u CPIC-tracering wilt inschakelen, moet u twee omgevingsvariabelen instellen: CPIC\_TRACE en CPIC\_TRACE\_DIR. Met de eerste variabele wordt het traceringsniveau ingesteld, met de tweede variabele wordt de bestandsmap voor tracering ingesteld. De map moet een locatie zijn waarnaar leden van de geverifieerde gebruikersgroep kunnen schrijven. Stel CPIC\_TRACE in op 3 en CPIC\_TRACE\_DIR naar de map waarnaar u traceringsbestanden wilt schrijven.

    ![CPIC-tracering](media/service-gateway-sso-kerberos/cpic-tracing.png)

    Reproduceer het probleem en controleer of CPIC\_TRACE\_DIR traceringsbestanden bevat.

1. **CommonCryptoLib-tracering:** Schakel CommonCryptoLib-tracering in door twee regels toe te voegen aan het sapcrypto.ini-bestand dat u eerder hebt gemaakt:

    ```
    ccl/trace/level=5
    ccl/trace/directory=\\<drive\\>:\logs\sectrace
    ```

    Wijzig de optie _ccl/trace/map_ in een locatie waarnaar leden van de geverifieerde gebruikersgroep kunnen schrijven. Een andere mogelijkheid is een nieuw .ini-bestand maken om dit gedrag te veranderen. In dezelfde map als sapcrypto.ini en sapcrypto.dll maakt u een bestand met de naam sectrace.ini, met de volgende inhoud.  Vervang de mapoptie door een locatie op uw computer waarnaar Geverifieerde gebruiker kunnen schrijven:

    ```
    LEVEL = 5
    
    DIRECTORY = \\<drive\\>:\logs\sectrace
    ```

    Reproduceer nu het probleem en controleer of de locatie waarnaar MAP verwijst de traceringsbestanden bevat. Schakel CPIC- en CCL-tracering uit zodra u klaar bent.

    Zie [SAP-notitie 2491573](https://launchpad.support.sap.com/#/notes/2491573) (s-gebruiker vereist) voor meer informatie over CommonCryptoLib-tracering.

## <a name="configure-sap-bw-for-sso-using-gsskrb5gx64krb5"></a>SAP BW voor SSO configureren met behulp van gsskrb5/gx64krb5

Als u CommonCryptoLib niet als uw SNC-bibliotheek kunt gebruiken, kunt u in plaats daarvan gsskrb5/gx64krb5 gebruiken. De installatiestappen zijn echter aanzienlijk complexer en SAP biedt niet langer ondersteuning voor gsskrb5.

We hebben geprobeerd deze handleiding zo uitgebreid mogelijk te maken. Als u een aantal van deze stappen al hebt uitgevoerd, kunt u deze overslaan. Als u bijvoorbeeld al een servicegebruiker voor uw SAP BW-server hebt gemaakt en aan deze gebruiker een SPN hebt toegewezen, of als u de `gsskrb5`-bibliotheek al hebt geïnstalleerd.

### <a name="set-up-gsskrb5gx64krb5-on-client-machines-and-the-sap-bw-server"></a>gsskrb5/gx64krb5 instellen op clientcomputers en de SAP BW-server

> [!NOTE]
> `gsskrb5/gx64krb5` wordt niet meer actief ondersteund door SAP. Zie [SAP-notitie 352295](https://launchpad.support.sap.com/#/notes/352295) voor meer informatie. Houd er ook rekening mee dat met `gsskrb5/gx64krb5` geen SSO-verbinding (met eenmalige aanmelding) kan worden gemaakt met de SAP BW-berichtenservers via de gegevensgateway. Er kan alleen verbinding worden gemaakt met SAP BW-toepassingsservers. Het is nu mogelijk om sapcrypto/CommonCryptoLib te gebruiken als de SNC-bibliotheek, waarmee het configuratieproces wordt vereenvoudigd. 

`gsskrb5` moet zowel op de client als op de server worden gebruikt om een SSO-verbinding te voltooien via de gateway.

1. Download `gsskrb5` of `gx64krb5`, afhankelijk van de gewenste hoeveelheid bits, van [SAP Note 2115486](https://launchpad.support.sap.com/) (SAP S-gebruiker vereist). Zorg ervoor dat u minstens over versie 1.0.11.x beschikt.

1. Plaats de bibliotheek op een locatie op de gatewaycomputer die toegankelijk is voor uw gatewayinstantie (en voor de SAP-GUI als u de SSO-verbinding wilt testen met behulp van SAP-aanmelding).

1. Plaats een andere kopie op uw SAP BW-servercomputer op een locatie die toegankelijk is voor de SAP BW-server.

1. Stel op de client- en servercomputers de omgevingsvariabelen `SNC_LIB` of `SNC_LIB_64` in om te verwijzen naar de locatie van gsskrb5.dll of gx64krb5.dll. Zoals u ziet hebt u slechts een van deze bibliotheken nodig, niet beide.

### <a name="create-a-sap-bw-service-user-and-enable-snc-communication"></a>Een SAP BW-servicegebruiker maken en SNC-communicatie inschakelen

Naast de configuratie van de gateway die u al hebt voltooid, zijn er enkele aanvullende stappen specifiek voor SAP BW. In het gedeelte [Instellingen voor het configureren van delegatie op het gatewayserviceaccount](#configure-delegation-settings-on-the-gateway-service-account) van de documentatie wordt ervan uitgegaan dat u al SPN-namen hebt geconfigureerd voor uw onderliggende gegevensbronnen. De gatewayconfiguratie voor SAP BW voltooien:

1. Maak op een Active Directory-domeincontrollerserver een servicegebruiker (in eerste instantie een gewone Active Directory-gebruiker) voor de SAP BW-toepassingsserver in de Active Directory-omgeving. Wijs er vervolgens een SPN-naam aan toe.

    U wordt aangeraden om de SPN-naam te beginnen met `SAP/`, maar u kunt ook andere voorvoegsels gebruiken, zoals `HTTP/`. Wat u na `SAP/` invoert is aan u. Gebruik bijvoorbeeld de gebruikersnaam van de servicegebruiker van de SAP BW-server. Als u bijvoorbeeld `BWServiceUser@\<DOMAIN\>` als uw servicegebruiker maakt, kunt u de `SAP/BWServiceUser` van de SPN gebruiken. Eén manier om de SPN-naam toe te wijzen is met de opdracht setspn. Als u de SPN-naam bijvoorbeeld wilt instellen op de servicegebruiker die zojuist is gemaakt, moet u de volgende opdracht uitvoeren vanuit een cmd-venster op een domeincontrollercomputer: `setspn -s SAP/ BWServiceUser DOMAIN\ BWServiceUser`. Zie de SAP BW-documentatie voor meer informatie.

1. Geef de servicegebruiker toegang tot de SAP BW-toepassingsserver:

    1. Voeg op de SAP BW-servercomputer de servicegebruiker toe aan de lokale beheerdersgroep voor de SAP BW-server. Open het programma Computerbeheer en dubbelklik op de lokale beheerdersgroep voor uw server.

        ![Schermopname van het programma Computerbeheer](media/service-gateway-sso-kerberos/computer-management.png)

    1. Dubbelklik op de groep Lokale beheerders en selecteer vervolgens **Toevoegen** om uw servicegebruiker toe te voegen aan de groep. Selecteer **Namen controleren** om te controleren of u de naam goed hebt ingevoerd. Selecteer **OK**.

1. Stel de servicegebruiker van de SAP BW-server in als de gebruiker die de SAP BW-serverservice start op de SAP BW-servercomputer.

    1. Open **Uitvoeren** en voer 'Services.msc' in. Zoek de service die overeenkomt met uw instantie van de SAP BW-toepassingsserver. Klik er met de rechtermuisknop op en selecteer **Eigenschappen**.

        ![Schermopname van Services, waarbij Eigenschappen is gemarkeerd](media/service-gateway-sso-kerberos/server-properties.png)

    1. Schakel over naar het tabblad **Aanmelden** en wijzig de gebruiker in uw SAP BW-servicegebruiker. Voer het wachtwoord van de gebruiker in en selecteer **OK**.

1. Meld u bij uw server aan bij SAP-aanmelding en stel de volgende profielparameters in met behulp van de transactie RZ10:

    1. Stel de profielparameter snc/identity/as in op p:\<de SAP BW-servicegebruiker die u hebt gemaakt\>, bijvoorbeeld p:BWServiceUser@MYDOMAIN.COM. Let op de p: die voorafgaat aan de UPN van de servicegebruiker. Het is geen p:CN=like wanneer Common Crypto Lib als de SNC-bibliotheek wordt gebruikt.

    1. Stel de profielparameter snc/gssapi\_lib in op \<pad naar gsskrb5.dll/gx64krb5.dll op de servercomputer (de bibliotheek die u gaat gebruiken hangt af van de hoeveelheid bits van het besturingssysteem)\>. Vergeet niet om de bibliotheek te plaatsen op een locatie die toegankelijk is voor de SAP BW-toepassingsserver.

    1. Stel ook de volgende aanvullende profielparameters in en wijzig zo nodig de waarden naar behoefte. Houd er rekening mee dat bij de laatste vijf opties clients via SAP-aanmelden verbinding kunnen maken met de SAP BW-server zonder dat de SNC is geconfigureerd.

        | **Instelling** | **Waarde** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Stel de eigenschap snc/enable in op 1.

1. Open na het instellen van deze profielparameters de SAP-beheerconsole op de servercomputer en start de SAP BW-instantie opnieuw op. Als de server niet start, controleert u of u de profielparameters juist hebt ingesteld. Zie de [SAP-documentatie](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm) voor meer informatie over de profielparameterinstellingen. U kunt ook onze probleemoplossingsinformatie verderop in deze sectie raadplegen als u problemen ondervindt.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Een SAP BW-gebruiker toewijzen aan een Active Directory-gebruiker

Wijs een Active Directory-gebruiker toe aan een SAP BW-toepassingsservergebruiker en test de SSO-verbinding bij SAP-aanmelding.

1. Meld u met behulp van SAP-aanmelding aan bij uw SAP BW-server. Voer transactie SU01 uit.

1. Voer bij **Gebruiker** de SAP BW-gebruiker in voor wie u SSO-verbindingen wilt inschakelen (in de vorige schermafbeelding worden machtigingen ingesteld voor BIUSER). Selecteer het pictogram **Bewerken** in de linkerbovenhoek van het SAP-aanmeldingsvenster (de afbeelding van een pen).

    ![Schermopname van het SAP BW-scherm voor gebruikersonderhoud](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Selecteer het tabblad **SNC**. Voer in het invoervak voor de SNC-naam p:\<uw Active Directory-gebruiker\>@\<uw domein\> in. Let op de verplichte p: die vooraf moet gaan aan de UPN van de Active Directory-gebruiker. De Active Directory-gebruiker die u opgeeft, moet horen bij de persoon of organisatie waarvoor u SSO-toegang tot de SAP BW-toepassingsserver wilt inschakelen. Als u bijvoorbeeld SSO-toegang wilt inschakelen voor de gebruiker testuser \@TESTDOMAIN.COM, voert u p:testuser@TESTDOMAIN.COM in.

    ![Schermopname van het SAP BW-scherm Gebruikers onderhouden](media/service-gateway-sso-kerberos/maintain-users.png)

1. Selecteer het pictogram **Opslaan** (de diskette in de linkerbovenhoek van het scherm).

### <a name="test-sign-in-by-using-sso"></a>Aanmelding met behulp van SSO testen

Controleer of u zich bij de server kunt aanmelden. Gebruik SAP-aanmelding via eenmalige aanmelding als de Active Directory-gebruiker voor wie u zojuist toegang via eenmalige aanmelding hebt ingeschakeld.

1. Meld u op een computer waarop SAP-aanmelding is geïnstalleerd aan als de Active Directory-gebruiker voor wie u zojuist SSO-toegang hebt ingeschakeld. Start SAP-aanmelding en maak een nieuwe verbinding.

1. Selecteer in het scherm **Nieuwe systeemvermelding maken** de optie **Gebruikergespecificeerd systeem** > **Volgende**.

    ![Schermopname van het scherm Nieuwe systeemvermelding maken](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Vul de relevante gegevens in op het volgende scherm, met inbegrip van de toepassingsserver, het instantienummer en de systeem-id. Selecteer vervolgens **Voltooien**.

1. Klik met de rechtermuisknop op de nieuwe verbinding en selecteer **Eigenschappen**. Selecteer het tabblad **Netwerk**. In het tekstvak **SNC Name** voert u p:\<UPN van de SAP BW-servicegebruiker\> in, bijvoorbeeld p:BWServiceUser@MYDOMAIN.COM. Selecteer **OK**.

    ![Schermopname van het scherm Eigenschappen van systeemvermelding](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Dubbelklik op de verbinding die u zojuist hebt gemaakt, om te proberen een SSO-verbinding met de BS-server tot stand te brengen. Als deze verbindingspoging lukt, gaat u verder met de volgende stap. Anders bekijkt u de eerdere stappen in dit document om te controleren of deze correct zijn uitgevoerd of controleert u de sectie met probleemoplossingen hieronder. Houd er rekening mee dat als u in deze context niet via SSO verbinding kunt maken met de SAP BW-server, u ook geen verbinding met de SAP BW-server kunt maken in de gatewaycontext.

### <a name="troubleshoot-installation-and-connections"></a>Installatie- en verbindingsproblemen oplossen

Als u problemen ondervindt, volgt u deze stappen om de problemen met de gsskrb5-installatie en SSO-verbindingen vanuit SAP-aanmelding op te lossen.

* Het kan nuttig zijn om de serverlogboeken (...work\dev\_w0 op de servercomputer) te bekijken om eventuele fouten op te lossen wanneer u de stappen voor het instellen van gsskrb5 voltooit. Dit is met name het geval wanneer de SAP BW-server niet kan worden gestart nadat u de profielparameters hebt gewijzigd.

* Als u de SAP BW-service niet kunt starten vanwege een aanmeldingsfout, hebt u mogelijk het verkeerde wachtwoord opgegeven bij het instellen van de SAP BW-'starten als'-gebruiker. Controleer het wachtwoord door u als de SAP BW-servicegebruiker aan te melden bij een computer in uw Active Directory-omgeving.

* Als de foutmelding wordt weergegeven dat SQL-referenties verhinderen dat de server wordt gestart, controleert u of u de servicegebruiker toegang tot de SAP BW-database hebt verleend.

* Mogelijk krijgt u het volgende bericht: '(GSS-API) specified target is unknown or unreachable' ((GSS-API) Opgegeven doel is onbekend of niet bereikbaar). Dit betekent doorgaans dat u de verkeerde SNC-naam hebt opgegeven. Zorg ervoor dat u in de clienttoepassing naast de UPN van de servicegebruiker alleen 'p:' gebruikt, niet 'p:CN=' of iets anders.

* Mogelijk krijgt u het volgende bericht: '(GSS-API) An invalid name was supplied' ((GSS-API) Mogelijk is er een ongeldige naam opgegeven). Zorg ervoor dat 'p:' de waarde heeft van de profielparameter voor de SNC-identiteit van de server.

* Mogelijk krijgt u het volgende bericht: '(SNC error) the specified module could not be found' ((SNC-fout) Kan de opgegeven module niet vinden). Dit wordt doorgaans veroorzaakt doordat u de `gsskrb5.dll/gx64krb5.dll` op een locatie hebt geplaatst waarvoor verhoogde bevoegdheden (beheerdersrechten) zijn vereist om er toegang tot te krijgen.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Registervermeldingen toevoegen aan de gatewaycomputer

Voeg vereiste registervermeldingen toe aan het register van de computer waarop de gateway is geïnstalleerd. U moet deze opdrachten uitvoeren:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="set-configuration-parameters-on-the-gateway-machine"></a>Configuratieparameters instellen op de gatewaycomputer

Er zijn twee opties voor het instellen van configuratieparameters, afhankelijk van of Azure AD Connect is geconfigureerd zodat gebruikers zich kunnen aanmelden bij de Power BI-service als een Azure AD-gebruiker.

Volg deze stappen als u Azure AD Connect hebt geconfigureerd.

1. Open het configuratiebestand van de hoofdgateway, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Dit bestand bevindt zich standaard in C:\Program Files\On-premises data gateway.

1. Zorg ervoor dat de eigenschap **FullDomainResolutionEnabled** is ingesteld op **True** en dat **SapHanaSsoRemoveDomainEnabled** is ingesteld op **False**.

1. Sla het configuratiebestand op.

1. Klik op het tabblad **Services** met de rechtermuisknop op de gateway-service en selecteer **Opnieuw opstarten**.

    ![Schermopname van het tabblad Taakbeheerservices](media/service-gateway-sso-kerberos/restart-gateway.png)

Als u Azure AD Connect niet hebt geconfigureerd, volgt u deze stappen voor elke Power BI-service die u wilt toewijzen aan een Azure AD-gebruiker. Met deze stappen wordt een Power BI-servicegebruiker handmatig gekoppeld aan een Active Directory-gebruiker met machtigingen voor aanmelden bij SAP BW.

1. Open het configuratiebestand van de hoofdgateway, `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll`. Dit bestand bevindt zich standaard in C:\Program Files\On-premises data gateway.

1. Stel **ADUserNameLookupProperty** in op `msDS-cloudExtensionAttribute1` en **ADUserNameReplacementProperty** op `SAMAccountName`. Sla het configuratiebestand op.

1. Klik op het tabblad **Services** met de rechtermuisknop op de gateway-service en selecteer **Opnieuw opstarten**.

    ![Schermopname van het tabblad Taakbeheerservices](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Stel de eigenschap `msDS-cloudExtensionAttribute1` van de Active Directory-gebruiker in. Dit is de gebruiker die u aan een SAP BW-gebruiker hebt toegewezen. Stel de eigenschap in op de Power BI-servicegebruiker voor wie u eenmalige aanmelding van Kerberos wilt inschakelen. U kunt de eigenschap `msDS-cloudExtensionAttribute1` onder andere instellen door de module Active Directory-gebruikers en Computers MMC te gebruiken. (U kunt ook andere methoden gebruiken.)

    1. Meld u als beheerder aan bij een domeincontrollercomputer.

    1. Open de map **Gebruikers** in het modulevenster en dubbelklik op de Active Directory-gebruiker die u hebt toegewezen aan een SAP BW-gebruiker.

    1. Selecteer het tabblad **Kenmerkeditor**.

        Als u dit tabblad niet ziet, moet u zoeken naar instructies over het inschakelen ervan of een andere methode gebruiken om de eigenschap in te stellen. Selecteer een van de kenmerken en vervolgens de M-sleutel om naar de Active Directory-eigenschappen die met een M beginnen te navigeren. Zoek de eigenschap `msDS-cloudExtensionAttribute1` en dubbelklik hierop. Stel de waarde in op de gebruikersnaam die u gebruikt om u aan te melden bij de Power BI-service, als YourUser@YourDomain.

    1. Selecteer **OK**.

        ![Schermopname van het dialoogvenster Kenmerkeditor voor tekenreeksen](media/service-gateway-sso-kerberos/edit-attribute.png)

    1. Selecteer **Toepassen**. Controleer of de juiste waarde is ingesteld in de kolom **Waarde**.

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service"></a>Een nieuwe gegevensbron van de SAP BW-toepassingsserver toevoegen aan de Power BI-service

Voeg de SAP BW-gegevensbron toe aan uw gateway: volg de instructies eerder in dit artikel voor het [uitvoeren van een rapport](#run-a-power-bi-report).

1. Voer in het venster voor gegevensbronconfiguratie de **Hostnaam**, het **Systeemnummer** en de **client-id** van de toepassingsserver in zoals u zou doen om u vanuit Power BI Desktop aan te melden bij uw SAP BW-server.

1. Voer in het veld **Naam van SNC-partner** p: \<de SPN die u hebt toegewezen aan de SAP BW-servicegebruiker\> in. Als de SPN bijvoorbeeld SAP/BWServiceUser@MYDOMAIN.COM is, voert u p:SAP/BWServiceUser@MYDOMAIN.COM in het veld **Naam van SNC-partner** in.

1. Als SNC-bibliotheek selecteert u **SNC_LIB** of **SNC_LIB_64**. Gebruik **SNC_LIB** voor 32-bits scenario's en **SNC_LIB_64** voor 64-bits scenario's. Zorg ervoor dat deze omgevingsvariabelen verwijzen naar respectievelijk gsskrb5.dll of gx64krb5.dll, afhankelijk van uw hoeveelheid bits.

1. Als u **Windows** hebt geselecteerd als **Verificatiemethode**, moeten de **Gebruikersnaam** en het **Wachtwoord** de gebruikersnaam en het wachtwoord van een Active Directory Domain Services-gebruiker zijn die gemachtigd is om zich met eenmalige aanmelding bij de SAP BW-server aan te melden. Met andere woorden: deze gegevens moeten bij een Active Directory-gebruiker horen die via de SU01-transactie aan een SAP BW-gebruiker is toegewezen. Als u **Basic** hebt geselecteerd, moeten de **Gebruikersnaam** en het **Wachtwoord** respectievelijk worden ingesteld op een SAP BW-gebruikersnaam en -wachtwoord. Deze referenties worden alleen gebruikt als het vak **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery-query's** niet is ingeschakeld.

1. Selecteer het vak **Eenmalige aanmelding via Kerberos gebruiken voor DirectQuery-query's** en selecteer **Toepassen**. Als de testverbinding mislukt, controleert u of de vorige installatie- en configuratiestappen correct zijn voltooid.

    In de gateway worden altijd de ingetypte referenties gebruikt om een testverbinding met de server tot stand te brengen en om geplande vernieuwingen van importrapporten uit te voeren. Er wordt alleen geprobeerd om een SSO-verbinding tot stand te brengen als de optie **SSO gebruiken via Kerberos voor DirectQuery-query's** is geselecteerd, en als de gebruiker een DirectQuery-rapport of gegevensset wil openen.

### <a name="test-your-setup"></a>Uw configuratie testen

Publiceer een DirectQuery-rapport vanuit Power BI Desktop in de Power BI-service om uw configuratie te controleren. Zorg ervoor dat u bij de Power BI-service bent aangemeld als een Azure AD-gebruiker of als een gebruiker die u hebt toegewezen aan de eigenschap `msDS-cloudExtensionAttribute1` van een Azure AD-gebruiker. Als de installatie is voltooid, kunt u een rapport maken op basis van de gepubliceerde gegevensset in de Power BI-service. Ook kunt u gegevens ophalen via de visuals in het rapport.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Het oplossen van problemen met de gatewayconnectiviteit

1. Controleer de gatewaylogboeken. Open de toepassing Gatewayconfiguratie en selecteer **Diagnostische gegevens** > **Logboeken exporteren**. De recentste fouten bevinden zich onder in de logboekbestanden die u onderzoekt.

    ![Schermopname van de toepassing On-premises gegevensgateway, waarbij Diagnostische gegevens is gemarkeerd](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Schakel SAP BW-tracering in en controleer de gegenereerde logboekbestanden. Er zijn verschillende soorten SAP BW-tracering beschikbaar. Raadpleeg de SAP-documentatie voor meer informatie.

## <a name="errors-from-an-insufficient-kerberos-configuration"></a>Fouten als gevolg van een incorrecte Kerberos-configuratie

Als de onderliggende databaseserver en de gateway niet juist zijn geconfigureerd voor beperkte Kerberos-delegering, kan het volgende foutbericht over het niet kunnen laden van gegevens worden weergegeven:

![Schermopname van het foutbericht](media/service-gateway-sso-kerberos/load-data-error.png)

De technische gegevens die horen bij dit foutbericht (DM_GWPipeline_Gateway_ServerUnreachable), kunnen er als volgt uitzien:

![Schermopname van de technische details van het foutbericht](media/service-gateway-sso-kerberos/server-unreachable.png)

Het gevolg is dat de gateway de oorspronkelijke gebruiker niet goed kan imiteren en de poging om verbinding te maken met de database mislukt.

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende bronnen voor meer informatie over de **on-premises gegevensgateway** en **DirectQuery**:

* [Wat is een on-premises gegevensgateway?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Gegevensbronnen die worden ondersteund door DirectQuery)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
