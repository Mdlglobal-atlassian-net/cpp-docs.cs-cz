---
title: "CSession – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs:
- C++
helpviewer_keywords:
- CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a5f2a764aaa7e10b957955dc11ee35ee44f9472
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="csession-class"></a>CSession – třída
Představuje relaci přístup k jedné databáze.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CSession  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Přerušení](../../data/oledb/csession-abort.md)|Zruší (ukončí) transakce.|  
|[Zavřete](../../data/oledb/csession-close.md)|Ukončení relace.|  
|[Potvrzení](../../data/oledb/csession-commit.md)|Potvrdí transakce.|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|Vrátí informace o transakci.|  
|[Open](../../data/oledb/csession-open.md)|Otevře se nová relace pro objekt zdroje dat.|  
|[StartTransaction –](../../data/oledb/csession-starttransaction.md)|Spustí novou transakci pro tuto relaci.|  
  
## <a name="remarks"></a>Poznámky  
 Jeden nebo více relací lze přidružit ke každé poskytovatele připojení (zdroj dat), která je reprezentována [CDataSource](../../data/oledb/cdatasource-class.md) objektu. Chcete-li vytvořit novou `CSession` pro `CDataSource`, volání [CSession::Open](../../data/oledb/csession-open.md). K zahájení transakce databáze, `CSession` poskytuje `StartTransaction` metoda. Po spuštění transakce můžete potvrdit se pomocí **potvrzení** metoda, nebo zrušit pomocí **Abort** metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CatDB](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)