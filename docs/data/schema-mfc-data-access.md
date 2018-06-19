---
title: Schéma (MFC Data Access) | Microsoft Docs
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
ms.openlocfilehash: f7ba3e7b64a8c65678830593098ef658b3495c75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104695"
---
# <a name="schema--mfc-data-access"></a>Schéma (Data MFC Access)
Schéma databáze popisuje aktuální struktura tabulky a zobrazení databáze v databázi. Obecně platí vygenerované průvodcem kód předpokládá, že nedojde ke změně schématu pro tabulku nebo tabulky přístup na sadu záznamů, ale databázové třídy můžete řešit některé změny schématu, jako je přidání, změna nebo odstranění nevázaných sloupců. Pokud se změní tabulky, je nutné ručně aktualizovat sadu záznamů pro tabulku a potom znovu zkompiluje vaší aplikace.  
  
 Můžete také doplnit kód generované v Průvodci jak nakládat s databází, jejichž schématu není znám zcela v době kompilace. Další informace najdete v tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům programování (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)