---
title: 'Recordset: Vytváření a uzavírání sad záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 5d5dae5bc766c0cfc31b4fb76f7fe104be0dbd74
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041264"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Recordset: Vytváření a uzavírání sad záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Pokud chcete použít sadu záznamů, sestavte objekt sady záznamů a poté zavolejte jeho `Open` členskou funkci pro spuštění dotazu sadu záznamů a výběr záznamů. Po dokončení sady záznamů, zavřete a zničte objekt.

Toto téma vysvětluje:

- [Kdy a jak vytvořit objekt sady záznamů](#_core_creating_recordsets_at_run_time).

- [Kdy a jak se můžete kvalifikovat chování sady záznamů Parametrizace, filtrování, řazení nebo zamčením](#_core_setting_recordset_options).

- [Kdy a jak zavřít objekt sady záznamů](#_core_closing_a_recordset).

##  <a name="_core_creating_recordsets_at_run_time"></a> Vytvoření sady záznamů v době běhu

Než budete moct vytvořit objekty sady záznamů ve svém programu, obvykle zápisu třídy sady záznamů specifické pro aplikaci. Další informace o tomto předběžném kroku najdete v tématu [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Když je nutné vybrat záznamy ze zdroje dat, otevřete dynamická sada nebo snímek objektu. Typ objektu pro vytváření závisí na co je potřeba udělat s daty v aplikaci a na jaké ovladače rozhraní ODBC, podporuje. Další informace najdete v tématu [dynamická sada](../../data/odbc/dynaset.md) a [snímku](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Chcete-li otevřít sadu záznamů

1. Sestavte objekt vaše `CRecordset`-odvozené třídy.

   Můžete vytvořit objekt na haldě nebo funkce v zásobníku.

1. Volitelně můžete změňte výchozí chování sady záznamů. Dostupné možnosti najdete v tématu [nastavení možností sady záznamů](#_core_setting_recordset_options).

1. Volání objektu [otevřít](../../mfc/reference/crecordset-class.md#open) členskou funkci.

V konstruktoru, můžete předat ukazatel `CDatabase` objekt nebo hodnota NULL pro použití dočasného objektu databáze, které sestavují rozhraní a otevře založené na připojovací řetězec vrácený funkcí [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) členskou funkci. `CDatabase` Objekt může být již připojen ke zdroji dat.

Volání `Open` používá k výběru záznamů ze zdroje dat SQL. První záznam (pokud existuje) je aktuální záznam. Hodnoty polí tento záznam se ukládají v objektu pole datových členů. Pokud nebyly vybrány žádné záznamy, jak `IsBOF` a `IsEOF` členské funkce vrátí 0.

Ve vaší [otevřít](../../mfc/reference/crecordset-class.md#open) volání, můžete:

- Zadejte, jestli je sada záznamů dynamická sada nebo snímku. Ve výchozím nastavení otevírat jako snímky sady záznamů. Nebo můžete zadat dopředné sady záznamů, což umožňuje posouváním pouze vpřed, jeden záznam v čase.

   Ve výchozím nastavení používá sadu záznamů výchozí typ uložený do `CRecordset` datový člen `m_nDefaultType`. Průvodci napsat kód pro inicializaci `m_nDefaultType` typ sady záznamů, vyberte v průvodci. Místo přijímá toto výchozí nastavení, můžete použít jiný typ sady záznamů.

- Zadejte řetězec, která nahradí výchozí SQL **vyberte** příkaz, který vytvoří sadu záznamů.

- Určete, jestli sady záznamů je jen pro čtení nebo jen pro připojení. Sady záznamů povolit úplnou aktualizaci ve výchozím nastavení, ale můžete omezit, které k přidávání nových záznamů pouze nebo můžete zakázat všechny aktualizace.

Následující příklad ukazuje, jak otevřít snímek jen pro čtení objektu třídy `CStudentSet`, třídu specifické pro aplikaci:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po zavolání `Open`, můžete členské funkce a datovým členům objektu práci se záznamy. V některých případech můžete chtít spustit dotaz nebo aktualizovat sadu záznamů na změny, ke kterým došlo ve zdroji dat. Další informace najdete v tématu [sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  Připojovací řetězec, který můžete použít při vývoji nemusí být stejný řetězec připojení, který konečné uživatelé potřebují. Zobecňování vaší aplikace v tomto ohledu, naleznete v tématu [zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="_core_setting_recordset_options"></a> Nastavení možností sady záznamů

Po vytvoření objektu sady záznamů, ale před voláním `Open` pro výběr záznamů, můžete chtít nastavit několik možností, které řídí chování sady záznamů. Pro všechny sady záznamů můžete:

- Zadejte [filtr](../../data/odbc/recordset-filtering-records-odbc.md) omezit výběr záznamů.

- Zadejte [řazení](../../data/odbc/recordset-sorting-records-odbc.md) pořadí záznamů.

- Zadejte [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) tak můžete vybírat záznamy pomocí informací o získaných nebo vypočítat v době běhu.

Splnění podmínek, nastavit následující možnost:

- Pokud sada záznamů je aktualizovat a podporuje možnosti uzamčení, zadejte [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) metody používané pro aktualizace.

> [!NOTE]
>  Vliv na výběr záznamu, musíte nastavit tyto možnosti před voláním `Open` členskou funkci.

##  <a name="_core_closing_a_recordset"></a> Zavření sady záznamů

Po dokončení sady záznamů, musíte vyřadit a uvolnění paměti.

#### <a name="to-close-a-recordset"></a>Zavřete sadu záznamů

1. Volat jeho [Zavřít](../../mfc/reference/crecordset-class.md#close) členskou funkci.

1. Zničte objekt sady záznamů.

   Pokud jsou deklarovány v rámci zásobníku funkce, objekt je zničen automaticky, když objekt dostane mimo rozsah. Jinak použijte **odstranit** operátor.

`Close` sady záznamů se uvolní `HSTMT` zpracovat. Tato možnost nezničí objekt jazyka C++.

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Recordset: Přidání, aktualizace nebo odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)