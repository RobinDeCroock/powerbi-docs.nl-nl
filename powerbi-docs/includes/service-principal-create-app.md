---
title: App voor service-principal maken
description: App voor service-principal maken
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524512"
---
1. Meld u aan bij [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Zoek naar **App-registraties** en klik op de koppeling **App-registraties**.

    ![Azure-app-registratie](media/embedded-service-principal/azure-app-registration.png)

3. Klik op **Nieuwe registratie**.

    ![nieuwe registratie](media/embedded-service-principal/new-registration.png)

4. Vul de vereiste gegevens in:
    * **Naam**: voer een naam in voor de toepassing
    * **Ondersteunde accounttypen**: selecteer ondersteunde accounttypen
    * (Optioneel) **Omleidings-URI**: voer een URI in, indien nodig

5. Klik op **Registreren**.

6. Na de app-registratie is de *toepassings-id* beschikbaar op het tabblad **Overzicht**. Kopieer de *toepassings-id* en sla deze op voor later gebruik.

    ![Schermopname die laat zien waar u een toepassings-i d kunt verkrijgen op het tabblad Overzicht.](media/embedded-service-principal/application-id.png)