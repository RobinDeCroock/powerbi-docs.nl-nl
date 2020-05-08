---
title: Een SSL-certificaat maken
description: Instructies voor een tijdelijke oplossing voor het handmatig maken van certificaten voor Development Server
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: fab40863d7beae4892a56975aa5e92c4fe5486ac
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380267"
---
# <a name="create-an-ssl-certificate"></a>Een SSL-certificaat maken

In dit artikel wordt beschreven hoe u een SSL-certificaat maakt.

Voer de volgende opdracht uit om het certificaat te genereren met behulp van de `New-SelfSignedCertificate`-cmdlet van Power shell in Windows 8 of hoger:

```cmd
pbiviz --install-cert
```

Voor het hulpprogramma is de installatie van OpenSSL voor Windows 7 vereist. Het OpenSSL-hulpprogramma moet beschikbaar zijn vanaf de opdrachtregel.

Als u OpenSSL wilt installeren, gaat u naar de website [OpenSSL](https://www.openssl.org) of [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

## <a name="create-a-certificate-mac-os-x"></a>Een certificaat maken (Mac OS X)

Normaal gesproken is het OpenSSL-hulpprogramma beschikbaar in het Linux- of Mac OS X-besturingssysteem.

U kunt het hulpprogramma ook installeren door een van de volgende opdrachten uit te voeren:

* Vanuit het *Brew*-pakketbeheer:

    ```cmd
    brew install openssl
    brew link openssl --force
    ```

* Met behulp van *MacPorts*:

    ```cmd
    sudo port install openssl
    ```

Nadat u het OpenSSL-hulpprogramma hebt geïnstalleerd voor het genereren van een nieuw certificaat, voert u de volgende opdracht uit:

```cmd
pbiviz --install-cert
```

## <a name="create-a-certificate-linux"></a>Een certificaat maken (Linux)

Als het OpenSSL-hulpprogramma niet beschikbaar is in uw Linux-besturingssysteem, kunt u het installeren met behulp een van de volgende opdrachten:

* Voor *APT*-pakketbeheer:

    ```cmd
    sudo apt-get install openssl
    ```

* Voor *Yellowdog Updater*:

    ```cmd
    yum install openssl
    ```

* Voor *Redhat-pakketbeheer*:

    ```cmd
    rpm install openssl
    ```

Als het OpenSSL-hulpprogramma al beschikbaar is in uw besturingssysteem, genereert u een nieuw certificaat door de volgende opdracht uit te voeren:

```cmd
pbiviz --install-cert
```

U kunt het OpenSSL-hulpprogramma ook ophalen door naar de website van [OpenSSL](https://www.openssl.org) of [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries) te gaan.

## <a name="generate-the-certificate-manually"></a>Het certificaat handmatig genereren

U kunt opgeven dat uw certificaten door elk hulpprogramma worden gegenereerd.

Als het OpenSSL-hulpprogramma al is geïnstalleerd op uw systeem, genereert u een nieuw certificaat door de volgende opdrachten uit te voeren:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

U vindt de webservercertificaten van de hulpprogramma's voor Power BI-visuals normaal gesproken door een van de volgende opdrachten uit te voeren:

* Voor het algemene exemplaar van de hulpprogramma's:

    ```cmd
    %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
    ```

* Voor het lokale exemplaar van de hulpprogramma's:

    ```cmd
    <custom visual project root>\node_modules\PowerBI-visuals-tools\certs
    ```

Als u de PEM-indeling gebruikt, slaat u het certificaatbestand op als *PowerBICustomVisualTest_public.crt* en slaat u privateKey op als *PowerBICustomVisualTest_public.key*.

Als u de PFX-indeling gebruikt, slaat u het certificaatbestand op als *PowerBICustomVisualTest_public.pfx*.

Als voor uw PFX-certificaatbestand een wachtwoordzin is vereist, gaat u als volgt te werk:
1. Geef in het configuratiebestand het volgende op:

    ```cmd
    \PowerBI-visuals-tools\config.json
    ```

1. Geef in de sectie `server` de wachtwoordzin op door de tijdelijke aanduiding *UW WACHTWOORDZIN* te vervangen:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBICustomVisualTest_private.key",
        "certificate":"certs/PowerBICustomVisualTest_public.crt",
        "pfx":"certs/PowerBICustomVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"YOUR PASSPHRASE"
    }
    ```