---
title: 'Sada záznamů: Záložky a absolutní umístění (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 77c8bbaf7c0bc21dab62c3785364e72656287815
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367072"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Sada záznamů: Záložky a absolutní umístění (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Při procházení sadou záznamů často potřebujete způsob, jak se vrátit k určitému záznamu. Záložka záznamu a absolutní pozice poskytují dvě takové metody.

Toto téma vysvětluje:

- [Jak používat záložky](#_core_bookmarks_in_mfc_odbc).

- [Jak nastavit aktuální záznam pomocí absolutních pozic](#_core_absolute_positions_in_mfc_odbc).

## <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Záložky v knihovně MFC ODBC

Záložka jednoznačně identifikuje záznam. Při procházení sady záznamů se nelze vždy spoléhat na absolutní pozici záznamu, protože záznamy lze ze sady záznamů odstranit. Spolehlivý způsob, jak sledovat polohu záznamu, je použít jeho záložku. Třída `CRecordset` dodává členské funkce pro:

- Získání záložky aktuálního záznamu, takže ji můžete uložit do proměnné[(GetBookmark).](../../mfc/reference/crecordset-class.md#getbookmark)

- Rychlý přechod na daný záznam zadáním jeho záložky, kterou jste uložili dříve v proměnné[(SetBookmark).](../../mfc/reference/crecordset-class.md#setbookmark)

Následující příklad ukazuje, jak pomocí těchto členských funkcí označit aktuální záznam a později se k němu vrátit:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Není nutné extrahovat základní datový typ z objektu [TŘÍDY CDBVariant.](../../mfc/reference/cdbvariant-class.md) Přiřaďte `GetBookmark` hodnotu s a `SetBookmark`vraťte se k této záloze s .

> [!NOTE]
> V závislosti na ovladači ODBC a typu sady záznamů nemusí být záložky podporovány. Můžete snadno určit, zda jsou záložky podporovány voláním [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Kromě toho pokud záložky jsou podporovány, musíte explicitně `CRecordset::useBookmarks` zvolit jejich implementaci zadáním možnosti v [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) členské funkce. Měli byste také zkontrolovat trvalost záložek po určité operace sady záznamů. Pokud například `Requery` vytvoříte sadu záznamů, mohou již být záložky platné. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolovat, zda `SetBookmark`můžete bezpečně volat .

## <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Absolutní pozice v knihovně MFC ODBC

Kromě záložek `CRecordset` umožňuje třída nastavit aktuální záznam zadáním pořadí. Tomu se říká absolutní umístění.

> [!NOTE]
> Absolutní umístění není k dispozici u sad záznamů pouze pro předávání. Další informace o sadách záznamů pouze pro předávání naleznete v [tématu Recordset (ODBC).](../../data/odbc/recordset-odbc.md)

Chcete-li přesunout ukazatel aktuálního záznamu pomocí absolutní polohy, zavolejte [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Když předáte hodnotu `SetAbsolutePosition`, záznam odpovídající této řadové pozici se stane aktuálním záznamem.

> [!NOTE]
> Absolutní pozice záznamu je potenciálně nespolehlivá. Pokud uživatel odstraní záznamy ze sady záznamů, změní se ordinální pozice všech následných záznamů. Záložky jsou doporučenou metodou pro přesunutí aktuálního záznamu. Další informace naleznete [v tématu Záložky v knihovně MFC ROZHRANÍ ODBC](#_core_bookmarks_in_mfc_odbc).

Další informace o navigaci v sadě záznamů naleznete v [tématu Recordset: Scrolling (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)
