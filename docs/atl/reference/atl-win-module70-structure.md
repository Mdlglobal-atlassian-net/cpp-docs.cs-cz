---
title: _Atl_win_module70 – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: c000175c031868136aad44e59644d0fa122d213e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084507"
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

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

