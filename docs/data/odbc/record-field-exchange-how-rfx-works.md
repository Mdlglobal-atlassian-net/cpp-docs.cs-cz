---
title: 'Výměna polí záznamu: Jak funkce RFX pracuje'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367173"
---
# <a name="record-field-exchange-how-rfx-works"></a>Výměna polí záznamu: Jak funkce RFX pracuje

Toto téma vysvětluje proces RFX. Toto je pokročilé téma zahrnující:

- [RFX a sada záznamů](#_core_rfx_and_the_recordset)

- [Proces RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na třídy odvozené z, ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, je implementována výměna pole hromadného záznamu (Bulk RFX). Hromadné RFX je podobný RFX. Rozdíly najdete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX a sada záznamů

Členové dat pole objektu sady záznamů dohromady tvoří vyrovnávací paměť pro úpravy, která obsahuje vybrané sloupce jednoho záznamu. Při prvním otevření sady záznamů a chystá se číst první záznam, RFX váže (přidruží) každý vybraný sloupec na adresu příslušného datového člena pole. Když sada záznamů aktualizuje záznam, RFX volá funkce rozhraní API ROZHRANÍ ODBC k odeslání příkazu SQL **UPDATE** nebo **INSERT** ovladači. RFX používá své znalosti datových členů pole k určení sloupců k zápisu.

Rozhraní framework zálohy do vyrovnávací paměti úprav v určitých fázích, takže můžete obnovit jeho obsah v případě potřeby. RFX zálohuje vyrovnávací paměť pro úpravy před přidáním nového záznamu a před úpravou existujícího záznamu. V některých případech obnoví vyrovnávací paměť pro `Update` úpravy, například po následujícím `AddNew`volání . Vyrovnávací paměť pro úpravy není obnovena, pokud opustíte nově změněnou vyrovnávací `Update`paměť úprav například přesunutím na jiný záznam před voláním .

Kromě výměny dat mezi zdrojem dat a datovými členy sady záznamů spravuje RFX parametry vazby. Při otevření sady záznamů jsou všechny datové členy parametrů vázány v pořadí zástupných `CRecordset::Open` symbolů "?" v příkazu SQL, který se vytváří. Další informace naleznete v [tématu Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Přepsání třídy sady `DoFieldExchange` záznamů provádí veškerou práci a přesouvá data v obou směrech. Podobně jako dialogová výměna dat (DDX), RFX potřebuje informace o datových členech vaší třídy. Průvodce poskytuje potřebné informace tak, že za `DoFieldExchange` vás na základě názvů datových členů polí a datových typů, které zadáte pomocí průvodce, napíše implementaci specifickou pro sadu záznamů.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proces výměny pole záznamu

Tato část popisuje posloupnost událostí RFX jako objekt sady záznamů je otevřen a při přidávání, aktualizaci a odstraňování záznamů. Tabulka [Sekvence operací RFX během open recordset](#_core_sequence_of_rfx_operations_during_recordset_open) a tabulka [Sekvence operací RFX během posouvání](#_core_sequence_of_rfx_operations_during_scrolling) v `Move` tomto tématu zobrazit proces jako RFX zpracovává příkaz v sadě záznamů a jako RFX spravuje aktualizaci. Během těchto procesů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je volána k provedení mnoha různých operací. Datový `m_nOperation` člen objektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) určuje, která operace je požadována. Může být užitečné číst [recordset: Jak sady záznamů vyberte záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [Recordset: Jak sady záznamů aktualizovat záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) před čtením tohoto materiálu.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Počáteční vazba sloupců a parametrů

Následující aktivity RFX dojít v uvedeném pořadí, při volání objektu recordset je [Open](../../mfc/reference/crecordset-class.md#open) členská funkce:

- Pokud sada záznamů má členy dat `DoFieldExchange` parametrů, rozhraní framework volá svázat parametry s zástupnými symboly parametrů v řetězci příkazu SQL sady záznamů. Pro každý zástupný symbol nalezený v příkazu **SELECT** se použije reprezentace hodnoty parametru závislá na datovém typu. K tomu dochází po sql příkaz je připraven, ale před jeho spuštěním. Informace o přípravě výkazu naleznete v `::SQLPrepare` části Odkaz na *programátorod*rozhraní ODBC .

- Rozhraní Framework `DoFieldExchange` volá podruhé svázat hodnoty vybraných sloupců odpovídající členy dat pole v sadě záznamů. Tím se vytvoří objekt sady záznamů jako vyrovnávací paměť pro úpravy obsahující sloupce prvního záznamu.

- Sada záznamů provede příkaz SQL a zdroj dat vybere první záznam. Sloupce záznamu jsou načteny do datových členů pole sady záznamů.

V následující tabulce je uvedena posloupnost operací RFX při otevření sady záznamů.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Posloupnost operací RFX během otevření sady záznamů

|Vaše operace|Operace DoFieldExchange|Operace databáze/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Otevřete sadu záznamů.|||
||2. Vytvořte příkaz SQL.||
|||3. Pošlete SQL.|
||4. Bind parametr datových členů.||
||5. Spojte datové členy pole se sloupci.||
|||6. ROZHRANÍ ODBC provádí přesun a vyplňuje data.|
||7. Opravte data pro C++.||

Sady záznamů používají připravené spuštění rozhraní ODBC, aby bylo možné rychle se dotazovat pomocí stejného příkazu SQL. Další informace o připraveném spuštění naleznete v příručce ODBC SDK *Programmer's Reference* v knihovně MSDN.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Posouvání

Při posouvání z jednoho záznamu do `DoFieldExchange` druhého, rozhraní framework volá nahradit hodnoty dříve uložené v datových členech pole s hodnotami pro nový záznam.

V následující tabulce je uvedena posloupnost operací RFX, když se uživatel přesune ze záznamu na záznam.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Posloupnost operací RFX během posouvání

|Vaše operace|Operace DoFieldExchange|Operace databáze/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Volání nebo některou z dalších funkcí Move.|||
|||2. ROZHRANÍ ODBC provádí přesun a vyplňuje data.|
||3. Opravte data pro C++.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Přidání nových záznamů a úpravy existujících záznamů

Pokud přidáte nový záznam, sada záznamů funguje jako vyrovnávací paměť pro úpravy pro vytvoření obsahu nového záznamu. Stejně jako při přidávání záznamů zahrnuje úpravy záznamů změnu hodnot datových členů pole sady záznamů. Z hlediska RFX je sekvence následující:

1. Vaše volání sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [upravit](../../mfc/reference/crecordset-class.md#edit) členská funkce způsobí, že RFX uložit aktuální vyrovnávací paměti úprav, takže ji lze obnovit později.

1. `AddNew`nebo `Edit` připraví pole ve vyrovnávací paměti pro úpravy, aby RFX mohl detekovat změněné datové členy pole.

   Vzhledem k tomu, že nový záznam nemá `AddNew` žádné předchozí hodnoty, s kterými by bylo možné porovnat nové, nastaví hodnotu každého datového člena pole na hodnotu PSEUDO_NULL. Později při `Update`volání RFX porovná hodnotu každého datového člena s PSEUDO_NULL hodnotu. Pokud je rozdíl, datový člen byl nastaven. (PSEUDO_NULL není stejný jako sloupec záznamu s hodnotou True Null ani není stejný jako c++ null.)

   Na `Update` rozdíl `AddNew`od `Update` volání `Edit` pro volání porovná aktualizované hodnoty s dříve uložené hodnoty spíše než pomocí PSEUDO_NULL. Rozdíl je, `AddNew` že nemá žádné dříve uložené hodnoty pro porovnání.

1. Můžete přímo nastavit hodnoty datových členů polí, jejichž hodnoty chcete upravit nebo které chcete vyplnit pro nový záznam. To může `SetFieldNull`zahrnovat volání .

1. Volání [update](../../mfc/reference/crecordset-class.md#update) zkontroluje změněné členy dat pole, jak je popsáno v kroku 2 (viz tabulka [Posloupnost operací RFX během posouvání).](#_core_sequence_of_rfx_operations_during_scrolling) Pokud se žádná `Update` nezměnila, vrátí hodnotu 0. Pokud se některé členy `Update` dat pole změnily, připraví a provede příkaz SQL **INSERT,** který obsahuje hodnoty pro všechna aktualizovaná pole v záznamu.

1. For `AddNew` `Update` , končí obnovením dříve uložené hodnoty záznamu, který `AddNew` byl aktuální před voláním. Pro `Edit`nové upravené hodnoty zůstanou na svém místě.

V následující tabulce je uvedena posloupnost operací RFX při přidání nového záznamu nebo úpravě existujícího záznamu.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Posloupnost operací RFX během přidání Nové a úpravy

|Vaše operace|Operace DoFieldExchange|Operace databáze/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Volejte `Edit`nebo .|||
||2. Zálohujte vyrovnávací paměť pro úpravy.||
||3. `AddNew`Pro , označit členy dat pole jako "čisté" a Null.||
|4. Přiřaďte hodnoty datovým členům sady záznamů.|||
|5. `Update`Volejte .|||
||6. Zkontrolujte změněná pole.||
||7. Sestavení **INSERT** příkazu `AddNew` SQL INSERT `Edit`pro příkaz nebo příkaz **UPDATE** pro .||
|||8. Pošlete SQL.|
||9. `AddNew`V případě , obnovit upravit vyrovnávací paměti do jeho zálohovaný obsah. V `Edit`případě , odstraňte zálohu.||

### <a name="rfx-deleting-existing-records"></a>RFX: Odstranění existujících záznamů

Když odstraníte záznam, RFX nastaví všechna pole na HODNOTU NULL jako připomenutí, že záznam je odstraněn a musíte jej přesunout. Nepotřebujete žádné další informace o sekvencích RFX.

## <a name="see-also"></a>Viz také

[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Spotřebovávat rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
