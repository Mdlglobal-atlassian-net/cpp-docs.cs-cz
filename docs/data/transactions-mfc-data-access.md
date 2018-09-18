---
title: Transakce (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 332568d0a4a275247c95fc6b5ecfbbfcb8712acc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052204"
---
# <a name="transactions--mfc-data-access"></a>Transakce (přístup k datům MFC)

Koncept transakce byla vyvinuta zpracovat případy, ve kterých výsledný stav databáze závisí na celkový počet úspěšných řady operací. To může dojít, protože následných operací může upravit výsledky předchozí operace. V takových případech Pokud jedna operace selže, výsledný stav může být neurčitý.  
  
K vyřešení tohoto problému je transakce skupině posloupnost operací takovým způsobem, který si být jistí integrity konečný výsledek. Buď musí být všechny operace úspěšná a potom potvrdit (zapsána do databáze), nebo celá transakce nezdaří. Zrušení transakce se nazývá vrácení zpět. Vrácení zpět umožňuje obnovení změny a vrátí databázi do stavu před transakcí.  
  
Například v transakci automatizované bankovnictví, peníze při přenosu z účtu A k účtu B, jak stažení zálohy A a B musí být úspěšně zpracovat fondů správně, nebo musí selhat, celá transakce.  
  
Transakce musí mít odpovídající zásadám ACID vlastnosti, které nechá následující:  
  
- **Atomicitu** transakce je atomickou jednotku práce a provede přesně jednou; všechny práci nebo žádná.  
  
- **Konzistence** konzistenci dat, transformace konzistentní stav dat na jiný konzistentní stav dat zachová transakce. Data vázaná transakcí musí být sémanticky zachovány.  
  
- **Izolace** transakce je jednotka izolace a každá se vyskytuje samostatně a nezávisle na souběžných transakcí. Transakce by nikdy neuvidí dílčích etap jinou transakcí.  
  
- **Odolnost** transakce je jednotka pro obnovení. Pokud je transakce úspěšná, její aktualizací vyskytovat i dál, i v případě systému dojde k chybě nebo se vypne. Pokud transakce selže, systém zůstane ve stavu před spuštěním transakce.  
  
Může podporovat transakce v OLE DB (viz [podpora transakcí v OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) nebo rozhraní ODBC (naleznete v tématu [transakce (ODBC)](../data/odbc/transaction-odbc.md)).  
  
Distribuované transakce je transakce, která aktualizuje distribuovaných dat, to znamená, že data ve více než jeden síťový počítač systému. Pokud chcete zajistit podporu transakcí v distribuovaném systému, používejte ADO.NET spíše než transakce podporu technologie OLE DB.  
  
## <a name="see-also"></a>Viz také  

[Přístup k datům programování knihovny MFC nebo ATL)](../data/data-access-programming-mfc-atl.md)