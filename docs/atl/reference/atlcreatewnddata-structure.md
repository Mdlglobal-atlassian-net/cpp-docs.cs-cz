---
title: _Atlcreatewnddata – struktura
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 860d5772279d0ca0581a8cac1e0ef224f829586d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534183"
---
# <a name="atlcreatewnddata-structure"></a>_Atlcreatewnddata – struktura

Tato struktura obsahuje data instance třídy v kódu časová okna v knihovně ATL

## <a name="syntax"></a>Syntaxe

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Členové

`m_pThis`<br/>
**To** ukazatel, použít k získání přístupu k instanci třídy v procedury okna.

`m_dwThreadID`<br/>
ID vlákna z aktuální instance třídy.

`m_pNext`<br/>
Ukazatel na další `_AtlCreateWndData` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

