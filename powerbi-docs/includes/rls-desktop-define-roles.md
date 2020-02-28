---
ms.openlocfilehash: 27d6db6cf8ad8ebd7b2c957954ceec34b83681d0
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464362"
---
## <a name="define-roles-and-rules-in-power-bi-desktop"></a>Rollen en regels definiëren in Power BI Desktop
U kunt rollen en regels definiëren binnen Power BI Desktop. Wanneer u naar Power BI publiceert, worden ook de roldefinities gepubliceerd.

Volg deze stappen om beveiligingsrollen te definiëren.

1. Gegevens importeren in uw Power BI Desktop-rapport of een DirectQuery-verbinding configureren.
   
   > [!NOTE]
   > U kunt geen rollen binnen Power BI Desktop definiëren voor live verbindingen met Analysis Services. U moet dat doen binnen het Analysis Services-model.
   > 
   > 
2. Op het tabblad **Modellering** selecteert u **Rollen beheren**.
   
   ![Rollen beheren selecteren](./media/rls-desktop-define-roles/powerbi-desktop-security.png)
3. Selecteer in het venster **Rollen beheren** de optie **Maken**.
   
   ![Selecteer Maken](./media/rls-desktop-define-roles/powerbi-desktop-security-create-role.png)
4. Geef onder **Rollen** een naam op voor de rol. 
5. Selecteer onder **Tabellen** de tabel waarop u een DAX-regel wilt toepassen.
6. Voer in het vak **DAX-expressie tabelfilter** de DAX-expressies in. Deze expressie retourneert de waarde True of False. Bijvoorbeeld: ```[Entity ID] = “Value”```.
      
   ![Venster Rollen beheren](./media/rls-desktop-define-roles/powerbi-desktop-security-create-rule.png)

   > [!NOTE]
   > U kunt *username()* binnen deze expressie gebruiken. Let op: *username()* heeft de indeling *DOMAIN\username* binnen Power BI Desktop. Binnen de Power BI-service en Power BI Report Server heeft deze de indeling van de UPN (User Principal Name) van de gebruiker. U kunt ook *userprincipalname()* gebruiken, waarmee altijd de gebruiker wordt geretourneerd in de indeling van zijn/haar naam van de principal van gebruiker, *username\@contoso.com*.
   > 
   > 

7. Nadat u de DAX-expressie hebt gemaakt, selecteert u het vinkje boven het expressievak om de expressie te valideren.
      
   ![DAX-expressie valideren](./media/rls-desktop-define-roles/powerbi-desktop-security-validate-dax.png)
   
   > [!NOTE]
   > In dit expressievak gebruikt u komma's om argumenten van DAX-functies te scheiden, zelfs als u een landinstelling gebruikt die gewoonlijk puntkomma's als scheidingsteken gebruikt (bijvoorbeeld Frans of Duits). 
   >
   >
   
8. Selecteer **Opslaan**.

U kunt geen rol toewijzen aan gebruikers binnen Power BI Desktop. U wijst deze toe in de Power BI-service. U kunt dynamische beveiliging inschakelen binnen Power BI Desktop door gebruik te maken van de DAX-functies voor *username()* of *userprincipalname()* en het configureren van de juiste relaties. 

