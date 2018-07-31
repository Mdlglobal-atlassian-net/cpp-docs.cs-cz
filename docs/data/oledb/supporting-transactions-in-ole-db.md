---
title: Podpora transakcí v prostředí OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 932185002032ab86ca80b2b3384bfe6cbb69f8b1
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338707"
---
# <a name="supporting-transactions-in-ole-db"></a>Podpora transakcí v prostředí OLE DB
A [transakce](../../data/transactions-mfc-data-access.md) je způsob, jak seskupit nebo služby batch, řadu aktualizací ke zdroji dat tak, aby všechny úspěšné a usilujeme o to najednou, nebo (Pokud některá z nich selže), žádná není potvrzena a celá transakce bude vrácena zpět. Tento proces zajistí integritu výsledek pro zdroj dat.  
  
 OLE DB podporuje transakce pomocí následujících tří metod:  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/library/ms709786.aspx)  
  
-   [ITransaction::Commit](https://msdn.microsoft.com/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>Vztah mezi relacemi a transakce  
 Objekt jednoho datového zdroje můžete vytvořit jeden nebo více objektů relace, z nichž každá může být uvnitř nebo mimo obor transakce v daném okamžiku.  
  
 Když relace není zadejte transakce, veškerou práci prováděnou v rámci této relace v úložišti dat okamžitě potvrzeny při každém volání metody. (To se někdy označuje jako automatický zápis nebo implicitní režimu.)  
  
 Když je relace zadá transakci, veškerou práci prováděnou v úložišti dat v rámci této relace je součástí této transakce a potvrzena nebo zrušena jako jeden celek. (To se někdy označuje jako ruční potvrzováním režim.)  
  
 Podpora transakcí je specifický pro zprostředkovatele. Pokud používáte poskytovatele podporuje transakce, objekt relace, který podporuje `ITransaction` a `ITransactionLocal` můžete zadat jednoduchý (to znamená bez vnoření) transakce. Třída šablony technologie OLE DB [CSession](../../data/oledb/csession-class.md) podporuje tato rozhraní a je doporučený způsob implementace podpora transakcí v jazyce Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Počáteční a koncovou transakce  
 Volání `StartTransaction`, `Commit`, a `Abort` metody v objektu sady řádků v příjemci.  
  
 Volání `ITransactionLocal::StartTransaction` spustí novou místní transakci. Při spuštění transakce zákonného následné operace se uplatní se všechny změny ve skutečnosti do úložiště dat. dokud potvrzení transakce.  
  
 Volání `ITransaction::Commit` nebo `ITransaction::Abort` končí transakce. `Commit` způsobí, že všechny změny v rámci oboru transakce u úložiště dat. `Abort` způsobí, že všechny změny v rámci oboru transakce budou zrušeny a úložiště dat se nacházela ve stavu došlo před spuštěním transakce.  
  
## <a name="nested-transactions"></a>Vnořené transakce  
 A [vnořená transakce](https://msdn.microsoft.com/library/ms716985.aspx) nastane, pokud se spuštění nové místní transakce v aktivní transakci již. Nové transakce je spuštěn jako vnořenou transakci pod aktuální transakce. Pokud zprostředkovatel nepodporuje vnořené transakce, volání `StartTransaction` již existuje aktivní transakce v relaci vrátí XACT_E_XTIONEXISTS.  
  
## <a name="distributed-transactions"></a>Distribuované transakce  
 Distribuované transakce je transakce, která aktualizuje distribuovaných dat; To znamená, že data ve více než jeden síťový počítač systému. Pokud chcete zajistit podporu transakcí v distribuovaném systému, používejte rozhraní .NET Framework než transakce podporu technologie OLE DB.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)