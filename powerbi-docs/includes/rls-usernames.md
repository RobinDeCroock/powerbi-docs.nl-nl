---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/29/2019
ms.locfileid: "61193812"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>De DAX-functie username() of userprincipalname() gebruiken
U kunt gebruik maken van de DAX-functies *username()* of *userprincipalname()* binnen uw gegevensset. U kunt deze gebruiken in expressies in Power BI Desktop. Wanneer u uw model publiceert, worden deze functies gebruikt in de Power BI-service.

In Power BI Desktop retourneert de functie *username()* een gebruiker met de indeling *DOMEIN\gebruiker* en retourneert de functie *userprincipalname()* een gebruiker met de indeling  <em>user@contoso.com</em>.

In de Power BI-service retourneren zowel *username()* als *userprincipalname()* de UPN (User Principal Name) van de gebruiker. Dit lijkt op een e-mailadres.

