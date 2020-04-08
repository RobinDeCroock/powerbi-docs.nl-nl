---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621567"
---
Service-principal is een verificatiemethode die kan worden gebruikt om een Azure AD-toepassing toegang te geven tot inhoud en API's van de Power BI-service.

Wanneer u een Azure Active Directory-app (Azure AD) maakt, wordt er een [service-principal-object](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) gemaakt. Met het service-principal-object, ook wel een *service-principal* genoemd, kan Azure AD uw app verifiëren. Nadat de app is geverifieerd, heeft deze toegang tot Azure AD-tenantbronnen.

Voor de verificatie gebruikt de service-principal de *toepassings-id* van de Azure AD-app en een van de volgende elementen:
* Toepassingsgeheim
* Certificaat