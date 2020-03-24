---
title: Přístup k rozhraní ODBC a jazyku SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 0b590ce9309cbbe95285001cc5befe70a1d1961f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213327"
---
# <a name="access-to-odbc-and-sql"></a>Přístup k rozhraní ODBC a jazyku SQL

Knihovna Microsoft Foundation Class zapouzdřuje mnoho volání rozhraní API systému Windows a stále umožňuje volat libovolné funkce rozhraní API systému Windows přímo. Třídy databáze poskytují stejnou flexibilitu s ohledem na rozhraní ODBC API. I když třídy databáze chráníte z velké části složitosti rozhraní ODBC, můžete volat funkce rozhraní ODBC API přímo z libovolného místa v programu.

Podobně se třídy databází chrání před tím, než jsou v [SQL](../../data/odbc/sql.md)fungovat mnohem, ale pokud chcete, můžete SQL použít přímo. Můžete přizpůsobit objekty sady záznamů předáním vlastního příkazu SQL (nebo nastavením částí výchozího příkazu) při otevření sady záznamů. Můžete také volat SQL přímo pomocí členské funkce [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) třídy [CDatabase](../../mfc/reference/cdatabase-class.md).

Další informace najdete v tématu [rozhraní ODBC: přímé volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) a [SQL: vytváření přímých volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)
