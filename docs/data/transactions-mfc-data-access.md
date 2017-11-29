---
title: Transakce (MFC Data Access) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 655c8e2cc900aa369055e5f1b9975e02c1a8ac88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="transactions--mfc-data-access"></a>Transakce (Data MFC Access)
Koncept transakce byla vyvinuta pro zpracování případů, kdy výsledný stav databáze závisí na celkový úspěch řady operací. Tato situace může přijít vzhledem k tomu, že po sobě jdoucí operace může upravit výsledky předchozí operace. V takových případech jedna operace selže, výsledný stav by neurčitou.  
  
 Chcete-li tento problém vyřešit, transakce skupiny řady operací takovým tak, aby bylo možno integritu konečný výsledek. Buď musí být všechny operace úspěšné a potom potvrzené (zapsána do databáze), nebo selže celá transakce. Zrušení transakce se nazývá vrácení zpět. Vrácení zpět umožňuje obnovení změny a vrátí databázi do stavu před transakcí.  
  
 Například v automatizované bankovní transakci, převod peněz z účtu A k účtu B, jak odstoupení od uložení A a b musí být zpracován fondů správně, nebo celá transakce selhat.  
  
 Transakce musí mít ACID vlastnosti, které stát pro následující:  
  
-   **Nedělitelnost** transakce je atomické jednotky práce a provede právě jednou, všechny práci nebo žádná.  
  
-   **Konzistence** transakce se zachovají konzistenci dat, převádí jeden konzistentní stav dat do jiné konzistentní stav dat. Data vázání transakce musí být sémanticky zachována.  
  
-   **Izolace** transakce je jednotka izolace a ke všem dochází samostatně a nezávisle na souběžných transakcí. Transakce by se nikdy zobrazit dílčí etapy jiné transakci.  
  
-   **Odolnost** transakce je jednotka obnovení. Pokud transakce úspěšné, uchová, jeho aktualizací, i když dojde k chybě systému, nebo se vypne. V případě selhání transakce systému zůstane ve stavu před spuštěním transakce.  
  
 Může podporovat transakce v OLE DB (najdete v části [podpora transakcí v OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) nebo rozhraní ODBC (viz [transakce (ODBC)](../data/odbc/transaction-odbc.md)).  
  
 Distribuovaná transakce je transakcí, která aktualizuje distribuované dat, který je dat na více systémů počítači v síti. Pokud chcete podporovat transakce přes distribuovaného systému, používejte ADO.NET, nikoli podporu transakce OLE DB.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k datům programování (MFC/ATL)](../data/data-access-programming-mfc-atl.md)