---
title: IRowsetChangeImpl::DeleteRows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
dev_langs: C++
helpviewer_keywords: DeleteRows method
ms.assetid: 462ad4f1-3b2a-4134-9733-be65708aa1d9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2416ab420473ceb0162a0ab0743047f7d51431a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimpldeleterows"></a>IRowsetChangeImpl::DeleteRows
Odstraní řádky ze sady řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      STDMETHOD ( DeleteRows )(  
   HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IRowsetChange::DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IRowsetChangeImpl – třída](../../data/oledb/irowsetchangeimpl-class.md)