---
title: Použití ručních přístupových objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dceca7ead0910474b2277538066d3cbae4bc791e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213825"
---
# <a name="using-manual-accessors"></a>Použití ručních přístupových objektů
Existují čtyři kroky, které při zpracování Neznámý příkaz:  
  
-   Určuje parametry  
  
-   Spusťte příkaz  
  
-   Určení výstupní sloupce  
  
-   Zkontrolujte, jestli více vrácení sad řádků  
  
 Chcete-li to provést pomocí šablony příjemce technologie OLE DB, použijte `CManualAccessor` třídy a postupujte podle těchto kroků:  
  
1.  Otevřít `CCommand` objekt s `CManualAccessor` jako parametr šablony.  
  
    ```cpp  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Dotaz na relaci `IDBSchemaRowset` rozhraní a používat parametry procedury sady řádků. Pokud `IDBSchemaRowset` rozhraní není k dispozici, dotázat `ICommandWithParameters` rozhraní. Volání `GetParameterInfo` informace. Pokud je k dispozici žádná rozhraní, můžete předpokládat, že neexistují žádné parametry.  
  
3.  Pro každý parametr volání `AddParameterEntry` přidat parametry a jejich nastavení.  
  
4.  Otevřít v sadě řádků, ale nastavit vazbu parametru **false**.  
  
5.  Volání `GetColumnInfo` načíst výstupní sloupce. Použití `AddBindEntry` Přidat výstupní sloupec do vazby.  
  
6.  Volání `GetNextResult` k určení, zda jsou k dispozici více sad řádků. Opakujte kroky 2 až 5.  
  
 Příklad ruční přistupujícího objektu, najdete v části `CDBListView::CallProcedure` v [DBVIEWER](https://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) vzorku.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)