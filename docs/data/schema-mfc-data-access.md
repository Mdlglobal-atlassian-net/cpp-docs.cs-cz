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
ms.openlocfilehash: 7ff1759203593cd556a91cbe17b93388488a2b07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091241"
---
# <a name="schema--mfc-data-access"></a>Schéma (přístup k datům MFC)

Schéma databáze popisuje aktuální struktura tabulky a zobrazení databáze v databázi. Obecně platí generované v Průvodci kód předpokládá, že nedojde ke změně schématu pro tabulku nebo tabulky přistupuje na sadu záznamů, ale databázové třídy můžete vyřešit některé změny schématu, jako je například přidání, změna uspořádání nebo odstranění nevázaných sloupců. Pokud tabulka změní, musíte ručně aktualizovat sadu záznamů tabulky a zkompilovat aplikaci znovu.  
  
Můžete doplnit generované v Průvodci kód vypořádat s databází, jejichž schématu není úplně známý v době kompilace. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Viz také  

[Přístup k datům programování knihovny MFC nebo ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)