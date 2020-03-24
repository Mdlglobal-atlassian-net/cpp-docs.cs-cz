---
title: 'SQL: Přímá volání SQL (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212625"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Přímá volání SQL (ODBC)

Toto téma vysvětluje:

- Kdy použít Přímá volání SQL.

- [Jak provedete Přímá volání SQL ke zdroji dat](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Tyto informace se vztahují na třídy knihovny MFC rozhraní ODBC. Pokud pracujete s třídami knihovny MFC DAO, přečtěte si téma "porovnání databáze Microsoft Jet Database Engine SQL a ANSI SQL" v nápovědě rozhraní DAO.

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Kdy přímo volat SQL

Chcete-li vytvořit nové tabulky, vyřadit (odstranit) tabulky, měnit existující tabulky, vytvářet indexy a provádět další funkce SQL, které mění schéma [zdroje dat (ODBC)](../../data/odbc/data-source-odbc.md) , je nutné vystavit příkaz SQL přímo ke zdroji dat pomocí jazyka DDL (Database Definition Language). Když použijete průvodce k vytvoření sady záznamů pro tabulku (v době návrhu), můžete vybrat, které sloupce tabulky se reprezentují v sadě záznamů. To neumožňuje, aby sloupce, které jste vy nebo jiný uživatel zdroje dat přidali do tabulky později, po zkompilování programu. Databázové třídy nepodporují DDL přímo, ale přesto můžete napsat kód pro svázání nového sloupce s vaší sadou záznamů v době běhu. Informace o tom, jak tuto vazbu provést, naleznete v tématu [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Můžete použít samotný systém DBMS pro změnu schématu nebo jiného nástroje, který umožňuje provádění funkcí DDL. Můžete také použít volání funkcí rozhraní ODBC pro odeslání příkazů jazyka SQL, například volání předdefinovaného dotazu (uložené procedury), který nevrací záznamy.

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Vytváření přímých volání funkcí SQL

Můžete přímo spustit volání SQL pomocí objektu [třídy CDatabase](../../mfc/reference/cdatabase-class.md) . Nastavte řetězec příkazu SQL (obvykle ve `CString`) a předejte ho do členské funkce [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) vašeho objektu `CDatabase`. Pokud používáte volání funkcí rozhraní ODBC k odeslání příkazu jazyka SQL, který obvykle vrací záznamy, záznamy budou ignorovány.

## <a name="see-also"></a>Viz také

[SQL](../../data/odbc/sql.md)
