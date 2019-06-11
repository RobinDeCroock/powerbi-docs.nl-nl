---
title: bestand opnemen
description: bestand opnemen
services: powerbi
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: mblythe
ms.openlocfilehash: 94b6959b6bcbf250e54a353e8b725b6c9e5a2e30
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448414"
---
## <a name="single-sign-on"></a>Eenmalige aanmelding

Nadat u een Azure SQL DirectQuery-gegevensset naar de service hebt gepubliceerd, kunt u eenmalige aanmelding (SSO) via Azure Active Directory (Azure AD) OAuth2 inschakelen voor uw eindgebruikers.

Als u eenmalige aanmelding wilt inschakelen, gaat u naar de instellingen voor de gegevensset. Open het tabblad **Gegevensbronnen** en schakel het vakje voor eenmalige aanmelding in.

![Het dialoogvenster Azure SQL DQ configureren](media/direct-query-sso/sso-dialog.png)

Wanneer de optie voor eenmalige aanmelding is ingeschakeld en uw gebruikers toegang hebben tot rapporten die op de gegevensbron zijn gebouwd, verzendt Power BI hun geverifieerde Azure AD-referenties in de query's naar de Azure SQL-database of datawarehouse. Hierdoor kan Power BI rekening houden met de beveiligingsinstellingen die op het niveau van de gegevensbronnen zijn geconfigureerd.

De optie voor eenmalige aanmelding heeft effect op alle gegevenssets die gebruikmaken van deze gegevensbron. Het heeft geen invloed op de verificatiemethode die wordt gebruikt om scenario's te importeren.

> [!Note]
> Azure Multi-Factor Authentication (MFA) wordt niet ondersteund. Gebruikers die gebruik willen maken van SSO met SQL DirectQuery, moeten worden uitgesloten van MFA.