---
title: Hoe beheerders het Power BI Desktop-aanmeldingsformulier kunnen beheren
description: Meer informatie over hoe u het formulier voor eerste aanmelding kunt beheren bij het openen van Power BI Desktop.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/15/2019
ms.openlocfilehash: 633d71326009881b22b7b7d235316b4ebe5c132f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386876"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>Beheerders: Het Power BI Desktop-aanmeldingsformulier beheren
De eerste keer dat Power BI Desktop wordt gestart, wordt een aanmeldingsformulier weergegeven. Er kunnen gegevens in worden ingevuld, of u kunt zich aanmelden bij Power BI om door te gaan. Beheerders beheren dit formulier met behulp van een registersleutel. 

![Schermopname van een formulier voor eerste aanmelding voor Power BI Desktop.](media/desktop-admin-sign-in-form/sign-in-form.png)

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

