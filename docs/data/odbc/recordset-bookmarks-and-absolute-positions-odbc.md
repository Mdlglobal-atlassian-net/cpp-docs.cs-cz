---
title: 'Recordset: Záložky a absolutní umístění (ODBC)'
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
ms.openlocfilehash: c4a223f01b25b4c321ccfb4f4c03c3c5241381ec
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023786"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Recordset: Záložky a absolutní umístění (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Během procházení záznamů, často potřebují způsob, jak vrácení konkrétního záznamu. Záložky a absolutní pozici záznamu zadejte tyto dvě metody.

Toto téma vysvětluje:

- [Použití záložek](#_core_bookmarks_in_mfc_odbc).

- [Jak nastavit aktuální záznam pomocí absolutní umístění](#_core_absolute_positions_in_mfc_odbc).

##  <a name="_core_bookmarks_in_mfc_odbc"></a> Záložky v rozhraní MFC ODBC

Záložka jednoznačně identifikuje záznam. Když si projdete sady záznamů, nelze vždy spoléhat na absolutní pozici záznam vzhledem k tomu může být odstraní záznamy ze sady záznamů. Spolehlivě udržovat přehled o pozici záznam se má používat své záložky. Třída `CRecordset` poskytuje členské funkce:

- Získání záložky aktuální záznam, abyste mohli uložit do proměnné ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Přesunutí rychle na daný záznam tak, že zadáte jeho záložky, kterou jste uložili dříve v proměnné ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

Následující příklad ukazuje, jak používat tyto členské funkce Označit aktuální záznam a později vrátit k ní:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Není potřeba extrahovat příslušný datový typ z [CDBVariant – třída](../../mfc/reference/cdbvariant-class.md) objektu. Přiřadí hodnotu s `GetBookmark` a vraťte se na tuto záložku pomocí `SetBookmark`.

> [!NOTE]
>  V závislosti na váš ovladač ODBC a typ sady záznamů nemusí být podporován záložky. Můžete také snadno zjistit, zda jsou podporovány záložky voláním [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Pokud jsou záložky podporovány, je nutné explicitně zvolit implementovat tak, že zadáte `CRecordset::useBookmarks` možnost [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) členskou funkci. Také byste měli zkontrolovat trvalost záložky po určitých operacích sady záznamů. Například pokud jste `Requery` sady záznamů záložky již nemusí být platný. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ke kontrole, jestli může bezpečně volat `SetBookmark`.

##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Absolutní umístění v rozhraní MFC ODBC

Kromě záložek třídy `CRecordset` vám umožní nastavit tak, že zadáte pořadového aktuální záznam. Tomu se říká absolutní pozici.

> [!NOTE]
>  Absolutní umístění není k dispozici sady záznamů s posouváním pouze vpřed. Další informace o pouze vpřed, naleznete v tématu [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md).

Chcete-li ukazatel aktuální záznam pomocí absolutní pozici, zavolejte [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Pokud předáte hodnotu `SetAbsolutePosition`, záznam odpovídající, že pořadí se stává aktuálním záznamem.

> [!NOTE]
>  Absolutní pozici záznamu je potenciálně nespolehlivým. Pokud uživatel odstraní záznamy ze sady záznamů, pořadové číslo pozice změny následujících záznamů. Záložky se doporučené metody pro přesouvání aktuální záznam. Další informace najdete v tématu [záložky v rozhraní MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Další informace o navigaci v sadě záznamů najdete v tématu [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)