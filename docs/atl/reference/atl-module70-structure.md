---
title: Struktura _ATL_MODULE70 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs: C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 104596d55ee2580cbee3cfc916ad9ef7390ce4c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atlmodule70-structure"></a>Struktura _ATL_MODULE70
Obsahuje data využívaná každých ATL modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>Členové  
 `cbSize`  
 Velikost strukturu, použít pro správu verzí.  
  
 `m_nLockCnt`  
 Odkaz na počet k určení, jak dlouho má zůstat modul zachování připojení.  
  
 **m_pTermFuncs**  
 Sleduje funkce, které byly zaregistrovány, která se má volat při vypnutí ATL.  
  
 **m_csStaticDataInitAndTypeInfo**  
 Slouží ke koordinaci přístup k interní dat v situacích s více vlákny.  
  
## <a name="remarks"></a>Poznámky  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) je definován jako typedef z `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury](../../atl/reference/atl-structures.md)







