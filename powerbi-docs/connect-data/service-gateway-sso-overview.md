---
title: Overzicht van eenmalige aanmelding (SSO) voor gateways in Power BI
description: Configureer uw gateway om eenmalige aanmelding (SSO) bij on-premises gegevensbronnen vanuit Power BI mogelijk te maken.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4a4bb6ccb74ce08ea1ff63f44b1c2c5406c527ad
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231306"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Overzicht van eenmalige aanmelding (SSO) voor gateways in Power BI

Door uw on-premises gegevensgateway te configureren, maakt u connectiviteit met naadloze eenmalige aanmelding mogelijk, zodat Power BI rapporten en dashboards kan bijwerken vanuit uw on-premises gegevens. U hebt de mogelijkheid om uw gateway te configureren met een beperkte [Kerberos](service-gateway-sso-kerberos.md)-delegering of Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)). De on-premises gegevensgateway ondersteunt SSO met behulp van [DirectQuery](desktop-directquery-about.md) of voor Vernieuwen, waarbij verbinding wordt gemaakt met on-premises gegevensbronnen. 

Power BI biedt ondersteuning voor de volgende gegevensbronnen:

* SQL Server (Kerberos)
* SAP HANA (Kerberos en SAML)
* SAP BW-toepassingsserver (Kerberos)
* SAP BW Message Server (Kerberos) 
* Oracle (Kerberos) 
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

We ondersteunen momenteel geen SSO voor [M-extensies](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

Wanneer een gebruiker in de Power BI-service een DirectQuery-rapport gebruikt, kan elke cross-filter, segmentering, sortering en bewerking van het rapport ertoe leiden dat query's live worden uitgevoerd naar de onderliggende on-premises gegevensbron. Als u SSO voor de gegevensbron configureert, worden query's uitgevoerd onder de identiteit van de gebruiker die Power BI gebruikt (via de webervaring of de mobiele Power BI-apps). Daarom ziet elke gebruiker exact die gegevens waarvoor hij machtigingen heeft in de onderliggende gegevensbron. 

U kunt ook een rapport dat is ingesteld op vernieuwen in de Power BI-service configureren voor het gebruik van eenmalige aanmelding. Wanneer u eenmalige aanmelding voor deze gegevensbron configureert, worden query's uitgevoerd onder de identiteit van de gegevensseteigenaar in Power BI. Daarom gebeurt het vernieuwen op basis van de machtigingen van de gegevensseteigenaar voor de onderliggende gegevensbron. Vernieuwen met eenmalige aanmelding is momenteel alleen ingeschakeld voor gegevensbronnen met behulp van beperkte [Kerberos](service-gateway-sso-kerberos.md)-delegering 

## <a name="query-steps-when-running-sso"></a>Querystappen bij het uitvoeren van SSO

Een query die wordt uitgevoerd met eenmalige aanmelding bestaat uit drie stappen, zoals weergegeven in het volgende diagram.

![Querystappen voor SSO](media/service-gateway-sso-overview/sso-query-steps.png)

Hier vindt u aanvullende informatie over deze stappen:

1. De Power BI-service bevat voor elke query de *user principal name (UPN)* , d.w.z. de volledig gekwalificeerde gebruikersnaam van de gebruiker die momenteel is aangemeld bij Power BI-service, als een queryaanvraag naar de geconfigureerde gateway wordt verzonden.

2. De gateway moet de UPN van Azure Active Directory toewijzen aan een lokale Active Directory-identiteit:

   a. Als Azure AD DirSync (ook wel bekend als *Azure AD Connect*) is geconfigureerd, wordt de toewijzing automatisch verzorgd in de gateway.

   b.  Anders kan de gateway de Azure AD UPN opzoeken en toewijzen aan een lokale AD-gebruiker door een zoekopdracht uit te voeren op basis van het lokale Active Directory-domein.

3. Het gatewayserviceproces imiteert de toegewezen lokale gebruiker, opent de verbinding met de onderliggende database en verzendt daarna de query. U hoeft de gateway niet te installeren op dezelfde computer als de gegevensbron.

## <a name="next-steps"></a>Volgende stappen

U kent nu de basisbeginselen voor het inschakelen van SSO via de gateway. Lees de volgende artikelen voor meer informatie over Kerberos en SAML:

* [Eenmalige aanmelding (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [Eenmalige aanmelding (SSO) - SAML](service-gateway-sso-saml.md)
