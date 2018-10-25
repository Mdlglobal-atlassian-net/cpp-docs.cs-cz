---
title: 'ODBC: Volání rozhraní API ODBC přímo funguje | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 918ae8dd0249479cf8a99b1476e0beda5efc72f2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059802"
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Přímé volání funkcí rozhraní API ODBC

Databázové třídy poskytují jednodušší rozhraní [zdroj dat](../../data/odbc/data-source-odbc.md) než rozhraní ODBC. V důsledku toho třídy není zapouzdřovat všechny možnosti rozhraní API ODBC. Pro všechny funkce, která spadá mimo vlastnosti třídy je nutné volat funkce rozhraní API ODBC přímo. Například lze zavolat funkce katalogu rozhraní ODBC (`::SQLColumns`, `::SQLProcedures`, `::SQLTables`a další) přímo.

> [!NOTE]
>  Zdroje dat rozhraní ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu, nebo třídy knihovny MFC objekt DAO (Data Access).

Voláním funkce rozhraní API ODBC přímo, je nutné provést stejné kroky, které byste prováděli, pokud jste volali bez rozhraní framework. Tyto kroky:

- Přidělení úložiště pro výsledky, které vrátí volání.

- Předejte ODBC `HDBC` nebo `HSTMT` zpracovat, v závislosti na parametru signatury funkce. Použití [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) – makro pro načtení popisovače ODBC.

   Členské proměnné `CDatabase::m_hdbc` a `CRecordset::m_hstmt` jsou k dispozici, takže není potřeba přidělit a inicializovat sami.

- Například volání další funkce ODBC se připravit nebo zpracovat hlavní výzvou.

- Po dokončení zrušit přidělení úložiště.

Další informace o těchto krocích najdete v článku [připojení ODBC (Open Database)](/previous-versions/windows/desktop/ms710252) sady SDK v dokumentaci MSDN.

Kromě těchto kroků budete muset udělat dodatečné kroky, chcete-li zkontrolovat vrácené hodnoty funkce, ujistěte se, že váš program nečeká na asynchronní volání dokončí a tak dále. Poslední takto můžete zjednodušit pomocí AFX_SQL_ASYNC a AFX_SQL_SYNC makra. Další informace najdete v tématu [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *odkaz knihovny MFC*.

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)
