---
title: Struktura _ATL_COM_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168628"
---
# <a name="_atl_com_module70-structure"></a>Struktura _ATL_COM_MODULE70

Používá se v kódu souvisejícím s COM v ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Členové

`cbSize`<br/>
Velikost struktury, která se používá pro správu verzí.

`m_hInstTypeLib`<br/>
Instance popisovače do knihovny typů pro tento modul.

`m_ppAutoObjMapFirst`<br/>
Adresa prvku pole, který označuje začátek položek mapy objektu pro tento modul.

`m_ppAutoObjMapLast`<br/>
Adresa prvku pole označujícího konec položek mapování objektu pro tento modul.

`m_csObjMap`<br/>
Oddíl critical k serializaci přístupu k položkám mapy objektů. Interně používá ATL.

## <a name="remarks"></a>Poznámky

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) je definován jako definice typu _ATL_COM_MODULE70.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)
