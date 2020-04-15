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
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367020"
---
# <a name="recordset-filtering-records-odbc"></a>Sada záznamů: Filtrování záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje, jak filtrovat sadu záznamů tak, aby vybrala pouze určitou podmnožinu dostupných záznamů. Můžete například vybrat pouze oddíly třídpro určitý kurz, například MATH101. Filtr je podmínka hledání definovaná obsahem klauzule SQL **WHERE.** Když framework připojí k příkazu SQL sady záznamů, **klauzule WHERE** omezí výběr.

Po vytvoření objektu je nutné vytvořit filtr objektu sady `Open` záznamů, ale před voláním jeho členské funkce (nebo před voláním `Requery` členské funkce pro existující objekt sady záznamů, jehož `Open` členská funkce byla dříve volána).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Určení filtru pro objekt sady záznamů

1. Vytvořte nový objekt sady záznamů `Requery` (nebo se připravte na volání existujícího objektu).

1. Nastavte hodnotu [datového](../../mfc/reference/crecordset-class.md#m_strfilter) člena m_strFilter objektu.

   Filtr je řetězec ukončený nulou, který obsahuje obsah klauzule SQL **WHERE,** ale nikoli klíčové slovo **WHERE**. Například můžete použít:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Literál řetězec "MATH101" je zobrazen s jednoduchými uvozovkami výše. Ve specifikaci ODBC SQL se jednotlivé uvozovky používají k označení literálu řetězce znaků. V této situaci zkontrolujte v dokumentaci k ovladači ROZHRANÍ ODBC požadavky na kotaci systému DBMS. Tato syntaxe je také popsána dále na konci tohoto tématu.

1. Nastavte všechny další možnosti, které potřebujete, například pořadí řazení, režim uzamčení nebo parametry. Zadání parametru je zvláště užitečné. Informace o parametrizaci filtru naleznete v tématu [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Volání `Open` nového objektu `Requery` (nebo dříve otevřeného objektu).

> [!TIP]
> Použití parametrů ve filtru je potenciálně nejúčinnější metodou pro načítání záznamů.

> [!TIP]
> Filtry sady záznamů jsou užitečné pro [spojování](../../data/odbc/recordset-performing-a-join-odbc.md) tabulek a pro použití parametrů na základě informací [získaných](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) nebo vypočtených za běhu.

Sada záznamů vybere pouze ty záznamy, které splňují zadanou podmínku hledání. Chcete-li například zadat výše popsaný filtr `strCourseID` kurzu (za předpokladu, že proměnná aktuálně nastavená například "MATH101"), postupujte takto:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Sada záznamů obsahuje záznamy pro všechny oddíly tříd pro MATH101.

Všimněte si, jak byl filtrační řetězec nastaven ve výše uvedeném příkladu pomocí proměnné řetězce. Toto je typické použití. Ale předpokládejme, že jste chtěli zadat hodnotu literálu 100 pro ID kurzu. Následující kód ukazuje, jak správně nastavit řetězec filtru s hodnotou literálu:

```
m_strFilter = "StudentID = '100'";   // correct
```

Všimněte si použití jednoduchých uvozovek; Pokud nastavíte filtrační řetězec přímo, řetězec filtru **není**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Výše uvedená citace odpovídá specifikaci ROZHRANÍ ODBC, ale některé systémy DBMS mohou vyžadovat jiné znaky uvozovek. Další informace naleznete v [tématu SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC).](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

> [!NOTE]
> Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním `Open`vlastního řetězce SQL , neměli byste nastavovat filtr, pokud má vlastní řetězec klauzuli **WHERE.** Další informace o přepsání výchozího jazyka SQL naleznete v tématu [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC).](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
