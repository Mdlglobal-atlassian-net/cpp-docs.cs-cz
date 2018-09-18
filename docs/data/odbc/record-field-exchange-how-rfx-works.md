---
title: 'Výměna polí záznamu: Jak funkce RFX pracuje | Dokumentace Microsoftu'
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
ms.openlocfilehash: cf22876ee49538f9e9a162e5defe4abe693617e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037096"
---
# <a name="record-field-exchange-how-rfx-works"></a>Výměna polí záznamu: Jak funkce RFX pracuje

Toto téma vysvětluje proces RFX. To je moderní tématu, mezi které patří:  
  
- [RFX a sady záznamů](#_core_rfx_and_the_recordset)  
  
- [Proces RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Toto téma platí pro třídy odvozené od `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné funkce RFX je podobný RFX. Pokud chcete znát rozdíly, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX a sady záznamů  

Objekt sady záznamů pole datových členů, dohromady, tvoří vyrovnávací paměti, která obsahuje vybrané sloupce jeden záznam. Pokud sada záznamů je nejprve otevřen a je načíst první záznam, RFX vazby (přidruží) každý vybraný sloupec adresu datový člen příslušné pole. Pokud sada záznamů aktualizuje záznam, RFX volání funkcí rozhraní ODBC API k odeslání SQL **aktualizace** nebo **vložit** příkaz k ovladači. RFX používá k určení sloupců pro zápis znalosti o datové členy polí.  
  
Architektura zálohuje vyrovnávací paměť pro úpravu v některých fázích v případě potřeby ho mohli obnovit její obsah. RFX zálohuje vyrovnávací paměť pro úpravu před přidáním nového záznamu a před úpravou existující záznam. Obnoví vyrovnávací paměť pro úpravu v některých případech, například po `Update` následující volání `AddNew`. Vyrovnávací paměť pro úpravu není obnovena, pokud opustit nově změněného úpravy vyrovnávací paměti, například přesun na jiný záznam před voláním `Update`.  
  
Kromě výměna dat mezi zdrojem dat a sady záznamů pole datových členů, spravuje RFX vazby parametrů. Při otevření sady záznamů jsou svázány žádné parametry datových členů v pořadí podle "?" zástupné symboly v příkazu SQL, který `CRecordset::Open` vytvoří. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
Třídy sady záznamů přepsání `DoFieldExchange` vykonává všechnu práci, přesun dat v obou směrech. Jako je výměna dat dialogových oken (DDX) funkce RFX potřebuje informace o datové členy třídy. Průvodce nabízí potřebné informace napsáním specifické sady záznamů provádění `DoFieldExchange` , na základě dat pole názvy a datové typy členů zadáte v průvodci.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Proces Exchange pole záznamu  

Tato část popisuje posloupnost událostí RFX, protože je otevřen objekt sady záznamů a jak budete přidávat, aktualizovat a odstraňovat záznamy. V tabulce [pořadí z RFX operací během záznamů otevřít](#_core_sequence_of_rfx_operations_during_recordset_open) a v tabulce [pořadí operací RFX při posouvání](#_core_sequence_of_rfx_operations_during_scrolling) v tomto tématu ukazují proces jako RFX procesy `Move` v příkaz Sada záznamů a jak funkce RFX spravuje aktualizace. Během těchto procesů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je volána k provedení mnoha různých operací. `m_nOperation` Datový člen třídy [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objekt určuje, jaké operace je požadována. Možná pro vás bude užitečné přečíst [sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) předtím, než čtete tento materiál.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX: Počáteční vazeb sloupců a parametry  

Následující aktivity RFX dojde k, v uvedeném pořadí, pokud voláte objekt sady záznamů [otevřít](../../mfc/reference/crecordset-class.md#open) členské funkce:  
  
- Pokud sada záznamů obsahuje parametry datových členů, volá framework `DoFieldExchange` pro vazbu parametrů pro parametr zástupné symboly v řetězec příkazu SQL sady záznamů. Součástí dat závislé na typu reprezentace hodnoty parametru se používá pro každý zástupný symbol **vyberte** příkazu. K tomu dochází po připravený příkaz jazyka SQL, ale před jeho provedením. Informace o přípravě příkazu najdete v tématu `::SQLPrepare` funkce v rozhraní ODBC *referenční informace pro programátory*.  
  
- Rámec volá `DoFieldExchange` podruhé k vázání hodnot vybraných sloupců na odpovídající pole datových členů v sadě záznamů. Tím dojde k vytvoření objektu sady záznamů jako vyrovnávací paměť úprav obsahující sloupce první záznam.  
  
- Sada záznamů provádí příkaz jazyka SQL a zdroj dat vybere první záznam. Tento záznam sloupce se načtou do sady záznamů pole datových členů.  
  
V následující tabulce jsou uvedeny sekvence operací RFX při otevření sady záznamů.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Posloupnost operací RFX při otevření sady záznamů  
  
|Operaci|DoFieldExchange operace|Database/SQL operace|  
|--------------------|-------------------------------|-----------------------------|  
|1. Otevřít sadu záznamů.|||  
||2. Vytvoření příkazu SQL.||  
|||3. Odešlete SQL.|  
||4. Vytvořit vazbu parametru datové členy.||  
||5. Svázat pole datové členy sloupců.||  
|||6. Rozhraní ODBC nepodporuje přesun a vyplní údaje.|  
||7. Oprava data jazyka C++.||  
  
Sady záznamů pomocí připraveného provádění ODBC umožňující rychlé opakování stejný příkaz jazyka SQL. Další informace o provádění připravený, najdete v části sada SDK rozhraní ODBC *referenční informace pro programátory* v knihovně MSDN.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX: posouvání.  

Posunete-li z jednoho záznamu do jiného, volá framework `DoFieldExchange` k nahrazení hodnoty dříve uložené v datové členy pole s hodnotami pro nový záznam.  
  
Následující tabulka uvádí posloupnost operací RFX, když uživatel přesune ze záznamu.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Posloupnost operací RFX při posouvání  
  
|Operaci|DoFieldExchange operace|Database/SQL operace|  
|--------------------|-------------------------------|-----------------------------|  
|1. Volání `MoveNext` nebo jednu z dalších funkcí přesunout.|||  
|||2. Rozhraní ODBC nepodporuje přesun a vyplní údaje.|  
||3. Oprava data jazyka C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX: Přidávání nových záznamů a úpravou existujících záznamů  

Pokud chcete přidat nový záznam, záznamů funguje jako vyrovnávací paměť úprav k vytvoření obsahu nový záznam. Stejně jako u přidání záznamů, Hromadná úprava záznamů zahrnuje změnu hodnoty pole data členů sady záznamů. Z pohledu RFX sekvence je následujícím způsobem:  
  
1. Volání sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [upravit](../../mfc/reference/crecordset-class.md#edit) členská funkce způsobí, že RFX uloží aktuální vyrovnávací paměť pro úpravu, takže ji lze později obnovit.  
  
1. `AddNew` nebo `Edit` připraví pole ve vyrovnávací paměti pro úpravy, takže RFX může zjistit změny pole datových členů.  
  
     Vzhledem k tomu, že nový záznam nemá žádné předchozí hodnoty k porovnání s `AddNew` nastaví na hodnotu PSEUDO_NULL hodnotu každého pole datového člena. Později, když voláte `Update`, porovnává hodnotu datový člen s hodnotou PSEUDO_NULL RFX. Pokud existuje rozdíl, datový člen se nastavilo. (PSEUDO_NULL není stejný jako sloupec záznamů s hodnotou true Null ani jeden z následujících není stejná jako hodnota NULL C++.)  
  
     Na rozdíl od `Update` zavolat `AddNew`, `Update` zavolat `Edit` porovná aktualizované hodnoty se dříve uložené hodnoty spíš než PSEUDO_NULL. Rozdíl je, že `AddNew` neobsahuje žádné dříve uložené hodnoty pro porovnání.  
  
1. Přímo nastavíte hodnoty pole datových členů, jehož hodnoty, kterou chcete upravit nebo že chcete vyplnit nového záznamu. To může zahrnovat volání `SetFieldNull`.  
  
1. Volání [aktualizace](../../mfc/reference/crecordset-class.md#update) vyhledá pole datových členů, jak je popsáno v kroku 2 (viz tabulka [pořadí operací RFX při posouvání](#_core_sequence_of_rfx_operations_during_scrolling)). Pokud jste změnili none, `Update` vrátí hodnotu 0. Pokud se změnily některé pole datových členů, `Update` připraví a spouští SQL **vložit** příkaz, který obsahuje hodnoty pro všechny aktualizovanými poli v záznamu.  
  
1. Pro `AddNew`, `Update` dojde k závěru dříve uložené hodnoty záznamu, který byl aktuální před obnovením `AddNew` volání. Pro `Edit`, nové a upravené hodnoty zůstávají v místě.  
  
V následující tabulce jsou uvedeny sekvence operací RFX při přidání nového záznamu nebo upravit existující záznam.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Posloupnost operací RFX během AddNew a úpravy  
  
|Operaci|DoFieldExchange operace|Database/SQL operace|  
|--------------------|-------------------------------|-----------------------------|  
|1. Volání `AddNew` nebo `Edit`.|||  
||2. Proveďte zálohu vyrovnávací paměť pro úpravu.||  
||3. Pro `AddNew`, označte pole datové členy jako "clean" a s hodnotou Null.||  
|4. Přiřadíte hodnoty pole data členů sady záznamů.|||  
|5. Volání `Update`.|||  
||6. Kontrola změněných polí.||  
||7. Sestavení SQL **vložit** příkaz pro `AddNew` nebo **aktualizace** příkaz pro `Edit`.||  
|||8. Odešlete SQL.|  
||9. Pro `AddNew`, obnovíte jeho obsah zálohovaných vyrovnávací paměť pro úpravu. Pro `Edit`, odstranit zálohy.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX: Odstranění existujících záznamů.  

Při odstranění záznamu RFX nastaví všechna pole na hodnotu NULL jako připomenutí, že záznam odstranit a musí přesunout mimo něj. Není nutné nějakých jiných informací RFX pořadí.  
  
## <a name="see-also"></a>Viz také  

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)