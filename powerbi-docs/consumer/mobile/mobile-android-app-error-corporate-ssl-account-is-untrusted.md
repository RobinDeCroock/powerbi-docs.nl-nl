---
title: De fout 'Zakelijk SSL-certificaat is niet vertrouwd' herstellen
description: Tijdens het aanmelden bij de Android-app voor Power BI ziet u mogelijk u het bericht, 'Kan niet worden geverifieerd omdat uw zakelijke SSL-certificaat niet vertrouwd is
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/28/2019
ms.author: mshenhav
ms.openlocfilehash: cde8a4bbaed9ef10940b7a102d40a8bc6009e9b9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879467"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>De fout 'Zakelijk SSL-certificaat is niet vertrouwd' herstellen - Power BI
Tijdens het aanmelden bij de mobiele Android-app voor Microsoft Power BI ziet u mogelijk u het bericht, 'Kan niet worden geverifieerd omdat uw zakelijke SSL-certificaat niet vertrouwd is door dit apparaat. Neem contact op met de IT-beheerder van uw bedrijf.' 

Wat u moet doen is meestal afhankelijk van het besturingssysteem op uw Android-apparaat, maar er zijn een aantal andere problemen waardoor deze fout kan optreden.

## <a name="on-android-7-or-later"></a>Op Android 7 of hoger
Zoek een update voor een app met de naam **Chrome** en installeer de update.

## <a name="on-android-6-and-earlier"></a>Op Android 6 en eerdere versies
Uw apparaat heeft mogelijk een bijgewerkte versie van System Webview nodig. Deze kan worden geïnstalleerd op uw apparaat en u hoeft mogelijk slechts op **Updaten** te klikken.

Ga als volgt te werk als System Webview niet is geïnstalleerd op uw apparaat:

1. Sluit Power BI op uw Android-apparaat.
2. Open de Google Play Store en zoek naar **System Webview** door Google Inc.
3. Installeren de app.
4. Start de Power BI-app en meld u aan.

## <a name="time-zone-settings"></a>Tijdzone-instellingen
De tijdzone-instellingen op het apparaat zijn mogelijk onjuist. 

Ga naar **Instellingen** > **Systeem** > **Datum en tijd** en controleer of ze.

## <a name="custom-authentication-server"></a>Aangepaste verificatieserver
Als u een aangepaste verificatieserver gebruikt, wordt het SSL-certificaat in de zakelijke verificatieserver mogelijk ongeldig. Werk samen met de IT-afdeling van uw organisatie om de configuratie van de zakelijke verificatieserver te testen. Volg daarbij de richtlijnen in [dit artikel](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Volgende stappen
* [De Android-app downloaden](https://go.microsoft.com/fwlink/?LinkID=544867) vanuit de Android-app-store.
* Vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/) 

