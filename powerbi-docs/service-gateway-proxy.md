---
title: Proxy-instellingen configureren voor de on-premises gegevensgateway
description: Informatie over de configuratie van de proxy-instellingen voor de on-premises gegevensgateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2122ce9bd6eb850a51a06188ca1c10faf78f4bb1
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964658"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Proxy-instellingen configureren voor de on-premises gegevensgateway
Het is mogelijk dat u in uw werkomgeving alleen toegang tot internet hebt via een proxy. Hierdoor is het mogelijk dat de on-premises gegevensgateway geen verbinding kan maken met de service.

## <a name="does-your-network-use-a-proxy"></a>Maakt uw netwerk gebruik van een proxy?
In het volgende bericht op superuser.com wordt beschreven hoe u kunt bepalen of er een proxy in uw netwerk wordt gebruikt.

[Hoe weet ik welke proxyserver die ik gebruik? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Locatie van het configuratiebestand en de standaardconfiguratie
De proxygegevens worden geconfigureerd in een .NET-configuratiebestand. De locatie en bestandsnamen kunnen afwijken. Dit is afhankelijk van de gateway die u gebruikt.

### <a name="on-premises-data-gateway"></a>On-premises gegevensgateway
Er zijn twee belangrijke configuratiebestanden betrokken bij de on-premises gegevensgateway.

**Configuratie**

De eerste is voor de configuratieschermen waarmee de gateway daadwerkelijk wordt geconfigureerd. Als u problemen ondervindt met het configureren van de gateway, is dit het bestand dat u moet controleren.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Windows-service**

Het tweede bestand is voor de Windows-service die communiceert met de Power BI-service en de aanvragen verwerkt.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Proxyinstellingen configureren
De standaardproxyconfiguratie is als volgt.

```
<system.net>
    <defaultProxy useDefaultCredentials="true" />
</system.net>
```


De standaardconfiguratie werkt met Windows-verificatie. Als uw proxy een andere vorm van verificatie gebruikt, moet u de instellingen wijzigen. Als u niet zeker weet welke vorm van verificatie wordt gebruikt, neemt u contact op met uw netwerkbeheerder. Basisproxyverificatie wordt niet aangeraden. Wanneer u probeert basisproxyverificatie te gebruiken, kan dit leiden tot proxyverificatiefouten waardoor de gateway niet goed wordt geconfigureerd. Gebruik een sterkere proxyverificatiemethode voor omzetten.

Naast het gebruik van standaardreferenties kunt u een <proxy>-element toevoegen om de proxyserverinstellingen uitgebreider te definiëren. U kunt bijvoorbeeld opgeven dat uw on-premises gegevensgateway altijd de proxy moet gebruiken, zelfs voor lokale resources, door de parameter bypassonlocal in te stellen op Onwaar. Dit is nuttig voor het oplossen van problemen als u alle https-aanvragen die afkomstig zijn van een on-premises gegevensgateway in de logboekbestanden van de proxy. De volgende voorbeeldconfiguratie geeft aan dat alle aanvragen via een specifieke proxy met IP-adres 192.168.1.10 moeten lopen.

```
<system.net>
    <defaultProxy useDefaultCredentials="true">
        <proxy  
            autoDetect="false"  
            proxyaddress="http://192.168.1.10:3128"  
            bypassonlocal="false"  
            usesystemdefault="true"
        />  
    </defaultProxy>
</system.net>
```

Bovendien moet u het volgende bestand bijwerken als u de gateway via een proxy wilt verbinden met cloudgegevensbronnen: *C:\Program Files\On-premises data gateway\Microsoft.Mashup.Container.NetFX45.exe*. In het bestand voegt u de onderstaande inhoud toe in de sectie `<configurations>` en vult u uw proxygegevens in bij het kenmerk `proxyaddress`. In het volgende voorbeeld worden alle cloudaanvragen doorgestuurd via een specifieke proxy met IP-adres 192.168.1.10.

```
<configuration>
<system.net>
    <defaultProxy useDefaultCredentials="true" enabled="true">
    <proxy proxyaddress=""http://192.168.1.10:3128" bypassonlocal="true" />
    </defaultProxy>
</system.net>
</configuration>
```

Zie [Het element defaultProxy (Netwerkinstellingen)](https://msdn.microsoft.com/library/kd3cf2ex.aspx) voor meer informatie over de configuratie van de proxyelementen voor .NET-configuratiebestanden.

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>De gatewayserviceaccount wijzigen in een domeingebruiker
Wanneer de proxyinstellingen worden geconfigureerd voor het gebruik van standaardreferenties, zoals hierboven is uitgelegd, ondervindt u mogelijk verificatieproblemen met uw proxy. Dit komt omdat het standaardserviceaccount de service-SID is geen geverifieerde domeingebruiker. U kunt het serviceaccount van de gateway wijzigen om de juiste verificatie met uw proxy toe te staan.

> [!NOTE]
> U kunt het beste een beheerd serviceaccount gebruiken om te voorkomen dat wachtwoorden opnieuw moeten worden ingesteld. Meer informatie over hoe u een [beheerd serviceaccount](https://technet.microsoft.com/library/dd548356.aspx) maakt in Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Het serviceaccount van de on-premises gegevensgateway wijzigen
1. Wijzig het Windows-serviceaccount voor de **on-premises gegevensgatewayservice**.

    Het standaardaccount voor deze service is *NT SERVICE\PBIEgwService*. U kunt dit het beste wijzigen in een domeingebruikersaccount in uw Active Directory-domein. U kunt ook een beheerd serviceaccount gebruiken om te voorkomen dat het wachtwoord opnieuw moet worden ingesteld.

    U kunt het account wijzigen op het tabblad **Aanmelden** in de eigenschappen van de Windows-service.
2. Start de **on-premises gegevensgatewayservice** opnieuw.

    Open een opdrachtprompt met verhoogde bevoegdheid en voer de volgende opdrachten uit:

        net stop PBIEgwService

        net start PBIEgwService
3. Start de **configurator voor de on-premises gegevensgateway**. U kunt de startknop van Windows selecteren en zoeken op *On-premises gegevensgateway*.
4. Meld u aan bij Power BI.
5. Gebruik de herstelsleutel om de gateway te herstellen.

    Zodoende stelt u het nieuwe serviceaccount in staat op de opgeslagen referenties voor gegevensbronnen te ontsleutelen.

> [!NOTE]
> Wanneer u het serviceaccount rechtstreeks wijzigt met het bedieningspaneel Services, worden ACL's niet automatisch ook bijgewerkt. U moet ervoor zorgen dat het nieuwe serviceaccount toegang heeft tot de installatiebestanden en -map. U vindt de gatewayinstallatiemap onder C:\Program Files\On-premises data gateway. 
> 

## <a name="next-steps"></a>Volgende stappen
[On-premises gegevensgateway (personal mode)](service-gateway-personal-mode.md)
[Firewallinformatie](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Nog vragen? [Misschien dat de Power BI-community het antwoord weet](http://community.powerbi.com/)

