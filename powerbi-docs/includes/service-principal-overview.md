---
title: Overzicht van een service-principal
description: Overzicht van een service-principal
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989430"
---
Service-principal is een verificatiemethode die kan worden gebruikt om een Azure AD-toepassing toegang te geven tot inhoud en API's van de Power BI-service.

Wanneer u een Azure Active Directory-app (Azure AD) maakt, wordt er een [service-principal-object](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) gemaakt. Met het service-principal-object, ook wel een *service-principal* genoemd, kan Azure AD uw app verifiëren. Nadat de app is geverifieerd, heeft deze toegang tot Azure AD-tenantbronnen.

Voor de verificatie gebruikt de service-principal de *toepassings-id* van de Azure AD-app en een van de volgende elementen:

* Toepassingsgeheim
* Certificaat