---
title: Struktura _ATL_WIN_MODULE70 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs: C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 733808006a3c301972c4ab3b3f8de3320d9fde46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atlwinmodule70-structure"></a>Struktura _ATL_WIN_MODULE70
Používaný kód oddílová v ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize; 
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```  
  
## <a name="members"></a>Členové  
 `cbSize`  
 Velikost strukturu, použít pro správu verzí.  
  
 `m_csWindowCreate`  
 Používaný k serializaci přístup ke kódu okno registrace. Interně jej využívá ATL.  
  
 **m_pCreateWndList**  
 Použije pro vazbu windows k jejich objekty. Interně jej využívá ATL.  
  
 **m_rgWindowClassAtoms**  
 Použít ke sledování registrace třídy okna tak, aby mohly být správně registrace na ukončení. Interně jej využívá ATL.  
  
## <a name="remarks"></a>Poznámky  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) je definován jako typedef z `_ATL_WIN_MODULE70`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury](../../atl/reference/atl-structures.md)





