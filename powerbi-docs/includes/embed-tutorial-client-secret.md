---
title: Zelf studie voor Inge sloten analyses voor het verkrijgen van client geheim
description: Het client geheim ophalen voor de zelf studies voor Inge sloten analyse.
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: 875243aa890b80d21a73b20dec291329d256ba21
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494608"
---
Als u het clientgeheim wilt ophalen, voert u de volgende stappen uit:

1. Meld u aan bij [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Ga naar **App-registraties** en selecteer de koppeling **App-registraties**.

3. Selecteer de Azure AD-app die u gebruikt voor het insluiten van uw Power BI-inhoud.

4. Selecteer onder **Beheren** de optie **Certificaten en geheimen**.

5. Selecteer onder **Clientgeheimen** de optie **Nieuw clientgeheim**.

6. Geef in het pop-upvenster **Een clientgeheim toevoegen** een beschrijving op voor uw app-geheim, selecteer wanneer het app-geheim verloopt en selecteer **Toevoegen**.

7. Kopieer in de sectie **Clientgeheimen** de tekenreeks in de kolom **Waarde** van het zojuist gemaakte app-geheim. De waarde van het clientgeheim is uw *client-id*.