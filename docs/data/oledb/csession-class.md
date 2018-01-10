---
title: "CSession – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs: C++
helpviewer_keywords: CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d8b6bb75d12b4ab96c3a44c74f4487eb8a70efc6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csession-class"></a>CSession – třída
Představuje relaci přístup k jedné databáze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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