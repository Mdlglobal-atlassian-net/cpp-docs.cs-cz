---
title: 'Výměna polí záznamu: Jak funkce RFX pracuje | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 48cece77101a14efb827e48b53be2f5852df83ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094296"
---
# <a name="record-field-exchange-how-rfx-works"></a>Výměna polí záznamu: Jak funkce RFX pracuje
Toto téma vysvětluje proces RFX. Toto je rozšířené zahrnut tématu:  
  
-   [RFX a sady záznamů](#_core_rfx_and_the_recordset)  
  
-   [Proces RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od třídy `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné RFX je podobná RFX. Chcete-li pochopit rozdíly, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX a sady záznamů  
 Objekt sady záznamů pole datových členů dohromady, tvoří upravit vyrovnávací paměti, která obsahuje vybrané sloupce jeden záznam. Pokud sadu záznamů prvním otevření a má číst na první záznam, RFX naváže (partnerů) každý vybraný sloupec na adresu odpovídající pole datového člena. Pokud sada záznamů aktualizuje záznam, RFX zavolá rozhraní API ODBC funkce Odeslat SQL **aktualizace** nebo **vložit** příkaz do ovladače. RFX používá znalosti o pole datových členů k určení sloupců k zápisu.  
  
 Rozhraní framework zálohuje upravené vyrovnávací paměti v některých fázích, v případě potřeby ho můžete obnovit jeho obsah. RFX zálohuje vyrovnávací paměť pro úpravu před přidáním nového záznamu a před úpravou existující záznam. Obnoví vyrovnávací paměti pro úpravy v některých případech, například po **aktualizace** následující volání `AddNew`. Vyrovnávací paměť pro úpravu funkce nebude obnovena, pokud abandon nově změněného upravené vyrovnávací paměti, například přesun na jiný záznam před voláním **aktualizace**.  
  
 Kromě výměny dat mezi zdroji dat a sady záznamů pole datových členů, spravuje RFX vázané parametry. Při otevření sady záznamů jsou všechny parametry datových členů vázány v pořadí podle "?" zástupné symboly v příkazu SQL, `CRecordset::Open` vytvoří. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 Třídy sady záznamů přepsat z `DoFieldExchange` vykonává všechnu práci přesouvání dat v obou směrech. Jako výměna dialogových dat (DDX) potřebuje RFX informace o datové členy vaší třídy. Průvodce zápisem specifické sady záznamů provádění zajišťuje informace nezbytné k `DoFieldExchange` , na základě pole dat člena názvy a typy dat zadáte v průvodci.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Proces Exchange pole záznamu  
 Tato část popisuje posloupnost událostí RFX, protože je otevřen objekt sady záznamů a při přidávání, aktualizace a odstranění záznamů. V tabulce [pořadí z RFX Operations během sada záznamů otevřete](#_core_sequence_of_rfx_operations_during_recordset_open) tabulky a [pořadí operací RFX během posouvání](#_core_sequence_of_rfx_operations_during_scrolling) v tomto tématu zobrazit proces jako RFX procesy **přesunout**příkazu v sadě záznamů a RFX spravuje aktualizace. Během těchto procesů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je volána k provedení mnoha různých operací. **M_nOperation** členem data [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu určuje, jaké operace je požadována. Může být užitečné číst [sada záznamů: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) před čtením této materiálů.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: Počáteční vazba sloupců a parametry  
 Následující činnosti RFX jsou prováděny v pořadí uvedeném, při volání objektu sady záznamů [otevřete](../../mfc/reference/crecordset-class.md#open) – členská funkce:  
  
-   Pokud má sada záznamů parametry datových členů, zavolá rozhraní `DoFieldExchange` pro vazbu parametrů zástupných symbolů parametrů v řetězci příkazu SQL sady záznamů. Data závislá na zvoleném typu reprezentaci hodnoty parametru se používá pro každý zástupný symbol nalezen v **vyberte** příkaz. K tomu dochází po připravený příkaz jazyka SQL, ale před jeho spuštěním. Informace o přípravě dotazu najdete v tématu **:: SQLPrepare** funkce v ODBC *referenční informace pro programátory*.  
  
-   Volání framework `DoFieldExchange` podruhé k vytvoření vazby na vybraných sloupcích odpovídající pole datových členů v sadě záznamů. To vytváří objekt sady záznamů jako vyrovnávací paměť úprav obsahující sloupce na první záznam.  
  
-   Sada záznamů provede příkaz jazyka SQL a zdroj dat vybere první záznam. Záznam se sloupci jsou načteny do sady záznamů pole datových členů.  
  
 V následující tabulce jsou uvedeny sekvence operací RFX při otevření sady záznamů.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Posloupnost operací RFX při otevření sady záznamů  
  
|Tuto operaci|DoFieldExchange – operace|Operace databáze/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Otevřete sadu záznamů.|||  
||2. Vytvoření příkazu SQL.||  
|||3. Odešlete SQL.|  
||4. Vazba parametru datových členů.||  
||5. Pole datových členů vazbu na sloupce.||  
|||6. ODBC provádí přesunutí a výplní v datech.|  
||7. Oprava data pro jazyk C++.||  
  
 Sady záznamů pomocí rozhraní ODBC je připravené provádění umožňující rychlé opakování stejný příkaz jazyka SQL. Další informace o provádění připravené, najdete v části sada SDK ODBC *referenční informace pro programátory* v knihovně MSDN.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: posouvání  
 Při posouvání z jednoho záznamu do jiného volá framework `DoFieldExchange` k nahrazení hodnot členů pole dat, s hodnotami pro nový záznam.  
  
 Následující tabulka zobrazuje posloupnost operací RFX, když se uživatel přesune mezi záznamy.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Posloupnost operací RFX při posouvání  
  
|Tuto operaci|DoFieldExchange – operace|Operace databáze/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Volání `MoveNext` nebo jednoho z dalších funkcí Move.|||  
|||2. ODBC provádí přesunutí a výplní v datech.|  
||3. Oprava data pro jazyk C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: Přidání nové záznamy a úpravou existujících záznamů  
 Pokud přidáte nový záznam, sadu záznamů funguje jako vyrovnávací paměť úprav pro sestaví obsah novém záznamu. Stejně jako u přidání záznamů, zahrnují úpravy záznamů hodnoty sady záznamů pole datových členů. Z pohledu RFX sekvenci vypadá takto:  
  
1.  Volání do sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [upravit](../../mfc/reference/crecordset-class.md#edit) – členská funkce způsobí, že RFX uloží aktuální vyrovnávací paměti pro úpravy, takže ji můžete později obnovit.  
  
2.  `AddNew` nebo **upravit** připraví pole ve vyrovnávací paměti upravit, takže RFX může zjistit pole datových členů.  
  
     Vzhledem k tomu, že nový záznam nemá žádné předchozí hodnoty k porovnání s `AddNew` nastaví hodnotu pro každé pole datového člena **PSEUDO_NULL** hodnotu. Později při volání **aktualizace**, RFX porovná hodnotu datového člena s **PSEUDO_NULL** hodnotu. Pokud existuje rozdíl, byl nastaven datový člen. (**PSEUDO_NULL** není stejný jako sloupec záznam s hodnotou Null true ani jedna z těchto je stejný jako C++ **NULL**.)  
  
     Na rozdíl od **aktualizace** volání pro `AddNew`, **aktualizace** volání pro **upravit** porovnává hodnoty aktualizováno dříve uložené hodnoty, nikoli pomocí **PSEUDO_NULL**. Rozdíl je, že `AddNew` neobsahuje žádné dříve uložené hodnoty pro porovnání.  
  
3.  Nastavíte přímo hodnoty pole datových členů, jejichž hodnoty, které chcete upravit nebo vyplňovat na nový záznam. To může zahrnovat volání `SetFieldNull`.  
  
4.  Volání do [aktualizace](../../mfc/reference/crecordset-class.md#update) zkontroluje pole datových členů tak, jak je popsáno v kroku 2 (viz tabulka [pořadí operací RFX během posouvání](#_core_sequence_of_rfx_operations_during_scrolling)). Pokud žádný změnili, **aktualizace** vrátí hodnotu 0. Pokud se změnily některé pole datových členů, **aktualizace** připraví a provede SQL **vložit** příkaz, který obsahuje hodnoty pro všechny aktualizované pole v záznamu.  
  
5.  Pro `AddNew`, **aktualizace** ukončí obnovení dříve uložené hodnoty záznam, který byl aktuální před `AddNew` volání. Pro **upravit**, nová upravená hodnota zůstávají na svém místě.  
  
 V následující tabulce jsou uvedeny sekvence operací RFX při přidávání nového záznamu nebo upravit existující záznam.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Posloupnost operací RFX během AddNew a úpravy  
  
|Tuto operaci|DoFieldExchange – operace|Operace databáze/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Volání `AddNew` nebo **upravit**.|||  
||2. Zálohujte upravené vyrovnávací paměti.||  
||3. Pro `AddNew`, označte pole datových členů jako "čištění" a s hodnotou Null.||  
|4. Přiřadíte hodnoty záznamů pole datových členů.|||  
|5. Volání **aktualizace**.|||  
||6. Kontrola změněných polí.||  
||7. Sestavení SQL **vložit** příkaz pro `AddNew` nebo **aktualizace** příkaz pro **upravit**.||  
|||8. Odešlete SQL.|  
||9. Pro `AddNew`, obnovení je vyrovnávací paměť k jejímu obsahu zálohy. Pro **upravit**, odstranit zálohování.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX: Odstranění existující záznamy  
 Pokud odstraníte záznam, RFX nastaví všechna pole na **NULL** jako připomenutí, který je záznam odstraněn a musíte přesunout mimo něj. Nepotřebujete žádné jiné informace RFX pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)  
 [CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)