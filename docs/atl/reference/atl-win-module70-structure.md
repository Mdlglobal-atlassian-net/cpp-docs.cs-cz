---
title: Struktura _ATL_WIN_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168550"
---
# <a name="_atl_win_module70-structure"></a>Struktura _ATL_WIN_MODULE70

Používá se kódem okna v ATL.

## <a name="syntax"></a>Syntaxe

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Členové

`cbSize`<br/>
Velikost struktury, která se používá pro správu verzí.

`m_csWindowCreate`<br/>
Slouží k serializaci přístupu k registračnímu kódu okna. Interně používá ATL.

`m_pCreateWndList`<br/>
Slouží k svázání oken s objekty. Interně používá ATL.

`m_rgWindowClassAtoms`<br/>
Používá se ke sledování registrací tříd oken, aby je bylo možné po ukončení správně zrušit. Interně používá ATL.

## <a name="remarks"></a>Poznámky

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) je definován jako definice typu `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)
