---
title: _AtlCreateWndData Structure
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286925"
---
# <a name="atlcreatewnddata-structure"></a>_AtlCreateWndData Structure

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

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../../atl/reference/atl-classes.md)
