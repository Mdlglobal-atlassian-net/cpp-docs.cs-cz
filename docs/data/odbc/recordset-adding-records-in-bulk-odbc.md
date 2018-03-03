---
title: "Sada záznamů: Přidávání záznamů (ODBC) hromadné | Microsoft Docs"
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
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 251d2fa4b7c28c1458fdc5643c9b17c53ba1b0ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Sada záznamů: Hromadné přidávání záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 MFC [CRecordset](../../mfc/reference/crecordset-class.md) třída má nové optimalizace, které ke zlepšení efektivity při přidávání nové záznamy hromadně do tabulky.  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Nová možnost pro **dwOptions** parametru [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) – členská funkce **optimizeBulkAdd**, zvyšuje výkon, když přidáváte více záznamů po sobě bez volání **Requery –** nebo **Zavřít**. Pouze pole, které jsou chybná před první **aktualizace** volání jsou označeny jako nekonzistentní pro následné `AddNew` / **aktualizace** volání.  
  
 Pokud chcete využít výhod používáte databázové třídy **:: SQLSetPos** rozhraní API ODBC funkce pro přidávání, úpravám a odstraňování záznamů, tato optimalizace je zbytečné.  
  
 Pokud knihovny kurzorů ODBC je načtena, nebo ovladač ODBC nepodporuje přidání, úpravy a odstraňování prostřednictvím **:: SQLSetPos**, tato optimalizace měli zlepšit hromadné přidání výkonu. Chcete-li zapnout optimalizace, nastavte **dwOptions** parametr ve **otevřete** volání pro sady záznamů pro následující:  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)