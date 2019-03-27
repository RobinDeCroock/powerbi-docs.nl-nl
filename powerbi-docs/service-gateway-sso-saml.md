---
title: SAML voor SSO (eenmalige aanmelding) gebruiken bij on-premises gegevensbronnen
description: Configureer uw gateway Security Assertion Markup Language (SAML) om eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI mogelijk te maken.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 91a4cf3ff4fef4530c7c45712a86419298da53f4
ms.sourcegitcommit: 89e9875e87b8114abecff6ae6cdc0146df40c82a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306499"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Security Assertion Markup Language (SAML) gebruiken om eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI mogelijk te maken

Gebruik [Security Assertion Markup Language (SAML)](https://www.onelogin.com/pages/saml) om naadloze connectiviteit dankzij eenmalige aanmelding mogelijk te maken. Met inschakeling van SSO is het eenvoudiger om gegevens van on-premises gegevensbronnen te vernieuwen in Power BI-rapporten en -dashboards.

## <a name="supported-data-sources"></a>Ondersteunde gegevensbronnen

Momenteel wordt SAP HANA met SAML ondersteund. Zie het onderwerp [SAML SSO voor BI-Platform voor HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) in de documentatie van SAP HANA voor meer informatie over het instellen en configureren van eenmalige aanmelding voor SAP HANA met behulp van SAML.

Er worden extra gegevensbronnen ondersteund met [Kerberos](service-gateway-sso-kerberos.md).

Houd er rekening mee dat voor HANA **ten zeerste** wordt aanbevolen om versleuteling in te schakelen voordat u een SAML SSO-verbinding tot stand brengt (met andere woorden: u moet de HANA-server zo configureren dat deze versleutelde verbindingen accepteert en de Gateway zo configureren dat deze versleuteling gebruikt tijdens de communicatie met uw HANA-server). Het HANA ODBC-stuurprogramma is standaard **niet** in staat SAML-asserties te versleutelen. Als geen versleuteling is ingeschakeld, wordt de ondertekende SAML-assertie onversleuteld verzonden van de Gateway naar de HANA-server en is deze kwetsbaar voor onderschepping en hergebruik door derde partijen.

## <a name="configuring-the-gateway-and-data-source"></a>De gateway en de gegevensbron configureren

Als u SAML wilt gebruiken, moet u een vertrouwensrelatie opzetten tussen de HANA-server(s) waarvoor u SSO wilt inschakelen en de Gateway, die in dit scenario als de SAML-identiteitsprovider (IdP) fungeert. Er zijn verschillende manieren om deze relatie tot stand te brengen, zoals het importeren van het X509-certificaat van de Gateway IdP in het vertrouwensarchief van de HANA-server(s), of het ondertekenen van het X509-certificaat van de Gateway door een basis-CA (Certificeringsinstantie) die wordt vertrouwd door de HANA-server(s). In deze handleiding beschrijven we de tweede benadering. Als u dit handiger vindt, kunt u ook een andere methode hanteren.

Houd er tevens rekening mee dat, waar deze handleiding OpenSSL gebruikt als cryptografieprovider voor de HANA-server, het ook mogelijk is om de cryptografische SAP-bibliotheek (ook wel bekend als CommonCryptoLib of sapcrypto) te gebruiken in plaats van OpenSSL om de installatiestappen uit te voeren waarmee de vertrouwensrelatie wordt bevestigd. Raadpleeg de officiële documentatie van SAP voor meer informatie.

In de volgende stappen wordt beschreven hoe u een vertrouwensrelatie tussen een HANA-server en de Gateway IdP tot stand brengt door het X509-certificaat van de Gateway te ondertekenen met een basis-CA die wordt vertrouwd door de HANA-server.

1. Maak het X509-certificaat van de basis-CA en de persoonlijke sleutel. Als u bijvoorbeeld het X509-certificaat van de basis-CA en de persoonlijke sleutel in PEM-indeling wilt maken, gaat u als volgt te werk:

```
openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
```

Voeg het certificaat (bijvoorbeeld CA_Cert.pem) toe aan de vertrouwde gegevensopslag van de HANA-server, zodat de HANA-server alle certificaten vertrouwt die zijn ondertekend door de basis-CA die u zojuist hebt gemaakt. U vindt de locatie van de vertrouwde gegevensopslag van uw HANA-server door de configuratie-instelling **ssltruststore** te bestuderen. Als u de SAP-documentatie over het configureren van OpenSSL hebt gevolgd, is er mogelijk al een basis-CA die door uw HANA-server wordt vertrouwd en die u kunt hergebruiken. Zie [How to Configure Open SSL for SAP HANA Studio to SAP HANA Server](https://archive.sap.com/documents/docs/DOC-39571) (Open SSL configureren voor SAP HANA Studio naar SAP HANA-server) voor meer informatie. Als u op meerdere HANA-servers SAML SSO wilt inschakelen, moet u ervoor zorgen dat elk van de servers deze basis-CA vertrouwt.

1. Maak het X509-certificaat voor de Gateway IdP. Als u bijvoorbeeld een aanvraag voor certificaatondertekening (IdP_Req.pem) en een persoonlijke sleutel (IdP_Key.pem) wilt maken die een jaar geldig zijn, voert u de volgende opdracht uit:

```
 openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
```


Onderteken de aanvraag voor certificaatondertekening met de basis-CA die u hebt geconfigureerd en die uw HANA server(s) vertrouwen. Als u bijvoorbeeld IdP_Req.pem wilt ondertekenen met CA_Cert.pem en CA_Key.pem (het certificaat en de sleutel van de basis-CA), voert u de volgende opdracht uit:

  ```
openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
```
Het resulterende IdP-certificaat is een jaar geldig (zie de -dagen optie). Importeert nu het certificaat van uw IdP in HANA Studio om een nieuwe SAML-identiteitsprovider te maken.

1. In SAP HANA Studio klikt u met de rechtermuisknop op uw SAP HANA-server en navigeert u vervolgens naar **Beveiliging** > **Beveiligingsconsole openen** > **SAML-identiteitsprovider** > **OpenSSL Cryptographic Library**.

    ![Id-providers](media/service-gateway-sso-saml/identity-providers.png)

1. Selecteer **Importeren**, navigeer naar IdP_Cert.pem en importeer dit bestand.

1. Selecteer in SAP HANA Studio de map **Beveiliging**.

    ![De map Beveiliging](media/service-gateway-sso-saml/security-folder.png)

1. Vouw **Gebruikers** uit en selecteer vervolgens de gebruiker die u wilt toewijzen aan uw Power BI-gebruiker.

1. Selecteer **SAML** en vervolgens **Configureren**.

    ![SAML configureren](media/service-gateway-sso-saml/configure-saml.png)

1. Selecteer de id-provider die u in stap 2 hebt gemaakt. Voer bij **Externe id** de UPN van de Power BI-gebruiker in en selecteer **Toevoegen**.

    ![Id-provider selecteren](media/service-gateway-sso-saml/select-identity-provider.png)

Nu u het certificaat en de identiteit hebt geconfigureerd, kunt u het certificaat converteren naar pfx-indeling en het gateway-apparaat configureren voor gebruik van het certificaat.

1. Converteer het certificaat naar pfx-indeling door de volgende opdracht uit te voeren. Houd er rekening mee dat met deze opdracht 'root' wordt ingesteld als wachtwoord voor het pfx-bestand.

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. Kopieer het pfx-bestand naar het gatewayapparaat:

    1. Dubbelklik op samltest.pfx en selecteer vervolgens **Lokale machine** > **Volgende**.

    1. Voer het wachtwoord in en selecteer vervolgens **Volgende**.

    1. Selecteer **Alle certificaten in het onderstaande archief opslaan** en selecteer vervolgens **Bladeren** > **Persoonlijk** > **OK**.

    1. Selecteer **Volgende** en vervolgens **Voltooien**.

    ![Certificaat importeren](media/service-gateway-sso-saml/import-certificate.png)

1. Geef het gatewayserviceaccount toegang tot de persoonlijke sleutel van het certificaat:

    1. Voer op de gatewaycomputer de Microsoft Management Console (MMC) uit.

        ![MMC uitvoeren](media/service-gateway-sso-saml/run-mmc.png)

    1. Selecteer onder **Bestand** de optie **Module toevoegen/verwijderen**.

        ![Module toevoegen](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selecteer **Certificaten** > **Toevoegen** en vervolgens **Computeraccount** > **Volgende**.

    1. Selecteer **Lokale computer** > **Voltooien** > **OK**.

    1. Vouw **Certificaten** > **Persoonlijk** > **Certificaten** uit en zoek het certificaat.

    1. Klik met de rechtermuisknop op het certificaat en navigeer naar **Alle taken** > **Persoonlijke sleutels beheren**.

        ![Persoonlijke sleutels beheren](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Voeg het gatewayserviceaccount toe aan de lijst. Het account is standaard **NT SERVICE\PBIEgwService.** U ontdekt in welk account de gatewayservice wordt uitgevoerd door **services.msc** uit te voeren en te zoeken naar **On-premises data gateway service**.

        ![Gatewayservice](media/service-gateway-sso-saml/gateway-service.png)

Ga ten slotte als volgt te werk om de vingerafdruk van het certificaat toe te voegen aan de gatewayconfiguratie.

1. Voer de volgende PowerShell-opdracht uit om de certificaten op uw computer weer te geven.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Kopieer de vingerafdruk voor het certificaat dat u hebt gemaakt.

1. Ga naar de map van de gateway. Standaard is dat C:\Program Files\On-premises data gateway.

1. Open PowerBI.DataMovement.Pipeline.GatewayCore.dll.config en zoek de sectie \*SapHanaSAMLCertThumbprint\*. Plak de vingerafdruk die u hebt gekopieerd.

1. Start de gatewayservice opnieuw op.

## <a name="running-a-power-bi-report"></a>Een Power BI-rapport uitvoeren

Nu kunt u de pagina **Gateway beheren** in Power BI gebruiken om de gegevensbron te configureren en onder **Geavanceerde instellingen** SSO in te schakelen. Vervolgens kunt u rapporten en gegevenssets publiceren die een binding met die gegevensbron hebben.

![Geavanceerde instellingen](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Problemen oplossen

Na het configureren van SSO, ziet u mogelijk de volgende fout in de Power BI-portal: "De opgegeven referenties kunnen niet worden gebruikt voor de bron SapHana." Deze fout geeft aan dat de referentie SAML is geweigerd door SAP HANA.

Verificatietraceringen bieden gedetailleerde informatie voor het oplossen van problemen met referenties op SAP HANA. Volg deze stappen om tracering voor uw SAP HANA-server te configureren.

1. Schakel de verificatietracering in op de SAP HANA-server door de volgende query uit te voeren.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduceer het probleem dat u heeft gehad.

1. Open de beheerconsole in HANA Studio en ga naar het tabblad **Diagnosis Files**.

1. Open de meest recente indexservertracering en zoek naar SAMLAuthenticator.cpp.

    U zou een gedetailleerd foutbericht moeten vinden dat de hoofdoorzaak aangeeft, zoals het volgende voorbeeld.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Schakel de verificatietracering uit zodra het oplossen van problemen is voltooid door de volgende query uit te voeren.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende bronnen voor meer informatie over de **on-premises gegevensgateway** en **DirectQuery**:

* [On-premises data gateway](service-gateway-onprem.md) (On-premises gegevensgateway)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](desktop-directquery-data-sources.md) (Gegevensbronnen die worden ondersteund door DirectQuery)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
