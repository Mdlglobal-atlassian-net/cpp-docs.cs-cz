---
title: "Schéma (MFC Data Access) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76a38525f7fdf451d40f555d76d3557cbc155936
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="schema--mfc-data-access"></a>Schéma (Data MFC Access)
Schéma databáze popisuje aktuální struktura tabulky a zobrazení databáze v databázi. Obecně platí vygenerované průvodcem kód předpokládá, že nedojde ke změně schématu pro tabulku nebo tabulky přístup na sadu záznamů, ale databázové třídy můžete řešit některé změny schématu, jako je přidání, změna nebo odstranění nevázaných sloupců. Pokud se změní tabulky, je nutné ručně aktualizovat sadu záznamů pro tabulku a potom znovu zkompiluje vaší aplikace.  
  
 Můžete také doplnit kód generované v Průvodci jak nakládat s databází, jejichž schématu není znám zcela v době kompilace. Další informace najdete v tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům programování (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)