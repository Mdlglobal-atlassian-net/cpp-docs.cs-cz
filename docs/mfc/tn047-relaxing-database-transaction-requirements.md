---
title: 'TN047: Uvolnění požadavků na databázové transakce'
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
ms.openlocfilehash: 968420658a90c983d8e6c3eaf1e0c61603fc5441
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305343"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: Uvolnění požadavků na databázové transakce

Tato poznámka Odborný popsané požadavků na transakce databáze tříd knihovny MFC rozhraní ODBC, je nyní zastaralá. Před MFC 4.2 databázové třídy vyžaduje, že při sady záznamů po zachovány kurzory **CommitTrans** nebo **vrácení zpět** operace. Pokud ovladač ODBC a DBMS nepodporuje tuto úroveň kurzoru a zachovávání s rozlišením, pak databázové třídy nepovolili transakce.

Od verze 4.2 knihovny MFC, databázové třídy mít mírnější omezení vyžadování kurzoru a zachovávání s rozlišením. Transakce se aktivuje, pokud je ovladač podporuje. Však musí nyní zkontrolovat dopad **CommitTrans** nebo **vrácení zpět** operace na otevřené sady záznamů. Podívat se na členské funkce [CDatabase::GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) a [CDatabase::GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) Další informace.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
