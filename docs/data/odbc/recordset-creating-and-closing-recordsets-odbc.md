---
title: 'Sada záznamů: Vytváření a uzavírání sad záznamů (rozhraní ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 155b51debfb6eacd3cbdd3293875274ca2dc4ab5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212976"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Sada záznamů: Vytváření a uzavírání sad záznamů (rozhraní ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Chcete-li použít sadu záznamů, Sestavte objekt sady záznamů a poté zavolejte jeho `Open` členské funkce pro spuštění dotazu sady záznamů a výběr záznamů. Po dokončení práce se sadou záznamů zavřete a zničit objekt.

Toto téma vysvětluje:

- [Kdy a jak vytvořit objekt sady záznamů](#_core_creating_recordsets_at_run_time).

- [Kdy a jak můžete kvalifikovat chování sady záznamů pomocí Parametrizace, filtrování, řazení nebo uzamykání](#_core_setting_recordset_options).

- [Kdy a jak zavřít objekt sady záznamů](#_core_closing_a_recordset).

##  <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a>Vytváření sad záznamů v době běhu

Předtím, než můžete v programu vytvořit objekty sady záznamů, obvykle píšete třídy sady záznamů specifické pro aplikaci. Další informace o tomto předběžném kroku najdete v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Pokud potřebujete vybrat záznamy ze zdroje dat, otevřete dynamickou sadu nebo objekt snímku. Typ objektu, který se má vytvořit, závisí na tom, co je třeba udělat s daty v aplikaci a na tom, co váš ovladač rozhraní ODBC podporuje. Další informace naleznete v tématu [dynamická sada](../../data/odbc/dynaset.md) a [Snapshot](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Otevření sady záznamů

1. Vytvořte objekt třídy odvozené od `CRecordset`.

   Můžete vytvořit objekt na haldě nebo v bloku zásobníku funkce.

1. Volitelně můžete změnit výchozí chování sady záznamů. Dostupné možnosti naleznete v tématu [Nastavení možností sady záznamů](#_core_setting_recordset_options).

1. Zavolejte na [otevřenou](../../mfc/reference/crecordset-class.md#open) členskou funkci objektu.

V konstruktoru předejte ukazatel na objekt `CDatabase` nebo předejte hodnotu NULL pro použití dočasného databázového objektu, který se konstrukce vytvoří a otevře na základě připojovacího řetězce vráceného členskou funkcí [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) . Objekt `CDatabase` mohl být již připojen ke zdroji dat.

Volání `Open` používá SQL k výběru záznamů ze zdroje dat. První záznam vybraný (pokud existuje) je aktuální záznam. Hodnoty polí tohoto záznamu jsou uloženy v datových členech pole objektu sady záznamů. Pokud byly vybrány nějaké záznamy, členské funkce `IsBOF` i `IsEOF` vrátí hodnotu 0.

V [otevřeném](../../mfc/reference/crecordset-class.md#open) volání můžete:

- Určete, zda je sada záznamů sadou nebo snímkem. Sady záznamů se ve výchozím nastavení otevřou jako snímky. Nebo můžete zadat pouze dopředné sady záznamů, což umožňuje pouze posouvání v jednom okamžiku.

   Ve výchozím nastavení používá sada záznamů výchozí typ uložený v datovém členu `CRecordset` `m_nDefaultType`. Průvodci napíší kód pro inicializaci `m_nDefaultType` pro typ sady záznamů, který zvolíte v průvodci. Místo toho, abyste přijali toto výchozí nastavení, můžete nahradit jiný typ sady záznamů.

- Zadejte řetězec, který nahradí výchozí příkaz jazyka SQL **Select** , který tvoří konstrukce sady záznamů.

- Určete, zda je sada záznamů určena pouze pro čtení nebo pouze pro připojení. Sady záznamů umožňují ve výchozím nastavení plné aktualizace, ale můžete omezit to pouze na přidávání nových záznamů nebo můžete zakázat všechny aktualizace.

Následující příklad ukazuje, jak otevřít objekt snímku třídy `CStudentSet`, který je jen pro čtení, třída specifická pro aplikaci:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po volání `Open`použijte členské funkce a datové členy objektu pro práci se záznamy. V některých případech můžete chtít znovu spustit dotaz nebo aktualizovat sadu záznamů, aby zahrnovaly změny, ke kterým došlo ve zdroji dat. Další informace naleznete v tématu [Sada záznamů: dotazování sady záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  Řetězec připojení, který použijete během vývoje, nemusí být stejný řetězec připojení, který potřebují vaši uživatelé. Nápady týkající se generalizace vaší aplikace v tomto ohledu najdete v tématu [zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a>Nastavení možností sady záznamů

Po sestavení objektu sady záznamů, ale před voláním `Open` pro výběr záznamů, je vhodné nastavit některé možnosti pro řízení chování sady záznamů. Pro všechny sady záznamů můžete:

- Určete [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) , který omezí výběr záznamů.

- Zadejte pořadí [řazení](../../data/odbc/recordset-sorting-records-odbc.md) záznamů.

- Zadejte [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , abyste mohli vybírat záznamy pomocí informací získaných nebo počítaných za běhu.

Můžete také nastavit následující možnost, pokud jsou podmínky správné:

- Pokud je sada záznamů aktualizovatelná a podporuje možnosti zamykání, určete metodu [zamykání](../../data/odbc/recordset-locking-records-odbc.md) použitou pro aktualizace.

> [!NOTE]
>  Chcete-li ovlivnit výběr záznamů, je nutné nastavit tyto možnosti před voláním členské funkce `Open`.

##  <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a>Zavření sady záznamů

Po dokončení práce se sadou záznamů je nutné ji navrátit a uvolnit její paměť.

#### <a name="to-close-a-recordset"></a>Zavření sady záznamů

1. Zavolejte jeho členskou funkci [Close](../../mfc/reference/crecordset-class.md#close) .

1. Zničit objekt sady záznamů.

   Pokud jste ho deklarovali v bloku funkce, objekt je zničen automaticky, když se objekt dostane mimo rozsah. V opačném případě použijte operátor **Delete** .

`Close` uvolní popisovač `HSTMT` sady záznamů. Nezničí C++ objekt.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
