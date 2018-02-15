---
title: IRowsetChangeImpl::InsertRow | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
dev_langs:
- C++
helpviewer_keywords:
- InsertRow method
ms.assetid: 93027be3-921e-438e-a19a-6e5aadb813eb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4700e5d3bdc46c3e62022fe5838c084f043ba1a3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetchangeimplinsertrow"></a>IRowsetChangeImpl::InsertRow
Vytvoří a inicializuje nový řádek v dané sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetChange::InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetChangeImpl – třída](../../data/oledb/irowsetchangeimpl-class.md)