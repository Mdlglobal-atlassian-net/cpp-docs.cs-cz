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
ms.openlocfilehash: 9a25c0fe4c1f08d376824fbc02211d22c7c14435
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212963"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Sada záznamů: Záložky a absolutní umístění (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Při procházení sady záznamů často potřebujete způsob, jak se vrátit na konkrétní záznam. Záložka a absolutní umístění záznamu poskytuje dvě takové metody.

Toto téma vysvětluje:

- [Jak používat záložky](#_core_bookmarks_in_mfc_odbc).

- [Nastavení aktuálního záznamu pomocí absolutních pozic](#_core_absolute_positions_in_mfc_odbc).

##  <a name="bookmarks-in-mfc-odbc"></a><a name="_core_bookmarks_in_mfc_odbc"></a>Záložky v knihovně MFC rozhraní ODBC

Záložka jednoznačně identifikuje záznam. Při procházení sady záznamů nelze vždy spoléhat na absolutní pozici záznamu, protože záznamy lze odstranit ze sady záznamů. Spolehlivý způsob, jak sledovat pozici záznamu, je použití jeho záložky. `CRecordset` třídy poskytuje členské funkce pro:

- Získání záložky aktuálního záznamu, takže ji můžete uložit v proměnné ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Rychlé přesunutí na daný záznam zadáním jeho záložky, kterou jste předtím uložili v proměnné ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

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

Nemusíte extrahovat základní datový typ z objektu [třídy CDBVariant –](../../mfc/reference/cdbvariant-class.md) . Přiřaďte hodnotu pomocí `GetBookmark` a vraťte se k této záložce pomocí `SetBookmark`.

> [!NOTE]
>  V závislosti na vašem typu ovladače a sady záznamů rozhraní ODBC nemusí být záložky podporovány. Můžete snadno určit, zda jsou záložky podporovány voláním [CRecordset:: CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Kromě toho, pokud jsou podporovány záložky, je nutné explicitně zvolit jejich implementaci zadáním možnosti `CRecordset::useBookmarks` do členské funkce [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) . Po určitých operacích sady záznamů byste také měli kontrolovat trvalost záložek. Pokud například `Requery` sadu záznamů, záložky již nemusí být platné. Voláním [CDatabase:: GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujete, jestli můžete bezpečně volat `SetBookmark`.

##  <a name="absolute-positions-in-mfc-odbc"></a><a name="_core_absolute_positions_in_mfc_odbc"></a>Absolutní pozice v rozhraní ODBC knihovny MFC

Kromě záložek `CRecordset` třídy vám umožní nastavit aktuální záznam zadáním pořadového čísla. Označuje se jako absolutní umístění.

> [!NOTE]
>  Absolutní umístění není k dispozici pro sady záznamů s pouze lomítkem. Další informace o sadách záznamů, které jsou jen pro čtení, naleznete v tématu [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md).

Chcete-li přesunout aktuální ukazatel záznamu pomocí absolutní pozice, zavolejte metodu [CRecordset:: SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Když předáte hodnotu do `SetAbsolutePosition`, bude záznam odpovídající danému pořadové pozici aktuální záznam.

> [!NOTE]
>  Absolutní pozice záznamu je potenciálně nespolehlivá. Pokud uživatel odstraní záznamy ze sady záznamů, pořadové místo všech pozdějších změn záznamu. Pro přesunutí aktuálního záznamu se doporučuje používat záložky. Další informace naleznete v tématu [záložky v knihovně MFC rozhraní ODBC](#_core_bookmarks_in_mfc_odbc).

Další informace o navigaci sady záznamů naleznete v tématu [Sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)
