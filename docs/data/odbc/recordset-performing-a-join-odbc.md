---
title: "Sada záznamů: Provedení spojení (rozhraní ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4091cd8e60eed569782021c811f12af227e79673
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-performing-a-join-odbc"></a>Sada záznamů: Provedení spojení (rozhraní ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
## <a name="what-a-join-is"></a>Co je spojení  
 Operace spojení, běžné úlohy přístupu k datům, umožňuje pracovat s daty z více než jedné tabulky pomocí objektu jedné sady záznamů. Spojení dvou nebo více tabulek přinese sady záznamů, které může obsahovat sloupce z každé tabulky, ale zobrazí se jako jednu tabulku do vaší aplikace. Někdy spojení používá všechny sloupce ze všech tabulek, ale někdy SQL **vyberte** klauzule ve spojení se používá pouze některé sloupce z každé tabulky. Databázové třídy podporují jen pro čtení spojení, ale není možné spojení aktualizovat.  
  
 Chcete-li vybrat záznamy obsahující sloupce z spojené tabulky, je třeba následující položky:  
  
-   Seznam tabulky obsahující názvy všech spojených tabulek.  
  
-   Seznam sloupců, který obsahuje názvy všech zúčastněných sloupců. Sloupce se stejným názvem, ale z různých tabulek jsou kvalifikovaný název tabulky.  
  
-   Filtr (SQL **kde** klauzule), který určuje sloupce, na kterých jsou spojeny tabulky. Tento filtr má podobu "Table1.KeyCol = Table2.KeyCol" a spojení.  
  
 Srovnáním několika párů sloupců, každý pár připojí pomocí klíčového slova SQL můžete spojit více než dvě tabulky stejným způsobem **a**.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)