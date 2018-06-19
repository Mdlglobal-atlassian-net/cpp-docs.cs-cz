---
title: 'Sada záznamů: Přidávání záznamů (ODBC) hromadné | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7bb39b910eae797f360513954ad0c32d5e99bb86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089282"
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