---
title: SSL-certificaten maken voor Power BI-visuals in ingesloten analyses in Power BI voor betere ingesloten BI-inzichten
description: Meer informatie over het genereren van SSL-certificaten met behulp van Power BI Visual Tools in Windows, Mac of Linux of handmatig. Maak betere geïntegreerde BI-inzichten mogelijk met geïntegreerde analytische gegevens voor Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 7897d25f3ac49c0f1b728f2aaf05b8612de67055
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885517"
---
# <a name="create-an-ssl-certificate"></a>Een SSL-certificaat maken

In dit artikel wordt beschreven hoe u SSL-certificaten (Secure Sockets Layer) voor Power BI-visuals genereert en installeert.

Voor de procedures in Windows, macOS X en Linux moet u het Power BI Visual Tools-pakket **pbiviz** geïnstalleerd hebben. Zie [Uw omgeving instellen voor het ontwikkelen van een Power BI-visual](./environment-setup.md) voor meer informatie. 

## <a name="create-a-certificate-on-windows"></a>Een certificaat maken in Windows

Voer de volgende opdracht uit om een certificaat te genereren met behulp van de PowerShell-cmdlet `New-SelfSignedCertificate` in Windows 8 of hoger:

```powershell
pbiviz --install-cert
```

In Windows 7 moet het hulpprogramma OpenSSL beschikbaar zijn vanaf de opdrachtregel in `pbiviz`. Als u OpenSSL wilt installeren, gaat u naar [OpenSSL](https://www.openssl.org) of [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Zie [Een certificaat maken en installeren in Windows](./environment-setup.md#create-and-install-a-certificate) voor meer informatie en instructies voor het installeren van een certificaat.

## <a name="create-a-certificate-on-macos-x"></a>Een certificaat maken in macOS X

Normaal gesproken is het hulpprogramma OpenSSL beschikbaar in het macOS X-besturingssysteem.

U kunt het hulpprogramma OpenSSL ook installeren door een van de volgende opdrachten uit te voeren:

- Vanuit het *Brew*-pakketbeheer:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Met behulp van *MacPorts*:
  
  ```cmd
  sudo port install openssl
  ```

Nadat u het hulpprogramma OpenSSL hebt geïnstalleerd, voert u de volgende opdracht uit om een nieuw certificaat te genereren:

```cmd
pbiviz --install-cert
```

Zie het tabblad OSX in [Een certificaat maken en installeren](./environment-setup.md#create-and-install-a-certificate) voor meer informatie en instructies.

## <a name="create-a-certificate-on-linux"></a>Een certificaat maken in Linux

Normaal gesproken is het hulpprogramma OpenSSL beschikbaar in het Linux-besturingssysteem.

Voordat u begint, voert u de volgende opdrachten uit om te controleren of `openssl` en `certutil` zijn geïnstalleerd:

```sh
which openssl
which certutil
```

Als `openssl` en `certutil` niet zijn geïnstalleerd, installeert u de hulpprogramma's `openssl` en `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Het SSL-configuratiebestand maken

Maak een bestand met de naam */tmp/openssl.cnf* dat de volgende tekst bevat:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Basiscertificeringsinstantie genereren

Voer de volgende opdrachten uit om de basiscertificeringsinstantie (CA) voor het ondertekenen van lokale certificaten te genereren:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Een certificaat voor localhost genereren 

Als u een certificaat voor `localhost` wilt genereren met behulp van de gegenereerde CA en *openssl.cnf*, voert u de volgende opdrachten uit:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Basiscertificaten toevoegen

Als u een basiscertificaat wilt toevoegen aan de database van de browser Chrome, voert u het volgende uit:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Als u een basiscertificaat wilt toevoegen aan de database van de browser Mozilla Firefox, voert u het volgende uit:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Als u een basiscertificaat voor het hele systeem wilt toevoegen, voert u het volgende uit:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Basiscertificaten verwijderen

Als u een basiscertificaat wilt verwijderen, voert u het volgende uit:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Een certificaat handmatig genereren

U kunt ook handmatig een SSL-certificaat genereren met behulp van OpenSSL. U kunt elk gewenst hulpprogramma voor het genereren van uw certificaten opgeven.

Als OpenSSL al is geïnstalleerd, genereert u een nieuw certificaat door het volgende uit te voeren:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

U vindt de webservercertificaten van `PowerBI-visuals-tools` normaal gesproken door een van de volgende opdrachten uit te voeren:

- Voor het algemene exemplaar van de hulpprogramma's:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Voor het lokale exemplaar van de hulpprogramma's:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM-indeling

Als u de certificaatindeling PEM (Privacy Enhanced Mail) gebruikt, slaat u het certificaatbestand op als *PowerBIVisualTest_public.crt* en slaat u de persoonlijke sleutel op als *PowerBIVisualTest_private.key*.

### <a name="pfx-format"></a>PFX-indeling

Als u de certificaatindeling PFX (Personal Information Exchange) gebruikt, slaat u het certificaatbestand op als *PowerBIVisualTest_public.pfx-* .

Als voor uw PFX-certificaatbestand een wachtwoordzin is vereist, gaat u als volgt te werk:

1. Geef in het configuratiebestand het volgende op:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. Geef in de sectie `server` de wachtwoordzin op door de tijdelijke aanduiding \<YOUR PASSPHRASE> te vervangen:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Volgende stappen
- [Een visual van een cirkelkaart ontwikkelen in Power BI](develop-circle-card.md)
- [Voorbeelden van Power BI-visuals](samples.md)
- [Een Power BI-visual publiceren naar AppSource](office-store.md)