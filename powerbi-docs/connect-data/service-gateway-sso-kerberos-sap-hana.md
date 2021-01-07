---
title: Kerberos gebruiken voor eenmalige aanmelding (SSO) bij SAP HANA
description: SAP BW-server configureren voor SSO vanuit Power BI-service
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675115"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Kerberos gebruiken voor eenmalige aanmelding (SSO) bij SAP HANA

> [!IMPORTANT]
> Aangezien [SAP geen ondersteuning meer biedt voor de OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html), biedt Microsoft hier ook geen ondersteuning meer voor. Bestaande verbindingen blijven werken, maar vanaf februari 2021 kunt u geen nieuwe verbindingen meer maken. Gebruik vanaf deze datum in plaats hiervan CommonCryptoLib.

In dit artikel wordt beschreven hoe u uw SAP HANA-gegevensbron configureert voor het gebruik van SSO vanuit de Power BI-service.

> [!NOTE]
> Volg de stappen in dit artikel en in [Kerberos SSO configureren](service-gateway-sso-kerberos.md) voordat u probeert een op SAP HANA gebaseerd rapport dat gebruikmaakt van Kerberos SSO te vernieuwen.

## <a name="enable-sso-for-sap-hana"></a>SSO inschakelen voor SAP HANA

Volg deze stappen om SSO in te schakelen voor SAP HANA:

1. Zorg ervoor dat de SAP HANA-server de vereiste minimumversie uitvoert die afhankelijk is van het platform-niveau van uw SAP HANA-server:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. Installeer op de gatewaycomputer het meest recente SAP HANA ODBC-stuurprogramma. De minimaal vereiste versie is HANA ODBC versie 2.00.020.00, vrijgegeven in augustus 2017.

3. Zorg ervoor dat de SAP HANA-server is geconfigureerd voor SSO op basis van Kerberos. Zie [Eenmalige aanmelding met behulp van Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) in de SAP HANA-beveiligingshandleiding voor meer informatie over het instellen van eenmalige aanmelding voor SAP HANA met behulp van Kerberos. Zie ook de koppelingen vanaf die pagina, met name SAP Note 1837331: HOWTO HANA DBSSO Kerberos/Active Directory.

We adviseren ook om de volgende aanvullende stappen te volgen om de prestaties nog iets verder te verbeteren:

1. Zoek en open dit configuratiebestand in de installatiemap van de gateway: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Zoek de eigenschap `FullDomainResolutionEnabled` en wijzig de waarde ervan in `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Voer nu [een Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report) uit.

## <a name="next-steps"></a>Volgende stappen

Raadpleeg de volgende bronnen voor meer informatie over de on-premises gegevensgateway en DirectQuery:

* [Wat is een on-premises gegevensgateway?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery in Power BI](desktop-directquery-about.md)
* [Data sources supported by DirectQuery](power-bi-data-sources.md) (Gegevensbronnen die worden ondersteund door DirectQuery)
* [DirectQuery en SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery en SAP HANA](desktop-directquery-sap-hana.md)
