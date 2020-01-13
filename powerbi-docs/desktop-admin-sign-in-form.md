---
title: Hoe beheerders het Power BI Desktop-aanmeldingsformulier kunnen beheren
description: Meer informatie over hoe u het formulier voor eerste aanmelding kunt beheren bij het openen van Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 934827311e089e34e56fbcffe4d4c58a056df4ad
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761698"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Beheerders: Het Power BI Desktop-aanmeldingsformulier beheren
De eerste keer dat Power BI Desktop wordt gestart, wordt een aanmeldingsformulier weergegeven. Er kunnen gegevens in worden ingevuld, of u kunt zich aanmelden bij Power BI om door te gaan. Beheerders beheren dit formulier met behulp van een registersleutel. 

![Formulier voor eerste aanmelding voor Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Beheerders gebruiken de volgende registersleutel om het aanmeldingsformulier uit te schakelen. Dit kan ook worden geactiveerd voor een gehele organisatie met behulp van globaal beleid.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
U kunt ook de volgende sleutel proberen, die heeft gewerkt voor sommige klanten op basis van hun configuraties:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Met een waarde van 0 wordt het dialoogvenster uitgeschakeld.




Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)

