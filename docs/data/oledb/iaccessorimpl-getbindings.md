---
title: IAccessorImpl::GetBindings | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
dev_langs:
- C++
helpviewer_keywords:
- GetBindings method
ms.assetid: eb550077-77ef-450b-89f1-a2930cee6ab8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 20c6bec779dbe026bbc0aa2cec41824c37570559
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="iaccessorimplgetbindings"></a>IAccessorImpl::GetBindings
Vrátí základní sloupce vazby od příjemce v přistupující objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(GetBindings)(HACCESSOR hAccessor,  
   DBACCESSORFLAGS* pdwAccessorFlags,  
   DBCOUNTITEM* pcBindings,  
   DBBINDING** prgBindings);  
```  
  
#### <a name="parameters"></a>Parametry  
 V tématu [IAccessor::GetBindings](https://msdn.microsoft.com/en-us/library/ms721253.aspx) v *referenční příručka programátora prostředí OLE DB*.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [IAccessorImpl – třída](../../data/oledb/iaccessorimpl-class.md)