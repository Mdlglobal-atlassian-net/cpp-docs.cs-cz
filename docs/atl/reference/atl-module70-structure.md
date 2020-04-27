---
title: Struktura _ATL_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8d39cdd281e09cdfe09546627aa630a11d12464e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168563"
---
# <a name="_atl_module70-structure"></a>Struktura _ATL_MODULE70

Obsahuje data používaná všemi moduly ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Členové

`cbSize`<br/>
Velikost struktury, která se používá pro správu verzí.

`m_nLockCnt`<br/>
Počet odkazů, který určuje, jak dlouho má modul zůstat aktivní

`m_pTermFuncs`<br/>
Sleduje funkce, které byly zaregistrovány pro volání při vypnutí knihovny ATL.

`m_csStaticDataInitAndTypeInfo`<br/>
Slouží k koordinaci přístupu k interním datům v situacích s více vlákny.

## <a name="remarks"></a>Poznámky

[_ATL_MODULE](atl-typedefs.md#_atl_module) je definován jako definice typu `_ATL_MODULE70`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)
