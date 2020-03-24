---
title: 'Sada záznamů: Hromadné přidávání záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213015"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Sada záznamů: Hromadné přidávání záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Třída knihovny MFC [CRecordset](../../mfc/reference/crecordset-class.md) má novou optimalizaci, která zvyšuje efektivitu při hromadném přidávání nových záznamů do tabulky.

> [!NOTE]
> Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, přečtěte si téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Nová možnost pro parametr *dwoptionss* členské funkce [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) , `optimizeBulkAdd`, zlepšuje výkon při přidávání více záznamů po sobě, aniž by bylo nutné volat `Requery` nebo `Close`. Pouze ta pole, která jsou zapsaná před prvním `Update` volání, jsou označena jako nečistá pro následná `AddNew`/`Update` volání.

Pokud používáte databázové třídy k využití funkce `::SQLSetPos` ODBC API k přidávání, úpravám a odstraňování záznamů, tato optimalizace není nutná.

Pokud je načtena knihovna kurzorů rozhraní ODBC nebo ovladač ODBC nepodporuje přidávání, úpravy a odstraňování prostřednictvím `::SQLSetPos`, měla by tato optimalizace zvýšit výkon hromadného přidání. Pro zapnutí této optimalizace nastavte parametr *dwOptions* ve `Open` volání vaší sady záznamů do následujících možností:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
