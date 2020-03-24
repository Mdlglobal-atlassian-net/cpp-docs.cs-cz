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
ms.openlocfilehash: 0eac4f47c3d00c34c1aadaef18202a95f831ad82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209090"
---
# <a name="schema--mfc-data-access"></a>Schéma (přístup k datům MFC)

Schéma databáze popisuje aktuální strukturu tabulek a zobrazení databáze v databázi. Obecně, kód vygenerovaný průvodcem předpokládá, že schéma tabulky nebo tabulek, ke kterým se přistupovalo sadou záznamů, se nezmění, ale třídy databáze mohou pracovat s některými změnami schématu, jako je například přidání, změna pořadí nebo odstranění nevázaných sloupců. Pokud se tabulka změní, je nutné ručně aktualizovat sadu záznamů pro tabulku a pak znovu zkompilovat aplikaci.

Můžete také doplnit kód vygenerovaný průvodcem pro práci s databází, jejíž schéma není zcela známo v době kompilace. Další informace naleznete v tématu [Sada záznamů: dynamické vazby datových sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Viz také

[Programování přístupu k datům (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)
