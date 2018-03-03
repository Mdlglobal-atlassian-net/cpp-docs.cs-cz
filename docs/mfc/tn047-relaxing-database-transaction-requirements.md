---
title: "TN047: Uvolnění požadavků transakcí databáze | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92631d96e8782a80275695ef4bf2623dc1bff833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: Uvolnění požadavků na databázové transakce
Tato technická Poznámka, která popsané požadavků transakce databázové třídy MFC rozhraní ODBC, je nyní zastaralá. Před MFC 4.2 databázové třídy vyžaduje, že kurzory se zachová, i na sady záznamů po **CommitTrans** nebo **vrácení zpět** operaci. Pokud ovladač ODBC a databázového systému nepodporují tato úroveň písmen a zachovávání kurzoru, pak databázové třídy nepovolili transakce.  
  
 Počínaje MFC 4.2, databázové třídy mít mírnější omezení vyžadoval písmen a zachovávání kurzoru. Transakce bude povoleno, jestliže je ovladač podporuje. Však musí být nyní zkontrolovat dopad **CommitTrans** nebo **vrácení zpět** operace na otevřete sady záznamů. Členské funkce v tématu [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) a [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

