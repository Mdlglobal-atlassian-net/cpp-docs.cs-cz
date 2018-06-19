---
title: Struktura _ATL_WIN_MODULE70 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 587b115c428b0d82183abbec9f712ff06ea448f4
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256077"
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
 [Třídy a struktury](../../atl/reference/atl-classes.md)





