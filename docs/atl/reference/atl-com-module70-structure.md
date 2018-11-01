---
title: _Atl_com_module70 – struktura
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: 4a5c464fd6449653517f0994ab8dac1ef7bbdd18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590206"
---
# <a name="atlcommodule70-structure"></a>_Atl_com_module70 – struktura

Používaný kód související s modelu COM v knihovně ATL

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

`cbSize`<br/>
Velikost struktury, použít pro správu verzí.

`m_hInstTypeLib`<br/>
Popisovač instance do knihovny typů pro tento modul.

`m_ppAutoObjMapFirst`<br/>
Adresa prvku pole označující začátek položky mapování objektu pro tento modul.

`m_ppAutoObjMapLast`<br/>
Adresa prvku pole označující konec položky mapování objektu pro tento modul.

`m_csObjMap`<br/>
Kritická sekce k serializaci přístup k položky objektu map. Vnitřně jej používá knihovnu ATL.

## <a name="remarks"></a>Poznámky

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) je definován jako typedef _atl_com_module70 –.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

