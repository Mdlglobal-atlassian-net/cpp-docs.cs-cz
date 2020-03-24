---
title: Transakce (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
ms.openlocfilehash: 742e95d896d107fb89b3d65f0eeb6d418f1b2057
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209063"
---
# <a name="transactions--mfc-data-access"></a>Transakce (přístup k datům MFC)

Koncept transakce byl vyvinut za účelem zpracování případů, ve kterých je výsledný stav databáze závislý na celkovém úspěchu řady operací. Může to být způsobeno tím, že po sobě jdoucí operace mohou změnit výsledky předchozích operací. V takových případech, pokud některá z operací dojde k chybě, výsledný stav může být neurčitý.

Chcete-li tento problém vyřešit, seskupí transakce řadu operací takovým způsobem, že může být zajištěna integrita konečného výsledku. Všechny operace musí být úspěšné a pak být potvrzeny (zapsány do databáze) nebo celá transakce selže. Zrušení transakce se nazývá vrácení. Vrácení zpět umožňuje obnovení ze změn a vrátí databázi do stavu před transakcí.

Například v případě automatizované bankovní transakce, pokud přenášíte peníze z účtu A na účet B, stažení z a a vklad na B musí úspěšně správně zpracovat prostředky nebo celá transakce musí selhat.

Transakce musí mít vlastnosti KYSELosti, které by měly být v následujících případech:

- **Nedělitelnost** Transakce je atomická jednotka práce a provede se právě jednou; buď je dokončená, nebo žádná z nich.

- **Konzistence** Transakce zachovává konzistenci dat a transformuje jeden konzistentní stav dat do jiného konzistentního stavu dat. Data vázaná transakcemi musí být sémanticky zachovaná.

- **Izolace** Transakce je jednotka izolace a každá dojde samostatně a nezávisle na souběžných transakcích. Transakce by nikdy neměla vidět mezilehlé fáze jiné transakce.

- **Odolnost** Transakce je jednotka obnovení. Pokud je transakce úspěšná, její aktualizace se zachovají, i když dojde k chybě nebo vypnutí systému. Pokud transakce dojde k chybě, systém zůstane ve stavu předchozí a potvrzení transakce.

Můžete podporovat transakce v OLE DB (viz [podpůrné transakce v OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) nebo rozhraní ODBC (viz [transakce (ODBC)](../data/odbc/transaction-odbc.md)).

Distribuovaná transakce je transakce, která aktualizuje distribuovaná data, tj. data ve více než jednom síťovém systému počítače. Pokud chcete podporovat transakce v distribuovaném systému, měli byste místo podpory OLE DB transakcí používat ADO.NET.

## <a name="see-also"></a>Viz také

[Programování přístupu k datům (MFC/ATL)](../data/data-access-programming-mfc-atl.md)
