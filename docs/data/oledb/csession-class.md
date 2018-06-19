---
title: CSession – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03c0bfec758bb663803b05b1f690816394f61239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097078"
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
|[Gettransactioninfo –](../../data/oledb/csession-gettransactioninfo.md)|Vrátí informace o transakci.|  
|[Otevřete](../../data/oledb/csession-open.md)|Otevře se nová relace pro objekt zdroje dat.|  
|[StartTransaction –](../../data/oledb/csession-starttransaction.md)|Spustí novou transakci pro tuto relaci.|  
  
## <a name="remarks"></a>Poznámky  
 Jeden nebo více relací lze přidružit ke každé poskytovatele připojení (zdroj dat), která je reprezentována [CDataSource](../../data/oledb/cdatasource-class.md) objektu. Chcete-li vytvořit novou `CSession` pro `CDataSource`, volání [CSession::Open](../../data/oledb/csession-open.md). K zahájení transakce databáze, `CSession` poskytuje `StartTransaction` metoda. Po spuštění transakce můžete potvrdit se pomocí **potvrzení** metoda, nebo zrušit pomocí **Abort** metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Ukázky CatDB](../../visual-cpp-samples.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)