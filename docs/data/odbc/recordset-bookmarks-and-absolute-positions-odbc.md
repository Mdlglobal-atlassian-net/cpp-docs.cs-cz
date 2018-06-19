---
title: 'Sada záznamů: Záložky a absolutní umístění (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
f1_keywords:
- SetAbsolutePosition
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e5e45d2f9dd942e76ccce4231e8280a142e66e56
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091314"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Sada záznamů: Záložky a absolutní umístění (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Při procházení sady záznamů, často potřebují způsob vrácení na konkrétní záznam. Záložky a absolutní umístění záznam poskytují takové dvě metody.  
  
 Toto téma vysvětluje:  
  
-   [Použití záložek](#_core_bookmarks_in_mfc_odbc).  
  
-   [Jak nastavit aktuální záznam pomocí absolutní umístění](#_core_absolute_positions_in_mfc_odbc).  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a> Záložky v knihovně MFC rozhraní ODBC  
 Záložka jednoznačně identifikuje záznam. Při procházení sady záznamů nelze vždy spoléhat na absolutní umístění záznamu vzhledem k tomu, že záznamy lze odstranit ze sady záznamů. Spolehlivě ke sledování pozici záznamu je použití jeho záložky. Třída `CRecordset` poskytuje členské funkce pro:  
  
-   Získání záložky na aktuální záznam, takže ho můžete uložit do proměnné ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).  
  
-   Rychlé přesunutí na daný záznam zadáním její záložky, kterou jste uložili dříve v proměnné ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).  
  
 Následující příklad ukazuje, jak používat tyto členské funkce k označení záznam na aktuální záznam a později vrátit:  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 Není potřeba extrahovat základní datový typ z [CDBVariant – třída](../../mfc/reference/cdbvariant-class.md) objektu. Přiřadit hodnotu s `GetBookmark` a vrátíte se na tuto záložku pomocí `SetBookmark`.  
  
> [!NOTE]
>  V závislosti na vašich ovladač ODBC a typ sady záznamů nemusí být podporován záložky. Můžete snadno zjistit, zda jsou podporovány záložky voláním [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Pokud jsou záložky podporovány, je nutné explicitně zvolit jejich implementaci zadáním **CRecordset::useBookmarks** možnost [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) – členská funkce. Také byste měli zkontrolovat zachování záložek po určité operace sady záznamů. Například pokud jste **Requery** sady záznamů, záložky může již nebude platný. Volání [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) zkontrolujte, zda můžete bezpečně volat `SetBookmark`.  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Absolutní umístění v knihovně MFC rozhraní ODBC  
 Kromě záložek třídy `CRecordset` vám umožní nastavit na aktuální záznam zadáním pořadové umístění. Tomu se říká absolutní umístění.  
  
> [!NOTE]
>  Absolutní umístění není k dispozici na dopředné sady záznamů. Další informace o dopředné sady záznamů najdete v tématu [záznamů (ODBC)](../../data/odbc/recordset-odbc.md).  
  
 Chcete-li přesunout ukazatel aktuální záznam pomocí absolutní umístění, volejte [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Pokud předáte hodnotu na `SetAbsolutePosition`, záznam odpovídající, pořadové číslo pozice stane aktuálním záznamem.  
  
> [!NOTE]
>  Absolutní umístění záznamu je potenciálně nespolehlivé. Pokud uživatel odstraní záznamy ze sady záznamů, změní se pořadová čísla všech následných záznamů. Záložky jsou uvedeny doporučené metody pro přesun na aktuální záznam. Další informace najdete v tématu [záložky v knihovně MFC rozhraní ODBC](#_core_bookmarks_in_mfc_odbc).  
  
 Další informace o navigaci v sadě záznamů najdete v tématu [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)