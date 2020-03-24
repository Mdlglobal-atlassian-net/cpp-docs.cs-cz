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
ms.openlocfilehash: 0661e61bceeedc0dd049ef47f5a0a0b71a8d82ed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213067"
---
# <a name="record-field-exchange-how-rfx-works"></a>Výměna polí záznamu: Jak funkce RFX pracuje

Toto téma vysvětluje proces RFX. Toto je pokročilé téma, které se týká:

- [RFX a sada záznamů](#_core_rfx_and_the_recordset)

- [Proces RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, je implementováno hromadné výměny pole záznamu (Bulk RFX). Hromadná RFX je podobná RFX. Pro pochopení rozdílů si přečtěte téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX a sada záznamů

Datové členy pole objektu sady záznamů společně tvoří vyrovnávací paměť pro úpravy, která obsahuje vybrané sloupce jednoho záznamu. Při prvním otevření sady záznamů a čtení prvního záznamu, RFX váže (přidruží) každý vybraný sloupec k adrese příslušného datového členu pole. Když sada záznamů aktualizuje záznam, RFX volá funkce rozhraní ODBC API pro odeslání příkazu SQL **Update** nebo příkazu **INSERT** do ovladače. RFX používá své znalosti datových členů pole k určení sloupců pro zápis.

Rozhraní zálohuje upravenou vyrovnávací paměť v určitých fázích, takže může v případě potřeby obnovit svůj obsah. RFX zálohuje upravenou vyrovnávací paměť před přidáním nového záznamu a před úpravou existujícího záznamu. V některých případech obnoví vyrovnávací paměť úprav, například po `Update` voláním následujících `AddNew`. Pokud zrušíte nově upravenou vyrovnávací paměť úprav, například přesunutí na jiný záznam před voláním `Update`, není obnovena vyrovnávací paměť.

Kromě výměny dat mezi zdrojem dat a datovými členy pole sady záznamů spravuje RFX parametry vazby. Při otevření sady záznamů jsou všechny datové členy parametrů vázány v pořadí zástupných symbolů "?" v příkazu jazyka SQL, který `CRecordset::Open` konstrukce. Další informace naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Přepsání `DoFieldExchange` třídy sady záznamů provede veškerou práci a přesouvá data v obou směrech. Podobně jako výměna dialogových dat (DDX) vyžaduje RFX informace o datových členech vaší třídy. Průvodce poskytuje potřebné informace napsáním implementace `DoFieldExchange` specifické pro sadu záznamů, na základě polí názvů datových členů a typů dat, které zadáte pomocí průvodce.

##  <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Proces výměny pole záznamu

Tato část popisuje sekvenci událostí RFX při otevření objektu sady záznamů a při přidávání, aktualizaci a odstraňování záznamů. Tabulková [sekvence operací RFX během otevírání sady záznamů](#_core_sequence_of_rfx_operations_during_recordset_open) a pořadí tabulek [operací RFX během posouvání](#_core_sequence_of_rfx_operations_during_scrolling) v tomto tématu ukazuje proces jako proces RFX zpracovává příkaz `Move` v sadě záznamů a jako RFX spravuje aktualizaci. Během těchto procesů je volána metoda [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) k provedení mnoha různých operací. Datový člen `m_nOperation` objektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) určuje, která operace se požaduje. Může být užitečné přečíst si [sadu záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) a [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) před čtením tohoto materiálu.

###  <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: počáteční vazba sloupců a parametrů

Následující aktivity RFX se objeví v zobrazeném pořadí při volání [otevřené](../../mfc/reference/crecordset-class.md#open) členské funkce objektu sady záznamů:

- Pokud sada záznamů obsahuje datové členy parametrů, rozhraní volá `DoFieldExchange`, aby navázala parametry zástupných symbolů parametrů v řetězci příkazu SQL sady záznamů. Hodnota parametru závislá na datovém typu se používá pro každý zástupný symbol, který najdete v příkazu **Select** . K tomu dochází po přípravě příkazu SQL, ale před jeho provedením. Informace o přípravě příkazu naleznete v tématu funkce `::SQLPrepare` v *referenci programátora*ODBC.

- Rozhraní volá `DoFieldExchange` podruhé k navázání hodnot vybraných sloupců na odpovídající pole datových členů v sadě záznamů. Tím se vytvoří objekt sady záznamů jako vyrovnávací paměť pro úpravy obsahující sloupce prvního záznamu.

- Sada záznamů provede příkaz SQL a zdroj dat vybere první záznam. Sloupce záznamu jsou načteny do datových členů pole sady záznamů.

Následující tabulka ukazuje posloupnost operací RFX při otevření sady záznamů.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Sekvence operací RFX při otevření sady záznamů

|Vaše operace|Operace DoFieldExchange|Operace Database/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Otevřete sadu záznamů.|||
||2. Sestavte příkaz SQL.||
|||3. odešlete SQL.|
||4. navázání datových členů parametrů||
||5. Vytvořte vazby datových členů pole na sloupce.||
|||6. rozhraní ODBC provede přesun a vyplní data.|
||7. Opravte data pro C++.||

Sady záznamů používají připravené spouštění rozhraní ODBC, které umožňuje rychlé dotazování se stejným příkazem SQL. Další informace o připraveném spuštění najdete v referenčních informacích o *programátorech* rozhraní ODBC SDK v knihovně MSDN.

###  <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: posouvání

Při posunu z jednoho záznamu na jiný volá rozhraní `DoFieldExchange`, aby nahradila hodnoty, které byly dříve uloženy v polích datových členů, s hodnotami nového záznamu.

V následující tabulce je uvedeno pořadí operací RFX, když se uživatel přesune ze záznamu na záznam.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Sekvence operací RFX během posouvání

|Vaše operace|Operace DoFieldExchange|Operace Database/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Zavolejte `MoveNext` nebo jednu z ostatních funkcí Move.|||
|||2. rozhraní ODBC provede přesun a vyplní data.|
||3. Opravte data pro C++.||

###  <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: přidávání nových záznamů a úprava stávajících záznamů

Pokud přidáte nový záznam, sada záznamů funguje jako vyrovnávací paměť úprav pro sestavení obsahu nového záznamu. Stejně jako u přidávání záznamů zahrnuje úpravy záznamů změny hodnot datových členů pole sady záznamů. V perspektivě RFX je sekvence následujícím způsobem:

1. Vaše volání metody [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [Edit](../../mfc/reference/crecordset-class.md#edit) člena sady záznamů způsobí, že RFX uloží aktuální upravenou vyrovnávací paměť, aby ji bylo možné obnovit později.

1. `AddNew` nebo `Edit` připraví pole ve vyrovnávací paměti, takže RFX dokáže detekovat změněné pole datových členů.

   Vzhledem k tomu, že nový záznam nemá žádné předchozí hodnoty pro porovnání nových hodnot s, `AddNew` nastaví hodnotu každého datového člena pole na hodnotu PSEUDO_NULL. Později při volání `Update`funkce RFX porovnává každou hodnotu datového člena s hodnotou PSEUDO_NULL. Pokud existuje rozdíl, byl nastaven datový člen. (PSEUDO_NULL není shodná se sloupcem záznamu s hodnotou true null, ani jedna z těchto hodnot není shodná s hodnotou C++ null.)

   Na rozdíl od `Update` volání `AddNew`, `Update` volání pro `Edit` porovná aktualizované hodnoty s dříve uloženými hodnotami namísto použití PSEUDO_NULL. Rozdílem je, že `AddNew` nemá žádné dříve uložené hodnoty pro porovnání.

1. Přímo nastavíte hodnoty datových členů pole, jejichž hodnoty chcete upravit nebo chcete vyplnit nový záznam. To může zahrnovat volání `SetFieldNull`.

1. Vaše volání [aktualizace](../../mfc/reference/crecordset-class.md#update) kontrol pro změněné pole datových členů, jak je popsáno v kroku 2 (viz [sekvence operace RFX během posouvání](#_core_sequence_of_rfx_operations_during_scrolling)). Pokud se žádná změna nezměnila, `Update` vrátí hodnotu 0. Pokud došlo ke změně některých datových členů, `Update` připraví a spustí příkaz pro **vložení** SQL, který obsahuje hodnoty všech aktualizovaných polí v záznamu.

1. Pro `AddNew``Update` končí obnovením dříve uložených hodnot záznamu, který byl aktuální před voláním `AddNew`. V případě `Edit`zůstanou nové upravované hodnoty na místě.

Následující tabulka ukazuje pořadí operací RFX při přidání nového záznamu nebo úpravě existujícího záznamu.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Sekvence operací RFX během metody AddNew a Edit

|Vaše operace|Operace DoFieldExchange|Operace Database/SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Zavolejte `AddNew` nebo `Edit`.|||
||2. Vytvořte zálohu vyrovnávací paměti pro úpravy.||
||3. pro `AddNew`označte datové členy pole jako "vyčistit" a hodnotu null.||
|4. přiřaďte hodnoty datovým členům pole sady záznamů.|||
|5. Zavolejte `Update`.|||
||6. Podívejte se na změněná pole.||
||7. Sestavte příkaz pro **vložení** SQL pro `AddNew` nebo příkaz **Update** pro `Edit`.||
|||8. odešlete SQL.|
||9. pro `AddNew`obnovte vyrovnávací paměť pro její zálohovaný obsah. Pro `Edit`odstraňte zálohu.||

### <a name="rfx-deleting-existing-records"></a>RFX: odstraňování stávajících záznamů

Při odstranění záznamu RFX nastaví všechna pole na hodnotu NULL jako připomenutí, že záznam je odstraněn a je nutné jej přesunout. Nepotřebujete žádné další informace o sekvenci RFX.

## <a name="see-also"></a>Viz také

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Využití MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::D oFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
