---
title: _Atlcreatewnddata – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c0fb14574aedb74d756e72a93cd0dc626ba086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057376"
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

