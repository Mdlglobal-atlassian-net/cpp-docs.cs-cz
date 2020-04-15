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
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374502"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Přímá volání SQL (ODBC)

Toto téma vysvětluje:

- Kdy použít přímá volání SQL.

- [Jak provádět přímé volání SQL ke zdroji dat](#_core_making_direct_sql_function_calls).

> [!NOTE]
> Tyto informace platí pro třídy Knihovny MFC ODBC. Pokud pracujete s třídami MFC DAO, přečtěte si téma "Porovnání Microsoft Jet Database Engine SQL a ANSI SQL" v nápovědě DAO.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Kdy volat přímo SQL

Chcete-li vytvořit nové tabulky, přetáhnout (odstranit) tabulky, změnit existující tabulky, vytvořit indexy a provádět další funkce SQL, které mění schéma [zdroje dat (ODBC),](../../data/odbc/data-source-odbc.md) musíte vydat příkaz SQL přímo do zdroje dat pomocí jazyka DDL (Database Definition Language). Při použití průvodce k vytvoření sady záznamů pro tabulku (v době návrhu) můžete zvolit, které sloupce tabulky budou v sadě záznamů představovat. To neumožňuje sloupce vy nebo jiný uživatel zdroje dat přidat do tabulky později, po zkompilování programu. Třídy databáze nepodporují DDL přímo, ale stále můžete napsat kód svázat nový sloupec na sadu záznamů dynamicky, v době běhu. Informace o tom, jak provést tuto vazbu, naleznete v [tématu Recordset: Dynamicky vazebné datové sloupce (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Samotný systém DBMS můžete použít ke změně schématu nebo jiného nástroje, který umožňuje provádět funkce DDL. Můžete také použít volání funkce ROZHRANÍ ODBC pro odesílání příkazů SQL, jako je například volání předdefinovaného dotazu (uložená procedura), který nevrací záznamy.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Volání funkcí direct SQL

Můžete přímo spustit volání SQL pomocí [cdatabase třídy](../../mfc/reference/cdatabase-class.md) objektu. Nastavte řetězec příkazu `CString`SQL (obvykle v ) a předejte jej členské funkci [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) vašeho `CDatabase` objektu. Pokud používáte volání funkce ODBC k odeslání příkazu SQL, který obvykle vrací záznamy, budou záznamy ignorovány.

## <a name="see-also"></a>Viz také

[SQL](../../data/odbc/sql.md)
