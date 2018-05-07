---
title: ICommandImpl::m_bCancelWhenExecuting | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
dev_langs:
- C++
helpviewer_keywords:
- m_bCancelWhenExecuting
ms.assetid: d7d33e4c-a862-4e6d-a9a1-4400bfe45b88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc76547be05976e21db7dd7207945608415ee620
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icommandimplmbcancelwhenexecuting"></a>ICommandImpl::m_bCancelWhenExecuting
Určuje, zda lze příkaz zrušit při provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bCancelWhenExecuting:1;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Použije se výchozí hodnota **true** (může být zrušena).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [ICommandImpl – třída](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)