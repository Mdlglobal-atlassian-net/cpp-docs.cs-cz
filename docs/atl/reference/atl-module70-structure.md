---
title: _Atl_module70 – struktura
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: bf733a10a0be53eafb634c645dad6a4b58b8206d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438841"
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

`cbSize`<br/>
Velikost struktury, použít pro správu verzí.

`m_nLockCnt`<br/>
Chcete-li zjistit, jak dlouho modul by mělo zůstat naživu počet referenční.

`m_pTermFuncs`<br/>
Sleduje funkce, které byly zaregistrovány, která se má volat při vypnutí ATL.

`m_csStaticDataInitAndTypeInfo`<br/>
Umožňuje koordinovat přístup k interní data v situacích s více vlákny.

## <a name="remarks"></a>Poznámky

[_ATL_MODULE](atl-typedefs.md#_atl_module) je definován jako typedef typu `_ATL_MODULE70`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

