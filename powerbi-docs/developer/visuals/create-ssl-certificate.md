---
title: SSL-certificaat maken
description: Instructies voor een tijdelijke oplossing voor het handmatig maken van certificaten voor Development Server
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425431"
---
# <a name="creating-ssl-certificate"></a>SSL-certificaat maken

Voer de volgende opdracht uit om het certificaat te genereren met behulp van de cmdlet New-SelfSignedCertificate van Power shell in Windows 8 of hoger.

Het hulpprogramma vereist installatie van OpenSSL voor **Windows** **7**. Het hulpprogramma `openssll` moet beschikbaar zijn vanaf de opdrachtregel.

Ga voor installatie van OpenSSL naar [https://www.openssl.org](https://www.openssl.org) of [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>Certificaat maken (Mac OS X)

OpenSSL-hulpprogramma's zijn gewoonlijk beschikbaar in Linux- of Mac OS X-systemen.

Anders kunt u ze installeren via

*Brew*-pakketbeheer

```cmd
brew install openssl
brew link openssl --force
```

of met behulp van *MacPorts*

```cmd
sudo port install openssl
```

Voer na installatie van OpenSSL de volgende aanroep uit om een nieuw certificaat te genereren:

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>Certificaat maken (Linux)

Als OpenSSL-hulpprogramma's niet beschikbaar zijn in uw Linux-besturingssysteem, kunt u ze installeren met behulp van de volgende opdrachten.

Voor *APT*-pakketbeheer:

```cmd
sudo apt-get install openssl
```

Voor *Yellowdog Updater*:

```cmd
yum install openssl
```

Voor *Redhat-pakketbeheer*:

```cmd
rpm install openssl
```

Als OpenSSl al beschikbaar is in uw besturingssysteem, roept u

```cmd
pbiviz --create-cert
```

aan om een nieuw certificaat te maken.

Haal het anders op van [https://www.openssl.org](https://www.openssl.org) of [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)

## <a name="generate-certificate-manually"></a>Certificaat handmatig genereren

U kunt certificaten opgeven die door elk hulpprogramma worden gegenereerd.

Als OpenSSL op uw systeem is geïnstalleerd, kunt u de volgende opdracht uitvoeren om een nieuw certificaat te genereren

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

De webservercertificaten van PowerBI-visuals-tools bevinden zich gewoonlijk in

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

voor de algemene instantie van de hulpprogramma's

of

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

voor de lokale instantie van de hulpprogramma's.

Sla het certificaatbestand op als `PowerBICustomVisualTest_public.cer` en PrivateKey als `PowerBICustomVisualTest_public.key` u de PEM-indeling gebruikt.
Sla het certificaatbestand op als `PowerBICustomVisualTest_public.pfx` als u de PFX-indeling gebruikt.

Als uw PFX-certificaatbestand een wachtwoordzin vereist, moet u deze opgeven in

```cmd
\PowerBI-visuals-tools\config.json
```

in de sectie 'server':

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
