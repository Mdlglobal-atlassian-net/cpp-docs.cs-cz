---
title: ICommandImpl::m_bIsExecuting | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
dev_langs:
- C++
helpviewer_keywords:
- m_bIsExecuting
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fccd78da21233a8b5b033d5b2b6d0e568a1aefb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="icommandimplmbisexecuting"></a>ICommandImpl::m_bIsExecuting
Určuje, zda příkaz právě probíhá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bIsExecuting:1;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Execute** metoda vaší třídy příkazu můžete tuto proměnnou nastavit na **true**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [ICommandImpl – třída](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)