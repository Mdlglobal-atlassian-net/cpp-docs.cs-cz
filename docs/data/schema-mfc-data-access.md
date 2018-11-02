---
title: Schéma (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: 2dcfb5d22cf84fed7313686c943fbbd7c7ce1c84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512486"
---
# <a name="schema--mfc-data-access"></a>Schéma (přístup k datům MFC)

Schéma databáze popisuje aktuální struktura tabulky a zobrazení databáze v databázi. Obecně platí generované v Průvodci kód předpokládá, že nedojde ke změně schématu pro tabulku nebo tabulky přistupuje na sadu záznamů, ale databázové třídy můžete vyřešit některé změny schématu, jako je například přidání, změna uspořádání nebo odstranění nevázaných sloupců. Pokud tabulka změní, musíte ručně aktualizovat sadu záznamů tabulky a zkompilovat aplikaci znovu.

Můžete doplnit generované v Průvodci kód vypořádat s databází, jejichž schématu není úplně známý v době kompilace. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Viz také

[Přístup k datům programování knihovny MFC nebo ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)