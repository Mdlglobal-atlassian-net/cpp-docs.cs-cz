---
title: IRowsetImpl::RefRows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
dev_langs: C++
helpviewer_keywords: RefRows method
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c1e39eb09ebfd3d93dd8302591db3406a8154449
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimplrefrows"></a>IRowsetImpl::RefRows
Voláno rozhraním [addrefrows –](../../data/oledb/irowsetimpl-addrefrows.md) a [releaserows –](../../data/oledb/irowsetimpl-releaserows.md) buď zvýšit nebo uvolnění počet odkazů na popisovač existující řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT RefRows(  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetImpl – třída](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow – třída](../../data/oledb/csimplerow-class.md)