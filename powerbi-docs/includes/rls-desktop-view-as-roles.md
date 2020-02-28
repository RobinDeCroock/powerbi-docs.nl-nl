---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464359"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>De rollen in Power BI Desktop valideren
Nadat u uw rollen hebt gemaakt, kunt u de resultaten van de rollen testen binnen Power BI Desktop.

1. Selecteer in het tabblad **Modellering** de optie **Als rollen weergeven**. 

    ![Als rollen weergeven selecteren](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    In het venster **Als rollen weergeven** dat wordt weergegeven, kunt u de rollen zien die u hebt gemaakt.

    ![Venster Als rollen weergeven](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. Selecteer een rol die u hebt gemaakt en selecteer **OK** om die rol toe te passen. 

   De rapporten geven de gegevens weer die relevant zijn voor die rol.

4. U kunt ook **Andere gebruiker** selecteren en een bepaalde gebruiker opgeven. 

    ![Andere gebruiker selecteren](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   U kunt het beste de User Principal Name (UPN) opgeven, omdat die door de Power BI-service Power BI Report Server wordt gebruikt.

   Binnen Power BI Desktop geeft **Andere gebruiker** alleen verschillende resultaten weer wanneer u dynamische beveiliging gebruikt op basis van uw DAX-expressies. 

5. Selecteer **OK**. 

   Het rapport wordt weergegeven op basis van wat de gebruiker kan zien.



