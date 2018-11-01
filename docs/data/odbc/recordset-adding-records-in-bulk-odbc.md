---
title: 'Sada záznamů: Hromadné přidávání záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: 5a6a627054cd2e90420ac66a9e56e570f29d281e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594659"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Sada záznamů: Hromadné přidávání záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

MFC [CRecordset](../../mfc/reference/crecordset-class.md) třída má nové optimalizace, které zvyšuje efektivitu při přidávání nových záznamů hromadné do tabulky.

> [!NOTE]
> Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Nová možnost pro *dwOptions* parametr [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) členskou funkci `optimizeBulkAdd`, zlepšuje výkon při přidávání více záznamů za sebou bez volání `Requery` nebo `Close`. Pouze pole, které jsou změny před první `Update` volání jsou označeny jako neaktualizovaní pro následné `AddNew` / `Update` volání.

Pokud používáte databázové třídy výhod `::SQLSetPos` rozhraní API ODBC funkce pro přidání, úpravy a odstranění záznamů, tato optimalizace je zbytečné.

Pokud je načtena knihovna kurzorů rozhraní ODBC nebo ovladač ODBC nepodporuje přidávání, úpravy a odstranění prostřednictvím `::SQLSetPos`, tyto optimalizace měl vylepšit hromadné přidání výkonu. Chcete-li na této optimalizace, nastavte *dwOptions* parametr `Open` volání pro sady záznamů pro následující:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)