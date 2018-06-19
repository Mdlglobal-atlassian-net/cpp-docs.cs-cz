---
title: 'SQL: Provedení přímá volání SQL (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2134fc41b604ffd659f9ee075abc9d462ff4f0db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093370"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Přímá volání SQL (ODBC)
Toto téma vysvětluje:  
  
-   Kdy použít přímé SQL volání.  
  
-   [Jak provedete přímé SQL volá ke zdroji dat](#_core_making_direct_sql_function_calls).  
  
> [!NOTE]
>  Tyto informace platí pro třídy MFC rozhraní ODBC. Pokud pracujete s tříd MFC rozhraní DAO, naleznete v tématu "Porovnání z Microsoft Jet databáze stroj SQL a ANSI SQL" v nápovědě rozhraní DAO.  
  
##  <a name="_core_when_to_call_sql_directly"></a> Kdy se má volat přímo SQL  
 Pokud chcete vytvořit nové tabulky, zrušit (odstranit) tabulky, měnit existující tabulky, vytvářejte indexy a provádět další funkce SQL, které změní [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md) schéma, musíte vydat příkaz SQL přímo ke zdroji dat pomocí databáze Definition Language (DDL). Pokud použijete průvodce k vytvoření sady záznamů pro tabulku (v době návrhu), můžete kterých sloupců tabulky představující v sadě záznamů. To není povoleno pro sloupce vy nebo jiný uživatel zdroje dat do tabulky později přidat, když je kompilovaná vašeho programu. Databázové třídy nepodporují DDL přímo, ale stále můžete napsat kód pro vazbu nový sloupec sady záznamů dynamicky za běhu. Informace o tom, jak provést tuto vazbu najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Databázového systému samotné můžete použít ke změně schématu nebo jiný nástroj, který umožňuje provádět operace DDL. Můžete taky volání funkcí rozhraní ODBC pro odesílání příkazů SQL, jako například volání předdefinovaný dotaz (uloženou proceduru), která nevrátí záznamy.  
  
##  <a name="_core_making_direct_sql_function_calls"></a> Vytvoření přímého volání funkce SQL  
 Můžete přímo spustit volání SQL pomocí [CDatabase – třída](../../mfc/reference/cdatabase-class.md) objektu. Nastavit váš příkaz SQL (obvykle ve `CString`) a předejte jej [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) členské funkce vaší `CDatabase` objektu. Používáte-li k odeslání příkazu SQL, který obvykle vrací záznamy volání funkcí rozhraní ODBC, můžete tyto záznamy jsou ignorovány.  
  
## <a name="see-also"></a>Viz také  
 [SQL](../../data/odbc/sql.md)