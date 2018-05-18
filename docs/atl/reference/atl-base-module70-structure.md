---
title: Struktura _ATL_BASE_MODULE70 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 484fc4a68d0421cb12e901b2d56f30e95f6cb79b
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="atlbasemodule70-structure"></a>Struktura _ATL_BASE_MODULE70
Použít žádný projekt, který používá ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>Členové  
 `cbSize`  
 Velikost strukturu, použít pro správu verzí.  
  
 `m_hInst`  
 **HInstance** pro tento modul (exe nebo dll).  
  
 `m_hInstResource`  
 Výchozí popisovač prostředku instance.  
  
 **m_bNT5orWin98**  
 Informace o verzi operačního systému. Interně jej využívá ATL.  
  
 **dwAtlBuildVer**  
 Ukládá verze ATL. Aktuálně 0x0700.  
  
 **pguidVer**  
 ATL pro interní identifikátor GUID.  
  
 **m_csResource**  
 Pro přístup k synchronizaci **m_rgResourceInstance** pole. Interně jej využívá ATL.  
  
 **m_rgResourceInstance**  
 Pole použitá k vyhledání prostředků ve všech instancích prostředků, ve kterých je ATL vědět. Interně jej využívá ATL.  
  
## <a name="remarks"></a>Poznámky  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) je definován jako typedef z `_ATL_BASE_MODULE70`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../../atl/reference/atl-classes.md)





