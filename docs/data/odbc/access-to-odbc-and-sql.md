---
title: Přístup k rozhraní ODBC a jazyku SQL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4635d482a08c486c1cf3259ae642fd82eb4bae82
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055941"
---
# <a name="access-to-odbc-and-sql"></a>Přístup k rozhraní ODBC a jazyku SQL

Knihovny Microsoft Foundation Class zapouzdřuje mnoho volání Windows API a stále umožňuje přímo volat jakékoli funkce rozhraní Windows API. Databázové třídy poskytují stejné flexibilitu z hlediska rozhraní API ODBC. Zatímco databázové třídy vás chrání před mnoho složitostí rozhraní ODBC, bude možné volat funkce rozhraní API ODBC přímo z libovolného místa v programu.

Obdobně databázové třídy vás chrání před nutností pracovat s příliš [SQL](../../data/odbc/sql.md), ale pokud chcete, můžete můžete přímo použít. Můžete přizpůsobit objekty sady záznamů předáním vlastní příkaz jazyka SQL (ani jeho části Nastavení výchozího příkazu) při otevření sady záznamů. Můžete provést také přímo pomocí volání SQL [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) členské funkce třídy [CDatabase](../../mfc/reference/cdatabase-class.md).

Další informace najdete v tématu [ODBC: volání rozhraní ODBC API funkce přímo](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) a [SQL: provádění přístupem SQL volání (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)