---
title: "Podpora transakcí v prostředí OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9be6fb1c86b43f7833818648d84875b1e4c55b59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-transactions-in-ole-db"></a>Podpora transakcí v prostředí OLE DB
A [transakce](../../data/transactions-mfc-data-access.md) je způsob, jak skupinu nebo dávky, řadu aktualizací ke zdroji dat, takže buď všechny úspěšné a jsou najednou, nebo (Pokud některá z nich selže) žádná není potvrzena a celá transakce bude vrácena zpět. Tento proces zajišťuje integritu výsledku na datovém zdroji.  
  
 OLE DB podporuje transakce s následující tři metody:  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [Metody ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>Vztah relací a transakcí  
 Objekt jednoho datového zdroje můžete vytvořit jeden nebo více objektů relace, z nichž každá může být uvnitř nebo mimo rozsah transakcí v daném okamžiku.  
  
 Pokud relace nevstupuje transakce, všechny práci v rámci této relace v úložišti dat se okamžitě potvrdí při každém volání metody. (To se někdy označuje jako režimu automatického zápisu nebo implicitní režimu.)  
  
 Když relaci zadá transakci, všechny práci v této relaci na úložiště dat je součástí této transakce a je potvrzené nebo přerušena jako na jednu jednotku. (To se někdy označuje jako režim ručního potvrzování.)  
  
 Podpora transakcí je specifický pro zprostředkovatele. Pokud používáte poskytovatele podporuje transakce, objekt relace, který podporuje **ITransaction** a **ITransactionLocal** můžete zadat jednoduchý (tedy bez vnoření) transakce. Třída šablon technologie OLE DB [CSession](../../data/oledb/csession-class.md) podporuje tato rozhraní a je doporučeným způsobem, jak implementovat podporu transakce v jazyce Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Počáteční a koncovou transakce  
 Volání `StartTransaction`, **potvrdit**, a **Abort** metody v objektu sady řádků v příjemci.  
  
 Volání metody **ITransactionLocal::StartTransaction** spustí novou místní transakce. Při spuštění transakce se změny provedou následující operace neaplikují ve skutečnosti k úložišti dat dokud potvrzení transakce.  
  
 Volání metody **metody ITransaction::Commit** nebo **ITransaction::Abort** končí transakce. **Potvrdit** způsobí, že všechny změny v rozsahu transakcí má být použita k úložišti dat. **Abort** příčiny všechny změny v rámci oboru transakce budou zrušeny a úložiště dat je nacházela ve stavu měl před zahájením transakce.  
  
## <a name="nested-transactions"></a>Vnořené transakce  
 A [vnořené transakce](https://msdn.microsoft.com/en-us/library/ms716985.aspx) dojde při spuštění nové místní transakce v rámci aktivní transakce. Novou transakci je spuštěn jako vnořenou transakci v aktuální transakci. Pokud zprostředkovatel nepodporuje vnořené transakce, volání `StartTransaction` při již existuje aktivní transakce na relaci vrátí **XACT_E_XTIONEXISTS**.  
  
## <a name="distributed-transactions"></a>Distribuované transakce  
 Distribuovaná transakce je transakci, která aktualizuje distribuovaná data; To znamená, data na více systémů počítači v síti. Pokud chcete podporovat transakce přes distribuovaného systému, používejte rozhraní .NET Framework, nikoli podporu transakce OLE DB.  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)