---
title: Beveiliging op rijniveau (RLS) in Power BI Report Server
description: Meer informatie over beveiliging op rijniveau (RLS) in Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 01/22/2021
ms.openlocfilehash: 50c89bdaa47aa8a687178a33627cf9148720acf2
ms.sourcegitcommit: e8c3f327ac0fc73c118874a24d2601733f8f9e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718572"
---
# <a name="row-level-security-rls-in-power-bi-report-server"></a>Beveiliging op rijniveau (RLS) in Power BI Report Server

Het instellen van beveiliging op rijniveau (RLS) met Power BI Report Server kan toegang tot gegevens beperken voor bepaalde gebruikers. Filters beperken de toegang tot gegevens op rijniveau en u kunt filters definiëren in rollen.  Als u de standaardmachtigingen in Power BI Report Server gebruikt, kan elke gebruiker met de machtigingen Uitgever of Inhoudsbeheerder voor het Power BI-rapport leden toewijzen aan rollen voor dat rapport.    

U configureert RLS voor rapporten die met Power BI Desktop zijn geïmporteerd in Power BI. U kunt RLS ook configureren voor rapporten die gebruikmaken van DirectQuery, zoals SQL Server.  Houd er rekening mee dat RLS niet wordt gerespecteerd als de DirectQuery-verbinding gebruikmaakt van geïntegreerde verificatie voor rapportlezers. Voor Analysis Services-liveverbindingen configureert u beveiliging op rijniveau voor het on-premises model. De beveiligingsoptie wordt niet weergegeven voor gegevenssets met een liveverbinding. 

[!INCLUDE [rls-desktop-define-roles](../includes/rls-desktop-define-roles.md)]

## <a name="bidirectional-cross-filtering"></a>Kruislings filteren in twee richtingen

Het beveiligingsfilter op rijniveau gebruikt standaard filters in één richting, ongeacht of de relaties zijn ingesteld op één richting of twee richtingen. U kunt kruislings filteren in twee richtingen handmatig inschakelen met beveiliging op rijniveau.

- Selecteer de relatie en schakel het selectievakje **Beveiligingsfilter in beide richtingen toepassen** in. 

    ![Beveiligingsfilter toepassen](media/row-level-security-report-server/rls-apply-security-filter.png)

Schakel dit selectievakje in wanneer u [dynamische beveiliging op rijniveau](/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters) implementeert op basis van gebruikersnaam of aanmeldings-id. 

Zie voor meer informatie [Kruislings filteren in twee richtingen met DirectQuery in Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) en het technisch document [Het semantische BI-model in tabelvorm beveiligen](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

[!INCLUDE [rls-desktop-view-as-roles](../includes/rls-desktop-view-as-roles.md)]


## <a name="add-members-to-roles"></a>Leden toevoegen aan rollen 

Nadat u uw rapport hebt opgeslagen in Power BI Report Server, kunt u beveiliging beheren en leden toevoegen of verwijderen op de server. Alleen voor gebruikers met de machtigingen Uitgever of Inhoudsbeheerder voor het rapport is de optie voor beveiliging op rijniveau beschikbaar en wordt deze niet grijs weergegeven.

 Als het rapport niet beschikt over de rollen die nodig zijn, opent u het in Power BI Desktop, voegt u rollen toe of wijzigt u ze, en slaat u het vervolgens weer op in Power BI Report Server. 

1. In Power BI Desktop slaat u het rapport op naar Power BI Report Server. U moet de versie van Power BI Desktop gebruiken die is geoptimaliseerd voor Power BI Report Server.
2. Selecteer in Power BI Report Server het beletselteken ( **...** ) naast het rapport. 

3. Selecteer **Beheren** > **Beveiliging op rijniveau**. 

     ![Beveiliging op rijniveau beheren](media/row-level-security-report-server/power-bi-report-server-rls-dialog.png)

    Op de pagina **Beveiliging op rijniveau** voegt u leden toe aan een rol die u hebt gemaakt in Power BI Desktop.

5. Als u een lid wilt toevoegen, selecteert u **Lid toevoegen**.

1. Voer de gebruiker of groep in het tekstvak in met de indeling Gebruikersnaam (DOMEIN\gebruiker) en selecteer de rollen die u eraan wilt toewijzen. Het lid moet zich binnen uw organisatie bevinden.   

    ![Lid aan rol toevoegen](media/row-level-security-report-server/power-bi-report-server-add-members.png)

    Afhankelijk van hoe u Active Directory hebt geconfigureerd, kunt u hier ook de User Principal Name invoeren. De rapportserver geeft in dat geval de overeenkomende gebruikersnaam in de lijst weer.

1. Klik op **OK** om toe te passen.   

8. Als u leden wilt verwijderen, schakelt u het selectievakje naast de namen in en selecteert u **Verwijderen**.  U kunt meerdere leden tegelijk verwijderen. 

    ![Leden verwijderen](media/row-level-security-report-server/power-bi-report-server-delete-members.png)


## <a name="username-and-userprincipalname"></a>username() en userprincipalname()

U kunt gebruikmaken van de DAX-functies username() of userprincipalname() binnen uw gegevensset. U kunt deze gebruiken in expressies in Power BI Desktop. Wanneer u uw model publiceert, gebruikt Power BI Report Server deze.

In Power BI Desktop retourneert de functie username() een gebruiker met de indeling DOMEIN\Gebruiker en retourneert userprincipalname() een gebruiker met de indeling user@contoso.com.

In Power BI Report Server retourneren username() en userprincipalname() beide de UPN (User Principal Name) van de gebruiker, die vergelijkbaar is met een e-mailadres.

Als u aangepaste verificatie gebruikt in Power BI Report Server, wordt de gebruikersnaamindeling geretourneerd die u hebt ingesteld voor gebruikers.  

## <a name="limitations"></a>Beperkingen 

Dit zijn de huidige beperkingen voor beveiliging op rijniveau in Power BI-modellen. 

Gebruikers die rapporten hadden met de DAX-functie username() zien nu nieuw gedrag waar de User Principal Name (UPN) wordt geretourneerd, TENZIJ DirectQuery wordt gebruikt met geïntegreerde beveiliging.  Aangezien RLS niet wordt gerespecteerd in dat scenario, is het gedrag in dat scenario niet gewijzigd.

U kunt RLS alleen definiëren in gegevenssets die zijn gemaakt met Power BI Desktop. Om RLS in te schakelen voor gegevenssets die zijn gemaakt met Excel, moet u uw bestanden eerst converteren naar PBIX-bestanden (Power BI Desktop). Meer informatie over [Excel-bestanden converteren](../connect-data/desktop-import-excel-workbooks.md).

Alleen Extraheren, Transformeren, Laden (ETL) en DirectQuery-verbindingen met behulp van de opgeslagen referenties worden ondersteund. Live-verbindingen met Analysis Services- en DirectQuery-verbindingen via geïntegreerde verificatie worden verwerkt in de onderliggende gegevensbron. 

Als u geïntegreerde beveiliging met DirectQuery gebruikt, kunnen uw gebruikers het volgende zien:
- RLS is uitgeschakeld en alle gegevens worden geretourneerd.
- Gebruikers kunnen hun roltoewijzingen niet bijwerken en krijgen een fout op de pagina RLS beheren.
- Voor de DAX-functie username blijft u de gebruikersnaam ontvangen als DOMEIN\GEBRUIKER. 

Auteurs van rapporten hebben geen toegang tot de rapportgegevens in Power BI Report Server totdat ze aan zichzelf dienovereenkomstig rollen hebben toegewezen nadat het rapport is geüpload. 

Roltoewijzingen via groepslid maatschappen worden alleen ondersteund als de Power BI Report Server is geconfigureerd om te worden uitgevoerd met NTLM-of Kerberos-verificatie. Servers met aangepaste verificatie of Windows Basic hebben gebruikers expliciet aan rollen toegewezen.
 

## <a name="faq"></a>Veelgestelde vragen 

### <a name="can-i-create-these-roles-for-analysis-services-data-sources"></a>Kan ik deze rollen voor Analysis Services-gegevensbronnen maken? 

Dat kan als u de gegevens hebt geïmporteerd in Power BI Desktop. Als u een liveverbinding gebruikt, kunt u RLS niet configureren binnen de Power BI-service. RLS wordt on-premises gedefinieerd in het Analysis Services-model. 

### <a name="can-i-use-rls-to-limit-the-columns-or-measures-accessible-by-my-users"></a>Kan ik RLS gebruiken om de kolommen of metingen te beperken die toegankelijk zijn voor mijn gebruikers? 

Nee. Als een gebruiker toegang heeft tot een bepaalde gegevensrij, kan deze alle gegevenskolommen voor die rij zien. 

### <a name="does-rls-let-me-hide-detailed-data-but-give-access-to-data-summarized-in-visuals"></a>Kan ik met RLS gedetailleerde gegevens verbergen maar toegang geven tot samengevatte gegevens in visuele elementen? 

Nee, u beveiligt individuele rijen met gegevens maar gebruikers kunnen altijd de details of de samengevatte gegevens zien. 

### <a name="can-i-add-new-roles-in-power-bi-desktop-if-i-already-have-existing-roles-and-members-assigned"></a>Kan ik nieuwe functies toevoegen in Power BI Desktop als ik al bestaande rollen en leden heb toegewezen? 

Ja, als u al bestaande rollen hebt gedefinieerd en leden hebt toegewezen in Power BI Report Server, kunt u aanvullende rollen maken en uw rapport opnieuw publiceren zonder dat dit invloed heeft op uw huidige toewijzingen. 
 

## <a name="next-steps"></a>Volgende stappen

[Wat is Power BI Report Server?](get-started.md) 
[Handboek voor beheerders](admin-handbook-overview.md)  

Hebt u nog vragen? [Misschien dat de Power BI-community het antwoord weet](https://community.powerbi.com/)
