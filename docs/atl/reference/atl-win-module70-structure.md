---
title: _Atl_win_module70 – struktura
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 0b636d328852daf821269230aae443cef084578b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260750"
---
# <a name="atlwinmodule70-structure"></a>_Atl_win_module70 – struktura

Používaný kód časová okna v knihovně ATL

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

`cbSize`<br/>
Velikost struktury, použít pro správu verzí.

`m_csWindowCreate`<br/>
Slouží k serializaci přístup k okna registrační kód. Vnitřně jej používá knihovnu ATL.

`m_pCreateWndList`<br/>
Lze svázat objekty, které windows. Vnitřně jej používá knihovnu ATL.

`m_rgWindowClassAtoms`<br/>
Používá ke sledování registrace tříd oken tak, aby mohly být správně zrušit registraci při ukončení. Vnitřně jej používá knihovnu ATL.

## <a name="remarks"></a>Poznámky

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) je definován jako typedef typu `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../../atl/reference/atl-classes.md)
