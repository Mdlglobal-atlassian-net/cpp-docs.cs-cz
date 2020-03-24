---
title: 'Sada záznamů: Řazení záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 4bbe635cdda9152be6ba178b863147db93b7c706
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212742"
---
# <a name="recordset-sorting-records-odbc"></a>Sada záznamů: Řazení záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak sadu záznamů seřadit. Můžete určit jeden nebo více sloupců, na kterých se má řazení založit, a můžete zadat vzestupné nebo sestupné pořadí (**ASC** nebo **DESC**). U každého zadaného sloupce je výchozí hodnota **ASC** . Pokud například zadáte dva sloupce, záznamy jsou nejprve řazeny do prvního sloupce s názvem a následně do druhého sloupce s názvem. Klauzule **ORDER by** SQL definuje řazení. Když rozhraní připojí klauzuli **ORDER by** k dotazu SQL sady záznamů, klauzule řídí řazení výběru.

Pořadí řazení sady záznamů je nutné vytvořit po vytvoření objektu, ale před voláním jeho členské funkce `Open` (nebo před voláním členské funkce `Requery` pro existující objekt recordset, jehož `Open` členské funkce již byla volána dříve).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Určení pořadí řazení pro objekt sady záznamů

1. Vytvořte nový objekt sady záznamů (nebo Připravte volání `Requery` pro stávající).

1. Nastavte hodnotu datového členu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) objektu.

   Řazení je řetězec zakončený hodnotou null. Obsahuje obsah klauzule **ORDER by** , ale nejedná se **o klíčové slovo ORDER by**. Například můžete použít:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Nastavte další možnosti, které potřebujete, například filtr, režim uzamčení nebo parametry.

1. Pro nový objekt (nebo `Requery` pro existující objekt) volejte `Open`.

Vybrané záznamy jsou seřazené podle zadání. Pokud například chcete seřadit sadu záznamů studenta v sestupném pořadí podle příjmení, pak postupujte takto:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Sada záznamů obsahuje všechny záznamy studentů seřazené v sestupném pořadí (od do A) podle příjmení a pak podle křestního jména.

> [!NOTE]
>  Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním vlastního řetězce SQL do `Open`, nenastavte řazení, pokud vlastní řetězec obsahuje klauzuli **ORDER by** .

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
