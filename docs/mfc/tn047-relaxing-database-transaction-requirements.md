---
title: 'TN047: Uvolnění požadavků transakcí databáze | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be5870efacb61d5c0bb74f85427c41f787d2edd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380930"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: Uvolnění požadavků na databázové transakce
Tato technická Poznámka, která popsané požadavků transakce databázové třídy MFC rozhraní ODBC, je nyní zastaralá. Před MFC 4.2 databázové třídy vyžaduje, že kurzory se zachová, i na sady záznamů po **CommitTrans** nebo **vrácení zpět** operaci. Pokud ovladač ODBC a databázového systému nepodporují tato úroveň písmen a zachovávání kurzoru, pak databázové třídy nepovolili transakce.  
  
 Počínaje MFC 4.2, databázové třídy mít mírnější omezení vyžadoval písmen a zachovávání kurzoru. Transakce bude povoleno, jestliže je ovladač podporuje. Však musí být nyní zkontrolovat dopad **CommitTrans** nebo **vrácení zpět** operace na otevřete sady záznamů. Členské funkce v tématu [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) a [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

