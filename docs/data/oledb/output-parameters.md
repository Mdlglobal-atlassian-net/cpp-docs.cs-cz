---
title: Výstupní parametry
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
ms.openlocfilehash: ece626eb7fbecae9b90321ccc2569607897cf520
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209856"
---
# <a name="output-parameters"></a>Výstupní parametry

Volání uložené procedury je podobné spuštění příkazu jazyka SQL. Hlavním rozdílem je, že uložené procedury používají výstupní parametry (neboli "výstupy") a návratové hodnoty.

V následující uložené proceduře první '? ' je návratovou hodnotou (Phone) a druhým '? ' je vstupní parametr (Name):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Zadejte parametry in a out v mapě parametrů:

```cpp
BEGIN_PARAM_MAP(CMySProcAccessor)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()
```

Vaše aplikace musí zpracovat výstup vrácený z uložených procedur. Různí poskytovatelé OLE DB vracejí výstupní parametry a návratové hodnoty v různých časech během zpracování výsledků. Například poskytovatel Microsoft OLE DB pro SQL Server (SQLOLEDB) nedodá výstupní parametry a návratové kódy, dokud uživatel nenačte nebo zruší sady výsledků vrácené uloženou procedurou. Výstup se vrátí v posledním paketu TDS ze serveru.

## <a name="row-count"></a>Počet řádků

Použijete-li šablony příjemce OLE DB ke spuštění uložené procedury, která má dílčí parametry, počet řádků není nastaven, dokud nezavřete sadu řádků.

Například zvažte uloženou proceduru se sadou řádků a dílčím parametrem:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```

`@_rowcount` dílčí parametr oznamuje, kolik řádků bylo vráceno z testovací tabulky. Tato uložená procedura ale omezuje počet řádků na 50. Například pokud byly v testu 100 řádky, rowcount by byl 50 (protože tento kód načte pouze hlavní 50 řádky). Pokud byla v tabulce pouze 30 řádků, rowcount by byl 30. Nezapomeňte volat `Close` nebo `CloseAll`, abyste naplnili dílčí parametr před tím, než načtete jeho hodnotu.

## <a name="see-also"></a>Viz také

[Použití uložených procedur](../../data/oledb/using-stored-procedures.md)
