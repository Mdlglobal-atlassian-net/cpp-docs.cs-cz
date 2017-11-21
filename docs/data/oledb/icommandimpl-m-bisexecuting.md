---
title: ICommandImpl::m_bIsExecuting | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
dev_langs: C++
helpviewer_keywords: m_bIsExecuting
ms.assetid: 1e152164-514c-4116-88a3-16984af99991
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f65bba12d56ec8e73dacd661ba551aa6e3ea636b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="icommandimplmbisexecuting"></a>ICommandImpl::m_bIsExecuting
Určuje, zda příkaz právě probíhá.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
unsigned m_bIsExecuting:1;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Execute** metoda vaší třídy příkazu můžete tuto proměnnou nastavit na **true**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [ICommandImpl – třída](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)