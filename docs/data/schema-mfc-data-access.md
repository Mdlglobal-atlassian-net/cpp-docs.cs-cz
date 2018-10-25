---
title: Schéma (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 597b3870dbfc70b6e1ac392a45491ee0f1804c2f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055421"
---
# <a name="schema--mfc-data-access"></a>Schéma (přístup k datům MFC)

Schéma databáze popisuje aktuální struktura tabulky a zobrazení databáze v databázi. Obecně platí generované v Průvodci kód předpokládá, že nedojde ke změně schématu pro tabulku nebo tabulky přistupuje na sadu záznamů, ale databázové třídy můžete vyřešit některé změny schématu, jako je například přidání, změna uspořádání nebo odstranění nevázaných sloupců. Pokud tabulka změní, musíte ručně aktualizovat sadu záznamů tabulky a zkompilovat aplikaci znovu.

Můžete doplnit generované v Průvodci kód vypořádat s databází, jejichž schématu není úplně známý v době kompilace. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Viz také

[Přístup k datům programování knihovny MFC nebo ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)