---
title: Voorbeelden van expressies in Power BI Report Builder
description: Expressies worden vaak gebruikt in gepagineerde rapporten van Power BI Report Builder voor het beheren van inhoud en de weergave van rapporten.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 48e81c91a4555b4c8ea847ddffb1413058bbb152
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/05/2020
ms.locfileid: "78921143"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Voorbeelden van expressies in Power BI Report Builder
Expressies worden vaak gebruikt in gepagineerde rapporten van Power BI Report Builder voor het beheren van inhoud en de weergave van rapporten. Expressies worden geschreven in Microsoft Visual Basic en kunnen gebruikmaken van ingebouwde functies, aangepaste code, rapport- en groepsvariabelen en door de gebruiker gedefinieerde variabelen. Expressies beginnen met een gelijkteken (=).   

Dit onderwerp bevat voorbeelden van expressies die kunnen worden gebruikt voor algemene taken in een rapport.  
  
-   [Visual Basic-functies](#VisualBasicFunctions) Voorbeelden van Visual Basic-functies voor datum, tekenreeks, conversie en voorwaardelijke Visual Basic-functies.  
  
-   [Rapportfuncties](#ReportFunctions) Voorbeelden van aggregaties en andere ingebouwde rapportfuncties.  
  
-   [Weergave van rapportgegevens](#AppearanceofReportData) Voorbeelden van het wijzigen van de weergave van een rapport.  
  
-   [Eigenschappen](#Properties) Voorbeelden van het instellen van eigenschappen van rapportitems voor het beheer van de opmaak of zichtbaarheid.  
  
-   [Parameters](#Parameters) Voorbeelden van het gebruik van parameters in een expressie.  
  
-   [Aangepaste Code](#CustomCode) Voorbeelden van ingesloten aangepaste code.  
  
Zie de onderwerpen onder [Expressies in Power BI Report Builder](report-builder-expressions.md) voor meer informatie over eenvoudige en complexe expressies, waar u expressies kunt gebruiken en de typen verwijzingen die u in een expressie kunt opnemen. 
  
## <a name="functions"></a>Functies  
 Veel expressies in een rapport bevatten functies. U kunt gegevens opmaken, logica toepassen en metagegevens van rapporten openen met behulp van deze functies. U kunt expressies schrijven die gebruikmaken van functies uit de Microsoft Visual Basic-runtime-bibliotheek en van de naamruimten `xref:System.Convert` en `xref:System.Math`. U kunt verwijzingen naar functies in aangepaste code toevoegen. U kunt ook de klassen van de Microsoft .NET Framework gebruiken, met inbegrip van `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic-functies  
 U kunt Visual Basic-functies gebruiken om de gegevens te bewerken die in tekstvakken worden weergegeven of die voor parameters, eigenschappen of andere elementen van het rapport worden gebruikt. Deze sectie bevat voorbeelden waarin sommige van deze functies worden gedemonstreerd. Zie [Visual Basic Runtime Library-leden](https://go.microsoft.com/fwlink/?LinkId=198941) op MSDN voor meer informatie.  
  
 Het .NET Framework biedt veel mogelijkheden voor aangepaste notaties, bijvoorbeeld voor specifieke datumnotaties. Zie [Typen notaties](/dotnet/standard/base-types/formatting-types) voor meer informatie.  
  
### <a name="math-functions"></a>Wiskundige functies  
  
-   De functie **Afronden** is handig om getallen af te ronden op het dichtstbijzijnde gehele getal. Met de volgende expressie wordt 1,3 afgerond op 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     U kunt ook een expressie schrijven waarin een waarde moet worden afgerond tot een veelvoud dat u opgeeft, vergelijkbaar met de functie **Afronden naar veelvoud** in Excel. Vermenigvuldig de waarde met een factor waarmee u een geheel getal krijgt, rond het getal af en deel het vervolgens door de dezelfde factor. Als u bijvoorbeeld 1,3 wilt afronden naar het dichtstbijzijnde veelvoud van 0,2 (1,4), gebruikt u de volgende expressie:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Datumfuncties  
  
-   Met de functie **Vandaag** wordt de huidige datum opgegeven. Deze expressie kan worden gebruikt in een tekstvak om de datum op het rapport weer te geven, of in een parameter om gegevens te filteren op basis van de huidige datum.  
  
    ```  
    =Today()  
    ```  
  
-   Gebruik de functie **DateInterval** om een specifiek deel van een datum op te halen. Hier volgen enkele geldige **DateInterval**-parameters:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Met deze expressie wordt bijvoorbeeld het nummer van de week in het huidige jaar weergegeven voor de datum van vandaag:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   De functie **DateAdd** is handig voor het opgeven van een reeks datums op basis van één parameter. De volgende expressie voorziet in een datum zes maanden na de datum van een parameter met de naam *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   Met de functie **Jaar** wordt het jaar voor een bepaalde datum weergegeven. U kunt hiermee datums groeperen of het jaar weergeven als een label voor een reeks datums. Deze expressie voorziet in het jaar voor een bepaalde groep datums van verkooporders. De functie **Maand** en andere functies kunnen ook worden gebruikt voor het bewerken van datums. Zie de Visual Basic-documentatie voor meer informatie.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   U kunt functies combineren in een expressie voor het aanpassen van de notatie. Met de volgende expressie wordt de notatie van een datum in de vorm maand-dag-jaar in maand-week-weeknummer gewijzigd. Bijvoorbeeld van 12-23-2009 in december week 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Wanneer deze wordt gebruikt als een berekend veld in een gegevensset, kunt u deze expressie in een grafiek gebruiken voor het samenvoegen van waarden per week voor elke maand.  
  
-   Met de volgende expressie wordt de waarde SellStartDate opgemaakt als MMM-JJ. Het veld SellStartDate is een gegevenstype Datum/tijd.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   Met de volgende expressie wordt de waarde SellStartDate opgemaakt als dd-MM-jjjj. Het veld SellStartDate is een gegevenstype Datum/tijd.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   Met de functie **CDate** wordt de waarde naar een datum geconverteerd. Met de functie **Nu** wordt een datumwaarde met de huidige datum en tijd overeenkomstig uw systeem geretourneerd. Met **DateDiff** wordt een Lang-waarde geretourneerd die het aantal tijdsintervallen opgeeft tussen twee Datum-waarden.  
  
     In het volgende voorbeeld wordt de begindatum van het huidige jaar getoond  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   In het volgende voorbeeld wordt de begindatum van de vorige maand getoond op basis van de huidige maand.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   Met de volgende expressie worden de intervaljaren tussen SellStartDate en LastReceiptDate gegenereerd. Deze velden bevinden zich in twee verschillende gegevenssets, DataSet1 en DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   Met de functie **DatePart** wordt een Geheel getal-waarde met het opgegeven onderdeel van een bepaalde Datum-waarde geretourneerd. Met de volgende expressie wordt het jaar voor de eerste waarde van de SellStartDate in DataSet1 geretourneerd. Het bereik van de gegevensset wordt opgegeven, omdat er meerdere gegevenssets in het rapport zijn.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   Met de functie **DateSerial** wordt een Datum-waarde geretourneerd waarmee een opgegeven jaar, maand en dag wordt weergegeven, waarbij de tijdsgegevens zijn ingesteld op middernacht. In het volgende voorbeeld wordt de einddatum van de vorige maand getoond op basis van de huidige maand.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Met de volgende expressies worden verschillende datums weergegeven op basis van een parameterwaarde voor de datum die is geselecteerd door de gebruiker.  
  
|Beschrijving voorbeeld|Voorbeeld|  
|-------------------------|-------------|  
|Gisteren|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Twee dagen geleden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Eén maand geleden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Twee maanden geleden|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Eén jaar geleden|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Twee jaar geleden|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Tekenreeksfuncties  
  
-   Combineer meer dan één veld met behulp van de samenvoegingsoperatoren en Visual Basic-constanten. Met de volgende expressie worden twee velden geretourneerd, elk op een afzonderlijke regel in hetzelfde tekstvak:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Maak datums en getallen op in een tekenreeks met de functie **Opmaken**. Met de volgende expressie worden waarden van de parameters *StartDate* en *EndDate* in de lange datumnotatie:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Als het tekstvak alleen een datum of een getal bevat, moet u de eigenschap Opmaak van het tekstvak gebruiken om opmaak toe te passen in plaats van de functie **Opmaken** in het tekstvak.  
  
-   De functies **Right**, **Len**, en **InStr** zijn handig voor het retourneren van een subtekenreeks, bijvoorbeeld het inkorten van *DOMEIN*\\*gebruikersnaam* tot alleen de gebruikersnaam. Met de volgende expressie wordt het gedeelte geretourneerd van de tekenreeks aan de rechterkant van een backslash (\\) uit een parameter met de naam *Gebruiker*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     De volgende expressie resulteert in dezelfde waarde als de vorige, waarbij gebruik wordt gemaakt van de leden van de `xref:System.String`-klasse van het .NET Framework in plaats van de Visual Basic-functies:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Geef de geselecteerde waarden van een parameter met meerdere waarden weer. In het volgende voorbeeld worden met de functie **Samenvoegen** de geselecteerde waarden van de parameter *MySelection* in één tekenreeks samengevoegd die als een expressie kan worden ingesteld voor de waarde van een tekstvak in een rapportitem:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     Het volgende voorbeeld heeft hetzelfde effect als het bovenstaande voorbeeld, en geeft tevens een teksttekenreeks weer voorafgaand aan de lijst met geselecteerde waarden.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   De **Regex**-functies van .NET Framework `xref:System.Text.RegularExpressions` zijn nuttig voor het wijzigen van de opmaak van bestaande tekenreeksen, bijvoorbeeld, het opmaken van een telefoonnummer. Met de volgende expressie wordt met de functie **Vervangen** de notatie van een telefoonnummer van tien cijfers in een veld gewijzigd van *nnn*-*nnn*-*nnnn* in (*nnn*) *nnn*-*nnnn*:  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Controleer of de waarde voor Fields!Phone.Value geen extra spaties bevat en van het type `xref:System.String` is.  
  
### <a name="lookup"></a>Opzoeken  
  
-   Door een sleutelveld op te geven, kunt u met de functie **Opzoeken** een waarde uit een gegevensset ophalen voor een een-op-een-relatie, bijvoorbeeld, een sleutel-waarde-paar. Met de volgende expressie wordt de productnaam uit een gegevensset (Product) weergegeven, op basis van de overeen te komen product-id:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Door een sleutelveld op te geven, kunt u met de functie **LookupSet** een reeks waarden uit een gegevensset ophalen voor een een-op-veel-relatie. Een gebruiker kan bijvoorbeeld meerdere telefoonnummers hebben. In het volgende voorbeeld wordt ervan uitgegaan dat de gegevensset PhoneList een persoon-id en een telefoonnummer in elke rij bevat. Met **LookupSet** wordt een matrix met waarden geretourneerd. Met de volgende expressie worden de retourwaarden gecombineerd in één tekenreeks en wordt de lijst met telefoonnummers voor de persoon die is opgegeven door ContactID weergegeven:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Conversiefuncties  
 Met Visual Basic-functies kunt u een veld van het ene gegevenstype converteren naar een ander. Met conversiefuncties kunt u het standaardgegevenstype voor een veld converteren naar het gegevenstype dat nodig is voor berekeningen, of om tekst te combineren.  
  
-   Met de volgende expressie wordt de constante 500 naar het decimale type geconverteerd om deze te vergelijken met een Transact-SQL-geldgegevenstype in het veld Waarde voor een filterexpressie.  
  
    ```  
    =CDec(500)  
    ```  
  
-   Met de volgende expressie wordt het aantal waarden weergegeven dat is geselecteerd voor de parameter met meerdere waarden *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Beslissingsfuncties  
  
-   Met de **Iif**-functie wordt een van twee waarden geretourneerd, afhankelijk van of de expressie waar is of niet. Met de volgende expressie wordt met de **Iif**-functie een Booleaanse waarde **Waar** geretourneerd als de waarde `LineTotal` groter is dan 100. Anders wordt er **Onwaar** geretourneerd:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   U kunt meerdere **IIF**-functies (ook wel bekend als ' geneste IIFs') gebruiken voor een van drie waarden, afhankelijk van de waarde `PctComplete`. De volgende expressie kan in de opvulkleur van een tekstvak worden geplaatst om de achtergrondkleur te wijzigen, afhankelijk van de waarde in het tekstvak.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Bij waarden hoger dan of gelijk aan 10 wordt een groene achtergrond, bij waarden tussen 1 en 9 een blauwe achtergrond en bij waarden minder dan 1 een rode achtergrond weergegeven.  
  
-   Voor een andere manier om dezelfde functionaliteit te krijgen wordt de functie **Switch** gebruikt. De functie **Switch** is handig wanneer er drie of meer voorwaarden zijn om te worden getest. Met de functie **Switch** wordt de waarde geretourneerd die is gekoppeld aan de eerste expressie in een serie die in waar resulteert:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Bij waarden hoger dan of gelijk aan 10 wordt een groene achtergrond, bij waarden tussen 1 en 9 een blauwe achtergrond, bij een waarde gelijk aan 1 een gele achtergrond en bij de waarde 0 of minder een rode achtergrond weergegeven.  
  
-   Hiermee wordt de waarde van het veld `ImportantDate` getest en wordt er 'rood' geretourneerd als deze meer dan een week oud is, in het andere geval wordt 'blauw' geretourneerd. Deze expressie kan worden gebruikt voor het beheren van de eigenschap Kleur van een tekstvak in een rapportitem:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Hiermee wordt de waarde van het veld `PhoneNumber` getest en wordt 'Geen waarde' geretourneerd als deze **null** (**niets** in Visual Basic) is; in het andere geval wordt de waarde van het telefoonnummer geretourneerd. Deze expressie kan worden gebruikt voor het beheren van de waarde van een tekstvak in een rapportitem.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Hiermee wordt de waarde van het veld `Department` en wordt een subrapportnaam of een **null** (**niets** in Visual Basic) geretourneerd. Deze expressie kan worden gebruikt voor voorwaardelijke drillthrough subrapporten.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Hiermee wordt getest of een veldwaarde null is. Deze expressie kan worden gebruikt voor het beheren van de eigenschap **Verborgen** van een afbeelding in een rapportitem. In het volgende voorbeeld wordt de afbeelding die is opgegeven door het veld [LargePhoto] alleen weergegeven als de waarde van het veld niet null is.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   Met de functie **MonthName** wordt een tekenreekswaarde met de naam van de opgegeven maand geretourneerd. In het volgende voorbeeld wordt N.v.t. in het veld Maand getoond als het veld de waarde 0 bevat.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Rapportfuncties  
 In een expressie kunt u een verwijzing naar extra rapportfuncties toevoegen waarmee u gegevens in een rapport kunt bewerken. Deze sectie bevat voorbeelden van twee van deze functies. 
  
###  <a name="sum"></a><a name="Sum"></a> Som  
  
-   Met de functie **Som** kunt u het totaal van de waarden in een groep of gegevensgebied berekenen. Deze functie is handig in de koptekst of voettekst van een groep. Met de volgende expressie wordt de som van de gegevens in de groep of het gegevensgebied Order weergegeven:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   U kunt de functie **Som** ook gebruiken voor voorwaardelijke aggregatieberekeningen. Als bijvoorbeeld een gegevensset een veld bevat met de naam Staat met de mogelijke waarden Niet gestart, Gestart en Voltooid, wordt met de volgende expressie de geaggregeerde som voor alleen de waarde Voltooid berekend wanneer deze wordt geplaatst in de koptekst van een groep:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   Met de functie **RowNumber** wordt, wanneer deze wordt gebruikt in een tekstvak in een gegevensgebied, het nummer van de rij weergegeven voor elk exemplaar van het tekstvak waarin de expressie wordt weergegeven. Deze functie kan handig zijn voor het nummeren van rijen in een tabel. Het kan ook nuttig zijn voor complexere taken, zoals de voorziening van pagina-einden op basis van het aantal rijen. Zie [Pagina-einden](#PageBreaks) in dit onderwerp voor meer informatie.  
  
     Het bereik dat u opgeeft voor **RowNumber** bepaalt wanneer het hernummeren begint. Het trefwoord **Niets** geeft aan dat de functie begint met tellen op de eerste rij in de buitenste gegevensgebied. Gebruik de naam van het gegevensgebied als u wilt beginnen met tellen binnen geneste gegevensgebieden. Als u wilt gaan tellen binnen een groep, moet u de naam van de groep gebruiken.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Weergave van rapportgegevens  
 U kunt expressies gebruiken voor het wijzigen van de wijze waarop de gegevens in een rapport worden weergegeven. U kunt bijvoorbeeld de waarden van twee velden in een enkel tekstvak weergeven, informatie over het rapport weergeven of de wijze bewerken waarop de pagina-einden worden ingevoegd in het rapport.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Kop- en voetteksten  
 Bij het ontwerpen van een rapport wilt u misschien de naam van het rapport en het paginanummer in de voettekst van het rapport weergeven. Hiervoor kunt u de volgende expressies gebruiken:  
  
-   Met de volgende expressie worden de naam van het rapport en het tijdstip waarop het is uitgevoerd, weergegeven. Het kan worden geplaatst in een tekstvak, in de voettekst van het rapport of in de hoofdtekst van het rapport. De tijd is opgemaakt met de .NET Framework-opmaaktekenreeks voor korte datum:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   Met de volgende expressie wordt, wanneer deze wordt geplaatst in een tekstvak in de voettekst van een rapport, het paginanummer en het totale aantal pagina's in het rapport opgegeven:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 In de volgende voorbeelden wordt beschreven hoe u de eerste en laatste waarden van een pagina in de paginakoptekst kunt weergeven, vergelijkbaar met wat in een mappenlijst te vinden is. In het voorbeeld wordt ervan uitgegaan dat een gegevensgebied een tekstvak bevat met de naam `LastName`.  
  
-   Met de volgende expressie wordt, wanneer deze wordt geplaatst in een tekstvak aan de linkerkant van de koptekst van de pagina, de eerste waarde opgegeven van het tekstvak `LastName` op de pagina:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   Met de volgende expressie wordt, wanneer deze wordt geplaatst in een tekstvak aan de rechterkant van de koptekst van de pagina, de laatste waarde opgegeven van het tekstvak `LastName` op de pagina:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 In het volgende voorbeeld wordt beschreven hoe u het totaal van een pagina kunt weergeven. In het voorbeeld wordt ervan uitgegaan dat een gegevensgebied een tekstvak bevat met de naam `Cost`.  
  
-   Met de volgende expressie wordt, wanneer deze wordt geplaatst in de paginakoptekst of -voettekst, de som opgegeven van de waarden in het tekstvak `Cost` voor de pagina:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  U kunt in een paginakoptekst of -voettekst naar slechts één rapportitem verwijzen per expressie. Tevens kunt u naar de naam van het tekstvak verwijzen, maar niet de werkelijke gegevensexpressie in het tekstvak, in de expressies paginakoptekst en voettekst.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Pagina-einden  
 In sommige rapporten wilt u mogelijk een pagina-einde plaatsen aan het einde van een opgegeven aantal rijen in plaats van of in aanvulling op groepen of rapportitems. U doet dit door een groep te maken met de groeps- of detailrecords die u wilt gebruiken, een pagina-einde aan de groep toe te voegen en vervolgens een groepsexpressie toe te voegen om deze te groeperen op een opgegeven aantal rijen.  
  
-   Met de volgende expressie wordt, wanneer deze wordt geplaatst in de groepsexpressie, een nummer toegewezen aan elke reeks van 25 rijen. Als een pagina-einde voor de groep is gedefinieerd, resulteert deze expressie in een pagina-einde per 25 rijen.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Als u wilt toestaan dat de gebruiker een waarde instelt voor het aantal rijen per pagina, maakt u een parameter met de naam `RowsPerPage` en baseert u de groepsexpressie op de parameter, zoals wordt weergegeven in de volgende expressie:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Eigenschappen  
 Expressies worden niet alleen gebruikt om gegevens in tekstvakken weer te geven. Deze kunnen ook worden gebruikt om de manier te wijzigen waarop de eigenschappen op rapportitems worden toegepast. U kunt informatie over de stijl van een rapportitem wijzigen, of de zichtbaarheid ervan wijzigen.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Opmaak  
  
-   Met de volgende expressie wordt, wanneer deze wordt gebruikt in de eigenschap Kleur van een tekstvak, de kleur van de tekst gewijzigd, afhankelijk van de waarde van het veld `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     U kunt ook de Visual Basic-objectvariabele `Me` gebruiken. Deze variabele is een andere manier om naar de waarde van een tekstvak te verwijzen.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   Met de volgende expressie wordt, wanneer deze wordt gebruikt in de eigenschap BackgroundColor van een rapportitem in een gegevensgebied, de achtergrondkleur van elke rij afwisselend in lichtgroen en wit weergegeven:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Als u van een expressie voor een opgegeven bereik gebruikmaakt, moet u mogelijk de gegevensset voor de aggregatiefunctie aangeven:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Beschikbare kleuren zijn afkomstig van de .NET Framework KnownColor-opsomming.  
  
### <a name="chart-colors"></a>De kleuren van grafieken  
 Als u kleuren voor een vormgrafiek opgeeft, kunt u met aangepaste code de volgorde bepalen waarin de kleuren worden toegewezen aan gegevenspuntwaarden. Zo kunt u consistente kleuren gebruiken voor meerdere diagrammen die over dezelfde categoriegroepen beschikken. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Zichtbaarheid  
 U kunt items in een rapport weergeven en verbergen met behulp van de zichtbaarheidseigenschappen van het rapportitem. In een gegevensgebied zoals een tabel kunt u in eerste instantie detailrijen verbergen op basis van de waarde in een expressie.  
  
-   Met de volgende expressie worden, wanneer deze wordt gebruikt voor initiële zichtbaarheid van rijen met details in een groep, de detailrijen weergegeven voor alle verkopen van meer dan 90 procent in het veld `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   Met de volgende expressie wordt, wanneer deze wordt ingesteld in de eigenschap Verborgen van een tabel, de tabel alleen weergegeven als deze meer dan 12 rijen bevat:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   Met de volgende expressie wordt, wanneer deze wordt ingesteld in de eigenschap **Verborgen** van een kolom, de kolom alleen weergegeven als het veld in de rapportgegevensset voorkomt bij het ophalen van de gegevens uit de gegevensbron:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL's  
 U kunt URL's aanpassen met behulp van de rapportgegevens en ook voorwaardelijk bepalen of de URL's als actie voor een tekstvak worden toegevoegd.  
  
-   Met de volgende expressie wordt, wanneer deze wordt gebruikt als actie in een tekstvak, een aangepaste URL gegenereerd waarin het gegevenssetveld `EmployeeID` als URL-parameter wordt opgegeven.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   Met de volgende expressie wordt voorwaardelijk bepaald of er een URL in een tekstvak wordt toegevoegd. Deze expressie is afhankelijk van een parameter met de naam `IncludeURLs` waarmee een gebruiker kan bepalen of deze actieve URL's in een rapport wil opnemen. Deze expressie is ingesteld als actie voor een tekstvak. Als u de parameter op onwaar instelt en het rapport weergeeft, kunt u het Microsoft Excel-rapport zonder hyperlinks exporteren.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="report-data"></a><a name="ReportData"></a> Rapportgegevens  
 U kunt met expressies de gegevens bewerken die worden gebruikt in het rapport. U kunt verwijzen naar parameters en andere rapportgegevens. U kunt zelfs de query wijzigen die wordt gebruikt voor het ophalen van gegevens voor het rapport.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Parameters  
 U kunt expressies gebruiken in een parameter om de standaardwaarde voor de parameter te variëren. U kunt bijvoorbeeld met een parameter gegevens filteren op een bepaalde gebruiker op basis van de gebruiker-id die wordt gebruikt voor het uitvoeren van het rapport.  
  
-   Met de volgende expressie wordt, wanneer deze wordt gebruikt als standaardwaarde voor een parameter, de gebruiker-id opgehaald van de persoon die het rapport uitvoert:  
  
    ```  
    =User!UserID  
    ```  
  
-   Gebruik de globale verzameling **Parameters** om naar een parameter in een queryparameter, filterexpressie, tekstvak of ander gedeelte van het rapport te verwijzen. In dit voorbeeld wordt ervan uitgegaan dat de parameter *Afdeling* heet:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   U kunt parameters maken in een rapport, maar deze instellen op Verborgen. Wanneer het rapport op de rapportserver wordt uitgevoerd, wordt de parameter niet weergegeven in de werkbalk en kan de rapportlezer de standaardwaarde niet wijzigen. U kunt een verborgen parameter gebruiken die is ingesteld op een standaardwaarde als aangepaste constante. U kunt deze waarde gebruiken in elke expressie, met inbegrip van een expressie voor een veld. Met de volgende expressie wordt het veld dat is opgegeven door de standaardparameterwaarde voor de parameter met de naam *ParameterField* bepaald:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Aangepaste code  
 U kunt aangepaste code ingesloten in een rapport gebruiken. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Groepsvariabelen gebruiken voor aangepaste aggregatie  
 U kunt de waarde initialiseren voor een groepsvariabele die lokaal is voor het bereik van een bepaalde groep en vervolgens een verwijzing naar die variabele in expressies invoegen. Een van de manieren waarop u een groepsvariabele met aangepaste code kunt gebruiken, is het implementeren van een aangepaste aggregatie. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Null of nulwaarden onderdrukken tijdens de uitvoering  
 Sommige waarden in een expressie kunnen null of onbepaald opleveren tijdens de verwerkingstijd van een rapport. Dit kan leiden tot runtimefouten die resulteren in het bericht **#Error** dat in het tekstvak wordt weergegeven in plaats van de geëvalueerde expressie. De functie **IIF** is bijzonder gevoelig voor dit gedrag, omdat in tegenstelling tot een If-Then-Else-instructie elk onderdeel van de **IIF**-instructie (inclusief functieaanroepen) wordt geëvalueerd voordat deze wordt doorgegeven aan de routine waarmee wordt getest op **waar** of **onwaar**. Met de instructie `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` wordt het bericht **#Error** gegenereerd in het weergegeven rapport als `Fields!Sales.Value` NIETS is.  
  
 Ter voorkoming van deze situatie moet u een van de volgende strategieën gebruiken:  
  
-   Stel de teller in op 0 en de noemer op 1 als de waarde voor veld B 0 of onbepaald is; stel anders de teller in op de waarde voor veld A en de noemer op de waarde voor veld B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Gebruik een functie met aangepaste code om de waarde voor de expressie te retourneren. In het volgende voorbeeld wordt het percentageverschil geretourneerd tussen de huidige waarde en een vorige waarde. Dit kan worden gebruikt voor het berekenen van het verschil tussen twee opeenvolgende waarden, waarbij de verwerking plaatsvindt van het randgeval van de eerste vergelijking (wanneer er geen vorige waarde is) en gevallen waarin de vorige waarde of de huidige waarde **null** (**Niets** in Visual Basic) is.  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     De volgende expressie laat zien hoe u deze aangepaste code kunt aanroepen vanuit een tekstvak voor de container 'ColumnGroupByYear' (groep of gegevensgebied).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Dit helpt om runtime-uitzonderingen te voorkomen. U kunt nu een expressie gebruiken als `=IIF(Me.Value < 0, "red", "black")` in de eigenschap **Kleur** van het tekstvak om de weergegeven tekst voorwaardelijk te bepalen op basis van het criterium of waarden groter dan of kleiner dan 0 zijn.  
  
## <a name="next-steps"></a>Volgende stappen

- [Wat zijn gepagineerde rapporten in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
