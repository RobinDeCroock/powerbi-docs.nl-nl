---
title: Waar bevindt mijn Power BI-tenant zich?
description: Informatie over waar uw Power BI-tenant zich bevindt en hoe deze locatie wordt geselecteerd. Het is belangrijk dat u dit weet, omdat dit gevolgen kan hebben voor interacties die u met de service hebt.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 632eca1fdcb1bed380ad699a36264bc0239baef5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412386"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Waar bevindt mijn Power BI-tenant zich?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Informatie over waar uw Power BI-tenant zich bevindt en hoe deze locatie wordt geselecteerd. Het is belangrijk om bekend te zijn met de locatie omdat deze van invloed kan zijn op interacties met de service.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Bepalen waar uw Power BI-tenant zich bevindt

Volg deze stappen om vast te stellen in welke regio uw tenant zich bevindt.

1. Selecteer in de Power BI-service in het bovenste menu Help ( **?** ) en vervolgens **Over Power BI**.

1. Kijk naar de waarde naast **Uw gegevens worden opgeslagen in**. Dit is de regio waar uw tenant zich bevindt. Deze waarde geeft ook de regio aan waarin uw gegevens worden opgeslagen, tenzij u voor uw werkruimten capaciteiten in verschillende regio's gebruikt.

    ![Gegevensgebied](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Hoe de gegevensregio wordt geselecteerd

Het gegevensgebied is gebaseerd op het land dat/de regio die u selecteert bij het maken van de tenant. De selectie geldt voor de registratie voor zowel Microsoft 365 als Power BI, aangezien deze informatie wordt gedeeld. Als dit een nieuwe tenant is, selecteert u het juiste land/de juiste regio uit de lijst wanneer u zich registreert.

![Land/regio selecteren](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI kiest een gegevensgebied het dichtst in de buurt van uw selectie, waarmee wordt bepaald waar gegevens voor uw tenant worden opgeslagen.

> [!IMPORTANT]
> U kunt deze selectie niet wijzigen nadat u de tenant hebt gemaakt.

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
