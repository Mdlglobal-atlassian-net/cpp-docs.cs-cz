---
title: 'Sada záznamů: Řazení záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366929"
---
# <a name="recordset-sorting-records-odbc"></a>Sada záznamů: Řazení záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje, jak seřadit sadu záznamů. Můžete určit jeden nebo více sloupců, na kterých má být řazení zakládáno, a můžete určit vzestupné nebo sestupné pořadí (**ASC** nebo **DESC**; **ASC** je výchozí) pro každý zadaný sloupec. Pokud například zadáte dva sloupce, záznamy se seřadí nejprve v prvním sloupci s názvem a potom na druhém s názvem sloupce. Klauzule SQL **ORDER BY** definuje řazení. Když rozhraní připojí **klauzuli ORDER BY** k dotazu SQL sady záznamů, klauzule řídí pořadí výběru.

Pořadí řazení sady záznamů je nutné vytvořit po vytvoření objektu, ale před voláním jeho `Open` členské funkce (nebo před voláním `Requery` členské funkce pro existující objekt sady záznamů, jehož `Open` členská funkce byla volána dříve).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Určení pořadí řazení pro objekt sady záznamů

1. Vytvořte nový objekt sady záznamů `Requery` (nebo se připravte na volání existujícího objektu).

1. Nastavte hodnotu [datového](../../mfc/reference/crecordset-class.md#m_strsort) člena m_strSort objektu.

   Řazení je řetězec ukončený nulou. Obsahuje obsah klauzule **ORDER BY,** nikoli však klíčové slovo **ORDER BY**. Například můžete použít:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Nastavte další možnosti, které potřebujete, například filtr, režim uzamčení nebo parametry.

1. Volání `Open` nového objektu `Requery` (nebo existujícího objektu).

Vybrané záznamy jsou seřazeny podle zadaných. Chcete-li například seřadit sadu záznamů studentů v sestupném pořadí podle příjmení, pak křestní jméno, postupujte takto:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Sada záznamů obsahuje všechny záznamy studentů seřazené v sestupném pořadí (Z až A) podle příjmení a poté podle křestního jména.

> [!NOTE]
> Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním `Open`vlastního řetězce SQL , nenastavujte řazení, pokud má vlastní řetězec klauzuli **ORDER BY.**

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
