---
title: 'Recordset: Filtrování záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 050524df840be28d661da89d04b685a44238f88c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041212"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset: Filtrování záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak filtrovat sadu záznamů tak, aby vybral jenom konkrétní podmnožinu dostupných záznamů. Například můžete chtít vybrat pouze oddíly třídy pro konkrétní kurz, jako je například MATH101. Filtr je podmínka vyhledávání definované obsah SQL **kde** klauzuli. Pokud systém připojí k příkazu SQL sady záznamů, **kde** klauzule omezí výběr.

Po vytvoření objektu, ale před voláním, je nutné vytvořit objekt sady záznamů filtr jeho `Open` členskou funkci (nebo před voláním `Requery` členské funkce pro existující sady záznamů objekt, jehož `Open` má členská funkce byla volána dříve).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Chcete-li zadat filtr pro objekt sady záznamů

1. Vytvořit nový objekt sady záznamů (nebo se připravte a volat `Requery` pro existující objekt).

1. Nastavte hodnotu vlastnosti objektu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datový člen.

   Tento filtr je řetězec zakončený hodnotou null, který obsahuje obsah SQL **kde** klauzule, ale nikoli klíčové slovo **kde**. Například použijte:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Řetězcový literál "MATH101" se zobrazí s jednoduchých uvozovek nahoře. Ve specifikaci ODBC SQL jednoduchých uvozovek a slouží k označení znak literálu. Zkontrolujte dokumentaci ovladače rozhraní ODBC pro použití apostrofů požadavky systému DBMS v této situaci. Tato syntaxe je také popsáno dále téměř na konci tohoto tématu.

1. Nastavte další možnosti, které potřebujete, jako je například pořadí řazení, režim uzamčení nebo parametry. Zadání parametru je obzvláště užitečné. Informace o parametrizaci filtru najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Volání `Open` pro nový objekt (nebo `Requery` dřív otevřených objektu).

> [!TIP]
>  Pomocí parametrů filtru je možná nejefektivnější metoda pro načtení záznamů.

> [!TIP]
>  Sada záznamů filtry jsou užitečné pro [propojení](../../data/odbc/recordset-performing-a-join-odbc.md) tabulky a pro použití [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na základě informací získaných nebo vypočítat v době běhu.

Sada záznamů vybere jen takové záznamy, které splňují zadané podmínky hledání. Například zadejte filtr kurzu popsané výše (za předpokladu, že proměnné `strCourseID` teď nastavené, například "MATH101"), postupujte takto:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Sada záznamů obsahuje záznamy pro všechny oddíly tříd pro MATH101.

Všimněte si, jak byl nastaven řetězec filtru v příkladu výše, pomocí proměnné řetězce. Toto je typická využití. Ale Předpokládejme, že chcete zadat hodnotu literálu 100 pro ID kurzu. Následující kód ukazuje, jak nastavit správně s literálovou hodnotou řetězec filtru:

```
m_strFilter = "StudentID = '100'";   // correct
```

Všimněte si použití jednoduché uvozovky znaků. Pokud nastavíte řetězec filtru přímo, je řetězec filtru **není**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Uvozovky u výše uvedené odpovídá specifikaci rozhraní ODBC, ale některé systémy DBMS můžou vyžadovat další znaky uvozovek. Další informace najdete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Pokud budete chtít přepsat výchozí řetězec SQL sady záznamů předáním vlastní řetězec SQL `Open`, by neměla nastavit filtr, pokud má váš vlastní řetězec **kde** klauzuli. Další informace o přepsání výchozího SQL najdete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Recordset: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Recordset: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Recordset: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)