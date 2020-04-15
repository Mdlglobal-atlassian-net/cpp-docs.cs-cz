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
ms.openlocfilehash: 41b1c11e2c820b6e5777e1af426c5e1253ed5468
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367080"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Sada záznamů: Vytváření a uzavírání sad záznamů (rozhraní ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Chcete-li použít sadu záznamů, vytvořte objekt `Open` sady záznamů a pak zavolejte jeho člennou funkci ke spuštění dotazu sady záznamů a výběru záznamů. Po dokončení sady záznamů objekt zavřete a zničte.

Toto téma vysvětluje:

- [Kdy a jak vytvořit objekt sady záznamů](#_core_creating_recordsets_at_run_time).

- [Kdy a jak můžete kvalifikovat chování sady záznamů parametrizací, filtrováním, řazením nebo uzamčením](#_core_setting_recordset_options).

- [Kdy a jak zavřít objekt sady záznamů](#_core_closing_a_recordset).

## <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a>Vytváření sad záznamů za běhu

Před vytvořením objektů sady záznamů v programu obvykle zapisujete třídy sady záznamů specifické pro aplikaci. Další informace o tomto předběžném kroku naleznete [v tématu Přidání příjemce knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Otevřete objekt dynasady nebo snímku, když potřebujete vybrat záznamy ze zdroje dat. Typ objektu, který chcete vytvořit, závisí na tom, co je třeba provést s daty v aplikaci a na tom, co ovladač ODBC podporuje. Další informace naleznete [v tématu Dynaset](../../data/odbc/dynaset.md) a [Snapshot](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Otevření sady záznamů

1. Vytvořte objekt `CRecordset`vaší odvozené třídy.

   Objekt můžete vytvořit na haldě nebo na rámci zásobníku funkce.

1. Volitelně můžete změnit výchozí chování sady záznamů. Dostupné možnosti naleznete v [tématu Nastavení voleb sady záznamů](#_core_setting_recordset_options).

1. Volání objektu [Open](../../mfc/reference/crecordset-class.md#open) členské funkce.

V konstruktoru předaj `CDatabase` ukazatel na objekt nebo předaj hodnotu NULL, chcete-li použít dočasný databázový objekt, který framework vytvoří a otevře na základě připojovacího řetězce vráceného členskou funkcí [GetDefaultConnect.](../../mfc/reference/crecordset-class.md#getdefaultconnect) Objekt `CDatabase` je již pravděpodobně připojen ke zdroji dat.

Volání `Open` používá SQL k výběru záznamů ze zdroje dat. První vybraný záznam (pokud existuje) je aktuální záznam. Hodnoty polí tohoto záznamu jsou uloženy v datových členech objektu sady záznamů. Pokud byly vybrány nějaké `IsBOF` `IsEOF` záznamy, vrácené funkce i členské funkce 0.

Ve svém [otevřeném](../../mfc/reference/crecordset-class.md#open) hovoru můžete:

- Určete, zda je sada záznamů dynaset nebo snímek. Sady záznamů se ve výchozím nastavení otevírají jako snímky. Nebo můžete určit sadu záznamů pouze pro předávání, která umožňuje pouze posouvání vpřed, po jednom záznamu.

   Ve výchozím nastavení používá sada záznamů výchozí `CRecordset` typ `m_nDefaultType`uložený v datovém členu . Průvodci napíší kód `m_nDefaultType` pro inicializaci typu sady záznamů, který zvolíte v průvodci. Místo přijetí tohoto výchozího nastavení můžete nahradit jiný typ sady záznamů.

- Zadejte řetězec, který nahradí výchozí příkaz SQL **SELECT,** který vytvoří sada záznamů.

- Určete, zda je sada záznamů jen pro čtení nebo jen pro připojení. Sady záznamů umožňují úplnou aktualizaci ve výchozím nastavení, ale můžete ji omezit pouze na přidávání nových záznamů nebo můžete zakázat všechny aktualizace.

Následující příklad ukazuje, jak otevřít objekt snímku `CStudentSet`jen pro čtení třídy , třídy specifické pro aplikaci:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po volání `Open`použijte členské funkce a datové členy objektu ke zpracování se záznamy. V některých případech můžete chtít znovu zadat dotaz nebo aktualizovat sadu záznamů tak, aby zahrnovala změny, ke kterým došlo ve zdroji dat. Další informace naleznete v tématu [Recordset: Requerying a Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
> Řetězec připojení, který používáte během vývoje, nemusí být stejný řetězec připojení, který potřebují případní uživatelé. Nápady na zobecnění aplikace v tomto ohledu naleznete v [tématu Zdroj dat: Správa připojení (ODBC).](../../data/odbc/data-source-managing-connections-odbc.md)

## <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a>Nastavení možností sady záznamů

Po vytvoření objektu sady záznamů, `Open` ale před voláním k výběru záznamů, můžete nastavit některé možnosti pro řízení chování sady záznamů. U všech sad záznamů můžete:

- Určete [filtr,](../../data/odbc/recordset-filtering-records-odbc.md) chcete-li omezit výběr záznamu.

- Zadejte pořadí [řazení](../../data/odbc/recordset-sorting-records-odbc.md) záznamů.

- Zadejte [parametry,](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) abyste mohli vybírat záznamy pomocí informací získaných nebo vypočtených za běhu.

Můžete také nastavit následující možnost, pokud jsou podmínky správné:

- Pokud je sada záznamů aktualizovatelná a podporuje možnosti uzamčení, zadejte metodu [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) použitou pro aktualizace.

> [!NOTE]
> Chcete-li ovlivnit výběr záznamů, musíte tyto `Open` možnosti nastavit před voláním členské funkce.

## <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a>Uzavření sady záznamů

Po dokončení sady záznamů je nutné ji vyřadit a navrátit její paměť.

#### <a name="to-close-a-recordset"></a>Zavření sady záznamů

1. Zavolejte jeho [zavřít](../../mfc/reference/crecordset-class.md#close) členská funkce.

1. Zničte objekt sady záznamů.

   Pokud jste deklarovali v rámci zásobníku funkce, objekt je zničen automaticky, když objekt přejde mimo rozsah. V opačném případě použijte operátor **delete.**

`Close`uvolní `HSTMT` popisovač sady záznamů. Nezničí objekt Jazyka C++.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
