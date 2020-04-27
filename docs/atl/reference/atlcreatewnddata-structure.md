---
title: Struktura _AtlCreateWndData
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168537"
---
# <a name="_atlcreatewnddata-structure"></a>Struktura _AtlCreateWndData

Tato struktura obsahuje data instance třídy v kódu okna v knihovně ATL.

## <a name="syntax"></a>Syntaxe

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Členové

`m_pThis`<br/>
**Tento** ukazatel, který slouží k získání přístupu k instanci třídy v postupech okna.

`m_dwThreadID`<br/>
ID vlákna aktuální instance třídy.

`m_pNext`<br/>
Ukazatel na další `_AtlCreateWndData` objekt.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)
