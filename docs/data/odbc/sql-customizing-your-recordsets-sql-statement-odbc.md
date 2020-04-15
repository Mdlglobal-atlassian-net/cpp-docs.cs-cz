---
title: 'SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374509"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)

Toto téma vysvětluje:

- Jak rozhraní framework ustaví příkaz SQL

- Jak přepsat příkaz SQL

> [!NOTE]
> Tyto informace platí pro třídy Knihovny MFC ODBC. Pokud pracujete s třídami MFC DAO, přečtěte si téma "Porovnání Microsoft Jet Database Engine SQL a ANSI SQL" v nápovědě DAO.

## <a name="sql-statement-construction"></a>Konstrukce příkazu SQL

Sada záznamů zakládá výběr záznamů především na příkazu SQL **SELECT.** Když deklarujete třídu pomocí průvodce, `GetDefaultSQL` zapíše přepsání verze členské funkce, `CAuthors`která vypadá přibližně takto (pro třídu sady záznamů s názvem ).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Ve výchozím nastavení vrátí toto přepsání název tabulky, který jste zadali průvodcem. V příkladu je název tabulky "AUTOŘI". Při pozdějším volání `Open` členské funkce sady `Open` záznamů vytvoří teč konečný příkaz **SELECT** formuláře:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

kde `table-name` je získán `GetDefaultSQL` `rfx-field-list` voláním a je získán `DoFieldExchange`z volání funkce RFX v . To je to, co získáte pro **příkaz SELECT,** pokud jej nenahradíte přepsáním verze za běhu, i když můžete také upravit výchozí příkaz s parametry nebo filtrem.

> [!NOTE]
> Pokud zadáte název sloupce, který obsahuje (nebo může obsahovat) mezery, musíte jej uzavřít do hranatých závorek. Například název "Jméno" by měl být "[Křestní jméno]".

Chcete-li přepsat výchozí příkaz **SELECT,** předejte **SELECT** při volání `Open`řetězec obsahující úplný příkaz SELECT . Místo vytváření vlastního výchozího řetězce používá sada záznamů zadávaný řetězec. Pokud příkaz nahrazení obsahuje klauzuli **WHERE,** nezadávejte filtr, `m_strFilter` protože byste pak měli dva příkazy filtru. Podobně pokud váš příkaz nahrazení obsahuje klauzuli **ORDER BY,** nezadávejte řazení, `m_strSort` takže nebudete mít dva příkazy řazení.

> [!NOTE]
> Pokud používáte literálové řetězce ve filtrech (nebo jiných částech příkazu SQL), bude pravděpodobně muset "citovat" (uzavřete v určených oddělovačů) takové řetězce s předponou dbms a literálpřím znak (nebo znaky).

Můžete také setkat se speciálními syntaktickými požadavky pro operace, jako jsou vnější spojení, v závislosti na vašem DBMS. Pomocí funkcí ROZHRANÍ ODBC získáte tyto informace z ovladače pro systém DBMS. Například volání `::SQLGetTypeInfo` pro konkrétní datový typ, například `SQL_VARCHAR`, chcete-li požádat o LITERAL_PREFIX a LITERAL_SUFFIX znaky. Pokud píšete kód nezávislý na databázi, naleznete [v dodatku C: SQL Gramatika](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) v [odkazu programátora ODBC pro](/sql/odbc/reference/odbc-programmer-s-reference) podrobné informace o syntaxi.

Objekt sady záznamů vytvoří příkaz SQL, který používá k výběru záznamů, pokud nepředáte vlastní příkaz SQL. Jak se to provádí, závisí především na hodnotě, kterou `Open` předáte v *parametru lpszSQL* členské funkce.

Obecná forma příkazu SQL **SELECT** je:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Jedním ze způsobů, jak přidat klíčové slovo **DISTINCT** do příkazu SQL sady záznamů, `DoFieldExchange`je vložit klíčové slovo do prvního volání funkce RFX . Příklad:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Tuto techniku používejte pouze se sadou záznamů otevřenou jen pro čtení.

## <a name="overriding-the-sql-statement"></a>Přepsání příkazu SQL

V následující tabulce jsou uvedeny možnosti parametru *lpszSQL* do `Open`. Případy v tabulce jsou vysvětleny v tabulce.

**Parametr lpszSQL a výsledný řetězec SQL**

|Obchodní případ|Co předáte v lpszSQL|Výsledný příkaz SELECT|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** název *tabulky*<br /><br /> `CRecordset::Open`volání `GetDefaultSQL` získat název tabulky. Výsledný řetězec je jedním z případů 2 až `GetDefaultSQL` 5, v závislosti na co vrátí.|
|2|Název tabulky|**SELECT** *rfx-field-list* **FROM** název *tabulky*<br /><br /> Seznam polí je převzat z příkazů `DoFieldExchange`RFX v . Pokud `m_strFilter` `m_strSort` a nejsou prázdné, přidá **doložky WHERE** a/nebo **ORDER BY.**|
|3\*|Úplné prohlášení **SELECT,** ale bez klauzule **WHERE** nebo **ORDER BY**|Jak se to přeneslo. Pokud `m_strFilter` `m_strSort` a nejsou prázdné, přidá **doložky WHERE** a/nebo **ORDER BY.**|
|4\*|Kompletní **příkaz SELECT** s klauzulí **WHERE** a/nebo **ORDER BY**|Jak se to přeneslo. `m_strFilter`a/nebo `m_strSort` musí zůstat prázdné, nebo jsou vytvořeny dva příkazy filtru a/nebo třídění.|
|5\*|Volání uložené procedury|Jak se to přeneslo.|

\*`m_nFields` musí být menší nebo roven počtu sloupců zadaným v příkazu **SELECT.** Datový typ každého sloupce zadaný v příkazu **SELECT** musí být stejný jako datový typ odpovídajícího výstupního sloupce RFX.

### <a name="case-1---lpszsql--null"></a>Případ 1 lpszSQL = NULL

Výběr sady záznamů závisí `GetDefaultSQL` na `CRecordset::Open` tom, co vrátí při volání. Případy 2 až 5 popisují možné řetězce.

### <a name="case-2---lpszsql--a-table-name"></a>Případ 2 lpszSQL = název tabulky

Sada záznamů používá výměnu pole záznamu (RFX) k vytvoření seznamu sloupců z názvů sloupců uvedených ve `DoFieldExchange`volání funkce RFX v přepsání třídy sady záznamů . Pokud jste použili průvodce k deklarování třídy sady záznamů, má tento případ stejný výsledek jako případ 1 (za předpokladu, že předáte stejný název tabulky, který jste zadali v průvodci). Pokud nepoužijete průvodce k napsání třídy, případ 2 je nejjednodušší způsob, jak vytvořit příkaz SQL.

Následující příklad vytvoří příkaz SQL, který vybírá záznamy z databázové aplikace knihovny MFC. Když framework volá `GetDefaultSQL` členská funkce, funkce vrátí název `SECTION`tabulky .

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Chcete-li získat názvy sloupců pro příkaz SQL `DoFieldExchange` **SELECT,** framework volá členská funkce.

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Po dokončení příkaz SQL vypadá takto:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Případ 3 lpszSQL = příkaz SELECT/FROM

Seznam sloupců zadáte ručně, nikoli se spoléháte na automatické sestavení rfx. Můžete to udělat, když:

- Chcete zadat klíčové slovo **DISTINCT** následující **SELECT**.

   Seznam sloupců by měl odpovídat názvům a typům `DoFieldExchange`sloupců ve stejném pořadí, v jakém jsou uvedeny v aplikaci .

- Máte důvod ručně načíst hodnoty sloupců `::SQLGetData` pomocí funkce ODBC, nikoli spoléhat na RFX pro vazbu a načtení sloupců za vás.

   Můžete například chtít přizpůsobit nové sloupce, které zákazník vaší aplikace přidal do databázových tabulek po distribuci aplikace. Je třeba přidat tyto další členy dat pole, které nebyly známy v době, kdy deklaroval třídu s průvodcem.

   Seznam sloupců by měl odpovídat názvům a typům `DoFieldExchange`sloupců ve stejném pořadí, v jakém jsou uvedeny v písmenu a), za nimiž následují názvy ručně vázaných sloupců. Další informace naleznete v [tématu Recordset: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Chcete spojit tabulky zadáním více tabulek v klauzuli **FROM.**

   Informace a příklad naleznete v tématu [Recordset: Provedení spojení (ODBC).](../../data/odbc/recordset-performing-a-join-odbc.md)

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Případ 4 lpszSQL = SELECT/FROM Plus KDE a/nebo OBJEDNÁVKA

Zadáte vše: seznam sloupců (na základě `DoFieldExchange`volání RFX v ), seznam tabulek a obsah **where** a/nebo **klauzule ORDER BY.** Pokud zadáte své klauzule **WHERE** a/nebo **ORDER** BY `m_strFilter` tímto `m_strSort`způsobem, nepoužívejte a/nebo .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Case 5 lpszSQL = volání uložené procedury

Pokud potřebujete volat předdefinovaný dotaz (například uloženou proceduru v databázi serveru Microsoft SQL Server), musíte napsat příkaz **CALL** v řetězci, který předáte *lpszSQL*. Průvodci nepodporují deklarování třídy sady záznamů pro volání předdefinovaného dotazu. Ne všechny předdefinované dotazy vrátí záznamy.

Pokud předdefinovaný dotaz nevrací záznamy, můžete `CDatabase` použít `ExecuteSQL` členská funkce přímo. Pro předdefinovaný dotaz, který vrací záznamy, musíte také ručně `DoFieldExchange` zapsat volání RFX pro všechny sloupce, které procedura vrátí. RFX volání musí být ve stejném pořadí a vrátit stejné typy jako předdefinovaný dotaz. Další informace naleznete v [tématu Recordset: Deklarování třídy pro předdefinovaný dotaz (ODBC).](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

## <a name="see-also"></a>Viz také

[SQL: Datové typy SQL a C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
