---
title: Struktura _ATL_BASE_MODULE70 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs: C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e824c2b85e7f80ad93a1f154be7f2e680bd00a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Struktury](../../atl/reference/atl-structures.md)





