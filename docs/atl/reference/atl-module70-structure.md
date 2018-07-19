---
title: _Atl_module70 – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 9666d73eec770ff8231e5730e01520b0bee68012
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886216"
---
# <a name="atlmodule70-structure"></a>_Atl_module70 – struktura
Data používaná každého modulu ATL obsahuje.  
  
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
 Velikost struktury, použít pro správu verzí.  
  
 `m_nLockCnt`  
 Chcete-li zjistit, jak dlouho modul by mělo zůstat naživu počet referenční.  
  
 `m_pTermFuncs`  
 Sleduje funkce, které byly zaregistrovány, která se má volat při vypnutí ATL.  
  
 `m_csStaticDataInitAndTypeInfo`  
 Umožňuje koordinovat přístup k interní data v situacích s více vlákny.  
  
## <a name="remarks"></a>Poznámky  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) je definován jako typedef typu `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="see-also"></a>Viz také  
  [Třídy a struktury](../../atl/reference/atl-classes.md)







