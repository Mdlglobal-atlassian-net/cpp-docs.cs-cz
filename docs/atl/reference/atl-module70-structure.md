---
title: Struktura _ATL_MODULE70 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f189ef58ab83a6e77852c109e6da3ae86dc5555d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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







