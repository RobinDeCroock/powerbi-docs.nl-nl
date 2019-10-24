---
title: Eenmalige aanmelding (SSO) gebruiken bij on-premises gegevensbronnen
description: Configureer uw gateway om eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI mogelijk te maken.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b1379bb783b090362215eaf7c317bbea435d1eec
ms.sourcegitcommit: e533c65607bbba0f620fddabd6b107e5933772c1
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72259933"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Overzicht van eenmalige aanmelding (SSO) voor gateways in Power BI

Als u uw on-premises gegevensgateway configureert met beperkte delegering van Kerberos of met Security Assertion Markup Language (SAML), kunt u connectiviteit met naadloze eenmalige aanmelding bewerkstelligen, zodat Power BI-rapporten en -dashboards in realtime kunnen worden bijgewerkt met on-premises gegevens. De on-premises gegevensgateway ondersteunt SSO met behulp van DirectQuery, waarmee de gateway verbinding maakt met on-premises gegevensbronnen.

Momenteel worden de volgende gegevensbronnen ondersteund:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) en [SAML](service-gateway-sso-saml.md))
* SAP BW-toepassingsserver ([Kerberos](service-gateway-sso-kerberos.md))
* SAP BW-berichtenserver ([Kerberos](service-gateway-sso-kerberos.md)) - openbare preview
* Oracle ([Kerberos](service-gateway-sso-kerberos.md)) - openbare preview
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Apache Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

We ondersteunen momenteel geen SSO voor [M-extensies](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Wanneer een gebruiker in de Power BI-service een DirectQuery-rapport gebruikt, kan elke cross-filter, segmentering, sortering en bewerking van het rapport ertoe leiden dat er live query's worden uitgevoerd naar de onderliggende on-premises gegevensbron. Wanneer SSO voor de gegevensbron,is geconfigureerd, worden query's uitgevoerd onder de identiteit van de gebruiker die Power BI gebruikt (via de webervaring of de mobiele Power BI-apps). Iedere gebruiker ziet dus exact die gegevens waar hij of zij op de onderliggende gegevensbron voor is gemachtigd. Wanneer eenmalige aanmelding is ingesteld, vindt er geen gedeelde gegevenscaching plaats tussen verschillende gebruikers.

## <a name="query-steps-when-running-sso"></a>Querystappen bij het uitvoeren van SSO

Een query die wordt uitgevoerd met eenmalige aanmelding bestaat uit drie stappen, zoals weergegeven in het volgende diagram.

![Querystappen voor SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Hier vindt u aanvullende informatie over deze stappen:

1. Voor elke query bevat de **Power BI-service** de *user principal name* (UPN, d.w.z. de volledig gekwalificeerde gebruikersnaam van de gebruiker die momenteel is aangemeld bij Power BI-service) bij het verzenden van een queryaanvraag naar de geconfigureerde gateway.

2. De gateway moet de UPN van Azure Active Directory toewijzen aan een lokale Active Directory-identiteit.

   a.  Als Azure AD DirSync (ook wel bekend als *Azure AD Connect*) is geconfigureerd, wordt de toewijzing automatisch verzorgd in de gateway.

   b.  Anders kan de gateway de Azure AD UPN opzoeken en toewijzen aan een lokale AD-gebruiker door een zoekopdracht uit te voeren op basis van het lokale Active Directory-domein.

3. Het gatewayserviceproces imiteert de toegewezen lokale gebruiker, opent de verbinding met de onderliggende database en verzendt de query. De gateway hoeft niet te zijn geïnstalleerd op dezelfde computer als de gegevensbron.

## <a name="next-steps"></a>Volgende stappen

U weet nu wat de basisbeginselen zijn van SSO via de gateway. Lees de volgende artikelen voor meer informatie over Kerberos en SAML:

* [Eenmalige aanmelding (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [Eenmalige aanmelding (SSO) - SAML](service-gateway-sso-saml.md)
