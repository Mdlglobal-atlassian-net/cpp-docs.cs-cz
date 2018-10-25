---
title: 'Sada záznamů: Řazení záznamů (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 304911c771be630fd3df867c46f8b01a08ed9d59
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080439"
---
# <a name="recordset-sorting-records-odbc"></a>Sada záznamů: Řazení záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak řadit sady záznamů. Můžete určit jeden nebo více sloupců, na kterém chcete založit řazení, a můžete určit vzestupném nebo sestupném pořadí (**ASC** nebo **DESC**; **ASC** je výchozí nastavení) pro každý zadaný sloupec. Například pokud chcete zadat dva sloupce, položky jsou seřazeny nejprve na první sloupec s názvem a pak na druhý sloupec s názvem. SQL **klauzule ORDER BY** klauzule definuje řazení. Když připojí rozhraní **klauzule ORDER BY** dotazování klauzule SQL sady záznamů, klauzule ovládací prvky výběru uživatele řazení.

Po vytvoření objektu, ale před voláním, je nutné vytvořit sadu záznamů řazení jeho `Open` členskou funkci (nebo před voláním `Requery` členské funkce pro existující sady záznamů objekt, jehož `Open` členskou funkci bylo volá se dříve).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Chcete-li určit pořadí řazení pro objekt sady záznamů

1. Vytvořit nový objekt sady záznamů (nebo se připravte a volat `Requery` pro některý z existujících).

1. Nastavte hodnotu vlastnosti objektu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) datový člen.

   Řazení je řetězec zakončený hodnotou null. Obsahuje obsah **klauzule ORDER BY** klauzule, ale nikoli klíčové slovo **klauzule ORDER BY**. Například použijte:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Nastavte další možnosti, které potřebujete, jako je filtr, režim uzamčení nebo parametry.

1. Volání `Open` pro nový objekt (nebo `Requery` pro existující objekt).

Vybrané záznamy jsou řazeny podle zadání. Například k řazení sady záznamů studentů v sestupném pořadí podle příjmení a pak křestní jméno, postupujte takto:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Sada záznamů obsahuje všechny záznamy student, seřazeny v sestupném pořadí (Z až A) podle příjmení, pak podle křestního jména.

> [!NOTE]
>  Pokud budete chtít přepsat výchozí řetězec SQL sady záznamů předáním vlastní řetězec SQL `Open`, nenastavujte řazení, pokud má vlastní řetězec **klauzule ORDER BY** klauzuli.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)