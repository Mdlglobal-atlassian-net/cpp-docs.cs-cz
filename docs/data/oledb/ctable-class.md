---
title: CTable – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
dev_langs:
- C++
helpviewer_keywords:
- CTable class
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e12ec9f7cc7db4da78df8f3b49ed4fdadef3f769
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100142"
---
# <a name="ctable-class"></a>CTable – třída
Poskytuje i prostředky přímý přístup k jednoduché sady řádků (jeden bez parametrů).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu.  
  
 `TRowset`  
 Třídy sady řádků.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Otevřete](../../data/oledb/ctable-open.md)|Otevře se v tabulce.|  
  
## <a name="remarks"></a>Poznámky  
 V tématu [CCommand](../../data/oledb/ccommand-class.md) informace o tom, jak provést příkaz pro přístup k sadě řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)