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
ms.openlocfilehash: c5751fa3c5c8bc20f287ca3c48d885fc41c60ba0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764326"
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

`m_pThis`  
**To** ukazatel, použít k získání přístupu k instanci třídy v procedury okna.

`m_dwThreadID`  
ID vlákna z aktuální instance třídy.

`m_pNext`  
Ukazatel na další `_AtlCreateWndData` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)

