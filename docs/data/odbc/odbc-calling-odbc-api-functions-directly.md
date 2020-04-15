---
title: 'ODBC: Přímé volání funkcí rozhraní API ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
ms.openlocfilehash: 208749438f40eef746a638dd12373397c426d454
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368671"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Přímé volání funkcí rozhraní API ODBC

Třídy databáze poskytují jednodušší rozhraní ke [zdroji dat](../../data/odbc/data-source-odbc.md) než rozhraní ODBC. V důsledku toho třídy nejsou zapouzdřit všechny ROZHRANÍ API ROZHRANÍ ODBC. Pro všechny funkce, které spadá mimo schopnosti tříd, musíte volat funkce rozhraní API ROZHRANÍ ODBC přímo. Například je nutné volat funkce katalogu `::SQLProcedures` `::SQLTables`ROZHRANÍ ODBC (`::SQLColumns`, , , a další) přímo.

> [!NOTE]
> Zdroje dat ROZHRANÍ ODBC jsou přístupné prostřednictvím tříd knihovny MFC ODBC, jak je popsáno v tomto tématu, nebo prostřednictvím tříd DAO (MFC Data Access Object).

Chcete-li volat funkci rozhraní API ROZHRANÍ ODBC přímo, musíte provést stejné kroky, které byste podnikli, pokud byste volání prováděli bez rozhraní. Jedná se o:

- Přidělit úložiště pro všechny výsledky volání vrátí.

- Předat rozhraní `HDBC` ODBC nebo `HSTMT` popisovač v závislosti na podpisu parametru funkce. Makro [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) slouží k načtení popisovače ODBC.

   Členské proměnné `CDatabase::m_hdbc` `CRecordset::m_hstmt` a jsou k dispozici, takže není nutné přidělit a inicializovat tyto sami.

- Možná volat další funkce ROZHRANÍ ODBC pro přípravu nebo sledování hlavního volání.

- Po dokončení navrátit úložiště.

Další informace o těchto krocích naleznete v sdk připojení [k otevřené databázi (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) v dokumentaci k msdn.

Kromě těchto kroků je třeba provést další kroky ke kontrole vrácených hodnot funkce, ujistěte se, že program nečeká na dokončení asynchronního volání a tak dále. Tyto poslední kroky můžete zjednodušit pomocí AFX_SQL_ASYNC a AFX_SQL_SYNC maker. Další informace naleznete v [tématu Makra a globální](../../mfc/reference/mfc-macros-and-globals.md) soubory v *referenční příručce knihovny MFC*.

## <a name="see-also"></a>Viz také

[Základy rozhraní ODBC](../../data/odbc/odbc-basics.md)
