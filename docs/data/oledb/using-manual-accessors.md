---
title: "Použití ručních přístupových objektů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7d6bd8f0228103e4899e6bc24f6d67af0f3fdb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="using-manual-accessors"></a>Použití ručních přístupových objektů
Existují čtyři co je třeba provést při zpracování Neznámý příkaz:  
  
-   Určení parametrů  
  
-   Spusťte příkaz  
  
-   Určit výstupní sloupce  
  
-   Podívejte se, pokud jsou vráceno více sad řádků  
  
 Chcete-li to provést pomocí šablony příjemce technologie OLE DB, použijte `CManualAccessor` třídy a postupujte podle těchto kroků:  
  
1.  Otevřete `CCommand` objektu s `CManualAccessor` jako parametr šablony.  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Dotaz na relaci **IDBSchemaRowset** rozhraní a používat parametry procedury sady řádků. Pokud **IDBSchemaRowset** rozhraní není k dispozici, dotazu `ICommandWithParameters` rozhraní. Volání `GetParameterInfo` informace. Pokud je k dispozici žádná rozhraní, můžete předpokládat, že neexistují žádné parametry.  
  
3.  Pro každý parametr volání `AddParameterEntry` k přidání parametrů a jejich nastavení.  
  
4.  Otevřete sadu řádků, ale nastavte vazbu parametru **false**.  
  
5.  Volání `GetColumnInfo` načíst výstupní sloupce. Použití `AddBindEntry` přidat výstupního sloupce do vazby.  
  
6.  Volání `GetNextResult` k určení, pokud je k dispozici více sad řádků. Opakujte kroky 2 až 5.  
  
 Příklad ruční přistupující objekt, naleznete v části **CDBListView::CallProcedure** v [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ukázka.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)