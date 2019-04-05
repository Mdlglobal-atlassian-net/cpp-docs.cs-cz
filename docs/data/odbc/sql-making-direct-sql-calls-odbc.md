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
ms.openlocfilehash: fd528e7abb713e4b3eb2bd5388a29958a1bb006c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024978"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Přímá volání SQL (ODBC)

Toto téma vysvětluje:

- Kdy použít SQL s přímým přístupem volá.

- [Jak vytvořit přímé SQL volá ke zdroji dat](#_core_making_direct_sql_function_calls).

> [!NOTE]
>  Tyto informace platí pro třídy knihovny MFC rozhraní ODBC. Pokud pracujete s tříd DAO knihovny MFC, naleznete v tématu "Porovnání z Microsoft Jet databáze modul SQL a ANSI SQL" v nápovědě k DAO.

##  <a name="_core_when_to_call_sql_directly"></a> Kdy se má volat přímo SQL

K vytvoření nových tabulek, drop (odstranit) tabulky, měnit existující tabulky, vytváření indexů a provádění dalších funkcí SQL, které se mění [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md) schéma, musíte vydat příkaz jazyka SQL přímo ke zdroji dat pomocí databáze Definice jazyka DDL. Když použijete průvodce k vytvoření sady záznamů pro tabulku (v době návrhu), můžete sloupce, které představují v sadě záznamů tabulky. To se nepovoluje pro sloupce, které vy nebo jiný uživatel zdroj dat přidat do tabulky později, až program byl zkompilován. Databázové třídy nepodporují DDL přímo, ale stále můžete napsat kód k vytvoření vazby nový sloupec sady záznamů dynamicky za běhu. Informace o tom, jak provést tuto vazbu, naleznete v tématu [sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Samotné DBMS můžete použít ke změně schématu nebo jiný nástroj, který umožňuje provádět funkce DDL. Volání funkcí rozhraní ODBC můžete také použít pro odesílání příkazů SQL, jako je například volání předdefinovaného dotazu (uložené procedury), která nevrací záznamy.

##  <a name="_core_making_direct_sql_function_calls"></a> Vytvoření přímého volání SQL – funkce

Můžete přímo spustit SQL pomocí volání [CDatabase – třída](../../mfc/reference/cdatabase-class.md) objektu. Nastavit řetězce příkaz jazyka SQL (obvykle v `CString`) a předat ho metodě [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) členskou funkci vaše `CDatabase` objektu. Používáte-li odeslat příkaz SQL, který se normálně vrací záznamy volání funkcí rozhraní ODBC, můžete tyto záznamy jsou ignorovány.

## <a name="see-also"></a>Viz také:

[SQL](../../data/odbc/sql.md)