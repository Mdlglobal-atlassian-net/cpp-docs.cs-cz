---
title: 'Sada záznamů: Filtrování záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212902"
---
# <a name="recordset-filtering-records-odbc"></a>Sada záznamů: Filtrování záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak filtrovat sadu záznamů tak, aby vybrala pouze konkrétní podmnožinu dostupných záznamů. Například můžete chtít vybrat pouze oddíly třídy pro konkrétní kurz, například MATH101. Filtr je podmínka vyhledávání definovaná obsahem klauzule **WHERE** jazyka SQL. Když rozhraní připojí k příkazu SQL sady záznamů, klauzule **WHERE** omezí výběr.

Filtr objektu sady záznamů je nutné vytvořit po vytvoření objektu, ale před voláním jeho členské funkce `Open` (nebo před voláním členské funkce `Requery` pro existující objekt recordset, jehož `Open` členské funkce již byla volána dříve).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Určení filtru pro objekt sady záznamů

1. Vytvořte nový objekt sady záznamů (nebo Připravte volání `Requery` pro existující objekt).

1. Nastavte hodnotu datového členu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) objektu.

   Filtr je řetězec zakončený hodnotou null, který obsahuje obsah klauzule **WHERE** jazyka SQL, ale ne klíčové slovo, **kde**. Například můžete použít:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Literální řetězec "MATH101" je zobrazen v jednoduchých uvozovkách. Ve specifikaci ODBC SQL jsou jednoduché uvozovky použity k označení řetězcového literálu znaků. V této situaci si projděte dokumentaci k ovladači rozhraní ODBC pro požadavky na quote v systému DBMS. Tato syntaxe je také popsána dále v blízkosti konce tohoto tématu.

1. Nastavte další možnosti, které potřebujete, například pořadí řazení, režim uzamčení nebo parametry. Zadání parametru je zvlášť užitečné. Informace o Parametrizace filtru naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Pro nový objekt (nebo `Requery` pro dříve otevřený objekt) volejte `Open`.

> [!TIP]
>  Použití parametrů v filtru je potenciálně nejúčinnější metodou pro načítání záznamů.

> [!TIP]
>  Filtry sady záznamů jsou užitečné pro [spojování](../../data/odbc/recordset-performing-a-join-odbc.md) tabulek a pro použití [parametrů](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na základě informací získaných nebo počítaných za běhu.

Sada záznamů vybere pouze ty záznamy, které splňují zadanou podmínku vyhledávání. Pokud například chcete zadat filtr kurzu popsaný výše (za předpokladu, že proměnná `strCourseID` aktuálně nastavená, například na "MATH101"), udělejte toto:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Sada záznamů obsahuje záznamy pro všechny oddíly třídy pro MATH101.

Všimněte si, jak byl řetězec filtru nastaven v předchozím příkladu, pomocí proměnné řetězce. Toto je typické použití. Ale Předpokládejme, že jste chtěli zadat hodnotu literálu 100 pro ID kurzu. Následující kód ukazuje, jak správně nastavit řetězec filtru s hodnotou literálu:

```
m_strFilter = "StudentID = '100'";   // correct
```

Všimněte si použití jednoduchých znaků uvozovek; Pokud nastavíte řetězec filtru přímo, řetězec filtru **není:**

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Výše uvedené quoty uvedené výše odpovídají specifikaci ODBC, ale některé systémy DBMS můžou vyžadovat jiné znaky uvozovek. Další informace najdete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním vlastního řetězce SQL do `Open`, neměli byste nastavit filtr, pokud má vlastní řetězec klauzuli **WHERE** . Další informace o přepsání výchozího SQL naleznete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
