---
title: Struktura _ATL_COM_MODULE70 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d78165481c8f2e9d8bba33ad14ebd0794f04fde
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="atlcommodule70-structure"></a>Struktura _ATL_COM_MODULE70
Používaný kód související s COM v ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Členové  
 `cbSize`  
 Velikost strukturu, použít pro správu verzí.  
  
 `m_hInstTypeLib`  
 Instance popisovače pro knihovnu typů pro tento modul.  
  
 **m_ppAutoObjMapFirst**  
 Adresa označující začátek položek mapování objektu pro tento modul pole elementu.  
  
 **m_ppAutoObjMapLast**  
 Adresa označující konec položek mapování objektu pro tento modul pole elementu.  
  
 `m_csObjMap`  
 Kritická sekce k serializaci přístup k položek mapování objektu. Interně jej využívá ATL.  
  
## <a name="remarks"></a>Poznámky  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) je definován jako typedef z `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../../atl/reference/atl-classes.md)





