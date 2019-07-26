---
title: Rapportparameters in Power BI Report Builder
description: In dit onderwerp worden de gebruikelijke toepassingen van rapportparameters van de gepagineerde Report Builder voor Power BI, de eigenschappen die u kunt instellen en nog veel meer beschreven.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.date: 06/06/2019
ms.openlocfilehash: 21fe08c2cba004a6aff77eae12303d0181ab56ec
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840528"
---
# <a name="report-parameters-in-power-bi-report-builder"></a>Rapportparameters in Power BI Report Builder

In dit onderwerp worden de gebruikelijke toepassingen van rapportparameters van de gepagineerde Report Builder voor Power BI, de eigenschappen die u kunt instellen en nog veel meer beschreven. Met behulp van rapportparameters kunt u rapportgegevens beheren, gerelateerde rapporten met elkaar verbinden en de presentatie van rapporten variëren. U kunt rapportparameters gebruiken in gepagineerde rapporten die u in Report Builder maakt.

## <a name="bkmk_Common_Uses_for_Parameters"></a> Veelvoorkomende toepassingen van parameters

 Hier volgen enkele veelvoorkomende manieren om parameters te gebruiken.  
  
**Gegevens voor gepagineerde rapporten beheren**
  
- Filter gegevens voor gepagineerde rapporten in de gegevensbron door gegevenssetquery's te schrijven die variabelen bevatten.  
  
- Stel gebruikers in staat om waarden op te geven voor het aanpassen van de gegevens op een gepagineerd rapport. Bied bijvoorbeeld twee parameters aan voor de begin- en einddatum van verkoopgegevens.  
  
**De rapportpresentatie variëren**
  
- Stel gebruikers in staat waarden op te geven waarmee ze de weergave van het rapport kunnen aanpassen. Bied bijvoorbeeld een booleaanse parameter aan om alle geneste rijgroepen in een tabel uit te vouwen of samen te vouwen.  
  
- Stel gebruikers in staat om rapportgegevens en de weergave ervan aan te passen door parameters op te nemen in een expressie.  
  
## <a name="UserInterface"></a> Een gepagineerd rapport met parameters weergeven

Wanneer u een rapport met parameters weergeeft, wordt elke parameter weergegeven op de werkbalk van de rapportviewer zodat u interactief waarden kunt opgeven. In de volgende illustratie ziet u het parametergebied voor een rapport met de parameters @ReportMonth, @ReportYear, @EmployeeID, @ShowAll, @ExpandTableRows, @CategoryQuota en @SalesDate.  

![Een rapport met parameters weergeven](media/report-builder-parameters/report-builder-parameters-power-bi-service.png "Een rapport met parameters weergeven")
  
1. **Het deelvenster Parameters** Op de werkbalk van de rapportviewer wordt voor elke parameter een prompt en een standaardwaarde weergegeven. U kunt de indeling van de parameters aanpassen in het deelvenster Parameters.  
  
2. **@SalesDate parameter** de parameter @SalesDate gegevenstype **datum-/** . De prompt Selecteer de datum wordt naast het tekstvak weergegeven. U kunt de datum wijzigen door een nieuwe datum in het tekstvak te typen of het kalenderbesturingselement te gebruiken.  
  
3. **@ShowAll parameter** de parameter @ShowAll gegevenstype **Booleaanse**. Gebruik de keuzerondjes om **Waar** of **Onwaar** op te geven.  
  
4. **De greep Parametergebied weergeven of verbergen** Op de werkbalk van de rapportviewer klikt u op deze pijl om het parametervenster weer te geven of te verbergen.  
  
5. **@CategoryQuota parameter** de parameter @CategoryQuota gegevenstype **drijvende komma**, zodat het duurt een numerieke waarde voordat.  @CategoryQuota is zo ingesteld dat er meerdere waarden zijn toegestaan.  
  
6. **Rapport weergeven** Nadat u parameterwaarden hebt ingevoerd, klikt u op **Rapport weergeven** om het rapport uit te voeren. Als alle parameters standaardwaarden hebben, wordt het rapport bij de eerste weergave automatisch uitgevoerd.  
  
## <a name="bkmk_Create_Parameters"></a> Parameters maken

U kunt op verschillende manieren rapportparameters maken.
  
> [!NOTE]
>  Niet alle gegevensbronnen ondersteunen parameters.
  
**Een gegevenssetquery of opgeslagen procedure met parameters**
  
 Voeg een gegevenssetquery die variabelen bevat of een in de gegevensset opgeslagen procedure die invoerparameters bevat toe. Er wordt een gegevenssetparameter gemaakt voor elke variabele of invoerparameter en er wordt een rapportparameter gemaakt voor elke gegevenssetparameter.  
  
![Eigenschappen van de parametergegevensset van Report Builder](media/report-builder-parameters/report-builder-parameter-dataset.png "Eigenschappen van de parametergegevensset van Report Builder")

  
 Op deze afbeelding van Report Builder is het volgende te zien:  
  
1.  De rapportparameters in het deelvenster Rapportgegevens.  
  
2.  De gegevensset met de parameters.  
  
3.  Het deelvenster Parameters.  
  
4.  De parameters die worden weergegeven in het dialoogvenster Eigenschappen van gegevensset.  
  
**Handmatig een parameter maken**
  
Maak een parameter handmatig in het deelvenster Rapportgegevens. U kunt rapportparameters configureren zodat een gebruiker interactief waarden kan invoeren om de inhoud of de weergave van een rapport aan te passen. U kunt ook zelf rapportparameters configureren, zodat een gebruiker vooraf geconfigureerde waarden niet kan wijzigen.  
  
> [!NOTE]  
>  Omdat parameters afzonderlijk op de server worden beheerd, worden de bestaande parameterinstellingen van een hoofdrapport niet overschreven als het rapport opnieuw wordt gepubliceerd met nieuwe parameterinstellingen.  

### <a name="parameter-values"></a>Parameterwaarden

 Hieronder vindt u opties voor het selecteren van parameterwaarden in het rapport.  
  
- Eén parameterwaarde selecteren in een vervolgkeuzelijst.  
  
- Meerdere parameterwaarden selecteren in een vervolgkeuzelijst.  
  
- Een waarde voor één parameter selecteren in een vervolgkeuzelijst, waarmee wordt bepaald welke waarden beschikbaar zijn in de vervolgkeuzelijst voor een andere parameter. Dit zijn trapsgewijze parameters. Met trapsgewijze parameters kunt u achter elkaar parameterwaarden van duizenden waarden filteren tot een beheersbaar getal.  
  
- Het rapport uitvoeren zonder eerst een parameterwaarde te moeten selecteren omdat er een standaardwaarde voor de parameter is gemaakt.  
  
## <a name="bkmk_Report_Parameters"></a> Eigenschappen van rapportparameters

 U kunt de eigenschappen van rapportparameters wijzigen in het dialoogvenster Rapporteigenschappen. De volgende tabel biedt een overzicht van de eigenschappen die u voor elke parameter kunt instellen:  
  
|Eigenschap|Beschrijving|  
|--------------|-----------------|  
|Naam|Typ een hoofdlettergevoelige naam voor de parameter. De naam moet beginnen met een letter en mag letters, cijfers en onderstrepingstekens (_) bevatten. De naam mag geen spaties bevatten. De naam van automatisch gegenereerde parameters komt overeen met de parameter in de gegevenssetquery. Standaard zijn handmatig gemaakte parameters gelijk aan ReportParameter1.|  
|Prompt|De tekst die op de werkbalk van de rapportviewer naast de parameter wordt weergegeven.|  
|Gegevenstype|Een rapportparameter moet een van de volgende gegevenstypen hebben:<br /><br /> **Booleaans**. De gebruiker selecteert Waar of Onwaar in een keuzerondje.<br /><br /> **Datum/tijd**. De gebruiker selecteert een datum in een kalenderbesturingselement.<br /><br /> **Geheel getal**. De gebruiker typt waarden in een tekstvak.<br /><br /> **Drijvend**. De gebruiker typt waarden in een tekstvak.<br /><br /> **Tekst**. De gebruiker typt waarden in een tekstvak.<br /><br /> Wanneer er beschikbare waarden voor een parameter zijn gedefinieerd, kiest de gebruiker waarden in een vervolgkeuzelijst, ook wanneer het gegevenstype **Datum/tijd** is.|  
|Lege waarde toestaan|Selecteer deze optie als de waarde van de parameter een lege tekenreeks of blanco mag zijn.<br /><br /> Als u bij het opgeven van geldige waarden voor een parameter wilt dat een lege waarde ook geldig is, moet u deze lege waarde ook opgeven. Bij selectie van deze optie wordt niet automatisch een lege waarde bij de beschikbare waarden opgenomen.|  
|De waarde null toestaan|Selecteer deze optie als de waarde van de parameter null mag zijn.<br /><br /> Als u bij het opgeven van geldige waarden voor een parameter wilt dat null ook een geldige waarde is, moet u null ook opgeven. Bij selectie van deze optie wordt null niet automatisch bij de beschikbare waarden opgenomen.|  
|Meerdere waarden toestaan|Geef beschikbare waarden op om een vervolgkeuzelijst te maken waaruit uw gebruikers kunnen kiezen. Dit is een goede manier om ervoor te zorgen dat alleen geldige waarden worden opgegeven in de gegevenssetquery.<br /><br /> Selecteer deze optie als de waarde voor de parameter mag bestaan uit meerdere waarden die worden weergegeven in een vervolgkeuzelijst. De waarde null is niet toegestaan. Wanneer deze optie is geselecteerd, worden er selectievakjes toegevoegd aan de lijst met beschikbare waarden in de vervolgkeuzelijst voor een parameter. Bovenaan de lijst komt het selectievakje **Alles selecteren**. Gebruikers kunnen de gewenste waarden selecteren.<br /><br /> Als de gegevens voor de waarden snel worden gewijzigd, is de lijst die de gebruiker te zien krijgt mogelijk niet de meest recente.|  
|Zichtbaar|Selecteer deze optie om de rapportparameter bovenaan het rapport weer te geven wanneer het wordt uitgevoerd. Met deze optie kunnen gebruikers tijdens de uitvoering parameterwaarden selecteren.|  
|Verborgen|Selecteer deze optie om de rapportparameter te verbergen in het gepubliceerde rapport. De waarden voor rapportparameters kunnen nog steeds worden ingesteld in een rapport-URL, in een abonnementsdefinitie of op de rapportserver.|  
|Intern|Selecteer deze optie om de rapportparameter te verbergen. In het gepubliceerde rapport kan de rapportparameter alleen worden weergegeven in de rapportdefinitie.|  
|Beschikbare waarden|Als u de beschikbare waarden voor een parameter hebt opgegeven, worden de geldige waarden altijd in een vervolgkeuzelijst weergegeven. Als u bijvoorbeeld beschikbare waarden opgeeft voor een **DateTime**-parameter, wordt er een vervolgkeuzelijst voor datums weergegeven in het deelvenster in plaats van een kalenderbesturingselement.<br /><br /> U kunt ervoor zorgen dat een lijst met waarden consistent blijft binnen rapporten en subrapporten door voor de gegevensbron de optie in te stellen dat er een enkele transactie wordt gebruikt voor alle query's in de gegevenssets die zijn gekoppeld aan een gegevensbron.<br /><br /> **Beveiligingsopmerking** Zorg er voor elk rapport met een parameter van het gegevenstype **Tekst** voor dat u een lijst met beschikbare/geldige waarden gebruikt en dat elke gebruiker die het rapport uitvoert alleen beschikt over de machtigingen die nodig zijn om de gegevens in het rapport weer te geven.|  
|Standaardwaarden|Stel standaardwaarden in via een query of een statische lijst.<br /><br /> Wanneer elke parameter een standaardwaarde heeft, wordt het rapport bij de eerste weergave automatisch uitgevoerd.|  
|Geavanceerd|Stel het rapportdefinitiekenmerk **UsedInQuery** in. Dat is een waarde die aangeeft of deze parameter direct of indirect invloed heeft op de gegevens in een rapport.<br /><br /> **Automatisch bepalen wanneer moet worden vernieuwd**<br /> Kies deze optie als u wilt dat de instelling van deze waarde door de rapportprocessor wordt bepaald. De waarde is **Waar** als er een gegevenssetquery met een directe of indirecte verwijzing naar deze parameter wordt gedetecteerd, of als het rapport subrapporten bevat.<br /><br /> **Altijd vernieuwen**<br /> Selecteer deze optie wanneer de rapportparameter direct of indirect wordt gebruikt in een gegevenssetquery of parameterexpressie. Met deze optie stelt u **UsedInQuery** in op Waar.<br /><br /> **Nooit vernieuwen**<br /> Selecteer deze optie wanneer de rapportparameter niet direct of indirect wordt gebruikt in een gegevenssetquery of parameterexpressie. Met deze optie stelt u **UsedInQuery** in op Onwaar.<br /><br /> **Waarschuwing** Pas op met het gebruik van **Nooit vernieuwen**. Op de rapportserver wordt **UsedInQuery** gebruikt bij het beheren van cacheopties voor rapportgegevens en voor weergegeven rapporten en van parameteropties voor momentopnamerapporten. Als u **Nooit vernieuwen** verkeerd instelt, kan dit leiden tot onjuiste rapportgegevens, ertoe leiden dat rapporten in de cache worden opgeslagen of dat momentopnamerapporten inconsistente gegevens bevatten. |  
  
##  <a name="bkmk_Dataset_Parameters"></a> Gegevenssetquery  
 Als u gegevens in de gegevenssetquery wilt filteren, kunt u een component opnemen om de opgehaalde gegevens te beperken door op te geven welke waarden moeten worden opgenomen in- of uitgesloten van de resultatenset.  
  
 Gebruik de queryontwerpfunctie voor de gegevensbron bij het maken van een geparameteriseerde query.  
  
-   Voor Transact-SQL-query's bieden verschillende gegevensbronnen ondersteuning voor verschillende syntaxissen voor parameters. De ondersteuning varieert van parameters die in de query worden geïdentificeerd op basis van de positie of op basis van de naam. In de ontwerpfunctie voor relationele query's moet u de parameteroptie voor een filter selecteren om een geparameteriseerde query te maken.   
  
-   Voor query's die zijn gebaseerd op een multidimensionale gegevensbron, zoals Microsoft SQL Server Analysis Services, kunt u opgeven of u een parameter wilt maken op basis van een filter dat u opgeeft in de ontwerpfunctie voor query's. 
  
##  <a name="bkmk_Manage_Parameters"></a> Parameters voor een gepubliceerd rapport beheren  
 Wanneer u een rapport ontwerpt, worden de rapportparameters opgeslagen in de rapportdefinitie. Wanneer u een rapport publiceert, worden de rapportparameters afzonderlijk van de rapportdefinitie opgeslagen en beheerd.  
  
 Voor een gepubliceerd rapport kunt u gebruikmaken van de volgende items:  
  
-   **Eigenschappen van rapportparameters.** Wijzig waarden voor rapportparameters rechtstreeks op de rapportserver, onafhankelijk van de rapportdefinitie.  
  
-   **Rapportabonnementen.** U kunt parameterwaarden opgeven om gegevens te filteren en rapporten te leveren via abonnementen. 
  
 Parametereigenschappen voor een gepubliceerd rapport blijven behouden als u de rapportdefinitie opnieuw publiceert. Als de rapportdefinitie opnieuw wordt gepubliceerd als hetzelfde rapport en de parameternamen en gegevenstypen gelijk blijven, blijven de instellingen voor de eigenschappen behouden. Als u parameters toevoegt aan of verwijdert uit de rapportdefinitie of als u de naam van een bestaande parameter wijzigt, moet u de parametereigenschappen in het gepubliceerde rapport mogelijk wijzigen.  
  
 Niet alle parameters kunnen in alle gevallen worden gewijzigd. Als een rapportparameter een standaardwaarde krijgt via een gegevenssetquery, kan die waarde niet worden gewijzigd voor een gepubliceerd rapport en niet worden gewijzigd op de rapportserver. De waarde die tijdens de uitvoering wordt gebruikt, wordt bepaald wanneer de query wordt uitgevoerd, of voor parameters op basis van een expressie wanneer de expressie wordt geëvalueerd.  
  
 Uitvoeringsopties voor een rapport kunnen invloed hebben op de verwerkingswijze van parameters. Een rapport dat wordt uitgevoerd als een momentopname kan niet gebruikmaken van parameters die worden opgehaald via een query, tenzij de query standaardwaarden voor de parameters bevat.  
  
##  <a name="bkmk_Parameters_Subscription"></a> Parameters voor een abonnement  
 U kunt een abonnement voor een rapport op aanvraag of voor een momentopname definiëren en opgeven welke parameterwaarden moeten worden gebruikt tijdens de verwerking van het abonnement.  
  
-   **Rapport op aanvraag.**  Voor een rapport op aanvraag kunt u een andere parameterwaarde opgeven dan de gepubliceerde waarde die voor elke parameter voor het rapport is vermeld. Stel bijvoorbeeld dat u een rapport Belservice hebt, waarmee op basis van de parameter *Periode* de klantenserviceaanvragen van de huidige dag, week of maand worden geretourneerd. Als de standaardwaarde van de parameterwaarde voor het rapport is ingesteld op **Vandaag**, kan er in uw abonnement een andere parameterwaarde worden gebruikt (zoals **Week** of **Maand**) om een rapport met week- of maandcijfers te produceren.  
  
## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
 
 
